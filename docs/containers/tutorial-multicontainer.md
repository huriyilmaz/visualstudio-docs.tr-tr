---
title: Docker Compose & kullanarak çok Kapsayıcılı öğretici ASP.NET Core
author: ghogen
description: Docker Compose ile birden çok kapsayıcıyı kullanmayı öğrenin
ms.author: ghogen
ms.date: 01/10/2020
ms.technology: vs-azure
ms.topic: include
ms.openlocfilehash: ebc0d8efb0d78dda45bba06dba8a497287b3597d
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75886469"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Öğretici: Docker Compose ile çok kapsayıcılı bir uygulama oluşturma

Bu öğreticide, birden fazla kapsayıcıyı yönetmeyi ve Visual Studio 'da kapsayıcı araçları kullanırken aralarında iletişim kurmayı öğreneceksiniz.  Birden çok kapsayıcıyı yönetmek için *kapsayıcı düzenlemesi* gerekir ve Docker Compose, Kubernetes veya Service Fabric gibi bir Orchestrator gerekir. Burada Docker Compose kullanacağız. Docker Compose, geliştirme döngüsünün üzerinde yerel hata ayıklama ve test için harika bir yoldur.

## <a name="prerequisites"></a>Prerequisites

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

Visual Studio 'da, `WebFrontEnd`adlı bir **ASP.NET Core Web uygulaması** projesi oluşturun. Razor sayfaları olan bir Web uygulaması oluşturmak için **Web uygulaması** ' nı seçin. 
  
::: moniker range="vs-2017"

**Docker desteğini etkinleştir**' i seçmeyin. Docker desteğini daha sonra ekleyeceksiniz.

![Web projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Web projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project1.png)

**Docker desteğini etkinleştir**' i seçmeyin. Docker desteğini daha sonra ekleyeceksiniz.

![Web projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/vs-2019/new-aspnet-core-project.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Web API projesi oluşturma

Aynı çözüme bir proje ekleyin ve *Mywebapi*olarak çağırın. Proje türü olarak **API** ' yi SEÇIN ve **https için yapılandırma**onay kutusunu temizleyin. Bu tasarımda, aynı Web uygulamasındaki kapsayıcılar arasında iletişim için değil, yalnızca istemciyle iletişim için SSL kullandık. Yalnızca `WebFrontEnd` HTTPS gerektirir ve örneklerdeki kod bu onay kutusunu temizlemiş olduğunu varsayar.

::: moniker range="vs-2017"
   ![Web API projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Web API projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/vs-2019/web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Web API 'sini çağırmak için kod ekleme

1. `WebFrontEnd` projesinde, *Index.cshtml.cs* dosyasını açın ve `OnGet` yöntemini aşağıdaki kodla değiştirin.

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

   Visual Studio 2019 veya sonraki sürümlerde .NET Core 3,1 için Web API şablonu bir dalgalı tahmin API 'SI kullanır, bu nedenle bu satırın açıklamasını kaldırın ve ASP.NET 2. x için satırı açıklama olarak yapın.

1. *Index. cshtml* dosyasında, dosyanın aşağıdaki kod gibi görünmesi için `ViewData["Message"]` görüntülenecek bir satır ekleyin:
    
      ```cshtml
      @page
      @model IndexModel
      @{
          ViewData["Title"] = "Home page";
      }
    
      <div class="text-center">
          <h1 class="display-4">Welcome</h1>
          <p>Learn about <a href="https://docs.microsoft.com/aspnet/core">building Web apps with ASP.NET Core</a>.</p>
          <p>@ViewData["Message"]</p>
      </div>
      ```

1. (Yalnızca ASP.NET 2. x) Şimdi Web API projesinde, *webön*ucunda eklediğiniz çağrı için API tarafından döndürülen iletiyi özelleştirmek üzere değerler denetleyicisine kod ekleyin.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    .NET Core 3,1 ile, zaten orada olan dalgalı tahmin API 'sini kullanabilmeniz için buna ihtiyacınız yoktur. Ancak, bu kod Web API 'sini çağırmak için HTTPS değil HTTP 'yi kullandığından, *Startup.cs*içindeki `Configure` yönteminde <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> çağrısını açıklamanız gerekir.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. `WebFrontEnd` projesinde, **ekle > kapsayıcı Orchestrator desteği**' ni seçin. **Docker destek seçenekleri** iletişim kutusu görüntülenir.

1. **Docker Compose**seçin.

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

1. Web API projesinde, proje düğümüne sağ tıklayın ve > **kapsayıcı Orchestrator desteği** **Ekle** ' yi seçin. **Docker Compose**öğesini seçin ve ardından aynı hedef işletim sistemini seçin.  

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

1. Siteyi, beklendiği gibi çalıştığını doğrulamak için şimdi yerel olarak çalıştırın (F5 veya CTRL + F5). Her şey .NET Core 2. x sürümü ile doğru şekilde yapılandırıldıysa, "Web ön ucu ve WebApi 'den (değer 1 ile) Merhaba" iletisini görürsünüz.  .NET Core 3 ile hava durumu tahmin verilerini görürsünüz.

   Kapsayıcı düzenlemesi eklediğinizde kullandığınız ilk proje, çalıştırdığınızda veya hata ayıkladığınızda başlatılacak şekilde ayarlanır. Başlatma eylemini Docker-Compose projesi için **proje özelliklerinde** yapılandırabilirsiniz.  Docker-Compose projesi düğümünde bağlam menüsünü açmak için sağ tıklayın, ardından **Özellikler**' i seçin veya alt + ENTER ' u kullanın.  Aşağıdaki ekran görüntüsünde, burada kullanılan çözüm için istediğiniz özellikler gösterilmektedir.  Örneğin, **hizmet URL 'si** özelliğini özelleştirerek yüklenen sayfayı değiştirebilirsiniz.

   ![Docker-Compose proje özelliklerinin ekran görüntüsü](media/tutorial-multicontainer/launch-action.png)

   Başlatıldığında gördüğünüz Özellikler (.NET Core 2. x sürümü):

   ![Çalışan Web uygulamasının ekran görüntüsü](media/tutorial-multicontainer/webfrontend.png)

   .NET 3,1 için Web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

## <a name="next-steps"></a>Sonraki adımlar

[Kapsayıcılarınızı Azure 'a](/azure/containers)dağıtmaya yönelik seçeneklere bakın.

## <a name="see-also"></a>Ayrıca bkz.
  
[Docker Compose](https://docs.docker.com/compose/)  
[Kapsayıcı araçları](/visualstudio/containers/)
