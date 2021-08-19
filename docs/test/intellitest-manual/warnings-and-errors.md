---
title: Uyarılar ve hatalar | Microsoft IntelliTest Geliştirici Test Aracı
description: Bu makalede, her uyarı ve hata için açıklamalarla birlikte kategorilere ayrılmış IntelliTest uyarıları ve hataları yer alır.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f6197b73c407069cca3ff20c862895c61e59b13a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092364"
---
# <a name="warnings-and-errors"></a>Uyarıları ve hatalar

## <a name="warnings-and-errors-by-category"></a>Kategoriye göre uyarılar ve hatalar

* **Sınırlar**
  * [MaxBranches aşıldı](#maxbranches-exceeded)
  * [MaxConstraintSolverTime aşıldı](#maxconstraintsolvertime-exceeded)
  * [MaxConditions aşıldı](#maxconditions-exceeded)
  * [MaxCalls aşıldı](#maxcalls-exceeded)
  * [MaxStack aşıldı](#maxstack-exceeded)
  * [MaxRuns aşıldı](#maxruns-exceeded)
  * [MaxRunsWithoutNewTests aşıldı](#maxrunswithoutnewtests-exceeded)

* **Kısıtlama Çözme**
  * [Çözümün Birleştirilenemleri](#cannot-concretize-solution)

* **Etki Alanları veya Çalışma Zamanı**
  * [Nesne oluşturmak için yardım gerekiyor](#help-construct)
  * [Türleri bulmak için yardım gerekiyor](#help-types)
  * [Tahmin Edilebilir Tür](#usable-type-guessed)

* **Yürütme**
  * [Araştırma Sırasında Beklenmeyen Hata](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)

* **Araçları**
  * [Çağrılmış Metot Çağrıldı](#uninstrumented-method-called)
  * [Çağrılan Dış Yöntem](#external-method-called)
  * [Çağrılamaz Yöntem Çağrıldı](#uninstrumentable-method-called)
  * [Sınanma Sorunu](#testability-issue)
  * [Sınırlama](#limitation)

* **Yorumlayıcı**
  * [Gözlemlenen Çağrı Eşleşmesi](#observed-call-mismatch)
  * [Statik alanda depolanan değer](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches aşıldı

IntelliTest, giriş oluşturma sırasında araştıran yürütme yollarının [uzunluğunu sınırlar.](input-generation.md) Bu özellik, program sonsuz bir döngüye geldiğinde IntelliTest'in yanıt vermemeye devamsını önler.

Yürütülen ve izlenen kodun her koşullu ve koşulsuz dalı, parametreli birim testinin girişlerine bağlı olmayan dallar da dahil olmak üzere [bu sınıra doğru sayılır.](test-generation.md#parameterized-unit-testing)

Örneğin, aşağıdaki kod dalları 100 sırasıyla tüketir:

```csharp
for (int i=0; i<100; i++) { }
```

**PexSettingsAttributeBase'den** türetilen bir özniteliğin [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi **MaxBranches** seçeneğini düzenleyebilirsiniz. Aşağıdaki örnek bu sınırı etkili bir şekilde kaldırır:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

IntelliTest'e bu sorunları genel olarak nasıl ele alacazın bildirmek için **TestExcludePathBoundsExceeded** seçeneğini de ayarlayın.

Test kodunda, döngü koşulu tarafından oluşturulan kısıtlamaları [yoksaymak için PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) kullanabilirsiniz:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime aşıldı

IntelliTest, yeni [test girişlerini hesaplamak](input-generation.md#constraint-solver) için bir kısıtlama çözücü kullanır. Kısıtlamayı çözmek çok zaman alan bir işlem olabilir, bu nedenle IntelliTest sınırları ( özellikle **MaxConstraintSolverTime) yapılandırmaya olanak sağlar.**

Birçok uygulama için zaman aşımının önemli ölçüde artırılması daha iyi kapsama neden olmaz. Bunun nedeni, çoğu zaman aşımının çözümüne sahip olan kısıtlama sistemlerinden kaynaksıyor olduğudur. Ancak IntelliTest, tüm olası çözümlerin deneyine gerek kalmadan tutarsız olduğunu belirleyene kadar zaman aşımına neden olabilir.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions aşıldı

IntelliTest, giriş oluşturma sırasında araştıran yürütme yollarının [uzunluğunu sınırlar.](input-generation.md) Bu özellik, program sonsuz bir döngüye girdiği zaman IntelliTest'in yanıt vermemeye devamsını önler.

Parametreli birim testinin girişlerine bağlı [olan her koşullu dal bu](test-generation.md#parameterized-unit-testing) sınıra doğru sayılır.

Örneğin, aşağıdaki kodda yer alan her yol **n+1 koşullarını** tüketir:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    // conditions are "0<n", "1<n", ..., "!(n<n)"
    for (int i=0; i<n; i++)
    { ... }

    // irrelevant for MaxConditions, since conditions do not depend on input
    for (int i=0; i<100; i++)
    { ... }
}
```

**PexSettingsAttributeBase'den** türetilen bir özniteliğin [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi **MaxConditions** seçeneğini düzenleyebilirsiniz. Örnek:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

IntelliTest'e bu sorunları genel olarak nasıl ele alacazın bildirmek için **TestExcludePathBoundsExceeded** seçeneğini de ayarlayın.

Döngü koşulu tarafından [oluşturulan kısıtlamaları yoksaymak için PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) kullanabilirsiniz:

```csharp
[PexMethod]
void ParameterizedTest(int n) {
    int nshadow = PexSymbolicValue.Ignore(n); // IntelliTest looses track of 'n'

    // irrevelant for MaxConditions, since nshadow is not related to input
    for (int i=0; i<nshadow; i++)
    {...}
}
```

<a name="maxcalls-exceeded"></a>
## <a name="maxcalls-exceeded"></a>MaxCalls aşıldı

IntelliTest, giriş oluşturma sırasında araştıran yürütme yollarının [uzunluğunu sınırlar.](input-generation.md) Bu özellik, program sonsuz bir döngüye girdiği zaman IntelliTest'in yanıt vermemeye devamsını önler.

Yürütülen ve izlenen kodun her çağrısı (doğrudan, dolaylı, sanal veya atlama) bu sınıra doğru sayılır.

**PexSettingsAttributeBase'den** türetilen bir özniteliğin [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi **MaxCalls** seçeneğini düzenleyebilirsiniz. Aşağıdaki örnek bu sınırı etkili bir şekilde kaldırır:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

IntelliTest'e bu sorunları genel olarak nasıl ele alacazın bildirmek için **TestExcludePathBoundsExceeded** seçeneğini de ayarlayın.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack aşıldı

IntelliTest, giriş oluşturma sırasında araştıran herhangi bir yürütme yolunun çağrı yığınının [boyutunu sınırlar.](input-generation.md) Bu özellik, yığın taşması oluştuğunda IntelliTest'in sonlandırıcısını önlemektedir.

**PexSettingsAttributeBase'den** türetilen bir özniteliğin [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi **MaxStack** seçeneğini düzenleyebilirsiniz. Aşağıdaki örnek bu sınırı etkili bir şekilde kaldırır (önerilmez):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

IntelliTest'e bu sorunları genel olarak nasıl ele alacazın bildirmek için **TestExcludePathBoundsExceeded** seçeneğini de ayarlayın.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns aşıldı

IntelliTest, giriş oluşturma sırasında araştıran yürütme yollarının [sayısını sınırlar.](input-generation.md) Bu özellik, intelliTest'in programda döngüler veya recursion olduğunda sonlandırılmalarını sağlar.

IntelliTest, parametreli testi belirli girişlerle her çalıştırsa yeni bir test çalıştırması gibi bir durumla karşılanamayabilirsiniz. Daha [fazla bilgi için bkz. TestEmissionFilter.](exploration-bounds.md#testemissionfilter)

**PexSettingsAttributeBase'den** türetilen bir özniteliğin **MaxRuns** seçeneğini [(PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi) düzenleyebilirsiniz. Aşağıdaki örnek bu sınırı etkili bir şekilde kaldırır (önerilmez):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests aşıldı

IntelliTest, giriş oluşturma sırasında araştıran yürütme yollarının [sayısını sınırlar.](input-generation.md) Bu özellik, intelliTest'in programda döngüler veya recursion olduğunda sonlandırılmalarını sağlar.

IntelliTest, parametreli testi belirli girişlerle her çalıştırsa yeni bir test çalıştırması gibi bir durumla karşılanamayabilirsiniz. Daha [fazla bilgi için bkz. TestEmissionFilter.](exploration-bounds.md#testemissionfilter)

IntelliTest genellikle başlangıçta pek çok ilgi çekici test girişi bulsa da, bir süre sonra başka test yaymaysa da bu durum ortaya çıktı. Bu seçenek, IntelliTest'in başka bir ilgili test girişini bulmaya ne kadar süreyle devam çalış çalışa çalışı yönetir.

**PexSettingsAttributeBase'den** türetilen bir özniteliğin [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi **MaxRunsWithoutNewTests** seçeneğini düzenleyebilirsiniz. Aşağıdaki örnek bu sınırı etkili bir şekilde kaldırır (önerilmez):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Çözüm somutlaştırılamıyor

Bu hata genellikle önceki bir hatanın sonucudur. IntelliTest, yeni [test girişlerini belirlemek](input-generation.md#constraint-solver) için bir kısıtlama çözücü kullanır. Bazen kısıtlama çözücü tarafından önerilen test [girişleri](input-generation.md#constraint-solver) geçersizdir. Bu durum şu zaman olabilir:

* belirli kısıtlamalar bilinmemektedir
* değerler kullanıcı tanımlı bir şekilde oluşturulduktan sonra kullanıcı kodunda hatalara neden oluyorsa
* Söz konusu türlerden bazıları IntelliTest tarafından denetlenen başlatma mantığına (örneğin COM sınıfları) sahip

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Nesne oluşturmak için yardım gerekiyor

IntelliTest [test girişleri oluşturur](input-generation.md)ve bazı girişler alanları olan nesneler olabilir.
Burada IntelliTest, özel alana sahip bir sınıfın örneğini üretmeye çalışır ve bu özel alan belirli bir değere sahip olduğunda ilginç bir program davranışının ortaya çıkar olduğunu varsayıyor.

Ancak Bu Yansıma ile mümkün olduğu gibi IntelliTest rastgele alan değerlerine sahip nesneler üretmez.
Bunun yerine, bu durumlarda kullanıcıya, bir sınıfın genel yöntemlerini kullanarak bir nesne oluşturma ve özel alanı istenen değere sahip olduğu bir durumuna getirme hakkında ipuçları sağlamasını kullanır.

[IntelliTest'in ilgi çekici nesneler](input-generation.md#existing-classes) oluşturması için mevcut sınıfların örneğini oluşturma makalesini okuyun.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Türleri bulmak için yardım gerekiyor

IntelliTest, [herhangi bir](input-generation.md) .NET türü için test girişleri üretir. Burada IntelliTest, soyut bir sınıftan türetilen veya soyut bir arabirim uygulayan bir örnek oluşturmak için çalışır ve IntelliTest kısıtlamaları yerine getiren herhangi bir türü bilmiyor.

Kısıtlamalarla eşleşen bir veya daha fazla türe işaret ederek IntelliTest 'e yardımcı olabilirsiniz. Genellikle, aşağıdaki özniteliklerden biri yardımcı olur:

* **PexUseTypeAttribute**, belirli bir türü işaret eder.

  Örneğin, IntelliTest, " **System. Collections. IDictionary** öğesine atanabilir herhangi bir türü bilmez" olarak bildirirse, teste aşağıdaki **PexUseTypeAttribute** öğesini ekleyerek (veya düzeni sınıfına) yardımcı olabilirsiniz:

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Derleme düzeyi özniteliği**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Kullanılabilir tür tahmin edildi

IntelliTest her türlü .NET türü için [Test girişleri oluşturur](input-generation.md) . Bir tür abstract veya Interface olduğunda, IntelliTest bu türün belirli bir uygulamasını seçmelidir. Bu seçimi yapmak için, hangi türlerin mevcut olduğunu bilmeleri gerekir.

Bu uyarı gösterildiğinde, IntelliTest 'in başvurulan derlemelerin bazılarına baktığı ve bir uygulama türü bulduğu, ancak bu türü kullanması ya da başka bir yerde kullanılabilir olan daha uygun türler varsa emin olduğunu gösterir. IntelliTest, yalnızca bir göz attığı bir tür seçti.

Bu uyarıyı önlemek için, IntelliTest 'in tür seçimini kabul edebilir veya ilgili bir [Pexusetype](attribute-glossary.md#pexusetype)ekleyerek diğer türleri kullanarak IntelliTest 'e yardımcı olabilirsiniz.

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Araştırma sırasında beklenmeyen hata oluştu

Test araştırılırken beklenmeyen bir özel durum yakalandı.

Lütfen [bunu bir hata olarak bildirin](#report-bug).

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

Kullanıcı kodunda bir özel durum oluştu. Yığın izlemesini inceleyin ve kodunuzda hatayı kaldırın.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>İzlenmeyen metot çağrıldı

IntelliTest program yürütmesini izleyerek [Test girişleri oluşturur](input-generation.md) . IntelliTest 'in davranışını izleyebilmesi için ilgili kodun düzgün şekilde işaretlenmiş olması önemlidir.

Bu uyarı, izlenen kod farklı, Araçlı bir derlemede Yöntemler çağırdığında görüntülenir.
IntelliTest 'in her ikisinin de etkileşimini araştırmasını istiyorsanız, diğer derlemeyi (veya bunun parçalarını) de göz atın.

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Dış metot çağrıldı

IntelliTest, .NET uygulamalarının yürütülmesini izleyerek [Test girişleri oluşturur](input-generation.md) .
IntelliTest, .NET dilinde yazılmayan kod için anlamlı test girişleri üretemiyor.

Bu uyarı, belgelenmiş kod IntelliTest 'in çözümleyemedikleri yönetilmeyen, yerel bir yöntemi çağırdığında görüntülenir. IntelliTest 'in her ikisinin de etkileşimini keşfetmesi için yönetilmeyen yöntemi tanımlamalısınız.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>İzlenmeyen metot çağrıldı

IntelliTest, .NET uygulamalarının yürütülmesini izleyerek [Test girişleri oluşturur](input-generation.md) . Ancak, teknik nedenlerden dolayı IntelliTest 'in izleyememesinin bazı yöntemleri vardır. Örneğin, IntelliTest bir statik oluşturucuyu izlenemez.

Bu uyarı, belgelenmiş kod IntelliTest 'in izleyemeyen bir yöntemi çağırdığında görüntülenir.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Test edilebilirlik sorunu

IntelliTest program yürütmesini izleyerek [Test girişleri oluşturur](input-generation.md) . Yalnızca program belirleyici olduğunda ve ilgili davranış test girişleri tarafından denetleniyorsa, ilgili test girişleri oluşturabilir.

Bu uyarı, test durumlarınızın yürütülmesi sırasında, belirleyici olmayan bir şekilde davranan ya da ortamla etkileşim kuran bir yöntem çağrıldığı için görüntülenir. Örnek olarak **System. Random** ve **System. IO. File** yöntemleri verilebilir. IntelliTest 'in anlamlı test girişleri oluşturmasını istiyorsanız, IntelliTest bayraklarının test edilebilirlik sorunları olarak bir test etme yöntemi olarak tanımlamalısınız.

<a name="limitation"></a>
## <a name="limitation"></a>Sınırlama

IntelliTest, [kısıtlama çözücü](input-generation.md#constraint-solver)kullanarak [Test girişleri oluşturur](input-generation.md) .
Ancak, [kısıtlama çözücü](input-generation.md#constraint-solver)kapsamının ötesinde bazı işlemler vardır.
Bu şu anda şunları içerir:

* çoğu kayan nokta işlemi (kayan nokta numaralarında yalnızca bir doğrusal aritmetik desteklenir)
* kayan nokta sayıları ve tamsayılar arasındaki dönüşümler
* **System. Decimal** türündeki tüm işlemler

Yürütülen kod bir işlem gerçekleştirdiğinde veya IntelliTest 'in yorumlayamadığı bir yöntemi çağırdığında bu uyarı görüntülenir.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Çağrı uyuşmazlığı gözlemlendi

IntelliTest program yürütmesini izleyerek [Test girişleri oluşturur](input-generation.md) . Ancak, IntelliTest tüm yönergeleri izleyemeyebilir. Örneğin, yerel kodu izleyemez ve işaretlenmeyen kodu izleyemez.

IntelliTest kodu izleyene zaman, bu kodla ilgili olan test girişlerini üretemiyor.
Genellikle, IntelliTest, bu yöntemin bir çağrısı döndürülünceye kadar bir yöntemi izleyemeyeceğine ilişkin farkında değildir. Ancak, bu uyarının nedeni:

* IntelliTest izlenen bir yönteme çağrı başlatan bazı kodları izlendi
* Belgelenmiş yöntemi, işaretlenmiş bir yöntem olarak çağrıldı
* IntelliTest, çağrılan yöntemi izler

IntelliTest, izlenmeyen ara yöntemin ne olduğunu bilmez, bu yüzden iç içe geçmiş çağrılarla ilgili olan test girişlerini oluşturamayacak olabilir.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Değer statik alanda depolandı

IntelliTest, yalnızca birim testi belirleyici olduğunda [ilgili test girişlerini](input-generation.md) sistematik olarak belirleyebilir; diğer bir deyişle, her zaman aynı test girişleri için aynı şekilde davranır. Özellikle, bu, testin sistemi yeniden yürütmeye izin veren bir durumda bırakması gerektiği anlamına gelir.
İdeal olarak, birim testi herhangi bir genel durumu değiştirmemelidir, ancak genel olan tüm etkileşimler mocize olmalıdır.

Bu uyarı statik bir alanın değiştirildiğini belirtir; Bu, testin belirleyici olmayan şekilde davranmasına de dikkat edebilir.

Bazı durumlarda, statik bir alanı değiştirmek kabul edilebilir:

* test girdileri kurulum veya temizleme kodunun değişikliği geri almasına neden olur
* alan yalnızca bir kez başlatıldığında ve değer daha sonra değişmezse

<a name="report-bug"></a>

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://aka.ms/feedback/suggest?space=8)’na gönderin.
