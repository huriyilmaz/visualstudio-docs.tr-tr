---
title: UsingTask (MSBuild) Görev Öğesi | Microsoft Dokümanlar
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
ms.openlocfilehash: 36644a6b21092361d92dba5f0886eb4198884995
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263194"
---
# <a name="task-element-of-usingtask-msbuild"></a>UsingTask (MSBuild) görev öğesi

Bir'e `UsingTask` `TaskFactory`geçirilen verileri içerir. Daha fazla bilgi için [Bkz. UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Proje \<> Görev \<> Görev>

## <a name="syntax"></a>Sözdizimi

```xml
<Task Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Evaluate`|İsteğe bağlı Boolean özniteliği.<br /><br /> `true`MSBuild, herhangi bir iç öğeyi değerlendirirse ve bilgileri görevin `TaskFactory` anında ne zaman geçtiğine geçmeden önce öğeleri ve özellikleri genişletir.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Veriler|`Task` Etiketler arasındaki metin harfi harfine `TaskFactory`.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Usingtask](../msbuild/usingtask-element-msbuild.md) | MSBuild'te görevleri kaydetmek için bir yol sağlar. Bir projede sıfır `UsingTask` veya daha fazla öğe olabilir. |

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öznitelik `Task` ile `Evaluate` öğenin nasıl kullanılacağını gösterir.

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
