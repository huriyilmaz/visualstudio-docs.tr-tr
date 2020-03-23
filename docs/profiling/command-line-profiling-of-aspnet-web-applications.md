---
title: ASP.NET Web Uygulamalarının Komut Satırı Profilleme | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779577"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>ASP.NET web uygulamalarının komut satırı profilleme
Bu bölümde, komut satırından Profil Oluşturma [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Araçları kullanarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Web uygulamaları için performans verileri toplamak için yordamlar ve seçenekler açıklanmaktadır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Bkz. Windows 8 ve Windows Server 2012 uygulamalarında Performans araçları.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Temel ASP.NET profil oluşturma verilerini kolayca toplayın:** VsPerfCmd için gerekli olan internet bilgi hizmetleri (IIS) yapılandırma gereksinimleri ve Internet Bilgi Hizmetleri (IIS) yeniden başlatmaları olmadan örnekleme, enstrümantasyon, .NET bellek, çekişme veya katman etkileşim verilerini toplamak için **VSPerfASPNETCmd** aracını kullanın. **VSPerfCmd** **VSPerfASPNETCmd** ek veri toplamanıza veya veri toplamayı denetlemenize izin vermez. **Not:**  **VSPerfASPNETCmd,** Web sitelerinin profilini ASP.NET tek başına profil oluşturabileceğiniz tercih edilen bir araçtır. | -   [VSPerfASPNETCmd ile hızlı web sitesi profiloluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Uygulama istatistiklerini toplayın:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanım sorunlarını çözümlemeve bir uygulamanın genel performans özelliklerini anlamak için yararlıdır. | -   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için enstrümantasyon yöntemini kullanın. Enstrümantasyon verileri, IO sorunlarını analiz etmek ve uygulama senaryolarının ince taneli analizi için yararlıdır. | -   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **.NET bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya enstrümantasyon kullanın. Ayrıca, her çöp toplama oluşturma da geri alınan nesnelerin boyutunu ve sayısını gösteren nesne yaşam boyu verileri de toplayabilirsiniz. | -   [Bellek verilerini toplama](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Eşzamanlılık verilerini toplayın:** Kaynak çekişme verileri toplamak için eşzamanlılık yöntemini kullanın. **Not:**  Web uygulamaları için iş parçacığı etkinliği ve görselleştirme verilerinin toplanması desteklenmez. | -   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Katman etkileşim verileri ekleyin:** Web uygulamasının [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] veritabanına [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] yaptığı eşzamanlı aramalarla ilgili performans verileri ekleyebilirsiniz. | -   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil tek başına (istemci) uygulamaları**|-   [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profil hizmetleri**|-   [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)|
