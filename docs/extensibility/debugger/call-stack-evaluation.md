---
title: Çağrı Yığını Değerlendirme | Microsoft Docs
description: EnumFrameInfo yöntemini ve kesme modu sırasında çağrı yığınının yığın çerçevelerini görüntülemek için nasıl uygulandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: a196560a3b0ee2fc10733b112540b1f9ff619e67
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145997"
---
# <a name="call-stack-evaluation"></a>Çağrı yığını değerlendirmesi
Kesme modu sırasında çağrı yığınının yığın çerçevelerini görüntülemek için [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) yöntemini uygulamalısınız.

## <a name="methods-for-evaluation"></a>Değerlendirme yöntemleri
 Basit bir hata ayıklama altyapısı (DE) için yalnızca bir yığın çerçevesi olabilir. Kesme modu sırasında yığın çerçevesini incelemek için aşağıdaki [IDebugStackFrame2 yöntemlerini uygulamalısınız.](../../extensibility/debugger/reference/idebugstackframe2.md)

|Yöntem|Açıklama|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Bir yığın çerçevesi için kod bağlamını alır. Kod bağlamı, bir yığın çerçevesindeki geçerli yönerge işaretçisini temsil eder.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Bir yığın çerçevesi için belge bağlamını alır. Belge bağlamı, bir yığın çerçevesinin kaynak kodundaki geçerli konumu temsil eder. Bir programda durdurulurken kaynak kodu görüntülemek için gereklidir.|

 Bu yöntemler, bağlamla ilgili çeşitli arabirimlerin ve yöntemlerin uygulanmasını gerektirir. Bu nedenle, [GetDocumentContext yöntemini ve](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) aşağıdaki [IDebugDocumentContext2 yöntemlerini uygulamalısınız.](../../extensibility/debugger/reference/idebugdocumentcontext2.md)

|Yöntem|Açıklama|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Belge bağlamının dosya deyimi aralığını alır.|

 Kod bağlamlarını numaralandırabilirsiniz, [IEnumDebugCodeContexts2'nin tüm yöntemlerini uygulamanız gerekir.](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme denetimi ve durum değerlendirmesi](../../extensibility/debugger/execution-control-and-state-evaluation.md)
