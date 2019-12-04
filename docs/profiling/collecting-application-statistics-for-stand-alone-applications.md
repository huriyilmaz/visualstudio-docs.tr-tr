---
title: Tek başına uygulama istatistiklerini toplamak için profil oluşturucu komut satırını kullanın
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: de399bf493e328e583bdd2765822ca3a66144698
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779642"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Profil oluşturucu komut satırını kullanarak bağımsız uygulamalar için uygulama istatistikleri toplama
Bu bölümde, komut satırından örnekleme yöntemi kullanılarak bir istemci (tek başına) uygulamasının performans istatistiklerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Ortak görevler

|Görev|İlgili içerik|
|----------|---------------------|
|**Profil oluşturma kullanarak bir uygulamayı başlatma**|-   [nasıl yapılır: tek başına uygulama başlatma ve uygulama istatistiklerini toplama](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Profil oluşturucuyu çalışan bir .NET Framework uygulamasına iliştirme**|-   [nasıl yapılır: profil oluşturucuyu bir .NET Framework uygulamasına iliştirme ve uygulama istatistiklerini toplama](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Profil oluşturucuyu çalışan bir C/C++ uygulamasına iliştirme**|-   [nasıl yapılır: yerel bir uygulamaya profil oluşturucu iliştirme ve uygulama istatistikleri toplama](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Katman etkileşim verileri ekleme**|[katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) -   |

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-stand-alone-applications"></a>Tek başına uygulamalar profili

|Görev|İlgili içerik|
|----------|---------------------|
|**Bir uygulamayı işaretleme**|[izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) -   |
|**.NET bellek ayırma ve çöp toplama verileri toplayın**|[.NET Framework bellek verileri toplama](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) -   |
|**Kaynak çekişmesini ve iş parçacığı yürütme verilerini toplayın**|-   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Örnekleme yöntemi kullanılarak profil

|Görev|İlgili içerik|
|----------|---------------------|
|**ASP.NET Web uygulamaları profili**|[örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) -   |
|**Profil hizmetleri**|[örnekleme kullanarak uygulama Istatistiklerini toplayın](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)-   . Örnekleme yöntemi kullanılarak Windows hizmetlerinden performans istatistiklerinin nasıl toplanılacağını açıklar.|

### <a name="analyze-sampling-data-views-and-reports"></a>Örnekleme veri görünümlerini ve raporlarını çözümleyin
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
