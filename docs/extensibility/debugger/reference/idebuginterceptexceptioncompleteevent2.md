---
description: De, kesme olayı işlemeyi tamamlayan oturum hata ayıklama yöneticisine (SDM) hata ayıklama altyapısı (DE) tarafından bu arabirim gönderilir.
title: IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e7f8f49af391bafaa94745fa82c286e762dd2b91
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725185"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
De, kesme olayı işlemeyi tamamlayan oturum hata ayıklama yöneticisine (SDM) hata ayıklama altyapısı (DE) tarafından bu arabirim gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugInterceptExceptionCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, araya bir özel durum işlemenin tamam olduğunu rapor etmek için bu arabirimini uygulamaya almaktadır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi, bu arabirimle aynı nesne üzerinde uygulanarak gerçekleştir gerekir. SDM, [arabirime erişmek için QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, araya bir özel durumun tamamlanmasını rapor etmek için bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklaması yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Arabirimi `IDebugInterceptExceptionCompleteEvent2` aşağıdaki yöntemleri kullanır.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|Tanıtıcı özel durumla ilişkili benzersiz değeri döndürür.|

## <a name="remarks"></a>Açıklamalar
 Bu olay, bu yöntem kesme özel durumu işlemeyi başarıyla tamamlamış olduğunda [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) tarafından gönderilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
