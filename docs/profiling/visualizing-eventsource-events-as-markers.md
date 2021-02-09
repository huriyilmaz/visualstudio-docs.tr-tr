---
title: EventSource olaylarını Işaretçiler olarak görselleştirme | Microsoft Docs
description: Eşzamanlılık görselleştiricinin EventSource olaylarını işaretçiler olarak görüntüleyip göstermediğini ve işaretçilerin nasıl görüntülendiğini kontrol edebilirsiniz.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8c919c72cbf06faccf5bb39b0753533f2b2a441f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890532"
---
# <a name="visualize-eventsource-events-as-markers"></a>EventSource olaylarını işaretçiler olarak görselleştirin
Eşzamanlılık görselleştiricisi, EventSource olaylarını işaretçiler olarak görüntüleyebilir ve işaretçilerin nasıl görüntüleneceğini denetleyebilir. EventSource işaretleyicilerini görüntülemek için, [Gelişmiş ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunu kullanarak ETW sağlayıcısı GUID 'sini kaydedin. Eşzamanlılık görselleştiricisi, olay [işaretçileri](../profiling/flag-markers.md), [span Işaretçileri](../profiling/span-markers.md)ve [ileti işaretçileri](../profiling/message-markers.md)olarak EventSource olaylarını temsil eden varsayılan kurallara sahiptir. Olaylara özel alanlar ekleyerek EventSource olaylarının nasıl görüntülendiğini özelleştirebilirsiniz. İşaretleyiciler hakkında daha fazla bilgi için bkz. [Eşzamanlılık görselleştiricisi işaretçileri](../profiling/concurrency-visualizer-markers.md). EventSource olayları hakkında daha fazla bilgi için bkz <xref:System.Diagnostics.Tracing> ..

## <a name="default-visualization-of-eventsource-events"></a>EventSource olaylarının varsayılan görselleştirmesi
 Varsayılan olarak eşzamanlılık görselleştiricisi, EventSource olaylarını göstermek için aşağıdaki kuralları kullanır.

### <a name="marker-type"></a>İşaret türü

1. [Işlem kodu](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) Win: Start veya Win: Stop olan olaylar sırasıyla bir yayılma alanının başlangıcında veya sonunda olarak değerlendirilir.  İç içe yerleştirilmiş veya çakışan yayılma görüntülenemez. Bir iş parçacığında başlayan ve diğeri üzerinde biten olay çiftleri görüntülenemez.

2. Işlem kodu ne bir Win: Start veya Win: Stop olan bir olay, [düzeyi](/windows/desktop/WES/defining-severity-levels) (EVENT_RECORD alanı olmadığı sürece işaret bayrağı olarak değerlendirilir. EVENT_HEADER. EVENT_DESCRIPTOR) WIN: ayrıntılı veya daha yüksek.

3. Diğer tüm durumlarda, olay ileti olarak kabul edilir.

### <a name="importance"></a>Önem
 Aşağıdaki tabloda, olay düzeyinin işaret önem derecesine göre nasıl eşlendiği tanımlanmaktadır.

|ETW düzeyi|Eşzamanlılık görselleştiricisi önem derecesi|
|---------------|---------------------------------------|
|Win: LogAlways|Normal|
|Win: kritik|Kritik|
|Win: hata|Kritik|
|Win: uyarı|Yüksek|
|Win: bilgilendirici|Normal|
|Win: verbose|Düşük|
|Win 'dan büyük: ayrıntılı|Düşük|

### <a name="series-name"></a>Seri adı
 Etkinliğin görev adı, seri adı olarak kullanılır. Olay için hiçbir görev tanımlanmamışsa, seri adı boştur.

### <a name="category"></a>Kategori
 Düzey Win: Critical veya Win: Error ise, kategori uyar (-1). Aksi halde kategori varsayılandır (0).

### <a name="text"></a>Metin
 Olay için bir printf-Type biçimli metin iletisi tanımlanmışsa, Işaretin açıklaması olarak görüntülenir. Aksi takdirde, açıklama olayın adı ve her yük alanının değeri olur.

## <a name="customize-visualization-of-eventsource-events"></a>EventSource olaylarını görselleştirmeyi özelleştirme
 Aşağıdaki bölümlerde açıklandığı gibi olaya uygun alanları ekleyerek EventSource olaylarının nasıl görüntülendiğini özelleştirebilirsiniz.

### <a name="marker-type"></a>İşaret türü
 `cvType`Olayı temsil etmek için kullanılan işaretleyici türünü denetlemek için bir bayt alanı kullanın. CvType için kullanılabilir değerler şunlardır:

|cvType değeri|Sonuç Işaretçisi türü|
|------------------|---------------------------|
|0|İleti|
|1|Yayılma başlangıcı|
|2|Yayılma bitişi|
|3|Bayrak|
|Diğer tüm değerler|İleti|

### <a name="importance"></a>Önem
 Bir `cvImportance` EventSource olayının önem derecesini denetlemek için, bir bayt alanını kullanabilirsiniz. Bununla birlikte, bir etkinliğin görüntülenen önemini düzeyini kullanarak denetlemenizi öneririz.

|Cvimportans değeri|Eşzamanlılık görselleştiricisi önem derecesi|
|------------------------|---------------------------------------|
|0|Normal|
|1|Kritik|
|2|Yüksek|
|3|Yüksek|
|4|Normal|
|5|Düşük|
|Diğer tüm değerler|Düşük|

### <a name="series-name"></a>Seri adı
 `cvSeries`Eşzamanlılık görselleştiricinin bir EventSource olayına verdiği seri adını denetlemek için bir dize olan olay alanını kullanın.

### <a name="category"></a>Kategori
 `cvCategory`Eşzamanlılık görselleştiricinin bir EventSource olayına verdiği kategoriyi denetlemek için bir bayt alanını kullanın.

### <a name="text"></a>Metin
 `cvTextW`Eşzamanlılık görselleştiricinin bir EventSource olayına verdiği açıklamayı denetlemek için bir dize alanı kullanın.

### <a name="spanid"></a>Spanıd
 Olay çiftlerini eşleştirmek için bir int olan CvSpanID alanını kullanın. Bir yayılımı temsil eden her bir başlatma/durdurma olayı çiftinin değeri benzersiz olmalıdır. Genellikle eşzamanlı kod için, <xref:System.Threading.Interlocked.Exchange%2A> anahtarın (CvSpanID için kullanılan değer) doğru olduğundan emin olmak gibi eşitleme temelleri kullanımını gerektirir.

> [!NOTE]
> İç içe yayılma için Spanıd kullanımı, aynı iş parçacığında kısmen örtüşmesine izin vermek veya bir iş parçacığında başlayıp bitmelerine izin vermek

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık görselleştiricisi işaretçileri](../profiling/concurrency-visualizer-markers.md)