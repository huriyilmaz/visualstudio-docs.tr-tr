---
title: Salt okuma kesimleri oluşturmak için kilitleme Ilkesi tanımlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5acbb4d2966e89f7913fa1479b882fad5c9650f7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295810"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Salt Okunur Kesimler Oluşturmak için Kilitleme İlkesi Tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] görselleştirme ve modelleme SDK 'sının kullanılabilirlik API 'SI, bir programın, bir etki alanına özgü dil (DSL) modelinin bir kısmını veya tamamını kilitlemesini, böylece okunabilmesi ancak değiştirilememesini sağlar. Bu salt okunurdur seçeneği, örneğin, bir kullanıcının iş arkadaşlarından bir DSL modeline açıklama ekleme ve gözden geçirmesine izin vermesini isteyebilir, ancak orijinalin değiştirilmesini engelleyebilir.

 Ayrıca, bir DSL yazarı olarak bir *kilitleme ilkesi tanımlayabilirsiniz.* Kilitleme ilkesi hangi kilitlerin izin verileceğini, izin verilmediğini veya zorunlu olduğunu tanımlar. Örneğin, bir DSL yayımladığınızda, üçüncü taraf geliştiricilere yeni komutlarla genişletecek şekilde teşvik edebilirsiniz. Ancak, modelin belirtilen bölümlerinin salt okunurdur durumunu değiştirmesini engellemek için bir kilitleme ilkesi de kullanabilirsiniz.

> [!NOTE]
> Kilitleme ilkesi, yansıma kullanılarak atlatılabilir. Üçüncü taraf geliştiricilere yönelik açık bir sınır sağlar, ancak güçlü güvenlik sağlamaz.

 Daha fazla bilgi ve örnek [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [görselleştirme ve modelleme SDK](https://go.microsoft.com/fwlink/?LinkId=186128) Web sitesinde bulunabilir.

## <a name="setting-and-getting-locks"></a>Kilitleri ayarlama ve alma
 Mağaza üzerinde, bir bölümde veya tek bir öğede kilit ayarlayabilirsiniz. Örneğin, bu ifade bir model öğesinin silinmesini engeller ve ayrıca özelliklerinin değiştirilmesini engeller:

```
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Diğer kilit değerleri, ilişkilerin, öğe oluşturma, bölümler arasında hareket etme ve bir roldeki bağlantıları yeniden sıralama gibi değişiklikleri engellemek için kullanılabilir.

 Kilitler hem kullanıcı eylemlerine hem de program koduna uygulanır. Program kodu değişiklik yapmayı denerse bir `InvalidOperationException` oluşturulur. Geri alma veya yineleme işleminde kilitler yok sayılır.

 Bir öğenin, `IsLocked(Locks)` kullanarak belirli bir küme içinde herhangi bir kilidi olup olmadığını ve `GetLocks()`kullanarak bir öğe üzerinde geçerli kilit kümesini elde edip etmeyeceğinizi bulabilirsiniz.

 İşlem kullanmadan bir kilit ayarlayabilirsiniz. Kilit veritabanı, deponun bir parçası değil. Depodaki bir değer değişikliğine yanıt olarak bir kilit ayarlarsanız, örneğin OnValueChanged içinde, geri alma işleminin parçası olan değişikliklere izin vermeniz gerekir.

 Bu yöntemler <xref:Microsoft.VisualStudio.Modeling.Immutability> ad alanında tanımlanan genişletme yöntemleridir.

### <a name="locks-on-partitions-and-stores"></a>Bölümler ve depolardaki kilitler
 Kilitler ayrıca bölümlere ve depoya da uygulanabilir. Bölüm üzerinde ayarlanan bir kilit, bölümdeki tüm öğelere uygulanır. Bu nedenle, örneğin, aşağıdaki ifade, kendi kilitleri durumlarından bağımsız olarak bir bölümdeki tüm öğelerin silinmesini engeller. Bununla birlikte, `Locks.Property` gibi diğer kilitler ayrı ayrı öğeler üzerinde de ayarlanabilir:

```
partition.SetLocks(Locks.Delete);
```

 Depolarda ayarlanan bir kilit, bölümler ve öğeler üzerindeki bu kilidin ayarlarından bağımsız olarak tüm öğelerine uygulanır.

### <a name="using-locks"></a>Kilitleri kullanma
 Aşağıdaki örnekler gibi şemaları uygulamak için kilitleri kullanabilirsiniz:

- Açıklamaları temsil eden öğeler hariç tüm öğe ve ilişkilerde değişikliklere izin vermeyin. Bu, kullanıcıların bir modele değişiklik yapmadan ek açıklama eklemesini sağlar.

- Varsayılan bölümdeki değişikliklere izin vermeyin, ancak diyagram bölümünde değişikliklere izin verin. Kullanıcı diyagramı yeniden düzenleyebilir, ancak temel modeli değiştiremezler.

- Ayrı bir veritabanına kayıtlı Kullanıcı grubu dışında depoda değişikliklere izin vermeyin. Diğer kullanıcılar için Diyagram ve model salt okunurdur.

- Diyagramın Boolean özelliği true olarak ayarlandıysa modelde değişikliklere izin vermeyin. Bu özelliği değiştirmek için bir menü komutu sağlayın. Bu, kullanıcılara yanlışlıkla değişiklik yapmamasını sağlamaya yardımcı olur.

- Belirli sınıfların öğelerinin ve ilişkilerinin eklenmesine ve silinmesine izin vermeyin, ancak özellik değişikliklerine izin vermez. Bu, kullanıcılara özellikleri dolduracakları sabit bir form sağlar.

## <a name="lock-values"></a>Değerleri kilitle
 Kilitler bir mağaza, bölüm veya tek bir ModelElement üzerinde ayarlanabilir. Kilitler `Flags` bir numaralandırmadır: değerlerini '&#124;' kullanarak birleştirebilirsiniz.

- Bir ModelElement 'in kilitleri her zaman bölümünün kilitlerini içerir.

- Bir bölümün kilitleri her zaman deponun kilitlerini içerir.

  Bir bölüm veya mağaza üzerinde kilit ayarlayamazsınız ve aynı zamanda tek bir öğe üzerindeki kilidi devre dışı bırakın.

|Value|`IsLocked(Value)` true ise anlamı|
|-----------|------------------------------------------|
|Yok.|Kısıtlama yoktur.|
|Özellik|Öğelerin etki alanı özellikleri değiştirilemez. Bu, bir ilişkide bir etki alanı sınıfının rolü tarafından oluşturulan özellikler için geçerlidir.|
|Ekle|Yeni öğeler ve bağlantılar bir bölüm veya depoda oluşturulamaz.<br /><br /> `ModelElement`için geçerli değildir.|
|Taşıma|`element.IsLocked(Move)` true ise veya `targetPartition.IsLocked(Move)` true ise, öğe bölümler arasında taşınamaz.|
|Sil|Bu kilit öğenin kendisinde ayarlandıysa veya katıştırılmış öğeler ve şekiller gibi silme işleminin yayıldığı öğelerin herhangi birinde bir öğe silinemez.<br /><br /> Bir öğenin silinip silinemediğini saptamak için `element.CanDelete()` kullanabilirsiniz.|
|Sütunlarını|Bir rolündeki RolePlayer 'da bağlantıların sıralaması değiştirilemez.|
|Rolündeki RolePlayer|Bu öğede kaynağı olan bağlantı kümesi değiştirilemez. Örneğin, yeni öğeler bu öğe altına Katıştırılamaz. Bu, bu öğenin hedef olduğu bağlantıları etkilemez.<br /><br /> Bu öğe bir bağlantı ise, kaynağı ve hedefi etkilenmez.|
|Tümü|Diğer değerlerin bit düzeyinde veya diğer değerleri.|

## <a name="locking-policies"></a>Ilkeleri kilitleme
 Bir DSL yazarı olarak bir *kilitleme ilkesi*tanımlayabilirsiniz. Bir kilitleme ilkesi SetLock () işlemini, belirli kilitlerin ayarlanmasını veya belirli kilitlerin ayarlanması gerektiğini önleyebilmenizi engelleyecek şekilde düzenler. Genellikle, bir değişken `private`bildirebilmeniz için kullanıcıların veya geliştiricilerin, bir DSL 'nin amaçlanan kullanımını yanlışlıkla kullanmasını önlemek için bir kilitleme ilkesi kullanırsınız.

 Ayrıca, öğe türüne bağımlı tüm öğelerde kilitleri ayarlamak için bir kilitleme ilkesi de kullanabilirsiniz. Bunun nedeni `SetLocks(Locks.None)` her zaman bir öğe ilk oluşturulduğunda veya dosyadan seri durumdan çıkarılacağından çağrılır.

 Ancak, bir ilke, ömrü boyunca bir öğe üzerindeki kilitleri değiştirmek için kullanılamaz. Bu etkiyi elde etmek için `SetLocks()`çağrıları kullanmanız gerekir.

 Kilitleme ilkesi tanımlamak için şunları yapmanız gerekir:

- <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>uygulayan bir sınıf oluşturun.

- Bu sınıfı, DSL 'nizin DocData aracılığıyla kullanılabilen hizmetlere ekleyin.

### <a name="to-define-a-locking-policy"></a>Kilitleme ilkesi tanımlamak için
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> aşağıdaki tanıma sahiptir:

```
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Bu yöntemler, bir mağaza, bölüm veya ModelElement üzerinde `SetLocks()` bir çağrı yapıldığında çağrılır. Her yöntemde, önerilen bir kilit kümesi sunulur. Önerilen kümeyi döndürebilir veya kilitleri ekleyip çıkarabilirsiniz.

 Örneğin:

```
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

 Kullanıcıların öğeleri her zaman silebilse de, diğer kod çağrısa bile `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Her MyClass öğesinin tüm özelliklerinde değişikliğe izin vermemek için:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>İlkenizin bir hizmet olarak kullanılabilmesini sağlamak için
 `DslPackage` projenizde, aşağıdaki örneğe benzer bir kod içeren yeni bir dosya ekleyin:

```
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
