---
title: Değerlendirme bağlamı | Microsoft Docs
description: "Hata ayıklama altyapısı ifade değerlendirici ' i çağırdığında, bağımsız değişkenler sembolleri bulmak ve değerlendirmek için bağlam belirleme: pSymbolProvider, pAddress ve Pciltçi."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0957a204a83ab72aabe14fe4a70d8e758e83a08f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99840593"
---
# <a name="evaluation-context"></a>Değerlendirme bağlamı
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Hata ayıklama altyapısı (DE), ifade değerlendirici 'ni (EE) çağırdığında, aşağıdaki tabloda gösterildiği gibi, [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) öğesine geçirilen üç bağımsız değişken sembolleri bulma ve değerlendirme bağlamını tespit ediyor.

## <a name="arguments"></a>Bağımsız değişkenler

|Bağımsız Değişken|Description|
|--------------|-----------------|
|`pSymbolProvider`|Sembolü tanımlamak için kullanılacak sembol işleyicisini (SH) belirleyen bir [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) arabirimi.|
|`pAddress`|Geçerli yürütme noktasını belirten bir [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) arabirimi. Bu arabirim, yürütülen kodu içeren yöntemi bulur.|
|`pBinder`|Adı verilen bir simgenin değerini ve türünü bulan bir [ıdebugciltçi](../../extensibility/debugger/reference/idebugbinder.md) arabirimi.|

 `IDebugParsedExpression::EvaluateSync` elde edilen değeri ve türünü temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Anahtar ifade değerlendirici arabirimleri](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Yerelleri görüntüleme](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
