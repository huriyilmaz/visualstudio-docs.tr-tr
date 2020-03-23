---
title: 'Nasıl Kullanılır: Birden Çok Proje Dosyasında Aynı Hedefi Kullanın | Microsoft Dokümanlar'
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
ms.openlocfilehash: 1b7b36a829e2e406ecd3f10ba3a2b588c6f7df25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633765"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Nasıl kullanılır: Birden çok proje dosyasında aynı hedefi kullanma

Birkaç MSBuild proje dosyası yazarsanız, aynı görevleri ve hedefleri farklı proje dosyalarında kullanmanız gerektiğini keşfetmiş olabilirsiniz. Bu görevlerin veya hedeflerin tam açıklamasını her proje dosyasına dahil etmek yerine, bir hedefi ayrı bir proje dosyasına kaydedebilir ve ardından bu projeyi hedefi kullanması gereken başka bir projeye aktarabilirsiniz.
## <a name="use-the-import-element"></a>Alma öğesini kullanma

 Öğe, `Import` bir proje dosyasını başka bir proje dosyasına eklemek için kullanılır. İçe aktarılan proje dosyası geçerli bir MSBuild proje dosyası olmalı ve iyi biçimlendirilmiş XML içermelidir. Öznitelik, `Project` içe aktarılan proje dosyasına giden yolu belirtir. `Import` Öğe hakkında daha fazla bilgi için [Alma öğesine (MSBuild)](../msbuild/import-element-msbuild.md)bakın.
Öğe, `Import` bir proje dosyasını başka bir proje dosyasına eklemek için kullanılır. İçe aktarılan proje dosyası geçerli bir MSBuild proje dosyası olmalı ve iyi biçimlendirilmiş XML içermelidir. Öznitelik, `Project` içe aktarılan proje dosyasına giden yolu belirtir. `Import` Öğe hakkında daha fazla bilgi için [Alma öğesine (MSBuild)](../msbuild/import-element-msbuild.md)bakın.

#### <a name="to-import-a-project"></a>Projeyi almak için

1. İçe aktarılan proje dosyasında, alınan projedeki özellikler ve maddeler için parametre olarak kullanılan tüm özellikleri ve öğeleri tanımlayın.

2. Projeyi `Import` almak için öğeyi kullanın. Örnek:

     `<Import Project="MyCommon.targets"/>`

3. Öğeyi `Import` takiben, içe aktarılan projedeki özelliklerin ve maddelerin varsayılan tanımlarını geçersiz kılacak tüm özellikleri ve öğeleri tanımlayın.

## <a name="order-of-evaluation"></a>Değerlendirme sırası

 MSBuild bir `Import` öğeye ulaştığında, içe aktarılan proje `Import` etkin bir şekilde öğenin konumunda ki içe aktarma projesine eklenir. Bu nedenle, `Import` öğenin konumu özellikleri ve öğelerin değerlerini etkileyebilir. İçe aktarılan proje tarafından ayarlanan özellikleri ve öğeleri ve alınan projenin kullandığı özellikleri ve öğeleri anlamak önemlidir.

 Proje inşa edildiğinde, tüm özellikler önce değerlendirilir ve ardından öğeler izlenir. Örneğin, aşağıdaki XML alınan proje dosyası *MyCommon.targets*tanımlar:

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

 Aşağıdaki XML *MyApp.proj*tanımlar , *MyCommon.targets*ithal:

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

 Proje inşa edildiğinde, aşağıdaki ileti görüntülenir:

 `Name="MyCommon"`

 Proje `Name` *MyApp.proj'da*özellik tanımlandıktan sonra içe aktarıldığı `Name` için *MyCommon.targets'daki* tanımı *MyApp.proj'daki*tanımı geçersiz kılar. Proje özellik Adı tanımlanmadan önce içe aktarılırsa, yapı aşağıdaki iletiyi görüntüler:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Projeleri alırken aşağıdaki yaklaşımı kullanın

1. Proje dosyasında, alınan projedeki özellikler ve maddeler için parametre olarak kullanılan tüm özellikleri ve öğeleri tanımlayın.

2. Projeyi içe aktarın.

3. Proje dosyasında, içe aktarılan projedeki özelliklerin ve öğelerin varsayılan tanımlarını geçersiz kılacak tüm özellikleri ve öğeleri tanımlayın.

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, ikinci kod örneğinin aktardığı *MyCommon.targets* dosyasını gösterir. *.targets* dosyası, yapıyı yapılandırmak için içe aktarma projesindeki özellikleri değerlendirir.

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

 Aşağıdaki kod örneği *MyCommon.targets* dosyasını içeri aktarın.

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

- [Alma öğesi (MSBuild)](../msbuild/import-element-msbuild.md)
- [Hedef](../msbuild/msbuild-targets.md)
