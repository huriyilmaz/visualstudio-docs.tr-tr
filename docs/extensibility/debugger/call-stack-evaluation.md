---
title: Çağrı yığını değerlendirmesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5557d7eae0ffe54b0f01f1f9e95935d71455229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739182"
---
# <a name="call-stack-evaluation"></a>Çağrı yığını değerlendirmesi
Kesme modu sırasında çağrı yığınının yığın çerçevelerini görüntülemek için, [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) yöntemini uygulamanız gerekir.

## <a name="methods-for-evaluation"></a>Değerlendirme yöntemleri
 Basit bir hata ayıklama altyapısı (DE) için yalnızca bir yığın çerçevesi olabilir. Kesme modunda yığın çerçevesini incelemek için aşağıdaki [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)yöntemlerini uygulamanız gerekir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Yığın çerçevesinin kod bağlamını alır. Kod bağlamı, yığın çerçevesindeki geçerli yönerge işaretçisini temsil eder.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Yığın çerçevesinin belge bağlamını alır. Belge bağlamı, yığın çerçevesinin kaynak kodundaki geçerli konumu temsil eder. Bir programda durdurulduğunda kaynak kodu görüntülemek için gerekir.|

 Bu yöntemler, bağlamla ilgili birkaç arabirim ve yöntemin uygulanmasını gerektirir. Bu nedenle, [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) yöntemini ve aşağıdaki [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)yöntemlerini uygulamanız gerekir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Belge bağlamının dosya deyimleri aralığını alır.|

 Kod bağlamlarını listelemek için tüm [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)yöntemlerini uygulamanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
