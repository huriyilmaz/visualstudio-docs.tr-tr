---
title: ASP.NET web uygulamaları için istatistik toplama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: a2cae807a8d833cf2653ea23616eeb819673229e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773250"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>web uygulamaları ASP.NET için istatistik toplama

Bu **bölümde, VSPerfASPNETCmd** ve **VSPerfCmd** komut satırı aracını ve örnekleme profil oluşturma yöntemini kullanarak ASP.NET bir Web uygulaması için performans istatistikleri toplama yordamları ve seçenekleri açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

> [!NOTE]
> **VSPerfCmd** aracı, profil oluşturmayı duraklatma ve devam ettirme ve işlemci ve Windows performans sayaçlarından ek veri toplama gibi Profil Oluşturma Araçları işlevine tam erişim sağlar, ancak bu işlevselliğe ihtiyacınız olmadığında **VSPerfASPNETCmd** komut satırı aracını kullanmanız gerekir. **VSPerfASPNETCmd** komut satırı aracı, tek başına profil oluşturma ASP.NET Web sitelerini tek başına profilyaparken tercih edilen yöntemdir. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracıyla karşılaştırıldığında, ortam değişkenlerinin ayarlanması gerekmez ve bilgisayarın yeniden başlatılması gerekmez. Daha fazla bilgi [için, VSPerfASPNETCmd ile Hızlı web sitesi profilleme](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)bakın.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil oluşturucuyu ASP.NET uygulamasına takın**|-   [Nasıl yapilir: Uygulama istatistiklerini toplamak için profil oluşturucuyu ASP.NET bir web uygulamasına ekleme](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-aspnet-web-applications"></a>Web uygulamaları ASP.NET profil

|Görev|İlgili İçerik|
|----------|---------------------|
|**Enstrümantasyon yöntemini kullanarak profil**|-   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profil bellek ayırma ve çöp toplama**|-   [Bellek verilerini toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Profil kaynak çekişmesi ve iş parçacığı etkinliği**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>Örnek yöntem

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil tek başına (istemci) uygulamaları**|-   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **Profil hizmetleri**|-   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Örnekleme veri görünümlerini ve raporlarını analiz
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
