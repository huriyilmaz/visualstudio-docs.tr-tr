---
title: Arayan-çağrılan görünümü | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779720"
---
# <a name="callercallee-view"></a>Arayan/Aranan görünümü
Arayan/çağrılan görünümü seçili bir işlev ve üst ve alt işlevleri için profil oluşturma bilgilerini görüntüler. Arayan/çağrılan görünümü üç kılavuz içerir:

 **Geçerli işlev** ortadaki kılavuzda görüntülenir ve seçili işlev için profil oluşturma bilgilerini gösterir. Değerler, profil oluşturma çalıştırmasında toplanan işleve yapılan tüm çağrıları içerir.

 **Geçerli işlevi çağıran işlevler** üst kılavuzda görüntülenir ve çağıran (üst) işlevden çağrılar tarafından oluşturulan seçili (geçerli) işlevin değerlerinin sayısını gösterir.

 **Geçerli işlev tarafından çağrılan işlevler** alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldığında seçili işlevin aranan (alt) işlevlerine ilişkin profil oluşturma bilgilerini gösterir.

 Arayan/çağrılan görünümünde kullanılabilen sütunlar, verileri toplamak için kullanılan profil oluşturma yöntemine (örnekleme veya izleme) ve .NET bellek verilerinin profil oluşturma çalıştırmasında toplanıp toplanmadığına bağlıdır.

 Görünümün diğer iki bölümünde listelenen işlevlerden herhangi birine çift tıklayarak rapor görünümünün ikinci bölümünde geçerli Işlev olarak farklı bir işlev seçebilirsiniz... Rapor görünümü değişiklikleri yansıtacak şekilde otomatik olarak güncelleştirilir.

 Sütun adları ' na tıklayarak verileri sıralayabilirsiniz. Çağıran/çağrılan görünümüne ek sütunlar eklenebilir. Daha fazla bilgi için bkz. [nasıl yapılır: rapor görünümü sütunlarını özelleştirme](../profiling/how-to-customize-report-view-columns.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Çağıran/çağrılan görünümü-örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)
- [Arayan/çağrılan görünümü-izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)
- [Arayan/Aranan görünümü-.NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Arayan/Aranan görünümü-.NET Bellek Örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/çağrılan görünümü-çekişme verileri](../profiling/caller-callee-view-contention-data.md)
