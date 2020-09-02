---
title: Kesme noktası siliniyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42cd353c216c21d14c4f6592da809c72acdba664
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64807128"
---
# <a name="deleting-a-breakpoint"></a>Kesme Noktasını Silme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bekleyen bir kesme noktası silinirken aşağıdaki işlem açıklanmaktadır:  
  
## <a name="deletion-process"></a>Silme Işlemi  
 Oturum hata ayıklama Yöneticisi (SDM), bekleyen kesme noktasını ve bundan sonra gelen tüm bağlantılı kesme noktalarını kaldırmak için [IDebugPendingBreakpoint2::D Sil](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) yöntemini çağırır.  
  
> [!NOTE]
> Tek bir bağlantılı kesme noktası, [IDebugBoundBreakpoint2::D Sil](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)çağrısıyla de silinebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Olaylarını Çağırma](../../extensibility/debugger/calling-debugger-events.md)
