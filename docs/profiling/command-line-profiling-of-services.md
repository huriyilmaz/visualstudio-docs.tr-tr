---
title: Hizmetlerin komut satırı profili oluşturma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b20835eaf8b81bd64bd90aa75d2efb32975a7c53
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74772837"
---
# <a name="command-line-profiling-of-services"></a>Komut satırından hizmetler profili oluşturma
Bu bölümde, komut satırından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları kullanarak Windows Hizmetleri için performans verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Ortak görevler

| Görev | İlgili Içerik |
| - | - |
| **Uygulama Istatistiklerini topla:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanımı sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için kullanışlıdır. | [örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) -    |
| **Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için izleme yöntemini kullanın. İzleme verileri, GÇ sorunlarını analiz etmek ve uygulama senaryolarına ilişkin ayrıntılı analizler için yararlıdır. | [izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) -    |
| **.Net bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya izleme kullanın. Ayrıca, her çöp toplama oluşturmada geri kazanılan nesne boyutunu ve sayısını gösteren nesne yaşam süresi verilerini toplayabilirsiniz. | [.net bellek verileri toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) -    |
| **Eşzamanlılık verilerini topla:** CPU kullanımını, iş parçacığı çekişmesini, iş parçacığı geçişini, eşitleme gecikmelerini, çakışan GÇ ve diğer sistem olaylarını gösteren kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın. | -   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Katman etkileşim verileri ekleme:** Hizmetin bir Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] veritabanına yaptığı zaman uyumlu ADO.NET çağrıları hakkında performans verileri ekleyebilirsiniz. | [katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) -    |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili Içerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamalar profili**|[tek başına uygulamalar -   profili](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profil ASP.NET uygulamaları**|-   [profili ASP.NET Web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
