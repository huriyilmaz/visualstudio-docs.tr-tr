---
title: Microsoft Fakes ile Test Edilen Kodu Yalıtma
ms.date: 06/03/2020
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- VB
- CSharp
ms.openlocfilehash: e837b1a0e9a1d8fe06342352e4eedf5ce0fa9117
ms.sourcegitcommit: f2bb3286028546cbd7f54863b3156bd3d65c55c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93325958"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Microsoft Fakes ile test edilen kodu yalıtma

Microsoft Fakes, uygulamanın diğer bölümlerini *saplamalar* *veya parçalar* ile değiştirerek test ettiğiniz kodu yalıtmanıza yardımcı olur. Bunlar, testlerinizin denetimi altında olan küçük kod parçalarıdır. Kodunuzu sınama için yalıttığınız zaman, sınama başarısız olduğunda nedeninin başka bir yerde değil, tam da orada olduğunu bileceksiniz. Uygulamanın diğer parçaları çalışmıyor olsa bile, saptamalar ve dolgular kodunuzu test etmenize olanak sağlar.

Fakes iki türde olabilir:

- [Saplama](#get-started-with-stubs) , bir sınıfı aynı arabirimi uygulayan küçük bir değiştirme ile değiştirir.  Saptamalar kullanmak için uygulamanızı her bir bileşenin diğer bileşenlere değil yalnızca arabirimlere bağlı olacak şekilde tasarlamanız gerekir. ("Bileşen" ifadesiyle, birlikte tasarlanan ve güncelleştirilen ve tipik olarak bir derlemede yer alan sınıf veya sınıflardan oluşan grup kastedilmektedir.)

- Bir [Dolgu](#get-started-with-shims) , çalışma zamanında uygulamanızın derlenmiş kodunu değiştirir, böylece belirli bir yöntem çağrısını yapmak yerine, testinizin sağladığı dolgu kodunu çalıştırır. Dolgu, .NET derlemeleri gibi değiştiremeyeceğiniz Derlemelerle değiştirmek için kullanılabilir.

![Fakes diğer bileşenleri değiştirir](../test/media/fakes-2.png)

**Gereksinimler**

- Visual Studio Enterprise
- Bir .NET Framework projesi
::: moniker range=">=vs-2019"
- Visual Studio 2019 güncelleştirme 6 ' da önizlenen .NET Core ve SDK stili proje desteği ve güncelleştirme 8 ' de varsayılan olarak etkinleştirilmiştir. Daha fazla bilgi için bkz. [.NET Core ve SDK stilindeki projeler Için Microsoft Fakes](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

> [!NOTE]
> - Visual Studio ile profil oluşturma, Microsoft Fakes kullanan testler için kullanılamaz.

## <a name="choose-between-stub-and-shim-types"></a>Saplama ve dolgu türleri arasında seçim yapın
Genelde bu sınıfları aynı anda geliştirip güncelleştirdiğinizden bir Visual Studio projesini bileşen olarak kabul edebilirsiniz. Projenin çözümünüzdeki diğer projelere veya diğer derlemelere yaptığı çağrılar için saptama ve dolgu kullanmayı deneyebilirsiniz.

Genel bir kılavuzluk sağlaması için, Visual Studio çözümünüzdeki çağrılar için saptamaları ve diğer başvurulan derlemelerde çağrılar için dolgu verilerini kullanın. Bunun nedeni kendi çözümünüzde bileşenleri, saptamaların gerektirdiği şekilde arabirimleri tanımlayarak ayırmanızın iyi bir uygulama olmasıdır. Ancak *System.dll* gibi dış derlemeler ayrı arabirim tanımlarıyla sağlanmaz, bu nedenle bunun yerine dolgular kullanmanız gerekir.

Diğer değerlendirmeler şunlardır:

**Mının.** Çalışma zamanında kodunuzu yeniden yazdıkları için dolgular daha yavaş çalışır. Saptamalarda bu performans düşüklüğü yoktur ve sanal yöntemler kadar hızlı ilerleyebilirler.

**Statik yöntemler, korumalı türler.** Arayüzleri uygulamak için yalnızca saptamalar kullanabilirsiniz. Bu nedenle saptama türleri statik yöntemler, sanal olmayan yöntemler, korumalı sanal yöntemler, korumalı türlerdeki yöntemler gibi yöntemlerle kullanılamaz.

**İç türler.** Hem saplamalar hem de parçalar, derleme özniteliği kullanılarak erişilebilir hale getirilen iç türlerle birlikte kullanılabilir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> .

**Özel yöntemler.** Dolgular, bir yöntem imzasındaki tüm türler görünür durumdaysa çağrıları özel yöntemlerle değiştirebilir. Saptamalar yalnızca görünür yöntemlerle değiştirilebilir.

**Arabirimler ve soyut yöntemler.** Saptamalar, test sırasında kullanılabilecek arayüzlerin ve özet yöntemlerin uygulanmalarını sağlar. Kims, metot gövdeleri olmadığından, arabirimleri ve soyut yöntemleri görüntüleyemez.

Genel olarak saptama türlerini kod temelindeki bağımlılıkları ayırmak için kullanmanızı öneririz. Bunu bileşenleri arayüzlerin arkasına gizleyerek yapabilirsiniz. Dolgu türleri, test edilebilir API sağlamayan üçüncü taraf bileşenlerden ayırmak için kullanılabilir.

## <a name="get-started-with-stubs"></a>Saplamalarla çalışmaya başlama
Daha ayrıntılı bir açıklama için, [birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)konusuna bakın.

1. **Arabirim Ekle**

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

2. **Fakes derlemesi Ekle**

   1. **Çözüm Gezgini** , 
       - Daha eski bir .NET Framework projesi (SDK olmayan stil) için, birim testi projenizin **Başvurular** düğümünü genişletin.
       ::: moniker range=">=vs-2019"
       - .NET Framework veya .NET Core 'u hedefleyen SDK stili bir proje için, **derlemeler** , **Projeler** veya **paketler** altında taklit etmek istediğiniz derlemeyi bulmak için **Bağımlılıklar** düğümünü genişletin.
       ::: moniker-end
       - Visual Basic ' de çalışıyorsanız, **Başvurular** düğümünü görmek için **Çözüm Gezgini** araç çubuğunda **tüm dosyaları göster** ' i seçin.
   2. Dolgu oluşturmak istediğiniz sınıf tanımlarını içeren derlemeyi seçin. Örneğin, **TarihSaat** dolgusu istiyorsanız **System.dll** ' yi seçin.

   3. Kısayol menüsünde **Fakes derlemesi Ekle** ' yi seçin.

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

    Burada Magic 'in özel parçası sınıftır `StubIStockFeed` . Başvurulan derlemedeki her arabirim için saptama sınıfı Microsoft Fakes mekanizması oluşturur. Saplama sınıfının adı, arabirim adından türetilir, `Fakes.Stub` ön ek olarak "" ve parametre türü adları eklenir.

    Saptamalar ayrıca olaylar ve genel yöntemlerle ilgili olarak özellik okuyucu ve ayarlayıcılar için oluşturulur. Daha fazla bilgi için bkz. [birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

## <a name="get-started-with-shims"></a>Dolgu ile çalışmaya başlama
(Daha ayrıntılı bir açıklama için bkz. [birim testi için uygulamanızı diğer derlemelerden yalıtmak için dolgu kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).)

Bileşeninizin şu çağrıları içerdiğini varsayalım `DateTime.Now` :

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Sınama sırasında, `Now` gerçek sürüm uygun şekilde her çağrıda farklı bir değer döndürdüğünden, özelliği dolgu yapmak istersiniz.

Dolgu kullanmak için uygulama kodunu değiştirmeniz veya belirli bir şekilde yazmanız gerekmez.

1. **Fakes derlemesi Ekle**

     **Çözüm Gezgini** , birim testi projenizin başvurularını açın ve taklit etmek istediğiniz yöntemi içeren derlemenin başvurusunu seçin. Bu örnekte, `DateTime` sınıfı *System.dll*.  Visual Basic projesindeki başvuruları görmek için **tüm dosyaları göster** ' i seçin.

     **Fakes derlemesi Ekle** ' yi seçin.

2. **ShimsContext içine dolgu ekleme**

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

    Dolgu sınıfı adları `Fakes.Shim` orijinal tür adının önüne eklenerek yapılır. Parametre adları yöntem adına eklenir. (System. Fakes 'e herhangi bir derleme başvurusu eklemeniz gerekmez.)

Önceki örnek statik yöntem olarak bir dolgu kullanır. Bir örnek yöntemi için dolgu kullanmak üzere `AllInstances` tür adı ve Yöntem adı arasına yazın:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(Başvurulacak ' System. ıO. Fakes ' derlemesi yok. Ad alanı dolgu oluşturma işlemi tarafından oluşturulur. , Ancak her zamanki şekilde ' Using ' veya ' Import ' kullanabilirsiniz.)

Ayrıca belirli örnekler, oluşturucular ve özellikler için dolgular oluşturabilirsiniz. Daha fazla bilgi için bkz. [birim testi için uygulamanızı diğer derlemelerden yalıtmak için dolgu kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="using-microsoft-fakes-in-the-ci"></a>CI 'da Microsoft Fakes 'i kullanma

### <a name="microsoft-fakes-assembly-generation"></a>Microsoft Fakes derleme oluşturma
Microsoft Fakes için Visual Studio Enterprise gerektiğinden, Fakes derlemelerinin oluşturulması, projenizi [Visual Studio Build görevi](/azure/devops/pipelines/tasks/build/visual-studio-build?view=azure-devops)kullanarak oluşturmanızı gerektirir.

::: moniker range=">=vs-2019"
> [!NOTE]
> Buna alternatif olarak, Fakes derlemelerinizi CI 'da denet, [MSBuild görevini](../msbuild/msbuild-task.md?view=vs-2019)kullanmaktır. Bunu yaptığınızda, aşağıdaki kod parçacığına benzer şekilde, test projenizde oluşturulan Fakes derlemesine bir derleme başvurunuz olduğundan emin olmanız gerekir:

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <ItemGroup>
        <Reference Include="FakesAssemblies\System.Fakes.dll">
    </ItemGroup>
</Project>
```

Bu başvurunun el ile özel SDK stili projelere eklenmesi gerekir (.NET Core ve .NET Framework). Bu, test projenize örtük olarak derleme başvuruları eklemek için taşınmıştır. Bu yöntemi izlerseniz, üst derleme değiştiğinde Fakes derlemesinin güncelleştirildiğinden emin olmanız gerekir.
::: moniker-end

### <a name="running-microsoft-fakes-tests"></a>Microsoft Fakes testlerini çalıştırma
Microsoft Fakes derlemeleri yapılandırılmış `FakesAssemblies` dizinde (varsayılan olarak) bulunduğu sürece `$(ProjectDir)FakesAssemblies` , [VSTest görevini](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops)kullanarak testleri çalıştırabilirsiniz.

::: moniker range=">=vs-2019"
[VSTest Task](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops) .NET Core projeleriyle Microsoft Fakes kullanılarak dağıtılmış test, Visual Studio 2019 güncelleştirme 9 Preview `20201020-06` ve üstünü gerektirir.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="transitioning-your-net-framework-test-projects-that-use-microsoft-fakes-to-sdk-style-net-framework-or-net-core-projects"></a>Microsoft Fakes kullanan .NET Framework test projelerinizi SDK stili .NET Framework veya .NET Core projelerine geçme
.NET Core 'a geçiş yapmak için .NET Framework, Microsoft Fakes için ayarlanmış en az değişiklik yapmanız gerekir. Göz önünde bulundurmanız gereken durumlar şunlardır:
- Özel bir proje şablonu kullanıyorsanız, bunun SDK stili ve uyumlu bir hedef çerçeve için yapılar olduğundan emin olmanız gerekir.
- Bazı türler .NET Framework ve .NET Core 'daki farklı derlemelerde mevcuttur (örneğin, .NET Framework içinde ve ' de `System.DateTime` `System` / `mscorlib` .NET Core 'da bulunur `System.Runtime` ) ve bu senaryolarda, faıllanmış olan derlemeyi değiştirmeniz gerekir.
- Fakes derlemesine ve test projesine bir derleme başvurunuz varsa, şuna benzer bir eksik başvuru hakkında bir derleme uyarısı görebilirsiniz:
  ```
  (ResolveAssemblyReferences target) ->
  warning MSB3245: Could not resolve this reference. Could not locate the assembly "AssemblyName.Fakes". Check to make sure the assembly exists on disk.
  If this reference is required by your code, you may get compilation errors.
  ```
  Bu uyarı, Fakes oluşturmada yapılan gerekli değişikliklerin yoksayılmasına neden olmuş olabilir. Artık derleme sırasında dolaylı olarak eklemediğimiz için, proje dosyasından derleme başvurusu kaldırılarak bu kaçınılabilir.
::: moniker-end

## <a name="microsoft-fakes-support"></a>Microsoft Fakes desteği 
### <a name="microsoft-fakes-in-older-projects-targeting-net-framework-non-sdk-style"></a>Daha eski projelerde .NET Framework (SDK olmayan stili) hedefleyen Microsoft Fakes.
- Microsoft Fakes derleme üretimi Visual Studio Enterprise 2015 ve üzeri sürümlerde desteklenir.
- Microsoft Fakes testleri, kullanılabilir tüm Microsoft. TestPlatform NuGet paketleriyle çalıştırılabilir.
- Kod kapsamı, Visual Studio Enterprise 2015 ve üzeri sürümlerde Microsoft Fakes kullanan test projeleri için desteklenir.

### <a name="microsoft-fakes-in-sdk-style-net-framework-and-net-core-projects"></a>SDK stilindeki .NET Framework ve .NET Core projelerinde Microsoft Fakes
- Microsoft Fakes derleme nesli, Visual Studio Enterprise 2019 güncelleştirme 6 ' da önizlenmiş ve güncelleştirme 8 ' de varsayılan olarak etkinleştirilmiştir.
- .NET Framework hedef olan projeler için Microsoft Fakes testleri, kullanılabilir tüm Microsoft. TestPlatform NuGet paketleriyle çalıştırılabilir.
- .NET Core ' u hedefleyen projelere yönelik Microsoft Fakes testleri, [16.8.0-Preview-20200921-01](https://www.nuget.org/packages/Microsoft.TestPlatform/16.8.0-preview-20200921-01) ve üzeri sürümlerle Microsoft. TestPlatform NuGet paketleri ile çalışabilir.
- Kod kapsamı, Visual Studio Enterprise Sürüm 2015 ve üzeri sürümlerde Microsoft Fakes 'i kullanarak .NET Framework Hedefleme test projeleri için desteklenir.
- Microsoft Fakes kullanarak .NET Core 'u hedefleyen test projeleri için kod kapsamı desteği geliştirme aşamasındadır.


## <a name="in-this-section"></a>Bu bölümde
[Birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Birim testi için uygulamanızı diğer derlemelerden yalıtmak üzere dolgular kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
