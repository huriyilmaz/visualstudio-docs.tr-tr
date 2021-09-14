---
title: dotnet-restore
description: devinit aracı DotNet-restore.
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
ms.openlocfilehash: 5beea84edce408acda7fc157f530c4a5f3253835
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725366"
---
# <a name="dotnet-restore"></a>dotnet-restore

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`dotnet-restore`Araç geri yükleme bağımlılıkları ve proje dosyasında belirtilen projeye özgü araçlar. [DotNet restore hakkında](/dotnet/core/tools/dotnet-restore)daha fazla bilgi edinin.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                                |
| [**girişinin**](#input)                              | dize | No       | Geri yüklenecek proje/çözüm dosyasının yolu. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                     |

### <a name="input"></a>Giriş

Geri yüklenecek proje/çözüm dosyasının yolu.

### <a name="additional-options"></a>Ek seçenekler

Ek seçenekler, dotnet restore komutuna olduğu gibi geçirilir.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `dotnet-restore` `dotnet restore` geçerli dizinde çalıştırılır.

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren bir örnek aşağıda verilmiştir `dotnet-restore` `.devinit.json` .

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>. devinit. JSON, bir projenin bağımlılıklarını ve araçlarını geri yükler:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-restore",
            "input": "C:\\app1\\app1.csproj"
        }
    ]
}
```