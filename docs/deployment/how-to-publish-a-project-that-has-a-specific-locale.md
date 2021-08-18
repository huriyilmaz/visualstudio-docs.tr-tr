---
title: Belirli bir yerel bölgeye sahip bir projeyi yayımlama
description: Makro kullanarak birkaç farklı yerel bölgeye yönelik projeler içeren bir çözümde ilk projeyi yayımlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, localized projects
- locales, publishing for
- deploying applications [ClickOnce], localized projects
- locales, deploying for
- publishing localized projects
- macros, deploying with
- macros, publishing with
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: f97d5cdce15d5bc46256db709421bf83ab48ac9c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127915"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Nasıllı: Belirli bir yerel bölgeye sahip bir projeyi yayımlama
Bir uygulamanın farklı yerellere sahip bileşenleri içermesi yaygın bir durum değildir. Bu senaryoda, birden fazla projesi olan bir çözüm oluşturabilir ve ardından her yerel bölge için ayrı projeler yayımlayacaktır. Bu yordam, 'en' yerel ifadesini kullanarak bir çözümde ilk projeyi yayımlamak için bir makronun nasıl kullanıla bir işlem olduğunu gösterir. Bu yordamı 'en' dışında bir yerel ayarla denemek için makroda, kullanmakta olduğunu yerel ayar ile eşle `localeString` (örneğin, 'de' veya 'de-DE' ) ayarlayın.

> [!NOTE]
> Bu makroyu kullanırken, Yayımlama Konumu geçerli bir URL veya Evrensel Adlandırma Kuralı (UNC) paylaşımı olmalıdır. Ayrıca, Internet Information Services (IIS) bilgisayarınızda yüklü olmalıdır. IIS'yi yüklemek için Başlat **menüsünde** **Denetim Masası.** Program Ekle veya **Kaldır'a çift tıklayın.** Program **Ekle veya Kaldır'da,** Bileşen **Ekle/Kaldır'Windows tıklayın.** Windows **Sihirbazı'nda,** Bileşenler listesinde **Internet Information Services (IIS)** onay **kutusunu** seçin. Ardından Sihirbazı **kapatmak** için Son'a tıklayın.

### <a name="to-create-the-publishing-macro"></a>Yayımlama makrosu oluşturmak için

1. Makro Gezgini'ni açmak için Araçlar **menüsünde** Makrolar'ın **üzerine gelin** ve Makro Gezgini'ne **tıklayın.**

2. Yeni bir makro modülü oluşturun. Makro Gezgini'nde **MyMacros'u seçin.** Araçlar  menüsünde Makrolar'ın **üzerine gelin ve** ardından Yeni Makro **Modülü'ne tıklayın.** Modülü **PublishSpecificCulture olarak adlayın.**

3. Makro Gezgini'nde **MyMacros** düğümünü genişletin ve **ardından PublishAllProjects** modülünü çift tıklayarak  açın (veya Araçlar menüsünde Makrolar'ın üzerine gelin ve **Makrolar IDE'ye tıklayın).**

4. Makrolar IDE'de aşağıdaki kodu modüle, deyimlerden `Import` sonra ekleyin:

    ```vb
    Module PublishSpecificCulture
        Sub PublishProjectFirstProjectWithEnLocale()
            ' Note: You should publish projects by using the IDE at least once
            ' before you use this macro. Items such as the certificate and the
            ' security zone must be set.
            Dim localeString As String = "en"

            ' Get first project.
            Dim proj As Project = DTE.Solution.Projects.Item(1)
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value

            ' GenerateManifests and SignManifests must always be set to
            ' True for publishing to work.
            proj.Properties.Item("GenerateManifests").Value = True
            proj.Properties.Item("SignManifests").Value = True

            'Set the publish language.
            'This will set the deployment language and pick up all
            ' en resource dlls:
            Dim originalTargetCulture As String = _
                publishProperties.Item("TargetCulture").Value
            publishProperties.Item("TargetCulture").Value = localeString

            'Append 'en' to end of publish, install, and update URLs if needed:
            Dim originalPublishUrl As String = _
                publishProperties.Item("PublishUrl").Value
            Dim originalInstallUrl As String = _
                publishProperties.Item("InstallUrl").Value
            Dim originalUpdateUrl As String = _
                publishProperties.Item("UpdateUrl").Value
            publishProperties.Item("PublishUrl").Value = _
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))
            If originalInstallUrl <> String.Empty Then
                publishProperties.Item("InstallUrl").Value = _
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))
            End If
            If originalUpdateUrl <> String.Empty Then
                publishProperties.Item("UpdateUrl").Value = _
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))
            End If
            proj.Save()

            Dim slnbld2 As SolutionBuild2 = _
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)
            slnbld2.Clean(True)

            slnbld2.BuildProject( _
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _
            proj.UniqueName, True)

            ' Only publish if build is successful.
            If slnbld2.LastBuildInfo <> 0 Then
                MsgBox("Build failed for " & proj.UniqueName)
            Else
                slnbld2.PublishProject( _
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _
                proj.UniqueName, True)
                If slnbld2.LastPublishInfo = 0 Then
                    MsgBox("Publish succeeded for " & proj.UniqueName _
                    & vbCrLf & "." _
                    & " Publish Language was '" & localeString & "'.")
                Else
                    MsgBox("Publish failed for " & proj.UniqueName)
                End If
            End If

            ' Return URLs and target culture to their previous state.
            publishProperties.Item("PublishUrl").Value = originalPublishUrl
            publishProperties.Item("InstallUrl").Value = originalInstallUrl
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl
            publishProperties.Item("TargetCulture").Value = originalTargetCulture
            proj.Save()
        End Sub

        Private Function AppendStringToUrl(ByVal str As String, _
        ByVal baseUri As Uri) As String
            Dim returnValue As String = baseUri.OriginalString
            If baseUri.IsFile OrElse baseUri.IsUnc Then
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)
            Else
                If Not baseUri.ToString.EndsWith("/") Then
                    returnValue = baseUri.OriginalString & "/" & str
                Else
                    returnValue = baseUri.OriginalString & str
                End If
            End If
            Return returnValue
        End Function
    End Module
    ```

5. Makrolar IDE'lerini kapatın. Odak, yeniden Visual Studio.

### <a name="to-publish-a-project-for-a-specific-locale"></a>Belirli bir yerel seçim için proje yayımlamak için

1. Uygulama projesi Visual Basic Windows oluşturmak için Dosya  menüsünde Yeni 'nin üzerine **gelin** ve ardından Yeni'ye Project.

2. Yeni uygulama **Project** iletişim kutusunda, Windows **düğümünden** Uygulama'Visual Basic seçin.  Projeyi *PublishLocales olarak adlayın.*

3. Form1'e tıklayın. Özellikler **penceresinde,** **Tasarım'ın altında** Language özelliğini **(Varsayılan) İngilizce olarak** **değiştirin.**  Formun **Text** özelliğini **MyForm olarak değiştirme.**

     Yerelleştirilmiş kaynak URL'leri gerekli olana kadar oluşturulmaz. Örneğin, siz yeni yerel ayarlarını belirttikten sonra formun metnini veya denetimlerinden birini değiştirdikten sonra oluşturulurlar.

4. *PublishLocales'i* IDE'Visual Studio yayımlayın.

     Bu **Çözüm Gezgini** YayımlaYeniler'i *seçin.* Yeni **Project** Özellikler'i **seçin.** Project Tasarımcısı'nda Yayımla **sayfasında,** yayımlama konumunu belirtin ve **http://localhost/PublishLocales** ardından Şimdi Yayımla'ya **tıklayın.**

     Web'i yayımla sayfası görüntülendiğinde kapatın. (Bu adım için yalnızca projeyi yayımlamanız gerekir; bunu yüklemenize gerek yok.)

5. *PublishLocales'i,* Komut İstemi penceresinde makroyu Visual Studio yeniden yayımlayın. Komut İstemi penceresini görüntülemek  için Görünüm menüsünde Diğer Girişler'in üzerine Windows Komut **Penceresi'ne** tıklayın veya Ctrl Alt A  +  + **tuşlarına basın.** Komut İstemi penceresinde `macros` yazın; otomatik tamamlama kullanılabilir makroların listesini sağlar. Aşağıdaki makroyu seçin ve ENTER tuşuna basın:

     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`

6. Yayımlama işlemi başarılı olduğunda " *PublishLocales\PublishLocales.vbproj* için yayımlama başarılı oldu. Yayımlama dili "en" şeklindedir." İleti **kutusunda** Tamam'a tıklayın. Web'i yayımla sayfası görüntülendiğinde **Yükle'ye tıklayın.**

7. *C:\Inetpub\wwwroot\PublishLocales\en dizinine bakın.* Yerelleştirilmiş kaynak DLL'sine ek olarak bildirim, *setup.exe* ve Web sayfası yayımlama dosyası gibi yüklü dosyaları görüyorsanız. (Varsayılan ClickOnce EXEs ve DLL'lere *bir .deploy* uzantısı ekler; dağıtımdan sonra bu uzantıyı kaldırabilirsiniz.)

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Makrolar geliştirme ortamı](/previous-versions/visualstudio/visual-studio-2010/fb30sxt3(v=vs.100))
- [Makro Gezgini penceresi](/previous-versions/visualstudio/visual-studio-2010/wwkx67sw(v=vs.100))
- [Nasıl yapılanlar: Makroları düzenleme ve program aracılığıyla oluşturma](/previous-versions/visualstudio/visual-studio-2010/k91y6132(v=vs.100))