---
title: Kesme Noktası Hataları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0766792f19faf7c1933c6576ab41f65ec1b31ae9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739224"
---
# <a name="breakpoint-errors"></a>Kesme noktası hataları
Bir kesme noktası koda bağlanmaya çalıştığında ancak başarısız olduğunda aşağıdaki işlemi açıklar.

## <a name="troubleshoot-a-breakpoint-error"></a>Bir kesme noktası hatagiderme

1. Hata ayıklama altyapısı (DE), oturum hata ayıklama yöneticisine (SDM) bir [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) gönderir.

2. SDM hata kesme noktası almak için [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2**) `ppErrorBP`çağırır.

3. SDM, hata kesme noktasının kaynaklandığı bekleyen kesme noktasını almak için [IDebugErrorBreakpoint2::GetPendingBreakpoint'i](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) çağırır.

4. SDM, hata kesme noktasının neden bağlanamamasının nedenini almak için [IDebugErrorBreakpoint2::GetBreakpointResolution'ı](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
