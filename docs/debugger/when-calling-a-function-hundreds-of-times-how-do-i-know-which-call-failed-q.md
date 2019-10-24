---
title: Bir işlevi birçok kez çağırırken hangi çağrının başarısız olduğunu bulun | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d054c60c45980b3d08b09987229febb99593090
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728043"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>İşlevi Yüzlerce Kere Çağırırken Hangi Çağrının Başarısız Olduğunu Nasıl Bilebilirim?
## <a name="problem-description"></a>Sorun açıklaması
 Programımı belirli bir işleve yapılan çağrıda başarısız olur, `CnvtV`. Program muhtemelen bu işlevi başarısız bir şekilde birkaç yüz kez çağırıyor. @No__t_0 bir konum kesme noktası ayarlarsanız, program bu işleve yapılan her çağrıda duraklar ve bunu istemiyorum. Çağrının başarısız olmasına neden olan koşullar bilinmiyor, bu nedenle koşullu kesme noktası ayarlayamıyorum. Ne yapabilirim?

## <a name="solution"></a>Çözüm
 **Isabet sayısı** alanıyla işlevde bir kesme noktasını bir değere, bu sayede hiçbir daha fazla ulaşılmayacak şekilde ayarlayabilirsiniz. Bu durumda, `CnvtV` işlevin birkaç yüz kez çağrıldığını düşüntiğinden, **Isabet sayısını** 1000 veya daha fazla olarak ayarlayabilirsiniz. Ardından programı çalıştırın ve çağrının başarısız olmasını bekleyin. Başarısız olduğunda, kesme noktaları penceresini açın ve kesme noktaları listesine bakın. @No__t_0 üzerinde ayarladığınız kesme noktası, ardından isabet sayısı ve kalan yineleme sayısı ile gösterilir:

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 Artık, bu işlevin 101 çağrısında başarısız olduğunu bilirsiniz. Kesme noktası olan 101 ' ı bir isabet sayısıyla sıfırlayıp programı yeniden çalıştırırsanız, program başarısız olmasına neden olan `CnvtV` çağrısında durmaktadır.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama SSS](../debugger/debugging-native-code-faqs.md)
- [Kesme noktalarını ayarlama](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
