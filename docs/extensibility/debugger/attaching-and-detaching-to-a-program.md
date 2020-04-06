---
title: Bir Programa Ekleme ve Ayırma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8bd6ea4b51c56a3cc42036b7bd26d34ff3a3eff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739275"
---
# <a name="attaching-and-detaching-to-a-program"></a>Bir programa ekleme ve ayırma
Hata ayıklayıcının takılması, doğru yöntem ve olay dizisini doğru özniteliklerle göndermeyi gerektirir.

## <a name="sequence-of-methods-and-events"></a>Yöntem ve olayların sırası

1. Oturum hata ayıklama yöneticisi (SDM) [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemini çağırır.

    Hata ayıklama motoru (DE) işlem `IDebugProgramNodeAttach2::OnAttach` modeline göre, yöntem aşağıdaki yöntemlerden birini döndürür ve bu yöntem daha sonra ne olacağını belirler.

    `S_FALSE` Döndürülürse, hata ayıklama altyapısı programa başarıyla iliştirilmiştir. Aksi takdirde, ekleme işlemini tamamlamak için [Ekle](../../extensibility/debugger/reference/idebugengine2-attach.md) yöntemi çağrılır.

    Döndürülürse, `S_OK` DE SDM ile aynı işlemde yüklenecektir. SDM aşağıdaki görevleri gerçekleştirir:

   1. De motor bilgilerini almak için [GetEngineInfo'yu](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) arar.

   2. DE'yi birlikte oluşturur.

   3. Aramalar [Ekle](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. DE, SDM'ye bir `EVENT_SYNC` öznitelik ile bir [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) gönderir.

3. DE, SDM'ye bir `EVENT_SYNC` öznitelik ile bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) gönderir.

4. DE, SDM'ye bir `EVENT_SYNC_STOP` öznitelik ile bir [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) gönderir.

   Bir programdan ayırmak aşağıdaki gibi basit, iki adımlı bir işlemdir:

5. SDM, [Detach'ı](../../extensibility/debugger/reference/idebugprogram2-detach.md)çağırıyor.

6. DE bir [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)gönderir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
