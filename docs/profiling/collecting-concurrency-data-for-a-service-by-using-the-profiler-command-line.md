---
title: Profil oluşturucu komut satırı-hizmet için eşzamanlılık verileri al
description: Visual Studio Profil Oluşturma Araçları eşzamanlılık yöntemini kullanarak kaynak çekişmesini ve iş parçacığı etkinlik verilerini toplayın.
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
ms.openlocfilehash: 53c44915ce1172b90a2896d3429f2866454f9820
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635857"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Profil oluşturucu komut satırını kullanarak bir hizmet için eşzamanlılık verileri toplama
Profil Oluşturma Araçları eşzamanlılık yöntemi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CPU kullanımı, iş parçacığı çakışması, iş parçacığı geçişi, eşitleme gecikmeleri, ÇAKıŞAN GÇ ve diğer sistem olayları gösteren kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamanıza olanak sağlar.

> [!NOTE]
> Windows 8 ve Windows Server 2012 gelişmiş güvenlik özellikleri Visual Studio profiler 'ın bu platformlarda verileri topladıkları şekilde gerekli önemli değişikliklere sahiptir. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Çalışan bir .NET hizmetine iliştirme**|-   [Nasıl yapılır: eşzamanlılık verileri toplamak için bir .NET hizmetine profil oluşturucu Iliştirme](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Katman etkileşim verileri ekleme**|-   [Katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Çalışan bir C/C++ hizmetine iliştirme**|-   [Nasıl yapılır: eşzamanlılık verileri toplamak için profil oluşturucuyu yerel bir hizmete Iliştirme](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-windows-services"></a>profil Windows hizmetleri

|Görev|İlgili İçerik|
|----------|---------------------|
|**Örnekleme yöntemi kullanılarak profil**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**İzleme yöntemini kullanarak profil**|-   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profile.NET bellek ayırma ve çöp toplama**|-   [.NET bellek verileri toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Eşzamanlılık verileri profili

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına uygulamalar profili**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Web uygulamalarının profilini ASP.NET**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Eşzamanlılık veri görünümlerini ve raporlarını çözümleme
- [Kaynak çakışması veri görünümleri](../profiling/resource-contention-data-views.md)

- [Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
