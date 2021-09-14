---
title: Belirli bir yerel ayara sahip bir proje yayımlama
description: Birden çok farklı yerel ayar için projeler içeren bir çözümde ilk projeyi yayımlamak için bir makro kullanmayı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725879"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Nasıl yapılır: belirli bir yerel ayara sahip bir projeyi yayımlama
Bir uygulamanın farklı yerel ayarlara sahip bileşenleri içermesi yaygın olmayan bir durumdur. Bu senaryoda, birden fazla proje içeren bir çözüm oluşturacak ve ardından her yerel ayar için ayrı projeler yayımlacaksınız. Bu yordamda, ' en ' yerel ayarını kullanarak bir çözümdeki ilk projeyi yayımlamak için bir makronun nasıl kullanılacağı gösterilmektedir. Bu yordamı ' en ' dışında bir yerel ayarda denemek istiyorsanız, `localeString` makroda, kullanmakta olduğunuz yerel ayara uyacak şekilde ayarlandığından emin olun (örneğin, ' de ' veya ' de-de ').

> [!NOTE]
> Bu makroyu kullandığınızda, yayımlama konumu geçerli bir URL veya evrensel adlandırma kuralı (UNC) paylaşımıdır. ayrıca, Internet Information Services (ııs) bilgisayarınıza yüklenmiş olmalıdır. IIS yüklemek için **Başlat** menüsünde, **Denetim Masası**' na tıklayın. **Program Ekle veya Kaldır**' a çift tıklayın. **program ekle/kaldır**' da **Windows bileşenleri ekle/kaldır**' a tıklayın. **Windows bileşenleri sihirbazında**, **bileşenler** listesinden **Internet Information Services (ııs)** onay kutusunu seçin. Sonra Sihirbazı kapatmak için **son** ' a tıklayın.

### <a name="to-create-the-publishing-macro"></a>Yayımlama makrosunu oluşturmak için

1. Makro Gezginini açmak için, **Araçlar** menüsünde **makrolar**' ın üzerine gelin ve **makro Gezgini**' ne tıklayın.

2. Yeni bir makro modülü oluşturun. Makro Gezgini ' nde **MyMacros**' u seçin. **Araçlar** menüsünde, **makrolar**' ın üzerine gelin ve ardından **yeni makro modülü**' ne tıklayın. Modülün **PublishSpecificCulture** olarak adlandırın.

3. Makro Gezgini ' nde **MyMacros** düğümünü genişletin ve ardından çift tıklayarak **PublishAllProjects** modülünü açın (ya da **Araçlar** menüsünden **MAKROLAR**' ın üzerine gelin ve **Makrolar IDE**' ye tıklayın).

4. Makrolar IDE ' de, aşağıdaki kodu deyimden sonra modüle ekleyin `Import` :

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

5. Makrolar IDE 'yi kapatın. Odak Visual Studio döndürülecek.

### <a name="to-publish-a-project-for-a-specific-locale"></a>Bir projeyi belirli bir yerel ayar için yayımlamak için

1. bir Visual Basic Windows uygulama projesi oluşturmak için, **dosya** menüsünde, **yeni**' nin üzerine gelin ve **Project**' ye tıklayın.

2. **yeni Project** iletişim kutusunda **Visual Basic** düğümünden **Windows uygulama** ' yı seçin. Projeyi *Publishyerelleri* olarak adlandırın.

3. Form1 ' e tıklayın. **Özellikler** penceresinde, **Tasarım** altında, **dil** özelliğini **(varsayılan)** iken **İngilizce** olarak değiştirin. Formun **Text** özelliğini **MyForm** olarak değiştirin.

     Yerelleştirilmiş kaynak dll 'Lerinin gerekene kadar oluşturulmadığını unutmayın. Örneğin, yeni yerel ayarı belirtduktan sonra formun veya denetimlerinden birinin metnini değiştirdiğinizde oluşturulur.

4. Visual Studio ıde 'yi kullanarak *publishyerelleri* yayımlayın.

     **Çözüm Gezgini**, *publishyerelleri*' ni seçin. **Project** menüsünde **özellikler**' i seçin. Project tasarımcısında **yayımla** sayfasında, bir yayımlama konumu belirtin **http://localhost/PublishLocales** ve ardından **şimdi yayımla**' ya tıklayın.

     Web 'i Yayımla sayfası göründüğünde kapatın. (Bu adım için yalnızca projeyi yayımlamanız gerekir; yüklemek zorunda değilsiniz.)

5. Visual Studio komut istemi penceresinde makroyu çağırarak *publishyerelleri* yeniden yayımlayın. komut istemi penceresini görüntülemek için, **görünüm** menüsünde **diğer Windows** ' ın üzerine gelin ve ardından **komut penceresi**' ne tıklayın veya **Ctrl** + **Alt** + **A**' ya basın. Komut Istemi penceresinde, şunu yazın `macros` ; otomatik olarak Tamam kullanılabilir makroların bir listesini sağlar. Aşağıdaki makroyu seçin ve ENTER tuşuna basın:

     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`

6. Yayımlama işlemi başarılı olduğunda, " *Publishlocales\publishlocales.exe* Için başarılı Yayımla ' yı bildiren bir ileti oluşturacaktır. Yayımlama dili ' en ' idi. " İleti kutusunda **Tamam** ' a tıklayın. Web 'i Yayımla sayfası göründüğünde, **yüklensin**' e tıklayın.

7. *C:\inetpub\wwwroot\publishlocales\en* bölümüne bakın. Yerelleştirilmiş kaynak DLL 'inin yanı sıra bildirimler, *setup.exe* ve Web sayfası Yayımla dosyası gibi yüklü dosyaları görmeniz gerekir. (varsayılan olarak ClickOnce, exes ve dll 'lerde bir *. deploy* uzantısı ekler; dağıtımdan sonra bu uzantıyı kaldırabilirsiniz.)

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Makrolar geliştirme ortamı](/previous-versions/visualstudio/visual-studio-2010/fb30sxt3(v=vs.100))
- [Makro Gezgini penceresi](/previous-versions/visualstudio/visual-studio-2010/wwkx67sw(v=vs.100))
- [Nasıl yapılır: makroları düzenleme ve program aracılığıyla oluşturma](/previous-versions/visualstudio/visual-studio-2010/k91y6132(v=vs.100))