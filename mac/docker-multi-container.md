---
title: Öğretici-Docker Compose ile çok kapsayıcılı bir uygulama oluşturma
description: Birden fazla kapsayıcıyı yönetmeyi ve Mac için Visual Studio aralarında iletişim kurmayı öğrenin
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 487945399252ca3627d625e3572637b5b2af2916
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983967"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Docker Compose ile çok kapsayıcılı bir uygulama oluşturma

Bu öğreticide, birden fazla kapsayıcıyı yönetmeyi ve Mac için Visual Studio Docker Compose kullanırken aralarında iletişim kurmayı öğreneceksiniz.

## <a name="prerequisites"></a>Prerequisites

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Mac için Visual Studio 2019](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>ASP.NET Core Web uygulaması oluşturma ve Docker desteği ekleme

1. **Yeni çözüm > dosyaya**giderek yeni bir çözüm oluşturun.
1. **.NET Core > uygulama** altında **Web uygulaması** şablonunu seçin: ![yeni bir ASP.NET uygulaması oluşturun](media/docker-quickstart-1.png)
1. Hedef çerçeveyi seçin. Bu örnekte, .NET Core 2,2: ![Target Framework 'ü kullanacak şekilde kullanacağız](media/docker-quickstart-2.png)
1. Proje adı (Bu örnekte_DockerDemoFrontEnd_ ) ve çözüm adı (_dockerdemo_) gibi proje ayrıntılarını girin. Oluşturulan proje, bir ASP.NET Core Web sitesi derlemek ve çalıştırmak için ihtiyacınız olan tüm temel bilgileri içerir.
1. Çözüm Bölmesi, DockerDemoFrontEnd projesine sağ tıklayın ve **ekle > Docker desteği**Ekle ' yi seçin: ![Docker desteği ekleyin](media/docker-quickstart-3.png)

Mac için Visual Studio, çözümünüze **Docker-Compose** adlı otomatik olarak yeni bir proje ekleyecek ve mevcut projenize bir **dockerfile** ekleyecek.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>ASP.NET Core Web API 'SI oluşturun ve Docker desteği ekleyin

Ardından, arka uç API 'SI olarak görev yapacak ikinci bir proje oluşturacağız. **.NET Core API** şablonu, yeniden gelen istekleri işleyebileceğimizi sağlayan bir denetleyici içerir.

1. Çözüme sağ tıklayıp **Yeni proje ekle > Ekle**' yi seçerek mevcut çözüme yeni bir proje ekleyin.
1. **.NET Core > uygulama** altında **API** şablonunu seçin.
1. Hedef çerçeveyi seçin. Bu örnekte, .NET Core 2,2 kullanacağız
1. Proje adı (Bu örnekteki_Dockerdemoapı_ ) gibi proje ayrıntılarını girin.
1. Oluşturulduktan sonra Çözüm Bölmesi gidin ve Dockerdemoapı projesine sağ tıklayın ve **ekle > Docker desteği ekle**' yi seçin.

**Docker-Compose** projesindeki **Docker-Compose. yıml** dosyası, mevcut Web UYGULAMASı projesinin yanı sıra API projesini dahil edecek şekilde otomatik olarak güncelleştirilir. **Docker-Compose** projesi oluşturup çalıştırdığımızda, bu projelerin her biri ayrı bir Docker kapsayıcısına dağıtılır.

```
version: '3.4'

services:
  dockerdemofrontend:
    image: ${DOCKER_REGISTRY-}dockerdemofrontend
    build:
      context: .
      dockerfile: DockerDemoFrontEnd/Dockerfile

  dockerdemoapi:
    image: ${DOCKER_REGISTRY-}dockerdemoapi
    build:
      context: .
      dockerfile: DockerDemoAPI/Dockerfile
```

## <a name="integrate-the-two-containers"></a>Iki kapsayıcıyı tümleştirin

Artık çözümünüzde iki ASP.NET projesi var ve her ikisi de Docker desteğiyle yapılandırılmış. Sonraki bir kod eklememiz gerekiyor!

1. `DockerDemoFrontEnd` projesinde, *Index.cshtml.cs* dosyasını açın ve `OnGet` yöntemini aşağıdaki kodla değiştirin:

   ```csharp
    public async Task OnGet()
    {
       ViewData["Message"] = "Hello from webfrontend";

       using (var client = new System.Net.Http.HttpClient())
       {
          // Call *mywebapi*, and display its response in the page
          var request = new System.Net.Http.HttpRequestMessage();
          request.RequestUri = new Uri("http://dockerdemoapi/api/values/1");
          var response = await client.SendAsync(request);
          ViewData["Message"] += " and " + await response.Content.ReadAsStringAsync();
       }
    }
   ```

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

1. Şimdi Web API projesinde, *webön*ucunda eklediğiniz çağrı için API tarafından döndürülen iletiyi özelleştirmek üzere değerler denetleyicisine kod ekleyin:

      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. `docker-compose` projesini başlangıç projesi olarak ayarlayın ve **hata ayıklamayı başlatmak > Çalıştır**' a gidin. Her şey doğru yapılandırılmışsa, "Web ön ucu ve WebApi 'den Merhaba (değer 1 ile)" iletisini görürsünüz.

![Docker Multi Container Solution çalışıyor](media/docker-multicontainer-debug.png)
