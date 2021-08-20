---
title: FormatUrl görevi | Microsoft Docs
description: bir giriş url 'sini doğru çıkış url biçimine dönüştürmek için MSBuild formaturl görevinin nasıl kullanılacağı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 300b64f3de940d7be3c28a8a13afe7b1bfc7b0e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137138"
---
# <a name="formaturl-task"></a>FormatUrl görevi

URL 'YI doğru URL biçimine dönüştürür.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `FormatUrl` .

|Parametre|Açıklama|
|---------------|-----------------|
|`InputUrl`|İsteğe bağlı `String` parametre.<br /><br /> Biçimlendirilecek URL 'YI belirtir.|
|`OutputUrl`|İsteğe bağlı `String` çıkış parametresi.<br /><br /> Biçimlendirilen URL 'YI belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelere sahip olmanın yanı sıra sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)