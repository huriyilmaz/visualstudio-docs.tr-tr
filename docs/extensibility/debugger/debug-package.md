---
title: Paket Hata Ayıklama | Microsoft Docs
description: Hata ayıklama paketinin kabukta nasıl Visual Studio ve hata ayıklama arabirimlerini kullanarak ve oturum hata ayıklama yöneticisiyle iletişim kurarak kullanıcı arabirimini nasıl işley olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8be920ae352067a6e77593ca0a922474d68851d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905676"
---
# <a name="debug-package"></a>Pakette hata ayıklama
Hata ayıklama paketi, Visual Studio kabuğunda çalışır ve tüm kullanıcı arabirimini işler. Hata ayıklama arabirimlerini Visual Studio ve oturum hata ayıklama yöneticisi (SDM) ile iletişim kurar.

 SDM aracılığıyla gönderilen kesme olayları, hata ayıklayıcıyı çalıştırma modundan kesme moduna geçer ve odağı kesmenin meydana geldiği programla değiştirir. Hata ayıklama paketi yığın çerçevesini ve iş parçacığını olaylar tarafından gönderilen bilgilerden izler.

 Hata ayıklama paketinin dil veya çalışma zamanı ortam bağımlılıkları yoktur. Hata ayıklama paketini uygulamak veya değiştirmek gerekli değildir.

 Hata ayıklama paketi, tarafından *vsdebug.dll.*

## <a name="see-also"></a>Ayrıca bkz.
- [Oturum hata ayıklama yöneticisi](../../extensibility/debugger/session-debug-manager.md)
- [Yığın çerçeveleri](../../extensibility/debugger/stack-frames.md)
- [İş Parçacıkları](../../extensibility/debugger/threads.md)
- [Hata ayıklayıcısı bileşenleri](../../extensibility/debugger/debugger-components.md)
