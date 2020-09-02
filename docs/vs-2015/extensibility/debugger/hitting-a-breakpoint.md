---
title: Kesme noktasına vurun | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0ddf7fd92ac0b2f745f9e73170de22e9724dad76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152688"
---
# <a name="hitting-a-breakpoint"></a>Kesme Noktasına Ulaşma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıda, hata ayıklama altyapısı (DE) çalışırken veya adımla bir kesme noktasına rastlarken işlem açıklanmaktadır:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Isabet kesme noktası sorunlarını giderme  
  
1. DE bir [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) arabirimini **event_sync_stop**olarak gönderir.  
  
2. Oturum hata ayıklama Yöneticisi (SDM), isabet noktasını almak için [IDebugBreakpointEvent2:::](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) enınınınınınınınınınınının  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Olaylarını Çağırma](../../extensibility/debugger/calling-debugger-events.md)
