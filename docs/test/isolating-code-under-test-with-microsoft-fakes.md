---
title: Microsoft Fakes ile Test Edilen Kodu Yalıtma
description: Microsoft Fakes, uygulamanın diğer bölümlerini saplamalar veya parçalar ile değiştirerek test ettiğiniz kodu yalıtmanıza nasıl yardımcı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/03/2020
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
dev_langs:
- VB
- CSharp
ms.openlocfilehash: 0155aae4ef2feb022bf0f8e9d56502e68244852d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628100"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Microsoft Fakes ile test edilen kodu yalıtma

Microsoft Fakes, uygulamanın diğer bölümlerini *saplamalar* *veya parçalar* ile değiştirerek test ettiğiniz kodu yalıtmanıza yardımcı olur. Bunlar, testlerinizin denetimi altında olan küçük kod parçalarıdır. Kodunuzu sınama için yalıttığınız zaman, sınama başarısız olduğunda nedeninin başka bir yerde değil, tam da orada olduğunu bileceksiniz. Uygulamanın diğer parçaları çalışmıyor olsa bile, saptamalar ve dolgular kodunuzu test etmenize olanak sağlar.

Fakes iki türde olabilir:

- [Saplama](#get-started-with-stubs) , bir sınıfı aynı arabirimi uygulayan küçük bir değiştirme ile değiştirir.  Saptamalar kullanmak için uygulamanızı her bir bileşenin diğer bileşenlere değil yalnızca arabirimlere bağlı olacak şekilde tasarlamanız gerekir. ("Bileşen" ifadesiyle, birlikte tasarlanan ve güncelleştirilen ve tipik olarak bir derlemede yer alan sınıf veya sınıflardan oluşan grup kastedilmektedir.)

- Bir [Dolgu](#get-started-with-shims) , çalışma zamanında uygulamanızın derlenmiş kodunu değiştirir, böylece belirli bir yöntem çağrısını yapmak yerine, testinizin sağladığı dolgu kodunu çalıştırır. Dolgu, .NET derlemeleri gibi değiştiremeyeceğiniz Derlemelerle değiştirmek için kullanılabilir.

![Fakes diğer bileşenleri değiştir](../test/media/fakes-2.png)

**Gereksinimler**

- Visual Studio Enterprise
- bir .NET Framework projesi
::: moniker range=">=vs-2019"
- Visual Studio 2019 güncelleştirme 6 ' da önizlenen .net Core, .net 5,0 ve SDK stili proje desteği ve güncelleştirme 8 ' de varsayılan olarak etkinleştirilmiştir. daha fazla bilgi için bkz. [.net Core ve SDK stilindeki projeler için Microsoft Fakes](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

> [!NOTE]
> - Visual Studio profil oluşturma Microsoft Fakes kullanan testler için kullanılamaz.

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

2. **Fakes derleme ekle**

   1. **Çözüm Gezgini**, 
       - daha eski bir .NET Framework Project (SDK olmayan stil) için, birim testi projenizin **başvurular** düğümünü genişletin.
       ::: moniker range=">=vs-2019"
       - .NET Framework, .net Core veya .net 5,0 ' i hedefleyen SDK stili bir proje için, **derlemeler**, **projeler** veya **paketler** altında taklit etmek istediğiniz derlemeyi bulmak için **bağımlılıklar** düğümünü genişletin.
       ::: moniker-end
       - Visual Basic ' de çalışıyorsanız, **başvurular** düğümünü görmek için **Çözüm Gezgini** araç çubuğunda **tüm dosyaları göster** ' i seçin.
   2. Dolgu oluşturmak istediğiniz sınıf tanımlarını içeren derlemeyi seçin. Örneğin, **TarihSaat** dolgusu istiyorsanız **System.dll**' yi seçin.

   3. kısayol menüsünde **Fakes derlemesi ekle**' yi seçin.

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

1. **Fakes derleme ekle**

     **Çözüm Gezgini**, birim testi projenizin başvurularını açın ve taklit etmek istediğiniz yöntemi içeren derlemenin başvurusunu seçin. Bu örnekte, `DateTime` sınıfı *System.dll*.  Visual Basic projesindeki başvuruları görmek için **tüm dosyaları göster**' i seçin.

     **Fakes derlemesi ekle**' yi seçin.

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

    Dolgu sınıfı adları `Fakes.Shim` orijinal tür adının önüne eklenerek yapılır. Parametre adları yöntem adına eklenir. (Sisteme herhangi bir derleme başvurusu eklemeniz gerekmez. Fakes.)

Önceki örnek statik yöntem olarak bir dolgu kullanır. Bir örnek yöntemi için dolgu kullanmak üzere `AllInstances` tür adı ve Yöntem adı arasına yazın:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(' System.IO ' yok. ' Fakes ' derlemesine başvuru. Ad alanı dolgu oluşturma işlemi tarafından oluşturulur. , Ancak her zamanki şekilde ' Using ' veya ' Import ' kullanabilirsiniz.)

Ayrıca belirli örnekler, oluşturucular ve özellikler için dolgular oluşturabilirsiniz. Daha fazla bilgi için bkz. [birim testi için uygulamanızı diğer derlemelerden yalıtmak için dolgu kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="using-microsoft-fakes-in-the-ci"></a>cı içinde Microsoft Fakes kullanma

### <a name="microsoft-fakes-assembly-generation"></a>Microsoft Fakes Derleme oluşturma
Microsoft Fakes Visual Studio Enterprise gerektirdiğinden Fakes derlemelerin oluşturulması projenizi [Visual Studio build görevi](/azure/devops/pipelines/tasks/build/visual-studio-build?view=azure-devops&preserve-view=true)kullanarak oluşturmanızı gerektirir.

::: moniker range=">=vs-2019"
> [!NOTE]
> bunun bir alternatifi Fakes derlemelerinizi cı 'da denet, [MSBuild görevini](../msbuild/msbuild-task.md?view=vs-2019&preserve-view=true)kullanmaktır. bunu yaptığınızda, aşağıdaki kod parçacığına benzer şekilde, test projenizde oluşturulan Fakes derlemesine bir derleme başvurunuz olduğundan emin olmanız gerekir:

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <ItemGroup>
        <Reference Include="FakesAssemblies\System.Fakes.dll"/>
    </ItemGroup>
</Project>
```

bu başvurunun el ile özel SDK stili projelere eklenmesi gerekir (.net Core, .net 5,0 ve .NET Framework). bu, test projenize örtük olarak derleme başvuruları eklemek için taşınmıştır. Bu yöntemi izlerseniz, üst derleme değiştiğinde Fakes derlemesinin güncelleştirildiğinden emin olmanız gerekir.
::: moniker-end

### <a name="running-microsoft-fakes-tests"></a>Microsoft Fakes testleri çalıştırma
Microsoft Fakes derlemeleri yapılandırılmış `FakesAssemblies` dizinde (varsayılan olarak) mevcut olduğu sürece `$(ProjectDir)FakesAssemblies` , [vstest görevini](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops&preserve-view=true)kullanarak testleri çalıştırabilirsiniz.

::: moniker range=">=vs-2019"
[vstest task](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops&preserve-view=true) .net Core ve .net 5,0 projeleriyle Microsoft Fakes kullanan dağıtılmış test, Visual Studio 2019 güncelleştirme 9 Preview `20201020-06` ve üstünü gerektirir.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="transitioning-your-net-framework-test-projects-that-use-microsoft-fakes-to-sdk-style-net-framework-net-core-or-net-50-projects"></a>Microsoft Fakes kullanan .NET Framework test projelerinizi SDK stili .NET Framework, .net Core veya .net 5,0 projelerine geçiş
.net Core veya .net 5,0 ' e geçişe Microsoft Fakes için .NET Framework ayarlamanız gereken en küçük değişikliklere ihtiyacınız olacaktır. Göz önünde bulundurmanız gereken durumlar şunlardır:
- Özel bir proje şablonu kullanıyorsanız, bunun SDK stilinde olduğundan ve uyumlu bir hedef çerçeve için oluşturulduğuna emin olmak gerekir.
- Bazı türler .NET Framework ve .NET Core/.NET 5.0'daki farklı derlemelerde (örneğin, .NET Framework'da ve .NET Core ve `System.DateTime` `System` / `mscorlib` `System.Runtime` .NET 5.0'da mevcuttur) ve bu senaryolarda sahte derlemeyi değiştirmelisiniz.
- Fakes derlemesi ve test projesine bir derleme başvurun varsa, aşağıdakine benzer eksik başvuruyla ilgili bir derleme uyarısıyla karşınız olabilir:
  ```
  (ResolveAssemblyReferences target) ->
  warning MSB3245: Could not resolve this reference. Could not locate the assembly "AssemblyName.Fakes". Check to make sure the assembly exists on disk.
  If this reference is required by your code, you may get compilation errors.
  ```
  Bu uyarı, oluşturmanın yoksayılabilir olması Fakes değişikliklerden dolayıdır. Derleme başvurusu proje dosyasından kaldırılarak bundan kaçınabilirsiniz çünkü artık derleme sırasında bunları örtülü olarak ekleyebilirsiniz.
::: moniker-end

## <a name="microsoft-fakes-support"></a>Microsoft Fakes desteği 
### <a name="microsoft-fakes-in-older-projects-targeting-net-framework-non-sdk-style"></a>Microsoft Fakes (SDK stili olmayan) .NET Framework eski projelerde yer alır.
- Microsoft Fakes derleme oluşturma, 2015 ve Visual Studio Enterprise için de destekleni.
- Microsoft Fakes tüm kullanılabilir Microsoft.TestPlatform ve paketlerle NuGet çalıştırabilirsiniz.
- Kod kapsamı, 2015 ve Microsoft Fakes Visual Studio Enterprise test projeleri için de destek sağlar.

### <a name="microsoft-fakes-in-sdk-style-net-framework-net-core-and-net-50-projects"></a>Microsoft Fakes, .NET Core .NET Framework .NET 5.0 projelerinde SDK stilinde uygulamalar
- Microsoft Fakes 2019 Güncelleştirme 6'Visual Studio Enterprise önizlemesi yapıldı ve Güncelleştirme 8'de varsayılan olarak etkindir.
- Microsoft Fakes projelerin tüm kullanılabilir Microsoft.TestPlat NuGet form .NET Framework paketleriyle çalıştırabilirsiniz.
- Microsoft Fakes .NET Core ve .NET 5.0'i hedef alan projeler için NuGet testleri, [16.9.0-preview-20210106-01](https://www.nuget.org/packages/Microsoft.TestPlatform/16.9.0-preview-20210106-01) ve daha yüksek sürümlerine sahip Microsoft.TestPlatform NuGet paketleriyle çalıştırabilirsiniz.
- Kod kapsamı, 2015 ve .NET Framework bir Microsoft Fakes Visual Studio Enterprise test projeleri için de destek sağlar.
- Microsoft Fakes kullanarak .NET Core ve .NET 5.0'ı hedef alan test projeleri için kod kapsamı desteği, Visual Studio 2019 güncelleştirme 9 ve üzerinde kullanılabilir.


## <a name="in-this-section"></a>Bu bölümde
[Birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Birim testi için uygulamanızı diğer derlemelerden yalıtmak üzere dolgular kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)
