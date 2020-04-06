---
title: Değerlendirme Bağlamı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e3d02bd652d6c46b5aabe00e049e425f0921c27
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738805"
---
# <a name="evaluation-context"></a>Değerlendirme bağlamı
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi [için, bkz.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Managed expression evaluator sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Hata ayıklama altyapısı (DE) ifade değerlendiricisi (EE) çağırdığında, [EvaluateSync'e](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) geçirilen üç bağımsız değişken, aşağıdaki tabloda gösterildiği gibi sembolleri bulma ve değerlendirme bağlamını belirler.

## <a name="arguments"></a>Bağımsız Değişkenler

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`pSymbolProvider`|Sembolü tanımlamak için kullanılacak sembol işleyicisini (SH) belirten bir [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) arabirimi.|
|`pAddress`|Geçerli yürütme noktasını belirten bir [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) arabirimi. Bu arabirim, yürütülen kodu içeren yöntemi bulur.|
|`pBinder`|Adını verilen bir sembolün değerini ve türünü bulan bir [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) arabirimi.|

 `IDebugParsedExpression::EvaluateSync`elde edilen değeri ve türünü temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Anahtar ifade değerlendirici arabirimleri](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Yerel halkların görüntülenmesi](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
