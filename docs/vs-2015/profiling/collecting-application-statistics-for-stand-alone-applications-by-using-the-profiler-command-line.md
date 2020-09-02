---
title: Profil oluşturucu komut satırını kullanarak tek başına uygulamalar için uygulama Istatistikleri toplama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- profilng tools,sampling method
ms.assetid: be2dbdd0-fc88-45f9-a1d5-bcb4f64e17ad
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 03e27d021b8b3c5ec29a8646a1bbe7bc6ebdecc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64818357"
---
# <a name="collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line"></a>Profil Oluşturucu Komut Satırını Kullanarak Bağımsız Uygulamalar için Uygulama İstatistikleri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, komut satırından örnekleme yöntemi kullanılarak bir istemci (tek başına) uygulamasının performans istatistiklerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**Profil oluşturma kullanarak bir uygulamayı başlatma**|-   [Nasıl yapılır: tek başına uygulama başlatma ve uygulama Istatistiklerini toplama](../profiling/how-to-launch-a-stand-alone-application-with-the-profiler-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Profil oluşturucuyu çalışan bir .NET Framework uygulamasına iliştirme**|-   [Nasıl yapılır: profil oluşturucuyu bir .NET Framework uygulamasına Iliştirme ve uygulama Istatistiklerini toplama](../profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Profil oluşturucuyu çalışan bir C/C++ uygulamasına iliştirme**|-   [Nasıl yapılır: yerel bir uygulamaya profil oluşturucu Iliştirme ve uygulama Istatistikleri toplama](../profiling/how-to-attach-the-profiler-to-a-native-stand-alone-application-and-collect-application-statistics-by-using-the-command-line.md)|  
|**Katman etkileşim verileri ekleme**|-   [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>İlgili görevler  
  
### <a name="profiling-stand-alone-applications"></a>Bağımsız Uygulamaların Profilini Oluşturma  
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**Bir uygulamayı işaretleme**|-   [Izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**.NET bellek ayırma ve çöp toplama verileri toplayın**|-   [.NET Framework bellek verileri toplanıyor](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Kaynak çekişmesini ve iş parçacığı yürütme verilerini toplayın**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Örnekleme yöntemi kullanılarak profil oluşturma  
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**ASP.NET Web uygulamaları profili**|-   [Örnekleme kullanarak uygulama Istatistikleri toplama](/visualstudio/profiling/collecting-concurrency-data-for-an-aspnet-web-application?view=vs-2015)|  
|**Profil hizmetleri**|-   [Örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md). Örnekleme yöntemi kullanılarak Windows hizmetlerinden performans istatistiklerinin nasıl toplanılacağını açıklar.|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Örnekleme veri görünümlerini ve raporlarını çözümleme  
 [Örnekleme Yöntemi Veri Görünümleri](../profiling/profiler-sampling-method-data-views.md)
