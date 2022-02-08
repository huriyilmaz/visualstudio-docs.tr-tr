---
title: 'Mac için VS: Docker Compose ile çok Kapsayıcılı uygulama'
description: birden fazla kapsayıcıyı yönetmeyi ve Mac için Visual Studio aralarında iletişim kurmayı öğrenin
ms.custom: SEO-VS-2020
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.date: 07/03/2020
ms.topic: how-to
ms.openlocfilehash: b3e00a9091c436877dcd4cf4adb7ed1e4dba3e12
ms.sourcegitcommit: 782992423db6e1cbbf206715c9b3b400c80052a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2022
ms.locfileid: "138101040"
---
# <a name="create-a-multi-container-app-with-docker-compose-for-visual-studio-for-mac"></a>Mac için Visual Studio için Docker Compose birden çok kapsayıcılı uygulama oluşturma

bu öğreticide, birden fazla kapsayıcıyı yönetmeyi ve Mac için Visual Studio Docker Compose kullanırken aralarında iletişim kurmayı öğreneceksiniz.

Visual Studio Windows sürümünde adımlar aranıyor [: Windows için Visual Studio ile Docker Compose ile çok kapsayıcılı bir uygulama oluşturma](/visualstudio/containers/tutorial-multicontainer).

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Mac için Visual Studio 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>ASP.NET Core Web uygulaması oluşturma ve docker desteği ekleme

1. **Yeni çözüm > dosyaya** giderek yeni bir çözüm oluşturun.
1. **web ve konsol > uygulama** altında **web uygulaması** şablonunu seçin: ![ yeni bir ASP.NET uygulaması oluşturun](media/docker-quickstart-1.png)
1. Hedef çerçeveyi seçin. Bu örnekte, .NET Core 3,1: ![ Target Framework 'ü ayarla ' yı kullanacağız](media/docker-quickstart-2.png)
1. Project adı (bu örnekte _DockerDemoFrontEnd_ ) ve çözüm adı (_dockerdemo_) gibi proje ayrıntılarını girin. oluşturulan proje, bir ASP.NET Core web sitesi derlemek ve çalıştırmak için ihtiyacınız olan tüm temel bilgileri içerir.
1. Çözüm penceresinde, DockerDemoFrontEnd projesine sağ tıklayın ve **ekle > Docker desteği** Ekle ' yi seçin: ![ Docker desteği ekle](media/docker-quickstart-3.png)

Mac için Visual Studio, çözümünüze **docker-compose** adlı otomatik olarak yeni bir proje ekleyecek ve mevcut projenize bir **dockerfile** ekleyecek.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>ASP.NET Core Web apı 'si oluşturun ve docker desteği ekleyin

Ardından, arka uç API 'SI olarak görev yapacak ikinci bir proje oluşturacağız. **.NET Core API** şablonu, yeniden gelen istekleri işleyebileceğimizi sağlayan bir denetleyici içerir.

1. Çözüme sağ tıklayıp **ekle > yeni Project Ekle**' yi seçerek mevcut çözüme yeni bir proje ekleyin.
1. **Web ve konsol > uygulama** altında **API** şablonunu seçin.
1. Hedef çerçeveyi seçin. Bu örnekte, .NET Core 3,1 kullanacağız.
1. Project adı (bu örnekte _mywebapi_ ) gibi proje ayrıntılarını girin.
1. Oluşturulduktan sonra çözüm penceresine gidin ve MyWebAPI projesine sağ tıklayın ve **ekle > Docker desteği ekle**' yi seçin.

**Docker-Compose** projesindeki **Docker-Compose. yıml** dosyası, mevcut Web UYGULAMASı projesinin yanı sıra API projesini dahil edecek şekilde otomatik olarak güncelleştirilir. **Docker-Compose** projesi oluşturup çalıştırdığımızda, bu projelerin her biri ayrı bir Docker kapsayıcısına dağıtılır.

```yaml
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  mywebapi:
    image: ${DOCKER_REGISTRY-}mywebapi
    build:
      context: .
      dockerfile: MyWebAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Iki kapsayıcıyı tümleştirin

artık çözümümüzde iki ASP.NET projesi var ve her ikisi de docker desteğiyle yapılandırıldı. Sonraki bir kod eklememiz gerekiyor!

1. `DockerDemoFrontEnd`Projesinde, *Pages/Index. cshtml. cs* dosyasını açın ve yöntemi aşağıdaki kodla değiştirin `OnGet` :

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://mywebapi/WeatherForecast");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```
   
    > [!NOTE]
    > Üretim kodunda, her istekten sonra atılamaz `HttpClient` . En iyi uygulamalar için bkz. [Esnek http isteklerini uygulamak Için HttpClientFactory kullanma](/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

1. *Index. cshtml* dosyasında, dosyanın aşağıdaki koda benzeymek üzere görüntülenecek `ViewData["Message"]` bir satır ekleyin:

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
  
1. Hem ön uç hem de Web API projelerinde, bu örnek kod, Web API 'sini çağırmak için HTTPS değil HTTP 'yi kullandığından, *Başlangıç. cs* Içindeki yönteminde [Microsoft. Aspnetcore. Builder. HttpsPolicyBuilderExtensions. usehttpsredirection](/dotnet/api/microsoft.aspnetcore.builder.httpspolicybuilderextensions.usehttpsredirection) `Configure` çağrısını not edin.

      ```csharp
                  //app.UseHttpsRedirection();
      ```

1. `docker-compose`Projeyi başlangıç projesi olarak ayarlayın ve **hata ayıklamayı başlatmak > Çalıştır**' a gidin. Her şey doğru yapılandırılmışsa, "Web ön ucu ve WebApi 'den Merhaba (değer 1 ile)" iletisini görürsünüz.

![Docker Multi Container Solution çalışıyor](media/docker-multicontainer-debug.png)
