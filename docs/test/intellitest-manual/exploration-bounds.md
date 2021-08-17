---
title: Keşif sınırları | Microsoft IntelliTest Geliştirici Test Aracı
description: PexSettingsAttributeBase, öznitelik olarak ayarlar sınırları için soyut temel sınıftır. Adlandırılmış özellikleri kullanarak ayarları değiştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: be5e90949089f92289c5f6b32ebafd9e81e658c3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059991"
---
# <a name="exploration-bounds"></a>Keşif sınırları

**PexSettingsAttributeBase,** öznitelik olarak ayarlar sınırları için soyut temel sınıftır. IntelliTest Ayarlar ayarlarına genel bakış için bkz. Ayarlar [Waterfall.](settings-waterfall.md)

Bunun adlandırılmış özelliklerini ve türetilmiş özniteliklerini kullanarak ayarları değiştirebilirsiniz:

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Kısıtlama çözme sınırları**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) - Kısıtlama çözücüs ünileri bulması gereken, yeni ve farklı bir yürütme yolunun izlenilmesine neden olacak saniye sayısı. [](input-generation.md#constraint-solver)
  * [MaxConstraintSolverMemory:](#maxconstraintsolvermemory) Kısıtlama çözücüsürleyicinin [](input-generation.md#constraint-solver) girişleri bulmak için kullanabileceği Megabayt cinsinden boyut.
* **Keşif Yolu Sınırları**
  * [MaxBranches:](#maxbranches) Tek bir yürütme yolu boyunca alınacak en fazla dal sayısı.
  * [MaxCalls:](#maxcalls) Tek bir yürütme yolu sırasında en fazla çağrı sayısı.
  * [MaxStack:](#maxstack) Tek bir yürütme yolu sırasında herhangi bir anda etkin çağrı çerçevelerinin sayısı olarak ölçülen en büyük yığın boyutu.
  * [MaxConditions:](#maxconditions) Tek bir yürütme yolu sırasında denetlenen girişler üzerinde en fazla koşul sayısı.
* **Keşif Sınırları**
  * [MaxRuns:](#maxruns) Araştırma sırasında denenecek en fazla çalıştırma sayısı.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) - Yeni bir test yayımlanacak olmadan ardışık çalıştırma sayısı üst sayısı.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) : Keşif sırasında denenecek benzersiz yürütme yollarına sahip en fazla çalıştırma sayısı.
  * [MaxExceptions](#maxexceptions) - Bulunan tüm yürütme yollarının birleşimi için bulunamayan en fazla özel durum sayısı.
* **Test Paketi Kod Oluşturma Ayarlar**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) - True olduğunda, yol sınırlardan herhangi birini[(MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [MaxConditions](#maxconditions)) aşan yürütme yolları yoksayılır.
  * [TestEmissionFilter](#testemissionfilter) - IntelliTest'in testleri hangi koşullarda yaysı gerektiğini gösterir.
  * [TestEmissionBranchHits](#testemissionbranchhits) - IntelliTest'in kaç test yayıyor olduğunu kontrol eder.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

Kısıtlama çözümleyicinin [yeni ve farklı](input-generation.md#constraint-solver) bir yürütme yolunun alınmasına neden olacak girişleri hesaplaması gereken saniye sayısı. Bu, **PexSettingsAttributeBase** ve türetilmiş türlerinin bir seçeneğidir.

IntelliTest bir programın yürütme yollarını ne kadar derinlemesine inceler ve IntelliTest'in programın denetim akışından ve veri akışından derlemesi daha karmaşık hale gelen kısıtlama sistemleri o kadar karmaşık olur. Zaman sınırlamanıza bağlı olarak, bu değeri IntelliTest'in yeni yürütme yollarını bulmak için daha fazla veya daha az zaman aldıracak şekilde ayarlayın.

Genellikle, zaman aşımının nedeni IntelliTest'in çözümüne sahip bir kısıtlama sistemi için bir çözüm bulmaya çalışıyor olmasıdır ancak bu durumun farkında değildir. Zaman aşımı için en yaygın durum bu olduğu için sınırı artırmak mantıklı olabilir.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

Kısıtlama çözümleyicinin yeni ve [farklı](input-generation.md#constraint-solver) bir yürütme yolunun alınmasına neden olacak girişleri hesaplaması gereken Megabayt sayısı. Bu, *PexSettingsAttributeBase** ve türetilmiş türlerinin bir seçeneğidir.

Daha derin IntelliTest, bir programın yürütme yollarını inceler; IntelliTest'in programın denetim akışından ve veri akışından derlemesi daha karmaşık olan kısıtlama sistemleri haline geldi. Bilgisayarınızın kullanılabilir belleğine bağlı olarak, IntelliTest'in daha karmaşık kısıtlama sistemleriyle başa olmasına izin vermek için bu değeri ayarlayın.

Genellikle, zaman aşımının nedeni IntelliTest'in çözümüne sahip bir kısıtlama sistemi için bir çözüm bulmaya çalışıyor olmasıdır ancak bu durumun farkında değildir. Yetersiz bellek durumunun en yaygın nedeni bu olduğu için sınırı artırmak mantıklı olabilir.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Tek bir yürütme yolu boyunca alınacak en fazla dal sayısı.

Bu araştırma sınırının ardındaki motivasyon, IntelliTest'in giriş oluşturma sırasında keşfeder olduğu yürütme yollarının uzunluğunu [sınırlamaktır.](input-generation.md) Özellikle, program sonsuz bir döngüye girse IntelliTest'in yanıt vermemeye devamsını önler.

Yürütülen ve izlenen kodun her koşullu ve koşulsuz dalı, parametreli testin girişlerine bağlı olmayan dallar da dahil olmak üzere bu sınıra doğru sayılır.

Örneğin, aşağıdaki kod 100 sırasına göre dalları tüketir:

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Tek bir yürütme yolu sırasında en fazla çağrı sayısı.

Bu araştırma sınırının ardındaki motivasyon, IntelliTest'in giriş oluşturma sırasında keşfeder olduğu yürütme yollarının uzunluğunu [sınırlamaktır.](input-generation.md) Özellikle, program bir yöntemi tekrar tekrar sonsuz sayıda kez çağırması, IntelliTest'in kurtarılamamasına neden olan yığın taşmasına neden olursa IntelliTest'in yanıt vermemeye devamsını önler.

Yürütülen ve izlenen kodun her çağrısı (doğrudan, dolaylı, sanal, atlama) bu sınıra doğru sayılır.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Tek bir yürütme yolu sırasında herhangi bir anda yığının etkin çağrı çerçevelerinin sayısıyla ölçülen en büyük boyutu.

Bu keşif sınırının ardındaki motivasyon, IntelliTest'in giriş oluşturma sırasında araştıran herhangi bir yürütme yolunun yığınının [boyutunu sınırlamaktır.](input-generation.md) Özellikle, IntelliTest'in tüm kullanılabilir yığın alanı kullanmasını önler ve bu da IntelliTest'in kurtarılmamasına neden olan yığın taşmasına neden olur.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Tek bir yürütme yolu sırasında denetlenen girişler üzerinde koşulların en fazla sayısı.

Bu araştırma sınırının ardındaki motivasyon, IntelliTest'in giriş oluşturma sırasında keşfeder olduğu yürütme yollarının [karmaşıklığını sınırlamaktır.](input-generation.md) Parametreli testin girişlerine bağlı olan her koşullu dal bu sınıra doğru sayılır.

Örneğin, aşağıdaki kodda yer alan her yol n+1 koşullarını tüketir:

```csharp
[PexMethod]
void ParameterizedTest(int n)
{
     for (int i=0; i<n; i++) { // conditions are "0<n", "1<n", ..., "!(n<n)"
          ...
     }
     for (int i=0; i<100; i++) { // irrelevant for MaxConditions, since conditions do not depend on input
          ...
     }
}
```

<a name="maxruns"></a>
## <a name="maxruns"></a>MaxRuns

IntelliTest'in bir testin keşfi sırasında deneyecek en fazla çalıştırma sayısı.

Bu keşif sınırlarının ardındaki motivasyon, döngüler veya yeniden yürütme içeren tüm kodlarda sonsuz sayıda yürütme yolu olması ve dolayısıyla IntelliTest'in giriş oluşturma sırasında sınırlı [olmasıdır.](input-generation.md)

MaxRuns ve **MaxRunsWithUniquePaths** iki ayarı aşağıdaki gibi ilişkili olur: 

* IntelliTest, farklı test girişleriyle **MaxRuns** saatine kadar parametreli bir test yöntemini çağıracak.
* Yürütülen kod belirlenmci ise, IntelliTest her zaman farklı bir yürütme yolu alır. Ancak, bazı koşullar altında yürütülen kod, farklı girişlerle daha önce alınmış bir yürütme yolunu takip ediyor olabilir.
* IntelliTest, bulduğu benzersiz yürütme yollarını sayar; Bu sayı **MaxRunsWithUniquePaths seçeneğiyle** sınırlıdır.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Yeni bir test yayımlanmadan ardışık çalıştırma sayısı üst üste.

IntelliTest genellikle kısa bir süre içinde birçok ilgi çekici test girişi bulsa da, bir süre sonra başka yeni test girişi bulamaz ve daha fazla birim testi yamayacaktır. Bu yapılandırma seçeneği, IntelliTest'in yeni bir test yaymadan gerçekleştirebilirsiniz ardışık girişim sayısına bir sınır ayarlar. Ulaşıldıklarda keşfi durduracak.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

IntelliTest'in araştırma sırasında dikkate alacacazı benzersiz yol sayısı.

Bu keşif sınırlarının ardındaki motivasyon, döngü veya recursion içeren herhangi bir kodun sınırsız sayıda yürütme yolu olabileceği ve bu nedenle IntelliTest'in giriş oluşturma sırasında sınırlı [olmasıdır.](input-generation.md)

MaxRuns ve **MaxRunsWithUniquePaths** iki ayarı aşağıdaki gibi ilişkili olur: 

* IntelliTest, farklı test girişleriyle **MaxRuns** saatine kadar parametreli bir test yöntemini çağıracak.
* Yürütülen kod belirlenmci ise, IntelliTest her zaman farklı bir yürütme yolu alır. Ancak, bazı koşullar altında yürütülen kod, farklı girişlerle daha önce alınmış bir yürütme yolunu takip ediyor olabilir.
* IntelliTest, bulduğu benzersiz yürütme yollarını sayar; Bu sayı **MaxRunsWithUniquePaths seçeneğiyle** sınırlıdır.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Araştırma durdurulmadan önce karşılaş karşılaşılan en fazla özel durum sayısı.

Bu keşif sınırlarının ardındaki motivasyon, birçok hata içeren kodun keşfini durdurmaktır. IntelliTest kodda çok fazla hata bulursa araştırma durdurulur.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Yapılandırılan yol sınırlarını aşan yürütme yolları [MaxCalls,](#maxcalls) [MaxBranches,](#maxbranches) [MaxStack](#maxstack)ve [MaxConditions](#maxconditions) yoksayılır.

Bu keşif sınırlarının ardındaki motivasyon, (büyük olasılıkla) sonlandırıcı olmayan testlerle uğraşmaktır. IntelliTest; [MaxCalls,](#maxcalls) [MaxBranches,](#maxbranches) [MaxStack](#maxstack)veya [MaxConditions](#maxconditions)gibi bir keşif sınırlarına ulaştığında testin sonlandıran bir işlem olmadığını ve daha sonra yığın taşmasına neden olmadığını varsayıyor. Bu tür test çalışmaları diğer test çerçeveleri için soruna neden olabilir ve bu öznitelik IntelliTest'in sonlandırıcı olmayabilecek işlemler veya yığın taşmasına neden olabilecek test çalışmaları için test çalışmaları yaymasına engel olmak için bir yol sağlar.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

IntelliTest'in yaymaları gereken test türlerini gösterir. Olası değerler şunlardır:

* **All** : Varsayım ihlalleri de dahil olmak üzere her şey için testler yayma.
* **FailuresAndIncreasedBranchHits** (varsayılan) - Tüm benzersiz hatalar için testleri yayın ve test çalışmalarında [TestEmissionBranchHits](#testemissionbranchhits)tarafından denetlenen kapsamı her artırıyor.
* **FailuresAndUniquePaths** - IntelliTest'in bulduğu tüm hatalar ve benzersiz bir yürütme yoluna neden olan her test girişi için testleri yayın.
* **Hatalar** - Testleri yalnızca hatalar için yayın.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

Geçerli [TestEmissionFilter](#testemissionfilter) ayarına bağlı olarak, IntelliTest programda daha önce kapsamamış olan bir dalı kapsamış olduğunda yeni test çalışmalarını yalıtır.

**TestEmissionBranchHits** ayarı, IntelliTest'in bir dalın kapsamına alınıp alın olmadığını **(TestEmissionBranchHits=1)** ve bir testin bir veya iki kez kapsaıp alına olmadığını **(TestEmissionBranchHits=2**) ve bu şekilde devam edip edip e-nce bir şey olmadığını belirler.

**TestEmissionBranchHits=1,** IntelliTest'in ulaşa ulaştığı tüm dalları kapsayacak çok küçük bir test paketi üretir. Bu test paketi özellikle ulaştığı tüm temel blokları ve deyimleri de kapsayacaktır.

Bu seçeneğin varsayılan ayarı **Testemissionbranchhits = 2**' dir. Bu, gelecekteki gerileme hatalarını saptamak için daha uygun olan daha açıklayıcı bir test paketi oluşturur.

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://aka.ms/feedback/suggest?space=8)’na gönderin.
