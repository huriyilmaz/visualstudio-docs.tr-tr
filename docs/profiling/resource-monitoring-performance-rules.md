---
title: Kaynak İzleme Performans Kuralları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2389c23b9089ebbdd96d337a3b47d5be9d576b4b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778329"
---
# <a name="resource-monitoring-performance-rules"></a>Kaynak İzleme Performans Kuralları
Kaynak İzleme kategorisindeki performans iletileri, uygulamanızın performansı hakkında ek veriler sağlar. Performans sorunlarını çözümlemek için bu verileri kullanabilirsiniz. Bu kurallar bilgilendirme amaçlıdır ve her profil oluşturma çalışması için raporlanır.

|||
|-|-|
|[DA0501: İşlemin ortalama CPU kullanımının profili oluşturuluyor.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Bu ileti, işlemcinin uygulamadan gelen yönergeleri yürütmekle meşgul olduğu süre yüzdesini bildirir. Bildirilen değer, profillenen işlemin etkin olduğu tüm ölçüm aralıklarının ortalamasıdır.|
|[DA0502: İşlemin maksimum CPU kullanımının profili oluşturuluyor](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Bu ileti, bir işlemcinin uygulamadan gelen yönergeleri yürütmekle meşgul olduğu maksimum süre yüzdesini bildirir. Bildirilen değer, profillenen işlemin etkin olduğu tüm ölçüm aralıkları arasında bildirilen maksimum değerdir.|
|[DA0503: İşlem için Bayt Cinsinden Ortalama Çalışma Kümesinin profili oluşturuluyor](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken işlemin kullandığı ortalama fiziksel bellek miktarını baytolarak bildirir. Fiziksel belleğin bu ölçüsü çalışma kümesi olarak bilinir.|
|[DA0504: İşlem için izin verilen Bayt Cinsinden En Büyük Çalışma Kümesinin profili oluşturuluyor](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken işlemin kullandığı maksimum fiziksel bellek miktarını baytolarak bildirir.|
|[DA0505: İşlem için izin verilen Ortalama Özel Bayt Sayısının profili oluşturuluyor](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma işlemi etkinken baytlara ayrılan işlemin ortalama sanal bellek miktarını bildirir. Sanal belleğin bu ölçüsü *özel bayt*olarak bilinir. Özel baytlar, yalnızca işlem içinde çalışan iş parçacıkları tarafından erişilebilen işlem tarafından ayrılan sanal bellek konumlarını temsil eder.|
|[DA0506: İşlem için izin verilen Maksimum Özel Bayt Sayısının profili oluşturuluyor](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken özel baytlara ayrılan işlemin en fazla sanal bellek miktarını bildirir.|
