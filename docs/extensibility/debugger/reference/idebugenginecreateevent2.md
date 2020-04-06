---
title: IDebugEngineCreateEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineCreateEvent2
helpviewer_keywords:
- IDebugEngineCreateEvent2 interface
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 41a964f1e08fc2e88ac9a1d211e4b3e36b32c5b8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730603"
---
# <a name="idebugenginecreateevent2"></a>IDebugEngineCreateEvent2
Hata ayıklama altyapısı (DE), DE'nin bir örneği oluşturulduğunda bu arabirimi oturum hata ayıklama yöneticisine (SDM) gönderir.

## <a name="syntax"></a>Sözdizimi

```
IDebugEngineCreateEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 DE, bu arabirimi normal işlemlerinin bir parçası olarak uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır (SDM `QueryInterface` `IDebugEvent2` arabirime erişmek için yöntemi kullanır).

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE anında olduğunda DE bu olay nesnesini oluşturur ve gönderir. Olay, sdm tarafından verilen [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugEngineCreateEvent2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|Yeni oluşturulan hata ayıklama altyapısını (DE) temsil eden nesneyi alır.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
