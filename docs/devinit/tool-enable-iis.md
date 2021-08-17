---
title: enable-iis
description: devinit tool enable-iis.
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
ms.openlocfilehash: 3af597ef953f98b850638cb9ad0dabe721e5692951dd961f14cc977f47214414
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390680"
---
# <a name="enable-iis"></a>enable-iis

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren Visual Studio 2019'dan GitHub Codespaces'a bağlanma desteklemeyecek ve bu özel önizleme sonuçlandırıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için Visual Studio geliştirici topluluğu forummize katılın.

Araç IIS özelliklerini etkinleştirmek ve IIS ile geliştirme `enable-iis` için [ASP.NET Core Modülünü](/aspnet/core/host-and-deploy/aspnet-core-module) ASP.NET için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak [açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                               |
| [**Giriş**](#input)                              | dize | No       | Kullanılmadı.                                                                           |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı.                                                                           |

### <a name="input"></a>Giriş

Kullanılmadı.

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `enable-iis` IIS özelliklerini etkinleştirmektir: IIS-WebServer, IIS-WebServerRole, IIS-WebSockets ve IIS-WebAuthentication ve ardından ASP.NET Core Modülünü içeren ASP.NET barındırma paketi en son sürümünü yükleyin.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırmaya bir `enable-iis` örnek `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-enable-iis-development"></a>.devinit.jsIIS geliştirmeyi etkinleştirecek olan diğer ilkeler:
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