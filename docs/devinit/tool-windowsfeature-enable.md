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
ms.openlocfilehash: 8cee0304f4fcca110234fb44393fad945572105000eda8d407b1ef28030275af
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378275"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`windowsfeature-enable`araç Windows özelliklerini etkinleştirmek için kullanılır.

## <a name="usage"></a>Kullanım

| Ad                                             | Tür   | Gerekli | Değer                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                    |
| [**girişinin**](#input)                              | string | Yes      | yüklenecek Windows özelliği. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.   |
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

#### <a name="devinitjson-that-will-install-the-windows-subsystem-for-linux-20"></a>.devinit.js, Linux için Windows Alt Sistemi 2,0 ' i yükleyecek:
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
