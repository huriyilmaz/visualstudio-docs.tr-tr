---
title: require-dotnetframeworksdk
description: devinit Aracı,-dotnetframeworksdk gerektirir.
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
ms.openlocfilehash: 5a4d68119ceb21553d7db1f6384904579003ce92
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99937153"
---
# <a name="require-dotnetframeworksdk"></a>require-dotnetframeworksdk

`require-dotnetframeworksdk`Araç, [.NET Framework SDK 'sını](https://dotnet.microsoft.com/) , [belirtilen yükleyiciler](https://dotnet.microsoft.com/download/visual-studio-sdks)aracılığıyla yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli  | Değer                                                                                    |
|--------------------------------------------------|--------|-----------|------------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No        | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                    |
| [**girişinin**](#input)                              | dize | No        | Yüklenecek .NET Framework SDK sürümü. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No        | Kullanılmadı. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.               |

### <a name="input"></a>Giriş

`input`Özelliği, yüklenecek .NET Framework SDK sürümünü belirtmek için kullanılır. [DotNet Framework sitesinde](https://dotnet.microsoft.com/download/visual-studio-sdks)sürümlerin bir listesini bulabilirsiniz.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `require-dotnetframeworksdk` en son sürümü yüklemektir. En son sürüm için [sunulan yükleyicilere](https://dotnet.microsoft.com/download/visual-studio-sdks) bakın.

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `require-dotnetframeworksdk` `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-latest-net-framework"></a>En son .NET Framework yükleyecek .devinit.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-the-net-framework"></a>.devinit.js, .NET Framework belirli bir sürümünü yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk",
            "input": "4.8.0"
        }
    ]
}
```