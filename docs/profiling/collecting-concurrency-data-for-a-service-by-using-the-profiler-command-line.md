---
title: Profil oluşturucu komut satırı-hizmet için eşzamanlılık verileri al
description: Visual Studio Profil Oluşturma Araçları eşzamanlılık yöntemini kullanarak kaynak çekişme verilerini ve iş parçacığı etkinlik verilerini toplayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b4d65490c0ae75c7ab17fd7764d499cb39824f7
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148324"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Profil oluşturucu komut satırını kullanarak bir hizmet için eşzamanlılık verileri toplama
Profil Oluşturma Araçları eşzamanlılık yöntemi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CPU kullanımı, iş parçacığı çakışması, iş parçacığı geçişi, eşitleme gecikmeleri, ÇAKıŞAN GÇ ve diğer sistem olayları gösteren kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamanıza olanak sağlar.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Çalışan bir .NET hizmetine iliştirme**|-   [Nasıl yapılır: eşzamanlılık verileri toplamak için bir .NET hizmetine profil oluşturucu Iliştirme](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Katman etkileşim verileri ekleme**|-   [Katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Çalışan bir C/C++ hizmetine iliştirme**|-   [Nasıl yapılır: eşzamanlılık verileri toplamak için profil oluşturucuyu yerel bir hizmete Iliştirme](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-windows-services"></a>Profil Windows Hizmetleri

|Görev|İlgili İçerik|
|----------|---------------------|
|**Örnekleme yöntemi kullanılarak profil**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**İzleme yöntemini kullanarak profil**|-   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profile.NET bellek ayırma ve çöp toplama**|-   [.NET bellek verileri toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Eşzamanlılık verileri profili

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına uygulamalar profili**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**ASP.NET Web uygulamaları profili**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Eşzamanlılık veri görünümlerini ve raporlarını çözümleme
- [Kaynak çakışması veri görünümleri](../profiling/resource-contention-data-views.md)

- [Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
