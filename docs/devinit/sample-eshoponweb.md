---
title: eShopOnWeb
description: DotNet-Architecture/eShopOnWeb deposu için devinit kullanan örnek özelleştirme.
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
ms.openlocfilehash: 052e89d276e122ebf44c2b541771bbb314f48ade
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809106"
---
# <a name="eshoponweb"></a>eShopOnWeb

Bu örnekte, [Eshoponweb](https://github.com/dotnet-architecture/eShopOnWeb) 'In [GitHub codespaces](https://github.com/features/codespaces)ile otomatik olarak sağlanması için DotNet mimarisinin nasıl özelleştirileceği gösterilmektedir.

## <a name="postclonesetupps1"></a>PostCloneSetup.ps1

Bu komut dosyası _PostCloneSetup.ps1_ çağrılır ve depoyu kurmak için yerel olarak da çalıştırılabilir. Bu dosyanın _.devcontainer.js_ile aynı klasörde olması gerekir.

```batch
devinit init
dotnet ef database update -c catalogcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
dotnet ef database update -c appidentitydbcontext -p src\Infrastructure\Infrastructure.csproj -s src\Web\Web.csproj
```

## <a name="devinitjson"></a>Üzerinde .devinit.js

Dosyadaki [_.devinit.js_](devinit-json.md) içeriği. Bu dosyanın _.devcontainer.js_ile aynı klasörde olması gerekir.

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
  "postCreateCommand": "Powershell.exe -ExecutionPolicy unrestricted -File PostCloneSetup.ps1"
}
```
