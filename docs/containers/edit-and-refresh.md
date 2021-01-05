---
title: Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklama | Microsoft Docs
description: Yerel bir Docker kapsayıcısında çalışan bir uygulamayı değiştirmeyi, Düzenle ve Yenile aracılığıyla kapsayıcıyı yenilemeyi ve sonra hata ayıklama kesme noktalarını ayarlamayı öğrenin.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: how-to
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: de7065ebdf5426077418e50d2c03118de9f9d68f
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729307"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklama

Visual Studio, Docker Kapsayıcıları geliştirmek ve uygulamanızı yerel olarak doğrulamak için tutarlı bir yol sağlar.
Uygulamalarınızı, Docker yüklü olan yerel Windows masaüstünüzde çalışan Linux veya Windows kapsayıcılarında çalıştırabilir ve hata ayıklamanıza olanak sağlar ve her kod değişikliği yaptığınızda kapsayıcıyı yeniden başlatmanız gerekmez.

Bu makalede, yerel bir Docker kapsayıcısında bir uygulamayı başlatmak, değişiklikler yapmak ve sonra değişiklikleri görmek için tarayıcıyı yenilemek üzere Visual Studio 'Nun nasıl kullanılacağı gösterilmektedir. Bu makalede ayrıca Kapsayıcılı uygulamalar için hata ayıklama için kesme noktalarının nasıl ayarlanacağı gösterilmektedir. Desteklenen proje türleri .NET Framework ve .NET Core Web ve Konsol uygulamalarını içerir. Bu makalede, ASP.NET Core Web Apps ve .NET Framework konsol uygulamaları kullanırız.

Desteklenen türde bir projeniz zaten varsa, Visual Studio bir Dockerfile oluşturabilir ve projenizi bir kapsayıcıda çalışacak şekilde yapılandırabilir. Bkz. [Visual Studio 'Da kapsayıcı araçları](overview.md).

## <a name="prerequisites"></a>Ön koşullar

Yerel bir Docker kapsayıcısında uygulamalarda hata ayıklamak için aşağıdaki araçların yüklü olması gerekir:

::: moniker range="vs-2017"

* Web geliştirme iş yükünün yüklü olduğu [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

* Web geliştirme iş yükünün yüklü olduğu [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

Docker kapsayıcılarını yerel olarak çalıştırmak için yerel bir Docker istemciniz olmalıdır. Hyper-V kullanan ve Windows 10 gerektiren [Docker for Windows](https://www.docker.com/get-docker)kullanabilirsiniz.

Docker kapsayıcıları .NET Framework ve .NET Core projeleri için kullanılabilir. İki örneğe bakalım. İlk olarak, bir .NET Core Web uygulamasına göz atacağız. Daha sonra, bir .NET Framework konsol uygulamasına göz atacağız.

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

1. Docker 'ın, kullanmakta olduğunuz kapsayıcı türünü (Linux veya Windows) kullanacak şekilde ayarlandığından emin olun. Görev çubuğundaki Docker simgesine sağ tıklayın ve **Linux kapsayıcılarına geç** ' i seçin veya uygun şekilde **Windows kapsayıcılarına geçiş** yapın.

1. (Yalnızca .NET Core 3 ve üzeri) Kodunuzun düzenlenmesine ve çalışan sitenin bu bölümde açıklandığı gibi yenilenmesi, .NET Core >= 3,0 ' deki varsayılan şablonlarda etkinleştirilmemiştir. Etkinleştirmek için [Microsoft. AspNetCore. Mvc. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)NuGet paketini ekleyin. *Startup.cs*' de, `IMvcBuilder.AddRazorRuntimeCompilation` yöntemi içindeki koda uzantı yöntemine bir çağrı ekleyin `ConfigureServices` . Bu, yalnızca hata ayıklama modunda etkinleştirilir, bu nedenle bunu aşağıdaki gibi kodlayın:

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

    Kapsayıcı görüntüsü bir Docker kapsayıcısında oluşturulup çalıştırıldığında, Visual Studio varsayılan tarayıcınızda Web uygulamasını başlatır.

1. *Dizin* sayfasına gidin. Bu sayfada değişiklik yapacağız.
1. Visual Studio 'ya dönün ve *Index. cshtml* dosyasını açın.
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

Genellikle, değişiklikler daha fazla inceleme gerektirir. Bu görev için Visual Studio 'nun hata ayıklama özelliklerini kullanabilirsiniz.

1. Visual Studio 'da *Index.cshtml.cs*' yi açın.
2. `OnGet` yönteminin içeriğini aşağıdaki kodla değiştirin:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Kod satırının solunda bir kesme noktası ayarlayın.
4. Hata ayıklamayı başlatmak ve kesme noktasına isabet etmek için F5 'e basın.
5. Kesme noktasını görüntülemek için Visual Studio 'ya geçin. Değerleri inceleyin.

   ![Visual Studio 'da Index.cshtml.cs için kodun bir bölümünü, sarı renkle vurgulanmış bir kod satırının soluna ayarlanmış bir kesme noktası ile gösteren ekran görüntüsü.](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>.NET Framework konsol uygulaması oluşturma

.NET Framework konsol uygulaması projelerini kullandığınızda, düzenleme olmadan Docker desteği ekleme seçeneği desteklenmez. Yalnızca tek bir Docker projesi kullanıyor olsanız bile aşağıdaki yordamı kullanabilirsiniz.

1. Yeni bir .NET Framework konsol uygulaması projesi oluşturun.
1. Çözüm Gezgini, proje düğümüne sağ tıklayın ve ardından   >  **kapsayıcı düzenleme desteği** Ekle ' yi seçin.  Görüntülenen iletişim kutusunda **Docker Compose**' yi seçin. Projenize bir Dockerfile eklenir ve ilişkili destek dosyalarına sahip bir Docker Compose projesi eklenir.

### <a name="debug-with-breakpoints"></a>Kesme noktalarıyla hata ayıkla

1. Çözüm Gezgini ' de, *program.cs*' yi açın.
2. `Main` yönteminin içeriğini aşağıdaki kodla değiştirin:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Kod satırının soluna bir kesme noktası ayarlayın.
4. Hata ayıklamayı başlatmak için F5 tuşuna basın ve kesme noktasına gidin.
5. Kesme noktası ve İnceleme değerlerini görüntülemek için Visual Studio 'ya geçin.

   ![Visual Studio 'da Program.cs için kod penceresinin, sarı renkle vurgulanmış bir kod satırının soluna ayarlanmış bir kesme noktası ile ekran görüntüsü.](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Kapsayıcı yeniden kullanımı

Geliştirme çevrimi sırasında, Visual Studio Dockerfile 'ı değiştirdiğinizde yalnızca kapsayıcı görüntülerinizi ve kapsayıcının kendisini yeniden oluşturur. Dockerfile 'ı değiştirmezseniz, Visual Studio önceki bir çalıştırağından kapsayıcıyı yeniden kullanır.

Kapsayıcınızı el ile değiştirdiyseniz ve temiz bir kapsayıcı görüntüsü ile yeniden başlatmak istiyorsanız, Visual Studio 'daki **derleme**  >  **temiz** komutunu kullanın ve normal olarak oluşturun.

## <a name="troubleshoot"></a>Sorun giderme

[Visual Studio Docker geliştirmede sorun gidermeyi](troubleshooting-docker-errors.md)öğrenin.

## <a name="next-steps"></a>Sonraki adımlar

[Visual Studio 'nun Kapsayıcılı uygulamaları nasıl](container-build.md)kullandığını okuyarak daha fazla bilgi alın.

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Visual Studio, Windows ve Azure ile Docker hakkında daha fazla bilgi

* [Visual Studio ile kapsayıcı geliştirme](./index.yml)hakkında daha fazla bilgi edinin.
* Bir Docker kapsayıcısı derlemek ve dağıtmak için bkz. [Azure Pipelines Için Docker tümleştirmesi](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker).
* Windows Server ve nano sunucu makalelerinin bir dizini için bkz. [Windows kapsayıcı bilgileri](/virtualization/windowscontainers/).
* [Azure Kubernetes hizmeti](https://azure.microsoft.com/services/kubernetes-service/) hakkında bilgi edinin ve [Azure Kubernetes hizmeti belgelerini](/azure/aks)gözden geçirin.
