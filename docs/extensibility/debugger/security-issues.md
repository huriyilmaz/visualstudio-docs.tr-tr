---
title: Güvenlik Sorunları | Microsoft Docs
description: Uzaktan hata ayıklama ve diğer hizmetleri içeren durumlar dahil olmak üzere Visual Studio kullanarak bir programda hata ayıklamak için gereken izinler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 63d8c78767cf6a32d541a37370a5b2742cfcc087
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057310"
---
# <a name="security-issues"></a>Güvenlik sorunları
Visual Studio kullanarak bir programda hata ayıklamak için gereken tek izinler, bir geliştiricinin programı çalıştırmak için gerektirdiği izinlerdir. Buna çoğu durumda uzaktan hata ayıklama dahildir. İnternet Bilgi Hizmeti gibi diğer hizmetlerle ilgili bazı durumlarda daha yüksek düzeyde izinler gerekli olabilir.

 İşlem Visual Studio çalışırken, işlem hata ayıklama yöneticisi (PDM) yerel makinede hata ayıklama işlemlerini izler. Uzaktan, uzaktan hata *msvsmon.exe* işlemek ve PDM'nin kullanılabilir hale geldirerek geliştirici tarafındanmsvsmon.exeadlı bir program başlatabilirsiniz. (*msvsmon.exe* bir hizmet değildir ve bu makinede uzaktan hata ayıklamayı etkinleştirmek için el ile başlatmalısınız.) Bir Visual Studio *(veyamsvsmon.exe)* çalışmazsa, hata ayıklama için hiçbir işlem izlanmaz.

 Bir geliştirici, özel izinler ile başlattıları programlarda hata ayıklar. Diğer kişi aynı güvenlik grubunun üyesi ise geliştirici başka biri tarafından başlatan işlemlerde hata ayıklar. Uzaktan hata ayıklamayı etkinleştirmek için yalnızca gerekli dosyaları uzak makineye kopyalayıp uzak makineye *msvsmon.exe.* Daha fazla bilgi için [bkz. Uzaktan hata ayıklama.](../../debugger/remote-debugging.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
- [İşlem hata ayıklama yöneticisi](../../extensibility/debugger/process-debug-manager.md)
- [Uzaktan hata ayıklama](../../debugger/remote-debugging.md)
