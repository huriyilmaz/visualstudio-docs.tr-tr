---
title: VCMessage Görevi | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2247240ae0992c8275520ec5d7bf94d98ae1053
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631217"
---
# <a name="vcmessage-task"></a>VCMessage görevi

Yapı sırasında uyarı ve hata iletilerini günlüğe kaydeder.

## <a name="remarks"></a>Açıklamalar

 Bu görev, C++ projeleri için MSBuild'in uygulanmasına yardımcı olur ve kullanıcı tarafından çağrılması amaçlanmamıştır. Daha fazla bilgi için bkz. <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parametreler

 Aşağıdaki **tabloda VCMessage** görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|**Bağımsız Değişkenler**|İsteğe bağlı **String** parametresi.<br /><br /> Görüntülenecek iletilerin yarı sütunlu sınırlı listesi.|
|**Kod**|Gerekli **String** parametresi.<br /><br /> İletiyi nitelendiren bir hata numarası.|
|**Tür**|İsteğe bağlı **String** parametresi.<br /><br /> Yayılacak ileti türünü belirtir. Uyarı iletisi yatsın diye "Uyarı" veya hata iletisi yontmak için "Hata" belirtin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
