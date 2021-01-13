---
title: Profil oluşturucu komut satırı-tek başına uygulama eşzamanlılık verilerini al
description: Visual Studio 'da profil oluşturucu komut satırını kullanarak tek başına uygulamalar için eşzamanlılık verileri toplayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- concurrency profiling method
- profiling tools,concurrency method
ms.assetid: 0a2c6d8a-50b3-48aa-b617-9137b049d21e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6a04740bdfd54a23ac1ac4e23e2007e0062ddcd3
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148292"
---
# <a name="collect-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Profil oluşturucu komut satırını kullanarak tek başına uygulamalar için eşzamanlılık verileri toplama
Profil Oluşturma Araçları eşzamanlılık yöntemi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CPU kullanımı, iş parçacığı çakışması, iş parçacığı geçişi, eşitleme gecikmeleri, ÇAKıŞAN GÇ ve diğer sistem olayları gösteren kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamanıza olanak sağlar.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili içerik|
|----------|---------------------|
|**.NET Framework bir uygulama başlatma ve eşzamanlılık verileri profili oluşturma**|-   [Nasıl yapılır: eşzamanlılık verileri toplamak için .NET Framework uygulaması başlatma](../profiling/how-to-launch-a-stand-alone-dotnet-framework-app-to-collect-concurrency-data.md)|
|**C/C++ uygulaması başlatma ve eşzamanlılık verileri profili oluşturma**|-   [Nasıl yapılır: eşzamanlılık verileri toplamak için yerel bir uygulama başlatma](../profiling/how-to-launch-a-stand-alone-native-application-to-collect-concurrency-data.md)|
|**Profil oluşturucuyu çalışan bir .NET Framework uygulamasına iliştirme**|-   [Nasıl yapılır: eşzamanlılık verileri toplamak için profil oluşturucuyu bir .NET Framework uygulamasına Iliştirme](../profiling/how-to-attach-the-profiler-to-a-dotnet-app-and-collect-concurrency-data.md)|
|**Profil oluşturucuyu çalışan bir C/C++ uygulamasına iliştirme**|-   [Nasıl yapılır: yerel bir uygulamaya profil oluşturucu Iliştirme ve eşzamanlılık verileri toplama](../profiling/how-to-attach-the-profiler-to-a-native-app-and-collect-concurrency-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-stand-alone-applications"></a>Tek başına uygulamalar profili

|Görev|İlgili içerik|
|----------|---------------------|
|**Örnekleme yöntemi kullanılarak profil**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**İzleme yöntemini kullanarak profil**|-   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**.NET bellek ayırma ve çöp toplama profili**|-   [.NET Framework bellek verileri toplama](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Katman etkileşim verileri ekleme**|-   [Katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|

### <a name="profile-concurrency-issues"></a>Profil eşzamanlılık sorunları

|Görev|İlgili içerik|
|----------|---------------------|
|**Profil ASP.NET uygulamaları**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|
|**Profil hizmetleri**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Eşzamanlılık veri görünümlerini ve raporlarını çözümleme
- [Kaynak çakışması veri görünümleri](../profiling/resource-contention-data-views.md)

- [Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
