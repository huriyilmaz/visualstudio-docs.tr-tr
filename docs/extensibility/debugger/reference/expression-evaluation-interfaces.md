---
title: İfade Değerlendirme Arayüzleri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da230a2da87b2dd3e3a85ce3ec6c914e829ccc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736944"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Hata [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Ayıklama SDK için İfade Değerlendirme Arayüzleri aşağıda verilmiştir.

## <a name="discussion"></a>Tartışma
 Bu arabirimler, kesme modu sırasında bir çağrı yığınındaki ifadeleri değerlendirmek için kullanılır. Bunlar yalnızca ortak dil çalışma zamanı ifade değerlendiriciler (EE) için uygulanır.

 Tablodaki her arabirim, aşağıdaki listeden uygulayabilecek bileşeni gösterir:

- Hata Ayıklama Motoru (DE)

- İfade Değerlendirici (EE)

- Görsel Stüdyo (VS)

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Bir değişken için sayısal bir diğer adı temsil eder.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Bir değişken için sayısal bir diğer adı temsil eder ve bir ifade değerlendiricinin (EE) diğer ad için uygulama etki alanını elde etmesini sağlar.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Bir dizi nesnesi temsil eder.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Yönetilen bir dizi nesnesini temsil eder ve bir ifade değerlendiricinin (EE) dizi için taban diziyi (alt sınırlar) belirlemesine olanak tanır.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Hata ayıklama sembollerini bellekteki gerçek adreslere bağlayan bağlayıcıyı temsil eder.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) arabirimiyle aynı, ancak türleri, diğer adlar ve özel görüntüleyicilere erişim sağlar.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|İfade değerlendiricisini temsil eder.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|İfade değerlendiricinin (EE) geliştirilmiş bir sürümünü temsil eder.|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Gelişmiş bir parser ağacı olan bir ifade değerlendiriciyi (EE) temsil eder.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Bir işlevi temsil eder.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Bir işlevi temsil eder ve [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) arabirimini geliştirir.|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Bir ifade değerlendiricisinin (EE) hata ayıklayıcının çıkış penceresinde bir ileti görüntülemesini sağlar.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Yönetilen kod nesnesini temsil eder.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Bellek adresine bağlı herhangi bir sembolü temsil eden temel arabirim.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimiyle aynıdır, ancak ek bilgilere erişim sağlar.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Değerlendirilmeye hazır ayrışmış bir ifadeyi temsil eder.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Bir işaretçiyi temsil eder.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Ayrışdırıcı ağacındaki bir işaretçiyi temsil eder ve **IDebugPointerObject** arabirimini genişletir.|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Bir tür görselleştiricisi aracılığıyla bir türün değerini değiştirme olanağı sağlar.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Özel görüntüleyenlere ve yazı görselleştiricilerine erişim sağlar.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Bir [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) nesnesi oluşturma olanağı sağlar.|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) nesnelerinin bir koleksiyonunu temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [CLR İfade Değerlendirici Yazma](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
