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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725857"
---
# <a name="net-core-app"></a>.NET Core uygulaması

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

Codespaces 'a gerekli .NET Core SDK sürümünü yüklemek için devinit kullanmanın tam bir örneği için [devinit-example-DotNet-Core](https://github.com/microsoft/devinit-example-dotnet-core) deposuna bakın.

## <a name="devinitjson"></a>.devinit.json

Depo kökündeki _. devinit. JSON_ dosyasının içeriği.

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

## <a name="devcontainerjson"></a>. devcontainer. JSON

Depo kökündeki _. devcontainer. JSON_ dosyasının içeriği.

```json
{
  "postCreateCommand": "devinit init"
}
```

## <a name="globaljson"></a>global.json

Depo kökündeki _Global. JSON_ dosyasının içeriği.

```json
{
  "sdk": {
    "version": "3.1.302"
  }
}
```
