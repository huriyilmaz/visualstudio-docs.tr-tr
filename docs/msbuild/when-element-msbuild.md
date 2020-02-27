---
title: Ne zaman öğesi (MSBuild) | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630931"
---
# <a name="when-element-msbuild"></a>Ne zaman öğesi (MSBuild)

Seçilecek `Choose` öğesi için olası bir kod bloğu belirtir.

 \<Proje > \<\<> > seçin \<>... \<> seçin \<...

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
|Koşul|Gerekli öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|['Yu](../msbuild/choose-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> , Çalıştırılacak kodun bir bölümünü seçmek için alt öğeleri değerlendirir. Bir `When` öğesinde sıfır veya daha fazla `Choose` öğe olabilir.|
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Kullanıcı tanımlı [öğe](../msbuild/item-element-msbuild.md) öğeleri kümesi içerir. Bir `When` öğesinde sıfır veya daha fazla `ItemGroup` öğe olabilir.|
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|İsteğe bağlı öğe.<br /><br /> Kullanıcı tanımlı [özellik](../msbuild/property-element-msbuild.md) öğeleri kümesi içerir. Bir `When` öğesinde sıfır veya daha fazla `PropertyGroup` öğe olabilir.|

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[Öğe seç (MSBuild)](../msbuild/choose-element-msbuild.md)|, Çalıştırılacak kodun bir bölümünü seçmek için alt öğeleri değerlendirir.|

## <a name="remarks"></a>Açıklamalar

 `Condition` özniteliği true olarak değerlendirilirse, `When` öğesinin alt `ItemGroup` ve `PropertyGroup` öğeleri yürütülür ve sonraki tüm `When` öğeleri atlanır.

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
