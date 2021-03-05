---
description: Bir ifade değerlendirici 'nin (EE) gelişmiş bir sürümünü temsil eder.
title: IDebugExpressionEvaluator2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 150ede0d3063fa8905b7cdfa5d67da16c0f68eed
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102152240"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bir ifade değerlendirici 'nin (EE) gelişmiş bir sürümünü temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu arabirim, bir ifade değerlendiricisi tarafından uygulanır.

## <a name="methods"></a>Yöntemler
 Bu arabirim, [ıdebugexpressiondeğerlendirici](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) arabirimindeki yöntemlere ek olarak aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Benzersiz tanımlayıcısı verilen bir hizmet nesnesini alır.|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Belirtilen sembol sağlayıcısı tarafından belirlenen modülleri önceden yükler.|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|, Hata ayıklayıcı altyapısının (DE) ölçüm ayarlarını okumak için kullanacağı geri çağırma arabirimini belirtmesini sağlar.|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Hata ayıklayıcıda yüklenen ortak dil çalışma zamanının (CLR) yolunu ayarlar.|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Bir hata ayıklama altyapısının başlatma sırasında ifade değerlendirici öğesine geri çağırma işlemi yapmasını sağlar.|
|[Terminate](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|İfade değerlendiricisi 'ni durdurup temizler.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
