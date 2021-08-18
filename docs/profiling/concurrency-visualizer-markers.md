---
title: Eşzamanlılık Görselleştiricisi İşaretçileri | Microsoft Docs
description: "Eşzamanlılık Görselleştiricisi'nde işaretçiler hakkında bilgi öğrenin. İşaretçiler, bir uygulama tarafından oluşturulan olayları temsil eden simgelerdir. Üç tür vardır: bayraklar, iletiler ve yayılmalar."
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
ms.openlocfilehash: 6ad086e4b17ebeb1e9ec3f04f56d102c5e6bc6cc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039598"
---
# <a name="concurrency-visualizer-markers"></a>Eşzamanlılık Görselleştiricisi işaretçileri
Eşzamanlılık Görselleştiricisi'nde işaretçiler, bir uygulamanın olaylarını temsil eden simgelerdir.  Genellikle, uygulama bir uygulamada aşamaları veya oluşumları tasarlamak için bu olayları üretir.  Olaylar uygulama tarafından veya uygulamanın kullandığı kitaplıklar ve çalışma zamanları tarafından oluşturabilir.

## <a name="kinds-of-markers"></a>İşaretçi türleri
 Eşzamanlılık Görselleştiricisi, uygulama olaylarını temsil etmek için üç tür işaretçi kullanır: bayraklar, iletiler ve yayılmalar.

1. Uygulamanıza *ilgi* çekici bir nokta belirtmek için bayrağını kullanın.  Örneğin, bir değişken değerinin belirli bir eşiğe ulaştığını veya bir özel durum olduğunu temsil etmek için bir bayrak kullanabilirsiniz.

2. İleti *aynı* zamanda bir zaman noktasını da işaretler, ancak bunu günlük stilinde izleme için kullanabilirsiniz.  Örneğin, bir günlük dosyasına nelerin çöpe atılmış olabileceğini artık bir ileti çağrısında sarmalayabilirsiniz; böylece dosyayı takip etmek ve Eşzamanlılık Görselleştiricisi'nde görüntülemek için. Bu verileri bir CSV dosyasına dışarı aktararak Eşzamanlılık Görselleştiricisi'yi de kullanabilirsiniz.

3. Bir *aralık,* uygulamanıza bir zaman aralığını (örneğin, aşamalarından birini) temsil eder.

## <a name="marker-linkage-to-threads"></a>İş parçacıklarına işaretçi bağlantısı
 İşaretleyiciler oluşturan her iş parçacığı ayrı bir zaman çizelgesi kanalına sahip olur.  İşaretçi olaylarını oluşturmakla sorumlu iş parçacığının kimliği, işaretçi kanalının açıklamasının yanında gösterilir.  İşaretçi kanalının sol tarafında gösterilen kimlik, geçerli işlemde yer alan başka bir iş parçacığının kimliğiyle eştir.

## <a name="marker-importance"></a>İşaretçi önemi
 İşaretçiler dört önem düzeyine sahip olabilir: düşük, normal, yüksek ve kritik.  İşaretçilerin kaynaklarını önem düzeyine göre filtreleysiniz.  Örneğin, yalnızca normal veya kritik öneme sahip olan belirli bir kaynaktan işaretçileri görmek için, Gelişmiş Etki Alanı iletişim [kutusunda Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) yapılandırabilirsiniz. İşaretçinin önemi araç ipucunda ve İşaretçiler [Raporu'nda görüntülenir.](../profiling/markers-report.md)

## <a name="marker-category"></a>İşaretçi kategorisi
 İşaretçi kategorisi, aynı kaynaktan gelen bir işaretçi olayları grubunu gösterir.  Eşzamanlılık Görselleştiricisi, farklı bayrak ve aralık kategorilerini ayırt etmek için rengi kullanır. Belirli bir olay sağlayıcısından gelen işaretleyici olaylarını filtrelemek için kategorileri kullanmak üzere Eşzamanlılık Görselleştiricisi'yi yapılandırabilirsiniz.  Filtreyi [yapılandırmak Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) Gelişmiş Erişim iletişim kutusunu kullanın.

## <a name="known-sources-of-markers"></a>İşaretçilerin bilinen kaynakları
 Sağlayıcı belirli kısıtlamalara bağlı olduğu sürece herhangi bir ETW sağlayıcısı işaretçiler üretebilirsiniz. Eşzamanlılık Görselleştiricisi'nin işaretçiler için ek olay kaynaklarını dinleyecek şekilde yapılandırarak. Varsayılan olarak şu olay kaynaklarını dinler:

- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)

- [Görev Paralel Kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)

- [Veri akışı](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)

- [Paralel LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)

- [Eşzamanlılık Çalışma Zamanı](/cpp/parallel/concrt/concurrency-runtime)

- [Senaryo İşaretçisi Desteği](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))

- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)

  Çeşitli kaynaklardan gelen işaretleyicilerin [](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) Eşzamanlılık Görselleştiricisi'nde görüntülendiğinden emin olmak için Gelişmiş Ayarlar iletişim kutusundaki İşaretçiler sekmesini kullanabilir ve işaretçileri önem ve kategoriye göre filtreleyebilirsiniz.

## <a name="markers-from-eventsource"></a>EventSource'tan işaretçiler
 Eşzamanlılık Görselleştiricisi, EventSource olaylarını da görüntüler.  Daha fazla bilgi için [bkz. EventSource olaylarını işaretçi olarak görselleştirme.](../profiling/visualizing-eventsource-events-as-markers.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Bayrak işaretçileri](../profiling/flag-markers.md)
- [İleti işaretçileri](../profiling/message-markers.md)
- [Yayma işaretçileri](../profiling/span-markers.md)
- [EventSource olaylarını işaretçi olarak görselleştirme](../profiling/visualizing-eventsource-events-as-markers.md)