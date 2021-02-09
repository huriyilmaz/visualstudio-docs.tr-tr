---
title: windowsfeature-enable
description: devinit aracı WindowsFeature-etkinleştirin.
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
ms.openlocfilehash: b24f118613fa1004275702ad27a789ec16e6a347
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874521"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

`windowsfeature-enable`Araç, Windows özelliklerini etkinleştirmek için kullanılır.

## <a name="usage"></a>Kullanım

| Ad                                             | Tür   | Gerekli | Değer                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                    |
| [**girişinin**](#input)                              | string | Yes      | Yüklenecek Windows özelliği. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.   |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.         |

### <a name="input"></a>Giriş

`input`Özelliği, `name` `windows feature` yüklemesinin için olmalıdır. Kullanılabilir özelliklerin listesi `Get-WindowsFeature` PowerShell cmd çalıştırılarak bulunabilir.

### <a name="additional-options"></a>Additional-Options

Yok.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `windowsfeature-enable` gerekli olduğu gibi hatada yapılır `input` .

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `windowsfeature-enable` `.devinit.json` .

#### <a name="devinitjson-that-will-install-iis"></a>IIS 'nin yükleneceği .devinit.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "web-server",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework"></a>.devinit.js, .NET Framework yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework-45"></a>.devinit.js, .NET Framework 4,5 ' i yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-windows-subsystem-for-linux-20"></a>.devinit.js, Linux 2,0 için Windows alt sistemini yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
