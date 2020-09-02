---
title: Performans oturumlarını yapılandırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- common tasks, performance
- common tasks, profiling tools
- profiling tools, common tasks
- performance, gathering data
ms.assetid: e1c3ba41-ffca-4edf-9a7f-8a5a9244ef9b
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d67801cedded1ccf66544e21257866feda828e31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64779680"
---
# <a name="configuring-performance-sessions"></a>Performans Oturumlarını Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil Oluşturma Araçları kullanarak [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çok sayıda uygulama türü için çok çeşitli performans verileri toplayabilirsiniz. Bu bölümde, sizi ilgilendiren verileri toplamak üzere Profil Oluşturma Araçları yapılandırmak için performans oturumu ve hedef ikilisinin performans Sihirbazı ve özelliklerinin nasıl kullanılacağı gösterilmektedir. Profil Oluşturma Araçları yapılandırma özellikleri, profil oluşturma çalıştırmasında ne kadar veri toplandığını denetlemek için de kullanılabilir. Daha fazla bilgi için bkz. [veri toplamayı denetleme](../profiling/controlling-data-collection.md).  
  
> [!NOTE]
> Çoğu durumda, performans sihirbazının varsayılan özelliklerinin kullanılması profil oluşturma verilerinin toplanması için etkili bir yoldur. Daha fazla bilgi için bkz. performans profili oluşturma ve [kullanmaya](../profiling/getting-started-with-performance-tools.md)başlama [Için yeni başlayanlar kılavuzu](../profiling/beginners-guide-to-performance-profiling.md) .  
  
## <a name="common-tasks"></a>Ortak Görevler  
  
|Görev|İlgili İçerik|  
|----------|---------------------|  
|**Temel profil oluşturma seçeneklerini ayarlayın:** ' İ [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Microsoft sembol sunucusunu kullanacak şekilde yapılandırmanız gerekir. Bu, Windows 'un geçerli sürümü ve diğer Microsoft uygulamaları için işlev ve parametre adları gibi simgelere erişiminizin olduğundan emin olmanızı sağlar. Profil oluşturma araçlarının sistem izinleri ve profil oluşturma veri dosyalarının adları gibi, profil oluşturma oturumu başlamadan önce diğer genel seçenekleri de belirtebilirsiniz.|-   [Nasıl yapılır: Windows sembol bilgilerine başvuru](../profiling/how-to-reference-windows-symbol-information.md)<br />-   [Nasıl yapılır: sembol bilgilerini serileştirme](../profiling/how-to-serialize-symbol-information.md)<br />-   [Nasıl yapılır: geçerli oturumu ayarlama](../profiling/how-to-set-the-current-session.md)<br />-   [Nasıl yapılır: Izinleri ayarlama](../profiling/how-to-set-permissions.md)<br />-   [Nasıl yapılır: performans veri dosyası adı seçeneklerini ayarlama](../profiling/how-to-set-performance-data-file-name-options.md)|  
|**Toplamak istediğiniz verileri belirtin:** Profil oluşturma oturumu yapılandırmak için kullandığınız yordamlar, profil oluşturmak istediğiniz hedef uygulamanın türüne ve toplamak istediğiniz performans verilerinin türüne bağlıdır.|-   [Nasıl yapılır: koleksiyon yöntemleri seçme](../profiling/how-to-choose-collection-methods.md)<br />-   [Örnekleme kullanarak performans Istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)<br />-   [.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Izleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)<br />-   [Nasıl yapılır: Web sayfalarında JavaScript kodu profili oluşturma](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Iş parçacığını toplama ve eşzamanlılık verilerini Işleme](../profiling/collecting-thread-and-process-concurrency-data.md)<br />-   [Ek performans verileri toplama](../profiling/collecting-additional-performance-data.md)|  
|**Gelişmiş yapılandırma seçeneklerini ayarla:** Ortak dil çalışma zamanı 'nın (CLR) birden çok sürümünü yükleyen .NET Framework uygulamalar profilini oluşturduğunuzda, hangi sürümün profilini istediğinizi belirtebilirsiniz. Bir performans oturumunda birden fazla. exe dosyası varsa, ikili dosyaların başlangıç sırasını ayarlayabilirsiniz.|-   [Nasıl yapılır: .NET Framework çalışma zamanını belirtme](../profiling/how-to-specify-the-dotnet-framework-runtime.md)<br />-   [Nasıl yapılır: başlatılacak Ikiliyi belirtme](../profiling/how-to-specify-the-binary-to-start.md)|  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Veri Toplama Denetimi](../profiling/controlling-data-collection.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Performans Gezgini](../profiling/performance-explorer.md)
