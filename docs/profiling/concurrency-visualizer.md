---
title: Eşzamanlılık görselleştiricisi | Microsoft Docs
description: Çok iş parçacıklı uygulamanızdaki iş parçacığı zamanlamasını gösteren grafikleri görmek için eşzamanlılık Görselleştiricisini kullanın, performans sorunlarını çözmenize yardımcı olur.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e6f36568568a59980316f3070f902027898e39e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720962"
---
# <a name="concurrency-visualizer"></a>Eşzamanlılık Görselleştiricisi

> [!NOTE]
> Eşzamanlılık görselleştiricisi, Visual Studio için isteğe bağlı bir uzantıdır. Aşağıdaki bağlantılardan eşzamanlılık görselleştiricisi ve eşzamanlılık görselleştiricisi koleksiyon araçlarını indirin:
>
> - [Visual Studio 2019 uzantısı Için eşzamanlılık görselleştiricisi](https://marketplace.visualstudio.com/items?itemName=Diagnostics.DiagnosticsConcurrencyVisualizer2019#overview) indirin.
> - [Visual Studio 2017 uzantısı Için eşzamanlılık görselleştiricisi](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview) indirin.
> - [Visual Studio 2015 uzantısı Için eşzamanlılık görselleştiricisi](https://marketplace.visualstudio.com/items?itemName=Diagnostics.ConcurrencyVisualizerforVisualStudio2015) indirin.
> - [Visual Studio 2015 Için eşzamanlılık görselleştiricisi koleksiyon araçlarını](https://www.microsoft.com/download/details.aspx?id=49103)indirin.
>
> [Eşzamanlılık görselleştiricisi Command-Line yardımcı programı (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) , komut satırından, Visual Studio 2015 Için eşzamanlılık görselleştiricisi içinde görüntüleyebileceğiniz izlemeleri toplamanıza olanak tanır. Araç, Visual Studio yüklü olmayan bilgisayarlarda kullanılabilir.

Çoklu iş parçacıklı uygulamanızın nasıl çalıştığını görmek için eşzamanlılık görselleştiricisi ' i kullanabilirsiniz. Eşzamanlılık görselleştiricisi içindeki görünümler, programınızdaki iş parçacıkları ve sistem için bir bütün olarak zamana bağlı ilişkileri gösteren grafik, tablo ve metin verileri sağlar. Performans sorunları, CPU kullanımı, iş parçacığı çekişmesi, platformlar arası iş parçacığı geçişi, eşitleme gecikmeleri, DirectX etkinliği, çakışan g/ç alanları ve diğer bilgilerin yerini bulmak için eşzamanlılık görselleştiricisi ' ni kullanabilirsiniz. Görünümler, grafik çıktısını yığınlar ve kaynak kodu çağırmak üzere bağlayarak üzerinde işlem yapmak için kullanabileceğiniz verileri sağlar.

> [!NOTE]
> Eşzamanlılık görselleştiricisi Web projelerini desteklemez.

Eşzamanlılık görselleştiricisi, [Windows Için olay izleme](/windows/win32/etw/event-tracing-portal) işlevselliğine bağımlıdır.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Kullanım Görünümü](../profiling/utilization-view.md)|Tüm işlemciler genelinde sistem etkinliğini görüntülemeyi ve çözümlemeyi açıklar.|
|[İş Parçacıkları Görünümü](../profiling/threads-view-parallel-performance.md)|Programınızdaki iş parçacıkları arasındaki etkileşimlerin nasıl analiz edileceğini açıklar.|
|[Çekirdekler Görünümü](../profiling/cores-view.md)|Çekirdekler arasında iş parçacığı geçişinin nasıl analiz edileceğini açıklar.|
|[Hatalı davranan çok iş parçacıklı uygulamalar için ortak desenler](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Birçok ortak deseni açıklar ve bunların eşzamanlılık görselleştiricisi içinde nasıl göründüğünü gösterir.|
|[Visual Studio blogda paralel geliştirme](/archive/blogs/visualizeparallel/)|Eşzamanlılık görselleştiricisi için ipuçları ve en iyi uygulamalar sağlar.|
|[Performans Raporu Görünümleri](../profiling/performance-report-views.md)|Visual Studio Profil Oluşturma Araçları raporları ve görünümleri için başvuru bilgileri sağlar.|
|[Eşzamanlılık Görselleştiricisi SDK](../profiling/concurrency-visualizer-sdk.md)|Eşzamanlılık görselleştiricisi içinde ek bilgileri göstermek için kaynak kodunuzun nasıl ekleneceğini açıklar.|
|[Eşzamanlılık görselleştiricisi komut satırı yardımcı programı (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Eşzamanlılık görselleştiricisi komut satırı yardımcı programının (CVCollectionCmd.exe), Visual Studio olmayan makinelerde izlemeleri toplamak ve işlemek için nasıl kullanılacağını açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)