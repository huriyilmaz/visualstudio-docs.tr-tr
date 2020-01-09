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
ms.openlocfilehash: d40e437763ba3eb75daa80a3a1bbf55ba9d896c9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75574463"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Nasıl yapılır: MSBuild proje SDK 'larını kullanma

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 15,0 "proje SDK" kavramını ortaya sunmuştur ve bu özellik ve hedeflerin içeri aktarılmasını gerektiren yazılım geliştirme setleri kullanımını basitleştirir.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Projenin değerlendirmesi sırasında, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projenizin üst ve alt kısmına örtük içeri aktarmalar ekler:

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

1. `<Project/>` öğesindeki `Sdk` özniteliğini kullanın:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Bir örtük içeri aktarma, yukarıda açıklandığı gibi projenin üst ve alt kısmına eklenir.
    
    SDK 'nın belirli bir sürümünü belirtmek için onu `Sdk` özniteliğine ekleyebilirsiniz:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > Bu, şu anda Mac için Visual Studio bir proje SDK 'sına başvurmak için desteklenen bir yoldur.

2. En üst düzey `<Sdk/>` öğesini kullanın:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Bir örtük içeri aktarma, yukarıda açıklandığı gibi projenin üst ve alt kısmına eklenir.  `Version` özniteliği gerekli değildir.

3. `<Import/>` öğesini projenizdeki herhangi bir yerde kullanın:

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

   `<Import/>` öğesi kullanılırken, isteğe bağlı bir `Version` özniteliği de belirtebilirsiniz.  Örneğin, `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`belirtebilirsiniz.

## <a name="how-project-sdks-are-resolved"></a>Proje SDK 'Ları nasıl çözümlenir

İçeri aktarma değerlendirilirken, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] belirttiğiniz ada ve sürüme göre proje SDK 'sının yolunu dinamik olarak çözer.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Ayrıca, makinenizde proje SDK 'larını içeren eklentiler olan kayıtlı SDK çözümleyicilerine ait bir liste de vardır.  Bu eklentiler şunları içerir:

1. Belirttiğiniz SDK 'nın KIMLIĞI ve sürümüyle eşleşen NuGet paketleri için yapılandırılmış paket akışlarınızı sorgulayan bir NuGet tabanlı çözümleyici.<br/>
   Bu çözümleyici yalnızca isteğe bağlı bir sürüm belirttiyseniz etkindir ve herhangi bir özel proje SDK 'Sı için kullanılabilir.
2. .NET CLı ile yüklenen SDK 'Ları çözen bir .NET CLı Çözümleyicisi.<br/>
   Bu çözümleyici, ürünün parçası olan `Microsoft.NET.Sdk` ve `Microsoft.NET.Sdk.Web` gibi proje SDK 'larını bulur.
3. MSBuild ile yüklenen SDK 'Ları çözen varsayılan çözümleyici.

NuGet tabanlı SDK Çözümleyicisi, [Global. JSON](/dotnet/core/tools/global-json) ' da her bir proje yerine bir yerde proje SDK sürümünü denetlemenize olanak sağlayan bir sürüm belirtmeyi destekler:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Bir derleme sırasında her bir proje SDK 'sının yalnızca bir sürümü kullanılabilir.  Aynı proje SDK 'sının iki farklı sürümüne başvuruyorsam, MSBuild bir uyarı yayacaktır.  *Global. JSON*uygulamanızda bir sürüm belirtilmişse, projelerinizde bir sürüm **belirtmemelidir** .

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [Derlemenizi özelleştirme](../msbuild/customize-your-build.md)
- [Paketler, meta veriler ve çerçeveler](/dotnet/core/packages)
- [.NET Core için csproj biçimine eklemeler](/dotnet/core/tools/csproj)
