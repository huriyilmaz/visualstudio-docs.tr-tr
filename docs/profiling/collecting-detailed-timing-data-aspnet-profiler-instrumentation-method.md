---
title: 'VSPerfCmd: Enstrümantasyon kullanarak ASP.NET web uygulaması için zamanlama verileri alın'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: d764ef32cdcb061992817d433dabb6ae61b64fd9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779655"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Komut satırından profil oluşturma enstrümantasyon yöntemini kullanarak ASP.NET bir web uygulaması için ayrıntılı zamanlama verileri toplama
Bu **bölümde, VSPerfCmd** komut satırı [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aracını ve enstrümantasyon yöntemini kullanarak bir Web uygulaması için ayrıntılı performans verileri toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> **VSPerfCmd** aracı, profil oluşturmayı duraklatma ve devam ettirme ve işlemci ve Windows performans sayaçlarından ek veri toplama gibi Profil Oluşturma Araçları işlevlerine tam erişim sağlar. Bu işlevselliğe ihtiyacınız olmadığında **VSPerfASPNETCmd** komut satırı aracını da kullanabilirsiniz. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracıyla karşılaştırıldığında, ortam değişkenlerinin ayarlanması gerekmez ve bilgisayarı yeniden başlatmak gerekmez. Daha fazla bilgi [için, VSPerfASPNETCmd ile Hızlı web sitesi profilleme](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)bakın.

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil statik olarak derlenmiş ikili**|-   [Nasıl yapılır: Statik olarak derlenmiş bir ASP.NET uygulama ve ayrıntılı zamanlama verileri toplamak enstrüman](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Profil dinamik olarak derlenmiş ikili**|-   [Nasıl yapılır: Dinamik olarak derlenmiş bir ASP.NET uygulama ve ayrıntılı zamanlama verileri toplamak enstrüman](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-aspnet-web-applications"></a>Web uygulamaları ASP.NET profil

|Görev|İlgili İçerik|
|----------|---------------------|
|**Örnekleme yöntemini kullanarak profil**|-   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profil bellek ayırma ve çöp toplama**|-   [Bellek verilerini toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Profil kaynak çekişmesi ve iş parçacığı etkinliği**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>Enstrümantasyon yöntemini kullanarak profil

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil tek başına (istemci) uygulamaları**|-   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profil hizmetleri**|-   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>Enstrümantasyon veri görünümlerini ve raporlarını analiz edin
- [Enstrümantasyon yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
