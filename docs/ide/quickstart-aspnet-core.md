---
title: "C'de ASP.NET Core web uygulaması oluşturma #"
description: Visual Studio'da C# ve ASP.NET Core ile adım adım basit bir Hello World web uygulaması oluşturmayı öğrenin.
ms.custom: mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1873c11d8f2e6243a0dc0f867e579f1927cd1607
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579969"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Quickstart: İlk ASP.NET Core web uygulamanızı oluşturmak için Visual Studio'yı kullanın

Visual Studio'nun nasıl kullanılacağına bu 5-10 dakikalık girişte, ASP.NET bir proje şablonu ve C# programlama dilini kullanarak basit bir "Hello World" web uygulaması oluşturacaksınız.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="install-visual-studio"></a>Visual Studio yükleme

::: moniker range="vs-2017"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Temanızı seçin (isteğe bağlı)

Bu hızlı başlangıç öğreticikaranlık tema kullanan ekran görüntüleri içerir. Karanlık temayı kullanmıyorsanız ancak kullanmak istiyorsanız, nasıl yapılacağını öğrenmek için [Visual Studio IDE ve Editor](quickstart-personalize-the-ide.md) sayfasını Kişiselleştir sayfasına bakın.

## <a name="create-a-project"></a>Proje oluşturma

Başlamak için bir ASP.NET Core web uygulaması projesi oluşturursunuz. Proje türü, bir web uygulaması oluşturmak için tüm şablon dosyalarıyla birlikte gelir, daha bir şey eklemeden önce!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.

1. **Yeni Proje** iletişim kutusunun sol bölmesinde **Visual C#** seçeneğini genişletin ve **ardından .NET Core'u**seçin. Orta bölmede, **Core Web Uygulaması ASP.NET**seçin. <br/><br/>Ardından, dosyanızı `HelloWorld` adlandırın ve **Tamam'ı**seçin.

   ![C için yeni ASP.NET Çekirdek Web Uygulaması projesi oluşturma #](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > **.NET Core** proje şablonu kategorisini görmüyorsanız, sol bölmedeki **Açık Visual Studio Yükleyici** bağlantısını seçin. (Ekran ayarlarınıza bağlı olarak, görüntülemek için kaydırmanız gerekebilir.)
   >
   > ![Yeni proje iletişim kutusundan Visual Studio Yükleyicisini Aç](../ide/media/open-visual-studio-installer.png)
   >
   > Visual Studio Installer başlattı. ASP.NET **ve web geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.
   >
   > ![VS Yükleyici'de ASP.NET iş yükü](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Yeni iş yükünü yüklemeye devam etmeden önce Visual Studio'yu kapatmanız gerekebilir.)

1. Yeni **ASP.NET Çekirdek Web Uygulaması** iletişim kutusunda, üst açılır menüden **Core 2.1ASP.NET'yi** seçin. Ardından, **Web Uygulaması'nı**seçin ve ardından **Tamam'ı**seçin.

   ![Yeni ASP.NET Çekirdek Web Uygulaması iletişim kutusu](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > **Core 2.1ASP.NET**görmüyorsanız Visual Studio'nun en son sürümünde olduğunuzu unutmayın. Yüklemenizi nasıl güncelleştirin izleyin, [görsel stüdyoyu en son sürüm sayfasına](../install/update-visual-studio.md) güncelleştir sayfasına bakın.

Kısa bir süre sonra Visual Studio proje dosyanızı açar.

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   !['Yeni proje oluşturma' penceresini görüntüleme](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur** penceresinde, arama kutusuna *ASP.NET* girin veya yazın. Ardından, Dil listesinden **C#'yi** seçin ve ardından Platform listesinden **Windows'u** seçin.

   Dil ve platform filtrelerini uyguladıktan **sonra, ASP.NET Çekirdek Web Uygulaması** şablonunu seçin ve sonra **İleri'yi**seçin.

   ![ASP.NET Çekirdek Web Uygulaması için C# şablonunu seçin](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > ASP.NET Çekirdek Web **Uygulaması** şablonu görmüyorsanız, **yeni bir proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Aradığınızı bulamıyor' iletisinden 'Daha fazla araç ve özellik yükleyin' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Installer'da **ASP.NET ve web geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyici'de ASP.NET Temel Web Uygulaması iş yükü](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Bundan sonra Visual Studio Installer'daki **Değiştir** düğmesini seçin. Çalışmanızı kaydetmeniz istenebilir; eğer öyleyse, bunu yapın. Ardından, iş yükünü yüklemeye **devam** et'i seçin. Daha sonra, bu "[Proje oluştur](#create-a-project)" yordamındaki 2.

1. Yeni **proje pencerenizi Yapılandır'da,** **Project ad** kutusuna *HelloWorld* yazın veya girin. Ardından **Oluştur'u**seçin.

   !['Yeni projenizi yapılandır' penceresinde, projenize 'HelloWorld' adını](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. Yeni **bir ASP.NET Core Web Uygulaması Oluşturma** penceresinde, ASP.NET Core **3.0'ın** üst açılır menüde göründüğünü doğrulayın. Ardından, örnek Razor Pages içeren **Web Uygulaması'nı**seçin. Sonra, **Oluştur'u**seçin.

   !['Yeni bir ASP.NET Çekirdek Web Uygulaması Oluşturma' penceresi](../get-started/csharp/media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio yeni projenizi açıyor.

::: moniker-end

## <a name="create-and-run-the-app"></a>Uygulamayı oluşturma ve çalıştırma

::: moniker range="vs-2017"

1. Çözüm **Gezgini'nde,** **Sayfalar** klasörünü genişletin ve ardından **About.cshtml'i**seçin.

   ![Çözüm Gezgini'nden About.cshtml dosyasını seçin](../ide/media/csharp-aspnet-about-page-html-file.png)

   Bu dosya, web uygulamasında Web tarayıcısında çalışan **Hakkında** adlı bir sayfaya karşılık gelir.

   ![Web uygulamasında Hakkında sayfası](../ide/media/csharp-aspnet-about-page.png)

   Düzenleyicide, **Hakkında** sayfanın "ek bilgi" alanı için HTML kodunu görürsünüz.

   ![Visual Studio düzenleyicisindeki ek bilgi alanının HTML kodu](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. "**Hello World!**" "ek bilgi" metnini değiştirin.

   ![Visual Studio düzenleyicisindeki ek bilgi alanının varsayılan HTML kodunu değiştirme](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. Çözüm **Gezgini'nde,** **About.cshtml'i**genişletin ve ardından **About.cshtml.cs**seçin. (Bu dosya aynı zamanda bir web tarayıcısında **hakkında** sayfa ile karşılık gelir.)

   ![Çözüm Gezgini'nden About.cshtml dosyasını seçin](../ide/media/csharp-aspnet-about-page-code-file.png)

   Düzenleyicide, **Hakkında** sayfanın "uygulama açıklaması" alanına ilişkin metin içeren C# kodunu görürsünüz.

   ![Visual Studio düzenleyicisindeki uygulama açıklama alanı için C# kodu](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. "Uygulama açıklaması" ileti metnini "**Mesajım nedir?"**"i bareni" olarak değiştirin.

   ![Visual Studio düzenleyicisindeki uygulama açıklama alanı için varsayılan ileti metnini değiştirme](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Uygulamayı çalıştırmak ve bir web tarayıcısında açmak için **IIS Express'i** seçin veya **Ctrl**+**F5** tuşuna basın.

   ![Visual Studio'da IIS Express düğmesini seçin](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Web **sunucusuna bağlanamayan 'IIS Express'** veya SSL sertifikasından bahseden bir hata iletisi alırsanız Visual Studio'yı kapatın. Ardından, sağ tıklatma bağlam menüsünden **Yönetici olarak Çalıştır** seçeneğini kullanarak Visual Studio'yu açın. Ardından, uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, **Hakkında** sayfasının güncelleştirilmiş metninizi içerdiğini doğrulayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Hakkında sayfasını görüntüleyin](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Web tarayıcısını kapatın.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirin

Önceki bölümde tamamladığınız çalışmayı denetlemek için aşağıdaki animasyonu görüntüleyin.

  ![Visual Studio'da basit bir C# ASP.NET Core web uygulamasının nasıl oluşturulup çalıştırılabildiğini gösteren animasyonlu .gif dosyasını görüntüleyin](../ide/media/csharp-aspnet-animated-hello-world.gif)

Bu Quickstart'ı tamamladığınız için tebrikler! C#, ASP.NET Core ve Visual Studio IDE (entegre geliştirme ortamı) hakkında biraz bilgi edindiğinizi umuyoruz.

::: moniker-end

::: moniker range="vs-2019"

1. Çözüm **Gezgini'nde,** **Sayfalar** klasörünü genişletin ve ardından **Index.cshtml'i**seçin.

   ![Çözüm Gezgini'nden Index.cshtml dosyasını seçin](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Bu dosya, web uygulamasında Ana **Sayfa** adlı ve bir web tarayıcısında çalışan bir sayfaya karşılık gelir.

   ![Web uygulamasında Hakkında sayfası](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   Düzenleyicide, **Giriş** sayfasında görünen metnin HTML kodunu görürsünüz.

   ![Visual Studio düzenleyicisindeki Ana sayfa için Index.cshtml dosyasındaki HTML kodu](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. "**Merhaba Dünya!**" "ı okumak için "Hoş Geldiniz" metnini değiştirin.

   ![Visual Studio düzenleyicisinde, yerine Merhaba Dünya deyinkabul edin diyen varsayılan HTML kodunu değiştirin](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Uygulamayı çalıştırmak ve bir web tarayıcısında açmak için **IIS Express'i** seçin veya **Ctrl**+**F5** tuşuna basın.

   ![Visual Studio'da IIS Express düğmesini seçin](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Web **sunucusuna bağlanamayan 'IIS Express'** veya SSL sertifikasından bahseden bir hata iletisi alırsanız Visual Studio'yı kapatın. Ardından, sağ tıklatma bağlam menüsünden **Yönetici olarak Çalıştır** seçeneğini kullanarak Visual Studio'yu açın. Ardından, uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, **Ana** Sayfanın güncelleştirilmiş metninizi içerdiğini doğrulayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş Giriş sayfasını görüntüleme](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Web tarayıcısını kapatın.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Visual Studio'da C# ve ASP.NET ile başlayın](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio'u kullanarak web uygulamanızı Azure Uygulama Hizmeti'nde yayımlayın](../deployment/quickstart-deploy-to-azure.md)
