---
title: Profil oluşturucu komut satırını kullanarak ASP.NET Web uygulaması bellek verileri alın
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74773065"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Profil oluşturucu komut satırını kullanarak bir ASP.NET Web uygulamasından bellek verileri toplama
Bu bölümde, **VSPerfCmd** komut satırı aracını kullanarak bir ASP.NET Web uygulaması için bellek ayırma ve nesne yaşam süresi verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> **VSPerfCmd** Aracı, profil oluşturmayı duraklatma ve sürdürme ve Işlemci ve Windows performans sayaçlarından ek veri toplama dahil olmak üzere profil oluşturma araçları işlevselliğine yönelik tüm erişimi sağlar. Bu işlevselliğe ihtiyacınız olmadığında **VSPerfASPNETCmd** komut satırı aracını da kullanabilirsiniz. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracı ile karşılaştırıldığında, hiçbir ortam değişkeninin ayarlanması gerekmez ve bilgisayarın yeniden başlatılması gerekmez. Daha fazla bilgi için bkz. [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Ortak görevler

|Görev|İlgili Içerik|
|----------|---------------------|
|**Profil oluşturucuyu çalışan bir ASP.NET uygulamasına iliştirme**|-   [nasıl yapılır: bellek verileri toplamak için profil oluşturucuyu bir ASP.NET Web uygulamasına iliştirme](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Statik olarak derlenen ikili dosyaları işaretleme**|-   [nasıl yapılır: statik olarak derlenen bir ASP.NET uygulamasını işaretleme ve bellek verileri toplama](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Dinamik olarak derlenen ikili dosyaları işaretleme**|-   [nasıl yapılır: dinamik olarak derlenen bir ASP.NET uygulamasını işaretleme ve bellek verileri toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-aspnet-web-applications"></a>ASP.NET Web uygulamaları profili

|Görev|İlgili Içerik|
|----------|---------------------|
|**Örnekleme yöntemi kullanılarak profil**|[örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) -   |
|**İzleme yöntemini kullanarak profil**|[izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) -   |
|**Profil kaynağı çekişmesi ve iş parçacığı etkinliği**|-   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>.NET Framework bellek verileri profili

|Görev|İlgili Içerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamalar profili**|[.NET Framework bellek verileri toplama](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) -   |
|**Profil hizmetleri**|[.net bellek verileri toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) -   |

### <a name="analyze-net-memory-data-views-and-reports"></a>.NET bellek verileri görünümlerini ve raporlarını çözümleyin
- [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Başvuru
- [Komut satırı profil oluşturma araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
