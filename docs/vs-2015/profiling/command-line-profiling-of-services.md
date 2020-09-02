---
title: Hizmetlerin komut satırı profili oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64cd62c29df9a7c43d690119194582b20a784c3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808263"
---
# <a name="command-line-profiling-of-services"></a>Komut Satırından Hizmetler Profili Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, komut satırından Profil Oluşturma Araçları kullanarak Windows Hizmetleri için performans verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Uygulama Istatistiklerini topla:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanımı sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için kullanışlıdır.|-   [Örnekleme kullanarak uygulama Istatistikleri toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
|**Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için izleme yöntemini kullanın. İzleme verileri, GÇ sorunlarını analiz etmek ve uygulama senaryolarına ilişkin ayrıntılı analizler için yararlıdır.|-   [Izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method-from-the-profiler-command-line.md)|  
|**.Net bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya izleme kullanın. Ayrıca, her çöp toplama oluşturmada geri kazanılan nesne boyutunu ve sayısını gösteren nesne yaşam süresi verilerini toplayabilirsiniz.|-   [.NET bellek verileri toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
|**Eşzamanlılık verilerini topla:** CPU kullanımını, iş parçacığı çekişmesini, iş parçacığı geçişini, eşitleme gecikmelerini, çakışan GÇ ve diğer sistem olaylarını gösteren kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın.|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|  
|**Katman etkileşim verileri ekleme:** Hizmetin bir Microsoft veritabanına yaptığı zaman uyumlu ADO.NET çağrıları hakkında performans verileri ekleyebilirsiniz [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-   [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
  
## <a name="related-tasks"></a>İlgili görevler  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Tek başına (istemci) uygulamalar profili**|-   [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profil ASP.NET uygulamaları**|-   [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
