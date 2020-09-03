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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89dcb8bddf2c92406ad5eff952d1f4050d7f9262
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593284"
---
# <a name="diagnosing-task-failures"></a>Görev başarısızlıklarını tanılama

`MSB6006` , <xref:Microsoft.Build.Utilities.ToolTask> -türetilmiş bir sınıf, görev daha belirli bir hata günlüğe oturum açmadığından sıfır olmayan çıkış kodu döndüren bir araç işlemi çalıştırdığında yayılır.

## <a name="identifying-the-failing-task"></a>Hatalı görevi tanımlama

Bir görev hatasıyla karşılaştığınızda, ilk adım başarısız olan görevi tanımlamaktır.

Hatanın metni, araç adını (görevin uygulamasının veya yürütülebilir dosyanın adı tarafından sağlanmış bir kolay ad <xref:Microsoft.Build.Utilities.ToolTask.ToolName> ) ve sayısal çıkış kodunu belirtir. Örneğin,

```text
error MSB6006: "custom tool" exited with code 1.
```

Araç adı `custom tool` ve çıkış kodu olur `1` .

### <a name="command-line-builds"></a>Komut satırı derlemeleri

Yapı bir Özet (varsayılan) içerecek şekilde yapılandırıldıysa Özet şöyle görünür:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Bu sonuç, dosyanın 19 `S:\MSB6006_demo\MSB6006_demo.csproj` . satırda, projede adlı hedefte tanımlanan bir görevde oluştuğunu gösterir `InvokeToolTask` `S:\MSB6006_demo\MSB6006_demo.csproj` .

### <a name="in-visual-studio"></a>Visual Studio’da

Aynı bilgiler, ve sütunlarındaki Visual Studio hata listesinde bulunur `Project` `File` `Line` .

## <a name="finding-more-failure-information"></a>Daha fazla hata bilgisi bulma

Bu hata, görev belirli bir hata günlük kaydı gerçekleştirmediği zaman yayınlanır. Bir hata kaydetme hatası genellikle görev, çağırdığı araç tarafından yayılan hata biçimini anlamak için yapılandırılmadığı için.

İyi davranmış araçlar, genellikle bazı bağlamsal veya hata bilgilerini standart çıktısına veya hata akışına yayar ve görevler bu bilgileri varsayılan olarak yakalayıp günlüğe kaydeder. Ek bilgi için hata oluşmadan önce günlük girdilerine bakın. Bu bilgileri korumak için derlemeyi daha yüksek bir günlük düzeyiyle yeniden çalıştırmak gerekebilir.

## <a name="next-steps"></a>Sonraki adımlar

Günlüğe kaydetme sırasında tanımlanan ek bağlam veya hatalar sorunun kök nedenini açığa çıkarır.

Aksi takdirde, başarısız olan göreve giriş olan özellikleri ve öğeleri inceleyerek olası nedenleri daraltmanız gerekebilir.
