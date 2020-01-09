---
title: ResolveNativeReference görevi | Microsoft Docs
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
ms.openlocfilehash: 417c4536f13aa90505ec5e69b2719219af0d7e81
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595169"
---
# <a name="resolvenativereference-task"></a>ResolveNativeReference görevi
Yerel başvuruları çözümler. <xref:Microsoft.Build.Tasks.ResolveNativeReference> sınıfını uygular. Bu sınıf, doğrudan kodunuzdan kullanılması amaçlanmayan .NET Framework altyapısını destekler.

## <a name="task-parameters"></a>Görev parametreleri
 Aşağıdaki tabloda `ResolveNativeReference` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AdditionalSearchPaths`|Gerekli <xref:System.String?displayProperty=fullName>`[]` parametresi.<br /><br /> Yerel başvuruların derleme kimliklerini çözümlemek için arama yollarını alır veya ayarlar.|
|`ContainedComComponents`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Yerel derlemenin COM bileşenlerini alır veya ayarlar.|
|`ContainedLooseEtcFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Yerel bildirimde listelenen gevşek *vs* dosyalarını alır veya ayarlar.|
|`ContainedLooseTlbFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Yerel derlemenin gevşek *. tlb* dosyalarını alır veya ayarlar.|
|`ContainedPrerequisiteAssemblies`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Bildirimin kullanılabilmesi için mevcut olması gereken derlemeleri alır veya ayarlar.|
|`ContainedTypeLibraries`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Yerel derlemenin tür kitaplıklarını alır veya ayarlar.|
|`ContainingReferenceFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Başvuru dosyalarını alır veya ayarlar.|
|`NativeReferences`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Win32 yerel derleme başvurularını alır veya ayarlar.|

## <a name="remarks"></a>Açıklamalar
 Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
