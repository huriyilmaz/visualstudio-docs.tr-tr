---
description: Çağıran/Çağrılı görünümü seçilen bir işlev ve üst ve alt işlevleri için profil oluşturma bilgilerini görüntüler.
title: Caller-Callee Görünüm | Microsoft Docs
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
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c6f7999b6b81316a28e329a3691d00f2acf5ba15
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142396"
---
# <a name="callercallee-view"></a>Arayan/Aranan görünümü
Çağıran/Çağrılı görünümü seçilen bir işlev ve üst ve alt işlevleri için profil oluşturma bilgilerini görüntüler. Çağıran/Çağrılı görünümü üç kılavuz içerir:

 **Geçerli işlev** orta kılavuzda görüntülenir ve seçilen işlev için profil oluşturma bilgilerini gösterir. Değerler, profil oluşturma çalıştırması içinde toplanan tüm işlev çağrılarını içerir.

 **Geçerli işlevi çağıran** işlevler üst kılavuzda görüntülenir ve çağıranın (üst) işlevinden gelen çağrılar tarafından oluşturulan seçili (geçerli) işlevin değerlerinin sayısını gösterir.

 **Geçerli işlev tarafından** çağrılan işlevler alt kılavuzda görüntülenir ve alt işlev geçerli işlev tarafından çağrıldıklarında seçili işlevin çağrılır (alt) işlevleri için profil oluşturma bilgilerini gösterir.

 Çağıran/Çağrılım görünümünde kullanılabilen sütunlar, verileri toplamak için kullanılan profil oluşturma yöntemine (örnekleme veya ölçüm) ve profil oluşturma çalıştırması içinde .NET bellek verisi toplanmış olup olmadığını bağlıdır.

 Görünümün diğer iki bölümünde listelenen işlevlerden herhangi birini çift tıklayarak Rapor görünümünün orta kısmında Geçerli İşlev olarak farklı bir işlev seçin. Rapor görünümü değişiklikleri yansıtacak şekilde otomatik olarak güncelleştirilir.

 Sütun adlara tıklayarak verileri sıraabilirsiniz. Çağıran/Çağrılı görünümüne ek sütunlar eklenebilir. Daha fazla bilgi için [bkz. Nasıl ekleyebilirsiniz: Rapor görünümü sütunlarını özelleştirme.](../profiling/how-to-customize-report-view-columns.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Arayan/Çağrılı görünümü - örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)
- [Arayan/Çağrılı görünümü - ölçüm verileri](../profiling/caller-callee-view-instrumentation-data.md)
- [Arayan/Çağrılı görünümü - .NET bellek ölçüm verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)
- [Arayan/Çağrılı görünümü - .NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)
- [Arayan/Çağrılı görünümü - karşıtlık verileri](../profiling/caller-callee-view-contention-data.md)
