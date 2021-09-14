---
description: Bu arabirim, oturum hata ayıklama yöneticisinin (SDM) geçerli kod konumda durıp durmayacaklarını sormak için kullanılır.
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6232618832b9cf25dcec97c1b3d3048d2e39b7de
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635142"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
Bu arabirim, oturum hata ayıklama yöneticisinin (SDM) geçerli kod konumda durıp durmayacaklarını sormak için kullanılır.

## <a name="syntax"></a>Syntax

```
IDebugCanStopEvent2 : IUknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), kaynak kodun adım uygulanmasını desteklemek için bu arabirimi uygulamaya almaktadır. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) arabiriminin bu arabirimle aynı nesne üzerinde uygulanması gerekir (SDM, arabirime erişmek için [QueryInterface](/cpp/atl/queryinterface) `IDebugEvent2` kullanır).

 Bu arabirimin uygulanması, SDM'nin [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) çağrısını hata ayıklama altyapısına iletir. Örneğin, bu işlem hata ayıklama altyapısının ileti işleme iş parçacığına gönderilen bir iletiyle yapılabilir veya bu arabirimi uygulayan nesne hata ayıklama altyapısına bir başvuru tutabilir ve bayrağı geçirilirken hata ayıklama altyapısına geri çağrı `IDebugCanStopEvent2::CanStop` yapılabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 DE bu yöntemi, DE'nin yürütmeye devam ettiği ve DE'nin kodda adım adım ilerleye devam ettiği her durumda gönderebilir. Bu olay, hata ayıklaması yapılan programa ekli olduğunda SDM tarafından sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) geri çağırma işlevi kullanılarak gönderilir.

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugCanStopEvent2` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Bu olayın nedenini alır.|
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Hata ayıklaması yapılan programın bu olayın bulunduğu konumda durdurulması (ve durdurma nedenini açıklayan bir olay göndermesi) veya yürütmeye devam edip edeceğini belirtir.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Bu olayın konumunu açıklayan belge bağlamını alır.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Bu olayın konumunu açıklayan kod bağlamını alır.|

## <a name="remarks"></a>Açıklamalar
 Kullanıcı bir işleve adım attığında ve DE orada hata ayıklama bilgisi veya hata ayıklama bilgisi yoksa DE bu arabirimi gönderir, ancak DE kaynak kodun bu konum için görüntülenemiyor olup olmadığını bilmiyor.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
