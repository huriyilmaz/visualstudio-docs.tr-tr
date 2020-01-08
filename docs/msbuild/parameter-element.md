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
ms.openlocfilehash: 9d1351f47ec8acc5aa5a510ede9c2284ec97c248
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590468"
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

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}

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
       <TaskBody Evaluate="true">
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
