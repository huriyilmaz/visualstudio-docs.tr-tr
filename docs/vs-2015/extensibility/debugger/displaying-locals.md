---
title: Yerelleri görüntüleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cdbba0cfa48792127accc71cba75f8542556d67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64793727"
---
# <a name="displaying-locals"></a>Yerel Öğeleri Görüntüleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Yürütme her zaman, kapsayan Yöntem veya geçerli yöntem olarak da bilinen bir yöntem bağlamı içinde gerçekleşir. Yürütme durakladığında, Visual Studio, her zaman yöntemin yerelleri olarak adlandırılan yerel değişkenlerin ve bağımsız değişkenlerin bir listesini almak için hata ayıklama altyapısını (DE) çağırır. Visual Studio bu yerelleri ve bunların değerlerini **Yereller** penceresinde görüntüler.  
  
 Yerelleri göstermek için, EE 'a ait [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) yöntemini çağırır ve buna bir değerlendirme bağlamı, yani bir sembol sağlayıcısı (SP), geçerli yürütme adresi ve bir Ciltçi nesnesi verir. Daha fazla bilgi için bkz. [değerlendirme bağlamı](../../extensibility/debugger/evaluation-context.md). Çağrı başarılı olursa, `IDebugExpressionEvaluator::GetMethodProperty` yöntemi geçerli yürütme adresini içeren yöntemi temsil eden bir [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) nesnesi döndürür.  
  
 Aynı şekilde, yalnızca Yereller döndürecek şekilde filtrelenmiş ve [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) yapılarının bir listesini oluşturmak için numaralandırılan bir [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) nesnesini almak için [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) çağrılır. Her yapı yerel değerin adını, türünü ve değerini içerir. Tür ve değer, görüntülenmek üzere uygun şekilde biçimlendirilen dizeler olarak depolanır. Ad, tür ve değer genellikle **Yereller** penceresinin tek bir satırında birlikte görüntülenir.  
  
> [!NOTE]
> **QuickWatch** ve **Watch** pencereleri aynı ada, değere ve türe sahip değişkenleri de görüntüler. Ancak, bu değerler yerine [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) çağırarak elde edilir `IDebugProperty2::EnumChildren` .  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Örnek Yerel Öğeler Uygulaması](../../extensibility/debugger/sample-implementation-of-locals.md)  
 Yerelleri uygulama sürecinde ilerlemek için örnekleri kullanır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Değerlendirme Bağlamı](../../extensibility/debugger/evaluation-context.md)  
 Hata ayıklama altyapısı (DE), ifade değerlendirici (EE) çağırıyorsa, üç bağımsız değişken geçirdiği açıklanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CLR İfade Değerlendirici Yazma](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
