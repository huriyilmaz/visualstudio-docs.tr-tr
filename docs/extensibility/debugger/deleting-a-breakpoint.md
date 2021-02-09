---
title: Kesme noktası siliniyor | Microsoft Docs
description: Bekleyen bir kesme noktası silindiğinde, oturum hata ayıklama yöneticisinin bekleyen bir kesme noktasını ve bundan sonra gelen tüm bağlantılı kesme noktalarını nasıl kaldırdığına öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ebd2922f48a53c371f4930e5de1fd86ed6852a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862181"
---
# <a name="deleting-a-breakpoint"></a>Kesme noktasını silme
Bekleyen bir kesme noktası silinirken aşağıdaki işlem açıklanmaktadır:

## <a name="deletion-process"></a>Silme işlemi
 Oturum hata ayıklama Yöneticisi (SDM), bekleyen kesme noktasını ve bundan sonra gelen tüm bağlantılı kesme noktalarını kaldırmak için [IDebugPendingBreakpoint2::D Sil](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) yöntemini çağırır.

> [!NOTE]
> Tek bir bağlantılı kesme noktası, [IDebugBoundBreakpoint2::D Sil](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)çağrısıyla de silinebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
