---
title: IDebugCanStopEvent2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0a3710756f02d7c622be94bab6c3056fb051827
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734515"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Bu arabirim, oturum hata ayıklama yöneticisine (SDM) geçerli kod konumunda durup durmayacağını sormak için kullanılır.

## <a name="syntax"></a>Sözdizimi

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE) kaynak kodu üzerinden adımlama desteklemek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde uygulanmalıdır (SDM `IDebugEvent2` [arabirime](/cpp/atl/queryinterface) erişmek için QueryInterface'i kullanır).

 Bu arabirimin uygulanması hata ayıklama motoruna SDM'nin [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) çağrısını iletmelidir. Örneğin, bu hata ayıklama altyapısının ileti işleme iş parçacığına gönderilen bir ileti yle yapılabilir veya bu arabirimi uygulayan nesne hata ayıklama altyapısına `IDebugCanStopEvent2::CanStop`bir başvuru tutabilir ve bayrak geçirilirken hata ayıklama altyapısına geri çağrı yapabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE bu yöntemi her de yürütmeye devam etmesi istendiğinde ve DE kod üzerinden adım la basınca gönderebilir. Bu olay, sdm tarafından sağlanan [iDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri arama işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugCanStopEvent2`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Bu olayın nedenini alır.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Debulama yapılan programın bu olayın bulunduğu yerde durması (ve durdurma nedenini açıklayan bir olay gönderme) veya yürütmeye devam etmesi gerekip gerekmediğini belirtir.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Bu olayın konumunu açıklayan belge bağlamını alır.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Bu olayın konumunu açıklayan kod bağlamını alır.|

## <a name="remarks"></a>Açıklamalar
 Kullanıcı bir işleve adım atarsa ve DE orada hata ayıklama bilgisi yoksa debug bilgisi yoksa DE bu arabirimi gönderir, ancak DE bu konum için kaynak kodun görüntülenip görüntülenmeyeceğini bilmez.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: msdbg.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
