---
title: Dokunma görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Touch
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Touch task
- Touch task [MSBuild]
ms.assetid: 8a978645-1393-4904-ae69-42afabd8c109
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 873783196a3eebdaca9cc4278b091e084c1488b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77631659"
---
# <a name="touch-task"></a>Dokunma görevi

Dosyaların erişim ve değiştirme zamanlarını ayarlar.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `Touch` .

|Parametre|Açıklama|
|---------------|-----------------|
|`AlwaysCreate`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , önceden mevcut olmayan dosyaları oluşturur.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dokunarak dosya koleksiyonunu belirtir.|
|`ForceTouch`|İsteğe bağlı `Boolean` parametre.<br /><br /> Varsa `true` , dosyalar salt okunurdur olsa bile bir dosya dokunmayı zorlar.|
|`Time`|İsteğe bağlı `String` parametre.<br /><br /> Geçerli saatten farklı bir saat belirtir. Biçim, yöntemi için kabul edilebilir bir biçim olmalıdır <xref:System.DateTime.Parse%2A> .|
|`TouchedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Başarıyla dokunmayan öğelerin koleksiyonunu içerir.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `Touch` öğe koleksiyonunda belirtilen dosyaların erişim ve değiştirme zamanlarını değiştirmek için görevini kullanır `Files` ve başarıyla dokunulmayan dosyaları `FilesTouched` öğe koleksiyonuna koyar.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

<ItemGroup>
    <Files Include="File1.cs;File2.cs;File3.cs" />
</ItemGroup>

    <Target Name="TouchFiles">
        <Touch
            Files="@(Files)">
            <Output
                TaskParameter="TouchedFiles"
                ItemName="FilesTouched"/>
    </Touch>
</Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
