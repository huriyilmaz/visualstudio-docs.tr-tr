---
title: Hata ayıklayıcı başlatılıyor | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738452"
---
# <a name="launch-the-debugger"></a>Hata ayıklayıcıyı Başlat
Hata ayıklayıcıyı başlatmak için doğru özniteliklerle doğru yöntem ve olay sırası gönderilmesi gerekir.

## <a name="sequences-of-methods-and-events"></a>Yöntem ve olay dizileri

1. Oturum hata ayıklama Yöneticisi (SDM), **hata ayıklama** menüsü seçilerek ve ardından **Başlat**' ı seçerek çağrılır. Daha fazla bilgi için bkz. [Program başlatma](../../extensibility/debugger/launching-a-program.md).

2. SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) metodunu çağırır.

3. Hata ayıklama altyapısı (DE) işlem modeline göre, yöntemi, `IDebugProgramNodeAttach2::OnAttach` İleri ' nin ne olacağını belirleyen aşağıdaki yöntemlerden birini döndürür.

     `S_FALSE`Şunu döndürürse, hata ayıklama altyapısı (de), sanal makine işlemine yüklenir.

     -veya-

     `S_OK`Döndürürse, de SDM 'nin işlem içinde yüklenmesi gerekir. SDM daha sonra aşağıdaki görevleri gerçekleştirir:

    1. , Öğesinin altyapı bilgilerini almak için [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) çağırır.

    2. Birlikte bulundurun DE oluşturur.

    3. [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)çağrısı.

4. DE, SDM 'ye bir özniteliği ile bir [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) gönderir `EVENT_SYNC` .

5. DE, SDM 'ye bir özniteliği ile bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) gönderir `EVENT_SYNC` .

6. DE, SDM 'ye bir özniteliği ile bir [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) gönderir `EVENT_SYNC` .

7. DE, SDM 'ye bir özniteliği ile bir [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) gönderir `EVENT_SYNC` .

8. DE, SDM 'ye bir özniteliği ile bir [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) gönderir `EVENT_SYNC` .

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
- [Program başlatma](../../extensibility/debugger/launching-a-program.md)
