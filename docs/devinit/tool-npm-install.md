---
title: npm-install
description: devinit tool npm-install.
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
ms.openlocfilehash: 011364e851670362ecaa9f4bdbfff965782ed706
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725357"
---
# <a name="npm-install"></a>npm-install

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren, Visual Studio 2019'dan GitHub Codespaces'a bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

Araç, `npm-install` [NPM](https://www.npmjs.com/) paketlerini yüklemek için kullanılabilir.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa araç hiçbir şey yapmaz.

| Ad                                             | Tür   | Gerekli | Değer                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                                                          |
| [**Giriş**](#input)                              | dize | No       | Yüklenilen paket. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın.                                                 |
| [**additionalOptions**](#additional-options)     | dize | No       | Araç için ek geçiş seçenekleri. Ayrıntılar [için aşağıdaki](#additional-options) Ek seçeneklere bakın.       |

### <a name="input"></a>Giriş

`input`özelliği, yüklemek için paketin adını belirtmek için kullanılır (örneğin, 'mongo').

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri değeri olarak `additionalOptions` geçirebilirsiniz. Bu bağımsız [değişkenler, npm install](https://docs.npmjs.com/cli/install)tarafından kullanılan bağımsız değişkenlere doğrudan geçiştir.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan `npm-install` davranışı, bağımsız değişken `npm install` kullanarak çalıştırmaktır. Bu [davranışın açıklaması için npm](https://docs.npmjs.com/cli/v6/commands/npm-install) belgelerine bakın.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `npm-install` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-install-mongo"></a>Mongo'nun yüklnln.devinit.json sürümü:
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
