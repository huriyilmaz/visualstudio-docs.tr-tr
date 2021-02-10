---
title: ASP.NET Web uygulamalarının profil oluşturmayı Command-Line | Microsoft Docs
description: ASP.NET Web uygulamalarına ilişkin performans verilerini toplamak için komut satırından Profil Oluşturma Araçları nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: e97e6a3d9115be2b14cac4e87698c6eeb9fc091d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945194"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>ASP.NET Web uygulamalarının komut satırı profili oluşturma
Bu bölümde, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] komut satırından profil oluşturma araçları kullanarak Web uygulamaları için performans verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Temel ASP.NET profil oluşturma verilerini kolayca toplayın:** **VSPerfCmd** için gereken yapılandırma gereksinimleri ve Internet INFORMATION SERVICES (IIS) yeniden başlatmaları olmadan örnekleme, izleme, .NET belleği, çekişme veya katman etkileşim verilerini toplamak Için **VSPerfASPNETCmd** aracını kullanın. **VSPerfASPNETCmd** , ek veri toplamanıza veya veri toplamayı denetlemenize izin vermez. **Note:**  **VSPerfASPNETCmd** , ASP.NET Web sitelerini profile için tek başına profil oluşturucuyu kullanacağınızı tercih ettiğiniz araçtır. | -   [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Uygulama Istatistiklerini topla:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanımı sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için kullanışlıdır. | -   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için izleme yöntemini kullanın. İzleme verileri, GÇ sorunlarını analiz etmek ve uygulama senaryolarına ilişkin ayrıntılı analizler için yararlıdır. | -   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **.Net bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya izleme kullanın. Ayrıca, her çöp toplama oluşturmada geri kazanılan nesne boyutunu ve sayısını gösteren nesne yaşam süresi verilerini toplayabilirsiniz. | -   [Bellek verileri toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Eşzamanlılık verilerini topla:** Kaynak çakışması verilerini toplamak için eşzamanlılık yöntemini kullanın. **Note:**  Web uygulamaları için iş parçacığı etkinliği ve görselleştirme verilerinin toplanması desteklenmez. | -   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Katman etkileşim verileri ekleme:** [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasının bir Microsoft veritabanına yaptığı zaman uyumlu çağrılar hakkında performans verileri ekleyebilirsiniz [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] . | -   [Katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamalar profili**|-   [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profil hizmetleri**|-   [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)|
