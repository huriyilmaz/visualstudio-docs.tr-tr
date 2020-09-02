---
title: Program sonlandırılıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f0b9ad248751af0885fa4edc0275be2ede5ddd9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421869"
---
# <a name="terminating-a-program"></a>Program Sonlandırma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıda, tek bir programın bir iş parçacığı ile sonlandırmasının açıklaması verilmiştir.  
  
## <a name="termination-process"></a>Sonlandırma Işlemi  
  
1. DE geçerli bir [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)Ile bir [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) gönderir.  
  
2. DE geçerli bir [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)Ile bir [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) gönderir.  
  
   IDE tasarım moduna girer. Hata ayıklama altyapısı veya çalışma zamanı ortamı, programı bağlantı noktasından kaldırmak için [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) yöntemini çağırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Olaylarını Çağırma](../../extensibility/debugger/calling-debugger-events.md)
