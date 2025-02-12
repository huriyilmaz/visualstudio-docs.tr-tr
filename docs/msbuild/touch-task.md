---
title: Touch Task | Microsoft Docs
description: Dosyaların erişim ve değişiklik zamanlarını ayar MSBuild Touch görevinin parametreleri ve kullanımı hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5fbc6924cf53d72dbbd92679008039c7df6bd1f4
ms.sourcegitcommit: 141efad8a6a303737bdc563a4f48964411f342eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2021
ms.locfileid: "131249679"
---
# <a name="touch-task"></a>Dokunma görevi

Dosyaların erişim ve değişiklik zamanlarını ayarlar.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `Touch` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AlwaysCreate`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` zaten mevcut olmayan herhangi bir dosya oluşturur.|
|`Files`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dokunacak dosyaların koleksiyonunu belirtir.|
|`ForceTouch`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` dosyalar salt okunur olsa bile bir dosya dokunmaya neden olur.|
|`Time`|İsteğe `String` bağlı parametre.<br /><br /> Bir saat belirtir. Varsayılan olarak geçerli saat `Now` ( ). biçimi kullanılarak yöntemi tarafından <xref:System.DateTime.Parse%2A> ayrıştırılabilir `DateTimeFormatInfo.InvariantInfo` olmalıdır.|
|`TouchedFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Başarıyla dokunan öğelerin koleksiyonunu içerir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

 Aşağıdaki örnek, öğe koleksiyonunda belirtilen dosyaların erişim ve değişiklik zamanlarını değiştirmek için görevini kullanır ve öğe koleksiyonuna başarıyla dokunan dosyaların `Touch` `Files` listesini `FilesTouched` koyar.

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
