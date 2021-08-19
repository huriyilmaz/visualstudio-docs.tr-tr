---
title: Profil oluşturma komut satırı - Rapor oluşturma
description: Profil oluşturma veri dosyalarından .xml veya .csv (virgülle ayrılmış değer) oluşturmak için VSPerfReport komut satırı aracını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 80af0b2206b6b5e30806c8bf98d85ef29da25f95
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039117"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Komut satırına profil oluşturma raporları oluşturma
**VSPerfReport** komut satırı aracı oluşturmanıza olanak sağlar. *xml* veya virgülle ayrılmış değer (.*csv*) profil oluşturma verilerinden raporlar ( .*vsp*) dosyaları. VSPerfReport rapor türleri için arabiriminin tablo tabanlı görünümlerini yakından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eşler. Raporu yalnızca kodunuzu gösterecek ve profil oluşturma veri dosyasının yalnızca bir segmentini gösterecek şekilde filtreleyebilirsiniz. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

 Ayrıca, içine semboller katıştırarak profil oluşturma veri dosyalarınızı daha kolay paylaşabilirsiniz. *vsp* dosyaları ve önceden analiz raporu () oluşturarak.*daha küçük* ve açılması daha hızlı olan vsps ) dosyaları.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Temel bir rapor oluşturun.** VSPerfReport rapor türlerinin hepsini veya bir alt kümesini oluşturun.|-   [Temel raporlar oluşturma](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**İki profil oluşturma veri dosyası karşılaştırın.** İki profil oluşturma verisi dosyası içinde performans verilerini karşılaştıran bir "fark" raporu oluşturun.|-   [Nasıl olur: Komut isteminden profil oluşturma karşılaştırma raporu oluşturma](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Veri kaynağı (ETW) verileri için Windows izleme ve Olay İzlemeyi görüntüleme.** Her giriş ve çıkış noktası için uygulamanın işlevlerine ve işlevinizin diğer işlevlere yapılan her çağrıya ilişkin zamanlama bilgilerini listeleen bir çağrı izleme raporu oluşturun. Veya profil oluşturma çalıştırması içinde toplanan tüm ETW olaylarının ayrıntılı bir listesini oluşturun.|-   [Nasıl: Çağrı izleme raporu oluşturma](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Raporu filtreleme.** Raporu yalnızca kodundaki işlevlerle veya profil oluşturma veri dosyasındaki belirli bir süreyle sınırla.|-   [Nasıl yapılanlar: Raporları komut satırına göre filtreleme](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Taşınabilir profil oluşturma veri dosyaları oluşturun.** Profil oluşturma verileri paylaşımını kolaylaştırmak için, profil oluşturmanın sembollerini içine katıştırabilirsiniz. *vsp* dosyası. Ayrıca, önceden analiz amaçlı profil oluşturma verileri de oluşturabilirsiniz ( .*daha küçük* ve açılması daha hızlı olan vsps ) dosyası.|-   [Taşınabilir profil oluşturma veri dosyaları oluşturma](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
