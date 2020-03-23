---
title: 'Öğretici: C# ve ASP.NET Core ile başlayın'
titleSuffix: ''
description: Visual Studio'da adım adım C#ile bir ASP.NET Core web uygulaması oluşturmayı öğrenin.
ms.custom: seodec18, get-started
ms.date: 05/29/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: ef41e28d994f27f66f616623d1b2c9798b65ede4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580053"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Öğretici: Visual Studio'da C# ve ASP.NET Core ile başlayın

Visual Studio'yu kullanarak ASP.NET Core ile C# geliştirme için yapılan bu eğitimde, bir C# ASP.NET Core web uygulaması oluşturacak, bu uygulamada değişiklik yapacak, IDE'nin bazı özelliklerini keşfedecek ve uygulamayı çalıştıracaksınız.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="install-visual-studio"></a>Visual Studio yükleme

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

### <a name="update-visual-studio"></a>Visual Studio’yu güncelleştirme

Visual Studio'yu zaten yüklediyseniz, en son sürümü çalıştırdığınızdan emin olun. Yüklemenizi nasıl güncelleştirin izleyin, [görsel stüdyoyu en son sürüm sayfasına](../../install/update-visual-studio.md) güncelleştir sayfasına bakın.

### <a name="choose-your-theme-optional"></a>Temanızı seçin (isteğe bağlı)

Bu öğretici, karanlık teonu kullanan ekran görüntülerini içerir. Karanlık temayı kullanmıyorsanız ancak kullanmak istiyorsanız, nasıl yapılacağını öğrenmek için [Visual Studio IDE ve Editor](../../ide/quickstart-personalize-the-ide.md) sayfasını Kişiselleştir sayfasına bakın.

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir ASP.NET Core projesi oluşturursunuz. Proje türü, daha bir şey eklemeden önce tamamen işlevsel bir web sitesi için ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.

3. Sol bölmedeki **Yeni Proje** iletişim kutusunda **Visual C#** seçeneğini genişletin, **Web'i**genişletin ve **ardından .NET Core'u**seçin. Orta bölmede, **Core Web Uygulaması ASP.NET**seçin. Ardından, Dosya *MyCoreApp* adını ve **Tamam**seçin.

   ![Visual Studio IDE'deki Yeni Proje iletişim kutusunda ASP.NET Çekirdek Web Uygulaması proje şablonu](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

**ASP.NET Çekirdek Web Uygulaması** proje şablonuna görmüyorsanız, ASP.NET ve web **geliştirme** iş yükünü ekleyerek bu şablonu alabilirsiniz. Bu iş yükünü, makinenize hangi Visual Studio 2017 güncelleştirmelerinin yüklendiğine bağlı olarak aşağıdaki iki şekilden birine ekleyebilirsiniz.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Seçenek 1: Yeni Proje iletişim kutusunu kullanma

1. **Yeni Proje** iletişim kutusunun sol bölmesinde Görsel **Stüdyo Yükleyici** aç bağlantısını seçin. (Ekran ayarlarınıza bağlı olarak, görüntülemek için kaydırmanız gerekebilir.)

   ![Yeni Proje iletişim kutusundan Görsel Stüdyo Yükleyici aç bağlantısını seçin](../media/open-visual-studio-installer-mycoreapp.png)

1. Visual Studio Installer başlattı. ASP.NET **ve web geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

   ![.NET Core platform ötesi geliştirme iş yükü Visual Studio Installer'da](../media/tutorial-aspnet-workload.png)

   (Yeni iş yükünü yüklemeye devam etmeden önce Visual Studio'yu kapatmanız gerekebilir.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Seçenek 2: Araçlar menü çubuğunu kullanma

1. **Yeni Proje** iletişim kutusunu iptal edin. Ardından, üst menü çubuğundan **Araçlar** > **Araçları ve Özellikleri Al'ı**seçin.

1. Visual Studio Installer başlattı. ASP.NET **ve web geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

   (Yeni iş yükünü yüklemeye devam etmeden önce Visual Studio'yu kapatmanız gerekebilir.)

### <a name="add-a-project-template"></a>Proje şablonu ekleme

1. Yeni **ASP.NET Çekirdek Web Uygulaması** iletişim kutusunda, **Web Uygulaması** proje şablonu seçin.

1. Core **2.1 ASP.NET** üst açılır menüde göründüğünü doğrulayın. Sonra, **Tamam'ı**seçin.

   ![Yeni ASP.NET Çekirdek Web Uygulaması iletişim kutusu](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Üst açılır menüden **Core 2.1 ASP.NET** göremiyorsanız, Visual Studio'nun en son sürümünde olduğunuzu unutmayın. Yüklemenizi nasıl güncelleştirin izleyin, [görsel stüdyoyu en son sürüm sayfasına](../../install/update-visual-studio.md) güncelleştir sayfasına bakın.

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   !['Yeni proje oluşturma' penceresini görüntüleme](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur** penceresinde, arama kutusuna *ASP.NET* girin veya yazın. Ardından, Dil listesinden **C#'yi** seçin ve ardından Platform listesinden **Windows'u** seçin.

   Dil ve platform filtrelerini uyguladıktan **sonra, ASP.NET Çekirdek Web Uygulaması** şablonunu seçin ve sonra **İleri'yi**seçin.

   ![ASP.NET Çekirdek Web Uygulaması için C# şablonunu seçin](./media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > **ASP.NET Çekirdek Web Uygulaması** şablonu görmüyorsanız, yeni bir **proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Aradığınızı bulamıyor' iletisinden 'Daha fazla araç ve özellik yükleyin' bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Installer'da **ASP.NET ve web geliştirme** iş yükünü seçin.
   >
   > ![.NET Core platform ötesi geliştirme iş yükü Visual Studio Installer'da](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Bundan sonra Visual Studio Installer'daki **Değiştir** düğmesini seçin. Çalışmanızı kaydetmeniz istenirse, bunu yapın. Ardından, iş yükünü yüklemeye **devam** et'i seçin. Daha sonra, bu "[Proje oluştur](#create-a-project)" yordamındaki 2.

1. Yeni **proje pencerenizi Yapılandır'da** **Proje adı** kutusuna *MyCoreApp* yazın veya girin. Ardından **Oluştur'u**seçin.

   !['Yeni projenizi yapılandır' penceresinde, projenize 'MyCoreApp' adını](./media/vs-2019/csharp-name-your-aspnet-mycoreapp-project.png)

1. Yeni **bir ASP.NET Core Web Uygulaması Oluşturma** penceresinde, ASP.NET Core **3.0'ın** üst açılır menüde göründüğünü doğrulayın. Ardından, örnek Razor Pages içeren **Web Uygulaması'nı**seçin. Sonra, **Oluştur'u**seçin.

   !['Yeni bir ASP.NET Çekirdek Web Uygulaması Oluşturma' penceresi](./media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio yeni projenizi açıyor.

::: moniker-end

### <a name="about-your-solution"></a>Çözümünüz hakkında

Bu **çözüm, Razor Page** tasarım modelini izler. [Model-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x) tasarım deseninden farklıdır ve model ve denetleyici kodunu Razor Page'in içine dahil etmek için düzene sokulabilir.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Çözümünüzü gezin

 1. Proje şablonu _MyCoreApp_adlı tek bir ASP.NET Core proje ile bir çözüm oluşturur. İçeriğini görüntülemek için **Çözüm Gezgini** sekmesini seçin.

    ![MyCoreApp adlı Razor Pages çözümü için Visual Studio ASP.NET Çözüm Explorer](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. **Sayfalar** klasörünü genişletin ve ardından *About.cshtml'i*genişletin.

     ![Visual Studio'daki Çözüm Gezgini'ndeki About.cshtml dosyası](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Kod düzenleyicisinde **About.cshtml** dosyasını görüntüleyin.

     ![Visual Studio kod düzenleyicisinde About.cshtml dosyasını görüntüleyin](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. **About.cshtml.cs** dosyasını seçin.

     ![Visual Studio kod düzenleyicisinde About.cshtml.cs dosyayı seçin](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Kod düzenleyicisinde **About.cshtml.cs** dosyasını görüntüleyin.

     ![Visual Studio kod düzenleyicisinde About.cshtml dosyasını görüntüleyin](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Proje, web sitenizin kökü olan bir **wwwroot** klasörü içerir. Klasörü içeriğini görüntülemek için genişletin.

     ![Visual Studio'daki Çözüm Gezgini'ndeki wwwroot klasörü](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    CSS, resimler&mdash;ve JavaScript kitaplıkları&mdash;gibi statik site içeriğini doğrudan istediğiniz yollara yerleştirebilirsiniz.

 1. Proje ayrıca, web uygulamasını çalışma zamanında yöneten yapılandırma dosyaları da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *appsettings.json*saklanır. Ancak, uygulama ayarlarını kullanarak bu ayarları geçersiz *kılabilirsiniz. Development.json*. Uygulama ayarlarını görüntülemek için **appsettings.json** dosyasını **genişletin. Development.json** dosyası.

     ![Visual Studio'daki Solution Explorer'daki yapılandırma dosyaları](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştır, hata ayıklama ve değişiklik yapma

1. Uygulamayı Hata Ayıklama modunda oluşturmak ve çalıştırmak için IDE'deki **IIS Express** düğmesini seçin. (Alternatif olarak, **F5**tuşuna basın veya menü çubuğundan **Hata Ayıklama** > **Başlat hata ayıklama'yı** seçin.)

     ![Visual Studio'da IIS Express düğmesini seçin](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **Web sunucusu 'IIS Express'e bağlanamadığını**söyleyen bir hata iletisi alırsanız, Visual Studio'yu kapatın ve sağ tıklatma veya bağlam menüsünden **yönetici olarak Çalıştır** seçeneğini kullanarak açın. Ardından, uygulamayı yeniden çalıştırın.
     >
     > Ayrıca, bir IIS SSL Express sertifikasını kabul etmek isteyip istemediğinizi soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için **Evet'i**seçin ve ardından bir izleme güvenlik uyarı iletisi alırsanız **Evet'i** seçin.

1. Visual Studio bir tarayıcı penceresi başlattı. Daha sonra menü çubuğunda **Ana Sayfa**, **Hakkında**ve **İletişim** sayfalarını görmeniz gerekir. (Bunu yapmazsanız, görüntülemek için "hamburger" menü öğesini seçin.)

    ![Web uygulamanızdaki menü çubuğundan "hamburger" menü öğesini seçin](media/csharp-aspnet-razor-browser-page.png)

1. Menü çubuğundan **Hakkında'yı** seçin.

   ![Uygulamanız için tarayıcı penceresinin menü çubuğunda Hakkında'yı seçin](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Diğer şeylerin yanı sıra, tarayıcıdaki **Hakkında** sayfası *About.cshtml* dosyasında ayarlanan metni işler.

   ![Hakkında sayfasındaki metni görüntüleme](media/csharp-aspnet-razor-browser-page-about.png)

1. Hata Ayıklama modunu durdurmak için Visual Studio'ya dönün ve **ardından Shift+F5** tuşuna basın. Bu da tarayıcı penceresinde proje kapatır.

1. Visual **Studio'da About.cshtml'i**seçin. Sonra, _ek_ kelime silin ve onun yerine, kelime _dosyası ve dizin_ekleyin.

    ![About.cshtml dosyasındaki metni değiştirme](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. **About.cshtml.cs**seçin. Ardından, aşağıdaki `using` kısayolu kullanarak dosyanın üst kısmındaki yönergeleri temizleyin:

   Gri renkten çıkmış `using` yönergeleri seçin ve Hızlı [Eylemler](../../ide/quick-actions.md) ampulü özentin hemen altında veya sol kenar boşluğunda görünür. Ampulü seçin ve gereksiz **kullanımı kaldır'ı**seçin.

   ![About.cshtml.cs dosyasındaki gereksiz Usings'i kaldırma](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio gereksiz `using` yönergeleri dosyadan siler.

1. Ardından, `OnGet()` yöntemde gövdeyi aşağıdaki kodla değiştirin:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
         Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. **Çevre** ve String altında iki dalgalı altı çizili nin göründüğüne dikkat **edin.** Bu türler kapsamiçinde olmadığından dalgalı alt çiziler görünür.

   ![OnGet yönteminde dalgalı altı çizilerle işaretlenmiş hatalar](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Burada listelenen hataları görmek için **Hata Listesi** araç çubuğunu açın. (Hata **Listesi** araç çubuğunu görmüyorsanız, üst menü çubuğundan**Hata Listesini** **Görüntüle'yi** > seçin.)

   ![Visual Studio'da Hata Listesi](media/csharp-aspnet-razor-error-list.png)

1. Bunu düzeltelim. Kod düzenleyicisinde imlecinizi hatayı içeren her iki satıra yerleştirin ve ardından sol kenar boşluğundaki Hızlı Eylemler ampulü seçin. Ardından, açılan menüden **Sistem'i kullanmayı seçin;** bu yönergeyi dosyanızın en üstüne ekleyin ve hataları çözün.

   !["Sistemi kullanma;" yönergesi ekleyin](media/csharp-aspnet-razor-add-usings.png)

1. Değişikliklerinizi kaydetmek için **Ctrl**+**S** tuşuna basın ve projenizi web tarayıcısında açmak için **F5** tuşuna basın.

1. Web sitesinin üst kısmında, değişikliklerinizi görüntülemek için **Hakkında'yı** seçin.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Hakkında sayfasını görüntüleyin](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Hata Ayıklama modunu durdurmak için web tarayıcısını kapatın, **Shift**+**F5** tuşuna basın ve ardından Visual Studio'yu kapatın.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>Çözümünüzü gezin

 1. Proje şablonu _MyCoreApp_adlı tek bir ASP.NET Core proje ile bir çözüm oluşturur. İçeriğini görüntülemek için **Çözüm Gezgini** sekmesini seçin.

    ![MyCoreApp adlı Razor Pages çözümü için Visual Studio ASP.NET Çözüm Explorer](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. **Sayfalar** klasörünü genişletin.

     ![Çözüm Gezgini'ndeki Sayfalar klasörü](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Kod düzenleyicisinde **Index.cshtml** dosyasını görüntüleyin.

     ![Visual Studio kod düzenleyicisinde Index.cshtml dosyasını görüntüleyin](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Her .cshtml dosyasının ilişkili bir kod dosyası vardır. Düzenleyicideki kod dosyasını açmak için Solution Explorer'daki **Index.cshtml** düğümini genişletin ve **Index.cshtml.cs** dosyasını seçin.

     ![Visual Studio kod düzenleyicisindeki Index.cshtml.cs dosyayı seçin](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Kod düzenleyicisindeki **Index.cshtml.cs** dosyasını görüntüleyin.

     ![Visual Studio kod düzenleyicisinde About.cshtml dosyasını görüntüleyin](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Proje, web sitenizin kökü olan bir **wwwroot** klasörü içerir. Klasörü içeriğini görüntülemek için genişletin.

     ![Visual Studio'daki Çözüm Gezgini'ndeki wwwroot klasörü](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    CSS, resimler&mdash;ve JavaScript kitaplıkları&mdash;gibi statik site içeriğini doğrudan istediğiniz yollara yerleştirebilirsiniz.

 1. Proje ayrıca, web uygulamasını çalışma zamanında yöneten yapılandırma dosyaları da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *appsettings.json*saklanır. Ancak, uygulama ayarlarını kullanarak bu ayarları geçersiz *kılabilirsiniz. Development.json*. Uygulama ayarlarını görüntülemek için **appsettings.json** dosyasını **genişletin. Development.json** dosyası.

     ![Visual Studio'daki Solution Explorer'daki yapılandırma dosyaları](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştır, hata ayıklama ve değişiklik yapma

1. Uygulamayı Hata Ayıklama modunda oluşturmak ve çalıştırmak için IDE'deki **IIS Express** düğmesini seçin. (Alternatif olarak, **F5**tuşuna basın veya menü çubuğundan **Hata Ayıklama** > **Başlat hata ayıklama'yı** seçin.)

     ![Visual Studio'da IIS Express düğmesini seçin](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **Web sunucusu 'IIS Express'e bağlanamadığını**söyleyen bir hata iletisi alırsanız, Visual Studio'yu kapatın ve sağ tıklatma veya bağlam menüsünden **yönetici olarak Çalıştır** seçeneğini kullanarak açın. Ardından, uygulamayı yeniden çalıştırın.
     >
     > Ayrıca, bir IIS SSL Express sertifikasını kabul etmek isteyip istemediğinizi soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için **Evet'i**seçin ve ardından bir izleme güvenlik uyarı iletisi alırsanız **Evet'i** seçin.

1. Visual Studio bir tarayıcı penceresi başlattı. Daha sonra menü çubuğunda **Ana Sayfa**ve **Gizlilik** sayfalarını görmelisiniz.

1. Menü çubuğundan **Gizlilik'i** seçin.

   Tarayıcıdaki **Gizlilik** sayfası *Privacy.cshtml* dosyasında ayarlanan metni işler.

   ![Metni Gizlilik sayfasında görüntüleme](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Hata Ayıklama modunu durdurmak için Visual Studio'ya dönün ve **ardından Shift+F5** tuşuna basın. Bu da tarayıcı penceresinde proje kapatır.

1. Visual Studio'da, düzenleme için **Privacy.cshtml'i** açın. Daha sonra, kelimeleri silin _Sitenizin gizlilik politikasını ayrıntılı olarak bu sayfayı kullanın_ ve onun yerine, _bu sayfa @ViewData["TimeStamp"] olarak yapım aşamasında olan_kelimeleri ekleyin.

    ![Privacy.cshtml dosyasındaki metni değiştirme](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Şimdi bir kod değişikliği yapalım. **Privacy.cshtml.cs**seçin. Ardından, aşağıdaki `using` kısayolu kullanarak dosyanın üst kısmındaki yönergeleri temizleyin:

   Gri renkten çıkmış `using` yönergeleri seçin ve Hızlı [Eylemler](../../ide/quick-actions.md) ampulü özentin hemen altında veya sol kenar boşluğunda görünür. Ampulü seçin ve gereksiz **kullanımı kaldır'ın**üzerine gezinin.

   ![Privacy.cshtml.cs dosyasındaki gereksiz Usings'i kaldırma](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Şimdi nelerin değişeceğini görmek için **Değişiklikleri Önizleme'yi** seçin.

   ![Değişiklikleri önizleme](media/vs-2019/csharp-aspnet-preview-changes.png)

   **Uygula**'yı seçin. Visual Studio gereksiz `using` yönergeleri dosyadan siler.

1. Ardından, `OnGet()` yöntemde gövdeyi aşağıdaki kodla değiştirin:

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. **DateTime'ın**altında iki dalgalı altı çizili nin göründüğüne dikkat edin. Dalgalı alt çizer, bu tür kapsam içinde olmadığından görünür.

   ![OnGet yönteminde dalgalı altı çizilerle işaretlenmiş hatalar](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Burada listelenen hataları görmek için **Hata Listesi** araç çubuğunu açın. (Hata **Listesi** araç çubuğunu görmüyorsanız, üst menü çubuğundan**Hata Listesini** **Görüntüle'yi** > seçin.)

   ![Visual Studio'da Hata Listesi](media/vs-2019/csharp-aspnet-error-list.png)

1. Bunu düzeltelim. Kod düzenleyicisinde imlecinizi hatayı içeren her iki satıra yerleştirin ve ardından sol kenar boşluğundaki Hızlı Eylemler ampulü seçin. Ardından, açılan menüden **Sistem'i kullanmayı seçin;** bu yönergeyi dosyanızın en üstüne ekleyin ve hataları çözün.

   !["Sistemi kullanma;" yönergesi ekleyin](media/vs-2019/csharp-aspnet-add-usings.png)

1. Projenizi web tarayıcısında açmak için **F5** tuşuna basın.

1. Web sitesinin üst kısmında, değişikliklerinizi görüntülemek için **Gizlilik'i** seçin.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Gizlilik sayfasını görüntüleyin](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Hata Ayıklama modunu durdurmak için web tarayıcısını kapatın, **Shift**+**F5** tuşuna basın ve ardından Visual Studio'yu kapatın.
::: moniker-end

## <a name="quick-answers-faq"></a>Hızlı yanıtlar SSS

Aşağıda, bazı temel kavramları vurgulamak için hızlı bir SSS'dir.

### <a name="what-is-c"></a>C# nedir?

[C#,](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) hem sağlam hem de öğrenmesi kolay olacak şekilde tasarlanmış tür güvenli ve nesne yönelimli bir programlama dilidir.

### <a name="what-is-aspnet-core"></a>ASP.NET Core nedir?

ASP.NET Core, web uygulamaları ve hizmetleri gibi internete bağlı uygulamalar oluşturmak için açık kaynak kodlu ve çapraz platform çerçevesidir. ASP.NET Core uygulamaları .NET Core veya .NET Framework üzerinde çalıştırılabilir. Windows, Mac ve Linux'ta ASP.NET Core uygulamalarınızı geliştirebilir ve çalıştırabilirsiniz. ASP.NET Core [GitHub](https://github.com/aspnet/home)açık kaynak.

### <a name="what-is-visual-studio"></a>Visual Studio nedir?

Visual Studio, geliştiriciler için entegre bir verimlilik araçları geliştirme paketidir. Bunu programlar ve uygulamalar oluşturmak için kullanabileceğiniz bir program olarak düşünün.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğretici tamamladıktan sonra tebrikler! C#, ASP.NET Core ve Visual Studio IDE hakkında biraz bilgi edindiğinizi umuyoruz. C# ve ASP.NET içeren bir web uygulaması veya web sitesi oluşturma hakkında daha fazla bilgi edinmek için aşağıdaki eğitimlerle devam edin:

> [!div class="nextstepaction"]
> [ASP.NET Core ile Jilet Sayfaları web uygulaması oluşturun](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio'u kullanarak web uygulamanızı Azure Uygulama Hizmeti'nde yayımlayın](../../deployment/quickstart-deploy-to-azure.md)
