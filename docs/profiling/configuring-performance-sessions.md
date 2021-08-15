---
title: Performans Oturumlarını Yapılandırma | Microsoft Docs
description: Verileri istediğiniz performans Visual Studio Profil Oluşturma Araçları için yapılandırmayı öğrenin. Bu makalede, ortak görevler liste ve bağlantılar sağlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 80b6e2f0e4ca08b78fe57d204e64b981183f8649a294bf38d5c7aa6c67e404d9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333580"
---
# <a name="configure-performance-sessions"></a>Performans oturumlarını yapılandırma
Bu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları kullanarak çok sayıda uygulama türü için çok çeşitli performans verileri toplayabilirsiniz. Bu bölümde performans sihirbazını ve performans oturumunun özelliklerini ve hedef ikiliyi kullanarak ilginiz Profil Oluşturma Araçları verileri nasıl yapılandırabilirsiniz? Profil Oluşturma Araçları yapılandırma özellikleri, profil oluşturma çalıştırması içinde ne kadar veri toplanacaklarını kontrol etmek için de kullanılabilir. Daha fazla bilgi için [bkz. Veri toplamayı denetleme.](../profiling/controlling-data-collection.md)

> [!NOTE]
> Çoğu durumda, Performans Sihirbazı'nın varsayılan özelliklerini kullanmak profil oluşturma verilerini toplamanın etkili bir yolu olur. Daha fazla bilgi için [bkz. Performans profili oluşturma ve Başlangıç](../profiling/beginners-guide-to-performance-profiling.md) kılavuzu. [](../profiling/getting-started-with-performance-tools.md)

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Temel profil oluşturma seçeneklerini ayarlayın:** 'yi [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Microsoft sembol sunucusunu kullanmak üzere yapılandırmalısınız. Bu, uygulamanın ve diğer Microsoft uygulamalarının geçerli sürümü için işlev ve parametre adları gibi sembollere Windows emin olur. Profil oluşturma oturumu başlamadan önce profil oluşturma araçlarına sistem izinleri ve profil oluşturma veri dosyalarının adları gibi diğer genel seçenekleri de belirtebilirsiniz. | -   [Nasıl Windows: Windows bilgilerine başvuru](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Nasıl gösterilir: Sembol bilgilerini seri hale getirme](../profiling/how-to-serialize-symbol-information.md)<br />-   [Nasıl ayarlanır: Geçerli oturumu ayarlama](../profiling/how-to-set-the-current-session.md)<br />-   [Nasıl ayarlanır: İzinleri ayarlama](../profiling/how-to-set-permissions.md)<br />-   [Nasıl kullanılır: Performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Toplamak istediğiniz verileri belirtin:** Profil oluşturma oturumunu yapılandırmak için kullandığınız yordamlar, profili oluşturmak istediğiniz hedef uygulamanın türüne ve toplamak istediğiniz performans verisi türüne bağlıdır. | -   [Nasıl yapılacaklar: Koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md)<br />-   [Örnekleme kullanarak performans istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Ölçüm ölçümlerini kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Nasıl kullanılır: Web sayfalarında JavaScript kodunun profilini oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [İş parçacığı ve işlem eşzamanlılık verileri toplama](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Ek performans verileri toplama](../profiling/collecting-additional-performance-data.md) |
| **Gelişmiş yapılandırma seçeneklerini ayarlayın:** Ortak dil çalışma .NET Framework (CLR) birden çok sürümünü yüken bir uygulamanın profilini sınarsanız, profilin hangi sürümde olduğunu belirtebilirsiniz. Bir performans oturumunda .exe dosya varsa, ikili dosyaların başlangıç sırasına göre ayarlayın. | -   [Nasıl kullanılır: Çalışma .NET Framework belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Nasıllı: Başlamak için ikili dosya belirtme](../profiling/how-to-specify-the-binary-to-start.md) |

## <a name="related-sections"></a>İlgili bölümler
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
