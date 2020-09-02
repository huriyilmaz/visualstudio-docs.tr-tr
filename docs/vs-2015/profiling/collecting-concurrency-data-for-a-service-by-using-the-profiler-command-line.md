---
title: Profil oluşturucu komut satırını kullanarak bir hizmet için eşzamanlılık verileri toplama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7d56f0d8540da90925ebe2f5fc4ab8f6372bc3f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64785638"
---
# <a name="collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Profil Oluşturucu Komut Satırını Kullanarak bir Hizmet için Eşzamanlılık Verileri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil Oluşturma Araçları eşzamanlılık yöntemi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CPU kullanımı, iş parçacığı çakışması, iş parçacığı geçişi, eşitleme gecikmeleri, ÇAKıŞAN GÇ ve diğer sistem olayları gösteren kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamanıza olanak sağlar.  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Çalışan bir .NET hizmetine iliştirme**|-   [Nasıl yapılır: eşzamanlılık verileri toplamak için bir .NET hizmetine profil oluşturucu Iliştirme](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
|**Katman etkileşim verileri ekleme**|-   [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Çalışan bir C/C++ hizmetine iliştirme**|-   [Nasıl yapılır: eşzamanlılık verileri toplamak için profil oluşturucuyu yerel bir hizmete Iliştirme](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>İlgili görevler  
  
### <a name="profiling-windows-services"></a>Windows Hizmetleri profili oluşturma  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Örnekleme yöntemi kullanılarak profil**|-   [Örnekleme kullanarak uygulama Istatistikleri toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**İzleme yöntemini kullanarak profil**|-   [Izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**Profile.NET bellek ayırma ve çöp toplama**|-   [.NET bellek verileri toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="profiling-concurrency-data"></a>Eşzamanlılık verilerinin profilini oluşturma  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Tek başına uygulamalar profili**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**ASP.NET Web uygulamaları profili**|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-concurrency-data-views-and-reports"></a>Eşzamanlılık veri görünümlerini ve raporlarını çözümleme  
 [Kaynak Çakışması Veri Görünümleri](../profiling/resource-contention-data-views.md)  
  
 [Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)  
  
## <a name="reference"></a>Başvuru  
 [Komut satırı Profil Oluşturma Araçları başvurusu](../profiling/command-line-profiling-tools-reference.md)
