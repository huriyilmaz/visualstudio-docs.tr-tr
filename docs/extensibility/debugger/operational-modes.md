---
title: İşletimsel modlar | Microsoft Docs
description: IDE 'nin çalışacağı, tasarım modu, çalıştırma modu ve kesme modu olan üç mod hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e0187a02dd14966ee9354d8865991531f1d66ae6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884903"
---
# <a name="operational-modes"></a>İşletimsel modlar
IDE 'nin çalışması için aşağıdaki gibi üç mod vardır:

- [Tasarım modu](#vsconoperationalmodesanchor1)

- [Çalıştırma modu](#vsconoperationalmodesanchor2)

- [Kesme modu](#vsconoperationalmodesanchor3)

  Bu modlar arasındaki özel hata ayıklama altyapısı (DE) geçişleriniz, geçiş mekanizmalarına alışmanızı gerektiren bir uygulama karardır. Bu modları doğrudan uygulayamayabilir. Bu modlar aslında Kullanıcı eylemine veya olayları temel alan paket modlarında hata ayıklamasız. Örneğin, çalıştırma modundan kesme moduna geçiş, DE ' dan bir durdurma olayı tarafından içe işlenir. Kesme modundan ya da adım moduna geçiş, Kullanıcı tarafından, adım veya yürütme gibi işlemleri gerçekleştiren işlemler tarafından geçersiz. DE geçişleri hakkında daha fazla bilgi için bkz. [yürütmenin denetimi](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Tasarım modu
 Tasarım modu, Visual Studio hata ayıklamanın çalışma dışı durumudur ve bu sırada uygulamanızdaki hata ayıklama özelliklerini ayarlayabilirsiniz.

 Tasarım modu sırasında yalnızca birkaç hata ayıklama özelliği kullanılır. Geliştirici, kesme noktaları ayarlamayı veya gözcü ifadeleri oluşturmayı seçebilir. IDE tasarım modundayken DE hiçbir şekilde yüklenilmez veya çağrılmaz. Yalnızca çalıştırma ve kesme modları sırasında aynı şekilde etkileşim gerçekleşir.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Çalıştırma modu
 Çalışma modu, bir program IDE 'deki bir hata ayıklama oturumunda çalıştığında oluşur. Uygulama sonlandırana kadar, bir kesme noktasına vurana veya bir özel durum oluşturuluncaya kadar çalışır. Uygulama sonlandırılmak üzere çalıştığında, DE tasarım moduna geçer. Kesme noktası isabet edildiğinde veya bir özel durum oluştuğunda kesme moduna geçiş yapar.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Kesme modu
 Hata ayıklama programının yürütülmesi askıya alındığında kesme modu oluşur. Kesme modu, geliştirici, kesme sırasında uygulamanın bir anlık görüntüsünü sunar ve geliştiricinin uygulamanın durumunu çözümlemesine ve uygulamanın nasıl çalışacağını değiştirmesine olanak tanır. Geliştirici kodu görüntüleyebilir ve düzenleyebilir, verileri inceleyebilir veya değiştirebilir, uygulamayı başlatabilir, yürütmeyi sonlandırabilir veya aynı noktadan yürütmeye devam edebilir.

 DE zaman uyumlu durdurma olayı gönderdiğinde kesme modu girilir. Olayları durdurma da denilen zaman uyumlu durdurma olayları, oturum hata ayıklama Yöneticisi 'ne (SDM) ve hata ayıklamakta olan uygulamanın kod yürütmeyi durdurduğunu bildirir. [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) ve [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) arabirimleri olayları durdurma örnekleridir.

 Olayları durdurma, hata ayıklayıcıyı kesme modundan çalışacak şekilde veya adım moduna geçirerek aşağıdaki yöntemlerden birine bir çağrı ile devam eder:

- [Yürütme](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Adım](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Devam et](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Adım modu
 Adım modu, program sonraki kod satırında veya bir işlevin içine, üzerine ya da dışına çıktığında oluşur. Yöntem [adımı](../../extensibility/debugger/reference/idebugprocess3-step.md)çağırarak bir adım yürütülür. Bu yöntem `DWORD` , giriş parametreleri olarak [stepunit](../../extensibility/debugger/reference/stepunit.md) ve [stepkind](../../extensibility/debugger/reference/stepkind.md) numaralandırmaları belirten s gerektirir.

 Program bir sonraki kod satırına veya bir işleve başarıyla adımla ya da imleç ya da bir küme kesme noktasına çalışırsa, DE otomatik olarak kesme moduna geçer.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütmenin denetimi](../../extensibility/debugger/control-of-execution.md)
