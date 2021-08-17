---
title: Profil oluşturma komut satırı - Hizmet için eşzamanlılık verilerini al
description: Kaynak etkinliğinin eşzamanlılık yöntemini kullanarak kaynak ve iş parçacığı etkinlik verilerini Visual Studio Profil Oluşturma Araçları.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bb948b30de72212c10d85192b195615ab7c79729ca60bb3c2714038929a1cb3d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121355769"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Profil oluşturma komut satırı kullanarak bir hizmet için eşzamanlılık verileri toplama
Profil Oluşturma Araçları eşzamanlılık yöntemi; CPU kullanımı, iş parçacığı çakışması, iş parçacığı geçişi, eşitleme gecikmeleri, çakışan IO alanlarını ve diğer sistem olaylarını gösteren kaynak çakışma verilerini ve iş parçacığı etkinlik verilerini toplamaya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olanak sağlar.

> [!NOTE]
> Windows 8 ve Windows Server 2012 profil oluşturma Visual Studio bu platformlarda veri toplama şeklinde önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Bkz. [Uygulama ve Windows 8 performans Windows Server 2012.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Çalışan bir .NET hizmetine ekleme**|-   [Nasıl kullanılır: Eşzamanlılık verileri toplamak için profil oluşturma hizmetini bir .NET hizmetine ekleme](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Katman etkileşim verileri ekleme**|-   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Çalışan bir C/C++ hizmetine ekleme**|-   [Nasıl kullanılır: Eşzamanlılık verileri toplamak için yerel bir hizmete profil oluşturma ekleme](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-windows-services"></a>Profil Windows hizmetleri

|Görev|İlgili İçerik|
|----------|---------------------|
|**Örnekleme yöntemini kullanarak profil oluşturma**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Ölçümleme yöntemini kullanarak profil oluşturma**|-   [Ölçüm ölçümlerini kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profile.NET ayırma ve çöp toplama**|-   [.NET bellek verilerini toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Profil eşzamanlılık verileri

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına uygulamaların profilini oluşturma**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Web ASP.NET profil oluşturma**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Eşzamanlılık veri görünümlerini ve raporlarını analiz etme
- [Kaynakla ilgili veri görünümleri](../profiling/resource-contention-data-views.md)

- [Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
