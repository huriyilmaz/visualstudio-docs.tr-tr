---
title: Hizmet profili oluşturmayı Command-Line | Microsoft Docs
description: Windows Hizmetleri için performans verilerini toplamak üzere komut satırından Profil Oluşturma Araçları nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f05ca0a11060e2a9009b38b0caf7ce9172773f36
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533660"
---
# <a name="command-line-profiling-of-services"></a>Komut satırından hizmetler profili oluşturma
Bu bölümde, komut satırından Profil Oluşturma Araçları kullanarak Windows Hizmetleri için performans verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Uygulama Istatistiklerini topla:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanımı sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için kullanışlıdır. | -   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için izleme yöntemini kullanın. İzleme verileri, GÇ sorunlarını analiz etmek ve uygulama senaryolarına ilişkin ayrıntılı analizler için yararlıdır. | -   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **.Net bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya izleme kullanın. Ayrıca, her çöp toplama oluşturmada geri kazanılan nesne boyutunu ve sayısını gösteren nesne yaşam süresi verilerini toplayabilirsiniz. | -   [.NET bellek verileri toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Eşzamanlılık verilerini topla:** CPU kullanımını, iş parçacığı çekişmesini, iş parçacığı geçişini, eşitleme gecikmelerini, çakışan GÇ ve diğer sistem olaylarını gösteren kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın. | -   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Katman etkileşim verileri ekleme:** Hizmetin bir Microsoft veritabanına yaptığı zaman uyumlu ADO.NET çağrıları hakkında performans verileri ekleyebilirsiniz [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] . | -   [Katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Tek başına (istemci) uygulamalar profili**|-   [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profil ASP.NET uygulamaları**|-   [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
