---
title: Eşzamanlı lık Görselleştiricisi | Microsoft Dokümanlar
ms.date: 07/11/2017
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3b4e151db08ad5490ed6238223d553f9e76aa0f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77192409"
---
# <a name="concurrency-visualizer"></a>Eşzamanlılık Görselleştiricisi

> [!NOTE]
> Eşzamanlılık Görselleştiricisi Visual Studio'nun isteğe bağlı bir uzantısıdır. Eşzamanlılık Görselleştiricisi ve Eşzamanlılık Görselleştiricisi Toplama Araçlarını aşağıdaki bağlantılardan indirin:
>
> - Visual [Studio 2019](https://marketplace.visualstudio.com/items?itemName=Diagnostics.DiagnosticsConcurrencyVisualizer2019#overview) uzantısı için Eşzamanlı Görselleştirici'yi indirin.
> - Visual [Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview) uzantısı için Eşzamanlı Görselleştirici'yi indirin.
> - Visual [Studio 2015](https://marketplace.visualstudio.com/items?itemName=Diagnostics.ConcurrencyVisualizerforVisualStudio2015) uzantısı için Eşzamanlı Görselleştirici'yi indirin.
> - Visual [Studio 2015 için EşzamanlıLık Görselleştirici Toplama Araçlarını](https://www.microsoft.com/download/details.aspx?id=49103)Indirin.
>
> [Eşzamanlı Visualizer Command-Line Utility (CVCollectionCmd),](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) Visual Studio 2015 için EşzamanlıLık Görselleştiricisi'nde görüntülediğiniz komut satırından izlemeler toplamanızı sağlar. Araç Visual Studio yüklü olmayan bilgisayarlarda kullanılabilir.

Çok iş parçacığı uygulamanızın nasıl performans gösterdiğini görmek için Eşzamanlılık Görselleştiricisini kullanabilirsiniz. Eşzamanlılık Görselleştiricisi'ndeki görünümler, programınızdaki iş parçacıkları ile sistem arasındaki zamansal ilişkileri bir bütün olarak gösteren grafiksel, eşzamanlı ve metinsel veriler sağlar. Eşzamanlılık Görselleştiricisini performans darboğazlarını, CPU az kullanımı, iş parçacığı çekişmesini, çapraz çekirdekli iş parçacığı geçişini, eşitleme gecikmelerini, DirectX etkinliğini, çakışan G/Ç alanlarını ve diğer bilgileri bulmak için kullanabilirsiniz. Görünümler, grafik çıktısını arama yığınlarına ve kaynak koduna bağlayarak hareket edebileceğiniz veriler sağlar.

> [!NOTE]
> Eşzamanlılık Görselleştiricisi Web projelerini desteklemez.

EşzamanlıLık Görselleştiricisi, [Windows](/windows/win32/etw/event-tracing-portal) için Olay İzleme işlevine dayanır.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Kullanım Görünümü](../profiling/utilization-view.md)|Tüm işlemciler arasında sistem etkinliğini görüntüleme ve çözümleme yi açıklar.|
|[İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)|Programınızdaki iş parçacıkları arasındaki etkileşimleri nasıl çözümleyeceklerini açıklar.|
|[Çekirdekler Görünümü](../profiling/cores-view.md)|Çekirdekler arasında iş parçacığı geçişini nasıl çözümlenebildiğini açıklar.|
|[Kötü şekilde kullanılan çok iş parçacığı uygulamaları için ortak desenler](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Çeşitli ortak desenleri açıklar ve Eşzamanlılık Görselleştiricisinde nasıl göründüklerini gösterir.|
|[Visual Studio blogunda Paralel Gelişim](https://blogs.msdn.microsoft.com/visualizeparallel/)|Eşzamanlılık Görselleştiricisi için ipuçları ve en iyi uygulamalar sağlar.|
|[Performans Raporu Görünümleri](../profiling/performance-report-views.md)|Visual Studio Profil Oluşturma Araçları raporları ve görünümleri için referans bilgileri sağlar.|
|[Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)|Eşzamanlılık Görselleştiricisi'nde ek bilgileri görüntülemek için kaynak kodunuzu nasıl enstrümanilen açıklar.|
|[Eşzamanlı Visualizer komut satırı yardımcı programı (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Visual Studio'su olmayan makinelerde izlemeleri toplamak ve işlemek için EşzamanlıLık Visualizer komut satırı yardımcı programını (CVCollectionCmd.exe) nasıl kullanacağımı açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Profil Oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
