---
title: Değişiklikleri Modelin İçinde Yayan Kurallar
description: Görselleştirme ve Modelleme SDK'sı (VMSDK) içinde bir öğeden diğerine değişiklik yaymayı öğrenmek için mağaza kuralı oluşturma hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: f6434d4427371a0e2bd39da7c9979b6c29d521e6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637481"
---
# <a name="rules-propagate-changes-within-the-model"></a>Değişiklikleri Modelin İçinde Yayan Kurallar
Görselleştirme ve Modelleme SDK'sı (VMSDK) içinde bir öğeden diğerine değişiklik yayacak bir depo kuralı oluşturabilirsiniz. Depodaki herhangi bir öğede değişiklik olduğunda, kurallar yürütülecek şekilde zamanlanmış olur ve genellikle en dıştaki işlem yürütülür. Öğe ekleme veya silme gibi farklı olay türleri için farklı türlerde kurallar vardır. Belirli öğe, şekil veya diyagram türlerine kurallar iliştirebilirsiniz. Birçok yerleşik özellik kurallarla tanımlanır: örneğin kurallar, model değiştiklerde diyagramın güncelleştirilmiş olmasını sağlar. Kendi kurallarınızı ekleyerek etki alanına özgü dilinizi özelleştirebilirsiniz.

 Mağaza kuralları, özellikle mağaza içindeki değişiklikleri yayın; diğer bir ifadeyle model öğelerinde yapılan değişiklikler, ilişkiler, şekiller veya bağlayıcılar ve bunların etki alanı özellikleri için kullanışlıdır. Kullanıcı Geri Al veya Yeniden Çalıştır komutlarını çağıran kurallar çalıştırlanmaz. Bunun yerine, işlem yöneticisi depo içeriğinin doğru durumuna geri yüklendiklerini emin olur. Değişiklikleri mağazanın dışındaki kaynaklara yayın, Store Events kullanın. Daha fazla bilgi için [bkz. Olay İşleyicileri Değişiklikleri Modelin Dışına Yayma.](../modeling/event-handlers-propagate-changes-outside-the-model.md)

 Örneğin, kullanıcı (veya kodunuz) ExampleDomainClass türünde yeni bir öğe oluşturduğunda, modelin başka bir bölümünde başka bir türün ek bir öğesinin oluşturulacak olduğunu belirtmek istediğinizi varsayalım. Bir AddRule yazıp ExampleDomainClass ile ilişkilendirmek için kullanabilirsiniz. Ek öğeyi oluşturmak için kuralda kod yazardınız.

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
> Bir kuralın kodu yalnızca Mağaza içindeki öğelerin durumunu değiştirsin; diğer bir ifadeyle kural yalnızca model öğelerini, ilişkileri, şekilleri, bağlayıcıları, diyagramları veya özelliklerini değiştirsin. Değişiklikleri mağazanın dışındaki kaynaklara yaymanız gerekirse, Mağaza Olayları'yı tanımlayın. Daha fazla bilgi için [bkz. Olay İşleyicileri Değişiklikleri Modelin Dışına Yayma.](../modeling/event-handlers-propagate-changes-outside-the-model.md)

### <a name="to-define-a-rule"></a>Kural tanımlamak için

1. Kuralı özniteliğiyle ön ekli bir sınıf olarak `RuleOn` tanımlayın. özniteliği, kuralı etki alanı sınıflarından, ilişkilerinize veya diyagram öğelerinize göre ilişkilendirmektedir. Kural bu sınıfın her örneğine uygulanır ve bu da soyut olabilir.

2. Etki alanı modeli sınıfınıza tarafından döndürülen kümeye `GetCustomDomainModelTypes()` ekleyerek kuralı kaydetme.

3. Kural sınıfını soyut Kural sınıflarından biri ile türetin ve yürütme yönteminin kodunu yazın.

   Aşağıdaki bölümlerde bu adımlar daha ayrıntılı olarak açıklanmaktadır.

### <a name="to-define-a-rule-on-a-domain-class"></a>Bir etki alanı sınıfında kural tanımlamak için

- Özel bir kod dosyasında, bir sınıf tanımlayın ve özniteliğiyle ön <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> eke sahip olun:

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- İlk parametrenin konu türü bir etki alanı sınıfı, etki alanı ilişkisi, şekil, bağlayıcı veya diyagram olabilir. Genellikle, etki alanı sınıflarında ve ilişkilerde kurallar uygulanır.

     genellikle `FireTime` `TopLevelCommit` olur. Bu, kuralın yalnızca işlemde tüm birincil değişiklikler yapıldıktan sonra yürütülmelerini sağlar. Alternatifler, değişikliğin hemen ardından kuralı yürüten Satır içidir; ve LocalCommit, kuralı geçerli işlem sonunda yürütür (en dıştaki olabilir). Ayrıca, bir kuralın kuyrukta sıralamasını etkileyecek şekilde önceliğini de ayarlayın, ancak bu, gereken sonucu elde etmek için güvenilir olmayan bir yöntemdir.

- Konu türü olarak soyut bir sınıf belirtsiniz.

- Kural, konu sınıfının tüm örnekleri için geçerlidir.

- için varsayılan değer `FireTime` TimeToFire.TopLevelCommit'tir. Bu, en dıştaki işlem işlendiklerinden kuralın yürütültülürken neden olur. Bunun alternatifi TimeToFire.Inline'dır. Bu, kuralın tetiklenen olaydan kısa süre sonra yürütüllecek olmasına neden olur.

### <a name="to-register-the-rule"></a>Kuralı kaydetmek için

- Etki alanı modelinize tarafından döndürülen türler listesine kural `GetCustomDomainModelTypes` sınıfınızı ekleyin:

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

- Etki alanı modeli sınıfı adının ne olduğundan emin değilsanız **Dsl\GeneratedCode\DomainModel.cs** dosyasının içine bakın

- Bu kodu DSL projenizin özel bir kod dosyasına yazın.

### <a name="to-write-the-code-of-the-rule"></a>Kuralın kodunu yazmak için

- Kural sınıfını aşağıdaki temel sınıflardan biri ile türetin:

  | Temel sınıf | Tetikleyici |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Bir öğe, bağlantı veya şekil eklenir.<br /><br /> Yeni öğelere ek olarak yeni ilişkileri algılamak için bunu kullanın. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Bir etki alanı özellik değeri değiştirilir. yöntem bağımsız değişkeni eski ve yeni değerleri sağlar.<br /><br /> Şekiller için, şekil taşınırsa yerleşik özellik `AbsoluteBounds` değiştirlendiğinde bu kural tetiklenir.<br /><br /> Çoğu durumda, geçersiz kılmak veya özellik `OnValueChanged` işleyicisinde `OnValueChanging` yapmak daha kullanışlıdır. Bu yöntemler değişiklik öncesinde ve sonrasında hemen çağrılır. Buna karşılık kural genellikle işlem sonunda çalışır. Daha fazla bilgi için [bkz. Etki Alanı Özellik Değeri Değişikliği İşleyicileri.](../modeling/domain-property-value-change-handlers.md) **Not:**  Bu kural, bir bağlantı oluşturulduğunda veya silindiğinde tetiklanmaz. Bunun yerine, etki `AddRule` alanı ilişkisi için bir ve `DeleteRule` yazın. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Bir öğe veya bağlantı silinecekken tetiklenir. ModelElement.IsDeleting özelliği, işlem sonuna kadar true olur. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Bir öğe veya bağlantı silindiğinde gerçekleştirilir. Kural, DeletingRules dahil olmak üzere diğer tüm kurallar yürütülürken yürütülür. ModelElement.IsDeleting false, ModelElement.IsDeleted ise true. Sonraki bir Geri Alma işlemi için izin vermek için öğe bellekten gerçekten kaldırılamaz, ancak Store.ElementDirectory'den kaldırılır. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Bir öğe bir mağaza bölümden diğerine taşınır.<br /><br /> (Bunun şeklin grafik konumuyla ilgili olmadığını fark etmek.) |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Bu kural yalnızca etki alanı ilişkileri için geçerlidir. Bir bağlantının herhangi bir ucunda açıkça bir model öğesi atarsanız tetiklenir. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Bir öğeye veya öğeden bağlantıların sırası bir bağlantıda MoveBefore veya MoveToIndex yöntemleri kullanılarak değiştirlendiğinde tetiklenir. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Bir işlem oluşturulduğunda yürütülür. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | İşlem işlendikleri zaman yürütülür. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | İşlem geri alınca yürütülür. |

- Her sınıfın geçersiz kılarak bir yöntemi vardır. Bulmak `override` için sınıfınıza yazın. Bu yöntemin parametresi, değiştirilen öğeyi tanımlar.

  Kurallar hakkında aşağıdaki noktalara dikkatin:

1. Bir işlemde yapılan değişiklikler kümesi birçok kuralı tetikler. Genellikle, en dıştaki işlem işlendikleri zaman kurallar yürütülür. Bunlar belirtilmemiş bir sırada yürütülür.

2. Kural her zaman bir işlem içinde yürütülür. Bu nedenle, değişiklik yapmak için yeni bir işlem oluşturmanıza gerek yok.

3. Kurallar, bir işlem geri alınırken veya Geri Al veya Yinele işlemleri gerçekleştiriliyorsa yürütülmez. Bu işlemler, Mağaza'nın tüm içeriğini önceki durumuna sıfırlar. Bu nedenle, kuralınız Store dışındaki herhangi bir şeyin durumunu değiştirirse, Store içeriğiyle zaman uyumlu olmaz. Mağaza dışındaki durumu güncelleştirmek için Olaylar'ın kullanımı daha iyidir. Daha fazla bilgi için [bkz. Olay İşleyicileri Değişiklikleri Modelin Dışına Yayma.](../modeling/event-handlers-propagate-changes-outside-the-model.md)

4. Bir model dosyadan yüklendiğinde bazı kurallar yürütülür. Yükleme veya kaydetmenin devam edip olmadığını belirlemek için `store.TransactionManager.CurrentTransaction.IsSerializing` kullanın.

5. Kuralınız daha fazla kural tetikleyicisi oluşturursa, bunlar tetikleme listesinin sonuna eklenir ve işlem tamamlandıktan önce yürütülür. DeletedRules diğer tüm kurallardan sonra yürütülür. Bir kural bir işlemde birçok kez, her değişiklik için bir kez çalışmasına neden olabilir.

6. Kurallara ve kurallardan bilgi geçmek için, bilgileri içinde `TransactionContext` depolarsiniz. Bu yalnızca işlem sırasında bakımı yapılan bir sözlüktir. İşlem sona erdiğinde atılması gerekir. Her kuralda olay bağımsız değişkenleri buna erişim sağlar. Kuralların öngörülebilir bir sırada yürütül olmadığını unutmayın.

7. Diğer alternatifleri göz önünde bulundurarak kuralları kullanın. Örneğin, bir değer değişirken bir özelliği güncelleştirmek için hesaplanmış özellik kullanmayı göz önünde bulundurabilirsiniz. Şeklin boyutunu veya konumunu sınırlamak için `BoundsRule` kullanın. Özellik değerindeki bir değişikliği yanıtlamak için özelliğine bir `OnValueChanged` işleyici ekleyin. Daha fazla bilgi için [bkz. Değişiklikleri Yanıt verme ve Yayma.](../modeling/responding-to-and-propagating-changes.md)

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir etki alanı ilişkisi örneği 2 öğeye bağlantı vermek için bir özelliği günceller. Kural yalnızca kullanıcı bir diyagramda bağlantı oluşturduğunda değil, aynı zamanda program kodu bir bağlantı oluşturduğunda da tetiklenir.

 Bu örneği test etmek için Task Flow çözüm şablonunu kullanarak bir DSL oluşturun ve aşağıdaki kodu Dsl projesine bir dosyaya girin. Çözümü derleme ve çalıştırma ve Hata ayıklama projesinde Örnek dosyasını açın. Açıklama şekli ile akış öğesi arasında Açıklama Bağlantısı çizme. Açıklamanın metni, bağlantılı olduğu en son öğeyle ilgili rapor olarak değişir.

 Uygulamada, genellikle her AddRule için bir DeleteRule yazardınız.

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