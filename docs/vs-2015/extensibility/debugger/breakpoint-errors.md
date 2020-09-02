---
title: Kesme noktası hataları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e98dc5e4645ac67ecdf5ebb06ecf0f31510202e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147988"
---
# <a name="breakpoint-errors"></a>Kesme Noktası Hataları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıdaki, bir kesme noktası koda bağlamayı denediğinde ancak başarısız olduğunda süreci açıklar:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Kesme noktası hatası sorunlarını giderme  
  
1. Hata ayıklama altyapısı (DE), oturum hata ayıklama Yöneticisi 'ne (SDM) bir [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) gönderir.  
  
2. SDM, hata kesme noktasını almak için [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * *) öğesini çağırır `ppErrorBP` .  
  
3. SDM, hata kesme noktasının kaynaklandığı bekleyen kesme noktasını almak için [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) öğesini çağırır.  
  
4. SDM, hata kesme noktasının bağlama nedenini almak için [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) öğesini çağırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Olaylarını Çağırma](../../extensibility/debugger/calling-debugger-events.md)
