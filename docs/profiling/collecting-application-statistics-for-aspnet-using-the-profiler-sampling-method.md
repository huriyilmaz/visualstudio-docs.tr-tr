---
title: ASP.NET web apps için istatistikleri toplama
description: vsperfaspnetcmd ve vsperfcmd aracını ve örnekleme profil oluşturma yöntemini kullanarak ASP.NET Web apps için performans istatistikleri toplamak üzere yordamları ve seçenekleri gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 37ab8f286f9c21c98899e94cd197473b50620675
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142370"
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>ASP.NET web apps için istatistikleri toplama

bu bölümde, **vsperfaspnetcmd** ve **vsperfcmd** komut satırı aracı ve örnekleme profili oluşturma yöntemi kullanılarak bir ASP.NET Web uygulaması için performans istatistiklerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 gelişmiş güvenlik özellikleri Visual Studio profiler 'ın bu platformlarda verileri topladıkları şekilde gerekli önemli değişikliklere sahiptir. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

> [!NOTE]
> **vsperfcmd** aracı, profil oluşturmayı duraklatma ve sürdürme ve işlemci ve Windows performans sayaçlarından ek veri toplama dahil olmak üzere Profil Oluşturma Araçları işlevselliğine erişim sağlar. bu işlevselliğe gerek duymadığınızda **vsperfaspnetcmd** komut satırı aracını kullanmanız gerekir. **vsperfaspnetcmd** komut satırı aracı, tek başına profil oluşturucuyu kullanarak ASP.NET Web siteleri profili oluşturulurken tercih edilen yöntemdir. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracı ile karşılaştırıldığında, hiçbir ortam değişkeninin ayarlanması gerekmez ve bilgisayarın yeniden başlatılması gerekmez. Daha fazla bilgi için bkz. [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Genel görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**profil oluşturucuyu bir ASP.NET uygulamasına iliştirme**|-   [nasıl yapılır: uygulama istatistikleri toplamak için profil oluşturucuyu bir ASP.NET web uygulamasına iliştirme](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>İlişkili görevler

### <a name="profile-aspnet-web-applications"></a>web uygulamalarının profilini ASP.NET

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
