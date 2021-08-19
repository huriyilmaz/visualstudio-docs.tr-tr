---
title: Uygulamalarınızı dolgularla yalıtma (birim testi)
description: Dolgu türlerini kullanarak çağrıları test kapsamında kod yazmak için belirli yöntemlere yönlendirmeyi öğrenin. Dolgu, her çağrıda tutarlı sonuçlar getireblir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
author: mikejo5000
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 9bba159da05ad3e1c893c3fc241c44cd1c6de8d1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053982"
---
# <a name="use-shims-to-isolate-your-app-for-unit-testing"></a>Birim testi için uygulamanızı yalıtmak için dolgular kullanma

**Dolgu türleri,** Microsoft Fakes Framework'Microsoft Fakes test kapsamındaki bileşenleri ortamdan yalıtmamak için kullandığı teknolojilerden birisidir. Dolgular, çağrıları testin bir parçası olarak kod yazmak için belirli yöntemlere yönlendirin. Birçok yöntem dış koşullara bağlı olarak farklı sonuçlar verir, ancak dolgu testinizin denetimindedir ve her çağrıda tutarlı sonuçlar getirebilirsiniz. Bu, testleri yazmayı kolaylaştırır.

Kodunuzu *çözümünün* parçası olan derlemelerden yalıtmak için dolgular kullanın. Çözüm bileşenlerinizi diğerlerinden yalıtmak için *saplamaları kullanın.*

Genel bakış ve "hızlı başlangıç" kılavuzu için bkz. Microsoft Fakes ile [test altındaki kodu yalıtma.](../test/isolating-code-under-test-with-microsoft-fakes.md)

**Gereksinimler**

- Visual Studio Enterprise
- .NET Framework projesi
::: moniker range=">=vs-2019"
- .NET Core, .NET 5.0 ve SDK stili proje desteği Visual Studio 2019 Güncelleştirme 6'da önizlemeye alındı ve Güncelleştirme 8'de varsayılan olarak etkindir. Daha fazla bilgi için [bkz. .NET Core Microsoft Fakes SDK stili projeleri](/visualstudio/releases/2019/release-notes#microsoft-fakes-for-net-core-and-sdk-style-projects)için bkz. .
::: moniker-end

## <a name="example-the-y2k-bug"></a>Örnek: Y2K hatası

1 Ocak 2000'de özel durum oluşturur bir yöntem düşünün:

```csharp
// code under test
public static class Y2KChecker {
    public static void Check() {
        if (DateTime.Now == new DateTime(2000, 1, 1))
            throw new ApplicationException("y2kbug!");
    }
}
```

Program, bilgisayarın saat, ortama bağımlı, belirlenmci olmayan bir yönteme bağlı olduğundan bu yöntemi test `DateTime.Now` etmek sorunludur. Ayrıca, `DateTime.Now` statik bir özelliktir, bu nedenle saplama türü burada kullanılamaz. Bu sorun, birim testinde yalıtım sorununun belirtisidir: doğrudan veritabanı API'lerine çağrıda bulunduran, web hizmetleriyle iletişim kuran programlar, mantığı ortama bağlı olduğundan birim testi yapmak zordur.

Dolgu türleri burada kullanılmalıdır. Dolgu türleri, herhangi bir .NET yöntemini kullanıcı tanımlı temsilciye sapmak için bir mekanizma sağlar. Dolgu türleri, Fakes oluşturucu tarafından kod oluşturulur ve yeni yöntem uygulamalarını belirtmek için dolgu türleri olarak çağırdiğimiz temsilciler kullanır.

Aşağıdaki test, DateTime.Now özel uygulamasını sağlamak için dolgu `ShimDateTime` türünün nasıl kullanılabını gösterir:

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

## <a name="how-to-use-shims"></a>Dolguları kullanma

İlk olarak, bir Fakes ekleyin:

1. Içinde **Çözüm Gezgini**, 
    - Daha eski bir .NET Framework Project (SDK stili olmayan), birim testi projenizin **Başvurular düğümünü** genişletin.
    ::: moniker range=">=vs-2019"
    - .NET Framework, .NET Core veya .NET 5.0'ı hedef alan SDK stili  bir proje için Bağımlılıklar düğümünü genişleterek  **Derlemeler,** Projeler veya Paketler altında sahtesini yapmak için derlemeyi **bulun.**
    ::: moniker-end
    - Visual Basic'da çalışıyorsanız **Başvurular** düğümünü görmek için **Çözüm Gezgini** araç çubuğunda Tüm **Dosyaları Göster'i** seçin.

2. Dolgu oluşturmak istediğiniz sınıf tanımlarını içeren derlemeyi seçin. Örneğin, **DateTime'ı** dolgu olarak eklemek için **System.dll.**

3. Kısayol menüsünde Derleme **ekle'yi Fakes seçin.**

### <a name="use-shimscontext"></a>ShimsContext kullanma

Birim testi çerçevesinde dolgu türlerini kullanırken, dolguların ömrünü kontrol etmek için test kodunu `ShimsContext` bir içinde sarmalar. Aksi takdirde dolgular AppDomain kapatana kadar devam ediyordur. oluşturmanın en kolay `ShimsContext` yolu, aşağıdaki kodda gösterildiği `Create()` gibi statik yöntemini kullanmaktır:

```csharp
//unit test code
[Test]
public void Y2kCheckerTest() {
  using(ShimsContext.Create()) {
    ...
  } // clear all shims
}
```

Her dolgu bağlamının düzgün bir şekilde atılması kritik öneme sahip. Bir kural olarak, kayıtlı dolguların düzgün bir şekilde temiz `ShimsContext.Create` olduğundan emin olmak için `using` deyiminin içinde çağrısında bulundurarak. Örneğin, yöntemini her zaman Ocak 2000'in ilkini döndüren bir temsilciyle değiştiren bir test yöntemi için dolgu `DateTime.Now` kaydedebilirsiniz. Test yönteminde kayıtlı dolgudan temizlemeyi unutursanız, test çalıştırmalarının geri kalanı her zaman değer olarak Ocak 2000'in ilkini `DateTime.Now` geri döner. Bu şaşırtıcı ve kafa karıştırıcı olabilir.

### <a name="write-a-test-with-shims"></a>Dolgularla test yazma

Test koduna sahtesi *yapmak istediğiniz yöntem* için bir sapma girin. Örnek:

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

Dolgu sınıfı adları, özgün tür adına ön `Fakes.Shim` ek ek olarak yapılır.

Dolgular, test altındaki *uygulamanın koduna* sapmalar ekerek çalışır. Özgün yönteme yapılan her çağrıda, Fakes sistemi bir sapma gerçekleştirir; böylece gerçek yöntemin çağrılma yerine dolgu kodunuz çağrılır.

Sapmaların çalışma zamanında oluşturularak silindi. Her zaman bir yaşam içinde bir sapma oluşturmanız `ShimsContext` gerekir. Atıldığı zaman, etkinken oluşturduğunuz tüm dolgular kaldırılır. Bunu yapmak için en iyi yol deyiminin `using` içindedir.

Ad alanının mevcut olmadığını belirten bir derleme Fakes olabilir. Bu hata bazen başka derleme hataları olduğunda görünür. Diğer hataları düzeltin ve kaybolur.

## <a name="shims-for-different-kinds-of-methods"></a>Farklı yöntem türleri için dolgular

Dolgu türleri, statik yöntemler veya sanal olmayan yöntemler de dahil olmak üzere herhangi bir .NET yöntemini kendi temsilcileriniz ile değiştirmenize olanak sağlar.

### <a name="static-methods"></a>Statik yöntemler

Statik yöntemlere dolgu ekleme özellikleri dolgu türüne yerleştirilir. Her özelliğin yalnızca hedef yönteme temsilci eklemek için kullanılan bir ayarıcısı vardır. Örneğin, statik yöntemine `MyClass` sahip bir sınıf `MyMethod` verilir:

```csharp
//code under test
public static class MyClass {
    public static int MyMethod() {
        ...
    }
}
```

Her zaman 5 döndüren `MyMethod` bir dolgu iliştirmek için:

```csharp
// unit test code
ShimMyClass.MyMethod = () => 5;
```

### <a name="instance-methods-for-all-instances"></a>Örnek yöntemleri (tüm örnekler için)

Statik yöntemlere benzer şekilde örnek yöntemleri de tüm örnekler için dolguya sabit olabilir. Bu dolguları eklemek için özellikler, karışıklığı önlemek için AllInstances adlı iç içe bir türe yerleştirilir. Örneğin, örnek yöntemine `MyClass` sahip bir sınıf `MyMethod` verilir:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

Örneğinden bağımsız olarak her `MyMethod` zaman 5 döndüren bir dolgu iliştirin:

```csharp
// unit test code
ShimMyClass.AllInstances.MyMethod = () => 5;
```

Oluşturulan ShimMyClass tür yapısı aşağıdaki koda benzer:

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

Bu Fakes örneğinin ilk bağımsız değişkeni olarak çalışma zamanı örneğini geçtiğine dikkat edebilirsiniz.

### <a name="instance-methods-for-one-runtime-instance"></a>Örnek yöntemleri (bir çalışma zamanı örneği için)

Örnek yöntemleri, çağrının alıcısına bağlı olarak farklı temsilciler tarafından da dolgulandırabilir. Bu, aynı örnek yönteminin türün örneği başına farklı davranışlara sahip olmasına olanak sağlar. Bu dolguları ayarlama özellikleri, dolgu türünün örnek yöntemleridir. Örneklenmiş her dolgu türü, dolgulu bir türün ham örneğiyle de ilişkilendirildi.

Örneğin, örnek yöntemine `MyClass` sahip bir sınıf `MyMethod` verilir:

```csharp
// code under test
public class MyClass {
    public int MyMethod() {
        ...
    }
}
```

İlki her zaman 5, ikincisinde her zaman 10 döndüren iki MyMethod dolgu türü ayarlamamız gerekir:

```csharp
// unit test code
var myClass1 = new ShimMyClass()
{
    MyMethod = () => 5
};
var myClass2 = new ShimMyClass { MyMethod = () => 10 };
```

Oluşturulan ShimMyClass tür yapısı aşağıdaki koda benzer:

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

Gerçek dolgu türü örneğine Örnek özelliği aracılığıyla erişilebilir:

```csharp
// unit test code
var shim = new ShimMyClass();
var instance = shim.Instance;
```

Dolgu türü de dolgu türüne örtülü bir dönüştürmeye sahip olduğu için genellikle dolgu türünü şu şekilde kullanabilirsiniz:

```csharp
// unit test code
var shim = new ShimMyClass();
MyClass instance = shim; // implicit cast retrieves the runtime instance
```

### <a name="constructors"></a>Oluşturucular

Oluşturucular, gelecekteki nesnelere dolgu türleri eklemek için de dolgulandırabilir. Her oluşturucu dolgu türünde statik bir yöntem Oluşturucusu olarak ortaya çıkar. Örneğin, bir tamsayı alan `MyClass` bir oluşturucu ile bir sınıf verilen:

```csharp
// code under test
public class MyClass {
    public MyClass(int value) {
        this.Value = value;
    }
    ...
}
```

Oluşturucuda değerden bağımsız olarak Değer alıcı çağrıldığında gelecekteki her örneğin -5'i döndürecek şekilde oluşturucusu dolgu türünü ayarlayacağız:

```csharp
// unit test code
ShimMyClass.ConstructorInt32 = (@this, value) => {
    var shim = new ShimMyClass(@this) {
        ValueGet = () => -5
    };
};
```

Her dolgu türü iki oluşturucu gösterir. Yeni bir örnek gerektiğinde varsayılan oluşturucu, bağımsız değişken olarak dolgu örneği alan oluşturucu yalnızca oluşturucu dolgularında kullanılmalıdır:

```csharp
// unit test code
public ShimMyClass() { }
public ShimMyClass(MyClass instance) : base(instance) { }
```

Oluşturulan ShimMyClass tür yapısı aşağıdaki koda benzer:

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

### <a name="base-members"></a>Temel üyeler

Temel üyelerin dolgu özelliklerine, temel tür için bir dolgu oluşturarak ve alt örneği temel dolgu sınıfının oluşturucussine parametre olarak geçirmeyle erişilebilir.

Örneğin, bir örnek yöntemi `MyBase` ve alt türü olan bir sınıf `MyMethod` `MyChild` verildi:

```csharp
public abstract class MyBase {
    public int MyMethod() {
        ...
    }
}

public class MyChild : MyBase {
}
```

Yeni dolgu oluşturarak dolgu ayarlamayı `MyBase` `ShimMyBase` da larız:

```csharp
// unit test code
var child = new ShimMyChild();
new ShimMyBase(child) { MyMethod = () => 5 };
```

Alt dolgu türünün, temel dolgu oluşturucuya parametre olarak geçir kullanıldığında örtülü olarak alt örneğine dönüştürülmesi olduğunu unutmayın.

Oluşturulan ShimMyChild ve ShimMyBase tür yapısı aşağıdaki koda benzer:

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

Dolgu türleri, bir türün `StaticConstructor` statik oluşturucus nedenle statik bir yöntemi ortaya çıkarır. Statik oluşturucular yalnızca bir kez yürütülürken, türün herhangi bir üyesine erişilmeden önce dolgu yapılandırıldığından emin olun.

### <a name="finalizers"></a>Sonlandırıcılar

Sonlandırıcılar, sonlandırıcılar Fakes.

### <a name="private-methods"></a>Özel yöntemler

Kod Fakes oluşturucu, özel yöntemler için yalnızca imzada görünür türlere (parametre türleri ve dönüş türü görünür) sahip dolgu özellikleri oluşturur.

### <a name="binding-interfaces"></a>Bağlama arabirimleri

Dolgulu bir tür bir arabirim uygulayan kod oluşturucu, aynı anda bu arabirimden tüm üyeleri bağlamaya olanak sağlayan bir yöntem yayır.

Örneğin, uygulayan bir `MyClass` sınıf `IEnumerable<int>` verildi:

```csharp
public class MyClass : IEnumerable<int> {
    public IEnumerator<int> GetEnumerator() {
        ...
    }
    ...
}
```

Bind yöntemini çağırarak `IEnumerable<int>` MyClass'daki uygulamalarını dolgu olarak kullanabilirsiniz:

```csharp
// unit test code
var shimMyClass = new ShimMyClass();
shimMyClass.Bind(new List<int> { 1, 2, 3 });
```

Oluşturulan ShimMyClass tür yapısı aşağıdaki koda benzer:

```csharp
// Fakes generated code
public class ShimMyClass : ShimBase<MyClass> {
    public ShimMyClass Bind(IEnumerable<int> target) {
        ...
    }
}
```

## <a name="change-the-default-behavior"></a>Varsayılan davranışı değiştirme

Oluşturulan her dolgu türü, özelliği aracılığıyla `IShimBehavior` arabirimin bir örneğini `ShimBase<T>.InstanceBehavior` tutar. Davranış, bir istemci açıkça dolgul olmayan bir örnek üyesi çağıran her durumda kullanılır.

Davranış açıkça ayarlanmazsa, statik özelliği tarafından döndürülen örneği `ShimBehaviors.Current` kullanır. Varsayılan olarak, bu özellik özel durum döndüren bir davranış `NotImplementedException` döndürür.

Bu davranış herhangi bir dolgu örneğinde özelliği `InstanceBehavior` ayar tarafından herhangi bir zamanda değiştirilebilir. Örneğin, aşağıdaki kod parçacığı dolgu değerini hiçbir şey yapacak veya dönüş türünün varsayılan değerini döndüren bir davranış olarak değiştirir; diğer bir `default(T)` ifade:

```csharp
// unit test code
var shim = new ShimMyClass();
//return default(T) or do nothing
shim.InstanceBehavior = ShimBehaviors.DefaultValue;
```

Bu davranış, statik özelliği ayarlandırarak özelliğin açıkça ayarlanmaması nedeniyle tüm dolgu örnekleri `InstanceBehavior` için genel olarak da `ShimBehaviors.Current` değiştirilebilir:

```csharp
// unit test code
// change default shim for all shim instances
// where the behavior has not been set
ShimBehaviors.Current = ShimBehaviors.DefaultValue;
```

## <a name="detect-environment-accesses"></a>Ortam erişimini algılama

Davranışı ilgili dolgu türünün statik özelliğine ataarak belirli bir türe ait statik yöntemler de dahil olmak üzere tüm üyelere bir `ShimBehaviors.NotImplemented` `Behavior` davranış eklemek mümkündür:

```csharp
// unit test code
// assigning the not implemented behavior
ShimMyClass.Behavior = ShimBehaviors.NotImplemented;
// shorthand
ShimMyClass.BehaveAsNotImplemented();
```

## <a name="concurrency"></a>Eşzamanlılık

Dolgu türleri AppDomain'deki tüm iş parçacıkları için geçerlidir ve iş parçacığı benzitesi yoktur. Eşzamanlılığı destekleyen bir test çalıştırıcısı kullanmayı planlıyorsanız bu önemli bir gerçektir. Dolgu türlerini içeren testler eşzamanlı olarak çalıştıramaz. Bu özellik, çalışma zamanı tarafından Fakes değildir.

## <a name="call-the-original-method-from-the-shim-method"></a>dolgu yönteminden özgün yöntemi çağırma

Imagine yöntemine geçirilen dosya adını doğruladikten sonra metni dosya sistemine yazmak istediğinize emin olun. Bu durumda, dolgu yönteminin ortasında özgün yöntemi çağırarak.

Bu sorunu çözmek için ilk yaklaşım, aşağıdaki kodda olduğu gibi ve temsilci kullanarak özgün `ShimsContext.ExecuteWithoutShims()` yönteme yapılan bir çağrıyı sarmaktır:

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

Başka bir yaklaşım da dolgu değerini null olarak ayarlamak, özgün yöntemi çağırarak dolguları geri yüklemektir.

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

## <a name="systemenvironment"></a>System.Environment

<xref:System.Environment?displayProperty=fullName>dolgusunu eklemek için, Assembly öğesi sonrasında mscorlib.fakes dosyasına aşağıdaki **içeriği** ekleyin:

```xml
<ShimGeneration>
    <Add FullName="System.Environment"/>
</ShimGeneration>
```

Çözümü yeniden oluşturmanın ardından sınıfındaki yöntemler ve özellikler <xref:System.Environment?displayProperty=fullName> dolguyla kullanılabilir, örneğin:

```csharp
System.Fakes.ShimEnvironment.GetCommandLineArgsGet = ...
```

## <a name="limitations"></a>Sınırlamalar

Dolgular, .NET temel sınıf kitaplığı **mscorlib** ve System  .NET Framework ve .NET Core veya .NET 5.0'daki **System.Runtime'daki** tüm türlerde kullanılamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Fakes ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)
- [Peter Provost'un blogu: Visual Studio 2012 dolguları](http://www.peterprovost.org/blog/2012/04/25/visual-studio-11-fakes-part-2)
- [Video (1h16): Visual Studio 2012'de fakes ile test edilemez kod](https://channel9.msdn.com/Events/TechEd/Europe/2012/DEV411)
