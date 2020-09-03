---
title: İş parçacıkları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8ed5c06e0c42dac1f0539cc2c7c5886d95b23ae1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712474"
---
# <a name="threads"></a>İş Parçacıkları
Hata ayıklayıcı mimarisinde bir *iş parçacığı*:

- , Temel hesaplama birimidir. Bir iş parçacığı, kendi talimatlarını tek bir çağrı yığınının bağlamı içinde yürütür ve bir kod bağlamından sonrakine taşınır.

- Kendisini ve üzerinde çalıştığı programı tanımlayabilir. İş parçacıkları adlandırılmış, askıya alınmış ve devam edebilir. Bir iş parçacığı ayrıca ilişkili yığın çerçevelerini de numaralandırabilirler ve bazı koşullar altında başka bir yığın çerçevesine taşınabilir. Yığın çerçevesinin bağlamı verildiğinde bir iş parçacığı, varsa ilişkili mantıksal iş parçacığını döndürebilir. Bir iş parçacığında, IDE 'nin **Iş parçacıkları** penceresinde görüntülenebilen bir askıya alma sayısı gibi özellikler vardır.

- , Genellikle bir program yürütmenin sonucu olarak bir hata ayıklama altyapısı (DE) veya sanal makine tarafından oluşturulan bir [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) arabirimi tarafından temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Programlar](../../extensibility/debugger/programs.md)
- [Yığın çerçeveleri](../../extensibility/debugger/stack-frames.md)
- [Hata ayıklama altyapısı](../../extensibility/debugger/debug-engine.md)
- [Hata ayıklayıcı kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Oturum hata ayıklama Yöneticisi](../../extensibility/debugger/session-debug-manager.md)
