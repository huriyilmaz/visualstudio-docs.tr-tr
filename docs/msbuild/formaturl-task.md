---
title: FormatUrl Görevi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fcd4ed0c60d615f0c213e1af5099c5e94a9b485
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634129"
---
# <a name="formaturl-task"></a>FormatUrl görevi

URL'yi doğru URL biçimine dönüştürür.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `FormatUrl` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`InputUrl`|İsteğe bağlı `String` parametre.<br /><br /> URL'yi biçimlendirmek için belirtir.|
|`OutputUrl`|İsteğe bağlı `String` çıktı parametresi.<br /><br /> Biçimlendirilmiş URL'yi belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere sahip olmanın yanı sıra, bu görev <xref:Microsoft.Build.Tasks.TaskExtension> sınıftan devralınan parametreleri de devralır. <xref:Microsoft.Build.Utilities.Task> Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)