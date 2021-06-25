---
title: Gerekli Olayları Gönderme | Microsoft Docs
description: Hata ayıklama altyapısı oluştururken ve bu altyapıyı hata ayıklama sırasında bir programa iliştirme sırasında gereken Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b04ca7ed68b975bc68fa509cdc75dc507b9603d6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902273"
---
# <a name="send-the-required-events"></a>Gerekli olayları gönderme
Gerekli olayları göndermek için bu yordamı kullanın.

## <a name="process-for-sending-required-events"></a>Gerekli olayları gönderme işlemi
 Bu sırada, bir hata ayıklama altyapısı (DE) oluşturulurken ve bir programa iliştirilen aşağıdaki olaylar gereklidir:

1. DE bir işlemde bir veya daha fazla programda hata ayıklama için başlatılmış olduğunda oturum hata ayıklama yöneticisine (SDM) [bir IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) olay nesnesi gönderin.

2. Hata ayıklanması gereken program ekli olduğunda, SDM'ye [bir IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olay nesnesi gönderin. Bu olay, altyapı tasarımınıza bağlı olarak durdurulan bir olay olabilir.

3. Program, işlem başlatılana bağlı ise, yeni iş parçacığının IDE'lerini bildirmek için SDM'ye bir [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) olay nesnesi gönderin. Bu olay, altyapı tasarımınıza bağlı olarak durdurulan bir olay olabilir.

4. Hata ayıklanacak programın yüklenmesi tamamlandığında veya programa ekleme tamamlandığında SDM'ye [bir IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) olay nesnesi gönderin. Bu olayın bir durdurma olayı olması gerekir.

5. Hata ayıklanacak uygulama başlatıldı ise, çalışma zamanı mimarisinde ilk kod yönergesi yürütülebilir olduğunda SDM'ye bir [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) olay nesnesi gönderin. Bu olay her zaman durdurulan bir olaydır. Hata ayıklama oturumuna adımlarken IDE bu olayda durur.

> [!NOTE]
> Birçok dil, kodunun başında genel başlatıcıları veya dış, önceden _Main işlevleri (CRT kitaplığından veya _Main) kullanır. Hata ayıklamakta olduğunu programın dili ilk giriş noktasından önce bu tür öğelerden birini içeriyorsa, bu kod çalıştırıldı ve  ana veya gibi kullanıcı giriş noktasına ulaşıldıklerinde giriş noktası olayı `WinMain` gönderilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Bir programın hata ayıklamasını etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
