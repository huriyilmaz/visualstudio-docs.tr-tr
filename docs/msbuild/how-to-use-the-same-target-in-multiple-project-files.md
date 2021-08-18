---
title: 'nasıl yapılır: birden çok Project dosyasında aynı hedefi kullanma | Microsoft Docs'
description: MSBuild bir proje dosyasında bir hedefin nasıl kaydedileceğini ve hedefin kullanması gereken başka bir projeye nasıl içeri aktarılacağını öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143345"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma

birkaç MSBuild proje dosyası oluşturduysanız, farklı proje dosyalarında aynı görevleri ve hedefleri kullanmanız gerektiğini fark edebilirsiniz. Her proje dosyasındaki bu görevlerin veya hedeflerin tüm açıklamalarını eklemek yerine, bir hedefi ayrı bir proje dosyasında kaydedebilir ve sonra bu projeyi, hedefi kullanmak için gereken diğer bir projeye içeri aktarabilirsiniz.

## <a name="use-the-import-element"></a>Içeri aktarma öğesini kullanın

Öğesi, başka bir proje dosyasına `Import` bir proje dosyası eklemek için kullanılır. içeri aktarılmakta olan proje dosyası geçerli bir MSBuild proje dosyası olmalı ve iyi biçimlendirilmiş XML içermelidir. `Project`Öznitelik, içeri aktarılan proje dosyasının yolunu belirtir. Öğesi hakkında daha fazla bilgi için `Import` bkz. [Import element (MSBuild)](../msbuild/import-element-msbuild.md).

#### <a name="to-import-a-project"></a>Bir projeyi içeri aktarmak için

1. İçeri aktarılan projedeki Özellikler ve öğeler için parametre olarak kullanılan proje dosyasını içeri aktarma, tüm özellikler ve öğeler ' i tanımlayın.

2. `Import`Projeyi içeri aktarmak için öğesini kullanın. Örnek:

     `<Import Project="MyCommon.targets"/>`

3. Öğesini takip `Import` eden tüm özellikleri ve içeri aktarılan projedeki özelliklerin ve öğelerin varsayılan tanımlarını geçersiz kılması gereken öğeleri tanımlayın.

## <a name="order-of-evaluation"></a>Değerlendirme sırası

 MSBuild bir öğeye ulaştığında `Import` , içeri aktarılan proje, öğe konumundaki içeri aktarma projesine etkin bir şekilde eklenir `Import` . Bu nedenle, `Import` öğesinin konumu Özellikler ve öğelerin değerlerini etkileyebilir. İçeri aktarılan proje tarafından ayarlanan özellikleri ve öğeleri ve içeri aktarılan projenin kullandığı özellikleri ve öğeleri anlamak önemlidir.

 Proje oluşturulduğunda tüm özellikler önce değerlendirilir ve ardından öğeler gelir. Örneğin, aşağıdaki XML içeri aktarılan proje dosyasını *MyCommon. targets* olarak tanımlar:

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

 Aşağıdaki XML, *MyCommon. targets* Içeri aktaran *MyApp. proj* öğesini tanımlar:

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

 Proje, özelliği `Name` *MyApp. proj* içinde tanımlandıktan sonra Içeri aktarıldığından `Name` *MyCommon. targets* içindeki tanımı, *MyApp. proj* içindeki tanımı geçersiz kılar. Proje, özellik adı tanımlanmadan önce içeri aktarıldıysa, yapı aşağıdaki iletiyi görüntüler:

 `Name="MyApp"`

#### <a name="use-the-following-approach-when-importing-projects"></a>Projeleri içeri aktarırken aşağıdaki yaklaşımı kullanın

1. Proje dosyasında, içeri aktarılan projedeki Özellikler ve öğeler için parametre olarak kullanılan tüm özellikleri ve öğeleri tanımlayın.

2. Projeyi içeri aktarın.

3. Proje dosyasında, içeri aktarılan projedeki özelliklerin ve öğelerin varsayılan tanımlarını geçersiz kılması gereken tüm özellikleri ve öğeleri tanımlayın.

## <a name="example-1"></a>Örnek 1

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

## <a name="example-2"></a>Örnek 2

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
- [Targets](../msbuild/msbuild-targets.md)
