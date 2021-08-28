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
ms.openlocfilehash: 1a42e1d1d083a383715db72b018b695fc4a9829c
ms.sourcegitcommit: 8f8804b885c3a68f20bf0e9fe3729f2764145815
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2021
ms.locfileid: "123097037"
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

1. Visual Studio ' de, **. cshtml**' yi seçin. Ardından, _ek_ sözcüğü silin ve onun yerine, sözcükler _dosyasını ve dizinini_ ekleyin.

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

::: moniker range=">=vs-2019"

## <a name="tour-your-solution"></a>Çözümünüze tura katılın

 1. proje şablonu, _mycoreapp_ adlı tek bir ASP.NET Core projesiyle bir çözüm oluşturur. İçeriğini görüntülemek için **Çözüm Gezgini** sekmesini seçin.

    ![ASP.NET mycoreapp adlı Razor Pages çözümü için Visual Studio Çözüm Gezgini](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. **Sayfalar** klasörünü genişletin.

     ![Çözüm Gezgini sayfa klasörü](media/vs-2019/csharp-aspnet-solution-explorer-pages.png)

 1. Kod düzenleyicisinde **Index. cshtml** dosyasını görüntüleyin.

     ![Visual Studio kod düzenleyicisinde Index. cshtml dosyasını görüntüleme](media/vs-2019/csharp-aspnet-index-cshtml.png)

 1. Her. cshtml dosyası, ilişkili bir kod dosyasına sahiptir. Kod dosyasını düzenleyicide açmak için, Çözüm Gezgini içindeki **index. cshtml** düğümünü genişletin ve **index. cshtml. cs** dosyasını seçin.

     ![Visual Studio kod düzenleyicisinde Index. cshtml. cs dosyasını seçin](media/vs-2019/csharp-aspnet-choose-index-cshtml.png)

 1. Kod düzenleyicisinde **Index. cshtml. cs** dosyasını görüntüleyin.

     ![Visual Studio code düzenleyicisinde About. cshtml dosyasını görüntüleme](media/vs-2019/csharp-aspnet-index-cshtml-editing.png)

 1. Proje, Web siteniz için kök olan bir **Wwwroot** klasörü içerir. İçeriğini görüntülemek için klasörü genişletin.

     ![Visual Studio Çözüm Gezgini Wwwroot klasörü](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    &mdash;CSS, resim ve JavaScript kitaplıkları gibi statik site içeriğini &mdash; doğrudan istediğiniz yollarla yerleştirebilirsiniz.

 1. Proje, çalışma zamanında Web uygulamasını yöneten yapılandırma dosyalarını da içerir. Varsayılan uygulama [yapılandırması](/aspnet/core/fundamentals/configuration) *üzerindeappsettings.js* depolanır. Ancak, *üzerindeappsettings.Development.js* kullanarak bu ayarları geçersiz kılabilirsiniz. Dosyadaki **appsettings.Development.js** görüntülemek için **appsettings.jsdosya '** yı genişletin.

     ![Visual Studio Çözüm Gezgini yapılandırma dosyaları](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Çalıştırma, hata ayıklama ve değişiklik yapma

1. uygulamayı derlemek ve hata ayıklama modunda çalıştırmak için ıde 'de **IIS Express** düğmesini seçin. (Alternatif olarak, **F5** tuşuna basın veya **Hata Ayıkla**  >  ' yı seçin Menü çubuğundan **hata ayıklamayı başlatın** .)

     ![Visual Studio IIS Express düğmesini seçin](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > **' IIS Express ' web sunucusuna bağlanmadığını** belirten bir hata iletisi alırsanız, Visual Studio kapatın ve sağ tıklama ya da bağlam menüsünde **yönetici olarak çalıştır** seçeneğini kullanarak açın. Sonra, uygulamayı yeniden çalıştırın.
     >
     > Ayrıca bir IIS SSL Express sertifikasını kabul etmek isteyip istemediğinizi soran bir ileti alabilirsiniz. Kodu bir Web tarayıcısında görüntülemek için **Evet**' i seçin ve ardından bir izleme güvenlik uyarısı Iletisi alırsanız **Evet** ' i seçin.

1. Visual Studio bir tarayıcı penceresi başlatır. Ardından, menü çubuğunda **giriş** ve **Gizlilik** sayfalarını görmeniz gerekir.

1. Menü çubuğundan **Gizlilik** ' i seçin.

   Tarayıcıdaki **Gizlilik** sayfası, *Gizlilik. cshtml* dosyasında ayarlanan metni işler.

   ![Gizlilik sayfasında metni görüntüleme](media/vs-2019/csharp-aspnet-browser-page-privacy.png)

1. Visual Studio döndürün ve sonra hata ayıklama modunu durdurmak için **shıft + F5** tuşlarına basın. Bu, projeyi tarayıcı penceresinde de kapatır.

1. Visual Studio, düzenlenecek **gizlilik. cshtml** dosyasını açın. Ardından, bu _sayfayı kullanarak sitenizin gizlilik ilkesini ayrıntılandırın_ ve onun yerine _bu sayfanın yapım aşamasında olduğu kelimeleri @ViewData ["timestamp"] olarak_ ekleyin.

    ![Gizlilik. cshtml dosyasındaki metni değiştirme](media/vs-2019/csharp-aspnet-privacy-cshtml-code-changed.png)

1. Şimdi bir kod değişikliği yapalim. **Gizlilik. cshtml. cs** öğesini seçin. Ardından, `using` aşağıdaki kısayolu kullanarak dosyanın en üstündeki yönergeleri temizleyin:

   Gri olmayan yönergelerden herhangi birini seçin `using` ve hızlı bir [eylem](../../ide/quick-actions.md) ampul, yalnızca giriş işaretinin altında veya sol kenar boşluğunda görünür. Ampul ' i seçin ve ardından **gereksiz kullanımları kaldır**' ın üzerine gelin.

   ![Gizlilik. cshtml. cs dosyasındaki gereksiz kullanımları kaldırın](media/vs-2019/csharp-aspnet-remove-unnecessary-usings.png)

   Şimdi nelerin olacağını görmek için **Değişiklikleri Önizle** ' yi seçin.

   ![Değişiklikleri Önizle](media/vs-2019/csharp-aspnet-preview-changes.png)

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

   ![OnGet yönteminde dalgalı alt çizgilerle işaretlenmiş hatalar](media/vs-2019/csharp-aspnet-add-new-onget-method.png)

    Burada listelenen hataların aynısını görmek için **hata listesi** araç çubuğunu açın. ( **Hata listesi** araç çubuğunu görmüyorsanız, **Görünüm**  >  ' ü seçin. Üst menü çubuğundan **hata listesi** .)

   ![Visual Studio Hata Listesi](media/vs-2019/csharp-aspnet-error-list.png)

1. Bunu düzeldelim. Kod Düzenleyicisi 'nde imlecinizi hatayı içeren bir satıra yerleştirin ve ardından sol kenar boşluğunda hızlı eylemler Ampul ampul ' i seçin. Daha sonra, açılan menüden, bu yönergeyi dosyanızın en üstüne eklemek ve hataları çözmek için, **Sistem kullanma** seçeneğini belirleyin.

   !["Using System;" yönergesini ekleyin](media/vs-2019/csharp-aspnet-add-usings.png)

1. **F5** tuşuna basarak projenizi web tarayıcısında açın.

1. Değişikliklerinizi görüntülemek için Web sitesinin en üstünde **Gizlilik** ' i seçin.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş gizlilik sayfasını görüntüleyin](media/vs-2019/csharp-aspnet-browser-page-privacy-changed.png)

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
