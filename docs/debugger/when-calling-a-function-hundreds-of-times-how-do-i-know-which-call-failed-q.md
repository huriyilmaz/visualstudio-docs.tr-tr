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
ms.openlocfilehash: 4790fa8c6fd0bba5b513fd2ce3d203b552b6c63b
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599998"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>İşlevi Yüzlerce Kere Çağırırken Hangi Çağrının Başarısız Olduğunu Nasıl Bilebilirim?
## <a name="problem-description"></a>Sorun Açıklaması
 Programım, belirli bir işleve yapılan çağrıda başarısız olur `CnvtV` . Program muhtemelen bu işlevi başarısız bir şekilde birkaç yüz kez çağırıyor. Üzerinde bir konum kesme noktası ayarlarsanız `CnvtV` , program bu işleve yapılan her çağrıda duraklar ve bunu istemiyorum. Çağrının başarısız olmasına neden olan koşullar bilinmiyor, bu nedenle koşullu kesme noktası ayarlayamıyorum. Ne yapabilirim?

## <a name="solution"></a>Çözüm
 **Isabet sayısı** alanıyla işlevde bir kesme noktasını bir değere, bu sayede hiçbir daha fazla ulaşılmayacak şekilde ayarlayabilirsiniz. Bu durumda, işleve `CnvtV` birkaç yüz kez çağrıldığını düşüntiğinden, **isabet sayısını** 1000 veya daha fazla olarak ayarlayabilirsiniz. Ardından programı çalıştırın ve çağrının başarısız olmasını bekleyin. Başarısız olduğunda, kesme noktaları penceresini açın ve kesme noktaları listesine bakın. Üzerinde ayarladığınız kesme noktası `CnvtV` , ardından isabet sayısı ve kalan yineleme sayısı ile gösterilir:

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 Artık, bu işlevin 101 çağrısında başarısız olduğunu bilirsiniz. Kesme noktasını 101 olan bir isabet sayısıyla sıfırlayıp programı yeniden çalıştırırsanız program, `CnvtV` başarısız olmasına neden olan çağrıya yanıt vermez.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kod Hata Ayıklaması SSS](../debugger/debugging-native-code-faqs.md)
- [Kesme noktalarını ayarlama](/previous-versions/ktf38f66(v=vs.100))
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)