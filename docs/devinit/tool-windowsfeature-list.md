---
title: windowsfeature-list
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
ms.openlocfilehash: b521009affbc1db81676481e33640a69e619aaf3
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671714"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

`windowsfeature-list`Araç, tüm Windows özelliklerinin etkinleştir/devre dışı durumunu listelemek için kullanılır.

| Ad                                             | Tür   | Gerekli | Değer                                      |
|--------------------------------------------------|--------|----------|--------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.      |
| [**girişinin**](#input)                              | dize | No       | Kullanılmadı. LIP.                         |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. LIP.                         |

### <a name="input"></a>Girdi

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
