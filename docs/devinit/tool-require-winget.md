---
title: gerektir-Winget
description: devinit aracı için-Winget gereklidir.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 9cc805841f5d89e41b82f899eda1b131f60baee4
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2021
ms.locfileid: "100012369"
---
# <a name="require-winget"></a>gerektir-Winget

`require-winget`Araç [Winget](https://docs.microsoft.com/windows/package-manager/winget/)'i yüklemek için kullanılır. 
## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                |
| [**girişinin**](#input)                              | dize | No       | Kullanılmadı.                                                                            |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı.                                                                            |

### <a name="input"></a>Giriş

Kullanılmadı.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `require-winget` [ `winget-cli` Git deposunu](https://github.com/microsoft/winget-cli)kullanarak en son sürümü yüklemektir.

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-6.0",
    "comments": "Example that installs the latest version of winget",
    "run": [
        {
            "tool": "require-winget",
            "comments": "Installs winget",
        }
    ]
}
```
