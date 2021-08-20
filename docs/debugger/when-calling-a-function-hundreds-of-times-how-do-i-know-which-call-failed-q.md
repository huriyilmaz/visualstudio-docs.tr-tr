---
title: Bir işlev birçok kez çağrılırken çağrı hatası bulma
description: Kesmenin yalnızca işlevin başarısız olduğu çağrıda gerçekleşmesi için işlevde kesme noktası ayarlama tekniğine bakın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 702a9ea54164fa4fa3fd62749c7e9aae18596266
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074091"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>İşlevi Yüzlerce Kere Çağırırken Hangi Çağrının Başarısız Olduğunu Nasıl Bilebilirim?
## <a name="problem-description"></a>Sorun Açıklaması
 Programım belirli bir işlev çağrısında başarısız `CnvtV` oluyor. Program büyük olasılıkla başarısız olmadan önce bu işlevi birkaç yüz kez çağırıyordur. üzerinde bir konum kesme noktası ayarlamam, program bu işleve yapılan her çağrıda durur ve `CnvtV` bunu istemiyorum. Çağrının başarısız olması için hangi koşulların neden olduğunu bilmiyorum, bu nedenle koşullu kesme noktası ayarlay bilmiyorum. Ne yapabilirim?

## <a name="solution"></a>Çözüm
 Hit **Count** alanına sahip işlevin kesme noktası değerini hiçbir zaman ulaşmayacak kadar yüksek bir değere ayarlayın. Bu durumda, işlevin birkaç yüz kez çağrıltığına inanıyorsunuz çünkü Hit `CnvtV` **Count'i** 1000 veya daha fazla olarak ayarlanmış olabilir. Ardından programı çalıştırın ve çağrının başarısız olması için bekleyin. Başarısız olduğunda Kesme Noktaları penceresini açın ve kesme noktaları listesine bakın. Ayar tarihi olarak ayar tarihi `CnvtV` ve ardından kalan isabet sayısı ve yineleme sayısı görüntülenir:

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 Artık işlevin 101. çağrıda başarısız olduğunu biliyorsunuz. Kesme noktası 101 isabet sayısıyla sıfırlanır ve programı yeniden çalıştırsanız, program başarısız olması için `CnvtV` çağrısında durur.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama hakkında SSS](../debugger/debugging-native-code-faqs.md)
- [Kesme Noktaları Ayarlama](/previous-versions/ktf38f66(v=vs.100))
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)