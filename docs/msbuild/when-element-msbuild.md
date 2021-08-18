---
title: Öğe (MSBuild) | Microsoft Docs
description: Seç öğesi MSBuild olası bir kod bloğu belirten When öğesi hakkında bilgi edinmek için.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#When
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <When> Element [MSBuild]
- When Element [MSBuild]
ms.assetid: eb27de6f-4e71-4e87-87e2-d93f7bf5899c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: a1434a264f53d3473c341d2b3b8b625a054f8ffe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040001"
---
# <a name="when-element-msbuild"></a>When öğesi (MSBuild)

Seçilen öğe için olası bir kod `Choose` bloğu belirtir.

 \<Project> \<Choose>
 \<When>
 \<Choose>
... \<Otherwise>
 \<Choose>
...

## <a name="syntax"></a>Syntax

```xml
<When Condition="'StringA'=='StringB'">
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Choose>... </Choose>
</When>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Koşul|Gerekli öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Seçin](../msbuild/choose-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Yürütülecek kodun bir bölümünü seçmek için alt öğeleri değerlendirir. Bir öğede sıfır veya `Choose` daha fazla öğe `When` olabilir.|
|[ıtemgroup](../msbuild/itemgroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Kullanıcı tanımlı Öğe öğeleri [kümesi](../msbuild/item-element-msbuild.md) içerir. Bir öğede sıfır veya `ItemGroup` daha fazla öğe `When` olabilir.|
|[Propertygroup](../msbuild/propertygroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Kullanıcı tanımlı Özellik öğeleri [kümesi](../msbuild/property-element-msbuild.md) içerir. Bir öğede sıfır veya `PropertyGroup` daha fazla öğe `When` olabilir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Öğe seçme (MSBuild)](../msbuild/choose-element-msbuild.md)|Yürütülecek kodun bir bölümünü seçmek için alt öğeleri değerlendirir.|

## <a name="remarks"></a>Açıklamalar

 özniteliği `Condition` true olarak değerlendirilirse, öğenin alt öğeleri ve öğeleri yürütülür ve sonraki `ItemGroup` tüm öğeler `PropertyGroup` `When` `When` atlanır.

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
