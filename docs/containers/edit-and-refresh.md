---
title: Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklama | Microsoft Docs
description: Yerel bir Docker kapsayıcısında çalışan bir uygulamayı değiştirmeyi, Düzenle ve Yenile aracılığıyla kapsayıcıyı yenilemeyi ve sonra hata ayıklama kesme noktalarını ayarlamayı öğrenin.
ms.author: ghogen
author: ghogen
manager: jmartens
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: how-to
ms.workload: multiple
ms.date: 03/08/2021
ms.technology: vs-container-tools
ms.openlocfilehash: 7faf85d07d0c6de4f559e038b47e1935886ac0c3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122104"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklama

Visual Studio, docker kapsayıcıları geliştirmek ve uygulamanızı yerel olarak doğrulamak için tutarlı bir yol sağlar.
uygulamalarınızı, Linux veya docker yüklü olan yerel Windows masaüstünüzde çalışan Windows kapsayıcılarda çalıştırabilir ve hata ayıklamanıza olanak sağlar ve her kod değişikliği yaptığınızda kapsayıcıyı yeniden başlatmanız gerekmez.

bu makalede, yerel bir docker kapsayıcısında bir uygulamayı başlatmak, değişiklikler yapmak ve sonra değişiklikleri görmek için tarayıcıyı yenilemek üzere Visual Studio nasıl kullanılacağı gösterilmektedir. Bu makalede ayrıca Kapsayıcılı uygulamalar için hata ayıklama için kesme noktalarının nasıl ayarlanacağı gösterilmektedir. desteklenen proje türleri .NET Framework ve .net Core web ve konsol uygulamalarını içerir. bu makalede, ASP.NET Core web apps ve .NET Framework konsol uygulamaları kullanırız.

desteklenen türde bir projeniz zaten varsa Visual Studio bir dockerfile oluşturabilir ve projenizi bir kapsayıcıda çalışacak şekilde yapılandırabilirsiniz. Bkz. [Visual Studio kapsayıcı araçları](overview.md).

## <a name="prerequisites"></a>Önkoşullar

Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklamak için aşağıdaki araçların yüklü olması gerekir:

::: moniker range="vs-2017"

* Web geliştirme iş yükü yüklü [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

* Web geliştirme iş yükü yüklü [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

::: moniker range="vs-2022"

* Web geliştirme iş yükü yüklüyken [2022 Visual Studio önizleme]()

::: moniker-end

Docker kapsayıcılarını yerel olarak çalıştırmak için yerel bir Docker istemciniz olmalıdır. Hyper-V kullanan ve Windows 10 gerektiren [Docker for Windows](https://www.docker.com/get-docker)kullanabilirsiniz.

docker kapsayıcıları .NET Framework ve .net Core projeleri için kullanılabilir. İki örneğe bakalım. İlk olarak, bir .NET Core Web uygulamasına göz atacağız. daha sonra, bir .NET Framework konsol uygulamasına göz atacağız.

## <a name="create-a-web-app"></a>Web uygulaması oluşturma

Bir projeniz varsa ve [genel bakış](overview.md)bölümünde açıklandığı gibi Docker desteği eklediyseniz, bu bölümü atlayın.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Kodunuzu düzenleyin ve yenileyin

Değişiklikleri hızlıca yinelemek için, uygulamanızı bir kapsayıcıda başlatabilirsiniz. Daha sonra, IIS Express istediğiniz gibi görüntüleyerek değişiklik yapmaya devam edin.

1. docker 'ın, kullanmakta olduğunuz kapsayıcı türünü (Linux veya Windows) kullanacak şekilde ayarlandığından emin olun. görev çubuğundaki docker simgesine sağ tıklayın ve **Linux kapsayıcılarına geç** ' i seçin ya da uygun şekilde **Windows kapsayıcılara geçiş** yapın.

1. (Yalnızca .NET Core 3 ve üzeri) Kodunuzun düzenlenmesine ve çalışan sitenin bu bölümde açıklandığı gibi yenilenmesi, .NET Core >= 3,0 ' deki varsayılan şablonlarda etkinleştirilmemiştir. etkinleştirmek için [Microsoft. aspnetcore. Mvc. Razor. runtimecompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)NuGet paketini ekleyin. *Startup. cs* dosyasında, `IMvcBuilder.AddRazorRuntimeCompilation` yöntemi içindeki koda uzantı yöntemine bir çağrı ekleyin `ConfigureServices` . Bu, yalnızca hata ayıklama modunda etkinleştirilir, bu nedenle bunu aşağıdaki gibi kodlayın:

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

    `Startup`Yöntemi aşağıdaki gibi değiştirin:

    ```csharp
    public Startup(IConfiguration configuration, IWebHostEnvironment webHostEnvironment)
    {
        Configuration = configuration;
        Env = webHostEnvironment;
    }
    ```

   Daha fazla bilgi için bkz. [ASP.NET Core Razor dosyası derlemesi](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1&preserve-view=true).

1. **Çözüm yapılandırmasını** **hata ayıklama** olarak ayarlayın. Ardından,  + Docker görüntünüzü derlemek ve yerel olarak çalıştırmak için CTRL **F5** tuşuna basın.

    kapsayıcı görüntüsü bir docker kapsayıcısında oluşturulup çalıştırıldığında, Visual Studio web uygulamasını varsayılan tarayıcınızda başlatır.

1. *Dizin* sayfasına gidin. Bu sayfada değişiklik yapacağız.
1. Visual Studio dönün ve *Index. cshtml* dosyasını açın.
1. Aşağıdaki HTML içeriğini dosyanın sonuna ekleyin ve değişiklikleri kaydedin.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Çıkış penceresinde, .NET Build tamamlandığında ve aşağıdaki satırları görürseniz, tarayıcınıza geri dönün ve sayfayı yenileyin:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Değişiklikleriniz uygulandı!

### <a name="debug-with-breakpoints"></a>Kesme noktalarıyla hata ayıkla

Genellikle, değişiklikler daha fazla inceleme gerektirir. bu görev için Visual Studio hata ayıklama özelliklerini kullanabilirsiniz.

1. Visual Studio ' de *Index. cshtml. cs* dosyasını açın.
2. `OnGet` yönteminin içeriğini aşağıdaki kodla değiştirin:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Kod satırının solunda bir kesme noktası ayarlayın.
4. Hata ayıklamayı başlatmak ve kesme noktasına isabet etmek için F5 'e basın.
5. kesme noktasını görüntülemek için Visual Studio değiştirin. Değerleri inceleyin.

   ![Visual Studio içindeki Index. cshtml. cs için kodun bir parçasını gösteren ekran görüntüsü, sarı renkle vurgulanmış bir kod satırının solunda ayarlanmış bir kesme noktası.](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app&quot;></a>.NET Framework konsol uygulaması oluşturma

.NET Framework konsol uygulaması projelerini kullandığınızda, düzenleme olmadan docker desteği ekleme seçeneği desteklenmez. Yalnızca tek bir Docker projesi kullanıyor olsanız bile aşağıdaki yordamı kullanabilirsiniz.

1. yeni bir .NET Framework konsol uygulaması projesi oluşturun.
1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve ardından   >  **kapsayıcı düzenleme desteği** Ekle ' yi seçin.  Görüntülenen iletişim kutusunda **Docker Compose**' yi seçin. Projenize bir Dockerfile eklenir ve ilişkili destek dosyalarına sahip bir Docker Compose projesi eklenir.

### <a name=&quot;debug-with-breakpoints&quot;></a>Kesme noktalarıyla hata ayıkla

1. Çözüm Gezgini, *program. cs*' yi açın.
2. `Main` yönteminin içeriğini aşağıdaki kodla değiştirin:

   ```csharp
       System.Console.WriteLine(&quot;Hello, world!");
   ```

3. Kod satırının soluna bir kesme noktası ayarlayın.
4. Hata ayıklamayı başlatmak için F5 tuşuna basın ve kesme noktasına gidin.
5. kesme noktasını görüntülemek ve değerleri denetlemek için Visual Studio ' ye geçin.

   ![Visual Studio içinde Program. cs için kod penceresinin ekran görüntüsü, sarı renkle vurgulanmış bir kod satırının solunda ayarlanmış bir kesme noktası ile.](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Kapsayıcı yeniden kullanımı

geliştirme çevrimi sırasında, dockerfile 'ı değiştirdiğinizde yalnızca kapsayıcı görüntülerinizi ve kapsayıcının kendisini yeniden oluşturur Visual Studio. dockerfile 'ı değiştirmezseniz, Visual Studio önceki bir çalıştırağından kapsayıcıyı yeniden kullanır.

kapsayıcınızı el ile değiştirdiyseniz ve temiz bir kapsayıcı görüntüsü ile yeniden başlatmak istiyorsanız, Visual Studio ' de **oluşturma**  >  **temiz** komutunu kullanın ve normal olarak oluşturun.

## <a name="troubleshoot"></a>Sorun giderme

[Visual Studio docker geliştirmede sorun gidermeyi](troubleshooting-docker-errors.md)öğrenin.

## <a name="next-steps"></a>Sonraki adımlar

[Visual Studio kapsayıcılı uygulamaları nasıl](container-build.md)kullandığını okuyarak daha fazla ayrıntı alın.

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Visual Studio, Windows ve Azure ile docker hakkında daha fazla bilgi

* [Visual Studio ile kapsayıcı geliştirmesi](./index.yml)hakkında daha fazla bilgi edinin.
* Bir Docker kapsayıcısı derlemek ve dağıtmak için bkz. [Azure Pipelines Için Docker tümleştirmesi](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Windows server ve Nano sunucu makalelerinin bir dizini için bkz. [Windows kapsayıcı bilgileri](/virtualization/windowscontainers/).
* [Azure Kubernetes hizmeti](https://azure.microsoft.com/services/kubernetes-service/) hakkında bilgi edinin ve [Azure Kubernetes hizmeti belgelerini](/azure/aks)gözden geçirin.
