---
title: Eşzamanlılık Görselleştiricisi | Microsoft Docs
description: Çok iş parçacıklı uygulamanıza iş parçacığı zamanlamasını göstermek ve performans sorunlarını çözmenize yardımcı olan grafikleri görmek için Eşzamanlılık Görselleştirici'yi kullanın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ec7e50f73d09202a238acbbad894f422b6877e6f27d032583b44f75e5d1fa311
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355562"
---
# <a name="concurrency-visualizer"></a>Eşzamanlılık Görselleştiricisi

> [!NOTE]
> Eşzamanlılık Görselleştiricisi, Visual Studio. Aşağıdaki bağlantılardan Eşzamanlılık Görselleştiricisi'nin ve Eşzamanlılık Görselleştiricisi Koleksiyon Araçları'nın indirin:
>
> - Visual Studio [2019 uzantısı için Eşzamanlılık Görselleştiricisi'yi](https://marketplace.visualstudio.com/items?itemName=Diagnostics.DiagnosticsConcurrencyVisualizer2019#overview) indirin.
> - Visual Studio [2017 uzantısı için Eşzamanlılık Görselleştiricisi'yi](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview) indirin.
> - Visual Studio [2015 uzantısı için Eşzamanlılık Görselleştiricisi'yi](https://marketplace.visualstudio.com/items?itemName=Diagnostics.ConcurrencyVisualizerforVisualStudio2015) indirin.
> - Visual Studio [2015 için Eşzamanlılık Görselleştiricisi Koleksiyon Araçları'Visual Studio indirin.](https://www.microsoft.com/download/details.aspx?id=49103)
>
> Eşzamanlılık Görselleştiricisi Command-Line Yardımcı Programı [(CVCollectionCmd),](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) Visual Studio 2015 için Eşzamanlılık Görselleştiricisi'nde görüntüleyebilirsiniz komut satırlarından izlemeleri toplamaya olanak sağlar. Araç, herhangi bir yüklemesi yüklü Visual Studio kullanılabilir.

Çok iş parçacıklı uygulamanın nasıl performans sergileyebli olduğunu görmek için Eşzamanlılık Görselleştiricisi'yi kullanabilirsiniz. Eşzamanlılık Görselleştiricisi'nde görünümler, program ve sistem içinde iş parçacıkları arasındaki zamana bağlı ilişkileri bir bütün olarak gösteren grafik, tablosal ve metinsel veriler sağlar. Performans sorunlarını, CPU az kullanımını, iş parçacığı çakışmasını, çekirdekler arası iş parçacığı geçişi, eşitleme gecikmelerini, DirectX etkinliğini, çakışan I/O alanlarını ve diğer bilgileri bulmak için Eşzamanlılık Görselleştirici'yi kullanabilirsiniz. Görünümler, grafik çıkışını çağrı yığınlarına ve kaynak koduna bağarak üzerinde eyleme geçebilirsiniz verileri sağlar.

> [!NOTE]
> Eşzamanlılık Görselleştiricisi Web projelerini desteklemez.

Eşzamanlılık Görselleştiricisi, olay izleme [özelliği için olay Windows](/windows/win32/etw/event-tracing-portal) temel almaktadır.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Kullanım Görünümü](../profiling/utilization-view.md)|Tüm işlemciler genelinde sistem etkinliğini görüntülemeyi ve analiz etme hakkında bilgi sağlar.|
|[İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)|Programda iş parçacıkları arasındaki etkileşimleri analiz etme hakkında bilgi sağlar.|
|[Çekirdekler Görünümü](../profiling/cores-view.md)|Çekirdekler arasında iş parçacığı geçişini çözümlemeyi açıklar.|
|[Hatalı davranan çok iş parçacıklı uygulamalar için ortak desenler](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Çeşitli yaygın desenleri açıklar ve Eşzamanlılık Görselleştiricisi'nde nasıl görüneceklerini gösterir.|
|[Visual Studio'da Paralel Geliştirme blogu](/archive/blogs/visualizeparallel/)|Eşzamanlılık Görselleştiricisi için ipuçları ve en iyi yöntemler sağlar.|
|[Performans Raporu Görünümleri](../profiling/performance-report-views.md)|Raporların ve raporların görünümleri için başvuru Visual Studio Profil Oluşturma Araçları.|
|[Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)|Eşzamanlılık Görselleştiricisi'nde ek bilgileri görüntülemek için kaynak kodunuzun nasıl takip edildiklerini açıklar.|
|[Eşzamanlılık Görselleştirici komut satırı yardımcı programı (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Eşzamanlılık Görselleştiricisi komut satırı yardımcı programını (CVCollectionCmd.exe) kullanarak izlemeleri toplamayı ve işlemeyi Visual Studio.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)