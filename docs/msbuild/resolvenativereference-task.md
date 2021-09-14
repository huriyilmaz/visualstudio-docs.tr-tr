---
title: ResolveNativeReference Görev | Microsoft Docs
description: Microsoft.Build.Tasks.ResolveNativeReference sınıfını MSBuild yerel başvuruları çözümlemek için ResolveNativeReference görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveNativeReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveNativeReference task
- ResolveNativeReference task [MSBuild]
ms.assetid: 56acd101-de77-4eec-92c6-f5c6d2187579
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 212239348ba1f4caf80be1ac9feb029bb702cee3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625563"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference görevi

Yerel başvuruları çözümler. sınıfını <xref:Microsoft.Build.Tasks.ResolveNativeReference> uygulayan. Bu sınıf, .NET Framework doğrudan koddan kullanılmak üzere tasarlanmış bir altyapıyı destekler.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevin parametreleri açık `ResolveNativeReference` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AdditionalSearchPaths`|Gerekli <xref:System.String?displayProperty=fullName>`[]` parametresi.<br /><br /> Yerel başvuruların derleme kimliklerini çözümlemek için arama yollarını alır veya ayarlar.|
|`ContainedComComponents`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Yerel derlemenin COM bileşenlerini alır veya ayarlar.|
|`ContainedLooseEtcFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Yerel bildirimde listelenen loose *Etc* dosyalarını alır veya ayarlar.|
|`ContainedLooseTlbFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Yerel derlemenin gevşek *.tlb* dosyalarını alır veya ayarlar.|
|`ContainedPrerequisiteAssemblies`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Bildirim kullanılmadan önce mevcut olması gereken derlemeleri alır veya ayarlar.|
|`ContainedTypeLibraries`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Yerel derlemenin tür kitaplıklarını alır veya ayarlar.|
|`ContainingReferenceFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Başvuru dosyalarını alır veya ayarlar.|
|`NativeReferences`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Win32 yerel derleme başvurularını alır veya ayarlar.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
