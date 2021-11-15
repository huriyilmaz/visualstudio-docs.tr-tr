---
title: "C 'de ASP.NET Core web uygulaması oluşturma #"
description: C# ve ASP.NET Core, adım adım Visual Studio basit bir Merhaba Dünya web uygulamasının nasıl oluşturulacağını öğrenin.
ms.custom: vs-acquisition
ms.date: 09/14/2021
ms.topic: quickstart
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: a4a763a221a6aba7ade463d27a608afcd8f406e0
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453664"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>hızlı başlangıç: ilk ASP.NET Core web uygulamanızı oluşturmak için Visual Studio kullanın

Visual Studio nasıl kullanılacağına ilişkin bu 5-10 dakika içinde, ASP.NET proje şablonunu ve C# programlama dilini kullanarak basit bir "Merhaba Dünya" web uygulaması oluşturacaksınız.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="<=vs-2019"
### <a name="choose-your-theme-optional"></a>Temanızı seçin (isteğe bağlı)

Bu Hızlı Başlangıç Öğreticisi, koyu temayı kullanan ekran görüntüleri içerir. koyu temayı kullanmıyorsanız ancak nasıl yapılacağını öğrenmek istiyorsanız, bkz. [nasıl yapılır: Visual Studio ıde ve düzenleyiciyi kişiselleştirme](quickstart-personalize-the-ide.md).

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

başlamak için bir ASP.NET Core web uygulaması projesi oluşturacaksınız. Proje türü, bir Web uygulaması oluşturmak için tüm şablon dosyalarıyla birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

1. **yeni Project** iletişim kutusunun sol bölmesinde, **Visual C#**' ı genişletin ve ardından **.net Core**' u seçin. orta bölmede **ASP.NET Core Web uygulaması**' nı seçin. <br/><br/>Sonra, Dosyanızı adlandırın `HelloWorld` ve **Tamam**' ı seçin.

   ![C için yeni ASP.NET Core Web uygulaması projesi oluşturma #](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > **.net Core** proje şablonu kategorisini görmüyorsanız sol bölmedeki **Visual Studio Yükleyicisi aç** bağlantısını seçin. (Görüntü ayarlarınıza bağlı olarak, görmek için kaydırmanız gerekebilir.)
   >
   > ![yeni proje iletişim kutusundan Visual Studio Yükleyicisi aç](../ide/media/open-visual-studio-installer.png)
   >
   > Visual Studio Yükleyicisi başlatılır. **ASP.NET ve web geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.
   >
   > ![VS yükleyicisinde iş yükünü ASP.NET](../ide/media/quickstart-aspnet-workload.png)
   >
   > (yeni iş yükünü yüklemeye devam edebilmeniz için önce Visual Studio kapatmanız gerekebilir.)

1. **yeni ASP.NET Core Web uygulaması** iletişim kutusunda üst açılan menüden **ASP.NET Core 2,1** ' ı seçin. Sonra, **Web uygulaması**' nı ve ardından **Tamam**' ı seçin.

   ![yeni ASP.NET Core Web uygulaması iletişim kutusu](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > **ASP.NET Core 2,1**' i görmüyorsanız Visual Studio en son sürümünü çalıştırdığınızdan emin olun. yüklemenizi güncelleştirme hakkında daha fazla bilgi için [güncelleştirme Visual Studio en son sürüm](../install/update-visual-studio.md) sayfasına bakın.

yakında Visual Studio, proje dosyanızı açar.

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   :::image type="content" source="../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="' yeni proje oluştur ' seçeneği vurgulanmış şekilde Visual Studio başlangıç penceresini gösteren ekran görüntüsü.":::

1. **Yeni proje oluştur** penceresinde dil listesinden **C#** ' ı seçin. ardından, Platform listesinden **Windows** ve proje türleri listesinden **Web** ' i seçin.

   dili, platformu ve proje türü filtrelerini uyguladıktan sonra, **ASP.NET Core Web uygulaması** şablonunu seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="' C# ', ' Windows ' ve ' Web ' üzerinde filtrelenmiş ' yeni proje oluştur ' penceresini gösteren ekran görüntüsü. ' ASP.NET Core Web uygulaması ' proje şablonu vurgulandı.":::

   > [!NOTE]
   > **ASP.NET Core Web uygulaması** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Daha fazla araç ve özellik yükler ' bağlantısını gösteren ve ' aradığınızı bulma ' iletisinde vurgulanan ekran görüntüsü.](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > ardından, Visual Studio Yükleyicisi **ASP.NET ve web geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükünü gösteren ekran görüntüsü.](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenirse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *HelloWorld* yazın veya girin. Ardından **İleri**' yi seçin.

    :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-hello-world-project.png" alt-text="Project adı alanında ' HelloWorld ' ile ' yeni projeyi yapılandır ' penceresini gösteren ekran görüntüsü.":::

1. **Ek bilgi** penceresinde, **.NET Core 3,1** ' ın üst açılan menüde göründüğünü doğrulayın. Kutuyu işaretleyerek Docker desteğini etkinleştirmeyi seçebileceğinizi unutmayın. Kimlik doğrulamasını Değiştir düğmesine tıklayarak da kimlik doğrulama desteği ekleyebilirsiniz. Buradan buradan seçim yapabilirsiniz:
    - Hiçbiri: kimlik doğrulaması yok.
    - Bireysel hesaplar: Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: bu seçenek, kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygun.
    
    **Docker 'ı etkinleştir** kutusunu işaretsiz bırakın ve kimlik doğrulama türü için **hiçbiri** ' ni seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="../get-started/csharp/media/vs-2019/aspnet-core-additional-information.png" alt-text="Framework alanında ' .NET Core 3,1 ' ile birlikte ek bilgi penceresini gösteren ekran görüntüsü.":::

   Visual Studio, yeni projenizi açacak.

::: moniker-end

::: moniker range=">=vs-2022"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   :::image type="content" source="media/vs-2022/create-new-project-dark-theme.png" alt-text="' yeni proje oluştur ' seçeneği vurgulanmış şekilde Visual Studio başlangıç penceresini gösteren ekran görüntüsü.":::

1. **Yeni proje oluştur** penceresinde dil listesinden **C#** ' ı seçin. ardından, Platform listesinden **Windows** ve proje türleri listesinden **Web** ' i seçin.

   dili, platformu ve proje türü filtrelerini uyguladıktan sonra, **ASP.NET Core Web uygulaması** şablonunu seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="media/vs-2022/csharp-create-new-project-aspnet-core.png" alt-text="' C# ', ' Windows ' ve ' Web ' üzerinde filtrelenmiş ' yeni proje oluştur ' penceresini gösteren ekran görüntüsü. ' ASP.NET Core Web uygulaması ' proje şablonu vurgulandı.":::

   > [!NOTE]
   > **ASP.NET Core Web uygulaması** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > :::image type="content" source="media/vs-2022/not-finding-what-looking-for.png" alt-text="' Daha fazla araç ve özellik yükler ' bağlantısını gösteren ve ' aradığınızı bulma ' iletisinde vurgulanan ekran görüntüsü.":::
   >
   > ardından, Visual Studio Yükleyicisi **ASP.NET ve web geliştirme** iş yükünü seçin.
   >
   > :::image type="content" source="media/vs-2022/aspnet-core-web-dev-workload.png" alt-text="Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükünü gösteren ekran görüntüsü.":::
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenirse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *HelloWorld* yazın veya girin. Ardından **İleri**' yi seçin.

    :::image type="content" source="media/vs-2022/csharp-name-your-aspnet-hello-world-project.png" alt-text="Project adı alanında ' HelloWorld ' ile ' yeni projeyi yapılandır ' penceresini gösteren ekran görüntüsü.":::

1. **Ek bilgi** penceresinde, **Framework** alanında **.net 6,0** ' ın göründüğünü doğrulayın. Kutuyu işaretleyerek Docker desteğini etkinleştirmeyi seçebileceğinizi unutmayın. Kimlik doğrulama desteği ' ni, **kimlik doğrulaması türü** açılır listesinden bir değer seçerek de ekleyebilirsiniz. Buradan buradan seçim yapabilirsiniz:

    - Hiçbiri: kimlik doğrulaması yok.
    - Bireysel hesaplar: Bu kimlik doğrulamaları yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: bu seçenek, kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygun.
    
    **Docker 'ı etkinleştir** kutusunu işaretsiz bırakın ve kimlik doğrulama türü için **hiçbiri** ' ni seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="media/vs-2022/aspnet-core-additional-information.png" alt-text="Framework alanında ' .NET 6,0 ' ile birlikte ek bilgi penceresini gösteren ekran görüntüsü.":::

   Visual Studio, yeni projenizi açacak.

::: moniker-end

## <a name="create-and-run-the-app"></a>Uygulamayı oluşturma ve çalıştırma

::: moniker range="vs-2017"

1. **Çözüm Gezgini**, **Sayfalar** klasörünü genişletin ve ardından **. cshtml**' yi seçin.

   ![HelloWorld projesindeki dosyaları gösteren Visual Studio Çözüm Gezgini ekran görüntüsü. Sayfalar klasörü genişletilir ve. cshtml hakkında seçilidir.](../ide/media/csharp-aspnet-about-page-html-file.png)

   Bu dosya, bir Web tarayıcısında çalışan Web uygulamasında **hakkında** adlı bir sayfaya karşılık gelir.

   ![Web uygulamasındaki hakkında sayfası](../ide/media/csharp-aspnet-about-page.png)

   Düzenleyicide, **hakkında** sayfasının "ek bilgiler" alanı için HTML kodu görürsünüz.

   ![Düzenleyicide ek bilgi alanına ilişkin HTML Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. "Ek bilgi" metnini "**Merhaba Dünya!**" olarak değiştirebilirsiniz.

   ![Visual Studio düzenleyicisinde ek bilgi alanı için varsayılan HTML Visual Studio değiştirme](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. Dosyanın **Çözüm Gezgini** **About.cshtml dosyasını genişletin** ve **About.cshtml.cs dosyasını seçin.** (Bu dosya bir web tarayıcısında **Hakkında** sayfasına da karşılık gelen bir dosyadır.)

   ![HelloWorld Visual Studio Çözüm Gezgini dosyaları gösteren ekran görüntüsü. About.cshtml genişletilir ve About.cshtml.cs seçilir.](../ide/media/csharp-aspnet-about-page-code-file.png)

   Düzenleyicide Hakkında sayfasının "uygulama açıklaması" alanı için metin içeren C# **kodunu** görebilirsiniz.

   ![Uygulama düzenleyicisinde uygulama açıklaması alanına ilişkin C# Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. "Uygulama açıklaması" ileti metnini " İletim **nedir?**" şeklinde olacak şekilde değiştirebilirsiniz.

   ![Uygulama açıklaması alanı için varsayılan ileti metnini düzenleyicide Visual Studio değiştirme](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Uygulamayı **IIS Express** çalıştırmak için **Ctrl** + **F5** tuşuna basın veya uygulamayı bir web tarayıcısında açın.

   ![Dosyanın IIS Express düğmesini Visual Studio](../ide/media/csharp-aspnet-hello-world-iis-button.png)

   > [!NOTE]
   > **'IIS Express' web** sunucusuna bağlanamıyor veya SSL sertifikasından bahseden bir hata iletisiyle ilgili bir hata iletisi alırsanız Visual Studio. Ardından, Visual Studio bağlam **menüsünden Yönetici olarak** çalıştır seçeneğini kullanarak oturum açın. Ardından uygulamayı yeniden çalıştırın.

1. Web tarayıcısında Hakkında sayfasında **güncelleştirilmiş metninizin** olduğunu doğrulayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Hakkında sayfasını görüntüleme](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Web tarayıcısını kapatın.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirme

Önceki bölümde tamamlamış olduğunu işi kontrol etmek için aşağıdaki animasyonu görüntüebilirsiniz.

  ![Basit bir C# .gif web uygulaması oluşturma ve çalıştırmayı gösteren animasyonlu ASP.NET Core dosyasını Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Tebrikler, bu Hızlı Başlangıç'a devam ediyoruz! C#, ASP.NET Core ve Visual Studio IDE (tümleşik geliştirme ortamı) hakkında biraz bilgi öğrendiğini umuyoruz.

::: moniker-end

::: moniker range="vs-2019"

1. Aşağıdaki **Çözüm Gezgini** Sayfalar klasörünü genişletin ve **Index.cshtml dosyasını seçin.** 

   ![Uygulamanın genişletilmiş Sayfalar klasöründe 'Index.cshtml' seçimini gösteren ekran Çözüm Gezgini.](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Bu dosya, bir web tarayıcısında çalışan web uygulamasında **Giriş** adlı bir sayfaya karşılık geliyor.

   ![Tarayıcı penceresinde web uygulamasının Giriş sayfasını gösteren ekran görüntüsü.](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   Düzenleyicide, Giriş sayfasında görüntülenen metnin HTML **kodunu** görebilirsiniz.

   ![Kod düzenleyicisinde Giriş sayfası için Index.cshtml dosyasını Visual Studio ekran görüntüsü.](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. "Hoş Geldiniz" metnini "**Merhaba Dünya!**".

   !['Hoş Geldiniz' metni 'Merhaba Dünya!' olarak değiştirilmiş, Visual Studio düzenleyicisinde 'Index.cshtml' dosyasını gösteren ekran görüntüsü.](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Uygulamayı **IIS Express** çalıştırmak için **Ctrl** + **F5** tuşuna basın veya uygulamayı bir web tarayıcısında açın.

   ![IIS Express düğmesi vurgulanmış şekilde gösteren Visual Studio.](../ide/media/vs-2019/csharp-aspnet-generic-iis-button.png)

   > [!NOTE]
   > **'IIS Express' web** sunucusuna bağlanamıyor veya SSL sertifikasından bahseden bir hata iletisiyle ilgili bir hata iletisi alırsanız Visual Studio. Ardından, Visual Studio bağlam **menüsünden Yönetici olarak** çalıştır seçeneğini kullanarak oturum açın. Ardından uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, Giriş sayfasında **güncelleştirilmiş metninizin** olduğunu doğrulayın.

   ![Tarayıcı penceresinde güncelleştirilmiş 'Merhaba Dünya!' iletisiyle web uygulamasının Giriş sayfasını gösteren ekran görüntüsü.](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Web tarayıcısını kapatın.

::: moniker-end

::: moniker range=">=vs-2022"

1. Aşağıdaki **Çözüm Gezgini** Sayfalar klasörünü genişletin ve **Index.cshtml dosyasını seçin.** 

   :::image type="content" source="media/vs-2022/csharp-aspnet-index-page-cshtml-file.png" alt-text="Uygulamanın genişletilmiş Sayfalar klasöründe 'Index.cshtml' seçimini gösteren Çözüm Gezgini.":::

   Bu dosya, bir web tarayıcısında çalışan web uygulamasında **Giriş** adlı bir sayfaya karşılık geliyor.

   :::image type="content" source="media/vs-2022/csharp-aspnet-index-page.png" alt-text="Tarayıcı penceresinde web uygulamasının Giriş sayfasını gösteren ekran görüntüsü.":::

   Düzenleyicide, Giriş sayfasında görüntülenen metnin HTML **kodunu** görebilirsiniz.

   :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml.png" alt-text="Kod düzenleyicisinde Giriş sayfası için Index.cshtml dosyasını Visual Studio ekran görüntüsü.":::

1. "Hoş Geldiniz" metnini "**Merhaba Dünya!**".

   :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml-page-hello-world.png" alt-text="'Hoş Geldiniz' metni 'Merhaba Dünya!' olarak değiştirilmiş, Visual Studio düzenleyicisinde 'Index.cshtml' dosyasını gösteren ekran görüntüsü.":::

1. Uygulamayı **IIS Express** ve bir web **tarayıcısında** açmak için Ctrl + **F5** tuşuna basın veya seçin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-generic-iis-button.png" alt-text="IIS Express düğmesi vurgulanmış şekilde gösteren Visual Studio.":::

   > [!NOTE]
   > **'IIS Express' web** sunucusuna bağlanamıyor veya SSL sertifikasından bahseden bir hata iletisiyle ilgili bir hata iletisi alırsanız Visual Studio. Ardından, Visual Studio bağlam **menüsünden Yönetici olarak** çalıştır seçeneğini kullanarak oturum açın. Ardından uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, Giriş sayfasında **güncelleştirilmiş metninizin** olduğunu doğrulayın.

   :::image type="content" source="media/vs-2022/csharp-aspnet-index-page-hello-world.png" alt-text="Tarayıcı penceresinde güncelleştirilmiş 'Merhaba Dünya!' iletisiyle web uygulamasının Giriş sayfasını gösteren ekran görüntüsü.":::

1. Web tarayıcısını kapatın.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Web uygulamaları oluşturma hakkında daha ASP.NET için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Kullanmaya başlayın C# ve ASP.NET ile Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

Veya Web uygulamalarınızı Docker ile kapsayıcılı hale nasıl ala öğrenin:

> [!div class="nextstepaction"]
> [Visual Studio'de Kapsayıcı Araçları](../containers/overview.md)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio kullanarak web Azure App Service web Visual Studio](../deployment/quickstart-deploy-to-azure.md)
