---
title: dotnet-toolinstall
description: devinit aracı DotNet-toolınstall.
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
ms.openlocfilehash: 464460d6a33c01e5c53b66e8a03de7aa7f844953
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399655"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will install the dotnet-trace tool.",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        },
        {
            "comments": "Example that will install the dotnet-trace tool as a global tool.",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```