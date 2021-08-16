---
title: Doğrudan Bir Program | Microsoft Docs
description: Visual Studio IDE'de bu yordamı kullanarak zaten çalışan bir işleme hata ayıklama altyapısı eklemenin nasıl Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 189a5e56e189240b014249e7e4b980bf3e8cce034c3647b59711d7a6ae2e84e1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403365"
---
# <a name="attach-directly-to-a-program"></a>Doğrudan bir programa ekleme
Zaten çalışan bir işlemde programlarda hata ayıklamak isteyen kullanıcılar genellikle şu işlemi takip eder:

1. IDE'de Araçlar **menüsünden Hata Ayıklama** İşlemleri **komutunu** seçin.

    İşlemler **iletişim** kutusu görüntülenir.

2. Bir işlem seçin ve Ekle **düğmesine** tıklayın.

    Makinede **yüklü olan** tüm hata ayıklama altyapılarını (DES) listelenin, İşleme Ekle iletişim kutusu görüntülenir.

3. Seçilen işlemde hata ayıklamak için kullanmak üzere DE'leri belirtin ve ardından Tamam'a **tıklayın.**

   Hata ayıklama paketi bir hata ayıklama oturumu başlatır ve DE listesini bu oturuma iletir. Hata ayıklama oturumu sırasıyla bu listeyi bir geri çağırma işleviyle birlikte seçili işleme iletir ve ardından işlemden çalışan programlarını listelesini sorar.

   Program aracılığıyla, kullanıcı isteğine yanıt olarak, hata ayıklama paketi oturum hata ayıklama yöneticisinin (SDM) örneğini sağlar ve seçili DE'ler listesini buna iletir. Listeyle birlikte, hata ayıklama paketi SDM'ye [bir IDebugEventCallback2 arabirimini](../../extensibility/debugger/reference/idebugeventcallback2.md) iletir. Hata ayıklama paketi, [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)çağırarak DE listesini seçili işleme iletir. Ardından SDM, işlemde çalışan programları numaralandırarak bağlantı noktası üzerinde [IDebugProcess2::EnumPrograms'ı](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) arar.

   Bu noktadan sonra, her hata ayıklama altyapısı bir programa, iki özel durum dışında bir başlatmadan sonra ekleme'de tam [olarak](../../extensibility/debugger/attaching-after-a-launch.md)ayrıntılı olarak ayrıntılı olarak iliştirilmiş olur.

   Verimlilik için, SDM ile bir adres alanı paylaşmak için uygulanan DE'ler, her DE'nin ekleyecekleri bir dizi program olacak şekilde gruplandı. Bu durumda [IDebugProcess2,](../../extensibility/debugger/reference/idebugprocess2.md) [IDebugEngine2::Attach'i](../../extensibility/debugger/reference/idebugengine2-attach.md) çağırarak bir dizi program iletir.

   İkinci özel durum, zaten çalışan bir programa DE eklemesi tarafından gönderilen başlatma olaylarının genellikle giriş noktası olayı içermeme durumudur.

## <a name="see-also"></a>Ayrıca bkz.
- [Başlatmadan sonra başlatma olaylarını gönderme](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
