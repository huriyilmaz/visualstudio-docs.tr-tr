---
title: require-nuget
description: devinit Aracı,-NuGet gerektirir.
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
ms.openlocfilehash: ef5de2d8358dae0f5f29b815cfa2dca26a3f1cef
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005178"
---
# <a name="require-nuget"></a>require-nuget

`require-nuget`NUGET CLI indirme ve yol değişkenine ekleme aracı. NuGet CLı, proje dosyalarında değişiklik yapmadan paketleri yüklemek, oluşturmak, yayımlamak ve yönetmek için NuGet işlevlerinin tam kapsamını sağlar. NuGet CLı hakkında [buradan](https://docs.microsoft.com/nuget/reference/nuget-exe-cli-reference)daha fazla bilgi edinin.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                |
| [**girişinin**](#input)                              | dize | No       | Yüklenecek NuGet CLı sürümü. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                     |

### <a name="input"></a>Giriş

, `input` Yüklenecek NUGET CLI sürümü için kullanılan isteğe bağlı bir özelliktir. `input`Atlanırsa, en son CLI sürümü yüklenir.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `require-nuget` NUGET CLI 'nın en son sürümünü yüklemektir.

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that downloads NuGet CLI and adds to PATH variable.'",
    "run": [
        {
            "tool": "require-nuget",
            "input": "5.5.1",
            "comments": "Installs NuGet for given input version. If no input given, then installs latest."
        }
    ]
}
```
