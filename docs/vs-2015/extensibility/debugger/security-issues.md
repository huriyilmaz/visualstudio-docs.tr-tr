---
title: Güvenlik sorunları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704417"
---
# <a name="security-issues"></a>Güvenlik Sorunları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio 'Yu kullanarak bir programda hata ayıklamak için, gerekli tek izinler, bir geliştiricinin programı çalıştırması için ihtiyacı olan izinlerdir. Bu, çoğu durum için uzaktan hata ayıklamayı içerir (Internet Information Service gibi diğer hizmetlere ilişkin bazı durumlar daha yüksek izinler gerektirebilir).  
  
 Visual Studio çalışırken, işlem hata ayıklama Yöneticisi (PDM) yerel makinedeki hata ayıklama işlemlerini izler. Uzaktan, msvsmon.exe adlı bir program, uzaktan hata ayıklamayı işlemek ve PDM kullanılabilir hale getirmek için geliştirici tarafından başlatılır. (msvsmon.exe bir hizmet değil ve bu makinede uzaktan hata ayıklamayı etkinleştirmek için el ile başlatılmış olması gerektiğini unutmayın.) Visual Studio (veya msvsmon.exe) çalışmadığı zaman, hata ayıklama için hiçbir işlem izlenmez.  
  
 Bu, bir geliştiricinin özel izinler olmadan başlattığı programlarda hata ayıklayabileceği anlamına gelir. Geliştirici, başka bir kişi aynı güvenlik grubunun bir üyesi ise, başka biri tarafından başlatılan işlemlerin hatalarını ayıklamanızı bile sağlayabilir. Uzaktan hata ayıklamayı etkinleştirmek için, yalnızca gerekli dosyaları uzak makineye kopyalamak ve msvsmon.exe başlatmak gerekir (daha fazla ayrıntı için [cihazdaki uzak araçları ayarlama](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) bölümüne bakın).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)   
 [İşlem hata ayıklama Yöneticisi](../../extensibility/debugger/process-debug-manager.md)   
 [Cihazda uzak araçları ayarlama](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
