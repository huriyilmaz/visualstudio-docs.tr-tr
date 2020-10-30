---
title: UsingTask öğesi (MSBuild) | Microsoft Docs
description: Bir UsingTask TaskFactory 'e geçirilen verileri içeren MSBuild UsingTask 'ın görev öğesi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f99452021b0efef1e5df305e984c684f3f446905
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047900"
---
# <a name="task-element-of-usingtask-msbuild"></a>UsingTask öğesi (MSBuild)

Bir öğesine geçirilen verileri içerir `UsingTask` `TaskFactory` . Daha fazla bilgi için bkz. [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
 \<Task>

## <a name="syntax"></a>Syntax

```xml
<Task Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Evaluate`|İsteğe bağlı Boolean özniteliği.<br /><br /> Eğer `true` MSBuild, tüm iç öğeleri değerlendirir ve görev örneği oluşturulduğunda bilgileri öğesine geçirmeden önce öğeleri ve özellikleri genişletir `TaskFactory` .|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Veriler|Etiketler arasındaki metin `Task` öğesine harfine gönderilir `TaskFactory` .|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | MSBuild 'e görevleri kaydetmek için bir yol sağlar. Bir projede sıfır veya daha fazla `UsingTask` öğe olabilir. |

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `Task` öğesinin bir özniteliğiyle nasıl kullanılacağını gösterir `Evaluate` .

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
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
