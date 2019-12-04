---
title: Komut satırından temel profil oluşturma raporları oluşturma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cd9748d88a9398792274c386a42bdaa3ce48ba70
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777796"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Komut satırından temel profil oluşturma raporları oluşturma
Bu makalede, virgülle ayrılmış değer (. *CSV*) bir. *VSP* veya. *vsps* profil oluşturma veri dosyası. Tüm rapor seçeneklerinin açıklaması için bkz. [VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Rapor komutları
 Belirtilen profil oluşturma veri dosyası için bir rapor oluşturmak üzere aşağıdaki komutlardan birini kullanın.

 **VSPerfReport** `VSPFile` **/summary: ALL** , için kullanılabilen tüm raporları oluşturur. *VSP* veya. *vsps* dosyası.

 **VSPerfReport** `VSPFile` **/summary:** `ReportType`[,`ReportType`...] Belirtilen rapor türlerini üretir.

 **VSPerfReport** `VSPFile` **/calltrace** , her veri toplama olayını listeleyen bir rapor oluşturur. Yalnızca izleme.

## <a name="summary-report-type-parameters"></a>Özet rapor türü parametreleri
 Aşağıdaki tablo, belirtilen rapor türü seçeneği tarafından oluşturulan raporları açıklar. Bir raporun sütunları, verileri toplamak için kullanılan profil oluşturma yöntemine bağlıdır.

|Özet parametresi|Rapor açıklaması|Rapor başvurusu|
|-----------------------|------------------------|----------------------|
|**CallerCallee**|İşlevler arasındaki üst/alt ilişkileri temsil eder.|[örnekleme verilerini](../profiling/caller-callee-view-sampling-data.md) -   <br />-   [izleme verileri](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.net bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />[.net bellek izleme verilerini](../profiling/caller-callee-view-net-memory-instrumentation-data.md) -   <br />[çekişme verileri](../profiling/caller-callee-view-contention-data.md) -   |
|**Çalışmayacaktır**|İşlevine göre profil oluşturma verilerini listeler.|[örnekleme verilerini](../profiling/functions-view-sampling-data.md) -   <br />-   [izleme verileri](../profiling/functions-view-instrumentation-data.md)<br />-   [.net bellek örnekleme verileri](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />[.net bellek izleme verilerini](../profiling/functions-view-dotnet-memory-instrumentation-data.md) -   <br />[çekişme verileri](../profiling/functions-view-contention-data.md) -   |
|**CallTree**|Profil oluşturma çalıştırmasında işlevlerin yürütme yollarını ve profil oluşturma verilerini temsil eder.|-   [izleme verileri](../profiling/call-tree-view-instrumentation-data.md)<br />[örnekleme verilerini](../profiling/call-tree-view-sampling-data.md) -   <br />-   [.net bellek örnekleme verileri](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />[.net bellek izleme verilerini](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md) -   <br />[çekişme verileri](../profiling/call-tree-view-contention-data.md) -   |
|**Counter**|Profil oluşturma çalıştırma sırasında toplanan profil oluşturma işaretlerini ve Windows performans sayacı değerlerini listeler.|-   [Işaretleri görünümü](../profiling/marks-view.md)|
|**IP**|Yönergeye göre profil oluşturma verilerini listeler.|[örnekleme verilerini](../profiling/instruction-pointers-ips-view-sampling-data.md) -   <br />-   [.net bellek örnekleme verileri](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />[çekişme verileri](../profiling/instruction-pointers-ips-view-contention-data.md) -   |
|**Hay**|Ayrılan nesnelerin ömrünü listeler.|-   [nesne ömrü görünümü](../profiling/object-lifetime-view.md)|
|**Satırı**|Kaynak kodu satırına göre profil oluşturma verilerini listeler.|[örnekleme verilerini](../profiling/lines-view-sampling-data.md) -   <br />-   [.net bellek örnekleme verileri](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />[çekişme verileri](../profiling/lines-view-contention-data.md) -   |
|**Üst bilgi**|Profil oluşturma veri dosyası üstbilgi bilgileri.|Dosyaya özgüdür.|
|**Mark**|Profil oluşturma çalıştırmasında toplanan profil oluşturma işaretleri.|-   [Işaretleri görünümü](../profiling/marks-view.md)|
|**Module**|Modüller için profil oluşturma verilerini listeler.|[örnekleme verilerini](../profiling/modules-view-sampling-data.md) -   <br />-   [izleme verileri](../profiling/modules-view-instrumentation-data.md)<br />-   [.net bellek örnekleme verileri](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />[.net bellek Izleme verilerini](../profiling/modules-view-dotnet-memory-instrumentation-data.md) -   <br />[çekişme verileri](../profiling/modules-view-contention-data.md) -   |
|**İşle**|Süreçler için profil oluşturma verilerini listeler.|-   [Işlem görünümü](../profiling/process-view.md)<br />[çekişme verileri](../profiling/process-view-contention-data.md) -   |
|**Zincirinin**|İş parçacıkları için profil oluşturma verilerini listeler.|-   [Işlem görünümü](../profiling/process-view.md)|
|**Türüyle**|Türe göre ayırma profil oluşturma verilerini listeler.|-   [ayırmaları görünümü](../profiling/dotnet-memory-allocations-view.md)|
|**Çekişmesi**|Kaynak çekişmeleri.|-   [kaynak çekişmeleri](../profiling/resource-contentions-view-contention-data.md)|
|**RuleWarnings**|Performans kuralı sorunlarını listeler.|-Kural sorununun CheckId, Description ve Source Code konumunu listeler.|
|**YÖNELIK**|Profil oluşturma çalıştırmasında toplanan Windows için olay Izleme (ETW) olaylarını listeler.|-   [ETW raporu](../profiling/event-tracing-for-windows-etw-report.md)|
