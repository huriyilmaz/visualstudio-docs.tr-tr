---
title: Ne zaman Eleman (MSBuild) | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcb9404b8c68171f0695b33c285582f5e4c5b4ec
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630931"
---
# <a name="when-element-msbuild"></a>Eleman (MSBuild)

Öğenin seçilen olası bir `Choose` kod bloğunu belirtir.

 \<Proje \<> \< \<>'> Ne Zaman> Seçin ... \<Aksi \<takdirde>> seçin ...

## <a name="syntax"></a>Sözdizimi

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
|Koşul|Gerekli öznitelik.<br /><br /> Değerlendirme koşulu. Daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Seçin:](../msbuild/choose-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Yürütülecek bir kod bölümünü seçmek için alt öğeleri değerlendirir. Bir `When` öğede sıfır `Choose` veya daha fazla öğe olabilir.|
|[ıtemgroup](../msbuild/itemgroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Kullanıcı tanımlı [Öğe](../msbuild/item-element-msbuild.md) öğeleri kümesi içerir. Bir `When` öğede sıfır `ItemGroup` veya daha fazla öğe olabilir.|
|[Propertygroup](../msbuild/propertygroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Kullanıcı tanımlı [Özellik](../msbuild/property-element-msbuild.md) öğeleri kümesi içerir. Bir `When` öğede sıfır `PropertyGroup` veya daha fazla öğe olabilir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Öğeyi seçin (MSBuild)](../msbuild/choose-element-msbuild.md)|Yürütülecek bir kod bölümünü seçmek için alt öğeleri değerlendirir.|

## <a name="remarks"></a>Açıklamalar

 `Condition` Öznitelik doğru değerlendirirse, alt `ItemGroup` `PropertyGroup` ve `When` öğe öğeleri yürütülür `When` ve sonraki tüm öğeler atlanır.

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
