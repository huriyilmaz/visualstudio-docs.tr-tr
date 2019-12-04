---
title: Hedef derleme sırası | Microsoft Docs
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee7a3c2530456a4c2b358fcea7507203feeb904b
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777887"
---
# <a name="target-build-order"></a>Hedef derleme sırası

Bir hedefin girişi, başka bir hedefin çıktısına bağımlıysa, hedefler sıralanmalıdır. Bu öznitelikleri, hedeflerin çalıştırıldığı sırayı belirtmek için kullanabilirsiniz:

- `InitialTargets`. Bu `Project` özniteliği, hedefler komut satırında veya `DefaultTargets` özniteliğinde belirtilmiş olsa bile önce çalıştırılacak hedefleri belirtir.

- `DefaultTargets`. Bu `Project` özniteliği, bir hedef açık olarak komut satırında belirtilmemişse hangi hedeflerin çalıştırılacağını belirtir.

- `DependsOnTargets`. Bu `Target` özniteliği, bu hedefin çalıştırılabilmesi için çalıştırılması gereken hedefleri belirtir.

- `BeforeTargets` ve `AfterTargets`. Bu `Target` öznitelikleri, bu hedefin belirtilen hedeflerden önce veya sonra çalışması gerektiğini belirtir (MSBuild 4,0).

Bir hedef, derleme sırasında bir sonraki hedefe bağlı olsa bile, hiçbir şekilde bir derleme sırasında iki kez çalıştırılmaz. Bir hedef çalıştırıldığında, derleme katkısı tamamlanmıştır.

Hedeflerin bir `Condition` özniteliği olabilir. Belirtilen koşul `false`değerlendirilirse, hedef yürütülmez ve derleme üzerinde hiçbir etkisi olmaz. Koşullar hakkında daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).

## <a name="initial-targets"></a>İlk hedefler

[Proje](../msbuild/project-element-msbuild.md) öğesinin `InitialTargets` özniteliği, hedefler komut satırında veya `DefaultTargets` özniteliğinde belirtilmiş olsa bile öncelikle çalıştırılacak hedefleri belirtir. İlk hedefler genellikle hata denetimi için kullanılır.

`InitialTargets` özniteliğinin değeri, noktalı virgülle ayrılmış bir hedef listesi olabilir. Aşağıdaki örnek `Warm` hedefinin çalıştığını ve sonra `Eject` hedefinin çalıştığını belirtir.

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

İçeri aktarılan projelerin kendi `InitialTargets` öznitelikleri olabilir. Tüm başlangıç hedefleri birlikte toplanır ve sırayla çalıştırılır.

Daha fazla bilgi için bkz. [nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="default-targets"></a>Varsayılan hedefler

[Proje](../msbuild/project-element-msbuild.md) öğesinin `DefaultTargets` özniteliği, bir hedef açıkça bir komut satırında belirtilmemişse, hangi hedefin veya hedeflerin derlenmediğini belirtir.

`DefaultTargets` özniteliğinin değeri noktalı virgülle ayrılmış, varsayılan hedeflerin sıralı bir listesi olabilir. Aşağıdaki örnek `Clean` hedefinin çalıştığını ve sonra `Build` hedefinin çalıştığını belirtir.

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Komut satırında **-target** anahtarını kullanarak varsayılan hedefleri geçersiz kılabilirsiniz. Aşağıdaki örnek `Build` hedefinin çalıştığını ve sonra `Report` hedefinin çalıştığını belirtir. Bu şekilde hedefleri belirttiğinizde, varsayılan tüm hedefler yok sayılır.

 `msbuild -target:Build;Report`

Hem ilk hedefler hem de varsayılan hedefler belirtilirse ve hiçbir komut satırı hedefi belirtilmemişse, MSBuild ilk hedefleri çalıştırır ve ardından varsayılan hedefleri çalıştırır.

İçeri aktarılan projelerin kendi `DefaultTargets` öznitelikleri olabilir. Karşılaşılan ilk `DefaultTargets` özniteliği, hangi varsayılan hedeflerin çalıştırılacağını belirler.

Daha fazla bilgi için bkz. [nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="first-target"></a>İlk hedef

İlk hedef, varsayılan hedef veya komut satırı hedefi yoksa, MSBuild, proje dosyasında veya içeri aktarılan proje dosyalarında karşılaştığı ilk hedefi çalıştırır.

## <a name="target-dependencies"></a>Hedef bağımlılıklar

Hedefler, bağımlılık ilişkilerini birbirleriyle tanımlayabilir. `DependsOnTargets` özniteliği bir hedefin diğer hedeflere bağlı olduğunu gösterir. Örneğin,

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

`Serve` hedefinin `Chop` hedefine ve `Cook` hedefine bağlı olduğunu MSBuild 'e söyler. MSBuild `Chop` hedefini çalıştırır ve sonra `Serve` hedefini çalıştırmadan önce `Cook` hedefini çalıştırır.

## <a name="beforetargets-and-aftertargets"></a>BeforeTargets ve AfterTargets

MSBuild 4,0 ' de, `BeforeTargets` ve `AfterTargets` özniteliklerini kullanarak hedef sırasını belirtebilirsiniz.

Aşağıdaki betiği göz önünde bulundurun.

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

`Compile` hedeften sonra çalışan bir ara hedef `Optimize` oluşturmak için, ancak `Link` hedeften önce, `Project` öğesinin herhangi bir yerinden aşağıdaki hedefi ekleyin.

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>Hedef derleme sırasını belirleme

MSBuild, hedef derleme sırasını aşağıdaki gibi belirler:

1. `InitialTargets` hedefler çalıştırılır.

2. Komut satırında **-target** anahtarı tarafından belirtilen hedefler çalıştırılır. Komut satırında hiçbir hedef belirtmezseniz, `DefaultTargets` hedefler çalıştırılır. Hiçbiri yoksa, karşılaşılan ilk hedef çalıştırılır.

3. Hedefin `Condition` özniteliği değerlendirilir. `Condition` özniteliği varsa ve `false`olarak değerlendirilirse, hedef yürütülmez ve derleme üzerinde başka etkiye sahip olmaz.

   `BeforeTargets` veya `AfterTargets` koşullu hedefi listeleyecek diğer hedefler de önceden tanımlanmış sırada yürütülür.

4. Hedef yürütülmeden veya atlanmadan önce, `Condition` özniteliği hedefe uygulanmadığı ve `false`olarak değerlendirilmediği müddetçe `DependsOnTargets` hedefleri çalıştırılır.

   > [!NOTE]
   > Bir hedef, çıkış öğeleri güncel olduğu için yürütülmediği kabul edilir (bkz. [Artımlı derleme](../msbuild/incremental-builds.md)). Bu denetim, hedef içinde görevleri yürütmeden önce yapılır ve hedeflerin yürütülme sırasını etkilemez.

5. Hedef yürütülmeden veya atlanmadan önce, hedefi bir `BeforeTargets` özniteliğinde listeleyen diğer tüm hedefler çalıştırılır.

6. Hedef yürütülmeden önce, `Inputs` özniteliği ve `Outputs` özniteliği karşılaştırılır. MSBuild, herhangi bir çıktı dosyasının ilgili giriş dosyası veya dosyalarına göre güncel olmadığını belirlerse, MSBuild hedefi yürütür. Aksi halde, MSBuild hedefi atlar.

7. Hedef yürütüldükten veya atlandıktan sonra, bunu bir `AfterTargets` özniteliğinde listeleyen diğer tüm hedefler çalıştırılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Hedefler](../msbuild/msbuild-targets.md)
