---
title: Görevi Sil | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9effb00c613c5a61a5a8d4d89cbbe5b785601d8
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634285"
---
# <a name="delete-task"></a>Silme görevi

Belirtilen dosyaları siler.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda `Delete` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DeletedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Başarıyla silinen dosyaları belirtir.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Silinecek dosyaları belirtir.|
|`TreatErrorsAsWarnings`|İsteğe bağlı `Boolean` parametresi<br /><br /> `true`, hatalar uyarı olarak günlüğe kaydedilir. Varsayılan değer: `false`.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

> [!WARNING]
> `Delete` göreviyle joker karakter kullanırken dikkatli olun. `$(SomeProperty)\**\*.*` veya `$(SomeProperty)/**/*.*`gibi ifadelerle yanlış dosyaları kolayca silebilirsiniz, özellikle özellik boş bir dize olarak değerlendirilir, bu durumda `Files` parametresi sürücünüzün köküne değerlendirilemiyor ve silmek isteenden çok daha fazlasını silebilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, *MyApp. pdb*dosyasını siler.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <AppName>MyApp</AppName>
    </PropertyGroup>

    <Target Name="DeleteFiles">
        <Delete Files="$(AppName).pdb" />
    </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
