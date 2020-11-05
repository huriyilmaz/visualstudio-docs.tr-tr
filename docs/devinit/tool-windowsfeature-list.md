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
ms.openlocfilehash: 3030ddaaa3cc19b8719b067d9bd5e3572957b84f
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400200"
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "comments": "Lists the state of all Windows features.",
            "tool": "windowsfeature-list"
        }
    ]
}
```
