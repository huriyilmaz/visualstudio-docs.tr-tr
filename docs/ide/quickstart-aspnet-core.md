---
title: "C'ASP.NET Core web uygulaması oluşturma #"
description: C# ve Merhaba Dünya adım Visual Studio basit bir ASP.NET Core web uygulaması oluşturma hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: 552630497554e66ae8dcf673f5c10cc695ea163c
ms.sourcegitcommit: d38d1b083322019663fec7d1d85a4cda456aadca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135534036"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Hızlı Başlangıç: Visual Studio web uygulamasını oluşturmak için ASP.NET Core kullanma

Visual Studio'yi kullanmaya 5-10 dakikalık bir giriş olarak, ASP.NET proje şablonu ve C# programlama dili kullanarak basit bir "Merhaba Dünya" web uygulaması oluşturabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

::: moniker range="vs-2017"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range=">=vs-2019"

Henüz yüklemedıysanız Visual Studio yüklemek [için Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeler sayfasına gidin.

::: moniker-end

::: moniker range="<=vs-2019"
### <a name="choose-your-theme-optional"></a>Temanızı seçin (isteğe bağlı)

Bu hızlı başlangıç öğreticisi, koyu temayı kullanan ekran görüntülerini içerir. Koyu temayı kullanmadıysanız ama nasıl öğrenmek istediğiniz hakkında bilgi edinmek için bkz. Nasıl: [IDE'Visual Studio düzenleyiciyi kişiselleştirme.](quickstart-personalize-the-ide.md)

::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

Başlamak için bir web uygulaması ASP.NET Core oluşturabilirsiniz. Proje türü, siz bir şey eklemeden önce web uygulaması oluşturmak için tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

1. Yeni Çalışma Alanı iletişim kutusunun **sol Project** **Visual C#** öğesini genişletin ve **.NET Core'ı seçin.** Orta bölmede Web **Uygulaması'ASP.NET Core seçin.** <br/><br/>Ardından dosyanıza bir ad girin `HelloWorld` ve Tamam'ı **seçin.**

   ![C için yeni ASP.NET Core Web Uygulaması projesi oluşturma #](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > **.NET Core** proje şablonu kategorisini görmüyorsanız sol **bölmedeki** Visual Studio Yükleyicisi aç bağlantısını seçin. (Görüntü ayarlarınıza bağlı olarak, bunu görmek için kaydırmanız gerekebilir.)
   >
   > ![Yeni Visual Studio Yükleyicisi iletişim kutusundan dosya açma](../ide/media/open-visual-studio-installer.png)
   >
   > Uygulama Visual Studio Yükleyicisi başlatıyor. Web geliştirme **ASP.NET iş yükünü ve** ardından Değiştir'i **seçin.**
   >
   > ![ASP.NET Yükleyicisi'ne iş yükü yükleme](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Yeni iş yükünü yüklemeye Visual Studio önce bu uygulamayı kapatmanız gerekir.)

1. Yeni **Web ASP.NET Core iletişim kutusunda,** üst **açılan menüden ASP.NET Core 2.1'i** seçin. Ardından Web **Uygulaması'ı ve** ardından Tamam'ı **seçin.**

   ![Yeni ASP.NET Core Web Uygulaması iletişim kutusu](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > **ASP.NET Core 2.1'i görmüyorsanız, 2.1'in** en son Visual Studio. Yüklemenizi güncelleştirme hakkında daha fazla bilgi için Güncelleştirme Visual Studio [en son sürüm sayfasına](../install/update-visual-studio.md) bakın.

Kısa süre sonra Visual Studio dosyanızı açar.

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="../get-started/media/vs-2019/create-new-project-dark-theme.png" alt-text="'Yeni proje oluştur' Visual Studio vurgulanmış başlangıç penceresini gösteren ekran görüntüsü.":::

1. Yeni **proje oluştur penceresinde Dil** **listesinden C#** dilini seçin. Ardından Platform **listesinden Windows'yi** ve proje türleri **listesinden Web'i** seçin.

   Dil, platform ve proje türü filtrelerini uyguladikten sonra, ASP.NET Core **Web Uygulaması** şablonunu ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-create-new-project-aspnet-core.png" alt-text="'C#', 'Windows' ve 'Web' üzerinde filtrelenmiş 'Yeni proje oluştur' penceresini gösteren ekran görüntüsü. 'ASP.NET Core Web Uygulaması' proje şablonu vurgulanmış.":::

   > [!NOTE]
   > ASP.NET Core **Web Uygulaması** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Ne arayabilirsiniz? iletisiyle vurgulanan 'Daha fazla araç ve özellik yükle' bağlantısını gösteren ekran görüntüsü.](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Yükleyicisi web geliştirme **ASP.NET iş yükünü** seçin.
   >
   > ![Uygulamanın .NET Core platformlar arası geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istenirse bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresinde,** Yeni projenizin adı kutusuna *HelloWorld* **Project girin.** Ardından, **Sonraki'yi seçin.**

    :::image type="content" source="../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-hello-world-project.png" alt-text="'Yeni projenizi yapılandır' penceresini, &quot;Yeni projeniz&quot; adı alanına 'HelloWorld' Project gösteren ekran görüntüsü.":::

1. Ek **bilgiler penceresinde** üst açılan **menüde .NET Core 3.1'in** görüntülendiğinden emin olur. Kutuyu işaret ederek Docker desteğini etkinleştirmeyi seçebilirsiniz. Kimlik doğrulamasını değiştir düğmesine tıklayarak da kimlik doğrulaması desteği ebilirsiniz. Buradan şunları seçebilirsiniz:
    - Hiçbiri: Kimlik doğrulaması yok.
    - Bireysel hesaplar: Bunlar yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: Bu seçenek kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygundur.
    
    **Docker'ı Etkinleştir kutusunun** işaretini kaldırın ve Kimlik Doğrulama Türü **için Hiçbiri'ne** tıklayın. Ardından **Oluştur**’u seçin.

   :::image type="content" source="../get-started/csharp/media/vs-2019/aspnet-core-additional-information.png" alt-text="Çerçeve alanında '.NET Core 3.1' seçilmiş Ek bilgiler penceresini gösteren ekran görüntüsü.":::

   Visual Studio projenizi açar.

::: moniker-end

::: moniker range=">=vs-2022"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="media/vs-2022/create-new-project-dark-theme.png" alt-text="'Yeni proje oluştur' Visual Studio vurgulanmış başlangıç penceresini gösteren ekran görüntüsü.":::

1. Yeni **proje oluştur penceresinde Dil** **listesinden C#** dilini seçin. Ardından Platform **listesinden Windows'yi** ve proje türleri **listesinden Web'i** seçin.

   Dil, platform ve proje türü filtrelerini uyguladikten sonra, ASP.NET Core **Web Uygulaması** şablonunu ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/csharp-create-new-project-aspnet-core.png" alt-text="'C#', 'Windows' ve 'Web' üzerinde filtrelenmiş 'Yeni proje oluştur' penceresini gösteren ekran görüntüsü. 'ASP.NET Core Web Uygulaması' proje şablonu vurgulanmış.":::

   > [!NOTE]
   > ASP.NET Core **Web Uygulaması** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > :::image type="content" source="media/vs-2022/not-finding-what-looking-for.png" alt-text="'Ne arayabilirsiniz? iletisiyle vurgulanan 'Daha fazla araç ve özellik yükle' bağlantısını gösteren ekran görüntüsü.":::
   >
   > Ardından, Visual Studio Yükleyicisi web geliştirme **ASP.NET iş yükünü** seçin.
   >
   > :::image type="content" source="media/vs-2022/aspnet-core-web-dev-workload.png" alt-text="Uygulamanın .NET Core platformlar arası geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.":::
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istenirse bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin. Ardından bu "Proje oluşturma" yordamının[2. adımına](#create-a-project)geri dön.

1. Yeni **projenizi yapılandır penceresinde,** Yeni projenizin adı kutusuna *HelloWorld* **Project girin.** Ardından, **Sonraki'yi seçin.**

    :::image type="content" source="media/vs-2022/csharp-name-your-aspnet-hello-world-project.png" alt-text="'Yeni projenizi yapılandır' penceresini, &quot;Yeni projeniz&quot; adı alanına 'HelloWorld' Project gösteren ekran görüntüsü.":::

1. Ek **bilgiler penceresinde** Framework **alanında .NET 6.0'ın** **görüntülendiğinden emin** olur. Kutuyu işaret ederek Docker desteğini etkinleştirmeyi seçebilirsiniz. Kimlik doğrulama türü açılan listesinden bir değer seçerek **de kimlik doğrulaması** desteği ekleyebilirsiniz. Buradan şunları seçebilirsiniz:

    - Hiçbiri: Kimlik doğrulaması yok.
    - Bireysel hesaplar: Bu kimlik doğrulamaları yerel veya Azure tabanlı bir veritabanında depolanır.
    - Microsoft kimlik platformu: Bu seçenek kimlik doğrulaması için Active Directory, Azure AD veya Microsoft 365 kullanır.
    - Windows: intranet uygulamaları için uygundur.
    
    **Docker'ı Etkinleştir kutusunu** işaretsiz bırakın ve Kimlik doğrulaması türü **için Hiçbiri'yi** seçin. Ardından **Oluştur**’u seçin.

   :::image type="content" source="media/vs-2022/aspnet-core-additional-information.png" alt-text="Çerçeve alanında '.NET 6.0' seçili ek bilgiler penceresini gösteren ekran görüntüsü.":::

   Visual Studio projenizi açar.

::: moniker-end

## <a name="create-and-run-the-app"></a>Uygulamayı oluşturma ve çalıştırma

::: moniker range="vs-2017"

1. dosya **Çözüm Gezgini** Sayfalar klasörünü **genişletin** ve **About.cshtml dosyasını seçin.**

   ![HelloWorld Visual Studio Çözüm Gezgini dosyaları gösteren ekran görüntüsü. Sayfalar klasörü genişletilir ve About.cshtml seçilir.](../ide/media/csharp-aspnet-about-page-html-file.png)

   Bu dosya, bir web tarayıcısında çalışan web **uygulamasında Hakkında** adlı bir sayfaya karşılık gelen bir sayfadır.

   ![Web uygulamasındaki Hakkında sayfası](../ide/media/csharp-aspnet-about-page.png)

   Düzenleyicide Hakkında sayfasının "ek bilgiler" alanına ilişkin HTML **kodunu** görebilirsiniz.

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

   ![Visual Studio IIS Express düğmesini seçin](../ide/media/csharp-aspnet-hello-world-iis-button.png)

   > [!NOTE]
   > **' IIS Express ' web sunucusuna** veya bir SSL sertifikasıyla ilgili bir hata iletisine bağlanmadığını belirten bir hata iletisi alırsanız, Visual Studio kapatın. sonra, sağ tıklama bağlam menüsünde **yönetici olarak çalıştır** seçeneğini kullanarak Visual Studio açın. Sonra, uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, **hakkında** sayfasının güncelleştirilmiş metninizi içerdiğini doğrulayın.

   ![Yaptığınız değişiklikleri içeren güncelleştirilmiş hakkında sayfasını görüntüleyin](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Web tarayıcısını kapatın.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirin

Önceki bölümde tamamladığınız işi denetlemek için aşağıdaki animasyonu görüntüleyin.

  ![içinde basit bir C# ASP.NET Core web uygulamasının nasıl oluşturulacağını ve çalıştırılacağını gösteren animasyonlu .gif dosyasını görüntüleyin Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Tebrikler, bu hızlı başlangıcı Tamamlanıyor! C#, ASP.NET Core ve Visual Studio ıde (tümleşik geliştirme ortamı) hakkında biraz daha öğrendiklerinizi umuyoruz.

::: moniker-end

::: moniker range="vs-2019"

1. **Çözüm Gezgini**, **Sayfalar** klasörünü genişletin ve **Index. cshtml**' yi seçin.

   ![Çözüm Gezgini genişletilmiş sayfalar klasörü içinde seçilen ' Index. cshtml ' öğesini gösteren ekran görüntüsü.](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Bu dosya, bir Web tarayıcısında çalışan Web uygulamasında **giriş** adlı bir sayfaya karşılık gelir.

   ![Tarayıcı penceresinde Web uygulamasının giriş sayfasını gösteren ekran görüntüsü.](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   Düzenleyicide, **giriş** sayfasında görüntülenen metnin HTML kodunu görürsünüz.

   ![Visual Studio kodu düzenleyicisindeki giriş sayfası için Index. cshtml dosyasını gösteren ekran görüntüsü.](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. "Hoş geldiniz" metnini "**Merhaba Dünya!**" okumak üzere değiştirin.

   ![Visual Studio kod düzenleyicisinde ' Welcome ' metni ' Merhaba Dünya! ' olarak değiştirilen ' Index. cshtml ' dosyasını gösteren ekran görüntüsü.](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. uygulamayı   + çalıştırmak ve bir web tarayıcısında açmak için IIS Express seçin veya Ctrl **F5** tuşuna basın.

   ![Visual Studio vurgulanmış IIS Express düğmesini gösteren ekran görüntüsü.](../ide/media/vs-2019/csharp-aspnet-generic-iis-button.png)

   > [!NOTE]
   > **' IIS Express ' web sunucusuna** veya bir SSL sertifikasıyla ilgili bir hata iletisine bağlanmadığını belirten bir hata iletisi alırsanız, Visual Studio kapatın. sonra, sağ tıklama bağlam menüsünde **yönetici olarak çalıştır** seçeneğini kullanarak Visual Studio açın. Sonra, uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, **ana** sayfanın güncelleştirilmiş metninizi içerdiğini doğrulayın.

   ![' Merhaba Dünya! ' güncelleştirilmiş iletisiyle tarayıcı penceresinde Web uygulamasının giriş sayfasını gösteren ekran görüntüsü.](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Web tarayıcısını kapatın.

::: moniker-end

::: moniker range=">=vs-2022"

1. **Çözüm Gezgini**, **Sayfalar** klasörünü genişletin ve **Index. cshtml**' yi seçin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-index-page-cshtml-file.png" alt-text="Çözüm Gezgini genişletilmiş sayfalar klasörü içinde seçilen ' Index. cshtml ' öğesini gösteren ekran görüntüsü.":::

   Bu dosya, bir Web tarayıcısında çalışan Web uygulamasında **giriş** adlı bir sayfaya karşılık gelir.

   :::image type="content" source="media/vs-2022/csharp-aspnet-index-page.png" alt-text="Tarayıcı penceresinde Web uygulamasının giriş sayfasını gösteren ekran görüntüsü.":::

   Düzenleyicide, **giriş** sayfasında görüntülenen metnin HTML kodunu görürsünüz.

   :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml.png" alt-text="Visual Studio kodu düzenleyicisindeki giriş sayfası için Index. cshtml dosyasını gösteren ekran görüntüsü.":::

1. "Hoş geldiniz" metnini "**Merhaba Dünya!**" okumak üzere değiştirin.

   :::image type="content" source="media/vs-2022/csharp-aspnet-index-cshtml-page-hello-world.png" alt-text="Visual Studio kod düzenleyicisinde ' Welcome ' metni ' Merhaba Dünya! ' olarak değiştirilen ' Index. cshtml ' dosyasını gösteren ekran görüntüsü.":::

1. uygulamayı   + çalıştırmak ve bir web tarayıcısında açmak için IIS Express seçin veya Ctrl **F5** tuşuna basın.

   :::image type="content" source="media/vs-2022/csharp-aspnet-generic-iis-button.png" alt-text="Visual Studio vurgulanmış IIS Express düğmesini gösteren ekran görüntüsü.":::

   > [!NOTE]
   > **' IIS Express ' web sunucusuna** veya bir SSL sertifikasıyla ilgili bir hata iletisine bağlanmadığını belirten bir hata iletisi alırsanız, Visual Studio kapatın. sonra, sağ tıklama bağlam menüsünde **yönetici olarak çalıştır** seçeneğini kullanarak Visual Studio açın. Sonra, uygulamayı yeniden çalıştırın.

1. Web tarayıcısında, **ana** sayfanın güncelleştirilmiş metninizi içerdiğini doğrulayın.

   :::image type="content" source="media/vs-2022/csharp-aspnet-index-page-hello-world.png" alt-text="' Merhaba Dünya! ' güncelleştirilmiş iletisiyle tarayıcı penceresinde Web uygulamasının giriş sayfasını gösteren ekran görüntüsü.":::

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

[Web uygulamanızı Visual Studio kullanarak Azure App Service yayımlayın](../deployment/quickstart-deploy-aspnet-web-app.md)
