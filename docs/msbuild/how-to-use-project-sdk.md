---
title: 'Nasıl: Başvuru bir MSBuild Proje SDK | Microsoft Dokümanlar'
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74ccc29417cdee7a9f93c39509c0f7d06a5c72ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76826477"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Nasıl kullanılır: MSBuild proje SDK'larını kullanma

MSBuild 15.0, alınan özellikleri ve hedefleri gerektiren yazılım geliştirme kitlerini kullanarak basitleştiren "Proje SDK" kavramını tanıttı.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Projenin değerlendirilmesi sırasında, MSBuild proje dosyasının üst ve alt kısmında örtülü içeri aktarımekler:

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

## <a name="reference-a-project-sdk"></a>Başvuru bir proje SDK

Bir proje SDK başvuru için üç yolu vardır:

- `<Project/>` Öğedeki `Sdk` özniteliği kullanın:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Daha önce tartışıldığı gibi projenin üst ve alt bölümüne örtülü bir alma eklenir.
    
    SDK'nın belirli bir sürümünü belirtmek için, `Sdk` özniteliğe ekle:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > Bu şu anda Mac için Visual Studio bir proje SDK başvuru için tek desteklenen yoludur.

- Üst düzey `<Sdk/>` öğeyi kullanın:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Daha önce tartışıldığı gibi projenin üst ve alt bölümüne örtülü bir alma eklenir.
   
   Öznitelik `Version` gerekli değildir.

- Öğeyi `<Import/>` projenizde herhangi bir yerde kullanın:

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

   Projenize içeri almalar dahil olmak üzere, sipariş üzerinde tam kontrol sağlar.

   Öğeyi `<Import/>` kullanırken, isteğe `Version` bağlı bir öznitelik de belirtebilirsiniz. Örneğin, belirtebilirsiniz. `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`

## <a name="how-project-sdks-are-resolved"></a>Proje SDK'ları nasıl çözülür?

Alma alma değerlendirirken, MSBuild dinamik olarak proje SDK için yol belirlediğiniz ada ve sürümü dayalı çözer.  MSBuild ayrıca, makinenizde proje SDK'larını bulunan eklentiler olan kayıtlı SDK çözümleyicilerinin bir listesine de sahiptir. Bu eklentiler şunlardır:

- Belirttiğiniz SDK'nın kimliği ve sürümüyle eşleşen NuGet paketleri için yapılandırılmış paket akışlarınızı sorgulayan NuGet tabanlı çözümleyici.

   Bu çözümleyici yalnızca isteğe bağlı bir sürüm belirttiyseniz etkindir. Herhangi bir özel proje SDK için kullanılabilir.
   
- .NET CLI ile yüklü Olan SDK'ları çözen [bir .NET CLI](/dotnet/core/tools/)çözümleyicisi.

   Bu çözümleyici, ürünün bir parçası `Microsoft.NET.Sdk` olan `Microsoft.NET.Sdk.Web` proje SDK'larını bulur.
   
- MSBuild ile yüklenen SDK'ları çözen varsayılan çözümleyici.

NuGet tabanlı SDK çözümleyicisi, [global.json](/dotnet/core/tools/global-json) dosyasında bir sürümün belirtilmesine destek verir ve bu da proje SDK sürümünü her projeyerine tek bir yerde kontrol etmenizi sağlar:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Her proje SDK'nın yalnızca bir sürümü yapı sırasında kullanılabilir. Aynı proje SDK'nın iki farklı sürümüne başvurursanız, MSBuild bir uyarı yatar. *Global.json* dosyasında bir sürüm belirtilmişse, projelerinizde bir sürüm **belirtmemeniz** önerilir.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Derlemenizi özelleştirme](../msbuild/customize-your-build.md)
- [Paketler, meta veriler ve çerçeveler](/dotnet/core/packages)
- [.NET Core için csproj formatına eklemeler](/dotnet/core/tools/csproj)
