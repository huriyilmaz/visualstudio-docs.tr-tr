---
title: IDebugSymbolSearchEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolSearchEvent2
helpviewer_keywords:
- IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbe99422e506fb86b0a7e1d9d3242783f3258e6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718793"
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Bu arabirim hata ayıklama motoru (DE) tarafından, hata ayıklanan bir modülün hata ayıklama sembollerinin yüklendiğini belirtmek üzere gönderilir.

## <a name="syntax"></a>Sözdizimi

```
IDebugSymbolSearchEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bir modülün sembollerinin yüklendiğini bildirmek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır. SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface kullanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE, bir modülün sembollerinin yüklendiğini bildirmek için bu olay nesnesini oluşturur ve gönderir. Olay, sdm tarafından verilen [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Arabirim `IDebugSymbolSearchEvent2` aşağıdaki yöntemi ortaya çıkarır.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Sembol aramasonuçları hakkında bilgi alır.|

## <a name="remarks"></a>Açıklamalar
 Bu olay, semboller yüklenmese bile gönderilir. Arama, `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` bu olayın işleyicisinin modülün gerçekten herhangi bir sembole sahip olup olmadığını belirlemesine olanak tanır.

 Visual Studio genellikle **modüller** penceresinde yüklenen sembollerin durumunu güncelleştirmek için bu olayı kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
