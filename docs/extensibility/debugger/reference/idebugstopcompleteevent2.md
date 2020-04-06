---
title: IDebugStopCompleteEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da3eb33d76f55310e6428a34dd09cabbc271aa68
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719450"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Hata ayıklama altyapısı (DE), bir program durdurulduğunda bu isteğe bağlı olayı oturum hata ayıklama yöneticisine (SDM) gönderebilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar

Bu arayüz Visual Studio 2005 ile tanıtıldı. Önceki sürümler asynchronous durdurma desteklemedi.

- [Durdurma,](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) çok işlemli veya çok programlı senaryolarda SDM tarafından çağrılır. Bir program SDM'ye durdurma olayı gönderdiğinde, SDM diğer programların da durmasını ister.

Stop, SDM'ye bir programın durdurulduğunu eşzamanlı olarak bildirmek için kullanılır. SDM'yi bilgilendirmek, bazen debugged program içinde hiçbir kodun çalışmadığı bir yorumlayıcı hata ayıklama motoru için yararlıdır, bu nedenle [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) eşzamanlı olarak tamamlanamaz. Hata ayıklama altyapısı bu eşzamanlı bildirimi kullanmak istiyorsa, `S_ASYNC_STOP` [Stop'tan](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)geri dönmelidir.

## <a name="requirements"></a>Gereksinimler

Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
