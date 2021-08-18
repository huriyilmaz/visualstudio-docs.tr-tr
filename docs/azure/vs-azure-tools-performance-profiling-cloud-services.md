---
title: Bulut hizmeti performansını test | Microsoft Docs
description: Visual Studio profilleyiciyi kullanarak bulut hizmetinin performansını test edin
author: mikejo5000
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.openlocfilehash: 79fd599b58a951f67c4fb095528e8be00bcd2a17
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059678"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Bulut hizmetinin performansını test etme
## <a name="overview"></a>Genel Bakış
Bulut hizmetinin performansını test etmek için aşağıdaki yöntemleri kullanabilirsiniz:

* İstekler Azure Tanılama bağlantılar hakkında bilgi toplamak ve hizmetin müşteri perspektifinden nasıl performans sergileyene site istatistiklerini gözden geçirmek için Azure Tanılama'i kullanın. ile çalışmaya başlama için, [bkz. Configuring diagnostics for Azure Cloud Services and Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).
* Hizmetin Visual Studio hesaplama yönlerini ayrıntılı bir şekilde analiz etmek için Visual Studio profilleyiciyi kullanın. Bu konu başlığında da anlatıldı. Azure'da hizmet çalıştırıldıklarında performansı ölçmek için profil oluşturma hizmetini kullanabilirsiniz. Bir hizmet bir işlem öykünücüsünün içinde yerel olarak çalıştırıldı olarak performansı ölçmek için profil oluşturmanın nasıl kullanıla hakkında bilgi için bkz. İşlem Emulator Using the Visual Studio [Profiler](/azure/cloud-services/cloud-services-performance-testing-visual-studio-profiler).

## <a name="choosing-a-performance-testing-method"></a>Performans testi yöntemi seçme
### <a name="use-azure-diagnostics-to-collect"></a>Şunları Azure Tanılama için Azure Tanılama kullanın:
* İstekler ve bağlantılar gibi web sayfaları veya hizmetleriyle ilgili istatistikler.
* Bir rolün ne sıklıkta yeniden başlat olduğu gibi rollerle ilgili istatistikler.
* Atık toplayıcının zaman yüzdesi veya çalışan rolün bellek kümesi gibi bellek kullanımı hakkında genel bilgiler.

### <a name="use-the-visual-studio-profiler-to"></a>Profil Visual Studio kullanarak:
* En uzun zaman alan işlevleri belirleme.
* Yoğun işlem gücü kullanımına sahip bir programın her parçasının ne kadar zaman alır ölçün.
* Bir hizmetin iki sürümü için ayrıntılı performans raporlarını karşılaştırın.
* Bellek ayırmayı tek tek bellek ayırma düzeyinden daha ayrıntılı olarak analiz etme.
* Çok iş parçacıklı kodda eşzamanlılık sorunlarını analiz etme.

Profilleyiciyi kullanarak, bir bulut hizmeti yerel olarak veya Azure'da çalıştır çalıştırıcıda veri toplayabilirsiniz.

### <a name="collect-profiling-data-locally-to"></a>Profil oluşturma verilerini yerel olarak toparak:
* Gerçekçi bir sanal yük gerektirmeyen belirli bir çalışan rolünün yürütülmesi gibi bir bulut hizmetinin bir parçasının performansını test edin.
* Denetimli koşullar altında bir bulut hizmetinin performansını yalıtarak test edin.
* Azure'a dağıtmadan önce bulut hizmetinin performansını test edin.
* Mevcut dağıtımları bozmadan bulut hizmetinin performansını özel olarak test edin.
* Azure'da çalıştırma için ücret ödemeden hizmetin performansını test edin.

### <a name="collect-profiling-data-in-azure-to"></a>Azure'da profil oluşturma verilerini toparak:
* Sanal veya gerçek yük altında bulut hizmetinin performansını test edin.
* Bu konu başlığında daha sonra açıklanmıştır. Profil oluşturma verilerini toplamak için ölçüm yöntemini kullanın.
* Hizmetin performansını üretim ortamında çalıştırarak aynı ortamda test etmek.

Bulut hizmetlerini normal veya stres koşullarında test etmek için genellikle yükün benzetimini siz sağlarız.

## <a name="profiling-a-cloud-service-in-azure"></a>Azure'da bulut hizmetinin profilini oluşturma
Buluttan bulut hizmetinizi Visual Studio, hizmetin profilini oluşturun ve size istediğiniz bilgileri verecek profil oluşturma ayarlarını belirtin. Bir rolün her örneği için profil oluşturma oturumu başlatıldı. Hizmetinizi Visual Studio'den yayımlama hakkında daha fazla bilgi için bkz. [Visual Studio.](vs-azure-tools-publishing-a-cloud-service.md)

Visual Studio'da performans profili oluşturma hakkında daha [](../profiling/beginners-guide-to-performance-profiling.md) fazla bilgi için bkz. Profil Oluşturma Araçları Kullanarak Uygulama Performansını Analiz Etme ve [Performans Profili Oluşturma için Profil Oluşturma Araçları.](../profiling/performance-explorer.md)

> [!NOTE]
> Bulut hizmetinizi yayımlarken IntelliTrace'i veya profil oluşturmayı etkinleştirabilirsiniz. her ikisini de etkinleştire diyez.
>
>

### <a name="profiler-collection-methods"></a>Profil oluşturma toplama yöntemleri
Performans sorunlarınıza bağlı olarak profil oluşturma için farklı koleksiyon yöntemleri kullanabilirsiniz:

* **CPU örnekleme** - Bu yöntem, CPU kullanım sorunlarının ilk analizinde yararlı olan uygulama istatistiklerini toplar. CPU örnekleme, çoğu performans araştırmalarını başlatmaya ilişkin önerilen yöntemdir. CPU örnekleme verilerini toplayan uygulama üzerinde profil oluşturmanın etkisi düşüktür.
* **Instrumentation** -Bu yöntem, odaklanmış analiz ve giriş/çıkış performans sorunlarını analiz etmek için yararlı olan ayrıntılı zamanlama verilerini toplar. Ölçüm yöntemi, profil oluşturma çalıştırması sırasında bir modülde işlevlerin giriş, çıkış ve işlev çağrılarını kaydediyor. Bu yöntem, kodunuzun bir bölümü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemlerinin uygulama performansı üzerindeki etkisini anlamak için yararlıdır. Bu yöntem, 32 bit işletim sistemi çalıştıran bir bilgisayar için devre dışıdır. Bu seçenek yalnızca bulut hizmetini azure'da çalıştırarak kullanılabilir, işlem öykünücüsünü yerel olarak çalıştırmaz.
* **.NET Bellek Ayırma** - Bu yöntem, .NET Framework profil oluşturma yöntemini kullanarak bellek ayırma verilerini toplar. Toplanan veriler, ayrılan nesnelerin sayısını ve boyutunu içerir.
* **Eşzamanlılık** - Bu yöntem, çok iş parçacıklı ve çok işlemli uygulamaları analiz etmede yararlı olan kaynak ve iş parçacığı yürütme verilerini ve işleme ve iş parçacığı yürütme verilerini toplar. Eşzamanlılık yöntemi, bir iş parçacığının uygulama kaynağına kilitli erişimin serbest bıraklığını beklemesi gibi kodunuzun yürütülmesini engelleyen her olay için veri toplar. Bu yöntem, çok iş parçacıklı uygulamaları analiz etmek için kullanışlıdır.
* Bir veya daha fazla veritabanıyla iletişim kuran çok katmanlı uygulamaların işlevlerinde zaman uyumlu ADO.NET yürütme süreleri hakkında ek bilgi sağlayan Katman Etkileşimi **Profili** Oluşturmayı da etkinleştirebilirsiniz. Profil oluşturma yöntemlerden herhangi biri ile katman etkileşim verileri toplayabilirsiniz. Katman etkileşimi profili oluşturma hakkında daha fazla bilgi için bkz. [Katman Etkileşimleri Görünümü.](../profiling/tier-interactions-view.md)

## <a name="configuring-profiling-settings"></a>Profil oluşturma ayarlarını yapılandırma
Aşağıdaki çizimde, Azure Uygulamasını Yayımla iletişim kutusundan profil oluşturma ayarlarınızı yapılandırma adımları gösterilmiştir.

![Profil Oluşturma Ayarlar](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> Profil oluşturmayı **etkinleştir onay** kutusunu etkinleştirmek için, profil oluşturmanın bulut hizmetinizi yayımlamak için kullanmakta olduğu yerel bilgisayarda yüklü olması gerekir. Varsayılan olarak, profil işleyiciyi Visual Studio.
>
>

### <a name="to-configure-profiling-settings"></a>Profil oluşturma ayarlarını yapılandırmak için
1. Bu Çözüm Gezgini Azure projenizin kısayol menüsünü açın ve Yayımla'yı **seçin.** Bulut hizmetini yayımlama hakkında ayrıntılı adımlar için bkz. [Azure araçlarını kullanarak bulut hizmeti yayımlama.](vs-azure-tools-publishing-a-cloud-service.md)
2. Azure **Uygulamasını Yayımla iletişim** kutusunda Gelişmiş Uygulama **sekmesini Ayarlar** seçin.
3. Profil oluşturmayı etkinleştirmek için Profil oluşturmayı **etkinleştir onay** kutusunu seçin.
4. Profil oluşturma ayarlarınızı yapılandırmak için profil oluşturma **Ayarlar** seçin. Profil Oluşturma Ayarlar iletişim kutusu görüntülenir.
5. Seçenek **düğmelerini kullanmak istediğiniz profil** oluşturma yöntemi menüsünden ihtiyacınız olan profil oluşturma türünü seçin.
6. Katman etkileşimi profil oluşturma verilerini toplamak için Katman Etkileşimi **Profili Oluşturmayı Etkinleştir onay** kutusunu seçin.
7. Ayarları kaydetmek için Tamam **düğmesini** seçin.

    Bu uygulamayı yayımlarken, her rol için profil oluşturma oturumunu oluşturmak için bu ayarlar kullanılır.

## <a name="viewing-profiling-reports"></a>Profil Oluşturma Raporlarını Görüntüleme
Bulut hizmetinize bir rolün her örneği için profil oluşturma oturumu oluşturulur. Her oturum için profil oluşturma raporlarınızı Visual Studio için Sunucu Gezgini penceresini görüntü Azure İşlem bir rol örneği seçmek için Azure İşlem düğümünü seçebilirsiniz. Daha sonra profil oluşturma raporunu aşağıdaki çizimde gösterildiği gibi görüntüebilirsiniz.

![Azure'dan Profil Oluşturma Raporunu Görüntüleme](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Profil oluşturma raporlarını görüntülemek için
1. Görünüm penceresinde Sunucu Gezgini görüntülemek Visual Studio menü çubuğunda Görünüm'e tıklayın ve Sunucu Gezgini.
2. Azure İşlem düğümünü seçin ve ardından bu düğümden yayımlarken profil oluşturmak üzere seçtiğiniz bulut hizmeti için Azure dağıtım Visual Studio.
3. Bir örneğin profil oluşturma raporlarını görüntülemek için hizmette rolü seçin, belirli bir örneğin kısayol menüsünü açın ve ardından Profil Oluşturma Raporunu **Görüntüle'yi seçin.**

    Bir .vsp dosyası olan rapor artık Azure'dan indirilir ve indirme durumu Azure Etkinlik Günlüğü'nden görüntülenir. İndirme işlemi tamamlandığında profil oluşturma raporu, \> *\>* .vsp Visual Studio Rol adı <Örnek Numarası<adlı<\> görünür. Raporun özet verileri görüntülenir.
4. Raporun farklı görünümlerini görüntülemek için Geçerli Görünüm listesinde istediğiniz görünüm türünü seçin. Daha fazla bilgi için [bkz. Profil Oluşturma Araçları Görünümlerini Görüntüleme.](../profiling/performance-report-views.md)

## <a name="next-steps"></a>Sonraki adımlar
[Hata ayıklama Cloud Services](vs-azure-tools-debug-cloud-services-virtual-machines.md)

[Visual Studio'den Azure Bulut Hizmeti'ne yayımlama](vs-azure-tools-publishing-a-cloud-service.md)
