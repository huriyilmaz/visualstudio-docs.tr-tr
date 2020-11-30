---
title: Test üretimi | Microsoft IntelliTest geliştirici test aracı
description: IntelliTest 'in uygulamanızın yöntemlerinden test çalışmalarını nasıl ürettireceğinizi öğrenin, ardından yöntemler için girişler oluşturur ve verilerin üzerinde onayları kontrol edin.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 790146e3014765224f22bd247732c7ac3f062269
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329451"
---
# <a name="test-generation"></a>Test oluşturma

Geleneksel birim testinde bir test birkaç şeyin oluşur:

* [Yöntem çağrıları dizisi](test-generation.md#test-generators)
* Yöntemlerin çağrıldığı bağımsız değişkenler; bağımsız değişkenler [Test girişlerdir](input-generation.md)
* Bir [onaylama](#assumptions-and-assertions) kümesi belirterek, sınanan uygulamanın amaçlanan davranışının doğrulanması

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

IntelliTest, genellikle daha genel [parametreli birim testleri](#parameterized-unit-testing)için ilgili bağımsız değişken değerlerini otomatik olarak belirleyebilir ve bu da yöntem çağrılarının ve onayların sırasını sağlar.

<a name="test-generators"></a>
## <a name="test-generators"></a>Test oluşturucuları

IntelliTest, çalıştırılacak test altında uygulamanın Yöntem sırasını seçerek ve ardından türetilmiş veriler üzerinde onayları denetlerken yöntemler için girişler oluşturarak test çalışmaları oluşturur.

[Parametreli birim testi](#parameterized-unit-testing) , gövdesinde bir dizi yöntem çağrısı olduğunu doğrudan belirtir.

IntelliTest 'in nesne oluşturulması gerektiğinde, oluşturuculara ve fabrika yöntemlerine yapılan çağrılar otomatik olarak gerektikçe sıraya eklenir.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Parametreli birim testi

*Parametreli birim testleri* (koyar) parametre alma sınamalardır. Genellikle kapalı Yöntemler olan geleneksel birim testlerin aksine, her bir parametre kümesini alır. Bu basit midir? Evet-buradan, IntelliTest, testten erişilebilen kodu [tamamen kapsayan](input-generation.md#dynamic-code-coverage) [girişlerin (minimal) bir kümesini oluşturmaya](input-generation.md) çalışır.

Koyar, MSTest (veya NUnit, xUnit) ile benzer bir biçimde [PexMethod](attribute-glossary.md#pexmethod) özel özniteliği kullanılarak tanımlanır. Koyar, [PexClass](attribute-glossary.md#pexclass)ile etiketlenmiş sınıflarda mantıksal olarak gruplanmış örnek yöntemlerdir. Aşağıdaki örnek **Mypextest** sınıfında saklanan basıt bir put öğesini göstermektedir:

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

Burada **Replacefirstchar** bir dizenin ilk karakterinin yerini alan bir yöntemdir:

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Bu testten, IntelliTest, test edilmiş kodun birçok yürütme yolunu içeren bir PUT için otomatik olarak [giriş](input-generation.md) oluşturabilir. Farklı bir yürütme yolunu kaplayan her giriş, birim testi olarak "serileştirilmiş" alır:

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

Parametreli birim testleri genel yöntemler olabilir. Bu durumda, kullanıcının [Pexgenericarguments](attribute-glossary.md#pexgenericarguments)kullanarak yöntemi örneğini oluşturmak için kullanılan türleri belirtmesi gerekir.

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

IntelliTest, özel durumların beklenen özel durumlara ve beklenmeyen özel durumlara yönelik önceliklendirme sağlamak için çok sayıda doğrulama özniteliği sağlar

Beklenen özel durumlar, **ExpectedException (typeof (*XXX*))** gibi uygun ek açıklamayla negatif test çalışmaları oluşturur, ancak beklenmeyen özel durumlar başarısız test çalışmaları oluşturur.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Doğrulayıcılar şunlardır:

* [Pexallowedexception](attribute-glossary.md#pexallowedexception): belirli bir özel durum türünün her yerden izin verir
* [Pexallowedexceptionfromassembly](attribute-glossary.md#pexallowedexceptionfromassembly): belirtilen derlemeden belirli bir özel durum türüne izin verir
* [Pexallowedexceptionfromtype](attribute-glossary.md#pexallowedexceptionfromtype): belirtilen türden belirli bir özel durum türüne izin verir
* [Pexallowedexceptionfromtypeundertest](attribute-glossary.md#pexallowedexceptionfromtypeundertest): test altındaki türden belirli bir özel durum türüne izin verir

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>İç türleri test etme

IntelliTest, onları görebileceğiniz sürece "test" iç türlerini "test edebilir". Türü görmek için IntelliTest için aşağıdaki öznitelik, Visual Studio IntelliTest sihirbazları tarafından ürün veya test projenize eklenir:

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293")]
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Varsayımlar ve onaylamalar

Kullanıcılar, testleri hakkında ön koşullar (varsayımlar) ve [Sonkoşulları](#postcondition) [(onaylar](#precondition) ) için varsayımlar ve onaylamaları kullanabilir. IntelliTest bir dizi parametre değeri oluşturduğunda ve kodu "araştırır", testin bir varsayımını ihlal edebilir. Söz konusu olduğunda, bu yol için bir test oluşturmaz, ancak sessizce yoksayacaktır.

Onaylar normal birim testi çerçevelerinizdeki iyi bilinen bir kavramdır. bu nedenle IntelliTest, desteklenen her test çerçevesi tarafından sunulan yerleşik **onay sınıflarını zaten** "anladı". Ancak, çoğu Framework bir **varsay** sınıfı sağlamaz. Bu durumda, IntelliTest [Pexvarsay](static-helper-classes.md#pexassume) sınıfını sağlar. Mevcut bir test çerçevesini kullanmak istemiyorsanız, IntelliTest [Pexonaylama](static-helper-classes.md#pexassert) sınıfına de sahiptir.

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

Özellikle, boş olmayan varsayımına özel bir öznitelik olarak kodlanabilen:

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

Bir yöntemin önkoşulunu yöntemin başarılı olacağı koşulları ifade eder.

Genellikle, önkoşul, parametreleri ve nesne durumunu denetleyerek ve ihlal edilirse bir **ArgumentException** veya **InvalidOperationException** oluşturarak zorlanır.

IntelliTest 'de, [parametreli birim testinin](#parameterized-unit-testing) bir önkoşulu, [pexvarsay](static-helper-classes.md#pexassume)ile ifade edilir.

<a name="postcondition"></a>
## <a name="postcondition"></a>Son koşul

Bir yöntemin sonkoşulu, bir yöntemin yürütülmesi sırasında ve sonrasında saklanması gereken koşulları ifade eder ve bu durum, önkoşullarının başlangıçta geçerli olduğunu varsayar.

Genellikle, Sonkoşul **onaylama** yöntemlerine yapılan çağrılar tarafından zorlanır.

IntelliTest ile, [parametreli birim testinin](#parameterized-unit-testing) bir sonkoşulu [pexonaylama](static-helper-classes.md#pexassert)ile ifade edilir.

<a name="test-failures"></a>
## <a name="test-failures"></a>Test hataları
Oluşturulan test çalışması ne zaman başarısız olur?

1. [Yapılandırılmış yol sınırları](exploration-bounds.md)içinde Sonlanmamışsa, [Testexcludepathboundsexceılsınıo](exploration-bounds.md#testexcludepathboundsexceeded) seçeneği ayarlanmamışsa hata olarak kabul edilir

1. Test bir **PexAssumeFailedException** oluşturursa başarılı olur. Ancak, [Testemissionfilter](exploration-bounds.md#testemissionfilter) **Tümü** olarak ayarlanmadığı takdirde genellikle filtrelenir.

1. Test bir [onaylama işlemi](#assumptions-and-assertions)ihlal ederse; Örneğin, bir birim testi çerçevesinin bir onaylama ihlali özel durumu oluşturarak başarısız olur

Yukarıdakilerden hiçbiri bir karar üretmezse, ve yalnızca bir özel durum oluşturmuyorsa test başarılı olur. Onaylama ihlalleri özel durumlarla aynı şekilde işlenir.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Kurulum ve kapatma

Test çerçeveleri ile tümleştirmenin bir parçası olarak, IntelliTest, kurulum ve ayırma yöntemlerini algılayıp çalıştırmayı destekler.

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

* [Kod bağlamaya test](https://devblogs.microsoft.com/devops/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Tümünü kurala göre bir test](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.
