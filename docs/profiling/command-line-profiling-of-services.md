---
title: Command-Line Profil Oluşturma | Microsoft Docs
description: Hizmetlerde performans verilerini Profil Oluşturma Araçları için komut satırına gelen komut Windows öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling toos,services
- profiling services
ms.assetid: f0d62318-b0e8-49c6-9a30-9f7a6adef2f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0fd7f5c6e44f356b44b7416629a62ac552379654
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637241"
---
# <a name="command-line-profiling-of-services"></a>Komut satırından hizmetler profili oluşturma
Bu bölümde, komut satırına ilişkin verileri kullanarak Windows verileri toplamaya Profil Oluşturma Araçları [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yordamları ve seçenekleri açıklanır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Bkz. [Uygulama ve Windows 8 performans Windows Server 2012.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Uygulama istatistiklerini toplama:** Performans istatistikleri toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanım sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için yararlıdır. | -   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Ayrıntılı zamanlama verileri toplama:** Ayrıntılı zamanlama bilgilerini toplamak için ölçüm yöntemini kullanın. Ölçüm ölçüm verileri, IO sorunlarını analiz etmek ve uygulama senaryolarının daha ince analizlerini yapmak için kullanışlıdır. | -   [Ölçüm ölçümlerini kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **.NET bellek verilerini toplayın:** Size ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya araçları kullanın. Ayrıca, her çöp toplama neslinde geri alan nesnelerin boyutunu ve sayısını gösteren nesne yaşam süresi verilerini de toplayabilirsiniz. | -   [.NET bellek verilerini toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Eşzamanlılık verileri toplama:** Cpu kullanımı, iş parçacığı çakışması, iş parçacığı geçişi, eşitleme gecikmeleri, çakışan IO alanları ve diğer sistem olaylarını gösteren kaynak çakışma verilerini ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın. | -   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Katman etkileşim verileri ekleme:** Hizmetin bir Microsoft veritabanına yaptığı zaman uyumlu ADO.NET ilgili performans verilerini [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] ekebilirsiniz. | -   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamaların profilini oluşturma**|-   [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profil ASP.NET uygulamaları**|-   [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
