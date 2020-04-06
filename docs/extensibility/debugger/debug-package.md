---
title: Hata Ayıklama Paketi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de6240ea5d938d02f8415009203962e124ff049e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739026"
---
# <a name="debug-package"></a>Hata ayıklama paketi
Hata ayıklama paketi Visual Studio kabuğunda çalışır ve tüm UI'yi işler. Visual Studio hata ayıklama arabirimlerini tüketir ve oturum hata ayıklama yöneticisi (SDM) ile iletişim kurar.

 SDM üzerinden gönderilen olayları kesme, hata ayıklama yıkıp modu nu bozun ve odağı kesmenin gerçekleştiği programa değiştirin. Hata ayıklama paketi, olaylar tarafından gönderilen bilgilerden yığın çerçevesini ve iş parçacığını izler.

 Hata ayıklama paketinin dil veya çalışma zamanı ortamı bağımlılıkları yoktur. Hata ayıklama paketini uygulamak veya değiştirmek gerekli değildir.

 Hata ayıklama paketi *vsdebug.dll*tarafından uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Oturum hata ayıklama yöneticisi](../../extensibility/debugger/session-debug-manager.md)
- [Yığın çerçeveleri](../../extensibility/debugger/stack-frames.md)
- [İş Parçacıkları](../../extensibility/debugger/threads.md)
- [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md)
