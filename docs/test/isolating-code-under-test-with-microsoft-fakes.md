---
title: Microsoft Fakes ile Test Edilen Kodu Yalıtma
description: Uygulamanın Microsoft Fakes parçalarını saplamalar veya dolgularla değiştirerek test etmekte olduğu kodu yalıtmanıza nasıl yardımcı olduğunu öğrenin.
ms.custom: SEO-VS-2020, devdivchpfy22
ms.date: 02/02/2022
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
ms.openlocfilehash: 23940edd4bdcbc16a9318fd6020093ef58b10303
ms.sourcegitcommit: 23b0ef3815833426933ff6491271034658683f9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137983812"
---
# <a name="isolate-code-under-test-with-microsoft-fakes"></a>Microsoft Fakes ile test edilen kodu yalıtma

Microsoft Fakes, uygulamanın diğer bölümlerini saplamalar veya dolgularla değiştirerek test etmekte olduğunu *kodu yalıtmanıza* *yardımcı olur*. Saplamalar ve dolgular, testlerinizi kontrol altında olan küçük kod parçalarıdır. Kodunuzu sınama için yalıttığınız zaman, sınama başarısız olduğunda nedeninin başka bir yerde değil, tam da orada olduğunu bileceksiniz. Saplamalar ve dolgular, uygulamanın diğer bölümleri henüz çalışmasa bile kodunuzu test etmenizi de sağlar.

Fakes iki türde olabilir:

- [Saplama](#get-started-with-stubs), bir sınıfı aynı arabirimi uygulayan küçük bir yedekle değiştirir.  Saptamalar kullanmak için uygulamanızı her bir bileşenin diğer bileşenlere değil yalnızca arabirimlere bağlı olacak şekilde tasarlamanız gerekir. ("Bileşen" ifadesiyle, birlikte tasarlanan ve güncelleştirilen ve tipik olarak bir derlemede yer alan sınıf veya sınıflardan oluşan grup kastedilmektedir.)

- Dolgu [,](#get-started-with-shims) belirtilen yöntem çağrısı yapmak yerine testin sağladığı dolgu kodunu çalıştırarak çalışma zamanında uygulamanın derlenmiş kodunu değiştiren bir değerdir. Dolgular, .NET derlemeleri gibi değiştire olmadığınız derlemelere yapılan çağrıları değiştirmek için kullanılabilir.

    ![Fakes bileşenleri değiştirme](../test/media/fakes-2.png)

**Gereksinimler**

- Visual Studio Enterprise
- .NET Framework projesi
::: moniker range=">=vs-2019"
- .NET Core, .NET 5.0 veya sonraki sürümü ve SDK stili proje desteği Visual Studio 2019 Güncelleştirme 6'da önizlemeye alındı ve Güncelleştirme 8'de varsayılan olarak etkindir. Daha fazla bilgi için bkz[. .NET Core Microsoft Fakes SDK stili projelerin nasıl oluşturulduğu](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects).
::: moniker-end

> [!NOTE]
> Visual Studio profil oluşturma, Microsoft Fakes kullanan testler için kullanılamaz.

## <a name="choose-between-stub-and-shim-types"></a>Saplama ve dolgu türleri arasında seçim

Genelde bu sınıfları aynı anda geliştirip güncelleştirdiğinizden bir Visual Studio projesini bileşen olarak kabul edebilirsiniz. Projenin çözümünüzdeki diğer projelere veya diğer derlemelere yaptığı çağrılar için saptama ve dolgu kullanmayı deneyebilirsiniz.

Derleme çözümünüz içindeki çağrılar için saplamaları Visual Studio diğer başvurulan derlemelere yapılan çağrılar için dolgular kullanabilirsiniz. Bunun nedeni kendi çözümünüz içinde, arabirimleri saplamanın gerektirdiği şekilde tanımlayarak bileşenlerin ayrımını yapmak iyi bir yöntemdir. Ancak,System.dllgibi dış derlemeler genellikle ayrı arabirim tanımları ile sağlanmalıdır, bu nedenle bunun yerine dolguları kullansanız gerekir.**

Diğer değerlendirmeler şunlardır:

**Performans.** Dolgular çalışma zamanında kodunuzu yeniden yazarak daha yavaş çalışır. Saplamalar bu performans ek yüküne sahip değildir ve sanal yöntemler kadar hızlıdır.

**Statik yöntemler, korumalı türler.** Arayüzleri uygulamak için yalnızca saptamalar kullanabilirsiniz. Bu nedenle, saplama türleri statik yöntemler, sanal olmayan yöntemler, korumalı sanal yöntemler, korumalı türlerde yöntemler ve diğer yöntemler için kullanılamaz.

**İç türler.** Hem saplamalar hem de dolgular derleme özniteliği kullanılarak erişilebilen iç türlerle kullanılabilir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.

**Özel yöntemler.** Dolgular, bir yöntem imzasındaki tüm türler görünür durumdaysa çağrıları özel yöntemlerle değiştirebilir. Saptamalar yalnızca görünür yöntemlerle değiştirilebilir.

**Arabirimler ve soyut yöntemler.** Saptamalar, test sırasında kullanılabilecek arayüzlerin ve özet yöntemlerin uygulanmalarını sağlar. Dolgular, yöntem gövdeleri olduğundan arabirimleri ve soyut yöntemleri takip etmelerini sağlar.

Kod tabanınız içindeki bağımlılıklardan yalıtmak için saplama türlerini kullanmanızı öneririz. Bunu bileşenleri arayüzlerin arkasına gizleyerek yapabilirsiniz. Test edilebilir BIR API sağlan etmeyen üçüncü taraf bileşenlerden yalıtmak için dolgu türlerini kullanabilirsiniz.

## <a name="get-started-with-stubs"></a>Kullanmaya başlayın ile birlikte

Daha ayrıntılı bir açıklama için bkz [. Birim testi için uygulama parçalarını diğerlerinden yalıtmak için saplamaları kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

1. **Arabirim ekleme**

     Saplamaları kullanmak için, test etmek istediğiniz kodu, uygulamanın başka bir bileşeninde sınıflardan açıkça bahsetmeyecektir şekilde yazmanız gerekir. "Bileşen" ifadesiyle, birlikte geliştirilen ve güncellenen ve tipik olarak tek Visual Studio projesinde yer alan sınıf veya sınıflar kastedilmektedir. Değişkenler ve parametreler arabirimler kullanılarak bildir olmalı ve diğer bileşenlerin örnekleri bir fabrika kullanılarak geçir olmalı veya oluşturularak oluşturul olmalıdır. Örneğin, StockFeed uygulamanın başka bir bileşeninde bir sınıfsa, bu kötü olarak kabul edilir:

     `return (new StockFeed()).GetSharePrice("COOO"); // Bad`

     Bunun yerine, diğer bileşen tarafından uygulanan bir arabirim tanımlayabilir ve test amacıyla bir saplama tarafından da uygulanabilirsiniz:

    ```csharp
    public int GetContosoPrice(IStockFeed feed) => feed.GetSharePrice("COOO");
    ```

    ```vb
    Public Function GetContosoPrice(feed As IStockFeed) As Integer
     Return feed.GetSharePrice("COOO")
    End Function

    ```

2. **Derleme Fakes ekleme**

   1. Şu **Çözüm Gezgini**: 
       - Daha eski bir .NET Framework Project (SDK stili olmayan), birim testi projenizin **Başvurular düğümünü** genişletin.
       ::: moniker range=">=vs-2019"
       - .NET Framework, .NET Core veya .NET 5.0 veya sonraki bir sürümü hedef alan SDK stili bir proje için Bağımlılıklar düğümünü  genişleterek Derlemeler **, Projeler** veya Paketler altında sahtesini yapmak için derlemeyi **bulun**. 
       ::: moniker-end
       - Visual Basic'da çalışıyorsanız **Başvurular** düğümünü görmek **için Çözüm Gezgini** araç çubuğunda Tüm **Dosyaları Göster'i** seçin.
   2. Dolgu oluşturmak istediğiniz sınıf tanımlarını içeren derlemeyi seçin. Örneğin, **DateTime'ı dolgu olarak eklemek için****System.dll.**

   3. Kısayol menüsünde Derleme **ekle'yi Fakes seçin**.

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

    Buradaki özel sihirli parça sınıfıdır `StubIStockFeed`. Başvurulan derlemedeki her arabirim için saptama sınıfı Microsoft Fakes mekanizması oluşturur. Saplama sınıfının adı, ön ek olarak "" ve eklenen`Fakes.Stub` parametre türü adları ile arabirimin adı türetildi.

    Saptamalar ayrıca olaylar ve genel yöntemlerle ilgili olarak özellik okuyucu ve ayarlayıcılar için oluşturulur. Daha fazla bilgi için bkz [. Birim testi için uygulama parçalarını diğerlerinden yalıtmak için saplamaları kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md).

## <a name="get-started-with-shims"></a>Kullanmaya başlayın ile birlikte

(Daha ayrıntılı bir açıklama için bkz [. Birim testi için diğer derlemelerden uygulamanızı yalıtmak için dolguları kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).)

Bileşeninizin çağrısı içerdiğini varsayalım `DateTime.Now`:

```csharp
// Code under test:
    public int GetTheCurrentYear()
    {
       return DateTime.Now.Year;
    }
```

Gerçek sürüm her çağrıda tutarsız `Now` bir şekilde farklı bir değer döndür olduğundan, test sırasında özelliğini dolguyla ifade etmektisiniz.

Dolguları kullanmak için uygulama kodunu değiştirmeniz veya belirli bir şekilde yazmanız gerek değildir.

1. **Derleme Fakes ekleme**

     Bu **Çözüm Gezgini**, birim testi projenizin başvurularını açın ve sahtesini yapmak istediğiniz yöntemi içeren derleme başvurularını seçin. Bu örnekte, sınıfı `DateTime` *System.dll.*  Bir projedeki başvuruları görmek Visual Basic Tüm Dosyaları **Göster'i seçin**.

     Derleme **ekle'Fakes seçin**.

2. **Bir ShimsContext içine dolgu ekleme**

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

    Dolgu sınıfı adları, özgün tür adına ön `Fakes.Shim` ek ek olarak yapılır. Parametre adları yöntem adına eklenir. (Sistem'e herhangi bir derleme başvurusu eklemenize gerek yok. Fakes.)

Önceki örnek statik yöntem olarak bir dolgu kullanır. Örnek yöntemi için dolgu kullanmak üzere tür adı `AllInstances` ile yöntem adı arasına yazın:

```vb
System.IO.Fakes.ShimFile.AllInstances.ReadToEnd = ...
```

(Hiçbir 'System.IO. Fakes derlemesi. Ad alanı dolgu oluşturma işlemi tarafından oluşturulur. Ancak 'using' veya 'Import' kullanabilirsiniz.)

Ayrıca belirli örnekler, oluşturucular ve özellikler için dolgular oluşturabilirsiniz. Daha fazla bilgi için bkz [. Birim testi için uygulamanızı diğer derlemelerden yalıtmak için dolguları kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md).

## <a name="using-microsoft-fakes-in-the-ci"></a>CI Microsoft Fakes de Microsoft Fakes kullanma

### <a name="microsoft-fakes-assembly-generation"></a>Microsoft Fakes Derleme Oluşturma

Derlemeler Microsoft Fakes Visual Studio Enterprise gerektirdiği için, Fakes Derleme Görevi'Visual Studio [projenizi derlemeniz gerekir](/azure/devops/pipelines/tasks/build/visual-studio-build?view=azure-devops&preserve-view=true).

::: moniker range=">=vs-2019"
> [!NOTE]
> Bunun alternatifi, derleme derlemelerinizi CI'Fakes denetleme ve derleme görevi MSBuild [kullanmaktır](../msbuild/msbuild-task.md?view=vs-2019&preserve-view=true). Bunu gerçekleştirecek olurken, aşağıdaki kod parçacığına benzer şekilde test projeniz içinde oluşturulan Fakes derlemeye bir derleme başvurusuna sahip olduğundan emin olmak gerekir:

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <ItemGroup>
        <Reference Include="FakesAssemblies\System.Fakes.dll"/>
    </ItemGroup>
</Project>
```

Test projenize örtülü derleme başvuruları eklemeye taşındığımız için, bu başvuru özellikle SDK stili projelerine (.NET Core, .NET 5.0 ve .NET Framework) el ile eklenmiştir. Bu yöntemi kullanırsanız, üst derleme değişirken fakes derlemenin güncelleştirilmiş olduğundan emin olun.
::: moniker-end

### <a name="running-microsoft-fakes-tests"></a>Test Microsoft Fakes çalıştırma

Yapılandırılmış dizinde Microsoft Fakes `FakesAssemblies` derlemeler olduğu sürece (`$(ProjectDir)FakesAssemblies`Varsayılan olarak), [vstest görevini kullanarak testleri çalıştırabilirsiniz](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops&preserve-view=true).

::: moniker range=">=vs-2019"
Microsoft Fakes [kullanan vstest](/azure/devops/pipelines/tasks/test/vstest?view=azure-devops&preserve-view=true) görevi .NET Core ve .NET 5.0 veya sonraki projeleriyle dağıtılmış test için Visual Studio 2019 Güncelleştirme 9 Önizlemesi `20201020-06` ve sonraki bir sürümü gerekir.
::: moniker-end

::: moniker range=">=vs-2019"

## <a name="transitioning-your-net-framework-test-projects-that-use-microsoft-fakes-to-sdk-style-net-framework-net-core-or-net-50-projects-or-later-projects"></a>.NET Framework kullanan Microsoft Fakes SDK stili .NET Framework, .NET Core veya .NET 5.0 projelerine veya sonraki projelere geçiş

.NET Core veya .NET 5.0'a Microsoft Fakes için ayar .NET Framework az değişiklik gerekir. Göz önünde bulundurarak dikkat etmek zorunda olacağınız durumlar:

- Özel bir proje şablonu kullanıyorsanız, bunun SDK stiline sahip olduğundan ve uyumlu bir hedef çerçeve için oluşturulduğuna emin olmak gerekir.
- Bazı türler .NET Framework ve .NET Core/.NET 5.0'daki farklı derlemelerde (örneğin, `System.DateTime``mscorlib` `System`/.NET Framework'de ve `System.Runtime` .NET Core ve .NET 5.0'da mevcuttur) ve bu senaryolarda sahte derlemeyi değiştirmek gerekir.
- Fakes derlemesi ve test projesine bir derleme başvurusu varsa, aşağıdakine benzer eksik başvuru hakkında bir derleme uyarısıyla karşınız olabilir:

  ```
  (ResolveAssemblyReferences target) ->
  warning MSB3245: Could not resolve this reference. Could not locate the assembly "AssemblyName.Fakes". Check to make sure the assembly exists on disk.
  If this reference is required by your code, you may get compilation errors.
  ```
  Bu uyarı, yeni nesilde yapılan gerekli Fakes ve yoksayılabilir. Derleme başvurusu proje dosyasından kaldırılarak bundan kaçınabilirsiniz çünkü artık derleme sırasında bunları örtülü olarak ekleyebilirsiniz.
::: moniker-end

## <a name="microsoft-fakes-support"></a>Microsoft Fakes desteği 
### <a name="microsoft-fakes-in-older-projects-targeting-net-framework-non-sdk-style"></a>Microsoft Fakes (SDK stili olmayan.NET Framework eski projelerde yer alır.
- Microsoft Fakes derleme oluşturma, 2015 ve Visual Studio Enterprise için de destekleni.
- Microsoft Fakes tüm kullanılabilir Microsoft.TestPlatform ve paketlerle NuGet çalıştırabilirsiniz.
- Kod kapsamı, 2015 ve Microsoft Fakes'Visual Studio Enterprise test projeleri için de destek sağlar.

### <a name="microsoft-fakes-in-sdk-style-net-framework-net-core-and-net-50-or-later-projects"></a>Microsoft Fakes, .NET Core .NET Framework .NET 5.0 veya sonraki projelerde sdk stilinde uygulamalar
- Microsoft Fakes 2019 Güncelleştirme 6'Visual Studio Enterprise önizlemesi yapıldı ve Güncelleştirme 8'de varsayılan olarak etkindir.
- Microsoft Fakes projelerin tüm kullanılabilir Microsoft.TestPlatform .NET Framework paketleriyle çalıştır NuGet abilirsiniz.
- .NET Core Microsoft Fakes .NET 5.0 veya sonraki sürümlerini hedef alan projelerin testlerini microsoft.TestPlatform NuGet paketleri [16.9.0-preview-20210106-01](https://www.nuget.org/packages/Microsoft.TestPlatform/16.9.0-preview-20210106-01) ve sonraki sürümleriyle çalıştırabilirsiniz.
- Kod kapsamı, 2015 ve .NET Framework Microsoft Fakes Visual Studio Enterprise test projeleri için de destek sağlar.
- Microsoft Fakes kullanarak .NET Core ve .NET 5.0 veya sonraki bir güncelleştirmeyi hedef alan test projeleri için kod kapsamı desteği, Visual Studio 2019 güncelleştirme 9 ve üzerinde kullanılabilir.


## <a name="in-this-section"></a>Bu bölümde

[Birim testi için uygulamanızın parçalarını birbirinden yalıtmak üzere saplamalar kullanma](../test/using-stubs-to-isolate-parts-of-your-application-from-each-other-for-unit-testing.md)

[Birim testi için uygulamanızı diğer derlemelerden yalıtmak üzere dolgular kullanma](../test/using-shims-to-isolate-your-application-from-other-assemblies-for-unit-testing.md)

[Microsoft Fakes'te kod oluşturma, derleme ve adlandırma kuralları](../test/code-generation-compilation-and-naming-conventions-in-microsoft-fakes.md)