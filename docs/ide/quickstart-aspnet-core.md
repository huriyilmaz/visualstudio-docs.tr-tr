---
title: "C 'de ASP.NET Core web uygulaması oluşturma #"
description: C# ve ASP.NET Core, adım adım Visual Studio basit bir Merhaba Dünya web uygulamasının nasıl oluşturulacağını öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635982"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>hızlı başlangıç: ilk ASP.NET Core web uygulamanızı oluşturmak için Visual Studio kullanın

Visual Studio nasıl kullanılacağına ilişkin bu 5-10 dakika içinde, ASP.NET proje şablonunu ve C# programlama dilini kullanarak basit bir "Merhaba Dünya" web uygulaması oluşturacaksınız.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range="vs-2022"

henüz 2022 önizleme Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio 2022 önizleme indirmeleri](https://visualstudio.microsoft.com/vs/preview/vs2022) sayfasına gidin.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Temanızı seçin (isteğe bağlı)

Bu Hızlı Başlangıç Öğreticisi, koyu temayı kullanan ekran görüntüleri içerir. koyu tema kullanmıyorsanız, ancak bunu yapmak istiyorsanız, nasıl yapılacağını öğrenmek için [Visual Studio ıde ve düzenleyiciyi kişiselleştirme](quickstart-personalize-the-ide.md) sayfasına bakın.

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

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   :::image type="content" source="../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="' Yeni proje oluştur ' penceresini görüntüleyin":::

1. **Yeni proje oluştur** penceresinde dil listesinden **C#** ' ı seçin. ardından, Platform listesinden **Windows** ve proje türleri listesinden **Web** ' i seçin.

      dili, platformu ve proje türü filtrelerini uyguladıktan sonra, **ASP.NET Core Web uygulaması** şablonunu seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="ASP.NET Core Web uygulaması için C# şablonunu seçin":::

   > [!NOTE]
   > **ASP.NET Core Web uygulaması** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > ardından, Visual Studio Yükleyicisi **ASP.NET ve web geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .net Core platformlar arası geliştirme iş yükü](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenirse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin. Ardından, bu "[Proje oluşturma](#create-a-project)" yordamında 2. adıma geri dönün.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *HelloWorld* yazın veya girin. Ardından **İleri**' yi seçin.

    :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png" alt-text="' yeni projenizi yapılandırın ' penceresinde, ' MyCoreApp ' projenizi adlandırın":::

1. **Ek bilgi** penceresinde, **.NET Core 3,1** ' ın üst açılan menüde göründüğünü doğrulayın. Kutuyu işaretleyerek Docker desteğini etkinleştirmeyi seçebileceğinizi unutmayın. Kimlik doğrulamasını Değiştir düğmesine tıklayarak da kimlik doğrulama desteği ekleyebilirsiniz. Buradan buradan seçim yapabilirsiniz:
    - Hiçbiri: kimlik doğrulaması yok.
    - Bireysel hesaplar: Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: bu seçenek, kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygun.
    
    **Docker 'ı etkinleştir** kutusunu işaretsiz bırakın ve kimlik doğrulama türü için **hiçbiri** ' ni seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="../get-started/csharp/media/vs-2019/aspnet-core-additional-information.png" alt-text="' ek bilgi ' penceresinde, .NET Core 3,1 ' in seçildiğinden emin olun ve tüm varsayılanları bırakın":::

   Visual Studio, yeni projenizi açacak.

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

   ![Visual Studio düzenleyicisinde ek bilgi alanı için varsayılan HTML kodunu değiştirme](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. **Çözüm Gezgini** **. cshtml**' i genişletin ve ardından **. cshtml. CS hakkında**' yı seçin. (Bu dosya Ayrıca, bir Web tarayıcısında **hakkında hakkında** sayfasına karşılık gelir.)

   ![HelloWorld projesindeki dosyaları gösteren Visual Studio Çözüm Gezgini ekran görüntüsü. . Cshtml hakkında genişletilir ve. cshtml. CS hakkında seçilidir.](../ide/media/csharp-aspnet-about-page-code-file.png)

   Düzenleyicide, **hakkında** sayfasının "uygulama açıklaması" alanı için metin Içeren C# kodu görürsünüz.

   ![Visual Studio düzenleyicisinde uygulama açıklaması alanı için C# kodu](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. "Uygulama açıklaması" ileti metnini "**My m?**" okunacak şekilde değiştirin.

   ![Visual Studio düzenleyicisinde uygulama açıklaması alanı için varsayılan ileti metnini değiştirme](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. uygulamayı   + çalıştırmak ve bir web tarayıcısında açmak için IIS Express seçin veya Ctrl **F5** tuşuna basın.

   ![Visual Studio IIS Express düğmesini seçin](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > **' IIS Express ' web sunucusuna** veya bir SSL sertifikasıyla ilgili bir hata iletisine bağlanmadığını belirten bir hata iletisi alırsanız, Visual Studio kapatın. sonra, sağ tıklama bağlam menüsünde **yönetici olarak çalıştır** seçeneğini kullanarak Visual Studio açın. Sonra, uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, **hakkında** sayfasının güncelleştirilmiş metninizi içerdiğini doğrulayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş hakkında sayfasını görüntüleyin](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Web tarayıcısını kapatın.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirin

Önceki bölümde tamamladığınız işi denetlemek için aşağıdaki animasyonu görüntüleyin.

  ![içinde basit bir C# ASP.NET Core web uygulamasının nasıl oluşturulacağını ve çalıştırılacağını gösteren animasyonlu .gif dosyasını görüntüleyin Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Tebrikler, bu hızlı başlangıcı Tamamlanıyor! C#, ASP.NET Core ve Visual Studio ıde (tümleşik geliştirme ortamı) hakkında biraz bilgi edindiniz.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Çözüm Gezgini**, **Sayfalar** klasörünü genişletin ve **Index. cshtml**' yi seçin.

   ![Çözüm Gezgini Index. cshtml dosyasını seçin](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Bu dosya, bir Web tarayıcısında çalışan Web uygulamasında **giriş** adlı bir sayfaya karşılık gelir.

   ![Web uygulamasındaki hakkında sayfası](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   Düzenleyicide, **giriş** sayfasında görüntülenen metnin HTML kodunu görürsünüz.

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
