---
title: Profil Oluşturucu örnekleme yöntemini kullanarak uygulama istatistikleri toplama
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779694"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Profil Oluşturucu örnekleme yöntemini kullanarak hizmetler için uygulama istatistikleri toplama
Bu bölümde, komut satırından örnekleme yöntemi kullanılarak Windows Hizmetleri için performans istatistiklerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Ortak görevler

|Görev|İlgili Içerik|
|----------|---------------------|
|**Profil oluşturucuyu bir .NET hizmetine iliştirme**|-   [nasıl yapılır: uygulama istatistikleri toplamak için bir .net hizmetine profil oluşturucu iliştirme](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Katman etkileşim verileri ekleme**|[katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) -   |
|**Profiler 'ı bir C/C++ Service 'e iliştirme**|-   [nasıl yapılır: uygulama istatistikleri toplamak için bir yerel hizmete profil oluşturucu iliştirme](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-windows-services"></a>Profil Windows Hizmetleri

|Görev|İlgili Içerik|
|----------|---------------------|
|**İzleme yöntemini kullanarak profil**|[izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) -   |
|**.NET bellek ayırma ve çöp toplama profili**|[.net bellek verileri toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) -   |
|**Profil kaynağı çekişmesi ve iş parçacığı etkinliği**|-   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Örnekleme yöntemi kullanılarak profil

|Görev|İlgili Içerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamalar profili**|[örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md) -   |
|**ASP.NET Web uygulamaları profili**|[örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) -   |

### <a name="analyze-sampling-data-views-and-reports"></a>Örnekleme veri görünümlerini ve raporlarını çözümleyin
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
