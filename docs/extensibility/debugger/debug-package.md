---
title: Hata ayıklama paketi | Microsoft Docs
description: Hata ayıklama paketinin Visual Studio Kabuğu 'nda nasıl çalıştığını öğrenin ve hata ayıklama arabirimlerini kullanıp oturum hata ayıklama yöneticisiyle iletişim kurarak Kullanıcı arabirimini işler.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ad62a487d38500617999a276aa3ae15a75089736
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914133"
---
# <a name="debug-package"></a>Hata ayıklama paketi
Hata ayıklama paketi Visual Studio Kabuğu 'nda çalışır ve tüm Kullanıcı arabirimini işler. Visual Studio hata ayıklama arabirimlerini kullanır ve oturum hata ayıklama Yöneticisi (SDM) ile iletişim kurar.

 SDM aracılığıyla gönderilen olayları kes hata ayıklayıcıyı çalıştırma modundan kesme moduna geçirin ve odağı, kesmenin gerçekleştiği programa değiştirin. Hata ayıklama paketi, olaylar tarafından kendisine gönderilen bilgilerden yığın çerçevesini ve iş parçacığını izler.

 Hata ayıklama paketinde dil veya çalışma zamanı ortamı bağımlılıkları yok. Hata ayıklama paketini uygulamak veya değiştirmek gerekli değildir.

 Hata ayıklama paketi *vsdebug.dll* tarafından uygulanır.

## <a name="see-also"></a>Ayrıca bkz.
- [Oturum hata ayıklama Yöneticisi](../../extensibility/debugger/session-debug-manager.md)
- [Yığın çerçeveleri](../../extensibility/debugger/stack-frames.md)
- [İş Parçacıkları](../../extensibility/debugger/threads.md)
- [Hata ayıklayıcı bileşenleri](../../extensibility/debugger/debugger-components.md)
