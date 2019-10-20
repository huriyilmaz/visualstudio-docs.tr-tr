---
title: Genel Bakış | Microsoft IntelliTest geliştirici test aracı
ms.date: 05/02/2017
ms.topic: conceptual
helpviewer_keywords:
- IntelliTest, Visual Studio IntelliTest developer testing tool
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 94bd67ecb4646e3b8079d2d1aadda097c655af4c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653167"
---
# <a name="overview-of-microsoft-intellitest"></a>Microsoft IntelliTest 'e genel bakış

IntelliTest, hataları erken bulmanıza ve test bakım maliyetlerini azaltmanızı sağlar. IntelliTest, otomatikleştirilmiş ve şeffaf bir test yaklaşımı kullanarak .NET kodunuz için bir aday test paketi oluşturabilir. Test paketi oluşturma, belirttiğiniz *doğruluk özelliklerine* göre daha fazla yönetilebilir. IntelliTest, sınama geliştikçe kod olarak test paketini otomatik olarak de gelişir.

**Karakter seçme testleri** IntelliTest, bir geleneksel birim testleri paketi açısından kodun davranışını belirlemenizi sağlar.
Böyle bir test paketi, bir gerileme paketi olarak kullanılabilir ve bu, eski veya tanıdık kod yeniden düzenleme ile ilişkili karmaşıklığa karşı bir temel oluşturulur.

**Kılavuzlu test girişi oluşturma** IntelliTest, kesin test girişi değerlerini otomatik olarak oluşturmak için açık kod analizini ve kısıtlama çözme yaklaşımını kullanır; genellikle herhangi bir kullanıcı müdahalesine gerek kalmadan. Karmaşık nesne türleri için otomatik olarak fabrika oluşturur. Fabrikaları gereksinimlerinize uyacak şekilde genişleterek ve yapılandırarak test girişi oluşturmaya kılavuzluk edebilirsiniz. Kodda onaylar olarak belirtilen doğruluk özellikleri, test girişi oluşturma hakkında daha fazla rehberlik için de otomatik olarak kullanılır.

**IDE tümleştirmesi** IntelliTest, Visual Studio IDE ile tamamen tümleşiktir. Test paketi oluşturma sırasında toplanan tüm bilgiler (otomatik olarak oluşturulan girişler, kodunuzun çıktısı, oluşturulan test çalışmaları ve bunların geçiş veya başarısızlık durumu gibi), Visual Studio IDE içinde görünür. Visual Studio IDE 'den çıkmadan kodunuzu düzeltme ve IntelliTest yeniden çalıştırma arasında kolayca yineleme yapabilirsiniz.
Testler bir birim testi projesi olarak çözüme kaydedilebilir ve daha sonra Visual Studio Test Gezgini tarafından otomatik olarak algılanır.

**Mevcut test uygulamalarını tamamlama** Zaten takip ettiğiniz mevcut test uygulamalarını tamamlamak için IntelliTest kullanın.

Test etmek istiyorsanız:

* Temel veriler veya temel veri dizileri üzerinde algoritmalar:
  * [parametreli birim testleri](test-generation.md#parameterized-unit-testing) yazma
* Derleyici gibi karmaşık veriler üzerinde algoritmalar:
  * IntelliTest 'in ilk olarak verilerin soyut bir gösterimini oluşturmasını sağlar ve ardından bunu algoritmaya akışın
  * [özel nesne oluşturma](input-generation.md#objects) ve veri ınvaryantları kullanarak IntelliTest derleme örneklerine izin verin ve ardından algoritmayı çağırır
* Veri kapsayıcıları:
  * [parametreli birim testleri](test-generation.md#parameterized-unit-testing) yazma
  * [özel nesne oluşturma](input-generation.md#objects) ve veri ınvaryantları kullanarak IntelliTest derleme örneklerine izin verin ve sonra kapsayıcının bir yöntemini çağırın ve daha sonra ınvarıant 'ları yeniden denetleyin
  * parametre değerlerine bağlı olarak uygulamanın farklı yöntemlerini çağıran [parametreli birim testleri](test-generation.md#parameterized-unit-testing) yazma
* Var olan bir kod tabanı:
  * [parametreli birim testleri kümesi (koyar)](test-generation.md#parameterized-unit-testing) oluşturarak başlamak Için Visual Studio 'Nun IntelliTest Sihirbazı 'nı kullanın

## <a name="the-hello-world-of-intellitest"></a>IntelliTest Merhaba Dünya

IntelliTest, sınanan programla ilgili girişleri bulur, bu da bunu kullanarak çok fazla Merhaba Dünya oluşturmak için kullanabilirsiniz **!** dizisinde. Bu, MSTest tabanlı bir C# test projesi oluşturduğunuzu ve **Microsoft. Pex. Framework**için bir başvuru eklendiğini varsayar. Farklı bir test çerçevesi kullanıyorsanız, bir C# sınıf kitaplığı oluşturun ve projenin nasıl ayarlanacağı hakkında test çerçevesi belgelerine başvurun.

Aşağıdaki örnek, IntelliTest 'in gerekli dizeyi oluşturması için **Value** adlı parametrede iki kısıtlama oluşturur:

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

Derlendikten ve yürütüldükten sonra, IntelliTest aşağıdaki küme gibi bir test kümesi oluşturur:

1. ""
2. "\ 0 \ 0 \ 0 \ 0 \ 0"
3. Herkese
4. "\ 0 \ 0 \ 0 \ 0 \ 0 \ 0"
5. "Merhaba \"
6. "Merhaba \0\0"
7. "Merhaba \0Dünya!"
8. "Merhaba Dünya!"

Oluşturulan testlerin nerede kaydedileceğini anlamak için [, IntelliTest ile birim testleri oluştur](../../test/generate-unit-tests-for-your-code-with-intellitest.md) konusunu okuyun. Oluşturulan test kodu aşağıdaki kod gibi bir test içermelidir:

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

Bu bölümde IntelliTest kısıtlamaları açıklanmaktadır:

* [Belirleyici olmayan ISM](#nondeterminism)
* [Eşzamanlılık](#concurrency)
* [Yerel .NET kodu](#native-code)
* [Platformunun](#platform)
* [Dil](#language)
* [Sembolik mantık yürütme](#symbolic-reasoning)
* [Yığın izlemeleri](#incorrect-stack-traces)

### <a name="nondeterminism"></a>Belirleyici olmayan ISM

IntelliTest, çözümlenen programın belirleyici olduğunu varsayar. Aksi takdirde, IntelliTest bir araştırmayla bağlanana kadar dolacaktır.

IntelliTest, IntelliTest 'in denetleyemeyen girdileri kullanıyorsa, bir programı determistic olmayan bir şekilde değerlendirir.

IntelliTest, [parametreli birim testlerine](test-generation.md#parameterized-unit-testing) sunulan ve [PexChoose](static-helper-classes.md#pexchoose)öğesinden elde edilen girişleri denetler.
Bu anlamda, yönetilmeyen veya açıklanmeyen koda yapılan çağrıların sonuçları, işaretlenmiş programa "girişler" olarak da değerlendirilir, ancak IntelliTest bunları denetleyebilir. Programın denetim akışı bu dış kaynaklardan gelen belirli değerlere bağımlıysa, IntelliTest, programı daha önce kapsamayan alanlara yönlendiren "sözcük" olamaz.

Ayrıca, program yeniden çalıştırıldığında dış kaynaklardaki değerler değiştiğinde program determistic olmayan olarak değerlendirilir. Bu gibi durumlarda, IntelliTest programın yürütülmesi üzerinde denetimi kaybeder ve arama verimsiz hale gelir.

Bazen bu gerçekleştiğinde belirgin değildir. Aşağıdaki örnekleri göz önünde bulundurun:

* **GetHashCode ()** yönteminin sonucu yönetilmeyen kod tarafından sağlanır ve tahmin edilebilir değildir.
* **System. Random** sınıfı, gerçekten rastgele değerler sunmak için geçerli sistem saatini kullanır.
* **System. DateTime** sınıfı, IntelliTest denetiminde olmayan geçerli zamanı sağlar.

### <a name="concurrency"></a>Eşzamanlılık

IntelliTest çok iş parçacıklı programları işlemez.

### <a name="native-code"></a>Yerel kod

IntelliTest, **P/Invoke**aracılığıyla çağrılan x86 yönergeleri gibi yerel kodu anlamaz. Bu tür çağrıların [kısıtlama çözücü](input-generation.md#constraint-solver)' ne geçirilebilen kısıtlamalara nasıl çevrileceğini bilmez.
.NET kodu için bile, yalnızca BT aletlerine yönelik kodu analiz edebilir. IntelliTest, yansıma kitaplığı dahil olmak üzere **mscorlib**'in bazı parçalarını işaretlemelidir. **DynamicMethod** , düzenlenemez.

Önerilen geçici çözüm, bu tür yöntemlerin dinamik bir derlemedeki türlerde bulunduğu bir test moduna sahip olur. Ancak, bazı yöntemler açıklanmasa bile, IntelliTest, belgelenmiş kodun mümkün olduğunca fazlasını ele almaya çalışır.

### <a name="platform"></a>Platform

IntelliTest yalnızca x86, 32 bit üzerinde desteklenir. NETframework.

### <a name="language"></a>Dil

İlke ' de, IntelliTest, herhangi bir .NET dilinde yazılmış rastgele .NET programlarını analiz edebilir. Ancak, Visual Studio 'da yalnızca C#destekler.

### <a name="symbolic-reasoning"></a>Sembolik mantık yürütme

IntelliTest, test ve test altındaki program için hangi değerlerin ilgili olduğunu belirleyen bir otomatik [kısıtlama çözücü](input-generation.md#constraint-solver) kullanır. Ancak, kısıtlama çözücü 'nün becerileri ve her zaman sınırlı olacaktır.

### <a name="incorrect-stack-traces"></a>Hatalı yığın izlemeleri

Her bir belgelenmiş yöntemde IntelliTest catch ve "Re," özel durumları, yığın izlemelerinde bulunan satır numaraları doğru olmayacaktır. Bu, "Rethrow" yönergesinin tasarımıyla bir kısıtlamadır.

## <a name="further-reading"></a>Daha fazla okuma

* [Giriş blog gönderisi](https://devblogs.microsoft.com/devops/introducing-smart-unit-tests/).
* [Intellitest ile kodunuz için birim testleri oluşturma](../../test/generate-unit-tests-for-your-code-with-intellitest.md)
