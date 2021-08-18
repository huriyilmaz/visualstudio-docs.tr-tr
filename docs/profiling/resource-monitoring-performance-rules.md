---
title: Kaynak İzleme Performans Kuralları | Microsoft Docs
description: Kaynak İzleme kategorisindeki performans iletilerinin, uygulamanın performansıyla ilgili ek veriler sağlamayı öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dcae9f26bd87192a2388eaf3403fdec39e210331d98f2b1f55340cf2f6dbbf04
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442027"
---
# <a name="resource-monitoring-performance-rules"></a>Kaynak İzleme Performans Kuralları
Kaynak İzleme kategorisindeki performans iletileri, uygulamanın performansı hakkında ek veriler sağlar. Performans sorunlarını analiz etmek için bu verileri kullanabilirsiniz. Bu kurallar, her profil oluşturma çalıştırması için bilgilendirmeye ve rapora ilişkindir.

|Kural|Açıklama|
|-|-|
|[DA0501: Profili yapılan İşlem tarafından ortalama CPU tüketimi.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Bu ileti, bir işlemcinin uygulama yönergelerini yürütmekle meşgul olduğu süre yüzdesini raporlar. Bildirilen değer, profili yapılan sürecin etkin olduğu tüm ölçüm aralıklarının ortalamasıdır.|
|[DA0502: Profili oluşturulan İşlemin En Yüksek CPU kullanımı](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Bu ileti, bir işlemcinin uygulama yönergelerini yürütmekle meşgul olduğu en uzun süre yüzdesini raporlar. Bildirilen değer, profili yapılan sürecin etkin olduğu tüm ölçüm aralıklarında bildirilen en yüksek değerdir.|
|[DA0503: Profili oluşturulan İşlemin Bayt Cinsinden Ortalama Çalışma Kümesi](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken işlem tarafından tüketilen ortalama fiziksel bellek miktarını bayt cinsinden raporlar. Bu fiziksel bellek ölçüsü çalışma kümesi olarak bilinir.|
|[DA0504: Profili oluşturulan İşlemin Bayt Cinsinden En Yüksek Sayıda Çalışma Kümesi](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Bu ileti, işlem profil oluşturma etkinken kullanmakta olduğu maksimum fiziksel bellek miktarını bayt cinsinden raporlar.|
|[DA0505: Profili oluşturulan İşlem için ayırılmış Ortalama Özel Baytlar](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken işlem tarafından bayt cinsinden ayrılan ortalama sanal bellek miktarını raporlar. Bu sanal bellek ölçüsü özel bayt *olarak bilinir.* Özel baytlar, işlem tarafından yalnızca işlem içinde çalışan iş parçacıkları tarafından erişilebilen sanal bellek konumlarını temsil eder.|
|[DA0506: Profili oluşturulan İşlem için ayırılmış En Yüksek Sayıda Özel Bayt](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken işlem tarafından özel baytlara ayrılan en yüksek sanal bellek miktarını raporlar.|
