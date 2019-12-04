---
title: Tek başına uygulamaların komut satırı profili oluşturma | Microsoft Docs
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
ms.openlocfilehash: c5fd11f12f368c266dd19577925db7cec1867e39
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779564"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Komut satırından tek başına uygulamaların profilini oluşturma
Bu bölümde, komut satırından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları kullanarak tek başına (istemci) uygulamalar için performans verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

## <a name="common-tasks"></a>Ortak görevler

| Görev | İlgili içerik |
| - | - |
| **Uygulama Istatistiklerini topla:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanımı sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için kullanışlıdır. | [örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md) -    |
| **Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için izleme yöntemini kullanın. İzleme verileri, g/ç sorunlarını analiz etmek ve uygulama senaryolarına ilişkin ayrıntılı analizler için yararlıdır. | [izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) -    |
| **.Net bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya izleme kullanın. Ayrıca, her çöp toplama oluşturmada geri kazanılan nesne boyutunu ve sayısını gösteren nesne yaşam süresi verilerini toplayabilirsiniz. | [.NET Framework bellek verileri toplama](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) -    |
| **Eşzamanlılık verilerini topla:** CPU kullanımı, iş parçacığı çakışması, iş parçacığı geçişi, eşitleme gecikmeleri, çakışan g/ç ve diğer sistem olayları gibi kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın. | -   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Katman etkileşim verileri ekleyin:** Uygulamanın bir Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] veritabanına yaptığı zaman uyumlu ADO.NET çağrıları hakkında performans verileri ekleyebilirsiniz. Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. | [katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) -    |
| **Deneyin:** Örnekleme veya izleme yöntemini kullanarak örnek bir istemci uygulaması profili eklemek için adım adım yordamları kullanın. | -   [Izlenecek yol: örnekleme kullanarak komut satırı profili oluşturma](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Izlenecek yol: izleme kullanarak komut satırı profili oluşturma](command-line-profiling-of-stand-alone-applications.md) |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili Içerik|
|----------|---------------------|
|**Profil ASP.NET uygulamaları**|-   [profili ASP.NET Web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Profil hizmetleri**|-   [profili Hizmetleri](../profiling/command-line-profiling-of-services.md)|
