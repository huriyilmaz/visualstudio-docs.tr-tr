---
title: VSPerfCmd-izleme kullanarak ASP.NET Web uygulaması için zamanlama verilerini al
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 55f682152731391bdb0d4c0de0a307c00c16e2c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85331846"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>Komut satırından profil oluşturucu izleme yöntemini kullanarak bir ASP.NET Web uygulaması için ayrıntılı zamanlama verileri toplama
Bu bölümde, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] **VSPerfCmd** komut satırı aracını ve izleme yöntemini kullanarak bir Web uygulaması için ayrıntılı performans verileri toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> **VSPerfCmd** Aracı, profil oluşturmayı duraklatma ve sürdürme ve Işlemci ve Windows performans sayaçlarından ek veri toplama dahil olmak üzere profil oluşturma araçları işlevselliğine yönelik tüm erişimi sağlar. Bu işlevselliğe ihtiyacınız olmadığında  **VSPerfASPNETCmd** komut satırı aracını da kullanabilirsiniz. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracına kıyasla, hiçbir ortam değişkeni ayarlanamaz ve bilgisayarın yeniden başlatılması gerekmez. Daha fazla bilgi için bkz. [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Statik olarak derlenen ikili dosyalar profili**|-   [Nasıl yapılır: statik olarak derlenen bir ASP.NET uygulamasını Işaretleme ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Dinamik olarak derlenen ikili dosyalar profili**|-   [Nasıl yapılır: dinamik olarak derlenen bir ASP.NET uygulamasını Işaretleme ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-aspnet-web-applications"></a>ASP.NET Web uygulamaları profili

|Görev|İlgili İçerik|
|----------|---------------------|
|**Örnekleme yöntemi kullanılarak profil**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Profil bellek ayırma ve çöp toplama**|-   [Bellek verileri toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Profil kaynağı çekişmesi ve iş parçacığı etkinliği**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-by-using-the-instrumentation-method"></a>İzleme yöntemini kullanarak profil

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamalar profili**|-   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md)|
|**Profil hizmetleri**|-   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|

### <a name="analyze-instrumentation-data-views-and-reports"></a>İzleme verileri görünümlerini ve raporlarını çözümleyin
- [İzleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)
