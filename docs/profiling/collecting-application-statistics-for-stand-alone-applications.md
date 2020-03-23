---
title: Tek başına uygulama istatistikleri toplamak için profiler komut satırLarını kullanın
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779642"
---
# <a name="collect-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Profil oluşturucu komut satırını kullanarak bağımsız uygulamalar için uygulama istatistikleri toplama
Bu bölümde, komut satırından örnekleme yöntemini kullanarak istemci (tek başına) uygulaması için performans istatistikleri toplamak için yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Bkz. Windows 8 ve Windows Server 2012 uygulamalarında Performans araçları.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili içerik|
|----------|---------------------|
|**Profil oluşturmayı kullanarak bir uygulama başlatma**|-   [Nasıl yapilir: Tek başına bir uygulama başlatın ve uygulama istatistiklerini toplayın](../profiling/how-to-launch-a-stand-alone-app-and-collect-application-statistics.md)|
|**Çalışan bir .NET Framework uygulamasına profil oluşturucuyu ekleme**|-   [Nasıl yapilir: Profiloluşturciyi bir .NET Framework uygulamasına takın ve uygulama istatistiklerini toplayın](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-application-statistics.md)|
|**Profiloluşturciyi çalışan c/c++ uygulamasına takın**|-   [Nasıl yapilir: Profiloluşturciyi yerel bir uygulamaya takın ve uygulama istatistiklerini toplayın](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-application-statistics.md)|
|**Katman etkileşimi verileri ekleme**|-   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-stand-alone-applications"></a>Profil tek başına uygulamalar

|Görev|İlgili içerik|
|----------|---------------------|
|**Enstrüman bir uygulama**|-   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**.NET bellek ayırma ve çöp toplama verilerini toplama**|-   [.NET Framework bellek verilerini topla](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Kaynak çekişmesi ve iş parçacığı yürütme verilerini toplama**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|

### <a name="profile-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak profil

|Görev|İlgili içerik|
|----------|---------------------|
|**Web uygulamaları ASP.NET profil**|-   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profil hizmetleri**|-   [Örneklemeyi kullanarak uygulama istatistiklerini toplayın.](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) Örnekleme yöntemini kullanarak Windows hizmetlerinden performans istatistiklerinin nasıl toplandığını açıklar.|

### <a name="analyze-sampling-data-views-and-reports"></a>Örnekleme veri görünümlerini ve raporlarını analiz
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
