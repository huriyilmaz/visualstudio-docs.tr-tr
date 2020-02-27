---
title: TaskBody öğesi (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45b255f782390cfc478ac2f7bce58170e4e2b268
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77631854"
---
# <a name="taskbody-element-msbuild"></a>TaskBody öğesi (MSBuild)

Bir `UsingTask` `TaskFactory`geçirilen verileri içerir. Daha fazla bilgi için bkz. [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project > \<UsingTask > \<TaskBody >

## <a name="syntax"></a>Sözdizimi

```xml
<TaskBody Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Evaluate`|İsteğe bağlı Boolean özniteliği.<br /><br /> `true`, MSBuild tüm iç öğeleri değerlendirir ve görev örneği oluşturulduğunda bilgileri `TaskFactory` geçirmeden önce öğeleri ve özellikleri genişletir.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Veriler|`TaskBody` etiketleri arasındaki metin, `TaskFactory`harfine gönderilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | MSBuild 'e görevleri kaydetmek için bir yol sağlar. Bir projede sıfır veya daha fazla öğe `UsingTask` olabilir. |

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `Evaluate` özniteliğiyle `TaskBody` öğesinin nasıl kullanılacağını gösterir.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <TaskBody Evaluate="true">
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
