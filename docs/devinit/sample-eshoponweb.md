---
title: eShopOnWeb
description: DotNet-Architecture/eShopOnWeb deposu için devinit kullanan örnek özelleştirme.
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
ms.openlocfilehash: e886ea23a8f4f0815773f704d1d8274fced610df
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134596"
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

Dosyadaki [_.devinit.js_](devinit-json.md) içeriği. Bu dosyanın _.devcontainer.js_ ile aynı klasörde olması gerekir.

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
