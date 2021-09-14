---
title: izleme kullanarak ASP.NET için zamanlama verileri toplama
description: vsperfcmd kullanarak bir ASP.NET Web uygulaması için ayrıntılı performans verileri nasıl toplayacağınızı öğrenin. Profil Oluşturma Araçları işlevlere tamamen erişim sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools,instrumentation method
- instrumentation profiling method
ms.assetid: 29f2fc55-aaf7-4e18-a672-8815455fba73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 78bcf3fcb7ae2512a3ab92474f68cc80e238a765
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635822"
---
# <a name="collect-detailed-timing-data-for-an-aspnet-web-application-using-the-profiler-instrumentation-method-from-the-command-line"></a>komut satırından profil oluşturucu izleme yöntemini kullanarak bir ASP.NET web uygulaması için ayrıntılı zamanlama verileri toplama
Bu bölümde, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] **VSPerfCmd** komut satırı aracını ve izleme yöntemini kullanarak bir Web uygulaması için ayrıntılı performans verileri toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> **vsperfcmd** aracı, profil oluşturmayı duraklatma ve sürdürme ve işlemci ve Windows performans sayaçlarından ek veri toplama dahil Profil Oluşturma Araçları işlevlere yönelik tüm erişimleri sağlar. Bu işlevselliğe ihtiyacınız olmadığında  **VSPerfASPNETCmd** komut satırı aracını da kullanabilirsiniz. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracına kıyasla, hiçbir ortam değişkeni ayarlanamaz ve bilgisayarın yeniden başlatılması gerekmez. Daha fazla bilgi için bkz. [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Statik olarak derlenen ikili dosyalar profili**|-   [nasıl yapılır: statik olarak derlenen ASP.NET bir uygulamayı izleme ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-statically-compiled-aspnet-and-collect-detailed-timing-data.md)|
|**Dinamik olarak derlenen ikili dosyalar profili**|-   [nasıl yapılır: dinamik olarak derlenen ASP.NET bir uygulamayı izleme ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-aspnet-web-applications"></a>web uygulamalarının profilini ASP.NET

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
