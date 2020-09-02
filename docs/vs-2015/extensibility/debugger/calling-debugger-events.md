---
title: Hata ayıklayıcı olaylarını çağırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: b3440ac3-80af-40c6-bef4-cbf00fa67885
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2f162affe2324afaa8fb1d506c3177311386bfc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146393"
---
# <a name="calling-debugger-events"></a>Hata Ayıklayıcısı Olaylarını Çağırma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama oturumlarındaki olaylar belirli bir sırada oluşur.  
  
## <a name="discussion"></a>Tartışma  
 Hata ayıklama altyapısı (DE) ve oturum hata ayıklama Yöneticisi (SDM) arasındaki çağrıların düzenini anlamak için, aşağıdaki, tipik bir hata ayıklama oturumunda gerçekleşen olayların arama sırasını temsil eder:  
  
1. [Bir programa ekleme ve ayırma](../../extensibility/debugger/attaching-and-detaching-to-a-program.md)  
  
2. [Hata ayıklayıcı başlatılıyor](../../extensibility/debugger/launching-the-debugger.md)  
  
3. [Program sonlandırılıyor](../../extensibility/debugger/terminating-a-program.md)  
  
4. [Kesme noktası oluşturma](../../extensibility/debugger/creating-a-breakpoint.md)  
  
5. [Bir kesme noktası bağlandığında veya ilişkisiz duruma geldiğinde](../../extensibility/debugger/when-a-breakpoint-binds-or-becomes-unbound.md)  
  
6. [Kesme noktası hataları](../../extensibility/debugger/breakpoint-errors.md)  
  
7. [Kesme noktasına vurun](../../extensibility/debugger/hitting-a-breakpoint.md)  
  
8. [Kesme noktasını silme](../../extensibility/debugger/deleting-a-breakpoint.md)  
  
9. [Kesme moduna giriliyor](../../extensibility/debugger/entering-break-mode.md)  
  
10. [Kesme modunda adımla](../../extensibility/debugger/stepping-in-break-mode.md)  
  
11. [Kesme modunda ifade değerlendirmesi](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
12. [Özel durum işleme](../../extensibility/debugger/exception-handling-visual-studio-sdk.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Hata Ayıklama Altyapısı Oluşturma](../../extensibility/debugger/creating-a-custom-debug-engine.md)
