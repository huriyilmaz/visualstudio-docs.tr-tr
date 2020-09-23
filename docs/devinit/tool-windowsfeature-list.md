---
title: WindowsFeature-listesi
description: devinit Tool WindowsFeature-List.
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 6c4c20fb92e0d854eb7745a598efabd7ac426bfc
ms.sourcegitcommit: 417ea66a8b07ec102ece2fa00e07b88edc404c00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91127836"
---
# <a name="windowsfeature-list"></a>WindowsFeature-listesi

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

```json
{
    "$schema": "./devinit.schema-2.0.json",
    "run": [
        {
            "comments": "Lists the state of all Windows features.",
            "tool": "windowsfeature-list"
        }
    ]
}
```
