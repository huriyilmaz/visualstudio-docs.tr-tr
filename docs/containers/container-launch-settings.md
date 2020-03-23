---
title: Visual Studio Konteyner Araçları başlatma ayarları
author: ghogen
description: Konteyner Araçları oluşturma sürecine genel bakış
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 1c9786c29573da3b0149a9ec6578f2ce58c4de9f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76542600"
---
# <a name="container-tools-launch-settings"></a>Konteyner Araçları başlatma ayarları

ASP.NET Core projesindeki *Özellikler* klasöründe, geliştirme makinenizde web uygulamanızın nasıl başlatıldığını kontrol eden ayarlar içeren launchSettings.json dosyasını bulabilirsiniz. Bu dosyanın ASP.NET geliştirmede nasıl kullanıldığı hakkında ayrıntılı bilgi [ASP.NET](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2)için bkz. *launchSettings.json'da,* **Docker** bölümündeki ayarlar Visual Studio'nun kapsayıcı uygulamaları nasıl işlediğiyle ilgilidir.

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

CommandName ayarı, bu bölümün Kapsayıcı Araçlar için geçerli olduğunu tanımlar. Aşağıdaki tablo, bu bölümde ayarlanabilecek özellikleri gösterir:

::: moniker range="vs-2017"

|Ayar adı|Sürüm|Örnek|Açıklama|
|------------|-------|-------|---------------|
|launchBrowser|Visual Studio 2017|"launchBrowser": doğru|Projeyi başarıyla başlattıktan sonra tarayıcıyı başlatıp başlatmayacağını gösterir.|
|launchUrl|Visual Studio 2017|"launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"|Bu URL tarayıcıyı başlatırken kullanılır.  Bu dize için desteklenen yedek belirteçleri şunlardır:<br>   {Scheme} - SSL kullanılıp kullanılmadığına bağlı olarak "http" veya "https" ile değiştirilir.<br>   {ServiceHost} - Genellikle "localhost" ile değiştirilir. Windows 10 RS3 veya daha büyük Windows kapsayıcıları hedeflenirken, ancak, kapsayıcının IP ile değiştirilir.<br>   {ServicePort} - SSL kullanılıp kullanılmadığına bağlı olarak genellikle sslPort veya httpPort ile değiştirilir.  Windows 10 RS3 veya daha büyük Windows kapsayıcıları hedeflenirken, ssl kullanılıp kullanılmadığına bağlı olarak "443" veya "80" ile değiştirilir.|

::: moniker-end

::: moniker range=">=vs-2019"

| Ayar adı         | Örnek                                               | Açıklama                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| commandLineArgs      | "commandLineArgs": "--mysetting myvalue"              | Bu komut satırı bağımsız değişkenleri, projenizi kapsayıcıda başlatırken kullanılır.                                     |
| çevreDeğişkenler | "çevreDeğişkenler": {                             | Bu ortam değişken değerleri, kapsayıcıda başlatıldığında işleme aktarılır.                       |
|                      | "ASPNETCORE_URLS":https://+:443" ; http://+:80",       |                                                                                                                         |
|                      | "ASPNETCORE_HTTPS_PORT": "44381"                      |                                                                                                                         |
|                      | }                                                     |                                                                                                                         |
| httpPort             | "https://www." 24051                                     | Ana bilgisayardaki bu bağlantı noktası, kapsayıcıyı başlatırken konteynerin bağlantı noktası 80'e eşlenir.                                |
|                      |                                                       | Belirtilmemişse, değer iisAyarlar değerinden alınır.                                                          |
| launchBrowser        | "launchBrowser": doğru                                 | Projeyi başarıyla başlattıktan sonra tarayıcıyı başlatıp başlatmayacağını gösterir.                                       |
| launchUrl            | "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}" | Bu URL tarayıcıyı başlatırken kullanılır. Bu dize için desteklenen yedek belirteçleri şunlardır:                          |
|                      |                                                       | - {Scheme} - SSL kullanılıp kullanılmadığına bağlı olarak "http" veya "https" ile değiştirilir.                                   |
|                      |                                                       | - {ServiceHost} - Genellikle "localhost" ile değiştirilir.                                                                    |
|                      |                                                       | Windows 10 RS3 veya daha büyük Windows kapsayıcıları hedeflenirken, ancak, kapsayıcının IP ile değiştirilir.           |
|                      |                                                       | - {ServicePort} - SSL kullanılıp kullanılmadığına bağlı olarak genellikle sslPort veya httpPort ile değiştirilir.                   |
|                      |                                                       | Windows 10 RS3 veya daha büyük windows kapsayıcıları hedeflenirken, "443" veya "80" ile değiştirilir,         |
|                      |                                                       | SSL kullanılıp kullanılmadığına bağlı olarak değişir.                                                                                       |
| sslPort              | "sslPort": 44381                                      | Ana bilgisayardaki bu bağlantı noktası, kapsayıcıyı başlatırken konteynerin 443 portuna eşlenir.                               |
|                      |                                                       | Belirtilmemişse, değer iisAyarlar değerinden alınır.                                                          |
| useSSL               | "useSSL": doğru                                        | Projeyi başlatırken SSL'nin kullanılıp kullanılmayacağını gösterir. UseSSL belirtilmemişse, sslPort > 0 olduğunda SSL kullanılır. |

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

[Kapsayıcı Araçları yapı özelliklerini](container-msbuild-properties.md)ayarlayarak projenizi yapılandırın.

## <a name="see-also"></a>Ayrıca bkz.

[Docker Oluşturma yapı özellikleri](docker-compose-properties.md)
