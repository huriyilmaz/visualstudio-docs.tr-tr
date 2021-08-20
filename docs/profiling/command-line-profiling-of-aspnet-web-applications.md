---
title: Command-Line Web Uygulamaları ASP.NET Profil Oluşturma | Microsoft Docs
description: Web uygulamalarına Profil Oluşturma Araçları verileri toplamak için komut satırına ASP.NET öğrenin.
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
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 9d551922a3088c7febe07f47d35af04511774a09
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107972"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Web uygulamalarının komut ASP.NET profili oluşturma
Bu bölümde, komut satırına ilişkin verileri kullanarak web uygulamaları için performans verilerini [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] toplamaya Profil Oluşturma Araçları yordamları ve seçenekleri açıklanır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Bkz. [Uygulama ve Windows 8 performans Windows Server 2012.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Profil oluşturma ASP.NET kolayca temel verileri toplayın:** **VsPerfASPNETCmd** aracını kullanarak yapılandırma gereksinimleri ve **VSPerfCmd** için gereken Internet Information Services (IIS) yeniden başlatmaları olmadan örnekleme, ölçüm, .NET belleği, karşılaştırması veya katman etkileşim verilerini toplayın. **VSPerfASPNETCmd,** ek veri toplama veya veri toplamayı denetlemeye izin vermez. **Not:****VSPerfASPNETCmd,** web sitelerinin profilini oluşturmak için tek başına profil ASP.NET tercih edilen araçtır.   | -   [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Uygulama istatistikleri toplama:** Performans istatistikleri toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanım sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için yararlıdır. | -   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Ayrıntılı zamanlama verileri toplama:** Ayrıntılı zamanlama bilgilerini toplamak için ölçüm yöntemini kullanın. Ölçüm ölçüm verileri, IO sorunlarını analiz etmek ve uygulama senaryolarının daha ince analizlerini yapmak için kullanışlıdır. | -   [Ölçüm ölçümlerini kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **.NET bellek verilerini toplayın:** Size ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya araçları kullanın. Ayrıca, her çöp toplama neslinde geri alan nesnelerin boyutunu ve sayısını gösteren nesne yaşam süresi verilerini de toplayabilirsiniz. | -   [Bellek verilerini toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Eşzamanlılık verileri toplama:** Kaynak musiki verilerini toplamak için eşzamanlılık yöntemini kullanın. **Not:**  web uygulamaları için iş parçacığı etkinliği ve görselleştirme verilerini toplama desteklenmiyor. | -   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Katman etkileşim verileri ekleme:** Web uygulamasının bir Microsoft veritabanına zaman uyumlu [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] çağrılar hakkında [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] performans verileri [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] eklemesini sebilirsiniz. | -   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamaların profilini oluşturma**|-   [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profil hizmetleri**|-   [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)|
