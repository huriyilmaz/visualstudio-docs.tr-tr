---
title: MSBuild koşullu yapılar | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26891fa67616b1796499722e03a764da2a8fd7d6
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589272"
---
# <a name="msbuild-conditional-constructs"></a>MSBuild koşullu yapılar
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], [seçim](../msbuild/choose-element-msbuild.md), [ne zaman](../msbuild/when-element-msbuild.md)ve [otherwise](../msbuild/otherwise-element-msbuild.md) öğelerinden birini kullanarak veya işlemek için bir mekanizma sağlar.

## <a name="use-the-choose-element"></a>Seçme öğesini kullanın
 `Choose` öğesi, bir `true`değerlendirilene kadar yukarıdan aşağıya doğru sırayla test edilen `Condition` özniteliklere sahip bir dizi `When` öğesi içerir. Birden fazla `When` öğesi `true`değerlendirilirse, yalnızca ilki kullanılır. Varsa bir `Otherwise` öğesi, bir `When` öğesindeki hiçbir koşul `true`olarak değerlendiriliyorsa değerlendirilir.

 `Choose` öğeleri `Project`, `When` ve `Otherwise` öğeleri için alt öğe olarak kullanılabilir. `When` ve `Otherwise` öğeleri `ItemGroup`, `PropertyGroup`veya `Choose` alt öğelerine sahip olabilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek,/veya işleme için `Choose` ve `When` öğelerini kullanır. Projenin özellikleri ve öğeleri `Configuration` özelliğinin değerine bağlı olarak ayarlanır.

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

## <a name="see-also"></a>Ayrıca bkz.
- [Öğe seç (MSBuild)](../msbuild/choose-element-msbuild.md)
- [Ne zaman öğesi (MSBuild)](../msbuild/when-element-msbuild.md)
- [Otherwise öğesi (MSBuild)](../msbuild/otherwise-element-msbuild.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
