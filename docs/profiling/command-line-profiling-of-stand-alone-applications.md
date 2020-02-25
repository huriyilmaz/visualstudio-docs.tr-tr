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
ms.openlocfilehash: 3f80f3e65969973202af08299b07ebfa420f3bd2
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557861"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Komut satırından tek başına uygulamaların profilini oluşturma
Bu bölümde, komut satırından [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları kullanarak tek başına (istemci) uygulamalar için performans verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır.

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili içerik |
| - | - |
| **Uygulama Istatistiklerini topla:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanımı sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için kullanışlıdır. | [örnekleme kullanarak uygulama Istatistiklerini toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md) -    |
| **Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için izleme yöntemini kullanın. İzleme verileri, g/ç sorunlarını analiz etmek ve uygulama senaryolarına ilişkin ayrıntılı analizler için yararlıdır. | [izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) -    |
| **.Net bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya izleme kullanın. Ayrıca, her çöp toplama oluşturmada geri kazanılan nesne boyutunu ve sayısını gösteren nesne yaşam süresi verilerini toplayabilirsiniz. | [.NET Framework bellek verileri toplama](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) -    |
| **Eşzamanlılık verilerini topla:** CPU kullanımı, iş parçacığı çakışması, iş parçacığı geçişi, eşitleme gecikmeleri, çakışan g/ç ve diğer sistem olayları gibi kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın. | -   [eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Katman etkileşim verileri ekleyin:** Uygulamanın bir Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] veritabanına yaptığı zaman uyumlu ADO.NET çağrıları hakkında performans verileri ekleyebilirsiniz. Bir profil oluşturma yürütmesine katman etkileşim verileri ekleme, komut satırı profil araçlarıyla özel yordamlar gerektirir. | [katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) -    |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**Profil ASP.NET uygulamaları**|-   [profili ASP.NET Web uygulamaları](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Profil hizmetleri**|-   [profili Hizmetleri](../profiling/command-line-profiling-of-services.md)|
