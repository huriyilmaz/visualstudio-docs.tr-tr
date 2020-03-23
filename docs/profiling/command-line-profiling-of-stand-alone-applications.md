---
title: Tek Başına Uygulamaların Komuta Hattı Profilleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3f80f3e65969973202af08299b07ebfa420f3bd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77557861"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Komut satırından tek başına uygulamaların profilini oluşturma
Bu bölümde, komut satırından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları'nı kullanarak tek başına (istemci) uygulamalar için performans verileri toplama yordamları ve seçenekleri açıklanmaktadır.

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili içerik |
| - | - |
| **Uygulama istatistiklerini toplayın:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanım sorunlarını çözümlemeve bir uygulamanın genel performans özelliklerini anlamak için yararlıdır. | -   [Örneklemeyi kullanarak uygulama istatistiklerini toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için enstrümantasyon yöntemini kullanın. Enstrümantasyon verileri, G/Ç sorunlarını çözümlemeve uygulama senaryolarının ince taneli analizi için yararlıdır. | -   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **.NET bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya enstrümantasyon kullanın. Ayrıca, her çöp toplama oluşturma da geri alınan nesnelerin boyutunu ve sayısını gösteren nesne yaşam boyu verileri de toplayabilirsiniz. | -   [.NET Framework bellek verilerini topla](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Eşzamanlılık verilerini toplayın:** CPU kullanımı, iş parçacığı çekişmesi, iş parçacığı geçişi, eşitleme gecikmeleri, çakışan G/Ç alanları ve diğer sistem olayları gösteren kaynak çekişme verileri ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın. | -   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Katman etkileşimi verileri ekleyin:** Uygulamanın Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] veritabanına yaptığı senkron ADO.NET çağrıları hakkında performans verileri ekleyebilirsiniz. Profil oluşturma çalışmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. | -   [Katman etkileşim verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil ASP.NET uygulamaları**|-   [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Profil hizmetleri**|-   [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)|
