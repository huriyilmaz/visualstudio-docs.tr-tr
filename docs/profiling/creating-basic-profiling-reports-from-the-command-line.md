---
title: Profil oluşturma komut satırı - Temel raporlar oluşturma
description: Bir .vsp veya .vsps profil oluşturma VSPerfReport.exe .csv (virgülle ayrılmış-değer) raporları oluşturan özet ve CallTrace seçenekleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 6d73e21e-c04e-48ea-91cc-e517a5f2cd3f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 37a06c119bc0f28ffd1a5efe46842f25155c237c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039143"
---
# <a name="create-basic-profiling-reports-from-the-command-line"></a>Komut satırdan temel profil oluşturma raporları oluşturma
Bu makalede virgülle ayrılmış değer () oluşturan temel VSPerfReport komutları açıklanmıştır.*csv*) raporları . *vsp* veya . *vsps* profil oluşturma veri dosyası. Tüm rapor seçeneklerinin açıklaması için bkz. [VSPerfReport](../profiling/vsperfreport.md).

## <a name="report-commands"></a>Rapor komutları
 Belirtilen profil oluşturma veri dosyası için rapor oluşturmak üzere aşağıdaki komutlardan birini kullanın.

 **VSPerfReport** `VSPFile` **/Summary:All** için kullanılabilir tüm raporları üretir. *vsp* veya . *vsps* dosyası.

 **VSPerfReport** `VSPFile` **/Summary:** `ReportType` [,`ReportType`...] Belirtilen rapor türlerini üretir.

 **VSPerfReport** `VSPFile` **/CallTrace** Her bir veri toplama olayı listelene bir rapor üretir. Yalnızca ölçümler.

## <a name="summary-report-type-parameters"></a>Özet rapor türü parametreleri
 Aşağıdaki tabloda, belirtilen rapor türü seçeneği tarafından oluşturulan raporlar açıklandı. Bir raporun sütunları, verileri toplamak için kullanılan profil oluşturma yöntemine bağlıdır.

|Özet Parametresi|Rapor Açıklaması|Rapor Başvurusu|
|-----------------------|------------------------|----------------------|
|**CallerCallee**|İşlevler arasındaki üst/alt ilişkileri temsil eder.|-   [Örnekleme verileri](../profiling/caller-callee-view-sampling-data.md)<br />-   [Ölçüm ölçüm verileri](../profiling/caller-callee-view-instrumentation-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek araçları verileri](../profiling/caller-callee-view-net-memory-instrumentation-data.md)<br />-   [İçerik verileri](../profiling/caller-callee-view-contention-data.md)|
|**İşlev**|İşleve göre profil oluşturma verilerini listeler.|-   [Örnekleme verileri](../profiling/functions-view-sampling-data.md)<br />-   [Ölçüm ölçüm verileri](../profiling/functions-view-instrumentation-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/functions-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek araçları verileri](../profiling/functions-view-dotnet-memory-instrumentation-data.md)<br />-   [İçerik verileri](../profiling/functions-view-contention-data.md)|
|**CallTree**|Profil oluşturma çalıştırması içinde işlevlerin yürütme yollarını ve profil oluşturma verilerini temsil eder.|-   [Ölçüm ölçüm verileri](../profiling/call-tree-view-instrumentation-data.md)<br />-   [Örnekleme verileri](../profiling/call-tree-view-sampling-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/call-tree-view-dotnet-memory-sampling-data.md)<br />-   [.NET bellek araçları verileri](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)<br />-   [İçerik verileri](../profiling/call-tree-view-contention-data.md)|
|**Sayaç**|Profil oluşturma işaretlerini ve Windows çalıştırması sırasında toplanan performans sayacı değerlerini listeler.|-   [İşaretler Görünümü](../profiling/marks-view.md)|
|**ıp**|Profil oluşturma verilerini yönergeye göre listeler.|-   [Örnekleme verileri](../profiling/instruction-pointers-ips-view-sampling-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)<br />-   [İçerik verileri](../profiling/instruction-pointers-ips-view-contention-data.md)|
|**Hayat**|Ayrılan nesnelerin ömrünü listeler.|-   [Nesne Ömrü Görünümü](../profiling/object-lifetime-view.md)|
|**Çizgi**|Kaynak kod satırına göre profil oluşturma verilerini listeler.|-   [Örnekleme verileri](../profiling/lines-view-sampling-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/lines-view-dotnet-memory-sampling-data.md)<br />-   [İçerik Verileri](../profiling/lines-view-contention-data.md)|
|**Üst bilgi**|Veri dosyası üst bilgisi bilgilerini profil oluşturma.|Dosyaya özgü.|
|**İşaret**|Profil oluşturma çalıştırması içinde toplanan profil oluşturma işaretleri.|-   [İşaretler Görünümü](../profiling/marks-view.md)|
|**Modül**|Modüller için profil oluşturma verilerini listeler.|-   [Örnekleme verileri](../profiling/modules-view-sampling-data.md)<br />-   [Ölçüm ölçüm verileri](../profiling/modules-view-instrumentation-data.md)<br />-   [.NET bellek örnekleme verileri](../profiling/modules-view-dotnet-memory-sampling-data.md)<br />-   [.NET Bellek Araçları Verileri](../profiling/modules-view-dotnet-memory-instrumentation-data.md)<br />-   [İçerik verileri](../profiling/modules-view-contention-data.md)|
|**İşleme**|İşlemler için profil oluşturma verilerini listeler.|-   [İşlem Görünümü](../profiling/process-view.md)<br />-   [İçerik verileri](../profiling/process-view-contention-data.md)|
|**Iş parçacığı**|İş parçacıkları için profil oluşturma verilerini listeler.|-   [İşlem Görünümü](../profiling/process-view.md)|
|**Tür**|Türe göre ayırma profili oluşturma verilerini listeler.|-   [Ayırmalar Görünümü](../profiling/dotnet-memory-allocations-view.md)|
|**Çekişme**|Kaynak irdeleleri.|-   [Kaynak irdeleleri](../profiling/resource-contentions-view-contention-data.md)|
|**RuleWarnings**|Performans kuralı sorunlarını listeler.|- Kural sorunun CheckId, açıklama ve kaynak kodu konumunu listeler.|
|**ETW**|Profil oluşturma çalıştırması Windows (ETW) olayları için Olay İzlemeyi listeler.|-   [ETW raporu](../profiling/event-tracing-for-windows-etw-report.md)|
