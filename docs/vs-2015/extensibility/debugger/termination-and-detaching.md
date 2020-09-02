---
title: Sonlandırma ve ayırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d92fe88826baf19ba66b200990aee7797e91f87b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176677"
---
# <a name="termination-and-detaching"></a>Sonlandırma ve Ayırma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aşağıda normal sonlandırma açıklanmaktadır.  
  
## <a name="discussion"></a>Tartışma  
 [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) veya [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) arabirimi devam ettikten sonra, hata ayıklama yapmak için uygulamada kesme noktası, özel durum, çalışma zamanı hataları veya sonsuz döngüler yoksa, hata ayıklanan programın tamamlanması için çalıştırması gerekir. Bu normal sonlandıraldır.  
  
 Normal sonlandırmayı uygulamak için bir [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) göndermeniz gerekir. Bunun için [IDebugProgramDestroyEvent2:: GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) yönteminin uygulanması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Hata Ayıklama Altyapısı Oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
