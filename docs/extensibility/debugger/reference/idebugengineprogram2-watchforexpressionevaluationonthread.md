---
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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ae9e10da02ab0bbef6be0fed5b9d505bf1b3e268
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892677"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Program durdurulmuş olsa bile, belirtilen iş parçacığında ifade değerlendirmesinin yapılmasına izin verir (veya izin vermez).

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
'ndaki Bir ifadeyi değerlendiren programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.

`dwTid`\
'ndaki İş parçacığının tanımlayıcısını belirtir.

`dwEvalFlags`\
'ndaki [Evalflags](../../../extensibility/debugger/reference/evalflags.md) numaralandırmasındaki, değerlendirmenin nasıl gerçekleştirileceğini belirten bayrakların birleşimi.

`pExprCallback`\
'ndaki İfade değerlendirmesi sırasında oluşan hata ayıklama olaylarını göndermek için kullanılacak bir [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`fWatch`\
'ndaki Sıfır olmayan ( `TRUE` ), tarafından tanımlanan iş parçacığında ifade değerlendirmesi yapılmasına izin verir `dwTid` ; Aksi takdirde sıfır ( `FALSE` ), bu iş parçacığında ifade değerlendirmesine izin vermez.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Oturum hata ayıklama Yöneticisi (SDM), bir ifadeyi değerlendirmek için parametresi tarafından tanımlanan bir programı istediğinde, `pOriginatingProgram` Bu yöntemi çağırarak diğer tüm ekli programları bilgilendirir.

 Tek bir programdaki ifade değerlendirmesi, işlev değerlendirmesi veya herhangi bir özellik değerlendirmesi nedeniyle kodun başka bir şekilde çalışmasına neden olabilir `IDispatch` . Bu nedenle, bu yöntem, iş parçacığı bu programda durdurulmuş olsa bile, bu yöntem, ifade değerlendirmesinin çalışmasına ve tamamlanmasını sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
