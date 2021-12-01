---
title: Test için uygulamanın parçalarını yalıtmak için saplamaları kullanma
description: Test sırasında başka bir bileşenin yerini alan küçük bir kod parçası olan saplama hakkında bilgi edinmek. Saplama kullanmak tutarlı sonuçlar döndürür.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: a74b4064d73130720b1e218d7e51347165b584ea
ms.sourcegitcommit: 263703af9c4840e0e0876aa99df6dd7455c43519
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2021
ms.locfileid: "133387474"
---
# <a name="use-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing"></a>Birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma

*Saplama* türleri, test etmekte Microsoft Fakes çağıran diğer bileşenlerden kolayca yalıtmamanizi sağlayan Microsoft Fakes çerçevesinin sağladığı teknolojilerden birisidir. Bir saplama test sırasında başka bir bileşenin yer aldığı kodun küçük bir parçasıdır. Bir saplama kullanmanın faydası testi yazmanızı kolaylaştırması, tutarlı sonuçlar döndürmesidir. Ve diğer bileşenleri henüz çalışmıyor olsa bile, testleri çalıştırabilirsiniz.

Genel bakış ve hızlı başlangıç kılavuzu için bkz. Fakes ile [test altındaki kodu yalıtma Microsoft Fakes.](../test/isolating-code-under-test-with-microsoft-fakes.md)

Saptamalar kullanmak için bileşen yazmalısınız böylece sınıfları değil uygulamanın başka bölümüne başvuran yalnızca arabirimleri kullanır. Diğer bölüme nazaran daha az değişiklik gerektiren bir bölümde değişiklik yaptığından bu iyi bir tasarım uygulamasıdır. Test etmek için gerçek bir bileşen yerine saplama kullanmanıza olanak tanır.

Diyagramda, StockAnalyzer bileşeni test etmek istediğimiz bir bileşendir. Normal olarak, başka bir bileşen, RealStockFeed kullanır. Ancak RealStockFeed her defasında StockAnalyzer test etmeyi zorlaştıran yöntemlerinin çağırdığı farklı sonuçlar döndürür.  Sınama sırasında StubStockFeed gibi farklı bir sınıf ile değiştiririz.

![Gerçek ve Saplama sınıfları tek bir arabirime uyum sağlar.](../test/media/fakesinterfaces.png)

Saplamalar bu yolla kodunuzun yapısına güveneceğinden genellikle saplamaları başka bir uygulamanın bir bölümünü ayırmak için kullanırsınız. Denetiminiz altında yer alan diğer derlemelerden (örneğin,System.dll) yalıtmak için normalde dolgular kullanırnız. ** Bkz. [Birim testi için uygulamanızı diğer derlemelerden yalıtmak için dolgular kullanma.](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

## <a name="how-to-use-stubs"></a>Saptamalar nasıl kullanılır?

### <a name="design-for-dependency-injection"></a>Tasarım için bağımlılık ekleme

Saptamaları kullanmak için uygulamanızın farklı bileşenlerini değil birbirlerine bağımlı ancak arabirim tanımlarının yalnızca bağımlı olmasını sağlamak için tasarlanır. Derleme zamanında bağlanmak yerine, bileşenler çalışma zamanında bağlıdır. Bu model yazılımın güncellemesinin güçlü ve kolay yapılmasına yardımcı olur çünkü değişiklikler bileşen sınırları boyunca yayılmaz. Saplamalar kullanmasanız bile bunu takip etmenizi öneririz. Yeni kod yazıyorsanız bağımlılık ekleme desenini [kolayca takip](https://en.wikipedia.org/wiki/Dependency_injection) edin. Varolan yazılım için testler yazıyorsanız, yeniden düzenlemeniz gerekebilir. Pratik olursa, yerine dolgu verileri kullanmayı düşünebilirsiniz.

Bu tartışmaya diyagramda yer alan motivasyon örneğiyle başlayalım. Sınıf StockAnalyzer fiyatları paylaşmayı okur ve bazı ilginç sonuçlar üretir. Test etmek istediğimiz bazı ortak yöntemler vardır. Basit tutmak için bu yöntemlerden birini( belirli bir paylaşımın geçerli fiyatını rapor eden çok basit bir yönteme) göz atacağız. Bu yöntemin bir birim testini yazmak istiyoruz. Testin ilk taslağı şöyledir:

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

StockAnalyzer tarafından kullanılan hala geliştirilmekte olan StockFeed bileşeninde başka bir sorun olabilir. Test altındaki yönteminin kodunun ilk taslağı şöyledir:

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

Uygulamanıza ilişkin herhangi bir bileşenin kodu hiçbir zaman bildirimde veya deyimde başka bir bileşende açıkça bir sınıfa `new` başvurmaması gerekir. Bunun yerine, değişkenler ve parametreler arabirimleriyle bildirilmesi gerekir. Bileşen örnekleri yalnızca bileşenin kapsayıcısı tarafından oluşturulacak.

- "Bileşen" olarak, birlikte geliştirdiğiniz ve güncelleştiren bir sınıf veya sınıf grubu anlamına geldik. Genellikle, bir bileşen Visual Studio projesindeki koddur. Aynı anda güncelleştirilen sınıfları tek bir bileşen içinde çözümlemek daha az önemlidir.

- Ayrıca bileşenlerinizi, bileşenleriniziSystem.dllgibi görece kararlı bir platformun *sınıflarındanSystem.dll.* Bu sınıfların arabirimlerini yazmak kodunuzu dağıtabilir.

Aşağıdakine benzer bir arabirim kullanarak StockAnalyzer kodunu StockFeed'den çözebilirsiniz:

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

Test etmek istediğiniz sınıfı, kullandığı diğer bileşenlerden ayranı. Uygulama yapmanın yanı sıra güçlü ve esnek, bağlantıyı kesmenize izin veren bileşen arayüzlerinin test amaçlı uygulamalarını saptama testteki bağlanmanıza olanak sağlar.

Her zamanki şekilde sınıflar gibi saptamaları basitçe yazabilirsiniz. Ancak Microsoft Fakes her test için en uygun saptama oluşturmak için daha dinamik bir yol sağlar.

Saptamalar kullanmak için saptama türleri arabirimi tanımlarından oluşturmanız gerekir.

#### <a name="add-a-fakes-assembly"></a>Fakes Derlemesi Ekleme

1. Içinde **Çözüm Gezgini**, 
    - Daha eski bir .NET Framework Project (SDK stili olmayan), birim testi projenizin **Başvurular düğümünü** genişletin.
    ::: moniker range=">=vs-2019"
    - .NET Framework, .NET Core veya .NET 5.0 ve sonraki bir sürümü hedef alan  SDK stili bir proje için Bağımlılıklar düğümünü genişleterek Derlemeler, Projeler veya Paketler altında sahtesini yapmak için derlemeyi **bulun.**
    ::: moniker-end
    - Visual Basic'da çalışıyorsanız **Başvurular** düğümünü görmek için **Çözüm Gezgini** araç çubuğunda Tüm **Dosyaları Göster'i** seçin.

2. Dolgu oluşturmak istediğiniz sınıf tanımlarını içeren derlemeyi seçin. Örneğin, **DateTime'ı** dolgu olarak eklemek için **System.dll.**

3. Kısayol menüsünde Derleme **ekle'yi Fakes seçin.**

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

Buradaki özel sihirli parça `StubIStockFeed` sınıfıdır. Başvurulan derlemedeki her genel tür için Microsoft Fakes mekanizması saptama sınıfı oluşturur. Saplama sınıfının adı, ön ek olarak " " ve eklenen parametre türü adları ile birlikte `Fakes.Stub` arabirimin adlarından türetilmiştir.

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

Örnekte açıklandığı gibi yöntemler saptama sınıfının bir örneği için temsilci ekleyerek tamamlanmamış. Saptama türünün adı yöntemi ve parametreleri adlarından türetilir. Örneğin, aşağıdaki arabirim ve `IMyInterface` yöntemine `MyMethod` göre:

```csharp
// application under test
interface IMyInterface
{
    int MyMethod(string value);
}
```

her zaman `MyMethod` 1 döndüren bir saplama iliştireriz:

```csharp
// unit test code
var stub = new StubIMyInterface ();
stub.MyMethodString = (value) => 1;
```

Bir işlev için saplama sağlasanız Fakes türün varsayılan değerini döndüren bir işlev üretir. Sayılar için varsayılan değer 0'dır ve sınıf türleri için `null` (C#) veya `Nothing` (Visual Basic).

### <a name="properties"></a>Özellikler

Özellik alıcılar ve ayarlayıcılar, ayrı temsilciler olarak sunulur ve ayrı ayrı saptanmış olabilirler. Örneğin, özelliğini `Value` `IMyInterface` düşünün:

```csharp
// code under test
interface IMyInterface
{
    int Value { get; set; }
}
```

Bir otomatik özelliğin benzetimini yapmak için getter ve `Value` setter'a temsilciler eklemektedir:

```csharp
// unit test code
int i = 5;
var stub = new StubIMyInterface();
stub.ValueGet = () => i;
stub.ValueSet = (value) => i = value;
```

Bir özelliğin ayarıcısı veya alıcısı için saplama yöntemleri sağlamıyorsanız, Fakes saplama özelliğinin basit bir değişken gibi çalışması için değerleri depolar bir saplama üretir.

### <a name="events"></a>Ekinlikler

Olaylar, temsilci alanları olarak sunulur. Sonuç olarak herhangi bir saptama olayı, olay yedekleme alanını çağırarak basitçe yükseltilebilir. Saplama için aşağıdaki arabirimi düşünebilirsiniz:

```csharp
// code under test
interface IWithEvents
{
    event EventHandler Changed;
}
```

Olayı yükseltmek `Changed` için yalnızca destek temsilcisini çağırıriz:

```csharp
// unit test code
  var withEvents = new StubIWithEvents();
  // raising Changed
  withEvents.ChangedEvent(withEvents, EventArgs.Empty);
```

### <a name="generic-methods"></a>Genel yöntemler

Yöntemin istenen her örneği için bir temsilci sağlayarak genel yöntemleri saplama mümkündür. Örneğin, aşağıda verilen arayüz genel yöntem içerir:

```csharp
// code under test
interface IGenericMethod
{
    T GetValue<T>();
}
```

Örneği saplama testi `GetValue<int>` yazabilirsiniz:

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

Kod başka bir `GetValue<T>` örnekle çağrılsa, saplama yalnızca davranışı çağırabilir.

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

Bu sınıftan oluşturulan saplamada ve için temsilci yöntemleri ayarlayın, ancak `DoAbstract()` `DoVirtual()` `DoConcrete()` ayarlanmaz.

```csharp
// unit test
  var stub = new Fakes.MyClass();
  stub.DoAbstractString = (x) => { Assert.IsTrue(x>0); };
  stub.DoVirtualInt32 = (n) => 10 ;
```

Sanal bir yöntem için temsilci belirtmezseniz, Fakes ya da varsayılan davranışı sağlayabilir veya temel sınıf yöntemi çağırabilirsiniz. Temel yöntemin çağrılmalarını yapmak için özelliğini `CallBase` ayarlayın:

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

- İşaretçileri olan yöntem imzaları desteklenmiyor.

- Saplama türleri sanal yöntem gönderme yöntemine bağlı olduğundan korumalı sınıflar veya statik yöntemler saplamaz. Bu gibi durumlarda, Birim testi için diğer derlemelerden uygulamalarınızı yalıtmak için dolguları kullanma konusunda açıklandığı [gibi dolgu türlerini kullanın](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

## <a name="change-the-default-behavior-of-stubs"></a>Saplamaların varsayılan davranışını değiştirme

Oluşturulan her saplama türü arabirimin bir örneğini `IStubBehavior` içerir (özelliği `IStub.InstanceBehavior` aracılığıyla). Hiç eklenmemiş özel temsilci ile üye istemci çağrıları olarak adlandırılır. Davranış ayarlanmazsa özelliği tarafından döndürülen örneği `StubsBehaviors.Current` kullanır. Varsayılan olarak, bu özellik özel durum döndüren bir davranış `NotImplementedException` döndürür.

Herhangi bir saplama örneğinde özelliği ayar tarafından `InstanceBehavior` herhangi bir zamanda davranış değiştirilebilir. Örneğin, aşağıdaki kod parçacığı hiçbir şey yapmadı veya dönüş türünün varsayılan değerini döndüren bir davranışı `default(T)` değiştirir:

```csharp
// unit test code
var stub = new StubIFileSystem();
// return default(T) or do nothing
stub.InstanceBehavior = StubsBehaviors.DefaultValue;
```

Davranışın ayarlandırarak davranış ayarlanmaz tüm saplama nesneleri için genel olarak da `StubsBehaviors.Current` değiştirilebilir:

```csharp
// Change default behavior for all stub instances
// where the behavior has not been set.
StubBehaviors.Current = BehavedBehaviors.DefaultValue;
```

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Fakes ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
