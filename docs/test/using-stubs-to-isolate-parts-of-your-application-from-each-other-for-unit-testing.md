---
title: Uygulama parçalarını test için yalıtmak üzere saplamalar kullanma
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 268cfaa0a5df458ae529f5f2d369dc157ef64548
ms.sourcegitcommit: f2bb3286028546cbd7f54863b3156bd3d65c55c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93325969"
---
# <a name="use-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing"></a>Birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma

*Saplama türleri* , Microsoft Fakes çerçevesinin, çağırdığı diğer bileşenlerden test ettiğiniz bir bileşeni kolayca ayırmanızı sağlamak için sağladığı iki teknolojiden biridir. Bir saplama test sırasında başka bir bileşenin yer aldığı kodun küçük bir parçasıdır. Bir saplama kullanmanın faydası testi yazmanızı kolaylaştırması, tutarlı sonuçlar döndürmesidir. Ve diğer bileşenleri henüz çalışmıyor olsa bile, testleri çalıştırabilirsiniz.

Fakes 'e genel bakış ve hızlı başlangıç kılavuzu için bkz. [Microsoft Fakes ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md).

Saptamalar kullanmak için bileşen yazmalısınız böylece sınıfları değil uygulamanın başka bölümüne başvuran yalnızca arabirimleri kullanır. Diğer bölüme nazaran daha az değişiklik gerektiren bir bölümde değişiklik yaptığından bu iyi bir tasarım uygulamasıdır. Test etmek için gerçek bir bileşen yerine saplama kullanmanıza olanak tanır.

Diyagramda, StockAnalyzer bileşeni test etmek istediğimiz bir bileşendir. Normal olarak, başka bir bileşen, RealStockFeed kullanır. Ancak RealStockFeed her defasında StockAnalyzer test etmeyi zorlaştıran yöntemlerinin çağırdığı farklı sonuçlar döndürür.  Sınama sırasında StubStockFeed gibi farklı bir sınıf ile değiştiririz.

![Gerçek ve saplama sınıfları bir arabirimle uyumlu.](../test/media/fakesinterfaces.png)

Saplamalar bu yolla kodunuzun yapısına güveneceğinden genellikle saplamaları başka bir uygulamanın bir bölümünü ayırmak için kullanırsınız. Denetiminiz altında olmayan diğer derlemelerden yalıtmak için, *System.dll* gibi Normalde, normal olarak shims kullanırsınız. [Birim testi için uygulamanızı diğer derlemelerden yalıtmak için bkz. dolgular kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="how-to-use-stubs"></a>Saptamalar nasıl kullanılır?

### <a name="design-for-dependency-injection"></a>Tasarım için bağımlılık ekleme

Saptamaları kullanmak için uygulamanızın farklı bileşenlerini değil birbirlerine bağımlı ancak arabirim tanımlarının yalnızca bağımlı olmasını sağlamak için tasarlanır. Derleme zamanında bağlanmak yerine, bileşenler çalışma zamanında bağlıdır. Bu model yazılımın güncellemesinin güçlü ve kolay yapılmasına yardımcı olur çünkü değişiklikler bileşen sınırları boyunca yayılmaz. Saplamalar kullanmıyor olsanız bile bunu yapmanızı öneririz. Yeni kod yazıyorsanız, [bağımlılık ekleme](https://en.wikipedia.org/wiki/Dependency_injection) düzeninin izlenmesi kolaydır. Varolan yazılım için testler yazıyorsanız, yeniden düzenlemeniz gerekebilir. Pratik olursa, yerine dolgu verileri kullanmayı düşünebilirsiniz.

Bu tartışmayı diyagramda bir mücadele örneği ile başlaalım. Sınıf StockAnalyzer fiyatları paylaşmayı okur ve bazı ilginç sonuçlar üretir. Test etmek istediğimiz bazı ortak yöntemler vardır. Şeyleri basit tutmak için, belirli bir paylaşımın geçerli fiyatını raporlayan çok basit bir yöntem olan bu yöntemlerden birine göz atalım. Bu yöntemin bir birim testini yazmak istiyoruz. Bir testin ilk taslağı aşağıda verilmiştir:

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

StockAnalyzer tarafından kullanılan hala geliştirilmekte olan StockFeed bileşeninde başka bir sorun olabilir. Test edilen yöntemin ilk taslağı aşağıda verilmiştir:

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

Uygulamanızın herhangi bir bileşeninin kodu asla açıkça bir bildirimde veya bir ifadede başka bir bileşendeki bir sınıfa başvurmamalıdır `new` . Bunun yerine, değişkenler ve parametreler arabirimleriyle bildirilmesi gerekir. Bileşen örnekleri yalnızca bileşenin kapsayıcısı tarafından oluşturulmalıdır.

- "Bileşen" olarak, bir sınıf veya geliştirmekte ve güncelleştirmekte olduğunuz bir sınıf grubu anlamına geliyor. Genellikle, bir bileşen Visual Studio projesindeki koddur. Aynı anda güncelleştirildiğinden, sınıfları bir bileşen içinde ayırmak daha az önemlidir.

- Ayrıca, *System.dll* gibi görece sağlam bir platformun sınıflarından bileşenlerinizi ayırmak de önemli değildir. Bu sınıfların arabirimlerini yazmak kodunuzu dağıtabilir.

Aşağıdaki gibi bir arabirim kullanarak StockAnalyzer kodunu StockFeed ' dan ayırarak kullanabilirsiniz:

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

Test etmek istediğiniz sınıfı, kullandığı diğer bileşenlerden ayırdık. Uygulama yapmanın yanı sıra güçlü ve esnek, bağlantıyı kesmenize izin veren bileşen arayüzlerinin test amaçlı uygulamalarını saptama testteki bağlanmanıza olanak sağlar.

Her zamanki şekilde sınıflar gibi saptamaları basitçe yazabilirsiniz. Ancak Microsoft Fakes her test için en uygun saptama oluşturmak için daha dinamik bir yol sağlar.

Saptamalar kullanmak için saptama türleri arabirimi tanımlarından oluşturmanız gerekir.

#### <a name="add-a-fakes-assembly"></a>Fakes derlemesi Ekle

1. **Çözüm Gezgini** , 
    - Daha eski bir .NET Framework projesi (SDK olmayan stil) için, birim testi projenizin **Başvurular** düğümünü genişletin.
    ::: moniker range=">=vs-2019"
    - .NET Framework veya .NET Core 'u hedefleyen SDK stili bir proje için, **derlemeler** , **Projeler** veya **paketler** altında taklit etmek istediğiniz derlemeyi bulmak için **Bağımlılıklar** düğümünü genişletin.
    ::: moniker-end
    - Visual Basic ' de çalışıyorsanız, **Başvurular** düğümünü görmek için **Çözüm Gezgini** araç çubuğunda **tüm dosyaları göster** ' i seçin.

2. Dolgu oluşturmak istediğiniz sınıf tanımlarını içeren derlemeyi seçin. Örneğin, **TarihSaat** dolgusu istiyorsanız **System.dll** ' yi seçin.

3. Kısayol menüsünde **Fakes derlemesi Ekle** ' yi seçin.

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

Burada Magic 'in özel parçası sınıftır `StubIStockFeed` . Başvurulan derlemedeki her genel tür için Microsoft Fakes mekanizması saptama sınıfı oluşturur. Saplama sınıfının adı, " `Fakes.Stub` " öneki ve parametre türü adları eklenmiş şekilde arabirimin adından türetilir.

Saptamalar ayrıca olaylar ve genel yöntemlerle ilgili olarak özellik okuyucu ve ayarlayıcılar için oluşturulur.

### <a name="verify-parameter-values"></a>Parametre değerlerini doğrulama

Bileşeniniz başka bir bileşen için çağrı yaptığında, doğrulayabilirsiniz, doğru değerleri geçirir. Bir onaylama işlemini saptamaya yerleştirebilirsiniz veya değer depolayabilir ve testin ana gövdesini de doğrulayabilirsiniz. Örneğin:

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

Örnekte açıklandığı gibi yöntemler saptama sınıfının bir örneği için temsilci ekleyerek tamamlanmamış. Saptama türünün adı yöntemi ve parametreleri adlarından türetilir. Örneğin, aşağıdaki `IMyInterface` arabirimi ve yöntemi verildiğinde `MyMethod` :

```csharp
// application under test
interface IMyInterface
{
    int MyMethod(string value);
}
```

`MyMethod`Her zaman 1 döndüren için bir saplama ekledik:

```csharp
// unit test code
var stub = new StubIMyInterface ();
stub.MyMethodString = (value) => 1;
```

Bir işlev için saplama sağlamazsanız, Fakes, dönüş türünün varsayılan değerini döndüren bir işlev oluşturur. Sayılar için varsayılan değer 0 ' dır ve sınıf türleri için `null` (C#) veya `Nothing` (Visual Basic).

### <a name="properties"></a>Özellikler

Özellik alıcılar ve ayarlayıcılar, ayrı temsilciler olarak sunulur ve ayrı ayrı saptanmış olabilirler. Örneğin, `Value` öğesinin özelliğini göz önünde bulundurun `IMyInterface` :

```csharp
// code under test
interface IMyInterface
{
    int Value { get; set; }
}
```

Otomatik özelliğin benzetimini yapmak için alıcı ve ayarlayıcısına temsilciler iliştirdik `Value` :

```csharp
// unit test code
int i = 5;
var stub = new StubIMyInterface();
stub.ValueGet = () => i;
stub.ValueSet = (value) => i = value;
```

Bir özelliğin ayarlayıcısı ya da alıcısı için saplama yöntemleri sağlamazsanız, Fakes, saplama özelliğinin basit bir değişken gibi çalışması için değerleri depolayan bir saplama oluşturur.

### <a name="events"></a>Olaylar

Olaylar, temsilci alanları olarak sunulur. Sonuç olarak herhangi bir saptama olayı, olay yedekleme alanını çağırarak basitçe yükseltilebilir. Saplama için aşağıdaki arabirimi ele alalım:

```csharp
// code under test
interface IWithEvents
{
    event EventHandler Changed;
}
```

Olayı yükseltmek için `Changed` , yalnızca yedekleme temsilcisini çağırdık:

```csharp
// unit test code
  var withEvents = new StubIWithEvents();
  // raising Changed
  withEvents.ChangedEvent(withEvents, EventArgs.Empty);
```

### <a name="generic-methods"></a>Genel yöntemler

Yöntemin her istenen örneği için bir temsilci sağlayarak genel yöntemleri saplama mümkündür. Örneğin, aşağıda verilen arayüz genel yöntem içerir:

```csharp
// code under test
interface IGenericMethod
{
    T GetValue<T>();
}
```

Örnek oluşturma için saplamalı bir test yazabilirsiniz `GetValue<int>` :

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

Kod `GetValue<T>` diğer bir örnek oluşturma ile çağrılıyorsa, saplama yalnızca davranışı çağırır.

### <a name="stubs-of-virtual-classes"></a>Sanal sınıf saptamaları

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

Bu sınıftan oluşturulan saplamaya, ve için temsilci yöntemleri ayarlayabilirsiniz `DoAbstract()` `DoVirtual()` , ancak kullanamazsınız `DoConcrete()` .

```csharp
// unit test
  var stub = new Fakes.MyClass();
  stub.DoAbstractString = (x) => { Assert.IsTrue(x>0); };
  stub.DoVirtualInt32 = (n) => 10 ;
```

Sanal bir yöntem için temsilci belirtmezseniz, Fakes ya da varsayılan davranışı sağlayabilir veya temel sınıf yöntemi çağırabilirsiniz. Temel yöntemin çağrılması için `CallBase` özelliği ayarlayın:

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

- İşaretçilerle yöntem imzaları desteklenmez.

- Saplama türleri sanal yöntem gönderimi kullandığından Sealed sınıflar veya statik yöntemler saplaması olamaz. Bu tür durumlarda, [birim testi için uygulamanızı diğer derlemelerden yalıtmak üzere](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md) dolgu türlerini, parça kullanma bölümünde açıklandığı şekilde kullanın

## <a name="change-the-default-behavior-of-stubs"></a>Saplamalarının varsayılan davranışını değiştirme

Oluşturulan her saplama türü arabirimin bir örneğini barındırır `IStubBehavior` ( `IStub.InstanceBehavior` özelliği aracılığıyla). Hiç eklenmemiş özel temsilci ile üye istemci çağrıları olarak adlandırılır. Davranış ayarlanmamışsa, özelliği tarafından döndürülen örneği kullanır `StubsBehaviors.Current` . Varsayılan olarak, bu özellik özel durum oluşturan bir davranış döndürür `NotImplementedException` .

Bu davranış herhangi bir saplama örneğindeki özelliği ayarlanarak herhangi bir zamanda değiştirilebilir `InstanceBehavior` . Örneğin, aşağıdaki kod parçacığı hiçbir şey yapan veya dönüş türünün varsayılan değerini döndüren bir davranışı değiştirir: `default(T)` :

```csharp
// unit test code
var stub = new StubIFileSystem();
// return default(T) or do nothing
stub.InstanceBehavior = StubsBehaviors.DefaultValue;
```

Bu davranış, özelliği ayarlanarak davranışın ayarlanmayan tüm saplama nesneleri için genel olarak da değiştirilebilir `StubsBehaviors.Current` :

```csharp
// Change default behavior for all stub instances
// where the behavior has not been set.
StubBehaviors.Current = BehavedBehaviors.DefaultValue;
```

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Fakes ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
