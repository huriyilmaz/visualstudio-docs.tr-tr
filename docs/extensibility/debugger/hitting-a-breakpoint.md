---
title: Bir Breakpoint vurmak | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738573"
---
# <a name="hit-a-breakpoint"></a>Bir kesme noktasına çarptım
Aşağıdaki bölümde hata ayıklama altyapısı (DE) çalışırken veya adım atarken bir kesme noktasına çarptığında işlem açıklanır:

## <a name="troubleshoot-a-hit-breakpoint"></a>Bir isabet kesme noktasını sorun giderme

1. DE, **EVENT_SYNC_STOP**olarak [bir IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) arabirimi gönderir.

2. Oturum hata ayıklama yöneticisi (SDM) [iDebugBreakpointEvent2 çağırır:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) vuruldu kırılma noktası almak için.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama olaylarını arama](../../extensibility/debugger/calling-debugger-events.md)
