---
title: İşlevi Yüzlerce Kere Çağırırken Hangi Çağrının Başarısız Olduğunu Nasıl Bilebilirim? | Microsoft Belgeleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fba5032860e21bbd323b8e49d5f32ab9b6f90540
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688126"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>İşlevi Yüzlerce Kere Çağırırken Hangi Çağrının Başarısız Olduğunu Nasıl Bilebilirim?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sorun Açıklaması  
 Programım, belirli bir işleve yapılan çağrıda başarısız olur `CnvtV` . Program muhtemelen bu işlevi başarısız bir şekilde birkaç yüz kez çağırıyor. Üzerinde bir konum kesme noktası ayarlarsanız `CnvtV` , program bu işleve yapılan her çağrıda duraklar ve bunu istemiyorum. Çağrının başarısız olmasına neden olan koşullar bilinmiyor, bu nedenle koşullu kesme noktası ayarlayamıyorum. Ne yapabilirim?  
  
## <a name="solution"></a>Çözüm  
 **Isabet sayısı** alanıyla işlevde bir kesme noktasını bir değere, bu sayede hiçbir daha fazla ulaşılmayacak şekilde ayarlayabilirsiniz. Bu durumda, işleve `CnvtV` birkaç yüz kez çağrıldığını düşüntiğinden, **isabet sayısını** 1000 veya daha fazla olarak ayarlayabilirsiniz. Ardından programı çalıştırın ve çağrının başarısız olmasını bekleyin. Başarısız olduğunda, kesme noktaları penceresini açın ve kesme noktaları listesine bakın. Üzerinde ayarladığınız kesme noktası `CnvtV` , ardından isabet sayısı ve kalan yineleme sayısı ile gösterilir:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Artık, bu işlevin 101 çağrısında başarısız olduğunu bilirsiniz. Kesme noktasını 101 olan bir isabet sayısıyla sıfırlayıp programı yeniden çalıştırırsanız program, `CnvtV` başarısız olmasına neden olan çağrıya yanıt vermez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kod SSS hatalarını ayıklama](../debugger/debugging-native-code-faqs.md)   
 [Kesme noktalarını ayarlama](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
