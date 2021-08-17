---
title: 'Profil oluşturma komut satırı: Tek başına uygulama istatistikleri toplama'
description: Profil oluşturma komut satırı kullanarak tek başına uygulamalar için uygulama istatistiklerini Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2dbc5e6dea90f60e5474d27c19a23fc0a10e348ba1ad3529d106555b885c195b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397013"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Profil oluşturucu komut satırını kullanarak bağımsız uygulamalar için uygulama istatistikleri toplama
Bu bölümde, komut satırı örnekleme yöntemini kullanarak bir istemci (tek başına) uygulaması için performans istatistikleri toplamaya ilişkin yordamlar ve seçenekler açıklanır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Bkz. [Uygulama ve Windows 8 performans Windows Server 2012 araçları.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili içerik|
|----------|---------------------|
|**Profil oluşturmayı kullanarak uygulama başlatma**|-   [Nasıl: Tek başına bir uygulama başlatma ve uygulama istatistikleri toplama](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Profilleyiciyi çalışan bir .NET Framework ekleme**|-   [Nasıl .NET Framework: Profil oluşturma .NET Framework uygulama istatistikleri toplama](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Profilleyiciyi çalışan bir C/C++ uygulamasına ekleme**|-   [Nasıl yapılanlar: Profilleyiciyi yerel bir uygulamaya ekleme ve uygulama istatistikleri toplama](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Katman etkileşim verileri ekleme**|-   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-stand-alone-applications"></a>Tek başına uygulamaların profilini oluşturma

|Görev|İlgili içerik|
|----------|---------------------|
|**Bir uygulamayı ölçümle**|-   [Ölçüm ölçümlerini kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**.NET bellek ayırma ve atık toplama verilerini toplama**|-   [Bellek .NET Framework toplama](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Kaynak ve iş parçacığı yürütme verilerini toplama**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak profil oluşturma

|Görev|İlgili içerik|
|----------|---------------------|
|**Web ASP.NET profil oluşturma**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profil hizmetleri**|-   [Örnekleme kullanarak uygulama istatistikleri toplama.](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) Örnekleme yöntemini kullanarak hizmetlerden performans Windows toplamayı açıklar.|

### <a name="analyze-sampling-data-views-and-reports"></a>Örnekleme veri görünümlerini ve raporlarını analiz etme
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
