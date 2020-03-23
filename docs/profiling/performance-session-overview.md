---
title: Performans Oturumuna Genel Bakış | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e7b23a7cbefeace19a3deaa5c1bfc05580081d39
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778472"
---
# <a name="performance-session-overview"></a>Performans oturumuna genel bakış
Bu genel bakış, profil oluşturmanın temellerini açıklar. Performans çalışmalarında yeni olan geliştiriciler, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları'nın hızlı bir şekilde üretken olmalarına ve kodlarının performansını artırmalarına nasıl yardımcı olabileceğini görür. Profil oluşturma konusunda deneyimli olan geliştiriciler, belirli Profil Oluşturma Araçları özellikleri ve süreçlerine genel bir bakış elde edebilir.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları, kaynak kodundaki performans sorunlarını belirlemenize ve olası çözümlerin performansını karşılaştırmanıza yardımcı olur. Profil Oluşturma Araçları sihirbazları ve varsayılan ayarlar, birçok performans sorunu hakkında anında bilgi edinebilirsiniz. Profil Oluşturma Araçları'nın özellikleri ve seçenekleri profil oluşturma işlemi üzerinde tam denetim sağlar. Bu denetim, kod bölümlerinin kesin hedeflemesini, blok düzeyinde zamanlama bilgilerinin toplanmasını ve verilerinize ek işlemci ve sistem performans verilerinin eklenmesini içerir.

 Aşağıdaki adımlar Profil Oluşturma Araçlarını kullanmanın temel işlemini oluşur:

1. Toplama yöntemini ve toplamak istediğiniz verileri belirterek performans oturumunu yapılandırın.

2. Uygulamayı performans oturumunda çalıştırarak profil oluşturma verileri toplayın.

3. Performans sorununu tanımlamak için verileri çözümleştirin.

4. Kodun [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uygulama performansını artırmak için tümleşik geliştirme ortamında (IDE) kodu değiştirme

5. Değiştirilen kodda profil oluşturma verileri toplayın ve özgün ve değiştirilen verilerin profil oluşturma verilerini karşılaştırın.

6. Performans artışını belgeleyen bir rapor oluşturun.

   Profil oluşturma tarafından sağlanan bilgilerle çalışmak için, profilini çıkarmak istediğiniz ikililer ve Windows işletim sisteminin ikilileri için kullanılabilir simge bilgilerine sahip olmalısınız.

## <a name="configure-the-performance-session"></a>Performans oturumunu yapılandırma
 Profil oluşturma oturumunu yapılandırmak için, kullanmak istediğiniz profil oluşturma yöntemini ve toplamak istediğiniz verileri seçin. Profil Oluşturma Araçları **Performans Sihirbazı** temel yapılandırmada size yol görebilir ve daha fazla seçenek eklemek için Performans Oturumu özelliği sayfalarını kullanabilirsiniz:

- Profil oluşturma yöntemleri örnekleme, izleme ve bellek ayırmayı içerir.

- Veri değerleri zaman, işlemci ve işletim sistemi performans sayaçları ve sayfa hataları ve çekirdek geçişleri gibi uygulama olayları içerir.

  Proje çözümünün bir parçası [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olarak projedeki performans oturumunu yapılandırabilir veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE aracılığıyla profil rasgele ikililer oluşturabilirsiniz. Performans Oturumu özellik sayfalarında oturum özelliklerini belirtebilir veya Profil Oluşturma Sihirbazı'nı kullanabilirsiniz.

## <a name="collect-profiling-data"></a>Profil oluşturma verilerini toplama
 **Performans Gezgini'nden**profil oluşturma verilerini toplamaya başlarsınız. Topladığınız veri miktarını sınırlamak için profil oluşturmayı duraklatabilir ve devam ettirebilirsiniz. Zaten çalışan bir işleme de ekleyebilirsiniz.

 Uygulama başlar başlamaz, **Veri Toplama Denetimi** penceresi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE'de görünür. Veri **Toplama Denetimi** penceresinden, toplama işlemini duraklatarak ve devam ettirerek uygulamanızın belirli bölümlerini profilleyebilirsiniz. Toplanan verilere işaret eklemek için **Veri Toplama Denetimi** penceresini de kullanabilirsiniz. İşaretler, profil görünümlerinde görüntülenen ve profil oluşturma verilerini filtrelemek için kullanılabilen kullanıcı tanımlı veri noktalarıdır.

 Hedef uygulama kapandığında, Profil Oluşturma Araçları bir profil oluşturma veri dosyası (*.vsp) oluşturur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve Özet Rapor görünümünü IDE'de görüntüler.

## <a name="analyze-the-data-and-identify-performance-issues"></a>Verileri analiz etme ve performans sorunlarını belirleme
 Profil oluşturma çalışmasını sonlandırdığınızda, veriler analiz edilir ve Profil Oluşturma Araçları **Performans Raporu** görünüm pencerelerinde bir özet görüntülenir. Profil oluşturma verileri, hedef uygulamanın çağrı yığını ve tek tek işlevleri için toplanır. Rapor görünümleri, uygulamanın süreçlerinin, iş parçacıklarının, modüllerin, işlevlerin ve kaynak kodu satırlarının veri aralıkları için performans çözümlemesi görüntüler. Bir işlev için veri değerlerini profil oluşturma aşağıdakileri içerir:

- İşlev ve işlev (kapsayıcı değerler) tarafından çağrılan alt işlevlerde harcanan toplam süre.

- Yalnızca işlevdeki kodu (özel değerler) yürütmek için harcanan süre.

  On ikiden fazla farklı görünüm, profil oluşturma verilerini en verimli şekilde çözümlemenize olanak tanır. Özelleştirmeleri görüntüleme, performans sorunlarına neden olabilecek işlevleri bulmak için verileri filtrelemenize ve sıralamanıza olanak tanır. Sıcak Yol filtreleme, Çağrı Ağacı ve Modül görünümlerinde en etkin yolların hemen vurgulanmasına neden olur.

## <a name="modify-the-application-code"></a>Uygulama kodunu değiştirme
 Bir veya daha fazla alakalı performans sorunlarını yalıtttınca, IDE'yi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanarak kodu değiştirebilir ve değişiklikleriniz için profil oluşturma verileri toplayabilirsiniz.

## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Profil oluşturma verilerini yeniden toplayın ve profil oluşturma çalıştırmaları arasındaki verileri karşılaştırın
 Profil Oluşturma Araçları Karşılaştırma Raporu Görünümü, seçili iki profil oluşturma veri dosyası arasındaki modül, işlev veya satır performansı arasındaki farkı görüntüler. Karşılaştırma Görünümü ile tek tek dosyaların görünümleri arasında geçiş yapmak istediğiniz profil oluşturma veri değerlerini belirtebilirsiniz.

## <a name="generate-a-report-of-the-results"></a>Sonuçların bir raporunu oluşturma
 Herhangi bir performans raporu görünümünün satırlarını e-postalara ve elektronik tablolara yapıştırabilir ve bir veya daha fazla görünüm için verileri içeren raporlar oluşturabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Genel bakış](../profiling/overviews-performance-tools.md)
- [İzlenecek yol: Performans sorunlarını tanımlama](beginners-guide-to-cpu-sampling.md)
