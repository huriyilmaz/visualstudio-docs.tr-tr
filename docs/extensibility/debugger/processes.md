---
title: İşlemler | Microsoft Docs
description: Bu makalede, hata ayıklayıcısı mimarisinde bir sürecin tanımı ve rolü açık Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f3cadf314b189c72320da3f54488af8560cf3fd8
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901259"
---
# <a name="processes"></a>İşlemler
Hata ayıklayıcısı mimarisinde bir *işlem:*

- Bir dizi program için kapsayıcıdır. Bir dizi iş parçacığının kapsayıcısı olan Windows işlemiyle benzerdir.

- Kendisini ad, tanımlayıcı veya fiziksel tanımlayıcıya göre tanımlayabilir.

- Çalışan tüm programları (ve bunların iş parçacıklarını) numaralara numara olarak numaralar.

- Kendisini, içinde çalıştırıldık bağlantı noktasını ve bu bağlantı noktasını içeren makineyi açıklar.

- Bir veya daha fazla program oluşturabilir, oluşturduğu programlardan herhangi birini sonlandırarak veya programın durdurmalarına neden olabilir.

- , işlem başlatıldıktan sonra oluşturulan bir [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) arabirimiyle temsil ediliyor. Oturum hata ayıklama yöneticisi (SDM) veya [LaunchSuspended tarafından bir işlem başlatıldı.](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)

  Hata ayıklama paketi, Ekle çağrısıyla bir hata ayıklama [](../../extensibility/debugger/reference/idebugprocess2-attach.md)altyapısını (DE) bir işleme iliştirebilir; başka bir ifade, DE'nin işleyebilen işlemde çalışan tüm olası programlara ekli olduğu anlamına gelir. Örneğin, de ortak dil çalışma zamanı bir işleme iliştiriliyorsa, yalnızca yönetilen kod çalıştıran programlara iliştirer.

## <a name="see-also"></a>Ayrıca bkz.
- [Programlar](../../extensibility/debugger/programs.md)
- [İş Parçacıkları](../../extensibility/debugger/threads.md)
- [Hata ayıklayıcısı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Pakette hata ayıklama](../../extensibility/debugger/debug-package.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [İliştir](../../extensibility/debugger/reference/idebugprocess2-attach.md)
