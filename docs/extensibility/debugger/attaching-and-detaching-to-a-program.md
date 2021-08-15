---
title: Program Ekleme ve Ayırma | Microsoft Docs
description: Bir hata ayıklayıcı eklemek için uygun özniteliklerle doğru yöntem ve olay sırasını göndermeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 678b2a3582eef3b803a838728a43a7e1444de064b3e29778fd5f077ab7c386f7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121324164"
---
# <a name="attaching-and-detaching-to-a-program"></a>Programa ekleme ve ayırma
Hata ayıklayıcıyı eklemek için doğru yöntem ve olay sırasının uygun özniteliklerle gönderilmesi gerekir.

## <a name="sequence-of-methods-and-events"></a>Yöntemler ve olaylar dizisi

1. Oturum hata ayıklama yöneticisi (SDM) [OnAttach yöntemini](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) çağırıyor.

    Yöntem, hata ayıklama altyapısı (DE) işlem modeline bağlı olarak aşağıdaki yöntemlerden birini döndürür ve bundan sonra `IDebugProgramNodeAttach2::OnAttach` ne olacağını belirler.

    `S_FALSE`döndürülürse, hata ayıklama altyapısı programa başarıyla eklenmiştir. Aksi [takdirde, ekleme](../../extensibility/debugger/reference/idebugengine2-attach.md) işlemini tamamlamak için Attach yöntemi çağrılır.

    `S_OK`döndürülürse DE, SDM ile aynı işlemde yüklenir. SDM aşağıdaki görevleri gerçekleştirir:

   1. DE'nin altyapı bilgilerini almak için [GetEngineInfo'ya](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) çağrılar.

   2. DE'i birlikte oluşturur.

   3. Attach [çağrılarını çağıran.](../../extensibility/debugger/reference/idebugengine2-attach.md)

2. DE, bir [özniteliğiyle SDM'ye bir IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) `EVENT_SYNC` gönderir.

3. DE, bir [özniteliğiyle SDM'ye bir IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) `EVENT_SYNC` gönderir.

4. DE, bir [özniteliğiyle SDM'ye bir IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) `EVENT_SYNC_STOP` gönderir.

   Bir programdan ayırmak, aşağıdaki gibi basit ve iki adımlı bir işlemdir:

5. SDM, [Ayır'a çağrılar.](../../extensibility/debugger/reference/idebugprogram2-detach.md)

6. DE bir [IDebugProgramDestroyEvent2 gönderir.](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
