---
title: Uyarılar ve hatalar | Microsoft IntelliTest geliştirici test aracı
description: Bu makalede, her bir uyarı ve hatanın açıklamalarıyla birlikte, her bir uyarı ve hata için açıklamaların bulunduğu IntelliTest uyarıları ve hataları bulunur
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 639b68c4d999a5e491f6e52a2cf3a7960563ed17
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329438"
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

* **Kısıtlama çözme**
  * [Çözüm değiştirilemez](#cannot-concretize-solution)

* **Etki alanları veya çalışma zamanı**
  * [Nesne oluşturmak Için yardım gerekiyor](#help-construct)
  * [Türleri bulmak Için yardım gerekiyor](#help-types)
  * [Kullanılabilir tür tahmin edildi](#usable-type-guessed)

* **Yürütme**
  * [Araştırma sırasında beklenmeyen hata oluştu](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)

* **Yapısı**
  * [Açıklanmeyen yöntem çağrıldı](#uninstrumented-method-called)
  * [Dış yöntem çağrıldı](#external-method-called)
  * [Unınstrumentable yöntemi çağrıldı](#uninstrumentable-method-called)
  * [Test edilebilirlik sorunu](#testability-issue)
  * [Sınırlama](#limitation)

* **Sından**
  * [Gözlemlenen çağrı uyumsuzluğu](#observed-call-mismatch)
  * [Statik alanda depolanan değer](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches aşıldı

IntelliTest, [giriş oluşturma](input-generation.md)sırasında incelendiğinden herhangi bir yürütme yolunun uzunluğunu sınırlandırır. Bu özellik, program sonsuz bir döngüye geçtiğinde IntelliTest 'in yanıt vermemesine engel olur.

Yürütülen ve izlenen kodun her koşullu ve koşulsuz dalı, [parametreli birim testinin](test-generation.md#parameterized-unit-testing)girdilerine bağlı olmayan dallar da dahil olmak üzere bu sınıra doğru sayılır.

Örneğin, aşağıdaki kod dalları 100 sırasıyla kullanır:

```csharp
for (int i=0; i<100; i++) { }
```

**PexSettingsAttributeBase**'den türetilmiş bir özniteliğin **maxbranches** seçeneğini ( [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi) düzenleyebilirsiniz. Aşağıdaki örnek bu sınırı etkin bir şekilde kaldırır:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Ayrıca, bu sorunlarla başa çıkmak için genel test ' i kullanarak **Testexcludepathboundsexcehariç** seçeneğini de ayarlayabilirsiniz.

Test kodunda, döngü koşulu tarafından oluşturulan kısıtlamaları yoksaymak için [Pexsembolicvalue](static-helper-classes.md#pexsymbolicvalue) kullanabilirsiniz:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime aşıldı

IntelliTest, yeni test girişlerini hesaplamak için bir [kısıtlama çözücü](input-generation.md#constraint-solver) kullanır. Kısıtlama çözme işlemi çok uzun süren bir işlem olabilir, bu nedenle IntelliTest, sınırları yapılandırmanıza olanak tanır, **MaxConstraintSolverTime**.

Birçok uygulama için zaman aşımını önemli ölçüde artırmak daha iyi kapsama neden olmaz. Bunun nedeni, en fazla zaman aşımlarının çözüm içermeyen kısıtlama sistemlerinden kaynaklanır. Ancak, IntelliTest tüm olası çözümleri denemeksizin tutarsız olduğunu belirleyemeyebilir, bu da zaman aşımına neden olur.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions aşıldı

IntelliTest, [giriş oluşturma](input-generation.md)sırasında incelendiğinden herhangi bir yürütme yolunun uzunluğunu sınırlandırır. Bu özellik, program sonsuz bir döngüye girdiğinde IntelliTest 'in yanıt vermemesine engel olur.

[Parametreli birim testinin](test-generation.md#parameterized-unit-testing) girdilerine bağlı olan her bir koşullu dal, bu sınıra doğru sayılır.

Örneğin, aşağıdaki koddaki her bir yol **n + 1** koşul kullanır:

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

**PexSettingsAttributeBase**'den türetilmiş bir özniteliğin **maxconditions** seçeneğini ( [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi) düzenleyebilirsiniz. Örneğin:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

**Testexcludepathboundsexceıda** seçeneğini, bu sorunları genel olarak nasıl ele alınacağını IntelliTest 'e bildirmek için de ayarlayabilirsiniz.

Döngü koşulu tarafından oluşturulan kısıtlamaları yoksaymak için [Pexsembolicvalue](static-helper-classes.md#pexsymbolicvalue) kullanabilirsiniz:

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

IntelliTest, [giriş oluşturma](input-generation.md)sırasında incelendiğinden herhangi bir yürütme yolunun uzunluğunu sınırlandırır. Bu özellik, program sonsuz bir döngüye girdiğinde IntelliTest 'in yanıt vermemesine engel olur.

Yürütülen ve izlenen kodun her çağrısı (doğrudan, dolaylı, sanal veya atlamanın) bu sınıra doğru sayılır.

**PexSettingsAttributeBase** öğesinden türetilmiş bir özniteliğin **maxgörüşmelerini** seçeneğini, örneğin [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod). Aşağıdaki örnek bu sınırı etkin bir şekilde kaldırır:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

**Testexcludepathboundsexceıda** seçeneğini, bu sorunları genel olarak nasıl ele alınacağını IntelliTest 'e bildirmek için de ayarlayabilirsiniz.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack aşıldı

IntelliTest, [giriş oluşturma](input-generation.md)sırasında incelendiğinden herhangi bir yürütme yolunun çağrı yığınının boyutunu sınırlandırır. Bu özellik, bir yığın taşması oluştuğunda IntelliTest 'in sonlandırmasını önler.

**PexSettingsAttributeBase** öğesinden türetilmiş bir özniteliğin **maxstack** seçeneğini ( [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi) düzenleyebilirsiniz. Aşağıdaki örnek, bu sınırı etkin bir şekilde kaldırır (önerilmez):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

**Testexcludepathboundsexceıda** seçeneğini, bu sorunları genel olarak nasıl ele alınacağını IntelliTest 'e bildirmek için de ayarlayabilirsiniz.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns aşıldı

IntelliTest, [giriş oluşturma](input-generation.md)sırasında ele aldığı yürütme yollarının sayısını sınırlar. Bu özellik, programda döngü veya özyineleme olduğunda IntelliTest 'in sonlandırılmasını sağlar.

Her IntelliTest, belirli girişlerle parametreli testi çalıştırdığında yeni bir test durumu yayar, bu durum olmayabilir. Daha fazla bilgi için bkz. [Testemissionfilter](exploration-bounds.md#testemissionfilter) .

**PexSettingsAttributeBase** öğesinden türetilmiş bir özniteliğin **maxçalıştırmaları** seçeneğini düzenleyerek, örneğin [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod). Aşağıdaki örnek, bu sınırı etkin bir şekilde kaldırır (önerilmez):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests aşıldı

IntelliTest, [giriş oluşturma](input-generation.md)sırasında ele aldığı yürütme yollarının sayısını sınırlar. Bu özellik, programda döngü veya özyineleme olduğunda IntelliTest 'in sonlandırılmasını sağlar.

Her IntelliTest, belirli girişlerle parametreli testi çalıştırdığında yeni bir test durumu yayar, bu durum olmayabilir. Daha fazla bilgi için bkz. [Testemissionfilter](exploration-bounds.md#testemissionfilter) .

IntelliTest başlangıçta çoğunlukla çok sayıda ilginç test girişi bulurken, daha fazla test bir süre içinde olabilir. Bu seçenek, IntelliTest 'in başka bir ilgili test girişini bulmaya ne kadar süreyle devam edebilir olduğunu yönetir.

**PexSettingsAttributeBase**'den türetilmiş bir özniteliğin **Maxrunswithoutnewtests** seçeneğini ( [PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi) düzenleyebilirsiniz. Aşağıdaki örnek, bu sınırı etkin bir şekilde kaldırır (önerilmez):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Çözüm somutlaştırılamıyor

Bu hata genellikle daha önceki bir hatanın sonucudur. IntelliTest, yeni test girişlerini belirlemede bir [kısıtlama çözücü](input-generation.md#constraint-solver) kullanır. Bazen, [kısıtlama çözücü](input-generation.md#constraint-solver) tarafından önerilen test girdileri geçersizdir. Bu durum şu durumlarda olabilir:

* belirli kısıtlamalar bilinmiyor
* değerler Kullanıcı tanımlı bir biçimde oluşturulduysa, hataların Kullanıcı kodunda oluşmasına neden olur
* dahil edilen türlerden bazıları IntelliTest tarafından denetlenmedi (örneğin, COM sınıfları)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Nesne oluşturmak için yardım gerekiyor

IntelliTest [Test girişleri oluşturur](input-generation.md)ve girdilerden bazıları alanlara sahip nesneler olabilir.
Burada, IntelliTest özel bir alana sahip bir sınıfın örneğini oluşturmaya çalışır ve bu özel alan belirli bir değere sahip olduğunda ilginç bir program davranışının gerçekleşeceğini varsayar.

Ancak, yansıma ile mümkün olsa da, IntelliTest rastgele alan değerleriyle nesne üretmez.
Bunun yerine, bu durumlarda, bir nesne oluşturmak için bir sınıfın genel yöntemlerinin nasıl kullanılacağına ilişkin ipuçları sağlamak ve özel alanının istenen değere sahip olduğu bir duruma getirmek için kullanıcıya bağımlıdır.

Her ilginç nesne oluşturmaya yönelik IntelliTest 'i nasıl sağlayabileceğinizi öğrenmek için [varolan sınıfların örneğini](input-generation.md#existing-classes) oluşturma bölümünü okuyun.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Türleri bulmak için yardım gerekiyor

IntelliTest her türlü .NET türü için [Test girişleri oluşturur](input-generation.md) . Burada, IntelliTest soyut bir sınıftan türetilmiş veya soyut bir arabirim uygulayan bir örnek oluşturmayı dener ve IntelliTest, kısıtlamaları karşılayan herhangi bir türden haberdar değildir.

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

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.
