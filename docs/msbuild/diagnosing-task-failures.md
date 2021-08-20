---
title: Görev hatalarını tanılama | Microsoft Docs
description: Başarısız görevi, araç MSBuild diğer bilgileri belirleyerek görev hatalarını tanılamayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: ab44e4e54c78f36fe4598771ca43847fc692150d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123352"
---
# <a name="diagnosing-task-failures"></a>Görev başarısızlıklarını tanılama

`MSB6006` , türetilen bir sınıf, görev daha belirli bir hata günlüğe daha özel bir hata günlüğe kaydedilirse sıfır olmayan bir çıkış kodu döndüren bir <xref:Microsoft.Build.Utilities.ToolTask> araç işlemi çalıştırdığı zaman yayımlar.

## <a name="identifying-the-failing-task"></a>Başarısız görevi tanımlama

Bir görev hatasıyla karşılaştığınız zaman ilk adım başarısız olan görevi tanımlamaktır.

Hatanın metni, araç adını (görevin uygulaması tarafından sağlanan kolay bir ad veya yürütülebilir dosyanın adı) ve sayısal çıkış <xref:Microsoft.Build.Utilities.ToolTask.ToolName> kodunu belirtir. Örneğin,

```text
error MSB6006: "custom tool" exited with code 1.
```

Araç adı, `custom tool` çıkış kodu ise `1` olur.

### <a name="command-line-builds"></a>Komut satırı derlemeleri

Derleme bir özet içerecek şekilde yapılandırılmışsa (varsayılan), özet şöyle olur:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Bu sonuç, hatanın projesinde adlı hedefte dosyasının 19. `S:\MSB6006_demo\MSB6006_demo.csproj` satırda tanımlanan bir `InvokeToolTask` görevde meydana geldiğine işaret `S:\MSB6006_demo\MSB6006_demo.csproj` ediyor.

### <a name="in-visual-studio"></a>Visual Studio’da

Aynı bilgiler , ve Visual Studio hata listesinde `Project` de `File` `Line` mevcuttur.

## <a name="finding-more-failure-information"></a>Daha fazla hata bilgisi bulma

Bu hata, görev belirli bir hatayı günlüğe kaydedilirken yayımlar. Bir hatayı günlüğe kaydetme hatası genellikle görevin çağırdığı araç tarafından yayılan hata biçimini anlamak için yapılandırılmamış bir durumdur.

İyi davranan araçlar genellikle bazı bağlamsal veya hata bilgilerini standart çıkışlarına veya hata akışına yayır ve görevler bu bilgileri varsayılan olarak yakalar ve günlüğe alır. Ek bilgi için hatanın meydana gelmeden önceki günlük girişlerine bakın. Bu bilgileri korumak için derlemeyi daha yüksek bir günlük düzeyiyle yeniden çalıştırmanız gerekebilir.

## <a name="next-steps"></a>Sonraki adımlar

Umarız günlük kaydında tanımlanan ek bağlam veya hatalar, sorunun kök nedenini ortaya çıkartır.

Yoksa, başarısız göreve giriş olan özellikleri ve öğeleri incelerken olası nedenleri daraltmanız gerekir.
