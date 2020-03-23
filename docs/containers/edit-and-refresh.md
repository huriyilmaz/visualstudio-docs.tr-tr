---
title: Yerel bir Docker konteynerinde hata ayıklama uygulamaları | Microsoft Dokümanlar
description: Yerel bir Docker kapsayıcısında çalışan bir uygulamayı nasıl değiştirip, Edit ve Refresh ile kapsayıcıyı yenileyerek ve hata ayıklama kesme noktalarını nasıl ayarladığını öğrenin.
ms.author: ghogen
author: ghogen
manager: jillfra
ms.assetid: 480e3062-aae7-48ef-9701-e4f9ea041382
ms.topic: conceptual
ms.workload: multiple
ms.date: 07/25/2019
ms.technology: vs-azure
ms.openlocfilehash: 9f1d80d540e9a25a3ef62ee0819c6f6655b9b3ab
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75916529"
---
# <a name="debug-apps-in-a-local-docker-container"></a>Yerel bir Docker konteynerinde hata ayıklama uygulamaları

Visual Studio, Docker kapsayıcıları geliştirmek ve uygulamanızı yerel olarak doğrulamak için tutarlı bir yol sağlar. Docker yüklüyken yerel Windows masaüstünüzde çalışan Linux veya Windows kapsayıcılarında uygulamalarınızı çalıştırıp hata ayıklayabilirsiniz ve her kod değişikliği yaptığınızda kapsayıcıyı yeniden başlatmanız gerekmez.

Bu makalede, yerel bir Docker kapsayıcısında bir uygulama başlatmak, değişiklik yapmak ve değişiklikleri görmek için tarayıcıyı yenilemek için Visual Studio'nun nasıl kullanılacağı gösterilmiştir. Bu makalede, kapsayıcı uygulamalar için hata ayıklama için kesme noktaları ayarlamak için nasıl gösterir. Desteklenen proje türleri arasında .NET Framework ve .NET Core web ve konsol uygulamaları yer almaktadır. Bu makalede, ASP.NET Core web uygulamalarını ve .NET Framework konsol uygulamalarını kullanıyoruz.

Zaten desteklenen bir türde bir projeniz varsa, Visual Studio bir Dockerfile oluşturabilir ve projenizi bir kapsayıcıda çalışacak şekilde yapılandırabilir. [Visual Studio'daki Konteyner Araçları'na](overview.md)bakın.

## <a name="prerequisites"></a>Önkoşullar

Uygulamaları yerel bir Docker kapsayıcısında hata ayıklamak için aşağıdaki araçların yüklenmesi gerekir:

::: moniker range="vs-2017"

* Web Geliştirme iş yükü yüklü [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

::: moniker-end

::: moniker range="vs-2019"

* Web Geliştirme iş yükü yüklü [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)

::: moniker-end

Docker konteynerlerini yerel olarak çalıştırmak için yerel bir Docker istemciniz olması gerekir. Hyper-V'nin devre dışı bırakılmasını gerektiren [Docker Araç Kutusu'nu](https://www.docker.com/products/docker-toolbox)kullanabilirsiniz. Hyper-V kullanan ve Windows 10 gerektiren [Docker for Windows'u](https://www.docker.com/get-docker)da kullanabilirsiniz.

Docker konteynerleri .NET Framework ve .NET Core projeleri için kullanılabilir. İki örnşeye bakalım. İlk olarak bir .NET Core web uygulamasına bakıyoruz. Daha sonra bir .NET Framework konsol uygulamasına bakıyoruz.

## <a name="create-a-web-app"></a>Web uygulaması oluşturma

Bir projeniz varsa ve [genel bakışta](overview.md)açıklandığı gibi Docker desteği eklediyseniz, bu bölümü atlayın.

::: moniker range="vs-2017"
[!INCLUDE [create-aspnet5-app](../azure/includes/create-aspnet5-app.md)]
::: moniker-end
::: moniker range=">= vs-2019"
[!INCLUDE [create-aspnet5-app-2019](../azure/includes/vs-2019/create-aspnet5-app-2019.md)]
::: moniker-end

### <a name="edit-your-code-and-refresh"></a>Kodunuzu ve yenilemenizi

Değişiklikleri hızlı bir şekilde doğrulamak için uygulamanızı bir kapsayıcıda başlatabilirsiniz. Ardından, Değişiklikleri IIS Express'te olduğu gibi görüntüleyerek yapmaya devam edin.

1. Docker'ın kullanmakta olduğunuz kapsayıcı türünü (Linux veya Windows) kullanacak şekilde ayarlandığınızdan emin olun. Görev Çubuğu'ndaki Docker simgesine sağ tıklayın ve uygun şekilde **Linux kapsayıcılarına Geçiş'i** veya **Windows kapsayıcılarına geçiş'i** seçin.

1. (.NET Core 3 ve daha sonra sadece) Kodunuzu düzenleme ve bu bölümde açıklandığı gibi çalışan siteyi yenilemek .NET Core >= 3.0'daki varsayılan şablonlarda etkinleştirilemez. Etkinleştirmek için, NuGet paketi [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)ekleyin. *Startup.cs,* `IMvcBuilder.AddRazorRuntimeCompilation` `ConfigureServices` yöntemdeki koda uzantı yöntemine bir çağrı ekleyin. Bunun yalnızca HATA Ayıklama modunda etkinleştirilmesi gerekir, bu nedenle aşağıdaki gibi kodlayın:

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

   Daha fazla bilgi için [ASP.NET Core'daki Razor dosya derlemesi'ne](/aspnet/core/mvc/views/view-compilation?view=aspnetcore-3.1)bakın.

1. **Çözüm Yapılandırmasını** **Hata Ayıklama**olarak ayarlayın. Ardından, Docker resminizi oluşturmak ve yerel olarak çalıştırmak için **Ctrl**+**F5** tuşuna basın.

    Kapsayıcı görüntüsü bir Docker kapsayıcısında oluşturulup çalıştırıldığında, Visual Studio varsayılan tarayıcınızda web uygulamasını başlatır.

1. *Dizin* sayfasına gidin. Bu sayfada değişiklikler yapacağız.
1. Visual Studio'ya dönün ve *Index.cshtml'i*açın.
1. Aşağıdaki HTML içeriğini dosyanın sonuna ekleyin ve değişiklikleri kaydedin.

    ```html
    <h1>Hello from a Docker container!</h1>
    ```

1. Çıktı penceresinde,.NET yapısı tamamlandığında ve aşağıdaki satırları gördüğünüzde tarayıcınıza geri dönve sayfayı yenileyin:

   ```output
   Now listening on: http://*:80
   Application started. Press Ctrl+C to shut down.
   ```

Değişiklikleriniz uygulandı!

### <a name="debug-with-breakpoints"></a>Kesme noktaları yla hata ayıklama

Genellikle, değişiklikler daha fazla denetim gerektirir. Bu görev için Visual Studio'nun hata ayıklama özelliklerini kullanabilirsiniz.

1. Visual Studio'da, *açık Index.cshtml.cs.*
2. Yöntemin `OnGet` içeriğini aşağıdaki kodla değiştirin:

   ```csharp
       ViewData["Message"] = "Your application description page from within a container";
   ```

3. Kod satırının solunda bir kesme noktası ayarlayın.
4. Hata ayıklamaya başlamak ve kesme noktasına basmak için F5 tuşuna basın.
5. Kesme noktasını görüntülemek için Visual Studio'ya geçin. Değerleri inceleyin.

   ![Kesme noktası](media/edit-and-refresh/breakpoint.png)

## <a name="create-a-net-framework-console-app"></a>Bir .NET Framework konsol uygulaması oluşturma

.NET Framework konsol uyrum uygulaması projelerini kullandığınızda, düzenleme olmadan Docker desteği ekleme seçeneği desteklenmez. Yalnızca tek bir Docker projesi kullanıyor sanız bile aşağıdaki yordamı kullanmaya devam edebilirsiniz.

1. Yeni bir .NET Framework Console uygulama projesi oluşturun.
1. Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve ardından**Kapsayıcı Düzenleme Desteği** **Ekle'yi** > seçin.  Görünen iletişim kutusunda **Docker Oluştur'u**seçin. Projenize bir Dockerdosyası eklenir ve ilişkili destek dosyalarıiçeren bir Docker Compose projesi eklenir.

### <a name="debug-with-breakpoints"></a>Kesme noktaları yla hata ayıklama

1. Çözüm Gezgini'nde, *Program.cs*açın.
2. Yöntemin `Main` içeriğini aşağıdaki kodla değiştirin:

   ```csharp
       System.Console.WriteLine("Hello, world!");
   ```

3. Kod satırının solunda bir kesme noktası ayarlayın.
4. Hata ayıklamaya başlamak ve kesme noktasına basmak için F5 tuşuna basın.
5. Kesme noktasını görüntülemek ve değerleri incelemek için Visual Studio'ya geçin.

   ![Kesme noktası](media/edit-and-refresh/breakpoint-console.png)

## <a name="container-reuse"></a>Konteyner yeniden kullanımı

Geliştirme döngüsü sırasında Visual Studio, Dockerfile'ı değiştirdiğinizde yalnızca konteyner görüntülerinizi ve konteynerin kendisini yeniden sağlar. Dockerfile'yi değiştirmezseniz, Visual Studio kapsayıcıyı daha önceki bir çalıştırmadan yeniden kullanır.

Kapsayıcınızı el ile değiştirdiyseniz ve temiz bir kapsayıcı görüntüsüyle yeniden başlatmak istiyorsanız, Visual Studio'daki > **TemizLe** komutunu kullanın ve normal olarak oluşturun. **Build**

## <a name="troubleshoot"></a>Sorun giderme

[Visual Studio Docker geliştirme](troubleshooting-docker-errors.md)sini nasıl gidereceklerini öğrenin.

## <a name="next-steps"></a>Sonraki adımlar

[Visual Studio'nun kapsayıcı uygulamaları nasıl oluşturduğunu](container-build.md)okuyarak daha fazla ayrıntı edinin.

## <a name="more-about-docker-with-visual-studio-windows-and-azure"></a>Visual Studio, Windows ve Azure ile Docker hakkında daha fazla şey

* [Visual Studio ile konteyner geliştirme](/visualstudio/containers)hakkında daha fazla bilgi edinin.
* Docker kapsayıcısı oluşturmak ve dağıtmak [için Azure Boru Hatları için Docker tümleştirmesi'ne](https://marketplace.visualstudio.com/items?itemName=ms-vscs-rm.docker)bakın.
* Windows Server ve Nano Server makalelerinin bir dizini için [Windows kapsayıcı bilgilerine](/virtualization/windowscontainers/)bakın.
* Azure [Kubernetes Hizmeti](https://azure.microsoft.com/services/kubernetes-service/) hakkında bilgi edinin ve [Azure Kubernetes Hizmeti belgelerini](/azure/aks)inceleyin.
