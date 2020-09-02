---
title: Bir programa ekleme ve ayırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e232a6f7fcb8813670ca6d949fdb6b3287bb79c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146454"
---
# <a name="attaching-and-detaching-to-a-program"></a>Programa Ekleme ve Programdan Ayırma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Olaylarını Çağırma](../../extensibility/debugger/calling-debugger-events.md)
