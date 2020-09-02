---
title: Kesme modunda adımla | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 482d7131692c1e22483c80f4b4bb22e07a6caf1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423367"
---
# <a name="stepping-in-break-mode"></a>Kesme Modunda Adımlama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıda, hata ayıklayıcı kesme modundayken gerçekleşen işlem açıklanmakta ve kodun adım adım olması gerekir:  
  
## <a name="stepping-process"></a>Işlem Adımlama  
  
1. Bir adımı yürütmek için [Stepkind](../../extensibility/debugger/reference/stepkind.md) ve [stepunit](../../extensibility/debugger/reference/stepunit.md) bağımsız değişkenleriyle [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) öğesini çağırın.  
  
2. Adım tamamlandığında, durdurma olayı olarak bir [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) gönderin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Olaylarını Çağırma](../../extensibility/debugger/calling-debugger-events.md)
