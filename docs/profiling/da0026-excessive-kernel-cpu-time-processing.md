---
title: DA0026-aşırı çekirdek CPU süresi işleme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 38452ce95b299be11e20150440c815127b66d061
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332400"
---
# <a name="da0026-excessive-kernel-cpu-time-processing"></a>DA0026: Aşırı çekirdek CPU süresi işlemesi

|||
|-|-|
|Kural kimliği|TODO|
|Kategori|Profil Oluşturma Araçları kullanımı|
|Profil oluşturma yöntemi|Örnekleme|
|İleti|Görece yüksek miktarda çekirdek modu CPU zamanı ölçüldü. SysCall örneklemesi etkin olarak kaynağı araştırın.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Çekirdek modunda yürütülen oran CPU süresi, kullanıcı modunda harcanan süre miktarını aştı. Profil oluşturmayı yeniden deneyin ve yüksek çekirdek modu yürütme sürelerinin nedenini öğrenmek için sistem çağrılarının sayısını (syscalls) örnekleme.

## <a name="rule-description"></a>Kural açıklaması
 Uygulamanın çekirdek modu yürütülürken harcadığı sürenin görece yüksek oranı, daha fazla araştırma sağlayabilir. Kullanıcı modu uygulaması, iş parçacığı veya işlem eşitleme temelleri için beklemek veya sistem çağrıları yapmak için g/ç işlemlerini gerçekleştirmek üzere çekirdek moduna geçiş yapar. Uygulama yaptığı sistem çağrılarının türlerini ve Sistem çağrılarına göre örnek çağrı yığınları toplama seçeneğini belirlediğinizde bunlardan sorumlu olan işlevleri araştırabilirsiniz.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 Uygulamanızın yaptığı sistem çağrılarının türlerini araştırmak için, profili yeniden çalıştırın ve Sistem çağrılarına göre örnek toplama seçeneğini belirleyin. Daha fazla bilgi için bkz. nasıl yapılır: IDE içinde profil oluşturma araçları çalıştırıyorsanız [örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md) . Profil oluşturma araçlarını komut satırından çalıştırıyorsanız, Profil Oluşturma Araçları komut satırı araçları başvurusu ' nda [VSPerfCmd](../profiling/vsperfcmd.md) makalesinin **örnek Aralık seçenekleri** bölümüne bakın.
