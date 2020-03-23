---
title: Hedef Yapı Siparişi | Microsoft Dokümanlar
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 607584b4b41bdfde224bdb35d30eec1c6c8a4197
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585463"
---
# <a name="target-build-order"></a>Hedef yapı sırası

Bir hedefe giriş başka bir hedefin çıktısına bağlıysa hedefler sıralanmalıdır. Bu öznitelikleri, hedeflerin çalıştırıldığı sırayı belirtmek için kullanabilirsiniz:

- `InitialTargets`. Bu `Project` öznitelik, komut satırında veya öznitelikte `DefaultTargets` hedefler belirtilmiş olsa bile, ilk çalışacak hedefleri belirtir.

- `DefaultTargets`. Bu `Project` öznitelik, bir hedef komut satırında açıkça belirtilmemişse hangi hedeflerin çalıştırıldığını belirtir.

- `DependsOnTargets`. Bu `Target` öznitelik, bu hedefin çalıştırılaabilmesi için çalışması gereken hedefleri belirtir.

- `BeforeTargets` ve `AfterTargets`. Bu `Target` öznitelikler, bu hedefin belirtilen hedeflerden önce veya sonra çalışması gerektiğini belirtir (MSBuild 4.0).

Bir hedef, yapıdaki sonraki bir hedef buna bağlı olsa bile, yapı sırasında asla iki kez çalıştırılamaz. Bir hedef çalıştırıldıktan sonra, yapıya katkısı tamamlanır.

Hedeflerin bir `Condition` özelliği olabilir. Belirtilen koşul , hedef `false`yürütülmez ve yapı üzerinde hiçbir etkisi yoktur değerlendirilmesi. Koşullar hakkında daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.

## <a name="initial-targets"></a>İlk hedefler

`InitialTargets` [Proje](../msbuild/project-element-msbuild.md) öğesinin özniteliği, komut satırında veya öznitelikte `DefaultTargets` hedefler belirtilmiş olsa bile, ilk çalışacak hedefleri belirtir. İlk hedefler genellikle hata denetimi için kullanılır.

Özniteliğin `InitialTargets` değeri, yarı sütunlu sınırlı, sıralı hedefler listesi olabilir. Aşağıdaki örnekte hedefin `Warm` çalıştığı ve hedefin `Eject` çalıştığı belirtilir.

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Alınan projelerin kendi `InitialTargets` öznitelikleri olabilir. Tüm ilk hedefler bir araya toplanır ve sırayla çalıştırılır.

Daha fazla bilgi için [bkz: İlk olarak hangi hedefin oluşturulabildiğini belirtin.](../msbuild/how-to-specify-which-target-to-build-first.md)

## <a name="default-targets"></a>Varsayılan hedefler

Proje `DefaultTargets` öğesinin [Project](../msbuild/project-element-msbuild.md) özniteliği, bir hedef bir komut satırında açıkça belirtilmemişse hangi hedefin veya hedefin oluşturulamadığını belirtir.

Özniteliğin `DefaultTargets` değeri, varsayılan hedeflerin yarı sütunlu, sıralı bir listesi olabilir. Aşağıdaki örnekte hedefin `Clean` çalıştığı ve hedefin `Build` çalıştığı belirtilir.

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Komut satırındaki **-hedef** anahtarını kullanarak varsayılan hedefleri geçersiz kılabilirsiniz. Aşağıdaki örnekte hedefin `Build` çalıştığı ve hedefin `Report` çalıştığı belirtilir. Hedefleri bu şekilde belirttiğiniz zaman, varsayılan hedefler yoksayılır.

 `msbuild -target:Build;Report`

Hem ilk hedefler hem de varsayılan hedefler belirtilirse ve komut satırı hedefleri belirtilmemişse, MSBuild önce ilk hedefleri çalıştırır ve sonra varsayılan hedefleri çalıştırır.

Alınan projelerin kendi `DefaultTargets` öznitelikleri olabilir. Karşılaşılan `DefaultTargets` ilk öznitelik, hangi varsayılan hedeflerin çalıştırılacağını belirler.

Daha fazla bilgi için [bkz: İlk olarak hangi hedefin oluşturulabildiğini belirtin.](../msbuild/how-to-specify-which-target-to-build-first.md)

## <a name="first-target"></a>İlk hedef

İlk hedef, varsayılan hedefler veya komut satırı hedefleri yoksa, MSBuild proje dosyasında veya içe aktarılan proje dosyalarında karşılaştığı ilk hedefi çalıştırır.

## <a name="target-dependencies"></a>Hedef bağımlılıklar

Hedefler birbirleriyle bağımlılık ilişkilerini açıklayabilir. Öznitelik, `DependsOnTargets` bir hedefin diğer hedeflere bağlı olduğunu gösterir. Örneğin,

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

MSBuild'e `Serve` hedefin `Chop` hedefe ve `Cook` hedefe bağlı olduğunu söyler. MSBuild `Chop` hedefi çalıştırır ve `Cook` hedefi çalıştırmadan `Serve` önce hedefi çalıştırır.

## <a name="beforetargets-and-aftertargets"></a>Önceki Hedefler ve AfterTargets

MSBuild 4.0'da, öznitelikleri `BeforeTargets` ni ve `AfterTargets` özniteliklerini kullanarak hedef sırasını belirtebilirsiniz.

Aşağıdaki komut dosyasını göz önünde bulundurun.

```xml
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="Compile">
        <Message Text="Compiling" />
    </Target>
    <Target Name="Link">
        <Message Text="Linking" />
    </Target>
</Project>
```

Hedeften `Optimize` `Compile` sonra, ancak hedeften `Link` önce çalışan bir ara hedef oluşturmak `Project` için, öğenin herhangi bir yerine aşağıdaki hedefi ekleyin.

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>Hedef yapı sırasını belirleme

MSBuild hedef yapı sırasını aşağıdaki gibi belirler:

1. `InitialTargets`hedefler çalıştırılır.

2. **-hedef** anahtarı ile komut satırında belirtilen hedefler çalıştırılır. Komut satırında hedef belirtmezseniz, `DefaultTargets` hedefler çalıştırılır. İkisi de yoksa, karşılaşılan ilk hedef çalıştırılır.

3. Hedefin `Condition` özniteliği değerlendirilir. `Condition` Öznitelik varsa ve değerlendirirse, `false`hedef yürütülmez ve yapı üzerinde başka bir etkisi yoktur.

   Koşullu hedefi listeleyen `BeforeTargets` veya `AfterTargets` yine de öngörülen sırada yürüten diğer hedefler.

4. Hedef yürütülmeden veya atılmadan önce, `DependsOnTargets` `Condition` öznitelik hedefe uygulanmadığı ve `false`''ye göre değerlendirilmediği sürece, hedefleri çalıştırılır.

   > [!NOTE]
   > Çıktı öğeleri güncel olduğundan yürütülmezse hedef atlanmış olarak kabul edilir [(bkz. artımlı yapı).](../msbuild/incremental-builds.md) Bu denetim, hedefin içindeki görevleri yürütmeden hemen önce yapılır ve hedeflerin yürütme sırasını etkilemez.

5. Hedef yürütülmeden veya atılmadan önce, bir `BeforeTargets` öznitelikteki hedefi listeleyen başka bir hedef çalıştırılır.

6. Hedef yürütülmeden `Inputs` önce, `Outputs` özniteliği ve özniteliği karşılaştırılır. MSBuild, ilgili giriş dosyası veya dosyalarıyla ilgili olarak herhangi bir çıktı dosyasının güncel olmadığını belirlerse, MSBuild hedefi yürütür. Aksi takdirde, MSBuild hedefi atlar.

7. Hedef yürütüldükten veya atlandıktan sonra, hedefin bir öznitelik te listelenebilen başka bir `AfterTargets` hedef çalıştırılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef](../msbuild/msbuild-targets.md)
