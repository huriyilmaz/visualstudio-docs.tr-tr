---
title: UsingTask Görev Öğesi (MSBuild) | Microsoft Docs
description: UsingTask TaskFactory'ye geçirilen verileri içeren usingtask MSBuild öğesinin Task öğesi hakkında bilgi öğrenin.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 6e5156d0d128bce8b927bbdc8faacdd93834e167
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142760"
---
# <a name="task-element-of-usingtask-msbuild"></a>UsingTask'ın görev öğesi (MSBuild)

bir 'a geçirilen verileri `UsingTask` `TaskFactory` içerir. Daha fazla bilgi için [bkz. UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).

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
|`Evaluate`|İsteğe bağlı Boole özniteliği.<br /><br /> , MSBuild herhangi bir iç öğe değerlendirirse ve görev örneği esnilene bilgileri iletir önce öğeleri `true` `TaskFactory` ve özellikleri genişleter.|

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|Veriler|Etiketler arasındaki `Task` metin, metnine tam olarak `TaskFactory` gönderilir.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Usingtask](../msbuild/usingtask-element-msbuild.md) | Görevleri MSBuild'a kaydetmenin bir yolunu sağlar. Projede sıfır veya daha `UsingTask` fazla öğe olabilir. |

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğesinin bir `Task` özniteliğiyle nasıl kullanıla bir `Evaluate` gösterir.

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
- [Project dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
