---
title: ParametreGrup Elemanı | Microsoft Dokümanlar
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
ms.openlocfilehash: 8c06b9c530d3fff0fdfa429df633daaa4dde8c52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263099"
---
# <a name="parametergroup-element"></a>ParametreGrup öğesi

Bir `UsingTask` `TaskFactory`. tarafından oluşturulan görevde bulunacak parametrelerin isteğe bağlı bir listesini içerir. Daha fazla bilgi için [Bkz. UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Proje \<> ParametreGrup>> \<KullanmaGörev

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
|[Parametre](../msbuild/parameter-element.md)|Bir `UsingTask` `TaskFactory`. tarafından oluşturulan bir görev için belirli bir parametre hakkında bilgi içerir. Öğenin adı parametrenin adıdır.|

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Usingtask](../msbuild/usingtask-element-msbuild.md) | MSBuild'te görevleri kaydetmek için bir yol sağlar. Bir projede sıfır `UsingTask` veya daha fazla öğe olabilir. |

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğenin `ParameterGroup` nasıl kullanılacağını gösterir.

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
