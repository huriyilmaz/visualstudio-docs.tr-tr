---
title: Hizmet için eşzamanlılık verilerini almak üzere profil oluşturucu komut satırını kullanma
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779681"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Profil oluşturucu komut satırını kullanarak bir hizmet için eşzamanlılık verileri toplama
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları eşzamanlılık yöntemi, CPU kullanımını, iş parçacığı çekişmesini, iş parçacığı geçişini, eşitleme gecikmelerini, çakışan GÇ ve diğer sistem olaylarını gösteren kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamanıza olanak sağlar.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Ortak görevler

|Görev|İlgili Içerik|
|----------|---------------------|
|**Çalışan bir .NET hizmetine iliştirme**|-   [nasıl yapılır: eşzamanlılık verileri toplamak için bir .net hizmetine profil oluşturucu iliştirme](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Katman etkileşim verileri ekleme**|[katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) -   |
|**Çalışan bir C/C++ Service 'e iliştirme**|-   [nasıl yapılır: eşzamanlılık verileri toplamak için profil oluşturucuyu yerel bir hizmete iliştirme](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-windows-services"></a>Profil Windows Hizmetleri

|Görev|İlgili Içerik|
|----------|---------------------|
|**Örnekleme yöntemi kullanılarak profil**|[örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) -   |
|**İzleme yöntemini kullanarak profil**|[izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) -   |
|**Profile.NET bellek ayırma ve çöp toplama**|[.net bellek verileri toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) -   |

### <a name="profile-concurrency-data"></a>Eşzamanlılık verileri profili

|Görev|İlgili Içerik|
|----------|---------------------|
|**Tek başına uygulamalar profili**|-   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**ASP.NET Web uygulamaları profili**|-   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Eşzamanlılık veri görünümlerini ve raporlarını çözümleme
- [Kaynak çakışması veri görünümleri](../profiling/resource-contention-data-views.md)

- [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
