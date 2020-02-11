---
title: Artımlı derlemeler | Microsoft Docs
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
ms.openlocfilehash: 43c739cc24d453ad4129d8cb7cc4bfbebec07aa4
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091827"
---
# <a name="incremental-builds"></a>Artımlı derlemeler

Artımlı derlemeler, en iyileştirilmiş derlemelerdir, böylece ilgili giriş dosyalarına göre güncel çıkış dosyaları olan hedefler yürütülmez. Hedef öğe, hedefin giriş olarak beklediği öğeleri belirten bir `Inputs` özniteliği ve bir `Outputs` özniteliği olabilir. Bu, çıktı olarak hangi öğelerin ürettiği gösterir. MSBuild, bu özniteliklerin değerleri arasında 1 ila 1 eşleme bulmaya çalışır. 1-1 eşleme varsa, MSBuild her giriş öğesinin zaman damgasını karşılık gelen çıkış öğesinin zaman damgasıyla karşılaştırır. 1--1 eşleştirmesi olmayan çıkış dosyaları tüm giriş dosyalarıyla karşılaştırılır. Çıkış dosyası, giriş dosyası veya dosyalarından aynı yaş veya daha yeniyse bir öğe güncel olarak değerlendirilir.

> [!NOTE]
> MSBuild, giriş dosyalarını değerlendirirken, yalnızca geçerli yürütmede listenin içeriği göz önünde bulundurululur. Son derlemeden listedeki değişiklikler otomatik olarak bir hedef güncel değildir.

Tüm çıkış öğeleri güncel ise, MSBuild hedefi atlar. Hedefin bu *artımlı derlemesi* , derleme hızını önemli ölçüde iyileştirebilir. Yalnızca bazı dosyalar güncel ise, MSBuild hedefi yürütür, ancak güncellik öğelerini atlar ve böylece tüm öğeleri güncel hale getirir. Bu işlem *kısmi Artımlı derleme*olarak bilinir.

1--1 eşlemeleri genellikle öğe dönüştürmeleri tarafından üretilir. Daha fazla bilgi için bkz. [dönüşümler](../msbuild/msbuild-transforms.md).

 Aşağıdaki hedefi göz önünde bulundurun.

```xml
<Target Name="Backup" Inputs="@(Compile)"
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">
    <Copy SourceFiles="@(Compile)" DestinationFiles=
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />
</Target>
```

`Compile` öğe türü tarafından temsil edilen dosya kümesi bir yedekleme dizinine kopyalanır. Yedekleme dosyaları *. bak* dosya adı uzantısına sahiptir. `Compile` öğe türü tarafından temsil edilen dosyalar veya buna karşılık gelen yedekleme dosyaları, yedekleme hedefi çalıştırıldıktan sonra silinmez veya değiştirilmez, ardından yedekleme hedefi sonraki derlemelerde atlanır.

## <a name="output-inference"></a>Çıkış çıkarımı

MSBuild, hedefin yürütülüp yürütülmeyeceğini anlamak için bir hedefin `Inputs` ve `Outputs` özniteliklerini karşılaştırır. İdeal olarak, bir artımlı derleme tamamlandıktan sonra var olan dosyalar kümesi, ilişkili hedeflerin yürütülüp yürütülmediği gibi aynı kalacaktır. Görevler tarafından oluşturulan veya değiştirilen özellikler ve öğeler derlemeyi etkileyebildiğinden, bunları etkileyen hedef atlansa bile MSBuild, değerlerini çıkarmalıdır. Bu işlem *Çıkış çıkarımı*olarak bilinir.

Üç durum vardır:

- Hedefte `false`değerlendirilen bir `Condition` özniteliği vardır. Bu durumda, hedef çalıştırılmaz ve derleme üzerinde hiçbir etkisi yoktur.

- Hedefte güncel olmayan çıkışlar vardır ve bunları güncel hale getirmek için çalıştırılır.

- Hedefte güncel olmayan çıkışlar yok ve atlandı. MSBuild hedefi değerlendirir ve hedef çalıştırılmışsınız gibi öğe ve özelliklerde değişiklikler yapar.

Artımlı derlemeyi desteklemek için görevler, herhangi bir `Output` öğesinin `TaskParameter` öznitelik değerinin bir görev giriş parametresine eşit olduğundan emin olmalıdır. İşte bazı örnekler:

```xml
<CreateProperty Value="123">
    <Output PropertyName="Easy" TaskParameter="Value" />
</CreateProperty>
```

Bu kod, hedefin yürütülüp yürütülmediğini veya atlanmadığını "123" değerine sahip kolay özelliğini oluşturur.

MSBuild 3,5 ' den başlayarak, bir hedefteki öğe ve özellik grupları üzerinde çıkış çıkarımı otomatik olarak gerçekleştirilir. `CreateItem` görevler bir hedefte gerekli değildir ve kaçınılmalıdır. Ayrıca, `CreateProperty` görevler yalnızca bir hedefin yürütülüp yürütülmediğini belirlemekte kullanılmalıdır.

MSBuild 3,5 ' den önce [CreateItem](../msbuild/createitem-task.md) görevini kullanabilirsiniz.

## <a name="determine-whether-a-target-has-been-run"></a>Bir hedefin çalıştırılıp çalıştırılmadığını belirleme

Çıkış çıkarımı nedeniyle, hedefin yürütülüp yürütülmediğini belirleyebilmeniz için özellikleri ve öğeleri incelemek üzere bir hedefe `CreateProperty` görevi eklemeniz gerekir. `CreateProperty` görevi hedefe ekleyin ve `TaskParameter` "ValueSetByTask" olan `Output` bir öğe verin.

```xml
<CreateProperty Value="true">
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />
</CreateProperty>
```

Bu kod, Compilera özelliğini oluşturur ve değeri yalnızca hedef yürütülürse `true`verir. Hedef atlandıysa, Compilera oluşturulmaz.

## <a name="see-also"></a>Ayrıca bkz.
- [Hedefler](../msbuild/msbuild-targets.md)
