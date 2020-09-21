---
title: gerektir-gitsubmodule
description: devinit Aracı,-gitsubmodule gerektirir.
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
ms.openlocfilehash: fc96c1d0bf278018c370795d6ad5f9d22cb59bcc
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810132"
---
# <a name="require-gitsubmodule"></a>gerektir-gitsubmodule

`require-gitsubmodule`Araç, belirtilen dosya Için Git alt modüllerini geri yükler `.gitmodules` . `.gitmodules`Hiçbir giriş geçirilmemişse, kök dizinde yerel dosyayı kullanır. Git alt modülleri hakkında [buradan](https://git-scm.com/book/en/v2/Git-Tools-Submodules)daha fazla bilgi edinin.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                |
| [**girişinin**](#input)                              | dize | No       | `.gitmodules` dosya tam yolu. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.               |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                     |

### <a name="input"></a>Giriş

İsteğe bağlı, `input` `.gitmodules` geri yükleme için dosya yolunu almak için kullanılır. `input`Atlanırsa, kök dizin `.gitmodules` dosyası kullanılır.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `require-gitsubmodule` dosyasında belirtilen git alt modüllerini geri yüklemektir `.gitmodules` .

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that restores Git submodules.'",
    "run": [
        {
            "tool": "require-gitsubmodule",
            "input": "RepoThatHasDotGitModulesFile",
            "comments": "Input specifies a folder that contains a .gitmodules file. If no input is specified, then current directory is used."
        }
    ]
}
```
