---
title: Visual Studio Kapsayıcı Araçları başlatma ayarları
author: ghogen
description: Kapsayıcılı uygulamaları işlemeyle ilgili Kapsayıcı Araçları'nın başlatma Visual Studio hakkında bilgi edinin.
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-container-tools
ms.topic: reference
ms.openlocfilehash: 1664eef6fcc8e92f5ce0f27574952222aa85597871cacc941573d72373daa485
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121436688"
---
# <a name="container-tools-launch-settings"></a>Kapsayıcı Araçları başlatma ayarları

Bir  ASP.NET Core projesinin Özellikler klasöründe, web launchSettings.jsgeliştirme makineniz üzerinde nasıl başlatılana kadar olan ayarları içeren dosyada yer alan launchSettings.jsdosyasını bulabilirsiniz. Bu dosyanın geliştirme aşamasında nasıl kullandığı hakkında ayrıntılı bilgi ASP.NET [bkz.](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2&preserve-view=true)ASP.NET Core. Üzerinde *launchSettings.jsbölümünde,* **Docker** bölümündeki ayarlar kapsayıcılı uygulamaları Visual Studio ile ilgilidir.

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

|Ayar adı|Sürüm|Örnek|Açıklama|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": true|Projeyi başarıyla başlattıktan sonra tarayıcının başlatıp başlatmay olmadığını gösterir.|
|launchUrl|Visual Studio 2017|"launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"|Bu URL, tarayıcı açılırken kullanılır.  Bu dize için desteklenen değiştirme belirteçleri:<br>   {Scheme} - SSL'nin kullanıp kullanılmadığına bağlı olarak "http" veya "https" ile değiştirilir.<br>   {ServiceHost} - Genellikle "localhost" ile değiştirilir. Rs3 veya Windows üzerinde Windows 10 hedeflese de, kapsayıcının IP'si ile değiştirilir.<br>   {ServicePort} - SSL'nin kullanıp kullanılmay durumuna bağlı olarak genellikle sslPort veya httpPort ile değiştirilir.  Ancak, Windows RS3 veya daha eski bir Windows 10 kapsayıcılarını hedeflerken, SSL'nin kullanıp kullanılmay durumuna bağlı olarak "443" veya "80" ile değiştirilir.|

::: moniker-end

::: moniker range=">=vs-2019"

| Ayar adı         | Örnek                                               | Açıklama                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| commandLineArgs      | "commandLineArgs": "--mysetting myvalue"              | Kapsayıcıda projenizi başlatmak için bu komut satırı bağımsız değişkenleri kullanılır.                                     |
| environmentVariables | "environmentVariables": {                             | Bu ortam değişkeni değerleri, kapsayıcıda başlatıldıklarında işleme geçiri.                       |
|                      | "ASPNETCORE_URLS": " https://+:443 ; http://+:80 ",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "httpPort": 24051                                     | Konakta bu bağlantı noktası, kapsayıcıyı başlatmadan önce kapsayıcının 80 bağlantı noktasıyla eşlenmiş.                                |
|                      |                                                       | Belirtilmezse, değer iisSettings değerinden alınır.                                                          |
| launchBrowser        | "launchBrowser": true                                 | Projeyi başarıyla başlattıktan sonra tarayıcının başlatıp başlatmay olmadığını gösterir.                                       |
| launchUrl            | "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}" | Bu URL, tarayıcı açılırken kullanılır. Bu dize için desteklenen değiştirme belirteçleri:                          |
|                      |                                                       | - {Scheme} - SSL'nin kullanıp kullanılmadığına bağlı olarak "http" veya "https" ile değiştirilir.                                   |
|                      |                                                       | - {ServiceHost} - Genellikle "localhost" ile değiştirilir.                                                                    |
|                      |                                                       | Rs3 veya Windows üzerinde Windows 10 hedeflese de, kapsayıcının IP'si ile değiştirilir.           |
|                      |                                                       | - {ServicePort} - SSL'nin kullanıp kullanılmay durumuna bağlı olarak genellikle sslPort veya httpPort ile değiştirilir.                   |
|                      |                                                       | Ancak, Windows RS3 veya Windows 10 üzerinde kapsayıcıları hedeflerken , "443" veya "80" ile değiştirilir,         |
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
