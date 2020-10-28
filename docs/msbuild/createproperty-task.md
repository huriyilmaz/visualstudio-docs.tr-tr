---
title: CreateProperty görevi | Microsoft Docs
description: Özellikleri geçirilen değerlerle doldurmak için MSBuild CreateProperty görevini kullanın, değerlerin bir özellikten veya dizeden diğerine kopyalanmasını sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d7dd8d7f5a50998832a8fac6f47bf66e9a6bbe9
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796193"
---
# <a name="createproperty-task"></a>CreateProperty görevi

Özellikleri geçirilen değerlerle doldurur. Bu, değerlerin bir özellikten veya dizeden diğerine kopyalanmasını sağlar.

## <a name="attributes"></a>Öznitelikler

Aşağıdaki tablo, görevin parametrelerini açıklar `CreateProperty` .

| Parametre | Açıklama |
|------------------| - |
| `Value` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yeni özelliğe kopyalanacak değeri belirtir. |
| `ValueSetByTask` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> Parametresiyle aynı değeri içerir `Value` . Bu parametreyi yalnızca, çıktılar güncel olduğundan, kapsayan hedefi atlayarak MSBuild tarafından ayarlanan çıkış özelliğini kullanmaktan kaçınmak istediğinizde kullanın. |

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `CreateProperty` `NewFile` ve özelliğinin değerlerinin birleşimini kullanarak özelliğini oluşturmak için görevini kullanır `SourceFilename` `SourceFileExtension` .

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <SourceFilename>Module1</SourceFilename>
        <SourceFileExtension>vb</SourceFileExtension>
    </PropertyGroup>

    <Target Name="CreateProperties">

        <CreateProperty
            Value="$(SourceFilename).$(SourceFileExtension)">
            <Output
                TaskParameter="Value"
                PropertyName="NewFile" />
        </CreateProperty>

    </Target>

</Project>
```

Projeyi çalıştırdıktan sonra `NewFile` özelliğin değeri *Module1. vb* ' dir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
