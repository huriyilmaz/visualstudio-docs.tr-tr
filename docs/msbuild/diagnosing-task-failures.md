---
title: Görev başarısızlıklarını tanılama | Microsoft Docs
ms.date: 09/25/2019
ms.topic: troubleshooting
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b77ea7ce288ead0af3d6a9879cab2216ffd6247d
ms.sourcegitcommit: 628eb202a1153ebfe69c668f966f821b98b34b34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2019
ms.locfileid: "71720800"
---
# <a name="diagnosing-task-failures"></a>Görev başarısızlıklarını tanılama

`MSB6006`, <xref:Microsoft.Build.Utilities.ToolTask>türetilen bir sınıf, görev daha belirli bir hatayla oturum açmadığından sıfır dışı çıkış kodu döndüren bir araç işlemi çalıştırdığında yayılır.

## <a name="identifying-the-failing-task"></a>Hatalı görevi tanımlama

Bir görev hatasıyla karşılaştığınızda, ilk adım başarısız olan görevi tanımlamaktır.

Hatanın metni, araç adını (görevin <xref:Microsoft.Build.Utilities.ToolTask.ToolName> ya da yürütülebilir dosyanın adı tarafından sağlanmış kolay bir ad) ve sayısal çıkış kodunu belirtir. Örneğin,

```text
error MSB6006: "custom tool" exited with code 1.
```

Araç adı `custom tool` ve çıkış kodu `1`.

### <a name="command-line-builds"></a>Komut satırı derlemeleri

Yapı bir Özet (varsayılan) içerecek şekilde yapılandırıldıysa Özet şöyle görünür:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Bu sonuç, proje `S:\MSB6006_demo\MSB6006_demo.csproj``InvokeToolTask`adında bir hedefte, `S:\MSB6006_demo\MSB6006_demo.csproj`dosyanın 19. satırında tanımlanan bir görevde hata oluştuğunu gösterir.

### <a name="in-visual-studio"></a>Visual Studio 'da

Aynı bilgiler, `Project`, `File`ve `Line`sütunlarındaki Visual Studio hata listesinde bulunur.

## <a name="finding-more-failure-information"></a>Daha fazla hata bilgisi bulma

Bu hata, görev belirli bir hata günlük kaydı gerçekleştirmediği zaman yayınlanır. Bir hata kaydetme hatası genellikle görev, çağırdığı araç tarafından yayılan hata biçimini anlamak için yapılandırılmadığı için.

İyi davranmış araçlar, genellikle bazı bağlamsal veya hata bilgilerini standart çıktısına veya hata akışına yayar ve görevler bu bilgileri varsayılan olarak yakalayıp günlüğe kaydeder. Ek bilgi için hata oluşmadan önce günlük girdilerine bakın. Bu bilgileri korumak için derlemeyi daha yüksek bir günlük düzeyiyle yeniden çalıştırmak gerekebilir.

## <a name="next-steps"></a>Sonraki adımlar

Günlüğe kaydetme sırasında tanımlanan ek bağlam veya hatalar sorunun kök nedenini açığa çıkarır.

Aksi takdirde, başarısız olan göreve giriş olan özellikleri ve öğeleri inceleyerek olası nedenleri daraltmanız gerekebilir.
