---
title: GetOutputFileName görevi | Microsoft Docs
description: cl.exe ve diğer araçların çıkış dosyası adı seçeneklerini belirtmek için MSBuild GetOutputFileName yardımcı görevini kullanın.
ms.custom: SEO-VS-2020
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutputfilename
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), GetOutputFileName task
- GetOutputFileName task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: cb4670bb84b151332951608f7b20ef5ea44e59a3
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436785"
---
# <a name="getoutputfilename-task"></a>GetOutputFileName görevi

Yalnızca çıkış dizini veya tam dosya adı ya da hiçbir şey belirtilmesine izin veren CL ve diğer araçların çıkış dosyası adını almak için yardımcı görev.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda, **Getoutputfilename** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**OutputExtension**|Gerekli **dize** parametresi.|
|**Çıktı**|İsteğe bağlı **dize** çıkış parametresi.|
|**OutputPath**|İsteğe bağlı **dize** parametresi.|
|**Kaynakdosya**|Gerekli **dize** parametresi.|

## <a name="see-also"></a>Ayrıca bkz.

[Görev başvurusu](../msbuild/msbuild-task-reference.md)
