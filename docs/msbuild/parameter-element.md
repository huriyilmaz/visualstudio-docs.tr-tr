---
title: Parametre Elemanı | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbf0c25967d84e930ee97a84709c808d3541e733
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263116"
---
# <a name="parameter-element"></a>Parametre elemanı

Bir `UsingTask` `TaskFactory`. tarafından oluşturulan bir görev için belirli bir parametre hakkında bilgi içerir.  Öğenin adı parametrenin adıdır.  Daha fazla bilgi için [Bkz. UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Proje \<> UsingTask> \< \<ParametreGroup> Parametre>

## <a name="syntax"></a>Sözdizimi

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
|`ParameterType`|İsteğe bağlı öznitelik.<br /><br /> Örneğin parametrenin .NET `System.String`türü.|
|`Output`|İsteğe bağlı Boolean özniteliği.<br /><br /> Eğer `true`, bu parametre görev için bir çıkış parametresi. Varsayılan değer `false` şeklindedir.|
|`Required`|İsteğe bağlı Boolean özniteliği.<br /><br /> Eğer `true`, bu parametre görev için gerekli bir parametre. Varsayılan değer `false` şeklindedir.|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ParametreGrubu](../msbuild/parametergroup-element.md)|Bir `UsingTask` `TaskFactory`. tarafından oluşturulan görevde bulunacak parametrelerin isteğe bağlı bir listesini içerir.|

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğenin `Parameter` nasıl kullanılacağını gösterir.

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
