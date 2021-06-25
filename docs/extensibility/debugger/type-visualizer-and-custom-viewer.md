---
title: Tür görselleştiricisi ve özel Görüntüleyici | Microsoft Docs
description: Belirli bir biçimde verileri görüntüleyen tür görselleştiricisi bileşenleri ve özel görüntüleyiciler hakkında bilgi edinin ve bunlar arasındaki farkları öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c18bb49c740362d42a4a54bf52f6998629acb0c0
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904428"
---
# <a name="type-visualizer-and-custom-viewer"></a>Tür görselleştiricisi ve özel Görüntüleyici
Tür görselleştiricisi, belirli bir biçimdeki bir veri parçasını görüntüleyen bir bileşendir. Biçim tamamen Görselleştiriciyi uygulayan, son kullanıcı veya görselin Görselleştiricisinin bir tedarikçisidir.

 Özel bir görüntüleyici, belirli bir biçimdeki verilerin bir parçasını görüntüleyen bir özel ifade değerlendiricisi bölümüdür. Bu biçim, özel görüntüleyicisinin uygulayıcısı 'na tamamıyla yapılır; bu, biçimin ifade değerlendiricisi (EE) uygulayıcısı 'na kadar olduğu anlamına gelir.

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>İfade değerlendirici içindeki tür Görselleştiriciler için destek
 Bir EE Görselleştiriciler için erişilebilen bir arabirim kümesini destekleyerek tür görselleştiricileri destekler: [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) ve [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)gibi arabirimler. Ancak, EE türü Görselleştirici kendisini uygulamaktan sorumlu değildir: EE yalnızca dış görselleştiricilerin tür bilgilerine erişmesine izin verir. Bu tür Görselleştiriciler, EE ile birlikte sevk edilebilir ve Visual Studio 'da, başka bir üçüncü taraf satıcı tarafından sağlanan ve hatta son kullanıcı tarafından sağlanan uygun yere yüklenmiş olabilir.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>İfade değerlendiricisi içinde özel görüntüleyiciler için destek
 EE Ayrıca, EE 'ın veri türünü görüntülemek için kod sağladığı özel görüntüleyiciler de destekleyebilir. Özel bir Görüntüleyici [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) arabirimini uygular, bu da her türlü biçimde verileri gösteren tüm görevleri işler. Görüntüleyici, ekran üzerinde tam denetime sahiptir ve verilerin değiştirilmesine izin verebilir. EE tarafından sağlanan tüm özel görüntüleyiciler, ürün sevk edildiğinde EE ile gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)
- [İfade değerlendirici](../../extensibility/debugger/expression-evaluator.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
