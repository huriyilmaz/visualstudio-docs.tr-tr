---
title: Profiler komut satırLarını kullanarak web uygulaması bellek verilerini ASP.NET alın
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 9e8d9fde00a2390793ae8efe05b684e73caca321
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773065"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Profiler komut satırını kullanarak ASP.NET bir web uygulamasından bellek verileri toplama
Bu **bölümde, VSPerfCmd** komut satırı aracını kullanarak ASP.NET bir Web uygulaması için bellek ayırma ve nesne yaşam boyu verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> **VSPerfCmd** aracı, profil oluşturmayı duraklatma ve devam ettirme ve işlemci ve Windows performans sayaçlarından ek veri toplama gibi Profil Oluşturma Araçları işlevlerine tam erişim sağlar. Bu işlevselliğe ihtiyacınız olmadığında **VSPerfASPNETCmd** komut satırı aracını da kullanabilirsiniz. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracıyla karşılaştırıldığında, ortam değişkenlerinin ayarlanması gerekmez ve bilgisayarın yeniden başlatılması gerekmez. Daha fazla bilgi [için, VSPerfASPNETCmd ile Hızlı web sitesi profilleme](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)bakın.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profiloluşturucuyu çalışan bir ASP.NET uygulamasına takın**|-   [Nasıl kullanılır: Bellek verileri toplamak için profil oluşturucuyu ASP.NET bir web uygulamasına ekleme](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Enstrüman statik olarak derlenmiş ikili**|-   [Nasıl yapılır: Statik olarak derlenmiş bir ASP.NET uygulama ve bellek verileri toplamak enstrüman](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Enstrüman dinamik olarak derlenmiş ikili**|-   [Nasıl yapılır: Dinamik olarak derlenmiş bir ASP.NET uygulama ve bellek verileri toplamak enstrüman](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-aspnet-web-applications"></a>Web uygulamaları ASP.NET profil

|Görev|İlgili İçerik|
|----------|---------------------|
|**Örnekleme yöntemini kullanarak profil**|-   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Enstrümantasyon yöntemini kullanarak profil**|-   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profil kaynak çekişmesi ve iş parçacığı etkinliği**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Profil .NET Framework bellek verileri

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil tek başına (istemci) uygulamaları**|-   [.NET Framework bellek verilerini topla](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Profil hizmetleri**|-   [.NET bellek verilerini toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>.NET bellek veri görünümlerini ve raporlarını analiz edin
- [.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
