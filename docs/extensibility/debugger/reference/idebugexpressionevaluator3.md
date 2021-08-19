---
description: Gelişmiş ayrıştırıcı ağacıyla bir EE değerlendiriciyi (EE) temsil eder.
title: IDebugExpressionEvaluator3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3 interface
ms.assetid: c27c2a14-300b-4535-be22-767c83602f69
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2a5ea566a7d7741be8157e7be8f235dd17c9ede3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122138477"
---
# <a name="idebugexpressionevaluator3"></a>IDebugExpressionEvaluator3
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR İfade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Gelişmiş ayrıştırıcı ağacıyla bir EE değerlendiriciyi (EE) temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugExpressionEvaluator3 : IDebugExpressionEvaluator2
```

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Ayrıştırıcının bu sürümü, değerlendirme çerçevesinin sembol sağlayıcısını ve adresini geçer.

## <a name="methods"></a>Yöntemler
 [Bu arabirim, IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) arabiriminde yöntemlere ek olarak aşağıdaki yöntemi de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[Parse2](../../../extensibility/debugger/reference/idebugexpressionevaluator3-parse2.md)|Bir ifade dizesini, sembol sağlayıcısı ve değerlendirme çerçevesinin adresine göre ayrıştırıldı bir ifadeye dönüştürür.|

## <a name="requirements"></a>Gereksinimler
 Üst Bilgi: Ee.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
