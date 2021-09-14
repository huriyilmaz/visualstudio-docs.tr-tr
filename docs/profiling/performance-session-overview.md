---
title: Performans oturumuna genel bakış | Microsoft Docs
description: Performans araçlarını kullanarak hızlı bir şekilde üretken olma ve zeni kodunun performansını artırma hakkında bilgi edinin.
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
ms.openlocfilehash: 877fff149234b091792035ade25cb18da7980fd1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726814"
---
# <a name="performance-session-overview"></a>Performans oturumuna genel bakış
Bu genel bakışta profil oluşturma temelleri açıklanmaktadır. Performans çalışmalarıyla yeni olan geliştiriciler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profil oluşturma araçları hızla üretken hale gelmesine ve kodun performansını artırmaya nasıl yardımcı olacağını görür. Profil oluşturma bölümünde deneyimli geliştiriciler, belirli Profil Oluşturma Araçları özelliklerine ve işlemlerine genel bir bakış elde edebilir.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Profil oluşturma araçları, kaynak kodundaki performans sorunlarını belirlemenize ve olası çözümlerin performansını karşılaştırmanıza yardımcı olur. Profil Oluşturma Araçları sihirbazları ve varsayılan ayarları birçok performans sorununa anında Öngörüler verebilir. Profil Oluşturma Araçları özellikleri ve seçenekleri, profil oluşturma işlemi üzerinde tam denetim sağlar. Bu denetim, kod bölümlerinin kesin hedeflemesini, blok düzeyinde zamanlama bilgilerini toplamayı ve verilerinize ek işlemci ve sistem performansı verilerinin eklenmesini içerir.

 Aşağıdaki adımlar Profil Oluşturma Araçları kullanmanın temel işlemini yapar:

1. Toplama yöntemini ve toplamak istediğiniz verileri belirterek performans oturumunu yapılandırın.

2. Performans oturumunda uygulamayı çalıştırarak profil oluşturma verilerini toplayın.

3. Performans sorununu belirlemek için verileri çözümleyin.

4. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Kodun uygulama performansını artıran tümleşik geliştirme ortamında (IDE) kodu değiştirin

5. Değiştirilen kodda profil oluşturma verilerini toplayın ve özgün ve değiştirilen verilerin profil oluşturma verilerini karşılaştırın.

6. Başarıdaki artışı belgeleyen bir rapor oluşturun.

   profil oluşturma tarafından sağlanan bilgilerle çalışmak için, profil oluşturmak istediğiniz ikili dosyalar için ve Windows işletim sisteminin ikilileri için sembol bilgisine sahip olmanız gerekir.

## <a name="configure-the-performance-session"></a>Performans oturumunu yapılandırma
 Bir profil oluşturma oturumu yapılandırmak için, kullanmak istediğiniz profil oluşturma yöntemini ve toplamak istediğiniz verileri seçin. Profil Oluşturma Araçları **Performans Sihirbazı** temel yapılandırmada size yol gösterebilir ve daha fazla seçenek eklemek Için performans oturumu özellik sayfalarını kullanabilirsiniz:

- Profil oluşturma yöntemleri örnekleme, izleme ve bellek ayırmayı içerir.

- Veri değerleri zaman, işlemci ve işletim sistemi performans sayaçlarını ve sayfa hataları ve çekirdek geçişleri gibi uygulama olaylarını içerir.

  Proje çözümünün bir parçası olarak bir projede bir performans oturumu yapılandırabilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] veya IDE aracılığıyla rastgele ikili dosyalar profili oluşturabilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Performans oturumu özellik sayfalarında oturum özelliklerini belirtebilir veya profil oluşturma Sihirbazı 'nı kullanabilirsiniz.

## <a name="collect-profiling-data"></a>Profil oluşturma verilerini topla
 **Performans Gezgini** profil oluşturma verilerinin koleksiyonunu başlatabilirsiniz. Topladığınız veri miktarını sınırlamak için profil oluşturmayı duraklatabilir ve devam ettirebilirsiniz. Zaten çalışan bir işleme ekleyebilirsiniz.

 Uygulama başladıktan hemen sonra **veri toplama denetim** penceresi IDE 'de görüntülenir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . **Veri toplama denetim** penceresinde, koleksiyon işlemini duraklatıp devam ettirerek uygulamanızın belirli bölümlerini profile olabilirsiniz. Toplanan verilere işaretler eklemek için **veri toplama denetim** penceresini de kullanabilirsiniz. İşaretler, profil görünümlerinde görüntülenen ve profil oluşturma verilerini filtrelemek için kullanılabilen, Kullanıcı tanımlı veri noktalarıdır.

 Hedef uygulama kapandığında Profil Oluşturma Araçları, bir profil oluşturma veri dosyası (*. vsp) oluşturur ve IDE 'de Özet rapor görünümünü görüntüler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="analyze-the-data-and-identify-performance-issues"></a>Verileri çözümleyin ve performans sorunlarını tanımla
 Bir profil oluşturma çalıştırmasını sonlandırdığınızda, veriler çözümlenir ve Profil Oluşturma Araçları **Performans raporu** görünümü penceresinde bir özet görüntülenir. Profil oluşturma verileri, çağrı yığını ve hedef uygulamanın ayrı işlevleri için toplanır. Rapor görünümleri, uygulamanın işlem, iş parçacığı, modül, işlev ve kaynak kod satırlarının veri aralıkları için performans analizini görüntüler. Bir işlev için profil oluşturma veri değerleri şunları içerir:

- İşlevinde ve işlev tarafından çağrılan alt işlevlerde harcanan toplam süre (dahil edilen değerler).

- Yalnızca işlevdeki kodu yürütmek için harcanan süre (dışlamalı değerler).

  On iki farklı görünüm, profil oluşturma verilerini en verimli şekilde çözümlemenize olanak tanır. Özelleştirmeleri görüntüle, performans sorunlarına neden olabilecek işlevleri bulmak için verileri filtrelemenizi ve sıralamanıza olanak tanır. Etkin yol filtrelemesi, çağrı ağacı ve modül görünümlerinde en etkin yolların hemen vurgulanmasını sağlar.

## <a name="modify-the-application-code"></a>Uygulama kodunu değiştirme
 Bir veya daha fazla ilgili performans sorununu yalıtdıktan sonra, IDE 'yi kullanarak kodu değiştirebilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve ardından değişiklikleriniz için profil oluşturma verileri toplayabilirsiniz.

## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Profil oluşturma verileri yeniden toplayın ve verileri profil oluşturma çalıştırmaları arasında karşılaştırın
 Profil Oluşturma Araçları karşılaştırma rapor görünümü, seçili iki profil oluşturma veri dosyası arasındaki modül, işlev veya satır performansı arasındaki farkı görüntüler. Karşılaştırmak istediğiniz profil oluşturma verileri değerlerini belirtebilir ve tek tek dosyaların karşılaştırma görünümü ve görünümleri arasında geçiş yapabilirsiniz.

## <a name="generate-a-report-of-the-results"></a>Sonuçların raporunu oluşturma
 Herhangi bir performans raporu görünümündeki satırları e-postalara ve elektronik tablolara yapıştırabilirsiniz ve bir veya daha fazla görünüm için verileri içeren raporlar oluşturabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- ['a Genel Bakış](../profiling/overviews-performance-tools.md)
- [İzlenecek yol: Performans sorunlarını tanımlama](beginners-guide-to-cpu-sampling.md)
