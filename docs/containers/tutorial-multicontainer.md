---
title: Docker Compose kullanarak birden çok kapsayıcıyla çalışma
author: ghogen
description: Docker Compose ile birden çok kapsayıcı kullanmayı Docker Compose
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 03/15/2021
ms.technology: vs-container-tools
ms.topic: tutorial
ms.openlocfilehash: 49a207b1a2234b12cebb95e9019fe15da28846ca6e4e7666fb5bf57c86ff1aff
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121363424"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Öğretici: Docker Compose ile çok kapsayıcılı uygulama oluşturma

Bu öğreticide, birden fazla kapsayıcıyı yönetmeyi ve kapsayıcılar arasında iletişim kurarken kapsayıcılar arasında iletişim Visual Studio.  Birden çok kapsayıcının *yönetilmesi için kapsayıcı düzenlemesi* gerekir ve Docker Compose, Kubernetes veya Service Fabric. Burada bu bilgileri Docker Compose. Docker Compose, geliştirme döngüsü sırasında yerel hata ayıklama ve test etme için harikadır.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü veya **.NET Core platformlar** arası geliştirme iş yükü yüklü olarak [2017'ye](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) geçiş
::: moniker-end

::: moniker range="vs-2019"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET Core platformlar** arası geliştirme iş yükünün yüklü olduğu [2019](https://visualstudio.microsoft.com/downloads) sürümü
* [.NET Core 2.2 ile geliştirme](https://dotnet.microsoft.com/download/dotnet-core/2.2) için .NET Core 2.2 Geliştirme Araçları
* [.NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) ile geliştirme için .NET Core 3 Geliştirme Araçları.
::: moniker-end

::: moniker range=">=vs-2022"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio **Geliştirme,** **Azure** Araçları iş yükü ve/veya **.NET Core platformlar** arası geliştirme iş yükü yüklü [2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) sürümü
* [.NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) ile geliştirme için .NET Core 3 Geliştirme Araçları.
* [.NET 5 Geliştirme .NET](https://dotnet.microsoft.com/download/dotnet-core/5.0) 5 ile geliştirme için çok fazla.
::: moniker-end

## <a name="create-a-web-application-project"></a>Web Uygulaması projesi oluşturma

Bu Visual Studio, Razor **ASP.NET Core bir web** uygulaması oluşturmak için adlı bir web uygulaması projesi `WebFrontEnd` oluşturun.
  
::: moniker range="vs-2017"

Docker Desteğini **Etkinleştir'i seçme.** Docker desteğini daha sonra eksersiniz.

![Web projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Web ASP.NET Core projesi oluşturma](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

Docker Desteğini **Etkinleştir'i seçme.** Docker desteğini daha sonra eksersiniz.

![Web projesi oluştururken Ek bilgiler ekran görüntüsü. Docker Desteğini Etkinleştir seçeneği seçilmez.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Web API'si projesi oluşturma

Aynı çözüme bir proje ekleyin ve *myWebAPI olarak buna çağrıyın.* Proje türü olarak **API'yi** seçin ve HTTPS için yapılandır **onay kutusunu temizleyin.** Bu tasarımda, aynı web uygulamasındaki kapsayıcılar arasındaki iletişim için değil, yalnızca istemciyle iletişim için SSL kullanıyoruz. Yalnızca `WebFrontEnd` HTTPS gerekir ve örneklerde yer alan kodda bu onay kutusunun işaretinin temiz olduğu varsayıldı. Genel olarak, Visual Studio tarafından kullanılan .NET geliştirici sertifikaları kapsayıcıdan kapsayıcıya istekler için değil yalnızca dıştan kapsayıcıya istekler için desteklemektedir.

::: moniker range="vs-2017"
   ![Web API'si projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range=">=vs-2019"
   ![Web API'si projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
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

   Visual Studio 2019 veya sonraki bir sonraki bir yıl içinde .NET Core 3.1 için Web API şablonu weatherForecast API'si kullanır, bu nedenle bu satırı açıklamadan çıkararak ASP.NET 2.x için satırı açıklama satırına yazın.

1. *Index.cshtml dosyasında,* dosyanın aşağıdaki koda benser şekilde benzlemesi `ViewData["Message"]` için görüntülemek için bir satır ekleyin:
    
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

1. Proje içinde `WebFrontEnd` Kapsayıcı **Orchestrator Desteğine >'yi seçin.** **Docker Destek Seçenekleri iletişim** kutusu görüntülenir.

1. 'yi **Docker Compose.**

1. Hedef işletim sisteminizi (örneğin, Linux) seçin.

   ![Hedef işletim sistemi seçme ekran görüntüsü](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio *çözümün docker-compose düğümünde bir docker-compose.yml* dosyası ve *bir .dockerignore* dosyası oluşturur ve bu proje başlangıç projesi olduğunu gösteren kalın yazı tipiyle gösterilir. 

   ![docker-compose Çözüm Gezgini eklenmiş bir dosyanın ekran görüntüsü](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

   *docker-compose.yml aşağıdaki* gibi görünür:

   ```yaml
   version: '3.4'

    services:
      webfrontend:
        image: ${DOCKER_REGISTRY-}webfrontend
        build:
          context: .
          dockerfile: WebFrontEnd/Dockerfile
   ```

   *.dockerignore* dosyası, Docker'ın kapsayıcıya dahil etmelerini istemeyebilirsiniz dosya türlerini ve uzantılarını içerir. Bu dosyalar genellikle geliştirme ortamı ve kaynak denetimiyle ilişkilendirilmektedir, geliştirmekte olan uygulamanın veya hizmetin bir parçası değildir.

   Çalıştırı **olan komutların** ayrıntıları için çıkış bölmesinin Kapsayıcı Araçları bölümüne bakın.  Çalışma zamanı kapsayıcılarını yapılandırmak ve oluşturmak için docker-compose komut satırı aracının kullan olduğunu görüyorsunuz.

1. Web API'si projesinde proje düğümüne tekrar sağ tıklayın ve Kapsayıcı Orchestrator **Desteği**  >  **Ekle'yi seçin.** Bir **Docker Compose** ve ardından aynı hedef işletim sistemi seçin.  

    > [!NOTE]
    > Bu adımda, Visual Studio dockerfile oluşturma teklifi sunmayacak. Docker desteği olan bir projede bunu yaparsanız, mevcut Dockerfile dosyasının üzerine yazmak isteyip istemediğiniz sorabilirsiniz. Dockerfile dosyanız üzerinde tutmak istediğiniz değişiklikler yaptısanız hayır'ı seçin.

    Visual Studio docker compose YML dosyanız üzerinde bazı değişiklikler yapar. Artık her iki hizmet de dahil edildi.

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

1. Siteyi şimdi yerel olarak (F5 veya Ctrl+F5) çalıştırarak beklendiği gibi çalıştığını doğrulayın. Her şey .NET Core 2.x sürümüyle doğru şekilde yapılandırıldıysa "Hello from webfrontend and webapi (1 değeriyle)" (Hello from webfrontend and webapi)" (Hello from webfrontend and webapi (1 değeriyle) iletisiyle birlikte gelirsiniz.  .NET Core 3 ile hava durumu tahmin verilerini görüyorsunuz.

   Kapsayıcı düzenlemesi eklerken kullanmakta olduğu ilk proje, çalıştırma veya hata ayıklama adımlarını başlatacak şekilde ayarlanır. Başlatma eylemlerini docker-compose **Project** Özellikler'de yapılandırabilirsiniz.  docker-compose proje düğümünde bağlam menüsünü açmak için sağ tıklayın ve özellikler'i **seçin** veya Alt+Enter tuşlarına basın.  Aşağıdaki ekran görüntüsü, burada kullanılan çözüm için istediğiniz özellikleri gösterir.  Örneğin, Hizmet URL'si özelliğini özelleştirerek yüklenen **sayfayı değiştirebilirsiniz.**

   ![docker-compose proje özelliklerinin ekran görüntüsü](media/tutorial-multicontainer/launch-action.png)

   İlk kez (.NET Core 2.x sürümü) şu şekildedir:

   ![Web uygulamasını çalıştırma ekran görüntüsü](media/tutorial-multicontainer/webfrontend.png)

   .NET 3.1 için web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

## <a name="next-steps"></a>Sonraki adımlar

Kapsayıcılarınızı Azure'a dağıtma [seçeneklerine bakın.](/azure/containers)

Hata ayıklama oturumu sırasında hangi hizmetlerin başlatıldığında daha fazla denetim için, hata ayıklama sırasında Docker Compose başlatma profillerini kullanmayı öğrenin. Bkz. [Docker Compose için başlatma profillerini yönetme](launch-profiles.md)

## <a name="see-also"></a>Ayrıca bkz.
  
[Docker Compose](https://docs.docker.com/compose/)  
[Kapsayıcı Araçları](./index.yml)