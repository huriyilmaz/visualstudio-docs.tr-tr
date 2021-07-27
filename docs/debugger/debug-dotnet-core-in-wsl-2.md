---
title: WSL 2 kullanarak Linux'ta .NET uygulamalarının hata ayıklaması
description: WsL 2'de .NET uygulamalarınızı çalışmadan çalıştırmayı ve hata ayıklamayı Visual Studio.
ms.date: 07/16/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 41bd6cf6f45862702e282691467ce1ef26137b8e
ms.sourcegitcommit: 3c5b1a1d51b521356f42a6879c1f1745573dda65
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2021
ms.locfileid: "114591988"
---
# <a name="debug-net-apps-in-wsl-2-with-visual-studio"></a>WSL 2'de .NET Apps'te Visual Studio

WSL 2 kullanarak .NET uygulamalarınızı Linux'ta kolayca çalıştırabilir ve Visual Studio ayıklayabilirsiniz. Platformlar arası bir geliştiriciyseniz, bu yöntemi hedef ortamlarınızı daha fazla test etmek için basit bir yol olarak kullanabilirsiniz.

Linux'Windows bir .NET kullanıcısı için WSL 2, üretim gerçekçiliği ve üretkenlik arasında güzel bir noktada yer amaktadır. Bu Visual Studio, uzaktan hata ayıklayıcısını kullanarak veya Kapsayıcı [](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)Araçları'nın kullanarak kapsayıcılarla uzak Linux ortamında zaten hata [ayıkabilirsiniz.](../containers/overview.md) Ana endişeniz üretim gerçekçiliği olduğunda bu seçeneklerden birini kullanabilirsiniz. Kolay ve hızlı bir iç döngü daha önemli olduğunda WSL 2 harika bir seçenektir.

Tek bir yöntem seçmenize gerek yok! Aynı projede Docker ve WSL 2 için bir başlatma profiline sahip olabilir ve belirli bir çalıştırma için uygun olanı seçin. Ayrıca, uygulama dağıtıldıktan sonra, bir sorun varsa, uzak hata ayıklayıcıyı kullanarak buna iliştirebilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2019 v16.9 Preview 1 veya sonraki sürümleri WSL 2 ile .NET Core Hata Ayıklama isteğe bağlı bileşeniyle birlikte gelir.

  İsteğe bağlı bileşen varsayılan olarak .NET Core platformlar arası veya web geliştirme ASP.NET iş yüklerine dahil edilir. Bu iş yüklerinden birini veya ikisini birden yüklemeniz gerekir.

- [WSL 2'ye yükleyin.](/windows/wsl/about)

- Tercihe [göre](https://aka.ms/wslstore) dağıtımı yükleyin.

## <a name="start-debugging-with-wsl-2"></a>WSL 2 ile hata ayıklamayı başlatma

1. Gerekli bileşenleri yükledikten sonra Visual Studio'de bir ASP.NET Core web uygulaması veya .NET Core konsol uygulaması açın. WSL 2 adlı yeni bir Başlatma Profili görüyorsunuz:

   ![Başlatma profili listesinde WSL 2 başlatma profili](media/linux-wsl2-debugging-select-launch-profile.png)

1. Bu profili seçerek üzerindelaunchSettings.js *ekleyin.*

   Dosyada yer alan anahtar özniteliklerden bazıları aşağıdaki örnekte gösterilmiştir.

    ```json
    "WSL 2": {
        "commandName": "WSL2",
        "launchBrowser": true,
        "launchUrl": "https://localhost:5001",
        "environmentVariables": {
            "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "distributionName": ""
    }
    ```

   Yeni profili seçmenizin ardından uzantı, WSL 2 dağıtımınızı .NET uygulamalarını çalıştıracak şekilde yapılandırıldığından emin olur ve eksik bağımlılıkları yüklemenize yardımcı olur. Bu bağımlılıkları yükleyemedikten sonra WSL 2'de hata ayıklamaya hazır oluruz.

1. Hata ayıklamayı normal şekilde başlatabilirsiniz ve uygulamanız varsayılan WSL 2 dağıtımında çalıştırılıyor.

   Linux'ta çalıştırmayı doğrulamanın kolay bir yolu değerini kontrol `Environment.OSVersion` etmektir.

>[!NOTE]
> Yalnızca Ubuntu ve Debian test edilmiştir ve desteklenebildi. .NET tarafından desteklenen diğer dağıtımlar çalışmalı, ancak .NET Çalışma Zamanı ve [Curl'in el ile](https://aka.ms/wsldotnet) yüklemesini [gerektirir.](https://curl.haxx.se/)

## <a name="choose-a-specific-distribution"></a>Belirli bir dağıtımı seçme

Varsayılan olarak, WSL 2 başlatma profili, 'de ayar olarak varsayılan *dağıtımıwsl.exe.* Başlatma profilinizin varsayılandan bağımsız olarak belirli bir dağıtımı hedeflemesini istiyorsanız, başlatma profilinizi değiştirebilirsiniz. Örneğin, bir web uygulamasında hata ayıklarken bunu Ubuntu 20.04'te test etmek için başlatma profiliniz şöyle olabilir:

```json
"WSL 2": {
    "commandName": "WSL2",
    "launchBrowser": true,
    "launchUrl": "https://localhost:5001",
    "environmentVariables": {
        "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
        "ASPNETCORE_ENVIRONMENT": "Development"
    },
    "distributionName": "Ubuntu-20.04"
}
```

## <a name="target-multiple-distributions"></a>Birden çok dağıtımı hedefleme

Bir adım daha ileri gitmek gerekirse, birden çok dağıtımda çalışması gereken bir uygulama üzerinde çalışıyorsanız ve bunların her birini test etmek için hızlı bir yol almak için birden çok başlatma profiline sahip olabilirsiniz. Örneğin konsol uygulamalarınızı Debian, Ubuntu 18.04 ve Ubuntu 20.04'te test etmek için aşağıdaki başlatma profillerini kullanabilirsiniz:

```json
"WSL 2 : Debian": {
    "commandName": "WSL2",
    "distributionName": "Debian"
},
"WSL 2 : Ubuntu 18.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-18.04"
},
"WSL 2 : Ubuntu 20.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-20.04"
}
```

Bu başlatma profilleriyle, hedef dağıtımlarınız arasında kolayca geçiş yapabilirsiniz. Tüm bunlar, dağıtımların rahat Visual Studio.

![Başlatma profili listesinde birden çok WSL 2 başlatma profili](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>Başlatma profilinde WSL ayarları

Aşağıdaki tabloda başlatma profilinde desteklenen ayarlar yer alır.

|Name|Varsayılan|Amaç|Belirteçler desteklesin mi?|
|-|-|-|-|
|executablePath|dotnet|Çalıştıracak yürütülebilir dosya|Yes|
|commandLineArgs|TargetPath MSBuild WSL ortamıyla eşlenen MSBuild değeri|executablePath'e geçirilen komut satırı bağımsız değişkenleri|Yes|
|Workingdirectory|Konsol uygulamaları için: {*OutDir*}</br>Web uygulamaları için: {*ProjectDir*}|Hata ayıklamanın başlat başlayacağı çalışma dizini|Yes|
|environmentVariables||Hata ayıklandı işlemi için ayar yapmak için ortam değişkenlerinin Anahtar Değer çiftleri.|Yes|
|setupScriptPath||Hata ayıklamadan önce çalıştıracak betik. ~/.bash_profile gibi betikleri çalıştırmaya .bash_profile.|Yes|
|distributionName||Kullanmak üzere WSL dağıtımının adı.|Hayır|
|launchBrowser|yanlış|Tarayıcı başlatıp başlatmama|Hayır|
|launchUrl||launchBrowser true ise başlatma URL'si|Hayır|

Desteklenen belirteçler:

{*ProjectDir*} - Proje dizininin yolu

{*OutDir*} - MSBuild özelliği`OutDir`

>[!NOTE]
> Tüm yollar WSL için değildir Windows.
