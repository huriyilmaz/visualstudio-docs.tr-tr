---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e988e1d64af38a55f5d946f704e1edb4df29b1d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730367"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Program durmuş olsa bile, verilen iş parçacığı üzerinde ifade değerlendirmesinin gerçekleşmesine izin verir (veya izin vermese).

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT WatchForExpressionEvaluationOnThread( 
   IDebugProgram2*       pOriginatingProgram,
   DWORD                 dwTid,
   DWORD                 dwEvalFlags,
   IDebugEventCallback2* pExprCallback,
   BOOL                  fWatch
);
```

```csharp
int WatchForExpressionEvaluationOnThread( 
   IDebugProgram2       pOriginatingProgram,
   uint                  dwTid,
   uint                  dwEvalFlags,
   IDebugEventCallback2 pExprCallback,
   int                   fWatch
);
```

## <a name="parameters"></a>Parametreler
`pOriginatingProgram`\
[içinde] Bir ifadeyi değerlendiren programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`dwTid`\
[içinde] İş parçacığının tanımlayıcısını belirtir.

`dwEvalFlags`\
[içinde] [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) numaralandırmasından değerlendirmenin nasıl yapılacağını belirten bayrakların birleşimi.

`pExprCallback`\
[içinde] İfade değerlendirmesi sırasında meydana gelen hata ayıklama olaylarını göndermek için kullanılacak bir [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`fWatch`\
[içinde] Sıfır olmayan ise`TRUE`( ), tarafından `dwTid`tanımlanan iş parçacığı üzerinde ifade değerlendirmesine izin verir; aksi takdirde,`FALSE`sıfır ( ) bu iş parçacığı üzerinde ifade değerlendirmesi disallows.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Oturum hata ayıklama yöneticisi (SDM) `pOriginatingProgram` bir ifadeyi değerlendirmek için parametre tarafından tanımlanan bir program istediğinde, bu yöntemi çağırarak diğer tüm ekli programları bildirir.

 Bir programdaki ifade değerlendirmesi, işlev değerlendirmesi veya herhangi bir `IDispatch` özelliğin değerlendirilmesi nedeniyle kodun başka bir programda çalışmasına neden olabilir. Bu nedenle, bu yöntem, iş parçacığı bu programda durdurulabilir olsa bile ifade değerlendirme çalışmasına ve tamamlanmasına olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
