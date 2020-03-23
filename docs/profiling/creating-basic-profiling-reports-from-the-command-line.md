---
title: Komut Satırından Temel Profil Oluşturma Raporları Oluşturma | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777796"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Komut satırından temel profil oluşturma raporları oluşturma
Bu makalede, virgülden ayrılmış değer oluşturan temel VSPerfReport komutları açıklanmaktadır (.* csv*) bir raporlar . *vsp* veya . *vsps* profil oluşturma veri dosyası. Tüm rapor seçeneklerinin açıklaması için [VSPerfReport'a](../profiling/vsperfreport.md)bakın.

## <a name="report-commands"></a>Rapor komutları
 Belirtilen profil oluşturma veri dosyası için rapor oluşturmak için aşağıdaki komutlardan birini kullanın.

 **VSPerfReport** `VSPFile` **/Summary:Tüm** için kullanılabilir tüm raporları oluşturur. *vsp* veya . *vsps* dosyası.

 **VSPerfReport** `VSPFile` **/Özet:**`ReportType``ReportType`[, ...] Belirtilen rapor türlerini oluşturur.

 **VSPerfReport** `VSPFile` **/CallTrace** Her veri toplama olayını listeleyen bir rapor oluşturur. Sadece enstrümantasyon.

## <a name="summary-report-type-parameters"></a>Özet rapor türü parametreleri
 Aşağıdaki tabloda, belirtilen rapor türü seçeneği tarafından oluşturulan raporlar açıklanmaktadır. Raporun sütunları, verileri toplamak için kullanılan profil oluşturma yöntemine bağlıdır.

|Özet Parametresi|Rapor Açıklaması|Rapor Başvurusu|
|-----------------------|------------------------|----------------------|
|**ArayanCallee**|Işlevler arasındaki üst/alt ilişkilerini temsil eder.|-   [Veri örneklemesi](../profiling/caller-callee-view-sampling-data.md)<br />-   [Enstrümantasyon verileri](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek enstrümantasyon verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [Çekişme verileri](../profiling/caller-callee-view-contention-data.md)|
|**İşlev**|Profil oluşturma verilerini işleve göre listeler.|-   [Veri örneklemesi](../profiling/functions-view-sampling-data.md)<br />-   [Enstrümantasyon verileri](../profiling/functions-view-instrumentation-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek enstrümantasyon verileri](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [Çekişme verileri](../profiling/functions-view-contention-data.md)|
|**CallTree**|Profil oluşturma çalışmasındaki işlevlerin yürütme yollarını ve profil oluşturma verilerini temsil eder.|-   [Enstrümantasyon verileri](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Veri örneklemesi](../profiling/call-tree-view-sampling-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek enstrümantasyon verileri](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [Çekişme verileri](../profiling/call-tree-view-contention-data.md)|
|**Sayaç**|Profil oluşturma işaretleri ve profil oluşturma çalışması sırasında toplanan Windows performans sayacı değerlerini listeler.|-   [İşaretler Görünümü](../profiling/marks-view.md)|
|**ıp**|Profil oluşturma verilerini yönergeye göre listeler.|-   [Veri örneklemesi](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [Çekişme verileri](../profiling/instruction-pointers-ips-view-contention-data.md)|
|**Hayat**|Ayrılan nesnelerin kullanım ömrünü listeler.|-   [Nesne Yaşam Boyu Görünümü](../profiling/object-lifetime-view.md)|
|**Satır**|Profil oluşturma verilerini kaynak kod satırına göre listeler.|-   [Veri örneklemesi](../profiling/lines-view-sampling-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [Çekişme Verileri](../profiling/lines-view-contention-data.md)|
|**Üst bilgi**|Veri dosyası üstbilgisi bilgilerini profil oluşturma.|Dosyaya özgü.|
|**İşaret**|Profil oluşturma çalışmasında toplanan profil işaretleri.|-   [İşaretler Görünümü](../profiling/marks-view.md)|
|**Modül**|Modüller için profil oluşturma verilerini listeler.|-   [Veri örneklemesi](../profiling/modules-view-sampling-data.md)<br />-   [Enstrümantasyon verileri](../profiling/modules-view-instrumentation-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [.NET Bellek Enstrümantasyon Verileri](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [Çekişme verileri](../profiling/modules-view-contention-data.md)|
|**İşleme**|İşlemler için profil oluşturma verilerini listeler.|-   [İşlem Görünümü](../profiling/process-view.md)<br />-   [Çekişme verileri](../profiling/process-view-contention-data.md)|
|**Iş parçacığı**|İş parçacıkları için profil oluşturma verilerini listeler.|-   [İşlem Görünümü](../profiling/process-view.md)|
|**Tür**|Ayırma profil oluşturma verilerini türüne göre listeler.|-   [Tahsisat Görünümü](../profiling/dotnet-memory-allocations-view.md)|
|**Çekişme**|Kaynak çekişmeleri.|-   [Kaynak çekişmeleri](../profiling/resource-contentions-view-contention-data.md)|
|**Kural Uyarılar**|Performans kuralı sorunlarını listeler.|- Kural sorununun Denetim Kimliğini, açıklamasını ve kaynak kodu konumunu listeler.|
|**ETW**|Profil oluşturma çalışmasında toplanan Windows (ETW) olayları için Olay İzleme'yi listeler.|-   [ETW raporu](../profiling/event-tracing-for-windows-etw-report.md)|
