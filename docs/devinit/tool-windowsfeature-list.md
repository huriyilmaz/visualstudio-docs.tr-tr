---
title: windowsfeature-list
description: devinit Tool WindowsFeature-List.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 79190ef76e0a3693dca7410fa06b55e0f3cb8768cdb60d0804730b5e1a2c6388
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378247"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`windowsfeature-list`araç tüm Windows özelliklerinin etkinleştir/devre dışı durumunu listelemek için kullanılır.

| Ad                                             | Tür   | Gerekli | Değer                                      |
|--------------------------------------------------|--------|----------|--------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.      |
| [**girişinin**](#input)                              | dize | No       | Kullanılmadı. LIP.                         |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. LIP.                         |

### <a name="input"></a>Giriş

Kullanılmadı. LIP.

#### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı. LIP.

### <a name="default-behavior"></a>Varsayılan davranış

aracın varsayılan davranışı, `windowsfeature-list` tüm Windows özelliklerinin etkinleştir/devre dışı durumunu listeleyeceği.

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren bir örnek aşağıda verilmiştir `windowsfeature-list` `.devinit.json` .

#### <a name="devinitjson-that-will-list-the-state-of-all-windows-features"></a>.devinit.js, tüm Windows özelliklerinin durumunu listeler:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "windowsfeature-list"
        }
    ]
}
```
