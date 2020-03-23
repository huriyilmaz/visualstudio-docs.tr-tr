---
title: Artımlı Yapılar | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7283d67710a3b5b319b2d25a1c5d6535fed83b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633726"
---
# <a name="incremental-builds"></a>Artımlı yapılar

Artımlı yapılar, ilgili giriş dosyalarıyla ilgili güncel çıktı dosyalarına sahip hedeflerin yürütülmemesi için en iyi duruma getirilmiş yapılardır. Hedef öğe, hem `Inputs` hedefin girdi olarak beklediği öğeleri gösteren bir özniteliğe hem de çıktı olarak hangi öğeleri ürettiğini gösteren bir `Outputs` öznitelike sahip olabilir. MSBuild, bu özniteliklerin değerleri arasında 1'e 1 eşleme bulmaya çalışır. 1'e 1 eşleme varsa, MSBuild her giriş öğesinin zaman damgasını karşılık gelen çıktı öğesinin zaman damgası ile karşılaştırır. 1'e 1 eşleme olmayan çıktı dosyaları tüm giriş dosyalarıyla karşılaştırılır. Bir öğe, çıktı dosyası giriş dosyası veya dosyalarından aynı yaşta veya daha yeniyse güncel olarak kabul edilir.

> [!NOTE]
> MSBuild giriş dosyalarını değerlendirdiğinde, yalnızca geçerli yürütmedeki listenin içeriği dikkate alınır. Son yapıdaki listedeki değişiklikler, hedefi otomatik olarak güncel yapmaz.

Tüm çıktı öğeleri güncelse, MSBuild hedefi atlar. Hedefin bu *artımlı yapı* önemli ölçüde yapı hızını artırabilir. Yalnızca bazı dosyalar güncelse, MSBuild hedefi yürütür, ancak güncel öğeleri atlar ve bu nedenle tüm öğeleri güncel getirir. Bu işlem kısmi *artımlı yapı*olarak bilinir.

1'e 1 eşlemeler genellikle madde dönüşümleri tarafından üretilir. Daha fazla bilgi için [Transforms'a](../msbuild/msbuild-transforms.md)bakın.

 Aşağıdaki hedefi göz önünde bulundurun.

```xml
<Target Name="Backup" Inputs="@(Compile)"
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">
    <Copy SourceFiles="@(Compile)" DestinationFiles=
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />
</Target>
```

`Compile` Madde türü tarafından temsil edilen dosya kümesi bir yedekleme dizinine kopyalanır. Yedekleme dosyalarında *.bak* dosya adı uzantısı vardır. `Compile` Öğe türü veya ilgili yedekleme dosyaları tarafından temsil edilen dosyalar, Yedekleme hedefi çalıştırıldıktan sonra silinmezse veya değiştirilmezse, sonraki yapılarda Yedek hedef atlanır.

## <a name="output-inference"></a>Çıktı çıkarımı

MSBuild, hedefin yürütülmesi gerekip gerekmediğini belirlemek için hedefin özniteliklerini `Inputs` ve `Outputs` özniteliklerini karşılaştırır. İdeal olarak, artımlı bir yapı tamamlandıktan sonra var olan dosya kümesi, ilişkili hedefler yürütülüp yürütülmediği ne kadar aynı kalır. Görevler tarafından oluşturulan veya değiştirilen özellikler ve öğeler yapıyı etkileyebileceğinden, MSBuild'in onları etkileyen hedef atlansa bile değerlerini çıkarması gerekir. Bu işlem *çıktı çıkarımı*olarak bilinir.

Üç durum vardır:

- Hedef, `Condition` `false`''ye göre değerlendirilen bir özniteliğe sahiptir. Bu durumda, hedef çalıştırılmıyor ve yapı üzerinde hiçbir etkisi yoktur.

- Hedefin güncel olmayan çıktıları vardır ve bunları güncel hale getirmek için çalıştırılır.

- Hedefin güncel olmayan çıktıları yoktur ve atlanır. MSBuild hedefi değerlendirir ve hedef çalıştırılmış gibi öğelerde ve özelliklerde değişiklikler yapar.

Artımlı derlemeyi desteklemek için, görevlerin herhangi `TaskParameter` bir `Output` öğenin öznitelik değerinin görev giriş parametresine eşit olduğundan emin olması gerekir. İşte bazı örnekler:

```xml
<CreateProperty Value="123">
    <Output PropertyName="Easy" TaskParameter="Value" />
</CreateProperty>
```

Bu kod, hedefin yürütülüp yürütülmediği veya atlansa da "123" değerine sahip Kolay özelliği oluşturur.

MSBuild 3.5'ten başlayarak, çıktı çıkarımı bir hedefteki madde ve özellik gruplarında otomatik olarak gerçekleştirilir. `CreateItem`görevler bir hedef gerekli değildir ve kaçınılmalıdır. Ayrıca, `CreateProperty` görevler yalnızca bir hedefin yürütülüp yürütülmediğini belirlemek için bir hedefte kullanılmalıdır.

MSBuild 3.5'ten önce [CreateItem](../msbuild/createitem-task.md) görevini kullanabilirsiniz.

## <a name="determine-whether-a-target-has-been-run"></a>Hedefin çalıştırılıp çalıştırılmadığını belirleme

Çıktı çıkarım nedeniyle, hedefin yürütülüp yürütülmediğini belirlemek için özellikleri ve öğeleri incelemek için hedefe bir `CreateProperty` görev eklemeniz gerekir. `CreateProperty` Görevi hedefe ekleyin ve "ValueSetByTask" olan `Output` `TaskParameter` bir öğe verin.

```xml
<CreateProperty Value="true">
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />
</CreateProperty>
```

Bu kod DereRan özelliğini oluşturur ve `true`yalnızca hedef yürütülürse, değeri verir. Hedef atlanırsa, CompileRan oluşturulmaz.

## <a name="see-also"></a>Ayrıca bkz.

- [Hedef](../msbuild/msbuild-targets.md)
