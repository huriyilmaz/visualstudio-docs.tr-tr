---
title: Stand-Alone uygulamalarının profilini oluşturma Command-Line | Microsoft Docs
description: İstemci (tek başına) uygulamalarına ilişkin performans verilerini toplamak için komut satırından Profil Oluşturma Araçları nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3d5494c5b1faa4a1dc1e4cc572158fcc719e3a15
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093326"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Komut satırından tek başına uygulamaların profilini oluşturma
Bu bölümde, komut satırından Profil Oluşturma Araçları kullanarak tek başına (istemci) uygulamalar için performans verilerini toplamaya yönelik yordamlar ve seçenekler açıklanmaktadır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili içerik |
| - | - |
| **Uygulama Istatistiklerini topla:** Performans istatistiklerini toplamak için örnekleme yöntemini kullanın. Örnekleme verileri, CPU kullanımı sorunlarını analiz etmek ve bir uygulamanın genel performans özelliklerini anlamak için kullanışlıdır. | -   [Örnekleme kullanarak uygulama istatistikleri toplama](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Ayrıntılı zamanlama verileri toplayın:** Ayrıntılı zamanlama bilgilerini toplamak için izleme yöntemini kullanın. İzleme verileri, g/ç sorunlarını analiz etmek ve uygulama senaryolarına ilişkin ayrıntılı analizler için yararlıdır. | -   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **.Net bellek verilerini toplayın:** Ayrılan nesnelerin boyutunu ve sayısını gösteren .NET bellek ayırma verilerini toplamak için örnekleme veya izleme kullanın. Ayrıca, her çöp toplama oluşturmada geri kazanılan nesne boyutunu ve sayısını gösteren nesne yaşam süresi verilerini toplayabilirsiniz. | -   [.NET Framework bellek verileri toplama](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Eşzamanlılık verilerini topla:** CPU kullanımı, iş parçacığı çakışması, iş parçacığı geçişi, eşitleme gecikmeleri, çakışan g/ç ve diğer sistem olayları gibi kaynak çekişmesi verilerini ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanın. | -   [Eşzamanlılık verileri toplama](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Katman etkileşim verileri ekleyin:** uygulamanın bir Microsoft veritabanına yaptığı zaman uyumlu ADO.NET çağrıları hakkında performans verileri ekleyebilirsiniz [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] . Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. | -   [Katman etkileşim verileri toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>İlişkili görevler

|Görev|İlgili İçerik|
|----------|---------------------|
|**ASP.NET uygulamalar profili**|-   [web uygulamalarının profilini ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Profil hizmetleri**|-   [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)|
