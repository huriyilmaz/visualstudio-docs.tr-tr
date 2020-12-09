---
title: Doğrudan bir programa iliştirme | Microsoft Docs
description: Visual Studio 'nun, Visual Studio IDE 'deki bu yordamı kullanarak zaten çalışmakta olan bir işleme hata ayıklama altyapısı ekleme işlemini nasıl uyguladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80ee40d60b5a7511c3f44c22c16e02751d9f1f36
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913782"
---
# <a name="attach-directly-to-a-program"></a>Doğrudan bir programa iliştirme
Zaten çalışmakta olan bir işlemde programlarda hata ayıklamak isteyen kullanıcılar genellikle bu işlemi izler:

1. IDE 'de **Araçlar** menüsünden **işlem hatalarını ayıkla** komutunu seçin.

    **Süreçler** iletişim kutusu görüntülenir.

2. Bir işlem seçin ve **Ekle** düğmesine tıklayın.

    **Işleme İliştir** iletişim kutusu, makinede yüklü olan tüm hata ayıklama altyapılarını (DES) listeleyerek görüntülenir.

3. Seçilen işlemde hata ayıklamak için kullanılacak DEs 'i belirtin ve ardından **Tamam**' a tıklayın.

   Hata ayıklama paketi bir hata ayıklama oturumu başlatır ve DEs listesini buna geçirir. İçindeki hata ayıklama oturumu, bu listeyi bir geri çağırma işleviyle birlikte, seçilen işleme göre geçirir ve sonra işlemin çalışan programlarını numaralandırmasını ister.

   Programlı olarak, kullanıcı isteğine yanıt olarak, hata ayıklama paketi oturum hata ayıklama Yöneticisi 'ni (SDM) başlatır ve seçilen DEs listesini buna geçirir. Liste ile birlikte hata ayıklama paketi, SDM 'yi bir [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) arabirimini geçirir. Hata ayıklama paketi, [IDebugProcess2:: Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)öğesini çağırarak des listesini seçilen işleme geçirir. SDM daha sonra işlemde çalışan programları numaralandırmak için bağlantı noktasındaki [IDebugProcess2:: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) öğesini çağırır.

   Bu noktadan itibaren, her hata ayıklama altyapısı, iki özel durum ile [bir başlatma sonrası](../../extensibility/debugger/attaching-after-a-launch.md)bir programa tam olarak eklenmiş şekilde iliştirilir.

   Verimlilik açısından, bir adres alanını SDM ile paylaşmak için uygulanan DEs, her ikisi DE iliştirilecek bir program kümesine sahip olacak şekilde gruplandırılır. Bu durumda, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , [IDebugEngine2:: Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) çağırır ve bunu iliştirilecek bir programlar dizisi ile geçirir.

   İkinci özel durum, bir DE, zaten çalışmakta olan bir programa ekleme tarafından gönderilen Başlangıç olaylarının, genellikle giriş noktası olayını içermediği durumdur.

## <a name="see-also"></a>Ayrıca bkz.
- [Başlatma sonrasında başlangıç olaylarını gönderme](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
