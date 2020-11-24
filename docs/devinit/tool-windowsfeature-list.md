---
title: windowsfeature-list
description: devinit Tool WindowsFeature-List.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 07b92e8783393fa19e5c09344a396a6c5c4fc011
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442128"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

`windowsfeature-list`Araç, tüm Windows özelliklerinin etkinleştir/devre dışı durumunu listelemek için kullanılır.

| Ad                                             | Tür   | Gerekli | Değer                                      |
|--------------------------------------------------|--------|----------|--------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.      |
| [**girişinin**](#input)                              | dize | No       | Kullanılmadı. LIP.                         |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. LIP.                         |

### <a name="input"></a>Giriş

Kullanılmadı. LIP.

#### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı. LIP.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `windowsfeature-list` tüm Windows özelliklerinin etkinleştirme/devre dışı bırakma durumunu Listeleyeceği.

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
