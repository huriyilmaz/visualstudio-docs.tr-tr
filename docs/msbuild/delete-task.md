---
title: Görevi Sil | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634285"
---
# <a name="delete-task"></a>Silme görevi

Belirtilen dosyaları siler.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevparametreleri `Delete` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DeletedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Başarıyla silinen dosyaları belirtir.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dosyaları silmek için belirtir.|
|`TreatErrorsAsWarnings`|İsteğe bağlı `Boolean` parametre<br /><br /> Hatalar `true`uyarı olarak günlüğe kaydedilirse. Varsayılan değer: `false`.|

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

> [!WARNING]
> `Delete` Görev ile joker kullanırken dikkatli olun. Gibi ifadeler ile yanlış dosyaları kolayca `$(SomeProperty)\**\*.*` `$(SomeProperty)/**/*.*`silebilirsiniz veya , özellikle özellik boş bir dize değerlendirir, bu durumda `Files` parametre sürücünüzün köküne değerlendirmek ve silmek istediğinizden çok daha fazla silmek.

## <a name="example"></a>Örnek

Aşağıdaki örnek *MyApp.pdb*dosyasını siler.

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
