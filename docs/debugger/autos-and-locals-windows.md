---
title: Değişkenleri inceleme - Otomatikler ve Yereller windows | Microsoft Docs
description: Yerel ayarlarda hata ayıklarken Otomatikler ve Yereller pencerelerinde değişkenleri Visual Studio. Otomatikler ve Yereller pencereleri, hata ayıklama sırasında değişken değerlerini gösterir.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 536a14065a86541e7748858f64229c5c5a0ab04f63c3d4f10025e68747ffec49
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346323"
---
# <a name="inspect-variables-in-the-autos-and-locals-windows"></a>Otomatikler ve Yereller pencerelerinde değişkenleri inceleme

Otomatikler **ve** **Yereller pencereleri,** hata ayıklama sırasında değişken değerlerini gösterir. Pencereler yalnızca hata ayıklama oturumu sırasında kullanılabilir. Otomatikler **penceresinde** geçerli kesme noktası etrafında kullanılan değişkenler gösterilir. Yereller **penceresinde** yerel kapsamda tanımlanan değişkenler gösterilir ve bu genellikle geçerli işlev veya yöntemdir.

> [!NOTE]
> Bu kodda ilk kez hata ayıklamayı denediyseniz, bu [](../debugger/debugging-absolute-beginners.md) makaleyi okumadan önce [](../debugger/write-better-code-with-visual-studio.md) yeni başlayanlar için Hata Ayıklama ve Hata ayıklama teknikleri ve araçları makalesine bakabilirsiniz.

 Otomatikler **penceresi** C#, Visual Basic, C++ ve Python kodu için kullanılabilir ancak JavaScript veya F# için kullanılamaz.

Otomatikler penceresini **açmak için,** hata ayıklama sırasında Hata Ayıkla'Windows Otomatikler'i seçin veya  >    >  Ctrl Alt V A  +  + **tuşlarına**  >  **basın.**

Hata ayıklama sırasında **Yereller penceresini** açmak için Yereller'de hata  >  **ayıkla'Windows**  >  **seçin** veya Alt  + **4'e basın.**

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. veri görselleştirmeleri Mac için Visual Studio.](/visualstudio/mac/data-visualizations)

## <a name="use-the-autos-and-locals-windows"></a>Otomatikler ve Yereller pencerelerini kullanma

Diziler ve nesneler, **Otomatikler ve Yereller** **pencerelerinde** ağaç denetimleri olarak gösterir. Alanları ve özellikleri göstermek için görünümü genişletmek için değişken adının sol yanındaki oku seçin. YerelLer penceresindeki <xref:System.IO.FileStream?displayProperty=fullName> bir nesne örneği **aşağıdaki gibidir:**

![Yereller penceresinin ekran görüntüsü, dosya System.IO.FileStream değerine ayarlanmış.](../debugger/media/locals-filestream.png)

Yereller veya Otomatikler **penceresindeki** **kırmızı değer,** değerin son değerlendirmeden bu yana değiştiğini gösterir. Değişiklik, önceki bir hata ayıklama oturumundan veya pencerede değerini değiştirmiş olduğunuz için olabilir.

Hata ayıklayıcı pencerelerde varsayılan sayısal biçim ondalıktır. Bunu onaltılık olarak değiştirmek için Yereller  veya Otomatikler penceresinde sağ tıklayın ve Onaltılık **Görüntü'leri seçin.**  Bu değişiklik tüm hata ayıklayıcı pencerelerini etkiler.

## <a name="edit-variable-values-in-the-autos-or-locals-window"></a>Otomatikler veya Yereller penceresinde değişken değerlerini düzenleme

Otomatikler veya Yereller pencerelerinde **çoğu** **değişkenin** değerlerini düzenlemek için değere çift tıklayın ve yeni değeri girin.

Bir değer için bir ifade girsiniz, örneğin `a + b` . Hata ayıklayıcısı en geçerli dil ifadelerini kabul eder.

Yerel C++ kodunda, değişken adının bağlamını nitelendirebilirsiniz. Daha fazla bilgi için [bkz. Bağlam işleci (C++)](../debugger/context-operator-cpp.md).

>[!CAUTION]
>Değerleri ve ifadeleri değiştirmeden önce sonuçları anlayasınız. Bazı olası sorunlar:
>
>- Bazı ifadelerin değerlendirilmesi değişkenin değerini değiştirebilir veya program durumunu etkileyebilir. Örneğin, değerlendirilmesi `var1 = ++var2` hem hem de değerini `var1` `var2` değiştirir. Bu ifadelerin yan etkileri [olduğu ifade edildi.](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)) Yan etkiler, farkında değilsanız beklenmeyen sonuçlara neden olabilir.
>
>- Kayan nokta değerlerini düzenlemek, kesirli bileşenlerin ondalıktan ikiliye dönüştürülmesi nedeniyle küçük yanlışlıklara neden olabilir. Zararsız gibi görünen bir düzenleme bile kayan nokta değişkende bazı bitlerde değişikliklere neden olabilir.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-autos-or-locals-window"></a>Otomatikler veya Yereller penceresinde arama

Her pencerenin üzerindeki arama çubuğunu kullanarak Otomatikler veya  Yereller  penceresinin Ad, Değer ve Tür sütunlarında anahtar sözcükleri arayabilirsiniz. ENTER tarak arama yürütmek için oklardan birini seçin. Devam eden bir arama işlemini iptal etmek için arama çubuğundaki "x" simgesini seçin.

Bulunan eşleşmeler arasında gezinmek için sol ve sağ okları (sırasıyla Shift+F3 ve F3) kullanın.

![YerelLer Penceresinde Ara](../debugger/media/ee-search-locals.png "YerelLer Penceresinde Ara")

Aramanızı daha fazla veya daha az ayrıntılı hale eklemek için  Otomatikler  veya Yereller penceresinin üst kısmında yer alan Daha Ayrıntılı Ara açılan penceresini kullanarak iç içe nesnelerde kaç düzey derinliğinde arama yapmak istediğinize karar verirsiniz.  

## <a name="pin-properties-in-the-autos-or-locals-window"></a>Otomatikler veya YerelLer penceresinde özellikleri sabitleme

> [!NOTE]
> Bu özellik .NET Core 3.0 veya daha yenisi için de kullanılabilir.

Sabitlenebilir Özellikler aracıyla Otomatikler ve Yereller pencerelerinde nesneleri özelliklerine göre **hızla inceebilirsiniz.**  Bu aracı kullanmak için bir özelliğin üzerine gelin ve görüntülenen sabitleme  simgesini seçin veya sağ tıklayın ve sonuçta elde edilen bağlam menüsünde Üyeyi Sık Kullanılan Olarak Sabitle seçeneğini belirleyin.  Bu, bu özelliği nesnenin özellik listesinin en üstüne kadar gösterir ve Özellik adı ve değeri **Değer** sütununda görüntülenir.  Bir özelliğin sabitlemesini geri eklemek için  sabitleme simgesini yeniden seçin veya bağlam menüsünde Üyeyi Sık Kullanılan olarak Kaldır seçeneğini belirleyin.

![YerelLer penceresinde özellikleri sabitleme](../debugger/media/basic-pin.gif "YerelLer penceresinde özellikleri sabitleme")

Ayrıca özellik adlarını açıp sabitlenmiş olmayan özellikleri Otomatikler veya Yereller pencerelerinde nesnenin özellik listesini görüntülerken filtreleebilirsiniz.  Otomatikler veya Yereller pencerelerinde yer alan araç çubuğundaki düğmeleri seçerek her bir seçence erişebilirsiniz.

![Sık kullanılan özellikleri filtreleme](../debugger/media/filter-pinned-properties-locals.png "Sık kullanılan özellikleri filtreleme") 
 ![Özellik adlarını değiştir](../debugger/media/toggle-property-names.gif "Özellik adlarını değiştir")

::: moniker-end

## <a name="change-the-context-for-the-autos-or-locals-window"></a>Otomatikler veya Yereller penceresinin bağlamını değiştirme

İstediğiniz işlevi, **iş parçacığını** veya işlemi seçmek için Hata Ayıklama Konumu araç çubuğunu kullanabilirsiniz. Bu araç, Otomatikler ve **Yereller** **pencerelerinde bağlamı** değiştirir.

Hata Ayıklama Konumu **araç çubuğunu etkinleştirmek** için araç çubuğu alanında  boş bir bölüme tıklayın ve açılan listeden Hata Ayıklama Konumu'nu seçin veya Araç Çubuklarını Görüntüle Hata Ayıklama  >    >  **Konumu'nu seçin.**

Bir kesme noktası ayarlayın ve hata ayıklamayı başlat. Kesme noktası isabetli olduğunda yürütme duraklatılır ve Hata Ayıklama Konumu araç **çubuğunda konumu** görebilir.

![Hata Ayıklama Konumu araç çubuğu](../debugger/media/debuglocationtoolbar.png "Hata Ayıklama Konumu araç çubuğu")

## <a name="variables-in-the-autos-window-c-c-visual-basic-python"></a><a name="bkmk_whatvariables"></a>Otomatikler penceresindeki değişkenler (C#, C++, Visual Basic, Python)

Farklı kod dilleri, Otomatikler penceresinde farklı **değişkenleri** görüntüler.

- C# ve Visual Basic, **Otomatikler** penceresinde geçerli veya önceki satırda kullanılan tüm değişkenler görüntülenir. Örneğin, C# veya Visual Basic kodunda aşağıdaki dört değişkeni bildirebilirsiniz:

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

   satırda bir kesme noktası ayarlayın `c = 3;` ve hata ayıklayıcıyı başlat. Yürütme duraklatılırsa **Otomatikler** penceresi görüntülenir:

   ![C değerinin 0 olarak ayar olduğu Otomatikler penceresinin ekran görüntüsü.](../debugger/media/autos-csharp.png)

   Satır henüz `c` yürütülmedi olduğundan `c = 3` değeri 0'dır.

- C++ içinde, **Otomatikler** penceresi yürütmenin duraklatılmış olduğu geçerli satırdan önce en az üç satırda kullanılan değişkenleri görüntüler. Örneğin C++ kodunda altı değişken bildirebilirsiniz:

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

    Satırda bir kesme noktası ayarlayın `e = 5;` ve hata ayıklayıcıyı çalıştırın. Yürütme durdurulursa **Otomatikler** penceresi görüntülenir:

    ![3 değerine sahip int c'yi gösteren satırın vurgulanmış olduğu Otomatikler penceresinin ekran görüntüsü.](../debugger/media/autos-cplus.png)

    Satır `e` henüz yürütülmedi olduğundan `e = 5` değişkeninin ilkelleştirilmiş değildir.

## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> Yöntem çağrılarının dönüş değerlerini görüntüleme
 .NET ve C++ kodunda, bir yöntem  çağrısının üzerinden veya dışındayken Otomatikler penceresinde dönüş değerlerini inceebilirsiniz. Yöntem çağrısı dönüş değerlerini görüntüleme, yerel değişkenlerde depolanmazken yararlı olabilir. Yöntem parametre olarak veya başka bir yöntemin dönüş değeri olarak kullanılabilir.

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

Otomatikler penceresinde ve yöntem `sumVars()` `subtractVars()` çağrılarının dönüş değerlerini görmek için:

1. Satırda bir kesme noktası `int x = sumVars(a, b) + subtractVars(c, d);` ayarlayın.

1. Hata ayıklamayı başlat ve kesme noktası üzerinde yürütme duraklatılırken Adımla'ya **tıklayın veya** **F10 tuşuna basın.** Otomatikler penceresinde aşağıdaki dönüş **değerlerini görüyor gerekir:**

  ![Otomatikler dönüş değeri C #](../debugger/media/autosreturnvaluecsharp2.png "Otomatikler dönüş değeri C #")

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklamaya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcısı pencereleri](../debugger/debugger-windows.md)
