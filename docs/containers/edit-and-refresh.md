---
title: Yerel bir Docker kapsayıcısı kapsayıcısı içinde uygulamaların | Microsoft Docs
description: Yerel Bir Docker kapsayıcısı içinde çalışan bir uygulamayı değiştirmeyi, Düzenle ve Yenile aracılığıyla kapsayıcıyı yenilemeyi ve ardından hata ayıklama kesme noktaları ayarlamayı öğrenin.
ms.author: ghogen
author: ghogen
manager: jmartens
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: how-to
ms.workload: multiple
ms.date: 10/27/2021
ms.technology: vs-container-tools
ms.openlocfilehash: 44d74c9ae684a5578f302f6333985c0372c9ff7c
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132001996"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Yerel Docker kapsayıcısı içinde uygulamalarda hata ayıklama

Visual Studio Docker kapsayıcıları geliştirmenin ve yerel olarak doğrulamanın tutarlı bir yolunu sağlar.
Docker'ın yüklü olduğu yerel Windows masaüstünüzde çalışan Linux veya Windows kapsayıcılarında uygulamalarınızı çalıştırabilir ve hata ayıklaması yapmak için her kod değişikliğinde kapsayıcıyı yeniden başlatmanız gerekmemektedir.

Bu makalede, Visual Studio yerel bir Docker kapsayıcısında uygulama başlatmak, değişiklikler yapmak ve ardından değişiklikleri görmek için tarayıcıyı yenilemek için nasıl kullanabileceğiniz açıklanmıştır. Bu makalede ayrıca kapsayıcılı uygulamalarda hata ayıklama için kesme noktaları ayarlama da açıklanmıştır. Desteklenen proje türleri, .NET Framework .NET Core web ve konsol uygulamalarını içerir. Bu makalede, web uygulamaları ASP.NET Core konsol uygulamaları için .NET Framework kullan kullanırsınız.

Desteklenen türde bir projeniz zaten varsa, Visual Studio dockerfile oluşturabilir ve projenizi kapsayıcıda çalıştıracak şekilde yapılandırabilirsiniz. Bkz. [Kapsayıcı Araçları Visual Studio.](overview.md)

## <a name="prerequisites"></a>Önkoşullar

Yerel bir Docker kapsayıcısı içinde uygulamaların hatasını ayıklamak için aşağıdaki araçların yüklü olması gerekir:

::: moniker range="vs-2017"

* Visual Studio Geliştirme iş yükünün yüklü olduğu [2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sürümü

::: moniker-end

::: moniker range="vs-2019"

* Visual Studio Geliştirme iş yükünün yüklü olduğu [2019](https://visualstudio.microsoft.com/downloads) sürümü

::: moniker-end

::: moniker range="vs-2022"

* Visual Studio Geliştirme iş yükünün yüklü olduğu [2022](https://visualstudio.microsoft.com/downloads) sürümü

::: moniker-end

Docker kapsayıcılarını yerel olarak çalıştırmak için yerel bir Docker istemciniz olması gerekir. Daha sonra veya daha yeni bir uygulama gerektiren [Docker Desktop](https://www.docker.com/get-docker)Windows 10 kullanabilirsiniz.

Docker kapsayıcıları, .NET Framework .NET Core projeleri için kullanılabilir. Şimdi iki örnekle bakalım. İlk olarak bir .NET Core web uygulamasına göz atabilirsiniz. Ardından bir konsol uygulamasına .NET Framework bakabilirsiniz.

## <a name="create-a-web-app"></a>Web uygulaması oluşturma

Bir projeniz varsa ve genel bakış bölümünde açıklandığı gibi Docker desteği [eklediyebilirsiniz.](overview.md)Bu bölümü atlayabilirsiniz.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range="vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end
::: moniker range=">=vs-2022"
[!INCLUDE [create-aspnet5-app-2022](../azure/includes/vs-2022/create-aspnet5-app-2022.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Kodunuzu düzenleme ve yenileme

Değişiklikleri hızla tekrar etmek için kapsayıcıda uygulama başlatabilirsiniz. Ardından değişiklik yapmaya devam edecek ve bu değişiklikleri dosyalarda olduğu gibi IIS Express.

1. Docker'ın, kullanmakta olduğu kapsayıcı türünü (Linux veya Windows) kullanmak üzere ayarlanmış olduğundan emin olun. Görev çubuğunda Docker simgesine sağ tıklayın ve Linux kapsayıcılara geç veya **Uygun** şekilde **Windows'yi** seçin.

1. (Yalnızca .NET Core 3 ve sonrası) Kodunuzu düzenleme ve bu bölümde açıklandığı gibi çalışan siteyi yenileme, .NET Core'daki varsayılan şablonlarda >= 3.0'da etkinleştirilmez. Etkinleştirmek için [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)NuGet paketini ekleyin. *Startup.cs* içinde, yönteminde koda uzantı `IMvcBuilder.AddRazorRuntimeCompilation` yöntemine bir çağrı `ConfigureServices` ekleyin. Bunun yalnızca HATA AYıKLAMA modunda etkinleştirilmesi gerekir, bu nedenle aşağıdaki gibi kodlayın:

    ```csharp
    public IWebHostEnvironment Env { get; set; }

    public void ConfigureServices(IServiceCollection services)
    {
        IMvcBuilder builder = services.AddRazorPages();

    #if DEBUG
        if (Env.IsDevelopment())
        {
            builder.AddRazorRuntimeCompilation();
        }
    #endif

        // code omitted for brevity
    }
    ```

    yöntemini `Startup` aşağıdaki gibi değiştirin:

    ```csharp
    public Startup(IConfiguration configuration, IWebHostEnvironment webHostEnvironment)
    {
        Configuration = configuration;
        Env = webHostEnvironment;
    }
    ```

   Daha fazla bilgi için bkz. [ASP.NET Core.](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1&preserve-view=true).

1. Çözüm **Yapılandırmasını Hata** Ayıklama **olarak ayarlayın.** Ardından **Ctrl** + **F5 tuşlarına** basarak Docker görüntülerinizi yerel olarak çalıştırın.

    Kapsayıcı görüntüsü bir Docker kapsayıcısında yerleşik olarak Visual Studio web uygulamasını varsayılan tarayıcınızdan başlatıyor.

1. Dizin *sayfasına* gidin. Bu sayfada değişiklikler yapacak.
1. Visual Studio *index.cshtml dosyasını açın.*
1. Aşağıdaki HTML içeriğini dosyanın sonuna ekleyin ve değişiklikleri kaydedin.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Çıkış penceresinde.NET derlemesi tamamlandığında ve aşağıdaki satırları gördüğünüzde tarayıcınıza geri dönüp sayfayı yenileyin:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Değişiklikleriniz uygulandı!

### <a name="debug-with-breakpoints"></a>Kesme noktalarıyla hata ayıklama

Değişiklikler genellikle daha fazla inceleme gerektirir. Bu görev için uygulamanın hata ayıklama Visual Studio kullanabilirsiniz.

1. Bu Visual Studio *Index.cshtml.cs dosyasını açın.*
2. `OnGet` yönteminin içeriğini aşağıdaki kodla değiştirin:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Kod çizgisinin sol tarafından bir kesme noktası ayarlayın.
4. Hata ayıklamayı başlatmak için F5 tuşuna basın.
5. Kesme Visual Studio görüntülemek için Visual Studio'ye geçiş. Değerleri inceleme.

   :::moniker range="vs-2019"
   ![Kod satırına sarı renkle vurgulanmış bir kesme noktası Visual Studio index.cshtml.cs kodunun bir bölümünü gösteren ekran görüntüsü.](media/edit-and-refresh/breakpoint.png)
   :::moniker-end
   :::moniker range=">=vs-2022"
   ![Kod satırına sarı renkle vurgulanmış bir kesme noktası Visual Studio index.cshtml.cs kodunun bir bölümünü gösteren ekran görüntüsü.](media/edit-and-refresh/vs-2022/breakpoint.png)
   :::moniker-end

## <a name="create-a-net-framework-console-app"></a>.NET Framework konsol uygulaması oluşturma

Konsol uygulaması .NET Framework, düzenleme olmadan Docker desteği ekleme seçeneği desteklenmiyor. Yalnızca tek bir Docker projesi kullanıyor olsa bile aşağıdaki yordamı kullanmaya devam edin.

1. Konsol uygulaması .NET Framework yeni bir uygulama oluşturun.
1. Bu Çözüm Gezgini proje düğümüne sağ tıklayın ve Kapsayıcı Düzenleme **Desteği**  >  **Ekle'yi seçin.**  Görüntülenen iletişim kutusunda, öğesini seçin **Docker Compose.** Projenize bir Dockerfile eklenir ve ilişkili destek Docker Compose bir proje eklenir.

### <a name="debug-with-breakpoints"></a>Kesme noktalarıyla hata ayıklama

1. Bu Çözüm Gezgini *Program.cs'yi açın.*
2. `Main` yönteminin içeriğini aşağıdaki kodla değiştirin:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Kod çizgisinin sol tarafından bir kesme noktası ayarlayın.
4. Hata **ayıklamayı başlatmak** için F5 tuşuna basın ve kesme noktalarına basın.
5. Kesme Visual Studio görüntülemek ve değerleri incelemek için Visual Studio'ye geçiş.

   :::moniker range="<=vs-2019"
   ![Program.cs için kod penceresinin ekran görüntüsü Visual Studio sarıyla vurgulanmış bir kod çizgisinin sol tarafından ayarlanmış bir kesme noktası.](media/edit-and-refresh/breakpoint-console.png)
   ::: moniker-end

## <a name="container-reuse"></a>Kapsayıcıyı yeniden kullanma

Geliştirme döngüsü sırasında, Visual Studio dockerfile'ı değiştiriyorken yalnızca kapsayıcı görüntülerinizi ve kapsayıcının kendisini yeniden yapılandırır. Dockerfile'ı değiştirmiyorsanız, Visual Studio önceki bir çalıştırmadan kapsayıcıyı yeniden kullanılır.

Kapsayıcınızı el ile değiştirdikten sonra temiz bir kapsayıcı görüntüsüyle yeniden başlatmak için Visual Studio'de Build Clean komutunu kullanın ve  >   ardından normal şekilde derlemeyi deneyin.

## <a name="troubleshoot"></a>Sorun giderme

[Docker geliştirmeyle ilgili Visual Studio öğrenin.](troubleshooting-docker-errors.md)

## <a name="next-steps"></a>Sonraki adımlar

Kapsayıcılı uygulamalar oluşturma [hakkında Visual Studio daha fazla ayrıntı edinin.](container-build.md)

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Visual Studio, Windows ve Azure ile Docker hakkında daha fazla bilgi

* Visual Studio [ile kapsayıcı geliştirme hakkında daha fazla bilgi Visual Studio.](./index.yml)
* Docker kapsayıcısı derlemek ve dağıtmak için bkz. [docker tümleştirmesi Azure Pipelines.](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker)
* Windows Server ve Nano Sunucu makalelerinin dizini için [bkz. Windows bilgileri.](/virtualization/windowscontainers/)
* Hakkında bilgi [Azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/) ve Azure Kubernetes Service [gözden geçirme.](/azure/aks)
