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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 0a3e5e678edd5d616ea3ffc132dce0b8e28e3ef170242ba7c9611cb9f6920201
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121306029"
---
# <a name="type-visualizer-and-custom-viewer"></a>Tür görselleştiricisi ve özel Görüntüleyici
Tür görselleştiricisi, belirli bir biçimdeki bir veri parçasını görüntüleyen bir bileşendir. Biçim tamamen Görselleştiriciyi uygulayan, son kullanıcı veya görselin Görselleştiricisinin bir tedarikçisidir.

 Özel bir görüntüleyici, belirli bir biçimdeki verilerin bir parçasını görüntüleyen bir özel ifade değerlendiricisi bölümüdür. Bu biçim, özel görüntüleyicisinin uygulayıcısı 'na tamamıyla yapılır; bu, biçimin ifade değerlendiricisi 'nin (EE) uygulayıcısı 'na kadar olduğu anlamına gelir.

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>İfade değerlendirici içindeki tür Görselleştiriciler için destek
 EE görselleştiriciler için erişilebilen bir arabirim kümesini destekleyerek tür görselleştiricileri destekler: [ıeevisualizerservice](../../extensibility/debugger/reference/ieevisualizerservice.md) ve [ıeevisualizerdataprovider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)gibi arabirimler. ancak, EE tür görselleştiricisini uygulamaktan sorumlu değildir: EE yalnızca dış görselleştiricilerin tür bilgilerine erişmesine izin verir. bu tür görselleştiriciler EE birlikte ve başka bir üçüncü taraf satıcı tarafından sağlanan Visual Studio uygun yere yüklenmiş ve hatta son kullanıcı tarafından yüklenebilir.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>İfade değerlendiricisi içinde özel görüntüleyiciler için destek
 bir EE ayrıca, EE kendisinin veri türünü görüntüleme kodunu sağladığı özel görüntüleyiciler de destekleyebilir. Özel bir Görüntüleyici [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) arabirimini uygular, bu da her türlü biçimde verileri gösteren tüm görevleri işler. Görüntüleyici, ekran üzerinde tam denetime sahiptir ve verilerin değiştirilmesine izin verebilir. EE tarafından sağlanan tüm özel görüntüleyiciler, ürün sevk edildiğinde EE ile birlikte gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)
- [İfade değerlendirici](../../extensibility/debugger/expression-evaluator.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
