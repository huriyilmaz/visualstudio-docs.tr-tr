---
title: 'Öğretici: C# ve ASP.NET Core kullanmaya başlama'
titleSuffix: ''
description: C# ile Visual Studio bir ASP.NET Core web uygulamasının nasıl oluşturulacağını öğrenin ve adım adım.
ms.custom: vs-acquisition, get-started
ms.date: 06/12/2021
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
ms.openlocfilehash: e744ef4ed6888673e6e412a197f6f941c0d0ae80
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2021
ms.locfileid: "122981053"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>öğretici: Visual Studio ' de C# ve ASP.NET Core kullanmaya başlama

Visual Studio kullanarak c# ASP.NET Core geliştirme için bu öğreticide, bir c# ASP.NET Core web uygulaması oluşturacaksınız, bu uygulamada değişiklikler yapmanız, ıde 'nin bazı özelliklerini araştırıp ve ardından uygulamayı çalıştırmanız gerekir.

## <a name="prerequisites"></a>Önkoşullar

1. Visual Studio'yu yükleme
   ::: moniker range="vs-2017"
   
   Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.
   
   ::: moniker-end
   
   ::: moniker range="vs-2019"
   
   Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.
   
   ::: moniker-end

   ::: moniker range="vs-2022"

   henüz 2022 önizleme Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio 2022 önizleme indirmeleri](https://visualstudio.microsoft.com/vs/preview/vs2022) sayfasına gidin.

   ::: moniker-end

1. güncelleştirme Visual Studio-Visual Studio zaten yüklediyseniz en son sürümü çalıştırdığınızdan emin olun. yüklemenizi güncelleştirme hakkında daha fazla bilgi için [güncelleştirme Visual Studio en son sürüm](../../install/update-visual-studio.md) sayfasına bakın.

1. Temanızı seçin (isteğe bağlı)-Bu öğretici, koyu temayı kullanan ekran görüntülerini içerir. [Visual Studio ıde ve düzenleyici sayfasını kişiselleştirerek](../../ide/quickstart-personalize-the-ide.md) nasıl yapılacağını öğrenebilirsiniz.

## <a name="create-a-project"></a>Proje oluşturma

ilk olarak, bir ASP.NET Core projesi oluşturacaksınız. Proje türü, tam olarak işlevsel bir Web sitesi için ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklenmeyecektir.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

3. sol bölmedeki **yeni Project** iletişim kutusunda, **Visual C#**' ı genişletin, **Web**' i genişletin ve ardından **.net Core**' u seçin. orta bölmede **ASP.NET Core Web uygulaması**' nı seçin. Ardından, dosyayı *Mycoreapp* olarak adlandırın ve **Tamam**' ı seçin.

   ![ASP.NET Core Visual Studio ıde 'deki yeni Project iletişim kutusunda Web uygulaması proje şablonu](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>İş yükü ekleme (isteğe bağlı)

**ASP.NET Core web uygulaması** proje şablonunu görmüyorsanız, **ASP.NET ve web geliştirme** iş yükünü ekleyerek alabilirsiniz. makinenizde hangi Visual Studio 2017 güncelleştirmelerinin yüklü olduğuna bağlı olarak, bu iş yükünü aşağıdaki iki yönden birine ekleyebilirsiniz.

#### <a name="option-1-use-the-new-project-dialog-box"></a>seçenek 1: yeni Project iletişim kutusunu kullanma

1. **yeni Project** iletişim kutusunun sol bölmesindeki **Visual Studio Yükleyicisi aç** bağlantısını seçin. (Görüntü ayarlarınıza bağlı olarak, görmek için kaydırmanız gerekebilir.)

   ![yeni Project iletişim kutusundan Visual Studio Yükleyicisi aç bağlantısını seçin](../media/open-visual-studio-installer-mycoreapp.png)

1. Visual Studio Yükleyicisi başlatılır. **ASP.NET ve web geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.

   ![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükü](../media/tutorial-aspnet-workload.png)

   (yeni iş yükünü yüklemeye devam edebilmeniz için önce Visual Studio kapatmanız gerekebilir.)

#### <a name="option-2-use-the-tools-menu-bar"></a>2. seçenek: Araçlar menü çubuğunu kullanma

1. **yeni Project** iletişim kutusunu iptal edin. Ardından, üstteki menü çubuğunda **Araçlar**  >  **ve Özellikler al**' ı seçin.

1. Visual Studio Yükleyicisi başlatılır. **ASP.NET ve web geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.

   (yeni iş yükünü yüklemeye devam edebilmeniz için önce Visual Studio kapatmanız gerekebilir.)

### <a name="add-a-project-template"></a>Proje şablonu ekleme

1. **yeni ASP.NET Core web uygulaması** iletişim kutusunda **web uygulaması** proje şablonunu seçin.

1. **ASP.NET Core 2,1** ' nin üst açılan menüde göründüğünü doğrulayın. Ardından **Tamam**' ı seçin.

   ![yeni ASP.NET Core Web uygulaması iletişim kutusu](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > üst açılan menüden **ASP.NET Core 2,1** ' u görmüyorsanız, en son Visual Studio sürümünü çalıştırdığınızdan emin olun. yüklemenizi güncelleştirme hakkında daha fazla bilgi için [güncelleştirme Visual Studio en son sürüm](../../install/update-visual-studio.md) sayfasına bakın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   :::image type="content" source="../../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="' Yeni proje oluştur ' penceresini görüntüleyin":::

1. **Yeni proje oluştur** penceresinde dil listesinden **C#** ' ı seçin. ardından, Platform listesinden **Windows** ve proje türleri listesinden **Web** ' i seçin.

      dili, platformu ve proje türü filtrelerini uyguladıktan sonra, **ASP.NET Core Web uygulaması** şablonunu seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="./media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="ASP.NET Core Web uygulaması için C# şablonunu seçin":::

   > [!NOTE]
   > **ASP.NET Core Web uygulaması** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > ardından, Visual Studio Yükleyicisi **ASP.NET ve web geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükü](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenirse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *mycoreapp* yazın veya girin. Ardından **İleri**' yi seçin.

   :::image type="content" source="./media/vs-2019/csharp-name-your-aspnet-app.png" alt-text="' yeni projenizi yapılandırın ' penceresinde, ' MyCoreApp ' projenizi adlandırın":::

1. **Ek bilgi** penceresinde, **.NET Core 3,1** ' ın üst açılan menüde göründüğünü doğrulayın. Kutuyu işaretleyerek Docker desteğini etkinleştirmeyi seçebileceğinizi unutmayın. Kimlik doğrulamasını Değiştir düğmesine tıklayarak da kimlik doğrulama desteği ekleyebilirsiniz. Buradan buradan seçim yapabilirsiniz:
    - Hiçbiri: kimlik doğrulaması yok.
    - Bireysel hesaplar: Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: bu seçenek, kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygun.
    
    **Docker 'ı etkinleştir** kutusunu işaretsiz bırakın ve kimlik doğrulama türü için **hiçbiri** ' ni seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="./media/vs-2019/aspnet-core-additional-information.png" alt-text="' ek bilgi ' penceresinde, .NET Core 3,1 ' in seçildiğinden emin olun ve tüm varsayılanları bırakın":::

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

 1. Proje, çalışma zamanında Web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *üzerindeappsettings.js* depolanır. Ancak, *üzerindeappsettings.Development.js* kullanarak bu ayarları geçersiz kılabilirsiniz. Dosyadaki **appsettings.Development.js** görüntülemek için **appsettings.jsdosya '** yı genişletin.

     ![Visual Studio Çözüm Gezgini yapılandırma dosyaları](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. Uygulamayı **IIS Express** modunda derlemek ve çalıştırmak için IDE'de IIS Express düğmesini seçin. (Alternatif olarak **F5 tuşuna basın** veya Hata Ayıkla'ya **basın**  >  **Menü çubuğundan** Hata Ayıklamayı Başlat.)

     ![Dosyanın IIS Express düğmesini Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **'IIS Express' web** sunucusuna bağlanamıyor hata iletisi alırsanız, Visual Studio'ı kapatın ve ardından sağ tıklama  veya bağlam menüsünden Yönetici olarak çalıştır seçeneğini kullanarak açın. Ardından uygulamayı yeniden çalıştırın.
     >
     > Iis SSL Express sertifikasını kabul etmek istiyor sanız soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için Evet'i seçin ve ardından bir **güvenlik** uyarısı iletisi alırsanız Evet'i seçin.

1. Visual Studio tarayıcı penceresi açar. Ardından menü çubuğunda **Giriş**, **Hakkında** ve **Kişi** sayfalarını görüyorsanız. (Bunu yapmak zorunda değilsanız görüntülemek için "hamburger" menü öğesini seçin.)

    ![Web uygulamanıza menü çubuğundan "hamburger" menü öğesini seçin](media/csharp-aspnet-razor-browser-page.png)

1. Menü **çubuğundan** Hakkında'ya tıklayın.

   ![Uygulamanıza uygun tarayıcı penceresinin menü çubuğunda Hakkında'ya tıklayın](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Diğer şeylerin dışında, **tarayıcının** Hakkında sayfası *About.cshtml* dosyasında ayarlanmış olan metni işler.

   ![Hakkında sayfasındaki metni görüntüleme](media/csharp-aspnet-razor-browser-page-about.png)

1. Hata ayıklama Visual Studio geri dönüp **Shift+F5** tuşlarına basın. Bu, tarayıcı penceresinde projeyi de kapatır.

1. Aşağıdaki Visual Studio **About.cshtml dosyasını seçin.** Ardından additional sözcüğüne _ve_ yerine file ve _directory sözcüklerini ekleyin._

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

1. Web tarayıcısını kapatın, **Shift** + **F5 tuşuna** basarak Hata Ayıklama modunu durdurun ve ardından Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>Çözümde tura çıkıyor

 1. Proje şablonu, _MyCoreApp_ adlı tek ASP.NET Core bir çözüm oluşturur. İçeriğini **görüntülemek Çözüm Gezgini** sekmeyi seçin.

    ![ASP.NET Çözüm Gezgini MyCoreApp Visual Studio Razor Pages çözüm için Razor Pages'de](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Sayfalar **klasörünü** genişletin.

     ![Çözüm Gezgini'daki Sayfalar klasörü](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Kod **düzenleyicisinde Index.cshtml** dosyasını görüntüleme.

     ![Index.cshtml dosyasını kod düzenleyicisinde Visual Studio görüntüleme](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Her .cshtml dosyasının ilişkili bir kod dosyası vardır. Kod dosyasını düzenleyicide açmak için, Çözüm Gezgini'de **Index.cshtml** düğümünü genişletin ve **Index.cshtml.cs dosyasını** seçin.

     ![Kod düzenleyicisinde Index.cshtml.cs Visual Studio seçin](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Kod **düzenleyicisinde Index.cshtml.cs** dosyasını görüntüleme.

     ![About.cshtml dosyasını kod düzenleyicisinde Visual Studio görüntüleme](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Proje, web sitenizin kökü olan bir **wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     ![Visual Studio'daki Çözüm Gezgini wwwroot Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini doğrudan &mdash; &mdash; istediğiniz yollara koyabilirsiniz.

 1. Proje ayrıca çalışma zamanında web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması,](/aspnet/core/fundamentals/configuration) üzerinde *appsettings.jsdepolanır.* Ancak, üzerinde bir uygulama kullanarak buappsettings.Development.js *geçersiz kılabilirsiniz.* Dosyanın **appsettings.jsdosyasını** görüntülemek için **appsettings.Development.jsgenişletin.**

     ![Çözüm Gezgini Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. Uygulamayı **IIS Express** modunda derlemek ve çalıştırmak için IDE'de IIS Express düğmesini seçin. (Alternatif olarak **F5 tuşuna basın** veya Hata Ayıkla'ya **basın**  >  **Menü çubuğundan** Hata Ayıklamayı Başlat.)

     ![Dosyanın IIS Express düğmesini Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **'IIS Express' web** sunucusuna bağlanamıyor hata iletisi alırsanız, Visual Studio'ı kapatın ve ardından sağ tıklama  veya bağlam menüsünden Yönetici olarak çalıştır seçeneğini kullanarak açın. Ardından uygulamayı yeniden çalıştırın.
     >
     > Iis SSL Express sertifikasını kabul etmek istiyor sanız soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için Evet'i seçin ve ardından bir **güvenlik** uyarısı iletisi alırsanız Evet'i seçin.

1. Visual Studio tarayıcı penceresi açar. Ardından menü çubuğunda **Giriş** ve **Gizlilik** sayfalarını görüyorsanız.

1. Menü **çubuğundan** Gizlilik'i seçin.

   **Tarayıcının** Gizlilik sayfası, *Privacy.cshtml* dosyasında ayarlanmış olan metni işler.

   ![Gizlilik sayfasında metni görüntüleme](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Hata ayıklama Visual Studio geri dönüp **Shift+F5** tuşlarına basın. Bu, tarayıcı penceresinde projeyi de kapatır.

1. Bu Visual Studio **privacy.cshtml dosyasını düzenlemek** için açın. Ardından Bu sayfayı kullanın sözcüklerini silin _ve sitenin_ gizlilik ilkesine ayrıntı ekleyin ve _@ViewData ["TimeStamp"]_ ile bu sayfa inşa aşamasındadır sözcüklerini ekleyin.

    ![Privacy.cshtml dosyasındaki metni değiştirme](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Şimdi bir kod değişikliğine bakalım. **Privacy.cshtml.cs dosyasını seçin.** Ardından, aşağıdaki `using` kısayolu kullanarak dosyanın üst kısmında yer alan yönergeleri temizleyin:

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

1. Şimdi bu sorunu çözeceğiz. Kod düzenleyicisinde imlecinizi hatayı içeren herhangi bir satıra yerleştirerek sol kenar boşluğundaki Hızlı Eylemler ampulü seçin. Ardından, açılan menüden Sistem'i kullan'ı **seçin;** bu yönergeyi dosyanın en üstüne ekleyin ve hataları düzeltin.

   !["using System;" yönergesi ekleme](media/vs-2019/csharp-aspnet-add-usings.png)

1. Projenizi web tarayıcısında açmak için **F5** tuşuna basın.

1. Yaptığınız değişiklikleri görüntülemek için web sitesi üst **kısmında Gizlilik'i** seçin.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Gizlilik sayfasını görüntüleme](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Web tarayıcısını kapatın, **Shift** + **F5 tuşuna** basarak Hata Ayıklama modunu durdurun ve ardından Visual Studio.
::: moniker-end

## <a name="quick-answers-faq"></a>Hızlı yanıtlar hakkında SSS

Bazı temel kavramları vurgulamak için burada hızlı bir SSS bulabilirsiniz.

### <a name="what-is-c"></a>C# nedir?

[C#](/dotnet/csharp/tour-of-csharp/) hem sağlam hem de öğrenmesi kolay olacak şekilde tasarlanmış tür kullanımı güvenli ve nesne odaklı bir programlama dilidir.

### <a name="what-is-aspnet-core"></a>ASP.NET Core nedir?

ASP.NET Core, web uygulamaları ve hizmetleri gibi İnternet'e bağlı uygulamalar için açık kaynak ve platformlar arası bir çerçevedir. ASP.NET Core uygulamaları .NET Core veya .NET Framework. ASP.NET Core, Mac ve Linux'ta platformlar arası Windows geliştirebilir ve çalıştırabilirsiniz. ASP.NET Core açık kaynaktır ve [GitHub.](https://github.com/aspnet/home)

### <a name="what-is-visual-studio"></a>Hangi Visual Studio?

Visual Studio, geliştiriciler için tümleşik bir üretkenlik araçları geliştirme paketidir. Bunu program ve uygulama oluşturmak için kullanabileceğiniz bir program olarak düşün.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamladıktan sonra! C#, ASP.NET Core ve Visual Studio IDE hakkında bilgi Visual Studio umuyoruz. C# ve ASP.NET ile web uygulaması veya web sitesi oluşturma hakkında daha fazla ASP.NET aşağıdaki öğreticilerle devam edin:

> [!div class="nextstepaction"]
> [ASP.NET Core Razor Pages web uygulaması oluşturma](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio kullanarak web Azure App Service yayımlama](../../deployment/quickstart-deploy-to-azure.md)
