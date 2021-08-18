---
description: Hata ayıklama altyapısı (DE), program ilk kullanıcı kodu yönergesini yürütmekle ilgili olduğunda bu arabirimi oturum hata ayıklama yöneticisine (SDM) gönderir.
title: IDebugEntryPointEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 041d8f7d4237504ff0201bd0b5069293c0b59d63
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089140"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Hata ayıklama altyapısı (DE), program ilk kullanıcı kodu yönergesini yürütmekle ilgili olduğunda bu arabirimi oturum hata ayıklama yöneticisine (SDM) gönderir.

## <a name="syntax"></a>Syntax

```
IDebugEntryPointEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bu arabirimi normal işlemlerinin bir parçası olarak uygulamaya almaktadır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi, bu arabirimle aynı nesne üzerinde uygulanarak uygulanarak. SDM, [arabirime erişmek için QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, hata ayıklaması yapılan program yüklendiğinde ve kullanıcı kodunun ilk yönergelerini yürütmeye hazır olduğunda bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklaması yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevi kullanılarak gönderilir.

## <a name="remarks"></a>Açıklamalar
- [Program ilk yönergeyi yürütmek üzereyken IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) gönderilir. Örneğin, `IDebugEntryPoint2` program kullanıcının işlevini yürütmek üzereyken `main` gönderilir.

 DE `IDebugEntryPointEvent2` gönderdiğinde, geçerli kod konumu gibi kullanıcı kodunun ilk yönergesinde yer alalıdır. `main`

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
