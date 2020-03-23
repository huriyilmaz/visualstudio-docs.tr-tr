---
title: Genel Bakış | Microsoft IntelliTest Geliştirici Test Aracı
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: dfa81e7afe313a112e2355ddf5efadb70c555477
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591611"
---
# <a name="overview-of-microsoft-intellitest"></a>Microsoft IntelliTest'e Genel Bakış

IntelliTest hataları erken bulmanızı sağlar ve test bakım maliyetlerini azaltır. IntelliTest, otomatik ve saydam bir test yaklaşımı kullanarak .NET kodunuz için bir aday test paketi oluşturabilir. Test paketi oluşturma, belirttiğiniz *doğruluk özellikleri* yle daha fazla yönlendirilebilir. IntelliTest, test altındaki kod geliştikçe test paketini bile otomatik olarak geliştirecektir.

**Karakterizasyon testleri** IntelliTest, geleneksel birim testleri paketi açısından kodun davranışını belirlemenize olanak tanır.
Böyle bir test paketi, eski veya yabancı kod refactoring ile ilişkili karmaşıklığı mücadele için temel oluşturan bir regresyon paketi olarak kullanılabilir.

**Kılavuzlu test giriş oluşturma** IntelliTest, hassas test girdi değerlerini otomatik olarak oluşturmak için açık kod çözümleme ve kısıtlama çözme yaklaşımını kullanır; genellikle herhangi bir kullanıcı müdahalesi için gerek kalmadan. Karmaşık nesne türleri için, otomatik olarak fabrikalar oluşturur. Fabrikaları gereksinimlerinize göre genişleterek ve yapılandırarak test girdisi üretimine rehberlik edebilirsiniz. Kodda öne etme olarak belirtilen doğruluk özellikleri de test girişi oluşturma yı yönlendirmek için otomatik olarak kullanılır.

**IDE entegrasyonu** IntelliTest, Visual Studio IDE'ye tamamen entegre edilmiştir. Test paketi oluşturma sırasında toplanan tüm bilgiler (otomatik olarak oluşturulan girişler, kodunuzdan çıktı, oluşturulan test örnekleri ve bunların geçme veya başarısız durumu gibi) Visual Studio IDE'de görünür. Visual Studio IDE'den ayrılmadan kodunuzu sabitleme ve IntelliTest'i yeniden çalıştırmak arasında kolayca yineleyebilirsiniz.
Testler Bir Birim Test Projesi olarak çözüme kaydedilebilir ve daha sonra Visual Studio Test Explorer tarafından otomatik olarak algılanır.

**Mevcut test uygulamalarını tamamla** Zaten takip edebilirsiniz herhangi bir mevcut test uygulamaları tamamlamak için IntelliTest kullanın.

Test etmek isterseniz:

* İlkel veri veya ilkel veri dizileri üzerindeki algoritmalar:
  * [parametreli birim testleri](test-generation.md#parameterized-unit-testing) yazma
* Derleyici gibi karmaşık veriler üzerindeki algoritmalar:
  * IntelliTest'in önce verilerin soyut bir temsilini oluşturmasına ve ardından algoritmaya beslemesine izin
  * IntelliTest'in özel [nesne oluşturma](input-generation.md#objects) ve veri değişmezlerini kullanarak örnekler oluşturmasına izin verin ve ardından algoritmayı çağırın
* Veri kapsayıcıları:
  * [parametreli birim testleri](test-generation.md#parameterized-unit-testing) yazma
  * IntelliTest'in özel [nesne oluşturma](input-generation.md#objects) ve veri değişmezlerini kullanarak örnekler oluşturmasına izin verin ve ardından kapsayıcının bir yöntemini çağırın ve daha sonra değişmezleri yeniden denetleyin
  * parametre değerlerine bağlı olarak, uygulamanın farklı yöntemlerini arayan [parametreli birim testleri](test-generation.md#parameterized-unit-testing) yazma
* Varolan bir kod tabanı:
  * bir dizi [parametreli birim testi (PUT)](test-generation.md#parameterized-unit-testing) oluşturarak başlamak için Visual Studio'nun IntelliTest Sihirbazı'nı kullanın

## <a name="the-hello-world-of-intellitest"></a>IntelliTest’in kullanıma sunulması

IntelliTest, test edilen programla ilgili girdiler bulur, bu da onu ünlü Hello World'ü oluşturmak için kullanabileceğiniz anlamına **gelir!** Dize. Bu, C# MSTest tabanlı bir test projesi oluşturduğunuzu ve **Microsoft.Pex.Framework'e**bir başvuru eklediğinizi varsayar. Farklı bir test çerçevesi kullanıyorsanız, c# sınıfı kitaplığı oluşturun ve projenin nasıl ayarlayacağına ilişkin test çerçevesi belgelerine bakın.

Aşağıdaki örnek, IntelliTest'in gerekli dizeyi oluşturabilmesi için parametre adı verilen **değerüzerinde** iki kısıtlama oluşturur:

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

Bir kez derlenmiş ve yürütülür, IntelliTest aşağıdaki küme gibi testler kümesi oluşturur:

1. ""
2. "\0\0\0\0\0"
3. "Merhaba"
4. "\0\0\0\0\0\0"
5. "Merhaba\0"
6. "Merhaba\0\0"
7. "Merhaba\0World!"
8. "Merhaba Dünya!"

> [!NOTE]
> Yapı sorunları için Microsoft.VisualStudio.TestPlatform.TestFramework ve Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions başvurularını Microsoft.VisualStudio.QualityTools.UnitTestFramework adresine başvurulayarak değiştirmeyi deneyin.

Oluşturulan testlerin nerede kaydolduğunu anlamak için [IntelliTest ile birim testleri oluştur'u](../../test/generate-unit-tests-for-your-code-with-intellitest.md) okuyun. Oluşturulan test kodu aşağıdaki kod gibi bir test içermelidir:

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

## <a name="limitations"></a>Sınırlamalar

Bu bölümde IntelliTest sınırlamaları açıklanır:

* [Belirleyici olmama](#nondeterminism)
* [Eşzamanlılık](#concurrency)
* [Yerel .NET kodu](#native-code)
* [Platform](#platform)
* [Dil](#language)
* [Sembolik akıl yürütme](#symbolic-reasoning)
* [Yığın izleri](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Belirleyici olmama

IntelliTest, analiz edilen programın deterministik olduğunu varsayar. Değilse, IntelliTest bir keşif bağlı ulaşana kadar döngüsü olacaktır.

IntelliTest, IntelliTest'in kontrol edemediği girişlere dayanıyorsa, bir programı determistik olmayan bir program olarak kabul eder.

IntelliTest, [parametreli birim testlerine](test-generation.md#parameterized-unit-testing) sağlanan ve [PexChoose'ten](static-helper-classes.md#pexchoose)elde edilen girişleri kontrol eder.
Bu anlamda, yönetilmeyen veya aracısız koda yapılan çağrıların sonuçları da enstrümante gösterilen programa "giriş" olarak kabul edilir, ancak IntelliTest bunları denetleyemez. Programın kontrol akışı bu dış kaynaklardan gelen belirli değerlere bağlıysa, IntelliTest programı daha önce açığa çıkarılan alanlara "yönlendiremez".

Buna ek olarak, programı yeniden çalıştırırken dış kaynaklardan gelen değerler değişirse program determistik olmayan olarak kabul edilir. Bu gibi durumlarda IntelliTest programın yürütülmesi üzerindeki kontrolünü kaybeder ve arama verimsiz hale gelir.

Bazen bu olduğunda belli değildir. Aşağıdaki örnekleri dikkate alın:

* **GetHashCode()** yönteminin sonucu yönetilmeyen kod tarafından sağlanır ve öngörülebilir değildir.
* **System.Random** sınıfı gerçekten rasgele değerler sunmak için geçerli sistem zamanını kullanır.
* **System.DateTime** sınıfı, IntelliTest'in denetimi altında olmayan geçerli saati sağlar.

### <a name="concurrency"></a>Eşzamanlılık

IntelliTest çok iş parçacığı programları işlemez.

### <a name="native-code"></a>Yerel kod

IntelliTest, **P/Invoke**ile çağrılan x86 yönergeleri gibi yerel kodu anlamaz. Bu tür [çağrıların kısıtlama çözücüye](input-generation.md#constraint-solver)geçirilebilecek kısıtlamalara nasıl çevrileceğini bilmiyor.
.NET kodu için bile, yalnızca kendi enstrümanları kodu analiz edebilirsiniz. IntelliTest, yansıma kitaplığı da dahil olmak üzere **mscorlib'in**belirli bölümlerini enstrüman edemez. **DynamicMethod** çalgılanamaz.

Önerilen geçici çözüm, bu tür yöntemlerin dinamik bir derlemedeki türlerde bulunduğu bir test moduna sahip olmaktır. Ancak, bazı yöntemler araçsız olsa bile, IntelliTest enstrümantelenmiş kodun mümkün olduğunca çoğunu kapsamaya çalışır.

### <a name="platform"></a>Platform

IntelliTest sadece X86, 32-bit desteklenir. Netframework.

### <a name="language"></a>Dil

Prensip olarak, IntelliTest herhangi bir .NET dilinde yazılmış rasgele .NET programlarını analiz edebilir. Ancak Visual Studio'da yalnızca C#'ı destekler.

### <a name="symbolic-reasoning"></a>Sembolik akıl yürütme

IntelliTest, test altındaki test ve program için hangi değerlerin alakalı olduğunu belirlemek için otomatik bir [kısıtlama çözücü](input-generation.md#constraint-solver) kullanır. Ancak, kısıtlama çözücü yetenekleri ve her zaman, sınırlı olacaktır.

### <a name="incorrect-stack-traces"></a>Hatalı yığın izlemeleri

IntelliTest her enstrümante yöntemdeki özel durumları yakalayıp "yeniden attığından" yığın izlerinde satır numaraları doğru olmaz. Bu " rethrow" talimatı tasarımı ile bir sınırlamadır.

## <a name="further-reading"></a>Daha fazla bilgi

* [Tanıtım blog yazısı](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [Intellitest ile kodunuz için birim testleri oluşturma](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
