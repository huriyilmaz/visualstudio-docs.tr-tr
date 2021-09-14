---
title: 'Nasıl kullanılır: Birden Çok DosyaDa Aynı Hedefi Project Kullanma | Microsoft Docs'
description: Hedef bir proje dosyasına MSBuild ve hedefi kullanmak zorunda olan herhangi bir projeye aktarmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 1f9fa6593cfb5e6ef21379b7513be02d943e9c66
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625671"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Nasıl kullanılır: Birden çok proje dosyalarında aynı hedefi kullanma

Birden fazla proje MSBuild yazarsanız, farklı proje dosyalarında aynı görevleri ve hedefleri kullanmak zorunda olduğunu keşfetebilirsiniz. Her proje dosyasına bu görevlerin veya hedeflerin tam açıklamasını dahil etmek yerine, bir hedefi ayrı bir proje dosyasına kaydedebilir ve ardından bu projeyi hedefi kullanması gereken başka bir projeye aktarabilirsiniz.

## <a name="use-the-import-element"></a>İçeri Aktarma öğesini kullanma

öğesi, `Import` bir proje dosyasını başka bir proje dosyasına eklemek için kullanılır. İçe aktarılan proje dosyası, proje dosyası için geçerli MSBuild ve iyi formed XML içermesi gerekir. özniteliği, `Project` içe aktarılan proje dosyasının yolunu belirtir. öğesi hakkında daha fazla bilgi `Import` için bkz. [Import element (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Projeyi içeri aktarma

1. İçeri aktarılan proje dosyasında, içeri aktarılan projedeki özellikler ve öğeler için parametre olarak kullanılan tüm özellikleri ve öğeleri tanımlayın.

2. Projeyi `Import` içeri aktarmak için öğesini kullanın. Örnek:

     `<Import Project="MyCommon.targets"/>`

3. öğesinin `Import` ardından, içe aktarılan projedeki özelliklerin ve öğelerin varsayılan tanımlarını geçersiz kılması gereken tüm özellikleri ve öğeleri tanımlayın.

## <a name="order-of-evaluation"></a>Değerlendirme sırası

 Bir MSBuild ulaştığında, içeri aktarılan proje öğenin bulunduğu `Import` konumda içeri aktarma projesine etkin bir şekilde `Import` eklenir. Bu nedenle, `Import` öğenin konumu özelliklerin ve öğelerin değerlerini etkileyebilir. İçe aktarılan proje tarafından ayarlanmış özellikleri ve öğeleri ve içe aktarılan projenin kullandığı özellikleri ve öğeleri anlamak önemlidir.

 Proje derlemesi sonrasında tüm özellikler önce değerlendirilir ve ardından öğeler kullanılır. Örneğin, aşağıdaki XML, *MyCommon.targets* içe aktarılan proje dosyasını tanımlar:

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

 Aşağıdaki XML, *MyCommon.targets'ı içeri aktaran MyApp.proj'yi tanımlar:* 

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

 Proje lendiğinde aşağıdaki ileti görüntülenir:

 `Name="MyCommon"`

 Proje, özelliği `Name` *MyApp.proj* içinde tanımlandığı için, `Name` *MyCommon.targets* içinde tanımı *MyApp.proj* içinde tanımı geçersiz kılar. Proje Ad özelliği tanımlanmamış şekilde içe aktarılmışsa derleme aşağıdaki iletiyi görüntüler:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Projeleri içeri aktarıyorken aşağıdaki yaklaşımı kullanın

1. Proje dosyasında, içe aktarılan projedeki özellikler ve öğeler için parametre olarak kullanılan tüm özellikleri ve öğeleri tanımlayın.

2. Projeyi içeri aktarın.

3. Proje dosyasında, içe aktarılan projedeki özelliklerin ve öğelerin varsayılan tanımlarını geçersiz kılması gereken tüm özellikleri ve öğeleri tanımlayın.

## <a name="example-1"></a>Örnek 1

 Aşağıdaki kod örneği, ikinci kod örneğinin içeri aktar olduğu *MyCommon.targets* dosyasını gösterir. *.targets dosyası,* derlemeyi yapılandırmak için içeri aktarma projesinin özelliklerini değerlendirir.

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

## <a name="example-2"></a>Örnek 2

 Aşağıdaki kod örneği *MyCommon.targets dosyasını içeri* aktarır.

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

- [Import öğesi (MSBuild)](../msbuild/import-element-msbuild.md)
- [Targets](../msbuild/msbuild-targets.md)
