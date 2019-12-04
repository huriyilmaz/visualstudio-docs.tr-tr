---
title: Kaynak Izleme performans kuralları | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778329"
---
# <a name="resource-monitoring-performance-rules"></a>Kaynak İzleme Performans Kuralları
Kaynak Izleme kategorisindeki performans iletileri uygulamanızın performansı hakkında ek veriler sağlar. Bu verileri, performans sorunlarını analiz etmek için kullanabilirsiniz. Bu kurallar bilgilendirme amaçlıdır ve her profil oluşturma çalışması için raporlanır.

|||
|-|-|
|[DA0501: İşlemin ortalama CPU kullanımının profili oluşturuluyor.](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Bu ileti, bir işlemcinin uygulamadan yönergeleri yürütürken meşgul olduğu sürenin yüzdesini bildirir. Bildirilen değer, işlem yapılan işlemin etkin olduğu tüm ölçüm aralıklarının ortalaması olarak belirlenir.|
|[DA0502: İşlemin maksimum CPU kullanımının profili oluşturuluyor](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Bu ileti, bir işlemcinin uygulamadan yönergeleri yürütürken meşgul olduğu sürenin en uzun yüzdesini bildirir. Bildirilen değer, işlem yapılan işlemin etkin olduğu tüm ölçüm aralıkları arasında raporlanan en büyük değerdir.|
|[DA0503: İşlem için Bayt Cinsinden Ortalama Çalışma Kümesinin profili oluşturuluyor](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken işlemin kullandığı ortalama fiziksel bellek miktarını bayt cinsinden bildirir. Bu fiziksel bellek ölçüsü çalışma kümesi olarak bilinir.|
|[DA0504: İşlem için izin verilen Bayt Cinsinden En Büyük Çalışma Kümesinin profili oluşturuluyor](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken işlemin kullandığı maksimum fiziksel bellek miktarını bayt cinsinden bildirir.|
|[DA0505: İşlem için izin verilen Ortalama Özel Bayt Sayısının profili oluşturuluyor](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken, işlemin bayt olarak ayırdığı ortalama sanal bellek miktarını bildirir. Bu sanal bellek ölçüsü *özel bayt*olarak bilinir. Özel baytlar, işlem tarafından yalnızca işlem içinde çalışan iş parçacıklarının erişebileceği sanal bellek konumlarını temsil eder.|
|[DA0506: İşlem için izin verilen Maksimum Özel Bayt Sayısının profili oluşturuluyor](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Bu ileti, profil oluşturma etkinken özel baytlara ayrılan işlemin en fazla sanal bellek miktarını bildirir.|
