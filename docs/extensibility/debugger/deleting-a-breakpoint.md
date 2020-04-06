---
title: Kesme Noktası Silme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a77be200a11eb7b3985a4c1a47e4cddaa543f900
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738943"
---
# <a name="deleting-a-breakpoint"></a>Kesme noktasını silme
Bekleyen bir kesme noktası nı silerken aşağıdaki işlem açıklanır:

## <a name="deletion-process"></a>Silme işlemi
 Oturum hata ayıklama yöneticisi (SDM), bekleyen kesme noktasını ve ondan bağlanan tüm kopuşu kaldırmak için [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) yöntemini çağırır.

> [!NOTE]
> Tek bir bağlı kesme noktası da [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)bir çağrı ile silinebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama olaylarını arama](../../extensibility/debugger/calling-debugger-events.md)
