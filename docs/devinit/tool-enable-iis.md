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
ms.openlocfilehash: ec326871f5565ecaabdc8cda369b36df14029414
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399832"
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "comments": "Example that will enable IIS features and install the latest ASP.NET hosting bundle.",
            "tool": "enable-iis"
        },
    ]
}
```