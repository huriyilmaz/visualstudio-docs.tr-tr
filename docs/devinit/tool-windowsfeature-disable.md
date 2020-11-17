---
title: windowsfeature-disable
description: devinit aracı WindowsFeature-devre dışı.
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
ms.openlocfilehash: 1f06f89a61b77bd4c323303ca796252d4874b3cc
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671734"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

`windowsfeature-disable`Araç, Windows özelliklerini almak için kullanılır.

## <a name="usage"></a>Kullanım

| Ad                                             | Tür   | Gerekli | Değer                                                                  |
|--------------------------------------------------|--------|----------|------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                  |
| [**girişinin**](#input)                              | string | Yes      | Yüklenecek Windows özelliği. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.       |

### <a name="input"></a>Girdi

`input`Özelliği `name` `windows feature` devre dışı bırakmak için özelliğinin öğesinin ' i olmalıdır.

### <a name="additional-options"></a>Additional-Options

Yok.

### <a name="default-behavior"></a>Varsayılan davranış

Aracının varsayılan davranışı `windowsfeature-disable` , gerekli olduğu gibi hata ' dır `input` .

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
