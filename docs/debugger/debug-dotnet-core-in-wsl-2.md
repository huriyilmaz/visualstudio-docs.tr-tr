---
title: WSL kullanarak Linux 'ta .NET uygulamalarında hata ayıklama
description: Visual Studio çıkmadan WSL 'de .NET uygulamalarınızı çalıştırmayı ve hata ayıklamayı öğrenin.
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
ms.openlocfilehash: e13cc2460ba5fa413ff17536a800a3ff125bbbcf9d46f296f853608d5eb82498
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345903"
---
# <a name="debug-net-apps-in-wsl-with-visual-studio"></a>Visual Studio ile WSL 'de .NET uygulamalarında hata ayıklama

wsl kullanarak Visual Studio çıkmadan, .net uygulamalarınızı Linux 'ta kolayca çalıştırabilir ve hata ayıklayabilirsiniz. Platformlar arası bir geliştiricisiyseniz, bu yöntemi hedef ortamlarınızın daha fazlasını test etmenin basit bir yolu olarak kullanabilirsiniz.

wsl, Linux 'u hedefleyen Windows bir .net kullanıcısı için üretim ve verimlilik arasında tatlı bir sıra yaşar. Visual Studio, uzak bir Linux ortamında, [uzaktan hata ayıklayıcıyı](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)kullanarak veya [kapsayıcı araçlarını](../containers/overview.md)kullanarak kapsayıcılarla hata ayıklaması yapabilirsiniz. Üretim için önemli bir sorun olduğunda, bu seçeneklerden birini kullanmanız gerekir. Kolay ve hızlı bir iç döngü daha önemliyse, WSL harika bir seçenektir.

Yalnızca bir yöntem seçmeniz gerekmez! Aynı projede Docker ve WSL için bir başlatma profili oluşturabilir ve belirli bir çalıştırma için uygun olanını seçebilirsiniz. Uygulamanız dağıtıldıktan sonra, bir sorun varsa, bu uygulamaya eklemek için her zaman uzaktan hata ayıklayıcıyı kullanabilirsiniz.

>[!NOTE]
> Visual Studio 2019 sürüm 16,11 Preview 3 ' te başlayarak, wsl 2 hata ayıklama hedefi wsl olarak yeniden adlandırıldı.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio 2019 v 16.9 Preview 1 veya sonraki sürümleri, wsl isteğe bağlı bileşeniyle .net hata ayıklaması ile birlikte.

  isteğe bağlı bileşen, .net Core platformlar arası veya ASP.NET ve web geliştirme iş yükleriyle varsayılan olarak dahil edilmiştir. Bu iş yüklerinin birini veya her ikisini de yüklemelisiniz.

- [WSL](/windows/wsl/about)'yi yükler.

- Seçtiğiniz [dağıtımı](https://aka.ms/wslstore) yükler.

## <a name="start-debugging-with-wsl"></a>WSL ile hata ayıklamayı Başlat

1. gerekli bileşenleri yükledikten sonra, Visual Studio ' de bir ASP.NET Core web uygulaması veya .net Core konsol uygulaması açın, wsl adlı yeni bir başlatma profili görürsünüz:

   ![Başlatma profili listesinde WSL başlatma profili](media/linux-wsl2-debugging-select-launch-profile.png)

1. *ÜzerindelaunchSettings.js* eklemek için bu profili seçin.

   Dosyadaki bazı anahtar öznitelikleri aşağıdaki örnekte gösterilmiştir.

    ::: moniker range=">=vs-2022"

    >[!NOTE]
    > Visual Studio 2022 Preview 3 ' ten başlayarak, başlatma profilindeki komut adı WSL2 iken wsl olarak değiştirilmiştir.

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

   Yeni profili seçtiğinizde, uzantı WSL dağılımının .NET uygulamalarını çalıştıracak şekilde yapılandırılıp yapılandırılmadığını denetler ve eksik bağımlılıkları yüklemenize yardımcı olur. Bu bağımlılıkları yükledikten sonra, WSL 'de hata ayıklamaya hazırsanız.

1. Hata ayıklamayı normal olarak başlatın ve uygulamanız varsayılan WSL dağıtımında çalışacaktır.

   Linux 'ta çalıştırdığınız için kolay bir yol, değerini denetliyoruz `Environment.OSVersion` .

>[!NOTE]
> Yalnızca Ubuntu ve deni test edilmiştir ve desteklenir. .NET tarafından desteklenen diğer dağıtımlar da çalışır, ancak [.NET çalışma zamanı](https://aka.ms/wsldotnet) ve [kıvrımlı](https://curl.haxx.se/)el ile yüklenmesi gerekir.

## <a name="choose-a-specific-distribution"></a>Belirli bir dağıtım seçin

Varsayılan olarak, WSL 2 başlatma profili, *wsl.exe* ayarlandığı şekilde varsayılan dağıtımı kullanır. Başlatma profilinizin belirli bir dağıtımı hedeflemesini istiyorsanız, bu varsayılan değer ne olursa olsun, başlatma profilinizi değiştirebilirsiniz. Örneğin, bir Web uygulamasında hata ayıklaması yapıyorsanız ve Ubuntu 20,04 ' de test etmek istiyorsanız, başlatma profiliniz şöyle görünür:

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

## <a name="target-multiple-distributions"></a>Birden çok dağıtımı hedefle

Bir adım daha devam etmek için, birden fazla dağıtımda çalışması gereken bir uygulama üzerinde çalışıyorsanız ve bunların her birinde test etmek için hızlı bir yol istiyorsanız birden fazla başlatma profili kullanabilirsiniz. Örneğin, konsol uygulamanızı de, Ubuntu 18,04 ve Ubuntu 20,04 ' de test etmeniz gerekiyorsa aşağıdaki başlatma profillerini kullanabilirsiniz:

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

Bu başlatma profilleriyle, Visual Studio rahatlığını yapmadan hedef dağıtımlarınız arasında kolayca geri ve ileri geçiş yapabilirsiniz.

![Başlatma profili listesinde birden çok WSL başlatma profili](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>Başlatma profilindeki WSL ayarları

Aşağıdaki tabloda, başlatma profilinde desteklenen ayarlar gösterilmektedir.

|Name|Varsayılan|Amaç|Belirteçleri destekliyor mu?|
|-|-|-|-|
|executablePath|dotnet|Çalıştırılacak yürütülebilir dosya|Yes|
|commandLineArgs|wsl ortamıyla eşlenen MSBuild özelliğinin değeri|ExecutablePath 'e geçirilen komut satırı bağımsız değişkenleri|Yes|
|workingDirectory|Konsol uygulamaları için: {*OutDir*}</br>Web Apps için: {*ProjectDir*}|Hata ayıklamanın başlatılacağı çalışma dizini|Yes|
|environmentVariables||Hata ayıklanan işlem için ayarlanacak ortam değişkenlerinin anahtar değeri çiftleri.|Yes|
|Kurulumbetiğiyolu||Hata ayıklamadan önce çalıştırılacak komut dosyası. ~/.Bash_profile gibi betikleri çalıştırmak için faydalıdır.|Yes|
|distributionName||Kullanılacak WSL dağıtımının adı.|Hayır|
|launchBrowser|yanlış|Tarayıcının başlatılıp başlatılmayacağını belirtir|Hayır|
|launchUrl 'Si||LaunchBrowser doğruysa başlatılacak URL|Hayır|

Desteklenen belirteçler:

{*ProjectDir*}-proje dizininin yolu

{*outdir*}-MSBuild özelliğinin değeri`OutDir`

>[!NOTE]
> Tüm yollar WSL Windows değil.
