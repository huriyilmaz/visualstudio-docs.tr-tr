---
title: Tür görselleştiricisi ve özel Görüntüleyici | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a85be2978abe35e91096b55fba5ec5281be25fbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185313"
---
# <a name="type-visualizer-and-custom-viewer"></a>Tür Görselleştiricisi ve Özel Görüntüleyici
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tür görselleştiricisi, verileri çok özel bir biçimde görüntüleyen bir bileşendir. Bu biçim, görselleştiricinin uygulayıcısı 'na tamamen sahiptir, son kullanıcı veya görselleştiricilerin bir üçüncü taraf tedarikçisidir.  
  
 Özel bir görüntüleyici, belirli bir biçimde veri parçasını görüntüleyen bir özel ifade değerlendiricisi bölümüdür. Bu biçim, özel görüntüleyicisinin uygulayıcısı 'na tamamıyla yapılır; bu, biçimin ifade değerlendiricisi (EE) uygulayıcısı 'na kadar olduğu anlamına gelir.  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Ifade değerlendirici içindeki tür Görselleştiriciler için destek  
 Bir EE, Görselleştiriciler için erişilebilen bir arabirim kümesini destekleyerek tür Görselleştiriciler destekleyebilir: [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) ve [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)gibi arabirimler. Ancak, EE 'ın tür Görselleştiricisinin kendisini uygulamaktan sorumlu olmadığına not edin: EE yalnızca dış görselleştiricilerin tür bilgilerine erişmesine izin verir. Bu tür Görselleştiriciler, EE ile birlikte sevk edilebilir ve Visual Studio 'da, başka bir üçüncü taraf satıcı tarafından sağlanan ve hatta son kullanıcı tarafından sağlanan uygun yere yüklenmiş olabilir.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Ifade Değerlendiricisi içinde özel görüntüleyiciler için destek  
 EE Ayrıca, EE 'ın veri türünü görüntülemek için kod sağladığı özel görüntüleyiciler de destekleyebilir. Özel bir Görüntüleyici [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) arabirimini uygular, bu da her türlü biçimde verileri gösteren tüm görevleri işler. Görüntüleyici, ekran üzerinde tam denetime sahiptir ve verilerin değiştirilmesine de izin verebilir. EE tarafından sağlanan tüm özel görüntüleyiciler, ürün sevk edildiğinde EE ile gelir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)   
 [İfade değerlendirici](../../extensibility/debugger/expression-evaluator.md)   
 [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [Ieevisualizerhizmeti](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
