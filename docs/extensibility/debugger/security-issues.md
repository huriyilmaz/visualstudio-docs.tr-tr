---
title: Güvenlik sorunları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40898f5633eac374206ed40bfcac96d9c1c5b753
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713046"
---
# <a name="security-issues"></a>Güvenlik sorunları
Visual Studio 'Yu kullanarak bir programda hata ayıklamak için, gerekli tek izinler, geliştiricinin programı çalıştırması için ihtiyaç duyduğu bir programdır. Bu, çoğu durumda uzaktan hata ayıklamayı içerir. Internet Information Service gibi diğer hizmetlerden oluşan bazı durumlar, daha yüksek bir izin düzeyi gerektirebilir.

 Visual Studio çalışırken, işlem hata ayıklama Yöneticisi (PDM) yerel makinedeki hata ayıklama işlemlerini izler. Uzaktan, *msvsmon.exe* adlı bir program, uzaktan hata ayıklamayı IŞLEMEK ve PDM kullanılabilir hale getirmek için geliştirici tarafından başlatılır. (*msvsmon.exe* bir hizmet değildir ve bu makinede uzaktan hata ayıklamayı etkinleştirmek için el ile başlatılmış olması gerekir.) Visual Studio (veya *msvsmon.exe*) çalışmadığı zaman, hata ayıklama için hiçbir işlem izlenmez.

 Geliştirici, başlattığı programlarda özel izinler olmadan hata ayıklama yapabilir. Geliştirici, başka bir kişi aynı güvenlik grubunun bir üyesi ise, başka biri tarafından başlatılan işlemlerin hatalarını ayıklamanızı bile sağlayabilir. Uzaktan hata ayıklamayı etkinleştirmek için, yalnızca gerekli dosyaları uzak makineye kopyalamak ve *msvsmon.exe*başlatmak gerekir. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
- [İşlem hata ayıklama Yöneticisi](../../extensibility/debugger/process-debug-manager.md)
- [Uzaktan hata ayıklama](../../debugger/remote-debugging.md)
