---
title: Node.js uygulaması
description: Bir Node.js Express projesi için NPM paketlerini yüklemek için devinit kullanan örnek depo.
ms.date: 11/04/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 0099c6404ef4189732ec5f0729239730815cb190
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943560"
---
# <a name="nodejs-app"></a>Node.js uygulaması

Bir Node.js Express projesi için NPM paketlerini yüklemek üzere devinit kullanmanın tam bir örneği için [devinit-example-NodeJS](https://github.com/microsoft/devinit-example-nodejs) deposuna bakın.

## <a name="devinitjson"></a>.devinit.json

Depo kökündeki dosya _.devinit.js_ içeriği.

```json
{
  "$schema": "https://json.schemastore.org/devinit.schema-2.0",
  "run": [
    {
      "comments": "Installs the body-parser package.",
      "tool": "npm-install",
      "input": "body-parser"
    },
    {
      "comments": "Installs the cookie-parser package.",
      "tool": "npm-install",
      "input": "cookier-parser"
    },
    {
      "comments": "Installs the debug package.",
      "tool": "npm-install",
      "input": "debug"
    },
    {
      "comments": "Installs the express package.",
      "tool": "npm-install",
      "input": "express"
    },
    {
      "comments": "Installs the morgan package.",
      "tool": "npm-install",
      "input": "morgan"
    },
    {
      "comments": "Installs the pug package.",
      "tool": "npm-install",
      "input": "pug"
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
