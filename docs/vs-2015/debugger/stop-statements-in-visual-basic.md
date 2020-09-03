---
title: Visual Basic deyimlerini durdur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f2749ef9a6cfd310da5da832a283b55b6af59a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198884"
---
# <a name="stop-statements-in-visual-basic"></a>Visual Basic'de Durdur Deyimleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Basic stop deyimleri, kesme noktası ayarlamaya yönelik bir alternatif sağlar. Hata ayıklayıcı bir stop ifadesiyle karşılaştığında, programın yürütülmesini keser (kesme moduna girer). C# programcıları, System. Diagnostics. Debugger. Break çağrısı kullanarak aynı etkiyi elde edebilir.  
  
 Bir stop ifadesini, kaynak kodunuzu düzenleyerek ayarlayabilir veya kaldırabilirsiniz. Bir kesme noktası gibi hata ayıklayıcı komutlarını kullanarak stop deyimlerini ayarlayamazsınız veya temizleyemezsiniz.  
  
 End ifadesinin aksine, stop deyimleri değişkenleri sıfırlamaz veya size tasarım moduna geri döndürmez. Uygulamayı çalıştırmaya devam etmek için hata ayıklama menüsünden devam ' ı seçebilirsiniz.  
  
 Hata ayıklayıcı dışında bir Visual Basic uygulaması çalıştırdığınızda, Just-In-Time hata ayıklaması etkinse bir stop ifadesiyle hata ayıklayıcı başlatılır. Just-In-Time hata ayıklaması etkinleştirilmemişse, stop deyimleri bir End deyimmiş gibi davranır ve yürütme sonlandırılıyor. QueryUnload veya Unload olayı gerçekleşmez, bu nedenle tüm stop deyimlerini Visual Basic uygulamanızın yayın sürümünden kaldırmanız gerekir. Daha fazla bilgi için bkz. [tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Stop deyimlerini kaldırma zorunludur kaçınmak için, koşullu derleme kullanabilirsiniz:  
  
```  
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 Diğer bir seçenek de stop ifadesinin yerine bir onay açıklaması kullanmaktır. Bir hata ayıklama. onaylama ekstresi, yalnızca belirtilen bir koşul karşılanmazsa ve bir yayın sürümü oluşturduğunuzda otomatik olarak kaldırıldığında yürütmeyi keser. Daha fazla bilgi için bkz. [Yönetilen koddaki Onaylamalar](../debugger/assertions-in-managed-code.md). Hata ayıklama sürümündeki yürütmeyi her zaman kesen bir onay bildirisi isterseniz, bunu yapabilirsiniz:  
  
```  
Debug.Assert(false)  
```  
  
 Diğer bir seçenek de Debug. Fail metodunu kullanmaktır:  
  
```  
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [C#, F # ve Visual Basic proje türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
