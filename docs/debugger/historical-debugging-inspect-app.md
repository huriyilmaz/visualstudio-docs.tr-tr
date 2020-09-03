---
title: Geçmiş hata ayıklama ile uygulamanızı inceleyin | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: efabc8cd185daed4f018e3e4209e391b5bc39f44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350452"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio-c-visual-basic-c"></a>Visual Studio 'da IntelliTrace geçmiş hata ayıklama ile uygulamanızı İnceleme (C#, Visual Basic, C++)

[Geçmiş hata ayıklamayı](../debugger/historical-debugging.md) , geri gitmek ve uygulamanızın yürütülmesi boyunca İleri doğru taşımak ve durumunu incelemek için kullanabilirsiniz.

IntelliTrace 'i Visual Studio Enterprise sürümünde kullanabilir, ancak Professional veya Community sürümlerinde kullanamazsınız.

## <a name="navigate-your-code-with-historical-debugging"></a>Geçmiş hata ayıklama ile kodunuzda gezinin

Hata içeren basit bir programla başlayalım. Bir C# konsol uygulamasında aşağıdaki kodu ekleyin:

```csharp
static void Main(string[] args)
{
    int testInt = 0;
    int resultInt = AddAll(testInt);
    Console.WriteLine(resultInt);
}
private static int AddAll(int j)
{
    for (int i = 0; i < 20; i++)
    {
        j = AddInt(j);
    }
    return j;
}

private static int AddInt(int add)
{
    if (add == 10)
    {
        return add += 25;
    }
    return ++add;
}
```

Çağırma sonrasında beklenen değerin 20 olduğunu varsayacağız `resultInt` `AddAll()` (20 kat arttırılmasının sonucu `testInt` ). (Ayrıca, içinde hatayı göremedik `AddInt()` ). Ancak sonuç aslında 44 ' dir. Hatayı 10 kez adımla nasıl bulabiliriz `AddAll()` ? Hatayı daha hızlı ve daha kolay bulmak için geçmiş hata ayıklamayı kullanabiliriz. Bunu yapmak için:

1. **Araçlar > seçenekler > ıntellitrace > Genel**, IntelliTrace 'in etkinleştirildiğinden emin olun ve **IntelliTrace olayları ve çağrı bilgileri**' ni seçin. Bu seçeneği seçmezseniz, gezinti Cilt payının (aşağıda açıklandığı gibi) görümeyeceksiniz.

2. Satırda bir kesme noktası ayarlayın `Console.WriteLine(resultInt);` .

3. Hata ayıklamayı başlatın. Kod kesme noktasına yürütülür. **Yereller** penceresinde, değerinin 44 olduğunu görebilirsiniz `resultInt` .

4. **Tanılama araçları** penceresini açın (**hata ayıkla > tanılama araçları göster**). Kod penceresi şöyle görünmelidir:

    ![Kesme noktasında kod penceresi](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")

5. Sol kenar boşluğunun yanında, kesme noktasının hemen üzerinde bir çift ok görmeniz gerekir. Bu alana gezinti cilt payı denir ve geçmiş hata ayıklama için kullanılır. Oka tıklayın.

    Kod penceresinde, yukarıdaki kod satırının ( `int resultInt = AddIterative(testInt);` ) pembe renkte olduğunu görmeniz gerekir. Pencerenin üstünde, şimdi geçmiş hata ayıklamada olduğunuz bir ileti görmeniz gerekir.

    Kod penceresi şimdi şöyle görünür:

    ![geçmiş hata ayıklama modundaki kod penceresi](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")

6. Şimdi, `AddAll()` Gezinti cilt payındaki yönteme (**F11**veya **Step into** düğmesine) erişebilirsiniz. İleri (**F10**) veya gezinti cilt payındaki **sonraki çağrıya git** . Pembe çizgi artık `j = AddInt(j);` satır üzerinde. Bu durumda **F10** , sonraki kod satırına ilerlemez. Bunun yerine, sonraki işlev çağrısının adımları vardır. Geçmiş hata ayıklama çağrıdan çağrıya gider ve bir işlev çağrısı içermeyen kod satırlarını atlar.

7. Şimdi yöntemine adımlayın `AddInt()` . Hatayı Bu kodda hemen görmeniz gerekir.

## <a name="next-steps"></a>Sonraki adımlar

Bu yordam, geçmiş hata ayıklaması ile yapabileceklerinize ilişkin yüzeyi ortaya ayıklamış.

- Hata ayıklama sırasında anlık görüntüleri görüntülemek için bkz. [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md).
- Farklı ayarlar hakkında daha fazla bilgi edinmek ve gezinti cilt payı içindeki farklı düğmelerin etkileri hakkında daha fazla bilgi edinmek için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md).
