---
title: .NET Core Runtime
description: DotNet/Runtime deposu için devinit kullanan örnek özelleştirme.
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
ms.openlocfilehash: d703e71b6f8ab57ab07c4143fdd5435585c6004c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725856"
---
# <a name="net-core-runtime"></a>.NET Core çalışma zamanı

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

bu örnekte, .net Core çalışma zamanı [dotnet/çalışma](https://github.com/dotnet/runtime) zamanının [GitHub codespaces](https://github.com/features/codespaces)ile otomatik olarak sağlanması için nasıl özelleştirileceği gösterilmektedir.

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Bu komut dosyası _PostCloneSetup.ps1_ çağrılır ve depoyu kurmak için yerel olarak da çalıştırılabilir. Bu dosyanın _. devcontainer. JSON_ ile aynı klasörde olması gerekir.

```console
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

_packages.config_ dosyası, yüklenecek Chocolatey paketlerinin listesini tanımlayan bir [Chocolatey](https://chocolatey.org/) dosyasıdır. Bu dosyanın _. devcontainer. JSON_ ile aynı klasörde olması gerekir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.json

[`.devinit.json`](devinit-json.md)Dosyanın içeriği. Bu dosyanın _. devcontainer. JSON_ dosyasıyla aynı klasörde olması gerekir.

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "choco-install",
            "input": "packages.config"
        },
        {
            "tool": "require-vscomponent"
        }
    ]
}
```

## <a name="devcontainerjson"></a>. devcontainer. JSON

Depo kökündeki _. devcontainer. JSON_ dosyasının içeriği.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
