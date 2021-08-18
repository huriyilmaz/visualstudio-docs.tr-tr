---
title: PerfTips | Microsoft Docs
description: Hata ayıklama sırasında uygulama performansınızı izlemek Visual Studio analiz etmek için Visual Studio hata ayıklayıcısı PerfTips'i ve tümleşik Tanılama Araçları nasıl kullanabileceğinizi öğrenin.
ms.date: 9/11/2020
ms.topic: how-to
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8a31872097d34a6ad7c8ce052c635c9b48770b5c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141603"
---
# <a name="perftips"></a>PerfTips

Visual Studio hata ayıklayıcısı *PerfTips* ve hata ayıklayıcı ile **tümleşik** Tanılama Araçları hata ayıklarken uygulamanın performansını izlemenize ve analiz etmenize yardımcı olur.

Hata ayıklayıcısı ile tümleşik tanılama araçları, geliştirme sırasında performans sorunlarının farkında olmanın harika bir yolu olsa da, hata ayıklayıcısı uygulamanın performansı üzerinde önemli bir etkisi olabilir. Daha doğru performans verileri toplamak için performans araştırmalarının ek bir Performans Profili Oluşturucu olarak hizmette yer alan araçları kullanmayı göz önünde bulundurabilirsiniz. Bkz. [Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

## <a name="perftips"></a>PerfTips

Hata ayıklayıcı bir kesme noktası veya adımlama işlemi sırasında yürütmeyi durdursa, kesme ile önceki kesme noktası arasındaki geçen süre düzenleyici penceresinde ipucu olarak görünür. Daha fazla bilgi için bkz. [PerfTips: Visual Studio](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)ile Hata Ayıklama sırasında bir bakışta performans bilgileri.

![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Tanılama Araçları penceresi

Kesme noktaları ve ilişkili zamanlama verileri Tanılama Araçları **kaydedilir.**

Aşağıdaki çizimde, **Tanılama Araçları** gösterilmiştir.

![Bellek ve CPU Tanılama Araçları için Olaylar zaman çizelgesini ve grafları gösteren Visual Studio hata ayıklayıcısının ekran görüntüsü.](../profiling/media/diagnostictools-update1.png)

- Olayları **Kesme zaman** çizelgesi, hata ayıklama oturumunda isabet alan kesme noktalarına işaret eder. Bir etkinliğe tıklar ve hata **ayıklayıcı ayrıntıları** listesini seçin.

- **CPU Kullanımı grafiği,** hata ayıklama oturumunda tüm işlemci çekirdeklerinde CPU kullanımında yapılan değişikliği gösterir.

- Hata **Ayıklayıcı** ayrıntıları **bölmesinin Olaylar** listesi, her bir kesme olayı için öğeleri içerir.

- Bir **kesme** olayın Süre sütunu, olay ile önceki kesme noktası arasındaki geçen süreyi görüntüler.

## <a name="turn-perftips-on-or-off"></a>PerfTips'i açma veya kapatma

PerfTips'i etkinleştirmek veya devre dışı bırakmak için:

1. Hata **Ayıkla menüsünde** Seçenekler'i **seçin.**

2. Hata ayıklarken **Geçen PerfTip'i göster'i denetleme veya temizleme.**

## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Tanılama Araçları penceresini açma veya kapatma

İlke penceresini etkinleştirmek veya devre Tanılama Araçları için:

1. Hata **Ayıkla menüsünde** Seçenekler'i **seçin.**

2. Hata ayıklarken **Tanılama Araçlarını Etkinleştir'i denetleme veya temizleme.**

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
