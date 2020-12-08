---
title: Gerekli olaylar gönderiliyor | Microsoft Docs
description: Hata ayıklama altyapısı oluştururken ve Visual Studio Hata ayıklamasında bir programa iliştirilirken gereken sıralı olaylar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 49c85e3d371bfd729d55e9d17a6c8de61924e35f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845316"
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
