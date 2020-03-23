---
title: Eşzamanlı Görselleştirici İşaretleyiciler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markersui
ms.assetid: c4692d17-6cd2-4ad1-8590-d7275c771c70
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab5e4b65db5c3d96b16a68a7b8e21a2786b9110b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "63001058"
---
# <a name="concurrency-visualizer-markers"></a>Eşzamanlı Görselleştirici işaretleri
Eşzamanlılık Görselleştiricisi'nde işaretçiler, bir uygulamadaki olayları temsil eden simgelerdir.  Genellikle, uygulama, bir uygulamadaki aşamaları veya oluşumları belirlemek için bu olayları oluşturur.  Etkinlikler uygulama veya uygulamanın kullandığı kitaplıklar ve çalışma saatleri tarafından oluşturulabilir.

## <a name="kinds-of-markers"></a>İşaretleyici çeşitleri
 Eşzamanlılık Görselleştiricisi, uygulama olaylarını temsil etmek için üç tür işaretçi kullanır: bayraklar, iletiler ve yayılmalar.

1. Uygulamanızda ilginç bir noktayı belirtmek için bir *bayrak* kullanın.  Örneğin, değişken bir değerin belirli bir eşiğe ulaştığını veya bir özel durum atıldığını temsil etmek için bir bayrak kullanabilirsiniz.

2. İleti *message* de zaman içinde bir nokta işaretler, ancak günlük stili izleme için kullanabilirsiniz.  Örneğin, bir günlük dosyasına atılmış olabilecekleri, artık bir ileti çağrısına sarıp, böylece onu izleyip EşzamanlıLık Görselleştiricisinde görüntüleyebilirsiniz. Bu verileri bir CSV dosyasına aktarmak için Eşzamanlılık Görselleştiricisini de kullanabilirsiniz.

3. *Bir yayılma,* uygulamanızdaki bir zaman aralığını (örneğin, onun aşamalarından birini) temsil eder.

## <a name="marker-linkage-to-threads"></a>İş parçacıklarına işaretleyici bağlantısı
 İşaretçileri oluşturan her iş parçacığının ayrı bir zaman çizelgesi kanalı vardır.  İşaretçi olayları oluşturmaktan sorumlu iş parçacığının kimliği işaretleyici kanalının açıklamasının yanında gösterilir.  İşaretleyici kanalının sol tarafında gösterilen kimlik, geçerli işlemdeki başka bir iş parçacığının kimliğiyle eşleşir.

## <a name="marker-importance"></a>Marker önemi
 İşaretleyiciler dört önem düzeyine sahip olabilir: düşük, normal, yüksek ve kritik.  İşaretçilerin kaynaklarını önem düzeyine göre filtreleyebilirsiniz.  Örneğin, yalnızca normal veya kritik öneme sahip belirli bir kaynaktan işaretçilergörmek istiyorsanız, [Gelişmiş Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusundafiltreyi yapılandırabilirsiniz. Bir işaretçinin önemi araç ucunda ve [İşaretçiler Raporu'nda](../profiling/markers-report.md)görüntülenir.

## <a name="marker-category"></a>İşaretleyici kategorisi
 İşaretçi kategorisi, aynı kaynaktan gelen işaretçi olayları grubunu gösterir.  Eşzamanlılık Görselleştiricisi, farklı bayrak ve yayılma kategorilerini ayırt etmek için renk kullanır. Eşpara Birimi Görselleştiricisini, belirli bir olay sağlayıcısının işaretçi olaylarını filtrelemek için kategorileri kullanacak şekilde yapılandırabilirsiniz.  Filtreyi yapılandırmak için [Gelişmiş Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusunu kullanın.

## <a name="known-sources-of-markers"></a>Bilinen işaretleyici kaynakları
 Sağlayıcı belirli kısıtlamalara uyduduğu sürece, herhangi bir ETW sağlayıcısı işaretçiler oluşturabilir. Eşpara Birimi Görselleştiricisini işaretçiler için ek olay kaynaklarını dinleyecek şekilde yapılandırabilirsiniz. Varsayılan olarak, bu olay kaynaklarını dinler:

- [Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)

- [Görev Paralel Kitaplığı (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)

- [Veri akışı](/dotnet/standard/parallel-programming/dataflow-task-parallel-library)

- [Paralel LINQ (PLINQ)](/dotnet/standard/parallel-programming/parallel-linq-plinq)

- [Eşzamanlılık Çalışma Zamanı](/cpp/parallel/concrt/concurrency-runtime)

- [Senaryo İşaretleyici Desteği](/previous-versions/visualstudio/visual-studio-2010/dd984115\(v\=vs.100\))

- [C++ AMP (C++ Accelerated Massive Parallelism)](/cpp/parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism)

  Çeşitli kaynaklardan gelen işaretçilerin Eşzamanlılık Görselleştiricisinde görüntülenip görüntülenmediğini denetlemek için [Gelişmiş Ayarlar](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) iletişim kutusundaki İşaretçiler sekmesini kullanabilirsiniz ve önem ve kategoriye göre işaretçilere filtre uygulayabilirsiniz.

## <a name="markers-from-eventsource"></a>EventSource'dan İşaretçiler
 EşzamanlıLık Görselleştiricisi, EventSource olaylarını da görüntüleyebilir.  Daha fazla bilgi için [EventSource olaylarını işaretleyici olarak görselleştir'e](../profiling/visualizing-eventsource-events-as-markers.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.
- [Bayrak işaretleri](../profiling/flag-markers.md)
- [İleti işaretçileri](../profiling/message-markers.md)
- [Yayılma işaretleri](../profiling/span-markers.md)
- [EventSource olaylarını işaretleyici olarak görselleştirin](../profiling/visualizing-eventsource-events-as-markers.md)