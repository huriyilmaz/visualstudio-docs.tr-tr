---
title: Görev Taşıma | Microsoft Docs
description: Dosyaları yeni konumlara MSBuild Taşıma görevi için parametreler ve ayarlar hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Move task
- Move task [MSBuild]
ms.assetid: d1405347-1309-4f18-b565-905408093d59
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0b89b5407d8f45d6f08a41f97337d754e4405136
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069019"
---
# <a name="move-task"></a>Taşıma görevi

Dosyaları yeni bir konuma taşır.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini `Move` açıklar.

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Kaynak dosyaları taşımak için dosyaların listesini belirtir. Bu listenin, parametresinde belirtilen listeye bire bir eşlemesi olması `SourceFiles` beklenir. Başka bir ifadeyle, içinde belirtilen ilk dosya içinde belirtilen ilk konuma taşınır `SourceFiles` ve bu şekilde devam `DestinationFiles` ediyor.|
|`DestinationFolder`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Dosyaları taşımak istediğiniz dizini belirtir.|
|`MovedFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Başarıyla taşınan öğeleri içerir.|
|`OverwriteReadOnlyFiles`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` salt okunur dosyalar olarak işaretlenmiş olsalar bile dosyaların üzerine yazma.|
|`SourceFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Taşınan dosyaları belirtir.|

## <a name="remarks"></a>Açıklamalar

 parametresi `DestinationFolder` veya parametresi `DestinationFiles` belirtilmelidir, ancak ikisi birden belirtilmez. Eğer her ikisi de belirtilirse görev başarısız olur ve bir hata günlüğe kaydedilir.

 Görev, `Move` istenen hedef dosyalar için gereken klasörleri oluşturur.

 Bu görev, tabloda listelenen parametrelerin yanı sıra sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
