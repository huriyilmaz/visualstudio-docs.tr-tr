---
title: Hizmetlerin Komuta Hattı Profilleme | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772837"
---
# <a name="command-line-profiling-of-services"></a>Komut satırından hizmetler profili oluşturma
Bu bölümde, komut satırından Profil Oluşturma Araçları kullanarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Windows hizmetleri için performans verileri toplama yordamları ve seçenekleri açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Bkz. Windows 8 ve Windows Server 2012 uygulamalarında Performans araçları.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Uygulama istatistiklerini toplayın:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanım sorunlarını çözümlemeve bir uygulamanın genel performans özelliklerini anlamak için yararlıdır. | -   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md) |
| **Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için enstrümantasyon yöntemini kullanın. Enstrümantasyon verileri, IO sorunlarını analiz etmek ve uygulama senaryolarının ince taneli analizi için yararlıdır. | -   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md) |
| **.NET bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya enstrümantasyon kullanın. Ayrıca, her çöp toplama oluşturma da geri alınan nesnelerin boyutunu ve sayısını gösteren nesne yaşam boyu verileri de toplayabilirsiniz. | -   [.NET bellek verilerini toplama](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md) |
| **Eşzamanlılık verilerini toplayın:** CPU kullanımı, iş parçacığı çekişmesi, iş parçacığı geçişi, eşitleme gecikmeleri, çakışan IO alanları ve diğer sistem olayları gösteren kaynak çekişme verileri ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın. | -   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md) |
| **Katman etkileşim verileri ekleyin:** Hizmetin Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] veritabanına yaptığı senkron ADO.NET aramalarla ilgili performans verileri ekleyebilirsiniz. | -   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil tek başına (istemci) uygulamaları**|-   [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profil ASP.NET uygulamaları**|-   [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
