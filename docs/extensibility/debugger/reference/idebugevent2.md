---
description: Bu arabirim, bir kesme noktasında durdurma gibi kritik hata ayıklama bilgilerini ve hata ayıklama iletisi gibi kritik olmayan bilgileri iletişim kurmak için kullanılır.
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f5406c70703b594236dba47539e5cc76bbe67a73
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065768"
---
# <a name="idebugevent2"></a>IDebugEvent2
Bu arabirim, bir kesme noktasında durdurma gibi kritik hata ayıklama bilgilerini ve hata ayıklama iletisi gibi kritik olmayan bilgileri iletişim kurmak için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE) ve özel bağlantı noktası sağlayıcısı, bu arabirimi diğer tüm olay arabirimleriyle aynı nesneye uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) veya [olaya](../../../extensibility/debugger/reference/idebugportevents2-event.md)VERILEN arabirim kimliği (IID) bağımsız değişkenini kullanarak, oturum hata ayıklama Yöneticisi (SDM), [](/cpp/atl/queryinterface) `IDebugEvent2` uygun olay arabirimini elde etmek için arabirimdeki QueryInterface 'i çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugEvent2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Bu hata ayıklama olayının özniteliklerini alır.|

## <a name="remarks"></a>Açıklamalar
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)gibi daha özel olay arabirimleri, IDebugEvent2 arabiriminden türemez, ancak bunun yerine aynı nesne üzerinde ayrı bir arabirim olarak uygulanır `IDebugEvent2` .

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
