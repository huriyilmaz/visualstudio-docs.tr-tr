---
title: DA0026 - Aşırı çekirdek CPU süresi işleme | Microsoft Docs
description: Çekirdek modunda yürütülen CPU süresi oranı, kullanıcı modunda harcanan süre miktarını aştı.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2c0c15ef033b6e27dd047992e3c50cdbb25cf53a14e1bf6092f527ee2a298da1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396727"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Aşırı çekirdek CPU süresi işlemesi

|Öğe|Değer|
|-|-|
|Kural Kimliği|Todo|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemi|Örnekleme|
|İleti|Çekirdek modu CPU süresi görece yüksek miktarda ölçülür. SysCall örneklemesi etkinken kaynağı araştırmayı göz önünde bulundurarak.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 10 örnek toplayan bu kuralı tetiklemeniz gerekir.

## <a name="cause"></a>Nedeni
 Çekirdek modunda yürütülen CPU süresi oranı, kullanıcı modunda harcanan süre miktarını aştı. Yüksek çekirdek modu yürütme zamanlarının nedenini belirlemek için profil oluşturmayı ve sistem çağrılarının (syscalls) sayısını örneklemeyi göz önünde bulundurabilirsiniz.

## <a name="rule-description"></a>Kural açıklaması
 Uygulamanın çekirdek modu yürütmesinde harcadığı sürenin nispeten yüksek olması daha fazla araştırmayı gerektirebilir. Kullanıcı modu uygulaması, iş parçacığı veya işlem eşitleme temellerini beklemek veya sistem çağrıları yapmak için I/O işlemlerini gerçekleştirmek üzere çekirdek moduna geçer. Sistem çağrılarını temel alarak örnek çağrı yığınları toplama seçeneğini tercih ederseniz uygulamanın ne tür sistem çağrıları ve bunlardan sorumlu olan işlevleri araştırabilirsiniz.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Uygulamanıza yapılan sistem çağrılarının ne tür olduğunu araştırmak için profili yeniden çalıştırın ve sistem çağrılarını temel alan örnekler toplama seçeneğini belirleyin. Daha [fazla bilgi için bkz.](../profiling/how-to-choose-sampling-events.md) IDE içinde profil oluşturma araçlarını çalıştırıyorsanız Örnekleme Olayları seçme. Profil oluşturma araçlarını komut satırıyla çalıştırıyorsanız,  komut satırı araçları başvurusunda [VSPerfCmd](../profiling/vsperfcmd.md) makalesi örnek aralık seçenekleri bölümüne Profil Oluşturma Araçları bakın.
