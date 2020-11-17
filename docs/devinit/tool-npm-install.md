---
title: npm-install
description: devinit aracı NPM-Install.
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
ms.openlocfilehash: 21630f5dbc80294547be33ab4a82bdf286a0b08f
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671908"
---
# <a name="npm-install"></a>npm-install

`npm-install`Araç [NPM](https://www.npmjs.com/) paketlerini yüklemek için kullanılabilir.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa araç hiçbir şey yapmaz.

| Ad                                             | Tür   | Gerekli | Değer                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                                          |
| [**girişinin**](#input)                              | string | Yes      | Yüklenecek paket. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                                                 |
| [**additionalOptions**](#additional-options)     | dize | No       | Araca geçirilecek ek seçenekler. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.       |

### <a name="input"></a>Girdi

`input`Özelliği, Yüklenecek paketin adını belirtmek için kullanılır (örneğin, ' Mongo ').

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . Bu bağımsız değişkenler [NPM yüklemesi](https://docs.npmjs.com/cli/install)tarafından kullanılan bağımsız değişkenlere doğrudan geçiş yapılır.

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren bir örnek aşağıda verilmiştir `npm-install` `.devinit.json` . 

#### <a name="devinitjson-that-will-install-mongo"></a>.devinit.js, Mongo yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "npm-install",
            "input": "mongo",
        }
    ]
}
```
