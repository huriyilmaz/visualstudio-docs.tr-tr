---
title: Yük testleri için Sanal Kullanıcı Etkinlik Grafiği'ni kullanma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c58dd4f6e6a0c8fe1bd468053bf18c3635b1ee9d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "78169384"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Walkthrough: Sorunları yalıtmak için Sanal Kullanıcı Etkinlik Grafiği'ni kullanma

Bu iznizde, yükleme testinizi çalıştıran tek tek sanal kullanıcılar için oluşan hataları yalıtmak için Sanal Kullanıcı Etkinlik Grafiği'ni nasıl kullanacağınızı öğreneceksiniz.

Sanal Kullanıcı Etkinlik Grafiği, yük testinizle ilişkili sanal kullanıcı etkinliğini görselleştirmenize olanak tanır. Grafikteki her satır tek bir sanal kullanıcıyı temsil eder. Sanal Kullanıcı Etkinlik Grafiği, her sanal kullanıcının test sırasında tam olarak ne yaptığını gösterir. Bu, kullanıcı etkinliği, yükleme desenleri, başarısız veya yavaş testleri ilişkilendirme ve diğer sanal kullanıcı etkinliği ile isteklerini görerek performans sorunlarını yalıtmak sağlar. Sanal Kullanıcı Etkinlik Grafiği, yalnızca yükleme çalışmaya bittikten sonra kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio Enterprise

- Bu yordamları tamamlayın:

  - [Bir web performans testi kaydedin ve çalıştırın.](/azure/devops/test/load-test/run-performance-tests-app-before-release#recordtests)

  - [Yük testi oluşturma ve çalıştırma](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-load-test)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Önceki walkthroughs oluşturulan ColorWebApp çözümünü açın

1. Visual Studio'yu açın.

2. *LoadTest1.loadtest*içeren **ColorWebApp** çözümlerini açın. Bu yük testi, önkoşullar bölümünde bu konunun başında listelenen üç gözden geçirme adımının yürütülmesinden kaynaklanır.

     Bu izlenecek yoldaki kalan adımlar ColorWebApp adlı bir web uygulaması, *ColorWebAppTest.webtest* adlı bir web performans testi ve *LoadTest1.loadtest*adlı bir yük testi varsayalım.

## <a name="run-the-load-test"></a>Yük testini çalıştırın

Sanal kullanıcı etkinliği verilerini toplamak için yük testinizi çalıştırın.

- Yük **Testi Düzenleyicisi'nde**araç çubuğundaki **Çalıştır** düğmesini seçin. LoadTest1 çalıştırmaya başlar.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Sanal Kullanıcı Etkinlik Grafiği'ndeki sorunları yalıtma

Yük testinizi çalıştırdıktan ve sanal kullanıcı etkinlik verilerini topladıktan sonra, **Sanal Kullanıcı Etkinlik Grafiği'ndeki**Yük **Testi Çözümleyici** Ayrıntıları görünümünü kullanarak yük testi sonuçlarındaki verileri görüntüleyebilirsiniz. Ayrıca, yük testinizdeki performans sorunlarını yalıtmaya yardımcı olmak için **Sanal Kullanıcı Etkinlik Grafiği'ni** kullanabilirsiniz.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Yük testi sonuçlarınızda Sanal Kullanıcı Etkinlik Grafiği'ni kullanmak için

1. Yük testi nin çalışması tamamlandıktan sonra, yük testi sonuçlarının **Özeti** sayfası **Yük Testi Çözümleyicisi'nde**görüntülenir. Araç çubuğundaki **Grafikler** düğmesini seçin.

     Grafikler görünümü görüntülenir.

2. Sayfa **Yanıt Süresi** grafiğinde, eşik ihlali simgelerinden birinin yakınına sağ tıklayın ve **kullanıcı ayrıntısına git'i**seçin.

    > [!NOTE]
    > Kullanıcı Etkinliği grafiğini de açmak için **Yükle Test Düzenleyicisi** araç çubuğundaki **Ayrıntılar** düğmesini kullanabilirsiniz. Ancak, **Kullanıcı ayrıntısına Git** seçeneğini kullanırsanız, **Sanal Kullanıcı Etkinlik Grafiği,** testin grafikte sağ tıkladığınız kısmını otomatik olarak yakınlaştırır.

     Ayrıntılar görünümü, eşik ihlallerinin gerçekleştiği döneme odaklanan **Sanal Kullanıcı Etkinlik Grafiği** ile görüntülenir.

     y ekseninde, yatay çizimler tek tek sanal kullanıcıları temsil eder. X ekseni yük testi çalışması için zaman çizgisini görüntüler.

3. **Sanal Kullanıcı Etkinlik Grafiği'nin**altındaki **zaman dilimini yakınlaştırma** aracında, her ikisi de eşik ihlali simgesine yakın olana kadar sol ve sağ kaydırıcıları ayarlayın. Bu, Sanal Kullanıcı **Etkinlik Grafiği'ndeki** zaman ölçeğini değiştirir

4. Ayrıntılar **Gösterge'sinde** **,(Hataları vurgulayın)** için onay kutusunu seçin. Eşik ihlaline neden olan sanal kullanıcının vurgulandığına dikkat edin.

5. Filtre **sonuçları** panelinde, **başarılı sonuçları ve** **HttpError** için onay kutularını temizleyin, ancak **Doğrulama Kuralı Hatası** onay kutusunu seçili bırakın.

     **Sanal Kullanıcı Etkinlik Grafiği,** önceki gözden geçirmede yapılandırılan eşik ihlalinde belirtildiği gibi yalnızca *Red.aspx* sayfasında 3 saniyeden fazla zaman geçiren sanal kullanıcıları görüntüler.

6. Fare işaretçisini, eşik ihlali için doğrulama kuralı hatası yla sanal kullanıcıyı temsil eden yatay çizginin üzerinde dinlendirin.

7. Bir araç ipucu aşağıdaki bilgilerle görüntülenir:

    - **Kullanıcı Kimliği**

    - **Senaryo**

    - **Test**

    - **Sonuç**

    - **Ağ**

    - **Başlangıç Saati**

    - **Süre**

    - **Aracı**

    - **Test günlüğü**

8. Test **günlüğünün** bir bağlantı olduğuna dikkat edin. Test **günlüğü** bağlantısını seçin.

9. Günlükle ilişkili ColorWebTest web performans testi **Web Performans Testi Sonuçları Görüntüleyici'de**açılır. Bu, eşik ihlallerinin oluştuğu yeri yalıtmanızı sağlar.

     Performans sorunlarını ve yük testlerinizdeki hataları yalıtmaya yardımcı olmak için **hem Ayrıntı Göstergesi** hem de Filtre **sonuçları** panellerinde çeşitli ayarları kullanabilirsiniz. Sanal kullanıcı verilerinin **Sanal Kullanıcı Etkinlik Grafiği'nde**nasıl sunulduğunu görmek için bu ayarları ve **zaman dilimini yakınlaştırma** aracıyla denemeler yapın.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılar görünümünde sanal kullanıcı etkinliğini analiz edin](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Nasıl? Dağıtılmış yük testi için test ayarı oluşturma](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
- [Test ayarlarını kullanarak tanılama bilgilerini toplama](../test/collect-diagnostic-information-using-test-settings.md)
