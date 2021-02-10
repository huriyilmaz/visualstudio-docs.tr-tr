---
title: İfade değerlendirme arabirimleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a048d11b09ee873a2f5a11e35db78f68df6ad680
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936944"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Hata ayıklama SDK 'Sı için Ifade değerlendirme arabirimleri aşağıda verilmiştir [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

## <a name="discussion"></a>Tartışma
 Bu arabirimler, kesme modunda bir çağrı yığınında ifadeleri değerlendirmek için kullanılır. Yalnızca ortak dil çalışma zamanı ifadesi değerlendiricileri (EE) için uygulanır.

 Tablodaki her arabirim, aşağıdaki listeden uygulayabilirler bileşeni gösterir:

- Hata ayıklama altyapısı (DE)

- İfade değerlendiricisi (EE)

- Visual Studio (VS)

|Arabirim|Uygulayan|Description|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Bir değişken için sayısal diğer adı temsil eder.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Bir değişken için sayısal diğer adı temsil eder ve diğer ad için uygulama etki alanını almak üzere bir ifade değerlendirici (EE) sağlar.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Bir dizi nesnesini temsil eder.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Yönetilen bir dizi nesnesini temsil eder ve bir ifade değerlendiricisi (EE) dizi için temel dizini (alt sınır) belirlemesine izin verir.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Hata ayıklama sembollerini bellekteki gerçek adreslere bağlayan bir cildi temsil eder.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|[Idebugciltçi](../../../extensibility/debugger/reference/idebugbinder.md) arabirimiyle aynı ancak türlere, diğer adlara ve özel görselleştiricilere erişim sağlar.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|İfade değerlendiricisi temsil eder.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Bir ifade değerlendirici 'nin (EE) gelişmiş bir sürümünü temsil eder.|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Gelişmiş ayrıştırıcı ağacı ile bir ifade değerlendirici (EE) temsil eder.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Bir işlevi temsil eder.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Bir işlevi temsil eder ve [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimini geliştirir.|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Bir ifade değerlendiricisi (EE) hata ayıklayıcının çıkış penceresinde bir ileti görüntülemesini sağlar.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Yönetilen bir kod nesnesini temsil eder.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Bir bellek adresine bağlanan herhangi bir sembolü temsil eden temel arabirim.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimiyle aynı ancak ek bilgilere erişim sağlar.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Değerlendirilen bir ayrıştırılmış ifadeyi temsil eder.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Bir işaretçiyi temsil eder.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Bir ayrıştırma ağacındaki bir işaretçiyi temsil eder ve **Ihata ayıklama Gpoınterobject** arabirimini genişletir.|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Bir tür görselleştiricisi aracılığıyla bir türün değerini değiştirme olanağı sağlar.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Özel görüntüleyenler ve tür Görselleştiriciler için erişim sağlar.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Bir [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) nesnesi oluşturma olanağı sağlar.|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnelerinin bir koleksiyonunu temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [CLR İfade Değerlendirici Yazma](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
