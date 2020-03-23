---
title: Test üretimi | Microsoft IntelliTest Geliştirici Test Aracı
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c251a1539b42da2b4e92c2996457075f3c3be135
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302611"
---
# <a name="test-generation"></a>Test oluşturma

Geleneksel birim testinde, bir test birkaç şeyden oluşur:

* Yöntem [çağrıları dizisi](test-generation.md#test-generators)
* Yöntemlerin çağrıldığı bağımsız değişkenler; bağımsız değişkenler [test girişleridir](input-generation.md)
* Bir dizi [iddia](#assumptions-and-assertions) belirterek test edilen uygulamanın amaçlanan davranışının doğrulanması

Aşağıda örnek bir test yapısı verilmiştir:

```csharp
[Test]
void MyTest() {
    // data
    ArrayList a = new ArrayList();

    // method sequence
    a.Add(5);

    // assertions
    Assert.IsTrue(a.Count==1);
    Assert.AreEqual(a[0], 5);
}
```

IntelliTest genellikle otomatik olarak daha genel [Parameterized Birim Testleri](#parameterized-unit-testing)için ilgili argüman değerlerini belirleyebilir , hangi yöntem aramaları ve iddiaları sırasını sağlar.

<a name="test-generators"></a>
## <a name="test-generators"></a>Test oluşturucuları

IntelliTest, yürütmek için test altında uygulama yöntemlerinin bir dizi seçerek test örnekleri oluşturur ve sonra türetilen veriler üzerinde iddiaları denetlerken yöntemler için girişler oluşturur.

[Parametreli birim testi,](#parameterized-unit-testing) gövdesindeki bir dizi yöntem çağrısını doğrudan belirtir.

IntelliTest nesneleri oluşturmak gerektiğinde, yapıcılar ve fabrika yöntemleri çağrıları gerektiği gibi diziotomatik olarak eklenecektir.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Parametreli birim testi

*Parametreli Birim Testleri* (PuTs) parametreleri alan testlerdir. Genellikle kapalı yöntemler olan geleneksel birim testlerinin aksine, PUT'lar herhangi bir dizi parametre alır. Bu kadar basit mi? Evet - oradan, IntelliTest [testten](input-generation.md#dynamic-code-coverage) erişilebilen kodu tam olarak kapsayan [(minimal) giriş kümesini oluşturmaya](input-generation.md) çalışacaktır.

PUT'lar, MsTest 'e (veya NUnit, xUnit) benzer bir şekilde [PexMethod](attribute-glossary.md#pexmethod) özel özniteliği kullanılarak tanımlanır. PUT'lar, [PexClass](attribute-glossary.md#pexclass)ile etiketlenmiş sınıflarda mantıksal olarak gruplanmış örnek yöntemleridir. Aşağıdaki örnek, **MyPexTest** sınıfında depolanan basit bir PUT'u gösterir:

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

**replaceFirstChar** bir dize ilk karakteri yerine bir yöntemdir nerede:

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Bu testten, IntelliTest test edilen kodun birçok yürütme yolunu kapsayan bir PUT için otomatik olarak [giriş oluşturabilir.](input-generation.md) Farklı bir yürütme yolunu kapsayan her giriş birim testi olarak "seri hale" alır:

```csharp
[TestMethod, ExpectedException(typeof(ArgumentNullException))]
void ReplaceFirstChar0() {
    this.ReplaceFirstChar(null, 0);
}
...
[TestMethod]
void ReplaceFirstChar10() {
    this.ReplaceFirstChar("a", 'c');
}
```

<a name="generic-parameterized"></a>
## <a name="generic-parameterized-unit-testing"></a>Genel parametreli birim testi

Parametreli birim testleri genel yöntemler olabilir. Bu durumda, kullanıcı [PexGenericArguments](attribute-glossary.md#pexgenericarguments)kullanarak yöntemi anında belirlemek için kullanılan türleri belirtmelidir.

```csharp
[PexClass]
public partial class ListTest {
    [PexMethod]
    [PexGenericArguments(typeof(int))]
    [PexGenericArguments(typeof(object))]
    public void AddItem<T>(List<T> list, T value)
    { ... }
}
```

<a name="allowing-exceptions"></a>
## <a name="allowing-exceptions"></a>Özel durumlara izin verme

IntelliTest beklenen özel durumlar ve beklenmeyen özel durumlar içine triyaj özel durumlar yardımcı olmak için çok sayıda doğrulama öznitelikleri sağlar.

Beklenen özel durumlar **ExpectedException(typeof(xxx ))*xxx*** gibi uygun ek açıklamayla negatif test örnekleri oluştururken, beklenmeyen özel durumlar başarısız test örnekleri oluşturur.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Doğrulayıcılar şunlardır:

* [PexAllowedException](attribute-glossary.md#pexallowedexception): her yerden belirli bir özel durum türü sağlar
* [PexAllowedExceptionFromAssembly](attribute-glossary.md#pexallowedexceptionfromassembly): belirli bir derlemebelirli bir özel durum türü sağlar
* [PexAllowedExceptionFromType](attribute-glossary.md#pexallowedexceptionfromtype): belirli bir tür belirli bir özel durum türü sağlar
* [PexAllowedExceptionFromTypeUnderTest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): test altındaki türden belirli bir özel durum türüsağlar

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>İç türleri test etme

IntelliTest iç türleri görebildiği sürece "sınayabilir". IntelliTest'in türleri görmesi için Visual Studio IntelliTest sihirbazları tarafından ürün veya test projenize aşağıdaki öznitelik eklenir:

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293")]
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Varsayımlar ve onaylamalar

Kullanıcılar, testleri hakkındaki [ön koşulları](#precondition) (varsayımları) ve [koşulları](#postcondition) (iddiaları) ifade etmek için varsayımları ve iddiaları kullanabilirler. IntelliTest bir parametre değerleri kümesi oluşturduğunda ve kodu "keşfettiğinde" testin varsayımını ihlal edebilir. Bu durumda, bu yol için bir test oluşturmaz, ancak sessizce yok sayar.

İddialar düzenli birim test çerçevelerinde iyi bilinen bir kavramdır, bu nedenle IntelliTest desteklenen her test çerçevesi tarafından sağlanan yerleşik **Assert** sınıflarını zaten "anlar". Ancak, çoğu çerçeve bir **Varsayma** sınıfı sağlamaz. Bu durumda, IntelliTest [PexAssume](static-helper-classes.md#pexassume) sınıfını sağlar. Varolan bir test çerçevesi kullanmak istemiyorsanız, IntelliTest [pexAssert](static-helper-classes.md#pexassert) sınıfına da sahiptir.

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

Özellikle, geçersizlik varsayımı özel bir öznitelik olarak kodlanabilir:

```csharp
[PexMethod]
public void Test2([PexAssumeNotNull] object o)
// precondition: o should not be null
{
   ...
}
```

<a name="precondition"></a>
## <a name="precondition"></a>Ön koşul

Bir yöntemin ön koşulu, yöntemin hangi koşullar altında başarılı olacağını ifade eder.

Genellikle, ön koşul parametreleri ve nesne durumunu denetleyerek ve ihlal edilirse Bir **Bağımsız Değişken Özel Durum** veya Geçersiz **İşlemÖzel Bir** atma tarafından zorlanır.

IntelliTest'te, [parametreli birim testinin](#parameterized-unit-testing) ön koşulu [PexAssume](static-helper-classes.md#pexassume)ile ifade edilir.

<a name="postcondition"></a>
## <a name="postcondition"></a>Son koşul

Bir yöntemin bir postcondition, ön koşullarının başlangıçta geçerli olduğunu varsayarak, yöntemin yürütülmesi sırasında ve sonrasında tutması gereken koşulları ifade eder.

Genellikle, postcondition **Ileri** yöntemleri çağrıları tarafından zorlanır.

IntelliTest ile [parametreli birim testinin](#parameterized-unit-testing) bir son koşulu [PexAssert](static-helper-classes.md#pexassert)ile ifade edilir.

<a name="test-failures"></a>
## <a name="test-failures"></a>Test hataları
Oluşturulan bir test çalışması ne zaman başarısız olur?

1. [Yapılandırılan yol sınırları](exploration-bounds.md)içinde sonlandırmazsa, [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) seçeneği ayarlanmadığı sürece hata olarak kabul edilir

1. Test bir **PexAssumeFailedException**atar, başarılı olur. Ancak, [TestEmissionFilter](exploration-bounds.md#testemissionfilter) **Tüm** olarak ayarlanmazsa genellikle filtrelenir

1. Test bir [iddiayı](#assumptions-and-assertions)ihlal ederse; örneğin, bir birim test çerçevesinin bir iddia ihlali istisnası atarak,

Yukarıdakilerden hiçbiri bir karar vermiyorsa, bir test yalnızca bir özel durum atmazsa başarılı olur. İddia ihlalleri, özel durumlar gibi ele alınır.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Kurulum ve kapatma

Test çerçeveleri ile tümleştirmenin bir parçası olarak, IntelliTest kurulum ve yırtılma yöntemlerini algılamayı ve çalıştırmayı destekler.

**Örnek**

```csharp
using Microsoft.Pex.Framework;
using NUnit.Framework;

namespace MyTests
{
    [PexClass]
    [TestFixture]
    public partial class MyTestClass
    {
        [SetUp]
        public void Init()
        {
            // monitored
        }

        [PexMethod]
        public void MyTest(int i)
        {
        }

        [TearDown]
        public void Dispose()
        {
            // monitored
        }
    }
}
```

<a name="further-reading"></a>
## <a name="further-reading"></a>Daha fazla bilgi

* [Kod bağlama testi](https://devblogs.microsoft.com/devops/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Hepsini yönetmek için bir test](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.
