---
title: SetNotificationForWaitCompletion Metodu | Microsoft Docs
description: Hata ayıklayıcının promise stili görevler için zaman uyumsuz yöntem gövdesinin dışında adım atmanıza yardımcı olması için durum biti nasıl kullandığını öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626433"
---
# <a name="setnotificationforwaitcompletion-method"></a>SetNotificationForWaitCompletion Metodu
Durum biti için TASK_STATE_WAIT_COMPLETION_NOTIFICATION veya temizler.

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
