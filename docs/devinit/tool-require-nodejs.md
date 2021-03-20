---
title: require-nodejs
description: devinit Aracı,-NodeJS gerektirir.
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
ms.openlocfilehash: 75690f85fb627140226242b476d70bfc4dac6ed2
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672305"
---
# <a name="require-nodejs"></a>require-nodejs

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

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
