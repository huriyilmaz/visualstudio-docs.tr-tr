---
title: "Nasıl yapılır: MSBuild projesi SDK 'sına başvurma | Microsoft Docs"
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
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76826477"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Nasıl yapılır: MSBuild proje SDK 'larını kullanma

MSBuild 15,0, özellik ve hedeflerin içeri aktarılmasını gerektiren yazılım geliştirme setleri kullanımını kolaylaştıran "proje SDK" kavramını sunmuştur.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Proje değerlendirmesi sırasında MSBuild, proje dosyasının en üstünde ve altında örtük içeri aktarmalar ekler:

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

## <a name="reference-a-project-sdk"></a>Proje SDK 'Sı başvurusu

Proje SDK 'sına başvurmak için üç yol vardır:

- `<Project/>` öğesindeki `Sdk` özniteliğini kullanın:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Daha önce anlatıldığı gibi projenin üst ve alt kısmına örtük bir içeri aktarma eklenir.
    
    SDK 'nın belirli bir sürümünü belirtmek için, `Sdk` özniteliğine ekleyin:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > Bu, şu anda Mac için Visual Studio bir proje SDK 'sına başvurmak için desteklenen bir yoldur.

- En üst düzey `<Sdk/>` öğesini kullanın:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Daha önce anlatıldığı gibi projenin üst ve alt kısmına örtük bir içeri aktarma eklenir.
   
   `Version` özniteliği gerekli değildir.

- `<Import/>` öğesini projenizdeki herhangi bir yerde kullanın:

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

   İçeri aktarmaların projenize açıkça dahil edilmesi, sipariş üzerinde tam denetim sağlar.

   `<Import/>` öğesi kullanılırken, isteğe bağlı bir `Version` özniteliği de belirtebilirsiniz. Örneğin, `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`belirtebilirsiniz.

## <a name="how-project-sdks-are-resolved"></a>Proje SDK 'Ları nasıl çözümlenir

İçeri aktarma değerlendirilirken, MSBuild, belirtilen adı ve sürümü temel alarak proje SDK 'sının yolunu dinamik olarak çözer.  MSBuild Ayrıca, makinenizde proje SDK 'larını belirleyen eklentiler olan kayıtlı SDK çözümleyicilerine sahiptir. Bu eklentiler şunları içerir:

- Belirttiğiniz SDK 'nın KIMLIĞI ve sürümüyle eşleşen NuGet paketleri için yapılandırılmış paket akışlarınızı sorgulayan bir NuGet tabanlı çözümleyici.

   Bu çözümleyici yalnızca isteğe bağlı bir sürüm belirttiyseniz etkindir. Bu, herhangi bir özel proje SDK 'Sı için kullanılabilir.
   
- [.Net CLI](/dotnet/core/tools/)Ile yüklenen SDK 'ları çözen BIR .net CLI Çözümleyicisi.

   Bu çözümleyici, ürünün parçası olan `Microsoft.NET.Sdk` ve `Microsoft.NET.Sdk.Web` gibi proje SDK 'larını bulur.
   
- MSBuild ile yüklenen SDK 'Ları çözen varsayılan çözümleyici.

NuGet tabanlı SDK çözümleyici, [genel. JSON](/dotnet/core/tools/global-json) dosyasındaki bir sürümü belirtmeyi destekler, bu da proje SDK sürümünü her bir proje yerine tek bir yerde denetlemenizi sağlar:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Bir derleme sırasında her bir proje SDK 'sının yalnızca bir sürümü kullanılabilir. Aynı proje SDK 'sının iki farklı sürümüne başvurdıysanız, MSBuild bir uyarı yayar. *Global. JSON* dosyasında bir sürüm belirtilmişse projelerinizde bir sürüm **belirtmemelidir** .

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Derlemenizi özelleştirme](../msbuild/customize-your-build.md)
- [Paketler, meta veriler ve çerçeveler](/dotnet/core/packages)
- [.NET Core için csproj biçimine eklemeler](/dotnet/core/tools/csproj)
