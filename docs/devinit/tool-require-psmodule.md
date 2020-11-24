---
title: require-psmodule
description: devinit aracı-psmodule gerektirir.
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
ms.openlocfilehash: c8c87e6df0e7ea66c2413f85fa39f397f30d50a7
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440006"
---
# <a name="require-psmodule"></a>require-psmodule

`require-psmodule`Araç, PowerShell betiklerine kullanılabilmesi için [PowerShell Galerisi](https://www.powershellgallery.com/) [install-Module](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true)aracılığıyla bir [PowerShell modülü](/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) yüklemek için kullanılır.

> [!TIP]
> Modül yüklendikten sonra, [Import-Module](/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true)kullanılarak bir betiğe içeri aktarılmalıdır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                   |
| [**girişinin**](#input)                              | string | Evet      | Yüklenecek paket (ler). Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                       |
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
| **-Force**   | Modül yükleme çakışmaları hakkında bir modül kurar ve uyarı iletilerini geçersiz kılar. Bilgisayarda aynı ada sahip bir modül zaten varsa, zorla birden çok sürümün yüklenmesine izin verir. Aynı ada ve sürüme sahip mevcut bir modül varsa modülün üzerine yazar. Zorla ve AllowClobber, Install-Module komutunda birlikte kullanılabilir. |
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