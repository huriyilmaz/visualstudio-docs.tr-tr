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
ms.openlocfilehash: cac0af3371a5c4ae385cc19367b360b8e8f608fd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590065"
---
# <a name="createproperty-task"></a>CreateProperty görevi
Özellikleri geçirilen değerlerle doldurur. Bu, değerlerin bir özellikten veya dizeden diğerine kopyalanmasını sağlar.

## <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}
Aşağıdaki tabloda `CreateProperty` görevinin parametreleri açıklanmaktadır.

| Parametre | Açıklama |
|------------------| - |
| `Value` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> Yeni özelliğe kopyalanacak değeri belirtir. |
| `ValueSetByTask` | İsteğe bağlı `String` çıkış parametresi.<br /><br /> `Value` parametresiyle aynı değeri içerir. Bu parametreyi yalnızca, çıktılar güncel olduğundan, kapsayan hedefi atlayan çıkış özelliğinin [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] tarafından ayarlanmış olmasını önlemek istediğinizde kullanın. |

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
