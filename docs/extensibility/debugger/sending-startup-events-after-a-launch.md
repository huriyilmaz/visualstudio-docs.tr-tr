---
title: Başlatma sonrasında başlangıç olaylarını gönderme | Microsoft Docs
description: Hata ayıklama altyapısı bir programa eklendikten sonra hata ayıklama altyapısının hata ayıklama oturumuna gönderdiği başlangıç olayları dizisi hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: eb5d382d54d8263cfe0e72f2c828453b8c29aba097973e7c32f1640cc1d2d4a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414954"
---
# <a name="send-startup-events-after-a-launch"></a>Başlatma sonrasında başlangıç olaylarını gönder
Hata ayıklama altyapısı (DE) programa eklendikten sonra, hata ayıklama oturumuna geri bir dizi başlangıç olayı gönderir.

 Hata ayıklama oturumuna geri gönderilen başlangıç olayları şunlardır:

- Motor oluşturma olayı.

- Program oluşturma olayı.

- İş parçacığı oluşturma ve modül yükleme olayları.

- Kod yüklendiğinde ve çalıştırılmaya hazırsanız, ancak herhangi bir kod yürütülmeden önce bir yük Tamam olayı gönderilir.

  > [!NOTE]
  > Bu olay devam ettiriliyor, genel değişkenler başlatılır ve Başlangıç yordamları çalıştırılır.

- Olası diğer iş parçacığı oluşturma ve modül yükleme olayları.

- Programın ana giriş noktasına ( **Main** veya gibi) ulaştığına işaret eden bir giriş noktası olayı `WinMain` . Bu olay genellikle zaten çalışmakta olan bir programa eklendiğinde gönderilmez.

  Program aracılığıyla ilk olarak, bir altyapı oluşturma olayını temsil eden bir IDebugEngineCreateEvent2 arabirimi olan ve ardından bir program oluşturma olayını temsil eden bir [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)olan oturum ayıklama Yöneticisi 'NI (SDM) gönderen bir [](../../extensibility/debugger/reference/idebugenginecreateevent2.md) arabirimini de gönderir.

  Bu olaylar genellikle bir veya daha fazla [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) iş parçacığı oluşturma olayı ve [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) modülü yükleme olayları tarafından izlenir.

  Kod yüklenip çalıştırılmaya hazırsanız, ancak herhangi bir kod yürütülmeden önce, DE SDM 'yi bir [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Load tamam olayı gönderir. Son olarak, program zaten çalışmıyorsa, bu, programın ana giriş noktasına ulaştığı ve hata ayıklamaya hazırlandığı sinyalde bir [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) giriş noktası olayı gönderir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yürütmenin denetimi](../../extensibility/debugger/control-of-execution.md)
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
