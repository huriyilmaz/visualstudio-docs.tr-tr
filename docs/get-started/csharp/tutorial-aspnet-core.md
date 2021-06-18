---
title: 'Öğretici: Kullanmaya başlayın Core ve C# ASP.NET kullanma'
titleSuffix: ''
description: C# ile ASP.NET adım Visual Studio Core web uygulaması oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: seodec18, get-started
ms.date: 02/12/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 58f9604cbecdbe6414e91079a9e0e4691a32b768
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308551"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Öğretici: Kullanmaya başlayın C# ve ASP.NET Core ile Visual Studio

Visual Studio kullanarak ASP.NET Core ile C# geliştirme öğreticisinde bir C# ASP.NET Core web uygulaması oluşturacak, üzerinde değişiklikler yapacak, IDE'nin bazı özelliklerini keşfeder ve ardından uygulamayı çalıştırabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio henüz yüklememişsinizdir, ücretsiz olarak yüklemek için [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidin.

::: moniker-end

### <a name="update-visual-studio"></a>Visual Studio’yu güncelleştirme

Daha önce bir Visual Studio, en son sürümü çalıştırmış olduğundan emin olun. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için Güncelleştirme Visual Studio [en son sürüm sayfasına](../../install/update-visual-studio.md) bakın.

### <a name="choose-your-theme-optional"></a>Temanızı seçin (isteğe bağlı)

Bu öğreticide koyu temayı kullanan ekran görüntüleri yer almaktadır. Koyu temayı kullanıyorsanız ancak bunu yapmak için [IDE](../../ide/quickstart-personalize-the-ide.md) ve Düzenleyici Visual Studio kişiselleştirme sayfasına bakın.

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir ASP.NET Core projesi oluştur. Proje türü, herhangi bir şey eklemeden önce tam işlevsel bir web sitesi için ihtiyacınız olacak tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **Proje'yi** >  > **seçin.**

3. Sol **bölmede Yeni** Proje iletişim kutusunda **Visual C#** öğesini genişletin, **Web'i genişletin** ve ardından **.NET Core'ı seçin.** Orta bölmede, Temel **Web ASP.NET'ni seçin.** Ardından, dosyayı *MyCoreApp olarak adlandırarak* Tamam'ı **seçin.**

   ![ASP.NET IDE'de Yeni Proje iletişim kutusundaki Temel Web Uygulaması proje Visual Studio şablonu](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

**ASP.NET Core Web Uygulaması** proje şablonunu görmüyorsanız, web geliştirme iş yükünü ve ASP.NET ekleyerek **edinebilirsiniz.** Makinenize 2017 güncelleştirmelerinin hangi Visual Studio bağlı olarak bu iş yükünü aşağıdaki yöntemlerden birini kullanabilirsiniz.

#### <a name="option-1-use-the-new-project-dialog-box"></a>1. Seçenek: Yeni Proje iletişim kutusunu kullan

1. Yeni **Proje iletişim Visual Studio Yükleyicisi** bölmesindeKimlik penceresini **aç** bağlantısını seçin. (Görüntü ayarlarınıza bağlı olarak, bunu görmek için kaydırmanız gerekebilir.)

   ![Yeni Proje Visual Studio Yükleyicisi Aç bağlantısını seçin](../media/open-visual-studio-installer-mycoreapp.png)

1. Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü seçin ve** ardından Değiştir'i **seçin.**

   ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../media/tutorial-aspnet-workload.png)

   (Yeni iş yükünü yüklemeye Visual Studio önce bu uygulamayı kapatmanız gerekir.)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. Seçenek: Araçlar menü çubuğunu kullanma

1. Yeni Proje iletişim **kutusundan iptal** edin. Ardından üst menü çubuğundan Araçlar Araçları ve **Özellikleri**  >  **Al'ı seçin.**

1. Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü seçin ve** ardından Değiştir'i **seçin.**

   (Yeni iş yükünü yüklemeye Visual Studio önce bu uygulamayı kapatmanız gerekir.)

### <a name="add-a-project-template"></a>Proje şablonu ekleme

1. Yeni **ASP.NET Çekirdek Web Uygulaması** iletişim kutusunda Web Uygulaması **proje** şablonunu seçin.

1. ASP.NET **Core 2.1'in** üst açılan menüde görüntülendiğinden emin olmak. Ardından **Tamam'ı seçin.**

   ![Yeni ASP.NET Core Web Uygulaması iletişim kutusu](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Üst açılan menüde **ASP.NET Core 2.1'i** görmüyorsanız, en son Visual Studio. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için Güncelleştirme Visual Studio [en son sürüm sayfasına](../../install/update-visual-studio.md) bakın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="../../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="'Yeni proje oluştur' penceresini görüntüleme":::

1. Yeni **proje oluştur penceresinde Dil** **listesinden C#** dilini seçin. Ardından Platform **listesinden Windows'u** ve proje türleri **listesinden Web'i** seçin.

      Dil, platform ve proje türü filtrelerini uyguladikten sonra, **ASP.NET Core Web Uygulaması** şablonunu ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="./media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="ASP.NET Core Web Uygulaması için C# şablonunu seçin":::

   > [!NOTE]
   > **ASP.NET Core Web Uygulaması** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Daha sonra, Visual Studio Yükleyicisi web geliştirme **ASP.NET iş yükünü** seçin.
   >
   > ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istenirse bunu yapma. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** Proje adı kutusuna *MyCoreApp* **yazın veya** girin. Ardından, **Sonraki'yi seçin.**

   :::image type="content" source="./media/vs-2019/csharp-name-your-aspnet-app.png" alt-text="'Yeni projenizi yapılandırma' penceresinde projenize 'MyCoreApp' adını girin":::

1. Ek **bilgiler penceresinde** üst açılan **menüde .NET Core 3.1'in** görüntülendiğinden emin olur. Kutuyu işaret ederek Docker desteğini etkinleştirmeyi seçebilirsiniz. Kimlik doğrulamasını değiştir düğmesine tıklayarak da kimlik doğrulaması desteği ebilirsiniz. Buradan şunları seçebilirsiniz:
    - Hiçbiri: Kimlik doğrulaması yok.
    - Bireysel hesaplar: Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: Bu seçenek kimlik doğrulaması için Active Directory, Azure AD Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygundur.
    
    **Docker'ı Etkinleştir kutusunun** işaretini kaldırın ve Kimlik Doğrulama Türü **için Hiçbiri'ne** tıklayın. Ardından **Oluştur**’u seçin.

   :::image type="content" source="./media/vs-2019/aspnet-core-additional-information.png" alt-text="'Ek bilgiler' penceresinde .NET Core 3.1'in seçili olduğundan emin olun ve tüm varsayılan değerleri bırakın":::

   Visual Studio projenizi açar.

::: moniker-end

### <a name="about-your-solution"></a>Çözümünüz hakkında

Bu çözüm, **Razor Sayfası tasarım desenini** izler. [Model-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x&preserve-view=true) tasarım modelinden farklıdır ve razor sayfasının içinde model ve denetleyici kodunun dahil basitleştirilmiştir.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Çözümde tura çıkıyor

 1. Proje şablonu, _MyCoreApp_ adlı tek bir ASP.NET Core projesiyle bir çözüm oluşturur. İçeriğini **Çözüm Gezgini** için sekmeyi seçin.

    ![ASP.NET Çözüm Gezgini MyCoreApp Visual Studio Razor Pages çözüm için Razor Pages'de](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Sayfalar **klasörünü ve** ardından *About.cshtml dosyasını genişletin.*

     ![Visual Studio'de yer alan Çözüm Gezgini.cshtml Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Kod **düzenleyicisinde About.cshtml** dosyasını görüntüleme.

     ![Visual Studio kod düzenleyicisinde About.cshtml dosyasının ilk on satırı gösteren ekran görüntüsü.](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. **About.cshtml.cs dosyasını** seçin.

     ![Kod düzenleyicisinde About.cshtml.cs Visual Studio seçin](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Kod **düzenleyicisinde About.cshtml.cs** dosyasını görüntüleme.

     ![Visual Studio kod düzenleyicisinde About.cshtml.cs dosyasının ilk 18 Visual Studio ekran görüntüsü. ](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Proje, web sitenizin kökü olan bir **wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     ![Visual Studio'de Çözüm Gezgini wwwroot klasörü](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini doğrudan &mdash; &mdash; istediğiniz yollara koyabilirsiniz.

 1. Proje ayrıca çalışma zamanında web uygulamasını yöneten yapılandırma dosyalarını içerir. Varsayılan uygulama [yapılandırması,](/aspnet/core/fundamentals/configuration) üzerindeappsettings.js *depolanır.* Ancak, üzerinde bir uygulama kullanarak buappsettings.Development.js *geçersiz kılabilirsiniz.* Dosyanın **appsettings.jsdosyasını** görüntülemek için **appsettings.Development.jsgenişletin.**

     ![Çözüm Gezgini Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. Uygulamayı **IIS Express** modunda derlemek ve çalıştırmak için IDE'de IIS Express düğmesini seçin. (Alternatif olarak **F5 tuşuna basın** veya Hata Ayıkla'ya **basın**  >  **Menü çubuğundan** Hata Ayıklamayı Başlat.)

     ![Dosyada IIS Express düğmesini Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **'IIS Express' web** sunucusuna bağlanamıyor hata iletisi alırsanız, Visual Studio'ı kapatın ve ardından sağ  tıklama veya bağlam menüsünden Yönetici olarak çalıştır seçeneğini kullanarak açın. Ardından uygulamayı yeniden çalıştırın.
     >
     > Iis SSL Express sertifikasını kabul etmek istiyor sanız soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için Evet'i seçin ve ardından bir **güvenlik** uyarısı iletisi alırsanız Evet'i seçin.

1. Visual Studio tarayıcı penceresi açar. Ardından menü çubuğunda **Giriş**, **Hakkında** ve **Kişi** sayfalarını görüyorsanız. (Bunu yapmak zorunda değilsanız görüntülemek için "hamburger" menü öğesini seçin.)

    ![Web uygulamanıza gelen menü çubuğundan "hamburger" menü öğesini seçin](media/csharp-aspnet-razor-browser-page.png)

1. Menü **çubuğundan** Hakkında'ya tıklayın.

   ![Uygulamanıza uygun tarayıcı penceresinin menü çubuğunda Hakkında'ya tıklayın](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Diğer şeylerin arasında, **tarayıcının** Hakkında sayfası *About.cshtml* dosyasında ayarlanmış metni işler.

   ![Hakkında sayfasındaki metni görüntüleme](media/csharp-aspnet-razor-browser-page-about.png)

1. Hata ayıklama Visual Studio geri dönüp **Shift+F5** tuşlarına basın. Bu, tarayıcı penceresinde projeyi de kapatır.

1. Aşağıdaki Visual Studio **About.cshtml dosyasını seçin.** Ardından additional sözcüğüne _ve_ yerine file ve _directory sözcüklerini ekleyin._

    ![About.cshtml dosyasındaki metni değiştirme](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. **About.cshtml.cs dosyasını seçin.** Ardından, aşağıdaki `using` kısayolu kullanarak dosyanın en üstünde yer alan yönergeleri temizleyin:

   Gri renkli yönergelerden birini seçin; bir Hızlı Eylemler ampulü, sağ altta veya sol kenar `using` boşluğunda görünür. [](../../ide/quick-actions.md) Ampulü ve ardından Gereksiz Kullanımı **Kaldır'ı seçin.**

   ![About.cshtml.cs dosyasında gereksiz Usings'ı kaldırma](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio gereksiz yönergeleri `using` dosyadan siler.

1. Ardından `OnGet()` yönteminde gövdeyi aşağıdaki kodla değiştirebilirsiniz:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
         Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. Ortam ve Dize altında iki dalgalı alt **çizgi görünür.**  Dalgalı alt çizgiler görünür çünkü bu türler kapsamda yer alan değil.

   ![OnGet yönteminde dalgalı alt çizgilerle işaretlenmiş hatalar](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Burada listelenen **hataları görmek** için Hata Listesi araç çubuğunu açın. (Hata Listesi araç çubuğunu **görmüyorsanız Görüntüle'yi** **seçin**  >  **Üst menü** çubuğundan Hata Listesi.)

   ![Visual Studio'de Hata Listesi](media/csharp-aspnet-razor-error-list.png)

1. Şimdi bu sorunu çözeceğiz. Kod düzenleyicisinde imlecinizi hatayı içeren herhangi bir satıra yerleştirerek sol kenar boşluğundaki Hızlı Eylemler ampulü seçin. Ardından, açılan menüden Sistem'i kullan'ı **seçin;** bu yönergeyi dosyanın en üstüne ekleyin ve hataları giderin.

   !["using System;" yönergesi ekleme](media/csharp-aspnet-razor-add-usings.png)

1. **Değişikliklerinizi kaydetmek için Ctrl** + **S** tuşlarına basın ve **ardından F5** tuşuna basarak projenizi web tarayıcısında açın.

1. Yaptığınız değişiklikleri görüntülemek için web sitesi üst **kısmında Hakkında'ya** tıklayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Hakkında sayfasını görüntüleme](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Web tarayıcısını kapatın, **Shift** + **F5 tuşuna** basarak Hata Ayıklama modunu durdurun ve ardından Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>Çözümde tura çıkıyor

 1. Proje şablonu, _MyCoreApp_ adlı tek bir ASP.NET Core projesiyle bir çözüm oluşturur. İçeriğini **görüntülemek Çözüm Gezgini** sekmeyi seçin.

    ![ASP.NET Çözüm Gezgini MyCoreApp Visual Studio Razor Pages çözüm için Razor Pages'de](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Sayfalar **klasörünü** genişletin.

     ![Çözüm Gezgini'daki Sayfalar klasörü](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Kod **düzenleyicisinde Index.cshtml** dosyasını görüntüleme.

     ![Dizin kodu düzenleyicisinde Index.cshtml Visual Studio görüntüleme](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Her .cshtml dosyasının ilişkili bir kod dosyası vardır. Kod dosyasını düzenleyicide açmak için, Çözüm Gezgini'de **Index.cshtml** düğümünü genişletin ve **Index.cshtml.cs dosyasını** seçin.

     ![Kod düzenleyicisinde Index.cshtml.cs Visual Studio seçin](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Kod **düzenleyicisinde Index.cshtml.cs** dosyasını görüntüleme.

     ![About.cshtml dosyasını kod düzenleyicisinde Visual Studio görüntüleme](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Proje, web sitenizin kökü olan bir **wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     ![Visual Studio'de Çözüm Gezgini wwwroot klasörü](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini doğrudan &mdash; &mdash; istediğiniz yollara koyabilirsiniz.

 1. Proje ayrıca çalışma zamanında web uygulamasını yöneten yapılandırma dosyalarını içerir. Varsayılan uygulama [yapılandırması,](/aspnet/core/fundamentals/configuration) üzerindeappsettings.js *depolanır.* Ancak, üzerinde bir uygulama kullanarak buappsettings.Development.js *geçersiz kılabilirsiniz.* Dosyanın **appsettings.jsdosyasını** görüntülemek için **appsettings.Development.jsgenişletin.**

     ![Çözüm Gezgini Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. Uygulamayı **IIS Express** modunda derlemek ve çalıştırmak için IDE'de IIS Express düğmesini seçin. (Alternatif olarak **F5 tuşuna basın** veya Hata Ayıkla'ya **basın**  >  **Menü çubuğundan** Hata Ayıklamayı Başlat.)

     ![Dosyada IIS Express düğmesini Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **'IIS Express' web** sunucusuna bağlanamıyor hata iletisi alırsanız, Visual Studio'ı kapatın ve ardından sağ  tıklama veya bağlam menüsünden Yönetici olarak çalıştır seçeneğini kullanarak açın. Ardından uygulamayı yeniden çalıştırın.
     >
     > Iis SSL Express sertifikasını kabul etmek istiyor sanız soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için Evet'i seçin ve ardından bir **güvenlik** uyarısı iletisi alırsanız Evet'i seçin.

1. Visual Studio tarayıcı penceresi açar. Ardından menü çubuğunda **Giriş** ve **Gizlilik** sayfalarını görüyorsanız.

1. Menü **çubuğundan** Gizlilik'i seçin.

   **Tarayıcının** Gizlilik sayfası, *Privacy.cshtml* dosyasında ayarlanmış olan metni işler.

   ![Gizlilik sayfasında metni görüntüleme](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Hata ayıklama Visual Studio geri dönüp **Shift+F5** tuşlarına basın. Bu, tarayıcı penceresinde projeyi de kapatır.

1. Bu Visual Studio **privacy.cshtml dosyasını düzenlemek için** açın. Ardından Bu sayfayı kullanın sözcüklerini silin _ve sitenin_ gizlilik ilkesine ayrıntı ekleyin ve _@ViewData ["TimeStamp"]_ ile bu sayfa inşa aşamasındadır sözcüklerini ekleyin.

    ![Privacy.cshtml dosyasındaki metni değiştirme](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Şimdi bir kod değişikliğine bakalım. **Privacy.cshtml.cs dosyasını seçin.** Ardından, aşağıdaki `using` kısayolu kullanarak dosyanın en üstünde yer alan yönergeleri temizleyin:

   Gri renkli yönergelerden birini seçin; bir Hızlı Eylemler ampulü, sağ altta veya sol kenar `using` boşluğunda görünür. [](../../ide/quick-actions.md) Ampulü seçin ve gereksiz kullanmaları **kaldır'ın üzerine gelin.**

   ![Privacy.cshtml.cs dosyasında gereksiz Usings'ı kaldırma](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Şimdi değişiklikleri **görmek için** Değişiklikleri önizle'yi seçin.

   ![Değişiklikleri önizleme](media/vs-2019/csharp-aspnet-preview-changes.png)

   **Uygula**'yı seçin. Visual Studio gereksiz yönergeleri `using` dosyadan siler.

1. Ardından `OnGet()` yönteminde gövdeyi aşağıdaki kodla değiştirebilirsiniz:

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. DateTime altında iki dalgalı alt çizginin **görünür.** Dalgalı alt çizgiler görünür çünkü bu tür kapsamda değil.

   ![OnGet yönteminde dalgalı alt çizgilerle işaretlenmiş hatalar](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Burada listelenen **hataları görmek** için Hata Listesi araç çubuğunu açın. (Hata Listesi araç çubuğunu **görmüyorsanız Görüntüle'yi** **seçin**  >  **Üst menü** çubuğundan Hata Listesi.)

   ![Visual Studio'de Hata Listesi](media/vs-2019/csharp-aspnet-error-list.png)

1. Şimdi bu sorunu çözeceğiz. Kod düzenleyicisinde imlecinizi hatayı içeren herhangi bir satıra yerleştirerek sol kenar boşluğundaki Hızlı Eylemler ampulü seçin. Ardından, açılan menüden Sistem'i kullan'ı **seçin;** bu yönergeyi dosyanın en üstüne ekleyin ve hataları giderin.

   !["using System;" yönergesi ekleme](media/vs-2019/csharp-aspnet-add-usings.png)

1. Projenizi web tarayıcısında açmak için **F5** tuşuna basın.

1. Değişikliklerinizi görüntülemek için web sitesi üst **kısmında Gizlilik'i** seçin.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Gizlilik sayfasını görüntüleme](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Web tarayıcısını kapatın, **Shift** + **F5 tuşuna** basarak Hata Ayıklama modunu durdurun ve ardından Visual Studio.
::: moniker-end

## <a name="quick-answers-faq"></a>Hızlı yanıtlar hakkında SSS

Bazı temel kavramları vurgulamak için burada hızlı bir SSS bulabilirsiniz.

### <a name="what-is-c"></a>C# nedir?

[C#](https://docs.microsoft.com/dotnet/csharp/tour-of-csharp/) hem sağlam hem de öğrenmesi kolay olacak şekilde tasarlanmış tür kullanımı güvenli ve nesne odaklı bir programlama dilidir.

### <a name="what-is-aspnet-core"></a>ASP.NET Core nedir?

ASP.NET Core, web uygulamaları ve hizmetleri gibi İnternet'e bağlı uygulamalar için açık kaynak ve platformlar arası bir çerçevedir. ASP.NET Core uygulamaları .NET Core veya .NET Framework. ASP.NET Core uygulamalarınızı Windows, Mac ve Linux üzerinde platformlar arası geliştirebilir ve çalıştırabilirsiniz. ASP.NET Core, [GitHub'da açık kaynaktır.](https://github.com/aspnet/home)

### <a name="what-is-visual-studio"></a>Hangi Visual Studio?

Visual Studio, geliştiriciler için tümleşik bir üretkenlik araçları geliştirme paketidir. Bunu program ve uygulama oluşturmak için kullanabileceğiniz bir program olarak düşün.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamladıktan sonra! C#, ASP.NET Core ve Visual Studio IDE hakkında bilgi Visual Studio umuyoruz. C# ve ASP.NET ile web uygulaması veya web sitesi oluşturma hakkında daha fazla ASP.NET aşağıdaki öğreticilerle devam edin:

> [!div class="nextstepaction"]
> [ASP.NET Core ile Razor Pages web uygulaması oluşturma](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio kullanarak web Azure App Service web Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
