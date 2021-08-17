---
title: Kesme Noktası Oluşturma | Microsoft Docs
description: Bir kesme noktası bağlamak için gereken modül yüklendiğinde oturum hata ayıklama yöneticisinin çağıran yöntem çağrılarını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ff6669ad1ce27582794461bd951785c3f35cde7d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080357"
---
# <a name="create-a-breakpoint"></a>Kesme noktası oluşturma
Aşağıda bir kesme noktası oluşturma işlemi açıkmektedir.

## <a name="methods-in-breakpoint-creation"></a>Kesme noktası oluşturma yöntemleri
 Bir kesme noktası bağlamak için gereken modül yüklendiğinde, oturum hata ayıklama yöneticisi (SDM) aşağıdaki yöntemleri çağrıları:

1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)

2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)

3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)

    > [!NOTE]
    > **CanBind** yalnızca kullanıcı Kesme Noktaları penceresinden bir kesme noktası **geldiğinde** çağrılır.

4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)

5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
