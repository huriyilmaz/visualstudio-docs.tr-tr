---
title: Uyarılar ve hatalar | Microsoft IntelliTest Geliştirici Test Aracı
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Warnings and errors
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c3f5fe55a4e1afb1a9551d43d0d61ae9f76b81e4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77275444"
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
  * [Çözüm Concretize Olamaz](#cannot-concretize-solution)

* **Etki Alanları veya Çalışma Zamanı**
  * [Nesne oluşturmak için yardıma ihtiyacınız var](#help-construct)
  * [Türleri bulmak için yardıma ihtiyacınız var](#help-types)
  * [Kullanılabilir Türü Tahmin](#usable-type-guessed)

* **Yürütme**
  * [Keşif Sırasında Beklenmeyen Hata](#unexpected-exploration)
  * [TargetInvocationException](#targetinvocationexception)

* **Araçları**
  * [Kullanılmayan Yöntem Called](#uninstrumented-method-called)
  * [Dış Yöntem Adlı](#external-method-called)
  * [Uninstrumentable Yöntemi Called](#uninstrumentable-method-called)
  * [Test edilebilirlik Sorunu](#testability-issue)
  * [Sınırlama](#limitation)

* **Yorumlayıcı**
  * [Gözlenen Çağrı Uyuşmazlığı](#observed-call-mismatch)
  * [Statik Alanda Depolanan Değer](#value-static-field)

<a name="maxbranches-exceeded"></a>
## <a name="maxbranches-exceeded"></a>MaxBranches aşıldı

IntelliTest, [giriş oluşturma](input-generation.md)sırasında keşfettiği herhangi bir yürütme yolunun uzunluğunu sınırlar. Bu özellik, program sonsuz bir döngüye girdiğinde IntelliTest'in yanıt vermesini önler.

Yürütülen ve izlenen kodun her koşullu ve koşulsuz dalı, [parametreli birim testinin](test-generation.md#parameterized-unit-testing)girişlerine bağlı olmayan dallar da dahil olmak üzere bu sınıra doğru sayılır.

Örneğin, aşağıdaki kod dalları 100 sırasına göre tüketir:

```csharp
for (int i=0; i<100; i++) { }
```

[PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi **PexSettingsAttributeBase'den**türetilen bir özniteliğin **MaxBranches** seçeneğini değiştirebilirsiniz. Aşağıdaki örnek bu sınırı etkili bir şekilde kaldırır:

```csharp
[PexMethod(MaxBranches=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

Ayrıca, IntelliTest'e bu sorunlarla ne kadar genel olarak başa çıkılacağı konusunda bilgi vermek için **TestExcludePathBoundsExceeded** seçeneğini de ayarlayabilirsiniz.

Test kodunda, döngü koşulu tarafından oluşturulan kısıtlamaları yoksaymak için [PexSymbolicValue'ı](static-helper-classes.md#pexsymbolicvalue) kullanabilirsiniz:

```csharp
for (int i=0;
    PexSymbolicValue.Ignore(i<100); // IntelliTest will 'forget' about this path condition
    i++)
{ }
```

<a name="maxconstraintsolvertime-exceeded"></a>
## <a name="maxconstraintsolvertime-exceeded"></a>MaxConstraintSolverTime aşıldı

IntelliTest, yeni test girişlerini hesaplamak için bir [kısıtlama çözücü](input-generation.md#constraint-solver) kullanır. Kısıtlama çözme çok zaman alıcı bir süreç olabilir, bu yüzden IntelliTest sınırları yapılandırmak için izin verir - özellikle, **MaxConstraintSolverTime**.

Birçok uygulama için, zaman anına önemli ölçüde artan daha iyi kapsama neden olmaz. Bunun nedeni, çoğu zaman anına çözüm olmayan kısıtlama sistemlerinden kaynaklanmaktadır. Ancak, IntelliTest bir zaman alacaktır tüm olası çözümleri denemeden tutarsız olduğunu belirlemek mümkün olmayabilir.

<a name="maxconditions-exceeded"></a>
## <a name="maxconditions-exceeded"></a>MaxConditions aşıldı

IntelliTest, [giriş oluşturma](input-generation.md)sırasında keşfettiği herhangi bir yürütme yolunun uzunluğunu sınırlar. Bu özellik, program sonsuz bir döngüye girdiğinde IntelliTest'in yanıt vermesini önler.

[Parametreli birim testinin](test-generation.md#parameterized-unit-testing) girişlerine bağlı her koşullu dal bu sınıra doğru sayılır.

Örneğin, aşağıdaki koddaki her yol **n+1** koşullarını tüketir:

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

[PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi **PexSettingsAttributeBase'den**türetilen bir özniteliğin **MaxConditions** seçeneğini değiştirebilirsiniz. Örnek:

```csharp
[PexMethod(MaxConditions=10000)]
void ParameterizedTest(int n) {
    // ...
}
```

IntelliTest'e bu sorunlarla genel olarak nasıl başa çıkılacağı konusunda bilgi vermek için **TestExcludePathBoundsExceeded** seçeneğini de ayarlayabilirsiniz.

Döngü koşulu tarafından oluşturulan kısıtlamaları yoksaymak için [PexSymbolicValue](static-helper-classes.md#pexsymbolicvalue) kullanabilirsiniz:

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

IntelliTest, [giriş oluşturma](input-generation.md)sırasında keşfettiği herhangi bir yürütme yolunun uzunluğunu sınırlar. Bu özellik, program sonsuz bir döngüye girdiğinde IntelliTest'in yanıt vermesini önler.

Yürütülen ve izlenen kodun her çağrısı (doğrudan, dolaylı, sanal veya atlama) bu sınıra doğru sayılır.

[PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi **PexSettingsAttributeBase'den**türetilen bir özniteliğin **MaxCalls** seçeneğini değiştirebilirsiniz. Aşağıdaki örnek bu sınırı etkili bir şekilde kaldırır:

```csharp
[PexMethod(MaxCalls=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

IntelliTest'e bu sorunlarla genel olarak nasıl başa çıkılacağı konusunda bilgi vermek için **TestExcludePathBoundsExceeded** seçeneğini de ayarlayabilirsiniz.

<a name="maxstack-exceeded"></a>
## <a name="maxstack-exceeded"></a>MaxStack aşıldı

IntelliTest, [giriş oluşturma](input-generation.md)sırasında keşfettiği herhangi bir yürütme yolunun çağrı yığınının boyutunu sınırlar. Bu özellik, bir yığın taşma oluştuğunda IntelliTest'in sonlandırmasını önler.

[PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi **PexSettingsAttributeBase'den**türetilen bir özniteliğin **MaxStack** seçeneğini değiştirebilirsiniz. Aşağıdaki örnek bu sınırı etkili bir şekilde kaldırır (önerilmez):

```csharp
[PexMethod(MaxStack=int.MaxValue)]
public void MyTest(...) {
    // ....
}
```

IntelliTest'e bu sorunlarla genel olarak nasıl başa çıkılacağı konusunda bilgi vermek için **TestExcludePathBoundsExceeded** seçeneğini de ayarlayabilirsiniz.

<a name="maxruns-exceeded"></a>
## <a name="maxruns-exceeded"></a>MaxRuns aşıldı

IntelliTest, [giriş oluşturma](input-generation.md)sırasında keşfettiği yürütme yollarının sayısını sınırlar. Bu özellik, program döngüleri veya özyineleme olduğunda IntelliTest'in sonlandırmasını sağlar.

IntelliTest, parametreli testi belirli girişlerle her çalıştırdığında yeni bir test çalışması yayan bir durum olmayabilir. Daha fazla bilgi için [TestEmissionFilter'e](exploration-bounds.md#testemissionfilter) bakın.

[PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi **PexSettingsAttributeBase'den**türetilen bir özniteliğin **MaxRuns** seçeneğini değiştirebilirsiniz. Aşağıdaki örnek bu sınırı etkili bir şekilde kaldırır (önerilmez):

```csharp
[PexMethod(MaxRuns=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="maxrunswithoutnewtests-exceeded"></a>
## <a name="maxrunswithoutnewtests-exceeded"></a>MaxRunsWithoutNewTests aşıldı

IntelliTest, [giriş oluşturma](input-generation.md)sırasında keşfettiği yürütme yollarının sayısını sınırlar. Bu özellik, program döngüleri veya özyineleme olduğunda IntelliTest'in sonlandırmasını sağlar.

IntelliTest, parametreli testi belirli girişlerle her çalıştırdığında yeni bir test çalışması yayan bir durum olmayabilir. Daha fazla bilgi için [TestEmissionFilter'e](exploration-bounds.md#testemissionfilter) bakın.

IntelliTest genellikle başlangıçta birçok ilginç test girişleri bulur, o olmayabilir - bir süre sonra - başka testler yontmak. Bu seçenek, IntelliTest'in başka bir ilgili test girdisi bulmaya ne kadar süre devam edebileceğini yönetir.

[PexClass](attribute-glossary.md#pexclass) veya [PexMethod](attribute-glossary.md#pexmethod)gibi **PexSettingsAttributeBase'den**türetilen bir özniteliğin **MaxRunsWithoutNewTests** seçeneğini değiştirebilirsiniz. Aşağıdaki örnek bu sınırı etkili bir şekilde kaldırır (önerilmez):

```csharp
[PexMethod(MaxRunsWithoutNewTests=2000)]
public void MyTest(...) {
    // ....
}
```

<a name="cannot-concretize-solution"></a>
## <a name="cannot-concretize-solution"></a>Çözüm somutlaştırılamıyor

Bu hata genellikle önceki bir hatanın sonucudur. IntelliTest, yeni test girişlerini belirlemek için bir [kısıtlama çözücü](input-generation.md#constraint-solver) kullanır. Bazen, [kısıtlama çözücü](input-generation.md#constraint-solver) tarafından önerilen test girişleri geçersizdir. Bu, şu anda olabilir:

* bazı kısıtlamalar bilinmemektedir
* değerler kullanıcı tanımlı bir şekilde oluşturulursa, kullanıcı kodunda hatalar oluşmasına neden
* ilgili türlerden bazıları IntelliTest tarafından denetlenmeyen başlatma mantığına sahiptir (örneğin, COM sınıfları)

<a name="help-construct"></a>
## <a name="need-help-to-construct-object"></a>Nesne oluşturmak için yardım gerekiyor

IntelliTest [test girişleri oluşturur](input-generation.md)ve bazı girişler alanları olan nesneler olabilir.
Burada, IntelliTest özel bir alana sahip bir sınıfın bir örneğini oluşturmaya çalışır ve bu özel alanın belirli bir değeri olduğunda ilginç bir program davranışının oluşacağını varsayar.

Ancak, bu Yansıma ile mümkün olsa da, IntelliTest rasgele alan değerleri ile nesneleri üretmez.
Bunun yerine, bu gibi durumlarda, bir nesne oluşturmak için bir sınıfın ortak yöntemlerini nasıl kullanacağı ve özel alanının istenen değere sahip olduğu bir duruma getirmek hakkında ipuçları sağlamak için kullanıcıya güvenir.

IntelliTest'in ilginç nesneler oluşturmasına nasıl yardımcı olabileceğinizi öğrenmek için [varolan sınıfları Anlık](input-generation.md#existing-classes) Olarak okuyun.

<a name="help-types"></a>
## <a name="need-help-to-find-types"></a>Türleri bulmak için yardım gerekiyor

IntelliTest herhangi bir .NET türü için [test girişleri oluşturur.](input-generation.md) Burada, IntelliTest soyut bir sınıftan türeyen veya soyut bir arabirim uygulayan bir örnek oluşturmaya çalışır ve IntelliTest kısıtlamaları karşılayan herhangi bir tür bilmez.

Kısıtlamalarla eşleşen bir veya daha fazla türü işaret ederek IntelliTest'e yardımcı olabilirsiniz. Genellikle, aşağıdaki özniteliklerden biri yardımcı olacaktır:

* **PexUseTypeAttribute**, belirli bir türe işaret eden.

  Örneğin, IntelliTest **"System.Collections.IDictionary'ye**atadan atabilen türleri bilmediğini" bildiriyorsa, teste (veya fikstür sınıfına) aşağıdaki **PexUseTypeAttribute'ı** ekleyerek yardımcı olabilirsiniz:

  ```csharp
  [PexMethod]
  [PexUseType(typeof(System.Collections.Hashtable))]
  public void MyTest(IDictionary[] dictionaries) { ... }
  ```

* **Derleme düzeyinde öznitelik**

  ```csharp
  [assembly: PexUseType(typeof(System.Collections.Hashtable))]
  ```

<a name="usable-type-guessed"></a>
## <a name="usable-type-guessed"></a>Kullanılabilir tür tahmin edildi

IntelliTest herhangi bir .NET türü için [test girişleri oluşturur.](input-generation.md) Bir tür soyut veya arabirim olduğunda, IntelliTest bu türde belirli bir uygulama seçmelidir. Bu seçimi yapmak için, hangi türlerin var olduğunu bilmek gerekir.

Bu uyarı gösterildiğinde, IntelliTest'in başvurulan derlemelerden bazılarına baktığını ve bir uygulama türü bulduğunu, ancak bu türü kullanıp kullanmaması veya başka bir yerde daha uygun türler olup olmadığından emin olmadığını gösterir. IntelliTest sadece umut verici görünüyordu bir tür seçti.

Bu uyarıyı önlemek için, IntelliTest'in tür seçimini kabul edebilir veya ilgili [pexUseType](attribute-glossary.md#pexusetype)ekleyerek intelliTest'e diğer türleri kullanmada yardımcı olabilirsiniz.

<a name="unexpected-exploration"></a>
## <a name="unexpected-failure-during-exploration"></a>Araştırma sırasında beklenmeyen hata oluştu

Bir testi araştırırken beklenmeyen bir özel durum yakalandı.

Lütfen [bunu bir hata olarak bildirin.](#report-bug)

<a name="targetinvocationexception"></a>
## <a name="targetinvocationexception"></a>TargetInvocationException

Kullanıcı kodunda bir özel durum oluştu. Yığın izini inceleyin ve kodunuzdaki hatayı kaldırın.

<a name="uninstrumented-method-called"></a>
## <a name="uninstrumented-method-called"></a>İzlenmeyen metot çağrıldı

IntelliTest, program yürütmeyi izleyerek [test girdileri oluşturur.](input-generation.md) IntelliTest'in davranışını izleyabilmesi için ilgili kodun düzgün bir şekilde işletilmiş olması esastır.

Bu uyarı, enstrümantetik kod başka bir, araçsız derlemeyöntemleri çağırır görüntülenir.
IntelliTest'in her ikisinin etkileşimini de keşfetmesini istiyorsanız, diğer derlemeyi (veya parçalarını) da enstrümanlamalısınız.

<a name="external-method-called"></a>
## <a name="external-method-called"></a>Dış metot çağrıldı

IntelliTest,.NET uygulamalarının yürütülmesini izleyerek [test girdileri oluşturur.](input-generation.md)
IntelliTest ,NET dilinde yazılmayan kod için anlamlı test girişleri oluşturamaz.

Bu uyarı, araçlı kod, IntelliTest'in çözümleyemediği yönetilmeyen, yerel bir yöntem aradığında görüntülenir. IntelliTest'in her ikisinin etkileşimini keşfetmesini istiyorsanız, yönetilmeyen yöntemle alay etmelisiniz.

<a name="uninstrumentable-method-called"></a>
## <a name="uninstrumentable-method-called"></a>İzlenmeyen metot çağrıldı

IntelliTest,.NET uygulamalarının yürütülmesini izleyerek [test girdileri oluşturur.](input-generation.md) Ancak, teknik nedenlerden dolayı IntelliTest'in izleyemediği bazı yöntemler vardır. Örneğin, IntelliTest statik bir oluşturucuya izleyemez.

Bu uyarı, araçlı kod IntelliTest'in izleyemeyeceği bir yöntem aradığında görüntülenir.

<a name="testability-issue"></a>
## <a name="testability-issue"></a>Test edilebilirlik sorunu

IntelliTest, program yürütülmesini izleyerek [test girdileri oluşturur.](input-generation.md) Yalnızca program deterministic olduğunda ve ilgili davranış test girişleri tarafından denetlendiğinde ilgili test girişleri oluşturabilir.

Bu uyarı, test deneme nizin yürütülmesi sırasında, deterministically olmayan ya da çevre ile etkileşimde bulunan bir yöntem çağrıldı çünkü görünür. Örnekler **System.Random** ve **System.IO.File**yöntemleridir. IntelliTest anlamlı test girişleri oluşturmak istiyorsanız, test edilebilirlik sorunları olarak IntelliTest bayraklar yöntemleri alay gerekir.

<a name="limitation"></a>
## <a name="limitation"></a>Sınırlama

IntelliTest bir [kısıtlama çözücü](input-generation.md#constraint-solver)kullanarak test [girişleri oluşturur.](input-generation.md)
Ancak, [kısıtlama çözücü](input-generation.md#constraint-solver)kapsamı dışında bazı işlemler vardır.
Bu şu anda içerir:

* çoğu kayan nokta işlemleri (yalnızca bazı doğrusal aritmetik kayan nokta numaraları nda desteklenir)
* kayan nokta sayıları ve tümsavarlar arasındaki dönüşümler
* **System.Ondalık** tipteki tüm işlemler

Bu uyarı, çalıştırılan kod bir işlem gerçekleştirdiğinde veya IntelliTest'in yorumlayamayacağı bir yöntem aradığında görüntülenir.

<a name="observed-call-mismatch"></a>
## <a name="observed-call-mismatch"></a>Çağrı uyuşmazlığı gözlemlendi

IntelliTest, program yürütmeyi izleyerek [test girdileri oluşturur.](input-generation.md) Ancak, IntelliTest tüm yönergeleri izlemek mümkün olmayabilir. Örneğin, yerel kodu izleyemez ve işletilen olmayan kodu izleyemez.

IntelliTest kodu izleyemiyorsa, bu kodla alakalı test girişleri oluşturamaz.
Genellikle, IntelliTest bu yönteme bir çağrı dönene kadar bir yöntemi izleyemez gerçeğinin farkında değildir. Ancak, bu uyarının nedeni:

* IntelliTest, enstrümanedilmemiş bir yönteme çağrı başlatan bazı kodları izledi
* Enstrümantine edilmiş bir yöntem olarak adlandırılan araçsız yöntem
* IntelliTest, çağrılan enstrümante yöntemi izler

IntelliTest, enstrümantif olmayan ara yöntemin ne yaptığını bilmediğinden, iç içe geçmeli çağrıyla ilgili test girişleri oluşturamayabilir.

<a name="value-static-field"></a>
## <a name="value-stored-in-static-field"></a>Değer statik alanda depolandı

IntelliTest, ilgili [test girişlerini](input-generation.md) yalnızca birim test deterministik olduğunda sistematik olarak belirleyebilir; başka bir deyişle, her zaman aynı test girişleri için aynı şekilde şekilde olur. Özellikle, bu testin sistemi bu testi yeniden yürütmeye izin veren bir durumda bırakması gerektiği anlamına gelir.
İdeal olarak, birim testi herhangi bir küresel durumu değiştirmemeli, ancak küresellerle tüm etkileşimler alay edilmelidir.

Bu uyarı, statik bir alanın değiştirilmediğini gösterir; bu testnonterministically olmayan şekilde görünmesini sağlayabilir.

Bazı durumlarda, statik bir alanı değiştirmek kabul edilebilir:

* test girişleri değişikliği geri almak için kurulum veya temizleme kodu neden olduğunda
* alan yalnızca bir kez başlatıldığında ve değer daha sonra değişmediğinde

<a name="report-bug"></a>

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.
