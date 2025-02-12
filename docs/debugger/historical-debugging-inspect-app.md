---
title: Geçmiş hata ayıklama bilgileriyle | Microsoft Docs
description: Bir C# konsol uygulamasındaki bir hatayı izlemek için IntelliTrace geçmiş hata ayıklamasını kullanan bir araştırmayı izleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 629b5d93-39b2-430a-b8ba-d2a47fdf2584
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 590ddc45d764b7bfffe54cb15e12463f2749f187
ms.sourcegitcommit: 7a300823cf1bd3355be03bde561cf2777bc09eae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "133978179"
---
# <a name="inspect-your-app-with-intellitrace-historical-debugging-in-visual-studio-c-visual-basic-c"></a>Visual Studio'de (C#, Visual Basic, C++) IntelliTrace geçmiş hata ayıklaması ile uygulamanızı inceleme

Geçmiş hata [ayıklamayı kullanarak,](../debugger/historical-debugging.md) uygulamanın yürütülmesiyle geriye ve ileriye doğru hareket edebilir ve durumunu inceebilirsiniz.

IntelliTrace'i Visual Studio Enterprise veya Professional veya Community kullanabilirsiniz.

## <a name="navigate-your-code-with-historical-debugging"></a>Geçmiş hata ayıklama ile kodunuzda gezinme

Hataya sahip basit bir programla başlayalım. Bir C# konsol uygulamasında aşağıdaki kodu ekleyin:

```csharp
static void Main(string[] args)
{
    int testInt = 0;
    int resultInt = AddIterative(testInt);
    Console.WriteLine(resultInt);
}
private static int AddIterative(int j)
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

Çağrısı sonrasında beklenen değerinin `resultInt` `AddIterative()` 20 olduğunu varsayacağız `testInt` (20 kez artırmanın sonucu). (Ayrıca hatanın içinde görene olmadığınız da `AddInt()` varsayacağız). Ancak sonuç aslında 44'tir. Hatayı 10 kez adımlamadan `AddIterative()` nasıl bulamıyorum? Hatayı daha hızlı ve daha kolay bulmak için geçmiş hata ayıklamayı kullanabiliriz. Aşağıdaki adımları uygulayın:

1. Araçlar **> Seçenekler > IntelliTrace > Genel** altında IntelliTrace'in etkinleştirildiğinden emin olun ve **IntelliTrace** olayları ile çağrı bilgilerini seçin. Bu seçeneği kullanmayacaksanız gezinti bölmesini (aşağıda açıklanmıştır) göreyebilirsiniz.

2. Satırda bir kesme noktası `Console.WriteLine(resultInt);` ayarlayın.

3. Hata ayıklamayı başlatın. Kod kesme noktası üzerinde yürütülür. Yereller **penceresinde** değerinin `resultInt` 44 olduğunu görebilirsiniz.

4. Tanılama Araçları **penceresini** açın (**Hata ayıklama > Show Tanılama Araçları**). Kod penceresi şu şekilde görünür:

    ![Kesme noktasındaki kod penceresi](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")

5. Sol kenar boşluğunda, kesme noktası üzerinde çift ok görüyor gerekir. Bu alan gezinti bölmesi olarak adlandırılan ve geçmiş hata ayıklama için kullanılır. Oka tıklayın.

    Kod penceresinde, önceki kod satırı ( ) pembe `int resultInt = AddIterative(testInt);` renklendirilmiştir. Pencerenin üzerinde, artık geçmiş hata ayıklamada olduğunuz bir ileti görüyorsanız.

    Kod penceresi şu şekilde görünür:

    ![geçmiş hata ayıklama modunda kod penceresi](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")

6. Artık yöntemine `AddIterative()` adımlayabilirsiniz (**F11**  veya gezinti bölmesindeki Adımla düğmesi). İleri (**F10** veya **gezinti bölmesinde sonraki çağrıya** git). Pembe çizgi artık `j = AddInt(j);` çizginin üzerindedir. **Bu durumda F10,** bir sonraki kod satırına adımlanmaz. Bunun yerine, sonraki işlev çağrısına adımlar. Geçmiş hata ayıklama çağrısından çağrısına gider ve işlev çağrısı içermeden kod satırlarını atlar.

7. Şimdi yöntemine `AddInt()` adım at. Hatayı bu kodda hemen görüyor olun.

## <a name="next-steps"></a>Sonraki adımlar

Bu yordam, geçmiş hata ayıklama ile neler yapalarının yüzeyini karaladı.

- Hata ayıklama sırasında anlık görüntüleri görüntülemek için [bkz. IntelliTrace kullanarak önceki uygulama eyaletlerini inceleme.](../debugger/view-historical-application-state.md)
- Farklı ayarlar ve gezinti bölmesindeki farklı düğmelerin etkileri hakkında daha fazla bilgi için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md).
