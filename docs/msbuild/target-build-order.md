---
title: Hedef Derleme Sırası | Microsoft Docs
description: Bir hedefin girişi başka bir hedefi MSBuild n çıkışına bağlı ise, hedef hedeflerinin hangi sırayla çalıştırılamayacaklarını belirtmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/02/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 7e2f5df6b5700127f6e10b8bb3f5fea758c1c1ca1ed5c86a9d88fa2331ca4dd0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121334048"
---
# <a name="target-build-order"></a>Hedef derleme sırası

Bir hedefe yapılan giriş başka bir hedefin çıkışına bağlı ise hedefler sıralanıyor. Hedeflerin çalıştırıma sırası belirtmek için bu öznitelikleri kullanabilirsiniz:

- `InitialTargets`. Bu öznitelik, hedefler komut satırı veya öznitelikte belirtilmiş olsa bile ilk `Project` olarak çalıştıracak hedefleri `DefaultTargets` belirtir.

- `DefaultTargets`. Bu `Project` öznitelik, bir hedef komut satırı üzerinde açıkça belirtilmezse çalıştıracak hedefleri belirtir.

- `DependsOnTargets`. Bu `Target` öznitelik, bu hedefin çalıştırılamadan önce çalışması gereken hedefleri belirtir.

- `BeforeTargets` ve `AfterTargets` . Bu öznitelikler, bu hedefin belirtilen hedeflerden önce veya sonra çalışması gerektiğini `Target` belirtir (MSBuild 4.0).

Derlemede sonraki bir hedef buna bağlı olsa bile bir hedef hiçbir zaman derleme sırasında iki kez çalıştırılamaz. Bir hedef çalıştırlandıktan sonra, derlemeye olan katkısı tamamlanır.

Hedeflerin bir özniteliği `Condition` olabilir. Belirtilen koşul olarak değerlendirilirse `false` hedef yürütülmez ve derleme üzerinde hiçbir etkisi olmaz. Koşullar hakkında daha fazla bilgi için bkz. [Koşullar.](../msbuild/msbuild-conditions.md)

## <a name="initial-targets"></a>İlk hedefler

Project öğesinin özniteliği, komut satırı veya öznitelikte hedefler belirtilmiş olsa bile ilk `InitialTargets` olarak çalıştıracak hedefleri [](../msbuild/project-element-msbuild.md) `DefaultTargets` belirtir. İlk hedefler genellikle hata denetimi için kullanılır.

Özniteliğin `InitialTargets` değeri noktalı virgülle ayrılmış, sıraılmış bir hedef listesi olabilir. Aşağıdaki örnek, hedefin `Warm` çalıştırı ve ardından hedef çalışır `Eject` olduğunu belirtir.

```xml
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

İçe aktarılan projelerin kendi `InitialTargets` öznitelikleri olabilir. Tüm ilk hedefler birlikte toplanır ve sırayla çalıştırıldı.

Daha fazla bilgi için, [bkz. How to: Specify which target to build first](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="default-targets"></a>Varsayılan hedefler

Project öğesinin özniteliği, bir hedef bir komut satırı içinde açıkça belirtilmezse hangi hedefin veya hedeflerin `DefaultTargets` yerleşik olduğunu belirtir. [](../msbuild/project-element-msbuild.md)

Özniteliğin `DefaultTargets` değeri noktalı virgülle ayrılmış, sıraılmış varsayılan hedefler listesi olabilir. Aşağıdaki örnek, hedefin `Clean` çalıştırı ve ardından hedef çalışır `Build` olduğunu belirtir.

```xml
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
```

Komut satırına **-target** anahtarını kullanarak varsayılan hedefleri geçersiz kılabilirsiniz. Aşağıdaki örnek, hedefin `Build` çalıştırı ve ardından hedef çalışır `Report` olduğunu belirtir. Hedefleri bu şekilde belirttiğinizde varsayılan hedefler yoksayılır.

 `msbuild -target:Build;Report`

Hem ilk hedefler hem de varsayılan hedefler belirtilirse ve hiçbir komut satırı hedefi belirtilmezse, MSBuild önce ilk hedefleri çalıştırır ve ardından varsayılan hedefleri çalıştırır.

İçe aktarılan projelerin kendi `DefaultTargets` öznitelikleri olabilir. Karşılaşılan `DefaultTargets` ilk öznitelik, hangi varsayılan hedeflerin çalıştıracaklarını belirler.

Daha fazla bilgi için, [bkz. How to: Specify which target to build first](../msbuild/how-to-specify-which-target-to-build-first.md).

## <a name="first-target"></a>İlk hedef

İlk hedefler, varsayılan hedefler veya komut satırı hedefleri yoksa, MSBuild proje dosyasında veya içe aktarılan proje dosyalarında karşılaştığı ilk hedefi çalıştırır.

## <a name="target-dependencies"></a>Hedef bağımlılıklar

Hedefler, bağımlılık ilişkilerini açıklar. özniteliği, `DependsOnTargets` bir hedefin diğer hedeflere bağlı olduğunu gösterir. Örneğin,

```xml
<Target Name="Serve" DependsOnTargets="Chop;Cook" />
```

MSBuild hedefin `Serve` hedefe ve hedefe bağlı olduğunu `Chop` `Cook` söyler. MSBuild, hedefi `Chop` çalıştırmadan önce `Cook` hedefi `Serve` çalıştırır.

## <a name="beforetargets-and-aftertargets"></a>BeforeTargets ve AfterTargets

4 MSBuild 4.0'da ve özniteliklerini kullanarak hedef `BeforeTargets` `AfterTargets` sırayı belirtsiniz.

Aşağıdaki betiği göz önünde bulundurarak.

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

Hedeften sonra ancak hedeften önce çalışan bir ara hedef `Optimize` oluşturmak için aşağıdaki hedefi `Compile` `Link` öğesinde herhangi bir yere `Project` ekleyin.

```xml
<Target Name="Optimize"
    AfterTargets="Compile" BeforeTargets="Link">
    <Message Text="Optimizing" />
</Target>
```

## <a name="determine-the-target-build-order"></a>Hedef derleme siparişini belirleme

MSBuild aşağıdaki gibi hedef derleme sırası belirler:

1. `InitialTargets` hedefler çalıştır.

2. **-target** anahtarı tarafından komut satırına belirtilen hedefler çalıştırlanır. Komut satırı üzerinde hedef belirtmezsiniz, `DefaultTargets` hedefler çalıştırabilirsiniz. Hiçbiri yoksa, karşılaşılan ilk hedef çalıştırıldı.

3. `Condition`Hedefin özniteliği değerlendirilir. Özniteliği `Condition` mevcutsa ve olarak `false` değerlendirilirse, hedef yürütülmez ve derleme üzerinde başka bir etkisi yoktur.

   Koşullu hedefi içinde listelene veya `BeforeTargets` yine de belirtilen sırada `AfterTargets` yürüten diğer hedefler.

4. Hedef yürütülmeden veya atlanmadan önce, özniteliği hedefe uygulanmadıkça ve olarak değerlendirilmediği `DependsOnTargets` `Condition` sürece hedefin hedefleri `false` çalıştırıldı.

   > [!NOTE]
   > Çıkış öğeleri güncel olduğundan bir hedef yürütülmezse atlandı olarak kabul edilir (bkz. [artımlı derleme).](../msbuild/incremental-builds.md) Bu denetim, görevlerin hedef içinde yürütülmeden hemen önce yapılır ve hedeflerin yürütülmesini etkilemez.

5. Hedef yürütülmeden veya atlanmadan önce, bir öznitelikte hedefi listelayan diğer `BeforeTargets` herhangi bir hedef çalıştırıldı.

6. Hedef yürütülmeden önce özniteliği `Inputs` ve `Outputs` özniteliği karşılaştırıldı. Bu MSBuild, karşılık gelen giriş dosyasına veya dosyalara göre herhangi bir çıkış dosyasının güncel olmadığını belirlerse, MSBuild hedef yürütülür. Aksi MSBuild hedefi atlar.

7. Hedef yürütülür veya atlandıktan sonra, bir öznitelikte listelene diğer `AfterTargets` tüm hedefler çalıştırıldı.

## <a name="see-also"></a>Ayrıca bkz.

- [Targets](../msbuild/msbuild-targets.md)
