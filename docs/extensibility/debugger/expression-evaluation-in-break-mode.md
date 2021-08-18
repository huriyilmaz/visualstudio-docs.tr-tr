---
title: Kesme Modunda İfade Değerlendirmesi | Microsoft Docs
description: Hata ayıklayıcı kesme modunda olduğunda ve ifade değerlendirmesi yürütmesi gereken işlem hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 7dbf82e8586dbd12b99b2c360b1da3fb021133d6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089439"
---
# <a name="expression-evaluation-in-break-mode"></a>Kesme modunda ifade değerlendirmesi
Aşağıdaki bölümde, hata ayıklayıcı kesme modunda olduğunda oluşan ve ifade değerlendirmesini yürütmesi gereken işlem açıkmektedir.

## <a name="expression-evaluation-process"></a>İfade değerlendirme işlemi
 Aşağıda, bir ifadenin değerlendirilmesinde yer alan temel adımlar ve ardından ve ardından gelen adımlar ve ardından gelen adımlar ve ardından aşağıdakiler yer alan temel adımlar ve ardından gelen adımlar yer a adımlarını içerir

1. Oturum hata ayıklama yöneticisi (SDM), [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)ifade bağlam arabirimini almak için [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) çağrısında bulundu.

2. SDM daha sonra ayrıştırıla dizesini içeren [IDebugExpressionContext2::P arseText'i](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) çağırar.

3. ParseText bir hata S_OK hatanın nedeni döndürülür.

     -otherwise-

     ParseText S_OK, ayrıştırılmış ifadeden son bir değer almak için [SDM IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) çağrısı yapar.

    - `IDebugExpression2::EvaluateSync`kullanılırken, verilen geri çağırma arabirimi değerlendirmenin devam eden işlemini iletir. Son değer bir [IDebugProperty2 arabiriminde](../../extensibility/debugger/reference/idebugproperty2.md) döndürülür.

    - `IDebugExpression2::EvaluateAsync`kullanılırken, verilen geri çağırma arabirimi değerlendirmenin devam eden işlemini iletir. Değerlendirme tamamlandıktan sonra EvaluateAsync, geri çağırma aracılığıyla [bir IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) arabirimi gönderir. Bu olay arabirimiyle, son değer [GetResult ile sonuç verir.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
