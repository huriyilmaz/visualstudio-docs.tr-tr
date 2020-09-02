---
title: IDebugExpression2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2
helpviewer_keywords:
- IDebugExpression2 interface
ms.assetid: f5e4b124-1e30-47c8-a511-80084a02dba5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ec8b26f422ca39b771a47f8eb60ee862d7d388f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568375"
---
# <a name="idebugexpression2"></a>IDebugExpression2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim, bağlama ve değerlendirme için bir ayrıştırılmış ifadeyi temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugExpression2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Hata ayıklama altyapısı (DE), değerlendirilen bir ifadeyi göstermek için bu arabirimi uygular.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) çağrısı bu arabirimi döndürür. [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) , [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimini döndürür. Bu arabirimlere yalnızca, hata Ayıklanan program duraklatıldığında ve yığın çerçevesi kullanılabilir olduğunda erişilebilir.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugExpression2` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Bu ifadeyi zaman uyumsuz olarak değerlendirir.|  
|[Durdurulmaya](../../../extensibility/debugger/reference/idebugexpression2-abort.md)|Zaman uyumsuz ifade değerlendirmesini sonlandırır.|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Bu ifadeyi zaman uyumlu olarak değerlendirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir program durdurulduğunda, oturum hata ayıklama Yöneticisi (SDM), bir [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)çağrısıyla de bir yığın çerçevesi edinir. SDM daha sonra [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabirimini almak Için [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) öğesini çağırır. Bu, daha sonra, değerlendirilecek olan ayrıştırılmış ifadeyi temsil eden arabirimini oluşturmak için bir [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) çağrısı izler `IDebugExpression2` .  
  
 SDM, ifadeyi gerçekten değerlendirmek ve bir değer üretmek için [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) öğesini çağırır.  
  
 Bir uygulamasında, bir `IDebugExpressionContext2::ParseText` `CoCreateInstance` ifade değerlendirici başlatmak ve bir [ıdebugexpressiondeğerlendirici](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) arabirimi almak için com Işlevini kullanır (arabirimindeki örneğe bakın `IDebugExpressionEvaluator` ). Sonra da bir [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) arabirimini almak için [ayrıştırmayı](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) çağırır. Bu arabirim, `IDebugExpression2::EvaluateSync` değerlendirmesi gerçekleştirmek için ve uygulamalarında kullanılır `IDebugExpression2::EvaluateAsync` .  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)
