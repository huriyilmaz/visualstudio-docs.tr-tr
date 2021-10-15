---
title: Docker Compose kullanarak birden çok kapsayıcıyla çalışma
author: ghogen
description: Docker Compose ile birden çok kapsayıcı kullanmayı Docker Compose
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 09/17/2021
ms.technology: vs-container-tools
ms.topic: tutorial
ms.openlocfilehash: c6ec7410c01dfb6a3d020ceaa7973c55dd087fa5
ms.sourcegitcommit: 72f8ce4992cc62c4833e6dcb0f79febb328c44be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130011139"
---
# <a name="tutorial-create-a-multi-container-app-with-docker-compose"></a>Öğretici: Docker Compose ile çok kapsayıcılı uygulama oluşturma

Bu öğreticide, birden fazla kapsayıcıyı yönetmeyi ve kapsayıcılar arasında iletişim kurarken kapsayıcılar arasında iletişim Visual Studio.  Birden çok kapsayıcının *yönetilmesi için kapsayıcı düzenlemesi* gerekir ve Docker Compose, Kubernetes veya Service Fabric. Burada bu bilgileri Docker Compose. Docker Compose, geliştirme döngüsü sırasında yerel hata ayıklama ve test etme için harikadır.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü veya **.NET Core platformlar** arası geliştirme iş yükünün yüklü olduğu [2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sürümü
::: moniker-end

::: moniker range="vs-2019"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET platformlar** arası geliştirme iş yükü yüklü olarak [2019'a](https://visualstudio.microsoft.com/downloads) geçiş
* [.NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) ile geliştirme için .NET Core 3 Geliştirme Araçları.
::: moniker-end

::: moniker range=">=vs-2022"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio **Geliştirme,** **Azure** Araçları iş yükü ve/veya **.NET platformlar** arası geliştirme iş yükü yüklü [2022 RC'ye](https://visualstudio.microsoft.com/vs/preview/) sahip. Buna .NET Core 3.1 ve .NET 6 geliştirme araçları dahildir.
* [.NET 5 Geliştirme .NET](https://dotnet.microsoft.com/download/dotnet-core/5.0) 5 ile geliştirme için çok fazla.
::: moniker-end

## <a name="create-a-web-application-project"></a>Web Uygulaması projesi oluşturma

Bu Visual Studio, Razor **ASP.NET Core bir web** uygulaması oluşturmak `WebFrontEnd` için adlı bir Web Uygulaması projesi oluşturun.
  
::: moniker range="vs-2017"

Docker Desteğini **Etkinleştir'i seçme.** Docker desteğini daha sonra eksersiniz.

![Web projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Web ASP.NET Core projesi oluşturma](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

Docker Desteğini **Etkinleştir'i seçme.** Docker desteğini daha sonra eksersiniz.

![Web projesi oluştururken Ek bilgiler ekran görüntüsü. Docker Desteğini Etkinleştir seçeneği seçilmez.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end
::: moniker range=">=vs-2022"

![Web ASP.NET Core projesi oluşturma](./media/tutorial-multicontainer/vs-2022/create-web-project.png)

Docker Desteğini **Etkinleştir'i seçme.** Docker desteğini daha sonra eksersiniz.

![Web projesi oluştururken Ek bilgiler ekran görüntüsü. Docker Desteğini Etkinleştir seçeneği seçilmez.](./media/tutorial-multicontainer/vs-2022/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Web API'si projesi oluşturma

Aynı çözüme bir proje ekleyin ve *myWebAPI olarak buna çağrıyın.* Proje türü olarak **API'yi** seçin ve HTTPS için yapılandır onay **kutusunu temizleyin.** Bu tasarımda, aynı web uygulamasındaki kapsayıcılar arasındaki iletişim için değil, yalnızca istemciyle iletişim için SSL kullanıyoruz. Yalnızca `WebFrontEnd` HTTPS gerekir ve örneklerde yer alan kodda bu onay kutusunun işaretinin temiz olduğu varsayıldı. Genel olarak, Visual Studio tarafından kullanılan .NET geliştirici sertifikaları kapsayıcıdan kapsayıcıya istekler için değil yalnızca dıştan kapsayıcıya istekler için desteklemektedir.

::: moniker range="vs-2017"
   ![Web API'si projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Web API'si projesi oluşturma ekran görüntüsü](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
::: moniker-end
::: moniker range=">=vs-2022"
   ![Web API'si projesi oluşturma ekran görüntüsü](media/tutorial-multicontainer/vs-2022/create-web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Web API'sini çağıran kod ekleme

::: moniker range="<=vs-2019"

1. Projede `WebFrontEnd` *Index.cshtml.cs* dosyasını açın ve yöntemini `OnGet` aşağıdaki kodla değiştirin.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/WeatherForecast");
          // request.RequestUri = new Uri("http://mywebapi/api/values/1"); // For ASP.NET 2.x, comment out previous line and uncomment this line.
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > Gerçek dünya kodunda, her istekten sonra `HttpClient` atmama gerekir. En iyi yöntemler [için, bkz. Use HttpClientFactory to implementsilient HTTP requests](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

1. *Index.cshtml dosyasında,* dosyanın aşağıdaki koda benser şekilde benzin `ViewData["Message"]` görüntüleniyor olacak şekilde bir satır ekleyin:
    
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

    .NET Core 3.1 ve sonraki bir ile, zaten orada olan WeatherForecast API'sini kullanabileceğiniz için buna ihtiyacınız yok. Ancak bu kod Web API'sini aramak için HTTPS değil HTTP kullandığından, Web API projesinde çağrısına <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*>  açıklama açıklamalarını açıklama olarak açıklama olarak bakabilirsiniz.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. Proje içinde `WebFrontEnd` Kapsayıcı **Orchestrator Desteğine >'yi seçin.** **Docker Destek Seçenekleri iletişim** kutusu görüntülenir.

1. **Docker Compose.**

1. Hedef işletim sisteminizi (örneğin, Linux) seçin.

   ![Hedef işletim sistemi seçme ekran görüntüsü](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio *çözümdeki docker-compose düğümünde bir docker-compose.yml* dosyası ve *bir .dockerignore* dosyası oluşturur ve bu proje başlangıç projesi olduğunu gösteren kalın yazı tipiyle gösterilir. 

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

   *.dockerignore* dosyası, Docker'ın kapsayıcıya dahil etmelerini istemeyebilirsiniz dosya türlerini ve uzantılarını içerir. Bu dosyalar genellikle geliştirmekte olan uygulamanın veya hizmetin parçası değil geliştirme ortamı ve kaynak denetimiyle ilişkilendirilmektedir.

   Çalıştırı **olan komutların** ayrıntıları için çıkış bölmesinin Kapsayıcı Araçları bölümüne bakın.  Çalışma zamanı kapsayıcılarını yapılandırmak ve oluşturmak için docker-compose komut satırı aracının kullan olduğunu görüyorsunuz.

1. Web API projesinde proje düğümüne tekrar sağ tıklayın ve Kapsayıcı Orchestrator **Desteği**  >  **Ekle'yi seçin.** İlk **Docker Compose** ve ardından aynı hedef işletim sistemi seçin.  

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

   Kapsayıcı düzenlemesi eklerken ilk proje, çalıştıracak veya hata ayıklayacak şekilde ayarlanır. Başlatma eylemlerini docker-compose **Project** Özellikler'de yapılandırabilirsiniz.  docker-compose proje düğümünde bağlam menüsünü açmak için sağ tıklayın ve özellikler'i **seçin** veya Alt+Enter tuşlarına basın.  Aşağıdaki ekran görüntüsü, burada kullanılan çözüm için istediğiniz özellikleri gösterir.  Örneğin, Hizmet URL'si özelliğini özelleştirerek yüklenen **sayfayı değiştirebilirsiniz.**

   ![docker-compose proje özelliklerinin ekran görüntüsü](media/tutorial-multicontainer/launch-action.png)

   İlk kez (.NET Core 2.x sürümü) şu şekildedir:

   ![Web uygulamasını çalıştırma ekran görüntüsü](media/tutorial-multicontainer/webfrontend.png)

   .NET 3.1 için web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

::: moniker-end
::: moniker range=">=vs-2022"

1. Projede `WebFrontEnd` *Index.cshtml.cs* dosyasını açın ve yöntemini `OnGet` aşağıdaki kodla değiştirin.

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/WeatherForecast");
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

    > [!NOTE]
    > Gerçek dünya kodunda, her istekten sonra `HttpClient` atmama gerekir. En iyi yöntemler [için, bkz. Use HttpClientFactory to implementsilient HTTP requests](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

1. *Index.cshtml dosyasında,* dosyanın aşağıdaki koda benser şekilde benzin `ViewData["Message"]` görüntüleniyor olacak şekilde bir satır ekleyin:

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

1. Web API projesinde çağrısına açıklama açıklaması girin çünkü bu kod Web API'sini aramak için HTTPS değil <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> HTTP kullanır.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. Proje içinde `WebFrontEnd` Kapsayıcı **Orchestrator Desteğine >'yi seçin.** **Docker Destek Seçenekleri iletişim** kutusu görüntülenir.

1. **Docker Compose.**

1. Hedef işletim sisteminizi (örneğin, Linux) seçin.

   ![Hedef işletim sistemi seçme ekran görüntüsü](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio *çözümdeki docker-compose düğümünde bir docker-compose.yml* dosyası ve *bir .dockerignore* dosyası oluşturur ve bu proje başlangıç projesi olduğunu gösteren kalın yazı tipiyle gösterilir. 

   ![docker-compose Çözüm Gezgini eklenmiş bir dosyanın ekran görüntüsü](media/tutorial-multicontainer/vs-2022/multicontainer-solution-explorer.png)

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

   *.dockerignore* dosyası, Docker'ın kapsayıcıya dahil etmelerini istemeyebilirsiniz dosya türlerini ve uzantılarını içerir. Bu dosyalar genellikle geliştirmekte olan uygulamanın veya hizmetin parçası değil geliştirme ortamı ve kaynak denetimiyle ilişkilendirilmektedir.

   Çalıştırı **olan komutların** ayrıntıları için çıkış bölmesinin Kapsayıcı Araçları bölümüne bakın.  Çalışma zamanı kapsayıcılarını yapılandırmak ve oluşturmak için docker-compose komut satırı aracının kullan olduğunu görüyorsunuz.

1. Web API projesinde proje düğümüne tekrar sağ tıklayın ve Kapsayıcı Orchestrator **Desteği**  >  **Ekle'yi seçin.** İlk **Docker Compose** ve ardından aynı hedef işletim sistemi seçin.  

    > [!NOTE]
    > Bu adımda, Visual Studio dockerfile oluşturma teklifi sunmayacak. Bunu zaten Docker desteği olan bir projede yaparsanız, var olan Dockerfile dosyasının üzerine yazmak isteyip istemediğiniz sorulur. Sürdürmek istediğiniz Dockerfile dosyanızda değişiklik yaptıysanız Hayır ' ı seçin.

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

1. Siteyi, beklendiği gibi çalıştığını doğrulamak için şimdi yerel olarak çalıştırın (**F5** veya **CTRL + F5**). Her şey doğru yapılandırılmışsa, hava durumu tahmin verileri ' ni görürsünüz.

   Kapsayıcı düzenlemesi eklediğinizde kullandığınız ilk proje, çalıştırdığınızda veya hata ayıkladığınızda başlatılacak şekilde ayarlanır. başlatma eylemini docker-compose projesi için **Project özelliklerinde** yapılandırabilirsiniz.  Docker-Compose projesi düğümünde bağlam menüsünü açmak için sağ tıklayın ve sonra **Özellikler**' i seçin veya **alt** + **ENTER**' u kullanın.  Aşağıdaki ekran görüntüsünde, burada kullanılan çözüm için istediğiniz özellikler gösterilmektedir.  Örneğin, **hizmet URL 'si** özelliğini özelleştirerek yüklenen sayfayı değiştirebilirsiniz.

   ![Docker-Compose proje özelliklerinin ekran görüntüsü](media/tutorial-multicontainer/launch-action.png)

   Bu, başlatıldığında gördüğünüz gibi:

   ![Çalışan Web uygulamasının ekran görüntüsü](media/tutorial-multicontainer/vs-2022/webfrontend.png)

   Web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

[Kapsayıcılarınızı Azure 'a](/azure/containers)dağıtmaya yönelik seçeneklere bakın.

Her bir hata ayıklama görevi için gerekli olmayan çok sayıda mikro hizmetlerle çalışıyorsanız, hata ayıklama oturumu sırasında hangi hizmetlerin başlatıldığı üzerinde daha fazla denetim için Docker Compose başlatma profillerini kullanabilirsiniz. Bkz. [Docker Compose için başlatma profillerini yönetme](launch-profiles.md).

## <a name="see-also"></a>Ayrıca bkz.
  
[Docker Compose](https://docs.docker.com/compose/)  
[Kapsayıcı araçları](./index.yml)