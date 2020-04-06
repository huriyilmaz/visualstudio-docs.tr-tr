---
title: Yazı Görselleştirici ve Özel Görüntüleyici | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712460"
---
# <a name="type-visualizer-and-custom-viewer"></a>Görselleştirici ve özel görüntüleyici yazın
Tür görselleştiricisi, bir veri parçasını belirli bir biçimde görüntüleyen bir bileşendir. Biçim tamamen görselleştiriciyi kimin uyguladığına bağlıdır, son kullanıcı veya görselleştiricilerin üçüncü taraf tedarikçisi olsun.

 Özel görüntüleyici, belirli bir biçimde bir veri parçası görüntüleyen özel bir ifade değerlendiricinin bir parçasıdır. Bu biçim tamamen özel görüntüleyicinin uygulayıcısına bağlıdır, bu da biçimin ifade değerlendiricinin (EE) uygulayıcısına bağlı olduğu anlamına gelir.

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>İfade değerlendiricisindeki tip görselleştiricileri desteği
 EE, görüntüleyiciler tarafından erişilebilen bir arayüz kümesini destekleyerek tip görselleştiricilerini destekler: [IEEVisualizerService ve IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerservice.md) gibi arayüzler. [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Ancak, EE tür görselleştiricinin kendisini uygulamaktan sorumlu değildir: EE yalnızca dış görselleştiricilerin tür bilgilerine erişmesine izin verir. Bu tür görselleştiriciler EE ile birlikte sevk edilebilir ve Visual Studio'da uygun bir yere kurulabilir, başka bir üçüncü taraf satıcı veya hatta son kullanıcı tarafından sağlanabilir.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>İfade değerlendiricisinde özel görüntüleyenler için destek
 Bir EE, EE'nin veri türünü görüntülemek için kodu kendisinin sağladığı özel görüntüleyenleri de destekleyebilir. Özel bir görüntüleyici, verileri istenilen biçimde göstermenin tüm görevlerini yerine getiren [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) arabirimini uygular; görüntüleyici ekran üzerinde tam kontrole sahiptir ve hatta verilerin değiştirilmesine izin verebilir. EE tarafından sağlanan tüm özel görüntüleyenler, ürün sevk edildiğinde EE ile birlikte gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md)
- [İfade değerlendiricisi](../../extensibility/debugger/expression-evaluator.md)
- [Hata ayıklama motoru](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
