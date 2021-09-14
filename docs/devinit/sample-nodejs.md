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
ms.openlocfilehash: 61e58109d98417e7b8b57a6c0fd23c64106413d7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725855"
---
# <a name="nodejs-app"></a>Node.js uygulaması

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

Bir Node.js Express projesi için NPM paketlerini yüklemek üzere devinit kullanmanın tam bir örneği için [devinit-example-NodeJS](https://github.com/microsoft/devinit-example-nodejs) deposuna bakın.

## <a name="devinitjson"></a>.devinit.json

Depo kökündeki _. devinit. JSON_ dosyasının içeriği.

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

## <a name="devcontainerjson"></a>. devcontainer. JSON

Depo kökündeki _. devcontainer. JSON_ dosyasının içeriği.

```json
{
  "postCreateCommand": "devinit init"
}
```
