---
title: Bir bulut hizmetinin performansını test etme | Microsoft Docs
description: Visual Studio profil oluşturucu kullanılarak bir bulut hizmetinin performansını test etme
author: mikejo5000
manager: jillfra
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.tgt_pltfrm: multiple
ms.workload: na
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 35593f4164ed024db19b5fa3503b2d7589a7ac2b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74289757"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Bulut hizmetinin performansını test etme
## <a name="overview"></a>Genel Bakış
Aşağıdaki yollarla bir bulut hizmetinin performansını test edebilirsiniz:

* Azure Tanılama, istekler ve bağlantılar hakkında bilgi toplamak ve hizmeti bir müşteri açısından nasıl çalıştığını gösteren site istatistiklerini gözden geçirmek için kullanın. Kullanmaya başlamak için bkz. [Azure Cloud Services ve sanal makineler için tanılamayı yapılandırma](https://go.microsoft.com/fwlink/p/?LinkId=623009).
* Visual Studio profil oluşturucu hizmeti nasıl çalışır hesaplama yönlerini derinlemesine analizini almak için kullanın. Bu konuda açıklandığı gibi bir hizmet, Azure'da çalışan performansını ölçmek için profil oluşturucu kullanabilirsiniz. Bir işlem öykünücüsünde yerel olarak çalışan bir hizmetin performansını ölçmek için profil oluşturucunun nasıl kullanılacağı hakkında bilgi için, bkz. [Visual Studio Profiler kullanarak Işlem öykünücüsünde Azure bulut hizmetinin performansını yerel olarak test etme](https://go.microsoft.com/fwlink/p/?LinkId=262845).

## <a name="choosing-a-performance-testing-method"></a>Performans sınama yöntemi seçme
### <a name="use-azure-diagnostics-to-collect"></a>Azure Tanılama verileri toplamak için kullanın:
* Web sayfaları veya istekler ve bağlantılar gibi Hizmetleri istatistikleri.
* Rolleri, rol ne sıklıkta yeniden gibi istatistikleri.
* Genel bir çalışan rolü gibi çöp toplayıcı geçen süreyi veya bellek yüzdesini, bellek kullanımı hakkında bilgi ayarlayın.

### <a name="use-the-visual-studio-profiler-to"></a>Visual Studio profil oluşturucu için kullanın:
* Hangi işlevlerin en uzun süre yürütülen belirleyin.
* Her bir işlem bakımından yoğun programın parçası süresini ölçün.
* Bir hizmeti iki sürümü için ayrıntılı porovnat sestavy výkonu
* Bellek ayırma bireysel bellek ayırmaları düzeyi daha ayrıntılı analiz edin.
* Eşzamanlılık sorunları çok iş parçacıklı kod analiz edin.

Profil oluşturucuyu kullandığınızda, bir bulut hizmeti yerel olarak veya azure'da çalıştırıldığında veri toplayabilir.

### <a name="collect-profiling-data-locally-to"></a>İçin profil oluşturma verilerini yerel olarak toplamak:
* Bir bölümü bir bulut hizmetinin performansını test etme, gerçekçi bir benzetim yapılmış yükleme gerektirmez belirli bir çalışan rolü yürütme gibi.
* Yalıtım, denetlenen koşullarda bir bulut hizmetinin performansını test.
* Azure'a dağıtmadan önce bir bulut hizmetinin performansını test edin.
* Özel bir bulut hizmetinin performansını var olan dağıtımları etkilemeden test edin.
* Azure'da çalıştırmak için ücret ödemeden hizmetinin performansını test edin.

### <a name="collect-profiling-data-in-azure-to"></a>Azure için profil oluşturma verilerini toplama:
* Sanal ya da gerçek bir yük altında bir bulut hizmetinin performansını test edin.
* Bu konuda daha sonra açıklandığı gibi profil oluşturma verileri toplama araçları yöntemini kullanın.
* Hizmet üretim ortamında çalıştığında olarak aynı ortamda hizmetinin performansını test.

Genellikle bir yük testi normal altındaki bulut Hizmetleri veya stres koşullarında benzetimini yapın.

## <a name="profiling-a-cloud-service-in-azure"></a>Azure'daki bir bulut hizmeti profili oluşturma
Bulut hizmetinizi Visual Studio'dan yayımladığınızda, hizmetin profilini ve istediğiniz bilgileri sağlamak için profil oluşturma ayarları belirtin. Her bir rol örneği için bir profil oluşturma oturumu başlatıldı. Hizmetinizi Visual Studio 'dan yayımlama hakkında daha fazla bilgi için bkz. [Visual Studio 'Dan Azure bulut hizmetinde yayımlama](vs-azure-tools-publishing-a-cloud-service.md).

Visual Studio 'da performans profili oluşturma hakkında daha fazla bilgi edinmek için bkz. [Yeni başlayanlar kılavuzu, performans profili oluşturma](https://msdn.microsoft.com/library/azure/ms182372.aspx) ve [profil oluşturma araçları kullanarak uygulama performansını çözümleme](https://msdn.microsoft.com/library/azure/z9z62c29.aspx).

> [!NOTE]
> IntelliTrace veya Bulut hizmetinizi yayımlayın, profil oluşturma etkinleştirebilirsiniz. Her ikisi de etkinleştirilemiyor.
> 
> 

### <a name="profiler-collection-methods"></a>Profiler koleksiyon metotları
Farklı bir koleksiyon metotları, performans sorunlarına temel profil oluşturma için kullanabilirsiniz:

* **CPU örnekleme** -bu yöntem, CPU kullanım sorunlarının ilk analizi için yararlı olan uygulama istatistiklerini toplar. CPU örnekleme, çoğu performans araştırmalar'ı başlatmak için önerilen yöntemdir. CPU örnekleme verileri topladığınızda, profil uygulama üzerinde düşük bir etkisi yoktur.
* **İzleme** -bu yöntem, odaklanmış analizler ve giriş/çıkış performans sorunlarını analiz etmek için yararlı olan ayrıntılı zamanlama verilerini toplar. Araçlar yöntemini her giriş, çıkış ve işlevlerin işlev çağrısı bir modüldeki bir profil oluşturma sırasında kaydeder. Bu yöntem, kodunuzu bir bölümünü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemleri uygulama performansı üzerindeki etkisini anlamak için kullanışlıdır. Bu yöntem, 32-bit işletim sistemi çalıştıran bir bilgisayar için devre dışı bırakıldı. Bu seçenek, yalnızca bulut hizmeti, Azure'da yerel olarak işlem öykünücüsünde çalıştırdığınızda kullanılabilir.
* **.Net bellek ayırma** -bu yöntem, örnekleme profil oluşturma yöntemini kullanarak .NET Framework bellek ayırma verileri toplar. Toplanan veriler, sayısını ve ayrılan nesnelerin boyutunu içerir.
* **Eşzamanlılık** -bu yöntem, çok iş parçacıklı ve çok işlem yapan uygulamaları çözümlemede yararlı olan kaynak çekişmesini ve işlem ve iş parçacığı yürütme verilerini toplar. Eşzamanlılık yöntemi gibi bir iş parçacığı zaman bekler, kodunuzun yürütülmesini engeller serbest bırakılacak Uygulama kaynağı için erişim kilitli her olay için veri toplar. Bu yöntem, çok iş parçacıklı uygulamalar çözümlemek için kullanışlıdır.
* Ayrıca, bir veya daha fazla veritabanıyla iletişim kuran çok katmanlı uygulamaların işlevlerinde zaman uyumlu ADO.NET çağrılarının yürütme zamanları hakkında ek bilgiler sağlayan **katman etkileşim profilini**de etkinleştirebilirsiniz. Profil oluşturma yöntemlerinden birini ile Katman etkileşim verileri toplayabilir. Katman etkileşimi profili oluşturma hakkında daha fazla bilgi için bkz. [Katman etkileşimleri görünümü](https://msdn.microsoft.com/library/azure/dd557764.aspx).

## <a name="configuring-profiling-settings"></a>Profil oluşturma ayarlarını yapılandırma
Aşağıdaki resimde, Azure uygulamasını Yayımla iletişim kutusu, profil oluşturma ayarlarını yapılandırma işlemi gösterilmektedir.

![Profil oluşturma ayarlarını yapılandır](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> **Profil oluşturmayı etkinleştir** onay kutusunu etkinleştirmek için, bulut hizmetinizi yayımlamak için kullandığınız yerel bilgisayarda profil oluşturucuyu yüklemiş olmanız gerekir. Varsayılan olarak, profil oluşturucu, Visual Studio'yu yüklediğinizde yüklenir.
> 
> 

### <a name="to-configure-profiling-settings"></a>Profil oluşturma ayarlarını yapılandırmak için
1. Çözüm Gezgini ' de, Azure projeniz için kısayol menüsünü açın ve ardından **Yayımla**' yı seçin. Bulut hizmeti yayımlama hakkında ayrıntılı adımlar için bkz. [Azure araçlarını kullanarak bulut hizmeti yayımlama](https://go.microsoft.com/fwlink/p?LinkId=623012).
2. **Azure uygulaması Yayımla** Iletişim kutusunda **Gelişmiş ayarlar** sekmesini seçin.
3. Profil oluşturmayı etkinleştirmek için **profil oluşturmayı etkinleştir** onay kutusunu seçin.
4. Profil oluşturma ayarlarınızı yapılandırmak için **Ayarlar** köprüsünü seçin. Profil ayarları iletişim kutusu görüntülenir.
5. **Profil oluşturma yönteminden seçenek düğmelerini kullanmak istediğinizde** , ihtiyacınız olan profil oluşturma türünü seçin.
6. Katman etkileşimi profil oluşturma verilerini toplamak için **katman etkileşim profilini etkinleştir** onay kutusunu seçin.
7. Ayarları kaydetmek için **Tamam** düğmesini seçin.
   
    Bu uygulama yayımladığınızda, bu ayarlar, her rol için profil oluşturma oturumu oluşturmak için kullanılır.

## <a name="viewing-profiling-reports"></a>Profil oluşturma raporları görüntüleme
Bulut hizmetinizde bir rolünün her örneği için profil oluşturma oturumunu oluşturulur. Visual Studio'dan her oturum, profil oluşturma raporları görüntülemek için Sunucu Gezgini penceresini görüntüleyin ve ardından bir rol örneği seçmek için Azure işlem düğümünü seçin. Ardından aşağıdaki çizimde gösterildiği gibi profil oluşturma raporu da görüntüleyebilirsiniz.

![Azure'dan Profil Oluşturma Raporunu görüntüleyin](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Profil oluşturma raporları görüntülemek için
1. Visual Studio'da Sunucu Gezgini penceresini görüntülemek için menü çubuğundaki Sunucu Gezgini görünümü seçin.
2. Azure bilgi işlem düğümünü seçin ve ardından Visual Studio'dan yayımlandığında, profil için seçili bulut hizmetini Azure dağıtım düğümünü seçin.
3. Bir örneğin profil oluşturma raporlarını görüntülemek için, hizmette rolü seçin, belirli bir örnek için kısayol menüsünü açın ve **profil oluşturma raporunu görüntüle**' yi seçin.
   
    Rapor, bir .vsp dosya artık Azure'dan indirilir ve yükleme durumu, Azure etkinlik günlüğü'nde görünür. İndirme işlemi tamamlandığında, profil oluşturma raporu, Visual Studio Düzenleyicisi 'ndeki < rol adı\> *< örnek numarası\>* < tanımlayıcı\>. vsp adlı bir sekmede görüntülenir. Rapor için Özet veriler görüntülenir.
4. Geçerli Görünüm listesinde, raporun farklı görünümleri görüntülemek için istediğiniz görünümü türünü seçin. Daha fazla bilgi için bkz. [profil oluşturma araçları rapor görünümleri](https://msdn.microsoft.com/library/azure/bb385755.aspx).

## <a name="next-steps"></a>Sonraki adımlar
[Hata ayıklama Cloud Services](vs-azure-tools-debugging-cloud-services-overview.md)

[Visual Studio 'dan bir Azure bulut hizmetinde yayımlama](vs-azure-tools-publishing-a-cloud-service.md)
