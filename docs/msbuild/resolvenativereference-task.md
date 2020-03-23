---
title: ÇözümleyiciReferans Görevi | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64b76b31e96947914c9a641ed4ceb23c7761eb85
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632686"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference görevi

Yerel başvuruları çözer. <xref:Microsoft.Build.Tasks.ResolveNativeReference> Sınıfı uygular. Bu sınıf, doğrudan kodunuzdan kullanılması amaçlanmayan .NET Framework altyapısını destekler.

## <a name="task-parameters"></a>Görev parametreleri

 Aşağıdaki tabloda görevparametreleri `ResolveNativeReference` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AdditionalSearchPaths`|Gerekli <xref:System.String?displayProperty=fullName>`[]` parametresi.<br /><br /> Yerel başvuruların derleme kimliklerini çözmek için arama yollarını alır veya ayarlar.|
|`ContainedComComponents`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Yerel derlemenin COM bileşenlerini alır veya ayarlar.|
|`ContainedLooseEtcFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Yerel bildirimde listelenen gevşek *Etc* dosyalarını alır veya ayarlar.|
|`ContainedLooseTlbFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Yerel derlemenin gevşek *.tlb* dosyalarını alır veya ayarlar.|
|`ContainedPrerequisiteAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Bildirimin kullanılabilmesi için bulunması gereken derlemeleri alır veya ayarlar.|
|`ContainedTypeLibraries`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Yerel derlemenin tür kitaplıklarını alır veya ayarlar.|
|`ContainingReferenceFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Başvuru dosyalarını alır veya ayarlar.|
|`NativeReferences`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Win32 yerel montaj başvurularını alır veya ayarlar.|

## <a name="remarks"></a>Açıklamalar

 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
