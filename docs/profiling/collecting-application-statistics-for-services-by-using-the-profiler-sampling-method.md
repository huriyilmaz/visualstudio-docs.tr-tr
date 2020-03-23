---
title: Profiler örnekleme yöntemini kullanarak uygulama istatistiklerini toplama
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 17217a51c58e1d30b6e6854ee9dbb0c1fb662a3a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779694"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Profil oluşturma örnekleme yöntemini kullanarak hizmetler için uygulama istatistiklerini toplama
Bu bölümde, komut satırından örnekleme yöntemini kullanarak Windows hizmetleri için performans istatistikleri toplamak için yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profiloluşturciyi bir .NET hizmetine takın**|-   [Nasıl yapilir: Uygulama istatistiklerini toplamak için profiloluşturcağı bir .NET hizmetine ekleme](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Katman etkileşimi verileri ekleme**|-   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Profil oluşturucuyu C/C++ hizmetine takın**|-   [Nasıl yapilir: Uygulama istatistiklerini toplamak için profiloluşturucuyu yerel bir hizmete iliştirin](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-windows-services"></a>Profil Windows hizmetleri

|Görev|İlgili İçerik|
|----------|---------------------|
|**Enstrümantasyon yöntemini kullanarak profil**|-   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profil .NET bellek ayırma ve çöp toplama**|-   [.NET bellek verilerini toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Profil kaynak çekişmesi ve iş parçacığı etkinliği**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak profil

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil tek başına (istemci) uygulamaları**|-   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Profil ASP.NET Web uygulamaları**|-   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Örnekleme veri görünümlerini ve raporlarını analiz
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
