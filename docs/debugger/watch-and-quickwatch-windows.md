---
title: Değişkenlere saat ayarlama | Microsoft Dokümanlar
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302009"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Watch windows ve QuickWatch ile değişkenleri izleyin

Hata ayıklama yaparken, değişkenleri ve ifadeleri izlemek için **Watch** pencerelerini ve **QuickWatch'u** kullanabilirsiniz. Pencereler yalnızca hata ayıklama oturumu sırasında kullanılabilir.

**İzleme** pencereleri hata ayıklama sırasında aynı anda birden fazla değişken görüntüleyebilir. **QuickWatch** iletişim kutusu aynı anda tek bir değişken görüntüler ve hata ayıklama devam etmeden önce kapatılmalıdır.

Bu kod hata ayıklama denedim ilk kez ise, bu makalede geçmeden önce mutlak yeni başlayanlar ve [Hata Ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md) için Hata [Ayıklama](../debugger/debugging-absolute-beginners.md) okumak isteyebilirsiniz.

## <a name="observe-variables-with-a-watch-window"></a>Saat penceresi olan değişkenleri gözlemleme

Birden fazla **İzleme** penceresi açabilir ve Bir **Saat** penceresinde birden fazla değişken gözlemleyebilirsiniz.

Örneğin, `a`, , `b`, ve `c` aşağıdaki kod değerleri bir saat ayarlamak için:

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

1. Sol kenar boşluğuna `c = a + b;` tıklayarak, **Hata Ayıklama** > **Kesme Noktası'nı**seçerek veya **F9**tuşuna basarak satırda bir kesme noktası ayarlayın.

1. Yeşil **Başlat** oku veya **Hata Ayıklama** > **Başlangıç Hata Ayıklama'yı**seçerek hata ayıklamaya başlayın veya **F5 tuşuna**basın. Yürütme kesme noktasında duraklar.

1. **Hata Ayıklama** > **Windows** > **Watch** > Watch 1'i seçerek veya **Ctrl**+**Alt**+**W** > **1'e**basarak **Bir İzleme** **penceresi**açın.

   Windows **2,** **3**veya **4'ünü**seçerek ek **İzle** pencereleri açabilirsiniz.

1. **İzleme** penceresinde boş bir satır seçin ve `a`değişken yazın. Için aynı `b` şeyi `c`yapın ve.

   ![Değişkenleri izleme](../debugger/media/watchvariables.png "WatchVariables")

1. Hata **Ayıklama** > **Adım Adım'ı** seçerek veya ilerlemek için gerektiğinde **F11** tuşuna basarak hata ayıklamaya devam edin. **Döngü** boyunca yinelediğiniz `for` şekilde İzleme penceresindeki değişken değerleri değişir.

>[!NOTE]
>Yalnızca C++ için,
>- Değişken adının bağlamını veya değişken adı kullanan bir ifadeyi nitelemeniz gerekebilir. Bağlam, bir değişkenin bulunduğu işlev, kaynak dosya veya modüldür. Bağlamı nitelemeniz gerekiyorsa, **Saat** penceresindeki **Ad'daki** [bağlam işleci (C++)](../debugger/context-operator-cpp.md) sözdizimini kullanın.
>
>- ** $ \<Kayıt adını>&nbsp;** kullanarak kayıt adları ve değişken adları ekleyebilir **Watch** veya **Name** ** @ \<&nbsp;** Saat penceresindeki Ad'a>kayıt adı ekleyebilirsiniz. Daha fazla bilgi için [Pseudovariables'e](../debugger/pseudovariables.md)bakın.

## <a name="use-expressions-in-a-watch-window"></a>İzleme penceresinde ifadeleri kullanma

**Saat** penceresinde hata ayıklayıcı tarafından tanınan geçerli bir ifadeyi gözlemleyebilirsiniz.

Örneğin, önceki bölümdeki kod `(a + b + c) / 3` **için, İzleme** penceresine girerek üç değerin ortalamasını alabilirsiniz:

![İfadeyi izleyin](../debugger/media/watchexpression.png "İfadeyi izleyin")

**İzleme** penceresindeki ifadeleri değerlendirme kuralları genellikle kod dilindeki ifadeleri değerlendirme kurallarıyla aynıdır. Bir ifadede sözdizimi hatası varsa, kod düzenleyicisindeki yle aynı derleyici hatasını bekleyin. Örneğin, önceki ifadedeki bir yazım hatası Bu hatayı **İzle** penceresinde üretir:

![İfade hatasini izleme](../debugger/media/watchexpressionerror.png "İfade hatasini izleme")

**İzleme** penceresinde iki dalgalı çizgi simgesiiçeren bir daire görünebilir. Bu simge, hata ayıklamanın olası bir çapraz iş parçacığı bağımlılığı nedeniyle ifadeyi değerlendirmediği anlamına gelir. Kodun değerlendirilmesi, uygulamanızdaki diğer iş parçacıklarının geçici olarak çalışmasını gerektirir, ancak kesme modunda olduğunuz için uygulamanızdaki tüm iş parçacıkları genellikle durdurulur. Diğer iş parçacıklarının geçici olarak çalışmasına izin vermek uygulamanızın durumu üzerinde beklenmeyen etkilere neden olabilir ve hata ayıklayan bu iş parçacıklarındaki kesme noktaları ve özel durumlar gibi olayları yok sayabilir.

::: moniker range=">= vs-2019" 
## <a name="search-in-the-watch-window"></a>İzleme penceresinde arama

Her pencerenin üzerindeki arama çubuğunu kullanarak **İzleme** penceresinin Ad, Değer ve Tür sütunlarında anahtar kelimeleri arayabilirsiniz. ENTER tuşuna basın veya aramayı yürütmek için oklardan birini seçin. Devam eden bir aramayı iptal etmek için, arama çubuğundaki "x" simgesini seçin.

Bulunan eşleşmeler arasında gezinmek için sol ve sağ okları (sırasıyla Shift+F3 ve F3) kullanın.

![İzleme Penceresinde Ara](../debugger/media/ee-search-watch.png "İzleme Penceresinde Ara")

Aramanızı daha fazla veya daha az kapsamlı hale getirmek için, iç içe nesnelerde kaç seviye derinliğinde arama yapmak istediğinizi seçmek için **Watch** penceresinin üst kısmındaki **Daha Derin Arama** açılır penceresini kullanın. 

## <a name="pin-properties-in-the-watch-window"></a>İzleme penceresindeki özellikleri sabitleme

>[!NOTE]
> Bu özellik .NET Core 3.0 veya daha yüksek olarak desteklenir.

**Sabitlenebilir Özellikler** aracıyla Nesneleri İzleme penceresindeki özelliklerine göre hızlı bir şekilde inceleyebilirsiniz.  Bu aracı kullanmak için, bir özelliğin üzerine gidip görünen veya sağ tıklayan pin simgesini seçin ve ortaya çıkan bağlam menüsünde **Favori seçeneği olarak Üye Pin'i** seçin.  Bu, bu özelliği nesnenin özellik listesinin en üstüne kabarcıklar ve özellik adı ve değeri **Değer** sütununda görüntülenir.  Bir özelliği niçin yeniden pin simgesini seçin veya bağlam menüsünde **Sık Kullanılan seçeneğini Unpin Seçeneğini** belirleyin.

![İzleme penceresindeki özellikleri sabitleme](../debugger/media/basic-pin-watch.gif "İzleme penceresindeki özellikleri sabitleme")

Ayrıca, nesnenin özellik listesini İzleme penceresinde görüntülerken özellik adlarını geçiş yapabilir ve sabitlenmemiş özellikleri filtreleyebilirsiniz.  Saat penceresinin üzerindeki araç çubuğundaki düğmeleri seçerek her iki seçenede de erişebilirsiniz.

::: moniker-end

### <a name="refresh-watch-values"></a><a name="bkmk_refreshWatch"></a>Saat değerlerini yenile

Bir ifade değerlendirildiğinde **İzleme** penceresinde bir yenileme simgesi (dairesel ok) görünebilir. Yenileme simgesi bir hatayı veya güncel olmayan bir değeri gösterir.

Değeri yenilemek için yenile simgesini seçin veya boşluk çubuğuna basın. Hata ayıklama, ifadeyi yeniden değerlendirmeye çalışır. Ancak, değerin neden değerlendirilmediğine bağlı olarak ifadeyi istemeyebilirsiniz veya yeniden değerlendirebilirsiniz.

Yenileme simgesinin üzerine dokunun veya ifadenin değerlendirilmemesinin nedeni için **Değer** sütununa bakın. Nedenleri şunlardır:

- Önceki örnekte olduğu gibi ifade değerlendirilirken bir hata oluştu. Bir zaman acısı oluşabilir veya bir değişken kapsam dışında olabilir.

- İfade, uygulamada bir yan etkiyi tetikleyebilecek bir işlev çağrısına sahiptir. Bkz. [İfade yan etkileri](#bkmk_sideEffects).

- Özelliklerin ve örtülü işlev çağrılarının otomatik değerlendirilmesi devre dışı bırakılır.

Özelliklerin ve örtülü işlev çağrılarının otomatik olarak değerlendirilmesi devre dışı bırakıldığıiçin yenileme simgesi görünüyorsa, **Genel Araçlar** > **Seçenekleri** > **Hata Ayıklama'da** > özellik **değerlendirmesini ve diğer örtülü işlev çağrılarını etkinleştir'i** seçerek bunu etkinleştirebilirsiniz.**General**

Yenileme simgesini kullanarak göstermek için:

1. Genel**General**Araç**Ayıklama** > **Araçlar'da** >  **Tools** >  **özellik değerlendirmesini etkinleştir ve diğer örtülü işlev çağrıları** onay kutusunu temizleyin.

1. Aşağıdaki kodu girin ve **İzleme** `list.Count` penceresine, özellik üzerinde bir saat ayarlayın.

   ```csharp
   static void Main(string[] args)
   {
       List<string> list = new List<string>();
       list.Add("hello");
       list.Add("goodbye");
   }
   ```

1. Hata ayıklamaya başla. **İzleme** penceresi aşağıdaki iletiye benzer bir şey gösterir:

   ![İzle yenile](../debugger/media/refreshwatch.png "İzle yenile")

1. Değeri yenilemek için yenile simgesini seçin veya boşluk çubuğuna basın. Hata ayıklama ifadeyi yeniden değerlendirir.

### <a name="expression-side-effects"></a><a name="bkmk_sideEffects"></a>Ekspresyon yan etkileri

Bazı ifadeleri değerlendirmek bir değişkenin değerini değiştirebilir veya uygulamanızın durumunu etkileyebilir. Örneğin, aşağıdaki ifadeyi değerlendirmek aşağıdaki `var1`ifadenin değerini değiştirir:

```csharp
var1 = var2
```

Bu kod bir [yan etkiye](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))neden olabilir. Yan etkiler, uygulamanızın çalışma şeklini değiştirerek hata ayıklamayı zorlaştırabilir.

Yan etkileri olan bir ifade, ilk girdiğinizde yalnızca bir kez değerlendirilir. Bundan sonra, ifade **İzleme Penceresi'nde** gri görünür ve diğer değerlendirmeler devre dışı bırakılır. Araç ipucu veya **Değer** sütunu, ifadenin bir yan etkiye neden olduğunu açıklar. Değerin yanında görünen yenileme simgesini seçerek yeniden değerlendirmeyi zorlayabilirsiniz.

Yan etkileri atama önlemek için bir yolu otomatik fonksiyon değerlendirmesi kapatmaktır. **Genel Araç** > **Ayıklama** > Araçlar**Seçenekleri'nde** > **özellik** **değerlendirmesini ve diğer örtülü işlev çağrılarını seçin.**

Yalnızca C# için, özelliklerin veya örtülü işlev çağrılarının değerlendirilmesi kapatıldığında, **Saat** penceresindeki **bir** ad değişkenine **ac** biçimi değiştiricisini ekleyerek değerlendirmeyi zorlayabilirsiniz. [C# format belirteçleri](../debugger/format-specifiers-in-csharp.md)bakın.

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a>İzleme penceresinde Nesne İngilizcesi Kullanma (C# ve Visual Basic)

Bazen belirli bir nesnenin davranışını gözlemlemek istersiniz. Örneğin, bu değişken kapsam dışına çıktıktan sonra yerel bir değişken tarafından başvurulan bir nesneyi izlemek isteyebilirsiniz. C# ve Visual Basic'te, belirli başvuru türleri için Nesne İngilizcesi oluşturabilir ve bunları **Watch** penceresinde ve kesme noktası koşullarında kullanabilirsiniz. Nesne Kimliği, ortak dil çalışma zamanı (CLR) hata ayıklama hizmetleri tarafından oluşturulur ve nesneyle ilişkilidir.

> [!NOTE]
> Nesne işleri, nesnenin toplanmasını engellemeyen zayışlı açıklamalar oluşuyor. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.

Aşağıdaki kodda, `MakePerson()` yöntem yerel `Person` bir değişken kullanarak oluşturur:

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

Yöntemdeki nin adını bulmak **için, Saat** penceresindeki `Person` Nesne Kimliği'ne bir başvuru ekleyebilirsiniz. `Person` `DoSomething()`

1. `Person` Nesne oluşturulduktan sonra kodda bir kesme noktası ayarlayın.

1. Hata ayıklamaya başla.

1. Yürütme kesme noktasında duraklattığında, **Hata Ayıklama** > **Windows** > **Locals'ı**seçerek **Yereller** penceresini açın.

1. **Yereller** penceresinde, değişkeni `Person` sağ tıklatın ve Nesne Kimliği **Yap'ı**seçin.

   Bir dolar işareti (**$**) artı Nesne Kimliği olan **Locals** penceresinde bir numara görmeniz gerekir.

1. Nesne Kimliği'ne sağ tıklayarak ve **İzle Ekle'yi**seçerek Nesne Kimliğini **İzleme** penceresine ekleyin.

1. `DoSomething()` Yöntemde başka bir kesme noktası ayarlayın.

1. Hata ayıklama devam edin. Yöntemde yürütme duraklattığında, **İzleme** penceresi `Person` nesneyi görüntüler. `DoSomething()`

   > [!NOTE]
   > Nesnenin özelliklerini görmek `Person.Name`istiyorsanız , Araçlar **Tools** > **Seçenekleri** > **Hata Ayıklama** > **Genel** > Özellik değerlendirme ve diğer örtülü işlev çağrıları seçerek özellik**değerlendirmesini**etkinleştirmelisiniz.

## <a name="dynamic-view-and-the-watch-window"></a>Dinamik Görünüm ve İzleme penceresi

Bazı komut dosyası dilleri (örneğin, JavaScript veya Python) dinamik veya [ördek](https://en.wikipedia.org/wiki/Duck_typing) yazma ve .NET sürüm 4.0 kullanır ve daha sonra normal hata ayıklama pencerelerinde gözlemlemek zor nesneleri destekler.

**İzleme** penceresi bu <xref:System.Dynamic.IDynamicMetaObjectProvider> nesneleri, arabirimi uygulayan türlerden oluşturulan dinamik nesneler olarak görüntüler. Dinamik nesne düğümleri dinamik nesnelerin dinamik üyelerini gösterir, ancak üye değerlerin düzenlenmesine izin vermez.

Dinamik **Görünüm** değerlerini yenilemek için dinamik nesne düğümünün yanındaki [yenileme simgesini](#bkmk_refreshWatch) seçin.

Yalnızca bir nesne için **Dinamik Görünüm'ü** görüntülemek için, **İzleme** penceresindeki dinamik nesne adından sonra **dinamik** bir biçim belirtici ekleyin:

- C#için:`ObjectName, dynamic`
- Visual Basic için:`$dynamic, ObjectName`

>[!NOTE]
>- C# hata ayıklayıcı, bir sonraki kod satırına adım attığınızda **Dinamik Görünüm'deki** değerleri otomatik olarak yeniden değerlendirmez.
>- Visual Basic hata **ayıkleyici, Dinamik Görünüm**üzerinden eklenen ifadeleri otomatik olarak yeniler.
>- **Dinamik Görünüm** üyelerinin değerlendirilmesi [yan etkileri](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))olabilir.

**Nesneyi dinamik bir nesneye atan yeni bir saat değişkeni eklemek için:**

1. **Dinamik Görünüm'ün**herhangi bir çocuğuna sağ tıklayın.
1. **İzle Ekle'yi**seçin. Olur `object.name` `((dynamic) object).name` ve yeni bir **İzle** penceresinde görünür.

Hata ayıklama, nesnenin **Dinamik Görünüm** alt düğümüne **De ekler.** **Otomatik Hata** ayıklama sırasında Otomatik Ler penceresini açmak için Hata **Ayıklama** > **Windows** > **Autos'u**seçin.

**Dinamik Görünüm,** COM nesneleri için hata ayıklamayı da geliştirir. Hata ayıklayıcı **System.__ComObject'a**sarılmış bir COM nesnesine ulaştığında, nesne için **Dinamik Görünüm** düğümü ekler.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>QuickWatch ile tek bir değişkeni veya ifadeyi gözlemleyin

Tek bir değişkeni gözlemlemek için **QuickWatch'u** kullanabilirsiniz.

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

1. `a = a + b;` Hatta bir kesme noktası ayarlayın.

1. Hata ayıklamaya başla. Yürütme kesme noktasında duraklar.

1. Koddaki `a` değişkeni seçin.

1. **Hata Ayıklama** > **QuickWatch'u**seçin, **Shift**+**F9**tuşuna basın veya sağ tıklayın ve **QuickWatch'u**seçin.

   **QuickWatch** iletişim kutusu görüntülenir. `a` Değişken, **1** **değeri** olan **İfade** kutusundadır.

   ![QuickWatch değişkeni](../debugger/media/quickwatchvariable.png "QuickWatch değişkeni")

1. Değişkeni kullanarak bir ifadeyi değerlendirmek `a + b` **için, İfade** kutusundaki gibi bir ifade yazın ve **Yeniden Değerlendir'i**seçin.

   ![QuickWatch ifadesi](../debugger/media/quickwatchexpression.png "QuickWatch ifadesi")

1. **QuickWatch'tan** **Saati İzle** penceresine değişken veya ifade eklemek için **İzle Ekle'yi**seçin.

1. **QuickWatch** penceresini kapatmak için **Kapat'ı** seçin. (**QuickWatch** bir modal iletişim kutusudur, bu nedenle açık olduğu sürece hata ayıklama devam edemez.)

1. Hata ayıklama devam edin. **Saati** penceresinde değişkeni gözlemleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcısı pencereleri](../debugger/debugger-windows.md)
