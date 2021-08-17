---
title: Öğe seçin (MSBuild) | Microsoft Docs
description: alt öğeleri değerlendirmek için MSBuild öğesini seçin ve değerlendirmek için bir ıtemgroup veya propertygroup öğesi kümesi seçin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Choose
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
ms.assetid: 7b8b025a-d944-4f5c-9018-c89fc2ef146d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 86370841d06bb2efbd5de5af635e2858d607e8c8969aade244aae45430d6744a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370443"
---
# <a name="choose-element-msbuild"></a>Öğe seçin (MSBuild)

, `ItemGroup` Değerlendirilecek öğe ve/veya öğe kümesi seçmek için alt öğeleri değerlendirir `PropertyGroup` .

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Syntax

```xml
<Choose>
    <When Condition="'StringA'=='StringB'">... </When>
    <Otherwise>... </Otherwise>
</Choose>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Güvenmiyorsanız](../msbuild/otherwise-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> `PropertyGroup` `ItemGroup` Tüm öğelerin koşulları değerlendirmesi durumunda değerlendirilecek kod ve öğe bloğunu belirtir `When` `false` . Öğesinde sıfır veya bir öğe olabilir `Otherwise` `Choose` ve bu öğe son öğe olmalıdır.|
|[Ne zaman](../msbuild/when-element-msbuild.md)|Gerekli öğe.<br /><br /> Öğe için seçilecek olası bir kod bloğu belirtir `Choose` . Öğesinde bir veya daha fazla `When` öğe olabilir `Choose` .|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Güvenmiyorsanız](../msbuild/otherwise-element-msbuild.md) | Tüm öğelerin koşulları değerlendirmesi durumunda yürütülecek kod bloğunu belirtir `When` `false` . |
| [Project](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |
| [Ne zaman](../msbuild/when-element-msbuild.md) | Öğe için seçilecek olası bir kod bloğu belirtir `Choose` . |

## <a name="remarks"></a>Açıklamalar

 `Choose`, `When` , Ve `Otherwise` öğeleri bir dizi olası alternatifden daha fazla yürütmek üzere kodun bir bölümünü seçmek için bir yol sağlamak üzere birlikte kullanılır. Daha fazla bilgi için bkz. [koşullu yapılar](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Örnek

 Aşağıdaki proje, `Choose` öğesini ayarlanacak öğelerde hangi özellik değerleri kümesini belirlemek için öğesini kullanır `When` . `Condition`Her iki öğenin öznitelikleri `When` olarak değerlendirilir `false` , öğesindeki özellik değerleri `Otherwise` ayarlanır.

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
- [Project dosya şeması başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
