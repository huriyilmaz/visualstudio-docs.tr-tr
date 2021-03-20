---
title: vcpkg-install
description: devinit Tool vcpkg-Install.
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
ms.openlocfilehash: 8a4cbe6bd1da12985da87d2f872dc74f988ef213
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672654"
---
# <a name="vcpkg-install"></a>vcpkg-install

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`vcpkg-install`Araç, [vcpkg](https://github.com/microsoft/vcpkg)kullanılarak C/C++ kitaplıklarını (bağlantı noktaları olarak adlandırılır) almak için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                   |
| [**girişinin**](#input)                              | string | Yes      | Yüklenecek paket (ler). Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                       |
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