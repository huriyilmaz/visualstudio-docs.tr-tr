---
title: Birim testi için uygulamanızı yalıtmak üzere dolgular kullanma
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: jillfra
manager: jillfra
author: jillre
dev_langs:
- CSharp
- VB
ms.openlocfilehash: e4a59cb4e3372e16634cddde2a163ac94ca73d24
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72982806"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>Birim testi için uygulamanızı yalıtmak üzere dolgular kullanma

**Dolgu türleri** , Microsoft Fakes çerçevesinin, ortamdan test altında bileşenleri yalıtmanızı sağlamak için kullandığı iki teknolojiden biridir. Öğims, testinizin bir parçası olarak yazdığınız koda yönelik belirli yöntemlere çağrı yapılır. Birçok yöntem dış koşullara bağlı farklı sonuçlar döndürür, ancak bir dolgu, testinizin denetimi altında bulunur ve her çağrıda tutarlı sonuçlar döndürebilir. Bu, testlerin yazmayı kolaylaştırır.

Kodunuzu çözümünüzün bir parçası olmayan derlemelerden yalıtmak için *dolgular* kullanın. Çözümünüzün bileşenlerini birbirinden yalıtmak için, *saplamalar*kullanın.

Genel bakış ve "hızlı başlangıç" Kılavuzu için bkz. [Microsoft Fakes ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md).

**Requirements**

- Visual Studio Enterprise
- Bir .NET Framework projesi

> [!NOTE]
> .NET Standard projeler desteklenmez.

## <a name="example-the-y2k-bug"></a>Örnek: Y2K hatası

1 Ocak 2000 ' de bir özel durum oluşturan bir yöntem düşünün:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Program, bilgisayarın saatine, ortama bağımlı, belirleyici olmayan bir yönteme bağlı olarak `DateTime.Now` bağlı olduğundan, bu yöntemin sınanması sorunlu olur. Ayrıca, `DateTime.Now` bir statik özelliktir, bu nedenle bir saplama türü burada kullanılamaz. Bu sorun, birim testinde yalıtım sorununun sentomasyonunu ' dir: doğrudan veritabanı API 'Lerine çağrı yapan, Web hizmetleriyle iletişim kuran ve bu şekilde olan programlar, ortamınız ortama bağlı olduğundan birim testi zor.

Bu, dolgu türlerinin kullanılması gereken yerdir. Dolgu türleri, bir .NET yönteminin Kullanıcı tanımlı bir temsilciye çıkarılması için bir mekanizma sağlar. Dolgu türleri, Fakes üreticisi tarafından kod tarafından oluşturulmuştur ve yeni yöntem uygulamalarını belirtmek için dolgu türlerini çağırdığımız temsilciler kullanırlar.

Aşağıdaki test, bir tarih saat için özel bir uygulama sağlamak üzere `ShimDateTime` dolgu türünü nasıl kullanacağınızı gösterir. şimdi:

```csharp
//unit test code
// create a ShimsContext cleans up shims
using (ShimsContext.Create()) {
    // hook delegate to the shim method to redirect DateTime.Now
    // to return January 1st of 2000
    ShimDateTime.NowGet = () => new DateTime(2000, 1, 1);
    Y2KChecker.Check();
}
```

## <a name="how-to-use-shims"></a>Dolgu kullanımı

İlk olarak, Fakes derlemesi ekleyin:

1. **Çözüm Gezgini**, birim testi projenizin **Başvurular** düğümünü genişletin.

   - Visual Basic ' de çalışıyorsanız, **Başvurular** düğümünü görmek için **Çözüm Gezgini** araç çubuğunda **tüm dosyaları göster** ' i seçin.

2. Dolgu oluşturmak istediğiniz sınıf tanımlarını içeren derlemeyi seçin. Örneğin, **TarihSaat**dolgusu istiyorsanız **System. dll**' yi seçin.

3. Kısayol menüsünde **Fakes derlemesi Ekle**' yi seçin.

### <a name="use-shimscontext"></a>ShimsContext kullanma

Bir birim testi çerçevesinde dolgu türleri kullanırken, parçalarınızın ömrünü denetlemek için test kodunu bir `ShimsContext` sarın. Aksi takdirde, parça AppDomain 'in kapanması için en son bir durum olur. `ShimsContext` oluşturmanın en kolay yolu, aşağıdaki kodda gösterildiği gibi statik `Create()` yöntemini kullanmaktır:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Her dolgu bağlamını doğru bir şekilde atmak önemlidir. Bir Thumb kuralı olarak, kayıtlı parçalamayı doğru temizlemeyi sağlamak için bir `using` deyimin içindeki `ShimsContext.Create` çağırın. Örneğin, `DateTime.Now` yönteminin yerini alan bir test yöntemi için bir Shim, her zaman Ocak 2000 ' in ilk döndüğü bir temsilciyle kaydedebilirsiniz. Test yönteminde kayıtlı dolgunun işaretini temizlemeye unutursanız, Test çalıştırmasının geri kalanı her zaman `DateTime.Now` değeri olarak Ocak 2000 ' nin ilk değerini döndürür. Bu, şaşırtıcı ve kafa karıştırıcı olabilir.

### <a name="write-a-test-with-shims"></a>Dolgular ile test yazma

Test kodunuzda, taklit etmek istediğiniz yöntem için bir *deturu* ekleyin. Örneğin:

```csharp
[TestClass]
public class TestClass1
{
        [TestMethod]
        public void TestCurrentYear()
        {
            int fixedYear = 2000;

            using (ShimsContext.Create())
            {
              // Arrange:
                // Detour DateTime.Now to return a fixed date:
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

Dolgu sınıfı adları, özgün tür adına `Fakes.Shim` önüne eklenerek yapılır.

Test edilen uygulamanın koduna *deturlar* ekleyerek parça çalışır. Özgün yöntemin bir çağrısının gerçekleştiği her yerde, Fakes sistemi bir deturtur, böylece gerçek yöntemi çağırmak yerine, dolgu kodunuz çağırılır.

Çalışma zamanında deturlar oluşturulup silindiğine dikkat edin. `ShimsContext`yaşam süresi içinde her zaman bir tur oluşturmanız gerekir. Bırakıldığında, etkin durumdayken oluşturduğunuz tüm parçalar kaldırılır. Bunu yapmanın en iyi yolu `using` deyimin içindedir.

Fakes ad alanının mevcut olmadığını belirten bir yapı hatası görebilirsiniz. Bu hata bazen başka derleme hataları olduğunda görüntülenir. Diğer hataları düzeltemedi ve bu işlem açılır.

## <a name="shims-for-different-kinds-of-methods"></a>Farklı türlerde yöntemler için dolgu

Dolgu türleri, statik yöntemler veya sanal olmayan yöntemler dahil olmak üzere herhangi bir .NET yöntemini kendi temsilcileriniz ile değiştirmenizi sağlar.

### <a name="static-methods"></a>Statik yöntemler

Statik yöntemlere parçalı olarak eklenecek özellikler bir dolgu türüne yerleştirilir. Her özellik yalnızca hedef metoda bir temsilci iliştirmek için kullanılabilecek bir ayarlayıcı içerir. Örneğin, `MyClass` bir statik yöntem `MyMethod` bir sınıf olarak verilmiştir:

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

Her zaman 5 döndüren `MyMethod` bir dolgu iliştiriyoruz:

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>Örnek yöntemleri (tüm örnekler için)

Statik yöntemlere benzer şekilde, örnek yöntemleri tüm örnekler için shimmed olabilir. Bu parçalamayı iliştirilecek özellikler, karışıklıkları önlemek için AllInstances adlı iç içe bir türe yerleştirilir. Örneğin, bir sınıf `MyClass` bir örnek yöntemiyle `MyMethod`:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Örnekten bağımsız olarak her zaman 5 döndüren `MyMethod` bir dolgu ekleyebilirsiniz:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

ShimMyClass 'in oluşturulan tür yapısı aşağıdaki kod gibi görünür:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public static class AllInstances {
        public static Func<MyClass, int>MyMethod {
            set {
                ...
            }
        }
    }
}
```

Fakes 'in çalışma zamanı örneğini bu durumda temsilcinin ilk bağımsız değişkeni olarak geçirdiğine dikkat edin.

### <a name="instance-methods-for-one-runtime-instance"></a>Örnek yöntemleri (bir çalışma zamanı örneği için)

Örnek yöntemleri, çağrının alıcısına göre farklı temsilciler tarafından da shimmed olabilir. Bu, aynı örnek yönteminin tür örneği başına farklı davranışlara sahip olmasını sağlar. Bu parçalamayı ayarlamaya yönelik özellikler Dolgu türünün örnek yöntemleridir. Her örneklenmiş dolgu türü, bir shimmed türünün ham örneğiyle de ilişkilendirilir.

Örneğin, bir sınıf `MyClass` bir örnek yöntemiyle `MyMethod`:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

İlk biri her zaman 5 ' i ve ikincisi her zaman 10 ' a geri döndüren MyMethod için iki dolgu türü ayarlayabiliriz:

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

ShimMyClass 'in oluşturulan tür yapısı aşağıdaki kod gibi görünür:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public Func<int> MyMethod {
        set {
            ...
        }
    }
    public MyClass Instance {
        get {
            ...
        }
    }
}
```

Gerçek shimmed tür örneğine örnek özelliği aracılığıyla erişilebilir:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Dolgu türünün Ayrıca, shimmed türüne örtük dönüştürmesi de vardır; bu nedenle genellikle dolgu türünü şöyle kullanabilirsiniz:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>Oluşturucular

Oluşturucular, gelecekteki nesnelere dolgu türleri iliştirmek için de shimmed olabilir. Her Oluşturucu, dolgu türünde statik bir yöntem Oluşturucu olarak sunulur. Örneğin, bir tamsayı alan bir Oluşturucu ile `MyClass` sınıfı verildiğinde:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Kurucudaki değere bakılmaksızın, her bir sonraki örneğin değer alıcısı çağrıldığında-5 döndürmesi için oluşturucunun dolgu türünü ayarladık:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Her dolgu türü iki Oluşturucu açığa çıkarır. Varsayılan Oluşturucu, yeni bir örnek gerektiğinde kullanılmalıdır, ancak bir shimmed örneğini bağımsız değişken olarak alan Oluşturucu yalnızca Oluşturucu dolgular içinde kullanılmalıdır:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

ShimMyClass 'in oluşturulan tür yapısı aşağıdaki koda benzer:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass>
{
    public static Action<MyClass, int> ConstructorInt32 {
        set {
            ...
        }
    }

    public ShimMyClass() { }
    public ShimMyClass(MyClass instance) : base(instance) { }
    ...
}
```

### <a name="base-members"></a>Temel Üyeler

Taban üyelerinin dolgu özelliklerine, temel tür için bir dolgu oluşturularak ve alt örnek, temel dolgu sınıfının oluşturucusuna parametre olarak geçirerek erişilebilir.

Örneğin, bir sınıf `MyBase` bir örnek yöntemi `MyMethod` ve bir alt tür `MyChild`:

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

Yeni bir `ShimMyBase` dolgusu oluşturarak `MyBase` Shim ayarlayabiliriz:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Alt Dolgu türünün, temel dolgu oluşturucusuna parametre olarak geçirildiğinde, örtülü olarak alt örneğe dönüştürüldüğünü unutmayın.

ShimMyChild ve ShimMyBase 'in oluşturulan tür yapısı aşağıdaki koda benzer:

```csharp
// Fakes generated code
public class ShimMyChild : ShimBase<MyChild> {
    public ShimMyChild() { }
    public ShimMyChild(Child child)
        : base(child) { }
}
public class ShimMyBase : ShimBase<MyBase> {
    public ShimMyBase(Base target) { }
    public Func<int> MyMethod
    { set { ... } }
}
```

### <a name="static-constructors"></a>Statik oluşturucular

Dolgu türleri bir türün statik yapıcısını dolgusu için `StaticConstructor` statik bir yöntem sunar. Statik oluşturucular yalnızca bir kez yürütüldüğü için, türden herhangi bir üyeye erişildikten sonra dolgunun yapılandırıldığından emin olmanız gerekir.

### <a name="finalizers"></a>Sonlandırıcılar

Sonlandırıcılar, Fakes 'te desteklenmez.

### <a name="private-methods"></a>Özel Yöntemler

Fakes kod Oluşturucusu yalnızca İmzada görünür türleri olan, diğer bir deyişle, parametre türleri ve dönüş türü görünür olan özel yöntemler için dolgu özellikleri oluşturur.

### <a name="binding-interfaces"></a>Bağlama arabirimleri

Bir shimmed türü bir arabirim uygularsa, kod Oluşturucu bu arabirimin tüm üyelerini aynı anda bağlamasını sağlayan bir yöntemi yayar.

Örneğin, `IEnumerable<int>` uygulayan bir sınıf `MyClass` verildiğinde:

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

Bağlama yöntemini çağırarak MyClass içindeki `IEnumerable<int>` uygulamalarını silebilirsiniz:

```csharp
// unit test code
var shimMyClass = new ShimMyClass();
shimMyClass.Bind(new List<int> { 1, 2, 3 });
```

ShimMyClass 'in oluşturulan tür yapısı aşağıdaki koda benzer:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public ShimMyClass Bind(IEnumerable<int> target) {
        ...
    }
}
```

## <a name="change-the-default-behavior"></a>Varsayılan davranışı değiştirme

Oluşturulan her dolgu türü, `ShimBase<T>.InstanceBehavior` özelliği aracılığıyla `IShimBehavior` arabiriminin bir örneğini barındırır. Bu davranış, istemci açıkça shimmed olmayan bir örnek üyesini her çağırdığında kullanılır.

Davranış açıkça ayarlanmamışsa, statik `ShimsBehaviors.Current` özelliği tarafından döndürülen örneği kullanır. Varsayılan olarak, bu özellik `NotImplementedException` özel durumu oluşturan bir davranış döndürür.

Bu davranış herhangi bir dolgu örneği üzerinde `InstanceBehavior` özelliği ayarlanarak herhangi bir zamanda değiştirilebilir. Örneğin, aşağıdaki kod parçacığı, Shim öğesini hiçbir şey yapan veya dönüş türünün varsayılan değerini döndüren bir davranışa değiştirir — diğer bir deyişle, `default(T)`:

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;
```

Ayrıca, `InstanceBehavior` özelliği statik `ShimsBehaviors.Current` özelliği ayarlanarak açıkça ayarlanmayan tüm shimmed örnekleri için de bu davranış genel olarak değiştirilebilir:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimsBehaviors.Current = ShimsBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>Ortam erişimlerini Algıla

`ShimsBehaviors.NotImplemented` davranışını ilgili Dolgu türünün statik `Behavior` özelliğine atayarak, belirli bir türdeki statik yöntemler dahil olmak üzere tüm üyelere bir davranış eklemek mümkündür:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>Eşzamanlılık

Dolgu türleri, AppDomain içindeki tüm iş parçacıkları için geçerlidir ve iş parçacığı benzeşimine sahip değildir. Eşzamanlılık destekleyen bir Test Çalıştırıcısı kullanmayı planlıyorsanız bu önemli bir olgu değildir. Dolgu türlerini içeren testler aynı anda çalıştırılamaz. Bu özellik Fakes çalışma zamanı tarafından zorlanmaz.

## <a name="call-the-original-method-from-the-shim-method"></a>Dolgu yönteminden özgün yöntemi çağırın

Yöntemine geçirilen dosya adı doğrulandıktan sonra, metni dosya sistemine yazmak istediğinizi düşünün. Bu durumda, orijinal yöntemi dolgu yönteminin ortasında çağıraöğreneceksiniz.

Bu sorunu çözmeye yönelik ilk yaklaşım, aşağıdaki kodda olduğu gibi, bir temsilciyi ve `ShimsContext.ExecuteWithoutShims()` kullanarak özgün yönteme bir çağrıyı sarmalıdır:

```csharp
// unit test code
ShimFile.WriteAllTextStringString = (fileName, content) => {
  ShimsContext.ExecuteWithoutShims(() => {

      Console.WriteLine("enter");
      File.WriteAllText(fileName, content);
      Console.WriteLine("leave");
  });
};
```

Başka bir yaklaşım, dolgunun değerini null olarak ayarlamak, özgün yöntemi çağırmak ve dolgunun geri yüklenmesi.

```csharp
// unit test code
ShimsDelegates.Action<string, string> shim = null;
shim = (fileName, content) => {
  try {
    Console.WriteLine("enter");
    // remove shim in order to call original method
    ShimFile.WriteAllTextStringString = null;
    File.WriteAllText(fileName, content);
  }
  finally
  {
    // restore shim
    ShimFile.WriteAllTextStringString = shim;
    Console.WriteLine("leave");
  }
};
// initialize the shim
ShimFile.WriteAllTextStringString = shim;
```

## <a name="systemenvironment"></a>System. Environment

<xref:System.Environment?displayProperty=fullName>dolgusu için, **derleme** öğesinden sonra mscorlib. Fakes dosyasına aşağıdaki içeriği ekleyin:

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

Çözümü yeniden oluşturduktan sonra, <xref:System.Environment?displayProperty=fullName> sınıfındaki Yöntemler ve Özellikler shimmed olarak mevcuttur, örneğin:

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>Sınırlamalar

Shims, .NET temel sınıf kitaplığı **mscorlib** ve **sistem**içindeki tüm türlerde kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Fakes ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Peter Provost blogu: Visual Studio 2012 dolgular](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Video (1h16): Visual Studio 2012 'de Fakes ile unstable kodu test etme](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
