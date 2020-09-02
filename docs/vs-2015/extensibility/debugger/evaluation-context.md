---
title: Değerlendirme bağlamı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, context
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7dae6ddcb0c75f0dcbc2207465aed522a4210159
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831745"
---
# <a name="evaluation-context"></a>Değerlendirme Bağlamı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Hata ayıklama altyapısı (DE), ifade değerlendirici 'ni (EE) çağırdığında, aşağıdaki tabloda gösterildiği gibi, [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) öğesine geçirilen üç bağımsız değişken sembolleri bulma ve değerlendirme bağlamını belirlemektir.  
  
## <a name="arguments"></a>Arguments  
  
|Bağımsız Değişken|Description|  
|--------------|-----------------|  
|`pSymbolProvider`|Sembolü tanımlamak için kullanılacak sembol işleyicisini (SH) belirleyen bir [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) arabirimi.|  
|`pAddress`|Geçerli yürütme noktasını belirten bir [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) arabirimi. Bu, yürütülen kodu içeren yöntemi bulmak için kullanılabilir.|  
|`pBinder`|Adı verilen bir simgenin değerini ve türünü bulmak için kullanılabilen bir [ıdebugciltçi](../../extensibility/debugger/reference/idebugbinder.md) arabirimi.|  
  
 `IDebugParsedExpression::EvaluateSync` elde edilen değeri ve türünü temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) arabirimi döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Anahtar Ifade değerlendirici arabirimleri](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Yerelleri görüntüleme](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)
