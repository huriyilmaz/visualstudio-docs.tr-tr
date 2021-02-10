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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 808bf95631bb4106d071c29d7af233d071ef5229
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947729"
---
# <a name="hit-a-breakpoint"></a>Kesme noktasına isabet edin
Aşağıdaki bölümde, hata ayıklama altyapısı (DE) çalışırken veya adımla bir kesme noktasına rastlarken işlem açıklanmaktadır:

## <a name="troubleshoot-a-hit-breakpoint"></a>İsabet kesme noktası sorunlarını giderme

1. DE bir [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) arabirimini **event_sync_stop** olarak gönderir.

2. Oturum hata ayıklama Yöneticisi (SDM), isabet noktasını almak için [IDebugBreakpointEvent2:::](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) enınınınınınınınınınınının

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
