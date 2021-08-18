---
title: SetNotificationForWaitCompletion yöntemi | Microsoft Docs
description: Hata ayıklayıcının, Promise stili görevlere yönelik zaman uyumsuz yöntem gövdesinin dışına çıkan bir durum bitini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- SetNotificationForWaitCompletion method, Task class [.NET Framework debug engines]
ms.assetid: da149c9a-20f4-4543-a29e-429c8c1d2e19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 88a0140ce27816592a7c43f1304f16638a2935b2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122102889"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion Metodu
TASK_STATE_WAIT_COMPLETION_NOTIFICATION durum bitini ayarlar veya temizler.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib ( *mscorlib.dll*)

## <a name="syntax"></a>Sözdizimi

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
