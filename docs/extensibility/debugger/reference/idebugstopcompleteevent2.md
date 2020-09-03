---
title: IDebugStopCompleteEvent2 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80719450"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2

Hata ayıklama altyapısı (DE), bir program durdurulduğunda bu isteğe bağlı olayı oturum hata ayıklama Yöneticisi 'ne (SDM) gönderebilir.

## <a name="syntax"></a>Syntax

```
IDebugStopCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları

Bu arabirim, Visual Studio 2005 ile tanıtılmıştır. Önceki yayınlar zaman uyumsuz durdurmayı desteklemiyor.

- [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) , çok işlem veya çok program senaryolarında SDM tarafından çağırılır. Bir program SDM 'ye durdurma olayı gönderdiğinde, SDM diğer programları da durdurur.

Durdur, bir programın durdurulma SDM 'yi zaman uyumsuz olarak bildirmek için kullanılır. SDM 'nin bir yorumlayıcı hata ayıklama altyapısı için yararlı olduğunu, bazen hata ayıklaması yapılan programın içinde hiçbir kod çalışmadığı, bu nedenle [Durdur](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) zaman uyumlu olarak tamamlanamayacağını bildiren bir hata oluştu. Bir hata ayıklama altyapısı bu zaman uyumsuz bildirimi kullanmak isterse, `S_ASYNC_STOP` [stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)'tan dönmesi gerekir.

## <a name="requirements"></a>Gereksinimler

Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
