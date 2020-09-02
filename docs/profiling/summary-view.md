---
title: Özet görünümü | Microsoft Docs
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
ms.openlocfilehash: a12989004b5bed8601bdda1ec0719eda789ff822
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546893"
---
# <a name="summary-view"></a>Özet görünümü
Özet görünümü, bir profil oluşturma çalıştırmasında en yüksek performanslı işlevler veya nesneler hakkında bilgi görüntüler. Bu görünüm, profil oluşturma yönteminin performans ölçümlerine göre en pahalı işlevlerin veya nesnelerin bir zaman çizelgesi grafiği ve iki veya daha fazla listesini sağlar. Bu görünümdeki veriler, kullanılan profil oluşturma yöntemine (örnekleme, izleme veya eşzamanlılık) ve .NET bellek ayırmasının toplanıp toplanmadığını gösterir.

 Eşzamanlılık verilerinin Özet görünümü dışındaki tüm Özet görünümleri için, Özet görünümündeki zaman çizelgesi grafiğinde profil oluşturma işleminin gerçekleştiği zaman içindeki profili oluşturulmuş uygulamanın işlemci (CPU) kullanımı gösterilir.

- Grafikte bir zaman kesimini belirtirseniz, bu segmentin verilerini yeniden çözümleyebilir veya zaman çizelgesini belirttiğiniz kesime yakınlaştırabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: rapor görünümlerini Özet zaman çizelgesinden filtreleme](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).

- İşlevin Işlev ayrıntıları görünümünü açmak için Özet Görünüm listesindeki bir işleve tıklayabilirsiniz. Diğer görünüm seçenekleri için de işleve sağ tıklayabilirsiniz.

- Özet Görünüm listelerinde görünen öğelerin sayısını değiştirmek için, **Araçlar** menüsünü açın, **Seçenekler**' in üzerine gelin ve ardından **performans araçları**' na tıklayın. **Genel ayarlar**altında, **Özet Görünüm ayarında işlev sayısını** değiştirin.

## <a name="notifications-links"></a>Bildirimler bağlantıları
 Raporun görüntüleme seçeneklerini ayarlamak için bildirim listesindeki bağlantılar ' a tıklayabilirsiniz. Liste, zaman çizelgesi grafiğinin sağında bulunur.

|Seçenek|Açıklama|
|-|-|
|**Kullanıcı dışı kodu göster**<br /><br /> **Yalnızca kendi kodum göster**|Yerel kod veya izleme yöntemi kullanılarak toplanan profil oluşturma verileri için kullanılamaz. Yalnızca Kullanıcı kodundaki verileri görüntüleme (**yalnızca kendi kodum göster**) ve sistem kodu (**Kullanıcı dışı kodu göster**) dahil olmak üzere tüm koddan verileri görüntüleme arasında geçiş yapar. Varsayılan olarak, veriler Kullanıcı kodu ile sınırlandırılmıştır. Ayarı değiştirmek için bkz. [nasıl yapılır: profil oluşturma araçları rapor görünümlerini yalnızca kendi kodum görüntülemek Için filtreleme](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|
|**Kılavuzu görüntüle**|**Hata listesi** penceresindeki performans kuralı uyarılarını görüntüler. Daha fazla bilgi için bkz. [verileri çözümlemek için performans kurallarını kullanma](../profiling/using-performance-rules-to-analyze-data.md)|

## <a name="report"></a>Rapor
 Farklı görünümleri açmak ve raporu karşılaştırmak, kaydetmek veya filtrelemek için rapor listesindeki bağlantılar ' a tıklayabilirsiniz. Liste, zaman çizelgesi grafiğinin sağında bulunur.

|Seçenek |Açıklama |
|----------------------------| - |
| **Kırpılmış çağrı ağacını göster** | Çağrı ağacı görünümünde en pahalı yürütme yollarını görüntüler. Daha fazla bilgi için bkz. [çağrı ağacı görünümü](../profiling/call-tree-view.md). |
| **Etkin çizgileri göster** | , İzleme yöntemi kullanılarak toplanan profil oluşturma verileri için kullanılamaz. Satırlar görünümünde en pahalı kaynak kodu satırlarını görüntüler. Daha fazla bilgi için bkz. [çizgiler görünümü](../profiling/lines-view.md). |
| **Raporları Karşılaştır** | Geçerli dosyayla karşılaştırmak için başka bir profil oluşturma veri dosyası belirtebileceğiniz, **karşılaştırma için analiz dosyalarını Seç** iletişim kutusunu görüntüler. Daha fazla bilgi için bkz. [performans veri dosyalarını karşılaştırma](../profiling/comparing-performance-data-files.md). |
| **Rapor verilerini dışarı aktar** | Virgülle ayrılmış değer (. csv) veya. xml dosyaları olarak kaydedilecek bir veya daha fazla rapor görünümü belirtebileceğiniz **raporu dışarı aktar** iletişim kutusunu görüntüler. Daha fazla bilgi için bkz. [nasıl yapılır: profil oluşturma araçları raporlarını dışarı aktarma](/previous-versions/visualstudio/visual-studio-2010/ms182394\(v\=vs.100\)). |
| **Çözümlenen raporu Kaydet** | Geçerli profil oluşturma veri dosyasını, için arabiriminde daha hızlı açılan bir. vsps dosyası olarak kaydeder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Daha fazla bilgi için bkz. [nasıl yapılır: çözümlenen profil oluşturma veri dosyalarını kaydetme](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\)). |
| **Rapor verilerini filtrele** | Rapor görünümündeki verileri kısıtlamak için ölçüt belirtebileceğiniz profil oluşturma rapor filtresi bölmesini görüntüler. Daha fazla bilgi için bkz. [performans rapor görünümü filtresi](../profiling/performance-report-view-filter.md) |
| **Tam ekrana geç** | Rapor görünümü için tam ekran moduna geçiş yapar. |

## <a name="see-also"></a>Ayrıca bkz.
- [Özet görünümü-örnekleme verileri](../profiling/summary-view-sampling-data.md)
- [Özet görünümü-izleme verileri](../profiling/summary-view-instrumentation-data.md)
- [Özet görünümü-.NET bellek verileri](../profiling/summary-view-dotnet-memory-data.md)
