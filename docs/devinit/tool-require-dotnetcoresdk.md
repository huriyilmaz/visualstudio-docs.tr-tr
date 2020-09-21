---
title: gerektir-dotnetcoresdk
description: devinit aracı gerekli-dotnetcoresdk.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: cf68889b9dbac39031a4a79fbe799dc02fc8e419
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809695"
---
# <a name="require-dotnetcoresdk"></a>gerektir-dotnetcoresdk

`require-dotnetcoresdk`Araç, [DotNet-install](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) betiği aracılığıyla [.NET Core SDK](https://dotnet.microsoft.com/) ve paylaşılan çalışma zamanını yüklemek için kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak açıklanan [varsayılan](#default-behavior) davranışı izler.

| Ad                                             | Tür   | Gerekli | Değer                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **açıklamaları**                                     | dize | No       | İsteğe bağlı Yorumlar özelliği. Kullanılmadı.                                               |
| [**girişinin**](#input)                              | dize | No       | Yüklenecek .NET Core SDK sürümü. Ayrıntılar için aşağıdaki [girişi](#input) inceleyin. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar için aşağıdaki [ek seçeneklere](#additional-options) bakın.                    |

### <a name="input"></a>Giriş

`input`Özelliği, yüklenecek .NET Core SDK sürümünü belirtmek için kullanılır. [DotNet-Core sitesinde](https://dotnet.microsoft.com/download/dotnet-core)sürümlerin bir listesi bulunabilir.

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri ' ın bir değeri olarak geçirilebilir `additionalOptions` . Bu bağımsız değişkenler, [DotNet-install](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) betikte kullanılan bağımsız değişkenlere doğrudan geçiş yapılır. Kullanılabilir parametreler hakkında daha fazla bilgi için, [DotNet-Install](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) betiğine yönelik [belgelere](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) bakın. Kullanırken `additionalOptions` , PowerShell bağımsız değişken adlarını ve biçimini kullandığınızdan emin olun.

Note: bir boşluk içeren bir bağımsız değişkene herhangi bir ek değer, ek bir kaçan tırnak işareti (ters eğik çizgi kullanılarak) içermelidir. Örneği kullanılarak [Örnek kullanım](#example-usage) halinde görünebilirler `-InstallDir` .

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı, `require-dotnetcoresdk` `global.json` geçerli çalışma dizinindeki bir [(belgeler)](https://docs.microsoft.com/dotnet/core/tools/global-json?tabs=netcore3x) dosyasında belirtilen .NET Core SDK sürümünü yüklemektir. `global.json`Dosya bulunamazsa, `require-dotnetcoresdk` .NET Core SDK ve paylaşılan çalışma zamanının en güncel sürümünü yükler.

## <a name="example-usage"></a>Örnek kullanım

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest or, if present, the SDK version from a global.json file.",
            "tool": "require-dotnetcoresdk"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        },
        {
            "comments": "Example that will install a specific version and the aspnetcore runtime.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        },
        {
            "comments": "Example that will install in a specific directory.",
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\Program Files\dotnet\""
        }
    ]
}
```
