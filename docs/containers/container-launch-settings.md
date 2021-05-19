---
title: Visual Studio Araçları başlatma ayarları
author: ghogen
description: Kapsayıcılı uygulamaları işlemeyle ilgili Kapsayıcı Araçları'nın başlatma Visual Studio hakkında bilgi edinin.
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: e50935145913bcd1f3c4457f4704376a0ac0f6ef
ms.sourcegitcommit: 162be102d2c22a1c4ad2c447685abd28e0e85d15
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2021
ms.locfileid: "109973245"
---
# <a name="container-tools-launch-settings"></a>Kapsayıcı Araçları başlatma ayarları

bir  ASP.NET Core projesinin Özellikler klasöründe, web launchSettings.jsgeliştirme makineniz üzerinde nasıl başlatılanı kontrol etmeyen ayarları içeren dosyada yer alan launchSettings.jsdosyasını bulabilirsiniz. Bu dosyanın geliştirme aşamasında nasıl ASP.NET için [bkz. ASP.NET Core'da birden çok ortam kullanma.](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2&preserve-view=true) Üzerinde *launchSettings.jsbölümünde,* **Docker** bölümündeki ayarlar kapsayıcılı uygulamaları Visual Studio ile ilgilidir.

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

commandName ayarı, bu bölümün Kapsayıcı Araçları için geçerli olduğunu tanımlar. Aşağıdaki tabloda bu bölümde ayarlanacak özellikler yer almaktadır:

::: moniker range="vs-2017"

|Ayar adı|Sürüm|Örnek|Description|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": true|Projeyi başarıyla başlattıktan sonra tarayıcının başlatıp başlatmay olmadığını gösterir.|
|launchUrl|Visual Studio 2017|"launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"|Bu URL, tarayıcı açılırken kullanılır.  Bu dize için desteklenen değiştirme belirteçleri:<br>   {Scheme} - SSL'nin kullanıp kullanılmadığına bağlı olarak "http" veya "https" ile değiştirilir.<br>   {ServiceHost} - Genellikle "localhost" ile değiştirilir. Ancak RS3 veya Windows 10 windows kapsayıcılarını hedeflerken, kapsayıcının IP'si ile değiştirilir.<br>   {ServicePort} - SSL'nin kullanıp kullanılmay durumuna bağlı olarak genellikle sslPort veya httpPort ile değiştirilir.  Ancak, Windows 10 RS3 veya daha eski bir modelde Windows kapsayıcılarını hedeflerken, SSL'nin kullanıp kullanılmay durumuna bağlı olarak "443" veya "80" ile değiştirilir.|

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
|                      |                                                       | - {ServiceHost} - Genellikle "localhost" ile değiştirilir.                                                                    |
|                      |                                                       | Ancak RS3 veya Windows 10 windows kapsayıcılarını hedeflerken, kapsayıcının IP'si ile değiştirilir.           |
|                      |                                                       | - {ServicePort} - SSL'nin kullanıp kullanılmay durumuna bağlı olarak genellikle sslPort veya httpPort ile değiştirilir.                   |
|                      |                                                       | Ancak RS3 veya daha Windows 10 Windows kapsayıcılarını hedeflerken , "443" veya "80" ile değiştirilir.         |
|                      |                                                       | SSL'nin kullanıp kullanılmay durumuna bağlı olarak.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Konakta bu bağlantı noktası, kapsayıcıyı başlatmadan önce kapsayıcının bağlantı noktası 443 ile eşlenmiş.                               |
|                      |                                                       | Belirtilmezse, değer iisSettings değerinden alınır.                                                          |
| useSSL               | "useSSL": true                                        | Projeyi başlatmada SSL kullanıp kullanmaycazını gösterir. useSSL belirtilmezse sslPort 0 olduğunda SSL > kullanılır. |

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Container Tools derleme özelliklerini [ayarerek projenizi yapılandırma.](container-msbuild-properties.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Docker Compose özellikleri oluşturma](docker-compose-properties.md)
- [Docker Compose için başlatma profillerini yönetme](launch-profiles.md)
