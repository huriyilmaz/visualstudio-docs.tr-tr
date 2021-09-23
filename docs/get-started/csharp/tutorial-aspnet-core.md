---
title: 'Öğretici: Kullanmaya başlayın C# ve ASP.NET Core'
titleSuffix: ''
description: C# ile ASP.NET Core adım Visual Studio web uygulaması oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: CSharp
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 8a7d6b0d29181ea464c8e98325e0c1ade53a45dd
ms.sourcegitcommit: 022ac348337f77c899996ac81060a969ebfb64bb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2021
ms.locfileid: "128134320"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Öğretici: Kullanmaya başlayın C# ve ASP.NET Core ile Visual Studio

Visual Studio kullanarak ASP.NET Core ile C# geliştirme öğreticisinde bir C# ASP.NET Core web uygulaması oluşturacak, bu uygulamada değişiklikler yapacak, IDE'nin bazı özelliklerini keşfeder ve ardından uygulamayı çalıştırabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

1. Visual Studio'yu yükleme
   ::: moniker range="vs-2017"
   
   Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.
   
   ::: moniker-end
   
   ::: moniker range=">=vs-2019"
   
   Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.
   
   ::: moniker-end

1. Güncelleştirme Visual Studio - Yüklemesini zaten Visual Studio, en son sürümü çalıştırmış olduğundan emin olun. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için Güncelleştirme Visual Studio [en son sürüm sayfasına](../../install/update-visual-studio.md) bakın.

1. Temanızı seçin (isteğe bağlı) - Bu öğreticide koyu temayı kullanan ekran görüntüleri yer almaktadır. Nasıl olduğunu [öğrenmek Visual Studio IDE ve Düzenleyici sayfasını](../../ide/quickstart-personalize-the-ide.md) kişiselleştirebilirsiniz.

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak yeni bir ASP.NET Core oluştur. Proje türü, herhangi bir şey eklemeden önce tam işlevsel bir web sitesi için ihtiyacınız olacak tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

3. Sol **bölmede yeni Project** iletişim kutusunda Visual **C#** öğesini genişletin, **Web'i** genişletin ve **ardından .NET Core'ı seçin.** Orta bölmede Web **Uygulaması'ASP.NET Core seçin.** Ardından, dosyayı *MyCoreApp olarak adlandırarak* Tamam'ı **seçin.**

   ![ASP.NET Core Visual Studio IDE'de Yeni Project iletişim kutusundaki Web Uygulaması proje şablonu](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

ASP.NET Core **Web** Uygulaması proje şablonunu görmüyorsanız, web uygulaması ve web geliştirme iş **ASP.NET ekleyerek bunu elde** edinebilirsiniz. Makinenize 2017 güncelleştirmelerinin hangi Visual Studio bağlı olarak bu iş yükünü aşağıdaki yöntemlerden birini kullanabilirsiniz.

#### <a name="option-1-use-the-new-project-dialog-box"></a>1. Seçenek: Yeni Project iletişim kutusunu kullanın

1. Yeni **Visual Studio Yükleyicisi** iletişim kutusunun sol bölmesindeKimlik aç **Project** seçin. (Görüntü ayarlarınıza bağlı olarak, bunu görmek için kaydırmanız gerekebilir.)

   ![Yeni Dosya iletişim Visual Studio Yükleyicisi Aç bağlantısını Project seçin](../media/open-visual-studio-installer-mycoreapp.png)

1. Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü ve** ardından Değiştir'i **seçin.**

   ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../media/tutorial-aspnet-workload.png)

   (Yeni iş yükünü yüklemeye Visual Studio önce bu uygulamayı kapatmanız gerekir.)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. Seçenek: Araçlar menü çubuğunu kullanma

1. Yeni Project iletişim **kutusundan** iptal edin. Ardından üst menü çubuğundan Araçlar Araçları ve **Özellikleri**  >  **Al'ı seçin.**

1. Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü ve** ardından Değiştir'i **seçin.**

   (Yeni iş yükünü yüklemeye Visual Studio önce bu uygulamayı kapatmanız gerekir.)

### <a name="add-a-project-template"></a>Proje şablonu ekleme

1. Yeni **Web ASP.NET Core iletişim** kutusunda Web Uygulaması **proje şablonunu** seçin.

1. **2 ASP.NET Core 2.1'in** üst açılan menüde görüntülendiğinden emin olur. Ardından **Tamam'ı seçin.**

   ![Yeni ASP.NET Core Web Uygulaması iletişim kutusu](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Üst açılan **menüden ASP.NET Core 2.1'i** görmüyorsanız, en son 2.1 Visual Studio. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için Güncelleştirme Visual Studio [en son sürüm sayfasına](../../install/update-visual-studio.md) bakın.

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="../../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="'Yeni Visual Studio oluştur' seçeneğinin vurgulanmış olduğu başlangıç penceresini gösteren ekran görüntüsü.":::

1. Yeni **proje oluştur penceresinde Dil** **listesinden C#** dilini seçin. Ardından Platform **listesinden Windows'yi** ve proje türleri **listesinden Web'i** seçin.

      Dil, platform ve proje türü filtrelerini uyguladikten sonra, ASP.NET Core **Web Uygulaması** şablonunu ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="./media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Web Uygulaması ASP.NET Core şablonunun Yeni Uygulama iletişim kutusunda vurgulanmış Project ekran görüntüsü.":::

   > [!NOTE]
   > ASP.NET Core **Web Uygulaması** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Ne arayabilirsiniz? iletisiyle birlikte 'Daha fazla araç ve özellik yükle' bağlantısını gösteren ekran görüntüsü.](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Yükleyicisi web geliştirme ASP.NET **iş yükünü** seçin.
   >
   > ![Uygulamanın .NET Core platformlar arası geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istenirse bunu yapma. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** *MyCoreApp* yazın veya **Project** girin. Ardından, **Sonraki'yi seçin.**

   :::image type="content" source="./media/vs-2019/csharp-name-your-aspnet-app.png" alt-text="Uygulama adı alanına 'MyCoreApp' girilen 'Yeni projenizi yapılandır' penceresini Project ekran görüntüsü.":::

1. Ek **bilgiler penceresinde** üst açılan menüde **.NET Core 3.1'in** görüntülendiğinden emin olur. Kutuyu işaret ederek Docker desteğini etkinleştirmeyi seçebilirsiniz. Kimlik doğrulamasını değiştir düğmesine tıklayarak da kimlik doğrulaması desteği ebilirsiniz. Buradan şunları seçebilirsiniz:
    - Hiçbiri: Kimlik doğrulaması yok.
    - Bireysel hesaplar: Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: Bu seçenek kimlik doğrulaması için Active Directory, Azure AD Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygundur.
    
    **Docker'ı Etkinleştir kutusunu** işaretsiz bırakın ve Kimlik Doğrulama Türü **için Hiçbiri'yi** seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="./media/vs-2019/aspnet-core-additional-information.png" alt-text="'Ek bilgiler' penceresindeki varsayılan ayarları gösteren ekran görüntüsü. Framework değeri '.NET Core 3.1' değeridir.":::

   Visual Studio projenizi açar.

::: moniker-end

::: moniker range=">=vs-2022"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="'Yeni Visual Studio oluştur' seçeneğinin vurgulanmış olduğu başlangıç penceresini gösteren ekran görüntüsü.":::

1. Yeni **proje oluştur penceresinde Dil** **listesinden C#** dilini seçin. Ardından Platform **listesinden Windows'yi** ve proje türleri **listesinden Web'i** seçin.

      Dil, platform ve proje türü filtrelerini uyguladikten sonra, ASP.NET Core **Web Uygulaması** şablonunu ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/csharp-create-new-project-aspnet-core.png" alt-text="Web Uygulaması ASP.NET Core şablonunun Yeni Uygulama iletişim kutusunda vurgulanmış Project ekran görüntüsü.":::

   > [!NOTE]
   > ASP.NET Core **Web Uygulaması** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > :::image type="content" source="media/vs-2022/not-finding-what-looking-for.png" alt-text="'Ne arayabilirsiniz? iletisiyle birlikte 'Daha fazla araç ve özellik yükle' bağlantısını gösteren ekran görüntüsü.":::
   >
   > Ardından, Visual Studio Yükleyicisi web geliştirme ASP.NET **iş yükünü** seçin.
   >
   > :::image type="content" source="media/vs-2022/aspnet-core-web-dev-workload.png" alt-text="Uygulamanın ASP.NET web geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.":::
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istenirse bunu yapma. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** *MyCoreApp* yazın veya **Project** girin. Ardından, **Sonraki'yi seçin.**

   :::image type="content" source="media/vs-2022/csharp-name-your-aspnet-app.png" alt-text="Uygulama adı alanına 'MyCoreApp' girilen 'Yeni projenizi yapılandır' penceresini Project ekran görüntüsü.":::

1. Ek **bilgiler penceresinde** Framework **alanında .NET 6.0'ın** **görüntülendiğinden emin** olur. Bu pencerede, kutuyu işaret ederek Docker desteğini etkinleştirmeyi seçebilirsiniz. Kimlik doğrulama türü açılan listesinden bir değer seçerek **de kimlik doğrulaması** desteği ekleyebilirsiniz. Buradan şunları seçebilirsiniz:

    - Hiçbiri: Kimlik doğrulaması yok.
    - Bireysel hesaplar: Yerel veya Azure tabanlı bir veritabanında depolanan kimlik doğrulamaları.
    - Microsoft kimlik platformu: Bu seçenek kimlik doğrulaması için Active Directory, Azure AD Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygun.
    
    **Docker 'ı etkinleştir** kutusunu işaretsiz bırakın ve kimlik doğrulama türü için **hiçbiri** ' ni seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="media/vs-2022/aspnet-core-additional-information.png" alt-text="' Ek bilgi ' penceresindeki varsayılan ayarları gösteren ekran görüntüsü. Çerçeve değeri ' .NET 6,0 '.":::

   Visual Studio, yeni projenizi açacak.

::: moniker-end

### <a name="about-your-solution"></a>Çözümünüz hakkında

Bu çözüm **Razor sayfası** tasarım modelini izler. Model ve denetleyici kodunu Razor sayfasının kendisine dahil etmek için kolaylaştırılmış olan [Model-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x&preserve-view=true) tasarım düzeninden farklıdır.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Çözümünüze tura katılın

 1. proje şablonu, _mycoreapp_ adlı tek bir ASP.NET Core projesiyle bir çözüm oluşturur. İçeriğini görüntülemek için **Çözüm Gezgini** sekmesini seçin.

    ![ASP.NET mycoreapp adlı Razor Pages çözümü için Visual Studio Çözüm Gezgini](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. **Sayfalar** klasörünü genişletin ve ardından *. cshtml* dosyasını genişletin.

     ![Visual Studio Çözüm Gezgini. cshtml dosyası](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Kod düzenleyicisinde **About. cshtml** dosyasını görüntüleyin.

     ![Visual Studio kod düzenleyicisinde About. cshtml dosyasının ilk on satırını gösteren ekran görüntüsü.](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. **About. cshtml. cs** dosyasını seçin.

     ![Visual Studio kod düzenleyicisinde About. cshtml. cs dosyasını seçin](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Kod düzenleyicisinde **About. cshtml. cs** dosyasını görüntüleyin.

     ![Visual Studio kod düzenleyicisinde About. cshtml. cs dosyasının ilk 18 satırını gösteren ekran görüntüsü. ](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Proje, Web siteniz için kök olan bir **Wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     ![Visual Studio Çözüm Gezgini Wwwroot klasörü](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    &mdash;CSS, resim ve JavaScript kitaplıkları gibi statik site içeriğini &mdash; doğrudan istediğiniz yollarla yerleştirebilirsiniz.

 1. Proje, çalışma zamanında Web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *appSettings. JSON*' da depolanır. Ancak, appSettings kullanarak bu ayarları geçersiz kılabilirsiniz *. Development. JSON*. AppSettings 'i görüntülemek için **appSettings. JSON** dosyasını genişletin **. Development. JSON** dosyası.

     ![Visual Studio Çözüm Gezgini yapılandırma dosyaları](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. uygulamayı derlemek ve hata ayıklama modunda çalıştırmak için ıde 'de **IIS Express** düğmesini seçin. (Alternatif olarak, **F5** tuşuna basın veya **Hata Ayıkla**  >  ' yı seçin Menü çubuğundan **hata ayıklamayı başlatın** .)

     ![Visual Studio IIS Express düğmesini seçin](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **' IIS Express ' web sunucusuna bağlanmadığını** belirten bir hata iletisi alırsanız, Visual Studio kapatın ve sağ tıklama ya da bağlam menüsünde **yönetici olarak çalıştır** seçeneğini kullanarak açın. Sonra, uygulamayı yeniden çalıştırın.
     >
     > Ayrıca bir IIS SSL Express sertifikasını kabul etmek isteyip istemediğinizi soran bir ileti alabilirsiniz. Kodu bir Web tarayıcısında görüntülemek için **Evet**' i seçin ve ardından bir izleme güvenlik uyarısı Iletisi alırsanız **Evet** ' i seçin.

1. Visual Studio bir tarayıcı penceresi başlatır. Ardından, menü çubuğunda **giriş**, **hakkında** ve **iletişim** sayfaları ' nı görmeniz gerekir. (Bunu yapmazsanız, görüntülemek için "hamburger" menü öğesini seçin.)

    ![Web uygulamanızdaki menü çubuğundan "hamburger" menü öğesini seçin](media/csharp-aspnet-razor-browser-page.png)

1. Menü çubuğundan **hakkında** ' yı seçin.

   ![Uygulamanızın tarayıcı penceresinin menü çubuğunda hakkında ' yı seçin](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Diğer şeyler arasında, tarayıcıdaki **hakkında** sayfası *About. cshtml* dosyasında ayarlanan metni işler.

   ![Hakkında sayfasında metni görüntüleme](media/csharp-aspnet-razor-browser-page-about.png)

1. Visual Studio döndürün ve sonra hata ayıklama modunu durdurmak için **shıft + F5** tuşlarına basın. Bu, projeyi tarayıcı penceresinde de kapatır.

1. Visual Studio ' de, **. cshtml**' yi seçin. Sonra, _başka bir_ sözcük silin ve onun yerine, sözcükler _dosyasını ve dizinini_ ekleyin.

    ![About. cshtml dosyasındaki metni değiştirin](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. **. Cshtml. cs** öğesini seçin. Ardından, `using` aşağıdaki kısayolu kullanarak dosyanın en üstündeki yönergeleri temizleyin:

   Gri olmayan yönergelerden herhangi birini seçin `using` ve hızlı bir [eylem](../../ide/quick-actions.md) ampul, yalnızca giriş işaretinin altında veya sol kenar boşluğunda görünür. Ampul ' i seçin ve ardından gereksiz kullanımları **Kaldır**' ı seçin.

   ![About. cshtml. cs dosyasındaki gereksiz kullanımları kaldırın](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio gereksiz `using` yönergeleri dosyadan siler.

1. Sonra, yönteminde, `OnGet()` gövdesini aşağıdaki kodla değiştirin:

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
         Message = String.Format("Your directory is {0}.", directory);
     }
    ```

1. **Ortam** ve **dize** altında iki dalgalı alt çizgi göründüğünü unutmayın. Bu türler kapsamda olmadığı için dalgalı alt çizgiler görüntülenir.

   ![OnGet yönteminde dalgalı alt çizgilerle işaretlenmiş hatalar](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Burada listelenen hataların aynısını görmek için **hata listesi** araç çubuğunu açın. ( **Hata listesi** araç çubuğunu görmüyorsanız, **Görünüm**  >  ' ü seçin. Üst menü çubuğundan **hata listesi** .)

   ![Visual Studio Hata Listesi](media/csharp-aspnet-razor-error-list.png)

1. Bunu düzeldelim. Kod Düzenleyicisi 'nde imlecinizi hatayı içeren bir satıra yerleştirin ve ardından sol kenar boşluğunda hızlı eylemler Ampul ampul ' i seçin. Daha sonra, açılan menüden, bu yönergeyi dosyanızın en üstüne eklemek ve hataları çözmek için, **Sistem kullanma** seçeneğini belirleyin.

   !["Using System;" yönergesini ekleyin](media/csharp-aspnet-razor-add-usings.png)

1.  +  Değişikliklerinizi kaydetmek için CTRL 'e basın ve ardından **F5** 'e basarak projenizi web tarayıcısında açın.

1. Web sitesinin en üstünde, değişikliklerinizi görüntülemek için **hakkında** ' yı seçin.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş hakkında sayfasını görüntüleyin](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. web tarayıcısını kapatın, **shıft** + **F5** tuşlarına basarak hata ayıklama modunu durdurun ve ardından Visual Studio kapatın.

::: moniker-end

::: moniker range="=vs-2019"

## <a name="tour-your-solution"></a>Çözümünüze tura katılın

 1. proje şablonu, _mycoreapp_ adlı tek bir ASP.NET Core projesiyle bir çözüm oluşturur. İçeriğini görüntülemek için **Çözüm Gezgini** sekmesini seçin.

    ![' mycoreapp ' adlı ASP.NET core projesinin içeriğini gösteren Visual Studio Çözüm Gezgini ekran görüntüsü.](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. **Sayfalar** klasörünü genişletin.

     ![' mycoreapp ' için sayfalar klasörünün içeriğini gösteren Visual Studio Çözüm Gezgini ekran görüntüsü.](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Kod düzenleyicisinde **Index. cshtml** dosyasını görüntüleyin.

     ![Visual Studio kod düzenleyicisinde açık Index. cshtml dosyasını gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Her. cshtml dosyası, ilişkili bir kod dosyasına sahiptir. Kod dosyasını düzenleyicide açmak için, Çözüm Gezgini içindeki **index. cshtml** düğümünü genişletin ve **index. cshtml. cs** dosyasını seçin.

     ![dizin. cshtml. cs dosyasının seçili Visual Studio gösterildiği Çözüm Gezgini ekran görüntüsü.](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Kod düzenleyicisinde **Index. cshtml. cs** dosyasını görüntüleyin.

     ![Visual Studio kod düzenleyicisinde açık Index. cshtml. cs dosyasını gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Proje, Web siteniz için kök olan bir **Wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     ![' wwwroot ' klasörünün içeriğini gösteren Visual Studio Çözüm Gezgini ekran görüntüsü.](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    &mdash;CSS, resim ve JavaScript kitaplıkları gibi statik site içeriğini &mdash; doğrudan istediğiniz yollarla yerleştirebilirsiniz.

 1. Proje, çalışma zamanında Web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *appSettings. JSON*' da depolanır. Ancak, appSettings kullanarak bu ayarları geçersiz kılabilirsiniz *. Development. JSON*. AppSettings 'i görüntülemek için **appSettings. JSON** dosyasını genişletin **. Development. JSON** dosyası.

     ![Visual Studio appsettings. json dosyasını gösteren ve appsettings 'i göstermek için genişletilen Çözüm Gezgini ekran görüntüsü. Development. JSON dosyası.](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. uygulamayı derlemek ve hata ayıklama modunda çalıştırmak için ıde 'de **IIS Express** düğmesini seçin. (Alternatif olarak, **F5** tuşuna basın veya **Hata Ayıkla**  >  ' yı seçin Menü çubuğundan **hata ayıklamayı başlatın** .)

     ![Visual Studio ıde 'de vurgulanmış IIS Express düğmesini gösteren ekran görüntüsü.](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **' IIS Express ' web sunucusuna bağlanmadığını** belirten bir hata iletisi alırsanız, Visual Studio kapatın ve sağ tıklama ya da bağlam menüsünde **yönetici olarak çalıştır** seçeneğini kullanarak açın. Sonra, uygulamayı yeniden çalıştırın.
     >
     > Ayrıca bir IIS SSL Express sertifikasını kabul etmek isteyip istemediğinizi soran bir ileti alabilirsiniz. Kodu bir Web tarayıcısında görüntülemek için **Evet**' i seçin ve ardından bir izleme güvenlik uyarısı Iletisi alırsanız **Evet** ' i seçin.

1. Visual Studio bir tarayıcı penceresi başlatır. Ardından, menü çubuğunda **giriş** ve **Gizlilik** sayfalarını görmeniz gerekir.

1. Menü çubuğundan **Gizlilik** ' i seçin.

   Tarayıcıdaki **Gizlilik** sayfası, *Gizlilik. cshtml* dosyasında ayarlanan metni işler.

   ![MyCoreApp gizlilik sayfasını, "sitenizin gizlilik ilkesini ayrıntılı olarak kullanın." metnini gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Visual Studio döndürün ve sonra hata ayıklama modunu durdurmak için **shıft + F5** tuşlarına basın. Bu, projeyi tarayıcı penceresinde de kapatır.

1. Visual Studio, düzenlenecek **gizlilik. cshtml** dosyasını açın. Ardından, bu _sayfayı kullanarak sitenizin gizlilik ilkesini ayrıntılandırın_ ve onun yerine _bu sayfanın yapım aşamasında olduğu kelimeleri @ViewData ["timestamp"] olarak_ ekleyin.

    ![güncelleştirilmiş metinle Visual Studio kod düzenleyicisinde açık olan gizlilik. cshtml dosyasını gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Şimdi bir kod değişikliği yapalim. **Gizlilik. cshtml. cs** öğesini seçin. Ardından, `using` aşağıdaki kısayolu kullanarak dosyanın en üstündeki yönergeleri temizleyin:

   Gri olmayan yönergelerden herhangi birini seçin `using` ve hızlı bir [eylem](../../ide/quick-actions.md) ampul, yalnızca giriş işaretinin altında veya sol kenar boşluğunda görünür. Ampul ' i seçin ve ardından **gereksiz kullanımları kaldır**' ın üzerine gelin.

   ![' gereksiz using 'leri kaldır ' iletişim kutusuyla Visual Studio kod düzenleyicisinde gizlilik. cshtml dosyasını gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Şimdi nelerin olacağını görmek için **Değişiklikleri Önizle** ' yi seçin.

   ![Yeni ' Using ' listesini ve gizlilik. cshtml dosyasındaki kodu gösteren önizleme değişiklikleri iletişim kutusunu gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-preview-changes.png)

   **Uygula**'yı seçin. Visual Studio gereksiz `using` yönergeleri dosyadan siler.

1. Sonra, yönteminde, `OnGet()` gövdesini aşağıdaki kodla değiştirin:

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. **Tarih saat** altında iki dalgalı alt çizgi göründüğünü unutmayın. Bu tür kapsamda olmadığından dalgalı alt çizgiler görüntülenir.

   ![OnGet yönteminde dalgalı alt çizgilerle işaretlenmiş hataları gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Burada listelenen hataların aynısını görmek için **hata listesi** araç çubuğunu açın. ( **Hata listesi** araç çubuğunu görmüyorsanız, **Görünüm**  >  ' ü seçin. Üst menü çubuğundan **hata listesi** .)

   ![Visual Studio Hata Listesi](media/vs-2019/csharp-aspnet-error-list.png)

1. Bunu düzeldelim. Kod Düzenleyicisi 'nde imlecinizi hatayı içeren bir satıra yerleştirin ve ardından sol kenar boşluğunda hızlı eylemler Ampul ampul ' i seçin. Daha sonra, açılan menüden, bu yönergeyi dosyanızın en üstüne eklemek ve hataları çözmek için, **Sistem kullanma** seçeneğini belirleyin.

   ![' Using System ' yönergesini ekleme önerisinde bulunan Hızlı Eylemler menüsünü gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-add-usings.png)

1. **F5** tuşuna basarak projenizi web tarayıcısında açın.

1. Değişikliklerinizi görüntülemek için Web sitesinin en üstünde **Gizlilik** ' i seçin.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş gizlilik sayfasını gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. web tarayıcısını kapatın, **shıft** + **F5** tuşlarına basarak hata ayıklama modunu durdurun ve ardından Visual Studio kapatın.
::: moniker-end

::: moniker range=">=vs-2022"

## <a name="tour-your-solution"></a>Çözümünüze tura katılın

 1. proje şablonu, *mycoreapp* adlı tek bir ASP.NET Core projesiyle bir çözüm oluşturur. İçeriğini görüntülemek için **Çözüm Gezgini** sekmesini seçin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-mycoreapp.png" alt-text="' mycoreapp ' adlı ASP.NET core projesinin içeriğini gösteren Visual Studio Çözüm Gezgini ekran görüntüsü.":::

 1. **Sayfalar** klasörünü genişletin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-solution-explorer-pages.png" alt-text="' mycoreapp ' için sayfalar klasörünün içeriğini gösteren Visual Studio Çözüm Gezgini ekran görüntüsü.":::

 1. Kod düzenleyicisinde **Index. cshtml** dosyasını görüntüleyin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml.png" alt-text="Visual Studio kod düzenleyicisinde açık Index. cshtml dosyasını gösteren ekran görüntüsü.":::

 1. Her. cshtml dosyası, ilişkili bir kod dosyasına sahiptir. Kod dosyasını düzenleyicide açmak için, Çözüm Gezgini içindeki **index. cshtml** düğümünü genişletin ve **index. cshtml. cs** dosyasını seçin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-choose-index-cshtml.png" alt-text="dizin. cshtml. cs dosyasının seçili Visual Studio gösterildiği Çözüm Gezgini ekran görüntüsü.":::

 1. Kod düzenleyicisinde **Index. cshtml. cs** dosyasını görüntüleyin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml-editing.png" alt-text="Visual Studio kod düzenleyicisinde açık Index. cshtml. cs dosyasını gösteren ekran görüntüsü.":::

 1. Proje, Web siteniz için kök olan bir **Wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-wwwroot.png" alt-text="' wwwroot ' klasörünün içeriğini gösteren Visual Studio Çözüm Gezgini ekran görüntüsü.":::

    &mdash;CSS, resim ve JavaScript kitaplıkları gibi statik site içeriğini &mdash; doğrudan istediğiniz yollarla yerleştirebilirsiniz.

 1. Proje, çalışma zamanında Web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *appSettings. JSON*' da depolanır. Ancak, appSettings kullanarak bu ayarları geçersiz kılabilirsiniz *. Development. JSON*. AppSettings 'i görüntülemek için **appSettings. JSON** dosyasını genişletin **. Development. JSON** dosyası.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-appsettingsjson.png" alt-text="Visual Studio appsettings. json dosyasını gösteren ve appsettings 'i göstermek için genişletilen Çözüm Gezgini ekran görüntüsü. Development. JSON dosyası.":::

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. uygulamayı derlemek ve hata ayıklama modunda çalıştırmak için ıde 'de **IIS Express** düğmesini seçin. (Alternatif olarak, **F5** tuşuna basın veya **Hata Ayıkla**  >  ' yı seçin Menü çubuğundan **hata ayıklamayı başlatın** .)

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-iisexpress.png" alt-text="Visual Studio ıde 'de vurgulanmış IIS Express düğmesini gösteren ekran görüntüsü.":::

     > [!NOTE]
     > **' IIS Express ' web sunucusuna bağlanmadığını** belirten bir hata iletisi alırsanız, Visual Studio kapatın ve sağ tıklama ya da bağlam menüsünde **yönetici olarak çalıştır** seçeneğini kullanarak açın. Sonra, uygulamayı yeniden çalıştırın.
     >
     > Ayrıca bir IIS SSL Express sertifikasını kabul etmek isteyip istemediğinizi soran bir ileti alabilirsiniz. Kodu bir Web tarayıcısında görüntülemek için **Evet**' i seçin ve ardından bir izleme güvenlik uyarısı Iletisi alırsanız **Evet** ' i seçin.

1. Visual Studio bir tarayıcı penceresi başlatır. Ardından, menü çubuğunda **giriş** ve **Gizlilik** sayfalarını görmeniz gerekir.

1. Menü çubuğundan **Gizlilik** ' i seçin.

   Tarayıcıdaki **Gizlilik** sayfası, *Gizlilik. cshtml* dosyasında ayarlanan metni işler.

   :::image type="content" source="media/vs-2022/csharp-aspnet-browser-page-privacy.png" alt-text="MyCoreApp gizlilik sayfasını, &quot;sitenizin gizlilik ilkesini ayrıntılı olarak kullanın.&quot; metnini gösteren ekran görüntüsü.":::

1. Visual Studio döndürün ve sonra hata ayıklama modunu durdurmak için **shıft + F5** tuşlarına basın. Bu, projeyi tarayıcı penceresinde de kapatır.

1. Visual Studio, düzenlenecek **gizlilik. cshtml** dosyasını açın. Ardından, bu *sayfayı kullanarak sitenizin gizlilik ilkesini ayrıntılandırın* ve onun yerine *bu sayfanın yapım aşamasında olduğu kelimeleri @ViewData ["timestamp"] olarak* ekleyin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-privacy-cshtml-code-changed.png" alt-text="güncelleştirilmiş metinle Visual Studio kod düzenleyicisinde açık olan gizlilik. cshtml dosyasını gösteren ekran görüntüsü.":::

1. Şimdi bir kod değişikliği yapalim. **Gizlilik. cshtml. cs** öğesini seçin. Ardından, `using` aşağıdaki kısayolu seçerek dosyanın en üstündeki yönergeleri temizleyin:

   Gri olmayan yönergelerden herhangi birini seçin `using` ve hızlı bir [eylem](../../ide/quick-actions.md) ampul, yalnızca giriş işaretinin altında veya sol kenar boşluğunda görünür. Ampul ' i seçin ve ardından **gereksiz kullanımları kaldır**' ın üzerine gelin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-remove-unnecessary-usings.png" alt-text="' gereksiz using 'leri kaldır ' iletişim kutusuyla Visual Studio kod düzenleyicisinde gizlilik. cshtml dosyasını gösteren ekran görüntüsü.":::

   Şimdi nelerin olacağını görmek için **Değişiklikleri Önizle** ' yi seçin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-preview-changes.png" alt-text="Yeni ' Using ' listesi ve gizlilik. cshtml dosyasındaki kod ile Değişiklikleri Önizle iletişim kutusunu gösteren ekran görüntüsü.":::

   **Uygula**'yı seçin. Visual Studio gereksiz `using` yönergeleri dosyadan siler.

1. Ardından, [DateTime. ToString](xref:System.DateTime.ToString%2A) yöntemini kullanarak kültür veya bölgeniz için biçimlendirilen geçerli tarih için bir dize oluşturun.

   - Yönteminin ilk bağımsız değişkeni tarihin nasıl görüntüleneceğini belirtir. Bu örnek, `d` kısa tarih biçimini gösteren Biçim Belirleyicisi () kullanır. 
   - İkinci bağımsız değişken, tarih için kültürü veya bölgeyi belirten [CultureInfo](/dotnet/api/system.globalization.cultureinfo) nesnesidir. Bu bağımsız değişken, diğer şeyleri, tarih içindeki sözcüklerin dilini ve kullanılan ayırıcıların türünü belirler.
 
`OnGet()`Yönteminin gövdesini şu kodla değiştirin:

   ```csharp
   public void OnGet()
   {
      string dateTime = DateTime.Now.ToString("d", new CultureInfo("en-US"));
      ViewData["TimeStamp"] = dateTime;
   }
   ```

1. **CultureInfo** altında iki dalgalı alt çizgi göründüğünü unutmayın. Bu tür kapsamda olmadığından dalgalı alt çizgiler görüntülenir.

   :::image type="content" source="media/vs-2022/csharp-aspnet-add-new-onget-method.png" alt-text="Kod düzenleyicisinde, CultureInfo nesnesinin altında dalgalı alt çizgiyle birlikte OnGet metodunu gösteren ekran görüntüsü.":::

    Burada listelenen hataların aynısını görmek için **hata listesi** araç çubuğunu açın. ( **Hata listesi** araç çubuğunu görmüyorsanız, **Görünüm**  >  ' ü seçin. Üst menü çubuğundan **hata listesi** .)

   :::image type="content" source="media/vs-2022/csharp-aspnet-error-list.png" alt-text="Visual Studio Hata Listesi penceresini gösteren ekran görüntüsü. ' CultureInfo ' türünde bir using yönergesi eksik.":::

1. Bunu düzeldelim. Kod Düzenleyicisi 'nde imlecinizi hatayı içeren bir satıra yerleştirin ve ardından sol kenar boşluğunda hızlı eylemler Ampul ampul ' i seçin. Ardından, dosyanın en üstüne yönergesini eklemek ve hataları çözmek için açılan **menüden System.Globalization** kullanarak öğesini seçin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-add-usings.png" alt-text="'using System.Globalization' yönergesini ekleme önerisiyle Birlikte Hızlı Eylemler menüsünü gösteren ekran görüntüsü.":::

1. Projenizi web tarayıcısında açmak için **F5** tuşuna basın.

1. Yaptığınız değişiklikleri görüntülemek için web sitesi üst **kısmında Gizlilik'i** seçin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-browser-page-privacy-changed.png" alt-text="MyCoreApp'in tarihi eklemek için yapılan değişiklikleri içeren Gizlilik sayfasını gösteren ekran görüntüsü.":::

1. Web tarayıcısını kapatın, **Shift** + **F5 tuşuna** basarak Hata Ayıklama modunu durdurun ve ardından Visual Studio.

::: moniker-end

## <a name="quick-answers-faq"></a>Hızlı yanıtlar hakkında SSS

Bazı temel kavramları vurgulamak için burada hızlı bir SSS bulabilirsiniz.

### <a name="what-is-c"></a>C# nedir?

[C#](/dotnet/csharp/tour-of-csharp/) hem sağlam hem de öğrenmesi kolay olacak şekilde tasarlanmış tür kullanımı güvenli ve nesne odaklı bir programlama dilidir.

### <a name="what-is-aspnet-core"></a>ASP.NET Core nedir?

ASP.NET Core, web uygulamaları ve hizmetleri gibi İnternet'e bağlı uygulamalar için açık kaynak ve platformlar arası bir çerçevedir. ASP.NET Core uygulamalar .NET Core veya .NET Framework. ASP.NET Core, Mac ve Linux üzerinde platformlar arası Windows geliştirebilir ve çalıştırabilirsiniz. ASP.NET Core açık kaynaktır ve [GitHub.](https://github.com/aspnet/home)

### <a name="what-is-visual-studio"></a>Hangi Visual Studio?

Visual Studio, geliştiriciler için tümleşik bir üretkenlik araçları geliştirme paketidir. Bunu program ve uygulama oluşturmak için kullanabileceğiniz bir program olarak düşün.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamladıktan sonra! C#, ASP.NET Core ve Visual Studio IDE hakkında bilgi Visual Studio umuyoruz. C# ve ASP.NET ile web uygulaması veya web sitesi oluşturma hakkında daha fazla ASP.NET aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [ASP.NET Core ile Razor Pages web uygulaması ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)

Veya Web uygulamalarınızı Docker ile kapsayıcılı hale nasıl ala öğrenin:

> [!div class="nextstepaction"]
> [Visual Studio'de Kapsayıcı Araçları](../../containers/overview.md)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio kullanarak web Azure App Service web Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
