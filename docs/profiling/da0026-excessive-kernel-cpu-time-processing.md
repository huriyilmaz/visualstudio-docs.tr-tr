---
title: 'DA0026: Aşırı çekirdek CPU zaman işleme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0026
- vs.performance.DA0026
- vs.performance.26
ms.assetid: 4cfc8a29-b29b-4a72-b386-03d8856fdf8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2c8b4cb63eb4647ddab4220ed6729894fe8a456f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777495"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Aşırı çekirdek CPU süresi işleme

|||
|-|-|
|Kural Id|Todo|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemi|Örnekleme|
|İleti|Çekirdek modu CPU süresi nispeten yüksek miktarda ölçüldü. SysCall örneklemesi etkinleştirilmiş olan kaynağı araştırmayı düşünün.|
|Kural türü|Bilgi|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Çekirdek modunda yürütülen CPU süresi, kullanıcı modunda harcanan süreyi aştı. Yüksek çekirdek modu yürütme sürelerinin nedenini belirlemek için yeniden profil oluşturmayı ve sistem çağrılarının (syscalls) sayısını örneklemeyi düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Uygulamanın çekirdek modu uygulamasında harcanan nispeten yüksek zaman oranı daha fazla araştırma yapılmasını gerektirebilir. Kullanıcı modu uygulaması, G/Ç işlemlerini gerçekleştirmek, iş parçacığı veya işlem senkronizasyonu ilkellerini beklemek veya sistem çağrıları yapmak için çekirdek moduna geçer. Sistem çağrılarına dayalı örnek çağrı yığınları toplama seçeneğini seçtiğinizde, uygulamanın yaptığı sistem çağrıları nın türlerini ve bunlardan hangi işlevleri sorumlu olduğunu araştırabilirsiniz.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Uygulamanızın yaptığı sistem çağrıları nın türlerini araştırmak için profili yeniden çalıştırın ve sistem çağrılarına göre örnek toplama seçeneğini seçin. [Bkz. Nasıl Yapılır:](../profiling/how-to-choose-sampling-events.md) Daha fazla bilgi için IDE içindeki profil oluşturma araçlarını çalıştırıyorsanız Örnekleme Etkinlikleri'ni seçin. Profil oluşturma araçlarını komut satırından çalıştırıyorsanız, Profil Oluşturma Araçları komut satırı araçları referansındaki [VSPerfCmd](../profiling/vsperfcmd.md) makalesinin **Örnek aralığı seçenekleri** bölümüne bakın.
