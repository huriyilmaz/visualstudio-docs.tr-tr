---
title: Özet Görünümü | Microsoft Docs
description: Özet görünümünün profil oluşturma çalıştırması içinde en yüksek performansa sahip işlevler veya nesneler hakkında nasıl bilgi görüntüley olduğunu öğrenin.
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
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6e44ca9418a08b1e31508634b63e6c58a2acdd7d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157182"
---
# <a name="summary-view"></a>Özet görünümü
Özet görünümü, profil oluşturma çalıştırması içinde en yüksek performansa sahip işlevler veya nesneler hakkında bilgi görüntüler. Bu görünüm, profil oluşturma yönteminin performans ölçümlerine göre bir zaman çizelgesi grafiği ve en pahalı işlevlerin veya nesnelerin iki veya daha fazla listesi sağlar. Bu görünümde yer alan veriler, kullanılan profil oluşturma yöntemine (örnekleme, ölçümleme veya eşzamanlılık) ve .NET bellek ayırmanın toplanmış olup olmadığını bağlıdır.

 Eşzamanlılık verilerinin Özet görünümü dışındaki tüm Özet görünümleri için, Özet görünümündeki zaman çizelgesi grafiği profil oluşturmanın meydana geldiği zaman içinde profili yapılan uygulamanın işlemci (CPU) kullanımını gösterir.

- Grafikte bir zaman dilimi belirtirsiniz, bu segment için verileri yeniden yalıtabilir veya zaman çizelgesinin grafitisini belirttiğiniz segmente yakınlaştırabilirsiniz. Daha fazla bilgi için [bkz. Nasıl ekleyebilirsiniz: Özet Zaman Çizelgesi'nde rapor görünümlerini filtreleme.](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)

- İşlevin İşlev Ayrıntıları görünümünü açmak için Özet görünümü listesinde bir işleve tıkabilirsiniz. Ayrıca diğer görünüm seçenekleri için işleve sağ tıkabilirsiniz.

- Özet görünümü listelerinde görünen öğe sayısını değiştirmek  için Araçlar menüsünü açın, Seçenekler'in üzerine **gelin** ve Performans Araçları'nın **üzerine tıklayın.** Genel **ayarlar'ın** altında Özet **görünümü ayarında işlev sayısı'nda değişiklik** yapın.

## <a name="notifications-links"></a>Bildirimler bağlantıları
 Rapor için görüntüleme seçeneklerini ayarlamak için Bildirim listesinde bağlantılara tıklarsınız. Liste, zaman çizelgesi grafiğinin sağ tarafından sağdır.

|Seçenek|Açıklama|
|-|-|
|**Kullanıcı Olmayan Kodu Göster**<br /><br /> **Yalnızca kendi kodum**|Yerel kod veya ölçümleme yöntemi kullanılarak toplanan verilerin profilini oluşturma için kullanılamaz. Yalnızca kullanıcı kodundaki verileri görüntüleme **(** Yalnızca kendi kodum göster) ile sistem kodu ( Kullanıcı Olmayan Kodu Göster ) dahil olmak üzere tüm kodlardan gelen verileri görüntüleme **arasında geçişler.** Varsayılan olarak, veriler kullanıcı koduyla sınırlıdır. Ayarı değiştirmek için bkz. Nasıl Yalnızca kendi kodum 1000000000000000000000000000000000000000000000000000000000 [](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)|
|**Kılavuzu Görüntüle**|Hata Listesi penceresinde performans **kuralı uyarılarını** görüntüler. Daha fazla bilgi için [bkz. Verileri analiz etmek için performans kurallarını kullanma](../profiling/using-performance-rules-to-analyze-data.md)|

## <a name="report"></a>Rapor
 Farklı görünümleri açmak ve raporu karşılaştırmak, kaydetmek veya filtrelemek için Rapor listesinde bağlantılara tıkabilirsiniz. Liste, zaman çizelgesi grafiğinin sağ tarafından sağdır.

|Seçenek |Açıklama |
|----------------------------| - |
| **Kırpıldı Çağrı Ağacını Göster** | Çağrı Ağacı Görünümünde en pahalı yürütme yollarını görüntüler. Daha fazla bilgi için [bkz. Çağrı Ağacı görünümü.](../profiling/call-tree-view.md) |
| **Hot Lines'i Göster** | Ölçümleme yöntemi kullanılarak toplanan verilerin profilini oluşturma için kullanılamaz. Satırlar Görünümünde en pahalı kaynak kod satırlarını görüntüler. Daha fazla bilgi için bkz. [Satırlar görünümü.](../profiling/lines-view.md) |
| **Raporları Karşılaştırma** | Geçerli **dosyayla karşılaştırmak için başka** bir profil oluşturma veri dosyası belirtebilirsiniz Karşılaştırma için analiz dosyalarını seçin iletişim kutusunu görüntüler. Daha fazla bilgi için [bkz. Performans veri dosyalarını karşılaştırma.](../profiling/comparing-performance-data-files.md) |
| **Rapor Verilerini Dışarı Aktarma** | Virgülle **ayrılmış değer** (.csv) olarak kaydetmek için bir veya daha fazla rapor görünümleri belirtebilirsiniz Raporu Dışarı Aktar iletişim .xml görüntüler. Daha fazla bilgi için [bkz. Nasıl: Profil oluşturma araçlarını dışarı aktarma raporları.](/previous-versions/visualstudio/visual-studio-2010/ms182394\(v\=vs.100\)) |
| **Analiz Raporu Kaydetme** | Geçerli profil oluşturma veri dosyasını bir .vsps dosyası olarak kaydeder ve bu dosya arabiriminde daha hızlı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açılır. Daha fazla bilgi için, [bkz. How to: Save analyzed profiling data files](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\)). |
| **Rapor Verilerini Filtreleme** | Rapor görünümündeki verileri kısıtlama ölçütlerini belirtebilirsiniz profil oluşturma raporu filtre bölmesini görüntüler. Daha fazla bilgi için [bkz. Performans raporu görünümü filtresi](../profiling/performance-report-view-filter.md) |
| **Tam Ekranı Değiştir** | Rapor görünümü için tam ekran modunu iki durumlu olarak gösterir. |

## <a name="see-also"></a>Ayrıca bkz.
- [Özet görünümü - örnekleme verileri](../profiling/summary-view-sampling-data.md)
- [Özet görünümü - ölçüm verileri](../profiling/summary-view-instrumentation-data.md)
- [Özet görünümü - .NET bellek verileri](../profiling/summary-view-dotnet-memory-data.md)
