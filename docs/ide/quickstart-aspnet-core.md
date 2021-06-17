---
title: "C'de ASP.NET Core web uygulaması oluşturma #"
description: C# ve ASP.NET Core Merhaba Dünya adım Visual Studio basit bir web uygulaması oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: acquisition, mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: b361446bb128fcc01ac9a33f3a367b7e60a050c4
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112113238"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Hızlı Başlangıç: Visual Studio Core web ASP.NET oluşturmak için ASP.NET kullanma

Visual Studio'ı kullanmaya 5-10 dakikalık bir giriş olarak, ASP.NET proje şablonu ve C# programlama dili kullanarak basit bir "Merhaba Dünya" web uygulaması oluşturabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Temanızı seçin (isteğe bağlı)

Bu hızlı başlangıç öğreticisi, koyu temayı kullanan ekran görüntülerini içerir. Koyu temayı kullanmadıysanız ama bunu öğrenmek için Visual Studio [IDE](quickstart-personalize-the-ide.md) ve Düzenleyici sayfasını kişiselleştirme sayfasına bakın.

## <a name="create-a-project"></a>Proje oluşturma

Başlamak için bir ASP.NET Core web uygulaması projesi oluşturabilirsiniz. Proje türü, siz bir şey eklemeden önce web uygulaması oluşturmak için tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Dosya Yeni **Proje'yi** >  > **seçin.**

1. Yeni Proje iletişim kutusunun sol **bölmesinde** **Visual C#** öğesini genişletin ve **.NET Core'ı seçin.** Orta bölmede, Temel **Web ASP.NET'ni seçin.** <br/><br/>Ardından dosyanıza bir ad girin `HelloWorld` ve Tamam'ı **seçin.**

   ![C için yeni ASP.NET Core Web Uygulaması projesi oluşturma #](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > **.NET Core** proje şablonu kategorisini görmüyorsanız sol **bölmedeki** Visual Studio Yükleyicisi aç bağlantısını seçin. (Görüntü ayarlarınıza bağlı olarak, bunu görmek için kaydırmanız gerekebilir.)
   >
   > ![Yeni Visual Studio Yükleyicisi iletişim kutusundan dosya açma](../ide/media/open-visual-studio-installer.png)
   >
   > Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü seçin ve** ardından Değiştir'i **seçin.**
   >
   > ![VS Yükleyicisi ASP.NET de iş yükü yükleme](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Yeni iş yükünü yüklemeye Visual Studio önce bu uygulamayı kapatmanız gerekir.)

1. Yeni **ASP.NET Çekirdek Web Uygulaması** iletişim kutusunda, üst açılan **menüden ASP.NET Core 2.1'i** seçin. Ardından Web **Uygulaması'ı ve** ardından Tamam'ı **seçin.**

   ![Yeni ASP.NET Core Web Uygulaması iletişim kutusu](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > **ASP.NET Core 2.1'i** görmüyorsanız, Visual Studio'nin en son yayınlarını çalıştırmayı Visual Studio. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için Güncelleştirme Visual Studio [en son sürüm sayfasına](../install/update-visual-studio.md) bakın.

Kısa süre sonra Visual Studio dosyanızı açar.

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="'Yeni proje oluştur' penceresini görüntüleme":::

1. Yeni **proje oluştur penceresinde Dil** **listesinden C#** dilini seçin. Ardından Platform **listesinden Windows'u** ve proje türleri **listesinden Web'i** seçin.

      Dil, platform ve proje türü filtrelerini uyguladikten sonra, **ASP.NET Core Web Uygulaması** şablonunu ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="ASP.NET Core Web Uygulaması için C# şablonunu seçin":::

   > [!NOTE]
   > **ASP.NET Core Web Uygulaması** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Yükleyicisi web geliştirme ASP.NET **iş yükünü** seçin.
   >
   > ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istenirse bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresinde** Proje adı kutusuna *HelloWorld* yazın **veya** girin. Ardından, **Sonraki'yi seçin.**

    :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png" alt-text="'Yeni projenizi yapılandırma' penceresinde projenize 'MyCoreApp' adını girin":::

1. Ek **bilgiler penceresinde** üst açılan menüde **.NET Core 3.1'in** görüntülendiğinden emin olur. Kutuyu işaret ederek Docker desteğini etkinleştirmeyi seçebilirsiniz. Kimlik doğrulamasını değiştir düğmesine tıklayarak da kimlik doğrulaması desteği ebilirsiniz. Buradan şunları seçebilirsiniz:
    - Hiçbiri: Kimlik doğrulaması yok.
    - Bireysel hesaplar: Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: Bu seçenek kimlik doğrulaması için Active Directory, Azure AD Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygundur.
    
    **Docker'ı Etkinleştir kutusunun** işaretini kaldırın ve Kimlik Doğrulama Türü **için Hiçbiri'ne** tıklayın. Ardından **Oluştur**’u seçin.

   :::image type="content" source="../get-started/csharp/media/vs-2019/aspnet-core-additional-information.png" alt-text="'Ek bilgiler' penceresinde .NET Core 3.1'in seçili olduğundan emin olun ve tüm varsayılan değerleri bırakın":::

   Visual Studio projenizi açar.

::: moniker-end

## <a name="create-and-run-the-app"></a>Uygulamayı oluşturma ve çalıştırma

::: moniker range="vs-2017"

1. dosya **Çözüm Gezgini** Sayfalar klasörünü genişletin **ve** **About.cshtml dosyasını seçin.**

   ![HelloWorld Visual Studio Çözüm Gezgini dosyaları gösteren ekran görüntüsü. Sayfalar klasörü genişletilir ve About.cshtml seçilir.](../ide/media/csharp-aspnet-about-page-html-file.png)

   Bu dosya, bir web tarayıcısında çalışan web **uygulamasında Hakkında** adlı bir sayfaya karşılık gelen bir sayfadır.

   ![Web uygulamasındaki Hakkında sayfası](../ide/media/csharp-aspnet-about-page.png)

   Düzenleyicide Hakkında sayfasının "ek bilgiler" alanına ilişkin HTML **kodunu** görebilirsiniz.

   ![Visual Studio düzenleyicisinde ek bilgi alanı için HTML kodu](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. "Ek bilgi" metnini "**Merhaba Dünya! ".**

   ![Visual Studio düzenleyicisinde ek bilgi alanı için varsayılan HTML Visual Studio değiştirme](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. dosya **Çözüm Gezgini** **About.cshtml'yi genişletin** ve **about.cshtml.cs dosyasını seçin.** (Bu dosya bir web **tarayıcısında Hakkında** sayfasına da karşılık gelen bir dosyadır.)

   ![HelloWorld Visual Studio Çözüm Gezgini dosyaları gösteren ekran görüntüsü. About.cshtml genişletilir ve About.cshtml.cs seçilir.](../ide/media/csharp-aspnet-about-page-code-file.png)

   Düzenleyicide Hakkında sayfasının "uygulama açıklaması" alanı için metin içeren C# **kodunu** görebilirsiniz.

   ![Uygulama düzenleyicisinde uygulama açıklaması alanına ilişkin C# Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. "Uygulama açıklaması" ileti metnini " İletim nedir? "**".**

   ![Uygulama düzenleyicisinde uygulama açıklaması alanı için varsayılan ileti Visual Studio değiştirme](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Uygulamayı **IIS Express** ve bir web **tarayıcısında** açmak için Ctrl + **F5** tuşuna basın veya seçin.

   ![Dosyanın IIS Express düğmesini Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > **'IIS Express' web** sunucusuna bağlanamıyor veya SSL sertifikasından bahseden bir hata iletisiyle ilgili bir hata iletisi alırsanız, Visual Studio. Ardından, Visual Studio **menüyü seçerek** yönetici olarak çalıştır seçeneğini kullanarak oturum açın. Ardından uygulamayı yeniden çalıştırın.

1. Web tarayıcısında Hakkında sayfasında **güncelleştirilmiş metninizin** olduğunu doğrulayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Hakkında sayfasını görüntüleme](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Web tarayıcısını kapatın.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirme

Önceki bölümde tamamlamış olduğunuz çalışmaları kontrol etmek için aşağıdaki animasyonu görüntüebilirsiniz.

  ![Visual Studio'.gif basit bir C# ASP.NET Core web uygulaması oluşturma ve çalıştırmayı gösteren animasyonlu Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Tebrikler, bu Hızlı Başlangıç'a devam ediyoruz! C#, ASP.NET Core ve Visual Studio IDE (tümleşik geliştirme ortamı) hakkında biraz bilgi öğrendiğini umuyoruz.

::: moniker-end

::: moniker range="vs-2019"

1. dosya **Çözüm Gezgini** Sayfalar klasörünü genişletin **ve** **Index.cshtml dosyasını seçin.**

   ![Dizinden Index.cshtml dosyasını Çözüm Gezgini](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Bu dosya, web uygulamasında web tarayıcısında çalışan **Giriş** adlı sayfaya karşılık geliyor.

   ![Web uygulamasındaki Hakkında sayfası](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   Düzenleyicide, Giriş sayfasında görüntülenen metnin HTML **kodunu** görebilirsiniz.

   ![Düzenleyicide Giriş sayfasının Index.cshtml dosyasındaki HTML Visual Studio](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. "Hoş Geldiniz" metnini "**Merhaba Dünya! ".**

   ![Visual Studio düzenleyicisinde Hoş Geldiniz ifadesinin yer alan varsayılan HTML kodunu Merhaba Dünya değiştirme](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Uygulamayı **IIS Express** çalıştırmak için **Ctrl** + **F5** tuşuna basın veya uygulamayı bir web tarayıcısında açın.

   ![Dosyanın IIS Express düğmesini Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > **'IIS Express' web** sunucusuna bağlanamıyor veya SSL sertifikasından bahseden bir hata iletisiyle ilgili bir hata iletisi alırsanız, Visual Studio. Ardından, Visual Studio **menüyü seçerek** yönetici olarak çalıştır seçeneğini kullanarak oturum açın. Ardından uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, Giriş sayfasında **güncelleştirilmiş metninizin** olduğunu doğrulayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Giriş sayfasını görüntüleme](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Web tarayıcısını kapatın.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Kullanmaya başlayın C# ve ASP.NET ile Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio kullanarak web Azure App Service web Visual Studio](../deployment/quickstart-deploy-to-azure.md)
