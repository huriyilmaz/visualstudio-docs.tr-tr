---
title: Docker Compose ile çok Kapsayıcılı uygulama
description: Birden fazla kapsayıcıyı yönetmeyi ve Mac için Visual Studio aralarında iletişim kurmayı öğrenin
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.topic: tutorial
ms.openlocfilehash: 4dd8695ccf8f1fcf13b9b52387d28c68f8812aec
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800729"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Docker Compose ile Çok Kapsayıcılı Uygulama Oluşturma

Bu öğreticide, birden fazla kapsayıcıyı yönetmeyi ve Mac için Visual Studio Docker Compose kullanırken aralarında iletişim kurmayı öğreneceksiniz.

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Mac için Visual Studio 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>ASP.NET Core Web uygulaması oluşturma ve Docker desteği ekleme

1. **Yeni çözüm > dosyaya**giderek yeni bir çözüm oluşturun.
1. **Web ve konsol > uygulama** altında **Web uygulaması** şablonunu seçin: ![ Yeni bir ASP.NET uygulaması oluşturma](media/docker-quickstart-1.png)
1. Hedef çerçeveyi seçin. Bu örnekte, .NET Core 3,1: ![ Target Framework 'ü ayarla ' yı kullanacağız](media/docker-quickstart-2.png)
1. Proje adı (Bu örnekte_DockerDemoFrontEnd_ ) ve çözüm adı (_dockerdemo_) gibi proje ayrıntılarını girin. Oluşturulan proje, bir ASP.NET Core Web sitesi derlemek ve çalıştırmak için ihtiyacınız olan tüm temel bilgileri içerir.
1. Çözüm Bölmesi, DockerDemoFrontEnd projesine sağ tıklayın ve **ekle > Docker desteği ekle**' yi seçin: ![ Docker desteği ekle](media/docker-quickstart-3.png)

Mac için Visual Studio, çözümünüze **Docker-Compose** adlı otomatik olarak yeni bir proje ekleyecek ve mevcut projenize bir **dockerfile** ekleyecek.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>ASP.NET Core Web API 'SI oluşturun ve Docker desteği ekleyin

Ardından, arka uç API 'SI olarak görev yapacak ikinci bir proje oluşturacağız. **.NET Core API** şablonu, yeniden gelen istekleri işleyebileceğimizi sağlayan bir denetleyici içerir.

1. Çözüme sağ tıklayıp **Yeni proje ekle > Ekle**' yi seçerek mevcut çözüme yeni bir proje ekleyin.
1. **Web ve konsol > uygulama** altında **API** şablonunu seçin.
1. Hedef çerçeveyi seçin. Bu örnekte, .NET Core 3,1 kullanacağız.
1. Proje adı (Bu örnekteki_Mywebapi_ ) gibi proje ayrıntılarını girin.
1. Oluşturulduktan sonra, Çözüm Bölmesi gidin ve MyWebAPI projesine sağ tıklayın ve **ekle > Docker desteği ekle**' yi seçin.

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

Artık çözümünüzde iki ASP.NET projesi var ve her ikisi de Docker desteğiyle yapılandırılmış. Sonraki bir kod eklememiz gerekiyor!

1. `DockerDemoFrontEnd`Projesinde, *Pages/Index. cshtml. cs* dosyasını açın ve `OnGet` yöntemi aşağıdaki kodla değiştirin:

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
    > Üretim kodunda, `HttpClient` her istekten sonra atılamaz. En iyi uygulamalar için bkz. [Esnek http isteklerini uygulamak Için HttpClientFactory kullanma](https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests).

1. *Index. cshtml* dosyasında, `ViewData["Message"]` dosyanın aşağıdaki koda benzeymek üzere görüntülenecek bir satır ekleyin:

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
  
1. Hem ön uç hem de Web API projelerinde, bu örnek kod Web API 'sini çağırmak için HTTPS değil HTTP 'yi kullandığından, Startup.cs içindeki yönteminde [Microsoft. AspNetCore. Builder. HttpsPolicyBuilderExtensions. UseHttpsRedirection](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.builder.httpspolicybuilderextensions.usehttpsredirection) çağrısını not edin. `Configure` *Startup.cs*

      ```csharp
                  //app.UseHttpsRedirection();
      ```

1. `docker-compose`Projeyi başlangıç projesi olarak ayarlayın ve **hata ayıklamayı başlatmak > Çalıştır**' a gidin. Her şey doğru yapılandırılmışsa, "Web ön ucu ve WebApi 'den Merhaba (değer 1 ile)" iletisini görürsünüz.

![Docker Multi Container Solution çalışıyor](media/docker-multicontainer-debug.png)
