---
title: Yük testleri için Sanal Kullanıcı etkinliği grafiğini kullanma
description: Yük testinizi çalıştıran tekil sanal kullanıcılar için oluşan hataları yalıtmak üzere sanal kullanıcı etkinliği grafiğini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 393c06f5526a0167661d6a181b81fee681a75969cb64ff3e7339f0ec2524234c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384580"
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>İzlenecek yol: sorunları yalıtmak için Sanal Kullanıcı etkinliği grafiğini kullanma

Bu kılavuzda, yük testinizi çalıştıran tekil sanal kullanıcılar için oluşan hataları yalıtmak üzere sanal kullanıcı etkinliği grafiğini nasıl kullanacağınızı öğreneceksiniz.

Sanal Kullanıcı etkinliği grafiği, yük testinizdeki ilişkili sanal kullanıcı etkinliğini görselleştirmenize olanak tanır. Grafikteki her satır, tek bir sanal kullanıcıyı temsil eder. Sanal Kullanıcı etkinliği grafiği, her bir sanal kullanıcının test sırasında hangi şekilde yürüttüğünü gösterir. Bu, Kullanıcı etkinliği desenlerini, yük düzenlerini ve başarısız veya yavaş testleri ilişkilendirmek ve diğer Sanal Kullanıcı etkinliğiyle istekleri görmek için performans sorunlarını yalıtmanızı sağlar. Sanal Kullanıcı etkinliği grafiği, yalnızca sonrasında yük çalıştırıldıktan sonra kullanılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio Enterprise

- Aşağıdaki yordamları uygulayın:

  - [Bir Web performans testini kaydedin ve çalıştırın](/azure/devops/test/load-test/run-performance-tests-app-before-release#recordtests).

  - [Yük testi oluşturma ve çalıştırma](/azure/devops/test/load-test/run-performance-tests-app-before-release#create-a-load-test)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Önceki izlenecek yollarda oluşturulan ColorWebApp çözümünü açın

1. Visual Studio'yu açın.

2. *LoadTest1. LoadTest* içeren **ColorWebApp** çözümünü açın. Bu yük testi, Önkoşullar bölümünde konunun başlangıcında listelenen üç izlenecek yoldaki adımları yürütmektedir.

     Bu yönergedeki geri kalan adımlarda, *ColorWebAppTest. webtest* adlı bir Web performans testi ve *LoadTest1. LoadTest* adlı bir yük testi olan ColorWebApp adlı bir Web uygulaması varsayılır.

## <a name="run-the-load-test"></a>Yük testini çalıştırma

Sanal Kullanıcı etkinliği verilerini toplamak için yük testinizi çalıştırın.

- **Yük Testi Düzenleyicisi**, araç çubuğundaki **Çalıştır** düğmesini seçin. LoadTest1 çalışmaya başlar.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Sanal Kullanıcı etkinliği grafiğindeki sorunları yalıtma

Yük testinizi çalıştırdıktan ve Sanal Kullanıcı etkinliği verilerini topladıktan sonra, **Sanal Kullanıcı etkinliği grafiğindeki** **Yük Testi Çözümleyicisi** ayrıntıları görünümünü kullanarak yük testi sonuçlarındaki verileri görüntüleyebilirsiniz. Ayrıca, **Sanal Kullanıcı etkinliği grafiğini** , yük testinizdeki performans sorunlarını yalıtmaya yardımcı olmak için kullanabilirsiniz.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>Yük testi sonuçlarınızda Sanal Kullanıcı etkinliği grafiğini kullanmak için

1. Yük testinin çalışmasını tamamladıktan sonra, yük testi sonuçlarına ilişkin **Özet** sayfası, **Yük Testi Çözümleyicisi**'nde görüntülenir. Araç çubuğundaki **grafikler** düğmesini seçin.

     Grafikler görünümü görüntülenir.

2. **Sayfa yanıt süresi** grafiğinde eşik ihlali simgelerinden birine sağ tıklayın ve **Kullanıcı ayrıntısına git**' i seçin.

    > [!NOTE]
    > Kullanıcı etkinliği grafiğini de açmak için **Yük Testi Düzenleyicisi** araç çubuğundaki **Ayrıntılar** düğmesini kullanabilirsiniz. Bununla birlikte, **Kullanıcı ayrıntısına git** seçeneğini kullanırsanız, **Sanal Kullanıcı etkinliği grafiği** , grafikte sağ tıklattığınız testin kısmına otomatik olarak yakınlaştıracaktır.

     Ayrıntılar görünümü, eşik ihlallerinin gerçekleştiği zaman dilimine odaklanan **Sanal Kullanıcı etkinliği grafiği** ile birlikte görüntülenir.

     Y ekseninde yatay çizimler tek tek sanal kullanıcıları temsil eder. X ekseni, yük testi çalıştırmasının zaman satırını görüntüler.

3. **Sanal Kullanıcı Etkinlik grafiğinin** altındaki **zaman dilimini Yakınlaştır** aracında, her ikisi de eşik ihlali simgesine kapatılana kadar sol ve sağ kaydırıcıları ayarlayın. Bu, **Sanal Kullanıcı Etkinlik grafiğinde** zaman ölçeğini değiştirir

4. **Ayrıntılar göstergesinde**, **(hataları vurgula)** onay kutusunu seçin. Eşik ihlaline neden olan sanal kullanıcı vurgulandığını unutmayın.

5. **Filtre sonuçları** panelinde, **başarılı sonuçları göster** ve **HttpError** onay kutularını temizleyin, ancak **ValidationRuleError** onay kutusunu seçili bırakın.

     **Sanal Kullanıcı etkinliği grafiği** , yalnızca *kırmızı. aspx* sayfasında 3 saniyeden daha fazla geçen sanal kullanıcıları görüntüler ve bu, önceki kılavuzda yapılandırılan eşik ihlaline göre belirlenir.

6. Fare işaretçisini, eşik ihlali için doğrulama kuralı hatası ile sanal kullanıcıyı temsil eden yatay çizginin üzerinde bekletin.

7. Aşağıdaki bilgilerle bir araç ipucu görüntülenir:

    - **Kullanıcı Kimliği**

    - **Senaryo**

    - **Test**

    - **Sonucu**

    - **Ağ**

    - **Başlangıç Zamanı**

    - **Süre**

    - **Aracı**

    - **Test günlüğü**

8. **Test günlüğünün** bir bağlantı olduğunu unutmayın. **Test günlüğü** bağlantısını seçin.

9. Günlük ile ilişkili ColorWebTest Web performans testi **Web performans test sonuçları görüntüleyicisinde** açılır. Bu, eşik ihlallerinin nerede oluştuğunu yalıtmanızı sağlar.

     Performans sorunlarını yalıtmaya yardımcı olmak için **Ayrıntılar göstergesinde** ve **filtre sonuçları** panellerinde çeşitli ayarları kullanabilir ve yük testlerinizdeki hataları izleyebilirsiniz. Sanal Kullanıcı verilerinin **Sanal Kullanıcı Etkinlik grafiğinde** nasıl sunulduğunu görmek için bu ayarları ve **zaman dilimi yakınlaştırma** aracını deneyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıntılar görünümündeki sanal kullanıcı etkinliğini çözümleme](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Nasıl yapılır: dağıtılmış yük testi için test ayarı oluşturma](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
- [Test ayarlarını kullanarak tanılama bilgilerini topla](../test/collect-diagnostic-information-using-test-settings.md)
