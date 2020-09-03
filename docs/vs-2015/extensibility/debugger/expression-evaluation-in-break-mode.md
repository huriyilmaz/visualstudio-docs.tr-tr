---
title: Kesme modunda ifade değerlendirmesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 362e50e20519c358564d13ba169f706fe384ca5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152754"
---
# <a name="expression-evaluation-in-break-mode"></a>Kesme Modunda İfade Değerlendirme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıda, hata ayıklayıcı kesme modundayken oluşan ve ifade değerlendirmesi yapmak zorunda olan işlem açıklanmaktadır.  
  
## <a name="expression-evaluation-process"></a>İfade değerlendirme Işlemi  
 Bunlar, bir ifadeyi değerlendirmek için temel adımlardır:  
  
1. Oturum hata ayıklama Yöneticisi (SDM), [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) yöntemini çağırarak bir ifade bağlamı arabirimi elde eder, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2. SDM daha sonra [IDebugExpressionContext2::P arseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) öğesini ayrıştırılacak dizeyle çağırır.  
  
3. ParseText S_OK döndürmezse, hatanın nedeni döndürülür.  
  
     güvenmiyorsanız  
  
     ParseText S_OK dönmezse, SDM, ayrıştırılmış ifadeden son bir değer elde etmek için [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ya da [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) öğesini çağırabilir.  
  
    - Kullanılması durumunda `IDebugExpression2::EvaluateSync` , belirtilen geri çağırma arabirimi değerlendirmenin devam eden işlemini iletmek için kullanılır. Son değer bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabiriminde döndürülür.  
  
    - Kullanılması durumunda `IDebugExpression2::EvaluateAsync` , belirtilen geri çağırma arabirimi değerlendirmenin devam eden işlemini iletmek için kullanılır. Değerlendirme tamamlandıktan sonra, EvaluateAsync geri çağırma aracılığıyla bir [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) arabirimi gönderir. Bu olay arabirimiyle, son değer [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)ile elde edilebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Olaylarını Çağırma](../../extensibility/debugger/calling-debugger-events.md)
