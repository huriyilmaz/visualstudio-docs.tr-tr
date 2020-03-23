---
title: Hizmet için eşzamanlı veri almak için profiler komut satırına kullanın
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4b7b60ad871f40e06e2a8fbf6782773ce6596f31
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779681"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Profil oluşturucu komut satırını kullanarak bir hizmet için eşzamanlılık verileri toplama
Profil Oluşturma Araçları'nın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] eşzamanlılık yöntemi, cpu kullanımı, iş parçacığı aktarım, eşitleme gecikmeleri, çakışan IO alanları ve diğer sistem olayları gösteren kaynak çekişme verileri ve iş parçacığı etkinlik verilerini toplamanızı sağlar.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Bkz. Windows 8 ve Windows Server 2012 uygulamalarında Performans araçları.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Çalışan bir .NET hizmetine ekleme**|-   [Nasıl kullanılır: Eşzamanlı veri toplamak için profil oluşturucuyu bir .NET hizmetine ekleme](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Katman etkileşimi verileri ekleme**|-   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Çalışan bir C/C++ hizmetine ekleme**|-   [Nasıl kullanılır: Eşzamanlı lık verileri toplamak için profil oluşturucuyu yerel bir hizmete iliştirin](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-windows-services"></a>Profil Windows hizmetleri

|Görev|İlgili İçerik|
|----------|---------------------|
|**Örnekleme yöntemini kullanarak profil**|-   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Enstrümantasyon yöntemini kullanarak profil**|-   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profile.NET bellek ayırma ve çöp toplama**|-   [.NET bellek verilerini toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Profil eşzamanlılık verileri

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil tek başına uygulamalar**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Profil ASP.NET Web uygulamaları**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Eşzamanlılık veri görünümlerini ve raporlarını analiz edin
- [Kaynak çekişme veri görünümleri](../profiling/resource-contention-data-views.md)

- [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
