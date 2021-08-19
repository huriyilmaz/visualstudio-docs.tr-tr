---
title: Profil oluşturma komut satırı - ASP.NET web uygulaması bellek verilerini al
description: Bir web uygulaması için bellek ayırma ve nesne yaşam süresi tarihini toplamak üzere VSPerfCmd komut ASP.NET öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: b8cf73fda68447f1d64ba6a597e9bbab47c9011b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076847"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Profil oluşturma komut ASP.NET kullanarak bir web uygulamasından bellek verileri toplama
Bu bölümde, **VSPerfCmd** komut satırı aracını kullanarak bir ASP.NET web uygulaması için bellek ayırma ve nesne yaşam süresi verilerini toplamaya ilişkin yordamlar ve seçenekler açıklanır.

> [!NOTE]
> **VSPerfCmd** aracı, profil oluşturmayı duraklatma ve devam Profil Oluşturma Araçları işlemci ve performans sayaçlarından ek veri toplama da dahil olmak üzere Windows tam erişim sağlar. Bu işleve ihtiyacınız yoksa  **VSPerfASPNETCmd** komut satırı aracını da kullanabilirsiniz. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracıyla karşılaştırıldığında, ortam değişkeni ayarlanmaz ve bilgisayarın yeniden başlatılması gerekmez. Daha fazla bilgi için [bkz. VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)ile hızlı web sitesi profili oluşturma.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profilleyiciyi çalışan bir ASP.NET ekleme**|-   [Nasıl kullanılır: Bellek verilerini toplamak için ASP.NET web uygulamasına profil oluşturma ekleme](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Statik olarak derlenmiş ikilileri araçları**|-   [Nasıl kullanılır: Statik olarak derlenmiş bir uygulamayı ASP.NET ve bellek verileri toplama](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Dinamik olarak derlenmiş ikilileri ölçümle**|-   [Nasıl kullanılır: Dinamik olarak derlenmiş bir ASP.NET uygulamanın ölçümlerini ve bellek verilerini toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-aspnet-web-applications"></a>Web ASP.NET profil oluşturma

|Görev|İlgili İçerik|
|----------|---------------------|
|**Örnekleme yöntemini kullanarak profil oluşturma**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Ölçümleme yöntemini kullanarak profil oluşturma**|-   [Ölçüm ölçümlerini kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profil kaynak etkinliği ve iş parçacığı etkinliği**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Bellek .NET Framework profili oluşturma

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamaların profilini oluşturma**|-   [Bellek .NET Framework toplama](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Profil hizmetleri**|-   [.NET bellek verilerini toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>.NET bellek veri görünümlerini ve raporlarını analiz etme
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
