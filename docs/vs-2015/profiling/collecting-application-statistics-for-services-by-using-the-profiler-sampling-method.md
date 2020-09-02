---
title: Profil Oluşturucu örnekleme yöntemini kullanarak hizmetler için uygulama Istatistikleri toplanıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f556a039ab131a563a90010112009b39f4c981
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64788928"
---
# <a name="collecting-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Profil Oluşturucu Örnekleme Yöntemini Kullanarak Hizmetler için Uygulama İstatistikleri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, komut satırından örnekleme yöntemi kullanılarak Windows Hizmetleri için performans istatistiklerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Profil oluşturucuyu bir .NET hizmetine iliştirme**|-   [Nasıl yapılır: uygulama Istatistikleri toplamak için bir .NET hizmetine profil oluşturucu Iliştirme](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|  
|**Katman etkileşim verileri ekleme**|-   [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Profiler 'ı bir C/C++ hizmetine iliştirme**|-   [Nasıl yapılır: uygulama Istatistikleri toplamak için bir yerel hizmete profil oluşturucu Iliştirme](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>İlgili görevler  
  
### <a name="profiling-windows-services"></a>Windows Hizmetleri profili oluşturma  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**İzleme yöntemini kullanarak profil**|-   [Izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**.NET bellek ayırma ve çöp toplama profili**|-   [.NET bellek verileri toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Profil kaynağı çekişmesi ve iş parçacığı etkinliği**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-by-using-the-sampling-method"></a>Örnekleme yöntemi kullanılarak profil oluşturma  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Tek başına (istemci) uygulamalar profili**|-   [Örnekleme kullanarak uygulama Istatistikleri toplama](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**ASP.NET Web uygulamaları profili**|-   [Örnekleme kullanarak uygulama Istatistikleri toplama](/visualstudio/profiling/collecting-concurrency-data-for-an-aspnet-web-application?view=vs-2015)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Örnekleme veri görünümlerini ve raporlarını çözümleme  
 [Örnekleme Yöntemi Veri Görünümleri](../profiling/profiler-sampling-method-data-views.md)
