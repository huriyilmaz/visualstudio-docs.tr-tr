---
description: Bu arabirim, kesme noktası sırasında durdurma gibi kritik hata ayıklama bilgilerini ve hata ayıklama iletisi gibi kritik olmayan bilgileri iletişim kurmak için kullanılır.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 9aca1f8ce1b8dbf4575f4ba9aecd4f714b0dbf83
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079057"
---
# <a name="idebugevent2"></a>IDebugEvent2
Bu arabirim, kesme noktası sırasında durdurma gibi kritik hata ayıklama bilgilerini ve hata ayıklama iletisi gibi kritik olmayan bilgileri iletişim kurmak için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) ve özel bağlantı noktası sağlayıcı, bu arabirimi diğer tüm olay arabirimleri ile aynı nesne üzerinde uygulama.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Olay veya Olay'a verilen arabirim [](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) kimliği (IID) bağımsız değişkenlerini [kullanarak,](../../../extensibility/debugger/reference/idebugportevents2-event.md)uygun olay arabirimini almak için oturum hata ayıklama yöneticisi (SDM) [arabiriminde QueryInterface'i](/cpp/atl/queryinterface) `IDebugEvent2` arar.

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugEvent2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Bu hata ayıklama olayı için öznitelikleri alır.|

## <a name="remarks"></a>Açıklamalar
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)gibi daha belirli olay arabirimleri, IDebugEvent2 arabiriminden türetilmez, ancak bunun yerine ile aynı nesnede ayrı bir arabirim olarak `IDebugEvent2` uygulanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [Olay](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Olay](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
