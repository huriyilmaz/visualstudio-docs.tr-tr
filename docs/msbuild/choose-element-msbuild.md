---
title: Öğe seç (MSBuild) | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4f699b4ffc9372af0c803d094390544932d652b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634480"
---
# <a name="choose-element-msbuild"></a>Öğe seç (MSBuild)

, Değerlendirmek için bir `ItemGroup` öğe ve/veya `PropertyGroup` öğeleri kümesi seçmek üzere alt öğeleri değerlendirir.

 \<Proje > \<\<> > seçin \<>... \<> seçin \<...

## <a name="syntax"></a>Sözdizimi

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
|[Güvenmiyorsanız](../msbuild/otherwise-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Tüm `When` öğelerinin koşulları `false`olarak değerlendirilmezse, değerlendirilecek kod `PropertyGroup` ve `ItemGroup` öğelerinin bloğunu belirtir. Bir `Choose` öğesinde sıfır veya bir `Otherwise` öğesi olabilir ve bu, son öğe olmalıdır.|
|[Oluşturulurken](../msbuild/when-element-msbuild.md)|Gerekli öğe.<br /><br /> Seçilecek `Choose` öğesi için olası bir kod bloğu belirtir. Bir `Choose` öğesinde bir veya daha fazla `When` öğesi olabilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Güvenmiyorsanız](../msbuild/otherwise-element-msbuild.md) | Tüm `When` öğelerinin koşulları `false`değerlendirmiyorsa yürütülecek kod bloğunu belirtir. |
| [Proje](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |
| [Oluşturulurken](../msbuild/when-element-msbuild.md) | Seçilecek `Choose` öğesi için olası bir kod bloğu belirtir. |

## <a name="remarks"></a>Açıklamalar

 `Choose`, `When`ve `Otherwise` öğeleri, bir dizi olası alternatifden yürütülecek bir kod bölümü seçmek için bir yol sağlamak üzere birlikte kullanılır. Daha fazla bilgi için bkz. [koşullu yapılar](../msbuild/msbuild-conditional-constructs.md).

## <a name="example"></a>Örnek

 Aşağıdaki proje, ayarlanacak `When` öğelerindeki özellik değerlerini belirlemek için `Choose` öğesini kullanır. Hem `When` öğelerin `Condition` öznitelikleri `false`olarak değerlendirilerse, `Otherwise` öğesindeki özellik değerleri ayarlanır.

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
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
