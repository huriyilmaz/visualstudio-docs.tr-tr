---
title: ASP.NET Web uygulamalarının komut satırı profili oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c93cb4774953f1425ff0330d7f588cbbf0f0b823
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64827442"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>ASP.NET Web Uygulamalarının Komut Satırından Profilinin Oluşturulması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] komut satırından profil oluşturma araçları kullanarak Web uygulamaları için performans verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Temel ASP.NET profil oluşturma verilerini kolayca toplayın:** **VSPerfCmd**için gereken yapılandırma gereksinimleri ve Internet INFORMATION SERVICES (IIS) yeniden başlatmaları olmadan örnekleme, izleme, .NET belleği, çekişme veya katman etkileşim verilerini toplamak Için **VSPerfASPNETCmd** aracını kullanın. **VSPerfASPNETCmd** , ek veri toplamanıza veya veri toplamayı denetlemenize izin vermez. **Note:**  **VSPerfASPNETCmd** , ASP.NET Web sitelerini profile için tek başına profil oluşturucuyu kullanacağınızı tercih ettiğiniz araçtır.|-   [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)|  
|**Uygulama Istatistiklerini topla:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanımı sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için kullanışlıdır.|-   [Örnekleme kullanarak uygulama Istatistikleri toplama](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için izleme yöntemini kullanın. İzleme verileri, GÇ sorunlarını analiz etmek ve uygulama senaryolarına ilişkin ayrıntılı analizler için yararlıdır.|-   [Izleme kullanarak ayrıntılı zamanlama verileri toplama](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**.Net bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya izleme kullanın. Ayrıca, her çöp toplama oluşturmada geri kazanılan nesne boyutunu ve sayısını gösteren nesne yaşam süresi verilerini toplayabilirsiniz.|-   [Bellek verileri toplanıyor](../profiling/collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line.md)|  
|**Eşzamanlılık verilerini topla:** Kaynak çakışması verilerini toplamak için eşzamanlılık yöntemini kullanın. **Note:**  Web uygulamaları için iş parçacığı etkinliği ve görselleştirme verilerinin toplanması desteklenmez.|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
|**Katman etkileşim verileri ekleme:** [!INCLUDE[vstecado](../includes/vstecado-md.md)] [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamasının bir Microsoft veritabanına yaptığı zaman uyumlu çağrılar hakkında performans verileri ekleyebilirsiniz [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-   [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>İlgili görevler  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Tek başına (istemci) uygulamalar profili**|-   [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profil hizmetleri**|-   [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)|
