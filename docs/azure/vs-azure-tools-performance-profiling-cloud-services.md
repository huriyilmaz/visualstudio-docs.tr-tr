---
title: Bulut hizmetinin performansını test etme | Microsoft Docs
description: Visual Studio Profiler kullanarak bir bulut hizmetinin performansını test etme
author: mikejo5000
manager: jillfra
ms.assetid: 7a5501aa-f92c-457c-af9b-92ea50914e24
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.openlocfilehash: 04e3ee89498447f7743fc1b5119e129f046b4fcc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72911775"
---
# <a name="testing-the-performance-of-a-cloud-service"></a>Bulut hizmetinin performansını test etme
## <a name="overview"></a>Genel Bakış
Bir bulut hizmetinin performansını aşağıdaki yollarla test edebilirsiniz:

* İstekler ve bağlantılarla ilgili bilgi toplamak ve hizmetin müşterinin perspektifinden nasıl gerçekleştiğini gösteren site istatistiklerini gözden geçirmek için Azure Tanılama kullanın. Kullanmaya başlamak için bkz. [Azure Cloud Services ve sanal makineler için tanılamayı yapılandırma](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md).
* Hizmetin nasıl çalıştığı hesaplama yönlerinin derinlemesine bir analizini öğrenmek için Visual Studio Profiler 'ı kullanın. Bu konuda açıklandığı gibi, Azure 'da bir hizmet olarak performansı ölçmek için profil oluşturucuyu kullanabilirsiniz. Bir işlem öykünücüsünde yerel olarak çalışan bir hizmetin performansını ölçmek için profil oluşturucunun nasıl kullanılacağı hakkında bilgi için, bkz. [Visual Studio Profiler kullanarak Işlem öykünücüsünde Azure bulut hizmetinin performansını yerel olarak test etme](/azure/cloud-services/cloud-services-performance-testing-visual-studio-profiler).

## <a name="choosing-a-performance-testing-method"></a>Performans testi yöntemi seçme
### <a name="use-azure-diagnostics-to-collect"></a>Toplamak için Azure Tanılama kullanın:
* Web sayfaları veya hizmetleri için İstekler ve bağlantılar gibi istatistikler.
* Rol hakkında, bir rolün ne sıklıkta yeniden başlatılma gibi istatistikler.
* Çöp toplayıcısının aldığı sürenin yüzdesi veya çalışan bir rolün bellek kümesi gibi bellek kullanımı hakkındaki genel bilgiler.

### <a name="use-the-visual-studio-profiler-to"></a>Visual Studio Profiler 'ı kullanarak şunları yapın:
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
Bulut hizmetinizi Visual Studio 'dan yayımladığınızda, hizmeti profilin profilini oluşturup istediğiniz bilgileri sağlayan profil oluşturma ayarlarını belirtebilirsiniz. Bir rol örneği için profil oluşturma oturumu başlatılır. Hizmetinizi Visual Studio 'dan yayımlama hakkında daha fazla bilgi için bkz. [Visual Studio 'Dan Azure bulut hizmetinde yayımlama](vs-azure-tools-publishing-a-cloud-service.md).

Visual Studio 'da performans profili oluşturma hakkında daha fazla bilgi edinmek için bkz. [Yeni başlayanlar kılavuzu, performans profili oluşturma](https://msdn.microsoft.com/library/azure/ms182372.aspx) ve [profil oluşturma araçları kullanarak uygulama performansını çözümleme](https://msdn.microsoft.com/library/azure/z9z62c29.aspx).

> [!NOTE]
> Bulut hizmetinizi yayımladığınızda IntelliTrace veya profil oluşturma seçeneklerinden birini etkinleştirebilirsiniz. Her ikisini de etkinleştiremezsiniz.
>
>

### <a name="profiler-collection-methods"></a>Profil Oluşturucu koleksiyon yöntemleri
Profil oluşturma için performans sorunlarınızı temel alarak farklı koleksiyon yöntemleri kullanabilirsiniz:

* **CPU örnekleme** -bu yöntem, CPU kullanım sorunlarının ilk analizi için yararlı olan uygulama istatistiklerini toplar. CPU örnekleme, en fazla performans araştırmamının başlatılması için önerilen yöntemdir. CPU örnekleme verilerini toplarken profil oluşturduğunuz uygulamada düşük bir etkisi vardır.
* **İzleme** -bu yöntem, odaklanmış analizler ve giriş/çıkış performans sorunlarını analiz etmek için yararlı olan ayrıntılı zamanlama verilerini toplar. İzleme yöntemi, bir profil oluşturma işlemi sırasında bir modüldeki işlevlerin her bir girdisini, çıkış ve işlev çağrısını kaydeder. Bu yöntem, kodunuzun bir bölümü hakkında ayrıntılı zamanlama bilgileri toplamak ve giriş ve çıkış işlemlerinin uygulama performansı üzerinde etkisini anlamak için yararlıdır. Bu yöntem, 32 bitlik bir işletim sistemi çalıştıran bir bilgisayar için devre dışıdır. Bu seçenek yalnızca, bulut hizmetini işlem öykünücüsünde yerel olarak değil, Azure 'da çalıştırdığınızda kullanılabilir.
* **.Net bellek ayırma** -bu yöntem, örnekleme profil oluşturma yöntemini kullanarak .NET Framework bellek ayırma verileri toplar. Toplanan veriler, ayrılan nesnelerin sayısını ve boyutunu içerir.
* **Eşzamanlılık** -bu yöntem, çok iş parçacıklı ve çok işlem yapan uygulamaları çözümlemede yararlı olan kaynak çekişmesini ve işlem ve iş parçacığı yürütme verilerini toplar. Eşzamanlılık yöntemi, kodunuzun yürütülmesini engelleyen her olay için veri toplar; Örneğin, bir iş parçacığı, bir uygulama kaynağına yönelik kilitli erişimin serbest gelmesini bekler. Bu yöntem, çok iş parçacıklı uygulamaların çözümlenmesi için yararlıdır.
* Ayrıca, bir veya daha fazla veritabanıyla iletişim kuran çok katmanlı uygulamaların işlevlerinde zaman uyumlu ADO.NET çağrılarının yürütme zamanları hakkında ek bilgiler sağlayan **katman etkileşim profilini**de etkinleştirebilirsiniz. Herhangi bir profil oluşturma yönteminden katman etkileşim verileri toplayabilirsiniz. Katman etkileşimi profili oluşturma hakkında daha fazla bilgi için bkz. [Katman etkileşimleri görünümü](https://msdn.microsoft.com/library/azure/dd557764.aspx).

## <a name="configuring-profiling-settings"></a>Profil oluşturma ayarlarını yapılandırma
Aşağıdaki çizimde, profil oluşturma ayarlarınızı Azure uygulaması yayımlama iletişim kutusundan yapılandırma gösterilmektedir.

![Profil oluşturma ayarlarını yapılandır](./media/vs-azure-tools-performance-profiling-cloud-services/IC526984.png)

> [!NOTE]
> **Profil oluşturmayı etkinleştir** onay kutusunu etkinleştirmek için, bulut hizmetinizi yayımlamak için kullandığınız yerel bilgisayarda profil oluşturucuyu yüklemiş olmanız gerekir. Varsayılan olarak, profil oluşturucu Visual Studio 'Yu yüklediğinizde yüklenir.
>
>

### <a name="to-configure-profiling-settings"></a>Profil oluşturma ayarlarını yapılandırmak için
1. Çözüm Gezgini ' de, Azure projeniz için kısayol menüsünü açın ve ardından **Yayımla**' yı seçin. Bulut hizmeti yayımlama hakkında ayrıntılı adımlar için bkz. [Azure araçlarını kullanarak bulut hizmeti yayımlama](vs-azure-tools-publishing-a-cloud-service.md).
2. **Azure uygulaması Yayımla** Iletişim kutusunda **Gelişmiş ayarlar** sekmesini seçin.
3. Profil oluşturmayı etkinleştirmek için **profil oluşturmayı etkinleştir** onay kutusunu seçin.
4. Profil oluşturma ayarlarınızı yapılandırmak için **Ayarlar** köprüsünü seçin. Profil oluşturma ayarları iletişim kutusu görüntülenir.
5. **Profil oluşturma yönteminden seçenek düğmelerini kullanmak istediğinizde** , ihtiyacınız olan profil oluşturma türünü seçin.
6. Katman etkileşimi profil oluşturma verilerini toplamak için **katman etkileşim profilini etkinleştir** onay kutusunu seçin.
7. Ayarları kaydetmek için **Tamam** düğmesini seçin.

    Bu uygulamayı yayımladığınızda, bu ayarlar her bir rol için profil oluşturma oturumu oluşturmak için kullanılır.

## <a name="viewing-profiling-reports"></a>Profil oluşturma raporlarını görüntüleme
Bulut hizmetinizde bir rolün her örneği için bir profil oluşturma oturumu oluşturulur. Visual Studio 'dan her bir oturumun profil oluşturma raporlarınızı görüntülemek için Sunucu Gezgini penceresini görüntüleyebilir ve ardından bir rolün örneğini seçmek üzere Azure Işlem düğümünü seçebilirsiniz. Daha sonra profil oluşturma raporunu aşağıdaki çizimde gösterildiği gibi görüntüleyebilirsiniz.

![Azure 'dan profil oluşturma raporunu görüntüle](./media/vs-azure-tools-performance-profiling-cloud-services/IC748914.png)

### <a name="to-view-profiling-reports"></a>Profil oluşturma raporlarını görüntülemek için
1. Visual Studio 'da Sunucu Gezgini penceresini görüntülemek için, menü çubuğunda Görünüm, Sunucu Gezgini öğesini seçin.
2. Azure Işlem düğümünü seçin ve ardından Visual Studio 'dan yayımlandığında profil için seçtiğiniz bulut hizmeti için Azure dağıtım düğümünü seçin.
3. Bir örneğin profil oluşturma raporlarını görüntülemek için, hizmette rolü seçin, belirli bir örnek için kısayol menüsünü açın ve **profil oluşturma raporunu görüntüle**' yi seçin.

    Bu rapor, bir. vsp dosyası artık Azure 'dan indirilir ve indirme durumu Azure etkinlik günlüğünde görüntülenir. İndirme işlemi tamamlandığında, profil oluşturma raporu Visual Studio Düzenleyicisi 'nde <rol adı \> *<örnek numarası \> *<Identifier. vsp adlı bir sekmede görüntülenir \> . Raporun özet verileri görüntülenir.
4. Raporun farklı görünümlerini görüntülemek için, geçerli görünüm listesinde istediğiniz görünüm türünü seçin. Daha fazla bilgi için bkz. [profil oluşturma araçları rapor görünümleri](https://msdn.microsoft.com/library/azure/bb385755.aspx).

## <a name="next-steps"></a>Sonraki adımlar
[Hata ayıklama Cloud Services](vs-azure-tools-debug-cloud-services-virtual-machines.md)

[Visual Studio 'dan bir Azure bulut hizmetinde yayımlama](vs-azure-tools-publishing-a-cloud-service.md)
