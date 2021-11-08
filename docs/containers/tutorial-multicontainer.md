---
title: Docker Compose kullanarak birden çok kapsayıcıyla çalışma
author: ghogen
description: Docker Compose ile birden çok kapsayıcıyı kullanmayı öğrenin
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 10/08/2021
ms.technology: vs-container-tools
ms.topic: tutorial
ms.openlocfilehash: 6959f7b913abc3a32c579ebe73454e78d97caeeb
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132001970"
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
* **Web geliştirme**, **Azure araçları** iş yükü ve/veya **.net platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2019](https://visualstudio.microsoft.com/downloads)
* .NET Core 3,1 ile geliştirme için [.NET Core 3 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/3.1) .
::: moniker-end

::: moniker range=">=vs-2022"

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-windows)
* **Web geliştirme**, **Azure araçları** iş yükü ve/veya **.net platformlar arası geliştirme** iş yükü yüklü [Visual Studio 2022](https://visualstudio.microsoft.com/downloads/) . Buna .NET Core 3,1 ve .NET 6 geliştirme araçları dahildir.
* .NET 5 ile geliştirme için [.NET 5 geliştirme araçları](https://dotnet.microsoft.com/download/dotnet-core/5.0) .
::: moniker-end

## <a name="create-a-web-application-project"></a>Web uygulaması projesi oluşturma

Visual Studio ' de, Razor sayfaları olan bir web uygulaması oluşturmak için adlı bir **ASP.NET Core web uygulaması** projesi oluşturun `WebFrontEnd` .
  
::: moniker range="vs-2017"

**Docker desteğini etkinleştir**' i seçmeyin. Docker desteğini daha sonra ekleyeceksiniz.

![Web projesi oluşturma ekranının ekran görüntüsü.](./media/tutorial-multicontainer/docker-tutorial-enable-docker-support.png)

::: moniker-end

::: moniker range="vs-2019"

![ASP.NET Core Web uygulaması projesi oluştur ' un gösterildiği ekran görüntüsü.](./media/tutorial-multicontainer/vs-2019/create-web-project1.png)

**Docker desteğini etkinleştir**' i seçmeyin. Docker desteğini daha sonra ekleyeceksiniz.

![Web projesi oluştururken ek bilgi ekranının ekran görüntüsü. Docker desteğini etkinleştirme seçeneği seçili değil.](./media/tutorial-multicontainer/vs-2019/create-web-project-additional-information.png)

::: moniker-end
::: moniker range=">=vs-2022"

![ASP.NET Core Web uygulaması projesi oluştur ' un gösterildiği ekran görüntüsü.](./media/tutorial-multicontainer/vs-2022/create-web-project.png)

**Docker desteğini etkinleştir**' i seçmeyin. Docker desteğini daha sonra ekleyeceksiniz.

![Web projesi oluştururken ek bilgi ekranının ekran görüntüsü. Docker desteğini etkinleştirme seçeneği seçili değil.](./media/tutorial-multicontainer/vs-2022/create-web-project-additional-information.png)

::: moniker-end

## <a name="create-a-web-api-project"></a>Web API projesi oluşturma

Aynı çözüme bir proje ekleyin ve *Mywebapi* olarak çağırın. Proje türü olarak **API** ' yi SEÇIN ve **https için yapılandırma** onay kutusunu temizleyin. Bu tasarımda, aynı Web uygulamasındaki kapsayıcılar arasında iletişim için değil, yalnızca istemciyle iletişim için SSL kullandık. Yalnızca `WebFrontEnd` https gerektirir ve örneklerdeki kod bu onay kutusunu temizlemiş olduğunu varsayar. genel olarak, Visual Studio tarafından kullanılan .net geliştirici sertifikaları, kapsayıcı istekleri için değil, yalnızca dış kapsayıcı istekleri için desteklenir.

::: moniker range="vs-2017"
   ![Web API projesi oluşturma ekranının ekran görüntüsü.](./media/tutorial-multicontainer/docker-tutorial-mywebapi.png)
::: moniker-end
::: moniker range="vs-2019"
   ![Web API projesi oluşturma ekranının ekran görüntüsü.](./media/tutorial-multicontainer/vs-2019/create-webapi-project.png)
::: moniker-end
::: moniker range=">=vs-2022"
   ![Web API projesi oluşturma ekranının ekran görüntüsü.](media/tutorial-multicontainer/vs-2022/create-web-api-project.png)
::: moniker-end

## <a name="add-code-to-call-the-web-api"></a>Web API 'sini çağırmak için kod ekleme

:::moniker range="vs-2017"

1. `WebFrontEnd`Projede *Index. cshtml. cs* dosyasını açın ve `OnGet` yöntemi aşağıdaki kodla değiştirin.

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
    > Gerçek dünyada kodda, `HttpClient` her istekten sonra atılamaz. En iyi uygulamalar için bkz. [Esnek http isteklerini uygulamak Için HttpClientFactory kullanma](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

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

    .NET Core 3,1 ve üzeri sürümlerde, zaten orada olan dalgalı tahmin API 'sini kullanabilmeniz için buna ihtiyacınız yoktur. Ancak, Web API <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*>  'si projesinde, Web API 'sini çağırmak IÇIN https DEĞIL http 'yi kullandığından, bu kod için ' a yönelik çağrıyı açıklamanız gerekir.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. `WebFrontEnd`Projede **> kapsayıcı Orchestrator desteği ekle**' yi seçin. **Docker destek seçenekleri** iletişim kutusu görüntülenir.

1. **Docker Compose** seçin.

1. Hedef işletim sistemini (örneğin, Linux) seçin.

   ![Hedef işletim sistemini seçme ekran görüntüsü.](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio çözümdeki **docker-compose** düğümünde bir *docker-compose. yıml* dosyası ve *. dockerıgnore* dosyası oluşturur ve bu proje, başlangıç projesi olduğunu gösteren kalýn yazı tipinde görünür.

   ![Docker-Compose projesi eklenen Çözüm Gezgini ekran görüntüsü.](media/tutorial-multicontainer/multicontainer-solution-explorer.png)

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

1. Siteyi yerel olarak çalıştırmak için, Web API hizmetine yapılan istek için farklı bir URL kullanmanız gerekir, çünkü Docker Compose konak adlarını kendi ağında ayarlıyor, bu nedenle `mywebapi` diğer hizmetlere ana bilgisayar adı olarak görünür. Yerel olarak çalıştırmak için, ilk olarak `mywebapi` `OnGet` *Index. cshtml. cs* dosyasındaki yöntemi bir localhost ve bağlantı noktası sözdizimiyle değiştirin. bağlantı noktası numarasını kendi üzerinde veya **Project özelliklerinin** **hata ayıklama** bölümünde yer alan **uygulama URL 'si** ayarından kendi üzerinde veya uygulama URL ayarından alabilirsiniz (**Alt** + **Enter**).

   ```csharp
   request.RequestUri = new Uri("http://localhost:{port}/WeatherForecast");
   ```

1. Siteyi beklendiği gibi çalıştığını doğrulamak için şimdi yerel olarak çalıştırın. Web API projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin **ve hata ayıklama**  >  **olmadan Başlat**' ı seçin. Ardından, Webön uç proje düğümüne sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin ve hata ayıklamayı başlatmak için **F5** ' e basın.

   Her şey .NET Core 2. x sürümü ile doğru şekilde yapılandırıldıysa, "Web ön ucu ve WebApi 'den (değer 1 ile) Merhaba" iletisini görürsünüz.  .NET Core 3 ile hava durumu tahmin verilerini görürsünüz.

   Yerel olarak çalıştığını doğruladıktan sonra, `OnGet` *Index. cshtml. cs* içindeki URL 'yi Docker Compose ' de çalıştırmaya hazırlanmakta mywebapi başvuruya geri doğru olarak değiştirin. Hem Docker hem de kapsayıcı olmayan çalışma ve hata ayıklama yapılandırmaları için aynı kodu kullanmak istiyorsanız, URL 'YI almak için bir yapılandırma dosyası kullanmak isteyebilirsiniz.

1. Kapsayıcı düzenlemesi eklediğinizde kullandığınız ilk proje, çalıştırdığınızda veya hata ayıkladığınızda başlatılacak şekilde ayarlanır. başlatma eylemini docker-compose projesi için **Project özelliklerinde** yapılandırabilirsiniz.  Docker-Compose projesi düğümünde bağlam menüsünü açmak için sağ tıklayın, ardından **Özellikler**' i seçin veya alt + ENTER ' u kullanın.  Aşağıdaki ekran görüntüsünde, burada kullanılan çözüm için istediğiniz özellikler gösterilmektedir.  Örneğin, **hizmet URL 'si** özelliğini özelleştirerek yüklenen sayfayı değiştirebilirsiniz.

   ![Docker-Compose proje özelliklerinin ekran görüntüsü.](media/tutorial-multicontainer/launch-action.png)

   Başlatıldığında gördüğünüz Özellikler (.NET Core 2. x sürümü):

   ![Çalışan Web uygulamasının ekran görüntüsü.](media/tutorial-multicontainer/webfrontend.png)

   .NET 3,1 için Web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

:::moniker-end

::: moniker range="vs-2019"

1. `WebFrontEnd`Projede *Index. cshtml. cs* dosyasını açın ve `OnGet` yöntemi aşağıdaki kodla değiştirin.

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
    > Gerçek dünyada kodda, `HttpClient` her istekten sonra atılamaz. En iyi uygulamalar için bkz. [Esnek http isteklerini uygulamak Için HttpClientFactory kullanma](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

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

    .NET Core 3,1 ve üzeri sürümlerde, zaten orada olan dalgalı tahmin API 'sini kullanabilmeniz için buna ihtiyacınız yoktur. Ancak, Web API <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*>  'si projesinde, Web API 'sini çağırmak IÇIN https DEĞIL http 'yi kullandığından, bu kod için ' a yönelik çağrıyı açıklamanız gerekir.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. `WebFrontEnd`Projede **> kapsayıcı Orchestrator desteği ekle**' yi seçin. **Docker destek seçenekleri** iletişim kutusu görüntülenir.

1. **Docker Compose** seçin.

1. Hedef işletim sistemini (örneğin, Linux) seçin.

   ![Hedef işletim sistemini seçme ekran görüntüsü.](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio çözümdeki **docker-compose** düğümünde bir *docker-compose. yıml* dosyası ve *. dockerıgnore* dosyası oluşturur ve bu proje, başlangıç projesi olduğunu gösteren kalýn yazı tipinde görünür.

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

1. Siteyi yerel olarak çalıştırmak için Web API hizmetine yapılan istek için farklı bir URL kullan çünkü docker compose konak adlarını kendi ağına ayarlar ve böylece diğer hizmetler konak adı olarak görünür `mywebapi` hale gelir. Yerel olarak çalıştırmak için, önce `mywebapi` `OnGet` *Index.cshtml.cs'de* yöntemini localhost ve bağlantı noktası söz dizimi ile değiştirin. Bağlantı noktası numarasını, webapi projesini kendi başına başlatmadan veya Özellikler (  **Alt** Enter) bölümündeki Hata Ayıklama bölümündeki Uygulama **URL'si** **ayarından Project** + **edinebilirsiniz.**

   ```csharp
   request.RequestUri = new Uri("http://localhost:{port}/WeatherForecast");
   ```

1. Sitenin beklendiği gibi çalıştığını doğrulamak için siteyi yerel olarak çalıştırın. Web API projesine sağ tıklayın, Başlangıç projesi olarak ayarla'yı ve ardından Hata Ayıklama olmadan   >  **Başlat'ı seçin.** Ardından WebFrontEnd proje düğümüne sağ tıklayın, Başlangıç projesi olarak ayarla'yı **seçin** ve hata ayıklamayı **başlatmak için F5'e** basın.

   Her şey .NET Core 2.x sürümüyle doğru şekilde yapılandırıldıysa "Hello from webfrontend and webapi (1 değeriyle)" (Hello from webfrontend and webapi)" (Hello from webfrontend and webapi (1 değeriyle) iletisiyle birlikte gelirsiniz.  .NET Core 3 ile hava durumu tahmin verilerini görüyorsunuz.

   Yerel olarak çalıştığını doğruladıktan `OnGet` *sonra, Dizin.cshtml.cs'de* URL'yi, dizinde çalıştırma hazırlığında mywebapi'ye başvurarak Docker Compose. Hem Docker hem de kapsayıcı dışı çalıştırma ve hata ayıklama yapılandırmaları için aynı kodu kullanmak isterseniz URL'yi almak için bir yapılandırma dosyası kullanabilirsiniz.

1. Kapsayıcı düzenlemesi eklerken ilk proje, çalıştıracak veya hata ayıklayacak şekilde ayarlanır. Başlatma eylemlerini docker-compose **Project** Özellikler'de yapılandırabilirsiniz.  docker-compose proje düğümünde bağlam menüsünü açmak için sağ tıklayın ve özellikler'i **seçin** veya Alt+Enter tuşlarına basın.  Aşağıdaki ekran görüntüsü, burada kullanılan çözüm için istediğiniz özellikleri gösterir.  Örneğin, Hizmet URL'si özelliğini özelleştirerek yüklenen **sayfayı değiştirebilirsiniz.**

   ![docker-compose proje özelliklerinin ekran görüntüsü.](media/tutorial-multicontainer/launch-action.png)

   İlk kez (.NET Core 2.x sürümü) şu şekildedir:

   ![Web uygulamasını çalıştırma ekran görüntüsü.](media/tutorial-multicontainer/webfrontend.png)

   .NET 3.1 için web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

1. Şimdi hata ayıklayıcının Web API projesine değil yalnızca WebFrontEnd'e bağlı olmasıyla ilgilendiğinizi varsayalım. Menü çubuğunda başlat düğmesinin yanındaki açılan menüyü kullanarak hata ayıklama seçenekleri menüsünü açabilirsiniz; **Başlat'ı Docker Compose'ı Ayarlar.**

   ![Hata Ayıklama Oluştur ve Oluştur menü Ayarlar ekran görüntüsü.](media/launch-settings/debug-dropdown-manage-compose.png)

   Yönetim **Docker Compose Başlat Ayarlar** iletişim kutusu görüntülenir. Bu iletişim kutusuyla, hata ayıklayıcı ekli veya hata ayıklayıcısı ekli olmadan başlatılan bir hata ayıklama oturumu sırasında hangi hizmet alt kümesinin başlat olduğunu ve başlatma hizmetini ve URL'sini kontrol edin. Bkz. [Compose hizmetlerinin bir alt kümesini başlatma.](launch-profiles.md)

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

1. Web API projesinde çağrısına açıklama açıklaması girin çünkü bu kod Web API'sini aramak için HTTPS değil <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection*> HTTP kullanır.

    ```csharp
                //app.UseHttpsRedirection();
    ```

1. Proje içinde `WebFrontEnd` Kapsayıcı **Orchestrator Desteğine >'yi seçin.** **Docker Destek Seçenekleri iletişim** kutusu görüntülenir.

1. **Docker Compose.**

1. Hedef işletim sisteminizi (örneğin, Linux) seçin.

   ![Hedef işletim sistemi seçme ekran görüntüsü.](media/tutorial-multicontainer/docker-tutorial-docker-support-options.PNG)

   Visual Studio *çözümdeki docker-compose düğümünde bir docker-compose.yml* dosyası ve *bir .dockerignore* dosyası oluşturur ve bu proje başlangıç projesi olduğunu gösteren kalın yazı tipiyle gösterilir. 

   ![docker-compose Çözüm Gezgini eklenmiş bir dosyanın ekran görüntüsü.](media/tutorial-multicontainer/vs-2022/multicontainer-solution-explorer.png)

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

1. Siteyi yerel olarak çalıştırmak için Web API hizmetine yapılan istek için farklı bir URL kullan çünkü docker compose konak adlarını kendi ağına ayarlar ve böylece diğer hizmetler konak adı olarak görünür `mywebapi` hale gelir. Yerel olarak çalıştırmak için, önce `mywebapi` `OnGet` *Index.cshtml.cs'de* yöntemini localhost ve bağlantı noktası söz dizimi ile değiştirin. Bağlantı noktası numarasını webapi projesini kendi başına başlatma veya Hata Ayıklama bölümündeki **Project**  Özellikleri'nde bulma, Hata ayıklama başlatma profilleri kullanıcı arabirimini aç'ı seçin, ardından **IIS Express'yi** seçin ve Uygulama **URL'si** ayarını bulun. 

   ```csharp
   request.RequestUri = new Uri("http://localhost:{port}/WeatherForecast");
   ```

   Siteyi şimdi yerel IIS Express çalıştırarak beklendiği gibi çalıştığını doğrulayın: Web API projesine sağ tıklayın ve Hata ayıklamadan  >  **Başlat'ı seçin.** Ardından WebFrontEnd proje düğümüne sağ tıklayın, Başlangıç projesi olarak ayarla'yı **seçin** ve hata ayıklamayı **başlatmak için F5'e** basın. Her şey doğru yapılandırıldıysa hava durumu tahmin verilerini görüyorsunuz.

   Yerel olarak çalıştığını doğruladıktan `OnGet` *sonra, Dizin.cshtml.cs'de* URL'yi, dizinde çalıştırma hazırlığında mywebapi'ye başvurarak Docker Compose. Hem Docker hem de kapsayıcı dışı çalıştırma ve hata ayıklama yapılandırmaları için aynı kodu kullanmak isterseniz URL'yi almak için bir yapılandırma dosyası kullanabilirsiniz.

1. Kapsayıcı düzenlemesi eklerken ilk proje, çalıştıracak veya hata ayıklayacak şekilde ayarlanır. Başlatma eylemlerini docker-compose **Project** Özellikler'de yapılandırabilirsiniz.  docker-compose proje düğümünde bağlam menüsünü açmak için sağ tıklayın ve özellikler'i **seçin veya** **Alt Enter'ı** + **kullanın.**  Aşağıdaki ekran görüntüsü, burada kullanılan çözüm için istediğiniz özellikleri gösterir.  Örneğin, Hizmet URL'si özelliğini özelleştirerek yüklenen **sayfayı değiştirebilirsiniz.**

   ![docker-compose proje özelliklerinin ekran görüntüsü.](media/tutorial-multicontainer/launch-action.png)

   Başlatıldıklarda şu ifadeleri görüyorsunuz:

   ![Web uygulamasını çalıştırma ekran görüntüsü.](media/tutorial-multicontainer/vs-2022/webfrontend.png)

   Web uygulaması, hava durumu verilerini JSON biçiminde gösterir.

1. Şimdi hata ayıklayıcının Web API projesine değil yalnızca WebFrontEnd'e bağlı olmasıyla ilgilendiğinizi varsayalım. Menü çubuğunda başlat düğmesinin yanındaki açılan menüyü kullanarak hata ayıklama seçenekleri menüsünü açabilirsiniz; **Başlat'ı Docker Compose'ı Ayarlar.**

   ![Hata Ayıklama Oluştur ve Oluştur menü Ayarlar ekran görüntüsü.](media/tutorial-multicontainer/vs-2022/debug-dropdown-manage-compose.png)

   Yönetim **Docker Compose Başlat Ayarlar** iletişim kutusu görüntülenir. Bu iletişim kutusuyla, hata ayıklayıcı ekli veya hata ayıklayıcısı ekli olmadan başlatılan bir hata ayıklama oturumu sırasında hangi hizmet alt kümesinin başlat olduğunu ve başlatma hizmetini ve URL'sini kontrol edin. Bkz. [Compose hizmetlerinin bir alt kümesini başlatma.](launch-profiles.md)

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
[Kapsayıcı Araçları](./index.yml)