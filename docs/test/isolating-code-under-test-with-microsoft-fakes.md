---
title: Microsoft Fakes ile Test Edilen Kodu Yalıtma
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- VB
- CSharp
ms.openlocfilehash: 662a61bf97e1726892b877dc79a0ef98340a34ec
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566910"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Microsoft Fakes ile test edilen kodu yalıtma

Microsoft Fakes, uygulamanın diğer bölümlerini *saplamalar* veya *şimlerle*değiştirerek test ettiğiniz kodu yalıtmanıza yardımcı olur. Bunlar, testlerinizin denetimi altında olan küçük kod parçalarıdır. Kodunuzu sınama için yalıttığınız zaman, sınama başarısız olduğunda nedeninin başka bir yerde değil, tam da orada olduğunu bileceksiniz. Uygulamanın diğer parçaları çalışmıyor olsa bile, saptamalar ve dolgular kodunuzu test etmenize olanak sağlar.

Fakes iki türde olabilir:

- [Saplama,](#get-started-with-stubs) bir sınıfın yerine aynı arabirimi uygulayan küçük bir yedek le yer değiştirir.  Saptamalar kullanmak için uygulamanızı her bir bileşenin diğer bileşenlere değil yalnızca arabirimlere bağlı olacak şekilde tasarlamanız gerekir. ("Bileşen" ifadesiyle, birlikte tasarlanan ve güncelleştirilen ve tipik olarak bir derlemede yer alan sınıf veya sınıflardan oluşan grup kastedilmektedir.)

- [Şim,](#get-started-with-shims) uygulamanızın derlenmiş kodunu çalışma zamanında değiştirir, böylece belirli bir yöntem araması yapmak yerine testinizin sağladığı şim kodunu çalıştırAr. Shims,.NET derlemeleri gibi değiştiremeyeceğiniz derlemelere yapılan çağrıları değiştirmek için kullanılabilir.

![Sahtediğer bileşenlerin yerine](../test/media/fakes-2.png)

**Gereksinimler**

- Visual Studio Enterprise
- A .NET Framework projesi

> [!NOTE]
> - .NET Standart projeler desteklenmez.
> - Visual Studio ile profil oluşturma, Microsoft Fakes kullanan testler için kullanılamaz.

## <a name="choose-between-stub-and-shim-types"></a>Saplama ve shim türleri arasında seçim yapın
Genelde bu sınıfları aynı anda geliştirip güncelleştirdiğinizden bir Visual Studio projesini bileşen olarak kabul edebilirsiniz. Projenin çözümünüzdeki diğer projelere veya diğer derlemelere yaptığı çağrılar için saptama ve dolgu kullanmayı deneyebilirsiniz.

Genel bir kılavuzluk sağlaması için, Visual Studio çözümünüzdeki çağrılar için saptamaları ve diğer başvurulan derlemelerde çağrılar için dolgu verilerini kullanın. Bunun nedeni kendi çözümünüzde bileşenleri, saptamaların gerektirdiği şekilde arabirimleri tanımlayarak ayırmanızın iyi bir uygulama olmasıdır. Ancak *System.dll* gibi harici derlemeler genellikle ayrı arabirim tanımlarıyla sağlanmaz, bu nedenle bunun yerine şimler kullanmanız gerekir.

Diğer değerlendirmeler şunlardır:

**Performans.** Çalışma zamanında kodunuzu yeniden yazdıkları için dolgular daha yavaş çalışır. Saptamalarda bu performans düşüklüğü yoktur ve sanal yöntemler kadar hızlı ilerleyebilirler.

**Statik yöntemler, mühürlü tipler.** Arayüzleri uygulamak için yalnızca saptamalar kullanabilirsiniz. Bu nedenle saptama türleri statik yöntemler, sanal olmayan yöntemler, korumalı sanal yöntemler, korumalı türlerdeki yöntemler gibi yöntemlerle kullanılamaz.

**İç tipler.** Hem saplamalar hem de şimler, derleme özniteliği <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>kullanılarak erişilebilir hale gelen dahili türleri ile kullanılabilir.

**Özel yöntemler.** Dolgular, bir yöntem imzasındaki tüm türler görünür durumdaysa çağrıları özel yöntemlerle değiştirebilir. Saptamalar yalnızca görünür yöntemlerle değiştirilebilir.

**Arayüzler ve soyut yöntemler.** Saptamalar, test sırasında kullanılabilecek arayüzlerin ve özet yöntemlerin uygulanmalarını sağlar. Şimler arayüzleri ve soyut yöntemleri enstrüman edemez, çünkü yöntem gövdeleri yoktur.

Genel olarak saptama türlerini kod temelindeki bağımlılıkları ayırmak için kullanmanızı öneririz. Bunu bileşenleri arayüzlerin arkasına gizleyerek yapabilirsiniz. Dolgu türleri, test edilebilir API sağlamayan üçüncü taraf bileşenlerden ayırmak için kullanılabilir.

## <a name="get-started-with-stubs"></a>Saplamalar ile başlayın
Daha ayrıntılı bir açıklama [için](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)bkz.

1. **Arayüzleri enjekte edin**

     Saptamalar kullanmak için test etmek istediğiniz kodu, uygulamanızın içindeki diğer bileşende yer alan sınıflara açıkça başvurmayacak şekilde yazmanız gerekir. "Bileşen" ifadesiyle, birlikte geliştirilen ve güncellenen ve tipik olarak tek Visual Studio projesinde yer alan sınıf veya sınıflar kastedilmektedir. Değişkenler ve parametreler, arabirimler kullanılarak bildirilmelidir ve diğer bileşenlerin örnekleri iletilmeli veya fabrika kullanılarak oluşturulmalıdır. Örneğin, StockFeed uygulamadaki farklı bir bileşende bulunan bir sınıfsa bu hatalı olarak değerlendirilir:

     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`

     Bunun yerine, başka bir bileşen tarafından uygulanabilecek ve bir saptama tarafından test amaçlarıyla uygulanabilecek bir arabirim tanımlayın:

    ```csharp
    public int GetContosoPrice(IStockFeed feed) => feed.GetSharePrice("COOO");
    ```

    ```vb
    Public Function GetContosoPrice(feed As IStockFeed) As Integer
     Return feed.GetSharePrice("COOO")
    End Function

    ```

2. **Fakes Montaj ekle**

    1. **Çözüm Gezgini'nde,** test projesinin başvuru listesini genişletin. Visual Basic'te çalışıyorsanız, başvuru listesini görmek için **Tüm Dosyaları Göster'i** seçmeniz gerekir.

    2. Arabirimin (örneğin IStockFeed) tanımlandığı derleme başvurusunu seçin. Bu başvurunun kısayol menüsünde **Sahte Derleme Ekle'yi**seçin.

    3. Çözümü yeniden derleyin.

3. Testlerinizde saptama örnekleri oluşturun ve yöntemleri için kod sağlayın:

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

    Buradaki özel sihir sınıfıdır. `StubIStockFeed` Başvurulan derlemedeki her arabirim için saptama sınıfı Microsoft Fakes mekanizması oluşturur. Saplama sınıfının adı, " önek olarak "`Fakes.Stub`ile arabirimin adından türetilmiş ve parametre türü adları eklenir.

    Saptamalar ayrıca olaylar ve genel yöntemlerle ilgili olarak özellik okuyucu ve ayarlayıcılar için oluşturulur. Daha fazla bilgi için [bkz.](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

## <a name="get-started-with-shims"></a>Şimlerle başlayın
(Daha ayrıntılı bir açıklama için, [bkz.](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

Bileşeninizin aşağıdakilere `DateTime.Now`yapılan aramalar içerdiğini varsayalım:

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Gerçek sürüm uygunsuz her aramada `Now` farklı bir değer döndürür, çünkü test sırasında, özelliği shim istiyorum.

Şimleri kullanmak için uygulama kodunu değiştirmeniz veya belirli bir şekilde yazmanız gerekmez.

1. **Fakes Montaj ekle**

     **Çözüm Gezgini'nde,** birim test projenizin başvurularını açın ve sahtesini yapmak istediğiniz yöntemi içeren derlemeye başvuruyu seçin. Bu örnekte, `DateTime` sınıf *System.dll'dedir.*  Visual Basic projesindeki başvuruları görmek için **Tüm Dosyaları Göster'i**seçin.

     **Sahte Montaj Ekle'yi**seçin.

2. **ShimsContext'a şim ekleme**

    ```csharp
    [TestClass]
    public class TestClass1
    {
            [TestMethod]
            public void TestCurrentYear()
            {
                int fixedYear = 2000;

                // Shims can be used only in a ShimsContext:
                using (ShimsContext.Create())
                {
                  // Arrange:
                    // Shim DateTime.Now to return a fixed date:
                    System.Fakes.ShimDateTime.NowGet =
                    () =>
                    { return new DateTime(fixedYear, 1, 1); };

                    // Instantiate the component under test:
                    var componentUnderTest = new MyComponent();

                  // Act:
                    int year = componentUnderTest.GetTheCurrentYear();

                  // Assert:
                    // This will always be true if the component is working:
                    Assert.AreEqual(fixedYear, year);
                }
            }
    }
    ```

    ```vb
    <TestClass()> _
    Public Class TestClass1
        <TestMethod()> _
        Public Sub TestCurrentYear()
            Using s = Microsoft.QualityTools.Testing.Fakes.ShimsContext.Create()
                Dim fixedYear As Integer = 2000
                ' Arrange:
                ' Detour DateTime.Now to return a fixed date:
                System.Fakes.ShimDateTime.NowGet = _
                    Function() As DateTime
                        Return New DateTime(fixedYear, 1, 1)
                    End Function

                ' Instantiate the component under test:
                Dim componentUnderTest = New MyComponent()
                ' Act:
                Dim year As Integer = componentUnderTest.GetTheCurrentYear
                ' Assert:
                ' This will always be true if the component is working:
                Assert.AreEqual(fixedYear, year)
            End Using
        End Sub
    End Class
    ```

    Şim sınıf adları özgün tür `Fakes.Shim` adına önseki yle oluşur. Parametre adları yöntem adına eklenir. (System.Fakes için herhangi bir montaj başvurusu eklemek zorunda değilsiniz.)

Önceki örnek statik yöntem olarak bir dolgu kullanır. Örnek bir yöntem için şim `AllInstances` kullanmak için, tür adı ve yöntem adı arasına yazın:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(Başvuru için hiçbir 'System.IO.Fakes' montaj. Ad alanı, şim oluşturma işlemi tarafından oluşturulur. Ancak her zamanki gibi 'kullanma' veya 'Alma'yı kullanabilirsiniz.)

Ayrıca belirli örnekler, oluşturucular ve özellikler için dolgular oluşturabilirsiniz. Daha fazla bilgi için bkz: [Uygulamanızı birim testi için diğer derlemelerden yalıtmak için shims kullanın.](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

## <a name="in-this-section"></a>Bu bölümde
[Birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Birim testi için uygulamanızı diğer derlemelerden yalıtmak üzere dolgular kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
