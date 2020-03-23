---
title: Çıktı Elemanı (MSBuild) | Microsoft Dokümanlar
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90fbd517608c9c36db0b1035f296b9d9402abddd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633037"
---
# <a name="output-element-msbuild"></a>Çıkış elemanı (MSBuild)

Görev çıktı değerlerini maddelerde ve özelliklerde depolar.

 \<Proje \<> \<Hedef \<görev> Çıktı>>

## <a name="syntax"></a>Sözdizimi

```xml
<Output TaskParameter="Parameter"
    PropertyName="PropertyName"
    Condition = "'String A' == 'String B'" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`TaskParameter`|Gerekli öznitelik.<br /><br /> Görevin çıktı parametresinin adı.|
|`PropertyName`|Ya `PropertyName` öznitelik `ItemName` gereklidir.<br /><br /> Görevin çıktı parametre değerini alan özellik. Projeniz daha sonra $(PropertyName\<>) sözdizimi ile tesise başvuruda bulunabilir. Bu özellik adı yeni bir özellik adı veya projede zaten tanımlanmış bir ad olabilir.<br /><br /> Bu öznitelik de `ItemName` kullanılıyorsa kullanılamaz.|
|`ItemName`|Ya `PropertyName` öznitelik `ItemName` gereklidir.<br /><br /> Görevin çıktı parametre değerini alan madde. Projeniz daha sonra öğeye @(ItemName\<>) sözdizimi ile başvuruda bulunabilir. Madde adı yeni bir madde adı veya projede zaten tanımlanmış bir ad olabilir. Madde adı varolan bir öğe olduğunda, çıktı parametre değerleri varolan öğeye eklenir. <br /><br /> Bu öznitelik de `PropertyName` kullanılıyorsa kullanılamaz.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek durum. Daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Görev](../msbuild/task-element-msbuild.md) | MSBuild görevinin bir örneğini oluşturur ve yürütür. |

## <a name="example"></a>Örnek

 Aşağıdaki kod örneği, `Csc` bir `Target` öğenin içinde yürütülmekte olan görevi gösterir. Görev parametrelerine geçirilen maddeler ve özellikler bu örneğin kapsamı dışında beyan edilir. `OutputAssembly` Çıktı parametresinden gelen değer `FinalAssemblyName` maddede depolanır ve çıktı parametresinden `BuildSucceeded` gelen değer `BuildWorked` özellikte depolanır. Daha fazla bilgi için [Görevler'e](../msbuild/msbuild-tasks.md)bakın.

```xml
<Target Name="Compile" DependsOnTargets="Resources">
    <Csc  Sources="@(CSFile)"
            TargetType="library"
            Resources="@(CompiledResources)"
            EmitDebugInformation="$(includeDebugInformation)"
            References="@(Reference)"
            DebugType="$(debuggingType)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
        <Output TaskParameter="BuildSucceeded"
                  PropertyName="BuildWorked" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
