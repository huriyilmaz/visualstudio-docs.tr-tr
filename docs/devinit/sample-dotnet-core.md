---
title: .NET Core uygulaması
description: Belirli bir .NET Core SDK yüklemek için devinit kullanan örnek depo.
ms.date: 11/04/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 26386631946bd37920ba89490a6210031ef945a6
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93398344"
---
# <a name="net-core-app"></a>.NET Core uygulaması

Codespaces 'a gerekli .NET Core SDK sürümünü yüklemek için devinit kullanmanın tam bir örneği için [devinit-example-DotNet-Core](https://github.com/microsoft/devinit-example-dotnet-core) deposuna bakın.

## <a name="devinitjson"></a>.devinit.json

Depo kökündeki dosya _.devinit.js_ içeriği.

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
