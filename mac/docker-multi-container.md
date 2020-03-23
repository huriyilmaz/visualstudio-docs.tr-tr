---
title: Öğretici - Docker Oluştur ile Çoklu Konteyner Uygulaması Oluşturun
description: Birden fazla konteynırı nasıl yöneteceklerini ve Mac için Visual Studio'da aralarında nasıl iletişim kurarak iletişim kurarak iletişim kurarak iletişim kurabilirsiniz
author: heiligerdankgesang
ms.author: dominicn
ms.date: 06/17/2019
ms.openlocfilehash: 487945399252ca3627d625e3572637b5b2af2916
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983967"
---
# <a name="create-a-multi-container-app-with-docker-compose"></a>Docker Compose ile Çok Kapsayıcılı Uygulama Oluşturma

Bu eğitimde, Mac için Visual Studio'da Docker Compose'u kullanırken birden fazla konteynırı nasıl yöneteceğinizi ve aralarında iletişim kurmayı öğreneceksiniz.

## <a name="prerequisites"></a>Önkoşullar

* [Docker Masaüstü](https://hub.docker.com/editions/community/docker-ce-desktop-mac)
* [Mac 2019 için Visual Studio](https://visualstudio.microsoft.com/vs/mac)

## <a name="create-an-aspnet-core-web-application-and-add-docker-support"></a>ASP.NET Çekirdek Web Uygulaması Oluşturun ve Docker Desteği Ekleyin

1. **Yeni > Çözüm Dosya'ya**giderek yeni bir çözüm oluşturun.
1. **.NET Core > Uygulaması** altında Web ![ **Uygulaması** şablonu seçin: Yeni bir ASP.NET uygulama oluşturma](media/docker-quickstart-1.png)
1. Hedef çerçeveyi seçin. Bu örnekte .NET Core 2.2: ![Hedef çerçeve yi ayarlama](media/docker-quickstart-2.png)
1. Proje Adı (Bu örnekte_DockerDemoFrontEnd)_ ve Çözüm Adı _(DockerDemo)_ gibi proje ayrıntılarını girin. Oluşturulan proje, bir ASP.NET Core web sitesi oluşturmak ve çalıştırmak için ihtiyacınız olan tüm temel bilgileri içerir.
1. Çözüm Defteri'nde DockerDemoFrontEnd projesine sağ tıklayın ve Ekle ![> Docker Desteği **Ekle'yi**seçin : Docker desteği ekle](media/docker-quickstart-3.png)

Mac için Visual Studio, **docker-compose** adlı çözümünüze otomatik olarak yeni bir proje ekler ve mevcut projenize bir **Dockerfile** ekler.

## <a name="create-an-aspnet-core-web-api-and-add-docker-support"></a>ASP.NET Core Web API oluşturma ve Docker Desteği Ekle

Daha sonra arka uç API olarak hareket edecek ikinci bir proje oluşturacaktır. **.NET Core API** şablonu, yeniden yapılan istekleri işlememizi sağlayan bir denetleyici içerir.

1. Çözüme sağ tıklayarak ve **Yeni Proje Ekle >'yi**seçerek varolan çözüme yeni bir proje ekleyin.
1. **.NET Core > Uygulaması** altında **API** şablonu seçin.
1. Hedef çerçeveyi seçin. Bu örnekte .NET Core 2.2
1. Proje Adı _(DockerDemoAPI_ bu örnekte) gibi proje ayrıntılarını girin.
1. Oluşturulduktan sonra Solution Pad'e gidin ve DockerDemoAPI projesine sağ tıklayın ve **Docker Desteği ekle >'i**seçin.

**Docker-compose** projesindeki **docker-compose.yml** dosyası, mevcut Web App projesinin yanı sıra API projesini de içerecek şekilde otomatik olarak güncellenir. **Docker-compose** projesini oluşturup çalıştırdığımızda, bu projelerin her biri ayrı bir Docker konteynerine dağıtılacaktır.

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

## <a name="integrate-the-two-containers"></a>İki Kapsayıcıyı Entegre Edin

Şu anda çözümümüzde iki ASP.NET projemiz var ve her ikisi de Docker desteği ile yapılandırıldı. Sonra bazı kod eklemek gerekir!

1. Projede, `DockerDemoFrontEnd` *Index.cshtml.cs* dosyasını açın ve `OnGet` yöntemi aşağıdaki kodla değiştirin:

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

1. *Index.cshtml* dosyasında, dosyanın aşağıdaki `ViewData["Message"]` koda benzemesi için görüntülemek için bir satır ekleyin:

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

1. Şimdi Web API projesinde, *webfrontend'den*eklediğiniz arama için API tarafından döndürülen iletiyi özelleştirmek için Değerler denetleyicisine kod ekleyin:

      ```csharp
        // GET api/values/5
        [HttpGet("{id}")]
        public ActionResult<string> Get(int id)
        {
            return "webapi (with value " + id + ")";
        }
      ```

1. Projeyi `docker-compose` başlangıç projesi olarak ayarlayın ve **Hata Ayıklama başlat'> çalıştır'a**gidin. Her şey doğru yapılandırılmışsa, "Webfrontend ve webapi'den merhaba (değer 1 ile)." iletisini görürsünüz:

![Docker çoklu konteyner çözümü çalışıyor](media/docker-multicontainer-debug.png)
