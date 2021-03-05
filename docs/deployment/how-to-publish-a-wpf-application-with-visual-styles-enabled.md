---
title: Görsel stiller etkinken WPF uygulaması yayımlama
description: Görsel stiller etkinken WPF uygulaması yayımlamayı öğrenin ve bu sayede denetimlerin görünümünün Kullanıcı tarafından seçilen temaya göre değiştirilmesine izin verir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 285d624debed6dc498e3d274af2839137b5094d1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102171285"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Nasıl yapılır: görsel stiller etkinken WPF uygulaması yayımlama

Görsel stiller, Kullanıcı tarafından seçilen temaya göre değişiklik yapmak için ortak denetimlerin görünümünü sağlar. Varsayılan olarak, görsel stiller Windows Presentation Foundation (WPF) uygulamaları için etkin değildir, bu nedenle bunları el ile etkinleştirmeniz gerekir. Ancak, bir WPF uygulaması için görsel stilleri etkinleştirmek ve sonra çözümün yayımlanması bir hataya neden olur. Bu konuda, bu hatanın nasıl çözümleneceği ve görsel stillerle bir WPF uygulaması yayımlama işleminin nasıl giderileceği açıklanmaktadır. Görsel stiller hakkında daha fazla bilgi için bkz. [görsel stillere genel bakış](/windows/desktop/Controls/visual-styles-overview). Hata iletisi hakkında daha fazla bilgi için bkz. [ClickOnce dağıtımlarında belirli hataların sorunlarını giderme](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md).

 Hatayı gidermek ve Çözümü yayımlamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:

- [Çözümü görsel stiller etkin olmadan yayımlayın](#publish-the-solution-without-visual-styles-enabled).

- [Bir bildirim dosyası oluşturun](#create-a-manifest-file).

- [Bildirim dosyasını yayımlanan çözümün yürütülebilir dosyasına ekleyin](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution).

- [Uygulama ve dağıtım bildirimlerini imzalayın](#sign-the-application-and-deployment-manifests).

  Ardından, yayımlanan dosyaları son kullanıcıların uygulamayı yüklemesini istediğiniz konuma taşıyabilirsiniz.

## <a name="publish-the-solution-without-visual-styles-enabled"></a>Çözümü görsel stiller etkin olmadan yayımlayın

1. Projenizde görsel stillerin etkin olmadığından emin olun. İlk olarak, aşağıdaki XML için projenizin bildirim dosyasını kontrol edin. Ardından, XML varsa, XML 'i bir açıklama etiketi ile birlikte iliştirin.

     Varsayılan olarak, görsel stiller etkin değildir.

    ```xml
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```

     Aşağıdaki yordamlarda, projenizle ilişkili bildirim dosyasının nasıl açılacağı gösterilmektedir.

    **Bildirim dosyasını Visual Basic bir projede açmak için**

    1. Menü çubuğunda, **Proje**, *ProjectName* **Özellikler**' i seçin, burada *ProjectName* WPF projenizin adıdır.

         WPF projeniz için özellik sayfaları görüntülenir.

    2. **Uygulama** sekmesinde, **Windows ayarlarını görüntüle**' yi seçin.

         App. manifest dosyası **kod düzenleyicisinde** açılır.

    **Bir C# projesinde bildirim dosyasını açmak için**

    1. Menü çubuğunda, **Proje**, *ProjectName* **Özellikler**' i seçin, burada *ProjectName* WPF projenizin adıdır.

         WPF projeniz için özellik sayfaları görüntülenir.

    2. **Uygulama** sekmesinde, bildirim alanında görüntülenen adı bir yere göz önünde yapın. Bu, projenizle ilişkili bildirimin adıdır.

        > [!NOTE]
        > Bildirimi **varsayılan ayarlarla katıştır** veya bildirim **olmadan uygulama oluşturursanız** , bildirim alanında görsel stiller etkinleştirilmez. Bildirim alanında bir bildirim dosyasının adı görünürse, bu yordamın bir sonraki adımına geçin.

    3. **Çözüm Gezgini**, **tüm dosyaları göster**' i seçin.

         Bu düğme, hariç tutulan ve normalde gizlenen olanlar da dahil olmak üzere tüm proje öğelerini gösterir. Bildirim dosyası bir proje öğesi olarak görünür.

2. Çözümünüzü derleyin ve yayımlayın. Çözümü yayımlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

## <a name="create-a-manifest-file"></a>Bildirim dosyası oluşturma

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
                <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
            </dependentAssembly>
        </dependency>
    </asmv1:assembly>
    ```

2. Not defteri 'nde **Dosya**' ya ve ardından **farklı kaydet**' e tıklayın.

3. **Farklı kaydet** iletişim kutusunda, **farklı kaydet türü** aşağı açılan listesinde **tüm dosyalar**' ı seçin.

4. Dosya **adı** kutusunda dosyayı adlandırın ve dosya adının sonuna *. bildirimini* ekleyin. Örneğin: *Themes. manifest*.

5. **Klasörlere Gözatadır** düğmesini seçin, herhangi bir klasör seçin ve ardından **Kaydet**' e tıklayın.

    > [!NOTE]
    > Kalan yordamlar, bu dosyanın adının *Temalar. manifest* olduğunu ve dosyanın bilgisayarınızdaki *C:\Temp* dizinine kaydedildiğini varsayar.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>Bildirim dosyasını yayımlanan çözümün yürütülebilir dosyasına ekleyin

1. **Visual Studio için geliştirici komut istemi** açın.

    Visual Studio Geliştirici Komut İstemi nasıl açılacağı hakkında daha fazla bilgi için, bkz. [Geliştirici komut istemi ve geliştirici PowerShell](../ide/reference/command-prompt-powershell.md).

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

   ```cmd
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. Komut isteminde, bildirim dosyasını uygulamanın yürütülebilir dosyasına eklemek için aşağıdaki komutu çalıştırın.

   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini imzalama

1. Komut isteminde, geçerli dizindeki yürütülebilir dosyadan *. deploy* uzantısını kaldırmak için aşağıdaki komutu çalıştırın.

   ```cmd
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > Bu örnek, yalnızca bir dosyanın *. deploy* dosya uzantısına sahip olduğunu varsayar. Bu dizindeki *. deploy* dosya uzantısına sahip tüm dosyaları yeniden adlandırdığınızdan emin olun.

2. Komut isteminde, uygulama bildirimini imzalamak için aşağıdaki komutu çalıştırın.

   ```cmd
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Bu örnek, projenin *. pfx* dosyasını kullanarak bildirimi imzalayabildiğinizi varsayar. Bildirimi imzalayamazsınız, `-cf` Bu örnekte kullanılan parametreyi atlayabilirsiniz. Bildirimi parola gerektiren bir sertifikayla imzaladıktan sonra `-password` () seçeneğini belirtin `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` .

3. Komut isteminde, bu yordamın önceki adımında yeniden adlandırdığınız dosyanın adına *. deploy* uzantısını eklemek için aşağıdaki komutu çalıştırın.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > Bu örnek, yalnızca bir dosyanın *. deploy* dosya uzantısına sahip olduğunu varsayar. Bu dizindeki, daha önce *. deploy* dosya adı uzantısına sahip olan tüm dosyaları yeniden adlandırdığınızdan emin olun.

4. Komut isteminde, dağıtım bildirimini imzalamak için aşağıdaki komutu çalıştırın.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Bu örnek, projenin *. pfx* dosyasını kullanarak bildirimi imzalayabildiğinizi varsayar. Bildirimi imzalayamazsınız, `-cf` Bu örnekte kullanılan parametreyi atlayabilirsiniz. Bildirimi parola gerektiren bir sertifikayla imzaladıktan sonra, `-password` Bu örnekte olduğu gibi seçeneğini belirtin: `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` .

   Bu adımları gerçekleştirdikten sonra, yayımlanan dosyaları son kullanıcıların uygulamayı yüklemesini istediğiniz konuma taşıyabilirsiniz. Çözümü sıklıkla güncelleştirmek istiyorsanız, bu komutları bir betiğe taşıyabilir ve yeni bir sürüm yayımladığınızda betiği çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce Dağıtımları İçinde Belirli Hataları Giderme](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [Görsel stillere genel bakış](/windows/desktop/Controls/visual-styles-overview)
- [Görsel stilleri etkinleştirme](/windows/desktop/Controls/cookbook-overview)
- [Geliştirici Komut İstemi ve geliştirici PowerShell](../ide/reference/command-prompt-powershell.md)
