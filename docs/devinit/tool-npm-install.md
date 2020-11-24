---
title: npm-install
description: devinit aracı NPM-Install.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: c69d9464622e1814f6289c925423a6674f113a2f
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440432"
---
# <a name="npm-install"></a>npm-install

`npm-install`Araç [NPM](https://www.npmjs.com/) paketlerini yüklemek için kullanılabilir.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa araç hiçbir şey yapmaz.

| Ad                                             | Tür   | Gerekli | Değer                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                                          |
| [**girişinin**](#input)                              | dize | No       | Yüklenecek paket. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                                                 |
| [**additionalOptions**](#additional-options)     | dize | No       | Araca geçirilecek ek seçenekler. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.       |

### <a name="input"></a>Giriş

`input`Özelliği, Yüklenecek paketin adını belirtmek için kullanılır (örneğin, ' Mongo ').

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . Bu bağımsız değişkenler [NPM yüklemesi](https://docs.npmjs.com/cli/install)tarafından kullanılan bağımsız değişkenlere doğrudan geçiş yapılır.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `npm-install` `npm install` bağımsız değişken olmadan çalıştırılır. Bu davranışın açıklaması için [NPM belgelerine](https://docs.npmjs.com/cli/v6/commands/npm-install) bakın.

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
