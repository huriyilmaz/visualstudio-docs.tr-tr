---
title: Profil oluşturucu komut satırını kullanarak bir ASP.NET Web uygulamasından bellek verileri toplama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f7c759d4c2c4760be6782a518f4cdf209e828d4
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "64838101"
---
# <a name="collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Profil Oluşturucu Komut Satırını Kullanarak bir ASP.NET Web Uygulamasından Bellek Verileri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, **VSPerfCmd** komut satırı aracını kullanarak bir ASP.NET Web uygulaması için bellek ayırma ve nesne yaşam süresi verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.  
  
> [!NOTE]
> **VSPerfCmd** Aracı, profil oluşturmayı duraklatma ve sürdürme ve Işlemci ve Windows performans sayaçlarından ek veri toplama dahil olmak üzere profil oluşturma araçları işlevselliğine yönelik tüm erişimi sağlar. Bu işlevselliğe ihtiyacınız olmadığında  **VSPerfASPNETCmd** komut satırı aracını da kullanabilirsiniz. [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracı ile karşılaştırıldığında, hiçbir ortam değişkeninin ayarlanması gerekmez ve bilgisayarın yeniden başlatılması gerekmez. Daha fazla bilgi için bkz. [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Profil oluşturucuyu çalışan bir ASP.NET uygulamasına iliştirme**|-   [Nasıl yapılır: bellek verileri toplamak için profil oluşturucuyu bir ASP.NET Web uygulamasına Iliştirme](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Statik olarak derlenen ikili dosyaları işaretleme**|-   [Nasıl yapılır: statik olarak derlenen bir ASP.NET uygulamasını Işaretleme ve bellek verileri toplama](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Dinamik olarak derlenen ikili dosyaları işaretleme**|-   [Nasıl yapılır: dinamik olarak derlenen bir ASP.NET uygulamasını Işaretleme ve bellek verileri toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="related-tasks"></a>İlgili görevler  
  
### <a name="profiling-aspnet-web-applications"></a>ASP.NET Web Uygulamalarında Profil Oluşturma  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Örnekleme yöntemi kullanılarak profil**|-   [Örnekleme kullanarak uygulama Istatistikleri toplama](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**İzleme yöntemini kullanarak profil**|-   [Izleme kullanarak ayrıntılı zamanlama verileri toplama](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**Profil kaynağı çekişmesi ve iş parçacığı etkinliği**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-net-framework-memory-data"></a>.NET Framework bellek verileri profili oluşturma  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Tek başına (istemci) uygulamalar profili**|-   [.NET Framework bellek verileri toplanıyor](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profil hizmetleri**|-   [.NET bellek verileri toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-net-memory-data-views-and-reports"></a>.NET bellek verileri görünümlerini ve raporlarını çözümleme  
 [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Başvuru  
 [Komut satırı Profil Oluşturma Araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
