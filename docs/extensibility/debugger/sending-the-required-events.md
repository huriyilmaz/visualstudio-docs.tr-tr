---
title: Gerekli Olayları Gönderme | Microsoft Docs
description: Hata ayıklama altyapısı oluştururken ve hata ayıklama sırasında bu altyapıyı bir programa iliştirme sırasında gereken Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 5080564527d2037c4ea376bc11c5df5a397c623616b6c08e62ab79e684256548
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448500"
---
# <a name="send-the-required-events"></a>Gerekli olayları gönderme
Gerekli olayları göndermek için bu yordamı kullanın.

## <a name="process-for-sending-required-events"></a>Gerekli olayları gönderme işlemi
 Bu sırayla, bir hata ayıklama altyapısı (DE) oluşturulurken ve bir programa iliştirilen aşağıdaki olaylar gereklidir:

1. DE bir işlemde bir veya daha fazla programda hata ayıklama için başlatılmış olduğunda oturum hata ayıklama yöneticisine (SDM) [bir IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) olay nesnesi gönderin.

2. Hata ayıklanması gereken program ekli olduğunda, SDM'ye [bir IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olay nesnesi gönderin. Bu olay, altyapı tasarımınıza bağlı olarak durdurulan bir olay olabilir.

3. Program, işlem başlatılana ekli ise, yeni iş parçacığının IDE'lerini bildirmek için SDM'ye bir [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) olay nesnesi gönderin. Bu olay, altyapı tasarımınıza bağlı olarak durdurulan bir olay olabilir.

4. Hata ayıklanacak programın yüklenmesi tamamlandığında veya programa ekleme tamamlandığında SDM'ye [bir IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) olay nesnesi gönderin. Bu olayın bir durdurma olayı olması gerekir.

5. Hata ayıklanacak uygulama başlatıldı ise, çalışma zamanı mimarisinde ilk kod yönergesi yürütülebilir olduğunda SDM'ye bir [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) olay nesnesi gönderin. Bu olay her zaman durdurulan bir olaydır. Hata ayıklama oturumuna adımlarken IDE bu olayda durur.

> [!NOTE]
> Birçok dil, kodunun başında genel başlatıcıları veya dış, önceden _Main işlevleri (CRT kitaplığından veya _Main) kullanır. Hata ayıklamakta olduğunu programın dili ilk giriş noktasından önce bu tür öğelerden birini içeriyorsa, bu kod çalıştırıldı ve  ana veya gibi kullanıcı giriş noktasına ulaşıldıklerinde giriş noktası olayı `WinMain` gönderilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Bir programın hata ayıklamasını etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
