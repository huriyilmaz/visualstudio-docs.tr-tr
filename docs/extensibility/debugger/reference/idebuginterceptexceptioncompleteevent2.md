---
title: IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugInterceptExceptionCompleteEvent2
helpviewer_keywords:
- IDebugInterceptExceptionCompleteEvent2
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d98f8653d851eb338a96f969d73a2514b555f400
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890285"
---
# <a name="idebuginterceptexceptioncompleteevent2"></a>IDebugInterceptExceptionCompleteEvent2
Bu arabirim, olay ayıklama altyapısı (DE) tarafından, iptal edilmiş bir olayın işlenmesini tamamladıktan sonra oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir.

## <a name="syntax"></a>Syntax

```
IDebugInterceptExceptionCompleteEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirimi, ele alınmış bir özel durumun işlenmesini raporlamak için DE uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir. SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Aynı şekilde, ele alınamayan bir özel durumun tamamlanmasını raporlamak için bu olay nesnesini oluşturur ve gönderir. Olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 `IDebugInterceptExceptionCompleteEvent2`Arabirimi aşağıdaki yöntemleri uygular.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetInterceptCookie](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2-getinterceptcookie.md)|İşlenmiş özel durumla ilişkili benzersiz değeri döndürür.|

## <a name="remarks"></a>Açıklamalar
 Bu olay, ele geçirilebilecek bir özel durumu işlemeyi başarıyla tamamladığında, bu olay [Yakatcurrentexception](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) tarafından gönderilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
