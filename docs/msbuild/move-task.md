---
title: Görev Taşı | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633466"
---
# <a name="move-task"></a>Taşıma görevi

Dosyaları yeni bir konuma taşır.

## <a name="parameters"></a>Parametreler

 Foling tablosu görevin parametrelerini `Move` açıklar.

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Kaynak dosyaları taşımak için dosyaların listesini belirtir. Bu listenin `SourceFiles` parametrede belirtilen listeye bire bir eşleme olması beklenir. Diğer bir deyişle, belirtilen `SourceFiles` ilk dosya belirtilen `DestinationFiles`ilk konuma taşınır ve benzeri.|
|`DestinationFolder`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Dosyaları taşımak istediğiniz dizini belirtir.|
|`MovedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Başarıyla taşınan öğeleri içerir.|
|`OverwriteReadOnlyFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> Yalnızca `true`okunur dosya olarak işaretlenmiş olsalar bile dosyaların üzerine yazarsa.|
|`SourceFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Taşımak için dosyaları belirtir.|

## <a name="remarks"></a>Açıklamalar

 `DestinationFolder` Parametre veya `DestinationFiles` parametre belirtilmelidir, ancak her ikisi de belirtilmemelidir. Eğer her ikisi de belirtilirse görev başarısız olur ve bir hata günlüğe kaydedilir.

 Görev, `Move` istenen hedef dosyalar için gerekli klasörleri oluşturur.

 Tabloda listelenen parametrelere sahip olmanın yanı sıra, bu görev <xref:Microsoft.Build.Tasks.TaskExtension> sınıftan devralınan parametreleri de devralır. <xref:Microsoft.Build.Utilities.Task> Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
