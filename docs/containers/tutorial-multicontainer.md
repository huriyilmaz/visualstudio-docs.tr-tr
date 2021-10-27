---
title: Docker Compose kullanarak birden çok kapsayıcıyla Docker Compose
author: ghogen
description: Docker Compose ile birden çok kapsayıcı kullanmayı Docker Compose
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 10/08/2021
ms.technology: vs-container-tools
ms.topic: tutorial
ms.openlocfilehash: 50e634e56f88c08ff23a0b668b74c0373d8d9dca
ms.sourcegitcommit: 4efdab6a579b31927c42531bb3f7fdd92890e4ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "130351541"
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
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET platformlar** arası geliştirme iş yükünün yüklü olduğu [2019](https://visualstudio.microsoft.com/downloads) sürümü
* [.NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) ile geliştirme için .NET Core 3 Geliştirme Araçları.
::: moniker-end

::: moniker range=">=vs-2022"

* [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* Visual Studio Geliştirme, **Azure** Araçları iş yükü ve/veya **.NET platformlar** arası geliştirme iş yükü yüklü [2022 RC'ye](https://visualstudio.microsoft.com/vs/preview/) sahip. Buna .NET Core 3.1 ve .NET 6 geliştirme araçları dahildir.
* [.NET 5 ile geliştirme](https://dotnet.microsoft.com/download/dotnet-core/5.0) için .NET 5 Geliştirme Araçları.
::: moniker-end

## <a name="create-a-web-application-project"></a>Web Uygulaması projesi oluşturma

Bu Visual Studio, Razor **ASP.NET Core bir web** uygulaması oluşturmak `WebFrontEnd` için adlı bir Web Uygulaması projesi oluşturun.
  
::: moniker range="vs-2017"

Docker Desteğini **Etkinleştir'i seçme.** Docker desteğini daha sonra eksersiniz.

![Web projesi oluşturma ekran görüntüsü.](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![Web Uygulaması projesi ASP.NET Core gösteren ekran görüntüsü.](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

Docker Desteğini **Etkinleştir'i seçme.** Docker desteğini daha sonra eksersiniz.

![Web projesi oluştururken Ek bilgiler ekran görüntüsü. Docker Desteğini Etkinleştir seçeneği seçilmez.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end
::: moniker range=">=vs-2022"

![Web Uygulaması projesi ASP.NET Core gösteren ekran görüntüsü.](./media/tutorial-multicontainer/vs-2022/create-web-project.png)

Docker Desteğini **Etkinleştir'i seçme.** Docker desteğini daha sonra eksersiniz.

![Web projesi oluştururken Ek bilgiler ekran görüntüsü. Docker Desteğini Etkinleştir seçeneği seçilmez.](./media/tutorial-multicontainer/vs-2022/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Web API'si projesi oluşturma

Aynı çözüme bir proje ekleyin ve *myWebAPI olarak buna çağrıyın.* Proje türü olarak **API'yi** seçin ve HTTPS için yapılandır onay **kutusunu temizleyin.** Bu tasarımda, aynı web uygulamasındaki kapsayıcılar arasındaki iletişim için değil, yalnızca istemciyle iletişim için SSL kullanıyoruz. Yalnızca `WebFrontEnd` HTTPS gerekir ve örneklerde yer alan kodda bu onay kutusunun işaretinin temiz olduğu varsayıldı. Genel olarak, Visual Studio tarafından kullanılan .NET geliştirici sertifikaları kapsayıcıdan kapsayıcıya istekler için değil yalnızca dıştan kapsayıcıya istekler için desteklemektedir.

::: moniker range="vs-2017"
   ![Web API'si projesi oluşturma ekran görüntüsü.](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Web API'si projesi oluşturma ekran görüntüsü.](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
::: moniker-end
::: moniker range=">=vs-2022"
   ![Web API'si projesi oluşturma ekran görüntüsü.](media/tutorial-multicontainer/vs-2022/create-web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Web API'sini çağıran kod ekleme

:::moniker range="vs-2017"

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

1. Projede `WebFrontEnd` Kapsayıcı **Orchestrator Desteği >'yi seçin.** **Docker Destek Seçenekleri iletişim** kutusu görüntülenir.

1. 'yi **Docker Compose.**

1. Hedef işletim sisteminizi (örneğin, Linux) seçin.

   ![Hedef işletim sistemi seçme ekran görüntüsü.](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio *çözümdeki docker-compose düğümünde bir docker-compose.yml* dosyası ve *bir .dockerignore* dosyası oluşturur ve bu proje başlangıç projesi olduğunu gösteren kalın yazı tipiyle gösterilir. 

   ![docker-compose Çözüm Gezgini eklenmiş bir dosyanın ekran görüntüsü.](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

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

1. Web API'si projesinde proje düğümüne tekrar sağ tıklayın ve Kapsayıcı Orchestrator **Desteği**  >  **Ekle'yi seçin.** İlk **Docker Compose** ve ardından aynı hedef işletim sistemi seçin.  

    > [!NOTE]
    > Bu adımda, Visual Studio dockerfile oluşturma teklifi sunacak. Docker desteği olan bir projede bunu yaparsanız, mevcut Dockerfile dosyasının üzerine yazmak isteyip istemediğiniz sorabilirsiniz. Dockerfile dosyanız üzerinde tutmak istediğiniz değişiklikler yaptıysanız hayır'ı seçin.

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

1. Siteyi yerel olarak çalıştırmak için Web API hizmetine yapılan istek için farklı bir URL kullan çünkü docker compose konak adlarını kendi ağına ayarlar ve böylece diğer hizmetler konak adı olarak görünür `mywebapi` hale gelir. Yerel olarak çalıştırmak için, önce `mywebapi` `OnGet` *Index.cshtml.cs'de* yöntemini localhost ve bağlantı noktası söz dizimi ile değiştirin. Bağlantı noktası numarasını, webapi projesini kendi başına başlatmadan veya Özellikler (  **Alt** Enter) bölümündeki Hata Ayıklama bölümündeki Uygulama **URL'si** **ayarından Project** + **edinebilirsiniz.**

   ```csharp
   request.RequestUri = new Uri("http://localhost:{port}/WeatherForecast");
   ```

1. Sitenin beklendiği gibi çalıştığını doğrulamak için siteyi yerel olarak çalıştırın. Web API projesine sağ tıklayın, Başlangıç projesi olarak ayarla'yı ve ardından Hata Ayıklama olmadan   >  **Başlat'ı seçin.** Ardından WebFrontEnd proje düğümüne sağ tıklayın, Başlangıç projesi olarak ayarla'yı **seçin** ve hata ayıklamayı **başlatmak için F5'e** basın.

   Her şey .NET Core 2.x sürümüyle doğru şekilde yapılandırıldıysa "Hello from webfrontend and webapi (1 değeriyle)" (Hello from webfrontend and webapi)" (Hello from webfrontend and webapi (1 değeriyle) iletisiyle birlikte gelirsiniz.  .NET Core 3 ile hava durumu tahmin verilerini görüyorsunuz.

   Yerel olarak çalıştığını doğruladıktan `OnGet` *sonra, Dizin.cshtml.cs'de* URL'yi, dizinde çalıştırmaya hazır olarak mywebapi'ye başvurarak Docker Compose. Hem Docker hem de kapsayıcı dışı çalıştırma ve hata ayıklama yapılandırmaları için aynı kodu kullanmak isterseniz URL'yi almak için bir yapılandırma dosyası kullanmak iyi olabilir.

1. Kapsayıcı düzenlemesi eklerken ilk proje, çalıştıracak veya hata ayıklayacak şekilde ayarlanır. Başlatma eylemlerini docker-compose **projesi Project** Özellikler'de yapılandırabilirsiniz.  docker-compose proje düğümünde bağlam menüsünü açmak için sağ tıklayın ve özellikler'i **seçin** veya Alt+Enter tuşlarına basın.  Aşağıdaki ekran görüntüsü, burada kullanılan çözüm için istediğiniz özellikleri gösterir.  Örneğin, Hizmet URL'si özelliğini özelleştirerek yüklenen **sayfayı değiştirebilirsiniz.**

   ![docker-compose proje özelliklerinin ekran görüntüsü.](media/tutorial-multicontainer/launch-action.png)

   İlk kez (.NET Core 2.x sürümü) şu şekildedir:

   ![Web uygulamasını çalıştırma ekran görüntüsü.](media/tutorial-multicontainer/webfrontend.png)

   .NET 3.1 için web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

:::moniker-end

::: moniker range="vs-2019"

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

1. Projede `WebFrontEnd` Kapsayıcı **Orchestrator Desteği >'yi seçin.** **Docker Destek Seçenekleri iletişim** kutusu görüntülenir.

1. 'yi **Docker Compose.**

1. Hedef işletim sisteminizi (örneğin, Linux) seçin.

   ![Hedef işletim sistemi seçme ekran görüntüsü.](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio *çözümdeki docker-compose düğümünde bir docker-compose.yml* dosyası ve *bir .dockerignore* dosyası oluşturur ve bu proje başlangıç projesi olduğunu gösteren kalın yazı tipiyle gösterilir. 

   ![docker-compose Çözüm Gezgini eklenmiş ekran görüntüsü.](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

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

1. Web API projesinde proje düğümüne tekrar sağ tıklayın ve Kapsayıcı Orchestrator **Desteği**  >  **Ekle'yi seçin.** Bir **Docker Compose** ve ardından aynı hedef işletim sistemi seçin.  

    > [!NOTE]
    > Bu adımda, Visual Studio dockerfile oluşturma teklifi sunacak. Docker desteği olan bir projede bunu yaparsanız, mevcut Dockerfile dosyasının üzerine yazmak isteyip istemediğiniz sorabilirsiniz. Dockerfile dosyanız üzerinde tutmak istediğiniz değişiklikler yaptısanız hayır'ı seçin.

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

1. Siteyi yerel olarak çalıştırmak için Web API hizmetine yapılan istek için farklı bir URL kullan çünkü docker compose konak adlarını kendi ağına ayarlar ve böylece diğer hizmetler konak adı olarak görünür `mywebapi` hale gelir. Yerel olarak çalıştırmak için, önce `mywebapi` `OnGet` *Index.cshtml.cs'de* yöntemini localhost ve bağlantı noktası söz dizimi ile değiştirin. Bağlantı noktası numarasını, webapi projesini kendi başına başlatmadan veya Özellikler (  **Alt** Enter) bölümündeki Hata Ayıklama bölümündeki Uygulama **URL'si** **ayarından Project** + **edinebilirsiniz.**

   ```csharp
   request.RequestUri = new Uri("http://localhost:{port}/WeatherForecast");
   ```

1. Sitenin beklendiği gibi çalıştığını doğrulamak için siteyi yerel olarak çalıştırın. Web API projesine sağ tıklayın, Başlangıç projesi olarak ayarla'yı ve ardından Hata Ayıklama olmadan   >  **Başlat'ı seçin.** Ardından WebFrontEnd proje düğümüne sağ tıklayın, Başlangıç projesi olarak ayarla'yı **seçin** ve hata ayıklamayı **başlatmak için F5'e** basın.

   Her şey .NET Core 2.x sürümüyle doğru şekilde yapılandırıldıysa "Hello from webfrontend and webapi (1 değeriyle)" (Hello from webfrontend and webapi)" (Hello from webfrontend and webapi (1 değeriyle) iletisiyle birlikte gelirsiniz.  .NET Core 3 ile hava durumu tahmin verilerini görüyorsunuz.

   Yerel olarak çalıştığını doğruladıktan sonra `OnGet` *Index.cshtml.cs'de* url'sini, dizinde çalıştırma hazırlığı için mywebapi'ye başvurarak Docker Compose. Hem Docker hem de kapsayıcı dışı çalıştırma ve hata ayıklama yapılandırmaları için aynı kodu kullanmak isterseniz URL'yi almak için bir yapılandırma dosyası kullanabilirsiniz.

1. Kapsayıcı düzenlemesi eklerken ilk proje, çalıştıracak veya hata ayıklayacak şekilde ayarlanır. Başlatma eylemlerini docker-compose **Project** Özellikler'de yapılandırabilirsiniz.  docker-compose proje düğümünde bağlam menüsünü açmak için sağ tıklayın ve özellikler'i **seçin** veya Alt+Enter tuşlarına basın.  Aşağıdaki ekran görüntüsü, burada kullanılan çözüm için istediğiniz özellikleri gösterir.  Örneğin, Hizmet URL'si özelliğini özelleştirerek yüklenen **sayfayı değiştirebilirsiniz.**

   ![docker-compose proje özelliklerinin ekran görüntüsü.](media/tutorial-multicontainer/launch-action.png)

   İlk kez (.NET Core 2.x sürümü) şu şekildedir:

   ![Web uygulamasını çalıştırma ekran görüntüsü.](media/tutorial-multicontainer/webfrontend.png)

   .NET 3.1 için web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

1. Şimdi hata ayıklayıcının Web API projesine değil yalnızca WebFrontEnd'e bağlı olmasıyla ilgilendiğinizi varsayalım. Menü çubuğunda başlat düğmesinin yanındaki açılan menüyü kullanarak hata ayıklama seçenekleri menüsünü açabilirsiniz; **Yönet'i Docker Compose Başlat'ı Ayarlar.**

   ![Oluştur ve Oluştur menü öğesinde hata Ayarlar ekran görüntüsü.](media/launch-settings/debug-dropdown-manage-compose.png)

   Yönetim **Docker Compose Başlatma Ayarlar** iletişim kutusu görüntülenir. Bu iletişim kutusuyla, hata ayıklayıcı ekli veya hata ayıklayıcısı ekli olmadan başlatılan bir hata ayıklama oturumu sırasında hangi hizmet alt kümesinin başlat olduğunu ve başlatma hizmetini ve URL'sini kontrol edin. Bkz. [Compose hizmetlerinin bir alt kümesini başlatma.](launch-profiles.md)

   ![Yönetim ve Başlatma Docker Compose iletişim Ayarlar ekran görüntüsü.](media/tutorial-multicontainer/vs-2022/launch-profile-1.png)

   Yeni **profil** oluşturmak için Yeni'yi seçin ve olarak ad `Debug WebFrontEnd only` girin. Ardından Web API projesini Hata **ayıklama** olmadan başlat olarak ayarlayın, WebFrontEnd projesini hata ayıklama ile başlayacak şekilde ayarlanmış şekilde bırakın ve Kaydet'i **seçin.**

   Yeni yapılandırma, sonraki F5 için varsayılan **olarak seçilir.**

1. Beklediğiniz gibi çalıştığını onaylamak için **F5** tuşuna basın.

Tebrikler, özel bir Docker Compose profiline sahip bir Docker Compose çalıştırabilirsiniz.


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

1. Web API projesinde çağrısına açıklama açıklaması girin çünkü bu kod Web API'sini aramak <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> için HTTPS değil HTTP kullanır.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. Projede `WebFrontEnd` Kapsayıcı **Orchestrator Desteği >'yi seçin.** **Docker Destek Seçenekleri iletişim** kutusu görüntülenir.

1. **Docker Compose.**

1. Hedef işletim sisteminizi (örneğin, Linux) seçin.

   ![Hedef işletim sistemi seçme ekran görüntüsü.](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio *çözümdeki docker-compose düğümünde bir docker-compose.yml* dosyası ve *bir .dockerignore* dosyası oluşturur ve bu proje başlangıç projesi olduğunu gösteren kalın yazı tipiyle gösterilir. 

   ![docker-compose Çözüm Gezgini eklenmiş ekran görüntüsü.](media/tutorial-multicontainer/vs-2022/multicontainer-solution-explorer.png)

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

1. Web API projesinde proje düğümüne tekrar sağ tıklayın ve Kapsayıcı Orchestrator **Desteği**  >  **Ekle'yi seçin.** Bir **Docker Compose** ve ardından aynı hedef işletim sistemi seçin.  

    > [!NOTE]
    > Bu adımda, Visual Studio dockerfile oluşturma teklifi sunacak. Docker desteği olan bir projede bunu yaparsanız, mevcut Dockerfile dosyasının üzerine yazmak isteyip istemediğiniz sorabilirsiniz. Dockerfile dosyanız üzerinde tutmak istediğiniz değişiklikler yaptısanız hayır'ı seçin.

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

1. Siteyi yerel olarak çalıştırmak için Web API hizmetine yapılan istek için farklı bir URL kullan çünkü docker compose konak adlarını kendi ağına ayarlar ve böylece diğer hizmetler konak adı olarak görünür `mywebapi` hale gelir. Yerel olarak çalıştırmak için, önce `mywebapi` `OnGet` *Index.cshtml.cs'de* yöntemini localhost ve bağlantı noktası söz dizimi ile değiştirin. Bağlantı noktası numarasını webapi projesini kendi başına başlatmadan veya Hata Ayıklama bölümündeki **Project** Özellikleri'nde bulup Hata ayıklama başlatma profilleri kullanıcı arabirimini aç'ı seçin, sonra **IIS Express**'yi seçin ve Uygulama **URL'si** ayarını bulun. 

   ```csharp
   request.RequestUri = new Uri("http://localhost:{port}/WeatherForecast");
   ```

   Siteyi şimdi IIS Express olarak çalıştırarak beklendiği gibi çalıştığını doğrulayın: Web API projesine sağ tıklayın ve Hata Ayıklamadan  >  **Başlat'ı seçin.** Ardından WebFrontEnd proje düğümüne sağ tıklayın, Başlangıç projesi olarak ayarla'yı **seçin** ve hata ayıklamayı **başlatmak için F5'e** basın. Her şey doğru yapılandırıldıysa hava durumu tahmin verilerini görüyorsunuz.

   Yerel olarak çalıştığını doğruladıktan sonra `OnGet` *Index.cshtml.cs'de* url'sini, dizinde çalıştırma hazırlığı için mywebapi'ye başvurarak Docker Compose. Hem Docker hem de kapsayıcı dışı çalıştırma ve hata ayıklama yapılandırmaları için aynı kodu kullanmak isterseniz URL'yi almak için bir yapılandırma dosyası kullanabilirsiniz.

1. Kapsayıcı düzenlemesi eklerken ilk proje, çalıştıracak veya hata ayıklayacak şekilde ayarlanır. Başlatma eylemlerini docker-compose **Project** Özellikler'de yapılandırabilirsiniz.  docker-compose proje düğümünde bağlam menüsünü açmak için sağ tıklayın ve özellikler'i **seçin veya** **Alt Enter'ı** + **kullanın.**  Aşağıdaki ekran görüntüsü, burada kullanılan çözüm için istediğiniz özellikleri gösterir.  Örneğin, Hizmet URL'si özelliğini özelleştirerek yüklenen **sayfayı değiştirebilirsiniz.**

   ![docker-compose proje özelliklerinin ekran görüntüsü.](media/tutorial-multicontainer/launch-action.png)

   Başlatıldıklarda şu ifadeleri görüyorsunuz:

   ![Web uygulamasını çalıştırma ekran görüntüsü.](media/tutorial-multicontainer/vs-2022/webfrontend.png)

   Web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

1. Şimdi hata ayıklayıcının Web API projesine değil yalnızca WebFrontEnd'e bağlı olmasıyla ilgilendiğinizi varsayalım. Menü çubuğunda başlat düğmesinin yanındaki açılan menüyü kullanarak hata ayıklama seçenekleri menüsünü açabilirsiniz; **Yönet'i Docker Compose Başlat'ı Ayarlar.**

   ![Oluştur ve Oluştur menü öğesinde hata Ayarlar ekran görüntüsü.](media/tutorial-multicontainer/vs-2022/debug-dropdown-manage-compose.png)

   Yönetim **Docker Compose Başlatma Ayarlar** iletişim kutusu görüntülenir. Bu iletişim kutusuyla, hata ayıklayıcı ekli veya hata ayıklayıcısı ekli olmadan başlatılan bir hata ayıklama oturumu sırasında hangi hizmet alt kümesinin başlat olduğunu ve başlatma hizmetini ve URL'sini kontrol edin. Bkz. [Compose hizmetlerinin bir alt kümesini başlatma.](launch-profiles.md)

   ![Yönetim ve Başlatma Docker Compose iletişim Ayarlar ekran görüntüsü.](media/tutorial-multicontainer/vs-2022/launch-profile-1.png)

   Yeni **profil** oluşturmak için Yeni'yi seçin ve olarak ad `Debug WebFrontEnd only` girin. Ardından Web API projesini Hata **ayıklama** olmadan başlat olarak ayarlayın, WebFrontEnd projesini hata ayıklama ile başlayacak şekilde ayarlanmış şekilde bırakın ve Kaydet'i **seçin.**

   Yeni yapılandırma, sonraki F5 için varsayılan **olarak seçilir.**

1. Beklediğiniz gibi çalıştığını onaylamak için **F5** tuşuna basın.

Tebrikler, özel bir Docker Compose profiline sahip bir Docker Compose çalıştırabilirsiniz.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Kapsayıcılarınızı Azure'a dağıtma [seçeneklerine bakın.](/azure/containers)

## <a name="see-also"></a>Ayrıca bkz.
  
[Docker Compose](https://docs.docker.com/compose/)  
[Kapsayıcı araçları](./index.yml)