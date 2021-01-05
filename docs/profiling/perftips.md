---
title: PerfTips | Microsoft Docs
description: Hata ayıklama sırasında uygulama performansınızı izlemek ve analiz etmek için Visual Studio hata ayıklayıcısı PerfTips ve tümleşik Tanılama Araçları nasıl kullanacağınızı öğrenin.
ms.date: 9/11/2020
ms.topic: how-to
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 481113e9f5e2f5b66aec5f4dad29f581462165ca
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815834"
---
# <a name="perftips"></a>PerfTips

Visual Studio hata ayıklayıcı *PerfTips* ve hata ayıklayıcı ile tümleşik **Tanılama araçları** , hata ayıklarken uygulamanızın performansını izlemenize ve çözümlemenize yardımcı olur.

Hata ayıklayıcı tümleşik tanılama araçları geliştirilirken performans sorunlarından haberdar olmanın harika bir yoludur, ancak hata ayıklayıcı uygulamanızın performansı üzerinde önemli bir etkiye sahip olabilir. Daha doğru performans verileri toplamak için performans araştırmalarınızın ek bir parçası olarak performans Profiler 'daki araçları kullanmayı göz önünde bulundurun. Bkz. [hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="perftips"></a>PerfTips

Hata ayıklayıcı, bir kesme noktası veya Adımlama işleminde yürütmeyi durdurduktan sonra, kesme ve önceki kesme noktası arasındaki geçen süre, düzenleyici penceresinde bir ipucu olarak görüntülenir. Daha fazla bilgi için bkz. [PerfTips: Visual Studio Ile hata ayıklama sırasında bir bakışta performans bilgileri](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/).

![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Tanılama Araçları penceresi

Kesme noktaları ve ilişkili zamanlama verileri **Tanılama araçları** penceresine kaydedilir.

Aşağıdaki çizimde **Tanılama araçları** penceresi gösterilmektedir.

![Visual Studio hata ayıklayıcısındaki Tanılama Araçları penceresinin ekran görüntüsü ve bellek ve CPU kullanımı için olaylar zaman çizelgesi ve grafikleri gösteriliyor.](../profiling/media/diagnostictools-update1.png)

- **Olayları kes** zaman çizelgesi, hata ayıklama oturumunda isabet noktalarını işaret ediyor. **Hata ayıklayıcı** ayrıntıları listesini seçmek için bir olaya tıklayın.

- **CPU kullanımı** grafiği, hata ayıklama oturumunda tüm işlemci çekirdekleri genelinde CPU kullanımı değişikliğini gösterir.

- **Hata ayıklayıcı** ayrıntıları bölmesinin **Olaylar** listesi, her bir kesme olayının öğelerini içerir.

- Bir break olayının **Duration** sütunu, olay ve önceki kesme noktası arasındaki geçen süreyi görüntüler.

## <a name="turn-perftips-on-or-off"></a>PerfTips 'ı aç veya kapat

PerfTips 'ı etkinleştirmek veya devre dışı bırakmak için:

1. **Hata Ayıkla** menüsünde **Seçenekler**' i seçin.

2. **Hata ayıklama sırasında geçen Perftıp 'Yi göster** veya temizle.

## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Tanılama Araçları penceresini açma veya kapatma

Tanılama Araçları penceresini etkinleştirmek veya devre dışı bırakmak için:

1. **Hata Ayıkla** menüsünde **Seçenekler**' i seçin.

2. **Hata ayıklama sırasında tanılama araçlarını etkinleştir** onay kutusunu işaretleyin veya temizleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
