---
description: Aşağıdakiler, Hata Ayıklama SDK'sı için Visual Studio Değerlendirme Arabirimleridir.
title: İfade Değerlendirme Arabirimleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: aa417eb1fea519647964b03af75f9f630cba4739
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065052"
---
# <a name="expression-evaluation-interfaces"></a>Expression Evaluation Interfaces
> [!IMPORTANT]
> 2015 Visual Studio de ifade değerlendiricilerini uygulamanın bu yolu kullanım dışıdır. CLR ifade değerlendiricilerini uygulama hakkında bilgi için bkz. [CLR İfade Değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Hata Ayıklama SDK'sı için İfade Değerlendirme [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Arabirimleri aşağıda velanmıştır.

## <a name="discussion"></a>Tartışma
 Bu arabirimler, kesme modu sırasında bir çağrı yığınında ifadeleri değerlendirmek için kullanılır. Bunlar yalnızca ortak dil çalışma zamanı ifade değerlendiricileri (EE).

 Tablodaki her arabirim, aşağıdaki listeden uygulayan bileşeni gösterir:

- Hata Ayıklama Altyapısı (DE)

- İfade Değerlendirici (EE)

- Visual Studio (VS)

|Arabirim|Uygulama tarafından|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Bir değişken için sayısal diğer adı temsil eder.|
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Bir değişkenin sayısal diğer adını temsil eder ve bir ifade değerlendiricinin (EE) diğer ad için uygulama etki alanını elde ettiğine olanak sağlar.|
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Bir dizi nesnesini temsil eder.|
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Yönetilen bir dizi nesnesini temsil eder ve bir ifade değerlendiricinin (EE) dizi için temel dizini (alt sınırları) belirlemesine izin verir.|
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Hata ayıklama sembollerini bellekte gerçek adreslere bağlayan bir bağlayıcıyı temsil eder.|
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|[IDebugBinder arabirimiyle aynı,](../../../extensibility/debugger/reference/idebugbinder.md) ancak türlere, diğer adlara ve özel görselleştiricilere erişim sağlar.|
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|İfade değerlendiriciyi temsil eder.|
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|İfade değerlendiricinin gelişmiş bir sürümünü temsil eder (EE).|
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Gelişmiş ayrıştırıcı ağacıyla bir EE değerlendiriciyi (EE) temsil eder.|
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Bir işlevi temsil eder.|
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Bir işlevi temsil eder ve [IDebugFunctionObject arabirimini](../../../extensibility/debugger/reference/idebugfunctionobject.md) iyiler.|
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Bir ifade değerlendiricinin (EE) hata ayıklayıcının çıkış penceresinde bir ileti görüntülemesine olanak sağlar.|
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Yönetilen bir kod nesnesini temsil eder.|
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Bir bellek adresine bağlı herhangi bir simgeyi temsil eden temel arabirim.|
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|[IDebugObject arabirimiyle aynı,](../../../extensibility/debugger/reference/idebugobject.md) ancak ek bilgilere erişim sağlar.|
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Değerlendirilmeye hazır ayrıştırmış bir ifadeyi temsil eder.|
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Bir işaretçiyi temsil eder.|
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Ayrıştırma ağacında bir işaretçiyi temsil eder ve **IDebugPointerObject arabirimini genişleter.**|
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Tür görselleştiricisi aracılığıyla bir türün değerini değiştirme olanağı sağlar.|
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Özel görüntüleyicilere ve tür görselleştiricilerine erişim sağlar.|
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|[IEEVisualizerService nesnesi oluşturma olanağı](../../../extensibility/debugger/reference/ieevisualizerservice.md) sağlar.|
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|[IDebugObject nesneleri koleksiyonunu temsil](../../../extensibility/debugger/reference/idebugobject.md) eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [CLR İfade Değerlendirici Yazma](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Tür Görselleştiricisi ve Özel Görüntüleyici](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
