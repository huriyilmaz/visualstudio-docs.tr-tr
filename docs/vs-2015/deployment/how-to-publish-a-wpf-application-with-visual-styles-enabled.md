---
title: 'Nasıl yapılır: görsel stiller etkinken WPF uygulaması yayımlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3691f782f317667b56f6bf3641c0f4c6a703eda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697568"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Nasıl yapılır: Görsel Stiller Etkinken WPF Uygulaması Yayımlama

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görsel stiller, Kullanıcı tarafından seçilen temaya göre değişiklik yapmak için ortak denetimlerin görünümünü sağlar. Varsayılan olarak, görsel stiller Windows Presentation Foundation (WPF) uygulamaları için etkin değildir, bu nedenle bunları el ile etkinleştirmeniz gerekir. Ancak, bir WPF uygulaması için görsel stilleri etkinleştirmek ve sonra çözümün yayımlanması bir hataya neden olur. Bu konuda, bu hatanın nasıl çözümleneceği ve görsel stillerle bir WPF uygulaması yayımlama işleminin nasıl giderileceği açıklanmaktadır. Görsel stiller hakkında daha fazla bilgi için bkz. [görsel stillere genel bakış](https://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e). Hata iletisi hakkında daha fazla bilgi için bkz. [ClickOnce dağıtımlarında belirli hataların sorunlarını giderme](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).

 Hatayı gidermek ve Çözümü yayımlamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:

- [Çözümü görsel stiller etkin olmadan yayımlayın](#BKMK_publishsolwovs).

- [Bir bildirim dosyası oluşturun](#BKMK_CreateManifest).

- [Bildirim dosyasını yayımlanan çözümün yürütülebilir dosyasına ekleyin](#BKMK_embedmanifest).

- [Uygulama ve dağıtım bildirimlerini imzalayın](#BKMK_signappdeplyman).

  Ardından, yayımlanan dosyaları son kullanıcıların uygulamayı yüklemesini istediğiniz konuma taşıyabilirsiniz.

## <a name="publish-the-solution-without-visual-styles-enabled"></a><a name="BKMK_publishsolwovs"></a> Çözümü görsel stiller etkin olmadan yayımlayın

1. Projenizde görsel stillerin etkin olmadığından emin olun. İlk olarak, aşağıdaki XML için projenizin bildirim dosyasını kontrol edin. Ardından, XML varsa, XML 'i bir açıklama etiketi ile birlikte iliştirin.

     Varsayılan olarak, görsel stiller etkin değildir.

    ```xml
    <dependency>
        <dependentAssembly>
          <assemblyIdentity
              type="win32"
              name="Microsoft.Windows.Common-Controls"
              version="6.0.0.0"
              processorArchitecture="*"
              publicKeyToken="6595b64144ccf1df"
              language="*" />
        </dependentAssembly>
      </dependency>
    ```

     Aşağıdaki yordamlarda, projenizle ilişkili bildirim dosyasının nasıl açılacağı gösterilmektedir.

    **Bildirim dosyasını Visual Basic bir projede açmak için**

    1. Menü çubuğunda, **Proje**, _ProjectName_**Özellikler**' i seçin, burada *ProjectName* WPF projenizin adıdır.

         WPF projeniz için özellik sayfaları görüntülenir.

    2. **Uygulama** sekmesinde, **Windows ayarlarını görüntüle**' yi seçin.

         App. manifest dosyası **kod düzenleyicisinde**açılır.

    **Bir C# projesinde bildirim dosyasını açmak için**

    1. Menü çubuğunda, **Proje**, _ProjectName_**Özellikler**' i seçin, burada *ProjectName* WPF projenizin adıdır.

         WPF projeniz için özellik sayfaları görüntülenir.

    2. **Uygulama** sekmesinde, bildirim alanında görüntülenen adı bir yere göz önünde yapın. Bu, projenizle ilişkili bildirimin adıdır.

        > [!NOTE]
        > Bildirimi **varsayılan ayarlarla katıştır** veya bildirim **olmadan uygulama oluşturursanız** , bildirim alanında görsel stiller etkinleştirilmez. Bildirim alanında bir bildirim dosyasının adı görünürse, bu yordamın bir sonraki adımına geçin.

    3. **Çözüm Gezgini**, **tüm dosyaları göster** () seçeneğini belirleyin.

         Bu düğme, hariç tutulan ve normalde gizlenen olanlar da dahil olmak üzere tüm proje öğelerini gösterir. Bildirim dosyası bir proje öğesi olarak görünür.

2. Çözümünüzü derleyin ve yayımlayın. Çözümü yayımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="create-a-manifest-file"></a><a name="BKMK_CreateManifest"></a> Bildirim dosyası oluşturma

1. Aşağıdaki XML 'i bir not defteri dosyasına yapıştırın.

     Bu XML, görsel stilleri destekleyen denetimleri içeren derlemeyi açıklar.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
     <asmv1:assembly manifestVersion="1.0"
         xmlns="urn:schemas-microsoft-com:asm.v1"
         xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
         xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
      <dependency>
        <dependentAssembly>
          <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="*"
            publicKeyToken="6595b64144ccf1df"
            language="*" />
        </dependentAssembly>
      </dependency>
    </asmv1:assembly>
    ```

2. Not defteri 'nde **Dosya**' ya ve ardından **farklı kaydet**' e tıklayın.

3. **Farklı kaydet** iletişim kutusunda, **farklı kaydet türü** aşağı açılan listesinde **tüm dosyalar**' ı seçin.

4. Dosya **adı** kutusunda dosyayı adlandırın ve dosya adının sonuna **. bildirimini** ekleyin. Örneğin: **Themes. manifest**.

5. **Klasörlere Gözatadır** düğmesini seçin, herhangi bir klasör seçin ve ardından **Kaydet**' e tıklayın.

    > [!NOTE]
    > Kalan yordamlar, bu dosyanın adının **Temalar. manifest** olduğunu ve dosyanın bilgisayarınızdaki C:\Temp dizinine kaydedildiğini varsayar.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a><a name="BKMK_embedmanifest"></a> Bildirim dosyasını yayımlanan çözümün yürütülebilir dosyasına ekleyin

1. **Visual Studio komut istemi**'ni açın.

    **Visual Studio komut istemini**açma hakkında daha fazla bilgi için bkz. [komut istemleri](https://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219).

   > [!NOTE]
   > Geri kalan adımlar çözümünüz hakkında aşağıdaki varsayımlar yapar:
   >
   > - Çözümün adı **MyWPFProject**' dir.
   > - Çözüm şu dizinde bulunur: `%UserProfile%\Documents\Visual Studio 2010\Projects\` .
   >
   > - Çözüm şu dizine yayımlandı: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` .
   > - Yayımlanan uygulama dosyalarının en son sürümü aşağıdaki dizinde bulunur: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Yukarıda açıklanan ad veya dizin konumlarını kullanmak zorunda değilsiniz. Yukarıda açıklanan ad ve konumlar yalnızca çözümünüzü yayımlamak için gereken adımları göstermek için kullanılır.

2. Komut isteminde, yayımlanan uygulama dosyalarının en son sürümünü içeren dizinin yolunu değiştirin. Aşağıdaki örnekte bu adım gösterilmektedir.

   ```
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. Komut isteminde, bildirim dosyasını uygulamanın yürütülebilir dosyasına eklemek için aşağıdaki komutu çalıştırın.

   ```
   mt –manifest c:\temp\themes.manifest –outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a><a name="BKMK_signappdeplyman"></a> Uygulama ve dağıtım bildirimlerini imzalama

1. Uzantıyı geçerli dizindeki yürütülebilir dosyadan kaldırmak için komut isteminde aşağıdaki komutu çalıştırın `.deploy` .

   ```
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > Bu örnek, yalnızca bir dosyanın `.deploy` dosya uzantısının olduğunu varsayar. Bu dizindeki dosya uzantısına sahip tüm dosyaları yeniden adlandırdığınızdan emin olun `.deploy` .

2. Komut isteminde, uygulama bildirimini imzalamak için aşağıdaki komutu çalıştırın.

   ```
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Bu örnek, projenin dosyasını kullanarak bildirimi imzalayabildiğinizi varsayar `.pfx` . Bildirimi imzalayamazsınız, `–cf` Bu örnekte kullanılan parametreyi atlayabilirsiniz. Bildirimi parola gerektiren bir sertifikayla imzaladıktan sonra `–password` () seçeneğini belirtin `For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password` .

3. `.deploy`Uzantıyı, bu yordamın önceki adımında yeniden adlandırmış olduğunuz dosyanın adına eklemek için komut isteminde aşağıdaki komutu çalıştırın.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > Bu örnekte, yalnızca bir dosyanın dosya uzantısının olduğunu varsaymaktadır `.deploy` . Bu dizindeki, daha önce dosya adı uzantısına sahip olan tüm dosyaları yeniden adlandırdığınızdan emin olun `.deploy` .

4. Komut isteminde, dağıtım bildirimini imzalamak için aşağıdaki komutu çalıştırın.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Bu örnek, projenin dosyasını kullanarak bildirimi imzalayabildiğinizi varsayar `.pfx` . Bildirimi imzalayamazsınız, `–cf` Bu örnekte kullanılan parametreyi atlayabilirsiniz. Bildirimi parola gerektiren bir sertifikayla imzaladıktan sonra, `–password` Bu örnekte olduğu gibi seçeneğini belirtin: `For example: mage –u MyWPFApp.exe.manifest –cf ..\..\..\MyWPFApp_TemporaryKey.pfx – password Password` .

   Bu adımları gerçekleştirdikten sonra, yayımlanan dosyaları son kullanıcıların uygulamayı yüklemesini istediğiniz konuma taşıyabilirsiniz. Çözümü sıklıkla güncelleştirmek istiyorsanız, bu komutları bir betiğe taşıyabilir ve yeni bir sürüm yayımladığınızda betiği çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca Bkz.

[ClickOnce dağıtımlarında](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md) 
 belirli hataların sorunlarını giderme [Görsel stillere genel bakış](https://msdn.microsoft.com/5b5d7bb6-684f-478d-bf5f-b8d18bbcff2e) 
 [Komut istemleri](https://msdn.microsoft.com/library/94fcf524-9045-4993-bfb2-e2d8bad44219)
