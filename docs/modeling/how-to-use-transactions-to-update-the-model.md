---
title: 'Nasıl yapılır: Modeli Güncelleştirmek için İşlemleri Kullanma'
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a08ea67477f42008c35b6f141351beaeee03d27b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661143"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Nasıl yapılır: Modeli Güncelleştirmek için İşlemleri Kullanma
İşlemler, depoda yapılan değişikliklerin grup olarak değerlendirildiğinden emin olmanızı sağlar. Gruplanmış değişiklikler, tek bir birim olarak uygulanabilir veya geri alınabilir.

 Program kodunuz, Visual Studio görselleştirme ve modelleme SDK 'daki depodaki herhangi bir öğeyi değiştirdiğinde, eklediğinde ya da sildiği zaman bir işlemin içinde bunu yapması gerekir. Değişiklik gerçekleştiğinde depolarla ilişkilendirilmiş <xref:Microsoft.VisualStudio.Modeling.Transaction> etkin bir örneği olmalıdır. Bu, tüm model öğeleri, ilişkiler, şekiller, diyagramlar ve özellikleri için geçerlidir.

 İşlem mekanizması tutarsız durumlardan kaçınmanıza yardımcı olur. Bir işlem sırasında hata oluşursa, tüm değişiklikler geri alınır. Kullanıcı bir geri alma komutu gerçekleştiriyorsa, her son işlem tek bir adım olarak değerlendirilir. Kullanıcılar, ayrı işlemlere açıkça yerleştirmediğiniz takdirde son bir değişikliğin parçalarını geri alamaz.

## <a name="opening-a-transaction"></a>İşlem açma
 Bir işlemi yönetmenin en kullanışlı yöntemi, `try...catch` bildiriminde yer aldığı `using` deyimidir:

```csharp
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Değişiklikler sırasında son `Commit()` engelleyen bir özel durum oluşursa, mağaza önceki durumuna sıfırlanır. Bu, hataların modeli tutarsız bir durumda bırakmadığından emin olmanıza yardımcı olur.

 Bir işlem içinde istediğiniz sayıda değişiklik yapabilirsiniz. Yeni işlemleri etkin bir işlem içinde açabilirsiniz. İç içe geçmiş işlemler, kapsayan işlem bitmeden önce yürütmeli veya geri alınmalıdır. Daha fazla bilgi için <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> özelliği örneğine bakın.

 Değişikliklerinizi kalıcı hale getirmek için, işlem atılmadan önce işlemi `Commit` gerekir. İşlem içinde yakalanamayan bir özel durum oluşursa, depo, değişikliklerden önce durumuna sıfırlanır.

## <a name="rolling-back-a-transaction"></a>Bir işlem geri alınıyor
 Deponun ' de kalmasını veya işlemden önce durumuna geri dönmemesini sağlamak için şu taktiklerinden birini kullanabilirsiniz:

1. İşlemin kapsamı içinde yakalanmayan bir özel durum yükseltir.

2. İşlemi açıkça geri alma:

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>İşlemler, depo olmayan nesneleri etkilemez
 İşlemler yalnızca deponun durumunu yönetir. Dosyalar, veritabanları ya da DSL tanımının dışında normal türlerle bildirdiğiniz nesneler gibi dış öğelerde yapılan kısmi değişiklikleri geri alamaz.

 Bir özel durum böyle bir değişikliği depolarla uyumsuz olarak bırakıyorsanız, özel durum işleyicisinde bu olasılığa karşı işlem yapmanız gerekir. Dış kaynakların mağaza nesneleri ile eşitlenmiş durumda kalmasını sağlamanın bir yolu, olay işleyicilerini kullanarak her bir dış nesnenin her bir bir yerleşik öğe için birkaç tane olmasını sağlar. Daha fazla bilgi için bkz. [olay Işleyicileri değişiklikleri model dışında yayma](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Bir Işlemin sonunda başlatılan kurallar
 İşlemin sonunda, işlem atılmadan önce, depodaki öğelere iliştirilmiş kurallar tetiklenir. Her kural, değiştirilen bir model öğesine uygulanan bir yöntemdir. Örneğin, model öğesi değiştirildiğinde bir şeklin durumunu güncelleştiren ve bir model öğesi oluşturulduğunda bir şekil oluşturan "düzeltmeler" kuralları vardır. Belirtilen bir tetikleme siparişi yok. Bir kural tarafından yapılan değişiklik, başka bir kural tetikleyerek.

 Kendi kurallarınızı tanımlayabilirsiniz. Kurallar hakkında daha fazla bilgi için bkz. [yanıt verme ve değişiklikleri yayma](../modeling/responding-to-and-propagating-changes.md).

 Geri alma, yineleme veya geri alma komutundan sonra kurallar işletilmez.

## <a name="transaction-context"></a>İşlem bağlamı
 Her bir işlem, istediğiniz bilgileri depolayabilmeniz için bir sözlüğe sahiptir:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Bu, özellikle kurallar arasında bilgi aktarımında yararlıdır.

## <a name="transaction-state"></a>İşlem durumu
 Bazı durumlarda, bir işlemi geri alma veya yeniden yapma nedeniyle değişikliğin nedeni bir değişikliği yaymaktan kaçınmanız gerekir. Bu, örneğin, depodaki başka bir değeri güncelleştirebilen bir özellik değer işleyicisi yazarsanız meydana gelebilir. Geri alma işlemi depodaki tüm değerleri önceki durumlarına sıfırlamadığı için, güncelleştirilmiş değerleri hesaplamak gerekli değildir. Şu kodu kullanın:

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Depo bir dosyadan ilk kez yüklenirken kurallar tetikde olur. Bu değişikliklere yanıt vermeyi önlemek için şunu kullanın:

```csharp
if (!this.Store.InSerializationTransaction) {...}
```