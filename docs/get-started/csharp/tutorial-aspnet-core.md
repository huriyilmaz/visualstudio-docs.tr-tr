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
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427056"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Öğretici: Kullanmaya başlayın C# ve ASP.NET Core ile Visual Studio

Visual Studio kullanarak ASP.NET Core ile C# geliştirme öğreticisinde bir C# ASP.NET Core web uygulaması oluşturacak, üzerinde değişiklikler yapacak, IDE'nin bazı özelliklerini keşfeder ve ardından uygulamayı çalıştırabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

1. Visual Studio'yu yükleme
   ::: moniker range="vs-2017"
   
   Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.
   
   ::: moniker-end
   
   ::: moniker range=">=vs-2019"
   
   Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.
   
   ::: moniker-end

1. Güncelleştirme Visual Studio - Daha önce Visual Studio, en son sürümü çalıştırmış olduğundan emin olun. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için Güncelleştirme Visual Studio [en son sürüm sayfasına](../../install/update-visual-studio.md) bakın.

1. Temanızı seçin (isteğe bağlı) - Bu öğreticide koyu temayı kullanan ekran görüntüleri yer almaktadır. Nasıl olduğunu [öğrenmek Visual Studio IDE ve Düzenleyici sayfasını](../../ide/quickstart-personalize-the-ide.md) kişiselleştirebilirsiniz.

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak yeni bir ASP.NET Core oluştur. Proje türü, herhangi bir şey eklemeden önce tam işlevsel bir web sitesi için ihtiyacınız olacak tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. Üst menü çubuğundan Dosya Yeni **dosya'Project.** >  > 

3. Sol **bölmede yeni Project** iletişim kutusunda Visual **C#** öğesini genişletin, **Web'i** genişletin ve **ardından .NET Core'ı seçin.** Orta bölmede Web **Uygulaması'ASP.NET Core seçin.** Ardından, dosyayı *MyCoreApp olarak adlandırarak* Tamam'ı **seçin.**

   ![ASP.NET Core Visual Studio IDE'de Yeni Project iletişim kutusundaki Web Uygulaması proje şablonu](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

ASP.NET Core **Web Uygulaması** proje şablonunu görmüyorsanız, web uygulaması ve web geliştirme iş ASP.NET ekleyerek **bunu elde** edinebilirsiniz. Makinenize 2017 güncelleştirmelerinin hangi Visual Studio bağlı olarak bu iş yükünü aşağıdaki yöntemlerden birini kullanabilirsiniz.

#### <a name="option-1-use-the-new-project-dialog-box"></a>1. Seçenek: Yeni Project iletişim kutusunu kullanın

1. Yeni **Visual Studio Yükleyicisi** iletişim kutusunun sol bölmesindeKimlik aç **Project** seçin. (Görüntü ayarlarınıza bağlı olarak, bunu görmek için kaydırmanız gerekebilir.)

   ![Yeni Dosya iletişim Visual Studio Yükleyicisi Aç bağlantısını Project seçin](../media/open-visual-studio-installer-mycoreapp.png)

1. Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü ve** ardından Değiştir'i **seçin.**

   ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../media/tutorial-aspnet-workload.png)

   (Yeni iş yükünü yüklemeye Visual Studio önce bu uygulamayı kapatmanız gerekir.)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. Seçenek: Araçlar menü çubuğunu kullanma

1. Yeni Dosya ekle **iletişim Project** iptal edin. Ardından üst menü çubuğundan Araçlar Araçları ve **Özellikleri**  >  **Al'ı seçin.**

1. Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü ve** ardından Değiştir'i **seçin.**

   (Yeni iş yükünü yüklemeye Visual Studio önce bu uygulamayı kapatmanız gerekir.)

### <a name="add-a-project-template"></a>Proje şablonu ekleme

1. Yeni **Web ASP.NET Core iletişim** kutusunda Web Uygulaması proje **şablonunu** seçin.

1. Üst **ASP.NET Core 2.1'in** görüntülendiğinden emin olmak. Ardından **Tamam'ı seçin.**

   ![Yeni ASP.NET Core Web Uygulaması iletişim kutusu](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Üst açılan menüde **ASP.NET Core 2.1'i** görmüyorsanız, en son 2.1 Visual Studio. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için Güncelleştirme Visual Studio [en son sürüm sayfasına](../../install/update-visual-studio.md) bakın.

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="../../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="'Yeni Visual Studio oluştur' seçeneğinin vurgulanmış olduğu başlangıç penceresini gösteren ekran görüntüsü.":::

1. Yeni **proje oluştur penceresinde Dil** **listesinden C#** dilini seçin. Ardından, **Windows** Listesinden Web'i ve proje türleri listesinden **Web'i** seçin.

      Dil, platform ve proje türü filtrelerini uygulayan web **uygulaması ASP.NET Core** ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="./media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="Web Uygulaması ASP.NET Core şablonunun Yeni Uygulama iletişim kutusunda vurgulanmış Project ekran görüntüsü.":::

   > [!NOTE]
   > ASP.NET Core **Web Uygulaması** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Ne arayabilirsiniz? iletisiyle birlikte 'Daha fazla araç ve özellik yükle' bağlantısını gösteren ekran görüntüsü.](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Yükleyicisi web geliştirme ASP.NET **seçin.**
   >
   > ![Uygulamanın .NET Core platformlar arası geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istenirse bunu yapma. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** *MyCoreApp* yazın veya **Project girin.** Ardından, **Sonraki'yi seçin.**

   :::image type="content" source="./media/vs-2019/csharp-name-your-aspnet-app.png" alt-text="Uygulama adı alanına 'MyCoreApp' girilen 'Yeni projenizi yapılandır' penceresini Project ekran görüntüsü.":::

1. Ek **bilgiler penceresinde** üst açılan menüde **.NET Core 3.1'in** görüntülendiğinden emin olur. Kutuyu işaret ederek Docker desteğini etkinleştirmeyi seçebilirsiniz. Kimlik doğrulamasını değiştir düğmesine tıklayarak da kimlik doğrulaması desteği ebilirsiniz. Buradan şunları seçebilirsiniz:
    - Hiçbiri: Kimlik doğrulaması yok.
    - Bireysel hesaplar: Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: Bu seçenek kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygundur.
    
    **Docker'ı Etkinleştir kutusunu** işaretsiz bırakın ve Kimlik Doğrulama Türü **için Hiçbiri'yi** seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="./media/vs-2019/aspnet-core-additional-information.png" alt-text="'Ek bilgiler' penceresindeki varsayılan ayarları gösteren ekran görüntüsü. Framework değeri '.NET Core 3.1' değeridir.":::

   Visual Studio projenizi açar.

::: moniker-end

::: moniker range=">=vs-2022"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="'Yeni Visual Studio oluştur' seçeneğinin vurgulanmış olduğu başlangıç penceresini gösteren ekran görüntüsü.":::

1. Yeni **proje oluştur penceresinde Dil** **listesinden C#** dilini seçin. Ardından, **Windows** Listesinden Web'i ve proje türleri listesinden **Web'i** seçin.

      Dil, platform ve proje türü filtrelerini uygulayan web **uygulaması ASP.NET Core** ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/csharp-create-new-project-aspnet-core.png" alt-text="Web Uygulaması ASP.NET Core şablonunun Yeni Uygulama iletişim kutusunda vurgulanmış Project ekran görüntüsü.":::

   > [!NOTE]
   > ASP.NET Core **Web Uygulaması** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > :::image type="content" source="media/vs-2022/not-finding-what-looking-for.png" alt-text="'Ne arayabilirsiniz? iletisiyle birlikte 'Daha fazla araç ve özellik yükle' bağlantısını gösteren ekran görüntüsü.":::
   >
   > Ardından, Visual Studio Yükleyicisi web geliştirme ASP.NET **seçin.**
   >
   > :::image type="content" source="media/vs-2022/aspnet-core-web-dev-workload.png" alt-text="Uygulamanın ASP.NET web geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.":::
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istenirse bunu yapma. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresine** *MyCoreApp* yazın veya **Project girin.** Ardından, **Sonraki'yi seçin.**

   :::image type="content" source="media/vs-2022/csharp-name-your-aspnet-app.png" alt-text="Uygulama adı alanına 'MyCoreApp' girilen 'Yeni projenizi yapılandır' penceresini Project ekran görüntüsü.":::

1. Ek **bilgiler penceresinde** Framework **alanında .NET 6.0'ın** **görüntülendiğinden emin** olur. Bu pencerede, kutuyu işaret ederek Docker desteğini etkinleştirmeyi seçebilirsiniz. Kimlik doğrulama türü açılan listesinden bir değer seçerek **de kimlik doğrulaması** desteği ekleyebilirsiniz. Buradan şunları seçebilirsiniz:

    - Hiçbiri: Kimlik doğrulaması yok.
    - Bireysel hesaplar: Yerel veya Azure tabanlı bir veritabanında depolanan kimlik doğrulamaları.
    - Microsoft kimlik platformu: Bu seçenek kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygundur.
    
    **Docker'ı Etkinleştir kutusunu** işaretsiz bırakın ve Kimlik doğrulaması türü **için Hiçbiri'yi** seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="media/vs-2022/aspnet-core-additional-information.png" alt-text="'Ek bilgiler' penceresindeki varsayılan ayarları gösteren ekran görüntüsü. Framework değeri '.NET 6.0'dır.":::

   Visual Studio projeniz açılır.

::: moniker-end

### <a name="about-your-solution"></a>Çözümünüz hakkında

Bu çözüm, **Razor Sayfası tasarım desenini** izler. [Model-View-Controller (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x&preserve-view=true) tasarım modelinden farklıdır ve razor sayfasının içinde model ve denetleyici kodunun dahil basitleştirilmiştir.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Çözümde tura çıkıyor

 1. Proje şablonu, _MyCoreApp_ adlı tek ASP.NET Core bir çözüm oluşturur. İçeriğini **Çözüm Gezgini** için sekmeyi seçin.

    ![ASP.NET Çözüm Gezgini MyCoreApp Visual Studio bir Razor Pages için Razor Pages'de](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Sayfalar **klasörünü ve** ardından *About.cshtml dosyasını genişletin.*

     ![Çözüm Gezgini'de yer alan About.cshtml Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Kod **düzenleyicisinde About.cshtml** dosyasını görüntüleme.

     ![Visual Studio kod düzenleyicisinde About.cshtml dosyasının ilk on Visual Studio gösteren ekran görüntüsü.](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. **About.cshtml.cs dosyasını** seçin.

     ![Kod düzenleyicisinde About.cshtml.cs Visual Studio seçin](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Kod **düzenleyicisinde About.cshtml.cs** dosyasını görüntüleme.

     ![Visual Studio kod düzenleyicisinde About.cshtml.cs dosyasının ilk 18 satırı gösteren ekran görüntüsü. ](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Proje, web sitenizin kökü olan bir **wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     ![Visual Studio'de Çözüm Gezgini wwwroot klasörü](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini doğrudan &mdash; &mdash; istediğiniz yollara koyabilirsiniz.

 1. Proje ayrıca çalışma zamanında web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *appsettings.json içinde depolanır.* Ancak, appsettings kullanarak bu ayarları *geçersiz kılabilirsiniz. Development.json*. **Appsettings.json dosyasını** genişletarak **appsettings dosyasını görüntüleyeceksiniz. Development.json** dosyası.

     ![Çözüm Gezgini Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. Uygulamayı **IIS Express** modunda derlemek ve çalıştırmak için IDE'de yeni uygulama düğmesini seçin. (Alternatif olarak **F5 tuşuna basın** veya Hata Ayıkla'ya **basın**  >  **Menü çubuğundan** Hata Ayıklamayı Başlat.)

     ![Dosyanın IIS Express düğmesini Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **'IIS Express' web** sunucusuna bağlanamıyor hata iletisi alırsanız, Visual Studio'yi kapatın ve ardından sağ tıklama  veya bağlam menüsünden Yönetici olarak çalıştır seçeneğini kullanarak açın. Ardından uygulamayı yeniden çalıştırın.
     >
     > Iis SSL Express sertifikasını kabul etmek istiyor sanız soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için Evet'i seçin ve ardından bir **güvenlik** uyarısı iletisi alırsanız Evet'i seçin.

1. Visual Studio tarayıcı penceresi açar. Ardından menü çubuğunda **Giriş**, **Hakkında** ve **Kişi** sayfalarını görüyorsanız. (Bunu yapmak zorunda değilsanız görüntülemek için "hamburger" menü öğesini seçin.)

    ![Web uygulamanıza menü çubuğundan "hamburger" menü öğesini seçin](media/csharp-aspnet-razor-browser-page.png)

1. Menü **çubuğundan** Hakkında'ya tıklayın.

   ![Uygulamanıza uygun tarayıcı penceresinin menü çubuğunda Hakkında'ya tıklayın](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Diğer şeylerin dışında, **tarayıcının** Hakkında sayfası *About.cshtml* dosyasında ayarlanmış olan metni işler.

   ![Hakkında sayfasındaki metni görüntüleme](media/csharp-aspnet-razor-browser-page-about.png)

1. Hata ayıklama Visual Studio geri dönüp **Shift+F5** tuşlarına basın. Bu, tarayıcı penceresinde projeyi de kapatır.

1. Aşağıdaki Visual Studio **About.cshtml dosyasını seçin.** Ardından başka bir sözcüğü _silin_ ve yerine file ve _directory sözcüklerini ekleyin._

    ![About.cshtml dosyasındaki metni değiştirme](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. **About.cshtml.cs dosyasını seçin.** Ardından, aşağıdaki `using` kısayolu kullanarak dosyanın üst kısmında yer alan yönergeleri temizleyin:

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

1. Ortam ve Dize altında iki dalgalı alt **çizgi görünür.**  Dalgalı alt çizgiler görünür çünkü bu türler kapsam içinde yer alan değil.

   ![OnGet yönteminde dalgalı alt çizgilerle işaretlenmiş hatalar](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Burada listelenen **hataları görmek** için Hata Listesi araç çubuğunu açın. (Hata Listesi araç çubuğunu **görmüyorsanız Görüntüle'yi** **seçin**  >  **Üst menü** çubuğundan Hata Listesi.)

   ![Visual Studio'de Hata Listesi](media/csharp-aspnet-razor-error-list.png)

1. Şimdi bu sorunu çözeceğiz. Kod düzenleyicisinde imlecinizi hatayı içeren herhangi bir satıra yerleştirerek sol kenar boşluğundaki Hızlı Eylemler ampulü seçin. Ardından, açılan menüden Sistem'i kullan'ı **seçin;** bu yönergeyi dosyanın en üstüne ekleyin ve hataları düzeltin.

   !["using System;" yönergesi ekleme](media/csharp-aspnet-razor-add-usings.png)

1. **Değişikliklerinizi kaydetmek için Ctrl** + **S** tuşlarına basın ve **ardından F5** tuşuna basarak projenizi web tarayıcısında açın.

1. Web sitesi üst kısmında, değişikliklerinizi görüntülemek **için Hakkında'ya** tıklayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Hakkında sayfasını görüntüleme](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Web tarayıcısını kapatın, **Hata Ayıklama modunu** durdurmak için Shift + **F5** tuşuna basın ve ardından Visual Studio.

::: moniker-end

::: moniker range="=vs-2019"

## <a name="tour-your-solution"></a>Çözümde tura çıkıyor

 1. Proje şablonu, _MyCoreApp_ adlı tek ASP.NET Core bir çözüm oluşturur. İçeriğini **Çözüm Gezgini** için sekmeyi seçin.

    !['MyCoreApp Çözüm Gezgini adlı Visual Studio projenin içeriğini gösteren ASP.NET ekran görüntüsü.](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Sayfalar **klasörünü** genişletin.

     !['MyCoreApp' Çözüm Gezgini Pages Visual Studio gösteren dosyanın ekran görüntüsü.](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Kod **düzenleyicisinde Index.cshtml** dosyasını görüntüleme.

     ![Dizin kodu düzenleyicisinde index.cshtml dosyasının Visual Studio ekran görüntüsü.](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Her .cshtml dosyasının ilişkili bir kod dosyası vardır. Kod dosyasını düzenleyicide açmak için, Çözüm Gezgini'de **Index.cshtml** düğümünü genişletin ve **Index.cshtml.cs dosyasını** seçin.

     ![Index.cshtml.cs Visual Studio seçilen dosyanın Çözüm Gezgini dosyanın ekran görüntüsü.](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Kod **düzenleyicisinde Index.cshtml.cs** dosyasını görüntüleme.

     ![Dizin kodu düzenleyicisinde index.cshtml.cs dosyasının Visual Studio ekran görüntüsü.](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Proje, web sitenizin kökü olan bir **wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     !['wwwroot' Çözüm Gezgini gösteren Visual Studio dosyanın ekran görüntüsü.](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini doğrudan &mdash; &mdash; istediğiniz yollara koyabilirsiniz.

 1. Proje ayrıca çalışma zamanında web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *appsettings.json içinde depolanır.* Ancak, appsettings kullanarak bu ayarları *geçersiz kılabilirsiniz. Development.json*. **Appsettings.json dosyasını** genişletarak **appsettings dosyasını görüntüleyeceksiniz. Development.json** dosyası.

     ![Appsettings.json Çözüm Gezgini Visual Studio appsettings.json dosyasını gösteren ve appsettings'i gösterecek şekilde genişletilen dosyanın ekran görüntüsü. Development.json dosyası.](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. Uygulamayı **IIS Express** modunda derlemek ve çalıştırmak için IDE'de yeni uygulama düğmesini seçin. (Alternatif olarak **F5 tuşuna basın** veya Hata Ayıkla'ya **basın**  >  **Menü çubuğundan** Hata Ayıklamayı Başlat.)

     ![IIS Express IDE'de vurgulanmış olan Visual Studio ekran görüntüsü.](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **'IIS Express' web** sunucusuna bağlanamıyor hata iletisi alırsanız, Visual Studio'yi kapatın ve ardından sağ tıklama  veya bağlam menüsünden Yönetici olarak çalıştır seçeneğini kullanarak açın. Ardından uygulamayı yeniden çalıştırın.
     >
     > Iis SSL Express sertifikasını kabul etmek istiyor sanız soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için Evet'i seçin ve ardından bir **güvenlik** uyarısı iletisi alırsanız Evet'i seçin.

1. Visual Studio tarayıcı penceresi açar. Ardından menü çubuğunda **Giriş** ve **Gizlilik** sayfalarını görüyorsanız.

1. Menü **çubuğundan** Gizlilik'i seçin.

   **Tarayıcının** Gizlilik sayfası, *Privacy.cshtml* dosyasında ayarlanmış olan metni işler.

   !['Bu sayfayı, sitenizin gizlilik ilkesinde ayrıntıya yer almak için kullan' metniyle Birlikte MyCoreApp Gizlilik sayfasını gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Hata ayıklama Visual Studio geri dönüp **Shift+F5** tuşlarına basın. Bu, tarayıcı penceresinde projeyi de kapatır.

1. Bu Visual Studio **privacy.cshtml dosyasını düzenlemek için** açın. Ardından Bu sayfayı kullanın sözcüklerini silin _ve sitenin_ gizlilik ilkesine ayrıntı ekleyin ve _@ViewData ["TimeStamp"]_ ile bu sayfa inşa aşamasındadır sözcüklerini ekleyin.

    ![Güncelleştirilmiş metinle birlikte Visual Studio Code Düzenleyicisi'nde privacy.cshtml dosyasının açık olduğunu gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Şimdi bir kod değişikliğine bakalım. **Privacy.cshtml.cs dosyasını seçin.** Ardından, aşağıdaki `using` kısayolu kullanarak dosyanın üst kısmında yer alan yönergeleri temizleyin:

   Gri renkli yönergelerden birini seçin; bir Hızlı Eylemler ampulü, sağ altta veya sol kenar `using` boşluğunda görünür. [](../../ide/quick-actions.md) Ampulü seçin ve gereksiz kullanmaları **kaldır'ın üzerine gelin.**

   !['Gereksiz Kullanımı Kaldır' iletişim kutusunun açık olduğu Visual Studio düzenleyicisinde Privacy.cshtml dosyasını gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Şimdi değişiklikleri **görmek için** Değişiklikleri önizle'yi seçin.

   ![Yeni 'Usings' listesini ve Privacy.cshtml dosyasındaki kodu gösteren Önizleme Değişiklikleri iletişim kutusunu gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-preview-changes.png)

   **Uygula**'yı seçin. Visual Studio gereksiz yönergeleri `using` dosyadan siler.

1. Ardından `OnGet()` yönteminde gövdeyi aşağıdaki kodla değiştirebilirsiniz:

     ```csharp
     public void OnGet()
     {
        string dateTime = DateTime.Now.ToShortDateString();
        ViewData["TimeStamp"] = dateTime;
     }
    ```

1. DateTime altında iki dalgalı alt çizginin **görünür.** Bu tür kapsamda yer çalışmay olduğundan dalgalı alt çizgiler görünür.

   ![OnGet yönteminde dalgalı alt çizgilerle işaretlenmiş hataları gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Burada listelenen **hataları görmek** için Hata Listesi araç çubuğunu açın. (Hata Listesi araç çubuğunu **görmüyorsanız Görüntüle'yi** **seçin**  >  **Üst menü** çubuğundan Hata Listesi.)

   ![Visual Studio'da Hata Listesi](media/vs-2019/csharp-aspnet-error-list.png)

1. Şimdi bu sorunu çözeceğiz. Kod düzenleyicisinde imlecinizi hatayı içeren herhangi bir satıra yerleştirerek sol kenar boşluğundaki Hızlı Eylemler ampulü seçin. Ardından, açılan menüden Sistem'i kullan'ı **seçin;** bu yönergeyi dosyanın en üstüne ekleyin ve hataları düzeltin.

   !['Using System' yönergesini ekleme önerisini gösteren Hızlı Eylemler menüsünü gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-add-usings.png)

1. Projenizi web tarayıcısında açmak için **F5** tuşuna basın.

1. Yaptığınız değişiklikleri görüntülemek için web sitesi üst **kısmında Gizlilik'i** seçin.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Gizlilik sayfasını gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Web tarayıcısını kapatın, **Shift** + **F5 tuşuna** basarak Hata Ayıklama modunu durdurun ve ardından Visual Studio.
::: moniker-end

::: moniker range=">=vs-2022"

## <a name="tour-your-solution"></a>Çözümde tura çıkıyor

 1. Proje şablonu, *MyCoreApp* adlı tek ASP.NET Core bir çözüm oluşturur. İçeriğini **görüntülemek Çözüm Gezgini** sekmeyi seçin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-mycoreapp.png" alt-text="'MyCoreApp Çözüm Gezgini adlı Visual Studio projenin içeriğini gösteren ASP.NET ekran görüntüsü.":::

 1. Sayfalar **klasörünü** genişletin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-solution-explorer-pages.png" alt-text="'MyCoreApp' Çözüm Gezgini Pages Visual Studio gösteren dosyanın ekran görüntüsü.":::

 1. Kod **düzenleyicisinde Index.cshtml** dosyasını görüntüleme.

     :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml.png" alt-text="Dizin kodu düzenleyicisinde index.cshtml dosyasının Visual Studio ekran görüntüsü.":::

 1. Her .cshtml dosyasının ilişkili bir kod dosyası vardır. Kod dosyasını düzenleyicide açmak için, Çözüm Gezgini'de **Index.cshtml** düğümünü genişletin ve **Index.cshtml.cs dosyasını** seçin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-choose-index-cshtml.png" alt-text="Index.cshtml.cs Visual Studio seçilen dosyanın Çözüm Gezgini dosyanın ekran görüntüsü.":::

 1. Kod **düzenleyicisinde Index.cshtml.cs** dosyasını görüntüleme.

     :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml-editing.png" alt-text="Dizin kodu düzenleyicisinde index.cshtml.cs dosyasının Visual Studio ekran görüntüsü.":::

 1. Proje, web sitenizin kökü olan bir **wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-wwwroot.png" alt-text="'wwwroot' Çözüm Gezgini gösteren Visual Studio dosyanın ekran görüntüsü.":::

    CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini doğrudan &mdash; &mdash; istediğiniz yollara koyabilirsiniz.

 1. Proje ayrıca çalışma zamanında web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *appsettings.json içinde depolanır.* Ancak, appsettings kullanarak bu ayarları *geçersiz kılabilirsiniz. Development.json*. **Appsettings.json dosyasını** genişletarak **appsettings dosyasını görüntüleyeceksiniz. Development.json** dosyası.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-appsettingsjson.png" alt-text="Appsettings.json Çözüm Gezgini Visual Studio appsettings.json dosyasını gösteren ve appsettings'i gösterecek şekilde genişletilen dosyanın ekran görüntüsü. Development.json dosyası.":::

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. Uygulamayı **IIS Express** modunda derlemek ve çalıştırmak için IDE'de IIS Express düğmesini seçin. (Alternatif olarak **F5 tuşuna basın** veya Hata Ayıkla'ya **basın**  >  **Menü çubuğundan** Hata Ayıklamayı Başlat.)

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-iisexpress.png" alt-text="Visual Studio IDE'de vurgulanmış olan IIS Express gösteren ekran görüntüsü.":::

     > [!NOTE]
     > **'IIS Express' web** sunucusuna bağlanamıyor hatası alırsanız, Visual Studio'ı kapatın ve ardından sağ tıklama veya  bağlam menüsünden Yönetici olarak çalıştır seçeneğini kullanarak açın. Ardından uygulamayı yeniden çalıştırın.
     >
     > Iis SSL Express sertifikasını kabul etmek istiyor sanız soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için Evet'i seçin ve ardından bir **güvenlik** uyarısı iletisi alırsanız Evet'i seçin.

1. Visual Studio tarayıcı penceresi açar. Ardından menü çubuğunda **Giriş** ve **Gizlilik** sayfalarını görüyorsanız.

1. Menü **çubuğundan** Gizlilik'i seçin.

   **Tarayıcının** Gizlilik sayfası, *Privacy.cshtml* dosyasında ayarlanmış olan metni işler.

   :::image type="content" source="media/vs-2022/csharp-aspnet-browser-page-privacy.png" alt-text="'Bu sayfayı, sitenizin gizlilik ilkesinde ayrıntıya yer almak için kullan' metniyle Birlikte MyCoreApp Gizlilik sayfasını gösteren ekran görüntüsü.":::

1. Hata ayıklama Visual Studio geri dönüp **Shift+F5** tuşlarına basın. Bu, tarayıcı penceresinde projeyi de kapatır.

1. Bu Visual Studio **privacy.cshtml dosyasını düzenlemek için** açın. Ardından Bu sayfayı kullanın sözcüklerini silin *ve sitenin* gizlilik ilkesine ayrıntı ekleyin ve *@ViewData ["TimeStamp"]* ile bu sayfa inşa aşamasındadır sözcüklerini ekleyin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-privacy-cshtml-code-changed.png" alt-text="Güncelleştirilmiş metinle birlikte Visual Studio Privacy.cshtml dosyasının açık olduğunu gösteren ekran görüntüsü.":::

1. Şimdi bir kod değişikliğine bakalım. **Privacy.cshtml.cs dosyasını seçin.** Ardından, aşağıdaki `using` kısayolu seçerek dosyanın en üstünde yer alan yönergeleri temizleyin:

   Gri renkli yönergelerden birini seçin; bir Hızlı Eylemler ampulü, sağ altta veya sol kenar `using` boşluğunda görünür. [](../../ide/quick-actions.md) Ampulü seçin ve gereksiz kullanmaları **kaldır'ın üzerine gelin.**

   :::image type="content" source="media/vs-2022/csharp-aspnet-remove-unnecessary-usings.png" alt-text="'Gereksiz Kullanımı Kaldır' iletişim kutusunun açık olduğu Visual Studio düzenleyicisinde Privacy.cshtml dosyasını gösteren ekran görüntüsü.":::

   Şimdi değişiklikleri **görmek için** Değişiklikleri önizle'yi seçin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-preview-changes.png" alt-text="Yeni 'Usings' listesini ve Privacy.cshtml dosyasındaki kodu gösteren Önizleme Değişiklikleri iletişim kutusunu gösteren ekran görüntüsü.":::

   **Uygula**'yı seçin. Visual Studio gereksiz yönergeleri `using` dosyadan siler.

1. Ardından, [DateTime.ToString](xref:System.DateTime.ToString%2A) yöntemini kullanarak kültürüz veya bölgeniz için biçimlendirilmiş geçerli tarih için bir dize oluşturun.

   - yöntemi için ilk bağımsız değişken tarihin nasıl görüntü olacağını belirtir. Bu örnek, kısa tarih biçimini gösteren biçim belirleyicisi ( `d` ) kullanır. 
   - İkinci bağımsız değişken, tarihin kültürünü veya bölgelerini belirten [CultureInfo](/dotnet/api/system.globalization.cultureinfo) nesnesidir. Bu bağımsız değişken, diğer şeylerin dışında tarihe geçen sözcüklerin dilini ve kullanılan ayırıcıların türünü belirler.
 
yönteminin gövdesini `OnGet()` aşağıdaki kodla değiştirebilirsiniz:

   ```csharp
   public void OnGet()
   {
      string dateTime = DateTime.Now.ToString("d", new CultureInfo("en-US"));
      ViewData["TimeStamp"] = dateTime;
   }
   ```

1. CultureInfo altında iki dalgalı alt çizginin **görünür.** Bu tür kapsamda yer çalışmay olduğundan dalgalı alt çizgiler görünür.

   :::image type="content" source="media/vs-2022/csharp-aspnet-add-new-onget-method.png" alt-text="CultureInfo nesnesinin altında dalgalı alt çizgiyle kod düzenleyicisinde OnGet yöntemini gösteren ekran görüntüsü.":::

    Burada listelenen **hataları görmek** için Hata Listesi araç çubuğunu açın. (Hata Listesi araç çubuğunu **görmüyorsanız Görüntüle'yi** **seçin**  >  **Üst menü** çubuğundan Hata Listesi.)

   :::image type="content" source="media/vs-2022/csharp-aspnet-error-list.png" alt-text="Hata Listesi penceresini gösteren ekran görüntüsü Visual Studio. 'CultureInfo' türünde bir using yönergesi eksik.":::

1. Şimdi bu sorunu çözeceğiz. Kod düzenleyicisinde imlecinizi hatayı içeren herhangi bir satıra yerleştirerek sol kenar boşluğundaki Hızlı Eylemler ampulü seçin. Ardından, açılır menüden **System. Globalization komutunu kullanarak** yönergeyi dosyanızın en üstüne ekleyin ve hataları çözün.

   :::image type="content" source="media/vs-2022/csharp-aspnet-add-usings.png" alt-text="' Using System. Globalization ' yönergesini ekleme önerisinde bulunan Hızlı Eylemler menüsünü gösteren ekran görüntüsü.":::

1. **F5** tuşuna basarak projenizi web tarayıcısında açın.

1. Değişikliklerinizi görüntülemek için Web sitesinin en üstünde **Gizlilik** ' i seçin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-browser-page-privacy-changed.png" alt-text="Tarihi eklemek için yapılan değişiklikleri içeren MyCoreApp gizlilik sayfasını gösteren ekran görüntüsü.":::

1. web tarayıcısını kapatın, **shıft** + **F5** tuşlarına basarak hata ayıklama modunu durdurun ve ardından Visual Studio kapatın.

::: moniker-end

## <a name="quick-answers-faq"></a>Hızlı yanıtlar SSS

İşte bazı temel kavramları vurgulamak için hızlı bir SSS.

### <a name="what-is-c"></a>C# nedir?

[C#](/dotnet/csharp/tour-of-csharp/) , hem dayanıklı hem de kolay öğrenilmesi için tasarlanan tür açısından güvenli ve nesne odaklı bir programlama dilidir.

### <a name="what-is-aspnet-core"></a>ASP.NET Core nedir?

ASP.NET Core, web uygulamaları ve hizmetleri gibi ınternet 'e bağlı uygulamalar oluşturmaya yönelik açık kaynaklı ve platformlar arası bir çerçevedir. ASP.NET Core uygulamalar, .net Core veya .NET Framework üzerinde çalışabilir. Windows, Mac ve Linux 'ta ASP.NET Core uygulamalarınızı platformlar arası geliştirebilir ve çalıştırabilirsiniz. ASP.NET Core [GitHub](https://github.com/aspnet/home)açık kaynaktır.

### <a name="what-is-visual-studio"></a>Visual Studio nedir?

Visual Studio, geliştiriciler için tümleşik bir üretkenlik araçları paketidir. Program ve uygulamalar oluşturmak için kullanabileceğiniz bir program olarak düşünün.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamlama! C#, ASP.NET Core ve Visual Studio ıde hakkında biraz bilgi edindiniz. C# ve ASP.NET bir web uygulaması veya web sitesi oluşturma hakkında daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [ASP.NET Core ile Razor Pages Web uygulaması oluşturma](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)

Ya da, Docker ile Web uygulamanızı kapsayıya nasıl kapsayıleyeceğinizi öğrenin:

> [!div class="nextstepaction"]
> [Visual Studio kapsayıcı araçları](../../containers/overview.md)

## <a name="see-also"></a>Ayrıca bkz.

[Web uygulamanızı Visual Studio kullanarak Azure App Service yayımlayın](../../deployment/quickstart-deploy-to-azure.md)
