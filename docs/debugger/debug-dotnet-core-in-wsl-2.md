---
title: WSL kullanarak Linux'ta .NET uygulamalarının hata ayıklaması
description: WsL'de .NET uygulamalarınızı çalışmadan çalıştırmayı ve hata ayıklamayı Visual Studio.
ms.date: 08/06/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: dab41bd2bbe83a648c72c64c413e8a9d5d8cf4ce
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630777"
---
# <a name="debug-net-apps-in-wsl-with-visual-studio"></a>WSL'de .NET Uygulamalarının hata ayıklaması Visual Studio

WSL kullanarak .NET uygulamalarınızı linux'ta kolayca çalıştırabilir ve Visual Studio ayıklayabilirsiniz. Platformlar arası bir geliştiriciyseniz, bu yöntemi hedef ortamlarınızı daha fazla test etmek için basit bir yol olarak kullanabilirsiniz.

Linux'ı Windows net bir .NET kullanıcısı için WSL, üretim gerçekçiliği ve üretkenlik arasında güzel bir noktada yaşıyor. Bu Visual Studio, uzaktan hata ayıklayıcısını kullanarak veya Kapsayıcı Araçları'nın kullanarak kapsayıcılarla [uzak](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)Linux ortamında zaten hata [ayıkabilirsiniz.](../containers/overview.md) Ana endişeniz üretim gerçekçiliği olduğunda bu seçeneklerden birini kullanabilirsiniz. Kolay ve hızlı bir iç döngü daha önemli olduğunda WSL harika bir seçenektir.

Tek bir yöntem seçmenize gerek yok! Aynı projede Docker ve WSL için bir başlatma profiline sahip olabilir ve belirli bir çalıştırma için uygun olanı seçin. Ayrıca, uygulama dağıtıldıktan sonra, bir sorun varsa, uzak hata ayıklayıcıyı kullanarak buna iliştirebilirsiniz.

>[!NOTE]
> 2019 Visual Studio 16.11 Preview 3 sürümünden başlayarak, WSL 2 hata ayıklama hedefi WSL olarak yeniden adlandırıldı.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio WSL isteğe bağlı bileşeniyle .NET Hata Ayıklama ile 2019 v16.9 Preview 1 veya sonraki sürümleri.

  İsteğe bağlı bileşen varsayılan olarak .NET Core platformlar arası veya web geliştirme ASP.NET iş yüklerine dahil edilir. Bu iş yüklerinden birini veya ikisini birden yüklemeniz gerekir.

- [WSL'i yükleyin.](/windows/wsl/about)

- Tercihe [göre](https://aka.ms/wslstore) dağıtımı yükleyin.

## <a name="start-debugging-with-wsl"></a>WSL ile hata ayıklamaya başlama

1. Gerekli bileşenleri yükledikten sonra ASP.NET Core'de bir ASP.NET Core web uygulaması veya .NET Core konsol uygulaması Visual Studio WSL adlı yeni bir Başlatma Profili görüyorsunuz:

   ![Başlatma profili listesinde WSL başlatma profili](media/linux-wsl2-debugging-select-launch-profile.png)

1. *LaunchSettings.json* dosyanıza eklemek için bu profili seçin.

   Dosyada yer alan anahtar özniteliklerden bazıları aşağıdaki örnekte gösterilmiştir.

    ::: moniker range=">=vs-2022"

    >[!NOTE]
    > 2022 Preview 3'Visual Studio başlayarak, Başlatma Profili'nin komut adı WSL2'den WSL'ye değiştirildi.

    ```json
    "WSL": {
        "commandName": "WSL",
        "launchBrowser": true,
        "launchUrl": "https://localhost:5001",
        "environmentVariables": {
            "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
            "ASPNETCORE_ENVIRONMENT": "Development"
        },
        "distributionName": ""
    }
    ```
    ::: moniker-end
    ::: moniker range="vs-2019"
    ```json
    "WSL": {
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
    ::: moniker-end

   Yeni profili seçmenizin ardından uzantı, WSL dağıtımınızı .NET uygulamalarını çalıştıracak şekilde yapılandırıldığından emin olur ve eksik bağımlılıkları yüklemenize yardımcı olur. Bu bağımlılıkları yüklemiş olduktan sonra WSL'de hata ayıklamaya hazır oluruz.

1. Hata ayıklamayı normal şekilde başlatsanız, uygulamanız varsayılan WSL dağıtımında çalıştırılıyor.

   Linux'ta çalıştırmayı doğrulamanın kolay bir yolu değerini kontrol `Environment.OSVersion` etmektir.

>[!NOTE]
> Yalnızca Ubuntu ve Debian test edilmiştir ve desteklenebildi. .NET tarafından desteklenen diğer dağıtımlar çalışmalı, ancak .NET Çalışma Zamanı ve [Curl'in el ile](https://aka.ms/wsldotnet) yüklemesini [gerektirir.](https://curl.haxx.se/)

## <a name="choose-a-specific-distribution"></a>Belirli bir dağıtımı seçme

Varsayılan olarak, WSL 2 başlatma profili, 'de ayar olarak varsayılan *dağıtımıwsl.exe.* Başlatma profilinizin varsayılandan bağımsız olarak belirli bir dağıtımı hedeflemesini istiyorsanız, başlatma profilinizi değiştirebilirsiniz. Örneğin, bir web uygulamasında hata ayıklarken bunu Ubuntu 20.04'te test etmek için başlatma profiliniz şöyle olabilir:

::: moniker range=">=vs-2022"
```json
"WSL": {
    "commandName": "WSL",
    "launchBrowser": true,
    "launchUrl": "https://localhost:5001",
    "environmentVariables": {
        "ASPNETCORE_URLS": "https://localhost:5001;http://localhost:5000",
        "ASPNETCORE_ENVIRONMENT": "Development"
    },
    "distributionName": "Ubuntu-20.04"
}
```
::: moniker-end
::: moniker range="vs-2019"
```json
"WSL": {
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
::: moniker-end

## <a name="target-multiple-distributions"></a>Birden çok dağıtımı hedefleme

Bir adım daha ileri gitmek gerekirse, birden çok dağıtımda çalışması gereken bir uygulama üzerinde çalışıyorsanız ve bunların her birini test etmek için hızlı bir yol almak için birden çok başlatma profiline sahip olabilirsiniz. Örneğin konsol uygulamalarınızı Debian, Ubuntu 18.04 ve Ubuntu 20.04'te test etmek için aşağıdaki başlatma profillerini kullanabilirsiniz:

::: moniker range=">=vs-2022"
```json
"WSL : Debian": {
    "commandName": "WSL",
    "distributionName": "Debian"
},
"WSL : Ubuntu 18.04": {
    "commandName": "WSL",
    "distributionName": "Ubuntu-18.04"
},
"WSL : Ubuntu 20.04": {
    "commandName": "WSL",
    "distributionName": "Ubuntu-20.04"
}
```
::: moniker-end
::: moniker range="vs-2019"
```json
"WSL : Debian": {
    "commandName": "WSL2",
    "distributionName": "Debian"
},
"WSL : Ubuntu 18.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-18.04"
},
"WSL : Ubuntu 20.04": {
    "commandName": "WSL2",
    "distributionName": "Ubuntu-20.04"
}
```
::: moniker-end

Bu başlatma profilleriyle, hedef dağıtımlarınız arasında kolayca geçiş yapabilirsiniz. Tüm bunlar, dağıtımların rahat Visual Studio.

![Başlatma profili listesinde birden çok WSL başlatma profili](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>Başlatma profilinde WSL ayarları

Aşağıdaki tabloda başlatma profilinde desteklenen ayarlar gösterildi.

|Name|Varsayılan|Amaç|Belirteçler desteklesin mi?|
|-|-|-|-|
|executablePath|dotnet|Çalıştıracak yürütülebilir dosya|Yes|
|commandLineArgs|TargetPath MSBuild WSL ortamıyla eşlenen MSBuild değeri|executablePath'e geçirilen komut satırı bağımsız değişkenleri|Yes|
|Workingdirectory|Konsol uygulamaları için: {*OutDir*}</br>Web uygulamaları için: {*ProjectDir*}|Hata ayıklamanın başlat başlayacağı çalışma dizini|Yes|
|environmentVariables||Hata ayıklandı işlemi için ayar yapmak için ortam değişkenlerinin Anahtar Değer çiftleri.|Yes|
|setupScriptPath||Hata ayıklamadan önce çalıştıracak betik. ~/.bash_profile gibi betikleri çalıştırmaya .bash_profile.|Yes|
|distributionName||Kullanmak üzere WSL dağıtımının adı.|No|
|launchBrowser|yanlış|Tarayıcı başlatıp başlatmama|No|
|launchUrl||launchBrowser true ise başlatma URL'si|No|

Desteklenen belirteçler:

{*ProjectDir*} - Proje dizininin yolu

{*OutDir*} - MSBuild özelliği`OutDir`

>[!NOTE]
> Tüm yollar WSL için değildir Windows.
