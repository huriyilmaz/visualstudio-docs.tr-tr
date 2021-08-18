---
title: Değerlendirme Bağlamı | Microsoft Docs
description: 'Hata ayıklama altyapısı ifade değerlendiriciyi çağıran bağımsız değişkenler sembolleri bulma ve değerlendirme bağlamını belirler: pSymbolProvider, pAddress ve pBinder.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 001a7a5b1e4d044e389317900a9192586575b44ed19caa5e09aa6ceca30a9c15
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121417827"
---
# <a name="evaluation-context"></a>Değerlendirme bağlamı
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR ifade değerlendiricileri ve](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) [Yönetilen ifade değerlendirici örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Hata ayıklama altyapısı (DE) ifade değerlendiricisini (EE) çağırsa, [EvaluateSync'e](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) geçirilen üç bağımsız değişken, aşağıdaki tabloda gösterildiği gibi sembolleri bulma ve değerlendirme bağlamını belirler.

## <a name="arguments"></a>Bağımsız değişkenler

|Bağımsız Değişken|Açıklama|
|--------------|-----------------|
|`pSymbolProvider`|Sembolü tanımlamak için kullanılacak sembol işleyicisini (SH) belirten [bir IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) arabirimi.|
|`pAddress`|Geçerli [yürütme noktasını belirten bir IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) arabirimi. Bu arabirim, yürütülen kodu içeren yöntemi bulur.|
|`pBinder`|Adına göre bir sembolün değerini ve türünü bulan [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) arabirimi.|

 `IDebugParsedExpression::EvaluateSync` , elde edilen değeri ve türünü temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [Anahtar ifadesi değerlendirici arabirimleri](../../extensibility/debugger/key-expression-evaluator-interfaces.md)
- [Yerelleri görüntüleme](../../extensibility/debugger/displaying-locals.md)
- [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
