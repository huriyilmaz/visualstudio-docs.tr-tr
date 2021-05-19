---
title: Docker Compose kullanarak birden çok kapsayıcıyla çalışma
author: ghogen
description: Docker Compose ile birden çok kapsayıcıyı kullanmayı öğrenin
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 03/15/2021
ms.technology: vs-azure
ms.topic: tutorial
ms.openlocfilehash: 43684288eea2e1864bf31a8bb68bbac1b217a976
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973284"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Öğretici: Docker Compose ile çok kapsayıcılı bir uygulama oluşturma

Bu öğreticide, birden fazla kapsayıcıyı yönetmeyi ve Visual Studio 'da kapsayıcı araçları kullanırken aralarında iletişim kurmayı öğreneceksiniz.  Birden çok kapsayıcıyı yönetmek için *kapsayıcı düzenlemesi* gerekir ve Docker Compose, Kubernetes veya Service Fabric gibi bir Orchestrator gerekir. Burada Docker Compose kullanacağız. Docker Compose, geliştirme döngüsünün üzerinde yerel hata ayıklama ve test için harika bir yoldur.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure Araçları** Iş yükü veya **.NET Core platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
::: moniker-end

::: moniker range=">= vs-2019"
* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure Araçları** iş yükü ve/veya **.NET Core platformlar arası geliştirme** iş yükü yüklü olan [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core 2,2 ile geliştirme için [.net core 2,2 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* .NET Core 3,1 ile geliştirme için [.NET Core 3 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/3.1) .
::: moniker-end

## <a name="create-a-web-application-project"></a>Web uygulaması projesi oluşturma

Visual Studio 'da, Razor sayfaları olan bir Web uygulaması oluşturmak için adlı bir **ASP.NET Core Web uygulaması** projesi oluşturun `WebFrontEnd` .
  
::: moniker range="vs-2017"

**Docker desteğini etkinleştir**' i seçmeyin. Docker desteğini daha sonra ekleyeceksiniz.

![Web projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![ASP.NET Core Web uygulaması projesi oluştur](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

**Docker desteğini etkinleştir**' i seçmeyin. Docker desteğini daha sonra eksersiniz.

![Web projesi oluştururken Ek bilgiler ekran görüntüsü. Docker Desteğini Etkinleştir seçeneği seçilmez.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Web API'si projesi oluşturma

Aynı çözüme bir proje ekleyin ve *myWebAPI olarak buna çağrıyın.* Proje türü olarak **API'yi** seçin ve HTTPS için yapılandır **onay kutusunu temizleyin.** Bu tasarımda, aynı web uygulamasındaki kapsayıcılar arasındaki iletişim için değil, yalnızca istemciyle iletişim için SSL kullanıyoruz. Yalnızca `WebFrontEnd` HTTPS gerekir ve örneklerde yer alan kodda bu onay kutusunun işaretinin temiz olduğu varsayıldı. Genel olarak, Visual Studio tarafından kullanılan .NET geliştirici sertifikaları kapsayıcıdan kapsayıcıya istekler için değil yalnızca dıştan kapsayıcıya istekler için desteklemektedir.

::: moniker range="vs-2017"
   ![Web API projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Web API projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Web API'sini çağıran kod ekleme

1. Projede `WebFrontEnd` *Index.cshtml.cs* dosyasını açın ve yöntemini `OnGet` aşağıdaki kodla değiştirin.

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
    > Gerçek dünya kodunda, her istekten sonra `HttpClient` atmama gerekir. En iyi yöntemler [için, bkz. Use HttpClientFactory to implementsilient HTTP requests](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

   Visual Studio 2019 veya sonraki bir sonraki bir yıl içinde .NET Core 3.1 için Web API şablonu WeatherForecast API'si kullanır, bu nedenle bu satırı açıklamadan çıkararak ASP.NET 2.x için satırı açıklama satırı oluşturun.

1. *Index.cshtml dosyasında,* dosyanın aşağıdaki koda benser gibi göründüğünü `ViewData["Message"]` göstermek için bir satır ekleyin:
    
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

1. (ASP.NET 2.x) Şimdi Web API projesinde, *webfrontend'den* eklenen çağrı için API tarafından döndürülen iletiyi özelleştirmek için Değerler denetleyicisine kod ekleyin.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    .NET Core 3.1 ile buna ihtiyacınız yok çünkü zaten orada olan WeatherForecast API'sini kullanabilirsiniz. Ancak, <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> `Configure` *çağrısının Startup.cs'de* yönteminde açıklamalarını açıklama olarak almanız gerekir çünkü bu kod Web API'sini aramak için HTTPS değil HTTP kullanır.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. `WebFrontEnd`Projede **> kapsayıcı Orchestrator desteği ekle**' yi seçin. **Docker destek seçenekleri** iletişim kutusu görüntülenir.

1. **Docker Compose** seçin.

1. Hedef işletim sistemini (örneğin, Linux) seçin.

   ![Hedef işletim sistemini seçme ekran görüntüsü](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio, çözümdeki **Docker-Compose** düğümünde bir *Docker-Compose. yıml* dosyası ve *. dockerıgnore* dosyası oluşturur ve bu proje, başlangıç projesi olduğunu gösteren kalýn yazı tipinde görüntülenir.

   ![Docker-Compose projesi eklenen Çözüm Gezgini ekran görüntüsü](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *Docker-Compose. yml* şu şekilde görünür:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   *. Dockerıgnore* dosyası, Docker 'ın kapsayıcıya dahil etmesini istemediğiniz dosya türlerini ve uzantılarını içerir. Bu dosyalar genellikle geliştirme ortamı ve kaynak denetimiyle ilişkilendirilir, geliştirmekte olduğunuz uygulamanın veya hizmetin bir parçası değildir.

   Çalıştırılmakta olan komutların ayrıntıları için çıkış bölmesinin **kapsayıcı araçları** bölümüne bakın.  Docker-Compose, çalışma zamanı kapsayıcılarını yapılandırmak ve oluşturmak için kullanılan komut satırı aracını görebilirsiniz.

1. Web API projesinde, proje düğümüne sağ tıklayın ve   >  **kapsayıcı Orchestrator desteği** Ekle ' yi seçin. **Docker Compose** öğesini seçin ve ardından aynı hedef işletim sistemini seçin.  

    > [!NOTE]
    > Bu adımda, Visual Studio bir Dockerfile oluşturmaya yönelik olarak sunulur. Bunu zaten Docker desteği olan bir projede yaparsanız, var olan Dockerfile dosyasının üzerine yazmak isteyip istemediğiniz sorulur. Sürdürmek istediğiniz Dockerfile dosyanızda değişiklik yaptıysanız Hayır ' ı seçin.

    Visual Studio, Docker Compose YıLML dosyanızda bazı değişiklikler yapar. Artık her iki hizmet de dahildir.

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

1. Siteyi, beklendiği gibi çalıştığını doğrulamak için şimdi yerel olarak çalıştırın (F5 veya CTRL + F5). Her şey .NET Core 2.x sürümüyle doğru şekilde yapılandırıldıysa "Hello from webfrontend and webapi (1 değeriyle)" (Hello from webfrontend and webapi)" (Hello from webfrontend and webapi (1 değeriyle) iletisiyle birlikte gelirsiniz.  .NET Core 3 ile hava durumu tahmin verilerini görüyorsunuz.

   Kapsayıcı düzenlemesi eklerken ilk proje, çalıştırarak veya hata ayıklarken başlatacak şekilde ayarlanır. Başlatma eylemlerini docker-compose **projesinin** Proje Özellikleri'ne göre yapılandırabilirsiniz.  docker-compose proje düğümünde bağlam menüsünü açmak için sağ tıklayın ve özellikler'i **seçin** veya Alt+Enter tuşlarına basın.  Aşağıdaki ekran görüntüsü, burada kullanılan çözüm için istediğiniz özellikleri gösterir.  Örneğin, Hizmet URL'si özelliğini özelleştirerek yüklenen **sayfayı değiştirebilirsiniz.**

   ![docker-compose proje özelliklerinin ekran görüntüsü](media/tutorial-multicontainer/launch-action.png)

   İlk kez (.NET Core 2.x sürümü) şu şekilde görüyorsunuz:

   ![Web uygulamasını çalıştırma ekran görüntüsü](media/tutorial-multicontainer/webfrontend.png)

   .NET 3.1 için web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

## <a name="next-steps"></a>Sonraki adımlar

Kapsayıcılarınızı Azure'a dağıtma [seçeneklerine bakın.](/azure/containers)

Bir hata ayıklama oturumu sırasında hangi hizmetlerin başlatıldığında daha fazla denetim için, hata ayıklama sırasında Docker Compose hangi hizmetlerin çalıştırıldığında yapılandıracak şekilde başlatma profillerini nasıl kullanabileceğinizi öğrenin. Bkz. [Docker Compose için başlatma profillerini yönetme](launch-profiles.md)

## <a name="see-also"></a>Ayrıca bkz.
  
[Docker Compose](https://docs.docker.com/compose/)  
[Kapsayıcı Araçları](./index.yml)