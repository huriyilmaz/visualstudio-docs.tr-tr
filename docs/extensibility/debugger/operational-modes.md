---
title: Çalışma Modları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027152b2b2fc18b509a687220e5d963ea1b7e721
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738285"
---
# <a name="operational-modes"></a>Çalışma modları
IDE'nin çalışabileceği üç mod vardır:

- [Tasarım modu](#vsconoperationalmodesanchor1)

- [Çalıştırma modu](#vsconoperationalmodesanchor2)

- [Kesme modu](#vsconoperationalmodesanchor3)

  Özel hata ayıklama altyapınızın (DE) bu modlar arasında nasıl geçiş yaptığı, geçiş mekanizmalarına aşina olmanızı gerektiren bir uygulama kararıdır. DE bu modları doğrudan uygulayabilir veya uygulamayabilir. Bu modlar, kullanıcı eylemine veya DE'deki olaylara dayalı olarak geçiş yapan paket hata ayıklama modlarıdır. Örneğin, çalışma modundan kesme moduna geçiş, DE'den bir durdurma olayı tarafından teşvik edilir. Kesme moduveya adım moduna geçiş, Adım veya Yürüt gibi işlemleri gerçekleştiren kullanıcı tarafından teşvik edilir. DE geçişleri hakkında daha fazla bilgi için [yürütme denetimi](../../extensibility/debugger/control-of-execution.md)ne bakın.

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a>Tasarım modu
 Tasarım modu, Visual Studio hata ayıklamanın çalışmayan durumudur ve bu süre zarfında uygulamanızda hata ayıklama özelliklerini ayarlayabilirsiniz.

 Tasarım modu sırasında yalnızca birkaç hata ayıklama özelliği kullanılır. Geliştirici kesme noktaları ayarlamayı veya saat ifadeleri oluşturmayı seçebilir. IDE tasarım modundayken DE hiçbir zaman yüklenmez veya çağrılmaz. DE ile etkileşim yalnızca çalışma ve kesme modları sırasında gerçekleşir.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a>Çalıştırma modu
 Çalışma modu, bir program IDE'de hata ayıklama oturumunda çalıştığında oluşur. Uygulama sonlandırma, kesme noktası vurulana veya özel durum atılına kadar çalışır. Uygulama sonlandırmaya çalıştığında, DE tasarım moduna geçer. Bir kesme noktası vurulduğunda veya bir özel durum atıldığında, DE kesme moduna geçer.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a>Kesme Modu
 Hata ayıklama programının yürütülmesi askıya aldığında kesme modu oluşur. Kesme modu, geliştiriciye mola sırasında uygulamanın anlık görüntüsünü sunar ve geliştiricinin uygulamanın durumunu analiz etmesine ve uygulamanın nasıl çalışacağını değiştirmesine olanak tanır. Geliştirici kodu görüntüleyebilir ve düzenlemeyapabilir, verileri inceleyebilir veya değiştirebilir, uygulamayı yeniden başlatabilir, yürütmeyi sonlandırabilir veya yürütmeyi aynı noktadan sürdürebilir.

 De eşzamanlı durdurma olayı gönderdiğinde kesme modu girilir. Olayları durdurma olarak da adlandırılan eşzamanlı durdurma olayları, oturum hata ayıklama yöneticisine (SDM) ve Hata Ayıklanan uygulamanın kodu yürütmeyi durdurduğunu Bildiren. [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) ve [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) arabirimleri durdurma olayları örnekleridir.

 Durdurma olayları, hata ayıklayıcıyı kesme modundan çalıştırma veya adım moduna geçiş yapan aşağıdaki yöntemlerden birine yapılan bir çağrıyla devam edilir:

- [Yürütmek](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Adım](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Devam](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a>Adım modu
 Adım modu, program bir sonraki kod satırına veya bir işlevin içine, üstünden veya dışına adım attığında oluşur. Bir adım, yöntem [Adım'ı](../../extensibility/debugger/reference/idebugprocess3-step.md)çağırarak yürütülür. Bu yöntem, `DWORD` [stepunit](../../extensibility/debugger/reference/stepunit.md) ve [STEPKIND](../../extensibility/debugger/reference/stepkind.md) yıllarını giriş parametreleri olarak belirtmeyi gerektirir.

 Program bir sonraki kod satırına veya bir işleve başarılı bir şekilde adım attığında veya imleçveya bir ayar kesme noktasına çalıştığında, DE otomatik olarak kesme moduna geri döner.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütmenin kontrolü](../../extensibility/debugger/control-of-execution.md)
