---
title: Visual Studio Kapsayıcı araçları başlatma ayarları
author: ghogen
description: Visual Studio kapsayıcılı uygulamaları nasıl işleyeceğinden ilişkili kapsayıcı araçları için başlatma ayarları hakkında bilgi edinin.
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-container-tools
ms.topic: reference
ms.openlocfilehash: d05d4a42a6e2433cc9dfc5190a9e380dda49dab0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631767"
---
# <a name="container-tools-launch-settings"></a>Kapsayıcı araçları başlatma ayarları

ASP.NET Core projesindeki *özellikler* klasöründe, web uygulamanızın geliştirme makinenizde nasıl başlatıldığını denetleyen ayarları içeren launchsettings. json dosyasını bulabilirsiniz. bu dosyanın ASP.NET geliştirmede nasıl kullanıldığı hakkında ayrıntılı bilgi için bkz. [ASP.NET Core birden çok ortam kullanma](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2&preserve-view=true). *launchsettings. json* dosyasında **docker** bölümündeki ayarlar kapsayıcılı uygulamaları nasıl işleyeceğinden Visual Studio ilgilidir.

::: moniker range="vs-2017"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"
    }
```

::: moniker-end
::: moniker range=">=vs-2019"

```json
    "Docker": {
      "commandName": "Docker",
      "launchBrowser": true,
      "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}",
      "environmentVariables": {
        "ASPNETCORE_URLS": "https://+:443;http://+:80",
        "ASPNETCORE_HTTPS_PORT": "44360"
      },
      "httpPort": 51803,
      "useSSL": true,
      "sslPort": 44360
    }
```

::: moniker-end

CommandName ayarı, bu bölümün kapsayıcı araçları için geçerli olduğunu tanımlar. Aşağıdaki tabloda, bu bölümde ayarlankullanılabilecek özellikler gösterilmektedir:

::: moniker range="vs-2017"

|Ayar adı|Sürüm|Örnek|Description|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": true|Projeyi başarıyla başlattıktan sonra tarayıcının başlatılıp başlatılmayacağını belirtir.|
|launchUrl 'Si|Visual Studio 2017|"launchUrl": "{Scheme}:/\ {ServiceHost}: {ServicePort}"|Bu URL tarayıcı başlatılırken kullanılır.  Bu dize için desteklenen değiştirme belirteçleri şunlardır:<br>   {Scheme}-SSL 'nin kullanılıp kullanılmadığından bağımsız olarak, "http" veya "https" ile değiştirilmiştir.<br>   {ServiceHost}-genellikle "localhost" ile değiştirilmiştir. Windows 10 RS3 veya daha eski bir sürüm Windows kapsayıcılar hedeflenirken, kapsayıcının ıp 'si ile değiştirilmiştir.<br>   {ServicePort}-genellikle, SSL 'nin kullanılıp kullanılmadığını bağlı olarak sslPort veya httpPort ile değiştirilmiştir.  Windows 10 RS3 veya daha eski bir sürüm Windows kapsayıcılar hedeflenirken, SSL 'nin kullanılıp kullanıldığına bağlı olarak, "443" veya "80" ile değiştirilmiştir.|

::: moniker-end

::: moniker range=">=vs-2019"

| Ayar adı         | Örnek                                               | Description                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| commandLineArgs      | "Commanddoğrgs": "--myValue" ayarı              | Uygulamanızı başlatmak için bu komut satırı bağımsız değişkenleri, projenizde projeniz başlatılırken kullanılır.                                     |
| environmentVariables | "environmentVariables": {                             | Bu ortam değişkeni değerleri, kapsayıcıda başlatıldığında işleme geçirilir.                       |
|                      | "ASPNETCORE_URLS": " https://+:443 ; http://+:80 ",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "httpPort": 24051                                     | Bu bağlantı noktası, kapsayıcıyı başlatırken kapsayıcının bağlantı noktası 80 ' e eşlenir.                                |
|                      |                                                       | Belirtilmemişse, değer iisSettings değerinden alınır.                                                          |
| launchBrowser        | "launchBrowser": true                                 | Projeyi başarıyla başlattıktan sonra tarayıcının başlatılıp başlatılmayacağını belirtir.                                       |
| launchUrl 'Si            | "launchUrl": "{Scheme}:/\ {ServiceHost}: {ServicePort}" | Bu URL tarayıcı başlatılırken kullanılır. Bu dize için desteklenen değiştirme belirteçleri şunlardır:                          |
|                      |                                                       | -{Scheme}-SSL 'nin kullanılıp kullanılmadığından bağımsız olarak "http" veya "https" ile değiştirilmiştir.                                   |
|                      |                                                       | -{ServiceHost}-genellikle "localhost" ile değiştirilmiştir.                                                                    |
|                      |                                                       | Windows 10 RS3 veya daha eski bir sürüm Windows kapsayıcılar hedeflenirken, kapsayıcının ıp 'si ile değiştirilmiştir.           |
|                      |                                                       | -{ServicePort}-genellikle, SSL 'nin kullanılıp kullanılmadığını bağlı olarak sslPort veya httpPort ile değiştirilmiştir.                   |
|                      |                                                       | Windows 10 RS3 veya daha eski bir sürüm Windows kapsayıcılar hedeflenirken, "443" veya "80" ile değiştirilmiştir         |
|                      |                                                       | SSL 'nin kullanılıp kullanılmadığını bağlı olarak.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Bu bağlantı noktası, kapsayıcıyı başlatırken kapsayıcının bağlantı noktası 443 ' e eşlenir.                               |
|                      |                                                       | Belirtilmemişse, değer iisSettings değerinden alınır.                                                          |
| useSSL               | "useSSL": true                                        | Projeyi başlatırken SSL kullanılıp kullanılmayacağını gösterir. UseSSL belirtilmemişse, sslPort 0 > için SSL kullanılır. |

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

[Kapsayıcı araçları derleme özelliklerini](container-msbuild-properties.md)ayarlayarak projenizi yapılandırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Docker Compose derleme özellikleri](docker-compose-properties.md)
- [Docker Compose için başlatma profillerini yönetme](launch-profiles.md)
