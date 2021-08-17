---
title: Görsel stillerin etkin olduğu bir WPF uygulaması yayımlama
description: Kullanıcı tarafından seçilen temaya göre denetimlerin görünümünün değişmesini sağlayan görsel stillerin etkinleştirildiğinde bir WPF uygulamasını yayımlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 73b22b02-fc75-42aa-82d3-51fdcaf8e5c8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: b231fc6635b5c974898ee2cc85ce8a4a64318039
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127902"
---
# <a name="how-to-publish-a-wpf-application-with-visual-styles-enabled"></a>Nasıl yapabilirsiniz: Görsel stiller etkinleştirilmiş bir WPF uygulaması yayımlama

Görsel stiller, kullanıcı tarafından seçilen temaya göre ortak denetimlerin görünümünün değişmesini sağlar. Varsayılan olarak, görsel stilleri Windows Presentation Foundation (WPF) uygulamaları için etkinleştirilmez, bu nedenle bunları el ile etkinleştirmeniz gerekir. Ancak, bir WPF uygulaması için görsel stilleri etkinleştirmek ve ardından çözümü yayımlamak hataya neden olur. Bu konuda, bu hatanın nasıl çözülecek ve görsel stiller etkinleştirilmiş bir WPF uygulaması yayımlama işlemi açıklanmıştır. Görsel stiller hakkında daha fazla bilgi için bkz. [Görsel stiller'e genel bakış.](/windows/desktop/Controls/visual-styles-overview) Hata iletisi hakkında daha fazla bilgi için [bkz. Dağıtımlarda belirli ClickOnce giderme.](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)

 Hatayı çözmek ve çözümü yayımlamak için aşağıdaki görevleri gerçekleştirmeniz gerekir:

- [Çözümü görsel stilleri etkinleştirilmeden yayımlayın.](#publish-the-solution-without-visual-styles-enabled)

- [Bir bildirim dosyası oluşturun.](#create-a-manifest-file)

- [Bildirim dosyasını yayımlanan çözümün yürütülebilir dosyasına ekleme.](#embed-the-manifest-file-into-the-executable-file-of-the-published-solution)

- [Uygulama ve dağıtım bildirimlerini imzalar.](#sign-the-application-and-deployment-manifests)

  Ardından, yayımlanan dosyaları son kullanıcıların uygulamayı yüklemelerini istediğiniz konuma taşıyabilirsiniz.

## <a name="publish-the-solution-without-visual-styles-enabled"></a>Çözümü görsel stilleri etkinleştirilmeden yayımlama

1. Projenizin görsel stillerinin etkinleştirilmemiş olduğundan emin olun. İlk olarak, aşağıdaki XML için projenizin bildirim dosyasını kontrol edin. Ardından, XML varsa, XML'i bir açıklama etiketiyle içine ekleyin.

     Varsayılan olarak, görsel stilleri etkin değildir.

    ```xml
    <dependency>
        <dependentAssembly>
            <assemblyIdentity type="win32" name="Microsoft.Windows.Common-Controls" version="6.0.0.0" processorArchitecture="*" publicKeyToken="6595b64144ccf1df" language="*" />
        </dependentAssembly>
    </dependency>
    ```

     Aşağıdaki yordamlar, projeniz ile ilişkili bildirim dosyasının nasıl aç olduğunu gösterir.

    **Bildirim dosyasını bir Visual Basic açmak için**

    1. Menü çubuğunda, Project **,** *ProjectName* **Özellikleri'ne tıklayın;** burada *ProjectName,* WPF projenizin adıdır.

         WPF projenizin özellik sayfaları görüntülenir.

    2. Uygulama sekmesinde **Görünüm'e** **tıklayın ve Windows Ayarlar.**

         app.manifest dosyası Kod **Düzenleyicisi'nde açılır.**

    **Bildirim dosyasını bir C# projesinde açmak için**

    1. Menü çubuğunda, Project **,** *ProjectName* **Özellikleri'ne tıklayın;** burada *ProjectName,* WPF projenizin adıdır.

         WPF projenizin özellik sayfaları görüntülenir.

    2. Uygulama **sekmesinde,** bildirim alanında görünen adı not ekleyin. Bu, projeniz ile ilişkili bildirimin adıdır.

        > [!NOTE]
        > Bildirim **alanında varsayılan ayarlarla bildirim** ekle veya Bildirim **olmadan** uygulama oluştur görünüyorsa, görsel stilleri etkinleştirilmez. Bildirim alanında bir bildirim dosyasının adı görünürse, bu yordamda bir sonraki adıma geçin.

    3. Bu **Çözüm Gezgini** Tüm Dosyaları **Göster'i seçin.**

         Bu düğme dışlananlar ve normalde gizlenenler de dahil olmak üzere tüm proje öğelerini gösterir. Bildirim dosyası bir proje öğesi olarak görünür.

2. Çözümlerinizi derleme ve yayımlama. Çözümü yayımlama hakkında daha fazla bilgi için bkz. [Yayımlama Sihirbazı'nı kullanarak ClickOnce uygulama yayımlama.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

## <a name="create-a-manifest-file"></a>Bildirim dosyası oluşturma

1. Aşağıdaki XML dosyasını bir Not Defteri yapıştırın.

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

2. Dosya Not Defteri'a **ve** ardından Farklı **Kaydet'e tıklayın.**

3. Farklı **Kaydet iletişim** kutusundaki Farklı Kaydet **türü açılan** listesinde Tüm Dosyalar'ı **seçin.**

4. Dosya **adı kutusunda,** dosyayı olarak ad girin ve dosya adının sonuna *.manifest* yazın. Örneğin: *themes.manifest*.

5. Klasörlere **Gözat düğmesini seçin,** herhangi bir klasörü seçin ve kaydet'e **tıklayın.**

    > [!NOTE]
    > Kalan yordamlar, bu dosyanın adının *themes.manifest* olduğunu ve dosyanın bilgisayarınızda *C:\temp* dizinine kayded olduğunu varsayır.

## <a name="embed-the-manifest-file-into-the-executable-file-of-the-published-solution"></a>Bildirim dosyasını yayımlanan çözümün yürütülebilir dosyasına ekleme

1. için **Geliştirici Komut İstemi'Visual Studio.**

    Geliştirici Komut İstemi için Geliştirici Komut İstemi hakkında daha fazla bilgi Visual Studio [bkz. Geliştirici Komut İstemi Geliştirici PowerShell.](../ide/reference/command-prompt-powershell.md)

   > [!NOTE]
   > Kalan adımlar çözümünüzle ilgili olarak aşağıdaki varsayımları yapın:
   >
   > - Çözümün adı **MyWPFProject'tir.**
   > - Çözüm şu dizinde bulunur: `%UserProfile%\Documents\Visual Studio 2010\Projects\` .
   >
   > - Çözüm şu dizinde yayımlanır: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish` .
   > - Yayımlanan uygulama dosyalarının en son sürümü aşağıdaki dizinde bulunur: `%UserProfile%\Documents\Visual Studio 2010\Projects\publish\Application Files\WPFApp_1_0_0_0`
   >
   > Yukarıda açıklanan adı veya dizin konumlarını kullanmak zorunda değildir. Yukarıda açıklanan ad ve konumlar yalnızca çözümlerinizi yayımlamak için gereken adımları göstermek için kullanılır.

2. Komut isteminde, yayımlanan uygulama dosyalarının en son sürümünü içeren dizin yolunu seçin. Aşağıdaki örnekte bu adım gösterildi.

   ```cmd
   cd "%UserProfile%\Documents\Visual Studio 2010\Projects\MyWPFProject\publish\Application Files\WPFApp_1_0_0_0"
   ```

3. Komut isteminde, bildirim dosyasını uygulamanın yürütülebilir dosyasına eklemek için aşağıdaki komutu çalıştırın.

   ```cmd
   mt -manifest c:\temp\themes.manifest -outputresource:MyWPFApp.exe.deploy
   ```

## <a name="sign-the-application-and-deployment-manifests"></a>Uygulama ve dağıtım bildirimlerini imzalama

1. Komut isteminde aşağıdaki komutu çalıştırarak geçerli dizinde yürütülebilir dosyadan *.deploy* uzantısını kaldırın.

   ```cmd
   ren MyWPFApp.exe.deploy MyWPFApp.exe
   ```

   > [!NOTE]
   > Bu örnekte yalnızca bir dosyanın .deploy dosya *uzantısına sahip olduğu* varsaydır. Bu dizinde .deploy dosya uzantısına sahip tüm dosyaları *yeniden adlandırırsanız emin* olun.

2. Komut isteminde, uygulama bildirimini imzalamak için aşağıdaki komutu çalıştırın.

   ```cmd
   mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Bu örnekte, projenin *.pfx* dosyasını kullanarak bildirimi imzalayabilirsiniz. Bildirimi imzalarsanız, bu örnekte kullanılan `-cf` parametresini atlarsanız. Bildirimi parola gerektiren bir sertifikayla imzalarsanız () `-password` seçeneğini `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` belirtin.

3. Komut isteminde aşağıdaki komutu çalıştırarak *.deploy* uzantısını bu yordamın önceki adımlarında yeniden adlandırdınız dosyanın adına ekleyin.

   ```
   ren MyWPFApp.exe MyWPFApp.exe.deploy
   ```

   > [!NOTE]
   > Bu örnekte, yalnızca bir dosyanın *.deploy* dosya uzantısı olduğu varsaydır. Daha önce .deploy dosya adı uzantısına sahip olan bu dizinde yer alan tüm *dosyaları yeniden adlandırırsanız* emin olun.

4. Komut isteminde, dağıtım bildirimini imzalamak için aşağıdaki komutu çalıştırın.

   ```
   mage -u ..\..\MyWPFApp.application -appm MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx
   ```

   > [!NOTE]
   > Bu örnekte, projenin *.pfx* dosyasını kullanarak bildirimi imzalayabilirsiniz. Bildirimi imzalarsanız, bu örnekte kullanılan `-cf` parametresini atlarsanız. Bildirimi parola gerektiren bir sertifikayla imzalarsanız, şu örnekte `-password` olduğu gibi seçeneğini belirtin: `For example: mage -u MyWPFApp.exe.manifest -cf ..\..\..\MyWPFApp_TemporaryKey.pfx - password Password` .

   Bu adımları gerçekleştirdikten sonra, yayımlanan dosyaları son kullanıcıların uygulamayı yüklemelerini istediğiniz konuma taşıyabilirsiniz. Çözümü sık sık güncelleştirmek için bu komutları bir betik içine taşımak ve her yeni sürüm yayımlasanız betiği çalıştırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce Dağıtımları İçinde Belirli Hataları Giderme](../deployment/troubleshooting-specific-errors-in-clickonce-deployments.md)
- [Görsel Stiller'e Genel Bakış](/windows/desktop/Controls/visual-styles-overview)
- [Görsel Stilleri Etkinleştirme](/windows/desktop/Controls/cookbook-overview)
- [Geliştirici Komut İstemi ve Geliştirici PowerShell](../ide/reference/command-prompt-powershell.md)
