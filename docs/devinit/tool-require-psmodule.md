---
title: require-psmodule
description: devinit aracı-psmodule gerektirir.
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
ms.openlocfilehash: 4e30a333812e2c313f9e35934643bcea03cf054c
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91352237"
---
# <a name="require-psmodule"></a>require-psmodule

`require-psmodule`Araç, PowerShell betiklerine kullanılabilmesi için [PowerShell Galerisi](https://www.powershellgallery.com/) [install-Module](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true)aracılığıyla bir [PowerShell modülü](https://docs.microsoft.com/powershell/scripting/developer/module/understanding-a-windows-powershell-module?view=powershell-7&preserve-view=true) yüklemek için kullanılır.

> [!TIP] 
> Modül yüklendikten sonra, [Import-Module](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7&preserve-view=true)kullanılarak bir betiğe içeri aktarılmalıdır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                   |
| [**girişinin**](#input)                              | string | Yes      | Yüklenecek paket (ler). Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                       |
| [**additionalOptions**](#additional-options)     | dize | No       | Kullanılmadı. Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.              |

### <a name="input"></a>Giriş

`input`Özelliği, `Name` yüklemek için PowerShell modülünün bir olmalıdır. Kullanılabilir PowerShell modüllerinin listesi [PowerShell Galerisi](https://www.powershellgallery.com/)arayarak bulunabilir.

### <a name="additional-options"></a>Ek seçenekler

Ek seçenekler doğrudan [Install-Module](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) komutuna geçirilir ve [Microsoft docs](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true)makalesinde belgelenmiştir.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `require-psmodule` gerekli olduğu gibi hatada yapılır `input` .

## <a name="builtin-options"></a>Yerleşik Seçenekler

`require-psmodule`Araç, gözetimsiz bir şekilde `Install-Module` çalışmasını sağlamak için bir dizi komut satırı bağımsız değişkeni ayarlar `Install-Module` . Bu bağımsız değişkenler aşağıda listelenmiştir ve bunlara ilişkin belgeler [Install-Module](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true)içinde bulunabilir.

| Ad         | Açıklama                                                                                                                                                                                                                                                                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **-Force**   | Modül yükleme çakışmaları hakkında bir modül kurar ve uyarı iletilerini geçersiz kılar. Bilgisayarda aynı ada sahip bir modül zaten varsa, zorla birden çok sürümün yüklenmesine izin verir. Aynı ada ve sürüme sahip mevcut bir modül varsa modülün üzerine yazar. Zorla ve AllowClobber, bir Install-Module komutunda birlikte kullanılabilir. |
| **-WhatIf**  | -WhatIf bayrağı, komut için kuru çalıştırması geçirildiğinde eklenir `devinit` .                                                                                                                                                                                                                                                                                                       |
| **-Ayrıntılı** | -Verbose komutu için verbose geçirildiğinde verbose bayrağı eklenir `devinit` .                                                                                                                                                                                                                                                                                                      |


## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the PowerShellGet module.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
        },
        {
            "comments": "Installs the PowerShellGet module from a specific repository.",
            "tool": "require-psmodule",
            "input": "PowerShellGet",
            "additionalOptions": "-Repository PSGallery"
        }
    ]
}
```
