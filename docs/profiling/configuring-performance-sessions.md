---
title: Performans oturumlarını yapılandırma | Microsoft Docs
description: Visual Studio Profil Oluşturma Araçları istediğiniz performans verilerini toplamak üzere nasıl yapılandıracağınızı öğrenin. Bu makalede ortak görevler listelenmekte ve bağlantılar sağlanmaktadır.
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
ms.openlocfilehash: 25144a4fe7e4664eb5b1172cf14e5103ef291881
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039559"
---
# <a name="configure-performance-sessions"></a>Performans oturumlarını yapılandırma
Profil Oluşturma Araçları kullanarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çok sayıda uygulama türü için çok çeşitli performans verileri toplayabilirsiniz. Bu bölümde, sizi ilgilendiren verileri toplamak üzere Profil Oluşturma Araçları yapılandırmak için performans oturumu ve hedef ikilisinin performans Sihirbazı ve özelliklerinin nasıl kullanılacağı gösterilmektedir. Profil Oluşturma Araçları yapılandırma özellikleri, profil oluşturma çalıştırmasında ne kadar veri toplandığını denetlemek için de kullanılabilir. Daha fazla bilgi için bkz. [Denetim verileri toplama](../profiling/controlling-data-collection.md).

> [!NOTE]
> Çoğu durumda, performans sihirbazının varsayılan özelliklerinin kullanılması profil oluşturma verilerinin toplanması için etkili bir yoldur. Daha fazla bilgi için bkz. performans profili oluşturma ve [kullanmaya](../profiling/getting-started-with-performance-tools.md)başlama [için yeni başlayanlar kılavuzu](../profiling/beginners-guide-to-performance-profiling.md) .

## <a name="common-tasks"></a>Genel görevler

| Görev | İlgili İçerik |
| - | - |
| **Temel profil oluşturma seçeneklerini ayarlayın:** ' İ [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Microsoft sembol sunucusunu kullanacak şekilde yapılandırmanız gerekir. bu, geçerli Windows sürümü ve diğer Microsoft uygulamaları için işlev ve parametre adları gibi simgelere erişiminizin olduğundan emin olmanızı sağlar. Profil oluşturma araçlarının sistem izinleri ve profil oluşturma veri dosyalarının adları gibi, profil oluşturma oturumu başlamadan önce diğer genel seçenekleri de belirtebilirsiniz. | -   [nasıl yapılır: Windows sembol bilgilerine başvuru](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Nasıl yapılır: sembol bilgilerini serileştirme](../profiling/how-to-serialize-symbol-information.md)<br />-   [Nasıl yapılır: geçerli oturumu ayarlama](../profiling/how-to-set-the-current-session.md)<br />-   [Nasıl yapılır: izinleri ayarlama](../profiling/how-to-set-permissions.md)<br />-   [Nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md) |
| **Toplamak istediğiniz verileri belirtin:** Profil oluşturma oturumu yapılandırmak için kullandığınız yordamlar, profil oluşturmak istediğiniz hedef uygulamanın türüne ve toplamak istediğiniz performans verilerinin türüne bağlıdır. | -   [Nasıl yapılır: koleksiyon yöntemleri seçme](../profiling/how-to-choose-collection-methods.md)<br />-   [Örnekleme kullanarak performans istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [.NET bellek ayırma ve yaşam süresi verilerini toplayın](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Nasıl yapılır: Web sayfalarında JavaScript kodu profili oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [İş parçacığı toplama ve eşzamanlılık verilerini işleme](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Ek performans verileri toplama](../profiling/collecting-additional-performance-data.md) |
| **Gelişmiş yapılandırma seçeneklerini ayarla:** ortak dil çalışma zamanı 'nın (CLR) birden çok sürümünü yükleyen .NET Framework uygulamalar profilini oluşturduğunuzda, hangi sürümün profilini istediğinizi belirtebilirsiniz. Bir performans oturumunda birden çok .exe dosyası varsa, ikili dosyaların başlangıç sırasını ayarlayabilirsiniz. | -   [nasıl yapılır: .NET Framework çalışma zamanını belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Nasıl yapılır: başlatılacak ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md) |

## <a name="related-sections"></a>İlgili bölümler
- [Veri toplamayı denetleme](../profiling/controlling-data-collection.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Performans Gezgini](../profiling/performance-explorer.md)
