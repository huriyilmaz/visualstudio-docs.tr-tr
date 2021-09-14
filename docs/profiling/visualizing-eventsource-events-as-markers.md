---
title: EventSource Olaylarını İşaretçi Olarak Görselleştirme | Microsoft Docs
description: Eşzamanlılık Görselleştiricisi'nin EventSource olaylarını işaretçi olarak görüntüleyeblir ve işaretçilerin nasıl görüntülenmiyor olduğunu kontrol etmeyi öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4a779f752a67853c620b3ce9da11ea9438d0d543
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725658"
---
# <a name="visualize-eventsource-events-as-markers"></a>EventSource olaylarını işaretçi olarak görselleştirme
Eşzamanlılık Görselleştiricisi, EventSource olaylarını işaretçi olarak görüntülenebilir ve işaretçilerin nasıl görüntülendiğinden siz de kontrol edin. EventSource işaretleyicilerini görüntülemek için Gelişmiş Giriş iletişim kutusunu kullanarak ETW sağlayıcısı [GUID Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) olun. Eşzamanlılık Görselleştiricisi, EventSource olaylarını Bayrak İşaretçileri, [Span](../profiling/span-markers.md) [Markers](../profiling/flag-markers.md)ve İleti İşaretçileri olarak temsil eden varsayılan [kuralları vardır.](../profiling/message-markers.md) Olaylara özel alanlar ekleyerek EventSource olaylarını özelleştirebilirsiniz. İşaretleyiciler hakkında daha fazla bilgi için [bkz. Eşzamanlılık Görselleştiricisi İşaretçileri.](../profiling/concurrency-visualizer-markers.md) EventSource olayları hakkında daha fazla bilgi için <xref:System.Diagnostics.Tracing> bkz. .

## <a name="default-visualization-of-eventsource-events"></a>EventSource olaylarının varsayılan görselleştirmesi
 Eşzamanlılık Görselleştiricisi varsayılan olarak EventSource olaylarını temsil etmek için aşağıdaki kuralları kullanır.

### <a name="marker-type"></a>İşaretçi türü

1. [Opcode win:Start](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) veya win:Stop olan olaylar sırasıyla bir aralığın başlangıcı veya sonu olarak kabul edilir.  İç içe geçmiş veya çakışan aralıklar görüntülenemiyor. Bir iş parçacığında başlayan ve başka bir iş parçacığında sona eren olay çiftleri görüntülenemiyor.

2. Opcode win:Start veya win:Stop olmayan bir olay, Düzeyi [](/windows/desktop/WES/defining-severity-levels) (win:Start veya Win:Stop) değilse işaretçi bayrağı EVENT_RECORD. EVENT_HEADER. EVENT_DESCRIPTOR) şu şekildedir: verbose veya daha yüksek.

3. Diğer tüm durumlarda, olay bir ileti olarak kabul edilir.

### <a name="importance"></a>Önem
 Aşağıdaki tablo, olay düzeyinin işaretçi önem düzeyiyle nasıl eşlen olduğunu tanımlar.

|ETW Düzeyi|Eşzamanlılık Görselleştiricisi Önemi|
|---------------|---------------------------------------|
|win:LogAlways|Normal|
|win:Critical|Kritik|
|win:Error|Kritik|
|win:Warning|Yüksek|
|win:Informational|Normal|
|win:Verbose|Düşük|
|Win'den büyük:ayrıntılı|Düşük|

### <a name="series-name"></a>Seri adı
 Seri adı için olayın görev adı kullanılır. Olay için hiçbir görev tanımlanmamışsa seri adı boştur.

### <a name="category"></a>Kategori
 Düzey win:Critical veya win:Error ise kategori Uyarı (-1) olur. Aksi takdirde kategori varsayılan değerdir (0).

### <a name="text"></a>Metin
 Olay için printf türünde biçimlendirilmiş bir metin iletisi tanımlanmışsa, İşaretçinin açıklaması olarak görüntülenir. Aksi takdirde, açıklama olayın adı ve her yük alanı değeridir.

## <a name="customize-visualization-of-eventsource-events"></a>EventSource olaylarının görselleştirmesini özelleştirme
 EventSource olaylarını, aşağıdaki bölümlerde açıklandığı gibi olaylarına uygun alanları ekleyerek özelleştirebilirsiniz.

### <a name="marker-type"></a>İşaretçi türü
 Olayı `cvType` temsil etmek için kullanılan işaretçinin nasıl olduğunu kontrol etmek için bir bayt alanını kullanın. cvType için kullanılabilir değerler şu şekildedir:

|cvType değeri|Sonuçta elde edilen İşaretçi Türü|
|------------------|---------------------------|
|0|İleti|
|1|Span Start|
|2|Yayma Bitişi|
|3|Bayrak|
|Diğer tüm değerler|İleti|

### <a name="importance"></a>Önem
 EventSource olayı için önem ayarını kontrol etmek için bir `cvImportance` bayt alanını kullanabilirsiniz. Ancak, Düzeyini kullanarak bir olayın görüntülenen önem derecesini denetlemenizi öneririz.

|cvImportance değeri|Eşzamanlılık Görselleştiricisi Önemi|
|------------------------|---------------------------------------|
|0|Normal|
|1|Kritik|
|2|Yüksek|
|3|Yüksek|
|4|Normal|
|5|Düşük|
|Diğer tüm değerler|Düşük|

### <a name="series-name"></a>Seri adı
 Eşzamanlılık Görselleştiricisi'nin bir EventSource olayına verdiği seri adını kontrol etmek için bir dize `cvSeries` olan olay alanını kullanın.

### <a name="category"></a>Kategori
 Eşzamanlılık Görselleştiricisi'nin bir EventSource olayına verdiği kategoriyi kontrol etmek `cvCategory` için bir bayt alanını kullanın.

### <a name="text"></a>Metin
 Eşzamanlılık `cvTextW` Görselleştiricisi'nin bir EventSource olayına verdiği açıklamayı kontrol etmek için bir dize olan alanını kullanın.

### <a name="spanid"></a>SpanID
 Olay çiftlerini eşleşmek için bir int olan cvSpanId alanını kullanın. Bir aralığı temsil eden her başlatma/durdurma olay çifti için değer benzersiz olmalıdır. Genellikle eşzamanlı kod için bu, anahtarın (CvSpanID için kullanılan değer) doğru olduğundan emin olmak gibi eşitleme temelleri <xref:System.Threading.Interlocked.Exchange%2A> kullanımını gerektirir.

> [!NOTE]
> SpanID'nin span'ları iç içe yerleştirmesi, aynı iş parçacığında kısmen çakışmasına izin vermeleri veya bir iş parçacığında başlatmalarına ve başka bir iş parçacığında sona ermelerine izin verme kullanımı desteklenmiyor.

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık görselleştiricisi işaretçileri](../profiling/concurrency-visualizer-markers.md)