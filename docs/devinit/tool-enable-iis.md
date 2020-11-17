---
title: enable-iis
description: devinit aracı Enable-IIS.
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
ms.openlocfilehash: 9b6ba2e22484850dd6079cfc7e4ab9cd68371dcb
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671928"
---
# <a name="enable-iis"></a>enable-iis

Araç, IIS `enable-iis` özelliklerini etkinleştirmek ve IIS ile ASP.net geliştirmesi için [ASP.NET Core modülünü](/aspnet/core/host-and-deploy/aspnet-core-module) yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                               |
| [**girişinin**](#input)                              | dize | No       | Kullanılmadı.                                                                           |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı.                                                                           |

### <a name="input"></a>Girdi

Kullanılmadı.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `enable-iis` IIS özelliklerini etkinleştirmektir: IIS-WebSunucusu, IIS-WebServerRole, IIS-WebSockets ve IIS-WebAuthentication ve ardından ASP.NET Core modülünü içeren ASP.NET barındırma paketinin en son sürümünü yükler. 

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren bir örnek aşağıda verilmiştir `enable-iis` `.devinit.json` . 

#### <a name="devinitjson-that-will-enable-iis-development"></a>.devinit.js, IIS geliştirmeyi etkinleştirecek:
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