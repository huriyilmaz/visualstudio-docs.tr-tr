---
title: 'Öğretici: C# ve ASP.NET Core kullanmaya başlama'
titleSuffix: ''
description: C# ile Visual Studio bir ASP.NET Core web uygulamasının nasıl oluşturulacağını öğrenin ve adım adım.
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
ms.openlocfilehash: 497012d04d0015d5b2006670475875240a6f5e83
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453781"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>öğretici: Visual Studio ' de C# ve ASP.NET Core kullanmaya başlama

Visual Studio kullanarak c# ASP.NET Core geliştirme için bu öğreticide, bir c# ASP.NET Core web uygulaması oluşturacaksınız, bu uygulamada değişiklikler yapmanız, ıde 'nin bazı özelliklerini araştırıp ve ardından uygulamayı çalıştırmanız gerekir.

## <a name="prerequisites"></a>Önkoşullar

1. Visual Studio'yu yükleme
   ::: moniker range="vs-2017"
   
   Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.
   
   ::: moniker-end
   
   ::: moniker range=">=vs-2019"
   
   Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.
   
   ::: moniker-end

1. güncelleştirme Visual Studio-Visual Studio zaten yüklediyseniz en son sürümü çalıştırdığınızdan emin olun. yüklemenizi güncelleştirme hakkında daha fazla bilgi için [güncelleştirme Visual Studio en son sürüm](../../install/update-visual-studio.md) sayfasına bakın.

1. Temanızı seçin (isteğe bağlı)-Bu öğretici, koyu temayı kullanan ekran görüntülerini içerir. [Visual Studio ıde ve düzenleyici sayfasını kişiselleştirerek](../../ide/quickstart-personalize-the-ide.md) nasıl yapılacağını öğrenebilirsiniz.

## <a name="create-a-project"></a>Proje oluşturma

ilk olarak, bir ASP.NET Core projesi oluşturacaksınız. Proje türü, tam olarak işlevsel bir Web sitesi için ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklenmeyecektir.

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

2. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

3. sol bölmedeki **yeni Project** iletişim kutusunda, **Visual C#**' ı genişletin, **Web**' i genişletin ve ardından **.net Core**' u seçin. orta bölmede **ASP.NET Core Web uygulaması**' nı seçin. Ardından, dosyayı *Mycoreapp* olarak adlandırın ve **Tamam**' ı seçin.

   ![Visual Studio ıde 'deki yeni Project iletişim kutusunda Web uygulaması proje şablonu ASP.NET Core](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

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

::: moniker range="vs-2019"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   :::image type="content" source="../../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="' yeni proje oluştur ' seçeneğinin vurgulandığı Visual Studio başlangıç penceresini gösteren ekran görüntüsü.":::

1. **Yeni proje oluştur** penceresinde dil listesinden **C#** ' ı seçin. ardından, Platform listesinden **Windows** ve proje türleri listesinden **Web** ' i seçin.

      dili, platformu ve proje türü filtrelerini uyguladıktan sonra, **ASP.NET Core Web uygulaması** şablonunu seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="./media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="yeni Project iletişim kutusunda vurgulanan ASP.NET Core Web uygulaması proje şablonunu gösteren ekran görüntüsü.":::

   > [!NOTE]
   > **ASP.NET Core Web uygulaması** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > !["Aradığınızı bulma" iletisinin bir parçası olan ' daha fazla araç ve özellik yüklemesi ' bağlantısını gösteren ekran görüntüsü.](../../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > ardından, Visual Studio Yükleyicisi **ASP.NET ve web geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükünü gösteren ekran görüntüsü.](../../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenirse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *mycoreapp* yazın veya girin. Ardından **İleri**' yi seçin.

   :::image type="content" source="./media/vs-2019/csharp-name-your-aspnet-app.png" alt-text="Project adı alanına ' mycoreapp ' ile ' yeni projeyi yapılandır ' penceresini gösteren ekran görüntüsü.":::

1. **Ek bilgi** penceresinde, **.NET Core 3,1** ' ın üst açılan menüde göründüğünü doğrulayın. Kutuyu işaretleyerek Docker desteğini etkinleştirmeyi seçebileceğinizi unutmayın. Kimlik doğrulamasını Değiştir düğmesine tıklayarak da kimlik doğrulama desteği ekleyebilirsiniz. Buradan buradan seçim yapabilirsiniz:
    - Hiçbiri: kimlik doğrulaması yok.
    - Bireysel hesaplar: Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: bu seçenek, kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygun.
    
    **Docker 'ı etkinleştir** kutusunu işaretsiz bırakın ve kimlik doğrulama türü için **hiçbiri** ' ni seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="./media/vs-2019/aspnet-core-additional-information.png" alt-text="' Ek bilgi ' penceresindeki varsayılan ayarları gösteren ekran görüntüsü. Framework değeri ' .NET Core 3,1 '.":::

   Visual Studio, yeni projenizi açacak.

::: moniker-end

::: moniker range=">=vs-2022"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="' yeni proje oluştur ' seçeneğinin vurgulandığı Visual Studio başlangıç penceresini gösteren ekran görüntüsü.":::

1. **Yeni proje oluştur** penceresinde dil listesinden **C#** ' ı seçin. ardından, Platform listesinden **Windows** ve proje türleri listesinden **Web** ' i seçin.

      dili, platformu ve proje türü filtrelerini uyguladıktan sonra, **ASP.NET Core Web uygulaması** şablonunu seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="media/vs-2022/csharp-create-new-project-aspnet-core.png" alt-text="yeni Project iletişim kutusunda vurgulanan ASP.NET Core Web uygulaması proje şablonunu gösteren ekran görüntüsü.":::

   > [!NOTE]
   > **ASP.NET Core Web uygulaması** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > :::image type="content" source="media/vs-2022/not-finding-what-looking-for.png" alt-text="&quot;Aradığınızı bulma&quot; iletisinin bir parçası olan ' daha fazla araç ve özellik yüklemesi ' bağlantısını gösteren ekran görüntüsü.":::
   >
   > ardından, Visual Studio Yükleyicisi **ASP.NET ve web geliştirme** iş yükünü seçin.
   >
   > :::image type="content" source="media/vs-2022/aspnet-core-web-dev-workload.png" alt-text="Visual Studio Yükleyicisi ASP.NET ve web geliştirme iş yükünü gösteren ekran görüntüsü.":::
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenirse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *mycoreapp* yazın veya girin. Ardından **İleri**' yi seçin.

   :::image type="content" source="media/vs-2022/csharp-name-your-aspnet-app.png" alt-text="Project adı alanına ' mycoreapp ' ile ' yeni projeyi yapılandır ' penceresini gösteren ekran görüntüsü.":::

1. **Ek bilgi** penceresinde, **Framework** alanında **.net 6,0** ' ın göründüğünü doğrulayın. Bu pencerede, kutuyu işaretleyerek Docker desteğini etkinleştirmeyi seçebilirsiniz. Kimlik doğrulama desteği ' ni, **kimlik doğrulaması türü** açılır listesinden bir değer seçerek de ekleyebilirsiniz. Buradan buradan seçim yapabilirsiniz:

    - Hiçbiri: kimlik doğrulaması yok.
    - Bireysel hesaplar: yerel veya Azure tabanlı bir veritabanında depolanan kimlik doğrulamaları.
    - Microsoft kimlik platformu: bu seçenek, kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygundur.
    
    **Docker'ı Etkinleştir kutusunu** işaretsiz bırakın ve Kimlik doğrulaması türü **için Hiçbiri'yi** seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="media/vs-2022/aspnet-core-additional-information.png" alt-text="'Ek bilgiler' penceresindeki varsayılan ayarları gösteren ekran görüntüsü. Framework değeri '.NET 6.0'dır.":::

   Visual Studio projenizi açar.

::: moniker-end

### <a name="about-your-solution"></a>Çözümünüz hakkında

Bu çözüm, **Razor Sayfası tasarım desenini** izler. [Model-Görünüm-Denetleyici (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x&preserve-view=true) tasarım modelinden farklıdır ve razor sayfasının içinde model ve denetleyici kodunun dahil basitleştirilmiştir.

::: moniker range="vs-2017"
## <a name="tour-your-solution"></a>Çözümde tura çıkıyor

 1. Proje şablonu, _MyCoreApp_ adlı tek ASP.NET Core bir çözüm oluşturur. İçeriğini **görüntülemek Çözüm Gezgini** sekmeyi seçin.

    ![ASP.NET Çözüm Gezgini MyCoreApp Visual Studio Razor Pages çözüm için Visual Studio'de](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Sayfalar **klasörünü ve** ardından *About.cshtml dosyasını genişletin.*

     ![Çözüm Gezgini'de yer alan About.cshtml Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Kod **düzenleyicisinde About.cshtml** dosyasını görüntüleme.

     ![Visual Studio kod düzenleyicisinde About.cshtml dosyasının ilk on Visual Studio gösteren ekran görüntüsü.](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. **About.cshtml.cs dosyasını** seçin.

     ![Kod düzenleyicisinde About.cshtml.cs Visual Studio seçin](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Kod **düzenleyicisinde About.cshtml.cs** dosyasını görüntüleme.

     ![Visual Studio kod düzenleyicisinde About.cshtml.cs dosyasının ilk 18 Visual Studio ekran görüntüsü. ](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Proje, web sitenizin kökü olan bir **wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     ![Visual Studio'de Çözüm Gezgini wwwroot klasörü](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini doğrudan &mdash; &mdash; istediğiniz yollara koyabilirsiniz.

 1. Proje ayrıca çalışma zamanında web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *appsettings.json içinde depolanır.* Ancak, appsettings kullanarak bu ayarları *geçersiz kılabilirsiniz. Development.json*. **Appsettings.json dosyasını** genişletarak **appsettings dosyasını görüntüleyeceksiniz. Development.json** dosyası.

     ![Visual Studio'daki Çözüm Gezgini dosyaları](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. Uygulamayı **IIS Express** modunda derlemek ve çalıştırmak için IDE'de IIS Express düğmesini seçin. (Alternatif olarak **F5 tuşuna basın** veya Hata Ayıkla'ya **basın**  >  **Menü çubuğundan** Hata Ayıklamayı Başlat.)

     ![Dosyanın IIS Express düğmesini Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **'IIS Express' web** sunucusuna bağlanamıyor hata iletisi alırsanız, Visual Studio'yi kapatın ve ardından sağ tıklama  veya bağlam menüsünden Yönetici olarak çalıştır seçeneğini kullanarak açın. Ardından uygulamayı yeniden çalıştırın.
     >
     > Iis SSL Express sertifikasını kabul etmek istiyor sanız soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için Evet'i seçin ve ardından bir **güvenlik** uyarısı iletisi alırsanız Evet'i seçin.

1. Visual Studio tarayıcı penceresi açar. Ardından menü çubuğunda **Giriş**, **Hakkında** ve **Kişi** sayfalarını görüyorsanız. (Bunu yapmak zorunda değilsanız görüntülemek için "hamburger" menü öğesini seçin.)

    ![Web uygulamanıza gelen menü çubuğundan "hamburger" menü öğesini seçin](media/csharp-aspnet-razor-browser-page.png)

1. Menü **çubuğundan** Hakkında'ya tıklayın.

   ![Uygulamanıza uygun tarayıcı penceresinin menü çubuğunda Hakkında'ya tıklayın](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Diğer şeylerin arasında, **tarayıcının** Hakkında sayfası *About.cshtml* dosyasında ayarlanmış metni işler.

   ![Hakkında sayfasındaki metni görüntüleme](media/csharp-aspnet-razor-browser-page-about.png)

1. Hata ayıklama Visual Studio geri dönüp **Shift+F5** tuşlarına basın. Bu, tarayıcı penceresinde projeyi de kapatır.

1. Aşağıdaki Visual Studio **About.cshtml dosyasını seçin.** Ardından başka bir sözcüğü _silin_ ve yerine file ve _directory sözcüklerini ekleyin._

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

   ![Visual Studio'da Hata Listesi](media/csharp-aspnet-razor-error-list.png)

1. Şimdi bu sorunu çözeceğiz. Kod düzenleyicisinde imlecinizi hatayı içeren herhangi bir satıra yerleştirerek sol kenar boşluğundaki Hızlı Eylemler ampulü seçin. Ardından, açılan menüden Sistem'i kullan'ı **seçin;** bu yönergeyi dosyanın en üstüne ekleyin ve hataları giderin.

   !["using System;" yönergesi ekleme](media/csharp-aspnet-razor-add-usings.png)

1. **Değişikliklerinizi kaydetmek için Ctrl** + **S** tuşlarına basın ve **ardından F5** tuşuna basarak projenizi web tarayıcısında açın.

1. Yaptığınız değişiklikleri görüntülemek için web sitesi üst **kısmında Hakkında'ya** tıklayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Hakkında sayfasını görüntüleme](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Web tarayıcısını kapatın, **Hata Ayıklama modunu** durdurmak için Shift + **F5** tuşuna basın ve ardından Visual Studio.

::: moniker-end

::: moniker range="=vs-2019"

## <a name="tour-your-solution"></a>Çözümde tura çıkıyor

 1. Proje şablonu, _MyCoreApp_ adlı tek ASP.NET Core bir çözüm oluşturur. İçeriğini **görüntülemek Çözüm Gezgini** sekmeyi seçin.

    !['MyCoreApp Çözüm Gezgini adlı Visual Studio projenin içeriğini gösteren ASP.NET ekran görüntüsü.](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Sayfalar **klasörünü** genişletin.

     !['MyCoreApp Visual Studio Çözüm Gezgini pages klasörünün içeriğini gösteren Çözüm Gezgini ekran görüntüsü.](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Kod **düzenleyicisinde Index.cshtml** dosyasını görüntüleme.

     ![Dizin kodu düzenleyicisinde index.cshtml dosyasının Visual Studio ekran görüntüsü.](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Her .cshtml dosyasının ilişkili bir kod dosyası vardır. Kod dosyasını düzenleyicide açmak için, Çözüm Gezgini'de **Index.cshtml** düğümünü genişletin ve **Index.cshtml.cs dosyasını** seçin.

     ![Çözüm Gezgini Index.cshtml.cs dosyasını Visual Studio dosyanın ekran görüntüsü.](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Kod **düzenleyicisinde Index.cshtml.cs** dosyasını görüntüleme.

     ![Dizin kodu düzenleyicisinde index.cshtml.cs dosyasının Visual Studio ekran görüntüsü.](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Proje, web sitenizin kökü olan bir **wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     !['wwwroot' Çözüm Gezgini gösteren Visual Studio dosyanın ekran görüntüsü.](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini doğrudan &mdash; &mdash; istediğiniz yollara koyabilirsiniz.

 1. Proje ayrıca çalışma zamanında web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *appsettings.json içinde depolanır.* Ancak, appsettings kullanarak bu ayarları *geçersiz kılabilirsiniz. Development.json*. **Appsettings.json dosyasını** genişletarak **appsettings dosyasını görüntüleyeceksiniz. Development.json** dosyası.

     ![Appsettings.json Çözüm Gezgini Visual Studio appsettings.json dosyasını gösteren ve appsettings'i gösterecek şekilde genişletilen dosyanın ekran görüntüsü. Development.json dosyası.](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. Uygulamayı **IIS Express** modunda derlemek ve çalıştırmak için IDE'de IIS Express düğmesini seçin. (Alternatif olarak **F5 tuşuna basın** veya Hata Ayıkla'ya **basın**  >  **Menü çubuğundan** Hata Ayıklamayı Başlat.)

     ![IDE'IIS Express vurgulanmış olan Visual Studio ekran görüntüsü.](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **'IIS Express' web** sunucusuna bağlanamıyor hata iletisi alırsanız, Visual Studio'yi kapatın ve ardından sağ tıklama  veya bağlam menüsünden Yönetici olarak çalıştır seçeneğini kullanarak açın. Ardından uygulamayı yeniden çalıştırın.
     >
     > Iis SSL Express sertifikasını kabul etmek istiyor sanız soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için Evet'i seçin ve ardından bir **güvenlik** uyarısı iletisi alırsanız Evet'i seçin.

1. Visual Studio tarayıcı penceresi açar. Ardından menü çubuğunda **Giriş** ve **Gizlilik** sayfalarını görüyorsanız.

1. Menü **çubuğundan** Gizlilik'i seçin.

   **Tarayıcının** Gizlilik sayfası, *Privacy.cshtml* dosyasında ayarlanmış olan metni işler.

   !["Bu sayfayı, sitenizin gizlilik ilkesinde ayrıntı almak için kullan" metniyle Birlikte MyCoreApp Gizlilik sayfasını gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Hata ayıklama Visual Studio geri dönüp **Shift+F5** tuşlarına basın. Bu, tarayıcı penceresinde projeyi de kapatır.

1. Bu Visual Studio **privacy.cshtml dosyasını düzenlemek için** açın. Ardından, Sitenizin  gizlilik ilkesine ayrıntı eklemek için bu sayfayı kullan sözcüklerini silin ve _@ViewData ["TimeStamp"]_ ile bu sayfa inşa aşamasındadır sözcüklerini ekleyin.

    ![Güncelleştirilmiş metinle birlikte Visual Studio Privacy.cshtml dosyasının açık olduğunu gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Şimdi bir kod değişikliğine bakalım. **Privacy.cshtml.cs dosyasını seçin.** Ardından, aşağıdaki `using` kısayolu kullanarak dosyanın en üstünde yer alan yönergeleri temizleyin:

   Gri renkli yönergelerden birini seçin; bir Hızlı Eylemler ampulü, sağ altta veya sol kenar `using` boşluğunda görünür. [](../../ide/quick-actions.md) Ampulü seçin ve gereksiz kullanmaları **kaldır'ın üzerine gelin.**

   !['Gereksiz Kullanımı Kaldır' iletişim kutusunun açık olduğu Visual Studio düzenleyicisinde Privacy.cshtml dosyasını gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Şimdi değişiklikleri **görmek için** Değişiklikleri önizle'yi seçin.

   ![Yeni 'Usings' listesini ve Privacy.cshtml dosyasındaki kodu gösteren Değişiklikleri Önizle iletişim kutusunu gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-preview-changes.png)

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

1. Şimdi bu sorunu çözeceğiz. Kod düzenleyicisinde imlecinizi hatayı içeren herhangi bir satıra yerleştirerek sol kenar boşluğundaki Hızlı Eylemler ampulü seçin. Ardından, açılan menüden Sistem'i kullan'ı **seçin;** bu yönergeyi dosyanın en üstüne ekleyin ve hataları giderin.

   !['Using System' yönergesini ekleme önerisini gösteren Hızlı Eylemler menüsünü gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-add-usings.png)

1. Projenizi web tarayıcısında açmak için **F5** tuşuna basın.

1. Değişikliklerinizi görüntülemek için web sitesi üst **kısmında Gizlilik'i** seçin.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Gizlilik sayfasını gösteren ekran görüntüsü.](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

1. Web tarayıcısını kapatın, **Hata Ayıklama modunu** durdurmak için Shift + **F5** tuşuna basın ve ardından Visual Studio.
::: moniker-end

::: moniker range=">=vs-2022"

## <a name="tour-your-solution"></a>Çözümde tura çıkıyor

 1. Proje şablonu, *MyCoreApp* adlı tek ASP.NET Core bir çözüm oluşturur. İçeriğini **Çözüm Gezgini** için sekmeyi seçin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-mycoreapp.png" alt-text="'MyCoreApp Çözüm Gezgini adlı Visual Studio projenin içeriğini gösteren ASP.NET ekran görüntüsü.":::

 1. Sayfalar **klasörünü** genişletin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-solution-explorer-pages.png" alt-text="'MyCoreApp' Çözüm Gezgini Pages Visual Studio gösteren dosyanın ekran görüntüsü.":::

 1. Kod **düzenleyicisinde Index.cshtml** dosyasını görüntüleme.

     :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml.png" alt-text="Dizin kodu düzenleyicisinde index.cshtml dosyasının Visual Studio ekran görüntüsü.":::

 1. Her .cshtml dosyasının ilişkili bir kod dosyası vardır. Kod dosyasını düzenleyicide açmak için, Çözüm Gezgini'de **Index.cshtml** düğümünü genişletin ve **Index.cshtml.cs dosyasını** seçin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-choose-index-cshtml.png" alt-text="Çözüm Gezgini Index.cshtml.cs dosyasını Visual Studio dosyanın ekran görüntüsü.":::

 1. Kod **düzenleyicisinde Index.cshtml.cs** dosyasını görüntüleme.

     :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml-editing.png" alt-text="Dizin kodu düzenleyicisinde index.cshtml.cs dosyasının Visual Studio ekran görüntüsü.":::

 1. Proje, web sitenizin kökü olan bir **wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-wwwroot.png" alt-text="'wwwroot' Çözüm Gezgini gösteren Visual Studio dosyanın ekran görüntüsü.":::

    CSS, görüntüler ve JavaScript kitaplıkları gibi statik site içeriğini doğrudan &mdash; &mdash; istediğiniz yollara koyabilirsiniz.

 1. Proje ayrıca çalışma zamanında web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *appsettings.json içinde depolanır.* Ancak, appsettings kullanarak bu ayarları *geçersiz kılabilirsiniz. Development.json*. **Appsettings.json dosyasını** genişletarak **appsettings dosyasını görüntüleyeceksiniz. Development.json** dosyası.

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-solution-explorer-appsettingsjson.png" alt-text="Appsettings.json Çözüm Gezgini Visual Studio appsettings.json dosyasını gösteren ve appsettings'i gösterecek şekilde genişletilen dosyanın ekran görüntüsü. Development.json dosyası.":::

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. Uygulamayı **IIS Express** modunda derlemek ve çalıştırmak için IDE'de IIS Express düğmesini seçin. (Alternatif olarak **F5 tuşuna basın** veya Hata Ayıkla'ya **basın**  >  **Menü çubuğundan** Hata Ayıklamayı Başlat.)

     :::image type="content" source="media/vs-2022/csharp-aspnet-razor-iisexpress.png" alt-text="IDE'IIS Express vurgulanmış olan Visual Studio ekran görüntüsü.":::

     > [!NOTE]
     > **'IIS Express' web** sunucusuna bağlanamıyor hata iletisi alırsanız, Visual Studio'yi kapatın ve ardından sağ  tıklama veya bağlam menüsünden Yönetici olarak çalıştır seçeneğini kullanarak açın. Ardından uygulamayı yeniden çalıştırın.
     >
     > Iis SSL Express sertifikasını kabul etmek istiyor sanız soran bir ileti de alabilirsiniz. Kodu bir web tarayıcısında görüntülemek için Evet'i seçin ve ardından bir **güvenlik** uyarısı iletisi alırsanız Evet'i seçin.

1. Visual Studio tarayıcı penceresi açar. Ardından menü çubuğunda **Giriş** ve **Gizlilik** sayfalarını görüyorsanız.

1. Menü **çubuğundan** Gizlilik'i seçin.

   **Tarayıcının** Gizlilik sayfası, *Privacy.cshtml* dosyasında ayarlanmış olan metni işler.

   :::image type="content" source="media/vs-2022/csharp-aspnet-browser-page-privacy.png" alt-text="&quot;Bu sayfayı, sitenizin gizlilik ilkesinde ayrıntı almak için kullan&quot; metniyle Birlikte MyCoreApp Gizlilik sayfasını gösteren ekran görüntüsü.":::

1. Hata ayıklama Visual Studio geri dönüp **Shift+F5** tuşlarına basın. Bu, tarayıcı penceresinde projeyi de kapatır.

1. Bu Visual Studio **privacy.cshtml dosyasını düzenlemek için** açın. Ardından, Sitenizin  gizlilik ilkesine ayrıntı eklemek için bu sayfayı kullan sözcüklerini silin ve *@ViewData ["TimeStamp"]* ile bu sayfa inşa aşamasındadır sözcüklerini ekleyin.

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

1. Şimdi bu sorunu çözeceğiz. Kod düzenleyicisinde imlecinizi hatayı içeren herhangi bir satıra yerleştirerek sol kenar boşluğundaki Hızlı Eylemler ampulü seçin. Ardından, dosyanın en üstüne yönergesini eklemek ve hataları çözmek için açılan **menüden System.Globalization** kullanarak öğesini seçin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-add-usings.png" alt-text="'using System.Globalization' yönergesini ekleme önerisiyle Birlikte Hızlı Eylemler menüsünü gösteren ekran görüntüsü.":::

1. Projenizi web tarayıcısında açmak için **F5** tuşuna basın.

1. Değişikliklerinizi görüntülemek için web sitesi üst **kısmında Gizlilik'i** seçin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-browser-page-privacy-changed.png" alt-text="MyCoreApp'in tarihi eklemek için yapılan değişiklikleri içeren Gizlilik sayfasını gösteren ekran görüntüsü.":::

1. Web tarayıcısını kapatın, **Hata Ayıklama modunu** durdurmak için Shift + **F5** tuşuna basın ve ardından Visual Studio.

::: moniker-end

## <a name="quick-answers-faq"></a>Hızlı yanıtlar hakkında SSS

Bazı temel kavramları vurgulamak için burada hızlı bir SSS bulabilirsiniz.

### <a name="what-is-c"></a>C# nedir?

[C#](/dotnet/csharp/tour-of-csharp/) hem sağlam hem de öğrenmesi kolay olacak şekilde tasarlanmış, tür kullanımı güvenli ve nesne odaklı bir programlama dilidir.

### <a name="what-is-aspnet-core"></a>ASP.NET Core nedir?

ASP.NET Core web uygulamaları ve hizmetleri gibi İnternet'e bağlı uygulamalar için açık kaynak ve platformlar arası bir çerçevedir. ASP.NET Core uygulamaları .NET Core veya .NET Framework. ASP.NET Core, Mac ve Linux üzerinde platformlar arası Windows geliştirebilir ve çalıştırabilirsiniz. ASP.NET Core açık kaynaktır ve [GitHub.](https://github.com/aspnet/home)

### <a name="what-is-visual-studio"></a>Hangi Visual Studio?

Visual Studio, geliştiriciler için tümleşik bir üretkenlik araçları geliştirme paketidir. Bunu program ve uygulama oluşturmak için kullanabileceğiniz bir program olarak düşün.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamladıktan sonra! C#, ASP.NET Core ve Visual Studio IDE hakkında bilgi Visual Studio umuyoruz. C# ve ASP.NET ile web uygulaması veya web sitesi oluşturma hakkında daha fazla ASP.NET aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Razor Pages web uygulaması ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1&preserve-view=true)

Veya Web uygulamalarınızı Docker ile kapsayıcılı hale nasıl ala öğrenin:

> [!div class="nextstepaction"]
> [Visual Studio'de Kapsayıcı Araçları](../../containers/overview.md)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio kullanarak web Azure App Service web Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
