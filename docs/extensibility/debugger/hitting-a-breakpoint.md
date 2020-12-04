---
title: Kesme noktasına vurun | Microsoft Docs
description: Bu makalede, hata ayıklama altyapısı çalışırken veya adımlarken bir kesme noktasına rastlarken gerçekleşen işlem açıklanır.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: dc796689b56518948c62196407ddeaefe3ea822f
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2020
ms.locfileid: "96560856"
---
# <a name="hit-a-breakpoint"></a>Kesme noktasına isabet edin
Aşağıdaki bölümde, hata ayıklama altyapısı (DE) çalışırken veya adımla bir kesme noktasına rastlarken işlem açıklanmaktadır:

## <a name="troubleshoot-a-hit-breakpoint"></a>İsabet kesme noktası sorunlarını giderme

1. DE bir [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) arabirimini **event_sync_stop** olarak gönderir.

2. Oturum hata ayıklama Yöneticisi (SDM), isabet noktasını almak için [IDebugBreakpointEvent2:::](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) enınınınınınınınınınınının

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
