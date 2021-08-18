---
description: Program durdurulmuş olsa bile, belirli bir iş parçacığında ifade değerlendirmesinin gerçekleşmesine izin verir (veya buna izin verir).
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c6f7563adf23ce6a75c504cca675e0f6ac7e9e84
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127226"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Program durdurulmuş olsa bile, belirli bir iş parçacığında ifade değerlendirmesinin gerçekleşmesine izin verir (veya buna izin verir).

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
[in] Bir ifadeyi değerlendiren programı temsil eden [bir IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`dwTid`\
[in] İş parçacığının tanımlayıcısını belirtir.

`dwEvalFlags`\
[in] Değerlendirmenin nasıl gerçekleştirilecek [olduğunu belirten EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) numaralamasında yer alan bayrakların birleşimi.

`pExprCallback`\
[in] İfade değerlendirmesi sırasında oluşan hata ayıklama olaylarını göndermek için kullanılacak [bir IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`fWatch`\
[in] Sıfır olmayan ( ), tarafından tanımlanan iş parçacığında ifade değerlendirmesine izin verir; aksi takdirde, sıfır ( ) o iş `TRUE` `dwTid` `FALSE` parçacığında ifade değerlendirmesine izin verir.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Oturum hata ayıklama yöneticisi (SDM), bir ifadeyi değerlendirmek için parametresiyle tanımlanan bir program sorduğunda, bu yöntemi çağırarak diğer tüm ekli `pOriginatingProgram` programları bilgisine sahip olur.

 Bir programda ifade değerlendirmesi, işlev değerlendirmesi veya herhangi bir özelliğin değerlendirilmesi nedeniyle kodun başka bir programda çalışmasına neden `IDispatch` olabilir. Bu nedenle, bu yöntem iş parçacığı bu programda durdurulmuş olsa bile ifade değerlendirmenin çalışmasına ve tamamlanmasına olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
