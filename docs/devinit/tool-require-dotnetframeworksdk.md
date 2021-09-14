---
title: require-dotnetframeworksdk
description: devinit tool require-dotnetframeworksdk.
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
ms.openlocfilehash: 0c40ebfd2a8b665a1421ba70c0f785774e97d3df
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725345"
---
# <a name="require-dotnetframeworksdk"></a>require-dotnetframeworksdk

> [!IMPORTANT]
> 12 Nisan 2021'den itibaren, Visual Studio 2019'dan GitHub Codespaces'a bağlanmak artık desteklemeyecek ve bu özel önizlemenin sonucuna varıldı. Bulut destekli iç döngü için gelişen deneyimlere ve çok çeşitli iş yükleri için iyileştirilmiş VDI çözümlerine Visual Studio odaklanacağız. Bu ve ilişkili `devinit` araçların bir parçası olarak artık kullanılamaz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi almak Visual Studio geliştirici topluluğu forummize dahil olmak için sizi teşvik ediyoruz.

Araç, `require-dotnetframeworksdk` sağlanan yükleyiciler [aracılığıyla .NET Framework SDK'yı](https://dotnet.microsoft.com/) yüklemek [için kullanılır.](https://dotnet.microsoft.com/download/visual-studio-sdks)

## <a name="usage"></a>Kullanım

Hem hem de `input` `additionalOptions` özellikleri atlanırsa veya boşsa, araç aşağıda ayrıntılı olarak [açıklanmış varsayılan](#default-behavior) davranışı takip eder.

| Ad                                             | Tür   | Gerekli  | Değer                                                                                    |
|--------------------------------------------------|--------|-----------|------------------------------------------------------------------------------------------|
| **yorumlar**                                     | dize | No        | İsteğe bağlı açıklamalar özelliği. Kullanılmadı.                                                    |
| [**Giriş**](#input)                              | dize | No        | .NET Framework SDK'sı sürümü. Ayrıntılar [için](#input) aşağıdaki Giriş'e bakın. |
| [**additionalOptions**](#additional-options)     | dize | No        | Kullanılmadı. Ayrıntılar [için aşağıdaki](#additional-options) Ek seçeneklere bakın.               |

### <a name="input"></a>Giriş

özelliği, `input` yüklemek için .NET Framework SDK sürümünü belirtmek için kullanılır. Sürümlerin listesi [dotnet-framework sitesinde bulunabilir.](https://dotnet.microsoft.com/download/visual-studio-sdks)

### <a name="additional-options"></a>Ek seçenekler

Kullanılmadı.

### <a name="default-behavior"></a>Varsayılan davranış

Aracın varsayılan davranışı `require-dotnetframeworksdk` en son sürümü yüklemektir. En son [sürüm için sağlanan](https://dotnet.microsoft.com/download/visual-studio-sdks) yükleyicilere bakın.

## <a name="example-usage"></a>Örnek kullanım
Aşağıda, kullanarak çalıştırma örnekleri `require-dotnetframeworksdk` `.devinit.json` verilmiştir.

#### <a name="devinitjson-that-will-install-the-latest-net-framework"></a>En son sürümü yükecek .devinit.json .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-the-net-framework"></a>Uygulamanın belirli bir sürümünü yükecek .devinit.json .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk",
            "input": "4.8.0"
        }
    ]
}
```