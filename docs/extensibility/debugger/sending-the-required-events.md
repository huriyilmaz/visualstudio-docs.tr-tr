---
title: Gerekli olaylar gönderiliyor | Microsoft Docs
description: bir hata ayıklama altyapısı oluştururken ve Visual Studio hata ayıklama içindeki bir programa iliştirirken gerekli olan sıralı olaylar hakkında bilgi edinin.
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
# <a name="send-the-required-events"></a>Gerekli olayları gönder
Gerekli olayları göndermek için bu yordamı kullanın.

## <a name="process-for-sending-required-events"></a>Gerekli olayları gönderme işlemi
 Aşağıdaki olaylar, hata ayıklama altyapısı (DE) oluştururken ve bir programa iliştirilirken gereklidir:

1. Bir işlemdeki bir veya daha fazla programda hata ayıklamak için DE başlatıldığında, oturum hata ayıklama Yöneticisi 'ne (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) olay nesnesi gönderin.

2. Hata Ayıklanacak program eklendiği zaman, SDM 'ye bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olay nesnesi gönderin. Bu olay, altyapı tasarımınıza bağlı olarak bir durdurma olayı olabilir.

3. Program, işlem başlatıldığında ekli ise, yeni iş parçacığının IDE 'sine bildirmek için SDM 'ye bir [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) olay nesnesi gönderin. Bu olay, altyapı tasarımınıza bağlı olarak bir durdurma olayı olabilir.

4. Hata ayıklamakta olan programın yüklenmesi tamamlandığında veya programa ekleme tamamlandığında SDM 'ye bir [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) olay nesnesi gönderin. Bu olay bir durdurma olayı olmalıdır.

5. Hata ayıklaması yapılacak uygulama başlatılmışsa, çalışma zamanı mimarisinde kodun ilk yönergesi yürütülene kadar, SDM 'ye bir [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) olay nesnesi gönderin. Bu olay her zaman bir durdurma olayıdır. Hata ayıklama oturumuna adımlarken, IDE bu olay üzerinde duraklar.

> [!NOTE]
> Birçok dil, kendi kodunun başındaki genel başlatıcıları veya dış, önceden derlenmiş işlevleri (CRT kitaplığından veya _Main) kullanır. Hata ayıkladığınız programın dili, ilk giriş noktasındaki bu türden öğelerden birini içeriyorsa, bu kod çalıştırılır ve **ana** veya gibi kullanıcı giriş noktasına ulaşıldığında giriş noktası olayı gönderilir `WinMain` .

## <a name="see-also"></a>Ayrıca bkz.
- [Bir programın ayıklanamayacağını etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
