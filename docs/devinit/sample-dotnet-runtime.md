---
title: .NET Core Runtime
description: DotNet/Runtime deposu için devinit kullanan örnek özelleştirme.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 0cc36dc58b65188b21115569f1216446784d227a
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438224"
---
# <a name="net-core-runtime"></a>.NET Core çalışma zamanı

Bu örnekte, .NET Core çalışma zamanı [DotNet/çalışma](https://github.com/dotnet/runtime) zamanının [GitHub codespaces](https://github.com/features/codespaces)ile otomatik olarak sağlanması için nasıl özelleştirileceği gösterilmektedir.

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Bu komut dosyası _PostCloneSetup.ps1_ çağrılır ve depoyu kurmak için yerel olarak da çalıştırılabilir. Bu dosyanın _.devcontainer.js_ ile aynı klasörde olması gerekir.

```console
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

_packages.config_ dosyası, yüklenecek Chocolatey paketlerinin listesini tanımlayan bir [Chocolatey](https://chocolatey.org/) dosyasıdır. Bu dosyanın _.devcontainer.js_ ile aynı klasörde olması gerekir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.json

[`.devinit.json`](devinit-json.md)Dosyanın içeriği. Bu dosyanın dosyadaki _.devcontainer.js_ klasörde olması gerekir.

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
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
