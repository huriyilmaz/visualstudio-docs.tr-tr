---
title: IDebugReturnValueEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReturnValueEvent2
helpviewer_keywords:
- IDebugReturnValueEvent2
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0afc4284795ae8dcae7b41d9207ddc6e7c11e67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720255"
---
# <a name="idebugreturnvalueevent2"></a>IDebugReturnValueEvent2
Bu arabirim hata ayıklama altyapısı (DE) tarafından bir işlevin dışına veya üzerine çıktıktan sonra oturum hata ayıklama yöneticisine (SDM) gönderilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugReturnValueEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, dışarı veya üzerine çıkarılan bir işlevin iade değerini bildirmek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE oluşturur ve bir işlevin geri dönüş değerini bildirmek için bu olay nesnesi gönderir. Olay, debugged olan programa iliştirildiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugReturnValueEvent2`. yöntemini gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|Bir işlevden çıkarken döndürülen değeri alır.|

## <a name="remarks"></a>Açıklamalar
 Bir işlev tarafından döndürülen değer [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)çağırılarak elde edilebilir. Döndürülen değer Otomatik **ler** penceresinde görüntülenir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
