---
title: Birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 73519dd9-f3d5-49b6-a634-38881b459ea4
caps.latest.revision: 19
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a230b55149152ba1d195f487951323eda855b8b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657149"
---
# <a name="using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing"></a>Birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Saplama türleri *, Microsoft Fakes çerçevesinin, çağırdığı diğer bileşenlerden test ettiğiniz bir bileşeni kolayca ayırmanızı sağlamak için sağladığı iki teknolojiden biridir. Bir saplama test sırasında başka bir bileşenin yer aldığı kodun küçük bir parçasıdır. Bir saplama kullanmanın faydası testi yazmanızı kolaylaştırması, tutarlı sonuçlar döndürmesidir. Ve diğer bileşenleri henüz çalışmıyor olsa bile, testleri çalıştırabilirsiniz.

 Fakes 'e genel bakış ve hızlı başlangıç kılavuzu için bkz. [Microsoft Fakes Ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md).

 Saptamalar kullanmak için bileşen yazmalısınız böylece sınıfları değil uygulamanın başka bölümüne başvuran yalnızca arabirimleri kullanır. Diğer bölüme nazaran daha az değişiklik gerektiren bir bölümde değişiklik yaptığından bu iyi bir tasarım uygulamasıdır. Test etmek için gerçek bir bileşen yerine saplama kullanmanıza olanak tanır.

 Diyagramda, StockAnalyzer bileşeni test etmek istediğimiz bir bileşendir. Normal olarak, başka bir bileşen, RealStockFeed kullanır. Ancak RealStockFeed her defasında StockAnalyzer test etmeyi zorlaştıran yöntemlerinin çağırdığı farklı sonuçlar döndürür.  Sınama sırasında StubStockFeed gibi farklı bir sınıf ile değiştiririz.

 ![Gerçek ve saplama sınıfları bir arabirimle uyumlu.](../test/media/fakesinterfaces.png "FakesInterfaces")

 Saplamalar bu yolla kodunuzun yapısına güveneceğinden genellikle saplamaları başka bir uygulamanın bir bölümünü ayırmak için kullanırsınız. System.dll gibi denetiminiz altında olan diğer derlemelerden ayırmak için normal olarak dolgu verileri kullanabilirsiniz. [Birim testi için uygulamanızı diğer derlemelerden yalıtmak için bkz. dolgular kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

 **Requirements**

- Visual Studio Enterprise

## <a name="How"></a>Saplamaları kullanma

### <a name="Dependency"></a>Bağımlılık ekleme için tasarım
 Saptamaları kullanmak için uygulamanızın farklı bileşenlerini değil birbirlerine bağımlı ancak arabirim tanımlarının yalnızca bağımlı olmasını sağlamak için tasarlanır. Derleme zamanında bağlanmak yerine, bileşenler çalışma zamanında bağlıdır. Bu model yazılımın güncellemesinin güçlü ve kolay yapılmasına yardımcı olur çünkü değişiklikler bileşen sınırları boyunca yayılmaz. Saptamaları kullanmasanız bile bunu öneririz. Yeni kod yazıyorsanız, [bağımlılık ekleme](http://en.wikipedia.org/wiki/Dependency_injection) düzeninin izlenmesi kolaydır. Varolan yazılım için testler yazıyorsanız, yeniden düzenlemeniz gerekebilir. Pratik olursa, yerine dolgu verileri kullanmayı düşünebilirsiniz.

 Bu tartışmaya diyagramdaki motive edici temel bir örnekle başlayalım. Sınıf StockAnalyzer fiyatları paylaşmayı okur ve bazı ilginç sonuçlar üretir. Test etmek istediğimiz bazı ortak yöntemler vardır. Örneği basit tutmak için yalnızca, belirli bir paylaşımın geçerli fiyatını raporlayan yöntemlerden çok basit olan bir tanesine bakalım. Bu yöntemin bir birim testini yazmak istiyoruz. Testin ilk taslağı aşağıdadır:

```csharp
[TestMethod]
public void TestMethod1()
{
    // Arrange:
    var analyzer = new StockAnalyzer();
    // Act:
    var result = analyzer.GetContosoPrice();
    // Assert:
    Assert.AreEqual(123, result); // Why 123?
}
```

```vb
<TestMethod()> Public Sub TestMethod1()
    ' Arrange:
    Dim analyzer = New StockAnalyzer()
    ' Act:
    Dim result = analyzer.GetContosoPrice()
    ' Assert:
    Assert.AreEqual(123, result) ' Why 123?
End Sub
```

 Bu test ile ilgili hemen açık bir sorun: paylaşım fiyatları farklılık gösterir ve bu nedenle onaylama işlemi genellikle başarısız olur.

 StockAnalyzer tarafından kullanılan hala geliştirilmekte olan StockFeed bileşeninde başka bir sorun olabilir. Test altındaki yöntem kodunun ilk taslağı aşağıdadır:

```csharp
public int GetContosoPrice()
{
    var stockFeed = new StockFeed(); // NOT RECOMMENDED
    return stockFeed.GetSharePrice("COOO");
}
```

```vb
Public Function GetContosoPrice()
    Dim stockFeed = New StockFeed() ' NOT RECOMMENDED
    Return stockFeed.GetSharePrice("COOO")
End Function
```

 Anlaşıldığı gibi bu yöntem, derleme veya StockFeed sınıf çalışmaları henüz tam olmadığı için özel bir durum fırlatabilir.

 Arabirim ekleme her iki sorunu giderir.

 Arabirim eklemeye aşağıdaki kural uygulanır:

- Uygulamanızın herhangi bir bileşeninin kodu, bir bildirimde veya `new` bildiriminde, başka bir bileşen içindeki bir sınıfa asla açıkça başvurmamalıdır. Bunun yerine, değişkenler ve parametreler arabirimleriyle bildirilmesi gerekir. Bileşen örnekleri yalnızca bileşen kapsayıcı tarafından oluşturulmalıdır.

   "Bileşeni" tarafından bu durumda bir sınıf veya geliştirdiğiniz ve birlikte güncelleştirdiğiniz sınıflar grubunu demek isteriz. Genellikle, bir bileşen Visual Studio projesindeki koddur. Aynı zamanda güncelleştirildiğinden sınıfları bir bileşen içinde ayırmak daha az önemlidir.

   Ayrıca bileşenlerinizi System.dll gibi göreceli olarak tutarlı platform sınıflardan ayırmak çok önemli değildir. Bu sınıfların arabirimlerini yazmak kodunuzu dağıtabilir.

  StockAnalyzer kodu, StockFeed böyle bir arabirim kullanarak bağlantıyı kesme tarafından geliştirilebilir:

```csharp
public interface IStockFeed
{
    int GetSharePrice(string company);
}

public class StockAnalyzer
{
    private IStockFeed stockFeed;
    public Analyzer(IStockFeed feed)
    {
        stockFeed = feed;
    }
    public int GetContosoPrice()
    {
        return stockFeed.GetSharePrice("COOO");
    }
}
```

```vb
Public Interface IStockFeed
    Function GetSharePrice(company As String) As Integer
End Interface

Public Class StockAnalyzer
    ' StockAnalyzer can be connected to any IStockFeed:
    Private stockFeed As IStockFeed
    Public Sub New(feed As IStockFeed)
        stockFeed = feed
    End Sub
    Public Function GetContosoPrice()
        Return stockFeed.GetSharePrice("COOO")
    End Function
End Class

```

 Bu örnekte, yeniden oluşturulduğunda StockAnalyzer bir IStockFeed uygulamasına geçirilir. Tamamlanan uygulamada, başlatma kodu bağlantı yerine getirilir:

```
analyzer = new StockAnalyzer(new StockFeed())
```

 Bu bağlantıyı gerçekleştirmede daha esnek bir yol vardır. Örneğin, StockAnalyzer, IStockFeed, farklı koşullarda farklı uygulamaları oluşturabileceğiniz factory nesnesi kabul edemedi.

### <a name="GeneratingStubs"></a>Saplamalar oluştur
 Bunu kullanan başka bir bileşenden test etmek istediğiniz sınıfı ayırdınız. Uygulama yapmanın yanı sıra güçlü ve esnek, bağlantıyı kesmenize izin veren bileşen arayüzlerinin test amaçlı uygulamalarını saptama testteki bağlanmanıza olanak sağlar.

 Her zamanki şekilde sınıflar gibi saptamaları basitçe yazabilirsiniz. Ancak Microsoft Fakes her test için en uygun saptama oluşturmak için daha dinamik bir yol sağlar.

 Saptamalar kullanmak için saptama türleri arabirimi tanımlarından oluşturmanız gerekir.

##### <a name="adding-a-fakes-assembly"></a>Fakes Derleme Ekleme

1. Çözüm Gezgini, birim testi projenizin **başvurularını**genişletin.

    - Visual Basic ' de çalışıyorsanız, başvurular listesini görmek için, Çözüm Gezgini araç çubuğunda **tüm dosyaları göster** ' i seçmeniz gerekir.

2. Saptamaları oluşturmak istediğiniz arabirim tanımlarını içeren derlemeyi seçin.

3. Kısayol menüsünde **Fakes derlemesi Ekle**' yi seçin.

### <a name="WriteTest"></a>Yer tutucular ile testinizi yazma

```csharp
[TestClass]
class TestStockAnalyzer
{
    [TestMethod]
    public void TestContosoStockPrice()
    {
      // Arrange:

        // Create the fake stockFeed:
        IStockFeed stockFeed =
             new StockAnalysis.Fakes.StubIStockFeed() // Generated by Fakes.
                 {
                     // Define each method:
                     // Name is original name + parameter types:
                     GetSharePriceString = (company) => { return 1234; }
                 };

        // In the completed application, stockFeed would be a real one:
        var componentUnderTest = new StockAnalyzer(stockFeed);

      // Act:
        int actualValue = componentUnderTest.GetContosoPrice();

      // Assert:
        Assert.AreEqual(1234, actualValue);
    }
    ...
}
```

```vb
<TestClass()> _
Class TestStockAnalyzer

    <TestMethod()> _
    Public Sub TestContosoStockPrice()
        ' Arrange:
        ' Create the fake stockFeed:
        Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed
        With stockFeed
            .GetSharePriceString = Function(company)
                                       Return 1234
                                   End Function
        End With
        ' In the completed application, stockFeed would be a real one:
        Dim componentUnderTest As New StockAnalyzer(stockFeed)
        ' Act:
        Dim actualValue As Integer = componentUnderTest.GetContosoPrice
        ' Assert:
        Assert.AreEqual(1234, actualValue)
    End Sub
End Class

```

 Burada Magic 'in özel parçası `StubIStockFeed` sınıftır. Başvurulan derlemedeki her genel tür için Microsoft Fakes mekanizması saptama sınıfı oluşturur. Saplama sınıfının adı, arabirimin adından türetilir, ön ek olarak "`Fakes.Stub`" ve parametre türü adları eklenir.

 Saptamalar ayrıca olaylar ve genel yöntemlerle ilgili olarak özellik okuyucu ve ayarlayıcılar için oluşturulur.

### <a name="mocks"></a>Parametre değerleri doğrulanıyor
 Bileşeniniz başka bir bileşen için çağrı yaptığında, doğrulayabilirsiniz, doğru değerleri geçirir. Bir onaylama işlemini saptamaya yerleştirebilirsiniz veya değer depolayabilir ve testin ana gövdesini de doğrulayabilirsiniz. Örneğin:

```csharp
[TestClass]
class TestMyComponent
{

    [TestMethod]
    public void TestVariableContosoPrice()
    {
     // Arrange:
        int priceToReturn;
        string companyCodeUsed;
        var componentUnderTest = new StockAnalyzer(new StubIStockFeed()
            {
               GetSharePriceString = (company) =>
                  {
                     // Store the parameter value:
                     companyCodeUsed = company;
                     // Return the value prescribed by this test:
                     return priceToReturn;
                  };
            };
        // Set the value that will be returned by the stub:
        priceToReturn = 345;

     // Act:
        int actualResult = componentUnderTest.GetContosoPrice();

     // Assert:
        // Verify the correct result in the usual way:
        Assert.AreEqual(priceToReturn, actualResult);

        // Verify that the component made the correct call:
        Assert.AreEqual("COOO", companyCodeUsed);
    }
...}

```

```vb
<TestClass()> _
Class TestMyComponent
    <TestMethod()> _
    Public Sub TestVariableContosoPrice()
        ' Arrange:
        Dim priceToReturn As Integer
        Dim companyCodeUsed As String = ""
        Dim stockFeed As New StockAnalysis.Fakes.StubIStockFeed()
        With stockFeed
            ' Implement the interface's method:
            .GetSharePriceString = _
                Function(company)
                    ' Store the parameter value:
                    companyCodeUsed = company
                    ' Return a fixed result:
                    Return priceToReturn
                End Function
        End With
        ' Create an object to test:
        Dim componentUnderTest As New StockAnalyzer(stockFeed)
        ' Set the value that will be returned by the stub:
        priceToReturn = 345

        ' Act:
        Dim actualResult As Integer = componentUnderTest.GetContosoPrice()

        ' Assert:
        ' Verify the correct result in the usual way:
        Assert.AreEqual(priceToReturn, actualResult)
        ' Verify that the component made the correct call:
        Assert.AreEqual("COOO", companyCodeUsed)
    End Sub
...
End Class
```

## <a name="BKMK_Stub_basics"></a>Farklı tür üyeleri için saplamalar

### <a name="BKMK_Methods"></a>Yöntem
 Örnekte açıklandığı gibi yöntemler saptama sınıfının bir örneği için temsilci ekleyerek tamamlanmamış. Saptama türünün adı yöntemi ve parametreleri adlarından türetilir. Örneğin, aşağıdaki `IMyInterface` arabirimi ve yöntemi `MyMethod` verilmiştir:

```csharp
// application under test
interface IMyInterface
{
    int MyMethod(string value);
}
```

 Her zaman 1 döndüren `MyMethod` için bir saplama ekledik:

```csharp
// unit test code
  var stub = new StubIMyInterface ();
  stub.MyMethodString = (value) => 1;

```

 Bir işlev için saptama belirtmezseniz, Fakes dönüş türünün varsayılan değerini döndüren bir işlev oluşturur. Sayılar için varsayılan değer 0 ' dır ve sınıf türleri için `null` (C#) veya `Nothing` (Visual Basic).

### <a name="BKMK_Properties"></a>Özelliklerinin
 Özellik alıcılar ve ayarlayıcılar, ayrı temsilciler olarak sunulur ve ayrı ayrı saptanmış olabilirler. Örneğin, `IMyInterface` `Value` özelliğini göz önünde bulundurun:

```csharp
// code under test
interface IMyInterface
{
    int Value { get; set; }
}

```

 Otomatik özelliğin benzetimini yapmak için `Value` alıcı ve ayarlayıcısına temsilciler iliştirdik:

```csharp
// unit test code
int i = 5;
var stub = new StubIMyInterface();
stub.ValueGet = () => i;
stub.ValueSet = (value) => i = value;

```

 Ayarlayıcı veya özellik alıcısı için saptama yöntemleri belirtmezseniz, saptama özelliği gibi basit bir değişken çalışmasını Fakes değerleri saklayan bir saptama oluşturacaktır.

### <a name="BKMK_Events"></a>Olayları
 Olaylar, temsilci alanları olarak sunulur. Sonuç olarak herhangi bir saptama olayı, olay yedekleme alanını çağırarak basitçe yükseltilebilir. Saptama için yandaki arayüzü göz önünde bulunduralım:

```csharp
// code under test
interface IWithEvents
{
    event EventHandler Changed;
}
```

 @No__t_0 olayını yükseltmek için, yalnızca yedekleme temsilcisini çağırdık:

```csharp
// unit test code
  var withEvents = new StubIWithEvents();
  // raising Changed
  withEvents.ChangedEvent(withEvents, EventArgs.Empty);

```

### <a name="BKMK_Generic_methods"></a>Genel Yöntemler
 Yöntemin istenen her örneklemesi için temsilci sağlayarak, genel yöntemleri saptamak mümkündür. Örneğin, aşağıda verilen arayüz genel yöntem içerir:

```csharp
// code under test
interface IGenericMethod
{
    T GetValue<T>();
}
```

 @No__t_0 örneğini oluşturan bir test yazabilirsiniz:

```csharp
// unit test code
[TestMethod]
public void TestGetValue()
{
    var stub = new StubIGenericMethod();
    stub.GetValueOf1<int>(() => 5);

    IGenericMethod target = stub;
    Assert.AreEqual(5, target.GetValue<int>());
}
```

 Kod, başka bir örneklemeyle `GetValue<T>` çağırırdı, saplama yalnızca davranışı çağırır.

### <a name="BKMK_Partial_stubs"></a>Sanal sınıfların saplamaları
 Önceki örneklerde saptamalar arabirimlerden üretilmedi. Sanal veya özet üyeler bir sınıftan saptamalar da oluşturabilir. Örneğin:

```csharp
// Base class in application under test
    public abstract class MyClass
    {
        public abstract void DoAbstract(string x);
        public virtual int DoVirtual(int n)
        { return n + 42; }
        public int DoConcrete()
        { return 1; }
    }
```

 Bu sınıftan üretilen yer DoAbstract() ve DoVirtual(), ancak değil DoConcrete() temsilci yöntemleri ayarlayabilirsiniz.

```csharp
// unit test
  var stub = new Fakes.MyClass();
  stub.DoAbstractString = (x) => { Assert.IsTrue(x>0); };
  stub.DoVirtualInt32 = (n) => 10 ;

```

 Sanal bir yöntem için temsilci belirtmezseniz, Fakes ya da varsayılan davranışı sağlayabilir veya temel sınıf yöntemi çağırabilirsiniz. Temel yöntemin çağrılması için `CallBase` özelliğini ayarlayın:

```csharp
// unit test code
var stub = new Fakes.MyClass();
stub.CallBase = false;
// No delegate set – default delegate:
Assert.AreEqual(0, stub.DoVirtual(1));

stub.CallBase = true;
//No delegate set - calls the base:
Assert.AreEqual(43,stub.DoVirtual(1));
```

## <a name="BKMK_Debugging_stubs"></a>Hata ayıklama saplamaları
 Saptama türleri, yumuşak bir hata ayıklama deneyimini sağlamak üzere tasarlanmıştır. Varsayılan olarak, hata ayıklayıcı herhangi oluşturulan bir kod üzerinde adım adım ilerler, bu nedenle saptamaya eklenmiş olan özel üye uygulamalarının içine doğrudan atlar.

## <a name="BKMK_Stub_limitation"></a>Saplama sınırlamaları

1. İşaretçilerle birlikte yöntem imzaları desteklenmez.

2. Saptama sınıfları veya statik yöntemleri saptanmamalı; çünkü saptama türü sanal yöntem gönderimine dayanır. Bu tür durumlarda, [birim testi için uygulamanızı diğer derlemelerden yalıtmak üzere](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) dolgu türlerini, parça kullanma bölümünde açıklanan şekilde kullanın

## <a name="BKMK_Changing_the_default_behavior_of_stubs"></a>Saplamalarının varsayılan davranışını değiştirme
 Oluşturulan her saplama türü `IStubBehavior` arabiriminin bir örneğini tutar (`IStub.InstanceBehavior` özelliği aracılığıyla). Hiç eklenmemiş özel temsilci ile üye istemci çağrıları olarak adlandırılır. Davranış ayarlanmamışsa, `StubsBehaviors.Current` özelliği tarafından döndürülen örneği kullanacaktır. Varsayılan olarak, bu özellik `NotImplementedException` özel durumu oluşturan bir davranış döndürür.

 Herhangi bir saplama örneğindeki `InstanceBehavior` özelliği ayarlanarak davranış herhangi bir zamanda değiştirilebilir. Örneğin, aşağıdaki kod parçacığı hiçbir şey yapan veya dönüş türünün varsayılan değerini döndüren bir davranışı değiştirir: `default(T)`:

```csharp
// unit test code
var stub = new StubIFileSystem();
// return default(T) or do nothing
stub.InstanceBehavior = StubsBehaviors.DefaultValue;
```

 Davranış, `StubsBehaviors.Current` özelliği ayarlanarak davranışın ayarlanmayan tüm saplama nesneleri için genel olarak da değiştirilebilir:

```csharp
// unit test code
//change default behavior for all stub instances
//where the behavior has not been set
StubBehaviors.Current =
    BehavedBehaviors.DefaultValue;
```

## <a name="external-resources"></a>Dış kaynaklar

### <a name="guidance"></a>Kılavuz
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 2: birim testi: Içini test etme](http://go.microsoft.com/fwlink/?LinkID=255188)

## <a name="see-also"></a>Ayrıca Bkz.
 [Microsoft Fakes ile Test Edilen Kodu Yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
