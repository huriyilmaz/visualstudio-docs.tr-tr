---
title: ASP.NET Web Apps için istatistikleri toplama
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 017195cc86e958c70204a588de7678a5f15e6e09
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808935"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>ASP.NET Web Apps için istatistikleri toplama

Bu bölümde, **VSPerfASPNETCmd** ve **VSPerfCmd** komut satırı aracı ve örnekleme profili oluşturma yöntemi kullanılarak bir ASP.NET Web uygulaması için performans istatistikleri toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> **VSPerfCmd** Aracı, profil oluşturmayı duraklatma ve sürdürme ve Işlemci ve Windows performans sayaçlarından ek veri toplama dahil olmak üzere profil oluşturma araçları işlevselliğine erişim sağlar. bu işlevselliğe ihtiyaç duymadığınızda **VSPerfASPNETCmd** komut satırı aracını kullanmanız gerekir. **VSPerfASPNETCmd** komut satırı aracı, tek başına profil oluşturucuyu kullanarak ASP.NET Web sitelerini profil oluştururken tercih edilen yöntemdir. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracı ile karşılaştırıldığında, hiçbir ortam değişkeninin ayarlanması gerekmez ve bilgisayarın yeniden başlatılması gerekmez. Daha fazla bilgi için bkz. [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil oluşturucuyu bir ASP.NET uygulamasına iliştirme**|-   [Nasıl yapılır: uygulama istatistikleri toplamak için profil oluşturucuyu bir ASP.NET Web uygulamasına Iliştirme](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-aspnet-web-applications"></a>ASP.NET Web uygulamaları profili

|Görev|İlgili İçerik|
|----------|---------------------|
|**İzleme yöntemini kullanarak profil**|-   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Profil bellek ayırma ve çöp toplama**|-   [Bellek verileri toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|
|**Profil kaynağı çekişmesi ve iş parçacığı etkinliği**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="sample-method"></a>Örnek Yöntem

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamalar profili**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|-   **Profil hizmetleri**|-   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Örnekleme veri görünümlerini ve raporlarını çözümleyin
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
