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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 061175326a19af1866262421b381eb14267c7efd
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96915563"
---
# <a name="deleting-a-breakpoint"></a>Kesme noktasını silme
Bekleyen bir kesme noktası silinirken aşağıdaki işlem açıklanmaktadır:

## <a name="deletion-process"></a>Silme işlemi
 Oturum hata ayıklama Yöneticisi (SDM), bekleyen kesme noktasını ve bundan sonra gelen tüm bağlantılı kesme noktalarını kaldırmak için [IDebugPendingBreakpoint2::D Sil](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) yöntemini çağırır.

> [!NOTE]
> Tek bir bağlantılı kesme noktası, [IDebugBoundBreakpoint2::D Sil](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)çağrısıyla de silinebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
