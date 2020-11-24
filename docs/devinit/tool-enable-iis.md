---
title: enable-iis
description: devinit aracı Enable-IIS.
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
ms.openlocfilehash: b4b7c3f9681dd636ef88a5cd9f59c84c4ecac89c
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440363"
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

### <a name="input"></a>Giriş

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