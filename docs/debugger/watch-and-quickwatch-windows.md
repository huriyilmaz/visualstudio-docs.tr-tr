---
title: Değişkenlere bir izleme ayarla | Microsoft Docs
description: Hata ayıklarken, bkz. Izleme ve hızlı Izleme içindeki değişkenler ve ifadeler. İzleme birkaç değişken görüntüleyebilir, hızlı bir şekilde yalnızca bir tane ve yalnızca kesme durumunda olabilir.
ms.custom: SEO-VS-2020, seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d13ee6163ebe8cf0f706cbe95e7451c2ebc7c411
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149488"
---
# <a name="watch-variables-with-watch-windows-and-quickwatch"></a>Pencereleri Izle ve hızlı Gözcü ile değişkenleri izleyin

Hata ayıklarken, değişkenleri ve ifadeleri izlemek için Windows 'u ve **hızlı Izlemeyi** **İzle** ' yi kullanabilirsiniz. Pencereler yalnızca hata ayıklama oturumu sırasında kullanılabilir.

**İzleme** pencereleri, hata ayıklama sırasında her seferinde birkaç değişken görüntüleyebilir. **QuickWatch** iletişim kutusu her seferinde tek bir değişken görüntüler ve hata ayıklamanın devam edebilmesi için kapatılması gerekir.

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

1.  **Hata Ayıkla**  >  **Windows**  >  **izleme**  >  **1**' i seçerek veya **CTRL** + **alt** + **W**  >  **1** tuşlarına basarak bir Gözcü penceresi açın.

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

![Gözcü ifadesi](../debugger/media/watchexpression.png "Gözcü ifadesi")

**İzleme** penceresindeki ifadeleri değerlendirmek için kurallar, kod dilinde ifadeleri değerlendirme kurallarıyla genellikle aynıdır. Bir ifadede sözdizimi hatası varsa, kod Düzenleyicisi 'nde olduğu gibi aynı derleyici hatasını da bekler. Örneğin, yukarıdaki ifadedeki bir yazım hatası, **Gözcü** penceresinde bu hatayı üretir:

![İzleme ifadesi hatası](../debugger/media/watchexpressionerror.png "İzleme ifadesi hatası")

**İzleme** penceresinde iki dalgalı çizgili bir daire simgesi görünebilir. Bu simge, olası bir çapraz iş parçacığı bağımlılığı nedeniyle hata ayıklayıcının ifadeyi değerlendirmediği anlamına gelir. Kodu değerlendirmek, uygulamanızdaki diğer iş parçacıklarının geçici olarak çalışmasını gerektirir, ancak kesme modundayken, uygulamanızdaki tüm iş parçacıkları genellikle durdurulur. Diğer iş parçacıklarının geçici olarak çalışmasına izin verilmesi uygulamanızın durumunda beklenmeyen etkilere sahip olabilir ve hata ayıklayıcı, bu iş parçacıklarında kesme noktaları ve özel durumlar gibi olayları yok sayabilir.

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

   ![Izlemeyi Yenile](../debugger/media/refreshwatch.png "Izlemeyi Yenile")

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

## <a name="use-object-ids-in-the-watch-window-c-and-visual-basic"></a><a name="bkmk_objectIds"></a> İzleme penceresi nesne kimliklerini kullanma (C# ve Visual Basic)

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

Yönteminin adını bulmak için `Person` `DoSomething()` , `Person` **izleme** penceresinde nesne kimliğine bir başvuru ekleyebilirsiniz.

1. Nesne oluşturulduktan sonra kodda bir kesme noktası ayarlayın `Person` .

1. Hata ayıklamayı başlatın.

1. Yürütme kesme noktasında durakladığında,  Windows   >    >  **yerelleri** Hata Ayıkla ' yı seçerek Yereller penceresini açın.

1. **Yereller** penceresinde değişkenine sağ TıKLAYıP `Person` **nesne kimliğini yap**' ı seçin.

   Bir dolar işareti ( **$** ) ve **Locals** PENCERESINDE, nesne kimliği olan bir sayı görmeniz gerekir.

1. Nesne kimliğini sağ tıklayıp **Gözcü Ekle**' yi seçerek, nesne kimliğini **izleme** penceresine ekleyin.

1. Yönteminde başka bir kesme noktası ayarlayın `DoSomething()` .

1. Hata ayıklamaya devam edin. Bu yöntemde Yürütme durakladığında `DoSomething()` , **Gözcü** penceresi `Person` nesneyi görüntüler.

   > [!NOTE]
   > Gibi nesnenin özelliklerini görmek isterseniz, `Person.Name` **araç**  >  **seçenekleri**  >  **hata ayıklama**  >  **genel**  >  **Etkinleştir Özellik değerlendirmesini ve diğer örtük işlev çağrılarını** seçerek Özellik değerlendirmesini etkinleştirmeniz gerekir.

## <a name="dynamic-view-and-the-watch-window"></a>Dinamik görünüm ve izleme penceresi

Bazı betik dilleri (örneğin, JavaScript veya Python) dinamik veya [Duck](https://en.wikipedia.org/wiki/Duck_typing) yazısı kullanır ve .net sürüm 4,0 ve üzeri, normal hata ayıklama pencerelerinin gözleneceği nesneleri destekler.

**Gözcü** penceresi, bu nesneleri arabirimini uygulayan türlerden oluşturulan dinamik nesneler olarak görüntüler <xref:System.Dynamic.IDynamicMetaObjectProvider> . Dinamik nesne düğümleri dinamik nesnelerin dinamik üyelerini gösterir, ancak üye değerlerinin düzenlenmesine izin vermez.

**Dinamik görünüm** değerlerini yenilemek için, dinamik nesne düğümünün yanındaki [Yenile simgesini](#bkmk_refreshWatch) seçin.

Bir nesnenin yalnızca **dinamik görünümünü** görüntülemek Için, **izleme** penceresindeki dinamik nesne adından sonra **dinamik** bir Biçim belirleyicisi ekleyin:

- C# için: `ObjectName, dynamic`
- Visual Basic için: `$dynamic, ObjectName`

>[!NOTE]
>- Bir sonraki kod satırına adımlamak için C# hata ayıklayıcısı **dinamik görünümdeki** değerleri otomatik olarak yeniden değerlendirmez.
>- Visual Basic hata ayıklayıcı **Dinamik görünüm** aracılığıyla eklenen ifadeleri otomatik olarak yeniler.
>- **Dinamik bir görünümün** üyelerini değerlendirmek [yan etkilere](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))sahip olabilir.

**Bir nesneyi dinamik bir nesneye bağlayan yeni bir izleme değişkeni eklemek için:**

1. **Dinamik görünümün** herhangi bir alt öğesine sağ tıklayın.
1. **Gözcü Ekle**' yi seçin. `object.name`Olur `((dynamic) object).name` ve yeni bir **Gözcü** penceresinde görünür.

Hata ayıklayıcı Ayrıca, nesnenin **Dinamik görünüm** alt düğümünü **ekler penceresine ekler** . Hata ayıklama sırasında **oto** penceresini açmak için Windows oto **hatalarını ayıkla**' yı seçin  >    >  .

**Dinamik görünüm** , com nesneleri için hata ayıklamayı da geliştirir. Hata ayıklayıcı **System.__ComObject** SARMALANAN bir com nesnesine aldığında, nesne için **dinamik bir görünüm** düğümü ekler.

## <a name="observe-a-single-variable-or-expression-with-quickwatch"></a>QuickWatch ile tek bir değişken veya ifadeyi gözlemleyin

**QuickWatch** kullanarak tek bir değişkeni gözlemleyebilirsiniz.

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

Değişkeni gözlemlemek için `a`

1. Satırda bir kesme noktası ayarlayın `a = a + b;` .

1. Hata ayıklamayı başlatın. Yürütme kesme noktasında duraklatılır.

1. Koddaki değişkeni seçin `a` .

1.   >  **Hızlı izleme** Hata Ayıkla ' yı seçin, **Shift** + **F9** tuşuna basın veya sağ tıklayıp **hızlı izleme**' yi seçin.

   **QuickWatch** iletişim kutusu görüntülenir. `a`Değişken, **1** **değeri** olan **ifade** kutusudur.

   ![QuickWatch değişkeni](../debugger/media/quickwatchvariable.png "QuickWatch değişkeni")

1. Değişkeni kullanarak bir ifadeyi değerlendirmek için, Ifade kutusuna gibi bir ifade yazın `a + b` ve yeniden  değerlendir ' i seçin. 

   ![QuickWatch ifadesi](../debugger/media/quickwatchexpression.png "QuickWatch ifadesi")

1. **Hızlı** bir şekilde **izleme penceresine değişken** veya Ifade eklemek için, **Gözcü Ekle**' yi seçin.

1. **QuickWatch** penceresini kapatmak için **Kapat** ' ı seçin. (**QuickWatch** kalıcı bir iletişim kutusu olduğundan, açık olduğu sürece hata ayıklamaya devam edemeyeceğinizi.)

1. Hata ayıklamaya devam edin. Değişkeni, **Gözcü** penceresinde gözlemleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama nedir?](../debugger/what-is-debugging.md)
- [Hata ayıklama teknikleri ve araçları](../debugger/write-better-code-with-visual-studio.md)
- [Hata ayıklama bölümüne ilk bakış](../debugger/debugger-feature-tour.md)
- [Hata ayıklayıcı pencereleri](../debugger/debugger-windows.md)
