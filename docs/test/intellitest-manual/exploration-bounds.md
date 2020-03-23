---
title: Keşif sınırları | Microsoft IntelliTest Geliştirici Test Aracı
ms.date: 05/02/2017
ms.topic: reference
helpviewer_keywords:
- IntelliTest, Exploration bounds
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 2a57d79fb64675f90edf50e6a0d7d50b8a3c6fd7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302639"
---
# <a name="exploration-bounds"></a>Keşif sınırları

**PexSettingsAttributeBase** öznitelikleri olarak ayarlar sınırları için soyut temel sınıftır. IntelliTest'teki ayarlara genel bakış için Ayarlar Şelalesi'ne bakın. [Settings Waterfall](settings-waterfall.md)

Bunun adlandırılmış özelliklerini ve türetilmiş özniteliklerini kullanarak ayarları değiştirebilirsiniz:

```csharp
[PexClass(MaxRuns = 10)]
public partial class FooTest {...}
```

* **Sınır çözme sınırları**
  * [MaxConstraintSolverTime](#maxconstraintsolvertime) - [Kısıtlama çözücünün](input-generation.md#constraint-solver) yeni ve farklı bir yürütme yolunun izlenmesine neden olacak girişleri keşfetmesi gereken saniye sayısı.
  * [MaxConstraintSolverMemory](#maxconstraintsolvermemory) - Megabaytboyutu kısıtlama [çözücü](input-generation.md#constraint-solver) girişleri keşfetmek için kullanabileceğiniz.
* **Keşif Yolu Sınırları**
  * [MaxBranches](#maxbranches) - Tek bir yürütme yolu boyunca alınabilecek en fazla dal sayısı.
  * [MaxCalls](#maxcalls) - Tek bir yürütme yolu sırasında yapılabilecek maksimum arama sayısı.
  * [MaxStack](#maxstack) - etkin çağrı çerçevelerinin sayısı olarak ölçülen tek bir yürütme yolu sırasında herhangi bir zamanda yığının maksimum boyutu.
  * [MaxConditions](#maxconditions) - Tek bir yürütme yolu sırasında denetlenen girişler üzerinde maksimum koşul sayısı.
* **Keşif Sınırları**
  * [MaxRuns](#maxruns) - Bir keşif sırasında denenecek maksimum çalıştırma sayısı.
  * [MaxRunsWithoutNewTests](#maxrunswithoutnewtests) - Yeni bir test yayımlanmadan üst üste maksimum sayıda çalıştırın.
  * [MaxRunsWithUniquePaths](#maxrunswithuniquepaths) - Bir keşif sırasında denenecek benzersiz yürütme yolları ile çalışan maksimum sayıda.
  * [MaxExceptions](#maxexceptions) - Keşfedilen tüm yürütme yollarının bir birleşimi için bulunabilecek en fazla özel durum sayısı.
* **Test Paketi Kod Oluşturma Ayarları**
  * [TestExcludePathBoundsExceeded](#testexcludepathboundsexceeded) - Doğru olduğunda, yol sınırları[(MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), [MaxConditions](#maxconditions)) herhangi bir aşan yürütme yolları yoksayılır.
  * [TestEmissionFilter](#testemissionfilter) - IntelliTest'in hangi koşullar altında test yaramagerektiğini gösterir.
  * [TestEmissionBranchHits](#testemissionbranchhits) - IntelliTest yayılacak kaç test kontrol eder.

<a name="maxconstraintsolvertime"></a>
## <a name="maxconstraintsolvertime"></a>MaxConstraintSolverTime

[Kısıtlama çözücünün,](input-generation.md#constraint-solver) yeni ve farklı bir yürütme yolunun alınmasına neden olacak girişleri hesaplaması gereken saniye sayısı. Bu, **PexSettingsAttributeBase** ve türetilen türlerinin bir seçenektir.

IntelliTest bir programın yürütme yollarını inceler daha derin, daha karmaşık kısıtlama sistemleri IntelliTest denetim akışı ve programın veri akışı oluşturur olur. Zaman sınırlamanıza bağlı olarak, Bu değeri IntelliTest'in yeni yürütme yollarını keşfetmeye az ya da çok zaman ayırmasına izin verecek şekilde ayarlayabilirsiniz.

Genellikle, bir zaman alabilen nedeni, IntelliTest'in çözümü olmayan bir kısıtlama sistemi için bir çözüm bulmaya çalışıyor olmasıdır, ancak bu gerçeğin farkında değildir. Bu bir zaman alabildiği için en yaygın durum olduğundan, sınırı artırmak mantıklı olmayabilir.

<a name="maxconstraintsolvermemory"></a>
## <a name="maxconstraintsolvermemory"></a>MaxConstraintSolverMemory

[Kısıtlama çözücünün,](input-generation.md#constraint-solver) yeni ve farklı bir yürütme yolunun alınmasına neden olacak girişleri hesaplamak zorunda olduğu Megabayt sayısı. Bu *PexSettingsAttributeBase** ve türetilen türleri bir seçenektir.

Daha derin IntelliTest bir programın yürütme yollarını araştırıyor, daha karmaşık kısıtlama sistemleri IntelliTest denetim akışı ve programın veri akışı oluşturur. Bilgisayarınızın kullanılabilir belleğinin bağlı olarak, IntelliTest'in daha karmaşık kısıtlama sistemleriyle başa çayına sahip olmasını sağlayacak şekilde bu değeri ayarlayabilirsiniz.

Genellikle, bir zaman alabilen nedeni, IntelliTest'in çözümü olmayan bir kısıtlama sistemi için bir çözüm bulmaya çalışıyor olmasıdır, ancak bu gerçeğin farkında değildir. Bu, bellek dışı bir durumun en yaygın nedeni olduğundan, sınırı artırmak mantıklı olmayabilir.

<a name="maxbranches"></a>
## <a name="maxbranches"></a>MaxBranches

Tek bir yürütme yolu boyunca alınabilecek en fazla dal sayısı.

Bu keşif sınırının arkasındaki motivasyon, IntelliTest'in [giriş üretimi](input-generation.md)sırasında keşfettiği herhangi bir yürütme yolunun uzunluğunu sınırlamaktır. Özellikle, program sonsuz bir döngüye girerse IntelliTest'in yanıt vermesini önler.

Yürütülen ve izlenen kodun koşullu ve koşulsuz dalı, parametreli testin girişlerine bağlı olmayan dallar da dahil olmak üzere bu sınıra doğru sayılır.

Örneğin, aşağıdaki kod 100 siparişdalları tüketir:

```csharp
for (int i=0; i<100; i++) { }
```

<a name="maxcalls"></a>
## <a name="maxcalls"></a>MaxCalls

Tek bir yürütme yolu sırasında yapılabilecek en fazla arama sayısı.

Bu keşif sınırının arkasındaki motivasyon, IntelliTest'in [giriş üretimi](input-generation.md)sırasında keşfettiği herhangi bir yürütme yolunun uzunluğunu sınırlamaktır. Özellikle, program bir yöntemi özyinelemeli olarak sonsuz sayıda çağırırsa IntelliTest'in yanıt vermemesini önler ve bu da IntelliTest'in kurtaramadığı bir yığın taşmasına neden olur.

Yürütülen ve izlenen kodun her çağrısı (doğrudan, dolaylı, sanal, atlama) bu sınıra doğru sayılır.

<a name="maxstack"></a>
## <a name="maxstack"></a>MaxStack

Etkin çağrı çerçevelerinin sayısıyla ölçülen tek bir yürütme yolu sırasında yığının herhangi bir zamanda ki maksimum boyutu.

Bu keşif sınırının arkasındaki motivasyon, IntelliTest'in [giriş üretimi](input-generation.md)sırasında keşfettiği herhangi bir yürütme yolunun yığınının boyutunu sınırlamaktır. Özellikle, IntelliTest'in kullanılabilir tüm yığın alanını kullanmasını engeller, bu da IntelliTest'in kurtaramayacağı bir yığın taşmasına neden olur.

<a name="maxconditions"></a>
## <a name="maxconditions"></a>MaxConditions

Tek bir yürütme yolu sırasında denetlenen girişler üzerindeki maksimum koşul sayısı.

Bu keşif sınırının arkasındaki motivasyon, IntelliTest'in [giriş üretimi](input-generation.md)sırasında keşfettiği herhangi bir yürütme yolunun karmaşıklığını sınırlamaktır. Parametreli testin girişlerine bağlı her koşullu dal bu sınıra doğru sayılır.

Örneğin, aşağıdaki koddaki her yol n+1 koşullarını tüketir:

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

IntelliTest'in bir testin keşfi sırasında deneyeceği maksimum sayıda çalıştırma.

Bu keşif bağlama arkasındaki motivasyon döngüler veya özyineleme içeren herhangi bir kod yürütme yolları sonsuz sayıda olabilir, ve böylece IntelliTest [giriş oluşturma](input-generation.md)sırasında sınırlı olması gerekir .

**MaxRuns** ve **MaxRunsWithUniquePaths** iki ayar aşağıdaki gibi ilişkilidir:

* IntelliTest, farklı test girişleri ile **MaxRuns** saatlerine kadar parametreli bir test yöntemi çağırır.
* Çalıştırılan kod deterministic ise, IntelliTest her seferinde farklı bir yürütme yolu alır. Ancak, bazı koşullar altında yürütme kodu, farklı girişleri ile, daha önce almış olduğu bir yürütme yolu izleyebilir.
* IntelliTest, kaç benzersiz yürütme yolu bulduğunu sayar; Bu sayı **MaxRunsWithUniquePaths** seçeneği ile sınırlıdır.

<a name="maxrunswithoutnewtests"></a>
## <a name="maxrunswithoutnewtests"></a>MaxRunsWithoutNewTests

Yeni bir test yayımlanmadan en fazla ardışık çalıştırma sayısı.

IntelliTest genellikle kısa bir süre içinde birçok ilginç test girişleri bulabilirsiniz iken, bir süre sonra daha fazla yeni test girişleri bulamaz ve daha fazla birim testleri yatacak. Bu yapılandırma seçeneği, IntelliTest'in yeni bir test yaymadan gerçekleştirebileceği ardışık deneme sayısına bir sınır koyar. Ulaşıldığında, keşfi durduracak.

<a name="maxrunswithuniquepaths"></a>
## <a name="maxrunswithuniquepaths"></a>MaxRunsWithUniquePaths

IntelliTest'in bir keşif sırasında göz önünde bulunduracağı en fazla benzersiz yol sayısı.

Bu keşif bağlama arkasındaki motivasyon döngüler veya özyineleme içeren herhangi bir kod yürütme yolları sonsuz sayıda olabilir, ve bu nedenle IntelliTest [giriş oluşturma](input-generation.md)sırasında sınırlı olmalıdır.

**MaxRuns** ve **MaxRunsWithUniquePaths** iki ayar aşağıdaki gibi ilişkilidir:

* IntelliTest, farklı test girişleri ile **MaxRuns** saatlerine kadar parametreli bir test yöntemi çağırır.
* Çalıştırılan kod deterministic ise, IntelliTest her seferinde farklı bir yürütme yolu alır. Ancak, bazı koşullar altında yürütme kodu, farklı girişleri ile, daha önce almış olduğu bir yürütme yolu izleyebilir.
* IntelliTest, kaç benzersiz yürütme yolu bulduğunu sayar; Bu sayı **MaxRunsWithUniquePaths** seçeneği ile sınırlıdır.

<a name="maxexceptions"></a>
## <a name="maxexceptions"></a>MaxExceptions

Keşif durdurulmadan önce karşılaşılabilen en fazla istisna sayısı.

Bu keşif sınırının arkasındaki motivasyon, birçok hata içeren kodun keşfini durdurmaktır. IntelliTest kodda çok fazla hata bulursa, arama durdurulur.

<a name="testexcludepathboundsexceeded"></a>
## <a name="testexcludepathboundsexceeded"></a>TestExcludePathBoundsExceeded

Yapılandırılan yolu aşan yürütme yolları [MaxCalls,](#maxcalls) [MaxBranches](#maxbranches), [MaxStack](#maxstack)ve [MaxConditions](#maxconditions) sınırları yoksayılır.

Bu keşif bağlı arkasındaki motivasyon (büyük olasılıkla) sonlandırıcı olmayan testler ile başa çıkmaktır. IntelliTest [MaxCalls](#maxcalls), [MaxBranches](#maxbranches), [MaxStack](#maxstack), veya [MaxConditions](#maxconditions)gibi bir arama bağlı ulaştığında , bu test olmayan bir sonlandırıcı işlem olmayacağını varsayar ve daha sonra bir yığın taşması neden olmaz. Bu tür test örnekleri diğer test çerçeveleri için sorun yaratabilir ve bu özellik, IntelliTest'in bir yığın taşmasına neden olacak sonlandırmama işlemleri veya test çalışmaları için test çalışmaları yaymasını önlemenin bir yolunu sağlar.

<a name="testemissionfilter"></a>
## <a name="testemissionfilter"></a>TestEmissionFilter

IntelliTest'in yakılması gereken test türlerini gösterir. Olası değerler şunlardır:

* **Tüm** - Varsayım ihlalleri de dahil olmak üzere her şey için testler yontun.
* **FailuresAndIncreasedBranchHits** (varsayılan) - Tüm benzersiz hatalar için testler yamit ve ne zaman bir test çalışması [TestEmissionBranchHits](#testemissionbranchhits)tarafından kontrol olarak kapsama artar .
* **FailuresAndUniquePaths** - IntelliTest bulduğu tüm hatalar için testleri ve benzersiz bir yürütme yolu neden olan her test girişi için de.
* **Hatalar** - Yalnızca hatalar için testleri yaslar.

<a name="testemissionbranchhits"></a>
## <a name="testemissionbranchhits"></a>TestEmissionBranchHits

Mevcut [TestEmissionFilter](#testemissionfilter) ayarına bağlı olarak, IntelliTest, programda daha önce kapsanmayan bir dalı kapsadığında yeni test çalışmaları yayır.

**TestEmissionBranchHits** ayarı, IntelliTest'in bir dalı **(TestEmissionBranchHits=1)** kapsanıp kapsanmadığını göz önünde bulundurmalı mı, bir veya iki kez **(TestEmissionBranchHits=2)** vb. bir test le kapsanıp kapsanmadığını belirler.

**TestEmissionBranchHits=1,** IntelliTest'in ulaşabileceği tüm dalları kapsayacak çok küçük bir test paketi üretecektir. Özellikle, bu test paketi de ulaştığı tüm temel blokları ve ifadeleri kapsayacak.

Bu seçenek için varsayılan **TestEmissionBranchHits =2**, aynı zamanda daha iyi gelecekteki regresyon hataları algılamak için uygundur daha anlamlı bir test paketi oluşturur.

## <a name="got-feedback"></a>Geri bildirimde mi bulunmak istiyorsunuz?

Fikirlerinizi ve özellik isteklerinizi [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)’na gönderin.
