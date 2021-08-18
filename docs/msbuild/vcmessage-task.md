---
title: VCMessage Görev | Microsoft Docs
description: C++ MSBuild derleme sırasında uyarı ve hata iletilerini günlüğe göndermek için VCMessage görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 705298bf73bceda32ca82a9dc85f96816794d8e9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108219"
---
# <a name="vcmessage-task"></a>VCMessage görevi

Derleme sırasında uyarı ve hata iletilerini günlüğe kaydeder.

## <a name="remarks"></a>Açıklamalar

 Bu görev C++ MSBuild projelerinin uygulanmasına yardımcı olur ve kullanıcı tarafından çağrılma amacını oluşturmaz. Daha fazla bilgi için bkz. <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda VCMessage görevinin **parametreleri açık** almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Bağımsız değişkenler**|İsteğe **bağlı Dize** parametresi.<br /><br /> Görüntülenmek için noktalı virgülle ayrılmış bir ileti listesi.|
|**Kod**|Gerekli **Dize** parametresi.<br /><br /> İletiyi niteleyici bir hata numarası.|
|**Tür**|İsteğe **bağlı Dize** parametresi.<br /><br /> Yayma ileti türlerini belirtir. Bir uyarı iletisi ya da bir hata iletisi ya da "Hata" ya da "Uyarı" belirtin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
