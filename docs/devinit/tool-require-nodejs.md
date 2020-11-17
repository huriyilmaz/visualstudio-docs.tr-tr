---
title: require-nodejs
description: devinit Aracı,-NodeJS gerektirir.
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
ms.openlocfilehash: 3da6bd121aff31c680bea2c4655ee2250f5edb05
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671789"
---
# <a name="require-nodejs"></a>require-nodejs

`require-nodejs`Araç, Node.js kuruluş tarafından dağıtılan BIR MSI aracılığıyla [Node.js](https://nodejs.org/) yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                     |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                     |
| [**girişinin**](#input)                              | dize | No       | Yüklenecek Node.JS sürümü. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.          |

### <a name="input"></a>Girdi

`input`Özelliği, Node.js sürümünü belirtmek için kullanılır. [Node.js indirme sayfasında](https://nodejs.org/en/download/)sürümlerin listesini bulabilirsiniz. Tam sürüm numarası gereklidir. Ikincil. yol (örneğin 14.4.0) varsa, yükleme başarısız olur.

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . Bu bağımsız değişkenler, Node.js için doğrudan MSI yükleyicisine PASSTHROUGH.  

### <a name="default-behavior"></a>Varsayılan davranış

Aracının varsayılan davranışı, `require-nodejs` Node.JS [Web sitesinde](https://nodejs.org/en/download/)açıklandığı gibi, düğümün en son LTS sürümünü yüklemektir.

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `require-nodejs` `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-lts-of-nodejs"></a>.devinit.js, Node.js LTS 'leri yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-nodejs"></a>.devinit.js, Node.js belirli bir sürümünü yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
