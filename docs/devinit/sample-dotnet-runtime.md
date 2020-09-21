---
title: .NET Core Runtime
description: DotNet/Runtime deposu için devinit kullanan örnek özelleştirme.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 477a498059be6d1ee5637a704512fd49b62e11b6
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809113"
---
# <a name="net-core-runtime"></a>.NET Core çalışma zamanı

Bu örnekte, .NET Core çalışma zamanı [DotNet/çalışma](https://github.com/dotnet/runtime) zamanının [GitHub codespaces](https://github.com/features/codespaces)ile otomatik olarak sağlanması için nasıl özelleştirileceği gösterilmektedir.

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Bu komut dosyası _PostCloneSetup.ps1_ çağrılır ve depoyu kurmak için yerel olarak da çalıştırılabilir. Bu dosyanın _.devcontainer.js_ile aynı klasörde olması gerekir.

```batch
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

_packages.config_ dosyası, yüklenecek Chocolatey paketlerinin listesini tanımlayan bir [Chocolatey](https://chocolatey.org/) dosyasıdır. Bu dosyanın _.devcontainer.js_ile aynı klasörde olması gerekir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>Üzerinde .devinit.js

Dosyadaki [_.devinit.js_](devinit-json.md) içeriği. Bu dosyanın dosyada _.devcontainer.js_ aynı klasörde olması gerekir.

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

## <a name="devcontainerjson"></a>Üzerinde .devcontainer.js

Depo kökündeki dosya _.devcontainer.js_ içeriği.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File PostCloneSetup.ps1"
}
```
