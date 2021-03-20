---
title: dotnet-toolinstall
description: devinit aracı DotNet-toolınstall.
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
ms.openlocfilehash: 4daa3722abd169c03656adec39aafc29d5e7e435
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104671639"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`dotnet-toolinstall`Araç, [.NET Core araçları](https://dotnet.microsoft.com/) 'nı komut aracılığıyla yüklemek için kullanılır `dotnet tool update` .

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                 |
| [**girişinin**](#input)                              | string | Yes      | Yüklenecek .NET Core aracı. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.      |

### <a name="input"></a>Giriş

`input`Özelliği, yüklenecek .NET Core aracını belirtmek için kullanılır. Adresinden resmi olmayan bir araç listesinde bulunur [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) .

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . Bu bağımsız değişkenler, komut tarafından kullanılan bağımsız değişkenlere doğrudan geçiş yapılır [`dotnet tool update`](/dotnet/core/tools/global-tools#update-a-tool) .

`dotnet tool update`Komut, bir aracın zaten yüklü olduğu durumu güvenli bir şekilde işlemek için kullanılır.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `dotnet-toolinstall` gerekli olduğu gibi hatada yapılır `input` .

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `dotnet-toolinstall` `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool"></a>DotNet-Trace aracını yükleyecek olan .devinit.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool-as-a-global-tool"></a>Bunun .devinit.js, DotNet-Trace aracını genel araç olarak yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```