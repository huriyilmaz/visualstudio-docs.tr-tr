---
title: Kesme noktası siliniyor | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738943"
---
# <a name="deleting-a-breakpoint"></a>Kesme noktasını silme
Bekleyen bir kesme noktası silinirken aşağıdaki işlem açıklanmaktadır:

## <a name="deletion-process"></a>Silme işlemi
 Oturum hata ayıklama Yöneticisi (SDM), bekleyen kesme noktasını ve bundan sonra gelen tüm bağlantılı kesme noktalarını kaldırmak için [IDebugPendingBreakpoint2::D Sil](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) yöntemini çağırır.

> [!NOTE]
> Tek bir bağlantılı kesme noktası, [IDebugBoundBreakpoint2::D Sil](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)çağrısıyla de silinebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
