---
title: Test oluşturma | Microsoft IntelliTest Geliştirici Test Aracı
description: IntelliTest'in uygulama yöntemlerinizin yöntemlerinden test çalışmalarını nasıl oluştur olduğunu öğrenin, ardından yöntemler için girişler üretir ve veriler üzerinde onayları kontrol edin.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Test generation
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: fd7c9b667e2c355267a22212684141a40bca9f7c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148434"
---
# <a name="test-generation"></a>Test oluşturma

Geleneksel birim testinde test birkaç şeyden oluşur:

* Yöntem [çağrıları dizisi](test-generation.md#test-generators)
* Yöntemlerin çağrıldı olduğu bağımsız değişkenler; bağımsız değişkenleri [test girişleridir](input-generation.md)
* Bir dizi onay belirterek test edilmiş uygulamanın amaçlanan [davranışını doğrulama](#assumptions-and-assertions)

Aşağıdaki örnek bir test yapısıdır:

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

IntelliTest genellikle daha genel Parametreli [](#parameterized-unit-testing)Birim Testleri için ilgili bağımsız değişken değerlerini otomatik olarak belirler ve bu da yöntem çağrılarının ve onaylarının sırasını sağlar.

<a name="test-generators"></a>
## <a name="test-generators"></a>Test oluşturucuları

IntelliTest, yürütülecek test kapsamında uygulamanın bir dizi yöntemini seçerek ve ardından türetilmiş veriler üzerinde onayları kontrol ederken yöntemler için girişler oluşturarak test çalışmaları üretir.

Parametreli [birim testi](#parameterized-unit-testing) doğrudan gövdesinde bir dizi yöntem çağrısı belirtir.

IntelliTest'in nesneleri oluşturması gerektiğinde, oluşturuculara ve fabrika yöntemlerine yapılan çağrılar gerektiğinde otomatik olarak diziye eklenir.

<a name="parameterized-unit-testing"></a>
## <a name="parameterized-unit-testing"></a>Parametreli birim testi

*Parametreli Birim Testleri* (PUT), parametre alan testlerdir. Genellikle kapalı yöntemler olan geleneksel birim testlerinin aksine, PUT'lar herhangi bir parametre kümesi alır. Bu kadar basit mi? Evet - Buradan IntelliTest, testten ulaşılabilir kodu tamamen [](input-generation.md#dynamic-code-coverage) [kapsatan (minimum)](input-generation.md) giriş kümesi oluşturmayı dener.

PUT'lar [PexMethod](attribute-glossary.md#pexmethod) özel özniteliği MSTest 'e (veya NUnit, xUnit) benzer şekilde kullanılarak tanımlanır. PUT'lar PexClass ile etiketlenmiş sınıflarda mantıksal olarak gruplanan [örnek yöntemleridir.](attribute-glossary.md#pexclass) Aşağıdaki örnek, **MyPexTest** sınıfında depolanan basit bir PUT'i gösterir:

```csharp
[PexMethod]
void ReplaceFirstChar(string target, char c) {

    string result = StringHelper.ReplaceFirstChar(target, c);

    Assert.AreEqual(result[0], c);
}
```

burada **ReplaceFirstChar,** bir dizenin ilk karakterinin yerini alan bir yöntemdir:

```csharp
class StringHelper {
    static string ReplaceFirstChar(string target, char c) {
        if (target == null) throw new ArgumentNullException();
        if (target.Length == 0) throw new ArgumentOutOfRangeException();
        return c + target.Substring(1);
    }
}
```

Bu testten IntelliTest, test edilen [kodun](input-generation.md) birçok yürütme yolunu kapsayan bir PUT için otomatik olarak girişler oluşturabilir. Farklı bir yürütme yolunu kapsayan her giriş, birim testi olarak "seri hale getirildi" olur:

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

Parametreli birim testleri genel yöntemler olabilir. Bu durumda, kullanıcının [PexGenericArguments](attribute-glossary.md#pexgenericarguments)kullanarak yönteminin örneğini belirlemek için kullanılan türleri belirtmesi gerekir.

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

IntelliTest, özel durumları beklenen özel durumlar ve beklenmeyen özel durumlar olarak triyale etmeye yardımcı olmak için çok sayıda doğrulama özniteliği sağlar.

Beklenen özel **durumlar, BeklenenException(typeof(*xxx*))** gibi uygun ek açıklamayla negatif test çalışmalarına neden olurken beklenmeyen özel durumlar başarısız test çalışmalarına neden olur.

```csharp
[PexMethod, PexAllowedException(typeof(ArgumentNullException))]
void SomeTest() {...}
```

Doğrulayıcılar:

* [PexAllowedException:](attribute-glossary.md#pexallowedexception)her yerden belirli bir özel durum türüne izin verir
* [PexAllowedExceptionFromAssembly:](attribute-glossary.md#pexallowedexceptionfromassembly)Belirtilen derlemeden belirli bir özel durum türüne izin verir
* [PexAllowedExceptionFromType:](attribute-glossary.md#pexallowedexceptionfromtype)Belirtilen türden belirli bir özel durum türüne izin verir
* [PexAllowedExceptionFromTypeUnderTest:](attribute-glossary.md#pexallowedexceptionfromtypeundertest)test altındaki türden belirli bir özel durum türüne izin verir

<a name="internal-types"></a>
## <a name="testing-internal-types"></a>İç türleri test etme

IntelliTest, iç türleri görene kadar "test"ler. IntelliTest'in türleri görmek için, intelliTest sihirbazları tarafından ürün veya test Visual Studio eklenir:

```csharp
[assembly: InternalsVisibleTo("Microsoft.Pex, PublicKey=002400000480000094000000060200000024000052534131000400000100010007d1fa57c4aed9f0a32e84aa0faefd0de9e8fd6aec8f87fb03766c834c99921eb23be79ad9d5dcc1dd9ad236132102900b723cf980957fc4e177108fc607774f29e8320e92ea05ece4e821c0a5efe8f1645c4c0c93c1ab99285d622caa652c1dfad63d745d6f2de5f17e5eaf0fc4963d261c8a12436518206dc093344d5ad293")]
```

<a name="assumptions-and-assertions"></a>
## <a name="assumptions-and-assertions"></a>Varsayımlar ve onaylamalar

Kullanıcılar, testleriyle ilgili önkoşulları [](#precondition) (varsayımları) ve sonkoşulları (onaylar) ifade etmek için varsayımları ve onayları kullanabilir. [](#postcondition) IntelliTest bir parametre değerleri kümesi oluşturması ve kodu "keşfetmesi", testin varsayımlarını ihlal ediyor olabilir. Bu durumda, bu yol için bir test oluşturmaz, ancak sessizce yoksayar.

Onaylar normal birim testi çerçeveleri içinde iyi bilinen bir kavramdır, bu nedenle IntelliTest desteklenen her test çerçevesi tarafından sağlanan yerleşik **Assert** sınıflarını zaten "anlar". Ancak, çoğu çerçeve bir **Assume sınıfı** sağlamaz. Bu durumda IntelliTest [PexAssume sınıfını](static-helper-classes.md#pexassume) sağlar. Mevcut bir test çerçevesini kullanmak istemiyorsanız, IntelliTest [pexAssert sınıfına da](static-helper-classes.md#pexassert) sahip olur.

```csharp
[PexMethod]
public void Test1(object o) {
    // precondition: o should not be null
    PexAssume.IsNotNull(o);

    ...
}
```

Özellikle, null olmayan varsayım özel bir öznitelik olarak kodlanmış olabilir:

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

Bir yöntemin önkoşulları, yöntemin başarılı olduğu koşulları ifade ediyor.

Genellikle önkoşul, parametreler ve nesne durumu denetlenerek ve ihlal edilirse **ArgumentException** veya **InvalidOperationException** atarak zorlar.

IntelliTest'te parametreli birim [testinin](#parameterized-unit-testing) önkoşulları [PexAssume ile ifade edildi.](static-helper-classes.md#pexassume)

<a name="postcondition"></a>
## <a name="postcondition"></a>Son koşul

Yöntemin sonkoşulları, yöntemin yürütülmesi sırasında ve sonrasında, önkoşullarının başlangıçta geçerli olduğunu varsayarak tutması gereken koşulları ifade ediyor.

Genellikle sonkoşul Assert yöntemlerine yapılan **çağrılar tarafından** zorlar.

IntelliTest ile parametreli birim testinin [sonkoşulları](#parameterized-unit-testing) [PexAssert ile ifade edildi.](static-helper-classes.md#pexassert)

<a name="test-failures"></a>
## <a name="test-failures"></a>Test hataları
Oluşturulan bir test çalışma ne zaman başarısız olur?

1. Yapılandırılmış yol sınırları içinde [](exploration-bounds.md)sonlandırılmazsa [TestExcludePathBoundsExceeded](exploration-bounds.md#testexcludepathboundsexceeded) seçeneği ayarlanmazsa hata olarak kabul edilir

1. Test bir **PexAssumeFailedException atarsa** başarılı olur. Ancak [TestEmissionFilter,](exploration-bounds.md#testemissionfilter) All olarak ayarlanmadıkça genellikle **filtrelenmiş olur**

1. Test bir onaylamayı ihlal [ediyorsa;](#assumptions-and-assertions) Örneğin, bir birim testi çerçevesinin onay ihlali özel durumu atarak başarısız olur

Yukarıdakilerin hiçbiri karar vermezse, yalnızca özel durum oluşturursa ve yoksa test başarılı olur. Onaylama ihlalleri, özel durumlar gibi kabul edilir.

<a name="setup-teardown"></a>
## <a name="setup-and-tear-down"></a>Kurulum ve kapatma

IntelliTest, test çerçeveleriyle tümleştirmenin bir parçası olarak kurulum ve çalıştırma yöntemlerini algılamayı ve çalıştırmayı destekler.

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

* [Kod bağlamayı test etmek](https://devblogs.microsoft.com/devops/smart-unit-tests-test-to-code-binding-test-case-management/)
* [Hepsini kurala göre karara varan bir test](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://aka.ms/feedback/suggest?space=8)’na gönderin.
