---
description: İfade değerlendiricinin gelişmiş bir sürümünü temsil eder (EE).
title: IDebugExpressionEvaluator2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2 interface
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6910b41431442819cf7641ced3763cc3ab316217
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138516"
---
# <a name="idebugexpressionevaluator2"></a>IDebugExpressionEvaluator2
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR İfade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 İfade değerlendiricinin gelişmiş bir sürümünü temsil eder (EE).

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim bir ifade değerlendiricisi tarafından uygulanır.

## <a name="methods"></a>Yöntemler
 [Bu arabirim, IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) arabiriminde yöntemlere ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Benzersiz tanımlayıcısı verilen bir hizmet nesnesini alın.|
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Belirtilen sembol sağlayıcısı tarafından belirlenen modülleri önceden yükleme.|
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|İfade değerlendiricinin (EE) hata ayıklayıcı altyapısının (DE) ölçüm ayarlarını okumak için kullandığı geri çağırma arabirimini belirtmesine olanak sağlar.|
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Hata ayıklayıcısında yüklenen ortak dil çalışma zamanının (CLR) yolunu ayarlar.|
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Bir hata ayıklama altyapısının başlatma sırasında ifade değerlendiricisine geri çağırmayı atmasına olanak sağlar.|
|[Terminate](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|İfade değerlendiriciyi durdurur ve temizler.|

## <a name="requirements"></a>Gereksinimler
 Üst Bilgi: Ee.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
