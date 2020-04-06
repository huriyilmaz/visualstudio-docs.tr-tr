---
title: Hata Ayıklama başlatılması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738452"
---
# <a name="launch-the-debugger"></a>Hata ayıklamayı başlatın
Hata ayıklayıcıyı başlatmak, doğru öznitelikleriyle doğru yöntem ve olay sırasını göndermeyi gerektirir.

## <a name="sequences-of-methods-and-events"></a>Yöntem ve olay dizileri

1. Hata Ayıklama yöneticisi (SDM), **Hata Ayıklama** menüsünü seçip sonra **Başlat'ı**seçerek çağrılır. Daha fazla bilgi için [bkz.](../../extensibility/debugger/launching-a-program.md)

2. SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemini çağırır.

3. Hata ayıklama motoru (DE) işlem `IDebugProgramNodeAttach2::OnAttach` modeline göre, yöntem aşağıdaki yöntemlerden birini döndürür ve bu yöntem daha sonra ne olacağını belirler.

     Dönerse, `S_FALSE` hata ayıklama motoru (DE) sanal makine nin işleminde yüklenir.

     -veya-

     İade `S_OK` edilirse, DE SDM'nin işlem de yüklenmesi gerekir. SDM daha sonra aşağıdaki görevleri gerçekleştirir:

    1. De motor bilgilerini almak için [GetEngineInfo'yu](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) arar.

    2. DE'yi birlikte oluşturur.

    3. Aramalar [Ekle](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. DE, SDM'ye bir `EVENT_SYNC` öznitelik ile bir [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) gönderir.

5. DE, SDM'ye bir `EVENT_SYNC` öznitelik ile bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) gönderir.

6. DE, SDM'ye bir `EVENT_SYNC` öznitelik ile bir [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) gönderir.

7. DE, SDM'ye bir `EVENT_SYNC` öznitelik ile bir [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) gönderir.

8. DE, SDM'ye bir `EVENT_SYNC` öznitelik ile bir [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) gönderir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
- [Program başlatma](../../extensibility/debugger/launching-a-program.md)
