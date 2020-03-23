---
title: EventSource Olaylarını İşaretçi Olarak Görselleştirme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bd6339b3f55b4a4c9a1e2c90ff3183a36f16c178
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "64811540"
---
# <a name="visualize-eventsource-events-as-markers"></a>EventSource olaylarını işaretleyici olarak görselleştirin
EşzamanlıLık Görselleştiricisi EventSource olaylarını işaretleyici olarak görüntüleyebilir ve işaretçilerin nasıl görüntüleneceğini denetleyebilirsiniz. EventSource işaretçilerini görüntülemek için [Gelişmiş Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunu kullanarak ETW sağlayıcısı GUID'e kaydolun. Eşzamanlı Görselleştirici, EventSource olaylarını [Bayrak İşaretçileri,](../profiling/flag-markers.md)Yayılma [İşaretçileri](../profiling/span-markers.md)ve [İleti İşaretçileri](../profiling/message-markers.md)olarak temsil eden varsayılan kuralları vardır. Olaylara özel alanlar ekleyerek EventSource olaylarının nasıl görüntüleneceğini özelleştirebilirsiniz. İşaretçiler hakkında daha fazla bilgi için [EşzamanlıLık Görselleştirici İşaretçileri'ne](../profiling/concurrency-visualizer-markers.md)bakın. EventSource etkinlikleri hakkında daha <xref:System.Diagnostics.Tracing>fazla bilgi için bkz.

## <a name="default-visualization-of-eventsource-events"></a>EventSource olaylarının varsayılan görselleştirmesi
 Varsayılan olarak, Eşzamanlılık Görselleştiricisi EventSource olaylarını temsil etmek için aşağıdaki kuralları kullanır.

### <a name="marker-type"></a>İşaretçi türü

1. [Opcode'un](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) kazanması olan olaylar:Başlat veya kazan:Durdur,sırasıyla bir açıkaralığın başlangıcı veya sonu olarak kabul edilir.  İç içe veya çakışan açıklıklar görüntülenemez. Bir iş parçacığında başlayıp başka bir iş parçacığında sona eren olay çiftleri görüntülenemez.

2. Opcode'u ne kazanmak:Başlat ne de kazan:Stop düzeyi [(EVENT_RECORD](/windows/desktop/WES/defining-severity-levels) alanı) olmadıkça işaretçi bayrağı olarak kabul edilir. EVENT_HEADER. EVENT_DESCRIPTOR) kazanmak:Verbose veya daha yüksek.

3. Diğer tüm durumlarda, olay bir ileti olarak kabul edilir.

### <a name="importance"></a>Önem
 Aşağıdaki tabloda olay düzeyinin işaretçi önemiyle nasıl eşleşiş olduğu açıklanmıştır.

|ETW Seviyesi|Eşzamanlı Görselleştirici nin Önemi|
|---------------|---------------------------------------|
|win:LogAlways|Normal|
|win:Kritik|Kritik|
|win:Hata|Kritik|
|win:Uyarı|Yüksek|
|win:Bilgilendirme|Normal|
|kazanmak:Verbose|Düşük|
|Kazanmaktan daha büyük:verbose|Düşük|

### <a name="series-name"></a>Seri adı
 Olay görev adı dizi adı için kullanılır. Olay için görev tanımlanmamışsa seri adı boştur.

### <a name="category"></a>Kategori
 Düzey kazanmak ise:Kritik veya kazan:Hata, kategori Uyarı (-1) olur. Aksi takdirde, kategori varsayılan (0) olur.

### <a name="text"></a>Metin
 Olay için printf türü biçimlendirilmiş bir metin iletisi tanımlanmışsa, işaretçiaçıklaması olarak görüntülenir. Aksi takdirde, açıklama olayın adı ve her yük alanının değeridir.

## <a name="customize-visualization-of-eventsource-events"></a>EventSource etkinliklerinin görselleştirmesini özelleştirme
 Aşağıdaki bölümlerde açıklandığı gibi, olayiçin uygun alanları ekleyerek EventSource olaylarının nasıl görüntüleneceğini özelleştirebilirsiniz.

### <a name="marker-type"></a>İşaretçi türü
 Olayı `cvType` temsil etmek için kullanılan işaretçi türünü denetlemek için bir bayt olan alanı kullanın. CvType için kullanılabilir değerler şunlardır:

|cvType değeri|Elde Eden İşaretleyici Türü|
|------------------|---------------------------|
|0|İleti|
|1|Yayılma Başlangıcı|
|2|Yayılma Sonu|
|3|Bayrak|
|Diğer tüm değerler|İleti|

### <a name="importance"></a>Önem
 Bir EventSource `cvImportance` etkinliğinin önem ayarını denetlemek için bir bayt olan alanı kullanabilirsiniz. Ancak, bir olayın görüntülenen önemini Düzeyini kullanarak denetlemenizi öneririz.

|cvImportance değeri|Eşzamanlı Görselleştirici nin Önemi|
|------------------------|---------------------------------------|
|0|Normal|
|1|Kritik|
|2|Yüksek|
|3|Yüksek|
|4|Normal|
|5|Düşük|
|Diğer tüm değerler|Düşük|

### <a name="series-name"></a>Seri adı
 EşzamanlıLık `cvSeries` Görselleştiricisi'nin bir EventSource olayına verdiği seri adını denetlemek için olay alanını, bir dizeyi kullanın.

### <a name="category"></a>Kategori
 EşzamanlıLık `cvCategory` Görselleştiricisinin Bir EventSource etkinliğine verdiği kategoriyi denetlemek için bir bayt olan alanı kullanın.

### <a name="text"></a>Metin
 EşzamanlıLık `cvTextW` Görselleştiricisinin Bir EventSource olayına verdiği açıklamayı denetlemek için alanı, bir dizeyi kullanın.

### <a name="spanid"></a>SpanID
 Olayların çiftleri maç için cvSpanid alanı, bir int kullanın. Bir yayılma süresini temsil eden her başlangıç/durdurma olayı çifti için değer benzersiz olmalıdır. Genellikle eşzamanlı kod için, bu anahtar (CvSpanID için <xref:System.Threading.Interlocked.Exchange%2A> kullanılan değer) doğru olduğundan emin olmak için eşitleme ilkel kullanımını gerektirir.

> [!NOTE]
> SpanID'nin yayılmayı yuvalamak, aynı iş parçacığı üzerinde kısmen çakışmalarına izin vermek veya bir iş parçacığı üzerinde başlayıp başka bir iş parçacığı üzerinde sona erdirmelerine izin vermek için SpanID kullanımı desteklenmez.

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlı görselleştirici işaretleri](../profiling/concurrency-visualizer-markers.md)