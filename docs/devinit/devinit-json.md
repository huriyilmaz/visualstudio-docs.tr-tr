---
title: devinit yapılandırma dosyası
description: Devınit için bildirim dosyası .devinit.jsbelgeleri.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 5ba7299f90ce5f3f253a7210456053faa6bd22c0
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852204"
---
# <a name="devinit-configuration-file"></a>devinit yapılandırma dosyası

## <a name="file-location"></a>Dosya konumu

`devinit.exe init`Komut, _.devinit.js_ dosyası aracılığıyla yönlendiriliyor. Varsayılan olarak, `devinit.exe` aşağıdaki konumlarda dosyayı arar:

- _{geçerli-dizin}\\_
- _{geçerli-dizin} \\ . devinit\\_
- _{geçerli-dizin} \\ . devcontainer\\_

_._ Dizin ve dosya adları atlanabilir.

Dosyadaki _.devinit.js_ , açıkça seçeneği aracılığıyla da belirlenebilir `--file` / `-f` .

### <a name="directories-and-relative-paths"></a>Dizinler ve göreli yollar

Yollar, devınit 'in çalıştığı konuma göre belirlenir. Bu, genellikle yürütülen geçerli çalışma dizinidir `devinit` .

## <a name="file-format"></a>Dosya Biçimi

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "string",
    "run": [
        {
            "comments": "string",
            "tool": "string",
            "input": "string|null|undefined",
            "additionalOptions": "string|null|undefined"
        }
    ]
}
```

### <a name="property-values"></a>Özellik değerleri

| Ad         | Tür   | Gerekli | Değer                              |
|--------------|--------|----------|------------------------------------|
| **açıklamaları** | dize | No       | Dosya için açıklamalar.             |
| **çalışmaz**      | array  | Yes      | [RunTool nesnesi](#run-tool-object) |

#### <a name="run-tool-object"></a>Araç nesnesi Çalıştır

| Ad                  | Tür   | Gerekli | Değer                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **açıklamaları**          | dize | No       | Araç girişi için açıklamalar.                                                                               |
| **Aracı**              | string | Yes      | Araç adı. `devinit list`Kullanılabilir araçların listesi için komutuna bakın.                            |
| **girişinin**             | dize | No       | Araç girişi. Araca göre farklılık gösterir. Örneğin, gerekli sürüm, paket KIMLIĞI, dosya adı veya klasör.|
| **additionalOptions** | dize | No       | Araca geçirilecek ek komut satırı bağımsız değişkenleri.                                                |

## <a name="examples"></a>Örnekler

Devinit kullanma hakkında daha fazla örnek için [örnekler bölümüne](sample-readme.md)bakın.
