---
title: Öğe (MSBuild) Seçin | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634480"
---
# <a name="choose-element-msbuild"></a>Öğeyi seçin (MSBuild)

Değerlendirilecek bir `ItemGroup` öğe ve/veya `PropertyGroup` öğe kümesi seçmek için alt öğeleri değerlendirir.

 \<Proje \<> \< \<>'> Ne Zaman> Seçin ... \<Aksi \<takdirde>> seçin ...

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
|[Aksi takdir -de](../msbuild/otherwise-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Tüm `When` öğelerin koşulları `PropertyGroup` nın `ItemGroup` değerlendirilmesi durumunda değerlendirmek için `false`kod ve öğeler bloğu belirtir. Bir `Choose` öğede sıfır `Otherwise` veya bir öğe olabilir ve bu son öğe olmalıdır.|
|[Tesis](../msbuild/when-element-msbuild.md)|Gerekli öğe.<br /><br /> Öğenin seçilen olası bir `Choose` kod bloğunu belirtir. Bir `Choose` öğede bir `When` veya daha fazla öğe olabilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Aksi takdir -de](../msbuild/otherwise-element-msbuild.md) | Tüm `When` öğelerin koşulları değerlendirirse, yürütülecek kod `false`bloğunu belirtir. |
| [Proje](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |
| [Tesis](../msbuild/when-element-msbuild.md) | Öğenin seçilen olası bir `Choose` kod bloğunu belirtir. |

## <a name="remarks"></a>Açıklamalar

 `Choose`, `When`ve `Otherwise` öğeler, olası alternatifler bir dizi yürütmek için kod bir bölümünü seçmek için bir yol sağlamak için birlikte kullanılır. Daha fazla bilgi için [Koşullu yapılara](../msbuild/msbuild-conditional-constructs.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki proje, `Choose` ayarlanacak öğelerdeki özellik değerleri `When` kümesini seçmek için öğeyi kullanır. Her `Condition` iki `When` öğenin öznitelikleri `false`değerlendirirse, `Otherwise` öğedeki özellik değerleri ayarlanır.

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
