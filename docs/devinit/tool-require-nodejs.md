---
title: gerektir-NodeJS
description: devinit Aracı,-NodeJS gerektirir.
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
ms.openlocfilehash: 6bc2de2e497bd58cfc036e74af3968a2f70d1f52
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808420"
---
# <a name="require-nodejs"></a>gerektir-NodeJS

`require-nodejs`Araç, Node.js kuruluş tarafından dağıtılan BIR MSI aracılığıyla [Node.js](https://nodejs.org/) yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                     |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                     |
| [**girişinin**](#input)                              | dize | No       | Yüklenecek Node.JS sürümü. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.          |

### <a name="input"></a>Giriş

`input`Özelliği, Node.js sürümünü belirtmek için kullanılır. [Node.js indirme sayfasında](https://nodejs.org/en/download/)sürümlerin listesini bulabilirsiniz. Tam sürüm numarası gereklidir. Ikincil. yol (örneğin 14.4.0) varsa, yükleme başarısız olur.

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . Bu bağımsız değişkenler, Node.js için doğrudan MSI yükleyicisine PASSTHROUGH.  

### <a name="default-behavior"></a>Varsayılan davranış

Aracının varsayılan davranışı, `require-nodejs` Node.JS [Web sitesinde](https://nodejs.org/en/download/)açıklandığı gibi, düğümün en son LTS sürümünü yüklemektir.

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest LTS of Node.JS.",
            "tool": "require-nodejs"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
