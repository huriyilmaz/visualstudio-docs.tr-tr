---
title: Mola Modunda İfade Değerlendirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738726"
---
# <a name="expression-evaluation-in-break-mode"></a>Kesme modunda ifade değerlendirmesi
Aşağıdaki bölümde hata ayıklama kesme modunda yken oluşan ve ifade değerlendirmesi yapması gereken işlem açıklanır.

## <a name="expression-evaluation-process"></a>İfade değerlendirme süreci
 Bir ifadeyi değerlendirmede yer alan temel adımlar şunlardır:

1. Oturum hata ayıklama yöneticisi (SDM) [iDebugStackFrame2 çağırır::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) bir ifade bağlamı arayüzü almak için, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. SDM daha sonra ayrıştılacak dize ile [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) çağırır.

3. ParseText S_OK dönmezse, hatanın nedeni döndürülür.

     -aksi takdirde-

     ParseText S_OK döndürürse, SDM daha sonra ayrıayrı ifadeden son bir değer almak için [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) veya [IDebugExpression2::EvaluateAsync'i](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) arayabilir.

    - Kullanırken, `IDebugExpression2::EvaluateSync`verilen geri arama arabirimi değerlendirmenin devam eden işlemini iletir. Son değer bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabiriminde döndürülür.

    - Kullanırken, `IDebugExpression2::EvaluateAsync`verilen geri arama arabirimi değerlendirmenin devam eden işlemini iletir. Değerlendirme tamamlandıktan sonra, EvaluateAsync geri arama yoluyla bir [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) arabirimi gönderir. Bu olay arayüzü [ile, GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)ile nihai değer sonuçları .

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama olaylarını arama](../../extensibility/debugger/calling-debugger-events.md)
