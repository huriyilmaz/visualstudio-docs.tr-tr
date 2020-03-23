---
title: Birim testi için uygulamanızı yalıtmak için şimler kullanma
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 480283b4f86f28fdedfb38687682fcee4e67646e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585541"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>Birim testi için uygulamanızı yalıtmak için şim'leri kullanın

**Shim türleri,** Microsoft Fakes Framework'ün, test altındaki bileşenleri ortamdan yalıtmanıza izin vermek için kullandığı iki teknolojiden biridir. Şimler, testinizin bir parçası olarak yazdığınız kodiçin çağrıları belirli yöntemlere yönlendirir. Birçok yöntem dış koşullara bağlı olarak farklı sonuçlar döndürebilir, ancak bir şim testinizin denetimi altındadır ve her çağrıda tutarlı sonuçlar döndürebilir. Bu, testleri yazmayı kolaylaştırır.

Kodunuzu çözümünüzün bir parçası olmayan derlemelerden ayırmak için *şimler* kullanın. Çözeltinizin bileşenlerini birbirinden ayırmak için *saplamalar*kullanın.

Genel bakış ve "hızlı başlangıç" kılavuzu için, [Microsoft Fakes ile test altında kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)'ya bakın.

**Gereksinimler**

- Visual Studio Enterprise
- A .NET Framework projesi

> [!NOTE]
> .NET Standart projeler desteklenmez.

## <a name="example-the-y2k-bug"></a>Örnek: Y2K hata

1 Ocak 2000'de özel bir durum sağlayan bir yöntem düşünün:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Program, `DateTime.Now`bilgisayarın saatine, ortama bağımlı, deterministik olmayan bir yönteme bağlı olduğu için bu yöntemin sınanması sorunludur. Ayrıca, bir `DateTime.Now` saplama türü burada kullanılamaz bu yüzden statik bir özelliktir. Bu sorun birim testinde izolasyon sorununun belirtisidir: doğrudan veritabanı API'lerine çağrı yapan, web hizmetleriyle iletişim kurabilen ve benzeri programlar, mantıkları ortama bağlı olduğundan testi birleştirmek zordur.

Bu, şim türlerinin kullanılması gereken yerdir. Shim türleri, kullanıcı tanımlı bir temsilciye herhangi bir .NET yöntemini saptamak için bir mekanizma sağlar. Şim türleri Fakes jeneratörü tarafından kod tarafından oluşturulur ve yeni yöntem uygulamalarını belirtmek için şim türleri dediğimiz temsilcileri kullanırlar.

Aşağıdaki test, DateTime.Now özel `ShimDateTime`bir uygulama sağlamak için, şim türünü nasıl kullanılacağını gösterir:

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

## <a name="how-to-use-shims"></a>Şimler nasıl kullanılır?

İlk olarak, bir Fakes derlemesi ekleyin:

1. **Çözüm Gezgini'nde,** birim test projenizin **Başvurudüğümü** genişletin.

   - Visual Basic'te çalışıyorsanız, **Başvurudüğümünü** görmek için **Çözüm Gezgini** araç çubuğundaki **Tüm Dosyaları Göster'i** seçin.

2. Şimler oluşturmak istediğiniz sınıf tanımlarını içeren derlemeyi seçin. Örneğin, **DateTime'ı**şimlemek istiyorsanız **System.dll'yi**seçin.

3. Kısayol menüsünde **Sahte Derleme Ekle'yi**seçin.

### <a name="use-shimscontext"></a>ShimsContext kullanın

Birim test çerçevesinde şim türlerini kullanırken, şimlerinizin ömrünü denetlemek için test kodunu a'da `ShimsContext` kaydırın. Aksi takdirde, appdomain kapanana kadar şimler sürecekti. A `ShimsContext` oluşturmanın en kolay yolu, `Create()` aşağıdaki kodda gösterildiği gibi statik yöntemi kullanmaktır:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Her şim bağlamını düzgün bir şekilde atmak çok önemlidir. Başparmak bir kural olarak, `ShimsContext.Create` kayıtlı `using` şimler doğru temizlenmesini sağlamak için bir ifadenin içini arayın. Örneğin, `DateTime.Now` yöntemi her zaman Ocak 2000'in ilkini döndüren bir temsilciyle değiştiren bir test yöntemi için bir şim kaydedebilirsiniz. Test yönteminde kayıtlı şimi temizlemeyi unutursanız, test çalışmasının geri kalanı her zaman Ocak `DateTime.Now` 2000'in ilk ini değer olarak döndürer. Bu şaşırtıcı ve kafa karıştırıcı olabilir.

### <a name="write-a-test-with-shims"></a>Şimlerle test yazın

Test kodunuza, sahtesini yapmak istediğiniz yöntem için bir *sapma* ekleyin. Örnek:

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

Şim sınıf adları özgün tür `Fakes.Shim` adına önseki yle oluşur.

Şimler, test altındaki uygulamanın koduna *sapmalar* ekleyerek çalışır. Orijinal yönteme çağrı nerede gerçekleşirse gerçekleşsin, Sahte sistem bir sapma gerçekleştirir, böylece gerçek yöntemi aramak yerine şim kodunuz çağrılır.

Detours oluşturulan ve çalışma zamanında silinir dikkat edin. Her zaman bir `ShimsContext`yaşam içinde bir dolambaçlı oluşturmanız gerekir. Bertaraf edildiğinde, etkinken oluşturduğunuz tüm shims kaldırılır. Bunu yapmanın en iyi yolu `using` bir ifade içinde.

Sahte ad alanının var olmadığını belirten bir yapı hatası görebilirsiniz. Bu hata bazen başka derleme hataları olduğunda görünür. Diğer hataları düzeltin ve kaybolur.

## <a name="shims-for-different-kinds-of-methods"></a>Farklı yöntemler için şimler

Şim türleri, statik yöntemler veya sanal olmayan yöntemler de dahil olmak üzere herhangi bir .NET yöntemini kendi temsilcilerinizle değiştirmenize olanak sağlar.

### <a name="static-methods"></a>Statik yöntemler

Statik yöntemlere şim eklemek için özellikleri bir şim türüne yerleştirilir. Her özellik, hedef yönteme bir temsilci eklemek için kullanılabilecek yalnızca bir ayarlayıcıvardır. Örneğin, statik bir `MyClass` yöntem `MyMethod`ile bir sınıf verilen:

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

Biz her zaman 5 `MyMethod` döner bir şim ekleyebilirsiniz:

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>Örnek yöntemleri (tüm örnekler için)

Statik yöntemlere benzer şekilde, örnek yöntemleri tüm örnekler için shimmed olabilir. Bu şimleri ekleyen özellikler, karışıklığı önlemek için AllInstances adlı iç içe geçen bir türe yerleştirilir. Örneğin, örnek yöntemi `MyClass` `MyMethod`olan bir sınıf verilir:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Örnekten bağımsız olarak, `MyMethod` her zaman 5 döndürür bir şim ekleyebilirsiniz:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

ShimMyClass'ın oluşturulan tür yapısı aşağıdaki koda benzer:

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

Fakes'in bu durumda temsilcinin ilk bağımsız değişkeni olarak çalışma zamanı örneğini geçtiğine dikkat edin.

### <a name="instance-methods-for-one-runtime-instance"></a>Örnek yöntemleri (bir çalışma zamanı örneği için)

Örnek yöntemleri, çağrının alıcısına bağlı olarak farklı temsilciler tarafından da şımamada bulunabilir. Bu, aynı örnek yönteminin türü örnek başına farklı davranışlara sahip olmasını sağlar. Bu şimleri ayarlamak için özellikler, şim türünün örnek yöntemleridir. Her anlık şim türü de bir shimmed türü ham bir örneği ile ilişkilidir.

Örneğin, örnek yöntemi `MyClass` `MyMethod`olan bir sınıf verilir:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

MyMethod'un iki şim tipini ayarlayabiliriz, bunlardan ilki her zaman 5, ikincisi ise her zaman 10'u döndürür:

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

ShimMyClass'ın oluşturulan tür yapısı aşağıdaki koda benzer:

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

Gerçek shimmed türü örneği Örnek özelliği üzerinden erişilebilir:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Şim türü de şimmli türüne örtülü bir dönüştürme vardır, bu nedenle genellikle sadece olduğu gibi şim türünü kullanabilirsiniz:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>Oluşturucular

Kurucular da gelecekteki nesnelere şim türleri eklemek için shimmed olabilir. Her yapıcı şim türünde statik bir yöntem Yapıcı olarak ortaya çıkarır. Örneğin, bir kurucu `MyClass` bir tamsayı alarak bir sınıf verilir:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Kurucunun şim türünü, kurucudaki değerden bağımsız olarak, Değer gettoru çağrıldığınızda -5'i gelecekteki her örneğin döndürür:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Her şim türü iki oluşturucuortaya çıkarır. Varsayılan oluşturucu, yeni bir örnek gerektiğinde, kurucu bağımsız değişken olarak parıldayan bir örneği alarak yalnızca oluşturucu şimlerde kullanılmalıdır:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

ShimMyClass'ın oluşturulan tür yapısı aşağıdaki kodu benzer:

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

### <a name="base-members"></a>Taban üyeler

Temel üyelerin şim özelliklerine, taban türü için bir şim oluşturarak ve alt örneği temel şim sınıfının oluşturucuya parametre olarak geçirerek erişilebilir.

Örneğin, örnek yöntemi `MyBase` `MyMethod` ve bir alt türü `MyChild`olan bir sınıf verilir:

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

Biz yeni `ShimMyBase` bir şim `MyBase` oluşturarak bir şim ayarlayabilirsiniz:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Alt şim türü, temel şim oluşturucuya parametre olarak geçtiğinde örtük olarak alt örneğe dönüştürülür.

ShimMyChild ve ShimMyBase'in oluşturulan tür yapısı aşağıdaki kodu benzer:

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

### <a name="static-constructors"></a>Statik yapıcılar

Şim türleri, bir `StaticConstructor` türün statik oluşturucuyu şimlemek için statik bir yöntem ortaya çıkarır. Statik oluşturucular yalnızca bir kez yürütüldeceğinden, türdeki herhangi bir üyeye erişilmeden önce şim'in yapılandırıldığından emin olmanız gerekir.

### <a name="finalizers"></a>Sonlandırıcılar

Finalizers Fakes desteklenmez.

### <a name="private-methods"></a>Özel yöntemler

Fakes kod üreteci, yalnızca imzada görünür türleri olan özel yöntemler için şim özellikleri oluşturur, yani parametre türleri ve görünür dönüş türü.

### <a name="binding-interfaces"></a>Bağlama arabirimleri

Bir şimmli tür bir arabirim uyguladığında, kod üreteci bu arabirimdeki tüm üyeleri aynı anda bağlamasına olanak tanıyan bir yöntem yayır.

Örneğin, uygulayan bir `MyClass` sınıf `IEnumerable<int>`verilir:

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

Bind yöntemini arayarak `IEnumerable<int>` MyClass'taki uygulamaları shimedebilirsiniz:

```csharp
// unit test code
var shimMyClass = new ShimMyClass();
shimMyClass.Bind(new List<int> { 1, 2, 3 });
```

ShimMyClass'ın oluşturulan tür yapısı aşağıdaki kodu benzer:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public ShimMyClass Bind(IEnumerable<int> target) {
        ...
    }
}
```

## <a name="change-the-default-behavior"></a>Varsayılan davranışı değiştirme

Oluşturulan her şim türü, `IShimBehavior` özellik aracılığıyla `ShimBase<T>.InstanceBehavior` arabirimin bir örneğini tutar. Davranış, bir istemci açıkça shimmed olmayan bir örnek üye çağırır zaman kullanılır.

Davranış açıkça ayarlanmadıysa, statik `ShimsBehaviors.Current` özellik tarafından döndürülen örneği kullanır. Varsayılan olarak, bu özellik bir özel `NotImplementedException` durum atan bir davranış döndürür.

Bu davranış, herhangi bir şim `InstanceBehavior` örneğinde özelliği ayarlayarak herhangi bir zamanda değiştirilebilir. Örneğin, aşağıdaki parçacık, şimi hiçbir şey yapmayan veya iade türünün varsayılan değerini döndüren `default(T)`bir davranışla değiştirir— diğer bir

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimsBehaviors.DefaultValue;
```

Davranış, statik `InstanceBehavior` `ShimsBehaviors.Current` özelliği ayarlayarak özelliğin açıkça ayarlanmadığı tüm shimmed örnekleri için genel olarak değiştirilebilir:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimsBehaviors.Current = ShimsBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>Ortam erişimlerini algılama

Davranışı ilgili şim türünün statik özelliğine `ShimsBehaviors.NotImplemented` `Behavior` atayarak, belirli bir türdeki statik yöntemler de dahil olmak üzere tüm üyelere bir davranış eklemek mümkündür:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimsBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>Eşzamanlılık

Shim türleri AppDomain'deki tüm iş parçacıkları için geçerlidir ve iş parçacığı yakınlığı yoktur. Eşzamanlılığı destekleyen bir test koşucusu kullanmayı planlıyorsanız, bu önemli bir gerçektir. Şim türlerini içeren testler aynı anda çalıştırılamaz. Bu özellik Fakes çalışma zamanı tarafından zorlanmaz.

## <a name="call-the-original-method-from-the-shim-method"></a>Orijinal yöntemi şim yönteminden arayın

Yönteme geçen dosya adını doğruladıktan sonra metni dosya sistemine yazmak istediğinizi düşünün. Bu durumda, şim yönteminin ortasında orijinal yöntemi çağırırsınız.

Bu sorunu çözmek için ilk yaklaşım, bir temsilci kullanarak özgün `ShimsContext.ExecuteWithoutShims()`yönteme bir çağrı sarmak ve , aşağıdaki kod gibi:

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

Başka bir yaklaşım, şim'i null'a ayarlamak, özgün yöntemi aramak ve şimi geri yüklemektir.

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

## <a name="systemenvironment"></a>Sistem.Çevre

Shim <xref:System.Environment?displayProperty=fullName>için, **Derleme** öğesi sonra mscorlib.fakes dosyasına aşağıdaki içeriği ekleyin:

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

Çözümü yeniden oluşturmadan sonra, sınıfdaki <xref:System.Environment?displayProperty=fullName> yöntemler ve özellikler, örneğin aşağıdakileri görmek için kullanılabilir:

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>Sınırlamalar

.NET taban sınıf kitaplığı **mscorlib** ve **System'den**her türlü şimler kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Fakes ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Peter Provost günlüğü: Visual Studio 2012 shims](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Video (1h16): Visual Studio 2012'de sahteleriyle test edilemeyen kodları test etme](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
