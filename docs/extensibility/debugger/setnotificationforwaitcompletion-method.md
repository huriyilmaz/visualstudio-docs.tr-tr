---
title: SetNotificationForWaitCompletion Yöntemi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 226ac41c8e3b7427ac3b9aba7bea08dbb7329d16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712867"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion Metodu
TASK_STATE_WAIT_COMPLETION_NOTIFICATION durum bitini ayarlar veya temizler.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaj:** mscorlib *(mscorlib.dll*olarak)

## <a name="syntax"></a>Sözdizimi

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametreler
 `enabled`

 `true`bit ayarlamak için; `false` biti ayarlamak için.

## <a name="exceptions"></a>Özel durumlar

## <a name="remarks"></a>Açıklamalar
 Hata ayıklama, bu biti bir async yöntem gövdesinden dışarı adım yardımcı olmak için ayarlar. `enabled` Ise, `true`bu yöntem yalnızca henüz tamamlanmamış bir görevde çağrılmalıdır. Ne `enabled` `false`zaman, bu yöntem tamamlanan görevlere çağrılabilir. Her iki durumda da, yalnızca söz tarzı görevler için kullanılmalıdır.

## <a name="requirements"></a>Gereksinimler

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
