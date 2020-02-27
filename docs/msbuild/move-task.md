---
title: Görevi taşı | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05b9f83fa7c80769ea3c584e2885c8fb1db24176
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633466"
---
# <a name="move-task"></a>Taşıma görevi

Dosyaları yeni bir konuma taşıın.

## <a name="parameters"></a>Parametreler

 Katlama tablosu `Move` görevin parametrelerini açıklar.

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Kaynak dosyaların taşınacağı dosyaların listesini belirtir. Bu listenin `SourceFiles` parametresinde belirtilen listeye bire bir eşleme olması beklenir. Diğer bir deyişle, `SourceFiles` belirtilen ilk dosya `DestinationFiles`belirtilen ilk konuma taşınır ve bu şekilde devam eder.|
|`DestinationFolder`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Dosyaları taşımak istediğiniz dizini belirtir.|
|`MovedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Başarıyla taşınan öğeleri içerir.|
|`OverwriteReadOnlyFiles`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, salt okuma dosyaları olarak işaretlenseler bile dosyaların üzerine yazar.|
|`SourceFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Taşınacak dosyaları belirtir.|

## <a name="remarks"></a>Açıklamalar

 `DestinationFolder` parametresi ya da `DestinationFiles` parametresi belirtilmelidir, ikisi birden belirtilmemelidir. Eğer her ikisi de belirtilirse görev başarısız olur ve bir hata günlüğe kaydedilir.

 `Move` görev, istenen hedef dosyalar için gereken klasörleri oluşturur.

 Tabloda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
