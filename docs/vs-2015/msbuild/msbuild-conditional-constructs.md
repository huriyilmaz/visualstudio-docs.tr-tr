---
title: MSBuild koşullu yapılar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b7b22f63d5d3d6e0b1f7789561029bbfbfb4cdf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143755"
---
# <a name="msbuild-conditional-constructs"></a>MSBuild Koşullu Yapıları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)][Seç](../msbuild/choose-element-msbuild.md), [ne zaman](../msbuild/when-element-msbuild.md)ve [otherwise](../msbuild/otherwise-element-msbuild.md) öğelerinden birini kullanarak/veya işleme için bir mekanizma sağlar.  
  
## <a name="using-the-choose-element"></a>Seçme öğesini kullanma  
 `Choose`Öğesi, `When` `Condition` bir olarak değerlendirilene kadar yukarıdan aşağıya doğru sırayla test edilen özniteliklere sahip bir dizi öğe içerir `true` . Birden fazla `When` öğe olarak değerlendirilirse `true` , yalnızca ilki kullanılır. Varsa, öğe `Otherwise` üzerinde hiçbir koşul hesaplanmıyorsa, bir öğesi değerlendirilir `When` `true` .  
  
 `Choose` öğeleri `Project` , ve öğelerinin alt öğeleri olarak kullanılabilir `When` `Otherwise` . `When` ve `Otherwise` öğeleri,, `ItemGroup` `PropertyGroup` veya `Choose` alt öğelerine sahip olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Choose` `When` /veya işleme için ve öğelerini kullanır. Projenin özellikleri ve öğeleri, özelliğinin değerine bağlı olarak ayarlanır `Configuration` .  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğe seç (MSBuild)](../msbuild/choose-element-msbuild.md)   
 [Ne zaman öğesi (MSBuild)](../msbuild/when-element-msbuild.md)   
 [Otherwise öğesi (MSBuild)](../msbuild/otherwise-element-msbuild.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)
