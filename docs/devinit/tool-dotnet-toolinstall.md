---
title: dotnet-toolinstall
description: dotnet-tostall devinit aracı.
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
ms.openlocfilehash: 609add9096932296e657f7b065f4fae33d470bc9c67a2e3ab4394246c6d0e74d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343204"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren, Visual Studio 2019'dan GitHub Codespaces'a bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

Araç, `dotnet-toolinstall` komutuyla [.NET Core Araçları'nı yüklemek](https://dotnet.microsoft.com/) için `dotnet tool update` kullanılır.

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı [olarak açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli | Değer                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **yorumlar**                                     | dize | No       | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                 |
| [**Giriş**](#input)                              | string | Yes      | Yüklemek için .NET Core aracı. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın. |
| [**additionalOptions**](#additional-options)     | dize | No       | Ayrıntılar [için aşağıdaki](#additional-options) Ek seçenekler'e bakın.      |

### <a name="input"></a>Giriş

özelliği, `input` yüklemek için .NET Core aracını belirtmek için kullanılır. 'de resmi olmayan bir araç listesi [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) vardır.

### <a name="additional-options"></a>Ek seçenekler

Ek yapılandırma seçenekleri değeri olarak `additionalOptions` geçirebilirsiniz. Bu bağımsız değişkenler, komutu tarafından kullanılan bağımsız değişkenlere doğrudan [`dotnet tool update`](/dotnet/core/tools/global-tools#update-a-tool) geçiştir.

komutu, `dotnet tool update` bir aracın zaten yüklü olduğu durumu güvenli bir şekilde işlemek için kullanılır.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `dotnet-toolinstall` gerektiğinde `input` hatadır.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırma örnekleri `dotnet-toolinstall` `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool"></a>.devinit.jsdotnet-trace aracını yüklemesi gerekir:
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

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool-as-a-global-tool"></a>.devinit.js, dotnet-trace aracını genel bir araç olarak yükleyecek:
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