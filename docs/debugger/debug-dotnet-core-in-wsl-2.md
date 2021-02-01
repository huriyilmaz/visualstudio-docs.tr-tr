---
title: WSL 2 ' de .NET Core uygulamalarında hata ayıklama
description: Visual Studio 'dan çıkmadan WSL 2 ' de .NET Core uygulamalarınızı çalıştırmayı ve hata ayıklamayı öğrenin.
ms.date: 01/25/2021
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux
- debugging, wsl2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 736987a02ca7e2f59ce689b8402d9a6fcd7407e9
ms.sourcegitcommit: 586369f5aa61d4a0330802f718f0ceaa55d7e9c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2021
ms.locfileid: "99227657"
---
# <a name="debug-net-core-apps-in-wsl-2-with-visual-studio"></a>Visual Studio ile WSL 2 içindeki .NET Core uygulamalarında hata ayıklama

.NET Core uygulamalarınızı, WSL 2 kullanarak Visual Studio 'dan çıkmadan Linux 'ta kolayca çalıştırabilir ve hata ayıklayabilirsiniz. Platformlar arası bir geliştiricisiyseniz, bu yöntemi hedef ortamlarınızın daha fazlasını test etmenin basit bir yolu olarak kullanabilirsiniz.

Linux 'u hedefleyen bir Windows .NET kullanıcısı için, WSL 2, üretim Reali ve üretkenlik arasında tatlı bir sıra yaşar. Visual Studio 'da, uzak bir Linux ortamında [Uzaktan hata ayıklayıcı](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)veya [kapsayıcı araçlarını](../containers/overview.md)kullanarak kapsayıcılarla hata ayıklaması yapabilirsiniz. Üretim için önemli bir sorun olduğunda, bu seçeneklerden birini kullanmanız gerekir. Kolay ve hızlı bir iç döngü daha önemliyse, WSL 2 harika bir seçenektir.

Yalnızca bir yöntem seçmeniz gerekmez! Aynı projede Docker ve WSL 2 için bir başlatma profiliniz olabilir ve belirli bir çalıştırma için uygun olanını seçebilirsiniz. Uygulamanız dağıtıldıktan sonra, bir sorun varsa, bu uygulamaya eklemek için her zaman uzaktan hata ayıklayıcıyı kullanabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- WSL 2 isteğe bağlı bileşeniyle .NET Core hata ayıklaması ile Visual Studio 2019 v 16.9 Preview 1 veya sonraki sürümleri.

  İsteğe bağlı bileşen, .NET Core platformlar arası veya ASP.NET ve Web geliştirme iş yükleri ile varsayılan olarak dahil edilmiştir. Bu iş yüklerinin birini veya her ikisini de yüklemelisiniz.

- [WSL 2](/windows/wsl/about)' i yükler.

- Seçtiğiniz [dağıtımı](https://aka.ms/wslstore) yükler.

## <a name="start-debugging-with-wsl-2"></a>WSL 2 ile hata ayıklamayı Başlat

1. Gerekli bileşenleri yükledikten sonra, Visual Studio 'da bir ASP.NET Core Web uygulaması veya .NET Core konsol uygulaması açın, WSL 2 adlı yeni bir başlatma profili görürsünüz:

   ![Başlatma profili listesinde WSL 2 başlatma profili](media/linux-wsl2-debugging-select-launch-profile.png)

1. *ÜzerindelaunchSettings.js* eklemek için bu profili seçin.

   Dosyadaki bazı anahtar öznitelikleri aşağıdaki örnekte gösterilmiştir.

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

   Yeni profili seçtikten sonra uzantı, WSL 2 dağılımının .NET Core uygulamaları çalıştıracak şekilde yapılandırılıp yapılandırılmadığını denetler ve eksik bağımlılıkları yüklemenize yardımcı olur. Bu bağımlılıkları yükledikten sonra, WSL 2 ' de hata ayıklamaya hazırsanız.

1. Hata ayıklamayı normal olarak başlatın ve uygulamanız varsayılan WSL 2 dağıtımında çalışacaktır.

   Linux 'ta çalıştırdığınız için kolay bir yol, değerini denetliyoruz `Environment.OSVersion` .

>[!NOTE]
> Yalnızca Ubuntu ve deni test edilmiştir ve desteklenir. .NET Core tarafından desteklenen diğer dağıtımlar çalışır, ancak [.NET Core çalışma zamanı](https://aka.ms/wsldotnet) ve [kıvrımlı](https://curl.haxx.se/)için el ile yükleme gerektirir.

## <a name="choose-a-specific-distribution"></a>Belirli bir dağıtım seçin

Varsayılan olarak, WSL 2 başlatma profili, *wsl.exe* ayarlandığı şekilde varsayılan dağıtımı kullanır. Başlatma profilinizin belirli bir dağıtımı hedeflemesini istiyorsanız, bu varsayılan değer ne olursa olsun, başlatma profilinizi değiştirebilirsiniz. Örneğin, bir Web uygulamasında hata ayıklaması yapıyorsanız ve Ubuntu 20,04 ' de test etmek istiyorsanız, başlatma profiliniz şöyle görünür:

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

## <a name="target-multiple-distributions"></a>Birden çok dağıtımı hedefle

Bir adım daha devam etmek için, birden fazla dağıtımda çalışması gereken bir uygulama üzerinde çalışıyorsanız ve bunların her birinde test etmek için hızlı bir yol istiyorsanız birden fazla başlatma profili kullanabilirsiniz. Örneğin, konsol uygulamanızı de, Ubuntu 18,04 ve Ubuntu 20,04 ' de test etmeniz gerekiyorsa aşağıdaki başlatma profillerini kullanabilirsiniz:

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

Bu başlatma profilleriyle, Visual Studio 'nun rahatlığını yapmadan hedef dağıtımlarınız arasında kolayca geri ve ileri geçiş yapabilirsiniz.

![Başlatma profili listesinde birden çok WSL 2 başlatma profili](media/linux-wsl2-debugging-switch-target-distribution.png)

## <a name="wsl-settings-in-the-launch-profile"></a>Başlatma profilindeki WSL ayarları

Aşağıdaki tabloda, başlatma profilinde desteklenen ayarlar gösterilmektedir.

|Name|Varsayılan|Amaç|Belirteçleri destekliyor mu?|
|-|-|-|-|
|executablePath|dotnet|Çalıştırılacak yürütülebilir dosya|Yes|
|commandLineArgs|WSL ortamıyla eşlenen, TargetPath MSBuild özelliğinin değeri|ExecutablePath 'e geçirilen komut satırı bağımsız değişkenleri|Yes|
|workingDirectory|Konsol uygulamaları için: {*OutDir*}</br>Web Apps için: {*ProjectDir*}|Hata ayıklamanın başlatılacağı çalışma dizini|Yes|
|environmentVariables||Hata ayıklanan işlem için ayarlanacak ortam değişkenlerinin anahtar değeri çiftleri.|Yes|
|Kurulumbetiğiyolu||Hata ayıklamadan önce çalıştırılacak komut dosyası. ~/.Bash_profile gibi betikleri çalıştırmak için faydalıdır.|Yes|
|distributionName||Kullanılacak WSL dağıtımının adı.|Hayır|
|launchBrowser|yanlış|Tarayıcının başlatılıp başlatılmayacağını belirtir|Hayır|
|launchUrl 'Si||LaunchBrowser doğruysa başlatılacak URL|Hayır|

Desteklenen belirteçler:

{*ProjectDir*}-proje dizininin yolu

{*OutDir*}-MSBuild özelliğinin değeri `OutDir`

>[!NOTE]
> Tüm yollar, WSL Windows değil.
