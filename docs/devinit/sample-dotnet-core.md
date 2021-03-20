---
title: .NET Core uygulaması
description: Belirli bir .NET Core SDK yüklemek için devinit kullanan örnek depo.
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
ms.openlocfilehash: b3e25835f305a96b2205fc96cc0200d68ad033af
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672462"
---
# <a name="net-core-app"></a>.NET Core uygulaması

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

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
