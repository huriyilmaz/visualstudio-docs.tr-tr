---
title: Komut satırından temel profil oluşturma raporları oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f13921dea810ab2185e626cc2889f339d9d174f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537195"
---
# <a name="creating-basic-profiling-reports-from-the-command-line"></a>Komut Satırından Temel Profil Oluşturma Raporları Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, bir. vsp veya. vsps profil oluşturma veri dosyasından virgülle ayrılmış değer (. csv) raporları üreten temel VSPerfReport komutlarını açıklamaktadır. Tüm rapor seçeneklerinin açıklaması için bkz. [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="report-commands"></a>Rapor komutları  
 Belirtilen profil oluşturma veri dosyası için bir rapor oluşturmak üzere aşağıdaki komutlardan birini kullanın.  
  
 **VSPerfReport** `VSPFile` **/Summary: tümü**  
 . Vsp veya. vsps dosyası için kullanılabilen tüm raporları oluşturur.  
  
 **VSPerfReport** `VSPFile` **/Summary:** `ReportType` [,`ReportType`...]  
 Belirtilen rapor türlerini üretir.  
  
 **VSPerfReport** `VSPFile` **/Calltrace**  
 Her veri toplama olayını listeleyen bir rapor oluşturur. Yalnızca izleme.  
  
## <a name="summary-report-type-parameters"></a>Özet rapor türü parametreleri  
 Aşağıdaki tablo, belirtilen rapor türü seçeneği tarafından oluşturulan raporları açıklar. Bir raporun sütunları, verileri toplamak için kullanılan profil oluşturma yöntemine bağlıdır.  
  
|Özet parametresi|Rapor açıklaması|Rapor başvurusu|  
|-----------------------|------------------------|----------------------|  
|**CallerCallee**|İşlevler arasındaki üst/alt ilişkileri temsil eder.|-   [Örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)<br />-   [İzleme verileri](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.NET Bellek Örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek Izleme verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Çekişme verileri](../profiling/caller-callee-view-contention-data.md)|  
|**İşlev**|İşlevine göre profil oluşturma verilerini listeler.|-   [Örnekleme verileri](../profiling/functions-view-sampling-data.md)<br />-   [İzleme verileri](../profiling/functions-view-instrumentation-data.md)<br />-   [.NET Bellek Örnekleme verileri](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek Izleme verileri](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Çekişme verileri](../profiling/functions-view-contention-data.md)|  
|**CallTree**|Profil oluşturma çalıştırmasında işlevlerin yürütme yollarını ve profil oluşturma verilerini temsil eder.|-   [İzleme verileri](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Örnekleme verileri](../profiling/call-tree-view-sampling-data.md)<br />-   [.NET Bellek Örnekleme verileri](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek Izleme verileri](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Çekişme verileri](../profiling/call-tree-view-contention-data.md)|  
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
