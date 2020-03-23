---
title: Uygulamanızın bazı bölümlerini test etmek için yalıtmak için saplamalar kullanma
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 328551a78464c7b682eea6a988c20e742f2797c9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568554"
---
# <a name="use-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing"></a>Birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma

*Saplama türleri,* Microsoft Fakes çerçevesinin, sınadığınız bir bileşeni çağırdığı diğer bileşenlerden kolayca yalıtmanıza olanak sağlayan iki teknolojiden biridir. Bir saplama test sırasında başka bir bileşenin yer aldığı kodun küçük bir parçasıdır. Bir saplama kullanmanın faydası testi yazmanızı kolaylaştırması, tutarlı sonuçlar döndürmesidir. Ve diğer bileşenleri henüz çalışmıyor olsa bile, testleri çalıştırabilirsiniz.

Fakes'e genel bakış ve hızlı başlangıç kılavuzu için, [Microsoft Fakes ile test altında kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)kılavuzuna bakın.

Saptamalar kullanmak için bileşen yazmalısınız böylece sınıfları değil uygulamanın başka bölümüne başvuran yalnızca arabirimleri kullanır. Diğer bölüme nazaran daha az değişiklik gerektiren bir bölümde değişiklik yaptığından bu iyi bir tasarım uygulamasıdır. Test etmek için gerçek bir bileşen yerine saplama kullanmanıza olanak tanır.

Diyagramda, StockAnalyzer bileşeni test etmek istediğimiz bir bileşendir. Normal olarak, başka bir bileşen, RealStockFeed kullanır. Ancak RealStockFeed her defasında StockAnalyzer test etmeyi zorlaştıran yöntemlerinin çağırdığı farklı sonuçlar döndürür.  Sınama sırasında StubStockFeed gibi farklı bir sınıf ile değiştiririz.

![Gerçek ve Stub sınıfları tek bir arabirime uygundur.](../test/media/fakesinterfaces.png)

Saplamalar bu yolla kodunuzun yapısına güveneceğinden genellikle saplamaları başka bir uygulamanın bir bölümünü ayırmak için kullanırsınız. *System.dll*gibi denetiminiz altında olmayan diğer derlemelerden izole etmek için normalde şimler kullanırsınız. Bkz. [Uygulamanızı birim testi için diğer derlemelerden yalıtmak için shims kullanın.](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

## <a name="how-to-use-stubs"></a>Saptamalar nasıl kullanılır?

### <a name="design-for-dependency-injection"></a>Tasarım için bağımlılık ekleme

Saptamaları kullanmak için uygulamanızın farklı bileşenlerini değil birbirlerine bağımlı ancak arabirim tanımlarının yalnızca bağımlı olmasını sağlamak için tasarlanır. Derleme zamanında bağlanmak yerine, bileşenler çalışma zamanında bağlıdır. Bu model yazılımın güncellemesinin güçlü ve kolay yapılmasına yardımcı olur çünkü değişiklikler bileşen sınırları boyunca yayılmaz. Saplama kullanmasanız bile izlemenizi öneririz. Yeni kod yazıyorsanız, [bağımlılık enjeksiyon](https://en.wikipedia.org/wiki/Dependency_injection) deseni takip etmek kolaydır. Varolan yazılım için testler yazıyorsanız, yeniden düzenlemeniz gerekebilir. Pratik olursa, yerine dolgu verileri kullanmayı düşünebilirsiniz.

Bu tartışmaya, diyagramdaki motive edici bir örnekle başlayalım. Sınıf StockAnalyzer fiyatları paylaşmayı okur ve bazı ilginç sonuçlar üretir. Test etmek istediğimiz bazı ortak yöntemler vardır. Basit şeyler tutmak için, sadece bu yöntemlerden biri, belirli bir payın geçerli fiyat raporları çok basit bir bakalım. Bu yöntemin bir birim testini yazmak istiyoruz. İşte bir testin ilk taslağı:

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

StockAnalyzer tarafından kullanılan hala geliştirilmekte olan StockFeed bileşeninde başka bir sorun olabilir. Test altındaki yöntemin kodunun ilk taslağı aşağıda veda edebilirsiniz:

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

Anlaşıldığı gibi bu yöntem, derleme veya StockFeed sınıf çalışmaları henüz tam olmadığı için özel bir durum fırlatabilir. Arabirim ekleme her iki sorunu giderir. Arabirim eklemeye aşağıdaki kural uygulanır:

Uygulamanızın herhangi bir bileşeninin kodu, bir bildirimde veya `new` deyimde, hiçbir zaman başka bir bileşendeki bir sınıfa açıkça başvurmamalıdır. Bunun yerine, değişkenler ve parametreler arabirimleriyle bildirilmesi gerekir. Bileşen örnekleri yalnızca bileşenin kapsayıcısı tarafından oluşturulmalıdır.

- "Bileşen" derken, birlikte geliştirdiğiniz ve güncellediğiniz bir sınıf veya sınıf grubunu kastediyoruz. Genellikle, bir bileşen Visual Studio projesindeki koddur. Sınıfları aynı anda güncelleştirdikleri için tek bir bileşen içinde ayırmak daha az önemlidir.

- Bileşenlerinizi *System.dll*gibi nispeten kararlı bir platformun sınıflarından ayırmak da o kadar önemli değildir. Bu sınıfların arabirimlerini yazmak kodunuzu dağıtabilir.

Aşağıdaki gibi bir arabirim kullanarak StockAnalyzer kodunu StockFeed'den ayırabilirsiniz:

```csharp
public interface IStockFeed
{
    int GetSharePrice(string company);
}

public class StockAnalyzer
{
    private IStockFeed stockFeed;
    public StockAnalyzer(IStockFeed feed)
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

```csharp
analyzer = new StockAnalyzer(new StockFeed());
```

Bu bağlantıyı gerçekleştirmede daha esnek bir yol vardır. Örneğin, StockAnalyzer, IStockFeed, farklı koşullarda farklı uygulamaları oluşturabileceğiniz factory nesnesi kabul edemedi.

### <a name="generate-stubs"></a>Saptamalar oluştur

Test etmek istediğiniz sınıfı kullandığı diğer bileşenlerden ayırdınız. Uygulama yapmanın yanı sıra güçlü ve esnek, bağlantıyı kesmenize izin veren bileşen arayüzlerinin test amaçlı uygulamalarını saptama testteki bağlanmanıza olanak sağlar.

Her zamanki şekilde sınıflar gibi saptamaları basitçe yazabilirsiniz. Ancak Microsoft Fakes her test için en uygun saptama oluşturmak için daha dinamik bir yol sağlar.

Saptamalar kullanmak için saptama türleri arabirimi tanımlarından oluşturmanız gerekir.

#### <a name="add-a-fakes-assembly"></a>Sahte Montaj Ekle

1. **Çözüm Gezgini'nde,** birim test projenizin **Başvurularını**genişletin.

   Visual Basic'te çalışıyorsanız, **Başvurudüğümünü** görmek için **Çözüm Gezgini** araç çubuğundaki **Tüm Dosyaları Göster'i** seçin.

2. Saptamaları oluşturmak istediğiniz arabirim tanımlarını içeren derlemeyi seçin.

3. Kısayol menüsünde **Sahte Derleme Ekle'yi**seçin.

### <a name="write-your-test-with-stubs"></a>Saptamalarla test yazma

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

Buradaki özel sihir sınıfıdır. `StubIStockFeed` Başvurulan derlemedeki her genel tür için Microsoft Fakes mekanizması saptama sınıfı oluşturur. Saplama sınıfının adı, " önek olarak "`Fakes.Stub`ile arabirimin adından türetilmiş ve parametre türü adları eklenir.

Saptamalar ayrıca olaylar ve genel yöntemlerle ilgili olarak özellik okuyucu ve ayarlayıcılar için oluşturulur.

### <a name="verify-parameter-values"></a>Parametre değerlerini doğrulama

Bileşeniniz başka bir bileşen için çağrı yaptığında, doğrulayabilirsiniz, doğru değerleri geçirir. Bir onaylama işlemini saptamaya yerleştirebilirsiniz veya değer depolayabilir ve testin ana gövdesini de doğrulayabilirsiniz. Örnek:

```csharp
[TestClass]
class TestMyComponent
{
    [TestMethod]
    public void TestVariableContosoPrice()
    {
        // Arrange:
        int priceToReturn = 345;
        string companyCodeUsed = "";
        var componentUnderTest = new StockAnalyzer(new StockAnalysis.Fakes.StubIStockFeed()
            {
               GetSharePriceString = (company) =>
                  {
                     // Store the parameter value:
                     companyCodeUsed = company;
                     // Return the value prescribed by this test:
                     return priceToReturn;
                  };
            };

        // Act:
        int actualResult = componentUnderTest.GetContosoPrice();

        // Assert:
        // Verify the correct result in the usual way:
        Assert.AreEqual(priceToReturn, actualResult);

        // Verify that the component made the correct call:
        Assert.AreEqual("COOO", companyCodeUsed);
    }
...
}
```

```vb
<TestClass()> _
Class TestMyComponent
    <TestMethod()> _
    Public Sub TestVariableContosoPrice()
        ' Arrange:
        Dim priceToReturn As Integer = 345
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

## <a name="stubs-for-different-kinds-of-type-members"></a>Tür üyelerinin farklı türleri için saptamalar

### <a name="methods"></a>Yöntemler

Örnekte açıklandığı gibi yöntemler saptama sınıfının bir örneği için temsilci ekleyerek tamamlanmamış. Saptama türünün adı yöntemi ve parametreleri adlarından türetilir. Örneğin, aşağıdaki `IMyInterface` arayüz ve `MyMethod`yöntem göz önüne alındığında:

```csharp
// application under test
interface IMyInterface
{
    int MyMethod(string value);
}
```

Biz her zaman `MyMethod` 1 döndürür bir saplama eklemek:

```csharp
// unit test code
var stub = new StubIMyInterface ();
stub.MyMethodString = (value) => 1;
```

Bir işlev için saplama sağlamazsanız, Fakes döndürme türünün varsayılan değerini döndüren bir işlev oluşturur. Sayılar için varsayılan değer 0 ve sınıf `null` türleri için (C#) veya `Nothing` (Visual Basic) değeridir.

### <a name="properties"></a>Özellikler

Özellik alıcılar ve ayarlayıcılar, ayrı temsilciler olarak sunulur ve ayrı ayrı saptanmış olabilirler. Örneğin, aşağıdakilerin `Value` özelliğini `IMyInterface`göz önünde bulundurun:

```csharp
// code under test
interface IMyInterface
{
    int Value { get; set; }
}
```

Otomatik özelliği simüle `Value` etmek için vericiye ve ayarlayıcıya temsilciler ekliyoruz:

```csharp
// unit test code
int i = 5;
var stub = new StubIMyInterface();
stub.ValueGet = () => i;
stub.ValueSet = (value) => i = value;
```

Bir özelliğin ayarlayıcısı veya getter'ı için saplama yöntemleri sağlamazsanız, Fakes, saplama özelliğinin basit bir değişken gibi çalışması için değerleri depolayan bir saplama oluşturur.

### <a name="events"></a>Olaylar

Olaylar, temsilci alanları olarak sunulur. Sonuç olarak herhangi bir saptama olayı, olay yedekleme alanını çağırarak basitçe yükseltilebilir. Saplamak için aşağıdaki arabirimi ele alalım:

```csharp
// code under test
interface IWithEvents
{
    event EventHandler Changed;
}
```

`Changed` Etkinliği yükseltmek için, sadece destek temsilcisini çağırırız:

```csharp
// unit test code
  var withEvents = new StubIWithEvents();
  // raising Changed
  withEvents.ChangedEvent(withEvents, EventArgs.Empty);
```

### <a name="generic-methods"></a>Genel yöntemler

Yöntemin istenilen her anlık kullanılabilirliği için bir temsilci sağlayarak genel yöntemleri saplamak mümkündür. Örneğin, aşağıda verilen arayüz genel yöntem içerir:

```csharp
// code under test
interface IGenericMethod
{
    T GetValue<T>();
}
```

`GetValue<int>` Anlık bir test yazabilirsiniz:

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

Kod başka bir `GetValue<T>` anlık la birlikte çağrılsaydı, saplama sadece davranışı çağırır.

### <a name="stubs-of-virtual-classes"></a>Sanal sınıf saptamaları

Önceki örneklerde saptamalar arabirimlerden üretilmedi. Sanal veya özet üyeler bir sınıftan saptamalar da oluşturabilir. Örnek:

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

Bu sınıftan oluşturulan saplamada, temsilci yöntemlerini `DoVirtual()`ve `DoConcrete()`, ama değil' i `DoAbstract()` ayarlayabilirsiniz.

```csharp
// unit test
  var stub = new Fakes.MyClass();
  stub.DoAbstractString = (x) => { Assert.IsTrue(x>0); };
  stub.DoVirtualInt32 = (n) => 10 ;
```

Sanal bir yöntem için temsilci belirtmezseniz, Fakes ya da varsayılan davranışı sağlayabilir veya temel sınıf yöntemi çağırabilirsiniz. Temel yöntemin çağrılması `CallBase` için özelliği ayarlayın:

```csharp
// unit test code
var stub = new Fakes.MyClass();
stub.CallBase = false;
// No delegate set - default delegate:
Assert.AreEqual(0, stub.DoVirtual(1));

stub.CallBase = true;
// No delegate set - calls the base:
Assert.AreEqual(43,stub.DoVirtual(1));
```

## <a name="debug-stubs"></a>Hata ayıklama saplamaları

Saptama türleri, yumuşak bir hata ayıklama deneyimini sağlamak üzere tasarlanmıştır. Varsayılan olarak, hata ayıklayıcı herhangi oluşturulan bir kod üzerinde adım adım ilerler, bu nedenle saptamaya eklenmiş olan özel üye uygulamalarının içine doğrudan atlar.

## <a name="stub-limitations"></a>Saptama sınırlamaları

- İşaretçileri içeren yöntem imzaları desteklenmez.

- Saplama türleri sanal yöntem gönderimine dayandığından, mühürlü sınıflar veya statik yöntemler saplandırılamaz. Bu gibi durumlarda, [uygulamanızı birim testi için diğer derlemelerden yalıtmak için Kullanım şimlerinde](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) açıklandığı şekilde şim türlerini kullanın

## <a name="change-the-default-behavior-of-stubs"></a>Saplamaların varsayılan davranışını değiştirme

Oluşturulan her saplama türü arabirimin bir `IStubBehavior` `IStub.InstanceBehavior` örneğini (özellik aracılığıyla) tutar. Hiç eklenmemiş özel temsilci ile üye istemci çağrıları olarak adlandırılır. Davranış ayarlanmadıysa, `StubsBehaviors.Current` özellik tarafından döndürülen örneği kullanır. Varsayılan olarak, bu özellik bir özel `NotImplementedException` durum atan bir davranış döndürür.

Davranış, `InstanceBehavior` özelliği herhangi bir saplama örneğine ayarlayarak herhangi bir zamanda değiştirilebilir. Örneğin, aşağıdaki parçacık hiçbir şey olmayan veya iade türünün varsayılan değerini döndüren bir davranışı değiştirir: `default(T)`:

```csharp
// unit test code
var stub = new StubIFileSystem();
// return default(T) or do nothing
stub.InstanceBehavior = StubsBehaviors.DefaultValue;
```

Davranış, `StubsBehaviors.Current` özelliği ayarlayarak davranışın ayarlanamayan tüm saplama nesneleri için genel olarak değiştirilebilir:

```csharp
// Change default behavior for all stub instances
// where the behavior has not been set.
StubBehaviors.Current = BehavedBehaviors.DefaultValue;
```

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Fakes ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
