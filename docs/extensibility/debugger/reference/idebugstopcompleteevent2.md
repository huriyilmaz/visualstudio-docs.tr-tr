---
description: Hata ayıklama altyapısı (DE), bir program durdurulduğunda bu isteğe bağlı olayı oturum hata ayıklama Yöneticisi 'ne (SDM) gönderebilir.
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e4fd1826f44cb1d830ef45874b1c41c21a34895
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087151"
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
