---
title: Performans Oturumuna Genel Bakış | Microsoft Docs
description: Hızlı bir şekilde üretken olmak ve kodunuzun performansını artırmak için Performans Araçları'nın nasıl kullanılacı olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b25024a71607690f4895027e3d3952741007f3cc8314ea879ad26c8f0dea756
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121246402"
---
# <a name="performance-session-overview"></a>Performans oturumuna genel bakış
Bu genel bakış, profil oluşturmanın temellerini açıklar. Performans çalışmalarına yeni yeni sahip olan geliştiriciler, bu Profil Oluşturma Araçları hızla üretken olmalarına ve kodlarının performansını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] artırmalarına nasıl yardımcı olduğunu görebilir. Profil oluşturmada deneyimli olan geliştiriciler, belirli yazılım özelliklerine ve işlemlerine Profil Oluşturma Araçları genel bakış elde ediyor olabilir.

 Bu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları kaynak kodundaki performans sorunlarını tanımlamanıza ve olası çözümlerin performansını karşılaştırmanıza yardımcı olur. Profil Oluşturma Araçları sihirbazları ve varsayılan ayarlar, birçok performans sorunuyla ilgili hemen içgörüler sağlar. Uygulamanın özellikleri ve seçenekleri Profil Oluşturma Araçları profil oluşturma işlemi üzerinde tam denetim sağlar. Bu denetim, kod bölümlerinin kesin hedefini, blok düzeyinde zamanlama bilgilerini toplamayı ve verilerinize ek işlemci ve sistem performansı verileri eklenmesini içerir.

 Aşağıdaki adımlar, aşağıdaki adımları kullanarak temel Profil Oluşturma Araçları:

1. Toplama yöntemini ve toplamak istediğiniz verileri belirterek performans oturumunu yapılandırma.

2. Uygulamayı performans oturumunda çalıştırarak profil oluşturma verilerini toplayın.

3. Performans sorunu tanımlamak için verileri analiz etme.

4. Kodun uygulama [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] performansını artıran tümleşik geliştirme ortamında (IDE) kodu değiştirme

5. Değiştirilen kodda profil oluşturma verilerini toplayın ve özgün ve değiştirilen verilerin profil oluşturma verilerini karşılaştırın.

6. Performans artışını belgeleen bir rapor oluşturma.

   Profil oluşturma tarafından sağlanan bilgilerle çalışmak için, profili oluşturmak istediğiniz ikili dosyalar ve profil oluşturma işletim sisteminin ikilileri için simge Windows sahipsiniz.

## <a name="configure-the-performance-session"></a>Performans oturumunu yapılandırma
 Profil oluşturma oturumu yapılandırmak için kullanmak istediğiniz profil oluşturma yöntemini ve toplamak istediğiniz verileri seçin. Performans Profil Oluşturma Araçları **Sihirbazı temel** yapılandırmada size yol gösterir ve daha fazla seçenek eklemek için Performans Oturumu özellik sayfalarını kullanabilirsiniz:

- Profil oluşturma yöntemleri örnekleme, izleme ve bellek ayırmayı içerir.

- Veri değerleri; zaman, işlemci ve işletim sistemi performans sayaçları ile sayfa hataları ve çekirdek geçişleri gibi uygulama olaylarını içerir.

  Proje çözümünün bir parçası olarak bir projede performans oturumu yapılandırabilirsiniz veya IDE aracılığıyla rastgele ikili [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dosyalar profili [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] atabilirsiniz. Performans Oturumu özellik sayfalarında oturum özelliklerini belirtebilir veya Profil Oluşturma Sihirbazı'nı kullanabilirsiniz.

## <a name="collect-profiling-data"></a>Profil oluşturma verilerini toplama
 Profil oluşturma verilerini koleksiyonuna **Performans Gezgini.** Toplayan veri miktarını sınırlamak için profil oluşturmayı duraklatabilir ve sürdürebilirsiniz. Zaten çalışan bir işleme de iliştirin.

 Uygulama başlar başlamaz **IDE'de** Veri Toplama Denetimi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] penceresi görünür. Veri **Toplama Denetimi penceresinden,** koleksiyon işlemini duraklatarak ve devamını kullanarak uygulamanın belirli bölümlerinin profilini oluşturabilirsiniz. Toplanan verilere işaretler **eklemek için** Veri Toplama Denetimi penceresini de kullanabilirsiniz. İşaretler profil görünümlerde görüntülenen ve profil oluşturma verilerini filtrelemek için kullanılan kullanıcı tanımlı veri noktalarıdır.

 Hedef uygulama kapanıyorsa, Profil Oluşturma Araçları profil oluşturma veri dosyası (*.vsp) oluşturulur ve IDE'de Özet Raporu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] görünümü görüntülenir.

## <a name="analyze-the-data-and-identify-performance-issues"></a>Verileri analiz etme ve performans sorunlarını belirleme
 Profil oluşturma çalıştırması sona ererse veriler analiz edilir ve Performans Raporu görünüm Profil Oluşturma Araçları **özet** görüntülenir. Profil oluşturma verileri, çağrı yığını ve hedef uygulamanın tek tek işlevleri için toplanır. Rapor görünümleri uygulamanın işlem, iş parçacığı, modül, işlev ve kaynak kod satırlarının veri aralıkları için performans analizini görüntüler. Bir işlev için veri değerlerinin profilini oluşturma aşağıdakileri içerir:

- İşlevde ve işlev tarafından çağrılan alt işlevlerde (kapsayıcı değerler) harcanan genel süre.

- Yalnızca işlevinde kodun yürütülmesi için harcanan süre (özel değerler).

  On ikiden fazla farklı görünüm, profil oluşturma verilerini en verimli şekilde analiz etmenize olanak sağlar. Özelleştirmeleri görüntüleme, performans sorunlarına neden olan işlevleri bulmak için verileri filtrelemenizi ve sıralamayı sağlar. Etkin Yol filtreleme, Çağrı Ağacı ve Modül görünümlerinde en etkin yolların hemen vurgulanır.

## <a name="modify-the-application-code"></a>Uygulama kodunu değiştirme
 Bir veya daha fazla ilgili performans sorunu yalıttıktan sonra, IDE kullanarak kodu değiştirebilir ve ardından değişiklikleriniz için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma verilerini toplayabilirsiniz.

## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Profil oluşturma verilerini yeniden toplayın ve verileri profil oluşturma çalıştırmaları arasında karşılaştırın
 Karşılaştırma Profil Oluşturma Araçları Görünümü, seçilen iki profil oluşturma veri dosyası arasındaki modül, işlev veya satır performansı farkını görüntüler. Karşılaştırmak istediğiniz profil oluşturma veri değerlerini belirtebilirsiniz ve Karşılaştırma Görünümü ile tek tek dosyaların görünümleri arasında geçişebilirsiniz.

## <a name="generate-a-report-of-the-results"></a>Sonuçların raporunu oluşturma
 Herhangi bir performans raporu görünümünün satırlarını e-postalara ve elektronik tablolara yapıştırabilirsiniz ve bir veya daha fazla görünüm için verileri içeren raporlar oluşturabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- ['a Genel Bakış](../profiling/overviews-performance-tools.md)
- [İzlenecek yol: Performans sorunlarını tanımlama](beginners-guide-to-cpu-sampling.md)
