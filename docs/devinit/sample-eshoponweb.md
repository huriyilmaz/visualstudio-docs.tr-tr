---
title: eShopOnWeb
description: DotNet-Architecture/eShopOnWeb deposu için devinit kullanan örnek özelleştirme.
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
ms.openlocfilehash: 3fe551626880c9a469abcfb22ef7b249c77c225b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943554"
---
# <a name="eshoponweb"></a>eShopOnWeb

Bu örnekte, [Eshoponweb](https://github.com/dotnet-architecture/eShopOnWeb) 'In [GitHub codespaces](https://github.com/features/codespaces)ile otomatik olarak sağlanması için DotNet mimarisinin nasıl özelleştirileceği gösterilmektedir.

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Bu komut dosyası _PostCloneSetup.ps1_ çağrılır ve depoyu kurmak için yerel olarak da çalıştırılabilir. Bu dosyanın _.devcontainer.js_ ile aynı klasörde olması gerekir.

```console
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

## <a name="devinitjson"></a>.devinit.json

[`.devinit.json`](devinit-json.md)Dosyanın içeriği. Bu dosyanın _.devcontainer.js_ ile aynı klasörde olması gerekir.

```json
{
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        },
        {
            "tool": "require-mssql"
        },
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
            "additionalOptions": "--global"
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
