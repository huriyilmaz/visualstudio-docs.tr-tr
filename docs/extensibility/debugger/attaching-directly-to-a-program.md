---
title: Doğrudan Bir Programa Bağlanma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9a5699ee81b8c8ae36bcf492e93467615a9e89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739255"
---
# <a name="attach-directly-to-a-program"></a>Doğrudan bir programa ekleme
Zaten çalışan bir işlemde programları hata ayıklamak isteyen kullanıcılar genellikle bu işlemi izler:

1. IDE'de, **Araçlar** menüsünden **Hata Ayıklama İşlemleri** komutunu seçin.

    **İşlemler** iletişim kutusu görüntülenir.

2. Bir işlem seçin ve **Ekle** düğmesini tıklatın.

    **İşleme Ekle** iletişim kutusu, makineye yüklenen tüm hata ayıklama motorlarını (DEs) listeleyen görüntülenir.

3. Seçili işlemi hata ayıklamak için kullanılacak DEs'leri belirtin ve ardından **Tamam'ı**tıklatın.

   Hata ayıklama paketi hata ayıklama oturumu başlatır ve DEs listesini ona geçirir. Sırayla hata ayıklama oturumu, bir geri arama işleviyle birlikte bu listeyi seçili işleme geçirir ve ardından işlemden çalışan programlarını sıralamasını ister.

   Programlı olarak, kullanıcı isteğine yanıt olarak, hata ayıklama paketi oturum hata ayıklama yöneticisini (SDM) anında alar ve seçili DEs listesini ona geçirir. Listeyle birlikte hata ayıklama paketi SDM bir [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) arabiriminden geçer. Hata ayıklama [paketi, IDebugProcess2::Attach'ı](../../extensibility/debugger/reference/idebugprocess2-attach.md)arayarak DEs listesini seçili işleme geçer. SDM daha sonra [iDebugProcess2::EnumPrograms'ı](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) işlemde çalışan programları sayısallandırmak için bağlantı noktasında çağırır.

   Bu noktadan itibaren, her hata ayıklama motoru, iki istisna dışında, [bir başlatmadan sonra Ekleme'de](../../extensibility/debugger/attaching-after-a-launch.md)ayrıntılı olarak ayrıntılı bir programa eklenir.

   Verimlilik için, bir adres alanını SDM ile paylaşmak için uygulanan DE'ler, her DE'nin ekleyeceği bir dizi programa sahip olacak şekilde gruplandırılır. Bu durumda, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) [iDebugEngine2 çağırır::Ekle](../../extensibility/debugger/reference/idebugengine2-attach.md) ve eklemek için programlar bir dizi geçer.

   İkinci özel durum, bir DE tarafından gönderilen başlangıç olaylarının zaten çalışan bir programa iliştirilmesi genellikle giriş noktası olayını içermemesidir.

## <a name="see-also"></a>Ayrıca bkz.
- [Başlatmadan sonra başlangıç etkinliklerigönderme](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Görevleri hata ayıklama](../../extensibility/debugger/debugging-tasks.md)
