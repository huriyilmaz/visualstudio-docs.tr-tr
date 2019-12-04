---
title: Tek başına uygulama eşzamanlılık verilerini almak için profil oluşturucu komut satırı
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6180d2f2e3ed655f378900d3d41691daa98a0354
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773263"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Profil oluşturucu komut satırını kullanarak tek başına uygulamalar için eşzamanlılık verileri toplama
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları eşzamanlılık yöntemi, CPU kullanımını, iş parçacığı çekişmesini, iş parçacığı geçişini, eşitleme gecikmelerini, çakışan GÇ ve diğer sistem olaylarını gösteren kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamanıza olanak sağlar.

## <a name="common-tasks"></a>Ortak görevler

|Görev|İlgili içerik|
|----------|---------------------|
|**.NET Framework bir uygulama başlatma ve eşzamanlılık verileri profili oluşturma**|-   [nasıl yapılır: eşzamanlılık verileri toplamak için .NET Framework uygulamasını başlatma](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**C/C++ uygulama ve profil eşzamanlılık verileri başlatma**|-   [nasıl yapılır: eşzamanlılık verileri toplamak için yerel bir uygulama başlatma](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Profil oluşturucuyu çalışan bir .NET Framework uygulamasına iliştirme**|-   [nasıl yapılır: eşzamanlılık verileri toplamak için profil oluşturucuyu bir .NET Framework uygulamasına iliştirme](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Profil oluşturucuyu çalışan bir C/C++ uygulamasına iliştirme**|-   [nasıl yapılır: yerel bir uygulamaya profil oluşturucu iliştirme ve eşzamanlılık verileri toplama](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-stand-alone-applications"></a>Tek başına uygulamalar profili

|Görev|İlgili içerik|
|----------|---------------------|
|**Örnekleme yöntemi kullanılarak profil**|[örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md) -   |
|**İzleme yöntemini kullanarak profil**|[izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) -   |
|**.NET bellek ayırma ve çöp toplama profili**|[.NET Framework bellek verileri toplama](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) -   |
|**Katman etkileşim verileri ekleme**|[katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) -   |

### <a name="profile-concurrency-issues"></a>Profil eşzamanlılık sorunları

|Görev|İlgili içerik|
|----------|---------------------|
|**Profil ASP.NET uygulamaları**|-   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Profil hizmetleri**|-   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Eşzamanlılık veri görünümlerini ve raporlarını çözümleme
- [Kaynak çakışması veri görünümleri](../profiling/resource-contention-data-views.md)

- [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
