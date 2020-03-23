---
title: Arayan-Callee Görünümü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.callercallee
helpviewer_keywords:
- profiling tools, reports, Caller/Callee view
- profiling tools, Caller/Callee view
- performance reports, Caller/Callee view
- Caller/Callee view
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bab816a0b71adef190a7d919b5ada7138a6a0e7c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779720"
---
# <a name="callercallee-view"></a>Arayan/Aranan görünümü
Arayan/Callee görünümü, seçili bir işlev ve üst ve alt işlevleri için profil oluşturma bilgilerini görüntüler. Arayan/Callee görünümü üç ızgara içerir:

 **Geçerli işlev** orta kılavuzda görüntülenir ve seçili işleviçin profil oluşturma bilgilerini gösterir. Değerler, profil oluşturma çalışmasında toplanan işleve yapılan tüm çağrıları içerir.

 **Geçerli işlev olarak adlandırılan işlevler** üst kılavuzda görüntülenir ve arayan (üst) işlevinden gelen çağrılar tarafından oluşturulan seçili (geçerli) işlevin değerlerinin sayısını gösterir.

 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldığında seçili işlevin callee (alt) işlevleri için profil oluşturma bilgilerini gösterir.

 Arayan/Callee görünümünde kullanılabilen sütunlar, verileri toplamak için kullanılan profil oluşturma yöntemine (örnekleme veya enstrümantasyon) ve .NET bellek verilerinin profil oluşturma çalışmasında toplanıp toplanmadığına bağlıdır.

 Görünümün diğer iki bölümünde listelenen işlevlerden herhangi birini çift tıklatarak Rapor görünümünün orta kısmında geçerli işlev olmak için farklı bir işlev seçebilirsiniz. Rapor görünümü değişiklikleri yansıtacak şekilde otomatik olarak güncelleştirilir.

 Sütun adlarını tıklatarak verileri sıralayabilirsiniz. Arayan/Callee görünümüne ek sütunlar eklenebilir. Daha fazla bilgi için [bkz: Rapor görünümü sütunlarını özelleştirin.](../profiling/how-to-customize-report-view-columns.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Arayan/Callee görünümü - veri örneklemesi](../profiling/caller-callee-view-sampling-data.md)
- [Arayan/Callee görünümü - enstrümantasyon verileri](../profiling/caller-callee-view-instrumentation-data.md)
- [Arayan/Callee görünümü - .NET bellek enstrümantasyon verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Arayan/Callee görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Callee görünümü - çekişme verileri](../profiling/caller-callee-view-contention-data.md)
