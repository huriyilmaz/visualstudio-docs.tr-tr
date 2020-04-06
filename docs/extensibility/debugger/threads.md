---
title: Konu İş Parçacıkları | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712474"
---
# <a name="threads"></a>İş Parçacıkları
Hata ayıklama mimarisinde, bir *iş parçacığı:*

- Hesaplamanın temel birimidir. İş parçacığı, yönergelerini tek bir çağrı yığını bağlamında sırayla yürütür ve bir kod bağlamından diğerine taşınır.

- Kendisini ve içinde çalıştırılabildiği programı tanımlayabilir. İş parçacıkları adlandırılmış, askıya alınabilir ve devam ettirilebilir. Bir iş parçacığı da ilişkili yığın çerçeveleri sayısalatabilir ve bazı koşullar altında, başka bir yığın çerçeveye taşınabilir. Yığın çerçevesi bağlamı göz önüne alındığında, bir iş parçacığı varsa ilişkili mantıksal iş parçacığı döndürebilir. İş parçacığı, **IDE'nin İş parçacıkları** penceresinde görüntülenebilecek askıya alma sayısı gibi özelliklere sahiptir.

- Genellikle bir hata ayıklama motoru (DE) veya sanal makine tarafından bir program yürütme sonucu oluşturulan bir [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) arabirimi tarafından temsil edilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Programlar](../../extensibility/debugger/programs.md)
- [Yığın çerçeveleri](../../extensibility/debugger/stack-frames.md)
- [Hata ayıklama motoru](../../extensibility/debugger/debug-engine.md)
- [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md)
- [Oturum hata ayıklama yöneticisi](../../extensibility/debugger/session-debug-manager.md)
