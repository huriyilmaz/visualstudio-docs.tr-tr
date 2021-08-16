---
title: Güvenlik sorunları | Microsoft Docs
description: uzaktan hata ayıklama ve diğer hizmetleri içeren durumlar dahil olmak üzere Visual Studio kullanarak bir programın hatalarını ayıklamak için gerekli izinler hakkında bilgi edinin.
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
ms.openlocfilehash: eaf0df177b59d14f07a1b71499841ffb447a45ab3df022ef03e5724d85e49310
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377021"
---
# <a name="security-issues"></a>Güvenlik sorunları
Visual Studio kullanarak bir programda hata ayıklamak için, gerekli tek izinler, bir geliştiricinin programı çalıştırması için ihtiyaç duyduğu izinlerdir. Bu, çoğu durumda uzaktan hata ayıklamayı içerir. Internet Information Service gibi diğer hizmetlerden oluşan bazı durumlar, daha yüksek bir izin düzeyi gerektirebilir.

 Visual Studio çalışırken, işlem hata ayıklama yöneticisi (PDM) yerel makinedeki hata ayıklama işlemlerini izler. Uzaktan, *msvsmon.exe* adlı bir program, uzaktan hata ayıklamayı IŞLEMEK ve PDM kullanılabilir hale getirmek için geliştirici tarafından başlatılır. (*msvsmon.exe* bir hizmet değildir ve bu makinede uzaktan hata ayıklamayı etkinleştirmek için el ile başlatılmış olması gerekir.) Visual Studio (veya *msvsmon.exe*) çalışmadığı zaman, hata ayıklama için hiçbir işlem izlenmez.

 Geliştirici, başlattığı programlarda özel izinler olmadan hata ayıklama yapabilir. Geliştirici, başka bir kişi aynı güvenlik grubunun bir üyesi ise, başka biri tarafından başlatılan işlemlerin hatalarını ayıklamanızı bile sağlayabilir. Uzaktan hata ayıklamayı etkinleştirmek için, yalnızca gerekli dosyaları uzak makineye kopyalamak ve *msvsmon.exe* başlatmak gerekir. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
- [İşlem hata ayıklama Yöneticisi](../../extensibility/debugger/process-debug-manager.md)
- [Uzaktan hata ayıklama](../../debugger/remote-debugging.md)
