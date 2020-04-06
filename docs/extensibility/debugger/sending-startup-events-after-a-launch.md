---
title: Lansmandan Sonra Başlangıç Etkinlikleri gönderme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c71db002420a2b822bffd34f2ae05e712f6a4bb9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713006"
---
# <a name="send-startup-events-after-a-launch"></a>Başlatmadan sonra başlangıç olaylarını gönderme
Hata ayıklama altyapısı (DE) programa iliştirildikten sonra, hata ayıklama oturumuna bir dizi başlangıç olayı gönderir.

 Hata ayıklama oturumuna geri gönderilen başlangıç olayları şunlardır:

- Bir motor oluşturma olayı.

- Bir program oluşturma olayı.

- İş parçacığı oluşturma ve modül yükleme olayları.

- Kod yüklendiğinde ve çalışmaya hazır olduğunda, ancak herhangi bir kod yürütülmeden önce gönderilen bir yük tam olayı.

  > [!NOTE]
  > Bu olay devam ettiğinde, genel değişkenler başharfe alınır ve başlangıç yordamları çalıştırılır.

- Olası diğer iş parçacığı oluşturma ve modül yükleme olayları.

- Programın Ana giriş noktasına ulaştığını gösteren bir giriş noktası olayı, `WinMain`örneğin **Main** veya . De zaten çalışan bir programa iliştiriyorsa, bu olay genellikle gönderilmez.

  Programlı olarak, DE ilk oturum hata ayıklama yöneticisi gönderir (SDM) bir [iDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) arabirimi, bir motor oluşturma olay temsil eder, bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)ardından , bir program oluşturma olayı temsil eder.

  Bu olayları genellikle bir veya daha fazla [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) iş parçacığı oluşturma olayları ve [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) modül yük olayları takip edilir.

  Kod yüklendiğinde ve çalışmaya hazır olduğunda, ancak herhangi bir kod yürütülmeden önce DE SDM'ye bir [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) yük tam olay gönderir. Son olarak, program zaten çalışmıyorsa, DE bir [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) giriş noktası olay gönderir, programın ana giriş noktasına ulaştığını ve hata ayıklama için hazır olduğunu sinyal.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütmenin kontrolü](../../extensibility/debugger/control-of-execution.md)
- [Görevleri hata ayıklama](../../extensibility/debugger/debugging-tasks.md)
