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
ms.openlocfilehash: 85573309e594fab49db75115a48b5a4e98e44de3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918852"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Salt Okunur Kesimler Oluşturmak için Kilitleme İlkesi Tanımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görselleştirme ve modelleme SDK 'sının kullanılabilirlik API 'SI, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir programın, bir etki alanına özgü dil (DSL) modelinin bir kısmını veya tamamını kilitlemesini, böylece okunabilmesi ancak değiştirilememesini sağlar. Bu salt okunurdur seçeneği, örneğin, bir kullanıcının iş arkadaşlarından bir DSL modeline açıklama ekleme ve gözden geçirmesine izin vermesini isteyebilir, ancak orijinalin değiştirilmesini engelleyebilir.

 Ayrıca, bir DSL yazarı olarak bir *kilitleme ilkesi tanımlayabilirsiniz.* Kilitleme ilkesi hangi kilitlerin izin verileceğini, izin verilmediğini veya zorunlu olduğunu tanımlar. Örneğin, bir DSL yayımladığınızda, üçüncü taraf geliştiricilere yeni komutlarla genişletecek şekilde teşvik edebilirsiniz. Ancak, modelin belirtilen bölümlerinin salt okunurdur durumunu değiştirmesini engellemek için bir kilitleme ilkesi de kullanabilirsiniz.

> [!NOTE]
> Kilitleme ilkesi, yansıma kullanılarak atlatılabilir. Üçüncü taraf geliştiricilere yönelik açık bir sınır sağlar, ancak güçlü güvenlik sağlamaz.

 Daha fazla bilgi [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [görselleştirme ve modelleme SDK](https://www.microsoft.com/download/details.aspx?id=48148) Web sitesinde bulunabilir.

## <a name="setting-and-getting-locks"></a>Kilitleri ayarlama ve alma
 Mağaza üzerinde, bir bölümde veya tek bir öğede kilit ayarlayabilirsiniz. Örneğin, bu ifade bir model öğesinin silinmesini engeller ve ayrıca özelliklerinin değiştirilmesini engeller:

```
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 Diğer kilit değerleri, ilişkilerin, öğe oluşturma, bölümler arasında hareket etme ve bir roldeki bağlantıları yeniden sıralama gibi değişiklikleri engellemek için kullanılabilir.

 Kilitler hem kullanıcı eylemlerine hem de program koduna uygulanır. Program kodu değişiklik yapmayı denerse, bir `InvalidOperationException` oluşturulur. Geri alma veya yineleme işleminde kilitler yok sayılır.

 Bir öğenin kullanarak belirli bir küme içinde herhangi bir kilidi olup olmadığını `IsLocked(Locks)` ve kullanarak bir öğe üzerinde geçerli kilit kümesini elde edip etmeyeceğinizi bulabilirsiniz `GetLocks()` .

 İşlem kullanmadan bir kilit ayarlayabilirsiniz. Kilit veritabanı, deponun bir parçası değil. Depodaki bir değer değişikliğine yanıt olarak bir kilit ayarlarsanız, örneğin OnValueChanged içinde, geri alma işleminin parçası olan değişikliklere izin vermeniz gerekir.

 Bu yöntemler ad alanında tanımlanan genişletme yöntemleridir <xref:Microsoft.VisualStudio.Modeling.Immutability> .

### <a name="locks-on-partitions-and-stores"></a>Bölümler ve depolardaki kilitler
 Kilitler ayrıca bölümlere ve depoya da uygulanabilir. Bölüm üzerinde ayarlanan bir kilit, bölümdeki tüm öğelere uygulanır. Bu nedenle, örneğin, aşağıdaki ifade, kendi kilitleri durumlarından bağımsız olarak bir bölümdeki tüm öğelerin silinmesini engeller. Bununla birlikte, gibi diğer kilitler `Locks.Property` ayrı ayrı öğeler üzerinde de ayarlanabilir:

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
 Kilitler bir mağaza, bölüm veya tek bir ModelElement üzerinde ayarlanabilir. Kilitler bir `Flags` sabit listesi: ' &#124; ' kullanarak değerlerini birleştirebilirsiniz.

- Bir ModelElement 'in kilitleri her zaman bölümünün kilitlerini içerir.

- Bir bölümün kilitleri her zaman deponun kilitlerini içerir.

  Bir bölüm veya mağaza üzerinde kilit ayarlayamazsınız ve aynı zamanda tek bir öğe üzerindeki kilidi devre dışı bırakın.

|Değer|True ise anlamı `IsLocked(Value)`|
|-----------|------------------------------------------|
|Hiçbiri|Kısıtlama yoktur.|
|Özellik|Öğelerin etki alanı özellikleri değiştirilemez. Bu, bir ilişkide bir etki alanı sınıfının rolü tarafından oluşturulan özellikler için geçerlidir.|
|Ekle|Yeni öğeler ve bağlantılar bir bölüm veya depoda oluşturulamaz.<br /><br /> İçin geçerli değildir `ModelElement` .|
|Taşı|Öğesi true ise bölümler arasında taşınamaz `element.IsLocked(Move)` veya `targetPartition.IsLocked(Move)` true ise geçerlidir.|
|Sil|Bu kilit öğenin kendisinde ayarlandıysa veya katıştırılmış öğeler ve şekiller gibi silme işleminin yayıldığı öğelerin herhangi birinde bir öğe silinemez.<br /><br /> `element.CanDelete()`Bir öğenin silinip silinemeyeceğini saptamak için kullanabilirsiniz.|
|Sütunlarını|Bir rolündeki RolePlayer 'da bağlantıların sıralaması değiştirilemez.|
|Rolündeki RolePlayer|Bu öğede kaynağı olan bağlantı kümesi değiştirilemez. Örneğin, yeni öğeler bu öğe altına Katıştırılamaz. Bu, bu öğenin hedef olduğu bağlantıları etkilemez.<br /><br /> Bu öğe bir bağlantı ise, kaynağı ve hedefi etkilenmez.|
|Tümü|Diğer değerlerin bit düzeyinde veya diğer değerleri.|

## <a name="locking-policies"></a>Ilkeleri kilitleme
 Bir DSL yazarı olarak bir *kilitleme ilkesi*tanımlayabilirsiniz. Bir kilitleme ilkesi SetLock () işlemini, belirli kilitlerin ayarlanmasını veya belirli kilitlerin ayarlanması gerektiğini önleyebilmenizi engelleyecek şekilde düzenler. Genellikle, bir kilitleme ilkesi kullanarak kullanıcıların veya geliştiricilerin, bir DSL 'nin amaçlanan kullanımını yanlışlıkla, bir değişken bildirebileceğiniz şekilde kullanmasını önleyin `private` .

 Ayrıca, öğe türüne bağımlı tüm öğelerde kilitleri ayarlamak için bir kilitleme ilkesi de kullanabilirsiniz. Bunun nedeni `SetLocks(Locks.None)` her zaman bir öğe ilk oluşturulduğunda veya dosyadan seri durumdan çıkarıldığı zaman çağrılır.

 Ancak, bir ilke, ömrü boyunca bir öğe üzerindeki kilitleri değiştirmek için kullanılamaz. Bu etkiyi elde etmek için, için çağrıları kullanmanız gerekir `SetLocks()` .

 Kilitleme ilkesi tanımlamak için şunları yapmanız gerekir:

- Uygulayan bir sınıf oluşturun <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> .

- Bu sınıfı, DSL 'nizin DocData aracılığıyla kullanılabilen hizmetlere ekleyin.

### <a name="to-define-a-locking-policy"></a>Kilitleme ilkesi tanımlamak için
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> Aşağıdaki tanıma sahiptir:

```
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Bu yöntemler `SetLocks()` , bir mağaza, bölüm veya ModelElement üzerinde bir çağrı yapıldığında çağrılır. Her yöntemde, önerilen bir kilit kümesi sunulur. Önerilen kümeyi döndürebilir veya kilitleri ekleyip çıkarabilirsiniz.

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

 Diğer kod çağrısa bile kullanıcıların her zaman öğeleri silebilse emin olmak için `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Her MyClass öğesinin tüm özelliklerinde değişikliğe izin vermemek için:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>İlkenizin bir hizmet olarak kullanılabilmesini sağlamak için
 `DslPackage`Projenizde, aşağıdaki örneğe benzer bir kod içeren yeni bir dosya ekleyin:

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
