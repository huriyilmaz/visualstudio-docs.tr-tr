---
title: ParameterGroup Öğesi | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28d6def203a819d41a420899663d1a974612c631
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632998"
---
# <a name="parametergroup-element"></a>ParameterGroup Öğesi

Bir `UsingTask` `TaskFactory`tarafından oluşturulan görevde mevcut olacak parametrelerin isteğe bağlı bir listesini içerir. Daha fazla bilgi için bkz. [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Proje > \<UsingTask > \<ParameterGroup >

## <a name="syntax"></a>Sözdizimi

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

 Yok.

### <a name="child-elements"></a>Alt öğeleri

|Öğe|Açıklama|
|-------------|-----------------|
|[Parametresinin](../msbuild/parameter-element.md)|Bir `UsingTask` `TaskFactory`tarafından oluşturulan bir görev için belirli bir parametre hakkında bilgi içerir. Öğesinin adı parametrenin adıdır.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | MSBuild 'e görevleri kaydetmek için bir yol sağlar. Bir projede sıfır veya daha fazla öğe `UsingTask` olabilir. |

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `ParameterGroup` öğesinin nasıl kullanılacağını gösterir.

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
