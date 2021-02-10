---
title: OpenCV
description: OpenCV deposu için hem Linux hem de Windows 'u hedeflemek için devinit kullanan örnek özelleştirme.
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
ms.openlocfilehash: 6524cec090f20c475724f1ae8615c5dd24cfa2d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943507"
---
# <a name="opencv"></a>OpenCV

Bu örnekte, [OpenCV/OpenCV](https://github.com/opencv/opencv)gibi çok platformlu projelerle geliştirmek Için [GitHub codespaces](https://github.com/features/codespaces) 'ın nasıl özelleştirileceği gösterilmektedir.

Aşağıdaki özelleştirmeler [Microsoft/OpenCV](https://github.com/microsoft/opencv) çatalından zaten uygulanmış ve Windows ve Ubuntu hedeflemesi oluşturmaya izin veriyor.

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

Her zaman adlı bir varsayılan derleme yapılandırması hedeflemesi oluşturulur `x64-Debug` .

Yukarıdaki belirtilen dosyaları ekleyerek, Codespace örnek oluşturma sırasında, Visual Studio [Bağlantı Yöneticisi](/cpp/linux/connect-to-your-remote-linux-computer)'nde yenı bir SSH bağlantısı sağlar ve yapılandırma SEÇICIDE, SSH bağlantısı aracılığıyla Ubuntu örneğini hedefleyen yeni bir yapılandırma oluşturur.

![Ubuntu 'ı hedefleyen yapılandırma](media/wsl-ssh-linux-configuration.png).

WSL 'yi hedefleyen vurgulanan yapılandırmayı seçerek, OpenCV 'nin derleme hedeflerini derlemek ve hata ayıklamak mümkündür.
