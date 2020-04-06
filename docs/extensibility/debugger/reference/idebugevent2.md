---
title: IDebugEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6341f8003b962a7f45420b076b23623ebdaf861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729915"
---
# <a name="idebugevent2"></a>IDebugEvent2
Bu arabirim, kesme noktasında durma gibi hem kritik hata ayıklama bilgilerini hem de hata ayıklama iletisi gibi kritik olmayan bilgileri iletmek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) ve özel bağlantı noktası tedarikçisi bu arabirimi diğer tüm olay arabirimleriyle aynı nesne üzerinde uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Olay veya `IDebugEvent2` [Olay'a](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) verilen arabirim [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)kimliği (IID) bağımsız değişkenini kullanarak, oturum hata ayıklama yöneticisi (SDM) uygun olay arabirimini elde etmek için [arabirimdeki QueryInterface'i](/cpp/atl/queryinterface) çağırır.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugEvent2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Bu hata ayıklama olayının özniteliklerini alır.|

## <a name="remarks"></a>Açıklamalar
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)gibi daha özel olay arabirimleri, IDebugEvent2 arabiriminden türetilmiş değil, bunun yerine aynı `IDebugEvent2`nesne üzerinde ayrı bir arabirim olarak uygulanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
