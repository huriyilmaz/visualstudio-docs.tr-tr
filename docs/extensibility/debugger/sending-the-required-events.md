---
title: Gerekli Olayları Gönderme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc83b47e53607fe1111ececbbf892c96f7bbb639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713003"
---
# <a name="send-the-required-events"></a>Gerekli olayları gönderme
Gerekli olayları göndermek için bu yordamı kullanın.

## <a name="process-for-sending-required-events"></a>Gerekli olayları gönderme işlemi
 Hata ayıklama altyapısı (DE) oluştururken ve bir programa iliştirilirken, bu sırada aşağıdaki olaylar gereklidir:

1. Bir işlemde bir veya daha fazla programın hata ayıklanması için DE para açığa çıktığında oturum hata ayıklama yöneticisine (SDM) bir [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) olay nesnesi gönderin.

2. Debugged edilecek program eklendiğinde, SDM'ye bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olay nesnesi gönderin. Bu olay, motor tasarımınıza bağlı olarak bir durdurma olayı olabilir.

3. Program başlatıldığında bağlıysa, IDE'ye yeni iş parçacığı bildirmek için SDM'ye bir [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) olay nesnesi gönderin. Bu olay, motor tasarımınıza bağlı olarak bir durdurma olayı olabilir.

4. Hata ayıklanan program yükleme tamamlandığında veya programa iliştirme tamamlandığında SDM'ye bir [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) olay nesnesi gönderin. Bu olay bir durdurma olayı olmalıdır.

5. Hata ayıklanacak uygulama başlatılırsa, çalışma zamanı mimarisindeki kodun ilk yönergesi yürütülmek üzereyken SDM'ye bir [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) olay nesnesi gönderin. Bu olay her zaman bir durdurma olayıdır. Hata ayıklama oturumuna adım atlarken, IDE bu olayı durdurur.

> [!NOTE]
> Birçok dil, kodlarının başında genel başlatma veya harici, önceden derlenmiş işlevler (CRT kitaplığı veya _Main) kullanır. Hata ayıklama programının dili ilk giriş noktasından önce bu tür öğelerden birini içeriyorsa, bu kod çalıştırılır ve **ana** veya `WinMain`, ana gibi kullanıcı giriş noktasına ulaşıldığında giriş noktası olayı gönderilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Bir programın debutlanmasına olanak sağlama](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
