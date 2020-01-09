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
ms.openlocfilehash: 4d34d8edca64987f9b6c4648bef1f239aca4d5ba
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594948"
---
# <a name="touch-task"></a>Dokunma görevi
Dosyaların erişim ve değiştirme zamanlarını ayarlar.

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda `Touch` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AlwaysCreate`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, önceden mevcut olmayan dosyaları oluşturur.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dokunarak dosya koleksiyonunu belirtir.|
|`ForceTouch`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, dosyalar salt okunurdur olsa bile bir dosya dokunmayı zorlar.|
|`Time`|İsteğe bağlı `String` parametresi.<br /><br /> Geçerli saatten farklı bir saat belirtir. Biçim <xref:System.DateTime.Parse%2A> yöntemi için kabul edilebilir bir biçim olmalıdır.|
|`TouchedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Başarıyla dokunmayan öğelerin koleksiyonunu içerir.|

## <a name="remarks"></a>Açıklamalar
 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `Files` öğesi koleksiyonunda belirtilen dosyaların erişim ve değiştirilme zamanlarını değiştirmek için `Touch` görevini kullanır ve başarıyla dokunulmayan dosyaların listesini `FilesTouched` öğesi koleksiyonuna koyar.

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
