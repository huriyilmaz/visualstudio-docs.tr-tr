---
title: Windows izleme ve hızlı Izleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.watch
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], Watch window
- expressions [debugger], evaluating
- variables [debugger], evaluating
- expression evaluation
- registers, evaluating
- debugging [Visual Studio], expression evaluation
ms.assetid: d5c18377-2a0e-4819-a645-407e24ccc58c
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c3f79e492440f98f733488afb241fa6f86e220b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780233"
---
# <a name="watch-and-quickwatch-windows"></a>İzleme ve Hızlı İzleme Pencereleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir hata ayıklama oturumu sırasında değişkenleri ve ifadeleri izlemek için **Gözcü** (**hata ayıklama/Windows/izleme/izleme (1, 2, 3, 4)**) ve **hızlı Izleme** (değişken/ **hata ayıklama/hızlı izleme**) Windows ' u kullanabilirsiniz.  Bu fark, **izleme** penceresinin çeşitli değişkenleri görüntülemesi ve **hızlı gözcü** penceresi aynı anda tek bir değişken görüntülebileceğine göre farklılık gösterir.  
  
## <a name="observing-a-single-variable-with-quickwatch"></a>Hızlı Gözcü ile tek bir değişkeni gözlemleme  
 **Hızlı gözcü** penceresini tek bir değişken gözlemlemek için kullanabilirsiniz. Örneğin, aşağıdaki koda sahipseniz:  
  
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
  
 QuickWatch penceresinde bir değişkeni aşağıdaki gibi gözlemleyebilirsiniz:  
  
1. Satırda bir kesme noktası ayarlayın `a = a + b;` .  
  
2. Hata ayıklamayı başlatın. Yürütme kesme noktasında durmaktadır.  
  
3. **QuickWatch** penceresini açın (a öğesine sağ tıklayın, ardından **Hata Ayıkla/QuickWatch**veya **SHIFT + F9**' i seçin). Pencereyi açabilir ve **ifade** penceresine bir değişken ekleyebilir, sonra yeniden **değerlendirme**' ye tıklayabilirsiniz. **Değerler** penceresinde 2 değeri ile bir değişken görmeniz gerekir.  
  
4. **QuickWatch** penceresi kalıcı bir iletişim kutusu penceresidir, bu nedenle açık olduğu sürece hata ayıklamaya devam edemeyeceğinizi. Gözcü **penceresine,** **Gözcü Ekle**' ye tıklayarak değişkeni ekleyebilirsiniz.  
  
5. **QuickWatch** penceresini kapatın. Artık **Gözcü** penceresindeki değeri gözlemlarken hata ayıklamaya devam edebilirsiniz  
  
## <a name="observing-variables-with-the-watch-window"></a>izleme penceresi değişkenleri gözlemleme  
 **İzleme** penceresi ile birden çok değişkeni gözlemleyebilirsiniz. Örneğin, aşağıdaki koda sahipseniz:  
  
```csharp  
static void Main(string[] args)  
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
}  
  
```  
  
 Üç değişkenin değerlerini izleme penceresi aşağıdaki gibi ekleyin:  
  
1. Satırda bir kesme noktası ayarlayın `c = a + b;` .  
  
2. Hata ayıklamayı Başlat (**F5**). Yürütme kesme noktasında durmaktadır.  
  
3. İzleme penceresi (**hata ayıklama/Windows/izleme/izleme 1**veya **CTRL + ALT + W, 1**) açın.  
  
4. `a`Değişkeni ilk satıra, `b` ikinci satıra ve değişkenine `c` üçüncü satıra ekleyin.  
  
5. Hata ayıklamaya devam edin.  
  
   Döngüde yineleme yaparken değişken değerlerinin değiştiğini görmeniz gerekir `for` .  
  
   Yerel kodda programlama yapıyorsanız, bazen bir değişken adının bağlamını veya değişken adını içeren bir ifadeyi nitelemeniz gerekebilir. Bağlam, bir değişkenin bulunduğu işlev, kaynak dosya ve modüldür. Bunu yapmanız gerekiyorsa, bağlam operatörü söz dizimini kullanabilirsiniz. Daha fazla bilgi için bkz. C++ içindeki Ifadeler.  
  
## <a name="observing-expressions-with-the-watch-window"></a>İfadeleri izleme penceresi ile gözlemleme  
 Şimdi bunun yerine bir ifade kullanmayı deneyelim. Hata ayıklayıcı tarafından tanınan geçerli bir ifade ekleyebilirsiniz.  
  
 Örneğin, önceki bölümde listelenen kod varsa, aşağıdaki gibi üç değerin ortalamasını alabilirsiniz:  
  
 ![WatchExpression](../debugger/media/watchexpression.png "WatchExpression")  
  
 Genel olarak, **izleme** penceresindeki ifadeleri değerlendirmek için kurallar, kodlama dilinizde ifadeleri değerlendirmek için kurallarla aynıdır. İfadenizde bir sözdizimi hatası varsa, kod düzenleyicisinde göreceğiniz derleyici hatasını da bekleyebilir. Bir örneği aşağıda verilmiştir:  
  
 ![WatchExpressionError](../debugger/media/watchexpressionerror.png "WatchExpressionError")  
  
## <a name="refreshing-watch-values-that-are-out-of-date"></a><a name="bkmk_refreshWatch"></a> Güncel olmayan Izleme değerlerini yenileme  
 Belirli durumlarda, **Gözcü** penceresinde bir ifade değerlendirildiğinde bir yenileme simgesi (iki oklu bir daire veya iki dalgalı çizgili bir daire) görebilirsiniz.  Örneğin, özellik değerlendirmesi kapalıysa (**Araçlar/Seçenekler/hata ayıklama/özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir**) ve aşağıdaki koda sahipsiniz:  
  
```csharp  
static void Main(string[] args)  
{  
    List<string> list = new List<string>();  
    list.Add("hello");  
    list.Add("goodbye");  
}  
  
```  
  
 Listenin özelliğinde bir izleme ayarlarsanız aşağıdakine `Count` benzer bir şey görmeniz gerekir:  
  
 ![RefreshWatch](../debugger/media/refreshwatch.png "RefreshWatch")  
  
 Bu, bir hatayı veya güncel olmayan bir değeri gösterir. Simgenin üzerine tıklayarak genellikle değeri yenileyebilirsiniz. ancak bazı durumlarda bunu yenilememeyi tercih edebilirsiniz. İlk olarak değerin neden değerlendirilmediğini bilmeniz gerekir.  
  
 Simgenin üzerine geldiğinizde, bir araç ipucu ifadenin neden değerlendirilmediğini gösteren bilgiler sağlar.  Circling oklar görünürse, ifade aşağıdaki nedenlerden biri için değerlendirilmemiştir:  
  
- • İfade değerlendirilirken bir hata oluştu. Örneğin, bir zaman aşımı oluşmuş olabilir veya bir değişken kapsam dışında olabilir.  
  
- • İfade, uygulamada yan etkiyi tetikleyebilen bir işlev çağrısı içeriyor (bkz. [yan etkileri ve ifadeler](#bkmk_sideEffects)).  
  
- Özellik ve örtük işlev çağrılarının hata ayıklayıcı tarafından otomatik değerlendirilmesi devre dışıdır (**Araçlar/Seçenekler/hata ayıklama/özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştir**) ve ardından ifade otomatik olarak değerlendirilemiyor.  
  
  Değeri yenilemek için Yenile simgesine tıklayın veya ara çubuğuna basın. Hata ayıklayıcı, ifadeyi yeniden değerlendirmeye çalışacaktır. Özellikler ve örtük yan etkilerin otomatik değerlendirmesi kapatılmış olduğundan, yenileme simgesi göründüyse, ifade değerlendirilemiyor.  
  
  İş parçacıklarına benzer iki dalgalı çizgi olan bir daire olan bir simge görürseniz, olası bir çapraz iş parçacığı bağımlılığı nedeniyle ifade değerlendirilmemiştir. Diğer bir deyişle, kodu değerlendirmek uygulamanızdaki diğer iş parçacıklarının geçici olarak çalışmasını gerektirir. Kesme modundayken, uygulamanızdaki tüm iş parçacıkları genellikle durdurulur. Diğer iş parçacıklarının geçici olarak çalışmasına izin verilmesi programınızın durumunda beklenmedik etkileri olabilir ve hata ayıklayıcının bu iş parçacıklarında oluşan kesme noktaları ve özel durumlar gibi olayları yoksaymasına neden olur.  
  
## <a name="side-effects-and-expressions"></a><a name="bkmk_sideEffects"></a> Yan etkiler ve Ifadeler  
 Bazı ifadelerin değerlendirilmesi, bir değişkenin değerini değiştirebilir veya programınızın durumunu etkileyebilir. Örneğin, aşağıdaki ifadeyi değerlendirmek değerini değiştirir `var1` :  
  
```  
var1 = var2  
```  
  
 Buna bir [yan etkisi](https://en.wikipedia.org/wiki/Side_effect_\(computer_science\))denir. Yan etkiler, programınızın çalışma biçimini değiştirerek hata ayıklamayı daha zor hale getirir.  
  
 Yan etkileri olan bilinen bir ifade, ilk kez girdiğinizde yalnızca bir kez değerlendirilir. Sonraki değerlendirmeler devre dışı bırakıldı. Değerin yanında görünen Güncelleştir simgesine tıklayarak bu davranışı el ile geçersiz kılabilirsiniz.  
  
 Tüm yan etkileri önlemenin bir yolu otomatik işlev değerlendirmesini devre dışı bırakmak (**Araçlar/Seçenekler/hata ayıklama/özellik değerlendirmesini ve diğer örtük işlev çağrılarını etkinleştirmek**).  
  
 Özellikleri veya örtük işlev çağrılarını değerlendirmede devre dışı bırakıldığında, **AC** biçimi değiştiricisini (yalnızca C# için) kullanarak değerlendirmeyi zorlayabilirsiniz. Bkz. [C# içindeki biçim belirticileri](../debugger/format-specifiers-in-csharp.md).  
  
## <a name="using-object-ids-in-the-watch-window-c-and-visual-basic"></a>İzleme penceresi nesne kimliklerini kullanma (C# ve Visual Basic)  
 Belirli bir nesnenin davranışını gözlemlemek istediğiniz zamanlar vardır; Örneğin, bir yerel değişken tarafından başvurulan bir nesneyi, bu değişken kapsam dışına çıktıktan sonra izlemek isteyebilirsiniz. C# ve Visual Basic içinde, başvuru türlerinin belirli örnekleri için nesne kimlikleri oluşturabilir ve bunları izleme penceresi ve kesme noktası koşullarında kullanabilirsiniz. Nesne KIMLIĞI, ortak dil çalışma zamanı (CLR) hata ayıklama Hizmetleri ve nesnesiyle ilişkili olarak oluşturulur.  
  
> [!NOTE]
> Nesne kimlikleri zayıf başvurular oluşturur ve nesnenin atık toplanmasını engellemez. Bunlar yalnızca geçerli hata ayıklama oturumu için geçerlidir.  
  
 Aşağıdaki kodda, bir yöntemi `Person` yerel bir değişken kullanarak oluşturur, ancak `Person` adının ne olduğunu farklı bir yöntemde öğrenmek istersiniz:  
  
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
    List<Person> _people = new List<Person>();  
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
  
 `Person`Aşağıdaki gibi, **Gözcü** penceresinde bu nesneye bir başvuru ekleyebilirsiniz:  
  
1. Nesne oluşturulduktan sonra kodda bir kesme noktası ayarlayın.  
  
2. Hata ayıklamayı başlatın ve yürütme kesme noktasında durdurulduğunda, **Yereller** penceresinde değişkeni bulun, sağ tıklayın ve **nesne kimliğini yap**' ı seçin.  
  
3. **$** **Yereller** penceresinde bir ve bir sayı görmeniz gerekir. Bu, nesne KIMLIĞIDIR.  
  
4. İzleme penceresi nesne KIMLIĞINI ekleyin.  
  
5. Nesnenin davranışını gözlemlemek istediğiniz bir kesme noktası ayarlayın.  Yukarıdaki kodda, bu, `DoSomething()` yönteminde olacaktır.  
  
6. Hata ayıklamaya devam et, ve yöntemde yürütme durdurulduğunda `DoSomething()` , **Gözcü** penceresi `Person` nesneyi görüntüler.  
  
> [!NOTE]
> Yukarıdaki örnekte olduğu gibi nesnenin özelliklerini görmek isterseniz `Person.Name` özellik değerlendirmesini etkinleştirmiş olmanız gerekir.  
  
## <a name="using-registers-in-the-watch-window-c-only"></a>İzleme penceresi yazmaçların kullanımı (yalnızca C++)  
 Yerel kod hata ayıklaması yapıyorsanız, veya kullanarak değişken adlarını ve kayıt adlarını ekleyebilirsiniz **$\<register name>** **@\<register name>** .  Daha fazla bilgi için bkz. [sözde değişkenler](../debugger/pseudovariables.md).  
  
## <a name="dynamicview-and-the-watch-window"></a>DynamicView ve izleme penceresi  
 Bazı betik dilleri (ör. JavaScript veya Python) dinamik veya [Duck yazısı](https://en.wikipedia.org/wiki/Duck_typing)kullanır ve .NET dilleri (sürüm 4,0 ve üzeri), normal hata ayıklama pencerelerini kullanarak gözlemlemeye zorlaştırılması gereken nesneleri destekler, çünkü bunlar, çalışma zamanı özelliklerine ve görüntülenemeyecek yöntemlere sahip olabilirler.  
  
 İzleme penceresi bir veya öğesini uygulayan bir türden oluşturulan bir nesneyi görüntülediğinde <xref:System.Dynamic.IDynamicMetaObjectProvider> , hata ayıklayıcı, **oto** ekranına özel bir **Dinamik görünüm** düğümü ekler. Bu düğüm, dinamik nesnenin dinamik üyelerini gösterir, ancak üye değerlerinin düzenlenmesine izin vermez.  
  
 **Dinamik görünümün** herhangi bir alt öğesine sağ tıklayıp **Gözcü Ekle**' yi seçerseniz, hata ayıklayıcı bir nesneyi dinamik bir nesneye bağlayan yeni bir izleme değişkeni ekler. Diğer bir deyişle, **nesne adı** (**(dinamik) nesnesi) olur. Ad**.  
  
 **Dinamik bir görünümün** üyelerini değerlendirmek yan etkilere sahip olabilir. Yan etkilerin ne olduğuna ilişkin bir açıklama için bkz. [yan etkiler ve ifadeler](#bkmk_sideEffects). C# için, yeni bir kod satırına tıkladığınızda hata ayıklayıcı **dinamik görünümde** gösterilen değerleri otomatik olarak yeniden değerlendirmez. Visual Basic için, **dinamik görünümden** eklenen ifadeler otomatik olarak yenilenir.  
  
 Dinamik görünüm değerlerinin nasıl yenileneceği hakkında yönergeler için, bkz. [yenileme izleme değerleri güncel değil](#bkmk_refreshWatch).  
  
 Bir nesne için yalnızca **dinamik görünümü** görüntülemek istiyorsanız, **dinamik** biçim belirticisini kullanabilirsiniz:  
  
- C#: **ObjectName, dinamik**  
  
- Visual Basic:: **$Dynamic, ObjectName**  
  
  **Dinamik görünüm** , com nesneleri için hata ayıklama deneyimini de geliştirir. Hata ayıklayıcı, **System. __ComObject**SARMALANAN bir com nesnesiyle karşılaştığında, nesne için **dinamik bir görünüm** düğümü ekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcısı Pencereleri](../debugger/debugger-windows.md)
