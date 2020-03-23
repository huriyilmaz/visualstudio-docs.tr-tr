---
title: Docker Compose & ASP.NET Core kullanarak multicontainer öğretici
author: ghogen
description: Docker Compose ile birden fazla kapsayıcıyı nasıl kullanacağınızı öğrenin
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: b9e1a2fc7c9027c34aeb8a0e0d1d44fdb0211e65
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77027325"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Öğretici: Docker Compose ile çok konteynerli bir uygulama oluşturun

Bu eğitimde, Visual Studio'da Konteyner Araçları kullanırken birden fazla konteynırı nasıl yöneteceğinizi ve aralarında iletişim kurmayı öğreneceksiniz.  Birden çok *konteynırı* yönetmek konteyner düzenlemegerektirir ve Docker Compose, Kubernetes veya Service Fabric gibi bir orkestratör gerektirir. Burada Docker Compose'u kullanacağız. Docker Compose geliştirme döngüsü sırasında yerel hata ayıklama ve test için harika.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Web **Geliştirme,** **Azure Araçları** iş yükü veya **.NET Core çapraz platform geliştirme** iş yükü yüklü
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) Web **Geliştirme,** **Azure Araçları** iş yükü ve/veya **.NET Core çapraz platform geliştirme** iş yükü yüklü
* [.NET Core 2.2 Geliştirme Araçları](https://dotnet.microsoft.com/download/dotnet-core/2.2) .NET Core 2.2 ile
* [.NET Core 3 Geliştirme Araçları](https://dotnet.microsoft.com/download/dotnet-core/3.1) ile .NET Core 3.1.
::: moniker-end

## <a name="create-a-web-application-project"></a>Web Uygulaması projesi oluşturma

Visual Studio'da, ASP.NET **Çekirdek Web** `WebFrontEnd`Uygulaması projesi oluşturun. Razor sayfalarında bir web uygulaması oluşturmak için **Web Uygulaması'nı** seçin. 
  
::: moniker range="vs-2017"

**Docker Desteğini Etkinleştir'i**seçmeyin. Docker desteğini daha sonra eklersiniz.

![Web projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Web projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

**Docker Desteğini Etkinleştir'i**seçmeyin. Docker desteğini daha sonra eklersiniz.

![Web projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Web API projesi oluşturma

Aynı çözüme bir proje ekleyin ve *MyWebAPI*deyin. Proje türü olarak **API'yi** seçin ve **HTTPS için Yapılandırma**onay kutusunu temizleyin. Bu tasarımda, SSL'yi yalnızca istemciyle iletişim için kullanıyoruz, aynı web uygulamasındaki kapsayıcılar arasındaki iletişim için değil. Yalnızca `WebFrontEnd` HTTPS'ye ihtiyaç duyar ve örneklerdeki kod, onay kutusunu temizlediğinizi varsayar.

::: moniker range="vs-2017"
   ![Web API projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Web API projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Web API'sini aramak için kod ekleme

1. Projede, `WebFrontEnd` *Index.cshtml.cs* dosyasını açın ve `OnGet` yöntemi aşağıdaki kodla değiştirin.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          // request.RequestUri = new Uri("http://mywebapi/WeatherForecast"); // ASP.NET 3 (VS 2019 only)
          request.RequestUri = new Uri("http://mywebapi/api/values/1"); // ASP.NET 2.x
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > Gerçek dünya kurallarına göre, her `HttpClient` istekten sonra elden çıkarmamalısınız. En iyi uygulamalar [için, esnek HTTP isteklerini uygulamak için HttpClientFactory'yi kullanın'a](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests)bakın.

   Visual Studio 2019 veya sonraki kısımlarda .NET Core 3.1 için, Web API şablonu WeatherForecast API kullanır, böylece yorum uncomment bu satırı ve ASP.NET 2.x için satır dışarı yorum.

1. *Index.cshtml* dosyasında, dosyanın aşağıdaki `ViewData["Message"]` koda benzemesi için görüntülemek için bir satır ekleyin:
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. (yalnızca ASP.NET 2.x) Şimdi Web API projesinde, *webfrontend'den*eklediğiniz arama için API tarafından döndürülen iletiyi özelleştirmek için Değerler denetleyicisine kod ekleyin.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    .NET Core 3.1 ile buna ihtiyacınız yoktur, çünkü zaten orada olan WeatherForecast API'sini kullanabilirsiniz. Ancak, bu kod Web API'yi aramak için <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> HTTPS değil HTTP kullandığından, `Configure` *Startup.cs'daki*yöntemde çağrıyı açıklamanız gerekir.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. Projede, > Konteyner `WebFrontEnd` **Orchestrator Desteği Ekle'yi**seçin. **Docker Destek Seçenekleri** iletişim kutusu görüntülenir.

1. **Docker Compose'u**seçin.

1. Örneğin, Hedef Işletim Sistemi'nizi seçin.

   ![Hedef Işletim Sistemi'ni seçme ekran görüntüsü](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio, çözümde *docker-compose.yml* dosyası ve **docker-create** düğümünde bir *.dockerignore* dosyası oluşturur ve bu proje, başlangıç projesi olduğunu gösteren boldface yazı tipinde gösterilir.

   ![Docker-compose projesi ile Solution Explorer ekran görüntüsü eklendi](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *Docker-compose.yml* aşağıdaki gibi görünür:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   *.dockerignore* dosyası, Docker'ın kapsayıcıya eklemesini istemediğiniz dosya türlerini ve uzantıları içerir. Bu dosyalar genellikle geliştirme ortamı ve kaynak denetimiyle ilişkilidir, geliştirmekte olduğunuz uygulamanın veya hizmetin bir parçası değildir.

   Çalıştırılan komutların ayrıntıları için çıktı bölmesinin **Kapsayıcı Araçları** bölümüne bakın.  Yapılandırılan ve çalışma zamanı kapsayıcıları oluşturmak için kullanılan komut satırı aracı docker-comcreate görebilirsiniz.

1. Web API projesinde, proje düğümüne tekrar sağ tıklayın ve**Kapsayıcı Orchestrator Desteği** **Ekle'yi** > seçin. **Docker Compose'u**seçin ve ardından aynı hedef işletim sistemi'ni seçin.  

    > [!NOTE]
    > Bu adımda, Visual Studio bir Dockerfile oluşturmak için sunacak. Bunu, Docker desteğine sahip bir projede yaparsanız, varolan Docker dosyasının üzerine yazmak isteyip istemediğiniz istenir. Dockerfile'nizde tutmak istediğiniz değişiklikler yaptıysanız, hayır'ı seçin.

    Visual Studio, docker'ınızda YML dosyası oluşturmak için bazı değişiklikler yapar. Şimdi her iki hizmet de dahildir.

    ```yaml
    version: '3.4'
    
    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
    
      mywebapi:
        image: ${DOCKER_REGISTRY-}mywebapi
        build:
          context: .
          dockerfile: MyWebAPI/Dockerfile
    ```

1. Beklendiği gibi çalıştığını doğrulamak için siteyi yerel olarak şimdi (F5 veya Ctrl+F5) çalıştırın. Her şey .NET Core 2.x sürümü ile doğru şekilde yapılandırılırsa, "Webfrontend ve webapi'den (değer 1 ile) merhaba" iletisini görürsünüz.  .NET Core 3 ile hava durumu verilerini görürsünüz.

   Kapsayıcı orkestrasyonu eklediğinizde kullandığınız ilk proje, çalıştırdığınızda veya hata ayıklama yaptığınızda başlatılacak şekilde ayarlanır. Docker-compose projesi için **Proje Özellikleri'ndeki** başlatma eylemini yapılandırabilirsiniz.  Docker-comproject project düğümünde, bağlam menüsünü açmak için sağ tıklatın ve ardından **Özellikler'i**seçin veya Alt+Enter'u kullanın.  Aşağıdaki ekran görüntüsü, burada kullanılan çözüm için istediğiniz özellikleri gösterir.  Örneğin, **Hizmet URL** özelliğini özelleştirerek yüklenen sayfayı değiştirebilirsiniz.

   ![Docker-beste proje özelliklerinin ekran görüntüsü](media/tutorial-multicontainer/launch-action.png)

   Başlatıldığında gördükleriniz şunlardır (.NET Core 2.x sürümü):

   ![Çalışan web uygulamasının ekran görüntüsü](media/tutorial-multicontainer/webfrontend.png)

   .NET 3.1 web uygulaması, hava durumu verilerini JSON formatında gösterir.

## <a name="next-steps"></a>Sonraki adımlar

[Kapsayıcılarınızı Azure'a](/azure/containers)dağıtma seçeneklerine bakın.

## <a name="see-also"></a>Ayrıca bkz.
  
[Docker Oluştur](https://docs.docker.com/compose/)  
[Konteyner Araçları](/visualstudio/containers/)
