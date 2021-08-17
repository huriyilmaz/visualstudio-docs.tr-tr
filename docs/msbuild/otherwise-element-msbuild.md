---
title: Otherwise Öğesi (MSBuild) | Microsoft Docs
description: Yalnızca MSBuild olduğunda öğelerinin koşulları false ise yürütülecek kod bloğu belirtmek için Otherwise öğesini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Otherwise
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
ms.assetid: de3997e9-1595-4263-a886-95530b56a319
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: a11331b751a491c3c39562b0b3cd509a5e3d1d9a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027714"
---
# <a name="otherwise-element-msbuild"></a>Otherwise öğesi (MSBuild)

Yalnızca tüm öğelerin koşulları olarak değerlendirilirse yürütülecek kod `When` `false` bloğudur.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Syntax

```xml
<Otherwise>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Choose>... </Choose>
</Otherwise>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Seçin](../msbuild/choose-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Yürütülecek kodun bir bölümünü seçmek için alt öğeleri değerlendirir. Bir öğede sıfır veya `Choose` daha fazla öğe `Otherwise` olabilir.|
|[ıtemgroup](../msbuild/itemgroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Kullanıcı tanımlı Öğe öğeleri [kümesi](../msbuild/item-element-msbuild.md) içerir. Bir öğede sıfır veya `ItemGroup` daha fazla öğe `Otherwise` olabilir.|
|[Propertygroup](../msbuild/propertygroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Kullanıcı tanımlı Özellik öğeleri [kümesi](../msbuild/property-element-msbuild.md) içerir. Bir öğede sıfır veya `PropertyGroup` daha fazla öğe `Otherwise` olabilir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Seçin](../msbuild/choose-element-msbuild.md)|Yürütülecek kodun bir bölümünü seçmek için alt öğeleri değerlendirir.|

## <a name="remarks"></a>Açıklamalar

 Bir öğede yalnızca `Otherwise` bir öğe olabilir ve son öğe olması `Choose` gerekir.

 `Choose`, `When` ve öğeleri birlikte, bir dizi olası alternatifi yürütmek için bir kod bölümü `Otherwise` seçmek için bir yol sağlamak için kullanılır. Daha fazla bilgi için [bkz. Koşullu yapılar.](../msbuild/msbuild-conditional-constructs.md)

## <a name="example"></a>Örnek

 Aşağıdaki proje, `Choose` öğelerinde hangi özellik değerleri kümesi ayarlamayacaklarını seçmek `When` için öğesini kullanır. Her `Condition` iki öğenin öznitelikleri `When` olarak `false` değerlendirilirse, öğesinde özellik `Otherwise` değerleri ayarlanır.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition="'$(Configuration)' == ''">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='debug' ">
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <DebugType>full</DebugType>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\Debug\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
            <ItemGroup>
                <Compile Include="UnitTesting\*.cs" />
                <Reference Include="NUnit.dll" />
            </ItemGroup>
        </When>
        <When Condition=" '$(Configuration)'=='retail' ">
            <PropertyGroup>
                <DebugSymbols>false</DebugSymbols>
                <Optimize>true</Optimize>
                <OutputPath>.\bin\Release\</OutputPath>
                <DefineConstants>TRACE</DefineConstants>
            </PropertyGroup>
        </When>
        <Otherwise>
            <PropertyGroup>
                <DebugSymbols>true</DebugSymbols>
                <Optimize>false</Optimize>
                <OutputPath>.\bin\$(Configuration)\</OutputPath>
                <DefineConstants>DEBUG;TRACE</DefineConstants>
            </PropertyGroup>
        </Otherwise>
        </Choose>
    <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Koşullu yapılar](../msbuild/msbuild-conditional-constructs.md)
- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
