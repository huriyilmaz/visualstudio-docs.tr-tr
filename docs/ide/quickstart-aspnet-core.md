---
title: "C 'de ASP.NET Core Web uygulaması oluşturma #"
description: Visual Studio 'da C# ve ASP.NET Core, adım adım ile basit bir Merhaba Dünya Web uygulaması oluşturmayı öğrenin.
ms.custom: mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: f9f442757b60b7dc9dc0e2dd0b8eba0c4928976b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959525"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Hızlı başlangıç: ilk ASP.NET Core Web uygulamanızı oluşturmak için Visual Studio 'Yu kullanma

Bu 5-10 dakika içinde, Visual Studio 'Yu nasıl kullanacağınızı gösteren bir ASP.NET proje şablonu ve C# programlama dili kullanarak basit bir "Merhaba Dünya" Web uygulaması oluşturacaksınız.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Temanızı seçin (isteğe bağlı)

Bu Hızlı Başlangıç Öğreticisi, koyu temayı kullanan ekran görüntüleri içerir. Koyu tema kullanmıyorsanız, ancak isterseniz, nasıl yapılacağını öğrenmek için [Visual STUDIO IDE ve düzenleyici 'Yi kişiselleştirme](quickstart-personalize-the-ide.md) sayfasına bakın.

## <a name="create-a-project"></a>Proje oluşturma

Başlamak için bir ASP.NET Core Web uygulaması projesi oluşturacaksınız. Proje türü, bir Web uygulaması oluşturmak için tüm şablon dosyalarıyla birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğundan **Dosya** > **Yeni** > **Proje**' yi seçin.

1. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#**' ı genişletin ve ardından **.NET Core**' u seçin. Orta bölmede **ASP.NET Core Web uygulaması**' nı seçin. <br/><br/>Sonra, Dosyanızı adlandırın `HelloWorld` ve **Tamam**' ı seçin.

   ![C için yeni ASP.NET Core Web uygulaması projesi oluşturma #](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > **.NET Core** proje şablonu kategorisini görmüyorsanız sol bölmedeki **Visual Studio yükleyicisi aç** bağlantısını seçin. (Görüntü ayarlarınıza bağlı olarak, görmek için kaydırmanız gerekebilir.)
   >
   > ![Yeni proje iletişim kutusundan Visual Studio Yükleyicisi aç](../ide/media/open-visual-studio-installer.png)
   >
   > Visual Studio Yükleyicisi başlatılır. **ASP.net ve Web geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.
   >
   > ![VS yükleyicisinde ASP.NET iş yükü](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Yeni iş yükünü yüklemeye devam edebilmeniz için önce Visual Studio 'Yu kapatmanız gerekebilir.)

1. **Yeni ASP.NET Core Web uygulaması** iletişim kutusunda üst açılan menüden **ASP.NET Core 2,1** ' ı seçin. Sonra, **Web uygulaması**' nı ve ardından **Tamam**' ı seçin.

   ![Yeni ASP.NET Core Web uygulaması iletişim kutusu](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > **ASP.NET Core 2,1** görmüyorsanız, Visual Studio 'nun en son sürümünü çalıştırdığınızdan emin olun. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için bkz. [Visual Studio 'yu en son sürüm sayfasına güncelleştirme](../install/update-visual-studio.md) .

Yakında, Visual Studio proje dosyanızı açar.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde, arama kutusuna *ASP.net* girin veya yazın. Ardından, dil listesinden **C#** öğesini seçin ve ardından platform listesinden **Windows** ' u seçin.

   Dil ve platform filtrelerini uyguladıktan sonra, **ASP.NET Core Web uygulaması** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![ASP.NET Core Web uygulaması için C# şablonunu seçin](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > **ASP.NET Core Web uygulaması** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından Visual Studio Yükleyicisi, **ASP.net ve Web geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi Web uygulaması iş yükünü ASP.NET Core](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Bundan sonra Visual Studio Yükleyicisi **Değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *HelloWorld* yazın veya girin. Ardından **Oluştur**' u seçin.

   ![' yeni projenizi yapılandırın ' penceresinde, projenizi ' HelloWorld ' olarak adlandırın](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. **Yeni ASP.NET Core Web uygulaması oluştur** penceresinde, **ASP.NET Core 3,0** ' ın üst açılan menüde göründüğünü doğrulayın. Ardından, örnek Razor Pages içeren **Web uygulaması**' nı seçin. Sonra  **Oluştur**' u seçin.

   ![' Yeni ASP.NET Core Web uygulaması oluşturma ' penceresi](../get-started/csharp/media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio yeni projenizi açar.

::: moniker-end

## <a name="create-and-run-the-app"></a>Uygulamayı oluşturma ve çalıştırma

::: moniker range="vs-2017"

1. **Çözüm Gezgini**, **Sayfalar** klasörünü genişletin ve ardından **. cshtml**' yi seçin.

   ![HelloWorld projesindeki dosyaları gösteren Visual Studio Çözüm Gezgini ekran görüntüsü. Sayfalar klasörü genişletilir ve. cshtml hakkında seçilidir.](../ide/media/csharp-aspnet-about-page-html-file.png)

   Bu dosya, bir Web tarayıcısında çalışan Web uygulamasında **hakkında** adlı bir sayfaya karşılık gelir.

   ![Web uygulamasındaki hakkında sayfası](../ide/media/csharp-aspnet-about-page.png)

   Düzenleyicide, **hakkında** sayfasının "ek bilgiler" alanı için HTML kodu görürsünüz.

   ![Visual Studio düzenleyicisinde ek bilgi alanı için HTML kodu](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. "Ek bilgiler" metnini "**Merhaba Dünya!**" okumak için değiştirin.

   ![Visual Studio Düzenleyicisi 'nde ek bilgi alanı için varsayılan HTML kodunu değiştirme](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. **Çözüm Gezgini** **. cshtml**' i genişletin ve ardından **About.cshtml.cs**' ı seçin. (Bu dosya Ayrıca, bir Web tarayıcısında **hakkında hakkında** sayfasına karşılık gelir.)

   ![HelloWorld projesindeki dosyaları gösteren Visual Studio Çözüm Gezgini ekran görüntüsü. . Cshtml hakkında genişletilmiş ve About.cshtml.cs seçilidir.](../ide/media/csharp-aspnet-about-page-code-file.png)

   Düzenleyicide, **hakkında** sayfasının "uygulama açıklaması" alanı için metin Içeren C# kodu görürsünüz.

   ![Visual Studio düzenleyicisinde uygulama açıklaması alanı için C# kodu](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. "Uygulama açıklaması" ileti metnini "**My m?**" okunacak şekilde değiştirin.

   ![Visual Studio Düzenleyicisi 'nde uygulama açıklaması alanı için varsayılan ileti metnini değiştirme](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Uygulamayı   + çalıştırmak ve bir Web tarayıcısında açmak için IIS Express seçin veya CTRL **F5** tuşuna basın.

   ![Visual Studio 'da IIS Express düğmesini seçin](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > **' IIS Express ' Web sunucusuna** veya bir SSL sertifikasıyla ilgili bir hata iletisine bağlanmadığını belirten bir hata iletisi alırsanız, Visual Studio 'yu kapatın. Ardından, sağ tıklama bağlam menüsünde **yönetici olarak çalıştır** seçeneğini kullanarak Visual Studio 'yu açın. Sonra, uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, **hakkında** sayfasının güncelleştirilmiş metninizi içerdiğini doğrulayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş hakkında sayfasını görüntüleyin](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Web tarayıcısını kapatın.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirin

Önceki bölümde tamamladığınız işi denetlemek için aşağıdaki animasyonu görüntüleyin.

  ![Visual Studio 'da basit bir C# ASP.NET Core Web uygulaması oluşturmayı ve çalıştırmayı gösteren animasyonlu. gif dosyasını görüntüleme](../ide/media/csharp-aspnet-animated-hello-world.gif)

Tebrikler, bu hızlı başlangıcı Tamamlanıyor! C#, ASP.NET Core ve Visual Studio IDE (tümleşik geliştirme ortamı) hakkında biraz bilgi edindiniz.

::: moniker-end

::: moniker range="vs-2019"

1. **Çözüm Gezgini**, **Sayfalar** klasörünü genişletin ve **Index. cshtml**' yi seçin.

   ![Çözüm Gezgini Index. cshtml dosyasını seçin](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Bu dosya, bir Web tarayıcısında çalışan Web uygulamasında **giriş** adlı bir sayfaya karşılık gelir.

   ![Web uygulamasındaki hakkında sayfası](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   Düzenleyicide, **giriş** sayfasında görüntülenen metnin HTML kodunu görürsünüz.

   ![Visual Studio Düzenleyicisi 'ndeki giriş sayfası için Index. cshtml dosyasındaki HTML kodu](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. "Hoş geldiniz" metnini "**Merhaba Dünya!**" okumak üzere değiştirin.

   ![Visual Studio Düzenleyicisi 'nde, bunun yerine Merhaba Dünya e-Welcome 'a hoş geldiniz varsayılan HTML kodunu değiştirin](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Uygulamayı   + çalıştırmak ve bir Web tarayıcısında açmak için IIS Express seçin veya CTRL **F5** tuşuna basın.

   ![Visual Studio 'da IIS Express düğmesini seçin](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > **' IIS Express ' Web sunucusuna** veya bir SSL sertifikasıyla ilgili bir hata iletisine bağlanmadığını belirten bir hata iletisi alırsanız, Visual Studio 'yu kapatın. Ardından, sağ tıklama bağlam menüsünde **yönetici olarak çalıştır** seçeneğini kullanarak Visual Studio 'yu açın. Sonra, uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, **ana** sayfanın güncelleştirilmiş metninizi içerdiğini doğrulayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş giriş sayfasını görüntüleyin](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Web tarayıcısını kapatın.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Visual Studio 'da C# ve ASP.NET kullanmaya başlama](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Ayrıca bkz.

[Web uygulamanızı Visual Studio 'Yu kullanarak Azure App Service yayımlayın](../deployment/quickstart-deploy-to-azure.md)
