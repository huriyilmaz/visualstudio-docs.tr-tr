---
title: Etki Alanı Özellik Değeri Değişiklik İşleyicileri
description: Etki alanına özgü bir dilde kullanılmaktadır etki alanı özellik değeri Visual Studio işleyicileri hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1c6cdb027bafdf4d1fe7689d7dd30d697b539370
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389003"
---
# <a name="domain-property-value-change-handlers"></a>Etki alanı özellik değeri değişiklik işleyicileri

Etki Visual Studio etki alanına özgü bir dilde, bir etki alanı özelliğinin değeri değişirse, ve yöntemleri etki alanı özellik `OnValueChanging()` `OnValueChanged()` işleyicisinde çağrılır. Değişikliği yanıtlamak için bu yöntemleri geçersiz kılebilirsiniz.

## <a name="override-the-property-handler-methods"></a>Özellik İşleyicisi yöntemlerini geçersiz kılma

Etki alanına özgü dilinizin her etki alanı özelliği, üst etki alanı sınıfının içinde iç içe geçmiş bir sınıf tarafından ele alındı. Adı *PropertyName* PropertyHandler biçimindedir. **Dsl\Generated Code\DomainClasses.cs dosyasında bu özellik işleyicisi sınıfını inceebilirsiniz.** sınıfında, değer `OnValueChanging()` daha önce hemen çağrılır ve değer `OnValueChanged()` değiştikten hemen sonra çağrılır.

Örneğin, adlı bir dize etki alanı özelliğine ve adlı bir tamsayı özelliğine sahip `Comment` adlı bir etki alanı `Text` sınıfına sahip olduğunu `TextLengthCount` varsayalım. Dizenin `TextLengthCount` uzunluğunun her zaman içermesi için aşağıdaki kodu Dsl `Text` projesinde ayrı bir dosyaya yazabilirsiniz:

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

Özellik işleyicileri hakkında aşağıdaki noktalara dikkatin:

- Özellik işleyicisi yöntemleri, kullanıcı bir etki alanı özelliğinde değişiklik yapar ve program kodu özelliğine farklı bir değer atarken çağrılır.

- Yöntemler yalnızca değer gerçekten değişirken çağrılır. Program kodu geçerli değere eşit bir değer atarsa işleyici çağrılmaz.

- Hesaplanan ve özel depolama etki alanı özelliklerinde OnValueChanged ve OnValueChanging yöntemleri yok.

- Yeni değeri değiştirmek için bir değişiklik işleyicisi kullanılamaz. Bunu yapmak için, örneğin değeri belirli bir aralıkla kısıtlamak için bir `ChangeRule` tanımlayın.

- Bir ilişkinin rolünü temsil eden bir özellik için değişiklik işleyicisi ek olamaz. Bunun yerine, ilişki `AddRule` sınıfında bir `DeleteRule` ve tanımlayın. Bağlantılar oluşturulduğunda veya değiştirlendiğinde bu kurallar tetiklenir. Daha fazla bilgi için [bkz. Kurallar Modelde Değişiklikleri Yayma.](../modeling/rules-propagate-changes-within-the-model.md)

### <a name="changes-in-and-out-of-the-store"></a>Mağaza içinde ve dışında yapılan değişiklikler

Özellik işleyicisi yöntemleri, değişikliği başlatan işlem içinde çağrılır. Bu nedenle, yeni bir işlem açmadan mağazada daha fazla değişiklik yapabilirsiniz. Değişiklikleriniz ek işleyici çağrıları ile sonuçlansa da olabilir.

Bir işlem geri alınırken, yeniden kullanılırken veya geri alınırken, mağazada, yani model öğelerinde, ilişkilerde, şekillerde, bağlayıcı diyagramlarında veya bunların özelliklerinde değişiklik yapmamanız gerekir.

Ayrıca, model dosyadan yüklenirken genellikle değerleri güncelleştirmezsiniz.

Bu nedenle model değişiklikleri aşağıdaki gibi bir test tarafından koruma altındadır:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Buna karşılık, özellik işleyiciniz değişiklikleri depo dışında bir dosyaya, veritabanına veya depo dışı değişkenlere yayırsa, kullanıcı geri almayı veya yeniden almayı çağıran dış değerlerin güncelleştirilsin diye bu değişiklikleri her zaman yapmanız gerekir.

### <a name="cancel-a-change"></a>Değişikliği iptal etme

Bir değişikliği önlemek için geçerli işlemi geri almak gerekir. Örneğin, bir özelliğin belirli bir aralıkta kalmasını sağlamak istiyor olabilir.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Alternatif teknik: Hesaplanmış Özellikler

Önceki örnekte OnValueChanged() işlevinin değerleri bir etki alanı özelliğinden diğerine yayma için nasıl kullanılası açıklandı. Her özelliğin kendi depolanmış değeri vardır.

Bunun yerine türetilmiş özelliği Hesaplanmış özellik olarak tanımlamayı göz önünde bulundurabilirsiniz. Bu durumda özelliğin kendi depolama alanı yoktur ve işlevi tanımlamak her değer gerektiğinde değerlendirilir. Daha fazla bilgi için [bkz. Hesaplanan ve Özel Depolama Özellikleri.](../modeling/calculated-and-custom-storage-properties.md)

Önceki örnek yerine, Tür alanını  DSL `TextLengthCount` Tanımında  Hesaplanmış olarak ayarlayın. Bu etki alanı özelliği için **kendi Get** yönteminizi sağlar. **Get** yöntemi, dizenin geçerli uzunluğunu `Text` döndürür.

Ancak, hesaplanmış özelliklerin olası bir dezavantajı, ifadenin değer her kullanılırken değerlendirilmesidir ve bu da bir performans sorununa neden olabilir. Ayrıca, hesaplanan bir özellikte OnValueChanging() ve OnValueChanged() yoktur.

### <a name="alternative-technique-change-rules"></a>Alternatif teknik: Kuralları Değiştirme

Bir ChangeRule tanımlarsanız, bir özelliğin değerinin değiştir olduğu bir işlem sonunda yürütülür.  Daha fazla bilgi için [bkz. Kurallar Modelde Değişiklikleri Yayma.](../modeling/rules-propagate-changes-within-the-model.md)

Tek bir işlemde birkaç değişiklik yapılırsa, hepsi tamamlandığında ChangeRule yürütülür. Buna karşılık, OnValue... yöntemleri, bazı değişiklikler gerçekleştirilene kadar yürütülür. Ne elde etmek istediğinize bağlı olarak, bu bir ChangeRule'a daha uygun hale gelir.

Özelliğin yeni değerini belirli bir aralıkta tutmak üzere ayarlamak için bir ChangeRule da kullanabilirsiniz.

> [!WARNING]
> Bir kural depo içeriğinde değişiklik yaparsa, diğer kurallar ve özellik işleyicileri tetiklenir. Bir kural, onu tetikleyen özelliği değiştirirse, yeniden çağrılır. Kural tanımlarınızı sonsuz tetiklemeye neden olmaz emin olun.

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

Aşağıdaki örnek, bir etki alanı özelliğinin özellik işleyicisini geçersiz kılar ve etki alanı sınıfı için bir özellik değiştir `ExampleElement` olduğunda kullanıcıya bilgi sağlar.

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
