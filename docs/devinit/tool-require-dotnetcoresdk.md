---
title: require-dotnetcoresdk
description: devinit aracı gerekli-dotnetcoresdk.
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
ms.openlocfilehash: d3c73ed7b7c463226e49dcf29bc80a7ffec9e677d017442e501cb13620f2baa7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390543"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

> [!IMPORTANT]
> 12 nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş vdı çözümleri için gelişen deneyimler üzerinde odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi edinmek için Visual Studio geliştirici topluluğu forumumuza dahil etmeniz önerilir.

`require-dotnetcoresdk`Araç, [DotNet-install](/dotnet/core/tools/dotnet-install-script) betiği aracılığıyla [.NET Core SDK](https://dotnet.microsoft.com/) ve paylaşılan çalışma zamanını yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                               |
| [**girişinin**](#input)                              | dize | No       | Yüklenecek .NET Core SDK sürümü. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                    |

### <a name="input"></a>Giriş

`input`Özelliği, yüklenecek .NET Core SDK sürümünü belirtmek için kullanılır. [DotNet-Core sitesinde](https://dotnet.microsoft.com/download/dotnet-core)sürümlerin bir listesi bulunabilir.

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . Bu bağımsız değişkenler, [DotNet-install](/dotnet/core/tools/dotnet-install-script) betikte kullanılan bağımsız değişkenlere doğrudan geçiş yapılır. Kullanılabilir parametreler hakkında daha fazla bilgi için, [DotNet-Install](/dotnet/core/tools/dotnet-install-script) betiğine yönelik [belgelere](/dotnet/core/tools/dotnet-install-script) bakın. Kullanırken `additionalOptions` , PowerShell bağımsız değişken adlarını ve biçimini kullandığınızdan emin olun.

> [!NOTE]
> Boşluk içeren bir bağımsız değişkene herhangi bir ek değer, ek bir kaçan tırnak işareti (ters eğik çizgi kullanılarak) içermelidir. Örneği kullanılarak [Örnek kullanım](#example-usage) halinde görünebilirler `-InstallDir` .

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `require-dotnetcoresdk` `global.json` geçerli çalışma dizinindeki bir [(belgeler)](/dotnet/core/tools/global-json?tabs=netcore3x) dosyasında belirtilen .NET Core SDK sürümünü yüklemektir. `global.json`Dosya bulunamazsa, `require-dotnetcoresdk` .NET Core SDK ve paylaşılan çalışma zamanının en güncel sürümünü yükler.

## <a name="example-usage"></a>Örnek kullanım
Kullanarak nasıl çalıştırılacağını gösteren örnekler aşağıda verilmiştir `require-dotnetcoresdk` `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-latest-version-of-net-core"></a>.NET Core 'un en son sürümünü yükleyecek .devinit.js.
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core"></a>.devinit.js, .NET Core 'un belirli bir sürümünü yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core-and-aspnet-core"></a>.devinit.js, .NET Core 'un belirli bir sürümünü yükleyecek ve ASP.NET Core:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-net-core-in-a-specific-directory"></a>.devinit.js, .NET Core 'u belirli bir dizine yükleyecek:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```