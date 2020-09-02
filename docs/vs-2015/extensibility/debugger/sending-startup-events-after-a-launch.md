---
title: Başlatma sonrasında başlangıç olaylarını gönderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caf36e6713e49bb1470cd720ba2d04f689abba43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64804195"
---
# <a name="sending-startup-events-after-a-launch"></a>Başlatmadan Sonra Başlangıç Olaylarını Gönderme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama altyapısı (DE) programa eklendikten sonra, hata ayıklama oturumuna geri bir dizi başlangıç olayı gönderir.  
  
 Hata ayıklama oturumuna geri gönderilen başlangıç olayları şunlardır:  
  
- Motor oluşturma olayı.  
  
- Program oluşturma olayı.  
  
- İş parçacığı oluşturma ve modül yükleme olayları.  
  
- Kod yüklendiğinde ve çalıştırılmaya hazırsanız, ancak herhangi bir kod yürütülmeden önce bir yük Tamam olayı gönderilir  
  
  > [!NOTE]
  > Bu olay devam ettiriliyor, genel değişkenler başlatılır ve Başlangıç yordamları çalıştırılır.  
  
- Olası diğer iş parçacığı oluşturma ve modül yükleme olayları.  
  
- Programın ana giriş noktasına ( **Main** veya gibi) ulaştığına işaret eden bir giriş noktası olayı `WinMain` . Bu olay genellikle zaten çalışmakta olan bir programa eklendiğinde gönderilmez.  
  
  Program aracılığıyla ilk olarak, bir altyapı oluşturma olayını temsil eden bir IDebugEngineCreateEvent2 arabirimi olan ve ardından bir program oluşturma olayını temsil eden bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)olan oturum ayıklama Yöneticisi 'NI (SDM) gönderen bir [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) arabirimini de gönderir.  
  
  Bu genellikle bir veya daha fazla [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) iş parçacığı oluşturma olayı ve [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) modülü yükleme olayları tarafından izlenir.  
  
  Kod yüklenip çalıştırılmaya hazırsanız, ancak herhangi bir kod yürütülmeden önce, DE SDM 'yi bir [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Load tamam olayı gönderir. Son olarak, program zaten çalışmıyorsa, bu, programın ana giriş noktasına ulaştığı ve hata ayıklamaya hazırlandığı sinyalde bir [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) giriş noktası olayı gönderir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yürütmenin denetimi](../../extensibility/debugger/control-of-execution.md)   
 [Hata Ayıklama Görevleri](../../extensibility/debugger/debugging-tasks.md)
