---
title: Değişiklikleri Modelin İçinde Yayan Kurallar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74d64b4fe0c0aa5293e11daad13f632c4a487736
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747413"
---
# <a name="rules-propagate-changes-within-the-model"></a>Değişiklikleri Modelin İçinde Yayan Kurallar
Bir değişikliği bir öğeden diğerine, görselleştirme ve modelleme SDK 'sını (VMSDK) yaymak için bir depolama kuralı oluşturabilirsiniz. Depodaki herhangi bir öğe için bir değişiklik olduğunda, genellikle en dıştaki işlem işlendiği zaman, kurallar yürütülmek üzere zamanlanır. Farklı türlerde olaylar için bir öğe ekleme veya silme gibi farklı türde kurallar vardır. Belirli öğe, şekil veya diyagram türlerine kurallar ekleyebilirsiniz. Birçok yerleşik özellik kurallar tarafından tanımlanır: Örneğin, kurallar model değiştiğinde bir diyagramın güncelleştirildiğinden emin olur. Kendi kurallarınızı ekleyerek, etki alanına özgü dilinizi özelleştirebilirsiniz.

 Mağaza kuralları özellikle mağaza içindeki değişiklikleri yayılırken, model öğelerinde, ilişkilerde, şekillerde veya bağlayıcılarda ve bunların etki alanı özelliklerinde yapılan değişiklikler için kullanışlıdır. Kullanıcı geri al veya Yinele komutlarını çağırdığında kurallar çalıştırılmaz. Bunun yerine, işlem Yöneticisi depo içeriklerinin doğru duruma geri yüklenmesini sağlar. Değişiklikleri mağaza dışındaki kaynaklara yaymak istiyorsanız mağaza olayları ' nı kullanın. Daha fazla bilgi için bkz. [olay Işleyicileri değişiklikleri model dışında yayma](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Örneğin, Kullanıcı (veya kodunuz) ExampleDomainClass türünde yeni bir öğe oluşturduğunda, modelin başka bir bölümünde başka bir türün ek bir öğesinin oluşturulduğunu belirtmek istediğinizi varsayalım. AddRule yazıp ExampleDomainClass ile ilişkilendirebilirsiniz. Ek öğeyi oluşturmak için kurala kod yazarsınız.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;

namespace ExampleNamespace
{
 // Attribute associates the rule with a domain class:
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class MyAddRule : AddRule
 {
  // Override the abstract method:
  public override void ElementAdded(ElementAddedEventArgs e)
  {
    base.ElementAdded(e);
    ExampleDomainClass element = e.ModelElement;
    Store store = element.Store;
    // Ignore this call if we're currently loading a model:
    if (store.TransactionManager.CurrentTransaction.IsSerializing)
       return;

    // Code here propagates change as required - for example:
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);
      echo.Name = element.Name;
      echo.Parent = element.Parent;
    }
  }
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
   protected override Type[] GetCustomDomainModelTypes()
   {
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
     types.Add(typeof(MyAddRule));
     // If you add more rules, list them here.
     return types.ToArray();
   }
 }
}
```

> [!NOTE]
> Bir kuralın kodu yalnızca depodaki öğelerin durumunu değiştirmeli; diğer bir deyişle, kuralın yalnızca model öğelerini, ilişkileri, şekilleri, bağlayıcıları, diyagramları veya özelliklerini değiştirmesi gerekir. Değişiklikleri mağaza dışındaki kaynaklara yaymak istiyorsanız mağaza olaylarını tanımlayın. Daha fazla bilgi için bkz. [olay Işleyicileri değişiklikleri model dışında yayma](../modeling/event-handlers-propagate-changes-outside-the-model.md).

### <a name="to-define-a-rule"></a>Bir kural tanımlamak için

1. Kuralı, `RuleOn` özniteliğiyle önekli bir sınıf olarak tanımlayın. Özniteliği, kuralı etki alanı sınıflarınız, ilişkilerinizde veya diyagram öğelerinden biriyle ilişkilendirir. Kural bu sınıfın soyut olabilecek her örneğine uygulanır.

2. Kuralı, etki alanı modeli sınıfınıza `GetCustomDomainModelTypes()` tarafından döndürülen kümesine ekleyerek kaydettirin.

3. Özet kural sınıflarından birindeki kural sınıfını türetirsiniz ve yürütme yönteminin kodunu yazın.

   Aşağıdaki bölümlerde bu adımlar daha ayrıntılı olarak açıklanır.

### <a name="to-define-a-rule-on-a-domain-class"></a>Bir etki alanı sınıfında bir kural tanımlamak için

- Özel bir kod dosyasında, bir sınıf tanımlayın ve <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> özniteliğiyle öneki yapın:

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- İlk parametresindeki konu türü bir etki alanı sınıfı, etki alanı ilişkisi, şekil, bağlayıcı veya diyagram olabilir. Genellikle, kuralları etki alanı sınıflarına ve ilişkilerine uygularsınız.

     @No__t_0 genellikle `TopLevelCommit`. Bu, kuralın yalnızca işlemin tüm birincil değişiklikleri yapıldıktan sonra yürütülmesini sağlar. Alternatif olarak, kuralı değişiklikten hemen sonra yürüten satır Içi olur; ve geçerli işlemin sonunda kuralı yürüten Localcommıt (en dıştaki olmayabilir). Ayrıca, kuyruktaki sıralamayı etkilemek için bir kuralın önceliğini ayarlayabilirsiniz, ancak bu, ihtiyacınız olan sonucu elde etmek için güvenilir bir yöntemdir.

- Konu türü olarak bir soyut sınıf belirtebilirsiniz.

- Kural, konu sınıfının tüm örneklerine uygulanır.

- @No__t_0 için varsayılan değer TimeToFire. TopLevelCommit ' dir. Bu, en dıştaki işlem yürütüldüğü zaman kuralın yürütülmesine neden olur. Bir alternatif TimeToFire. Inline. Bu, kuralın tetikleme olayından kısa bir süre sonra yürütülmesini sağlar.

### <a name="to-register-the-rule"></a>Kuralı kaydetmek için

- Kural sınıfınızı, etki alanı modelinizdeki `GetCustomDomainModelTypes` tarafından döndürülen türler listesine ekleyin:

    ```csharp
    public partial class ExampleDomainModel
     {
       protected override Type[] GetCustomDomainModelTypes()
       {
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
         types.Add(typeof(MyAddRule));
         // If you add more rules, list them here.
         return types.ToArray();
       }
     }

    ```

- Etki alanı modeli sınıfınızın adından emin değilseniz, dosyanın içine bakın **Dsl\GeneratedCode\DomainModel.cs**

- Bu kodu DSL projenizdeki özel bir kod dosyasına yazın.

### <a name="to-write-the-code-of-the-rule"></a>Kural kodunu yazmak için

- Kural sınıfını aşağıdaki temel sınıflardan birinden türet:

  | Temel sınıf | Tetikleyicinin |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Öğe, bağlantı veya şekil eklendi.<br /><br /> Yeni öğelere ek olarak yeni ilişkileri algılamak için bunu kullanın. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Bir etki alanı özellik değeri değiştirildi. Method bağımsız değişkeni eski ve yeni değerleri sağlar.<br /><br /> Şekiller için bu kural, şekil taşındığında, yerleşik `AbsoluteBounds` özelliği değiştiğinde tetiklenir.<br /><br /> Çoğu durumda, özellik işleyicisinde `OnValueChanged` veya `OnValueChanging` geçersiz kılmak daha uygundur. Bu yöntemler değişiklikten hemen önce ve sonra çağrılır. Buna karşılık, kural genellikle işlemin sonunda çalışır. Daha fazla bilgi için bkz. [etki alanı özellik değeri değişiklik işleyicileri](../modeling/domain-property-value-change-handlers.md). **Note:**  Bu kural bir bağlantı oluşturulduğunda veya silindiğinde tetiklenmez. Bunun yerine, etki alanı ilişkisi için bir `AddRule` ve `DeleteRule` yazın. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Bir öğe veya bağlantı silinmek üzere olduğunda tetiklenir. ModelElement. ıssilmenin özelliği işlemin sonuna kadar doğru. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Bir öğe veya bağlantı silindiğinde yapılır. Kural, DeletingRules dahil tüm diğer kuralların çalıştırıldıktan sonra yürütülür. ModelElement. IsDeleted yanlış ve ModelElement. IsDeleted doğru. Sonraki geri almaya izin vermek için, öğe bellekten kaldırılmamıştır, ancak Store. ElementDirectory 'den kaldırılır. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Bir öğe bir depolama bölümünden diğerine taşınır.<br /><br /> (Bunun şeklin grafik konumuyla ilgili olmadığına dikkat edin.) |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Bu kural yalnızca etki alanı ilişkileri için geçerlidir. Bir bağlantı sonuna açıkça bir model öğesi atarsanız tetiklenir. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Bir bağlantı üzerinde MoveBefore veya MoveToIndex metotları kullanılarak bir öğeden veya bir öğeden bağlantı sıralaması değiştirildiğinde tetiklenir. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Bir işlem oluşturulduğunda yürütülür. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | İşlem teslim etmek üzere olduğunda yürütülür. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | İşlem geri alınana kadar yürütüldüğünde yürütülür. |

- Her sınıfın geçersiz kılabileceğiniz bir yöntemi vardır. Bunu öğrenmek için sınıfınıza `override` yazın. Bu yöntemin parametresi, değiştirilmekte olan öğeyi tanımlar.

  Kurallarla ilgili aşağıdaki noktalara dikkat edin:

1. Bir işlemdeki değişiklikler kümesi birçok kuralı tetikleyebilirler. Genellikle, en dıştaki işlem işlendiği zaman kurallar yürütülür. Belirtilmemiş bir sırada yürütülürler.

2. Bir kural, her zaman bir işlem içinde yürütülür. Bu nedenle, değişiklik yapmak için yeni bir işlem oluşturmanız gerekmez.

3. Bir işlem geri alındığında veya geri alma veya yineleme işlemleri gerçekleştirildiğinde kurallar yürütülmez. Bu işlemler deponun tüm içeriğini önceki durumuna sıfırlar. Bu nedenle, kuralınız mağaza dışındaki herhangi bir şeyin durumunu değiştirirse mağaza içeriğiyle eşitlenmiş halde kalabilir. Durumu mağaza dışında güncelleştirmek için olayları kullanmak daha iyidir. Daha fazla bilgi için bkz. [olay Işleyicileri değişiklikleri model dışında yayma](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Bazı kurallar, bir model dosyadan yüklendiğinde yürütülür. Yükleme veya kaydetme işleminin devam edilip edilmeyeceğini öğrenmek için `store.TransactionManager.CurrentTransaction.IsSerializing` kullanın.

5. Kuralınızın kodu daha fazla kural tetikleyicisi oluşturursa, bu bunlar tetikleme listesinin sonuna eklenir ve işlem tamamlanmadan önce yürütülür. Silinmeyen kurallar tüm diğer kurallardan sonra yürütülür. Bir kural, her değişiklik için bir kez olmak üzere bir işlem içinde birçok kez çalıştırılabilir.

6. Kurallara ve kurallardan bilgi geçirmek için `TransactionContext` bilgileri depolayabilmeniz gerekir. Bu yalnızca işlem sırasında tutulan bir sözlüktür. İşlem sona erdiğinde atılmış olur. Her kuraldaki olay bağımsız değişkenleri buna erişim sağlar. Kuralların öngörülebilir bir sırada yürütülebileceğini unutmayın.

7. Diğer alternatifleri göz önünde bulundurarak kuralları kullanın. Örneğin, bir değer değiştiğinde bir özelliği güncellemek istiyorsanız, hesaplanmış bir özellik kullanmayı düşünün. Bir şeklin boyutunu veya konumunu kısıtlamak istiyorsanız, `BoundsRule` kullanın. Özellik değerindeki bir değişikliğe yanıt vermek istiyorsanız, özelliğine bir `OnValueChanged` işleyicisi ekleyin. Daha fazla bilgi için bkz. [değişiklikleri yanıtlama ve yayma](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Örnek
 Aşağıdaki örnek, iki öğeyi bağlamak için bir etki alanı ilişkisi örneği oluşturulduğunda bir özelliği günceller. Kural, yalnızca Kullanıcı diyagramda bir bağlantı oluşturduğunda değil, aynı zamanda program kodu bir bağlantı oluşturduğunda tetiklenecektir.

 Bu örneği test etmek için, görev akışı çözüm şablonunu kullanarak bir DSL oluşturun ve DSL projesindeki bir dosyaya aşağıdaki kodu ekleyin. Çözümü derleyin ve çalıştırın ve hata ayıklama projesinde örnek dosyayı açın. Açıklama şekli ve flow öğesi arasında bir açıklama bağlantısı çizin. Açıklamadaki metin, üzerine bağladığınız en son öğe üzerinde rapor olarak değişir.

 Uygulamada, genellikle her AddRule için bir DeleteRule yazarsınız.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.TaskRuleExample
{

  [RuleOn(typeof(CommentReferencesSubjects))]
  public class RoleRule : AddRule
  {

    public override void ElementAdded(ElementAddedEventArgs e)
    {
      base.ElementAdded(e);
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;
      Comment comment = link.Comment;
      FlowElement subject = link.Subject;
      Transaction current = link.Store.TransactionManager.CurrentTransaction;
      // Don't want to run when we're just loading from file:
      if (current.IsSerializing) return;
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";
    }

  }

  public partial class TaskRuleExampleDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(RoleRule));
      return types.ToArray();
    }
  }

}
```

## <a name="see-also"></a>Ayrıca bkz.

- [Değişiklikleri Modelin Dışına Yayan Olay İşleyicileri](../modeling/event-handlers-propagate-changes-outside-the-model.md)