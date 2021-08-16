---
title: require-psmodule
description: devinit aracı-psmodule gerektirir.
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
ms.openlocfilehash: 4aac45dfe7d23be35962a126fe995867cede7df9b4a27b12a6eed03bd5dbefe1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378344"
---
# <a name="require-psmodule"></a>require-psmodule

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.


`require-psmodule`Araç, PowerShell betiklerine kullanılabilmesi için [PowerShell Galerisi](https://www.powershellgallery.com/) [install-Module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true)aracılığıyla bir [PowerShell modülü](/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) yüklemek için kullanılır.

> [!TIP]
> Modül yüklendikten sonra, [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true)kullanılarak bir betiğe içeri aktarılmalıdır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                   |
| [**girişinin**](#input)                              | string | Yes      | Yüklenecek paket (ler). Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                       |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.              |

### <a name="input"></a>Giriş

`input`Özelliği, `Name` yüklemek için PowerShell modülünün bir olmalıdır. Kullanılabilir PowerShell modüllerinin listesi [PowerShell Galerisi](https://www.powershellgallery.com/)arayarak bulunabilir.

### <a name="additional-options"></a>Ek seçenekler

Ek seçenekler doğrudan [Install-Module](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7) komutuna geçirilir ve [Microsoft docs](/powershell/module/powershellget/install-module?preserve-view=true&view=powershell-7)makalesinde belgelenmiştir.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `require-psmodule` gerekli olduğu gibi hatada yapılır `input` .

### <a name="built-in-options"></a>Yerleşik Seçenekler

`require-psmodule`Araç, gözetimsiz bir şekilde `Install-Module` çalışmasını sağlamak için bir dizi komut satırı bağımsız değişkeni ayarlar `Install-Module` . Bu bağımsız değişkenler aşağıda listelenmiştir ve bunlara ilişkin belgeler [Install-Module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true)içinde bulunabilir.

| Ad         | Açıklama                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Zorla**   | Modül yükleme çakışmaları hakkında bir modül kurar ve uyarı iletilerini geçersiz kılar. Bilgisayarda aynı ada sahip bir modül zaten varsa, zorla birden çok sürümün yüklenmesine izin verir. Aynı ada ve sürüme sahip mevcut bir modül varsa modülün üzerine yazar. Zorla ve AllowClobber, Install-Module komutunda birlikte kullanılabilir. |
| **-WhatIf**  | -WhatIf bayrağı, komut için kuru çalıştırması geçirildiğinde eklenir `devinit` .                                                                                                                                                                                                                                                                                                       |
| **-Ayrıntılı** | -Verbose komutu için verbose geçirildiğinde verbose bayrağı eklenir `devinit` .                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `require-psmodule` `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-powershellget-module"></a>PowerShellGet modülünü yükleyecek .devinit.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-powershellget-module-from-a-specific-repository"></a>.devinit.js, PowerShellGet modülünü belirli bir depodan yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```