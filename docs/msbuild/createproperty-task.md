---
title: CreateProperty Görevi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634324"
---
# <a name="createproperty-task"></a>CreateProperty görevi

Özellikleri geçirilen değerlerle doldurur. Bu, değerlerin bir özellik veya dizeden diğerine kopyalanmasını sağlar.

## <a name="attributes"></a>Öznitelikler

Aşağıdaki tabloda görevparametreleri `CreateProperty` açıklanmaktadır.

| Parametre | Açıklama |
|------------------| - |
| `Value` | İsteğe bağlı `String` çıktı parametresi.<br /><br /> Yeni özellik kopyalamak için değer belirtir. |
| `ValueSetByTask` | İsteğe bağlı `String` çıktı parametresi.<br /><br /> `Value` Parametreyle aynı değeri içerir. Bu parametreyi yalnızca, çıktılar güncel olduğundan, çevreleyen hedefi atladığında MSBuild tarafından belirlenen çıktı özelliğini önlemek istediğinizde kullanın. |

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `CreateProperty` özellik `SourceFilename` ve `SourceFileExtension` `NewFile` özellik değerlerinin birleşimini kullanarak özelliği oluşturmak için görevi kullanır.

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

Projeyi çalıştırdıktan sonra, `NewFile` özelliğin değeri *Module1.vb*' dir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
