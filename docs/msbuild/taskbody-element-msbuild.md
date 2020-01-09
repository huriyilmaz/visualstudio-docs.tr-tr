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
ms.openlocfilehash: ac4e04c1a75fe7afdebc984381e17d7e55913fd4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594987"
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

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Evaluate`|İsteğe bağlı Boolean özniteliği.<br /><br /> `true`, MSBuild tüm iç öğeleri değerlendirir ve görev örneği oluşturulduğunda bilgileri `TaskFactory` geçirmeden önce öğeleri ve özellikleri genişletir.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Veri|`TaskBody` etiketleri arasındaki metin, `TaskFactory`harfine gönderilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]görevleri kaydetmek için bir yol sağlar. Bir projede sıfır veya daha fazla öğe `UsingTask` olabilir. |

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
