---
title: Etki Alanına Özgü bir Dilde Doğrulama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a37dbb4d9754641b4bcca826ff0ec77c7298d9b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594012"
---
# <a name="validation-in-a-domain-specific-language"></a>Etki Alanına Özgü bir Dilde Doğrulama
Etki alanına özgü dilin (DSL) yazarı olarak, Kullanıcı tarafından oluşturulan modelin anlamlı olduğunu doğrulamak için doğrulama kısıtlamaları tanımlayabilirsiniz. Örneğin, DSL 'niz kullanıcıların bir kişi ve üst öğelerinden oluşan aile ağacını çizmesini sağlamasına izin veriyorsa, alt öğelerinden sonra Doğum tarihleri olmasını sağlayan bir kısıtlama yazabilirsiniz.

 Model kaydedildiğinde, ne zaman açıldığı ve Kullanıcı **Doğrula** menü komutunu açıkça çalıştırdığında doğrulama kısıtlamalarının yürütmesini sağlayabilirsiniz. Ayrıca, program denetimi altında doğrulama yürütebilirsiniz. Örneğin, bir özellik değerindeki veya ilişkisindeki bir değişikliğe yanıt olarak doğrulamayı çalıştırabilirsiniz.

 Yalnızca metin şablonları veya kullanıcılarınızın modellerini işleyen diğer araçlar yazıyorsanız doğrulama özellikle önemlidir. Doğrulama, modellerin bu araçların kabul edilen önkoşulları yerine getirmelerini sağlar.

> [!WARNING]
> Ayrıca, uzantı menü komutları ve hareket işleyicileri ile birlikte, DSL 'nize ayrı Uzantılarda, doğrulama kısıtlamalarının tanımlanmasına de izin verebilirsiniz. Kullanıcılar, bu uzantıları DSL 'ye ek olarak yüklemeyi seçebilirler. Daha fazla bilgi için bkz. [mef kullanarak DSL 'Nizi genişletme](../modeling/extend-your-dsl-by-using-mef.md).

## <a name="running-validation"></a>Doğrulama çalıştırılıyor
 Bir Kullanıcı bir modeli düzenlenirken, diğer bir deyişle, etki alanına özgü dilinizin bir örneğidir, aşağıdaki eylemler doğrulamayı çalıştırabilir:

- Diyagrama sağ tıklayın ve **Tümünü doğrula**' yı seçin.

- DSL Gezgininde en üst düğüme sağ tıklayın ve **Tümünü doğrula** ' yı seçin.

- Modeli kaydedin.

- Modeli açın.

- Ayrıca, doğrulama çalıştıran program kodunu (örneğin, bir menü komutunun parçası olarak veya bir değişikliğe yanıt olarak) yazabilirsiniz.

  Herhangi bir doğrulama hatası, **hata listesi** penceresinde görünür. Kullanıcı, hatanın nedeni olan model öğelerini seçmek için bir hata iletisine çift tıklatabilir.

## <a name="defining-validation-constraints"></a>Doğrulama kısıtlamalarını tanımlama
 Doğrulama kısıtlamalarını, etki alanı sınıflarına veya DSL ilişkilerine doğrulama yöntemleri ekleyerek tanımlarsınız. Doğrulama çalıştırıldığında ya Kullanıcı veya program denetimi altında doğrulama yöntemlerinin bazıları veya tümü yürütülür. Her yöntem sınıfının her örneğine uygulanır ve her sınıfta birkaç doğrulama yöntemi olabilir.

 Her doğrulama yöntemi bulduğu hataları bildirir.

> [!NOTE]
> Doğrulama yöntemleri hataları raporlar, ancak modeli değiştirmez. Belirli değişiklikleri ayarlamak veya engellemek isterseniz bkz. [doğrulamaya alternatifler](#alternatives).

#### <a name="to-define-a-validation-constraint"></a>Doğrulama kısıtlaması tanımlamak için

1. **Editor\validation** düğümünde doğrulamayı etkinleştir:

   1. **Dsl\dsldefinition.exe**' i açın.

   2. DSL Gezgini ' nde **Düzenleyici** düğümünü genişletin ve **doğrulama**' yı seçin.

   3. Özellikler penceresi, **kullanım** özelliklerini `true`olarak ayarlayın. Bu özelliklerin tümünü ayarlamak en kolay yöntemdir.

   4. **Çözüm Gezgini** araç çubuğunda **Tüm Şablonları Dönüştür** ' e tıklayın.

2. Bir veya daha fazla etki alanı sınıfınız veya etki alanı ilişkilerinden oluşan kısmi sınıf tanımları yazın. Bu tanımları **DSL** projesindeki yeni bir kod dosyasına yazın.

3. Her sınıfın Bu öznitelikle ön eki:

   ```csharp
   [ValidationState(ValidationState.Enabled)]
   ```

   - Bu öznitelik, varsayılan olarak türetilmiş sınıflar için doğrulamayı de etkinleştirir. Belirli bir türetilmiş sınıf için doğrulamayı devre dışı bırakmak istiyorsanız `ValidationState.Disabled`kullanabilirsiniz.

4. Sınıflara doğrulama yöntemleri ekleyin. Her doğrulama yöntemi herhangi bir ada sahip olabilir, ancak <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext>türünde bir parametreye sahip olabilir.

    Ön eki bir veya daha fazla `ValidationMethod` özniteliği olmalıdır:

   ```csharp
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]
   ```

    ValidationCategories, yöntemin ne zaman yürütüleceğini belirtir.

   Örneğin:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;

// Allow validation methods in this class:
[ValidationState(ValidationState.Enabled)]
// In this DSL, ParentsHaveChildren is a domain relationship
// from Person to Person:
public partial class ParentsHaveChildren
{
  // Identify the method as a validation method:
  [ValidationMethod
  ( // Specify which events cause the method to be invoked:
    ValidationCategories.Open // On file load.
  | ValidationCategories.Save // On save to file.
  | ValidationCategories.Menu // On user menu command.
  )]
  // This method is applied to each instance of the
  // type (and its subtypes) in a model:
  private void ValidateParentBirth(ValidationContext context)
  {
    // In this DSL, the role names of this relationship
    // are "Child" and "Parent":
     if (this.Child.BirthYear < this.Parent.BirthYear
        // Allow user to leave the year unset:
        && this.Child.BirthYear != 0)
      {
        context.LogError(
             // Description:
                       "Child must be born after Parent",
             // Unique code for this error:
                       "FAB001ParentBirthError",
              // Objects to select when user double-clicks error:
                       this.Child,
                       this.Parent);
    }
  }
```

 Bu kodla ilgili aşağıdaki noktalara dikkat edin:

- , Etki alanı sınıflarına veya etki alanı ilişkilerine doğrulama yöntemleri ekleyebilirsiniz. Bu türlerin kodu **Dsl\generated Code\Domain\*. cs**' dir.

- Her doğrulama yöntemi, sınıfının ve alt sınıflarının her örneğine uygulanır. Bir etki alanı ilişkisi söz konusu olduğunda, her örnek iki model öğesi arasında bir bağlantıdır.

- Doğrulama yöntemleri belirtilen sırada uygulanmaz ve her yöntem, öngörülebilir bir sırada sınıfının örneklerine uygulanmaz.

- Genellikle, bu durum tutarsız sonuçlara yol açacağından, depolama içeriğini güncelleştirmek için bir doğrulama yöntemi için hatalı uygulamadır. Bunun yerine, yöntemi `context.LogError`, `LogWarning` veya `LogInfo`çağırarak herhangi bir hata bildirmelidir.

- LogError çağrısında, Kullanıcı hata iletisine çift tıkladığında seçilecek model öğelerinin veya ilişki bağlantılarının bir listesini sağlayabilirsiniz.

- Program kodundaki modeli okuma hakkında daha fazla bilgi için bkz. [program kodunda modeli gezinme ve güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Örnek, aşağıdaki etki alanı modeli için geçerlidir. ParentsHaveChildren ilişkisinde, alt ve üst öğe olarak adlandırılan roller bulunur.

  ![DSL tanımı diyagramı &#45; aile ağacı modeli](../modeling/media/familyt_person.png)

## <a name="validation-categories"></a>Doğrulama kategorileri
 <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> özniteliğinde, doğrulama yönteminin ne zaman yürütülmesi gerektiğini belirtirsiniz.

|Kategori|Yürütme|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Kullanıcı Doğrula menü komutunu istediğinde.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Model dosyası açıldığında.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Dosya kaydedildiğinde. Doğrulama hataları varsa, kullanıcıya kaydetme işlemini iptal etme seçeneği verilir.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Dosya kaydedildiğinde. Bu kategorideki metotlardan hata varsa, Kullanıcı dosyayı yeniden açmak mümkün olmayabilir.<br /><br /> Yinelenen adlar veya kimlikler veya yükleme hataları oluşmasına neden olabilecek diğer koşullar için test edilen doğrulama yöntemleri için bu kategoriyi kullanın.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|ValidateCustom yöntemi çağrıldığında. Bu kategorideki doğrulamalar yalnızca program kodundan çağrılabilir.<br /><br /> Daha fazla bilgi için bkz. [özel doğrulama kategorileri](#custom).|

## <a name="where-to-place-validation-methods"></a>Doğrulama yöntemlerinin yerleştirileceği konum
 Aynı etkiyi, farklı bir türe bir doğrulama yöntemi yerleştirerek genellikle elde edebilirsiniz. Örneğin, ParentsHaveChildren ilişkisi yerine Person sınıfına bir yöntem ekleyebilir ve bağlantılar arasında yineleme yapabilirsiniz:

```
[ValidationState(ValidationState.Enabled)]
public partial class Person
{[ValidationMethod
 ( ValidationCategories.Open
 | ValidationCategories.Save
 | ValidationCategories.Menu
 )
]
  private void ValidateParentBirth(ValidationContext context)
  {
    // Iterate through ParentHasChildren links:
    foreach (Person parent in this.Parents)
    {
        if (this.BirthYear <= parent.BirthYear)
        { ...
```

 **Doğrulama kısıtlamalarını toplama.** Doğrulamayı öngörülebilir bir sırayla uygulamak için, modelinizin kök öğesi gibi bir sahip sınıfında tek bir doğrulama yöntemi tanımlayın. Bu teknik, birden çok hata raporunu tek bir iletide toplamanızı sağlar.

 Dezavantajları, birleştirilmiş metodun yönetilmesi daha kolaydır ve kısıtlamaların tümünün aynı `ValidationCategories`sahip olması gerekir. Bu nedenle, mümkünse her kısıtlamayı ayrı bir yöntemde tutmanızı öneririz.

 **Bağlam önbelleğindeki değerleri geçirme.** Bağlam parametresinde, içine rastgele değerler yerleştirebileceğiniz bir sözlük bulunur. Sözlük, doğrulama çalışmasının ömrü boyunca devam ettirir. Belirli bir doğrulama yöntemi, örneğin, bağlamda hata sayısını tutabilir ve yinelenen iletilerle hata penceresinin taşmasını önlemek için kullanabilirsiniz. Örneğin:

```csharp
List<ParentsHaveChildren> erroneousLinks;
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))
erroneousLinks = new List<ParentsHaveChildren>();
erroneousLinks.Add(this);
context.SetCacheValue("erroneousLinks", erroneousLinks);
if (erroneousLinks.Count < 5) { context.LogError( ... ); }
```

## <a name="validation-of-multiplicities"></a>Çeşitlilimler doğrulaması
 Minimum çoğulluğu denetlemek için doğrulama yöntemleri DSL 'niz için otomatik olarak oluşturulur. Kod **Dsl\generated Code\MultiplicityValidation.cs dizinine**yazılır. Bu yöntemler, DSL Explorer 'daki **Editor\validation** düğümünde doğrulamayı etkinleştirdiğinizde geçerli olur.

 Bir etki alanı ilişkisinin bir rolünün çokluğunu 1.. * veya 1.. 1 olacak şekilde ayarlarsanız, Kullanıcı bu ilişkinin bir bağlantısını oluşturmaz, bir doğrulama hata iletisi görüntülenir.

 Örneğin, DSL 'niz kişi ve kasaya sahip bir ilişkiye sahip olan bir ilişki olan bir ilişki olan bir ilişki olan **1...\\** * adlı ilişki, şehir rolü olan her kişi için bir hata mesajı görüntülenir.

## <a name="running-validation-from-program-code"></a>Program kodundan doğrulama çalıştırma
 Doğrulaması, bir ValidationController 'a erişerek veya oluşturarak çalıştırabilirsiniz. Hataların hata penceresinde kullanıcıya görüntülenmesini istiyorsanız, diyagramınızın DocData 'a eklenmiş olan ValidationController ' ı kullanın. Örneğin, bir menü komutu yazıyorsanız, `CurrentDocData.ValidationController` komut kümesi sınıfında kullanılabilir:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
partial class MyLanguageCommandSet
{
  private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
  {
   ValidationController controller = this.CurrentDocData.ValidationController;
...
```

 Daha fazla bilgi için bkz. [nasıl yapılır: kısayol menüsüne komut ekleme](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).

 Ayrıca ayrı bir doğrulama denetleyicisi oluşturabilir ve hataları kendiniz yönetebilirsiniz. Örneğin:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
Store store = ...;
VsValidationController validator = new VsValidationController(s);
// Validate all elements in the Store:
if (!validator.Validate(store, ValidationCategories.Save))
{
  // Deal with errors:
  foreach (ValidationMessage message in validator.ValidationMessages) { ... }
}
```

## <a name="running-validation-when-a-change-occurs"></a>Değişiklik gerçekleştiğinde doğrulama çalıştırma
 Modelin geçersiz hale gelmesi durumunda kullanıcının hemen uyarı olduğundan emin olmak istiyorsanız, doğrulamayı çalıştıran bir depo olayı tanımlayabilirsiniz. Mağaza olayları hakkında daha fazla bilgi için bkz. [olay Işleyicileri değişiklikleri model dışında yayma](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Doğrulama koduna ek olarak, aşağıdaki örneğe benzer içeriğe sahip **DslPackage** projenize özel bir kod dosyası ekleyin. Bu kod, belgeye bağlı `ValidationController` kullanır. Bu denetleyici, Visual Studio hata listesindeki doğrulama hatalarını görüntüler.

```csharp
using System;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
namespace Company.FamilyTree
{
  partial class FamilyTreeDocData // Change name to your DocData.
  {
    // Register the store event handler:
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded();
      DomainClassInfo observedLinkInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(ParentsHaveChildren));
      DomainClassInfo observedClassInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(Person));
      EventManagerDirectory events = this.Store.EventManagerDirectory;
      events.ElementAdded
         .Add(observedLinkInfo, new EventHandler<ElementAddedEventArgs>(ParentLinkAddedHandler));
      events.ElementDeleted.Add(observedLinkInfo, new EventHandler<ElementDeletedEventArgs>(ParentLinkDeletedHandler));
      events.ElementPropertyChanged.Add(observedClassInfo, new EventHandler<ElementPropertyChangedEventArgs>(BirthDateChangedHandler));
    }
    // Handler will be called after transaction that creates a link:
    private void ParentLinkAddedHandler(object sender,
                                ElementAddedEventArgs e)
    {
      this.ValidationController.Validate(e.ModelElement,
           ValidationCategories.Save);
    }
    // Called when a link is deleted:
    private void ParentLinkDeletedHandler(object sender,
                                ElementDeletedEventArgs e)
    {
      // Don't apply validation to a deleted item!
      // - Validate store to refresh the error list.
      this.ValidationController.Validate(this.Store,
           ValidationCategories.Save);
    }
    // Called when any property of a Person element changes:
    private void BirthDateChangedHandler(object sender,
                      ElementPropertyChangedEventArgs e)
    {
      Person person = e.ModelElement as Person;
      // Not interested in changes in other properties:
      if (e.DomainProperty.Id != Person.BirthYearDomainPropertyId)
          return;

      // Validate all parent links to and from the person:
      this.ValidationController.Validate(
        ParentsHaveChildren.GetLinksToParents(person)
        .Concat(ParentsHaveChildren.GetLinksToChildren(person))
        , ValidationCategories.Save);
    }
  }
}
```

 İşleyiciler, bağlantıları veya öğeleri etkileyen geri alma veya yineleme işlemlerinden sonra da çağrılır.

## <a name="custom"></a>Özel doğrulama kategorileri
 Menü ve açık gibi standart doğrulama kategorilerinin yanı sıra kendi kategorilerinizi de tanımlayabilirsiniz. Bu kategorileri program kodundan çağırabilirsiniz. Kullanıcı bunları doğrudan çağıramıyor.

 Özel kategoriler için tipik bir kullanım, modelin belirli bir aracın ön koşulları 'nı karşılayıp karşılamadığını test eden bir kategori tanımlamaktır.

 Belirli bir kategoriye bir doğrulama yöntemi eklemek için, bunu şöyle bir öznitelik ile öneki:

```csharp
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]
[ValidationMethod(ValidationCategory.Menu)]
private void TestForCircularLinks(ValidationContext context)
{...}
```

> [!NOTE]
> Bir yöntemi istediğiniz sayıda `[ValidationMethod()]` özniteliğine önek olarak ekleyebilirsiniz. Hem özel hem de standart kategorilere bir yöntem ekleyebilirsiniz.

 Özel bir doğrulama çağırmak için:

```csharp

// Invoke all validation methods in a custom category:
validationController.ValidateCustom
  (store, // or a list of model elements
   "PreconditionsForGeneratePartsList");
```

## <a name="alternatives"></a>Doğrulamanın alternatifleri
 Doğrulama kısıtlamaları hataları raporlar, ancak modeli değiştirmez. Bunun yerine, modelin geçersiz hale gelmesini engellemek isterseniz, diğer teknikleri kullanabilirsiniz.

 Ancak, bu teknikler önerilmez. Kullanıcının geçersiz bir modeli nasıl düzelteceğine karar vermesini sağlamak genellikle daha iyidir.

 **Modeli doğruluğuna geri yüklemek için değişikliği ayarlayın.** Örneğin, Kullanıcı izin verilen en büyük düzeyin üzerinde bir özellik ayarlarsa, özelliği maksimum değere sıfırlayabilirsiniz. Bunu yapmak için bir kural tanımlayın. Daha fazla bilgi için [kuralları yaymak değişiklikleri içinde modeli](../modeling/rules-propagate-changes-within-the-model.md).

 **Geçersiz bir değişiklik denendiğinde işlemi geri alın.** Ayrıca, bu amaçla bir kural tanımlayabilirsiniz, ancak bazı durumlarda **OnValueChanging ()** Özellik işleyicisini geçersiz kılmak veya bir işlemi geri almak için `OnDeleted().` gibi bir yöntemi geçersiz kılmak için `this.Store.TransactionManager.CurrentTransaction.Rollback().` kullanın, bkz. [etki alanı özellik değeri değişiklik işleyicileri](../modeling/domain-property-value-change-handlers.md).

> [!WARNING]
> Kullanıcının değişikliğin ayarlandığını veya geri alındı olduğunu bildiğinden emin olun. Örneğin, `System.Windows.Forms.MessageBox.Show("message").` kullanın

## <a name="see-also"></a>Ayrıca bkz.

- [Program Kodunda Modeli Gezinme ve Güncelleştirme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Değişiklikleri Modelin Dışına Yayan Olay İşleyicileri](../modeling/event-handlers-propagate-changes-outside-the-model.md)
