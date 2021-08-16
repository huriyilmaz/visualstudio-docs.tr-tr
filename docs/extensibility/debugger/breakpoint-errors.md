---
title: Kesme Noktası Hataları | Microsoft Docs
description: Bir kesme noktası koda bağlamayı denemesine rağmen başarısız olduğunda işlemi ve kesme noktası hatalarını gidermeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 592441e057e5b726f6fb474bf4dae66365203d73a64eb569b6e785ac1d1f2d48
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403352"
---
# <a name="breakpoint-errors"></a>Kesme noktası hataları
Aşağıda, bir kesme noktası koda bağlamayı denemesi ancak başarısız olduğu işlemi açıklar.

## <a name="troubleshoot-a-breakpoint-error"></a>Kesme noktası hatasını giderme

1. Hata ayıklama altyapısı (DE), oturum hata ayıklama yöneticisine (SDM) [bir IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) gönderir.

2. SDM, hata kesme noktası almak için [IDebugBreakpointErrorEvent2::GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2** `ppErrorBP` ) çağrısında bulundu.

3. SDM, hata kesme noktası kaynaklı bekleyen kesme noktası almak için [IDebugErrorBreakpoint2::GetPendingBreakpoint'i](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) arar.

4. SDM, hata kesme noktası bağlamanın neden başarısız olduğunu almak için [IDebugErrorBreakpoint2::GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) çağrısında bulundu.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
