---
title: Profil oluşturma komut satırı - Tek başına uygulama eşzamanlılık verilerini al
description: Profil oluşturma komut satırı kullanarak tek başına uygulamalar için eşzamanlılık verilerini Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5d5b02fb61082f1bea1936e4590c8fd7f478ea60
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093352"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Profil oluşturma komut satırı kullanarak tek başına uygulamalar için eşzamanlılık verileri toplama
Profil Oluşturma Araçları eşzamanlılık yöntemi; CPU kullanımı, iş parçacığı çakışması, iş parçacığı geçişi, eşitleme gecikmeleri, çakışan IO alanlarını ve diğer sistem olaylarını gösteren kaynak çakışma verilerini ve iş parçacığı etkinlik verilerini toplamaya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olanak sağlar.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili içerik|
|----------|---------------------|
|**Bir .NET Framework uygulama ve profil eşzamanlılık verileri başlatma**|-   [Nasıl kullanılır: Eşzamanlılık .NET Framework için bir uygulama başlatma](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**C/C++ uygulaması ve profil eşzamanlılık verileri başlatma**|-   [Nasıl kullanılır: Eşzamanlılık verileri toplamak için yerel bir uygulama başlatma](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Profilleyiciyi çalışan bir .NET Framework ekleme**|-   [Nasıl kullanılır: Eşzamanlılık verileri toplamak .NET Framework profil oluşturma uygulamasına profil oluşturma](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Profilleyiciyi çalışan bir C/C++ uygulamasına ekleme**|-   [Nasıl kullanılır: Profilleyiciyi yerel bir uygulamaya ekleme ve eşzamanlılık verileri toplama](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-stand-alone-applications"></a>Tek başına uygulamaların profilini oluşturma

|Görev|İlgili içerik|
|----------|---------------------|
|**Örnekleme yöntemini kullanarak profil oluşturma**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Ölçümleme yöntemini kullanarak profil oluşturma**|-   [Ölçüm ölçümlerini kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**.NET bellek ayırma ve atık toplama profilini oluşturma**|-   [Bellek .NET Framework toplama](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Katman etkileşim verileri ekleme**|-   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Profil eşzamanlılığı sorunları

|Görev|İlgili içerik|
|----------|---------------------|
|**Profil ASP.NET uygulamaları**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Profil hizmetleri**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Eşzamanlılık veri görünümlerini ve raporlarını analiz etme
- [Kaynakla ilgili veri görünümleri](../profiling/resource-contention-data-views.md)

- [Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
