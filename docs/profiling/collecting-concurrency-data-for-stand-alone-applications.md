---
title: Tek başına uygulama eşzamanlılık verilerini almak için Profiler komut satırı
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773263"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Profil oluşturucu komut satırını kullanarak tek başına uygulamalar için eşzamanlılık verileri toplama
Profil Oluşturma Araçları'nın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eşzamanlılık yöntemi, cpu kullanımı, iş parçacığı aktarım, eşitleme gecikmeleri, çakışan IO alanları ve diğer sistem olayları gösteren kaynak çekişme verileri ve iş parçacığı etkinlik verilerini toplamanızı sağlar.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili içerik|
|----------|---------------------|
|**Bir .NET Framework uygulaması ve profil eşzamanlılık verileri başlatma**|-   [Nasıl kullanılır: Eşzamanlılık verileri toplamak için bir .NET Framework uygulaması başlatın](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**C/C++ uygulaması ve profil eşzamanlılık verilerini başlatma**|-   [Nasıl kullanılır: Eşzamanlılık verileri toplamak için yerel bir uygulama başlatma](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Çalışan bir .NET Framework uygulamasına profil oluşturucuyu ekleme**|-   [Nasıl kullanılır: Eşzamanlı lık verileri toplamak için profil oluşturucuyu bir .NET Framework uygulamasına ekleme](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Profiloluşturciyi çalışan c/c++ uygulamasına takın**|-   [Nasıl kullanılır: Profiloluşturucuyu yerel bir uygulamaya takın ve eşzamanlılık verilerini toplayın](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-stand-alone-applications"></a>Profil tek başına uygulamalar

|Görev|İlgili içerik|
|----------|---------------------|
|**Örnekleme yöntemini kullanarak profil**|-   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Enstrümantasyon yöntemini kullanarak profil**|-   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profil .NET bellek ayırma ve çöp toplama**|-   [.NET Framework bellek verilerini topla](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Katman etkileşimi verileri ekleme**|-   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Profil eşzamanlılık sorunları

|Görev|İlgili içerik|
|----------|---------------------|
|**Profil ASP.NET uygulamaları**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Profil hizmetleri**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Eşzamanlılık veri görünümlerini ve raporlarını analiz edin
- [Kaynak çekişme veri görünümleri](../profiling/resource-contention-data-views.md)

- [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
