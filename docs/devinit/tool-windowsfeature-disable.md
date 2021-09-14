---
title: windowsfeature-disable
description: devinit tool windowsfeature-disable.
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
ms.openlocfilehash: cd06b3a3d063a2c209a901bbed1600570c31cd8e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725335"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren, Visual Studio 2019'dan GitHub Codespaces'a bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

Araç, `windowsfeature-disable` yeni özellikler Windows kullanılır.

## <a name="usage"></a>Kullanım

| Ad                                             | Tür   | Gerekli | Değer                                                                  |
|--------------------------------------------------|--------|----------|------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                  |
| [**Giriş**](#input)                              | string | Yes      | Yük Windows özelliği. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar [için aşağıdaki](#additional-options) Ek seçeneklere bakın.       |

### <a name="input"></a>Giriş

Özelliği `input` devre dışı bırakmak için `name` `windows feature` değerine sahip olması gerekir.

### <a name="additional-options"></a>Additional-Options

Yok.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `windowsfeature-disable` gerektiğinde `input` hatadır.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `windowsfeature-disable` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-disable-a-specified-feature"></a>Belirtilen bir özelliği devre dışı bırakacak .devinit.json:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-windowsfeature",
            "input": "web-server",
        }
    ]
}
```
