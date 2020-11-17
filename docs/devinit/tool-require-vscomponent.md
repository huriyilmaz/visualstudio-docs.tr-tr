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
ms.openlocfilehash: e9d2f546e99f83b4c53d0b76abfdaf8ec91868ac
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672113"
---
# <a name="require-vscomponent"></a>require-vscomponent

`require-vscomponent`Araç, Visual Studio yapılandırmasını var olan Visual Studio 'ya aktarmak için kullanılır. Buradan daha fazla bilgi edinin `.vsconfig` [here](../install/import-export-installation-configurations.md).

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                     | Tür   | Gerekli | Değer                                                                |
|------------------------------------------|--------|----------|----------------------------------------------------------------------|
| **açıklamaları**                             | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                |
| [**girişinin**](#input)                      | dize | No       | Tam yolu `.vsconfig` . Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [additionalOptions](#additional-options) | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.     |

### <a name="input"></a>Girdi

`input`Özelliği, dosyanın tam yolunu belirtmek için kullanılır `.vsconfig` . Söz konusu değilse, araç `.vsconfig` geçerli dizinde arama yapılır ve değeri Visual Studio yükleyicisi iletir.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `require-vscomponent` `.vsconfig` geçerli dizindeki bir dosyayı aramak ve bu ayrıntılarla Visual Studio yükleyicisi sessiz modda çalıştırmak içindir. `require-vscomponent` yalnızca var olan bir Visual Studio yüklemesinin değiştirilmesini destekler.

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren bir örnek aşağıda verilmiştir `require-vscomponent` `.devinit.json` . 

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path"></a>.devinit.js, belirli bir. vsconfig dosyası yolunun yapılandırmalarını içeri aktaracak:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig"
        }
    ]
}
```