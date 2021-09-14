---
title: vcpkg-install
description: devinit aracı vcpkg-ınstall.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725344"
---
# <a name="vcpkg-install"></a>vcpkg-install

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`vcpkg-install`Araç, [Vcpkg](https://github.com/microsoft/vcpkg)kullanılarak C/C++ kitaplıklarını (bağlantı noktaları olarak adlandırılır) almak için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                   |
| [**girişinin**](#input)                              | string | Yes      | Yüklenecek paket (ler). Ayrıntılar için aşağıdaki [girişi](#input) inceleyin.                       |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                        |

### <a name="input"></a>Giriş

`input`Özelliği, `name` bir `vcpkg` veya birden çok paket yüklemek için boşlukla ayrılmış adların bir listesi olmalıdır. kullanılabilir bağlantı noktalarının listesi, [vcpkg GitHub](https://github.com/microsoft/vcpkg/tree/master/ports)deposunda bulunabilir.

### <a name="additional-options"></a>Ek seçenekler

ek seçenekler doğrudan [vcpkg](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) komutuna geçirilir ve [vcpkg GitHub](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md)deposunda belgelenmiştir.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `vcpkg-install` gerekli olduğu gibi hatada yapılır `input` .

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `vcpkg-install` `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-sdl2-port"></a>sdl2 bağlantı noktasını yükleyecek. devinit. JSON:
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

#### <a name="devinitjson-that-will-install-multiple-ports"></a>birden çok bağlantı noktası yükleyecek. devinit. JSON:
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