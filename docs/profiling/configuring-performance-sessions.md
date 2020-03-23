---
title: Performans Oturumlarını Yapılandırma | Microsoft Dokümanlar
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
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bdf1c372ffcb3ad3a0ebf102827565853947e2b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777874"
---
# <a name="configure-performance-sessions"></a>Performans oturumlarını yapılandırma
Profil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Oluşturma Araçları'nı kullanarak, çok sayıda uygulama türü için çok çeşitli performans verileri toplayabilirsiniz. Bu bölümde, ilginizi çeken verileri toplamak için Profil Oluşturma Araçlarını yapılandırmak için Performans Sihirbazı ve performans oturumunun özelliklerini ve hedef ikiliyi nasıl kullanacağınızı gösterir. Profil Oluşturma Araçları yapılandırma özellikleri, bir profil oluşturma çalışmasında ne kadar veri toplandığını denetlemek için de kullanılabilir. Daha fazla bilgi için [bkz.](../profiling/controlling-data-collection.md)

> [!NOTE]
> Çoğu durumda, Performans Sihirbazı'nın varsayılan özelliklerini kullanmak, profil oluşturma verilerini toplamanın etkili bir yoludur. Daha fazla bilgi için, performans profilleme ve [başlarken](../profiling/getting-started-with-performance-tools.md) [Yeni Başlayanlar kılavuzuna](../profiling/beginners-guide-to-performance-profiling.md) bakın.

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Temel profil oluşturma seçeneklerini ayarlayın:** Microsoft sembol [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] sunucusunu kullanacak şekilde yapılandırmanız gerekir. Bu, Windows'un ve diğer Microsoft uygulamalarının geçerli sürümü için işlev ve parametre adları gibi simgelere erişmenizi sağlayacaktır. Profil oluşturma oturumu başlamadan önce profil oluşturma araçlarına sistem izinleri ve profil oluşturma veri dosyalarının adları gibi diğer genel seçenekleri de belirtebilirsiniz. | -   [Nasıl kullanılır: Başvuru Windows simge bilgileri](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Nasıl kullanılır: Sembol bilgilerini serihale](../profiling/how-to-serialize-symbol-information.md)<br />-   [Nasıl yapılır: Geçerli oturumu ayarlama](../profiling/how-to-set-the-current-session.md)<br />-   [Nasıl yapılsın: İzinleri ayarlama](../profiling/how-to-set-permissions.md)<br />-   [Nasıl kullanılır: Performans verisi dosya adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Toplamak istediğiniz verileri belirtin:** Profil oluşturma oturumunu yapılandırmak için kullandığınız yordamlar, profilini çıkarmak istediğiniz hedef uygulamatürüne ve toplamak istediğiniz performans verisinin türüne bağlıdır. | -   [Nasıl yapılır: Toplama yöntemlerini seçin](../profiling/how-to-choose-collection-methods.md)<br />-   [Örnekleme yi kullanarak performans istatistiklerini toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [.NET bellek ayırma ve yaşam boyu verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Enstrümantasyon kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Nasıl kullanılır: Web sayfalarında Profil JavaScript kodu](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [İş parçacığı toplama ve eşzamanlılık verilerini işleme](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Ek performans verileri toplama](../profiling/collecting-additional-performance-data.md) |
| **Gelişmiş yapılandırma seçeneklerini ayarlayın:** Ortak dil çalışma zamanının (CLR) birden çok sürümünü yükleyen .NET Framework uygulamalarının profilini attığınızda, hangi sürümün profilini niçin oluşturacağımı belirtebilirsiniz. Bir performans oturumunda birden çok .exe dosyanız varsa, ikili dosyaların başlangıç sırasını ayarlayabilirsiniz. | -   [Nasıl yapılsın: .NET Framework çalışma süresini belirtin](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Nasıl yapılır: Başlamak için ikiliyi belirtin](../profiling/how-to-specify-the-binary-to-start.md) |

## <a name="related-sections"></a>İlgili bölümler
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
