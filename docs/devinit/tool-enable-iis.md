---
title: enable-iis
description: devinit aracı Enable-IIS.
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
ms.openlocfilehash: eecdc2a020117b7345682068cb27509df805ff9b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725367"
---
# <a name="enable-iis"></a>enable-iis

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

araç, ııs `enable-iis` özelliklerini etkinleştirmek ve ııs ile ASP.NET geliştirmeye yönelik [ASP.NET Core modülünü](/aspnet/core/host-and-deploy/aspnet-core-module) yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                               |
| [**girişinin**](#input)                              | dize | No       | Kullanılmadı.                                                                           |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı.                                                                           |

### <a name="input"></a>Giriş

Kullanılmadı.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

aracın varsayılan davranışı `enable-iis` ııs özelliklerini etkinleştirmektir: ııs-websunucusu, ııs-WebServerRole, ııs-WebSockets ve ııs-WebAuthentication ve sonra ASP.NET Core modülünü içeren ASP.NET barındırma paketinin en son sürümünü yükler.

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren bir örnek aşağıda verilmiştir `enable-iis` `.devinit.json` .

#### <a name="devinitjson-that-will-enable-iis-development"></a>IIS geliştirmeyi etkinleştirecek. devinit. JSON:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "enable-iis"
        },
    ]
}
```