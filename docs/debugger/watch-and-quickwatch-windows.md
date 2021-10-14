---
title: Değişkenlere bir izleme ayarla | Microsoft Docs
description: Hata ayıklarken, bkz. Izleme ve hızlı Izleme içindeki değişkenler ve ifadeler. İzleme birkaç değişken görüntüleyebilir, hızlı bir şekilde yalnızca bir tane ve yalnızca kesme durumunda olabilir.
ms.custom: SEO-VS-2020
ms.date: 09/10/2021
ms.topic: how-to
f1_keywords:
- vs.debug.quickwatch
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7f0de0163b157afb6216ff407cc33d949735aada
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972447"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Pencereleri Izle ve hızlı Gözcü ile değişkenleri izleyin

Hata ayıklarken, değişkenleri ve ifadeleri izlemek için Windows 'u ve **hızlı Izlemeyi** **İzle** ' yi kullanabilirsiniz. Pencereler yalnızca hata ayıklama oturumu sırasında kullanılabilir.

**İzleme** pencereleri, hata ayıklama sırasında her seferinde birkaç değişken görüntüleyebilir. **QuickWatch** iletişim kutusu her seferinde tek bir değişken görüntüler ve hata ayıklamanın devam edebilmesi için kapatılması gerekir. QuickWatch kullanma hakkında daha fazla bilgi için bkz. [QuickWatch ile tek bir değişkeni veya Ifadeyi gözlemleyin](#observe-a-single-variable-or-expression-with-quickwatch).

> [!NOTE]
> Kodu ilk kez ayıklamaya çalıştığınızda, bu makaleye geçmeden önce mutlak yeni başlayanlar ve [hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md) [için hata ayıklamayı](../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

## <a name="observe-variables-with-a-watch-window"></a>izleme penceresi değişkenleri gözlemleyin

Birden fazla **Gözcü** penceresi açabilir ve bir **izleme** penceresinde birden fazla değişken gözlemleyebilirsiniz.

Örneğin,,, ve değerlerinde bir izleme ayarlamak için `a` `b` `c` aşağıdaki kodda:

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

1. `c = a + b;`Sol kenar boşluğuna tıklayarak, **Hata Ayıkla**  >  **geçiş noktasını** seçerek veya **F9** tuşuna basarak satırda bir kesme noktası ayarlayın.

1. Yeşil **Başlangıç** okunu seçerek hata ayıklamayı **başlatın veya hata**  >  **ayıklamayı başlatın** veya **F5**'e basın. Yürütme kesme noktasında duraklatılır.

1.  **hata ayıkla**  >  **Windows**  >  **izleme**  >  **1**' i seçerek veya **Ctrl** + **Alt** + **W**  >  **1** tuşlarına basarak bir izleme penceresi açın.

   Windows **2**, **3** veya **4**' ü seçerek daha fazla **izleme** penceresi açabilirsiniz.

1. **İzle** penceresinde boş bir satır seçin ve değişken yazın `a` . Ve için aynısını yapın `b` `c` .

   ![Değişkenleri izleme](../debugger/media/watchvariables.png "WatchVariables")

1. **Hata** ayıklama  >  **adımını** seçerek veya ilerlemek için gerektiğinde **F11** tuşuna basarak hata ayıklamaya devam edin. **İzleme** penceresindeki değişken değerleri, döngüde yineleme yaparken değişir `for` .

>[!NOTE]
>Yalnızca C++ için,
>- Bir değişken adı ya da değişken adı kullanan bir ifadenin bağlamını nitelemeniz gerekebilir. Bağlam, bir değişkenin bulunduğu işlev, kaynak dosya veya modüldür. Bağlamı nitelemeniz gerekiyorsa, **izleme** penceresindeki **ad** Içindeki [Bağlam işleci (C++)](../debugger/context-operator-cpp.md) söz dizimini kullanın.
>
>- Kayıt adlarını ve değişken adlarını, **$\<register&nbsp;name>** **@\<register&nbsp;name>** **izleme** penceresindeki **adı** kullanarak ekleyebilirsiniz. Daha fazla bilgi için bkz. [sözde değişkenler](../debugger/pseudovariables.md).

## <a name="use-expressions-in-a-watch-window"></a>izleme penceresi ifadeleri kullanma

Hata ayıklayıcı tarafından tanınan geçerli bir ifadeyi bir **Gözcü** penceresinde gözlemleyebilirsiniz.

Örneğin, önceki bölümdeki kod için, Izleme penceresine girerek üç değerin ortalamasını alabilirsiniz `(a + b + c) / 3` : 

![Gözcü ifadesi](../debugger/media/watchexpression.png "İzleme ifadesi")

**İzleme** penceresindeki ifadeleri değerlendirmek için kurallar, kod dilinde ifadeleri değerlendirme kurallarıyla genellikle aynıdır. Bir ifadede sözdizimi hatası varsa, kod Düzenleyicisi 'nde olduğu gibi aynı derleyici hatasını da bekler. Örneğin, yukarıdaki ifadedeki bir yazım hatası, **Gözcü** penceresinde bu hatayı üretir:

![İzleme ifadesi hatası](../debugger/media/watchexpressionerror.png "İfadeyi izleme hatası")

**İzleme** penceresinde iki dalgalı çizgili bir daire simgesi görünebilir. Bu simge, olası bir çapraz iş parçacığı bağımlılığı nedeniyle hata ayıklayıcının ifadeyi değerlendirmediği anlamına gelir. Kodu değerlendirmek, uygulamanızdaki diğer iş parçacıklarının geçici olarak çalışmasını gerektirir, ancak kesme modundayken, uygulamanızdaki tüm iş parçacıkları genellikle durdurulur. Diğer iş parçacıklarının geçici olarak çalışmasına izin verilmesi uygulamanızın durumunda beklenmeyen etkilere sahip olabilir ve hata ayıklayıcı, bu iş parçacıklarında kesme noktaları ve özel durumlar gibi olayları yok sayabilir.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>izleme penceresi arama

Her pencerenin üzerindeki arama çubuğunu kullanarak, **izleme** penceresinin Ad, değer ve tür sütunlarında anahtar sözcük arayabilirsiniz. Bir arama yürütmek için ENTER tuşuna basın veya oklardan birini seçin. Devam eden bir aramayı iptal etmek için arama çubuğundaki "x" simgesini seçin.

Bulunan eşleşmeler arasında gezinmek için sol ve sağ okları (sırasıyla SHIFT + F3 ve F3) kullanın.

![Gözcü penceresinde ara](../debugger/media/ee-search-watch.png "İzleme Penceresinde Ara")

Aramanızı daha fazla veya daha az kapsamlı hale getirmek için, **izleme** penceresinin en üstündeki **arama daha derin** açılan listesini kullanarak iç içe geçmiş nesnelerde kaç düzey derinlikte arama yapmayı istediğinizi seçin. 

## <a name="pin-properties-in-the-watch-window"></a>izleme penceresi özellikleri sabitleme

>[!NOTE]
> Bu özellik .NET Core 3,0 veya üzeri sürümlerde desteklenir.

İzleme penceresi,, **Pininceleyi Özellikler** aracıyla nesneleri hızla inceleyebilirsiniz.  Bu aracı kullanmak için bir özelliğin üzerine gelin ve görüntülenen sabitleme simgesini seçin ya da sağ tıklayın ve ortaya çıkan bağlam menüsünde **üyeyi sık kullanılanlara sabitle** seçeneğini belirleyin.  Bu özelliği nesnenin özellik listesinin en üstüne, özellik adı ve değeri ise **değer** sütununda görüntülenir.  Bir özelliği kaldırmak için, PIN simgesini yeniden seçin veya bağlam menüsünde **üyeyi sık kullanılanlara ayır** seçeneğini belirleyin.

![izleme penceresi özellikleri sabitleme](../debugger/media/basic-pin-watch.gif "Özellikleri izleme penceresi")

Ayrıca, izleme penceresi nesnenin özellik listesini görüntülerken özellik adlarını açıp sabitlenmemiş özellikleri filtreleyebilirsiniz.  İzleme penceresinin üstündeki araç çubuğunda bulunan düğmeleri seçerek her iki seçeneğe da erişebilirsiniz.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a> İzleme değerlerini Yenile

Bir ifade değerlendirildiğinde bir yenileme simgesi (dairesel ok) **izleme** penceresinde görünebilir. Yenile simgesi bir hatayı veya güncel olmayan bir değeri gösterir.

Değeri yenilemek için Yenile simgesini seçin veya ara çubuğuna basın. Hata ayıklayıcı, ifadeyi yeniden değerlendirmeye çalışır. Ancak, değerin neden değerlendirilmediğini bağlı olarak, ifadeyi yeniden değerlendirilemez ya da tercih edebilirsiniz.

Yenileme simgesinin üzerine gelin veya ifadenin değerlendirilmemesi nedeniyle **değer** sütununa bakın. Nedenler şunlardır:

- Önceki örnekte olduğu gibi ifade değerlendirilirken bir hata oluştu. Zaman aşımı oluşabilir veya bir değişken kapsam dışında olabilir.

- İfadede, uygulamada yan etkiyi tetikleyebilecek bir işlev çağrısı vardır. Bkz. [ifade yan etkileri](#bkmk_sideEffects).

- Özelliklerin otomatik değerlendirilmesi ve örtük işlev çağrıları devre dışı bırakıldı.

Özellikler ve örtük işlev çağrılarının otomatik değerlendirilmesi devre dışı bırakıldığı için Yenile simgesi görüntülenirse, özellik değerlendirmesini etkinleştir ' i ve **Araçlar** seçenekler hata ayıklama genel ' de **diğer örtük işlev çağrılarını etkinleştir** ' i seçerek etkinleştirebilirsiniz  >    >    >  .

Yenileme simgesini kullanmayı göstermek için:

1. **Araçlar**  >  **Seçenekler**  >  **Genel hata ayıklama** bölümünde  >  , **özellik değerlendirmesini etkinleştir ve diğer örtük işlev çağrılarını etkinleştir** onay kutusunu temizleyin.

1. Aşağıdaki kodu girin ve **İzle** penceresinde, özelliği üzerinde bir izleme ayarlayın `list.Count` .

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Hata ayıklamayı başlatın. **Gözcü** penceresinde aşağıdaki iletiye benzer bir şey gösterilir:

   ![Izlemeyi Yenile](../debugger/media/refreshwatch.png "İzlemeyi Yenile")

1. Değeri yenilemek için Yenile simgesini seçin veya ara çubuğuna basın. Hata ayıklayıcı ifadeyi yeniden değerlendirsin.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a> İfade yan etkileri

Bazı ifadelerin değerlendirilmesi bir değişkenin değerini değiştirebilir veya aksi takdirde uygulamanızın durumunu etkileyebilir. Örneğin, aşağıdaki ifadeyi değerlendirmek değerini değiştirir `var1` :

```csharp
var1 = var2
```

Bu kod, [yan etkiye](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))neden olabilir. Yan etkiler, uygulamanızın çalışma biçimini değiştirerek hata ayıklamayı daha zor hale getirir.

Yan etkileri olan bir ifade yalnızca bir kez değerlendirilir, ilk girdiğinizde. Bundan sonra ifade, **Gözcü** penceresinde gri renkte görünür ve daha fazla değerlendirme devre dışı bırakılır. Araç ipucu veya **değer** sütunu, ifadenin bir yan etkiye neden olduğunu açıklar. Değerin yanında görünen yenileme simgesini seçerek, yeniden değerlemeyi zorlayabilirsiniz.

Yan efekt atamasını önlemenin bir yolu otomatik işlev değerlendirmesini devre dışı bırakmak. **Araçlar**  >  **Seçenekler**  >  **Genel hata ayıklama** bölümünde  >   **özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir** seçimini kaldırın.

Yalnızca C# için, özellikler veya örtük işlev çağrıları değerlendirmesi kapalıyken, **izleme** penceresindeki bir değişken **adına** **AC** biçim değiştiricisi ekleyerek değerlendirmeyi zorlayabilirsiniz. Bkz. [C# içindeki biçim belirticileri](../debugger/format-specifiers-in-csharp.md).

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>İzleme penceresi nesne kimliklerini kullanma (C# ve Visual Basic)

Bazen belirli bir nesnenin davranışını gözlemlemek isteyebilirsiniz. Örneğin, bir yerel değişken tarafından başvurulan bir nesneyi, bu değişken kapsam dışına çıktıktan sonra izlemek isteyebilirsiniz. C# ve Visual Basic içinde, başvuru türlerinin belirli örnekleri için nesne kimlikleri oluşturabilir ve bunları **izleme** penceresinde ve kesme noktası koşullarında kullanabilirsiniz. Nesne KIMLIĞI, ortak dil çalışma zamanı (CLR) hata ayıklama Hizmetleri ve nesnesiyle ilişkili olarak oluşturulur.

> [!NOTE]
> Nesne kimlikleri, nesnenin atık olarak toplanmasını önleyen zayıf başvurular oluşturur. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.

Aşağıdaki kodda, `MakePerson()` yöntemi `Person` yerel bir değişken kullanarak bir oluşturur:

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

1. Kesme noktası üzerinde yürütme duraklatılırsa, **Yereller'de** Hata Ayıkla'ya ve **Yereller'e**  >  **Windows**  >  **açın.**

1. Yereller **penceresinde** değişkenine sağ tıklayın ve Nesne `Person` Kimliği **Yapma'yı seçin.**

   YerelLer penceresinde bir dolar işareti ( ) ve sayı **$** (Nesne Kimliği)  görüyor olun.

1. Nesne Kimliği'ne sağ **tıklar** ve İzleme Ekle'yi seçerek nesne kimliğini İzleme **penceresine ekleyin.**

1. yönteminde başka bir kesme noktası `DoSomething()` ayarlayın.

1. Hata ayıklamaya devam. yürütme yönteminde `DoSomething()` duraklatılırsa, **İzleme** penceresi nesneyi `Person` görüntüler.

   > [!NOTE]
   > nesnesinin gibi özelliklerini görmek için Araçlar Seçenekler Hata Ayıklama Genel Etkinleştirme özelliği değerlendirmesini ve diğer örtülü işlev çağrılarını seçerek özellik `Person.Name`   >    >    >    >  **değerlendirmesini etkinleştirmeniz gerekir.**

## <a name="dynamic-view-and-the-watch-window"></a>Dinamik Görünüm ve izleme penceresi

Bazı betik dillerinde (örneğin, JavaScript veya [](https://en.wikipedia.org/wiki/Duck_typing) Python) dinamik veya ördeğin yazılması kullanılır ve .NET sürüm 4.0 ve sonrası normal hata ayıklama pencerelerinde gözlemlen zor nesneleri destekler.

İzleme **penceresinde** bu nesneler, arabirimi uygulayan türlerden oluşturulan dinamik nesneler olarak <xref:System.Dynamic.IDynamicMetaObjectProvider> görüntülenir. Dinamik nesne düğümleri dinamik nesnelerin dinamik üyelerini gösterir, ancak üye değerlerinin düzenlenmesine izin vermez.

Dinamik Görünüm **değerlerini yenilemek** için dinamik [nesne düğümünün](#bkmk_refreshWatch) yanındaki yenileme simgesini seçin.

Bir nesnenin yalnızca **Dinamik Görünümünü** görüntülemek için, İzleme **penceresinde** dinamik nesne adının ardından bir dinamik biçim **belirleyicisi** ekleyin:

- C# için: `ObjectName, dynamic`
- Daha Visual Basic:`$dynamic, ObjectName`

>[!NOTE]
>- C# hata ayıklayıcısı, bir sonraki kod satırına adım atarak **Dinamik** Görünüm'de değerleri otomatik olarak yeniden değerlendirmez.
>- Hata Visual Basic ayıklayıcısı Dinamik Görünüm aracılığıyla eklenen ifadeleri otomatik **olarak yeniler.**
>- Dinamik Görünümün üyelerini **değerlendirmenin** yan [etkileri olabilir.](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))

**Bir nesneyi dinamik nesneye alan yeni bir izleme değişkeni eklemek için:**

1. Dinamik Görünümün herhangi bir alt öğesini **sağ tıklatın.**
1. İzleme **Ekle'yi seçin.** , `object.name` yeni bir İzleme penceresinde görünür ve `((dynamic) object).name` olur. 

Hata ayıklayıcısı ayrıca nesnenin **Dinamik Görünüm** alt düğümünü Otomatikler **penceresine** ekler. Otomatikler penceresini **açmak için,** hata ayıklama sırasında Otomatikler'de **hata**  >  **Windows**  >  **seçin.**

**Dinamik Görünüm,** COM nesneleri için hata ayıklamayı da iyiler. Hata ayıklayıcı, içinde sarmalanmış bir COM **nesnesine System.__ComObject,** nesne için **bir Dinamik Görünüm** düğümü ekler.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>QuickWatch ile tek bir değişkeni veya ifadeyi gözlemle

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

1.   >  **QuickWatch'da Hata Ayıkla'yı** seçin, **Shift** + **F9 tuşuna** basın veya sağ tıklar ve **QuickWatch'u seçin.**

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
