---
title: Değişkenleri İnceleme-oto ve Yereller Windows | Microsoft Docs
ms.custom: seodec18
ms.date: 10/18/2018
ms.topic: how-to
f1_keywords:
- vs.debug.autos
- vs.debug.locals
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ae67fadf5d9710f2088f47617b74eeeb8212826
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350751"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Oto ve Yereller pencerelerinde değişkenleri İnceleme

Hata ayıklarken, **oto** ve **Locals** pencereleri değişken değerlerini gösterir. Pencereler yalnızca hata ayıklama oturumu sırasında kullanılabilir. **Oto** penceresi, geçerli kesme noktası etrafında kullanılan değişkenleri gösterir. **Yereller** penceresi, genellikle geçerli işlev veya yöntem olan yerel kapsamda tanımlanan değişkenleri gösterir. Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce mutlak yeni başlayanlar ve [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md) [için hata ayıklamayı](../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

 Bu **pencere,** JavaScript veya F # Için değil C#, Visual Basic, C++ ve Python kodu için kullanılabilir.

Hata ayıklama sırasında **oto** penceresini açmak için Windows oto **hatalarını ayıkla**  >  **Windows**  >  **Autos**' yı seçin veya **CTRL** + **alt** + **V**  >  **A**tuşlarına basın.

**Yereller** penceresini açmak için hata ayıklama sırasında **Debug**  >  **Windows**  >  **yerelleri**Hata Ayıkla ' yı seçin veya **alt** + **4**' e basın.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio veri görselleştirmeleri](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Oto ve Yereller pencerelerini kullanma

Diziler ve nesneler, ağaç denetimleri olarak **oto** ve **Yereller** pencerelerinde gösterilir. Alanı ve özellikleri göstermek üzere görünümü genişletmek için bir değişken adının solundaki oku seçin. <xref:System.IO.FileStream?displayProperty=fullName> **Locals** penceresinde bir nesne örneği aşağıda verilmiştir:

![Yereller-FILESTREAM](../debugger/media/locals-filestream.png "Yereller-FILESTREAM")

**Yereller** veya **oto** penceresinde kırmızı bir değer, en son değerlendirmeden bu yana değerin değiştiği anlamına gelir. Değişiklik, önceki bir hata ayıklama oturumundan veya penceredeki değeri değiştirdiğiniz için olabilir.

Hata ayıklayıcı pencerelerinin varsayılan sayısal biçimi Decimal 'dir. Onaltılık olarak değiştirmek için, **Yereller** veya **oto** penceresinde sağ tıklayın ve **Onaltılı görüntü**' i seçin. Bu değişiklik, tüm hata ayıklayıcı pencerelerini etkiler.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Oto veya Yereller penceresinde değişken değerlerini düzenleme

**Oto** veya **Yereller** pencerelerinde çoğu değişkenin değerlerini düzenlemek için, değere çift tıklayın ve yeni değeri girin.

Örneğin, bir değer için bir ifade girebilirsiniz `a + b` . Hata ayıklayıcı çoğu geçerli dil ifadesini kabul eder.

Yerel C++ kodunda, bir değişken adının bağlamını nitelemeniz gerekebilir. Daha fazla bilgi için bkz. [Bağlam işleci (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Değerleri ve ifadeleri değiştirmeden önce sonuçları anladığınızdan emin olun. Olası bazı sorunlar şunlardır:
>
>- Bazı ifadelerin değerlendirilmesi, bir değişkenin değerini değiştirebilir veya programınızın durumunu etkileyebilir. Örneğin, değerlendirmek için `var1 = ++var2` hem hem de değeri değişir `var1` `var2` . Bu ifadelerin [yan etkileri](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))olduğu söylenir. Yan etkileri, bunlardan haberdar değilseniz beklenmedik sonuçlara neden olabilir.
>
>- Kayan nokta değerlerini düzenlemek, kesirli bileşenlerin ondalıktan ikiliye dönüştürülmesi nedeniyle küçük yanlışlıklara neden olabilir. Anlık zararsız bir düzenleme bile kayan nokta değişkeninde bazı bitlerin değişikliklerine neden olabilir.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Oto veya Yereller penceresinde ara

Her pencerenin üzerindeki arama çubuğunu kullanarak, **oto** veya **Yereller** penceresinin Ad, değer ve tür sütunlarında anahtar sözcük araması yapabilirsiniz. Bir arama yürütmek için ENTER tuşuna basın veya oklardan birini seçin. Devam eden bir aramayı iptal etmek için arama çubuğundaki "x" simgesini seçin.

Bulunan eşleşmeler arasında gezinmek için sol ve sağ okları (sırasıyla SHIFT + F3 ve F3) kullanın.

![Yereller penceresinde ara](../debugger/media/ee-search-locals.png "Yereller penceresinde ara")

Aramanızı daha fazla veya daha az kapsamlı hale getirmek için, iç içe geçmiş nesnelerde kaç düzey derinlikte arama yapmak istediğinizi seçmek üzere, **oto s** veya **Locals** penceresinin en üstündeki **arama daha derin** açılan listesini kullanın. 

## <a name="pin-properties-in-the-autos-or-locals-window"></a>Oto veya Yereller penceresinde sabitleme özellikleri

> [!NOTE]
> Bu özellik .NET Core 3,0 veya üzeri sürümlerde desteklenir.

Hızlı bir şekilde nesneleri, Windows ve yerel öğeler pencerelerinde, **Pinınspectlik özellikleri** aracıyla hızlıca inceleyebilirsiniz.  Bu aracı kullanmak için bir özelliğin üzerine gelin ve görüntülenen sabitleme simgesini seçin ya da sağ tıklayın ve ortaya çıkan bağlam menüsünde **üyeyi sık kullanılanlara sabitle** seçeneğini belirleyin.  Bu özelliği nesnenin özellik listesinin en üstüne, özellik adı ve değeri ise **değer** sütununda görüntülenir.  Bir özelliği kaldırmak için, PIN simgesini yeniden seçin veya bağlam menüsünde **üyeyi sık kullanılanlara ayır** seçeneğini belirleyin.

![Yereller penceresindeki sabitleme özellikleri](../debugger/media/basic-pin.gif "Yereller penceresindeki sabitleme özellikleri")

Ayrıca, oto veya yerel öğeler pencerelerinde nesnenin özellik listesini görüntülerken özellik adlarını açıp sabitlenmemiş özellikleri filtreleyebilirsiniz.  Her seçeneğe, oto veya Yereller pencerelerinin üstündeki araç çubuğunda bulunan düğmeleri seçerek erişebilirsiniz.

![Sık kullanılan özellikleri filtrele](../debugger/media/filter-pinned-properties-locals.png "Sık kullanılan özellikleri filtrele") 
 ![Özellik adlarını değiştirme](../debugger/media/toggle-property-names.gif "Özellik adlarını değiştirme")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Oto veya Yereller penceresinin bağlamını değiştirme

**Hata ayıklama konumu** araç çubuğunu, **oto** ve **Yereller** pencerelerinin bağlamını değiştiren istenen bir işlevi, iş parçacığını veya işlemi seçmek için kullanabilirsiniz.

**Hata ayıklama konumu** araç çubuğunu etkinleştirmek için, araç çubuğu alanının boş bir bölümüne tıklayın ve açılan menüden **hata ayıklama konumu** ' nu seçin ya da **View**  >  **araç çubuğu**  >  **hata ayıklama konumunu**görüntüle ' yi seçin.

Bir kesme noktası ayarlayın ve hata ayıklamayı başlatın. Kesme noktası isabet edildiğinde, yürütme duraklatılır ve konumu **hata ayıklama konumu** araç çubuğunda görebilirsiniz.

![Hata Ayıklama Konumu araç çubuğu](../debugger/media/debuglocationtoolbar.png "Hata Ayıklama Konumu araç çubuğu")

## <a name="variables-in-the-autos-window-c-c-visual-basic-python"></a><a name="bkmk_whatvariables"></a> Oto penceresindeki değişkenler (C#, C++, Visual Basic, Python)

Farklı kod dilleri, **oto** penceresinde farklı değişkenler görüntüler.

- C# ve Visual Basic içinde, **oto** penceresinde geçerli veya önceki satırda kullanılan herhangi bir değişken görüntülenir. Örneğin, C# veya Visual Basic Code 'da aşağıdaki dört değişkeni bildirin:

   ```csharp
       public static void Main()
       {
          int a, b, c, d;
          a = 1;
          b = 2;
          c = 3;
          d = 4;
       }
   ```

   Satırda bir kesme noktası ayarlayın `c = 3;` ve hata ayıklayıcıyı başlatın. Yürütme durakladığında, **oto** penceresi görüntülenecektir:

   ![Oto 'lar-CSharp](../debugger/media/autos-csharp.png "Oto 'lar-CSharp")

   `c`Satırı henüz yürütülmediği için değeri 0 ' dır `c = 3` .

- C++ ' da, **oto** , yürütmenin duraklatıldığı geçerli satırdan önce en az üç satırda kullanılan değişkenleri görüntüler. Örneğin, C++ kodunda altı değişken bildirin:

   ```C++
       void main() {
           int a, b, c, d, e, f;
           a = 1;
           b = 2;
           c = 3;
           d = 4;
           e = 5;
           f = 6;
       }
   ```

    Satırda bir kesme noktası ayarlayın `e = 5;` ve hata ayıklayıcıyı çalıştırın. Yürütme durdurulduğunda, **oto** penceresi görüntülenecektir:

    ![Oto s-C + +](../debugger/media/autos-cplus.png "Oto s-C + +")

    `e`Satır `e = 5` henüz yürütülmediği için değişken başlatılmamış.

## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> Yöntem çağrılarının dönüş değerlerini görüntüle
 .NET ve C++ kodunda, bir yöntem çağrısının üstündeyken veya dışına dönerek, dönüş değerlerini, **oto s** penceresinde inceleyebilirsiniz. Yöntem çağrısı döndürme değerlerini görüntüleme, yerel değişkenlerde depolanmayan yararlı olabilir. Bir yöntem bir parametre olarak veya başka bir yöntemin dönüş değeri olarak kullanılabilir.

 Örneğin, aşağıdaki C# kodu iki işlevin dönüş değerlerini ekler:

```csharp
static void Main(string[] args)
{
    int a, b, c, d;
    a = 1;
    b = 2;
    c = 3;
    d = 4;
    int x = sumVars(a, b) + subtractVars(c, d);
}

private static int sumVars(int i, int j)
{
    return i + j;
}

private static int subtractVars(int i, int j)
{
    return j - i;
}
```

`sumVars()`Ve yöntem çağrılarının dönüş değerlerini, `subtractVars()` oto penceresinde görmek için:

1. Satırda bir kesme noktası ayarlayın `int x = sumVars(a, b) + subtractVars(c, d);` .

1. Hata ayıklamayı başlatın ve yürütme kesme noktasında durakladığında, **Atla** ' yı seçin veya **F10**tuşuna basın. Aşağıdaki dönüş değerlerini, **oto s** penceresinde görmeniz gerekir:

  ![Cs dönüş değeri C #](../debugger/media/autosreturnvaluecsharp2.png "Cs dönüş değeri C #")

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama bölümüne ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcı pencereleri](../debugger/debugger-windows.md)
