---
title: SetNotificationForWaitCompletion Yöntemi | Microsoft Docs
description: Hata ayıklayıcının promise stili görevler için zaman uyumsuz yöntem gövdesinde adım yardımcı olması için durum biti nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ec469ed4f9c4fa2e503b2350235299a81a94bf9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902117"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion Metodu
Durum biti kümelerini TASK_STATE_WAIT_COMPLETION_NOTIFICATION veya temizler.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Derleme:** mscorlib *(mscorlib.dll*)

## <a name="syntax"></a>Sözdizimi

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametreler
 `enabled`

 `true` biti ayarlamak için; `false` biti unset.

## <a name="exceptions"></a>Özel durumlar

## <a name="remarks"></a>Açıklamalar
 Hata ayıklayıcısı, zaman uyumsuz yöntem gövdesinin dışında adım adım yardımcı olmak için bu biti ayarlar. ise, `enabled` `true` bu yöntemin yalnızca henüz tamamlanmadı olan bir görev üzerinde çağrılmış olması gerekir. olduğunda, `enabled` `false` bu yöntem tamamlanan görevlerde çağrılebilir. Her iki durumda da yalnızca promise stilinde görevler için kullanılmalıdır.

## <a name="requirements"></a>Gereksinimler

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
