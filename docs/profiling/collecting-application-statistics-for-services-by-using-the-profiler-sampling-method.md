---
title: Profil oluşturma hizmetleri Windows istatistikleri toplama - profil oluşturma örnekleme yöntemi
description: Komut satırdan profil oluşturma örnekleme yöntemini kullanarak Windows hizmetleri için performans istatistikleri toplamak için yordamları ve seçenekleri gözden geçirme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5012303345e02d3070e868f23f706fe785f3078a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107985"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Profil oluşturma örnekleme yöntemini kullanarak hizmetler için uygulama istatistikleri toplama
Bu bölümde, komut satırdan örnekleme yöntemini kullanarak Windows hizmetleri için performans istatistikleri toplamaya ilişkin yordamlar ve seçenekler açıklanır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil oluşturma hizmetini bir .NET hizmetine ekleme**|-   [Nasıl yapılanlar: Uygulama istatistikleri toplamak için bir .NET hizmetine profil oluşturma ekleme](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Katman etkileşim verileri ekleme**|-   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Profilleyiciyi C/C++ hizmetine ekleme**|-   [Nasıl yapılanlar: Uygulama istatistikleri toplamak için yerel bir hizmete profil oluşturma ekleme](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-windows-services"></a>Profil Windows hizmetleri

|Görev|İlgili İçerik|
|----------|---------------------|
|**Ölçümleme yöntemini kullanarak profil oluşturma**|-   [Ölçüm ölçümlerini kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**.NET bellek ayırma ve atık toplama profilini oluşturma**|-   [.NET bellek verilerini toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Profil kaynak etkinliği ve iş parçacığı etkinliği**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Örnekleme yöntemini kullanarak profil oluşturma

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamaların profilini oluşturma**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Web ASP.NET profil oluşturma**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Örnekleme veri görünümlerini ve raporlarını analiz etme
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
