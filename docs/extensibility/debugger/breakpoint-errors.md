---
title: Kesme noktası hataları | Microsoft Docs
description: Bir kesme noktası koda bağlamayı denediğinde ancak başarısız olduğunda ve kesme noktası hatalarını gidermeye çalıştığında işlem hakkında bilgi edinin.
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
ms.openlocfilehash: 2c38817ce41131c936138078f0dc8787854a4116
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051059"
---
# <a name="breakpoint-errors"></a>Kesme noktası hataları
Aşağıdaki, bir kesme noktası koda bağlamayı denediğinde ancak başarısız olduğunda süreci açıklar.

## <a name="troubleshoot-a-breakpoint-error"></a>Kesme noktası hatası sorunlarını giderme

1. Hata ayıklama altyapısı (DE), oturum hata ayıklama Yöneticisi 'ne (SDM) bir [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) gönderir.

2. SDM, hata kesme noktasını almak için [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * *) öğesini çağırır `ppErrorBP` .

3. SDM, hata kesme noktasının kaynaklandığı bekleyen kesme noktasını almak için [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) öğesini çağırır.

4. SDM, hata kesme noktasının bağlama nedenini almak için [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) öğesini çağırır.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
