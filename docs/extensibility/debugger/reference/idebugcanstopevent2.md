---
description: Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) geçerli kod konumunda durdurulup durdurulmayacağını sormak için kullanılır.
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d46f4aacdc886e455771f5a30ba82b941b29c957
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154853"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) geçerli kod konumunda durdurulup durdurulmayacağını sormak için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Hata ayıklama altyapısı (DE), kaynak kodu üzerinden adımlamayı desteklemek için bu arabirimi uygular. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabirimi bu arabirimle aynı nesne üzerinde UYGULANMALıDıR (SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) kullanır `IDebugEvent2` ).

 Bu arabirimin uygulanması için, SDM 'nin [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) çağrısını hata ayıklama altyapısına iletmesi gerekir. Örneğin, bu, hata ayıklama altyapısının ileti işleme iş parçacığına postalanan bir iletiyle yapılabilir veya bu arabirimi uygulayan nesne hata ayıklama altyapısına bir başvuru tutabilir ve geçirilen bayrak ile hata ayıklama altyapısına geri çağrı yapabilir `IDebugCanStopEvent2::CanStop` .

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Aynı zamanda, her seferinde yürütmeye devam etmesi istenir ve DE kod aracılığıyla adımla bu yöntem de gönderebilir. Bu olay, hata ayıklamakta olan programa eklendiğinde SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) callback işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugCanStopEvent2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Bu olayın nedenini alır.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Hata ayıklamakta olan programın bu olayın konumunda durmasının gerekip gerekmediğini belirtir (ve durdurma nedenini açıklayan bir olay gönderin) veya yürütmeye devam edin.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Bu olayın konumunu açıklayan belge bağlamını alır.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Bu olayın konumunu açıklayan kod bağlamını alır.|

## <a name="remarks"></a>Açıklamalar
 Bu, Kullanıcı bir işleve bir işlev halinde gösterildiğinde ve bir hata ayıklama bilgisi yoksa veya hata ayıklama bilgileri bulursa ve bu konum için kaynak kodun görüntülenip görüntülenemediğini bilmez, bu arabirimi DE gönderir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
