---
title: Komut Satırından Profil Oluşturma Raporları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7f28d7271fdf33822475a663debed269bb515959
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777783"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Komut satırından profil oluşturraporları oluşturma
**VSPerfReport** komut satırı aracı oluşturmanıza olanak sağlar. *xml* veya virgülden ayrılmış değer (.* csv*) profil oluşturma verilerinden raporlar (.* vsp*) dosyaları. VSPerfReport rapor türleri, arabirimin tablo tabanlı görünümlerini yakından eşleştirir. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Raporu yalnızca kodunuzu göstermek ve profil oluşturma veri dosyasının yalnızca bir bölümünü göstermek için filtreleyebilirsiniz. Daha fazla bilgi için [VSPerfReport'a](../profiling/vsperfreport.md)bakın.

 Ayrıca, ''nin simgelerini katıştırarak profil oluşturma veri dosyalarınızı paylaşmayı kolaylaştırabilirsiniz. *vsp* dosyaları ve önceden analiz edilmiş rapor oluşturarak (.* vsps*) daha küçük ve daha hızlı açmak için dosyaları.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Temel bir rapor oluşturun.** VSPerfReport rapor türlerinin tamamını veya bir alt kümesini oluşturun.|-   [Temel raporlar oluşturma](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**İki profil oluşturma veri dosyalarını karşılaştırın.** İki profil oluşturma veri dosyasındaki performans verilerini karşılaştıran bir "diff" raporu oluşturun.|-   [Nasıl yapilir: Komut isteminden profil oluşturucu karşılaştırma raporu oluşturma](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Windows (ETW) verileri için arama izleme ve Olay İzleme'yi görüntüleyin.** Uygulamanızın işlevlerine her giriş ve çıkış noktası için zamanlama bilgilerini listeleyen bir çağrı izleme raporu ve işleviniz tarafından diğer işlevlere yapılan her çağrıyı oluşturun. Veya profil oluşturma çalışmasında toplanan tüm ETW olaylarının ayrıntılı bir listesini oluşturun.|-   [Nasıl yapilir: Çağrı izleme raporu oluşturma](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Bir raporu filtreleyin.** Raporu yalnızca kodunuzdaki işlevler veya profil oluşturma veri dosyasındaki belirli bir zaman ile sınırlandırın.|-   [Nasıl yapılı: Komut satırındaki raporları filtreleme](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Taşınabilir profil oluşturma veri dosyaları oluşturun.** Profil oluşturma verilerinin paylaşımını kolaylaştırmak için, profil oluşturma için sembolleri katıştırabilirsiniz. *vsp* dosyası. Ayrıca önceden analiz edilmiş bir profil oluşturma verileri de oluşturabilirsiniz (.* vsps*) daha küçük ve daha hızlı açmak için dosya.|-   [Taşınabilir profil oluşturma veri dosyaları oluşturma](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
