---
title: Kaynak Izleme performans kuralları | Microsoft Docs
description: Kaynak Izleme kategorisindeki performans iletilerinin uygulamanızın performansı hakkında nasıl ek veri sağladığını öğrenin.
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
ms.openlocfilehash: d9a683aa6b3beaeea11c696ab1dbac66f9c94685
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157351"
---
# <a name="resource-monitoring-performance-rules"></a>Kaynak İzleme Performans Kuralları
Kaynak Izleme kategorisindeki performans iletileri uygulamanızın performansı hakkında ek veriler sağlar. Bu verileri, performans sorunlarını analiz etmek için kullanabilirsiniz. Bu kurallar bilgilendirme amaçlıdır ve her profil oluşturma çalışması için raporlanır.

|Kural|Açıklama|
|-|-|
|[DA0501: Işlem tarafından ortalama CPU kullanımı profili oluşturuldu.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Bu ileti, bir işlemcinin uygulamadan yönergeleri yürütürken meşgul olduğu sürenin yüzdesini bildirir. Bildirilen değer, işlem yapılan işlemin etkin olduğu tüm ölçüm aralıklarının ortalaması olarak belirlenir.|
|[DA0502: Profili oluşturulan İşlemin En Yüksek CPU kullanımı](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Bu ileti, bir işlemcinin uygulamadan yönergeleri yürütürken meşgul olduğu sürenin en uzun yüzdesini bildirir. Bildirilen değer, işlem yapılan işlemin etkin olduğu tüm ölçüm aralıkları arasında raporlanan en büyük değerdir.|
|[DA0503: Profili oluşturulan İşlemin Bayt Cinsinden Ortalama Çalışma Kümesi](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken işlemin kullandığı ortalama fiziksel bellek miktarını bayt cinsinden bildirir. Bu fiziksel bellek ölçüsü çalışma kümesi olarak bilinir.|
|[DA0504: Profili oluşturulan İşlemin Bayt Cinsinden En Yüksek Sayıda Çalışma Kümesi](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken işlemin kullandığı maksimum fiziksel bellek miktarını bayt cinsinden bildirir.|
|[DA0505: Profili oluşturulan İşlem için ayırılmış Ortalama Özel Baytlar](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken, işlemin bayt olarak ayırdığı ortalama sanal bellek miktarını bildirir. Bu sanal bellek ölçüsü *özel bayt* olarak bilinir. Özel baytlar, işlem tarafından yalnızca işlem içinde çalışan iş parçacıklarının erişebileceği sanal bellek konumlarını temsil eder.|
|[DA0506: Profili oluşturulan İşlem için ayırılmış En Yüksek Sayıda Özel Bayt](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken özel baytlara ayrılan işlemin en fazla sanal bellek miktarını bildirir.|
