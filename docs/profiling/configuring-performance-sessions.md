---
title: Performans oturumlarını yapılandırma | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777874"
---
# <a name="configure-performance-sessions"></a>Performans oturumlarını yapılandırma
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları kullanarak çok sayıda uygulama türü için çok çeşitli performans verileri toplayabilirsiniz. Bu bölümde, sizi ilgilendiren verileri toplamak üzere Profil Oluşturma Araçları yapılandırmak için performans oturumu ve hedef ikilisinin performans Sihirbazı ve özelliklerinin nasıl kullanılacağı gösterilmektedir. Profil Oluşturma Araçları yapılandırma özellikleri, profil oluşturma çalıştırmasında ne kadar veri toplandığını denetlemek için de kullanılabilir. Daha fazla bilgi için bkz. [Denetim verileri toplama](../profiling/controlling-data-collection.md).

> [!NOTE]
> Çoğu durumda, performans sihirbazının varsayılan özelliklerinin kullanılması profil oluşturma verilerinin toplanması için etkili bir yoldur. Daha fazla bilgi için bkz. performans profili oluşturma ve [kullanmaya](../profiling/getting-started-with-performance-tools.md)başlama [için yeni başlayanlar kılavuzu](../profiling/beginners-guide-to-performance-profiling.md) .

## <a name="common-tasks"></a>Ortak görevler

| Görev | İlgili Içerik |
| - | - |
| **Temel profil oluşturma seçeneklerini ayarlayın:** [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], Microsoft sembol sunucusunu kullanacak şekilde yapılandırmanız gerekir. Bu, Windows 'un geçerli sürümü ve diğer Microsoft uygulamaları için işlev ve parametre adları gibi simgelere erişiminizin olduğundan emin olmanızı sağlar. Profil oluşturma araçlarının sistem izinleri ve profil oluşturma veri dosyalarının adları gibi, profil oluşturma oturumu başlamadan önce diğer genel seçenekleri de belirtebilirsiniz. | -   [nasıl yapılır: Windows sembol bilgilerine başvuru](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [nasıl yapılır: sembol bilgilerini seri hale getirme](../profiling/how-to-serialize-symbol-information.md)<br />-   [nasıl yapılır: geçerli oturumu ayarlama](../profiling/how-to-set-the-current-session.md)<br />-   [nasıl yapılır: Izinleri ayarlama](../profiling/how-to-set-permissions.md)<br />-   [nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Toplamak istediğiniz verileri belirtin:** Profil oluşturma oturumu yapılandırmak için kullandığınız yordamlar, profil oluşturmak istediğiniz hedef uygulamanın türüne ve toplamak istediğiniz performans verilerinin türüne bağlıdır. | -   [nasıl yapılır: koleksiyon Yöntemleri Seçme](../profiling/how-to-choose-collection-methods.md)<br />[örnekleme kullanarak performans Istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md) -   <br />[.net bellek ayırma ve ömür verileri toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) -   <br />[izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md) -   <br />-   [nasıl yapılır: Web sayfalarında JavaScript kodunun profilini](../profiling/how-to-profile-javascript-code-in-web-pages.md) oluşturma<br />[iş parçacığı toplama ve eşzamanlılık verilerini işleme](../profiling/collecting-thread-and-process-concurrency-data.md) -   <br />[ek performans verileri toplama](../profiling/collecting-additional-performance-data.md) -    |
| **Gelişmiş yapılandırma seçeneklerini ayarla:** Ortak dil çalışma zamanı 'nın (CLR) birden çok sürümünü yükleyen .NET Framework uygulamalar profilini oluşturduğunuzda, hangi sürümün profilini istediğinizi belirtebilirsiniz. Bir performans oturumunda birden fazla. exe dosyası varsa, ikili dosyaların başlangıç sırasını ayarlayabilirsiniz. | -   [nasıl yapılır: .NET Framework çalışma zamanını belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [nasıl yapılır: başlatılacak Ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md) |

## <a name="related-sections"></a>İlgili bölümler
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
