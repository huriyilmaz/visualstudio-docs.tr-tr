---
title: Değişkenler üzerinde bir izleme ayarlama | Microsoft Docs
ms.custom: seodec18
ms.date: 10/11/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ea3d2a1e82e92473859fef29754fbb831cf3685b
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409355"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>İzleme ve QuickWatch değişkenlerle izleyin

Hata ayıklarken, değişkenleri ve ifadeleri izlemek için Windows 'u ve **hızlı Izlemeyi** **İzle** ' yi kullanabilirsiniz. Windows, yalnızca hata ayıklama oturumu sırasında kullanılabilir.

**İzleme** pencereleri, hata ayıklama sırasında her seferinde birkaç değişken görüntüleyebilir. **QuickWatch** iletişim kutusu her seferinde tek bir değişken görüntüler ve hata ayıklamanın devam edebilmesi için kapatılması gerekir.

Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce mutlak yeni başlayanlar ve [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md) [için hata ayıklamayı](../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

## <a name="observe-variables-with-a-watch-window"></a>İzleme penceresi değişkenleri gözlemleyin

Birden fazla **Gözcü** penceresi açabilir ve bir **izleme** penceresinde birden fazla değişken gözlemleyebilirsiniz.

Örneğin, aşağıdaki kodda `a`, `b`ve `c` değerlerinde bir izleme ayarlamak için:

```C++
int main()
{
    int a, b, c;
    a = 1;
    b = 2;
    c = 0;

    for (int i = 0; i < 10; i++)
    {
        a++;
        b *= 2;
        c = a + b;
    }

    return 0;
}

```

1. Sol kenar boşluğunda, **hata ayıkla** > **kesme noktası**' nı seçerek veya **F9**tuşuna basarak `c = a + b;` satırında bir kesme noktası ayarlayın.

1. Hata ayıklamayı **başlatmak** > yeşil **Başlangıç** okunu veya **Hata Ayıkla** ' yı seçerek hata ayıklamayı başlatın veya **F5**tuşuna basın. Yürütme kesme noktasında duraklatır.

1. **Hata ayıkla** > **Windows** > **İzle** ** > Izle**' yi seçerek veya **CTRL**+**alt**+**W** > **1**tuşlarına basarak bir **Gözcü** penceresi açın.

   Windows **2**, **3**veya **4**' ü seçerek daha fazla **izleme** penceresi açabilirsiniz.

1. **İzle** penceresinde boş bir satır seçin ve değişken `a`yazın. `b` ve `c`için aynısını yapın.

   ![Değişkenleri izle](../debugger/media/watchvariables.png "WatchVariables")

1. **Hata** ayıklama > **adımla** ' yı seçerek veya ilerlemek için gerektiğinde **F11** tuşuna basarak hata ayıklamaya devam edin. **İzleme** penceresindeki değişken değerleri, `for` döngüsünde yineleme yaparken değişir.

>[!NOTE]
>Yalnızca C++ için
>- Bir değişken veya değişken adını kullanan bir ifade bağlamını nitelemeniz gerekebilir. İşlevi, kaynak dosya veya bir değişkenin bulunduğu modül bağlamıdır. Bağlamı nitelemeniz gerekiyorsa, **izleme** penceresindeki **ad** içindeki [BağlamC++işleci ()](../debugger/context-operator-cpp.md) sözdizimini kullanın.
>
>- Kayıt adları ve değişken adlarını$kullanarak \<Kaydet **&nbsp;ad >** veya@kaydet \<**adını** **İzle** penceresindeki **ada**&nbsp;kaydedebilirsiniz. Daha fazla bilgi için bkz. [sözde değişkenler](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>İfadeleri İzleme penceresinde kullanma

Hata ayıklayıcı tarafından tanınan geçerli bir ifadeyi bir **Gözcü** penceresinde gözlemleyebilirsiniz.

Örneğin, önceki bölümdeki kod için, **izleme** penceresine `(a + b + c) / 3` girerek üç değerin ortalamasını alabilirsiniz:

![Gözcü ifadesi](../debugger/media/watchexpression.png "Gözcü ifadesi")

**İzleme** penceresindeki ifadeleri değerlendirmek için kurallar, kod dilinde ifadeleri değerlendirme kurallarıyla genellikle aynıdır. Bir ifade söz dizimi hatası varsa, Kod Düzenleyicisi olduğu gibi aynı derleyici hatası bekler. Örneğin, yukarıdaki ifadedeki bir yazım hatası, **Gözcü** penceresinde bu hatayı üretir:

![İzleme ifadesi hatası](../debugger/media/watchexpressionerror.png "İzleme ifadesi hatası")

**İzleme** penceresinde iki dalgalı çizgili bir daire simgesi görünebilir. Bu simge, hata ayıklayıcı olası iş parçacıkları arası bağımlılık nedeniyle ifadeyi değerlendirmez anlamına gelir. Diğer iş parçacıklarını geçici olarak çalıştırmayı uygulamanıza kod değerlendirme gerektirir, ancak kesme modunda olduğundan, uygulamanızı tüm iş parçacıkları genellikle durdurulur. Diğer iş parçacıklarını geçici olarak çalışmasına izin vererek olabilir beklenmeyen etkileri durumunu uygulamanızı ve hata ayıklayıcı kesme noktaları ve bu iş parçacıklarında özel durumlar gibi olayları yoksay.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>izleme penceresi arama

Her pencerenin üzerindeki arama çubuğunu kullanarak, **izleme** penceresinin Ad, değer ve tür sütunlarında anahtar sözcük arayabilirsiniz. Bir arama yürütmek için ENTER tuşuna basın veya oklardan birini seçin. Devam eden bir aramayı iptal etmek için arama çubuğundaki "x" simgesini seçin.

Bulunan eşleşmeler arasında gezinmek için sol ve sağ okları (sırasıyla SHIFT + F3 ve F3) kullanın.

![Gözcü penceresinde ara](../debugger/media/ee-search-watch.png "Gözcü penceresinde ara")

Aramanızı daha fazla veya daha az kapsamlı hale getirmek için, **izleme** penceresinin en üstündeki **arama daha derin** açılan listesini kullanarak iç içe geçmiş nesnelerde kaç düzey derinlikte arama yapmayı istediğinizi seçin. 

## <a name="pin-properties-in-the-watch-window"></a>izleme penceresi özellikleri sabitleme

>[!NOTE]
> Bu özellik .NET Core 3,0 veya üzeri sürümlerde desteklenir.

İzleme penceresi,, **Pininceleyi Özellikler** aracıyla nesneleri hızla inceleyebilirsiniz.  Bu aracı kullanmak için bir özelliğin üzerine gelin ve görüntülenen sabitleme simgesini seçin ya da sağ tıklayın ve ortaya çıkan bağlam menüsünde **üyeyi sık kullanılanlara sabitle** seçeneğini belirleyin.  Bu özelliği nesnenin özellik listesinin en üstüne, özellik adı ve değeri ise **değer** sütununda görüntülenir.  Bir özelliği kaldırmak için, PIN simgesini yeniden seçin veya bağlam menüsünde **üyeyi sık kullanılanlara ayır** seçeneğini belirleyin.

![izleme penceresi özellikleri sabitleme](../debugger/media/basic-pin-watch.gif "izleme penceresi özellikleri sabitleme")

Ayrıca, izleme penceresi nesnenin özellik listesini görüntülerken özellik adlarını açıp sabitlenmemiş özellikleri filtreleyebilirsiniz.  İzleme penceresinin üstündeki araç çubuğunda bulunan düğmeleri seçerek her iki seçeneğe da erişebilirsiniz.

::: moniker-end

### <a name="bkmk_refreshWatch"></a>İzleme değerlerini Yenile

Bir ifade değerlendirildiğinde bir yenileme simgesi (dairesel ok) **izleme** penceresinde görünebilir. Yenileme simgesi bir hata veya güncel değil bir değeri gösterir.

Değer yenilemek için yenile simgesini seçin veya Ara çubuğuna basın. Hata ayıklayıcısı ifadeyi yeniden dener. Ancak, değil istediğiniz veya ifade değeri Hesaplandı neden değildi bağlı olarak yeniden değerlendirmek kullanabilirsiniz.

Yenileme simgesinin üzerine gelin veya ifadenin değerlendirilmemesi nedeniyle **değer** sütununa bakın. Nedenler şunlardır:

- İfade, önceki örnekte olduğu gibi değerlendirilen gibi bir hata oluştu. Bir zaman aşımı oluşabilir veya bir değişken kapsam dışına olabilir.

- Uygulamasında bir yan etkisi tetikleyebilir bir işlev çağrısı ifadesi var. Bkz. [ifade yan etkileri](#bkmk_sideEffects).

- Özellikler ve örtük işlev çağrılarını otomatik olarak değerlendirilmesini devre dışı bırakıldı.

Özellikler ve örtük işlev çağrılarının otomatik değerlendirilmesi devre dışı bırakıldığı için Yenile simgesi görüntülenirse, **araç** > **seçeneklerinde** **özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir** ' i seçerek etkinleştirebilirsiniz > **genel**olarak **hata ayıklama** > .

Yenile simgesini kullanarak göstermek için:

1. **Araçlar** > **Seçenekler** > **hata ayıklama** > **genel**olarak, **özellik değerlendirmesini etkinleştir ve diğer örtük işlev çağrılarını etkinleştir** onay kutusunu temizleyin.

1. Aşağıdaki kodu girin ve **Gözcü** penceresinde `list.Count` özelliği üzerinde bir izleme ayarlayın.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Hata ayıklama başlatılamıyor. **Gözcü** penceresinde aşağıdaki iletiye benzer bir şey gösterilir:

   ![Izlemeyi Yenile](../debugger/media/refreshwatch.png "Izlemeyi Yenile")

1. Değer yenilemek için yenile simgesini seçin veya Ara çubuğuna basın. Hata ayıklayıcı ifade reevaluates.

### <a name="bkmk_sideEffects"></a>İfade yan etkileri

Bazı ifadelerin değerlendirilmesi bir değişkenin değerini değiştirebilir veya aksi halde uygulamanızı durumunu etkiler. Örneğin, aşağıdaki ifadeyi değerlendirmek `var1`değerini değiştirir:

```csharp
var1 = var2
```

Bu kod, [yan etkiye](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))neden olabilir. Yan etkileri hata ayıklama uygulamanızı çalışır değiştirerek güçleştirebilir.

Yan etkileri olan bir ifade, yalnızca ilk önce onu girdiğinizde bir kez değerlendirilir. Bundan sonra ifade, **Gözcü** penceresinde gri renkte görünür ve daha fazla değerlendirme devre dışı bırakılır. Araç ipucu veya **değer** sütunu, ifadenin bir yan etkiye neden olduğunu açıklar. Değerin yanında görüntülenen yenile simgesini seçerek yeniden değerlendirme zorlayabilirsiniz.

Yan etkileri atamasını önlemek için bir yol otomatik İşlev değerlendirmesi açmaktır. **Araçlar** > **Seçenekler** > **hata ayıklama** > **genel**olarak, **özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir**seçimini kaldırın.

C# Yalnızca, özellikler veya örtük işlev çağrılarının değerlendirmesi kapalıyken, **izleme** penceresindeki bir değişken **adına** **AC** biçim değiştiricisi ekleyerek değerlendirmeyi zorlayabilirsiniz. [Içindeki C#biçim belirticilerine ](../debugger/format-specifiers-in-csharp.md)bakın.

## <a name="bkmk_objectIds"></a>İzleme penceresi nesne kimliklerini kullanın (C# ve Visual Basic)

Bazen, belirli bir nesneyi davranışını gözlemlemek istediğiniz. Örneğin, bu değişken kapsam dışına geçti sonra bir yerel değişkeni tarafından başvurulan nesne izlemek isteyebilirsiniz. C# Ve Visual Basic, başvuru türlerinin belirli örnekleri Için nesne kimlikleri oluşturabilir ve bunları **izleme** penceresinde ve kesme noktası koşullarında kullanabilirsiniz. Nesne Kimliği hizmetlerinde hata ayıklama ortak dil çalışma zamanı tarafından (CLR) oluşturulan ve nesnesiyle ilişkili.

> [!NOTE]
> Nesne kimlikleri nesnenin çöp olarak toplanacak engellemek yoksa zayıf başvurular oluşturun. Bunlar, yalnızca geçerli hata ayıklama oturumu için geçerli olur.

Aşağıdaki kodda `MakePerson()` yöntemi yerel bir değişken kullanarak bir `Person` oluşturur:

```csharp
class Person
{
    public Person(string name)
    {
        Name = name;
    }
    public string Name { get; set; }
}

public class Program
{
    static List<Person> _people = new List<Person>();
    public static void Main(string[] args)
    {
        MakePerson();
        DoSomething();
    }

    private static void MakePerson()
    {
        var p = new Person("Bob");
        _people.Add(p);
    }

    private static void DoSomething()
    {
        // more processing
         Console.WriteLine("done");
    }
}
```

`DoSomething()` yönteminde `Person` adını öğrenmek için, **İzle** penceresindeki `Person` nesne kimliğine bir başvuru ekleyebilirsiniz.

1. `Person` nesnesi oluşturulduktan sonra kodda bir kesme noktası ayarlayın.

1. Hata ayıklama başlatılamıyor.

1. Yürütme kesme noktasında durakladığında, **Windows** > **Yereller** > **Hata Ayıkla** ' yı seçerek **Yereller** penceresini açın.

1. **Yereller** penceresinde `Person` değişkenine sağ TıKLAYıP **nesne kimliğini yap**' ı seçin.

   Bir dolar işareti ( **$** ) ve **Locals** penceresinde, nesne kimliği olan bir sayı görmeniz gerekir.

1. Nesne kimliğini sağ tıklayıp **Gözcü Ekle**' yi seçerek, nesne kimliğini **izleme** penceresine ekleyin.

1. `DoSomething()` yönteminde başka bir kesme noktası ayarlayın.

1. Hata ayıklamaya devam et. `DoSomething()` yönteminde Yürütme durakladığında, **Gözcü** penceresi `Person` nesnesini görüntüler.

   > [!NOTE]
   > Nesnenin özelliklerini görmek isterseniz, `Person.Name`gibi **araçlar** > **seçenekler** ' i > **hata ayıklama** > **genel** > **özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir**' i etkinleştirmeniz gerekir.

## <a name="dynamic-view-and-the-watch-window"></a>Dinamik Görünüm ve İzleme penceresi

Bazı betik dilleri (örneğin, JavaScript veya Python) dinamik veya [Duck](https://en.wikipedia.org/wiki/Duck_typing) yazısı kullanır ve .net sürüm 4,0 ve üzeri, normal hata ayıklama pencerelerinin gözleneceği nesneleri destekler.

**Gözcü** penceresi, bu nesneleri <xref:System.Dynamic.IDynamicMetaObjectProvider> arabirimini uygulayan türlerden oluşturulan dinamik nesneler olarak görüntüler. Dinamik Nesne düğümleri, dinamik dinamik Nesne üyelerini gösterir, ancak üye değerlerinin düzenlenmesine izin verme.

**Dinamik görünüm** değerlerini yenilemek için, dinamik nesne düğümünün yanındaki [Yenile simgesini](#bkmk_refreshWatch) seçin.

Bir nesnenin yalnızca **dinamik görünümünü** görüntülemek Için, **izleme** penceresindeki dinamik nesne adından sonra **dinamik** bir Biçim belirleyicisi ekleyin:

- İçin C#: `ObjectName, dynamic`
- Visual Basic için: `$dynamic, ObjectName`

>[!NOTE]
>- Bir C# sonraki kod satırına adımlamak için hata ayıklayıcı **dinamik görünümdeki** değerleri otomatik olarak yeniden değerlendirmez.
>- Visual Basic hata ayıklayıcı **Dinamik görünüm**aracılığıyla eklenen ifadeleri otomatik olarak yeniler.
>- **Dinamik bir görünümün** üyelerini değerlendirmek [yan etkilere](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))sahip olabilir.

**Bir nesneyi dinamik bir nesneye bağlayan yeni bir izleme değişkeni eklemek için:**

1. **Dinamik görünümün**herhangi bir alt öğesine sağ tıklayın.
1. **Gözcü Ekle**' yi seçin. `object.name` `((dynamic) object).name` olur ve yeni bir **Gözcü** penceresinde görünür.

Hata ayıklayıcı Ayrıca, nesnenin **Dinamik görünüm** alt düğümünü **ekler penceresine ekler** . Hata ayıklama sırasında **oto** penceresini açmak Için **hata ayıkla** > **Windows** > **oto**' ı seçin.

**Dinamik görünüm** , com nesneleri için hata ayıklamayı da geliştirir. Hata ayıklayıcı, **System. __ComObject**SARMALANAN bir com nesnesine geldiğinde, nesne için dinamik bir **Görünüm** düğümü ekler.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>Tek bir değişken veya QuickWatch ifadesiyle gözlemleyin

**QuickWatch** kullanarak tek bir değişkeni gözlemleyebilirsiniz.

Örneğin, aşağıdaki kodu:

```csharp
static void Main(string[] args)
{
    int a, b;
    a = 1;
    b = 2;
    for (int i = 0; i < 10; i++)
    {
        a = a + b;
    }
}
```

`a` değişkenini gözlemlemek için,

1. `a = a + b;` satırında bir kesme noktası ayarlayın.

1. Hata ayıklama başlatılamıyor. Yürütme kesme noktasında duraklatır.

1. Koddaki değişkeni `a` seçin.

1. **Quickwatch** > **Hata Ayıkla** ' yı seçin, **SHIFT**+**F9**tuşuna basın veya sağ tıklayıp **hızlı izleme**' yi seçin.

   **QuickWatch** iletişim kutusu görüntülenir. `a` değişkeni, **değeri** **1**olan **ifade** kutusudur.

   ![QuickWatch değişkeni](../debugger/media/quickwatchvariable.png "QuickWatch değişkeni")

1. Değişkeni kullanarak bir ifadeyi değerlendirmek için, **ifade** kutusuna `a + b` gibi bir ifade yazın ve yeniden değerlendir ' **i seçin.**

   ![QuickWatch ifadesi](../debugger/media/quickwatchexpression.png "QuickWatch ifadesi")

1. **Hızlı** bir şekilde **izleme penceresine değişken** veya Ifade eklemek için, **Gözcü Ekle**' yi seçin.

1. **QuickWatch** penceresini kapatmak için **Kapat** ' ı seçin. (**QuickWatch** kalıcı bir iletişim kutusu olduğundan, açık olduğu sürece hata ayıklamaya devam edemeyeceğinizi.)

1. Hata ayıklamaya devam et. Değişkeni, **Gözcü** penceresinde gözlemleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama bölümüne ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcısı pencereleri](../debugger/debugger-windows.md)
