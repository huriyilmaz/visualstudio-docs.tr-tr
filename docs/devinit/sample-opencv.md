---
title: OpenCV
description: opencv deposu için hem Linux hem de Windows hedeflemek için devinit kullanan örnek özelleştirme.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 2d7750d6a77965527b4bf396afd8de094762821923c543a06d184509c238b205
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452838"
---
# <a name="opencv"></a>OpenCV

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

bu örnekte, [opencv/opencv](https://github.com/opencv/opencv)gibi çok platformlu projelerle geliştirmek için [GitHub codespaces](https://github.com/features/codespaces) 'ın nasıl özelleştirileceği gösterilmektedir.

aşağıdaki özelleştirmeler [microsoft/opencv](https://github.com/microsoft/opencv) çatalından zaten uygulanmış ve Windows ve ubuntu hedeflemesi oluşturmaya izin veriyor.

## <a name="customization-with-devcontainerjson-and-devinitjson"></a>Üzerinde devcontainer.jsve devinit.jsile özelleştirme

`.devcontainer`Dizinin aşağıdaki dosyaları içermesi gerekir:

* devcontainer.json
* Üzerinde devinit.js

### <a name="devcontainerjson"></a>devcontainer.json

_devcontainer.js_ dosyadaki içeriği aşağıda verilmiştir.

```json
{
  "postCreateCommand": "devinit init"
}
```

, `postCreateCommand` _Üzerindedevinit.js_ tüketen [devinit](devinit-and-codespaces.md) aracını başlatır.

### <a name="devinitjson"></a>Üzerinde devinit.js

[_devinit.js_](devinit-json.md) dosyadaki içeriği aşağıda verilmiştir.

```json
{
    "run": [
        {
            "comments": "Example that will install Ubuntu 20.04 using WSL2, and configure it with various packages useful for C++ development.",
            "tool": "wsl-install",
            "input": "https://aka.ms/wslubuntu2004",
            "additionalOptions": "--wsl-version 2 --post-create-command 'apt-get update && apt-get install g++ gcc g++-9 gcc-9 cmake gdb ninja-build zip rsync -y'"
        }
    ]
}
```

_devinit.js_ , [devinit](devinit-and-codespaces.md) aracı tarafından tüketilen dosyadır ve _üzerindedevcontainer.js_ aynı dizinde olmalıdır.

Bu örnekte, [WSL-install](tool-wsl-install.md) Aracı, Ubuntu 20,04 çalıştıran bir WSL örneği oluşturmak ve bunu temel C++ geliştirme araçlarıyla sağlamak için kullanılır.
## <a name="targeting-windows-or-linux"></a>Windows veya Linux 'u hedefleme

Windows varsayılan derleme yapılandırması hedefleme her zaman adlı olarak oluşturulur `x64-Debug` .

yukarıdaki belirtilen dosyaları ekleyerek, codespace örnek oluşturma sırasında, Visual Studio [bağlantı yöneticisi](/cpp/linux/connect-to-your-remote-linux-computer)'nde yeni bir SSH bağlantısı sağlar ve yapılandırma seçicide, ssh bağlantısı aracılığıyla ubuntu örneğini hedefleyen yeni bir yapılandırma oluşturur.

![Ubuntu 'ı hedefleyen yapılandırma](media/wsl-ssh-linux-configuration.png).

WSL 'yi hedefleyen vurgulanan yapılandırmayı seçerek, OpenCV 'nin derleme hedeflerini derlemek ve hata ayıklamak mümkündür.
