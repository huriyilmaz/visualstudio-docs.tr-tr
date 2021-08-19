---
title: Artımlı Derlemeler | Microsoft Docs
description: Güncel MSBuild yürütülmez şekilde iyileştirilmiş artımlı derlemeler hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 9535d77469277f7b9133a8ee68950164c308193d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143267"
---
# <a name="incremental-builds"></a>Artımlı derlemeler

Artımlı derlemeler, karşılık gelen giriş dosyalarına göre güncel çıkış dosyalarına sahip hedeflerin yürütülmey için iyileştirilmiş derlemelerdir. Hedef öğenin hem hedefin giriş olarak hangi öğeleri beklediğinizi belirten bir özniteliği ve çıkış olarak hangi öğeleri ürettiğini belirten `Inputs` `Outputs` bir özniteliği olabilir. MSBuild özniteliklerin değerleri arasında 1'e 1 eşleme bulmaya çalışır. 1-1 eşlemesi varsa, MSBuild giriş öğesinin zaman damgasını karşılık gelen çıkış öğesinin zaman damgasıyla karşılaştırıldığında. 1-1 eşlemesi olmayan çıkış dosyaları, tüm giriş dosyalarıyla karşılaştırıldı. Çıkış dosyası, giriş dosyasından veya dosyalardan aynı yaş veya daha yeni ise bir öğe güncel olarak kabul edilir.

> [!NOTE]
> Bu MSBuild dosyaları değerlendirirken, yalnızca geçerli yürütmede listenin içeriği dikkate alınır. Son derlemeden gelen listede yapılan değişiklikler otomatik olarak bir hedefin güncel olmadığını ortaya çıkar.

Tüm çıkış öğeleri güncelse, MSBuild atlar. Hedefin *bu* artımlı derlemesi, derleme hızını önemli ölçüde geliştirabilir. Yalnızca bazı dosyalar güncelse, MSBuild hedefi yürütür, ancak güncel öğeleri atlar ve böylece tüm öğeleri güncel getirir. Bu işlem kısmi artımlı *derleme olarak bilinir.*

1'den 1'e eşlemeler genellikle öğe dönüştürmeleri tarafından üretir. Daha fazla bilgi için bkz. [Dönüşümler.](../msbuild/msbuild-transforms.md)

 Aşağıdaki hedefi göz önünde bulundurarak.

```xml
<Target Name="Backup" Inputs="@(Compile)"
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">
    <Copy SourceFiles="@(Compile)" DestinationFiles=
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />
</Target>
```

Öğe türüyle temsil edilen `Compile` dosya kümesi bir yedekleme dizinine kopyalanır. Yedekleme dosyaları *.bak dosya adı* uzantısına sahip. Öğe türüyle temsil edilen dosyalar veya karşılık gelen yedekleme dosyaları, Yedekleme hedefi çalıştırıldıktan sonra silinmez veya değiştirilmezse, sonraki derlemelerde Yedekleme `Compile` hedefi atlanır.

## <a name="output-inference"></a>Çıkış çıkarı

MSBuild, hedefin `Inputs` `Outputs` yürütülecek olup olmadığını belirlemek için hedefin ve özniteliklerini karşılar. İdeal olarak, artımlı derleme tamamlandıktan sonra mevcut olan dosya kümesi, ilişkili hedeflerin yürütülse de yürütülse de aynı kalması gerekir. Görevler tarafından oluşturulan veya değişen özellikler ve öğeler derlemeyi etkileyene MSBuild onları etkileyen hedef atlanmış olsa bile değerlerini çıkaramaz. Bu işlem çıkış *çıkarı olarak bilinir.*

Üç durum vardır:

- Hedef, olarak `Condition` değerlendirilen bir özniteliğine `false` sahip. Bu durumda hedef çalıştırlanmaz ve derleme üzerinde hiçbir etkisi yoktur.

- Hedef güncel olmayan çıkışlara sahip ve bunları güncel getirmek için çalıştır.

- Hedefte güncel olmayan çıkışlar yoktur ve atlanır. MSBuild, hedefi değerlendirir ve hedef çalıştırıIıyor gibi öğelerde ve özelliklerde değişiklikler yapar.

Artımlı derlemeyi desteklemek için, görevlerin herhangi bir öğenin öznitelik değerinin bir görev `TaskParameter` `Output` giriş parametresine eşit olduğundan emin olması gerekir. İşte bazı örnekler:

```xml
<CreateProperty Value="123">
    <Output PropertyName="Easy" TaskParameter="Value" />
</CreateProperty>
```

Bu kod, hedefin yürütülse de atlansa da atlanmasa da "123" değerine sahip olan Easy özelliğini oluşturur.

3.5 MSBuild başlayarak, çıkış çıkarı bir hedefte öğe ve özellik gruplarında otomatik olarak gerçekleştirilir. `CreateItem` görevleri bir hedefte gerekli değildir ve kaçınılmalıdır. Ayrıca, `CreateProperty` görevler yalnızca bir hedefin yürütülebilir olup olmadığını belirlemek için bir hedefte kullanılmalıdır.

3.5 MSBuild önce [CreateItem görevini kullanabilirsiniz.](../msbuild/createitem-task.md)

## <a name="determine-whether-a-target-has-been-run"></a>Bir hedefin çalıştır olup olmadığını belirleme

Çıkış çıkarı nedeniyle, hedefin yürütülüp yürütül olmadığını belirlemek üzere özellikleri ve öğeleri incelemek için bir hedefe `CreateProperty` görev eklemeniz gerekir. Görevi `CreateProperty` hedefe ekleyin ve `Output` `TaskParameter` "ValueSetByTask" olan bir öğe ekleyin.

```xml
<CreateProperty Value="true">
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />
</CreateProperty>
```

Bu kod CompileRan özelliğini oluşturur ve yalnızca hedef `true` yürütülürse değerini verir. Hedef atlanırsa CompileRan oluşturulmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Targets](../msbuild/msbuild-targets.md)
