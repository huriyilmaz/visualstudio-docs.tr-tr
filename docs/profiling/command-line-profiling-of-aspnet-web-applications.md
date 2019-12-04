---
title: ASP.NET Web uygulamalarının komut satırı profili oluşturma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: aa184667e5d569bc2662052a29b25bfea6e470a7
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779577"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>ASP.NET Web uygulamalarının komut satırı profili oluşturma
Bu bölümde, komut satırından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları kullanarak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamalarına yönelik performans verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Ortak görevler

| Görev | İlgili Içerik |
| - | - |
| **Temel ASP.NET profil oluşturma verilerini kolayca toplayın:** **VSPerfCmd**için gereken yapılandırma gereksinimleri ve Internet INFORMATION SERVICES (IIS) yeniden başlatmaları olmadan örnekleme, izleme, .NET belleği, çekişme veya katman etkileşim verilerini toplamak Için **VSPerfASPNETCmd** aracını kullanın. **VSPerfASPNETCmd** , ek veri toplamanıza veya veri toplamayı denetlemenize izin vermez. **Note:**  **VSPerfASPNETCmd** , ASP.NET Web sitelerini profile için tek başına profil oluşturucuyu kullanacağınızı tercih ettiğiniz araçtır. | [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) -    |
| **Uygulama Istatistiklerini topla:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanımı sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için kullanışlıdır. | [örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) -    |
| **Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için izleme yöntemini kullanın. İzleme verileri, GÇ sorunlarını analiz etmek ve uygulama senaryolarına ilişkin ayrıntılı analizler için yararlıdır. | [izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) -    |
| **.Net bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya izleme kullanın. Ayrıca, her çöp toplama oluşturmada geri kazanılan nesne boyutunu ve sayısını gösteren nesne yaşam süresi verilerini toplayabilirsiniz. | [bellek verileri toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) -    |
| **Eşzamanlılık verilerini topla:** Kaynak çakışması verilerini toplamak için eşzamanlılık yöntemini kullanın. **Note:**  Web uygulamaları için iş parçacığı etkinliği ve görselleştirme verilerinin toplanması desteklenmez. | -   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Katman etkileşim verileri ekleme:** [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasının bir Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] veritabanına yaptığı zaman uyumlu [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] çağrıları hakkında performans verileri ekleyebilirsiniz. | [katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) -    |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili Içerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamalar profili**|[tek başına uygulamalar -   profili](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profil hizmetleri**|-   [profili Hizmetleri](../profiling/command-line-profiling-of-services.md)|
