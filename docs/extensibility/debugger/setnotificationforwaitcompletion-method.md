---
title: SetNotificationForWaitCompletion yöntemi | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712867"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion Metodu
TASK_STATE_WAIT_COMPLETION_NOTIFICATION durum bitini ayarlar veya temizler.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib ( *mscorlib.dll*)

## <a name="syntax"></a>Söz dizimi

```vb
internal void SetNotificationForWaitCompletion(bool enabled)
```

### <a name="parameters"></a>Parametreler
 `enabled`

 `true` bit ' i ayarlamak için; `false` bit.

## <a name="exceptions"></a>Özel durumlar

## <a name="remarks"></a>Açıklamalar
 Hata ayıklayıcı, zaman uyumsuz yöntem gövdesinin dışına yardım etmek için bu biti ayarlar. `enabled`İse `true` , bu yöntemin yalnızca henüz tamamlanmamış bir görevde çağrılması gerekir. Ne zaman, `enabled` `false` Bu yöntem tamamlanmış görevlerde çağrılabilir. Her iki olayda yalnızca Promise stili görevler için kullanılmalıdır.

## <a name="requirements"></a>Gereksinimler

## <a name="see-also"></a>Ayrıca bkz.
- [Görev sınıfı](../../extensibility/debugger/task-class-internal-members.md)
