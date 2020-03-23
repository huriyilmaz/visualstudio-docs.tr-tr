---
title: PerfTips | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 509d2d4f-48a5-4cdf-acad-6f7b75421303
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 93703bdd4bf2f0046176ceb1f6febd5564f61705
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71128311"
---
# <a name="perftips"></a>PerfTips
Visual Studio hata ayıklama *PerfTips* ve hata ayıklama tümleşik **Tanı Araçları,** hata ayıklama sırasında uygulamanızın performansını izlemenize ve analiz etmeye yardımcı olur.

 Hata ayıklama tümleşik tanı araçları, siz geliştirirken performans sorunlarının farkına varmenın harika bir yolu olsa da, hata ayıklama aracının uygulamanızın performansı üzerinde önemli bir etkisi olabilir. Daha doğru performans verileri toplamak için, performans araştırmalarınızın ek bir parçası olarak hata ayıklamanın dışında çalışan Visual Studio tanılama araçlarını kullanmayı düşünün. Bkz. [Hata ayıklayıcılı veya hata ayıklayıcısız profil oluşturma araçlarını çalıştırın.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

## <a name="perftips"></a>PerfTips
 Hata ayıklayıcı yürütmeyi kesme noktasında veya basamaklama işleminde durdurduğunda, kesme ile önceki kesme noktası arasında geçen süre düzenleyici penceresinde bir ipucu olarak görünür. Daha fazla bilgi için, [Visual Studio ile Hata Ayıklarken PerfTips: Performans Bilgileri](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)ne zaman bir bakışta bakın.

 ![PerfTip](../profiling/media/dbgdiag_perf_perftip.png "DBGDIAG_PERF_PerfTip")

## <a name="diagnostics-tools-window"></a>Tanılama Araçları penceresi
 Kesme noktaları ve ilişkili zamanlama verileri **Tanılama Araçları** penceresine kaydedilir.

 Aşağıdaki grafik, Visual Studio 2015 Güncelleştirmesi 1'deki **Tanılama Araçları** penceresini gösterir:

 ![DiagnosticTools&#45;Güncelleme1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

- **Olayları Kesme** zaman çizelgesi, hata ayıklama oturumunda vurulan kesme noktalarını işaretler. **Hata Ayıklama** ayrıntıları listesini seçmek için bir olayı tıklatın.

- **CPU Kullanım** grafiği, hata ayıklama oturumundaki tüm işlemci çekirdekleri arasında CPU kullanımındaki değişikliği gösterir.

- **Hata Ayıklama** ayrıntıları bölmesinin **Olaylar** listesi, her kesme olayı için öğeler içerir.

- Kesme olayının **Süre** sütunu, olay la önceki kesme noktası arasında geçen süreyi görüntüler.

## <a name="turn-perftips-on-or-off"></a>PerfTips'i açma veya kapatma
 PerfTips'i etkinleştirmek veya devre dışı kalmak için:

1. Hata **Ayıklama** menüsünde **Seçenekler'i**seçin.

2. **Hata ayıklama sırasında geçen PerfTip'i göster'i**kontrol edin veya temizleyin.

## <a name="turn-the-diagnostic-tools-window-on-or-off"></a>Tanılama Araçları penceresini açma veya kapatma
 Tanılama Araçları penceresini etkinleştirmek veya devre dışı kalımiçin:

1. Hata **Ayıklama** menüsünde **Seçenekler'i**seçin.

2. **Hata ayıklama sırasında Tanılama Araçlarını Etkinleştir'i**denetleyin veya temizleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Profil Oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
