---
title: Eşzamanlılık görselleştiricisi Işaretçileri | Microsoft Docs
description: 'Eşzamanlılık görselleştiricisi içindeki işaretçiler hakkında bilgi edinin. İşaretleyiciler, bir uygulama tarafından oluşturulan olayları temsil eden simgelerdir. Üç tür vardır: bayraklar, iletiler ve yayılma.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 12ed8b9b71fe8d0a8a5260069709ca1f8a2bad15c65869020d735f42f5af3447
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333541"
---
# <a name="concurrency-visualizer-markers"></a>Eşzamanlılık görselleştiricisi işaretçileri
Eşzamanlılık görselleştiricisi içinde işaretçiler, bir uygulamadaki olayları temsil eden simgelerdir.  Genellikle uygulama, bir uygulamadaki aşamaları veya oluşumları belirlemek için bu olayları oluşturur.  Olaylar, uygulama tarafından veya uygulama tarafından kullanılan kitaplıklar ve çalışma zamanları tarafından oluşturulabilir.

## <a name="kinds-of-markers"></a>İşaretçiler türleri
 Eşzamanlılık görselleştiricisi uygulama olaylarını temsil etmek için üç tür işaretçi kullanır: bayraklar, iletiler ve yayılmalar.

1. Uygulamanızda ilginç bir zaman noktası belirtmek için bir *bayrak* kullanın.  Örneğin, bir değişken değerinin belirli bir eşiğe ulaşmış olduğunu veya bir özel durumun oluşturulduğunu temsil eden bir bayrak kullanabilirsiniz.

2. *İleti* Ayrıca bir zaman noktası da işaretler, ancak bunu günlük stili izleme için kullanabilirsiniz.  Örneğin, bir günlük dosyasına kaydedilmiş olabilecek özellikler artık bir ileti çağrısına kaydırabilmenizi sağlayacak ve bunu Eşzamanlılık Görselleştiricisinin içinde görüntüleyebilmenizi sağlayabilir. Eşzamanlılık Görselleştiricisini Ayrıca bu verileri bir CSV dosyasına aktarmak için de kullanabilirsiniz.

3. Bir *yayılma* , uygulamanızdaki bir zaman aralığını temsil eder, örneğin aşamalarından biri.

## <a name="marker-linkage-to-threads"></a>İş parçacığına işaret bağlantısı
 İşaretçiler üreten her iş parçacığının ayrı bir zaman çizelgesi kanalı vardır.  İşaretleyici olayları oluşturmaktan sorumlu iş parçacığının KIMLIĞI, işaret kanalının açıklamasının yanında gösterilir.  İşaret kanalının sol tarafında gösterilen KIMLIK, geçerli işlemdeki başka bir iş parçacığının KIMLIĞIYLE eşleşir.

## <a name="marker-importance"></a>İşaret önemi
 İşaretçiler dört önem düzeyinden birine sahip olabilir: düşük, normal, yüksek ve kritik.  İşaret kaynaklarını önem düzeyine göre filtreleyebilirsiniz.  örneğin, yalnızca normal veya kritik öneme sahip belirli bir kaynağın işaretçilerini görmek isterseniz, filtreyi [gelişmiş Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunda yapılandırabilirsiniz. Bir işaretin önem derecesi, araç ipucunda ve [Işaretçiler raporunda](../profiling/markers-report.md)görüntülenir.

## <a name="marker-category"></a>İşaretleyici kategorisi
 İşaretleyici kategorisi, aynı kaynaktan gelen bir işaretleyici olayları grubunu belirtir.  Eşzamanlılık görselleştiricisi, bayrakların ve yayılmaları farklı kategorilerini ayırt etmek için renk kullanır. Eşzamanlılık Görselleştiricisini, belirli bir olay sağlayıcısından işaret olaylarını filtrelemek için kategorileri kullanacak şekilde yapılandırabilirsiniz.  filtreyi yapılandırmak için [gelişmiş Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunu kullanın.

## <a name="known-sources-of-markers"></a>Bilinen işaret kaynakları
 Tüm ETW sağlayıcıları, sağlayıcı belirli kısıtlamalara uygun olduğu sürece işaretçiler oluşturabilir. Eşzamanlılık Görselleştiricisi ' i işaretçiler için ek olay kaynaklarını dinleyecek şekilde yapılandırabilirsiniz. Varsayılan olarak, bu olay kaynaklarını dinler:

- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)

- [Görev Paralel Kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)

- [Veri akışı](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)

- [Paralel LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)

- [Eşzamanlılık Çalışma Zamanı](/cpp/parallel/concrt/concurrency-runtime)

- [Senaryo Işaretçisi desteği](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))

- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)

  çeşitli kaynaklardaki işaretlerin eşzamanlılık görselleştiricide görüntülenip görüntülenmeyeceğini denetlemek için, [gelişmiş Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusundaki işaretçiler sekmesini kullanabilirsiniz. bu, önemli ve kategoriye göre işaretleyiciler için filtre uygulayabilirsiniz.

## <a name="markers-from-eventsource"></a>EventSource 'tan işaretçiler
 Eşzamanlılık görselleştiricisi Ayrıca EventSource olaylarını gösterebilir.  Daha fazla bilgi için bkz. [EventSource olaylarını işaretçiler olarak görselleştirme](../profiling/visualizing-eventsource-events-as-markers.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Bayrak işaretçileri](../profiling/flag-markers.md)
- [İleti işaretçileri](../profiling/message-markers.md)
- [Aralık işaretçileri](../profiling/span-markers.md)
- [EventSource olaylarını işaretçiler olarak görselleştirin](../profiling/visualizing-eventsource-events-as-markers.md)