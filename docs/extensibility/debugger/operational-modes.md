---
title: İşlem Modları | Microsoft Docs
description: IDE'nin çalışabiliyor olduğu üç mod hakkında bilgi edinebilirsiniz. Bu mod tasarım modu, çalıştırma modu ve kesme modudur.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 559df92545f4c14eb0575e7ef758e73028349b76
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899114"
---
# <a name="operational-modes"></a>İşletimsel modlar
IDE'nin çalışabiliyor olduğu üç mod vardır:

- [Tasarım modu](#vsconoperationalmodesanchor1)

- [Çalıştırma modu](#vsconoperationalmodesanchor2)

- [Kesme modu](#vsconoperationalmodesanchor3)

  Özel hata ayıklama altyapınız (DE) bu modlar arasında nasıl geçişler yapmak, geçiş mekanizmalarını tanımanızı gerektiren bir uygulama kararıdır. DE bu modları doğrudan uygulayabilir veya uygulamayabilir. Bu modlar, de'den gelen kullanıcı eylemlerini veya olayları temel alan hata ayıklama paket modlarıdır. Örneğin, çalıştırma modundan kesme moduna geçiş, DE'den bir durdurma olayı ile uzuyor. Kesme modundan çalıştırma moduna veya adım moduna geçiş, Adım veya Yürütme gibi işlemler gerçekleştiren kullanıcı tarafından teşvik ediliyor. DE geçişleri hakkında daha fazla bilgi için [bkz. Yürütme denetimi.](../../extensibility/debugger/control-of-execution.md)

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Tasarım modu
 Tasarım modu, uygulamanıza hata ayıklama Visual Studio ayarlandırarak hata ayıklamanın çalıştırılamayan durumudur.

 Tasarım modu sırasında yalnızca birkaç hata ayıklama özelliği kullanılır. Geliştirici kesme noktaları ayarlamayı veya izleme ifadeleri oluşturmayı seçebilir. IDE tasarım modundayken DE hiçbir zaman yüklenmez veya çağrılmaz. DE ile etkileşim yalnızca çalıştırma ve kesme modları sırasında sürer.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Çalıştırma modu
 Çalıştırma modu, bir program IDE'de bir hata ayıklama oturumunda çalıştır olduğunda gerçekleşir. Uygulama sonlandırmaya kadar, bir kesme noktası isabet olana kadar veya bir özel durum ana kadar çalışır. Uygulama sonlandırmak için çalıştır geldiğinde DE tasarım moduna geçer. Bir kesme noktası isabet olduğunda veya bir özel durum thrown, DE kesme moduna geçer.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Kesme Modu
 Hata ayıklama programının yürütülmesi askıya alınırsa kesme modu oluşur. Kesme modu, geliştiriciye kesme anında uygulamanın anlık görüntüsünü sunar ve geliştiricinin uygulamanın durumunu analiz edip uygulamanın çalışma durumunu değiştirmesini sağlar. Geliştirici kodu görüntüleyemez ve düzenleyebilir, verileri inceler veya değiştirebilir, uygulamayı yeniden başlatabilir, yürütmeyi bitirebilir veya aynı noktadan yürütmeye devam eder.

 DE zaman uyumlu bir durdurma olayı gönderdiğinde kesme modu girilir. Durdurma olayları olarak da adlandırılan zaman uyumlu durdurma olayları, oturum hata ayıklama yöneticisine (SDM) ve hata ayıklaması yapılan uygulamanın kodu yürütmeyi durdurmuş olduğunu IDE'ye bildirme. [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) ve [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) arabirimleri, olayları durdurma örnekleridir.

 Durdurma olayları, hata ayıklayıcıyı kesme modundan çalıştırma veya adım moduna alan aşağıdaki yöntemlerden biri çağrısıyla devam eder:

- [Yürütme](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Adım](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Devam et](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Adım modu
 Adım modu, program bir sonraki kod satırına veya işlevin içine, üzerine veya dışından adım attığında gerçekleşir. Adım yöntemi çağrılarak bir adım [yürütülür.](../../extensibility/debugger/reference/idebugprocess3-step.md) Bu yöntem, `DWORD` giriş parametreleri olarak [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) ve [STEPKIND](../../extensibility/debugger/reference/stepkind.md) numaralarını belirten s gerektirir.

 Program bir sonraki kod satırına veya bir işleve başarıyla ilerler veya imleç veya ayarlanmış bir kesme noktası için çalıştırılırsa, DE otomatik olarak kesme moduna geri döner.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütme denetimi](../../extensibility/debugger/control-of-execution.md)
