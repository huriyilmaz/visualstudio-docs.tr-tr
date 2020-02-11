---
title: Keşif sınırları | Microsoft IntelliTest geliştirici test aracı
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: jillre
ms.openlocfilehash: 03f23aacbe95615b565dfcee54d2b620c0ae1cd9
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091840"
---
# <a name="exploration-bounds"></a>Keşif sınırları

**PexSettingsAttributeBase** , ayarlar sınırları için soyut temel sınıftır. IntelliTest içindeki ayarlara genel bakış için bkz. [Ayarlar şelale](settings-waterfall.md) .

Bu ve türetilmiş özniteliklerinin adlandırılmış özelliklerini kullanarak ayarları değiştirebilirsiniz:

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Kısıtlama çözme sınırları**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) - [kısıtlama çözücü 'nün](input-generation.md#constraint-solver) yeni ve farklı bir yürütme yolunun izlenmesine neden olacak girişleri bulması gereken saniye sayısı.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) - [kısıtlama çözücü 'nün](input-generation.md#constraint-solver) girişleri keşfetmesi için kullanabileceği megabayt cinsinden boyut.
* **Araştırma yolu sınırları**
  * [Maxbranches](#maxbranches) -tek bir yürütme yolu üzerinde alınabilecek dal sayısı üst sınırı.
  * [Maxçağrılarında](#maxcalls) -tek bir yürütme yolu sırasında yapılabilecek en fazla çağrı sayısı.
  * [Maxstack](#maxstack) -tek bir yürütme yolu sırasında her zaman en fazla yığın boyutu, etkin çağrı çerçevesi sayısı olarak ölçülür.
  * [Maxconditions](#maxconditions) -tek bir yürütme yolu sırasında denetlenecek girişler üzerinde en fazla koşul sayısı.
* **Keşif sınırları**
  * [Maxçalıştırmaları](#maxruns) -bir keşif sırasında denenecek en fazla çalıştırma sayısı.
  * [Maxrunswithoutnewtests](#maxrunswithoutnewtests) -yeni bir test yayınlanmadan en fazla art arda çalıştırma sayısı.
  * [Maxrunswithuniquepaths](#maxrunswithuniquepaths) -bir keşif sırasında denenecek benzersiz yürütme yolları olan en fazla çalıştırma sayısı.
  * [Maxexceptions](#maxexceptions) -tüm bulunan yürütme yollarının bir birleşimi için bulunan en fazla özel durum sayısı.
* **Test paketi kod oluşturma ayarları**
  * [Testexcludepathboundsexceılation-](#testexcludepathboundsexceeded) true olduğunda, yol sınırlarının ([maxçağrılarının](#maxcalls), [maxbranches](#maxbranches), [maxstack](#maxstack), [maxconditions](#maxconditions)) herhangi birini aşan yürütme yolları yok sayılır.
  * [Testemissionfilter](#testemissionfilter) -hangi koşullarda IntelliTest 'in testleri yaydığını gösterir.
  * [Testemissionbranchhits](#testemissionbranchhits) -kaç test IntelliTest yayılacağını denetler.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

[Kısıtlama çözücü 'nün](input-generation.md#constraint-solver) , yeni ve farklı bir yürütme yolunun alınmasına neden olacak girişleri hesaplamak için gereken saniye sayısı. Bu, **PexSettingsAttributeBase** 'in ve türetilen türlerin bir seçeneğidir.

IntelliTest 'in bir programın yürütme yollarını inceleyen daha derin, IntelliTest 'in denetim akışından ve veri akışından olduğu daha karmaşık kısıtlama sistemleri olur. Zaman sınırlamaınıza bağlı olarak, bu değeri IntelliTest 'in daha fazla veya daha az zaman alacak şekilde yeni yürütme yolları keşfetmesini sağlamak için ayarlayabilirsiniz.

Genellikle, bir zaman aşımı nedeni, IntelliTest 'in çözüm içermeyen bir kısıtlama sistemine yönelik çözüm bulmaya çalışıyor, ancak bu olguyu bilmez. Bu, zaman aşımı için en yaygın durum olduğundan, bağı artırmak mantıklı olmayabilir.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

[Kısıtlama çözücü 'nün](input-generation.md#constraint-solver) , yeni ve farklı bir yürütme yolunun alınmasına neden olacak girişleri hesaplamak Için gereken megabayt sayısı. Bu, *PexSettingsAttributeBase** ve türetilmiş türlerinin bir seçeneğidir.

Derin IntelliTest bir programın yürütme yollarını araştırır, bu, programın denetim akışından ve veri akışından, IntelliTest tarafından derlemelerin daha karmaşık kısıtlama sistemleri olur. Bilgisayarınızın kullanılabilir belleğine bağlı olarak, bu değeri IntelliTest 'in daha karmaşık kısıtlama sistemlerini eklemesine izin verecek şekilde ayarlayabilirsiniz.

Genellikle, bir zaman aşımı nedeni, IntelliTest 'in çözüm içermeyen bir kısıtlama sistemine yönelik çözüm bulmaya çalışıyor, ancak bu olguyu bilmez. Bu, bellek yetersiz durumunun en yaygın nedeni olduğundan, bu, bağı artırmak mantıklı olmayabilir.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Tek bir yürütme yolu üzerinde alınabilecek dal sayısı üst sınırı.

Bu araştırmayla ilgili yolun arkasındaki mosyon, [giriş oluşturma](input-generation.md)sırasında IntelliTest tarafından araştırıp herhangi bir yürütme yolunun uzunluğunu sınırlandırmasıdır. Özellikle, program sonsuz bir döngüye geçtiğinde IntelliTest 'in yanıt vermemesine engel olur.

Yürütülen ve izlenen kodun her koşullu ve koşulsuz dalı, parametreli testin girdilerine bağlı olmayan dallar da dahil olmak üzere bu sınıra doğru sayılır.

Örneğin, aşağıdaki kod sipariş 100 ' deki dalları kullanır:

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>Maxçağrılarında

Tek bir yürütme yolu sırasında yapılabilecek en fazla çağrı sayısı.

Bu araştırmayla ilgili yolun arkasındaki mosyon, [giriş oluşturma](input-generation.md)sırasında IntelliTest tarafından araştırıp herhangi bir yürütme yolunun uzunluğunu sınırlandırmasıdır. Özellikle, program bir yöntemi yinelemeli olarak sonsuz bir kez çağırırsa IntelliTest 'in yanıt vermemesine engel olur ve bu da IntelliTest 'in kurtarabileceği bir yığın taşmasına neden olabilir.

Yürütülen ve izlenen kodun her çağrısı (doğrudan, dolaylı, sanal, atlamanın) bu sınıra doğru sayılır.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Tek bir yürütme yolu sırasında her zaman, etkin çağrı çerçevelerinin sayısıyla ölçülen en büyük yığın boyutu.

Bu araştırmayla ilgili yolun arkasındaki mosyon, [giriş oluşturma](input-generation.md)sırasında IntelliTest tarafından araştırıp yürütme yolunun yığın boyutunu sınırlandırmasıdır. Özellikle, IntelliTest 'in tüm kullanılabilir yığın alanını kullanmasını engeller ve bu, IntelliTest 'in kurtarabileceği bir yığın taşmasına neden olabilir.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Tek bir yürütme yolu sırasında denetlenecek girişler üzerinde en yüksek koşul sayısı.

Bu araştırmayla ilgili yolun arkasındaki mosyon, [giriş oluşturma](input-generation.md)sırasında IntelliTest tarafından araştırıp herhangi bir yürütme yolunun karmaşıklığını sınırlandırmasıdır. Parametreli test girdilerine bağlı olan her bir koşullu dal, bu sınıra doğru sayılır.

Örneğin, aşağıdaki koddaki her bir yol n + 1 koşul kullanır:

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
## <a name="maxruns"></a>Maxçalıştırmaları

IntelliTest 'in bir test araştırması sırasında deneyeen yüksek çalıştırma sayısı.

Bu araştırmayla ilgili olarak, döngü veya özyineleme içeren herhangi bir kodun sonsuz sayıda yürütme yolu olabilir ve bu nedenle IntelliTest 'in [giriş oluşturma](input-generation.md)sırasında sınırlı olması gerekir.

**Maxçalıştırmaları** ve **Maxrunswithuniquepaths** iki ayarı aşağıdaki gibi ilişkilidir:

* IntelliTest, farklı test girişleri ile en fazla **Maxçalıştırması** olan parametreli test yöntemini çağırır.
* Yürütülen kod belirleyici ise, IntelliTest her seferinde farklı bir yürütme yolu alır. Ancak, bazı koşullarda yürütülen kod, daha önce daha önce alınmış olan bir yürütme yolunu, farklı girişlerle izleyebilir.
* IntelliTest, kaç benzersiz yürütme yolunun bulduğunu sayar; Bu sayı **Maxrunswithuniquepaths** seçeneğiyle sınırlıdır.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Yeni bir test yayınlanmadan en fazla ardışık çalıştırma sayısı.

IntelliTest genellikle kısa bir süre içinde çok sayıda ilginç test girişi bulurken, daha sonra başka bir test girişi bulmayacak ve daha fazla birim testi göstermeyecektir. Bu yapılandırma seçeneği, yeni bir test yaymadan, her ardışık deneme için IntelliTest tarafından gerçekleştirilecek bir bağlı değer koyar. Ulaşıldığında, araştırmayı durduracaktır.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

IntelliTest 'in bir keşif sırasında göz önünde bulundurulması gereken en fazla benzersiz yol sayısı.

Bu araştırmayla ilgili olarak, döngü veya özyineleme içeren herhangi bir kodun sonsuz sayıda yürütme yolu olabilir ve bu nedenle IntelliTest [giriş oluşturma](input-generation.md)sırasında sınırlandırılmalıdır.

**Maxçalıştırmaları** ve **Maxrunswithuniquepaths** iki ayarı aşağıdaki gibi ilişkilidir:

* IntelliTest, farklı test girişleri ile en fazla **Maxçalıştırması** olan parametreli test yöntemini çağırır.
* Yürütülen kod belirleyici ise, IntelliTest her seferinde farklı bir yürütme yolu alır. Ancak, bazı koşullarda yürütülen kod, daha önce daha önce alınmış olan bir yürütme yolunu, farklı girişlerle izleyebilir.
* IntelliTest, kaç benzersiz yürütme yolunun bulduğunu sayar; Bu sayı **Maxrunswithuniquepaths** seçeneğiyle sınırlıdır.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Araştırmadan önce karşılaşılabilecek en fazla özel durum sayısı.

Bu araştırmanın arkasındaki mosyon, birçok hata içeren kodun araştırmasını durdurmaktır. IntelliTest kodda çok fazla hata bulursa, araştırma durdurulur.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

[Maxçağrılarını](#maxcalls), [maxbranches](#maxbranches), [maxstack](#maxstack)ve [maxconditions](#maxconditions) yapılandırılmış yol sınırlarını aşan yürütme yolları yok sayılır.

Bu araştırmayla ilişkili mosyon, (en olası) sonlandırılamayan testler ile uğraşmak. IntelliTest, [Maxçağrılarında](#maxcalls), [maxbranches](#maxbranches), [maxstack](#maxstack)veya [maxconditions](#maxconditions)gibi bir araştırmaya eriştiğinde, testin Sonlandırılmamış bir işlem olmadığı ve daha sonra yığın taşmasına neden olmayacak olduğunu varsayar. Bu tür test çalışmaları diğer test çerçevelerine sorun oluşturabilir. Bu öznitelik, IntelliTest 'in, büyük olasılıkla Sonlandırılmamış süreçler veya yığın taşmasına neden olacak test çalışmaları için test çalışmalarını yaymasını engellemek için bir yol sağlar.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

IntelliTest 'in yayılmaları gereken testlerin türlerini gösterir. Olası değerler şunlardır:

* Her şey için testleri, varsayım ihlalleri dahil olmak üzere **Tüm** her şeyi yayar.
* **Failuresandincreasedbranchhits** (varsayılan)-tüm benzersiz hatalara yönelik testleri ve bir test çalışması, [Testemissionbranchhits](#testemissionbranchhits)tarafından denetlenen şekilde kapsamı arttırır.
* **Failuresanduniquepaths** -tüm hata IntelliTest bulduğu testleri ve ayrıca benzersiz bir yürütme yoluna neden olan her test girişi için testler yayar.
* **Başarısızlıklar** -testleri yalnızca hatalara yönelik olarak yay.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

Geçerli [Testemissionfilter](#testemissionfilter) ayarına bağlı olarak, IntelliTest, daha önce kapsanmayan programdaki bir dalı kapsadıklarında yeni test çalışmalarını yayar.

**Testemissionbranchhits** ayarı, IntelliTest 'in bir kez veya iki kez (**testemissionbranchhits = 2**) veya daha fazlasını ele aldığı bir dalın (**testemissionbranchhits = 1**) kapsanıp kapsamadığını düşünmeyeceğini belirler.

**Testemissionbranchhits = 1** , IntelliTest 'in ulaşabileceği tüm dalları kapsayan çok küçük bir test paketi oluşturacak. Özellikle, bu test paketi, ulaşılan tüm temel blokları ve deyimleri de kapsar.

Bu seçeneğin varsayılan ayarı **Testemissionbranchhits = 2**' dir. Bu, gelecekteki gerileme hatalarını saptamak için daha uygun olan daha açıklayıcı bir test paketi oluşturur.

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.
