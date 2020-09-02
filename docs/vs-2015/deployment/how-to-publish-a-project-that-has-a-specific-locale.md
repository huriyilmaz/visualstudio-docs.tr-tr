---
title: 'Nasıl yapılır: belirli bir yerel ayara sahip bir proje yayımlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 42fc6e45e0e32e9b165251c7ec61d3d67b924e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697615"
---
# <a name="how-to-publish-a-project-that-has-a-specific-locale"></a>Nasıl yapılır: Özel Yerel Ayara Sahip Olan Bir Projeyi Yayımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir uygulamanın farklı yerel ayarlara sahip bileşenleri içermesi yaygın olmayan bir durumdur. Bu senaryoda, birden fazla proje içeren bir çözüm oluşturacak ve ardından her yerel ayar için ayrı projeler yayımlacaksınız. Bu yordamda, ' en ' yerel ayarını kullanarak bir çözümdeki ilk projeyi yayımlamak için bir makronun nasıl kullanılacağı gösterilmektedir. Bu yordamı ' en ' dışında bir yerel ayarda denemek istiyorsanız, `localeString` makroda, kullanmakta olduğunuz yerel ayara uyacak şekilde ayarlandığından emin olun (örneğin, ' de ' veya ' de-de ').  
  
> [!NOTE]
> Bu makroyu kullandığınızda, yayımlama konumu geçerli bir URL veya evrensel adlandırma kuralı (UNC) paylaşımıdır. Ayrıca, Internet Information Services (IIS) bilgisayarınıza yüklenmiş olmalıdır. IIS yüklemek için **Başlat** menüsünde, **Denetim Masası**' na tıklayın. **Program Ekle veya Kaldır**' a çift tıklayın. **Program Ekle/Kaldır**' da **Windows Bileşenlerini Ekle/Kaldır**' a tıklayın. **Windows bileşenleri sihirbazında**, **Bileşenler** listesinden **Internet Information Services (IIS)** onay kutusunu seçin. Sonra Sihirbazı kapatmak için **son** ' a tıklayın.  
  
### <a name="to-create-the-publishing-macro"></a>Yayımlama makrosunu oluşturmak için  
  
1. Makro Gezginini açmak için, **Araçlar** menüsünde **makrolar**' ın üzerine gelin ve **makro Gezgini**' ne tıklayın.  
  
2. Yeni bir makro modülü oluşturun. Makro Gezgini ' nde **MyMacros**' u seçin. **Araçlar** menüsünde, **makrolar**' ın üzerine gelin ve ardından **yeni makro modülü**' ne tıklayın. Modülün **PublishSpecificCulture**olarak adlandırın.  
  
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
  
5. Makrolar IDE 'yi kapatın. Odak Visual Studio 'ya döndürülür.  
  
### <a name="to-publish-a-project-for-a-specific-locale"></a>Bir projeyi belirli bir yerel ayar için yayımlamak için  
  
1. Visual Basic bir Windows uygulama projesi oluşturmak için, **Dosya** menüsünde **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.  
  
2. **Yeni proje** iletişim kutusunda, **Visual Basic** düğümünden **Windows uygulaması** ' nı seçin. Projeyi **Publishyerelleri**olarak adlandırın.  
  
3. Form1 ' e tıklayın. **Özellikler** penceresinde, **Tasarım**altında, **dil** özelliğini **(varsayılan)** iken **İngilizce**olarak değiştirin. Formun **Text** özelliğini **MyForm**olarak değiştirin.  
  
     Yerelleştirilmiş kaynak dll 'Lerinin gerekene kadar oluşturulmadığını unutmayın. Örneğin, yeni yerel ayarı belirtduktan sonra formun veya denetimlerinden birinin metnini değiştirdiğinizde oluşturulur.  
  
4. Visual Studio IDE 'yi kullanarak Publishyerelleri yayımlayın.  
  
     **Çözüm Gezgini**, publishyerelleri ' ni seçin. **Proje** menüsünde **Özellikler**' i seçin. Proje Tasarımcısı ' nda, **Yayımla** sayfasında, bir yayımlama konumu belirtin **http://localhost/PublishLocales** ve ardından **Şimdi Yayımla**' ya tıklayın.  
  
     Web 'i Yayımla sayfası göründüğünde kapatın. (Bu adım için yalnızca projeyi yayımlamanız gerekir; yüklemek zorunda değilsiniz.)  
  
5. Visual Studio komut Istemi penceresinde makroyu çağırarak Publishyerelleri yeniden yayımlayın. Komut Istemi penceresini görüntülemek için, **Görünüm** menüsünde **diğer pencereler** ' in üzerine gelin ve ardından **komut PENCERESI**' ne tıklayın veya Ctrl + Alt + A tuşlarına basın. Komut Istemi penceresinde, şunu yazın `macros` ; otomatik olarak Tamam kullanılabilir makroların bir listesini sağlar. Aşağıdaki makroyu seçin ve ENTER tuşuna basın:  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6. Yayımlama işlemi başarılı olduğunda, "Publishlocales\publishlocales.exe için başarılı Yayımla ' yı belirten bir ileti oluşturacaktır. Yayımlama dili ' en ' idi. " İleti kutusunda **Tamam** ' a tıklayın. Web 'i Yayımla sayfası göründüğünde, **yüklensin**' e tıklayın.  
  
7. C:\inetpub\wwwroot\publishlocales\enbölümüne bakın. Yerelleştirilmiş kaynak DLL 'inin yanı sıra bildirimler, setup.exe ve Web sayfası Yayımla dosyası gibi yüklü dosyaları görmeniz gerekir. (Varsayılan olarak ClickOnce, EXEs ve DLL 'lerde bir. deploy uzantısı ekler; dağıtımdan sonra bu uzantıyı kaldırabilirsiniz.)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Makrolar geliştirme ortamı](https://msdn.microsoft.com/d23105d8-34fe-4ad9-8278-fae2c660aeac)   
 [Makro Gezgini penceresi](https://msdn.microsoft.com/762169e6-f83f-44b4-bffa-d0f107cae9a3)   
 [Nasıl yapılır: makroları düzenleme ve program aracılığıyla oluşturma](https://msdn.microsoft.com/6716f820-1feb-48ad-a718-27eb6b473c5a)
