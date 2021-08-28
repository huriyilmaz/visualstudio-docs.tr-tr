---
title: Docker Compose kullanarak birden çok kapsayıcıyla çalışma
author: ghogen
description: Docker Compose ile birden çok kapsayıcıyı kullanmayı öğrenin
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 03/15/2021
ms.technology: vs-container-tools
ms.topic: tutorial
ms.openlocfilehash: 437663a4c3f1af07d5137aacb32e26e6021597ed
ms.sourcegitcommit: 8f8804b885c3a68f20bf0e9fe3729f2764145815
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2021
ms.locfileid: "123096997"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Öğretici: Docker Compose ile çok kapsayıcılı bir uygulama oluşturma

Bu öğreticide, birden fazla kapsayıcıyı yönetmeyi ve Visual Studio kapsayıcı araçlarını kullanırken aralarında iletişim kurmayı öğreneceksiniz.  Birden çok kapsayıcıyı yönetmek için *kapsayıcı düzenlemesi* gerekir ve Docker Compose, Kubernetes veya Service Fabric gibi bir Orchestrator gerekir. Burada Docker Compose kullanacağız. Docker Compose, geliştirme döngüsünün üzerinde yerel hata ayıklama ve test için harika bir yoldur.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure araçları** iş yükü veya **.net Core platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)
::: moniker-end

::: moniker range="vs-2019"

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure araçları** iş yükü ve/veya **.net Core platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core 2,2 ile geliştirme için [.net core 2,2 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/2.2)
* .NET Core 3,1 ile geliştirme için [.NET Core 3 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/3.1) .
::: moniker-end

::: moniker range=">=vs-2022"

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure araçları** iş yükü ve/veya **.net Core platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022)
* .NET Core 3,1 ile geliştirme için [.NET Core 3 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/3.1) .
* .NET 5 ile geliştirme için [.NET 5 geliştirme Toos](https://dotnet.microsoft.com/download/dotnet-core/5.0) .
::: moniker-end

## <a name="create-a-web-application-project"></a>Web uygulaması projesi oluşturma

Visual Studio ' de, Razor sayfaları olan bir web uygulaması oluşturmak için adlı bir **ASP.NET Core web uygulaması** projesi oluşturun `WebFrontEnd` .
  
::: moniker range="vs-2017"

**Docker desteğini etkinleştir**' i seçmeyin. Docker desteğini daha sonra ekleyeceksiniz.

![Web projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range=">=vs-2019"

![ASP.NET Core Web uygulaması projesi oluştur](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

**Docker desteğini etkinleştir**' i seçmeyin. Docker desteğini daha sonra ekleyeceksiniz.

![Web projesi oluştururken ek bilgi ekranının ekran görüntüsü. Docker desteğini etkinleştirme seçeneği seçili değil.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Web API projesi oluşturma

Aynı çözüme bir proje ekleyin ve *Mywebapi* olarak çağırın. Proje türü olarak **API** ' yi SEÇIN ve **https için yapılandırma** onay kutusunu temizleyin. Bu tasarımda, aynı Web uygulamasındaki kapsayıcılar arasında iletişim için değil, yalnızca istemciyle iletişim için SSL kullandık. Yalnızca `WebFrontEnd` https gerektirir ve örneklerdeki kod bu onay kutusunu temizlemiş olduğunu varsayar. genel olarak, Visual Studio tarafından kullanılan .net geliştirici sertifikaları, kapsayıcı istekleri için değil, yalnızca dış kapsayıcı istekleri için desteklenir.

::: moniker range="vs-2017"
   ![Web API projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Web API projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Web API 'sini çağırmak için kod ekleme

1. `WebFrontEnd`Projede *Index. cshtml. cs* dosyasını açın ve `OnGet` yöntemi aşağıdaki kodla değiştirin.

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
    > Gerçek dünyada kodda, `HttpClient` her istekten sonra atılamaz. En iyi uygulamalar için bkz. [Esnek http isteklerini uygulamak Için HttpClientFactory kullanma](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

   Visual Studio 2019 veya üzeri sürümlerde .net Core 3,1 için Web apı şablonu bir azthertahmini apı kullanır. bu nedenle, bu satırın açıklamasını kaldırın ve ASP.NET 2. x için satırı açıklama olarak yapın.

1. *Index. cshtml* dosyasında, `ViewData["Message"]` dosyanın aşağıdaki koda benzeymek üzere görüntülenecek bir satır ekleyin:
    
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

1. (yalnızca ASP.NET 2. x) Şimdi Web API projesinde, *webön* ucunda eklediğiniz çağrı için API tarafından döndürülen iletiyi özelleştirmek üzere değerler denetleyicisine kod ekleyin.
    
      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

    .NET Core 3,1 ile, zaten orada olan dalgalı tahmin API 'sini kullanabilmeniz için buna ihtiyacınız yoktur. Ancak, <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> `Configure` Bu kod Web API 'sini ÇAĞıRMAK için https değil http 'yi kullandığından, *Başlangıç. cs* içindeki yönteminde öğesine yapılan çağrıyı açıklamanız gerekir.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. `WebFrontEnd`Projede **> kapsayıcı Orchestrator desteği ekle**' yi seçin. **Docker destek seçenekleri** iletişim kutusu görüntülenir.

1. **Docker Compose** seçin.

1. Hedef işletim sistemini (örneğin, Linux) seçin.

   ![Hedef işletim sistemini seçme ekran görüntüsü](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio çözümdeki **docker-compose** düğümünde bir *docker-compose. yıml* dosyası ve *. dockerıgnore* dosyası oluşturur ve bu proje, başlangıç projesi olduğunu gösteren kalýn yazı tipinde görünür.

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
    > bu adımda Visual Studio bir dockerfile oluşturmak için teklif edilecek. Bunu zaten Docker desteği olan bir projede yaparsanız, var olan Dockerfile dosyasının üzerine yazmak isteyip istemediğiniz sorulur. Sürdürmek istediğiniz Dockerfile dosyanızda değişiklik yaptıysanız Hayır ' ı seçin.

    Visual Studio docker compose yılml dosyanızda bazı değişiklikler yapar. Artık her iki hizmet de dahildir.

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

   Kapsayıcı düzenlemesi eklediğinizde kullandığınız ilk proje, çalıştırdığınızda veya hata ayıkladığınızda başlatılacak şekilde ayarlanır. başlatma eylemini docker-compose projesi için **Project özelliklerinde** yapılandırabilirsiniz.  Docker-Compose projesi düğümünde bağlam menüsünü açmak için sağ tıklayın, ardından **Özellikler**' i seçin veya alt + ENTER ' u kullanın.  Aşağıdaki ekran görüntüsünde, burada kullanılan çözüm için istediğiniz özellikler gösterilmektedir.  Örneğin, **hizmet URL 'si** özelliğini özelleştirerek yüklenen sayfayı değiştirebilirsiniz.

   ![Docker-Compose proje özelliklerinin ekran görüntüsü](media/tutorial-multicontainer/launch-action.png)

   Başlatıldığında gördüğünüz Özellikler (.NET Core 2. x sürümü):

   ![Çalışan Web uygulamasının ekran görüntüsü](media/tutorial-multicontainer/webfrontend.png)

   .NET 3,1 için Web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

## <a name="next-steps"></a>Sonraki adımlar

[Kapsayıcılarınızı Azure 'a](/azure/containers)dağıtmaya yönelik seçeneklere bakın.

Her bir hata ayıklama görevi için gerekli olmayan çok sayıda mikro hizmetlerle çalışıyorsanız, hata ayıklama oturumu sırasında hangi hizmetlerin başlatıldığı üzerinde daha fazla denetim için Docker Compose başlatma profillerini kullanabilirsiniz. Bkz. [Docker Compose için başlatma profillerini yönetme](launch-profiles.md).

## <a name="see-also"></a>Ayrıca bkz.
  
[Docker Compose](https://docs.docker.com/compose/)  
[Kapsayıcı araçları](./index.yml)