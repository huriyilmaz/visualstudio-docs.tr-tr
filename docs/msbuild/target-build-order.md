---
title: Hedef derleme sırası | Microsoft Docs
description: Bir hedefin girişi başka bir hedefin çıktısına bağımlıysa, MSBuild hedeflerinin çalıştırıldığı sırayı belirtmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 873f669890e84281f73a96fa1739d267c10e83a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966142"
---
# <a name="target-build-order"></a>Hedef derleme sırası

Bir hedefin girişi, başka bir hedefin çıktısına bağımlıysa, hedefler sıralanmalıdır. Bu öznitelikleri, hedeflerin çalıştırıldığı sırayı belirtmek için kullanabilirsiniz:

- `InitialTargets`. Bu `Project` öznitelik, hedefler komut satırında veya özniteliğinde belirtilmiş olsa bile ilk olarak çalışacak hedefleri belirtir `DefaultTargets` .

- `DefaultTargets`. Bu `Project` öznitelik, bir hedef açık olarak komut satırında belirtilmemişse hangi hedeflerin çalıştırılacağını belirtir.

- `DependsOnTargets`. Bu `Target` öznitelik, bu hedefin çalıştırılabilmesi için çalıştırılması gereken hedefleri belirtir.

- `BeforeTargets` ve `AfterTargets` . Bu `Target` öznitelikler, bu hedefin belirtilen hedeflerden önce veya sonra çalışması gerektiğini belirtir (MSBuild 4,0).

Bir hedef, derleme sırasında bir sonraki hedefe bağlı olsa bile, hiçbir şekilde bir derleme sırasında iki kez çalıştırılmaz. Bir hedef çalıştırıldığında, derleme katkısı tamamlanmıştır.

Hedeflerin bir özniteliği olabilir `Condition` . Belirtilen koşul olarak değerlendirilirse `false` , hedef yürütülmez ve derleme üzerinde hiçbir etkisi olmaz. Koşullar hakkında daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).

## <a name="initial-targets"></a>İlk hedefler

`InitialTargets` [Proje](../msbuild/project-element-msbuild.md) öğesinin özniteliği, hedefler komut satırında veya özniteliğinde belirtilmiş olsa bile öncelikle çalıştırılacak hedefleri belirtir `DefaultTargets` . İlk hedefler genellikle hata denetimi için kullanılır.

Özniteliğin değeri, `InitialTargets` noktalı virgülle ayrılmış bir hedef listesi olabilir. Aşağıdaki örnek, `Warm` hedefin çalıştığını ve ardından `Eject` hedefin çalıştığını belirtir.

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

İçeri aktarılan projelerin kendi öznitelikleri olabilir `InitialTargets` . Tüm başlangıç hedefleri birlikte toplanır ve sırayla çalıştırılır.

Daha fazla bilgi için bkz. [nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="default-targets"></a>Varsayılan hedefler

`DefaultTargets` [Proje](../msbuild/project-element-msbuild.md) öğesinin özniteliği, bir hedef açıkça bir komut satırında belirtilmemişse hangi hedefin veya hedeflerin derlenmediğini belirtir.

Özniteliğin değeri, `DefaultTargets` noktalı virgülle ayrılmış, varsayılan hedeflerin sıralı bir listesi olabilir. Aşağıdaki örnek, `Clean` hedefin çalıştığını ve ardından `Build` hedefin çalıştığını belirtir.

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Komut satırında **-target** anahtarını kullanarak varsayılan hedefleri geçersiz kılabilirsiniz. Aşağıdaki örnek, `Build` hedefin çalıştığını ve ardından `Report` hedefin çalıştığını belirtir. Bu şekilde hedefleri belirttiğinizde, varsayılan tüm hedefler yok sayılır.

 `msbuild -target:Build;Report`

Hem ilk hedefler hem de varsayılan hedefler belirtilirse ve hiçbir komut satırı hedefi belirtilmemişse, MSBuild ilk hedefleri çalıştırır ve ardından varsayılan hedefleri çalıştırır.

İçeri aktarılan projelerin kendi öznitelikleri olabilir `DefaultTargets` . Karşılaşılan ilk `DefaultTargets` öznitelik, hangi varsayılan hedeflerin çalıştırılacağını belirler.

Daha fazla bilgi için bkz. [nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="first-target"></a>İlk hedef

İlk hedef, varsayılan hedef veya komut satırı hedefi yoksa, MSBuild, proje dosyasında veya içeri aktarılan proje dosyalarında karşılaştığı ilk hedefi çalıştırır.

## <a name="target-dependencies"></a>Hedef bağımlılıklar

Hedefler, bağımlılık ilişkilerini birbirleriyle tanımlayabilir. `DependsOnTargets`Özniteliği bir hedefin diğer hedeflere bağlı olduğunu gösterir. Örneğin,

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

, hedefin hedefe `Serve` ve hedefe bağlı olduğunu MSBuild 'e söyler `Chop` `Cook` . MSBuild hedefi çalıştırır `Chop` ve hedefi `Cook` çalıştırmadan önce hedefi çalıştırır `Serve` .

## <a name="beforetargets-and-aftertargets"></a>BeforeTargets ve AfterTargets

MSBuild 4,0 ' de, ve özniteliklerini kullanarak hedef sırasını belirtebilirsiniz `BeforeTargets` `AfterTargets` .

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

Hedeften sonra çalışan bir ara hedef oluşturmak için, `Optimize` `Compile` hedeften önce, `Link` aşağıdaki hedefi öğesinde bir yere ekleyin `Project` .

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

3. `Condition`Hedefin özniteliği değerlendirilir. `Condition`Öznitelik varsa ve olarak değerlendirilirse `false` , hedef yürütülmez ve derleme üzerinde başka etkiye sahip olmaz.

   Koşullu hedefi ' de listeleyecek `BeforeTargets` veya `AfterTargets` hala tanımlanmış sırada yürütülen diğer hedefler.

4. Hedef yürütülmeden veya atlanmadan önce, `DependsOnTargets` `Condition` özniteliği hedefe uygulanmadığından ve olarak değerlendirilmediği takdirde, hedefleri çalıştırılır `false` .

   > [!NOTE]
   > Bir hedef, çıkış öğeleri güncel olduğu için yürütülmediği kabul edilir (bkz. [Artımlı derleme](../msbuild/incremental-builds.md)). Bu denetim, hedef içinde görevleri yürütmeden önce yapılır ve hedeflerin yürütülme sırasını etkilemez.

5. Hedef yürütülmeden veya atlanmadan önce, bir öznitelikte hedefi listeleyen diğer tüm hedefler `BeforeTargets` çalıştırılır.

6. Hedef yürütülmeden önce `Inputs` özniteliği ve `Outputs` özniteliği karşılaştırılır. MSBuild, herhangi bir çıktı dosyasının ilgili giriş dosyası veya dosyalarına göre güncel olmadığını belirlerse, MSBuild hedefi yürütür. Aksi halde, MSBuild hedefi atlar.

7. Hedef yürütüldükten veya atlandıktan sonra, bir özniteliğinde onu listeleyen diğer tüm hedefler `AfterTargets` çalıştırılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Targets](../msbuild/msbuild-targets.md)
