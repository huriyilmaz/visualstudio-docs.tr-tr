---
title: require-vscomponent
description: devinit aracı-vscomponent gerektirir.
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
ms.openlocfilehash: 7c47c219fa0c0ef32946d6e0500bc37ce9aec0ff
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005039"
---
# <a name="require-vscomponent"></a>require-vscomponent

`require-vscomponent`Araç, Visual Studio yapılandırmasını var olan Visual Studio 'ya aktarmak için kullanılır. Buradan daha fazla bilgi edinin `.vsconfig` [here](https://docs.microsoft.com/visualstudio/install/import-export-installation-configurations).

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                     | Tür   | Gerekli | Değer                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **açıklamaları**                             | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                |
| [**girişinin**](#input)                      | dize | No       | Tam yolu `.vsconfig` . Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [additionalOptions](#additional-options) | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.     |

### <a name="input"></a>Giriş

`input`Özelliği, dosyanın tam yolunu belirtmek için kullanılır `.vsconfig` . Söz konusu değilse, araç `.vsconfig` geçerli dizinde arama yapılır ve değeri Visual Studio yükleyicisi iletir.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `require-vscomponent` `.vsconfig` geçerli dizindeki bir dosyayı aramak ve bu ayrıntılarla Visual Studio yükleyicisi sessiz modda çalıştırmak içindir. `require-vscomponent` yalnızca var olan bir Visual Studio yüklemesinin değiştirilmesini destekler.

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "comments": "Imports .vsconfig file which is passed as input to Visual Studio.",
            "input": "C:\\.vsconfig"
        }
    ]
}
```
