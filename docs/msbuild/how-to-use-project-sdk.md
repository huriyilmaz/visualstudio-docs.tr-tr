---
title: Nasıl MSBuild Project SDK | Microsoft Docs
description: Özelliklerin ve hedeflerin MSBuild yazılım geliştirme setlerinin kullanımını basitleştirmek için proje SDK'lerini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: b26c8704be6770954849a440f15683be68ce82aa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069170"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Nasıllı: MSBuild PROJE SDK'lerini kullanma

MSBuild 15.0'da, özelliklerin ve hedeflerin içe aktarılmış olması gereken yazılım geliştirme setlerinin kullanımı kolaylaştıran "proje SDK'sı" kavramı tanıtıldı.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Projenin değerlendirmesi sırasında MSBuild dosyanın üst ve alt kısmında örtülü içeri aktarmalar ekler:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

## <a name="reference-a-project-sdk"></a>Proje SDK'sı başvurusu

Bir proje SDK'sı için üç yol vardır:

- öğesinde `Sdk` özniteliğini `<Project/>` kullanın:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Daha önce tartıştığımız gibi projenin üst ve alt kısmında örtülü bir içeri aktarma eklenir.
    
    SDK'nın belirli bir sürümünü belirtmek için özniteliğine `Sdk` bunu ekleme:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

- Üst düzey öğesini `<Sdk/>` kullanın:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Daha önce tartıştığımız gibi projenin üst ve alt kısmında örtülü bir içeri aktarma eklenir.
   
   `Version`özniteliği gerekli değildir.

- öğesini `<Import/>` projenizin herhangi bir yerinde kullanın:

    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```

   İçeri aktarmaları projenize açıkça dahil etmek, sipariş üzerinde tam denetime sahip olur.

   öğesini `<Import/>` kullanırken, isteğe bağlı bir öznitelik `Version` de belirtebilirsiniz. Örneğin, `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />` belirtesiniz.

## <a name="how-project-sdks-are-resolved"></a>Proje SDK'ları nasıl çözümlenir?

İçeri aktarmayı değerlendirirken MSBuild proje SDK'sı yolunu belirttiğiniz ad ve sürüme göre dinamik olarak çözümler.  MSBuild, makineniz üzerinde proje SDK'larını bulan eklentiler olan kayıtlı SDK çözümleyicilerinin bir listesine de sahip olur. Bu eklentiler şunları içerir:

- Yapılandırılan NuGet, belirttiğiniz SDK kimliği ve sürümüyle NuGet paketleri için yapılandırılan paket akışlarınızı sorguleyen bir çözümleyici.

   Bu çözümleyici yalnızca isteğe bağlı bir sürüm belirttiysteğe bağlı olarak etkindir. Herhangi bir özel proje SDK'sı için kullanılabilir.
   
- .NET SDK ile yüklü MSBuild SDK'ları çözümleye bir .NET SDK [çözümleyicisi.](/dotnet/core/sdk/)

   Bu çözümleyici, ürünün parçası olan ve gibi `Microsoft.NET.Sdk` `Microsoft.NET.Sdk.Web` proje SDK'lerini bularak.
   
- Birlikte yüklenmiş OLAN SDK'ları çözümleen varsayılan çözümleyici MSBuild.

NuGet SDK çözümleyicisi, [global.json](/dotnet/core/tools/global-json) dosyasında bir sürüm belirtmeyi destekler; böylece proje SDK'sı sürümünü tek tek proje yerine tek bir yerde denetlemenize olanak sağlar:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Derleme sırasında her proje SDK'sı yalnızca bir sürümü kullanılabilir. Aynı proje SDK'sı için iki farklı sürüme başvurursanız MSBuild uyarı verir. Dosyanın **dosyasındaki** dosyada bir sürüm belirtilirse projelerinize bir sürüm *global.jsönerilir.*

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Derlemenizi özelleştirme](../msbuild/customize-your-build.md)
- [Paketler, meta veriler ve çerçeveler](/dotnet/core/packages)
- [.NET Core için csproj biçimine eklemeler](/dotnet/core/tools/csproj)
