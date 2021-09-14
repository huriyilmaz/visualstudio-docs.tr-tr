---
title: Bulut hizmetinin performansını test etme | Microsoft Docs
description: Visual Studio profil oluşturucuyu kullanarak bir bulut hizmetinin performansını Test etme
author: mikejo5000
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.openlocfilehash: 79fd599b58a951f67c4fb095528e8be00bcd2a17
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633086"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Bulut hizmetinin performansını test etme
## <a name="overview"></a>Genel Bakış
Bir bulut hizmetinin performansını aşağıdaki yollarla test edebilirsiniz:

* İstekler ve bağlantılarla ilgili bilgi toplamak ve hizmetin müşterinin perspektifinden nasıl gerçekleştiğini gösteren site istatistiklerini gözden geçirmek için Azure Tanılama kullanın. Kullanmaya başlamak için bkz. [Azure Cloud Services ve sanal makineler için tanılamayı yapılandırma](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).
* hizmetin nasıl çalıştığını gösteren hesaplama yönlerinin derinlemesine bir analizini öğrenmek için Visual Studio profiler 'ı kullanın. Bu konuda açıklandığı gibi, Azure 'da bir hizmet olarak performansı ölçmek için profil oluşturucuyu kullanabilirsiniz. bir hizmet olarak performansı bir işlem öykünücüsünde yerel olarak ölçmek üzere profil oluşturucunun nasıl kullanılacağı hakkında bilgi için, bkz. [Visual Studio profil oluşturucu kullanarak, işlem Emulator yerel olarak Azure bulut hizmeti performansını test etme](/azure/cloud-services/cloud-services-performance-testing-visual-studio-profiler).

## <a name="choosing-a-performance-testing-method"></a>Performans testi yöntemi seçme
### <a name="use-azure-diagnostics-to-collect"></a>Toplamak için Azure Tanılama kullanın:
* Web sayfaları veya hizmetleri için İstekler ve bağlantılar gibi istatistikler.
* Rol hakkında, bir rolün ne sıklıkta yeniden başlatılma gibi istatistikler.
* Çöp toplayıcısının aldığı sürenin yüzdesi veya çalışan bir rolün bellek kümesi gibi bellek kullanımı hakkındaki genel bilgiler.

### <a name="use-the-visual-studio-profiler-to"></a>Visual Studio profil oluşturucuyu kullanın:
* Hangi işlevlerin en iyi şekilde çalışacağını saptayın.
* Yoğun bir şekilde yoğun bir programın her bir parçasının ne kadar zaman aldığını ölçün.
* Bir hizmetin iki sürümü için ayrıntılı performans raporlarını karşılaştırın.
* Bellek ayırmayı, tek tek bellek ayırmaları düzeyinden daha ayrıntılı olarak analiz edin.
* Çok iş parçacıklı koddaki eşzamanlılık sorunlarını analiz edin.

Profil oluşturucuyu kullandığınızda, bir bulut hizmeti yerel olarak veya Azure 'da çalıştığında verileri toplayabilirsiniz.

### <a name="collect-profiling-data-locally-to"></a>Profil oluşturma verilerini yerel olarak toplayın:
* Belirli bir çalışan rolünün yürütülmesi gibi, gerçekçi bir sanal yük gerektirmeyen bir bulut hizmeti bölümünün performansını test edin.
* Denetlenen koşullar altında, bulut hizmetinin performansını yalıtımda test edin.
* Azure 'a dağıtmadan önce bir bulut hizmetinin performansını test edin.
* Mevcut dağıtımları bozmadan bir bulut hizmetinin performansını özel olarak test edin.
* Azure 'da çalışmaya yönelik ücretler ödemeden hizmetin performansını test edin.

### <a name="collect-profiling-data-in-azure-to"></a>Azure 'da profil oluşturma verilerini şu şekilde toplayın:
* Bir bulut hizmetinin sanal veya gerçek bir yük altında performansını test edin.
* Bu konuda daha sonra açıklandığı gibi, profil oluşturma verilerini toplamak için izleme yöntemini kullanın.
* Hizmetin, üretimde çalıştırıldığı hizmetin performansını aynı ortamda test edin.

Genellikle, normal veya stres koşullarında bulut hizmetlerini test etmek için bir yükün benzetimini yapabilirsiniz.

## <a name="profiling-a-cloud-service-in-azure"></a>Azure 'da bir bulut hizmetinin profilini oluşturma
bulut hizmetinizi Visual Studio yayımladığınızda, hizmeti profilin profilini oluşturup istediğiniz bilgileri sağlayan profil oluşturma ayarlarını belirtebilirsiniz. Bir rol örneği için profil oluşturma oturumu başlatılır. hizmetinizi Visual Studio 'den yayımlama hakkında daha fazla bilgi için, bkz. [Visual Studio Azure bulut hizmetinde yayımlama](vs-azure-tools-publishing-a-cloud-service.md).

Visual Studio ' de performans profili oluşturma hakkında daha fazla bilgi için bkz. performans profili oluşturma ve [Profil Oluşturma Araçları kullanarak uygulama performansını çözümleme](../profiling/performance-explorer.md) [için yeni başlayanlar kılavuzu](../profiling/beginners-guide-to-performance-profiling.md) .

> [!NOTE]
> Bulut hizmetinizi yayımladığınızda IntelliTrace veya profil oluşturma seçeneklerinden birini etkinleştirebilirsiniz. Her ikisini de etkinleştiremezsiniz.
>
>

### <a name="profiler-collection-methods"></a>Profil Oluşturucu koleksiyon yöntemleri
Profil oluşturma için performans sorunlarınızı temel alarak farklı koleksiyon yöntemleri kullanabilirsiniz:

* **CPU örnekleme** -bu yöntem, CPU kullanım sorunlarının ilk analizi için yararlı olan uygulama istatistiklerini toplar. CPU örnekleme, en fazla performans araştırmamının başlatılması için önerilen yöntemdir. CPU örnekleme verilerini toplarken profil oluşturduğunuz uygulamada düşük bir etkisi vardır.
* **İzleme** -bu yöntem, odaklanmış analizler ve giriş/çıkış performans sorunlarını analiz etmek için yararlı olan ayrıntılı zamanlama verilerini toplar. İzleme yöntemi, bir profil oluşturma işlemi sırasında bir modüldeki işlevlerin her bir girdisini, çıkış ve işlev çağrısını kaydeder. Bu yöntem, kodunuzun bir bölümü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemlerinin uygulama performansı üzerinde etkisini anlamak için yararlıdır. Bu yöntem, 32 bitlik bir işletim sistemi çalıştıran bir bilgisayar için devre dışıdır. Bu seçenek yalnızca, bulut hizmetini işlem öykünücüsünde yerel olarak değil, Azure 'da çalıştırdığınızda kullanılabilir.
* **.net bellek ayırma** -bu yöntem, örnekleme profil oluşturma yöntemini kullanarak .NET Framework bellek ayırma verileri toplar. Toplanan veriler, ayrılan nesnelerin sayısını ve boyutunu içerir.
* **Eşzamanlılık** -bu yöntem, çok iş parçacıklı ve çok işlem yapan uygulamaları çözümlemede yararlı olan kaynak çekişmesini ve işlem ve iş parçacığı yürütme verilerini toplar. Eşzamanlılık yöntemi, kodunuzun yürütülmesini engelleyen her olay için veri toplar; Örneğin, bir iş parçacığı, bir uygulama kaynağına yönelik kilitli erişimin serbest gelmesini bekler. Bu yöntem, çok iş parçacıklı uygulamaların çözümlenmesi için yararlıdır.
* ayrıca, bir veya daha fazla veritabanıyla iletişim kuran çok katmanlı uygulamaların işlevlerinde zaman uyumlu ADO.NET çağrılarının yürütme zamanları hakkında ek bilgiler sağlayan **katman etkileşim profilini** de etkinleştirebilirsiniz. Herhangi bir profil oluşturma yönteminden katman etkileşim verileri toplayabilirsiniz. Katman etkileşimi profili oluşturma hakkında daha fazla bilgi için bkz. [Katman etkileşimleri görünümü](../profiling/tier-interactions-view.md).

## <a name="configuring-profiling-settings"></a>Profil oluşturma ayarlarını yapılandırma
Aşağıdaki çizimde, profil oluşturma ayarlarınızı Azure uygulaması yayımlama iletişim kutusundan yapılandırma gösterilmektedir.

![profil oluşturma Ayarlar yapılandırma](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> **Profil oluşturmayı etkinleştir** onay kutusunu etkinleştirmek için, bulut hizmetinizi yayımlamak için kullandığınız yerel bilgisayarda profil oluşturucuyu yüklemiş olmanız gerekir. Varsayılan olarak, Visual Studio yüklediğinizde profil oluşturucu yüklenir.
>
>

### <a name="to-configure-profiling-settings"></a>Profil oluşturma ayarlarını yapılandırmak için
1. Çözüm Gezgini ' de, Azure projeniz için kısayol menüsünü açın ve ardından **Yayımla**' yı seçin. Bulut hizmeti yayımlama hakkında ayrıntılı adımlar için bkz. [Azure araçlarını kullanarak bulut hizmeti yayımlama](vs-azure-tools-publishing-a-cloud-service.md).
2. **Azure uygulaması yayımla** iletişim kutusunda **gelişmiş Ayarlar** sekmesini seçin.
3. Profil oluşturmayı etkinleştirmek için **profil oluşturmayı etkinleştir** onay kutusunu seçin.
4. profil oluşturma ayarlarınızı yapılandırmak için **Ayarlar** köprü öğesini seçin. profil oluşturma Ayarlar iletişim kutusu görüntülenir.
5. **Profil oluşturma yönteminden seçenek düğmelerini kullanmak istediğinizde** , ihtiyacınız olan profil oluşturma türünü seçin.
6. Katman etkileşimi profil oluşturma verilerini toplamak için **katman etkileşim profilini etkinleştir** onay kutusunu seçin.
7. Ayarları kaydetmek için **Tamam** düğmesini seçin.

    Bu uygulamayı yayımladığınızda, bu ayarlar her bir rol için profil oluşturma oturumu oluşturmak için kullanılır.

## <a name="viewing-profiling-reports"></a>Profil oluşturma raporlarını görüntüleme
Bulut hizmetinizde bir rolün her örneği için bir profil oluşturma oturumu oluşturulur. Visual Studio her bir oturumun profil oluşturma raporlarınızı görüntülemek için Sunucu Gezgini penceresini görüntüleyebilir ve ardından bir rolün örneğini seçmek üzere Azure işlem düğümünü seçebilirsiniz. Daha sonra profil oluşturma raporunu aşağıdaki çizimde gösterildiği gibi görüntüleyebilirsiniz.

![Azure 'dan profil oluşturma raporunu görüntüle](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Profil oluşturma raporlarını görüntülemek için
1. Visual Studio Sunucu Gezgini penceresini görüntülemek için, menü çubuğunda görünüm, Sunucu Gezgini ' yı seçin.
2. Azure Işlem düğümünü seçin ve ardından Visual Studio ' den yayımladığınızda profil için seçtiğiniz bulut hizmeti için Azure dağıtım düğümünü seçin.
3. Bir örneğin profil oluşturma raporlarını görüntülemek için, hizmette rolü seçin, belirli bir örnek için kısayol menüsünü açın ve **profil oluşturma raporunu görüntüle**' yi seçin.

    Bu rapor, bir. vsp dosyası artık Azure 'dan indirilir ve indirme durumu Azure etkinlik günlüğünde görüntülenir. indirme tamamlandığında, profil oluşturma raporu, <rol adı \> *<örnek numarası \>*<ıdentifier. vsp adlı Visual Studio için düzenleyicide bir sekmede görüntülenir \> . Raporun özet verileri görüntülenir.
4. Raporun farklı görünümlerini görüntülemek için, geçerli görünüm listesinde istediğiniz görünüm türünü seçin. Daha fazla bilgi için bkz. [profil oluşturma araçları rapor görünümleri](../profiling/performance-report-views.md).

## <a name="next-steps"></a>Sonraki adımlar
[Hata ayıklama Cloud Services](vs-azure-tools-debug-cloud-services-virtual-machines.md)

[Visual Studio Azure bulut hizmetinde yayımlama](vs-azure-tools-publishing-a-cloud-service.md)
