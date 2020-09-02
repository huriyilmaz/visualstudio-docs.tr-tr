---
title: 'IDebugEngineProgram2:: WatchForExpressionEvaluationOnThread | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ebc513ead1ae911147217becd8f541cb11cd5585
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431478"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Program durdurulmuş olsa bile, belirtilen iş parçacığında ifade değerlendirmesinin yapılmasına izin verir (veya izin vermez).  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametreler  
 `pOriginatingProgram`  
 'ndaki Bir ifadeyi değerlendiren programı temsil eden bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) nesnesi.  
  
 `dwTid`  
 'ndaki İş parçacığının tanımlayıcısını belirtir.  
  
 `dwEvalFlags`  
 'ndaki [Evalflags](../../../extensibility/debugger/reference/evalflags.md) numaralandırmasındaki, değerlendirmenin nasıl gerçekleştirileceğini belirten bayrakların birleşimi.  
  
 `pExprCallback`  
 'ndaki İfade değerlendirmesi sırasında oluşan hata ayıklama olaylarını göndermek için kullanılacak bir [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.  
  
 `fWatch`  
 'ndaki Sıfır olmayan ( `TRUE` ), tarafından tanımlanan iş parçacığında ifade değerlendirmesi yapılmasına izin verir `dwTid` ; Aksi takdirde sıfır ( `FALSE` ), bu iş parçacığında ifade değerlendirmesine izin vermez.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Oturum hata ayıklama Yöneticisi (SDM), bir ifadeyi değerlendirmek için parametresi tarafından tanımlanan bir programı istediğinde, `pOriginatingProgram` Bu yöntemi çağırarak diğer tüm ekli programları bilgilendirir.  
  
 Tek bir programdaki ifade değerlendirmesi, işlev değerlendirmesi veya herhangi bir özellik değerlendirmesi nedeniyle kodun başka bir şekilde çalışmasına neden olabilir `IDispatch` . Bu nedenle, bu yöntem, iş parçacığı bu programda durdurulmuş olsa bile, bu yöntem, ifade değerlendirmesinin çalışmasına ve tamamlanmasını sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
