---
title: "C'ASP.NET Core web uygulaması oluşturma #"
description: C# ve Merhaba Dünya adım Visual Studio basit bir ASP.NET Core web uygulaması oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: vs-acquisition
ms.date: 11/06/2019
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
ms.openlocfilehash: 974f6bf70d6866893a61a14f9e2999ba265fb166
ms.sourcegitcommit: 8f8804b885c3a68f20bf0e9fe3729f2764145815
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2021
ms.locfileid: "123097024"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Hızlı Başlangıç: Visual Studio web uygulaması oluşturmak için ASP.NET Core kullanma

Visual Studio'ı kullanmaya 5-10 dakikalık bir giriş olarak, ASP.NET proje şablonu ve C# programlama dili kullanarak basit bir "Merhaba Dünya" web uygulaması oluşturabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio [2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) yüklemelerini henüz yüklememişsinizdir.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Temanızı seçin (isteğe bağlı)

Bu hızlı başlangıç öğreticisi, koyu temayı kullanan ekran görüntülerini içerir. Koyu temayı kullanıyorsanız ancak bunu öğrenmek için Visual Studio [IDE](quickstart-personalize-the-ide.md) ve Düzenleyici sayfasını kişiselleştirme sayfasına bakın.

## <a name="create-a-project"></a>Proje oluşturma

Başlamak için bir web uygulaması ASP.NET Core oluşturabilirsiniz. Proje türü, siz bir şey eklemeden önce web uygulaması oluşturmak için tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

1. Yeni Çalışma Alanı iletişim kutusunun **sol Project** **Visual C#** öğesini genişletin ve **ardından .NET Core'ı seçin.** Orta bölmede Web **Uygulaması'ASP.NET Core seçin.** <br/><br/>Ardından dosyanıza bir ad girin `HelloWorld` ve Tamam'ı **seçin.**

   ![C için yeni ASP.NET Core Web Uygulaması projesi oluşturma #](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > **.NET Core** proje şablonu kategorisini görmüyorsanız sol **bölmedeki** Visual Studio Yükleyicisi aç bağlantısını seçin. (Görüntü ayarlarınıza bağlı olarak, bunu görmek için kaydırmanız gerekebilir.)
   >
   > ![Yeni Visual Studio Yükleyicisi iletişim kutusundan dosya açma](../ide/media/open-visual-studio-installer.png)
   >
   > Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü ve** ardından Değiştir'i **seçin.**
   >
   > ![VS Yükleyicisi ASP.NET de iş yükü yükleme](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Yeni iş yükünü yüklemeye Visual Studio önce bu uygulamayı kapatmanız gerekir.)

1. Yeni **Web ASP.NET Core iletişim kutusunda,** üst **açılan menüden ASP.NET Core 2.1'i** seçin. Ardından Web **Uygulaması'ı ve** ardından Tamam'ı **seçin.**

   ![Yeni ASP.NET Core Web Uygulaması iletişim kutusu](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > ASP.NET Core **2.1'i görmüyorsanız, 2.1'in** en son yayınlarını Visual Studio. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için Güncelleştirme Visual Studio [en son sürüm sayfasına](../install/update-visual-studio.md) bakın.

Kısa süre sonra Visual Studio dosyanızı açar.

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="'Yeni proje oluştur' penceresini görüntüleme":::

1. Yeni **proje oluştur penceresinde Dil** **listesinden C#** dilini seçin. Ardından Platform **listesinden Windows'yi** ve proje türleri **listesinden Web'i** seçin.

      Dil, platform ve proje türü filtrelerini uyguladikten sonra, ASP.NET Core **Web Uygulaması** şablonunu ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="ASP.NET Core Web Uygulaması için C# şablonunu seçin":::

   > [!NOTE]
   > ASP.NET Core **Web Uygulaması** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Yükleyicisi web geliştirme ASP.NET **seçin.**
   >
   > ![.NET Core platformlar arası geliştirme iş yükü Visual Studio Yükleyicisi](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istenirse bunu yapma. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresinde,** Yeni projenizin adı kutusuna *HelloWorld* **Project girin.** Ardından, **Sonraki'yi seçin.**

    :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png" alt-text="'Yeni projenizi yapılandırma' penceresinde projenize 'MyCoreApp' adını girin":::

1. Ek **bilgiler penceresinde** üst açılan menüde **.NET Core 3.1'in** görüntülendiğinden emin olur. Kutuyu işaret ederek Docker desteğini etkinleştirmeyi seçebilirsiniz. Kimlik doğrulamasını değiştir düğmesine tıklayarak da kimlik doğrulaması desteği ebilirsiniz. Buradan şunları seçebilirsiniz:
    - Hiçbiri: Kimlik doğrulaması yok.
    - Bireysel hesaplar: Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: Bu seçenek kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygundur.
    
    **Docker'ı Etkinleştir kutusunu** işaretsiz bırakın ve Kimlik Doğrulama Türü **için Hiçbiri'yi** seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="../get-started/csharp/media/vs-2019/aspnet-core-additional-information.png" alt-text="'Ek bilgiler' penceresinde .NET Core 3.1'in seçili olduğundan emin olun ve tüm varsayılan değerleri bırakın":::

   Visual Studio projenizi açar.

::: moniker-end

## <a name="create-and-run-the-app"></a>Uygulamayı oluşturma ve çalıştırma

::: moniker range="vs-2017"

1. Dosyanın **Çözüm Gezgini** Sayfalar klasörünü **genişletin** ve **About.cshtml dosyasını seçin.**

   ![HelloWorld Visual Studio Çözüm Gezgini dosyaları gösteren ekran görüntüsü. Sayfalar klasörü genişletilir ve About.cshtml seçilir.](../ide/media/csharp-aspnet-about-page-html-file.png)

   Bu dosya, bir web tarayıcısında çalışan web uygulamasında **Hakkında** adlı bir sayfaya karşılık gelen bir sayfadır.

   ![Web uygulamasındaki Hakkında sayfası](../ide/media/csharp-aspnet-about-page.png)

   Düzenleyicide Hakkında sayfasının "ek bilgiler" alanına ilişkin HTML **kodunu** görebilirsiniz.

   ![Düzenleyicide ek bilgi alanına ilişkin HTML Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. "Ek bilgi" metnini "**Merhaba Dünya! ".**

   ![Visual Studio düzenleyicisinde ek bilgi alanı için varsayılan HTML Visual Studio değiştirme](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. Dosyanın **Çözüm Gezgini** **About.cshtml dosyasını genişletin** ve **About.cshtml.cs dosyasını seçin.** (Bu dosya bir web **tarayıcısında Hakkında** sayfasına da karşılık gelen bir dosyadır.)

   ![HelloWorld Visual Studio Çözüm Gezgini dosyaları gösteren ekran görüntüsü. About.cshtml genişletilir ve About.cshtml.cs seçilir.](../ide/media/csharp-aspnet-about-page-code-file.png)

   Düzenleyicide Hakkında sayfasının "uygulama açıklaması" alanı için metin içeren C# **kodunu** görebilirsiniz.

   ![Uygulama düzenleyicisinde uygulama açıklaması alanına ilişkin C# Visual Studio kodu](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. "Uygulama açıklaması" ileti metnini " İletim nedir? "**".**

   ![Uygulama açıklaması alanı için varsayılan ileti metnini düzenleyicide Visual Studio değiştirme](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Uygulamayı **IIS Express** çalıştırmak için **Ctrl** + **F5** tuşuna basın veya uygulamayı bir web tarayıcısında açın.

   ![Dosyanın IIS Express düğmesini Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > **'IIS Express' web** sunucusuna bağlanamıyor veya SSL sertifikasından bahseden bir hata iletisiyle ilgili bir hata iletisi alırsanız Visual Studio. Ardından, Visual Studio bağlam **menüsünden Yönetici** olarak çalıştır seçeneğini kullanarak bu seçeneği açın. Ardından uygulamayı yeniden çalıştırın.

1. Web tarayıcısında Hakkında sayfasında **güncelleştirilmiş metninizin** olduğunu doğrulayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Hakkında sayfasını görüntüleme](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Web tarayıcısını kapatın.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirme

Önceki bölümde tamamlamış olduğunu işi kontrol etmek için aşağıdaki animasyonu görüntüebilirsiniz.

  ![Basit bir C# .gif web uygulaması oluşturma ve çalıştırmayı gösteren animasyonlu ASP.NET Core dosyasını Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Tebrikler, bu Hızlı Başlangıç'a devam ediyoruz! C#, ASP.NET Core ve Visual Studio IDE (tümleşik geliştirme ortamı) hakkında biraz bilgi öğrendiğini umuyoruz.

::: moniker-end

::: moniker range=">=vs-2019"

1. Aşağıdaki **Çözüm Gezgini** Sayfalar klasörünü genişletin ve **Index.cshtml dosyasını seçin.** 

   ![Dosyadan Index.cshtml dosyasını Çözüm Gezgini](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Bu dosya, web uygulamasında web tarayıcısında çalışan **Giriş** adlı sayfaya karşılık geliyor.

   ![Web uygulamasındaki Hakkında sayfası](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   Düzenleyicide, Giriş sayfasında görüntülenen metnin HTML **kodunu** görebilirsiniz.

   ![Visual Studio düzenleyicisinde giriş sayfası için Index. cshtml dosyasındaki HTML kodu](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. "Hoş geldiniz" metnini "**Merhaba Dünya!**" okumak üzere değiştirin.

   ![Visual Studio düzenleyicide, bunun yerine Merhaba Dünya e-Welcome 'a hoş geldiniz varsayılan HTML kodunu değiştirin](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. uygulamayı   + çalıştırmak ve bir web tarayıcısında açmak için IIS Express seçin veya Ctrl **F5** tuşuna basın.

   ![Visual Studio IIS Express düğmesini seçin](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > **' IIS Express ' web sunucusuna** veya bir SSL sertifikasıyla ilgili bir hata iletisine bağlanmadığını belirten bir hata iletisi alırsanız, Visual Studio kapatın. sonra, sağ tıklama bağlam menüsünde **yönetici olarak çalıştır** seçeneğini kullanarak Visual Studio açın. Sonra, uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, **ana** sayfanın güncelleştirilmiş metninizi içerdiğini doğrulayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş giriş sayfasını görüntüleyin](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Web tarayıcısını kapatın.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

ASP.NET web uygulamaları oluşturma hakkında daha fazla bilgi edinmek için aşağıdaki öğreticiye geçin:

> [!div class="nextstepaction"]
> [ASP.NET C# ve Visual Studio ile çalışmaya başlama](../get-started/csharp/tutorial-aspnet-core.md)

Ya da, Docker ile Web uygulamanızı kapsayıya nasıl kapsayıleyeceğinizi öğrenin:

> [!div class="nextstepaction"]
> [Visual Studio kapsayıcı araçları](../containers/overview.md)

## <a name="see-also"></a>Ayrıca bkz.

[Web uygulamanızı Visual Studio kullanarak Azure App Service yayımlayın](../deployment/quickstart-deploy-to-azure.md)
