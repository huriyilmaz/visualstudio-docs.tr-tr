---
title: MSBuild Koşullu Yapılar | Microsoft Docs
description: Choose, When MSBuild Otherwise öğeleriyle koşullu işleme mekanizmasını nasıl sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Choose> Element [MSBuild]
- Choose Element [MSBuild]
- conditional constructs [MSBuild]
- MSBuild, conditional constructs
- <When> Element [MSBuild]
- <Otherwise> Element [MSBuild]
- Otherwise Element [MSBuild]
- When Element [MSBuild]
ms.assetid: dd54258e-f4fb-448f-9da4-d1817e0cbaf2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: c0b371f4aceef5baadd7a00738d885974b88c584
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628466"
---
# <a name="msbuild-conditional-constructs"></a>MSBuild koşullu yapıları

MSBuild, Seç , Ne Zaman ve Aksi [](../msbuild/choose-element-msbuild.md)takdirde [](../msbuild/when-element-msbuild.md)öğeleriyle işlemeye yönelik bir [mekanizma](../msbuild/otherwise-element-msbuild.md) sağlar.

## <a name="use-the-choose-element"></a>Choose öğesini kullanma

 öğesi, değerlendirilene kadar üstten aşağıya doğru sırayla test edilen `Choose` `When` `Condition` özniteliklere sahip bir dizi öğe `true` içerir. Birden fazla öğe `When` olarak değerlendirilirse `true` yalnızca ilk öğe kullanılır. Bir `Otherwise` öğe varsa, bir öğedeki hiçbir koşul olarak değerlendirilmezse `When` `true` değerlendirilir.

 `Choose` öğeleri, ve öğelerinin alt öğeleri `Project` `When` olarak `Otherwise` kullanılabilir. `When` ve `Otherwise` öğeleri , veya alt `ItemGroup` `PropertyGroup` `Choose` öğelerine sahip olabilir.

## <a name="example"></a>Örnek

 Aşağıdaki örnek/ veya `Choose` işleme için ve öğelerini `When` kullanır. Projenin özellikleri ve öğeleri, özelliğin değerine bağlı olarak `Configuration` ayarlanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <OutputType>Exe</OutputType>
        <RootNamespace>ConsoleApplication1</RootNamespace>
        <AssemblyName>ConsoleApplication1</AssemblyName>
        <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <Choose>
        <When Condition=" '$(Configuration)'=='Debug' ">
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
    </Choose>
    <!-- Rest of Project -->
</Project>
```

Bu örnekte, derleyici sabiti üzerinde bir `DEFINED_CONSTANT` koşul kullanılır. Bunlar özelliğine `DefinedConstants` dahil edilir. Normal ifade, noktalı virgülle ayrılmış bir listede tam sabitle eşleşmek için kullanılır.

```xml
<Choose>
   <When Condition="$([System.Text.RegularExpressions.Regex]::IsMatch(
         $(DefineConstants), '^(.*;)*DEFINED_CONSTANT(;.*)*$'))">
      <!-- When DEFINED_CONSTANT is defined. -->
   </When>
   <!-- other conditions -->
</Choose>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Öğe seçme (MSBuild)](../msbuild/choose-element-msbuild.md)
- [When öğesi (MSBuild)](../msbuild/when-element-msbuild.md)
- [Otherwise öğesi (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
