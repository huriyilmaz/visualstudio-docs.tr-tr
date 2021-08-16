---
title: Görevi taşı | Microsoft Docs
description: dosyaları yeni konumlara taşımak MSBuild taşıma görevinin parametreleri ve ayarları hakkında bilgi edinin.
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
ms.openlocfilehash: 761d499c01fdc2fda0a7f8e539377a9ce2bb50edb8e33429cf799265ac59c494
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270516"
---
# <a name="move-task"></a>Taşıma görevi

Dosyaları yeni bir konuma taşıın.

## <a name="parameters"></a>Parametreler

 Katlama tablosu, görevin parametrelerini açıklar `Move` .

|Parametre|Açıklama|
|---------------|-----------------|
|`DestinationFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Kaynak dosyaların taşınacağı dosyaların listesini belirtir. Bu listenin, parametresinde belirtilen listeye bire bir eşleme olması beklenir `SourceFiles` . Diğer bir deyişle, içinde belirtilen ilk dosya `SourceFiles` ' de belirtilen ilk konuma taşınır ve bu şekilde devam eder `DestinationFiles` .|
|`DestinationFolder`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Dosyaları taşımak istediğiniz dizini belirtir.|
|`MovedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Başarıyla taşınan öğeleri içerir.|
|`OverwriteReadOnlyFiles`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , salt okuma dosyaları olarak işaretlenseler bile dosyaların üzerine yazar.|
|`SourceFiles`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Taşınacak dosyaları belirtir.|

## <a name="remarks"></a>Açıklamalar

 `DestinationFolder`Parametre ya da `DestinationFiles` parametre belirtilmelidir, ancak her ikisi birden belirtilmemelidir. Eğer her ikisi de belirtilirse görev başarısız olur ve bir hata günlüğe kaydedilir.

 `Move`Görev, istenen hedef dosyalar için gereken klasörleri oluşturur.

 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
