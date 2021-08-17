---
title: CPU ve Windows Sayaçları | Microsoft Docs
description: CPU (donanım) ve Windows (yazılım) sayaçları performans verileri sağlar. Bunları görüntülemeyi ve veri toplamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 675061b7a094364122535d429a6835b43a666924011c2b6fea4203514a2222fa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355625"
---
# <a name="cpu-and-windows-counters"></a>CPU ve Windows sayaçları

Visual Studio Profiler, işletim sistemi (Windows sayaçları) tarafından oluşturulan performans verilerini ve işlemci birimi (CPU sayaçları) tarafından oluşturulan performans verilerini toplamaya olanak sağlar.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="windows-counters"></a>Windows sayaçları

Windows sayaçları, işletim sisteminin Windows uygulama, hizmet veya sürücünün performansı hakkında bilgi sağlayan tanılama altyapısının bir parçasıdır. Windows sayaçları, geçerli bilgisayarın yapılandırmasına bağlıdır ve diğer bilgisayarlarda kullanılamıyor olabilir. Windows sayaçları profil oluşturma veri dosyalarında profil oluşturma işaretleri olarak toplanır ve bunlar daha sonra görünümleri ve raporları filtrelemek için kullanılabilir.

## <a name="cpu-counters"></a>CPU sayaçları

CPU sayaçları, bilgisayarın CPU's un donanımla ilgili olayların sayısını depolar. Ölçüm ölçümünü profil oluşturma yöntemini kullanarak CPU sayacı verilerini toplayan veriler, işlevler ve modüller için verilere eklenir. Ölçüm ölçüm yöntemini kullanarak birden çok CPU sayacı toplayabilirsiniz. Örnekleme yöntemini kullanarak örneklene olay olarak kullanmak üzere bir sayaç seçersiniz.

Performans sayaçları CPU'ya özeldir. Bir CPU'nun farklı modelleri ve sürümleri, aynı performans sayacını etkinleştirmek için önemli ölçüde farklı yapılandırma ayarlarına sahip olabilir. [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] Profilleyici taşınabilir olayları bazı yaygın performans sayaçlarını belirli işlemcilerden bağımsızdır ve genel performans olaylarını toplamaya veya örneklemeye olanak sağlar.

Profilleyiciyi kullanırken belirli bir olayı saymak (örneğin, L2 önbellek isabetleri) için ilgili olay göndereni etrafında bir performans oturumu derlemeniz gerekir. Bunu L2 önbelleğine sahip herhangi bir CPU'da da yapabiliriz. Performans oturumu, değişiklik yapmadan platformdan platforma taşınabilirsiniz.

Profil Visual Studio, belirli bir platform için belirli olayları desteklemeye devam eder. Örneğin, Pentium 4 platformunda bir geliştirici NetBurst mimarisine özgü olayları saymak istiyor olabilir. Bu olay taşınabilir değildir, ancak geliştirici tarafından belirli bir platformda belirli bir performans oturumu için kullanılabilir.

## <a name="portable-and-platform-events"></a>Taşınabilir ve platform olayları

Taşınabilir olaylar, belirli bir işlemciye özgü bir grup CPU sayacıdır. Diğer tüm CPU sayaçları platform olayları olarak anılabilir ve çeşitli platformlarda desteklenmiyor olabilir.

 Hem taşınabilir hem de platform olayları için sayaçlar içinde tanımlanır. *sayaçlarla* ilgili belirli değerlerin sağlanmıştır xml dosyaları. Intel ve AMD CPU'ları için veriler farklı olduğundan, farklı CPU'lar için birden çok dosya vardır. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]ProfilLeyici, performans ölçümü için kullanıcıya hem taşınabilir hem de platform olarak uygun sayaçları sunmak için bu bilgileri kullanır.

### <a name="portable-events"></a>Taşınabilir olaylar

Taşınabilir olaylar aşağıdaki olayları içerir:

**Genel Olaylar**

|Olay Adı|Olay Açıklaması|
|----------------|-----------------------|
|Kullanımdan Kaldıran Yönergeler|Olay tamamlanana kadar yürütülen yönergelerin sayısını gösterir.|
|Durdurulan Olmayan Döngüler|Yalnızca işlemcinin durdurulmama durumuna (örneğin, I/O için bekleme) sahip döngüleri gösterir.|

**Ön Uç Olayları**

|Olay Adı|Olay Açıklaması|
|----------------|-----------------------|
|ITLB Misses|Hataya neden olan Yönerge Çevirisi AraBelleği aramalarının sayısını gösterir.|

**Dal Olayları**

|Olay Adı|Olay Açıklaması|
|----------------|-----------------------|
|Dallar Kaldırıldı|Olay tamamlanana kadar yürütülen dal yönergelerinin sayısını gösterir.|
|Yanlış Tahmin Edilen Dallar|İşlemci yanlış bir yol tahmin etti diye yanlış tahmin edilen dalları gösterir. yanlış tahmin edilen dallar performansı etkiler çünkü işlemcinin yapılan tüm işi atarak doğru yolda yeniden başlatması gerekir.|

**Bellek Olayları:**

|Olay Adı|Olay Açıklaması|
|----------------|-----------------------|
|L2 Önbelleği Okuma Isabetleri|İkinci düzey önbellek okuma isabetleri sayısını gösterir.|
|L2 Önbelleği Okuma Başvuruları|İkinci düzey önbellek okuma başvurularının sayısını gösterir. Yük isabet almama ve sahiplik (RFO) isabetleri ve isabetleri okuma içerir.|

## <a name="view-available-counters"></a>Kullanılabilir sayaçları görüntüleme

Kullanılabilir CPU sayaçlarını IDE'nin Visual Studio komut istemi penceresinde listeleyebilirsiniz.

### <a name="visual-studio-ui"></a>Visual Studio Uı

IDE'de bulunan bir bilgisayarda kullanılabilir sayaçları Visual Studio için, Performans Gezgini'da açık bir profil Performans Gezgini.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen tüm CPU sayaçlarının listesini görüntülemek için

1. Bu Performans Gezgini performans oturumuna sağ tıklayın ve ardından Özellikler'e **tıklayın.**

2. Aşağıdakilerden birini yapın:

   - Örnekleme **'ye** tıklayın ve ardından **Örnek olay** listesinden Performans **sayacı'ı** seçin. CPU sayaçları Kullanılabilir performans **sayaçları altında listelenir.**

      **Not** Önceki **örnekleme yapılandırmasına** dönmek için İptal'e tıklayın.

     -veya-

   - **CPU Sayaçları'ı** ve ardından **CPU Sayaçlarını Topla'yi seçin.** CPU sayaçları Kullanılabilir **sayaçlar altında listelenir.**

      **Not** Önceki **sayaç koleksiyonu** yapılandırmasına dönmek için İptal'e tıklayın.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen Pencere sayaçlarının listesini görüntülemek için

1. Bu Performans Gezgini performans oturumuna sağ tıklayın ve ardından Özellikler'e **tıklayın.**

2. **Sayaçlar Windows a tıklayın.**

3. Sayaçları **Windows seçin.**

4. Sayaç **Kategorisi listesinden** bir sayaç grubu seçin. Grubun Windows sayacı liste kutusunda görüntülenir.

     **Not:** Önceki **sayaç koleksiyonu** yapılandırmasına dönmek için İptal'e tıklayın.

### <a name="command-line"></a>Komut satırı

[VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracını kullanarak, bir bilgisayarda kullanılabilen CPU sayaçlarını komut satırıyla listeebilirsiniz.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen CPU sayaçlarının listesi için

1. Bir komut istemi penceresi açın.

2. Tür

     **\<Visual Studio Performance Tools Directory>\VSPerfCmd /querycounters**

     burada, *\<Visual Studio Performance Tools Directory>* yüklemenizin Performans Araçları dizininin Visual Studio olur. Performans araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)

## <a name="see-also"></a>Ayrıca bkz.

- ['a Genel Bakış](../profiling/overviews-performance-tools.md)
- [Nasıl olur: Örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md)
- [Nasıl yapılır: CPU sayaç verileri toplama](../profiling/how-to-collect-cpu-counter-data.md)
- [Nasıl Windows toplama](../profiling/how-to-collect-windows-counter-data.md)
