---
title: Süreçler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c59b90bb117dded0f528bc33a617370b091a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738241"
---
# <a name="processes"></a>İşlemler
Hata ayıklama mimarisinde, bir *işlem:*

- Bir dizi program için bir kapsayıcıdır. Bir dizi iş parçacığı için bir kapsayıcı olan Bir Windows işlemine yakından benzer.

- Ad, tanımlayıcı veya fiziksel tanımlayıcı ile kendini tanıtabilir.

- Tüm çalışan programları (ve iş parçacıklarını) sayısalatabilir.

- Kendisini, içinde çalıştığını bağlantı noktasını ve onu içeren makineyi açıklayabilir.

- Bir veya daha fazla program oluşturabilir, oluşturduğu programlardan herhangi birini sonlandırabilir veya bir programın durmasına neden olabilir.

- İşlem başlatıldığında oluşturulan bir [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) arabirimi ile temsil edilir. Oturum hata ayıklama yöneticisi (SDM) veya [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)tarafından başlatılan bir işlem.

  Hata ayıklama [paketi, Ekle'yi](../../extensibility/debugger/reference/idebugprocess2-attach.md)arayarak bir işleme hata ayıklama altyapısı (DE) ekleyebilir, bu da DE'nin işleyebilir işleminde çalışan tüm olası programlara iliştirildiği anlamına gelir. Örneğin, ortak dil çalışma zamanı DE bir işleme ekleniyorsa, yalnızca yönetilen kod çalıştıran programlara bağlanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Programlar](../../extensibility/debugger/programs.md)
- [İş Parçacıkları](../../extensibility/debugger/threads.md)
- [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Hata ayıklama paketi](../../extensibility/debugger/debug-package.md)
- [Hata ayıklama motoru](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [İliştir](../../extensibility/debugger/reference/idebugprocess2-attach.md)
