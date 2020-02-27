---
title: CreateProperty görevi | Microsoft Docs
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
ms.openlocfilehash: 155e8e6b57cc388e8c2981297be8b26ef5444c1b
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634324"
---
# <a name="createproperty-task"></a>CreateProperty görevi

Özellikleri geçirilen değerlerle doldurur. Bu, değerlerin bir özellikten veya dizeden diğerine kopyalanmasını sağlar.

## <a name="attributes"></a>Öznitelikler

Aşağıdaki tabloda `CreateProperty` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|------------------| - |
| `Value` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yeni özelliğe kopyalanacak değeri belirtir. |
| `ValueSetByTask` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> `Value` parametresiyle aynı değeri içerir. Bu parametreyi yalnızca, çıktılar güncel olduğundan, kapsayan hedefi atlayarak MSBuild tarafından ayarlanan çıkış özelliğini kullanmaktan kaçınmak istediğinizde kullanın. |

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `SourceFilename` ve `SourceFileExtension` özelliğinin değerlerinin birleşimini kullanarak `NewFile` özelliğini oluşturmak için `CreateProperty` görevini kullanır.

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

Projeyi çalıştırdıktan sonra, `NewFile` özelliğinin değeri *Module1. vb*' dir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
