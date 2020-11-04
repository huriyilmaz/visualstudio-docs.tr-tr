---
title: .NET Core uygulaması
description: Belirli bir .NET Core SDK yüklemek için devinit kullanan örnek depo.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 35971ac1fde5fc272f22579cc6640cbea6724db5
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344520"
---
# <a name="net-core-app"></a>.NET Core uygulaması

Codespaces 'a gerekli .NET Core SDK sürümünü yüklemek için devinit kullanmanın tam bir örneği için [Dotnetcoredevınitexexample](https://github.com/microsoft/DotnetCoreDevinitExample) deposuna bakın.

## <a name="devinitjson"></a>.devinit.json

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Installs the .NET Core SDK specified in the global.json file.",
      "tool": "require-dotnetcoresdk"
    }
  ]
}
```

## <a name="devcontainerjson"></a>Üzerinde .devcontainer.js

Depo kökündeki dosya _.devcontainer.js_ içeriği.

```json
{
  "postCreateCommand": "devinit init"
}
```

## <a name="globaljson"></a>global.json

Depo kökündeki dosya _global.js_ içeriği.

```json
{
  "sdk": {
    "version": "3.1.302"
  }
}
```
