---
title: Tek başına uygulamaların komut satırı profili oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f4b2b78f7187b7a49b78312a1105a2af884fda3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186632"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Bağımsız Uygulamaların Komut Satırından Profilinin Oluşturulması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, komut satırından Profil Oluşturma Araçları kullanarak tek başına (istemci) uygulamalar için performans verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|İlgili içerik|  
|----------|---------------------|  
|**Uygulama Istatistiklerini topla:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanımı sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için kullanışlıdır.|-   [Örnekleme kullanarak uygulama Istatistikleri toplama](../profiling/collecting-application-statistics-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için izleme yöntemini kullanın. İzleme verileri, g/ç sorunlarını analiz etmek ve uygulama senaryolarına ilişkin ayrıntılı analizler için yararlıdır.|-   [Izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application-by-using-the-profiler-command-line.md)|  
|**.Net bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya izleme kullanın. Ayrıca, her çöp toplama oluşturmada geri kazanılan nesne boyutunu ve sayısını gösteren nesne yaşam süresi verilerini toplayabilirsiniz.|-   [.NET Framework bellek verileri toplanıyor](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Eşzamanlılık verilerini topla:** CPU kullanımı, iş parçacığı çakışması, iş parçacığı geçişi, eşitleme gecikmeleri, çakışan g/ç ve diğer sistem olayları gibi kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın.|-   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Katman etkileşim verileri ekleyin:** Uygulamanın bir Microsoft veritabanına yaptığı zaman uyumlu ADO.NET çağrıları hakkında performans verileri ekleyebilirsiniz [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir.|-   [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md)|  
|**Deneyin:** Örnekleme veya izleme yöntemini kullanarak örnek bir istemci uygulaması profili eklemek için adım adım yordamları kullanın.|-   [İzlenecek yol: örnekleme kullanarak komut satırı profili oluşturma](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [İzlenecek yol: Izleme kullanarak komut satırı profili oluşturma](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)|  
  
## <a name="related-tasks"></a>İlgili görevler  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Profil ASP.NET uygulamaları**|-   [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)|  
|**Profil hizmetleri**|-   [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)|
