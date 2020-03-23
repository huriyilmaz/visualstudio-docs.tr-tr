---
title: Görev hatalarını tanılama | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593284"
---
# <a name="diagnosing-task-failures"></a>Görev başarısızlıklarını tanılama

`MSB6006`türemiş bir <xref:Microsoft.Build.Utilities.ToolTask>sınıf, görev daha özel bir hatayı günlüğe kaydetmemişse sıfır olmayan bir çıkış kodu döndüren bir araç işlemi çalıştırdığında yayılır.

## <a name="identifying-the-failing-task"></a>Başarısız görevi tanımlama

Bir görev hatasıyla karşılaştığında, ilk adım başarısız olan görevi tanımlamaktır.

Hata metni, araç adını (görevin <xref:Microsoft.Build.Utilities.ToolTask.ToolName> uygulanması yla sağlanan dostça bir ad veya yürütülebilir adı) ve sayısal çıkış kodunu belirtir. Örneğin,

```text
error MSB6006: "custom tool" exited with code 1.
```

Araç adı `custom tool` ve çıkış kodu `1`.

### <a name="command-line-builds"></a>Komut satırı oluşturur

Yapı bir özet (varsayılan) içerecek şekilde yapılandırıldıysa, özet aşağıdaki gibi görünür:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Bu sonuç, dosyanın `S:\MSB6006_demo\MSB6006_demo.csproj`19 satırında tanımlanan bir görevde oluşan hatanın `InvokeToolTask`, projede `S:\MSB6006_demo\MSB6006_demo.csproj`adlı bir hedefte olduğunu gösterir.

### <a name="in-visual-studio"></a>Visual Studio’da

Aynı bilgiler Visual Studio hata listesinde sütunlarda `Project` `File`mevcuttur `Line`, ve .

## <a name="finding-more-failure-information"></a>Daha fazla hata bilgisi bulma

Görev belirli bir hatayı günlüğe kaydetmediğinde bu hata yayımlanır. Görev, çağırdığı aracın yaydığı hata biçimini anlayacak şekilde yapılandırılmaması nedeniyle genellikle hata günlüğe kaydedilememesidir.

İyi davranışta bulunan araçlar genellikle standart çıktılarına veya hata akışlarına bazı bağlamsal veya hata bilgileri yayar ve görevler varsayılan olarak bu bilgileri yakalar ve günlüğe kaydeder. Ek bilgi için hata oluşmadan önce günlük girişlerine bakın. Bu bilgileri korumak için yapıyı daha yüksek bir günlük düzeyiyle yeniden çalıştırmak gerekebilir.

## <a name="next-steps"></a>Sonraki adımlar

Umarım, günlük tanımlanan ek bağlam veya hatalar sorunun temel nedenini ortaya çıkarır.

Aksi takdirde, başarısız göreve giriş yapan özellikleri ve öğeleri inceleyerek olası nedenleri daraltmanız gerekebilir.
