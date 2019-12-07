---
title: Değişkenleri - denetleyin Otolar ve yerel öğeler pencerelerinde | Microsoft Docs
ms.custom: seodec18
ms.date: 10/18/2018
ms.topic: conceptual
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
ms.openlocfilehash: b159f631534135ac568fb03dbffa46ae0360fc47
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2019
ms.locfileid: "74904118"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Otolar ve yerel öğeler pencerelerinde değişkenleri denetleyin

**Otolar** ve **Yereller** windows ayıklarken değişken değerleri gösterir. Windows, yalnızca hata ayıklama oturumu sırasında kullanılabilir. **Otolar** geçerli kesme noktası kullanılan değişkenler penceresi gösterir. **Yereller** penceresi, genellikle geçerli işlev veya yöntem olan yerel kapsamda tanımlanan değişkenler gösterir. Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce mutlak yeni başlayanlar ve [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md) [için hata ayıklamayı](../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

 **Otolar** penceresi, kullanılabilir C#, Visual Basic, C++ ve Python kodu, ancak JavaScript veya F#.

Açmak için **Otolar** hata ayıklarken, penceresinde **hata ayıklama** > **Windows** > **Otolar**, veya tuşuna basın **Ctrl**+**Alt**+**V** > **A**.

Açmak için **Yereller** hata ayıklarken, penceresinde **hata ayıklama** > **Windows** > **Yereller**, veya tuşuna basın **Alt**+**4**.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz: [Mac için Visual Studio'da veri görselleştirmeleri](/visualstudio/mac/data-visualizations).

## <a name="use-the-autos-and-locals-windows"></a>Otolar ve yerel öğeler pencerelerinde kullanın

Diziler ve nesneleri göster **Otolar** ve **Yereller** ağaç denetimleri olarak windows. Görünümü alanlar ve Özellikler'i gösterecek şekilde genişletmek için bir değişken adının sol tarafındaki oku seçin. İşte bir örnek bir <xref:System.IO.FileStream?displayProperty=fullName> nesnesine **Yereller** penceresi:

![Yereller-FILESTREAM](../debugger/media/locals-filestream.png "Yereller-FILESTREAM")

Kırmızı bir değer **Yereller** veya **Otolar** penceresi anlamına gelir değeri son değerlendirme bu yana değişti. Değişiklik, bir önceki hata ayıklama oturumundan olabilir veya penceresinde değeri değiştirildi.

Hata ayıklayıcı pencerelerinde varsayılan sayısal biçimi ondalık. Onaltılığa değiştirmek için sağ **Yereller** veya **Otolar** penceresi ve select **onaltılık gösterim**. Bu değişiklik tüm hata ayıklayıcı pencereleri etkiler.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Otomatik değişkenler veya yerel öğeler penceresinde değişken değerlerini düzenleyin

Çoğu değişkenin değerlerini düzenlemek için **Otolar** veya **Yereller** windows değerine çift tıklayın ve yeni bir değer girin.

Örneğin bir değer için bir ifade girin `a + b`. Hata ayıklayıcı en geçerli dili ifadelerini kabul eder.

Yerel C++ kod içinde bir değişken adının bağlamını nitelemeniz gerekebilir. Daha fazla bilgi için [bağlam işleci (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Değerleri ve ifadeleri değiştirmeden önce sonuçları anladığınızdan emin olun. Olası bazı sorunlar şunlardır:
>
>- Bazı ifadelerin değerlendirilmesi bir değişkenin değerini değiştirebilir veya aksi halde, programınızın durumunu etkileyebilir. Örneğin, değerlendirme `var1 = ++var2` hem değerini değiştirir `var1` ve `var2`. Bu deyimler olduğu söylenir [yan etkileri](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)). Yan etkiler, bunları uyumlu değilse, beklenmeyen sonuçlara neden olabilir.
>
>- Kayan nokta değerlerini düzenlemek, kesirli bileşenlerin ondalıktan ikiliye dönüştürülmesi nedeniyle küçük yanlışlıklara neden olabilir. Görünüşte zararsız bir düzenleme bitler kayan nokta değişkenindeki bazı değişikliklere neden olabilir.

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
![özellik adlarını değiştirme](../debugger/media/toggle-property-names.gif "Özellik adlarını değiştirme")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Bağlam otomatik değişkenler veya yerel öğeler penceresi için değiştirin

Kullanabileceğiniz **hata ayıklama konumu** istenen işlevi, iş parçacığı veya bağlamı değiştiren işlem seçmek için araç **Otolar** ve **Yereller** windows.

Etkinleştirmek için **hata ayıklama konumu** araç seçin ve araç çubuğu alanı boş bir bölümünden tıklama **hata ayıklama konumu** açılan ya da seçin **görünümü**  >   **Araç çubukları** > **hata ayıklama konumu**.

Bir kesme noktası ayarlayın ve hata ayıklamaya başlayın. Kesme noktası isabet edildiğinde yürütme duraklatır ve konumda görebilirsiniz **hata ayıklama konumu** araç çubuğu.

![Hata ayıklama konumu araç çubuğu](../debugger/media/debuglocationtoolbar.png "Hata Ayıklama Konumu araç çubuğu")

## <a name="bkmk_whatvariables"></a> Otomatik değişkenler penceresi değişkenleri (C#, C++, Visual Basic, Python)

Farklı kod dilleri görüntülemek farklı değişkenlerinde **Otolar** penceresi.

- İçinde C# ve Visual Basic **Otolar** geçerli ya da önceki satırında kullanılan herhangi bir değişken penceresinde görüntülenir. Örneğin, C# veya kod, aşağıdaki dört değişkenleri bildirin Visual Basic:

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

   Satırına bir kesme noktası ayarlamak `c = 3;`, ve hata ayıklayıcıyı başlatın. Yürütme durakladığında **Otolar** penceresi görüntülenir:

   ![Oto 'lar-CSharp](../debugger/media/autos-csharp.png "Oto 'lar-CSharp")

   Değerini `c` 0, çünkü satır `c = 3` henüz çalıştırılmadı.

- C++ ' ta **Otolar** nerede yürütülmesi duraklatıldı geçerli satırı önce en az üç satır içinde kullanılan değişkenler penceresinde görüntülenir. Örneğin, C++ kodu altı değişkenleri bildirin:

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

    Satırına bir kesme noktası ayarlamak `e = 5;` ve hata ayıklayıcı çalıştırın. Yürütme sona erdiğinde, **Otolar** penceresi görüntülenir:

    ![OtolarC++](../debugger/media/autos-cplus.png "OtolarC++")

    Değişken `e` olduğundan başlatılmadı satır `e = 5` henüz çalıştırılmadı.

## <a name="bkmk_returnValue"></a> Yöntem çağrılarının dönüş değerlerini görüntüleme
 .NET ve C++ kodunda, dönüş değerlerini inceleyebilirsiniz **Otolar** üzerinden veya bir yöntem çağrısının dışına adımladığınızda penceresi. Görüntüleme yöntem çağrısının dönüş yerel değişkenlerle depolanmaz değerleri kullanışlı olabilir. Bir yöntemi, bir parametre veya başka bir yöntemin dönüş değeri olarak kullanılabilir.

 Örneğin, aşağıdaki C# kod iki işlev dönüş değerlerini ekler:

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

Dönüş değerleri görmek için `sumVars()` ve `subtractVars()` yöntemini çağırır Otolar penceresinde:

1. Bir kesme noktası ayarlamak `int x = sumVars(a, b) + subtractVars(c, d);` satır.

1. Hata ayıklamayı başlatmak ve yürütme kesme noktasında durakladığında seçin **Step Over** veya basın **F10**. Aşağıdaki dönüş değerleri görmelisiniz **Otolar** penceresi:

  ![Oto dönüş değeriC#](../debugger/media/autosreturnvaluecsharp2.png "Oto dönüş değeriC#")

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklıyor?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcısı pencereleri](../debugger/debugger-windows.md)
