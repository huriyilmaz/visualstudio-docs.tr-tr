---
title: .NET Core Runtime
description: dotnet/runtime repo için devinit kullanan örnek özelleştirme.
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
ms.openlocfilehash: 3c8ba55338a957239732f7a45a46acbcb3d9c95bf980efc5e49af4e898cbfac1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452862"
---
# <a name="net-core-runtime"></a>.NET Core çalışma zamanı

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Bu örnek, .NET Core Çalışma Zamanı [dotnet/runtime'ın](https://github.com/dotnet/runtime) [Codespaces](https://github.com/features/codespaces)ile otomatik olarak sağ GitHub göstermektedir.

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Bu betik, _PostCloneSetup.ps1_ olarak çağrılır ve depoyu ayarlamak için yerel olarak da çalıştırılabilir. Bu dosyanın, üzerinde dosyayla aynı _.devcontainer.jsgerekir._

```console
devinit init
git config --system core.longpaths true
```

## <a name="packagesconfig"></a>packages.config

Bu _packages.config,_ [yüklenilen Chocolatey](https://chocolatey.org/) paketlerinin listesini tanımlayan bir Chocolatey dosyasıdır. Bu dosyanın, üzerinde dosyayla aynı _.devcontainer.jsgerekir._

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
    <package id="python" version="3.8.3"  />
    <package id="cmake" version="3.17.3"  />
</packages>
```

## <a name="devinitjson"></a>.devinit.json

Dosyanın [`.devinit.json`](devinit-json.md) içeriği. Bu dosyanın, dosyada yer alan dosyanın _.devcontainer.jsolması_ gerekir.

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

## <a name="devcontainerjson"></a>.devcontainer.js

Dosyanın _.devcontainer.js_ kökte.

```json
{
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File .\\PostCloneSetup.ps1"
}
```
