---
title: İşlem Görünümü | Microsoft Docs
description: İşlem görünümünün profil oluşturma çalıştırması sırasında yürütülen işlemler ve iş parçacıkları için profil oluşturma verilerini nasıl görüntüley olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.process
helpviewer_keywords:
- performance tools reports, process view
- Process view
- performance tools, process view
- Profiling Tools,process view
- Profiling Tools,process report
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3415e235dae67fbf9f69c50242d4e9187cd45ed9ef1d4830736081c3338a8d55
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121316025"
---
# <a name="process-view"></a>İşlem Görünümü
İşlem görünümü, profil oluşturma çalıştırması sırasında yürütülen işlemler ve iş parçacıkları için profil oluşturma verilerini görüntüler.

 İşlemler ad ile listelenir. İş parçacıkları, bunları oluşturan sürecin alt düğümleri olarak listelenir. İş parçacıkları, iş parçacığını başlatan işlev tarafından veya herhangi bir simge **yoksa [ntdll.dll]** etiketiyle adlandırılmıştır.

 Sütun eklemek veya kaldırmak için görünüme sağ tıklayın ve ardından Sütun **Ekle/Kaldır'ı seçin.** Ayrıca, bir sütun adına tıklayarak verileri sıraabilirsiniz. Daha fazla bilgi için [bkz. Nasıl ekleyebilirsiniz: Rapor görünümü sütunlarını özelleştirme.](../profiling/how-to-customize-report-view-columns.md)

 İşlem görünümünün sütunları, örnekleme ve ölçüm yöntemleri kullanılarak oluşturulan veriler ve .NET bellek verilerini içeren veriler için aynıdır. Aşağıdaki tabloda sütun değerleri açık almaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Benzersiz Kimlik**|İşlem veya iş parçacığı için benzersiz olan profil oluşturma tarafından oluşturulan tanımlayıcı.|
|**ID**|İşlem veya iş parçacığının sistem tarafından oluşturulan tanımlayıcısı.|
|**Ad**|İşlem veya iş parçacığının adı.|
|**Başlangıç Saati**|Profil oluşturmanın başlamasından işlem veya iş parçacığının başlangıcına kadar olan milisaniye veya işlemci döngüsü sayısı.|
|**Bitiş Zamanı**|Profil oluşturmanın başlamasından işlem veya iş parçacığının sonuna kadar olan milisaniye veya işlemci döngüsü sayısı.|

## <a name="see-also"></a>Ayrıca bkz.
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
- [Ölçüm izleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
