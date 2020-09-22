---
title: require-dotnetframeworksdk
description: devinit Aracı,-dotnetframeworksdk gerektirir.
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
ms.openlocfilehash: 4de8daf4b57d4775e4f1ede57392bb594bae53ea
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005112"
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install a specific version of the .NET Framework SDK.",
            "tool": "require-dotnetframeworksdk",
            "input": "4.8.0"
        },
        {
            "comments": "Example that will install the latest version of the .NET Framework SDK.",
            "tool": "require-dotnetframeworksdk"
        }
    ]
}
```
