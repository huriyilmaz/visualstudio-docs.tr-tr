---
title: Özet Görünüm | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 87692c938462f166f93b4cfb8b223a45e2553ada
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771594"
---
# <a name="summary-view"></a>Özet görünümü
Özet görünümü, profil oluşturma çalışmasındaki en performans pahalı işlevler veya nesneler hakkındaki bilgileri görüntüler. Bu görünüm, profil oluşturma yönteminin performans ölçümlerine dayalı bir zaman çizelgesi grafiği ve en pahalı işlevlerin veya nesnelerin iki veya daha fazla listesini sağlar. Bu görünümdeki veriler, kullanılan profil oluşturma yöntemine (örnekleme, enstrümantasyon veya eşzamanlılık) ve .NET bellek ayırmanın toplanıp toplanmadığına bağlıdır.

 Eşzamanlılık verilerinin Özet görünümü dışındaki tüm Özet görünümleri için Özet görünümündeki zaman çizelgesi grafiği, profil oluşturmanın gerçekleştiği süre içinde profillenen uygulamanın işlemci (CPU) kullanımını gösterir.

- Grafikte bir zaman dilimi belirtirseniz, o kesime ait verileri yeniden çözümleyebilir veya zaman çizelgesi ekranını belirttiğiniz segmente yakınlaştırabilirsiniz. Daha fazla bilgi için [bkz: Özet Zaman Çizelgesi'nden rapor görünümlerini filtreleyin.](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)

- İşlevin İşlev Ayrıntıları görünümünü açmak için Özet görünüm listesindeki bir işlevi tıklatabilirsiniz. Ayrıca, diğer görünüm seçenekleri için işlevi sağ tıklatabilirsiniz.

- Özet görünüm listelerinde görünen öğelerin sayısını değiştirmek için **Araçlar** menüsünü açın, **Seçenekler'e**işaret edin ve ardından **Performans Araçları'nı**tıklatın. **Genel ayarlar**altında, Özet görünüm ayarındaki **işlev sayısını** değiştirin.

## <a name="notifications-links"></a>Bildirimler bağlantıları
 Raporun görüntü seçeneklerini ayarlamak için Bildirim listesindeki bağlantıları tıklatabilirsiniz. Liste zaman çizelgesi grafiğinin sağındadır.

|||
|-|-|
|**Kullanıcı Olmayan Kodu Göster**<br /><br /> **Sadece Kodumu Göster**|Yerel kod veya enstrümantasyon yöntemi kullanılarak toplanan verilerin profilini çıkarmak için kullanılamaz. Yalnızca kullanıcı kodundan **(Yalnızca Kodumu Göster)** verileri görüntülemekle sistem kodu da dahil olmak üzere tüm kodlardan **(Kullanıcı Kodu Olmayanları Göster)** verileri görüntülemek arasında geçiş yapılır. Varsayılan olarak, veriler kullanıcı koduyla sınırlıdır. Ayarı değiştirmek için [bkz: Profil oluşturma araçları yalnızca Kodum'u görüntülemek için görünümleri filtreleyin.](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)|
|**Kılavuzu Görüntüle**|**Hata Listesi** penceresinde performans kuralı uyarılarını görüntüler. Daha fazla bilgi için [bkz.](../profiling/using-performance-rules-to-analyze-data.md)|

## <a name="report"></a>Rapor
 Farklı görünümler açmak ve raporu karşılaştırmak, kaydetmek veya filtrelemek için Rapor listesindeki bağlantıları tıklatabilirsiniz. Liste zaman çizelgesi grafiğinin sağındadır.

| | |
|----------------------------| - |
| **Kesilmiş Çağrı Ağacını Göster** | Çağrı Ağacı Görünümü'nde en pahalı yürütme yollarını görüntüler. Daha fazla bilgi için [Bkz. Çağrı Ağacı görünümü.](../profiling/call-tree-view.md) |
| **Sıcak Hatları Göster** | Enstrümantasyon yöntemi kullanılarak toplanan verilerin profilini çıkarmak için kullanılamaz. Satır Görünümü'nde en pahalı kaynak kod satırlarını görüntüler. Daha fazla bilgi için [Bkz. Satırlar görünümü.](../profiling/lines-view.md) |
| **Raporları Karşılaştır** | Geçerli dosyayla karşılaştırmak için başka bir profil oluşturma veri dosyası belirtebileceğiniz karşılaştırma iletişim kutusu **için analiz dosyalarını seç'i** görüntüler. Daha fazla bilgi için [bkz.](../profiling/comparing-performance-data-files.md) |
| **İhracat Raporu Verileri** | Virgülle ayrılmış değer (.csv) veya .xml dosyaları olarak kaydetmek için bir veya daha fazla rapor görünümü belirtebileceğiniz **Dışa** Aktar Raporu iletişim kutusunu görüntüler. Daha fazla bilgi için [bkz: Profil oluşturma araçları raporlarını dışa aktarma.](/previous-versions/visualstudio/visual-studio-2010/ms182394\(v\=vs.100\)) |
| **Analiz Raporunu Kaydet** | Geçerli profil oluşturma veri dosyasını .vsps dosyası olarak kaydeder ve bu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]dosya için arabirimde daha hızlı açılır. Daha fazla bilgi için [bkz: Çözümlenmiş profil oluşturma veri dosyalarını kaydedin.](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\)) |
| **Rapor Verilerini Filtreleme** | Rapor görünümünde verileri kısıtlamak için ölçütler belirtebileceğiniz profil oluşturma raporu filtresi bölmesi görüntüler. Daha fazla bilgi için Bkz. [Performans raporu görünüm filtresi](../profiling/performance-report-view-filter.md) |
| **Tam Ekran'ı Geçişle** | Rapor görünümü için tam ekran modunu geçişler. |

## <a name="see-also"></a>Ayrıca bkz.
- [Özet görünüm - örnekleme verileri](../profiling/summary-view-sampling-data.md)
- [Özet görünüm - enstrümantasyon verileri](../profiling/summary-view-instrumentation-data.md)
- [Özet görünüm - .NET bellek verileri](../profiling/summary-view-dotnet-memory-data.md)
