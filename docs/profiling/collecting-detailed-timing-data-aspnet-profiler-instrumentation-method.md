---
title: 'VSPerfCmd: izleme kullanarak ASP.NET Web uygulaması için zamanlama verilerini al'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779655"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Komut satırından profil oluşturucu izleme yöntemini kullanarak bir ASP.NET Web uygulaması için ayrıntılı zamanlama verileri toplama
Bu bölümde, **VSPerfCmd** komut satırı aracı ve izleme yöntemi kullanılarak bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulaması için ayrıntılı performans verileri toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> **VSPerfCmd** Aracı, profil oluşturmayı duraklatma ve sürdürme ve Işlemci ve Windows performans sayaçlarından ek veri toplama dahil olmak üzere profil oluşturma araçları işlevselliğine yönelik tüm erişimi sağlar. Bu işlevselliğe ihtiyacınız olmadığında **VSPerfASPNETCmd** komut satırı aracını da kullanabilirsiniz. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracına kıyasla, hiçbir ortam değişkeni ayarlanamaz ve bilgisayarın yeniden başlatılması gerekmez. Daha fazla bilgi için bkz. [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Ortak görevler

|Görev|İlgili Içerik|
|----------|---------------------|
|**Statik olarak derlenen ikili dosyalar profili**|-   [nasıl yapılır: statik olarak derlenen bir ASP.NET uygulamasını işaretleme ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Dinamik olarak derlenen ikili dosyalar profili**|-   [nasıl yapılır: dinamik olarak derlenen bir ASP.NET uygulamasını işaretleme ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-aspnet-web-applications"></a>ASP.NET Web uygulamaları profili

|Görev|İlgili Içerik|
|----------|---------------------|
|**Örnekleme yöntemi kullanılarak profil**|[örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) -   |
|**Profil bellek ayırma ve çöp toplama**|[bellek verileri toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) -   |
|**Profil kaynağı çekişmesi ve iş parçacığı etkinliği**|-   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>İzleme yöntemini kullanarak profil

|Görev|İlgili Içerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamalar profili**|[izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) -   |
|**Profil hizmetleri**|[izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) -   |

### <a name="analyze-instrumentation-data-views-and-reports"></a>İzleme verileri görünümlerini ve raporlarını çözümleyin
- [İzleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
