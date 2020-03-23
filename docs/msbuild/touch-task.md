---
title: Dokunmatik Görev | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631659"
---
# <a name="touch-task"></a>Dokunma görevi

Dosyaların erişim ve değişiklik saatlerini ayarlar.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `Touch` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AlwaysCreate`|İsteğe bağlı `Boolean` parametre.<br /><br /> , `true`zaten var olmayan dosyaları oluşturursa.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dokunulacak dosyaların toplanmasını belirtir.|
|`ForceTouch`|İsteğe bağlı `Boolean` parametre.<br /><br /> Dosyalar `true`salt okunur olsa bile dosya dokunuşunu zorlarsa.|
|`Time`|İsteğe bağlı `String` parametre.<br /><br /> Geçerli saat dışında bir zaman belirtir. <xref:System.DateTime.Parse%2A> Biçim, yöntem tarafından kabul edilebilir bir biçim olmalıdır.|
|`TouchedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Başarıyla dokunulan öğelerin koleksiyonunu içerir.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, `Touch` `Files` madde koleksiyonunda belirtilen dosyaların erişim ve değişiklik sürelerini değiştirmek için görevi kullanır ve `FilesTouched` madde koleksiyonuna başarıyla dokunulan dosyaların listesini koyar.

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
