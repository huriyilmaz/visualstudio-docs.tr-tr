---
title: Ifade Değerlendiricisi uygulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
ms.assetid: e9ada7be-845e-4baa-bf8f-e4890e7ba490
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82e6f1fb4e6f78c7fb1f614144f9a836d9676fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64789156"
---
# <a name="implementing-an-expression-evaluator"></a>ifade Değerlendiricisi Uygulama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Bir ifadeyi değerlendirmek, hata ayıklama altyapısı (DE), sembol sağlayıcısı (SP), Ciltçi nesnesi ve ifade değerlendirici (EE) arasında karmaşık bir karşılıklı yürütme işlemi olur. Bu dört bileşen, bir bileşen tarafından uygulanan ve başka bir bileşen tarafından tüketilen arabirimlere bağlanır.  
  
 EE, bir dize biçimindeki öğesinden DE bir ifade alır ve bunu ayrıştırır veya değerlendirir. EE, DE tarafından tüketilen aşağıdaki arayüzleri uygular:  
  
- [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
- [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
  EE, sembol ve nesne değerlerini almak için DE tarafından sağlanan cilt nesnesini çağırır. EE, ve tarafından uygulanan aşağıdaki arayüzleri kullanır:  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
- [IDebugArrayObject](../../extensibility/debugger/reference/idebugarrayobject.md)  
  
- [IDebugFunctionObject](../../extensibility/debugger/reference/idebugfunctionobject.md)  
  
- [IDebugPointerObject](../../extensibility/debugger/reference/idebugpointerobject.md)  
  
- [IDebugManagedObject](../../extensibility/debugger/reference/idebugmanagedobject.md)  
  
- [IEnumDebugObjects](../../extensibility/debugger/reference/ienumdebugobjects.md)  
  
- [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
  EE, [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)uygular. `IDebugProperty2` Yerel değişken, temel öğe veya nesne gibi bir ifade değerlendirmesinin sonucunu Visual Studio 'ya açıklamak için, daha sonra **Yereller**, **İzle**veya **hemen** penceresinde uygun bilgileri görüntüleyen bir mekanizma sağlar.  
  
  SP, bilgi istediğinde DE Bu, EE 'a verilir. SP, aşağıdaki arabirimler ve bunların türevleri gibi adresleri ve alanları tanımlayan arayüzleri uygular:  
  
- [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)  
  
- [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
- [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
  EE bu arabirimlerin tümünü tüketir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İfade Değerlendiricisi Uygulama Stratejisi](../../extensibility/debugger/expression-evaluator-implementation-strategy.md)  
 İfade değerlendirici (EE) uygulama stratejisi için üç adımlı bir işlem tanımlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR İfade Değerlendirici Yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
