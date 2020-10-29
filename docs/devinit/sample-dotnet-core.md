---
title: .NET Core uygulaması
description: Belirli bir .NET Core SDK yüklemek için devinit kullanan örnek depo.
ms.date: 10/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: ce94dc9cf4b6368a96cc027e1a9fc14e0d7e0650
ms.sourcegitcommit: 7915cedf2f5988db25cb90042aa8466a1d3cee7f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2020
ms.locfileid: "93028149"
---
# <a name="net-core-app"></a>.NET Core uygulaması

Codespaces 'a gerekli .NET Core SDK sürümünü yüklemek için devinit kullanmanın tam bir örneği için [Devınitexexample](https://github.com/microsoft/DevinitExample) deposuna bakın.

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