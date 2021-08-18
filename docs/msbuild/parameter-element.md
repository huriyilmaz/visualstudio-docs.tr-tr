---
title: Parameter öğesi | Microsoft Docs
description: bir usingtask taskfactory tarafından oluşturulan bir görev için belirli bir parametre hakkında bilgi içeren MSBuild Parameter öğesi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: d408158d203d62c562073d188dc0a5319b964738
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100744"
---
# <a name="parameter-element"></a>Parameter öğesi

Tarafından oluşturulan bir görev için belirli bir parametre hakkında bilgi içerir `UsingTask` `TaskFactory` .  Öğesinin adı parametrenin adıdır.  Daha fazla bilgi için bkz. [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<ParameterGroup>
 \<Parameter>

## <a name="syntax"></a>Syntax

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`ParameterType`|İsteğe bağlı öznitelik.<br /><br /> Parametresinin .NET türü, örneğin, `System.String` .|
|`Output`|İsteğe bağlı Boolean özniteliği.<br /><br /> Eğer `true` , bu parametre, görev için bir çıkış parametresidir. Varsayılan değer `false` şeklindedir.|
|`Required`|İsteğe bağlı Boolean özniteliği.<br /><br /> `true`Bu parametre, görev için gerekli bir parametredir. Varsayılan değer `false` şeklindedir.|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Tarafından oluşturulan görevde mevcut olacak parametrelerin isteğe bağlı bir listesini içerir `UsingTask` `TaskFactory` .|

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğesinin nasıl kullanılacağını gösterir `Parameter` .

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Project dosya şeması başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
