---
title: Güvenlik Sorunları | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713046"
---
# <a name="security-issues"></a>Güvenlik sorunları
Visual Studio'yu kullanarak bir programı hata ayıklamak için, gereken tek izinler bir geliştiricinin programı çalıştırmak için ihtiyaç duyduğu izinlerdir. Bu, çoğu durum için uzaktan hata ayıklama içerir. Internet Bilgi Hizmeti gibi diğer hizmetleri içeren bazı durumlar daha yüksek düzeyde izin gerektirebilir.

 Visual Studio çalışırken, işlem hata ayıklama yöneticisi (PDM) yerel makinedeki hata ayıklama işlemlerini izler. Uzaktan, uzaktan hata ayıklama işlemek ve PDM kullanılabilir hale getirmek için geliştirici tarafından *msvsmon.exe* adlı bir program başlatılır. (*msvsmon.exe* bir hizmet değildir ve bu makinede uzaktan hata ayıklama etkinleştirmek için el ile başlatılmalıdır.) Visual Studio (veya *msvsmon.exe)* çalışmadığında, hata ayıklama için hiçbir işlem izlenmez.

 Geliştirici, özel izinler olmadan başlattığı programları hata ayıklayabilir. Geliştirici, başka bir kişi aynı güvenlik grubunun üyesiyse, başka biri tarafından başlatılan hata ayıklama işlemlerini bile alabilir. Ve, uzaktan hata ayıklama etkinleştirmek için, sadece uzak makineye gerekli dosyaları kopyalamak ve *msvsmon.exe*başlatmak için gereklidir. Daha fazla bilgi için [Uzaktan hata ayıklama](../../debugger/remote-debugging.md)bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Görevleri hata ayıklama](../../extensibility/debugger/debugging-tasks.md)
- [İşlem hata ayıklama yöneticisi](../../extensibility/debugger/process-debug-manager.md)
- [Uzaktan hata ayıklama](../../debugger/remote-debugging.md)
