---
title: İşlem görünümü | Microsoft Docs
description: Işlem görünümünün profil oluşturma çalışması sırasında yürütülen işlemler ve iş parçacıkları için profil oluşturma verilerini nasıl görüntülediğini öğrenin.
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
ms.openlocfilehash: 27aaa8d043ffce98e5d3a03a57226478d49a634f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628335"
---
# <a name="process-view"></a>İşlem Görünümü
Işlem görünümü, profil oluşturma çalışması sırasında yürütülen işlemler ve iş parçacıkları için profil oluşturma verilerini görüntüler.

 Süreçler ada göre listelenir. İş parçacıkları, kendilerini oluşturan işlemin alt düğümleri olarak listelenir. İş parçacıkları, bir sembol yoksa, iş parçacığını Başlatan işlev veya **[ntdll.dll]** etiketi ile adlandırılır.

 Sütun eklemek veya kaldırmak için, görünümü sağ tıklayın ve ardından **sütun Ekle/Kaldır**' ı seçin. Ayrıca, bir sütun adına tıklayarak verileri sıralayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md).

 Işlem görünümünün sütunları, örnekleme ve izleme yöntemleri kullanılarak oluşturulan veriler ve .NET bellek verileri içeren veriler için aynıdır. Aşağıdaki tabloda sütun değerleri açıklanmaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Benzersiz Kimlik**|İşlem veya iş parçacığı için benzersiz olan profil oluşturucu tarafından oluşturulan bir tanımlayıcı.|
|**ID**|İşlemin veya iş parçacığının sistem tarafından oluşturulan tanıtıcısı.|
|**Ad**|İşlemin veya iş parçacığının adı.|
|**Başlangıç zamanı**|Profil oluşturmanın başından işlemin veya iş parçacığının başlangıcına kadar geçen milisaniye veya işlemci döngüsü sayısı.|
|**Bitiş zamanı**|Profil oluşturmanın başından işlemin veya iş parçacığının sonuna kadar geçen milisaniye veya işlemci döngüsü sayısı.|

## <a name="see-also"></a>Ayrıca bkz.
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
- [İzleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
- [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)
