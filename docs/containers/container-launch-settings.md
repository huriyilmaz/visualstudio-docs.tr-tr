---
title: Visual Studio Kapsayıcı Araçları başlatma ayarları
author: ghogen
description: Kapsayıcılı uygulamaları nasıl işleyebilirsiniz? ile ilgili kapsayıcı araçları Visual Studio başlatma ayarları hakkında bilgi edinin.
ms.author: ghogen
ms.date: 08/15/2019
ms.technology: vs-container-tools
ms.topic: reference
---
# <a name="container-tools-launch-settings"></a>Kapsayıcı Araçları başlatma ayarları

ASP.NET Core projesinin Özellikler klasöründe, web uygulamanın geliştirme makineniz üzerinde nasıl başlat olduğunu kontrol altına alan ayarları içeren launchSettings.json dosyasını bulabilirsiniz. Bu dosyanın geliştirme aşamasında nasıl ASP.NET hakkında ayrıntılı bilgi için bkz. Birden çok [ortamda ASP.NET Core](/aspnet/core/fundamentals/environments?view=aspnetcore-2.2&preserve-view=true). *launchSettings.json'da* **Docker** bölümündeki ayarlar, kapsayıcılı uygulamaların Visual Studio ilgilidir.

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
      "DockerfileRunArguments": "-v $(pwd)/host-folder:/container-folder:ro",
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
|launchUrl|Visual Studio 2017|"launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}"|Bu URL, tarayıcı açılırken kullanılır.  Bu dize için desteklenen değiştirme belirteçleri:<br/><br/>   - {Scheme} - SSL'nin kullanıp kullanılmadığına bağlı olarak "http" veya "https" ile değiştirilir.<br/><br/>   - {ServiceHost} - Genellikle "localhost" ile değiştirilir. Rs3 veya Windows üzerinde Windows 10 hedeflese de, kapsayıcının IP'si ile değiştirilir.<br/><br/>   {ServicePort} - SSL'nin kullanıp kullanılmay durumuna bağlı olarak genellikle sslPort veya httpPort ile değiştirilir.  Ancak, Windows RS3 veya daha eski bir Windows 10 kapsayıcılarını hedeflerken, SSL'nin kullanıp kullanılmay durumuna bağlı olarak "443" veya "80" ile değiştirilir.|

::: moniker-end

::: moniker range=">=vs-2019"

| Ayar adı         | Örnek                                               | Description                                                                                                             |
| -------------------- | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| commandLineArgs      | "commandLineArgs": "--mysetting myvalue"              | Kapsayıcıda projenizi başlatmak için bu komut satırı bağımsız değişkenleri kullanılır.                                     |
|DockerfileRunArguments|"dockerfileRunArguments": "-v $(pwd)/host-folder:/container-folder:ro"|[Docker run komutuna geçilen ek bağımsız değişkenler](https://docs.docker.com/engine/reference/commandline/run/).|
| environmentVariables | "environmentVariables": {<br/>   "ASPNETCORE_URLS": "https://+:443;http://+:80", <br/>   "ASPNETCORE_HTTPS_PORT": "44381" <br/> }                    | Bu ortam değişkeni değerleri, kapsayıcıda başlatıldıklarında işleme geçiri.                       |
| httpPort             | "httpPort": 24051                                     | Konakta bu bağlantı noktası, kapsayıcıyı başlatmadan önce kapsayıcının 80 bağlantı noktasıyla eşlenmiş. |
| launchBrowser        | "launchBrowser": true                                 | Projeyi başarıyla başlattıktan sonra tarayıcının başlatıp başlatmay olmadığını gösterir.                                       |
| launchBrowserTimeout | "launchBrowserTimeout": 1                             | Tarayıcıyı başlatmadan önce uygulamanın hazır hale gelmeden önce beklemesi gereken en uzun süre (saniye olarak). |
| launchUrl            | "launchUrl": "{Scheme}://{ServiceHost}:{ServicePort}" | Bu URL, tarayıcı açılırken kullanılır. Bu dize için desteklenen değiştirme belirteçleri: <br/><br/> - {Scheme} - SSL'nin kullanıp kullanılmadığına bağlı olarak "http" veya "https" ile değiştirilir. <br/><br/> - {ServiceHost} - Genellikle "localhost" ile değiştirilir. <br/> Rs3 veya Windows üzerinde Windows 10 hedeflese de, kapsayıcının IP'si ile değiştirilir. <br/><br/> - {ServicePort} - SSL'nin kullanıp kullanılmay durumuna bağlı olarak genellikle sslPort veya httpPort ile değiştirilir. <br/> Ancak, Windows RS3 veya daha eski bir Windows 10 kapsayıcılarını hedeflerken, SSL'nin kullanıp kullanılmay durumuna bağlı olarak "443" veya "80" ile değiştirilir. |
| sslPort              | "sslPort": 44381                                      | Konakta bu bağlantı noktası, kapsayıcıyı başlatmadan önce kapsayıcının bağlantı noktası 443 ile eşlenmiş. |
| useSSL               | "useSSL": true                                        | Projeyi başlatmada SSL kullanıp kullanmaycazını gösterir. useSSL belirtilmezse sslPort 0 olduğunda SSL > kullanılır. |

> [!NOTE]
> DockerfileRunArguments gibi aynı ayarlar hem proje dosyasında hem de başlatma ayarları dosyasında bulunursa başlatma ayarları dosyasındaki değer önceliklidir.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Container Tools derleme özelliklerini [ayarerek projenizi yapılandırma](container-msbuild-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Docker Compose özellikleri oluşturma](docker-compose-properties.md)
- [Docker Compose için başlatma profillerini yönetme](launch-profiles.md)
