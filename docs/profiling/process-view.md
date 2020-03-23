---
title: Süreç Görünümü | Microsoft Dokümanlar
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: da3097c276557238e6f5b521f6f7d3231434cd10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772182"
---
# <a name="process-view"></a>İşlem Görünümü
İşlem görünümü, profil oluşturma çalışması sırasında yürütülen işlemler ve iş parçacıkları için profil oluşturma verilerini görüntüler.

 İşlemler ada göre listelenir. İş parçacıkları, onları oluşturan işlemin alt düğümleri olarak listelenir. İş parçacıkları, sözcük parçacığını başlatan işlevle veya sembol yoksa **[ntdll.dll]** etiketiyle adlandırılır.

 Sütun eklemek veya kaldırmak için görünüme sağ tıklayın ve ardından **Sütun Ekle/Kaldır'ı**seçin. Ayrıca, bir sütun adını tıklatarak verileri sıralayabilirsiniz. Daha fazla bilgi için [bkz: Rapor görünümü sütunlarını özelleştirin.](../profiling/how-to-customize-report-view-columns.md)

 İşlem görünümü sütunları, örnekleme ve enstrümantasyon yöntemleri kullanılarak oluşturulan veriler ve .NET bellek verilerini içeren veriler için aynıdır. Aşağıdaki tabloda sütun değerleri açıklanmaktadır.

|Sütun|Açıklama|
|------------|-----------------|
|**Benzersiz Kimlik**|İşleme veya iş parçacığına özgü bir profil oluşturucu tarafından oluşturulan tanımlayıcı.|
|**Kimliği**|İşlemin veya iş parçacığının sistem tarafından oluşturulan tanımlayıcısı.|
|**Adı**|İşlemin veya iş parçacığının adı.|
|**Başlangıç Zamanı**|Profil oluşturmanın başlangıcından işlemin veya iş parçacığının başlangıcına kadar milisaniye veya işlemci döngülerinin sayısı.|
|**Bitiş Saati**|Profil oluşturmanın başlangıcından işlemin veya iş parçacığının sonuna kadar milisaniye veya işlemci döngülerinin sayısı.|

## <a name="see-also"></a>Ayrıca bkz.
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
- [Enstrümantasyon yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)
