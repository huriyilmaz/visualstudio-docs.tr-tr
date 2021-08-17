---
title: Etki Alanı Özellik Değeri Değişiklik İşleyicileri
description: Visual Studio etki alanına özgü bir dilde kullanılabilen etki alanı özellik değeri değişiklik işleyicileri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: bfd2a8d12d61f795afb07dd250fef312b1720b627ac2888bc390a73a071985c4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370755"
---
# <a name="domain-property-value-change-handlers"></a>Etki alanı özellik değeri değişiklik işleyicileri

etki alanına özgü bir dilde Visual Studio, bir etki alanı özelliğinin değeri değiştiğinde, `OnValueChanging()` ve `OnValueChanged()` yöntemleri etki alanı özelliği işleyicisinde çağrılır. Değişikliğe yanıt vermek için bu yöntemleri geçersiz kılabilirsiniz.

## <a name="override-the-property-handler-methods"></a>Özellik Işleyici yöntemlerini geçersiz kıl

Etki alanına özgü dilinizin her etki alanı özelliği, üst etki alanı sınıfının içinde iç içe yerleştirilmiş bir sınıf tarafından işlenir. Adı *PropertyName* propertyhandler biçimini izler. Bu özellik işleyicisi sınıfını **Dsl\generated Code\DomainClasses.cs** dosyasında inceleyebilirsiniz. Sınıfında, `OnValueChanging()` değer değiştirilmeden hemen önce çağrılır ve `OnValueChanged()` değer değiştirildikten hemen sonra çağrılır.

Örneğin, adında bir `Comment` dize alanı özelliği ve adlı bir tamsayı özelliği olan adlı bir etki alanı sınıfınız olduğunu varsayalım `Text` `TextLengthCount` . `TextLengthCount`Her zaman dize uzunluğunu içermesine neden olmak için `Text` aşağıdaki kodu DSL projesindeki ayrı bir dosyaya yazabilirsiniz:

```csharp
// Domain Class "Comment":
public partial class Comment
{
  // Domain Property "Text":
  partial class TextPropertyHandler
  {
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)
    {
      base.OnValueChanging(element, oldValue, newValue);

      // To update values outside the Store, write code here.

      // Let the transaction manager handle undo:
      Store store = element.Store;
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;

      // Update values in the Store:
      this.TextLengthCount = newValue.Length;
    }
  }
}
```

Özellik işleyicileri hakkında aşağıdaki noktalara dikkat edin:

- Özellik işleyici yöntemleri, Kullanıcı bir etki alanı özelliğinde değişiklik yaptığında ve program kodu özelliğe farklı bir değer atarken, her ikisi de çağrılır.

- Yöntemler yalnızca değeri aslında değiştiğinde çağrılır. Program kodu geçerli değere eşit bir değer atadığında işleyici çağrılmaz.

- Hesaplanan ve özel depolama alanı özelliklerinde OnValueChanged ve OnValueChanging yöntemleri yok.

- Yeni değeri değiştirmek için bir değişiklik işleyicisi kullanamazsınız. Bunu yapmak istiyorsanız, örneğin değeri belirli bir aralığa kısıtlamak için bir tanımlayın `ChangeRule` .

- Bir ilişkinin rolünü temsil eden bir özelliğe değişiklik işleyicisi ekleyemezsiniz. Bunun yerine, `AddRule` ilişki sınıfında bir ve bir tanımlayın `DeleteRule` . Bu kurallar, bağlantılar oluşturulduğunda veya değiştirildiğinde tetiklenir. Daha fazla bilgi için bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Mağaza içindeki ve çıkan değişiklikler

Özellik işleyici yöntemleri değişikliği Başlatan işlemin içinde çağırılır. Bu nedenle, yeni bir işlem açmadan mağazada daha fazla değişiklik yapabilirsiniz. Değişiklikleriniz ek işleyici çağrılarına neden olabilirler.

Bir işlem geri alındığında, redone veya geri alındığında mağazada değişiklik yapmamalıdır, diğer bir deyişle, model öğelerinde, ilişkilerde, şekillerde, bağlayıcılar diyagramlarında veya özelliklerinde değişiklik yapmanız gerekmez.

Ayrıca, model dosyadan yüklenirken genellikle değerleri güncelleştiremezsiniz.

Bu nedenle modelde yapılan değişiklikler şöyle bir test tarafından korunmalıdır:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Buna karşılık, özellik işleyiciniz mağaza dışındaki değişiklikleri (örneğin, bir dosya, veritabanı veya depolama olmayan değişkenler) yaysa, bu değişiklikleri her zaman, Kullanıcı geri alma veya yineleme istediğinde dış değerlerin güncelleştirilmesini sağlayacak şekilde yapmalısınız.

### <a name="cancel-a-change"></a>Değişikliği iptal et

Bir değişikliği engellemek isterseniz, geçerli işlemi geri alabilirsiniz. Örneğin, bir özelliğin belirli bir Aralık içinde kalmasını sağlamak isteyebilirsiniz.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Alternatif Teknik: hesaplanmış Özellikler

Önceki örnekte, bir etki alanı özelliğinden diğerine değer yaymak için OnValueChanged () nasıl kullanılabileceği gösterilmektedir. Her özelliğin kendi saklı değeri vardır.

Bunun yerine, türetilmiş özelliği hesaplanmış bir özellik olarak tanımlamayı düşünebilirsiniz. Bu durumda, özelliği kendi kendine depolamayı içermez ve değeri her gerektiğinde değerlendirilir. daha fazla bilgi için bkz. [hesaplanan ve özel Depolama özellikleri](../modeling/calculated-and-custom-storage-properties.md).

Önceki örnek yerine, ' nin **tür** alanını `TextLengthCount` DSL tanımında **hesaplanacak** şekilde ayarlayabilirsiniz. Bu etki alanı özelliği için kendi **Get** yönteminizi sağlarsınız. **Get** yöntemi, dizenin geçerli uzunluğunu döndürür `Text` .

Ancak, hesaplanan özelliklerin potansiyel bir dezavantajı, ifadenin değeri her kullanıldığında, bir performans sorunu oluşturabilecek şekilde değerlendirilmesidir. Ayrıca, bir hesaplanmış özellikte OnValueChanging () ve OnValueChanged () yoktur.

### <a name="alternative-technique-change-rules"></a>Alternatif Teknik: kuralları değiştirme

Bir ChangeRule tanımlarsanız, bu, özelliğin değerinin değiştiği bir işlemin sonunda yürütülür.  Daha fazla bilgi için bkz. [model Içindeki değişiklikleri yayma kuralları](../modeling/rules-propagate-changes-within-the-model.md).

Tek bir işlemde birkaç değişiklik yapılırsa, her tamamlandıklarında ChangeRule yürütülür. Bunun aksine OnValue... bazı değişiklikler gerçekleştirilmeyen Yöntemler yürütülür. Elde etmek istediğinize bağlı olarak, bu bir ChangeRule daha uygun hale gelebilir.

Ayrıca, özelliğin yeni değerini belirli bir Aralık içinde tutmak üzere ayarlamak için bir ChangeRule de kullanabilirsiniz.

> [!WARNING]
> Bir kural mağaza içeriklerde değişiklikler yapıyorsa, diğer kurallar ve özellik işleyicileri tetiklenebilir. Bir kural onu tetikleyen özelliği değiştirirse, yeniden çağrılır. Kural tanımlarınızın sonsuz tetikleme sonucu olmadığından emin olmanız gerekir.

```csharp
using Microsoft.VisualStudio.Modeling;
...
// Change rule on the domain class Comment:
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]
class MyCommentTrimRule : ChangeRule
{
  public override void
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)
  {
    base.ElementPropertyChanged(e);
    Comment comment = e.ModelElement as Comment;

    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))
      comment.Text = comment.Text.Trim();
    // If changed, rule will trigger again.
  }
}

// Register the rule:
public partial class MyDomainModel
{
 protected override Type[] GetCustomDomainModelTypes()
 { return new Type[] { typeof(MyCommentTrimRule) };
 }
}
```

## <a name="example"></a>Örnek

### <a name="description"></a>Açıklama

Aşağıdaki örnek, bir etki alanı özelliğinin özellik işleyicisini geçersiz kılar ve etki alanı sınıfı için bir özellik değiştiğinde kullanıcıya bildirir `ExampleElement` .

### <a name="code"></a>Kod

```csharp
using DslModeling = global::Microsoft.VisualStudio.Modeling;
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;

namespace msft.FieldChangeSample
{
  public partial class ExampleElement
  {
    internal sealed partial class NamePropertyHandler
    {
      protected override void OnValueChanged(ExampleElement element,
         string oldValue, string newValue)
      {
        if (!this.Store.InUndoRedoOrRollback)
        {
           // make in-store changes here...
        }
        // This part is called even in undo:
        System.Windows.Forms.MessageBox.Show("Value Has Changed");
        base.OnValueChanged(element, oldValue, newValue);
      }
    }
  }
}
```
