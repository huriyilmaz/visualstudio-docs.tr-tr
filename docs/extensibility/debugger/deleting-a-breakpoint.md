---
title: Kesme Noktası silme | Microsoft Docs
description: Bekleyen bir kesme noktası silindiğinde oturum hata ayıklama yöneticisinin bekleyen bir kesme noktası ve ona bağlı olan tüm kesme noktaları nasıl kaldır olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: adaa20e57670148c9c7129c5c31d5de6da915515
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073350"
---
# <a name="deleting-a-breakpoint"></a>Kesme noktası silme
Aşağıda bekleyen bir kesme noktası silinirken yapılan işlem açıkmektedir:

## <a name="deletion-process"></a>Silme işlemi
 Oturum hata ayıklama yöneticisi (SDM), bekleyen kesme noktası ve ona bağlı tüm bağlı kesme noktaları kaldırmak için [IDebugPendingBreakpoint2::D elete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) yöntemini çağırıyor.

> [!NOTE]
> Tek bir bağlı kesme noktası [IDebugBoundBreakpoint2::D elete çağrısıyla da silinebilir.](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı olaylarını çağırma](../../extensibility/debugger/calling-debugger-events.md)
