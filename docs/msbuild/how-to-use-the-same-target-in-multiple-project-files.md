---
title: 'Nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50a4b756e0f0926e6c0ccd1a68ab44b7bc13e25c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75574064"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma
Birkaç [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası oluşturduysanız, farklı proje dosyalarında aynı görevleri ve hedefleri kullanmanız gerektiğini fark edebilirsiniz. Her proje dosyasındaki bu görevlerin veya hedeflerin tüm açıklamalarını eklemek yerine, bir hedefi ayrı bir proje dosyasında kaydedebilir ve sonra bu projeyi, hedefi kullanmak için gereken diğer bir projeye içeri aktarabilirsiniz.

## <a name="use-the-import-element"></a>Içeri aktarma öğesini kullanın
 `Import` öğesi, başka bir proje dosyasına bir proje dosyası eklemek için kullanılır. İçeri aktarılmakta olan proje dosyası geçerli bir [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyası olmalı ve iyi biçimlendirilmiş XML içermelidir. `Project` özniteliği içeri aktarılan proje dosyasının yolunu belirtir. `Import` öğesi hakkında daha fazla bilgi için bkz. [Import element (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Bir projeyi içeri aktarmak için

1. İçeri aktarılan projedeki Özellikler ve öğeler için parametre olarak kullanılan proje dosyasını içeri aktarma, tüm özellikler ve öğeler ' i tanımlayın.

2. Projeyi içeri aktarmak için `Import` öğesini kullanın. Örneğin:

     `<Import Project="MyCommon.targets"/>`

3. `Import` öğeden sonra, içeri aktarılan projedeki özelliklerin ve öğelerin varsayılan tanımlarını geçersiz kılması gereken tüm özellikleri ve öğeleri tanımlayın.

## <a name="order-of-evaluation"></a>Değerlendirme sırası
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bir `Import` öğesine ulaştığında, içeri aktarılan proje `Import` öğesi konumundaki içeri aktarma projesine etkin bir şekilde eklenir. Bu nedenle, `Import` öğesinin konumu Özellikler ve öğelerin değerlerini etkileyebilir. İçeri aktarılan proje tarafından ayarlanan özellikleri ve öğeleri ve içeri aktarılan projenin kullandığı özellikleri ve öğeleri anlamak önemlidir.

 Proje oluşturulduğunda tüm özellikler önce değerlendirilir ve ardından öğeler gelir. Örneğin, aşağıdaki XML içeri aktarılan proje dosyasını *MyCommon. targets*olarak tanımlar:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyCommon</Name>
    </PropertyGroup>

    <Target Name="Go">
        <Message Text="Name=$(Name)"/>
    </Target>
</Project>
```

 Aşağıdaki XML, *MyCommon. targets*Içeri aktaran *MyApp. proj*öğesini tanımlar:

```xml
<Project
    DefaultTargets="Go"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Name>MyApp</Name>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

 Proje oluşturduğunda, aşağıdaki ileti görüntülenir:

 `Name="MyCommon"`

 Proje, özellik `Name`, *MyApp. proj*içinde tanımlandıktan sonra içeri aktarıldığından, *MyCommon. targets* Içindeki `Name` tanımı, *MyApp. proj*içindeki tanımı geçersiz kılar. Proje, özellik adı tanımlanmadan önce içeri aktarıldıysa, yapı aşağıdaki iletiyi görüntüler:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Projeleri içeri aktarırken aşağıdaki yaklaşımı kullanın

1. Proje dosyasında, içeri aktarılan projedeki Özellikler ve öğeler için parametre olarak kullanılan tüm özellikleri ve öğeleri tanımlayın.

2. Projeyi içeri aktarın.

3. Proje dosyasında, içeri aktarılan projedeki özelliklerin ve öğelerin varsayılan tanımlarını geçersiz kılması gereken tüm özellikleri ve öğeleri tanımlayın.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, ikinci kod örneği içe aktardığı *MyCommon. targets* dosyasını gösterir. *. Targets* dosyası, derlemeyi yapılandırmak için içeri aktarma projesinden özellikleri değerlendirir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>
        <appname>$(MSBuildProjectName)</appname>
    <PropertyGroup>
    <Target Name="Build">
        <Csc Sources="hello.cs"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe"/>
    </Target>
</Project>
```

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği *MyCommon. targets* dosyasını içeri aktarır.

```xml
<Project DefaultTargets="Build"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <PropertyGroup>
        <Flavor>RETAIL</Flavor>
    </PropertyGroup>
    <Import Project="MyCommon.targets"/>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.
- [İçeri aktarma öğesi (MSBuild)](../msbuild/import-element-msbuild.md)
- [Hedefler](../msbuild/msbuild-targets.md)
