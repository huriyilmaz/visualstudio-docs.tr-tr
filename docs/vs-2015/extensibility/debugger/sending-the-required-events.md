---
title: Gerekli olaylar gönderiliyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 457e2daf3e52c23ba9733d09d3aeb94750b5fab9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831370"
---
# <a name="sending-the-required-events"></a>Gerekli Olayları Gönderme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gerekli olayları göndermek için bu yordamı kullanın.  
  
## <a name="process-for-sending-required-events"></a>Gerekli olayları gönderme işlemi  
 Aşağıdaki olaylar, hata ayıklama altyapısı (DE) oluştururken ve bir programa iliştirilirken gereklidir:  
  
1. Bir işlemdeki bir veya daha fazla programda hata ayıklamak için DE başlatıldığında, oturum hata ayıklama Yöneticisi 'ne (SDM) [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) olay nesnesi gönderin.  
  
2. Hata Ayıklanacak program eklendiği zaman, SDM 'ye bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) olay nesnesi gönderin. Bu olay, altyapı tasarımınıza bağlı olarak bir durdurma olayı olabilir.  
  
3. Program, işlem başlatıldığında ekli ise, yeni iş parçacığının IDE 'sine bildirmek için SDM 'ye bir [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) olay nesnesi gönderin. Bu olay, altyapı tasarımınıza bağlı olarak bir durdurma olayı olabilir.  
  
4. Hata ayıklamakta olan programın yüklenmesi tamamlandığında veya programa ekleme tamamlandığında SDM 'ye bir [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) olay nesnesi gönderin. Bu olay bir durdurma olayı olmalıdır.  
  
5. Hata ayıklaması yapılacak uygulama başlatılmışsa, çalışma zamanı mimarisinde kodun ilk yönergesi yürütülene kadar, SDM 'ye bir [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) olay nesnesi gönderin. Bu olay her zaman bir durdurma olayıdır. Hata ayıklama oturumuna adımlarken, IDE bu olay üzerinde duraklar.  
  
> [!NOTE]
> Birçok dil, kendi kodunun başındaki genel başlatıcıları veya dış, önceden derlenmiş işlevleri (CRT kitaplığından veya _Main) kullanır. Hata ayıkladığınız programın dili, ilk giriş noktasında bu tür öğelerden birini içeriyorsa, bu kod çalıştırılır ve **ana** veya gibi kullanıcı giriş noktasına ulaşıldığında giriş noktası olayı gönderilir `WinMain` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Programı Hataları Ayıklanacak Şekilde Etkinleştirme](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
