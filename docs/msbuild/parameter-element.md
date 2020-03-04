---
title: Parameter öğesi | Microsoft Docs
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
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263116"
---
# <a name="parameter-element"></a>Parameter öğesi

Bir `UsingTask` `TaskFactory`tarafından oluşturulan bir görev için belirli bir parametre hakkında bilgi içerir.  Öğesinin adı parametrenin adıdır.  Daha fazla bilgi için bkz. [UsingTask öğesi (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Proje > \<UsingTask > \<ParameterGroup > \<parametresi >

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
|`ParameterType`|İsteğe bağlı öznitelik.<br /><br /> Parametrenin .NET türü, örneğin, `System.String`.|
|`Output`|İsteğe bağlı Boolean özniteliği.<br /><br /> `true`, bu parametre görev için bir çıkış parametresidir. Varsayılan değer `false` şeklindedir.|
|`Required`|İsteğe bağlı Boolean özniteliği.<br /><br /> `true`, bu parametre görev için gerekli bir parametredir. Varsayılan değer `false` şeklindedir.|

### <a name="child-elements"></a>Alt öğeleri

 Yok.

### <a name="parent-elements"></a>Üst öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Bir `UsingTask` `TaskFactory`tarafından oluşturulan görevde mevcut olacak parametrelerin isteğe bağlı bir listesini içerir.|

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `Parameter` öğesinin nasıl kullanılacağını gösterir.

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
