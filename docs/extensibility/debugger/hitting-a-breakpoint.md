---
title: Kesme noktasına vurun | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6e75eb1e807e72f3bd035b5dd0534860f5fd8df2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738573"
---
# <a name="hit-a-breakpoint"></a>Kesme noktasına isabet edin
Aşağıdaki bölümde, hata ayıklama altyapısı (DE) çalışırken veya adımla bir kesme noktasına rastlarken işlem açıklanmaktadır:

## <a name="troubleshoot-a-hit-breakpoint"></a>İsabet kesme noktası sorunlarını giderme

1. DE bir [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) arabirimini **event_sync_stop**olarak gönderir.

2. Oturum hata ayıklama Yöneticisi (SDM), isabet noktasını almak için [IDebugBreakpointEvent2:::](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) enınınınınınınınınınınının

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
