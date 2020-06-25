---
title: Komut satırından temel profil oluşturma raporları oluşturma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bca944b67b19fdbb4138c479acf5693994d1c717
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329046"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Komut satırından temel profil oluşturma raporları oluşturma
Bu makalede, virgülle ayrılmış değer (.* CSV*) bir. *VSP* veya. *vsps* profil oluşturma veri dosyası. Tüm rapor seçeneklerinin açıklaması için bkz. [VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Rapor komutları
 Belirtilen profil oluşturma veri dosyası için bir rapor oluşturmak üzere aşağıdaki komutlardan birini kullanın.

 **VSPerfReport** `VSPFile` **/Summary: tümü** İçin kullanılabilir tüm raporları oluşturur. *VSP* veya. *vsps* dosyası.

 **VSPerfReport** `VSPFile` **/Summary:** `ReportType` [,`ReportType`...] Belirtilen rapor türlerini üretir.

 **VSPerfReport** `VSPFile` **/Calltrace** Her veri toplama olayını listeleyen bir rapor oluşturur. Yalnızca izleme.

## <a name="summary-report-type-parameters"></a>Özet rapor türü parametreleri
 Aşağıdaki tablo, belirtilen rapor türü seçeneği tarafından oluşturulan raporları açıklar. Bir raporun sütunları, verileri toplamak için kullanılan profil oluşturma yöntemine bağlıdır.

|Özet parametresi|Rapor açıklaması|Rapor başvurusu|
|-----------------------|------------------------|----------------------|
|**CallerCallee**|İşlevler arasındaki üst/alt ilişkileri temsil eder.|-   [Örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)<br />-   [İzleme verileri](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.NET Bellek Örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Çekişme verileri](../profiling/caller-callee-view-contention-data.md)|
|**İşlev**|İşlevine göre profil oluşturma verilerini listeler.|-   [Örnekleme verileri](../profiling/functions-view-sampling-data.md)<br />-   [İzleme verileri](../profiling/functions-view-instrumentation-data.md)<br />-   [.NET Bellek Örnekleme verileri](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek izleme verileri](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Çekişme verileri](../profiling/functions-view-contention-data.md)|
|**CallTree**|Profil oluşturma çalıştırmasında işlevlerin yürütme yollarını ve profil oluşturma verilerini temsil eder.|-   [İzleme verileri](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Örnekleme verileri](../profiling/call-tree-view-sampling-data.md)<br />-   [.NET Bellek Örnekleme verileri](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek izleme verileri](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Çekişme verileri](../profiling/call-tree-view-contention-data.md)|
|**Sayaç**|Profil oluşturma çalıştırma sırasında toplanan profil oluşturma işaretlerini ve Windows performans sayacı değerlerini listeler.|-   [İşaretler görünümü](../profiling/marks-view.md)|
|**IP**|Yönergeye göre profil oluşturma verilerini listeler.|-   [Örnekleme verileri](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [.NET Bellek Örnekleme verileri](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Çekişme verileri](../profiling/instruction-pointers-ips-view-contention-data.md)|
|**Hay**|Ayrılan nesnelerin ömrünü listeler.|-   [Nesne ömrü görünümü](../profiling/object-lifetime-view.md)|
|**Çizgi**|Kaynak kodu satırına göre profil oluşturma verilerini listeler.|-   [Örnekleme verileri](../profiling/lines-view-sampling-data.md)<br />-   [.NET Bellek Örnekleme verileri](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Çekişme verileri](../profiling/lines-view-contention-data.md)|
|**Üst bilgi**|Profil oluşturma veri dosyası üstbilgi bilgileri.|Dosyaya özgüdür.|
|**İşaret**|Profil oluşturma çalıştırmasında toplanan profil oluşturma işaretleri.|-   [İşaretler görünümü](../profiling/marks-view.md)|
|**Modül**|Modüller için profil oluşturma verilerini listeler.|-   [Örnekleme verileri](../profiling/modules-view-sampling-data.md)<br />-   [İzleme verileri](../profiling/modules-view-instrumentation-data.md)<br />-   [.NET Bellek Örnekleme verileri](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek Izleme verileri](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Çekişme verileri](../profiling/modules-view-contention-data.md)|
|**İşleme**|Süreçler için profil oluşturma verilerini listeler.|-   [İşlem görünümü](../profiling/process-view.md)<br />-   [Çekişme verileri](../profiling/process-view-contention-data.md)|
|**Zincirinin**|İş parçacıkları için profil oluşturma verilerini listeler.|-   [İşlem görünümü](../profiling/process-view.md)|
|**Tür**|Türe göre ayırma profil oluşturma verilerini listeler.|-   [Ayırmalar görünümü](../profiling/dotnet-memory-allocations-view.md)|
|**Çekişmesi**|Kaynak çekişmeleri.|-   [Kaynak çekişmeleri](../profiling/resource-contentions-view-contention-data.md)|
|**RuleWarnings**|Performans kuralı sorunlarını listeler.|-Kural sorununun CheckId, Description ve Source Code konumunu listeler.|
|**ETW**|Profil oluşturma çalıştırmasında toplanan Windows için olay Izleme (ETW) olaylarını listeler.|-   [ETW raporu](../profiling/event-tracing-for-windows-etw-report.md)|
