---
title: 'IDebugExpression2:: EvaluateAsync | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e084152f6215878816739f46dc91fa322cf9c94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158437"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, ifadeyi zaman uyumsuz olarak değerlendirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwFlags`  
 'ndaki İfade değerlendirmesini denetleyen [Evalflags](../../../extensibility/debugger/reference/evalflags.md) numaralandırmasındaki bayrakların birleşimi.  
  
 `pExprCallback`  
 'ndaki Bu parametre her zaman bir null değerdir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde bir hata kodu döndürür. Tipik bir hata kodu:  
  
|Hata|Açıklama|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Şu anda başka bir ifade değerlendirilemekte ve eşzamanlı ifade değerlendirmesi desteklenmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, ifade değerlendirmesini başlattıktan hemen sonra döndürmelidir. İfade başarıyla değerlendirildiğinde, [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) veya [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)aracılığıyla sağlanan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Event geri çağırması için bir [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) gönderilmesi gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `CExpression` [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) arabirimini uygulayan basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir.  
  
```cpp#  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
