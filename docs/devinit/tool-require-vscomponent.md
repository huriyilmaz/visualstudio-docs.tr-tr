---
title: require-vscomponent
description: devinit aracı-vscomponent gerektirir.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 50172f96a49e2384553a372ded0c889b30a23fff
ms.sourcegitcommit: e262f4c2a147c3fa2d27de666aae3a0497317867
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2021
ms.locfileid: "100006395"
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

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . 

| Ad                      | Tür      | Gerekli | Değer                                                                                                                                                                                    |
|---------------------------|-----------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| --InstallPath             | dize    | No       | Değiştirmek istediğiniz Visual Studio örneğinin install yolu.                                                                                                                       |

Hiçbir yükleme yolu belirtilmemişse, makinenizde birden çok örnek varsa, araç makinenizde en eski yüklü Visual Studio 'Yu değiştirecektir. 

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

#### <a name="devinitjson-that-will-import-the-configurations-of-a-given-vsconfig-file-path-to-the-visual-studio-instance-specified-via-an-install-path"></a>Bunun .devinit.js, belirli bir. vsconfig dosyası yolunun yapılandırmalarını, bir install yolu ile belirtilen Visual Studio örneğine aktarır:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "comments": "A sample dot-devinit file.",
    "run": [
        {
            "tool": "require-vscomponent",
            "input": "C:\\.vsconfig",
            "additionalOptions": "--installPath 'C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Enterprise'"
        }
    ]
}
```