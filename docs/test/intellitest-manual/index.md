---
title: Genel Bakış | Microsoft IntelliTest Geliştirici Test Aracı
description: IntelliTest'in otomatikleştirilmiş ve saydam bir test yaklaşımını nasıl kullandığını öğrenin. IntelliTest.NET kodunuz için bir aday test paketi oluşturabilir.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e17f61311b321bc7f531ba746bd05060fdcf888f
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517703"
---
# <a name="overview-of-microsoft-intellitest"></a>Microsoft IntelliTest’e Genel Bakış

IntelliTest, hataları erkenden bulmanıza olanak sağlar ve test bakımı maliyetlerini düşürür. IntelliTest, otomatikleştirilmiş ve şeffaf bir test yaklaşımı kullanarak .NET kodunuz için bir aday test paketi oluşturabilir. Belirttiğiniz *doğruluk özellikleri*, test paketi oluşturma işlemine daha fazla yol gösterebilir. IntelliTest, test edilen kod geliştikçe, otomatik olarak test paketini de geliştirir.

> [!NOTE]
> ıntellitest yalnızca Enterprise sürümünde kullanılabilir. .NET Framework hedefleyen C# kodu için desteklenir. .NET Core ve .NET Standard Şu anda desteklenmiyor.

**Karakterizasyon testleri** IntelliTest, geleneksel birim testi paketi açısından kodun davranışını belirlemenize olanak sağlar.
Böyle bir test paketi, gerileme paketi olarak kullanılabilir ve eski veya bilindik olmayan kodun yeniden düzenlenmesiyle ilişkili karmaşıklığın giderilmesinde temeli oluşturur.

**Kılavuzlu test girişi oluşturma** IntelliTest, genellikle herhangi bir kullanıcı müdahalesi olmadan hassas test girişi değerlerini otomatik olarak oluşturmak için açık kod analizi ve kısıtlamayı giderme yaklaşımını benimser. Karmaşık nesne türleri için otomatik olarak üreteçler oluşturur. Üreteçleri gereksinimlerinize uygun şekilde genişletip yapılandırarak test girişi oluşturma işlemine yol gösterebilirsiniz. Kodda onay deyimi olarak belirtilen doğruluk özellikleri, test girişi oluşturma işlemine yol göstermek için otomatik olarak da kullanılır.

**IDE tümleştirmesi** IntelliTest, Visual Studio IDE ile tamamen tümleşiktir. Test paketi oluşturma sırasında toplanan tüm bilgiler (örn. otomatik olarak oluşturulan girişler, kodunuzun çıktısı, oluşturulan test çalışmaları ve bunların başarı veya başarısızlık durumu), Visual Studio IDE içinde görüntülenir. Visual Studio IDE’den çıkmadan kodunuzu düzeltme ile IntelliTest’i yeniden çalıştırma arasında kolayca yineleme yapabilirsiniz.
Testler bir Birim Testi Projesi olarak çözüme kaydedilebilir ve daha sonra Visual Studio Test Gezgini tarafından otomatik olarak algılanır.

**Mevcut test uygulamalarını tamamlama** Hali hazırda takip ediyor olabileceğiniz tüm mevcut test uygulamalarını tamamlamak için IntelliTest’i kullanın.

Test etmek istiyorsanız:

* Temel veriler veya temel veri dizileri üzerinde algoritmalar:
  * [parametreli birim testleri](test-generation.md#parameterized-unit-testing) yazın
* Derleyici gibi, karmaşık veriler üzerinde algoritmalar:
  * IntelliTest’in önce verilerin soyut temsilini oluşturmasını ve sonra bunu algoritmaya beslemesini sağlayın
  * IntelliTest’in [özel nesne oluşturma](input-generation.md#objects) ve veri sabitlerini kullanarak örnekler derlemesini ve sonra algoritmayı çağırmasını sağlayın
* Veri kapsayıcıları:
  * [parametreli birim testleri](test-generation.md#parameterized-unit-testing) yazın
  * IntelliTest’in [özel nesne oluşturma](input-generation.md#objects) ve veri sabitlerini kullanarak örnekler derlemesini, sonra kapsayıcı yöntemini çağırmasını ve sabitleri yeniden denetlemesini sağlayın
  * Parametre değerlerine bağlı olarak farklı uygulama yöntemlerini çağıran [parametreli birim testleri](test-generation.md#parameterized-unit-testing) yazın
* Mevcut bir kod tabanı:
  * Bir dizi [parametreli birim testi (PUT)](test-generation.md#parameterized-unit-testing) oluşturarak başlamak için Visual Studio’nun IntelliTest Sihirbazını kullanın

## <a name="the-hello-world-of-intellitest"></a>IntelliTest Merhaba Dünya

IntelliTest, test edilmiş programla ilgili girişleri bulur, başka bir deyişle, ünlü **Merhaba Dünya!** dizesini oluşturmak için bunu kullanabilirsiniz. Burada, C# MSTest tabanlı bir test projesi oluşturduğunuz ve **Microsoft.Pex.Framework** başvurusunu eklediğiniz varsayılır. Farklı bir test çerçevesi kullanıyorsanız, C# sınıf kitaplığı oluşturun ve projenin nasıl ayarlanacağına ilişkin test çerçevesi belgelerine başvurun.

Aşağıdaki örnek, IntelliTest’in gerekli dizeyi oluşturması için **value** adlı parametre üzerinde iki kısıtlama oluşturur:

```csharp
using System;
using Microsoft.Pex.Framework;
using Microsoft.VisualStudio.TestTools.UnitTesting;

[TestClass]
public partial class HelloWorldTest {
    [PexMethod]
    public void HelloWorld([PexAssumeNotNull]string value) {
        if (value.StartsWith("Hello")
            && value.EndsWith("World!")
            && value.Contains(" "))
            throw new Exception("found it!");
    }
}
```

IntelliTest, derlenip yürütüldükten sonra aşağıdaki küme gibi bir dizi test oluşturur:

1. ""
2. "\0\0\0\0\0"
3. "Merhaba"
4. "\0\0\0\0\0\0"
5. "Merhaba\0"
6. "Merhaba\0\0"
7. "Merhaba\0Dünya!"
8. "Merhaba Dünya!"

> [!NOTE]
> Derleme sorunları için, Microsoft.VisualStudio.TestPlatform.TestFramework ve Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions başvurularını, Microsoft.VisualStudio.QualityTools.UnitTestFramework başvurusuyla değiştirin.

Oluşturulan testlerin nereye kaydedileceğini anlamak için [IntelliTest ile birim testleri oluşturma](../../test/generate-unit-tests-for-your-code-with-intellitest.md) bölümünü okuyun. Oluşturulan test kodu, aşağıdaki kod gibi bir test içermelidir:

```csharp
[TestMethod]
[PexGeneratedBy(typeof(global::HelloWorldTest))]
[PexRaisedException(typeof(Exception))]
public void HelloWorldThrowsException167()
{
    this.HelloWorld("Hello World!");
}
```

Bu kadar kolay!

Ek kaynaklar:
  * Bu [MSDN Magazine genel bakışını](/archive/msdn-magazine/2015/february/visual-studio-2015-build-better-software-with-smart-unit-tests) okuyun

## <a name="important-attributes"></a>Önemli öznitelikler

* [PexClass](attribute-glossary.md#pexclass), **PUT** içeren bir türü işaretler
* [PexMethod](attribute-glossary.md#pexmethod) bir **PUT**’u işaretler
* [PexAssumeNotNull](attribute-glossary.md#pexassumenotnull), null olmayan bir parametreyi işaretler

```csharp
using Microsoft.Pex.Framework;

[..., PexClass(typeof(Foo))]
public partial class FooTest {
    [PexMethod]
    public void Bar([PexAssumeNotNull]Foo target, int i) {
        target.Bar(i);
    }
}
```

* [PexAssemblyUnderTest](attribute-glossary.md#pexassemblyundertest), bir test projesini bir projeye bağlar
* [PexInstrumentAssembly](attribute-glossary.md#pexinstrumentassemblyattribute), işaretlenecek bir derlemeyi belirtir

```csharp
[assembly: PexAssemblyUnderTest("MyAssembly")] // also instruments "MyAssembly"
[assembly: PexInstrumentAssembly("Lib")]
```

## <a name="important-static-helper-classes"></a><a name="helper-classes"></a> Önemli statik yardımcı sınıfları

* [PexAssume](static-helper-classes.md#pexassume), varsayımları değerlendirir (giriş filtreleme)
* [PexAssert](static-helper-classes.md#pexassert), onay deyimlerini değerlendirir
* [PexChoose](static-helper-classes.md#pexchoose), yeni seçimler oluşturur (ek girişler)
* [PexObserve](static-helper-classes.md#pexobserve), oluşturulan testlere canlı değerleri kaydeder

```csharp
[PexMethod]
void StaticHelpers(Foo target) {
    PexAssume.IsNotNull(target);

    int i = PexChoose.Value<int>("i");
    string result = target.Bar(i);

    PexObserve.ValueForViewing<string>("result", result);
    PexAssert.IsNotNull(result);
}
```

## <a name="limitations"></a>Sınırlamalar

Bu bölümde, IntelliTest kısıtlamaları açıklanmaktadır:

* [Belirleyici olmama](#nondeterminism)
* [Eşzamanlılık](#concurrency)
* [Yerel .NET kodu](#native-code)
* [Platform](#platform)
* [Dil](#language)
* [Sembolik akıl yürütme](#symbolic-reasoning)
* [Yığın izlemeler](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Belirleyici olmama

IntelliTest, analiz edilen programın belirleyici olduğunu varsayar. Aksi takdirde IntelliTest, bir araştırma sınırına ulaşıncaya kadar döngüye girer.

IntelliTest, bir program, IntelliTest’in denetleyemeyeceği girişlere bağlıysa, o programı belirleyici değil olarak değerlendirir.

IntelliTest, [parametreli birim testlerine](test-generation.md#parameterized-unit-testing) sağlanan ve [PexChoose](static-helper-classes.md#pexchoose) öğesinden alınan girişleri denetler.
Bu anlamda, yönetilmeyen veya işaretlenmeyen koda yapılan çağrıların sonuçları, işaretlenmiş programa “girişler” olarak da değerlendirilir, ancak IntelliTest bunları denetleyemez. Programın denetim akışı, bu dış kaynaklardan gelen belirli değerlere bağımlıysa IntelliTest, programı daha önce kapsanmayan alanlara “yönlendiremez”.

Ayrıca program yeniden çalıştırılırken dış kaynaklardan gelen değerler değişiyorsa da o program belirleyici değil olarak değerlendirilir. Bu gibi durumlarda IntelliTest, programın yürütmesi üzerinde denetimini kaybeder ve araması verimsiz olur.

Bazen bunun ne zaman gerçekleştiği net değildir. Aşağıdaki örnekleri inceleyin:

* **GetHashCode()** yönteminin sonucu, yönetilmeyen kod tarafından sağlanır ve tahmin edilemez.
* **System.Random** sınıfı, gerçekten rastgele değerler sunmak için geçerli sistem saatini kullanır.
* **System.DateTime** sınıfı, IntelliTest’in denetiminde olmayan geçerli saati sağlar.

### <a name="concurrency"></a>Eşzamanlılık

IntelliTest, çok iş parçacıklı programları işlemez.

### <a name="native-code"></a>Yerel kod

IntelliTest, **P/Invoke** aracılığıyla çağrılan x86 yönergeleri gibi yerel kodları anlamaz. Bu tür çağrıların, [kısıtlama çözücüye](input-generation.md#constraint-solver) geçirilebilen kısıtlamalara nasıl çevrileceğini bilmez.
.NET kodu için bile yalnızca işaretlediği kodu analiz edebilir. IntelliTest, yansıma kitaplığı da dahil, **mscorlib** öğesinin belirli bölümlerini işaretleyemez. **DynamicMethod** işaretlenemez.

Önerilen çözüm, bu tür yöntemlerin dinamik bir derlemedeki türlerde bulunduğu bir test modunun olmasıdır. Ancak, bazı yöntemler işaretlenmemiş olsa bile IntelliTest, işaretlenmiş kodun mümkün olduğunca fazla kısmını ele almaya çalışır.

### <a name="platform"></a>Platform

IntelliTest yalnızca X86, 32-bit .NET framework’te desteklenir.

### <a name="language"></a>Dil

Prensipte IntelliTest, herhangi bir .NET dilinde yazılmış rastgele .NET programlarını analiz edebilir. Ancak Visual Studio’da yalnızca C# dilini destekler.

### <a name="symbolic-reasoning"></a>Sembolik akıl yürütme

IntelliTest, test ve test edilmekte olan program için hangi değerlerin ilişkili olduğunu belirlemek için otomatik bir [kısıtlama çözücü](input-generation.md#constraint-solver) kullanır. Ancak kısıtlama çözücünün yetenekleri şu an ve gelecekte her zaman sınırlı olacaktır.

### <a name="incorrect-stack-traces"></a>Hatalı yığın izlemeleri

IntelliTest, işaretlenmiş her bir yöntemde özel durumları yakalayıp “yeniden oluşturduğundan” yığın izlemesindeki satır numaraları doğru olmaz. Bu, “yeniden oluşturma” yönergesinin tasarımından kaynaklanan bir sınırlamadır.

## <a name="further-reading"></a>Daha fazla bilgi

* [Tanıtım blog gönderisi](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [Intellitest ile kodunuz için birim testleri oluşturma](../../test/generate-unit-tests-for-your-code-with-intellitest.md)