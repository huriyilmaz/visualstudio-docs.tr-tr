---
title: require-vscomponent
description: devinit aracı-vscomponent gerektirir.
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
ms.openlocfilehash: 0b58e80a03828bf486e6beb4d0014f6fe2267485
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918356"
---
# <a name="require-vscomponent"></a>require-vscomponent

`require-vscomponent`Araç, Visual Studio yapılandırmasını var olan Visual Studio 'ya aktarmak için kullanılır. Buradan daha fazla bilgi edinin `.vsconfig` [](../install/import-export-installation-configurations.md).

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