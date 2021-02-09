---
title: İşlem | Microsoft Docs
description: Bu makalede, Visual Studio 'daki hata ayıklayıcı mimarisinde bir işlemin tanımı ve rolü açıklanır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2fe8d170f6e7b4dcd774773109c4880d4898e0b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884838"
---
# <a name="processes"></a>İşlemler
Hata ayıklayıcı mimarisinde bir *işlem*:

- , Bir program kümesi için bir kapsayıcıdır. Bir dizi iş parçacığı için kapsayıcı olan bir Windows işlemine yakından benzer.

- Kendisini ada, tanımlayıcıya veya fiziksel tanımlayıcıya göre tanımlayabilir.

- Çalışan tüm programları (ve bunların iş parçacıklarını) numaralandırabilirler.

- Kendisini, üzerinde çalıştığı bağlantı noktasını ve onu içeren makineyi açıklayabilir.

- Bir veya daha fazla program oluşturabilir, oluşturduğu programlardan herhangi birini sonlandırabilir veya bir programın durmasına neden olabilir.

- , İşlem başlatıldığında oluşturulan bir [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) arabirimi tarafından temsil edilir. Bir işlem, oturum hata ayıklama Yöneticisi (SDM) ya da [Launchaskıya alındı](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)tarafından başlatılır.

  Hata ayıklama paketi, [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)'i çağırarak bir işlem hata ayıklama ALTYAPıSı (de) ekleyebilir ve bu da, bunun işleyebileceği işlemde çalışan tüm olası programları iliştirir anlamına gelir. Örneğin, ortak dil çalışma zamanı bir işleme DE iliştiriyorsa, yalnızca yönetilen kodu çalıştıran programlara iliştirir.

## <a name="see-also"></a>Ayrıca bkz.
- [Programlar](../../extensibility/debugger/programs.md)
- [İş Parçacıkları](../../extensibility/debugger/threads.md)
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Hata ayıklama paketi](../../extensibility/debugger/debug-package.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [İliştir](../../extensibility/debugger/reference/idebugprocess2-attach.md)
