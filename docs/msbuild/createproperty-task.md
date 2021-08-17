---
title: CreateProperty Task | Microsoft Docs
description: CreateProperty MSBuild kullanarak değerleri geçirilen değerlerle doldurmak ve değerlerin bir özellik veya dizeden diğerine kopyalanır.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: be38b53074bb8f290cd9cd865d60513712be5505
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122054840"
---
# <a name="createproperty-task"></a>CreateProperty görevi

Özellikleri geçirilen değerlerle doldurmak. Bu, değerlerin bir özellikten veya dizeden diğerine kopyalanır.

## <a name="attributes"></a>Öznitelikler

Aşağıdaki tabloda görevin parametreleri açık `CreateProperty` almaktadır.

| Parametre | Açıklama |
|------------------| - |
| `Value` | İsteğe `String` bağlı çıkış parametresi.<br /><br /> Yeni özelliğine kopya eklenecek değeri belirtir. |
| `ValueSetByTask` | İsteğe `String` bağlı çıkış parametresi.<br /><br /> parametresiyle aynı değeri `Value` içerir. Bu parametreyi yalnızca çıkış özelliğinin MSBuild çıkışlar güncel olduğundan kapsayan hedefi atlarken bu parametreyi kullanın. |

## <a name="remarks"></a>Açıklamalar

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Aşağıdaki örnek, `CreateProperty` ve özelliğinin `NewFile` değerlerinin birleşimini kullanarak özelliğini oluşturmak için `SourceFilename` görevini `SourceFileExtension` kullanır.

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

Projeyi çalıştırdıktan sonra özelliğinin değeri `NewFile` *Module1.vb olur.*

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [Görevler](../msbuild/msbuild-tasks.md)
