---
title: windowsfeature-disable
description: devinit aracı WindowsFeature-devre dışı.
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
ms.openlocfilehash: ba0bcea403033d869d429c2bc85d86434a3b3846
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874514"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

`windowsfeature-disable`Araç, Windows özelliklerini almak için kullanılır.

## <a name="usage"></a>Kullanım

| Ad                                             | Tür   | Gerekli | Değer                                                                  |
|--------------------------------------------------|--------|----------|------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                  |
| [**girişinin**](#input)                              | string | Yes      | Yüklenecek Windows özelliği. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.       |

### <a name="input"></a>Giriş

`input`Özelliği `name` `windows feature` devre dışı bırakmak için özelliğinin öğesinin ' i olmalıdır.

### <a name="additional-options"></a>Additional-Options

Yok.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `windowsfeature-disable` gerekli olduğu gibi hatada yapılır `input` .

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren bir örnek aşağıda verilmiştir `windowsfeature-disable` `.devinit.json` .

#### <a name="devinitjson-that-will-disable-a-specified-feature"></a>.devinit.js, belirtilen bir özelliği devre dışı bırakacak:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-windowsfeature",
            "input": "web-server",
        }
    ]
}
```
