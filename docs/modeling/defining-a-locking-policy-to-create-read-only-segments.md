---
title: Salt Okunur Kesimler Oluşturmak için Kilitleme İlkesi Tanımlama
description: Okunmalarını ancak değiştirilene kadar etki alanına özgü dil (DSL) modelinin bir bölümünü veya hepsini kilitlemek üzere program için ilke tanımlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb8e05ffc030716f32ab7e79233ca9e02ef2e11
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385792"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Salt Okunur Kesimler Oluşturmak için Kilitleme İlkesi Tanımlama
Visual Studio Görselleştirme ve Modelleme SDK'sı'nın Sabitlik API'si, bir programın etki alanına özgü dil (DSL) modelinin bir kısmını veya hepsini okuyabilsin ama değiştirilesin diye kilitlemesini sağlar. Bu salt okunur seçenek, örneğin, bir kullanıcının iş arkadaşlarınızdan DSL modeline not ek açıklama ve gözden geçirmesini isteyerek özgün modeli değiştirmelerine izin veremelerini sağ şekilde etkinleştirmek için kullanılabilir.

 Ayrıca DSL'nin yazarı olarak bir kilitleme ilkesi *tanımlayabilirsiniz.* Kilitleme ilkesi hangi kilitlere izin verildiğini, hangilerinin izin verilmediğini veya zorunlu olduğunu tanımlar. Örneğin, dsl yayımlarken üçüncü taraf geliştiricileri yeni komutlarla genişletmeye teşvik yapabilirsiniz. Ancak, modelin belirtilen bölümlerinin salt okunur durumunu değiştirmelerini önlemek için bir kilitleme ilkesi de kullanabilirsiniz.

> [!NOTE]
> Bir kilitleme ilkesi, yansıma kullanılarak yok olabilir. Üçüncü taraf geliştiriciler için net bir sınır sağlar, ancak güçlü güvenlik sağlamaz.

 Görselleştirme ve Modelleme SDK'sı web Visual Studio [daha fazla bilgi ve örnek](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) bulabilirsiniz.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>KilitLeri Ayarlama ve Alma
 Depoda, bölümde veya tek bir öğede kilitler ayarlayın. Örneğin, bu deyim model öğesinin silinmesini ve özelliklerinin değişmesini de önler:

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 İlişkilerdeki değişiklikleri, öğe oluşturmayı, bölümler arasındaki hareketi ve bir roldeki bağlantıları yeniden sıralamayı önlemek için diğer kilit değerleri kullanılabilir.

 Kilitler hem kullanıcı eylemlerine hem de program koduna uygulanır. Program kodu bir değişiklik yapmaya `InvalidOperationException` çalışırsa, bir atılan. Geri Al veya Tekrarla işleminde kilitler yoksayılır.

 kullanarak bir öğenin bir kümede herhangi bir kilidi olup olmadığını keşfedebilirsiniz ve kullanarak bir öğede geçerli `IsLocked(Locks)` kilitler kümesi elde `GetLocks()` edebilirsiniz.

 Bir işlem kullanmadan bir kilit ayarlayın. Kilit veritabanı, depolamanın bir parçası değildir. Depoda bir değer değişikliğine (örneğin OnValueChanged içinde) yanıt olarak bir kilit ayarlarsanız, Geri Alma işleminin parçası olan değişikliklere izin ver gerekir.

 Bu yöntemler, ad alanı içinde tanımlanan uzantı <xref:Microsoft.VisualStudio.Modeling.Immutability> yöntemleridir.

### <a name="locks-on-partitions-and-stores"></a>Bölümler ve depolar üzerinde kilitler
 Kilitler bölümlere ve depoya da uygulanabilir. Bir bölümde ayarlanmış bir kilit, bölümdeki tüm öğelere uygulanır. Bu nedenle, örneğin, aşağıdaki deyim kendi kilitlerinin durumları ne olursa olsun bir bölümdeki tüm öğelerin silinmesini önler. Bununla birlikte, gibi diğer `Locks.Property` kilitler yine de tek tek öğelerde ayarlanmış olabilir:

```csharp
partition.SetLocks(Locks.Delete);
```

 Store'da ayarlanmış bir kilit, bölümler ve öğelerde bu kilidin ayarlarından bağımsız olarak tüm öğeleri için geçerlidir.

### <a name="using-locks"></a>Kilitleri Kullanma
 Aşağıdaki örnekler gibi şemaları uygulamak için kilitleri kullanabilirsiniz:

- Yorumları temsil eden öğeler dışındaki tüm öğelerde ve ilişkilerde yapılan değişikliklere izin veılamaz. Bu, kullanıcıların bir modele değiştirmeden not ek açıklamalarını sağlar.

- Varsayılan bölümdeki değişikliklere izin verme, ancak diyagram bölümde değişikliklere izin verme. Kullanıcı diyagramı yeniden düzenleyebilir ancak temel alınan modeli değiştirilemez.

- Ayrı bir veritabanına kayıtlı bir grup kullanıcı dışında Mağazada yapılan değişikliklere izin ve değildir. Diğer kullanıcılar için diyagram ve model salt okunur olur.

- Diyagramın Boole özelliği true olarak ayarlanırsa modelde yapılan değişikliklere izin ve son. Bu özelliği değiştirmek için bir menü komutu sağlar. Bu, kullanıcıların yanlışlıkla değişiklik yapmalarını sağlamaya yardımcı olur.

- Öğelerin ve belirli sınıfların ilişkilerinin ek ve silinmesine izin verme, ancak özellik değişikliklerine izin verme. Bu, kullanıcılara özellikleri dolduracakları sabit bir form sağlar.

## <a name="lock-values"></a>Değerleri kilitleme
 Kilitler Bir Mağazada, Bölümde veya tek tek ModelElement'de ayar olabilir. Kilitler bir `Flags` numaralamadır: değerlerini '&#124;' kullanarak birleştirebilirsiniz.

- ModelElement kilitleri her zaman Bölümünün Kilitlerini içerir.

- Bir Bölümün kilitleri her zaman Depo Kilitlerini içerir.

  Bir bölümde veya depoda kilit ayaramaz ve aynı zamanda tek bir öğede kilidi devre dışı bırakamaz.

|Değer|True ise `IsLocked(Value)` anlamına gelir|
|-|-|
|Hiçbiri|Kısıtlama yok.|
|Özellik|Öğelerin etki alanı özellikleri değiştirilemez. Bu, bir ilişkide bir etki alanı sınıfının rolü tarafından oluşturulan özellikler için geçerli değildir.|
|Ekle|Yeni öğeler ve bağlantılar bir bölümde veya depoda oluşturulamaz.<br /><br /> için geçerli `ModelElement` değildir.|
|Taşı|True ise veya true ise `element.IsLocked(Move)` öğe bölümler arasında `targetPartition.IsLocked(Move)` taşınamaz.|
|Sil|Bu kilit öğenin kendisinde ayarlanırsa veya silme işleminin yayma işlemi sinen öğeler (katıştırılmış öğeler ve şekiller gibi) üzerinde bir öğe silinemez.<br /><br /> Bir öğenin `element.CanDelete()` silinip siline olmadığını bulmak için kullanabilirsiniz.|
|Sipariş|Bir roleplayer'da bağlantıların sırası değiştirilemez.|
|Roleplayer|Bu öğede kaynak olarak alınan bağlantı kümesi değiştirilemez. Örneğin, yeni öğeler bu öğenin altına katıştıramaz. Bu, bu öğenin hedef olduğu bağlantıları etkilemez.<br /><br /> Bu öğe bir bağlantı ise, kaynağı ve hedefi etkilenmez.|
|Tümü|Diğer değerlerin Bit olarak OR değeri.|

## <a name="locking-policies"></a>İlkeleri Kilitleme
 DSL'nin yazarı olarak bir kilitleme ilkesi *tanımlayabilirsiniz.* Kilitleme ilkesi SetLocks() işlemiyle denetlenmesiyle, belirli kilitlerin ayarlanmış olması engellenebilir veya belirli kilitlerin ayarlanmış olması zorunlu olabilir. Genellikle, kullanıcıların veya geliştiricilerin DSL'nin amaçlanan kullanımını yanlışlıkla bir değişken bildirerek yanlışlıkla dolamalarını engellememek için bir kilitleme ilkesi `private` kullanırsınız.

 Kilitleri öğenin türüne bağlı tüm öğelerde ayarlamak için bir kilitleme ilkesi de kullanabilirsiniz. Bunun nedeni, `SetLocks(Locks.None)` bir öğe dosyadan ilk kez oluşturulduğunda veya dosyadan deserialized olduğunda her zaman çağrılır.

 Ancak, bir öğenin kilitlerini yaşam süresi boyunca değiştirmesi için bir ilke kullanılamaz. Bu etkiyi elde etmek için çağrıları kullan `SetLocks()` gerekir.

 Kilitleme ilkesi tanımlamak için şunları yapmak gerekir:

- uygulayan bir sınıf <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> oluşturun.

- Bu sınıfı DSL'nizin DocData'sı aracılığıyla kullanılabilen hizmetlere ekleyin.

### <a name="to-define-a-locking-policy"></a>Kilitleme ilkesi tanımlamak için
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> aşağıdaki tanımı içerir:

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Bu yöntemler Store, Partition veya ModelElement üzerinde çağrısı `SetLocks()` yapılırken çağrılır. Her yöntemde önerilen bir kilit kümesi sağlanır. Önerilen kümeyi veya kilitleri ekleyip çıkarabilirsiniz.

 Örneğin:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  public class MyLockingPolicy : ILockingPolicy
  {
    /// <summary>
    /// Moderate SetLocks(this ModelElement target, Locks locks)
    /// </summary>
    /// <param name="element">target</param>
    /// <param name="proposedLocks">locks</param>
    /// <returns></returns>
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)
    {
      // In my policy, users can never delete an element,
      // and other developers cannot easily change that:
      return proposedLocks | Locks.Delete);
    }
    public Locks RefineLocks(Store store, Locks proposedLocks)
    {
      // Only one user can change this model:
      return Environment.UserName == "aUser"
           ? proposedLocks : Locks.All;
    }
```

 Kullanıcıların, diğer kod çağrıları bile olsa her zaman öğeleri silebilir olduğundan emin olmak için `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 MyClass öğesinin her öğesinin tüm özelliklerinde değişiklike izin ve etmek için:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>İlkenizi hizmet olarak kullanılabilir hale yapmak için
 `DslPackage`Projenize, aşağıdaki örnekteki gibi kod içeren yeni bir dosya ekleyin:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  // Override the DocData GetService() for this DSL.
  internal partial class YourDslDocData // Change
  {
    /// <summary>
    /// Custom locking policy cache.
    /// </summary>
    private ILockingPolicy myLockingPolicy = null;

    /// <summary>
    /// Called when a service is requested.
    /// </summary>
    /// <param name="serviceType">Service requested</param>
    /// <returns>Service implementation</returns>
    public override object GetService(System.Type serviceType)
    {
      if (serviceType == typeof(SLockingPolicy)
       || serviceType == typeof(ILockingPolicy))
      {
        if (myLockingPolicy == null)
        {
          myLockingPolicy = new MyLockingPolicy();
        }
        return myLockingPolicy;
      }
      // Request is for some other service.
      return base.GetService(serviceType);
    }
}
```
