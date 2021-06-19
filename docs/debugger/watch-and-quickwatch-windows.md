---
title: Değişken kümesi üzerinde saat | Microsoft Docs
description: Hata ayıklarken Watch ve QuickWatch'da değişkenlere ve ifadelere bakın. Watch, QuickWatch'ta yalnızca bir değişken ve yalnızca kesme sırasında birkaç değişken gösterebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/11/2018
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 192a11a028c297dc2c642e65982a978f7b5596a7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385025"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>İzleme pencereleri ve QuickWatch ile değişkenleri izleme

Hata ayıklama sırasında Değişkenleri ve ifadeleri **izlemek** için Pencereleri ve **QuickWatch'u** izleyebilirsiniz. Pencereler yalnızca hata ayıklama oturumu sırasında kullanılabilir.

**İzleme** pencereleri hata ayıklama sırasında aynı anda birkaç değişken görüntüleyebilirsiniz. **QuickWatch iletişim** kutusunda aynı anda tek bir değişken görüntülenir ve hata ayıklamanın devam etmek için kapatılacak olması gerekir.

> [!NOTE]
> Bu kodda ilk kez hata ayıklamayı denediyseniz, bu [](../debugger/debugging-absolute-beginners.md) makaleyi okumadan önce [](../debugger/write-better-code-with-visual-studio.md) yeni başlayanlar için Hata Ayıklama ve Hata ayıklama teknikleri ve araçları makalesine bakabilirsiniz.

## <a name="observe-variables-with-a-watch-window"></a>Değişkenleri bir izleme penceresi

Birden fazla İzleme penceresi açabilir **ve** bir İzleme penceresinde birden fazla değişken **gözlemlersiniz.**

Örneğin, aşağıdaki kodda `a` , ve `b` değerlerine bir `c` saat ayarlamak için:

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

1. Sol kenar boşluğuna tıklayarak, Hata Ayıklama Kesme Noktası Geçişini Değiştir'i seçerek veya `c = a + b;`   >  F9 tuşuna basarak satırda bir **kesme noktası ayarlayın.**

1. Yeşil Başlat okunu seçerek veya Hata **AyıklamaYı** Başlat **Hata** Ayıklamayı Başlat seçeneğini kullanarak hata  >  ayıklamaya **başlayabilir** veya **F5 tuşuna basın.** Yürütme kesme noktası sırasında duraklatılır.

1. Windows Watch **Watch** 1'de Hata   >  Ayıkla'ya **veya**  >    >  **Ctrl** Alt W 1 **tuşlarına** +  +   >  basarak bir İzleme penceresi açın.

   Windows **2, 3** veya 4'ü **seçerek ek** İzleme pencereleri **açsanız da.** 

1. İzle **penceresinde** boş bir satır seçin ve değişkeni `a` yazın. ve için de aynı şeyi `b` `c` yapar.

   ![Değişkenleri izleme](../debugger/media/watchvariables.png "WatchVariables")

1. Hata Ayıklama Adımını Seçerek **veya ilerlemek için** gereken  >   **F11** tuşuna basarak hata ayıklamaya devam edin. Döngüde **tekrarlarken** İzleme penceresindeki değişken değerleri `for` değişir.

>[!NOTE]
>Yalnızca C++ için,
>- Değişken adının bağlamını veya değişken adı kullanan bir ifadeyi tanımlamanız gerekir. Bağlam, değişkenin bulunduğu işlev, kaynak dosya veya modüldür. Bağlamı uygun şekilde nitelendirin, İzleme [penceresindeki Ad'da](../debugger/context-operator-cpp.md) bağlam işleci (C++) **söz** **dizimi kullanın.**
>
>- İzleme penceresindeki Ad'a veya kullanarak **$\<register&nbsp;name>** yazman **@\<register&nbsp;name>** adları ve **değişken** adları  ekebilirsiniz. Daha fazla bilgi için [bkz. Pseudovariables](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>Bir izleme penceresi'de ifadeleri kullanma

İzleme penceresinde hata ayıklayıcı tarafından tanınan geçerli ifadeleri **gözlemlersiniz.**

Örneğin, önceki bölümdeki kod için İzleme penceresine girerek üç değerin `(a + b + c) / 3` ortalamasını **elde** edersiniz:

![İzleme ifadesi](../debugger/media/watchexpression.png "İzleme ifadesi")

İzleme penceresindeki ifadeleri değerlendirme  kuralları genellikle kod dilindeki ifadeleri değerlendirme kurallarıyla aynıdır. Bir ifadede söz dizimi hatası varsa, kod düzenleyicisinde olduğu gibi aynı derleyici hatasını beklersiniz. Örneğin, önceki ifadede yer alan bir yazım hatası İzleme penceresinde şu **hatayı** üretir:

![İfadeyi izleme hatası](../debugger/media/watchexpressionerror.png "İzleme ifadesi hatası")

İzleme penceresinde iki dalgalı çizgi simgesi olan bir **daire** görünebilir. Bu simge, hata ayıklayıcısının olası bir iş parçacığı arası bağımlılık nedeniyle ifadeyi değerlendirmey olduğu anlamına gelir. Kodun değerlendirilmesi için uygulamandaki diğer iş parçacıklarının geçici olarak çalışması gerekir, ancak kesme modunda olduğunuz için uygulamanıza gelen tüm iş parçacıkları genellikle durdurulur. Diğer iş parçacıklarının geçici olarak çalışmasına izin vermenin, uygulamanın durumu üzerinde beklenmedik etkileri olabilir ve hata ayıklayıcı bu iş parçacıklarında kesme noktaları ve özel durumlar gibi olayları yoksayabilirsiniz.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>Arama izleme penceresi

Her pencerenin üzerindeki arama çubuğunu kullanarak İzleme penceresinin  Ad, Değer ve Tür sütunlarında anahtar sözcükleri arayabilirsiniz. ENTER tarak arama yürütmek için oklardan birini seçin. Devam eden bir arama işlemini iptal etmek için arama çubuğundaki "x" simgesini seçin.

Bulunan eşleşmeler arasında gezinmek için sol ve sağ okları (sırasıyla Shift+F3 ve F3) kullanın.

![İzleme Penceresinde Arama](../debugger/media/ee-search-watch.png "İzleme Penceresinde Arama")

Aramanızı daha fazla veya daha  az ayrıntılı hale eklemek için  İzleme penceresinin üst kısmında yer alan Daha Ayrıntılı Ara açılan penceresini kullanarak iç içe nesnelerde kaç düzey derinliğinde arama yapmak istediğinize karar verirsiniz. 

## <a name="pin-properties-in-the-watch-window"></a>Özellikleri izleme penceresi

>[!NOTE]
> Bu özellik .NET Core 3.0 veya üzerinde de destek sağlar.

Sabitlenebilir Özellikler aracını kullanarak nesneleri izleme penceresi **hızla inceebilirsiniz.**  Bu aracı kullanmak için bir özelliğin üzerine gelin ve görüntülenen sabitleme  simgesini seçin veya sağ tıklayın ve sonuçta elde edilen bağlam menüsünde Üyeyi Sık Kullanılan Olarak Sabitle seçeneğini belirleyin.  Bu, bu özelliği nesnenin özellik listesinin en üstüne kadar gösterir ve Özellik adı ve değeri **Değer** sütununda görüntülenir.  Bir özelliğin sabitlemesini geri eklemek için  sabitleme simgesini yeniden seçin veya bağlam menüsünde Üyeyi Sık Kullanılan olarak Kaldır seçeneğini belirleyin.

![Özellikleri izleme penceresi](../debugger/media/basic-pin-watch.gif "Özellikleri izleme penceresi")

Ayrıca, özellik adlarını açıp sabitlenmiş olmayan özellikleri filtrenin dışında kullanarak nesnenin özellik listesini izleme penceresi.  İzleme penceresinin üzerindeki araç çubuğundaki düğmeleri seçerek her iki seçenen bilgilere de erişebilirsiniz.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a> İzleme değerlerini yenileme

Bir ifade değerlendirlendiğinde İzleme penceresinde bir yenileme **simgesi** (dairesel ok) görünebilir. Yenileme simgesi, bir hatayı veya güncel olan bir değeri gösterir.

Değeri yenilemek için yenile simgesini seçin veya ara çubuğuna basın. Hata ayıklayıcısı ifadeyi yeniden değerlendirmeye çalışır. Ancak, değerin neden değerlendirilmesine bağlı olarak ifadeyi yeniden değerlendirmek istemeyip yeniden değerlendiresiniz.

Yenileme simgesinin üzerine gelin **veya ifadenin** değerlendirilme nedeninin Value sütununa bakın. Nedenler şunlardır:

- Önceki örnekte olduğu gibi ifade değerlendirilirken bir hata oluştu. Zaman aşımı oluşabilir veya bir değişken kapsam dışında olabilir.

- İfade, uygulamada yan etkiyi tetikleyen bir işlev çağrısına sahiptir. Bkz. [İfade yan etkileri.](#bkmk_sideEffects)

- Özelliklerin ve örtülü işlev çağrılarının otomatik olarak değerlendirilmesi devre dışı bırakılır.

Özelliklerin otomatik değerlendirilmesi ve örtülü işlev çağrıları devre dışı bırakıldıkları için yenileme  simgesi görünürse, Araçlar Seçenekler Hata Ayıklama Genel'de Özellik değerlendirmesini ve diğer örtülü işlev çağrılarını etkinleştir'i seçerek  >    >    >  **etkinleştirebilirsiniz.**

Yenileme simgesini kullanmayı göstermek için:

1. Araçlar **Seçenekler**  >  **Hata**  >  **Ayıklama**  >  **Genel'de** Özellik **değerlendirmesini ve diğer örtülü işlev çağrılarını etkinleştir onay kutusunun** işaretini kaldırın.

1. Aşağıdaki kodu girin ve İzleme **penceresine** özelliğinde bir saat `list.Count` ayarlayın.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Hata ayıklamayı başlatın. İzle **penceresinde** aşağıdaki iletiye benzer bir şey gösterilir:

   ![İzlemeyi Yenile](../debugger/media/refreshwatch.png "İzlemeyi Yenile")

1. Değeri yenilemek için yenile simgesini seçin veya ara çubuğuna basın. Hata ayıklayıcısı ifadeyi yeniden değerlendirir.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a> İfade yan etkileri

Bazı ifadelerin değerlendirilmesi bir değişkenin değerini değiştirebilir veya başka bir şekilde uygulama durumunu etkileyebilir. Örneğin, aşağıdaki ifadenin değerlendirilmesi değerini `var1` değiştirir:

```csharp
var1 = var2
```

Bu kod yan etkiye [neden olabilir.](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\)) Yan etkiler, uygulamanın nasıl çalışır durumda olduğunu değiştirerek hata ayıklamayı zorlaştırabilirsiniz.

Yan etkileri olan bir ifade, ilk kez girerek yalnızca bir kez değerlendirilir. Bundan sonra, ifade İzleme penceresinde gri **görünür** ve diğer değerlendirmeler devre dışı bırakılır. Araç ipucu veya **Değer sütunu,** ifadenin yan etkiye neden olduğunu açıklar. Değerin yanında görünen yenileme simgesini seçerek yeniden değerlendirmeyi zorlarsanız.

Yan etkiler atamasını önlemenin bir yolu, otomatik işlev değerlendirmesini kapatmaktır. Araçlar **Seçenekler**  >  **Hata**  >  **Ayıklama Genel'de** Özellik  >   **değerlendirmesini etkinleştir'in ve diğer örtülü işlev çağrılarının seçimini kaldırın.**

Yalnızca C# için, özelliklerin veya örtülü işlev çağrılarının değerlendirilmesi kapalı olduğunda, İzleme **penceresindeki** bir değişken **Name** değişkenine ac biçim değiştiricisini ekleyerek **değerlendirmeyi** zorlarsınız. Bkz. [C# içinde biçim belirleyicileri.](../debugger/format-specifiers-in-csharp.md)

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a> Nesne kimliklerini izleme penceresi (C# ve Visual Basic) kullanma

Bazen belirli bir nesnenin davranışını gözlemlemek istersiniz. Örneğin, bu değişken kapsam dışında kaldıktan sonra yerel değişken tarafından başvurulan bir nesneyi izlemek istiyor olabilir. C# ve Visual Basic, başvuru türlerinin belirli örnekleri için Nesne Kimlikleri oluşturabilir ve bunları  İzleme penceresinde ve kesme noktası koşullarında kullanabilirsiniz. Nesne Kimliği, ortak dil çalışma zamanı (CLR) hata ayıklama hizmetleri tarafından oluşturulur ve nesnesiyle ilişkilendirildi.

> [!NOTE]
> Nesne kimlikleri, nesnenin atık toplamasını önlemeyen zayıf başvurular oluşturur. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.

Aşağıdaki kodda yöntemi `MakePerson()` yerel değişken kullanarak bir `Person` oluşturur:

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

yönteminin adını bulmak `Person` `DoSomething()` için, İzleme penceresinde Nesne Kimliği'ne `Person` bir başvuru eklemek için **kullanabilirsiniz.**

1. Nesne oluşturulduktan sonra kodda bir `Person` kesme noktası ayarlayın.

1. Hata ayıklamayı başlatın.

1. Kesme noktası üzerinde yürütme duraklatılırsa, Windows **YerelLerinde Hata Ayıkla'yi** **seçerek**  >  **Yereller penceresini**  >  **açın.**

1. Yereller **penceresinde** değişkenine sağ tıklayın ve `Person` Nesne Kimliği **Yapma'yı seçin.**

   YerelLer penceresinde bir dolar işareti ( ) ve sayı **$** (Nesne Kimliği)  görüyor olun.

1. Nesne Kimliği'ne sağ **tıklar** ve İzleme Ekle'yi seçerek nesne kimliğini İzleme **penceresine ekleyin.**

1. yönteminde başka bir kesme noktası `DoSomething()` ayarlayın.

1. Hata ayıklamaya devam. yürütme yönteminde `DoSomething()` duraklatılırsa, **İzleme** penceresi nesneyi `Person` görüntüler.

   > [!NOTE]
   > nesnesinin gibi özelliklerini görmek için Araçlar Seçenekler Hata Ayıklama Genel Etkinleştirme özelliği değerlendirmesini ve diğer örtülü işlev çağrılarını seçerek özellik `Person.Name`   >    >    >    >  **değerlendirmesini etkinleştirmeniz gerekir.**

## <a name="dynamic-view-and-the-watch-window"></a>Dinamik Görünüm ve izleme penceresi

Bazı betik dillerinde (örneğin, JavaScript veya [](https://en.wikipedia.org/wiki/Duck_typing) Python) dinamik veya ördeğil yazma kullanılır ve .NET sürüm 4.0 ve sonrası normal hata ayıklama pencerelerinde gözlemlen zor nesneleri destekler.

İzleme **penceresinde** bu nesneler, arabirimi uygulayan türlerden oluşturulan dinamik nesneler olarak <xref:System.Dynamic.IDynamicMetaObjectProvider> görüntülenir. Dinamik nesne düğümleri dinamik nesnelerin dinamik üyelerini gösterir, ancak üye değerlerinin düzenlenmesine izin vermez.

Dinamik Görünüm **değerlerini yenilemek** için dinamik [nesne düğümünün](#bkmk_refreshWatch) yanındaki yenileme simgesini seçin.

Bir nesnenin yalnızca **Dinamik Görünümünü** görüntülemek için, İzleme **penceresinde** dinamik nesne adının ardından bir dinamik biçim **belirleyicisi** ekleyin:

- C# için: `ObjectName, dynamic`
- For Visual Basic: `$dynamic, ObjectName`

>[!NOTE]
>- C# hata ayıklayıcısı, bir sonraki kod satırına adım atarak **Dinamik** Görünüm'de değerleri otomatik olarak yeniden değerlendirmez.
>- Hata Visual Basic ayıklayıcısı Dinamik Görünüm aracılığıyla eklenen ifadeleri otomatik **olarak yeniler.**
>- Dinamik Görünümün üyelerini **değerlendirmenin** yan [etkileri olabilir.](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))

**Bir nesneyi dinamik nesneye alan yeni bir izleme değişkeni eklemek için:**

1. Dinamik Görünüm'de herhangi bir alt **aya sağ tıklayın.**
1. İzleme **Ekle'yi seçin.** , `object.name` yeni bir İzleme penceresinde görünür ve `((dynamic) object).name` olur. 

Hata ayıklayıcısı ayrıca nesnenin **Dinamik Görünüm** alt düğümünü Otomatikler **penceresine** ekler. Otomatikler penceresini **açmak için** hata ayıklama sırasında Windows Autos'da **Hata Ayıkla'ya**  >    >  **tıklayın.**

**Dinamik Görünüm,** COM nesneleri için hata ayıklamayı da iyiler. Hata ayıklayıcı, içinde sarmalanmış bir COM **nesnesine System.__ComObject,** nesne için **bir Dinamik Görünüm** düğümü ekler.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>QuickWatch ile tek bir değişken veya ifade gözlemle

Tek bir değişkeni gözlemlemek için **QuickWatch** kullanabilirsiniz.

Örneğin, aşağıdaki kod için:

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

Değişkeni `a` gözlemlemek için,

1. Satırda bir kesme noktası `a = a + b;` ayarlayın.

1. Hata ayıklamayı başlatın. Yürütme kesme noktası sırasında duraklatılır.

1. Kodda `a` değişkeni seçin.

1.   >  **QuickWatch'da Hata Ayıkla'yı** seçin, **Shift** F9 tuşuna + basın veya sağ tıklar ve **QuickWatch'u seçin.**

   **QuickWatch iletişim** kutusu görüntülenir. değişkeni, `a` 1 **değerine** sahip **İfade** **kutusundadır.**

   ![QuickWatch değişkeni](../debugger/media/quickwatchvariable.png "QuickWatch değişkeni")

1. Değişken kullanarak bir ifadeyi değerlendirmek için İfade kutusuna gibi bir ifade yazın ve Yeniden `a + b` **Değerlendir'i seçin.** 

   ![QuickWatch ifadesi](../debugger/media/quickwatchexpression.png "QuickWatch ifadesi")

1. QuickWatch'dan İzleme **penceresine değişken veya** ifade **eklemek için İzleme** Ekle'yi **seçin.**

1. QuickWatch **penceresini** kapatmak için **Kapat'ı** seçin. (**QuickWatch** kalıcı bir iletişim kutusu olduğu için açık olduğu sürece hata ayıklamaya devam etmek mümkün değil.)

1. Hata ayıklamaya devam. Değişkene İzleme penceresinden **bakabilirsiniz.**

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklamaya ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcısı pencereleri](../debugger/debugger-windows.md)
