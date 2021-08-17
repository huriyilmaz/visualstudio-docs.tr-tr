---
title: Tür Görselleştiricisi ve Özel Görüntüleyici | Microsoft Docs
description: Tür görselleştirici bileşenleri ve verileri belirli bir biçimde görüntüleyen özel görüntüleyiciler ve aralarındaki farklar hakkında bilgi.
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
ms.openlocfilehash: a27606abf4b33acfb812d55cad83a801f05d3f2f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042620"
---
# <a name="type-visualizer-and-custom-viewer"></a>Tür görselleştiricisi ve özel görüntüleyici
Tür görselleştirici, bir veri parçasını belirli bir biçimde görüntüleyen bir bileşendir. Biçim, son kullanıcı veya üçüncü taraf görselleştirici sağlayıcı gibi görselleştiriciyi kimin uygulayan kişi olduğu tamamen size göredir.

 Özel görüntüleyici, bir veri parçasını belirli bir biçimde görüntüleyen özel ifade değerlendiricinin bir kısmıdır. Bu biçim tamamen özel görüntüleyicinin uygulayıcısı tarafından biçimlendirilmiş ve bu da biçimin ifade değerlendiricisine (EE) ait olduğu anlamına gelir.

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>İfade değerlendiricisinde tür görselleştirici desteği
 Bir EE görselleştiriciler için erişilebilir bir arabirim kümesi destekleyip tür görselleştiricileri destekler: [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) ve [IEEVisualizerDataProvider gibi arabirimler.](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Ancak, EE görselleştiricinin kendisi uygulamaktan sorumlu değildir: EE yalnızca dış görselleştiricilerin tür bilgilerine erişmesine izin verir. Bu tür görselleştiriciler EE birlikte göndererek Visual Studio üçüncü taraf satıcı tarafından veya hatta son kullanıcı tarafından sağlanan uygun yere yüklenmiş olabilir.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>İfade değerlendiricisinde özel görüntüleyici desteği
 Bir EE, veri türünü görüntülemek için kodu EE özel görüntüleyicileri de desteklemektedir. Özel görüntüleyici, verileri istenen biçimde göstermenin tüm görevlerini yerine gösteren [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) arabirimini kullanır; görüntüleyici, görüntü üzerinde tam denetime sahip olur ve hatta verilerin değiştirilmesine izin ve hatta hatta izin ve hatta olabilir. Ürün tarafından sağlanan tüm özel EE, ürün EE ile birlikte gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı bileşenleri](../../extensibility/debugger/debugger-components.md)
- [İfade değerlendirici](../../extensibility/debugger/expression-evaluator.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
