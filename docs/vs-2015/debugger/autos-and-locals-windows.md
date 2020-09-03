---
title: Oto ve Yereller Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.autos
- vs.debug.locals
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugger, variable windows
- debugging [Visual Studio], variable windows
ms.assetid: bb6291e1-596d-4af0-9f22-5fd713d6b84b
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 261c0c0bd8b48634c8d24d56ee4df7ea3bbcf135
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161716"
---
# <a name="autos-and-locals-windows"></a>Otomatikler ve Yereller Pencereleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklama sırasında değişken değerlerini görmek istediğinizde, **oto** penceresinde (hata ayıklama, **Ctrl + Alt + v, A**veya **hata ayıklama/Windows/oto**) ve **Locals** penceresinde (hata ayıklama, **Ctrl + Alt + v, L**veya **hata ayıklama/Windows/Yereller**) çok yararlı olur. **Yereller** penceresi, genellikle yürütülen işlev veya yöntem olan yerel kapsamda tanımlanan değişkenleri görüntüler. **Oto** penceresi, geçerli satır (hata ayıklayıcının durdurulduğu yer) etrafında kullanılan değişkenleri görüntüler. Tam olarak hangi değişkenlerin farklı dillerde farklı olduğu gösteriliyor. & oto penceresinde hangi değişkenlerin göründüğünü görün? below.  
  
 Temel hata ayıklama hakkında daha fazla bilgiye ihtiyacınız varsa, bkz. [hata ayıklayıcısını](../debugger/getting-started-with-the-debugger.md)kullanmaya başlama.  
  
## <a name="looking-at-objects-in-the-autos-and-locals-windows"></a>Oto ve Yereller pencerelerinde nesnelere bakma  
 Diziler ve nesneler, ağaç denetimleri olarak oto ve Yereller pencerelerinde görüntülenir. Alanı ve özellikleri göstermek üzere görünümü genişletmek için, değişken adının solundaki oka tıklayın. <xref:System.IO.FileStream> **Locals** penceresinde bir nesne örneği aşağıda verilmiştir:  
  
 ![Yereller&#45;FILESTREAM](../debugger/media/locals-filestream.png "Yereller-FILESTREAM")  
  
## <a name="what-variables-appear-in-the-autos-window"></a>Oto penceresinde hangi değişkenler görünür?  
 C#, Visual Basic ve C++ kodundaki **oto & k** penceresini kullanabilirsiniz. **Oto 'lar** penceresi JavaScript veya F # desteklemez.  
  
 C# ve Visual Basic içinde, **oto** penceresinde geçerli veya önceki satırda kullanılan herhangi bir değişken görüntülenir. Örneğin, dört değişken bildirirseniz ve bunları şu şekilde ayarlarsanız:  
  
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
  
 Satırda bir kesme noktası ayarlar `c = 3` ve hata ayıklayıcıyı çalıştırırsanız, yürütme durdurulduğunda bu pencere aşağıdaki gibi görünür: **Autos**  
  
 ![Oto&#45;, CSharp](../debugger/media/autos-csharp.png "Oto 'lar-CSharp")  
  
 `c`Satırı henüz yürütülmediği için değerinin 0 olduğunu unutmayın `c = 3` .  
  
 C++ ' da, **oto** penceresinde geçerli satırdan en az üç satır önce kullanılan değişkenler görüntülenir (yürütmenin durdurulduğu satır). Altı değişken bildirirseniz:  
  
```cpp  
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
  
 Satırda bir kesme noktası ayarlar `e = 5;` ve hata ayıklayıcıyı çalıştırırsanız, yürütme durdurulduğunda, bu pencerede şöyle görünür **Autos** :  
  
 ![& Oto&#45;cplus](../debugger/media/autos-cplus.png "Oto-cplus")  
  
 Satırdaki kod henüz yürütülmediği için e değişkeninin başlatılmamış olduğunu unutmayın `e = 5;` .  
  
 Ayrıca, işlevlerin ve yöntemlerin dönüş değerlerini belirli koşullarda görebilirsiniz. Bkz. aşağıdaki [Yöntem çağrılarının dönüş değerlerini görüntüleme](#bkmk_returnValue) .  
  
## <a name="view-return-values-of-method-calls"></a><a name="bkmk_returnValue"></a> Yöntem çağrılarının dönüş değerlerini görüntüle  
 .NET ve C++ kodunda, bir yöntem çağrısının üzerinde veya dışına adımla dönüş değerlerini inceleyebilirsiniz. Bu işlev, yöntem çağrısının sonucu yerel bir değişkende depolanmıyorsa, örneğin bir yöntem parametre olarak veya başka bir yöntemin dönüş değeri olarak kullanıldığında faydalıdır.  
  
 Aşağıdaki C# kodu iki işlevin dönüş değerlerini ekler:  
  
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
  
 İnt satırında bir kesme noktası ayarlayın `x = sumVars(a, b) + subtractVars(c, d);` .  
  
 Hata ayıklamayı başlatın ve yürütme ilk kesme noktasında kesildüğünde **F10 (Adımlama)** tuşuna basın. Aşağıdaki **öğeleri, oto** penceresinde görmeniz gerekir:  
  
 ![AutosReturnValueCSharp2](../debugger/media/autosreturnvaluecsharp2.png "AutosReturnValueCSharp2")  
  
## <a name="why-are-variable-values-sometimes-red-in-locals-and-autos-windows"></a>Değişken değerleri neden bazen Yereller ve oto pencerelerinde kırmızıdır?  
 Değişken değerinin bazen **Yereller** ve **oto** pencerelerinde kırmızı olduğunu fark edebilirsiniz. Bunlar, son değerlendirmeden bu yana değiştirilen değişken değerlerdir. Değişiklik, önceki bir hata ayıklama oturumundan veya değer pencerede değiştirildiğinden olabilir.  
  
## <a name="changing-the-numeric-format-of-a-variable-window"></a>Bir değişken penceresinin sayısal biçimini değiştirme  
 Varsayılan sayısal biçim Decimal 'dir, ancak onaltılık olarak değiştirebilirsiniz. **Yereller** veya **oto** penceresinin Içine sağ tıklayın ve **Onaltılı görüntü**' i seçin. Değişiklik, tüm hata ayıklayıcı pencerelerini etkiler.  
  
## <a name="editing-a-value-in-a-variable-window"></a>Değişken penceresinde bir değeri Düzenle  
 **Oto**, **Yereller**, **izleme**ve **QuickWatch** pencerelerinde görünen çoğu değişkenin değerlerini düzenleyebilirsiniz. **İzleme** ve **hızlı izleme** pencereleri hakkında bilgi için bkz. [izleme ve hızlı izleme pencereleri](../debugger/watch-and-quickwatch-windows.md). Değiştirmek istediğiniz değere çift tıklayın ve yeni değeri ekleyin.  
  
 Örneğin, bir değer için bir ifade girebilirsiniz `a + b` . Hata ayıklayıcı çoğu geçerli dil ifadesini kabul eder.  
  
 Yerel C++ kodunda, bir değişken adının bağlamını nitelemeniz gerekebilir. Daha fazla bilgi için bkz. [Bağlam işleci (C++)](../debugger/context-operator-cpp.md).  
  
 Ancak, değerleri değiştirirken dikkatli olmanız gerekir. Olası bazı sorunlar şunlardır:  
  
- Bazı ifadelerin değerlendirilmesi, bir değişkenin değerini değiştirebilir veya programınızın durumunu etkileyebilir. Örneğin, `var1 = ++var2` ve değerlerini değerlendirmek, ve değerlerini `var1` değiştirir `var2` .  
  
     Verileri değiştiren ifadeler [yan etkileri](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))olduğu söylenir, bu da bunları farkında değilseniz beklenmedik sonuçlara neden olabilir. Bu tür bir değişikliği yapmadan önce sonuçlarını anladığınızdan emin olun.  
  
- Kayan nokta değerlerini düzenlemek, kesirli bileşenlerin ondalıktan ikiliye dönüştürülmesi nedeniyle küçük yanlışlıklara neden olabilir. Zararsız görünen bir düzenleme bile, kayan nokta değişkenindeki en az önemli bitlerin bazılarının değişmesine neden olabilir.  
  
## <a name="debug-location-toolbar"></a>Hata Ayıklama Konumu araç çubuğu  
 İstenen işlevi, iş parçacığını veya işlemi seçmek için **hata ayıklama konumu** araç çubuğunu kullanabilirsiniz. Bir kesme noktası ayarlayın ve hata ayıklamayı başlatın. (Bu araç çubuğunu görmüyorsanız, araç çubuğu alanının boş bir kısmına tıklayarak etkinleştirebilirsiniz. Araç çubuklarının bir listesini görmeniz gerekir. **hata ayıklama konumu**seçin). Kesme noktası isabet edildiğinde, yürütme duraklar ve aşağıdaki grafiğin alt satırı olan hata ayıklama konumu araç çubuğunu görebilirsiniz:  
  
 ![DebugLocationToolbar](../debugger/media/debuglocationtoolbar.png "DebugLocationToolbar")  
  
 Ayrıca, **çağrı yığını** penceresinde, **iş parçacıkları** penceresinde veya **süreçler** penceresinde öğesine çift tıklayarak bağlamı farklı işlev çağrıları, iş parçacıkları veya süreçler olarak değiştirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Pencereleri](../debugger/debugger-windows.md)
