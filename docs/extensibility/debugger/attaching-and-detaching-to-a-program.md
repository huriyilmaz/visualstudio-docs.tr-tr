---
title: Bir programa ekleme ve ayırma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42a751e6aa70c1aacd5df598e0c0e62da3b9d14b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903152"
---
# <a name="attaching-and-detaching-to-a-program"></a>Bir programa ekleme ve ayırma
Hata ayıklayıcıyı iliştirmek için doğru özniteliklere sahip yöntemlerin ve olayların doğru dizisini göndermesi gerekir.

## <a name="sequence-of-methods-and-events"></a>Yöntemler ve olaylar dizisi

1. Oturum hata ayıklama Yöneticisi (SDM) [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemini çağırır.

    Hata ayıklama altyapısı (DE) işlem modeline göre, yöntemi, `IDebugProgramNodeAttach2::OnAttach` İleri ' nin ne olacağını belirleyen aşağıdaki yöntemlerden birini döndürür.

    `S_FALSE`Döndürülürse, hata ayıklama altyapısı programa başarıyla eklendi. Aksi [takdirde, Attach yöntemi iliştirme](../../extensibility/debugger/reference/idebugengine2-attach.md) işlemini tamamlamaya yönelik olarak çağırılır.

    `S_OK`Döndürülürse, de SDM ile aynı işleme yüklenir. SDM aşağıdaki görevleri gerçekleştirir:

   1. , Öğesinin altyapı bilgilerini almak için [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) çağırır.

   2. Birlikte bulundurun DE oluşturur.

   3. [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)çağrısı.

2. DE, SDM 'ye bir özniteliği ile bir [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) gönderir `EVENT_SYNC` .

3. DE, SDM 'ye bir özniteliği ile bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) gönderir `EVENT_SYNC` .

4. DE, SDM 'ye bir özniteliği ile bir [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) gönderir `EVENT_SYNC_STOP` .

   Bir programdan ayırmak, aşağıdaki gibi basit ve iki adımlı bir işlemdir:

5. SDM çağrısı [Ayır](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. DE bir [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)gönderir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
