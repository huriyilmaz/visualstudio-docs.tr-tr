---
title: vcpkg-install
description: devinit Tool vcpkg-Install.
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
ms.openlocfilehash: 5247bdd262a7c5ec2c3c7e3b77ab21f2777524d1
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442168"
---
# <a name="vcpkg-install"></a>vcpkg-install

`vcpkg-install`Araç, [vcpkg](https://github.com/microsoft/vcpkg)kullanılarak C/C++ kitaplıklarını (bağlantı noktaları olarak adlandırılır) almak için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                   |
| [**girişinin**](#input)                              | string | Evet      | Yüklenecek paket (ler). Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                       |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                        |

### <a name="input"></a>Giriş

`input`Özelliği, `name` bir `vcpkg` veya birden çok paket yüklemek için boşlukla ayrılmış adların bir listesi olmalıdır. Kullanılabilir bağlantı noktalarının listesi [vcpkg GitHub](https://github.com/microsoft/vcpkg/tree/master/ports)deposunda bulunabilir.

### <a name="additional-options"></a>Ek seçenekler

Ek seçenekler doğrudan [vcpkg](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) komutuna geçirilir ve [Vcpkg GitHub deposu](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md)'nda belgelenmiştir.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `vcpkg-install` gerekli olduğu gibi hatada yapılır `input` .

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `vcpkg-install` `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-sdl2-port"></a>.devinit.js, sdl2 bağlantı noktasını yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "vcpkg-install",
            "input": "sdl2",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-multiple-ports"></a>Birden fazla bağlantı noktası yükleyecek .devinit.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [

        {
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```