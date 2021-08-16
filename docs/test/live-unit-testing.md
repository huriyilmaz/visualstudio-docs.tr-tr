---
title: Live Unit Testing
description: Desteklenen çerçeveler ve Live Unit Testing yapılandırma dahil olmak üzere uygulama geliştirme sırasındaki diğer Live Unit Testing.
ms.custom: SEO-VS-2020
ms.date: 04/07/2020
ms.topic: how-to
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: e26fe6aceeb08ad4c46411adda2a7c6d628de19e7ae386ff7b1b88b3bf16d70e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121441241"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Live Unit Testing'yi yapılandırma ve kullanma

Bir uygulama geliştirilirken, Live Unit Testing birim testlerini arka planda otomatik olarak çalıştırır ve sonuçları ve kod kapsamayı gerçek zamanlı olarak sunar. Siz kodunuzu değiştirirken, Live Unit Testing değişikliklerinizin mevcut testleri nasıl etkileyene ve eklenen yeni kodun bir veya daha fazla mevcut testin kapsamında olup olmadığı hakkında geri bildirim sağlar. Bu size hata düzeltmeleri yaparken veya yeni özellikler eklerken birim testleri yazmanız anımsatıyor.

> [!NOTE]
> Live Unit Testing, .NET Core'Visual Basic hedef alan C# ve .NET Framework projeleri için Enterprise sürümü Visual Studio.

Testlerinizi Live Unit Testing, testlerinin durumuyla ilgili verileri kalıcı olarak kullanır. Kalıcı verilerin kullanımı, Live Unit Testing değişikliklerine yanıt olarak testlerinizi dinamik olarak çalıştırma sırasında üstün performans sunabilirsiniz.

## <a name="supported-test-frameworks"></a>Desteklenen test çerçeveleri

Live Unit Testing, aşağıdaki tabloda listelenen üç popüler birim testi çerçevesiyle birlikte çalışır. Bağdaştırıcılarının ve çerçevelerinin desteklenen en düşük sürümü de gösterilir. Birim testi çerçeveleri NuGet.org adresinden edinebilirsiniz.

|Test Çerçevesi  |Visual Studio Bağdaştırıcı en düşük sürümü  |Çerçeve en düşük sürümü  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio sürüm 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter sürüm 3.5.1 |NUnit sürüm 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Microsoft.VisualStudio.QualityTools.UnitTestFramework'e başvurulan eski MSTest tabanlı test projeleriniz varsa ve daha yeni MSTest NuGet paketlerine taşımak zorunda değilsanız, Visual Studio 2019 veya Visual Studio 2017'ye yükseltin.

Bazı durumlarda, proje tarafından başvurulan NuGet paketlerin çalışması için açıkça geri Live Unit Testing gerekir. Bunu yapmak için çözümün açık bir derlemesini (üst düzey Visual Studio menüsünden Çözümü Yeniden Derleme'yi seçin) veya çözümde paketleri geri yükleyerek (çözüme sağ tıklayın ve Geri Yükle'yi NuGet Packages seçeneğini  >   **belirleyin)** yapabilirsiniz.

## <a name="configure"></a>Yapılandırma

Üst Live Unit Testing **menü** çubuğundan Araçlar Seçenekleri'ni Visual Studio ve ardından Seçenekler iletişim kutusunun sol bölmesinde Live Unit Testing'yi seçerek bu seçeneği  >   **belirleyin.** 

> [!TIP]
> Bu Live Unit Testing etkinleştirildikten sonra (sonraki bölüme bakın, Başlat, duraklat ve [Live Unit Testing),](#start-pause-and-stop)Seçenekler iletişim kutusunu Açmak için **Test**  Seçenekleri'Live Unit Testing  >    >  **açabilirsiniz.**

Aşağıdaki görüntüde iletişim kutusunda Live Unit Testing yapılandırma seçenekleriyle ilgili bilgiler ve bilgiler yer alıyor:

![Live Unit Testing yapılandırma seçenekleri](./media/lut-options.png)

Yapılandırılabilir seçenekler şunlardır:

- Bir Live Unit Testing ve hata ayıklaması olduğunda bu sorunun duraklatıp duraklatmayıp duraklatmayılır.

- Sistemin pil Live Unit Testing belirtilen eşiğin altına düştüğünde sistemin duraklatıp duraklatılamayyıp çalışmay olmadığı.

- Çözüm Live Unit Testing otomatik olarak çalıştırıp çalıştırmama.

- Hata ayıklama sembolünü ve XML belge açıklaması oluşturmanın etkinleştirip etkinleştirmey olmadığı.

- Kalıcı verilerin depolan olduğu dizin.

- Kalıcı olan tüm verileri silme özelliği. Bu, Live Unit Testing tahmin edilemeyen veya beklenmeyen bir şekilde davranış gösterir ve bu da kalıcı verilerin bozulmuş olduğunu gösterir.

- Test sonrasındaki zaman aralığı. Varsayılan değer 30 saniyedir.

- En fazla test işlemi sayısı Live Unit Testing.

- Bu işlemlerin tükettiği Live Unit Testing bellek miktarı.

- Çıkış penceresine yazılan Live Unit Testing **düzeyi.**

   Seçenekler günlüğe kaydetme yok (**Yok),** yalnızca hata iletileri (**Hata),** hata ve bilgilendirme iletileri (**Bilgi**, varsayılan) veya tüm ayrıntıları ( Ayrıntılı )**içerir.**

   Ayrıca, adlı kullanıcı düzeyinde bir ortam değişkenine "1" değeri ataarak ve ardından Live Unit Testing'yi yeniden başlatarak da ayrıntılı çıktıyı  `VS_UTE_DIAGNOSTICS` Visual Studio.

   Bir dosyada MSBuild günlük iletilerini Live Unit Testing için, kullanıcı düzeyi ortam değişkenlerini günlüğü içeren `LiveUnitTesting_BuildLog` dosyanın adına ayarlayın.

## <a name="start-pause-and-stop"></a>Başlatma, duraklatma ve durdurma

Bu Live Unit Testing üst düzey **Live Unit Testing**  >    >  **Başlat'ı** seçerek test Visual Studio seçin. Bu Live Unit Testing etkinleştirildiğinde, Live Unit Testing menüsündeki  seçenekler tek bir öğe (Başlat) olarak değiştirildiğinde **Duraklat** ve Durdur **olarak** **değişir:**

- **Duraklatma** geçici olarak geçici olarak Live Unit Testing.

  Bir Live Unit Testing duraklatılırsa, kapsam görselleştirmesi düzenleyicide görünmez, ancak toplanan tüm veriler korunur. Bu Live Unit Testing devam etmek için **Devam'ı** seçin Live Unit Testing seçin. Live Unit Testing duraklatılırken yapılan tüm düzenlemeleri yakalamak ve uygun şekilde güncelleştirme yapmak için gerekli çalışmaları yapar.

- **Durdurma işlemi** tamamen Live Unit Testing. Live Unit Testing topladığı tüm verileri atar.

> [!NOTE]
> Birim testi Live Unit Testing bir çözümde başlatmaya başlarsanız, Live Unit Testing menüsünde  Duraklat ve Durdur  seçenekleri görünür ancak Live Unit Testing başlamaz.  Çıkış **penceresinde** "Bu çözüm tarafından desteklenen test bağdaştırıcılarına başvurulmadı..." şeklinde bir ileti görüntülenir.

Herhangi bir zamanda, bu hizmeti geçici olarak duraklatabilir veya tamamen Live Unit Testing. Örneğin, yeniden düzenlemenin ortasındaysanız ve testlerinizi bir süre bozuk olacağını biliyorsanız bunu yapmak istiyor olabilirsiniz.

## <a name="view-coverage-visualization"></a>Kapsam görselleştirmesini görüntüleme

Etkinleştirildikten sonra Live Unit Testing, Visual Studio düzenleyicide kod satırlarından her biri, yazdığın kodun birim testlerinin kapsamına alınıp alınmay olmadığını gösterecek şekilde Visual Studio düzenleyicisinde her kod satırı etkinleştirilmiş olur Aşağıdaki görüntüde hem geçen hem de başarısız olan testlere sahip kod satırlarının yanı sıra testlerin kapsamında yer alan kod satırları da yer alelaceledir. Yeşil "×" ile dekore edilmiş çizgiler yalnızca testlerden geçerek, kırmızı "x" ile dekore edilmiş çizgiler bir veya daha fazla başarısız test kapsamındadır ve mavi "➖" ile dekore edilmiş çizgiler hiçbir test kapsamında değildir.

![Visual Studio'de kod kapsamı](./media/lut-codewindow.png)

Live Unit Testing kapsamı görselleştirmesi, kod düzenleyicisinde kod değiştirdiğinde hemen güncelleştirilir. Düzenlemeler işleme sırasında görselleştirme, aşağıdaki görüntüde gösterilen şekilde, geçiş, başarısız ve kaplanmış sembollerin altına yuvarlak süreölçer görüntüsü ekleyerek verilerin güncel olmadığını belirtmek için değişir.

![Zamanlayıcı simgesi Visual Studio kod kapsamı](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Test durumu hakkında bilgi al

Kod penceresinde başarılı veya başarısız sembolünü üzerine gelerek bu satıra kaç test isabet edeni görebilirsiniz. Tek tek testlerin durumunu görmek için simgesini seçin:

![Visual Studio'da bir simgenin durumunu test Visual Studio](./media/lut-failedinfo.png)

Araç ipucu, testlerin adlarını ve sonucu sağlamanın yanı sıra test kümesinde yeniden çalıştırma veya hata ayıklama da sağlar. Araç ipucunda bir veya daha fazla test seçersiniz, yalnızca bu testleri de çalıştırabilirsiniz veya hata ayıkabilirsiniz. Bu, kod penceresinden ayrılmak zorunda kalmadan testlerde hata ayıklamanıza olanak sağlar. Hata ayıklarken, önceden ayarlamış olabilir herhangi bir kesme noktası gözlemleye ek olarak, hata ayıklayıcı beklenmeyen bir sonuç döndüren bir yöntem yürütürken program yürütme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> duraklatılır.

Araç ipucunda başarısız bir testin üzerine gelindiğinde, aşağıdaki görüntüde gösterildiği gibi hata hakkında ek bilgi sağlamak için genişletildi. Doğrudan başarısız olan bir teste gitmek için araç ipucunda bu teste çift tıklayın.

![Visual Studio'da test araç ipucu bilgileri başarısız oldu](./media/lut-failedmsg.png)

Başarısız teste gidilen zaman, Live Unit Testing aşağıdaki testlerin yöntem imzasını görsel olarak gösterir:

- geçirildi (yeşil "")" ile birlikte yarı dolu bir beaker ile gösterilen
- başarısız (kırmızı " ile birlikte yarı dolu bir beaker 🞩 )
- (mavi "Live Unit Testing" ile birlikte yarı renkli bir beaker) ➖

Test dışı yöntemler bir sembolle birlikte dekore edilmiş değildir. Aşağıdaki görüntüde dört yöntem türü de göstermektedir.

![Geçiş veya Visual Studio ile test yöntemleri](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Test hatalarını tanılama ve düzeltme

Başarısız testten ürün kodunda kolayca hata ayıklayabilirsiniz, düzenlemeler yapabilirsiniz ve uygulama geliştirmeye devam edersiniz. Arka Live Unit Testing çalıştırılana kadar, hata ayıklama, düzenleme ve devam etme döngüsü Live Unit Testing yeniden başlatmanız ve durdurmanız gerek yok.

Örneğin, önceki görüntüde gösterilen test hatasının nedeni, test yönteminde alfabetik olmayan karakterlerin yöntemine geçirilen yanlış `true` bir <xref:System.Char.IsLower%2A?displayProperty=fullName> varsayımdan kaynaklanır. Test yöntemini düzelttikten sonra tüm testlerin geçmesi gerekir. Bu hizmeti duraklatma veya durdurma Live Unit Testing.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Test Gezgini

**Test Gezgini,** testleri çalıştırmaya, testlerde hata ayıklamaya ve test sonuçlarını analiz etmenize olanak sağlayan bir arabirim sağlar. Live Unit Testing Test Gezgini ile **tümleştirilmiştir.** Test Live Unit Testing etkinleştirilmediyse veya durdurulmuşsa, Test Gezgini bir **testin** son çalıştırıisinde birim testlerinin durumunu görüntüler. Kaynak kodu değişiklikleri, testleri yeniden çalıştırmanız gerektirir. Buna karşılık, Live Unit Testing, Test Gezgini'nde birim testlerinin **durumu hemen** güncelleştirilir. Birim testlerini açıkça çalıştırmaya gerek yok.

> [!TIP]
> Üst **Live Unit Testing** üst düzey Windows  >    >  **Test Gezgini'ni** seçerek test Visual Studio açın.

Test Gezgini penceresinde **bazı testlerin** soluk olduğunu görebilirsiniz. Örneğin, daha önce Live Unit Testing bir projeyi açtıktan sonra test penceresini etkinleştirdikten sonra, aşağıdaki görüntüde olduğu gibi **Test** Gezgini penceresi başarısız olan test dışında tüm görüntüler soluk görüntüye açıldı. Bu durumda, Live Unit Testing testi yeniden çalıştırdı ama başarılı testleri yeniden çalıştırmadı. Bunun nedeni Live Unit Testing kalıcı veriler, testlerin son çalıştırması başarıyla çalıştırılana kadar hiçbir değişiklik olmadığını gösterir.

![Test Gezgini'nde başarısız test](media/lut-test-explorer.png)

Test Gezgini menüsünden Hepsini Çalıştır veya Çalıştır seçeneklerini  seçerek soluk **görünen** testleri **yeniden çalıştırabilirsiniz.** Ya da, **Test** Gezgini menüsünde bir veya daha fazla test  seçin,  sağ tıklayın ve ardından açılan menüden Seçili Testleri Çalıştır veya Seçili Testlerde Hata Ayıkla'yı seçin. Testler çalıştırılırken en üstte kabarcığı olur.

Test sonuçlarını otomatik olarak çalıştırma Live Unit Testing test gezgininden açıkça çalıştırma arasında bazı **farklar vardır.** Bu farklar şunlardır:

- Test Gezgini penceresinden testleri çalıştırma veya hata ayıklama normal ikililer çalıştırırken, Live Unit Testing ikililer çalıştırır.
- Live Unit Testing, testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, varsayılan etki alanındaki testleri çalıştırır. Test Gezgini penceresinden **çalıştır olunan** testler yeni bir uygulama etki alanı oluştur.
- Live Unit Testing her test derlemesinde testleri sırayla çalıştırır. Test **Gezgini penceresinde** birden çok testi paralel olarak çalıştırmayı seçebilirsiniz.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Live Unit Testing penceresi

**Live Unit Testing,** **Test** Gezgini'ne benzer şekilde, testleri çalıştırmaya, testlerde hata ayıklamaya ve test sonuçlarını analiz etmenize olanak sağlayan bir arabirim sağlar. Bu Live Unit Testing etkinleştirildiğinde, Test Gezgini'nde birim **testlerinin durumu** hemen güncelleştirilir. Birim testlerini açıkça çalıştırmaya gerek yok. Bir Live Unit Testing etkin değilken veya **durdurulursa, Live Unit Testing** testlerin durumunu testlerin son çalıştır zamanı görüntüler. Testleri yeniden Live Unit Testing yeniden çalıştırmanız için bir kaynak kodu değişikliği gerekir.

> [!TIP]
> Üst Live Unit Testing **menüsünden Test**  >  **Live Unit Testing**  >  **Başlat'ı** seçerek Visual Studio başlatabilirsiniz. Ayrıca, Görünüm Diğer **Live Unit Testing** penceresini kullanarak da **Windows**  >    >  **Live Unit Testing açabilirsiniz.**

Bu pencerede Live Unit Testing **testlerin** soluk olduğunu görebilirsiniz. Örneğin, aşağıdaki görüntüde Live Unit Testing yeniden **Live Unit Testing** penceresi tüm testleri soluk gösterir. Soluk gösterilen test sonuçları, testin en son Live Unit Test çalıştırması kapsamında olmadığını gösteriyor. Testler yalnızca testte bir değişiklik algılandığında veya test bağımlılıkları algılandığında dolar. Değişiklik yoksa, testi gereksiz yere çalıştırmayı önler. Bu durumda, gri renkli test sonucu hala "günceldir" ancak en son çalıştırmanın parçası değildir.

![Test Gezgini'nde soluk testler](media/vs-2019/lut-test-explorer.png)

Kod değişikliği yaparak soluk görünen tüm testleri yeniden çalıştırabilirsiniz.

Test sonuçlarını otomatik olarak çalıştırma Live Unit Testing test gezgininden açıkça çalıştırma arasında bazı **farklar vardır.** Bu farklar şunlardır:

- Test Gezgini penceresinden testleri çalıştırma veya hata ayıklama normal ikililer çalıştırırken, Live Unit Testing ikililer çalıştırır.
- Live Unit Testing, testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, varsayılan etki alanındaki testleri çalıştırır. Test Gezgini penceresinden **çalıştır olunan** testler yeni bir uygulama etki alanı oluştur.
- Live Unit Testing her test derlemesinde testleri sırayla çalıştırır. Test **Gezgini penceresinde** birden çok testi paralel olarak çalıştırmayı seçebilirsiniz.
::: moniker-end

## <a name="large-solutions"></a>Büyük çözümler

Çözümde 10 veya daha fazla proje Visual Studio aşağıdaki iletişim kutusu görüntülenir:

- başlatma Live Unit Testing ve kalıcı veri yok
- Kalıcı **Verileri**  >  **Silmek**  >  **Live Unit Testing** Araçlar  >  **Seçenekleri'ne tıklayın**

![Live Unit Testing projeler için iletişim kutusu](media/lut-large-project.png)

İletişim kutusu, büyük projelerde çok sayıda testin dinamik olarak yürütülmesinin performansı ciddi ölçüde etkileyeceni konusunda sizi uyarıyor. Tamam 'ı **seçer** Live Unit Testing çözümde tüm testleri yürütür. **İptal'i seçerse** yürütülecek testleri seçin. Aşağıdaki bölümde bunun nasıl gerçekleştir adımları açık bir şekilde açık almaktadır.

## <a name="include-and-exclude-test-projects-and-test-methods&quot;></a>Test projelerini ve test yöntemlerini dahil etmek ve hariç tutmak

Birçok test projesine sahip çözümler için, bir projede yer alan projelerin ve tek tek yöntemlerin hangi projelerde ve Live Unit Testing. Örneğin, yüzlerce test projesine sahip bir çözümünüz varsa, bir dizi hedeflenen test projesine katılarak bu Live Unit Testing. Proje veya çözümde yer alan tüm testleri hariç tutmak, çoğu testi dahil etmek veya hariç tutmak ya da tek tek testleri dışlamak istemenize bağlı olarak bunu yapmak için çeşitli yollar vardır. Live Unit Testing dahil/dışlama durumunu kullanıcı ayarı olarak kaydeder ve bir çözüm kapatılan ve yeniden açılan zaman bunu anımsar.

### <a name=&quot;exclude-all-tests-in-a-project-or-solution&quot;></a>Proje veya çözümde tüm testleri dışlama

Birim testlerinde projeleri ayrı ayrı seçmek için, proje başlatıldıktan sonra Live Unit Testing yapın:

1. İlkeler menüsünde çözüme **sağ Çözüm Gezgini** ve **çözümün Live Unit Testing**  >  **dışlamak** için Dışla'yı seçin.
1. Testlere eklemek istediğiniz her test projesine sağ tıklayın ve Ekle'yi **Live Unit Testing**  >  **seçin.**

### <a name=&quot;exclude-individual-tests-from-the-code-editor-window&quot;></a>Tek tek testleri kod düzenleyicisi penceresinden dışlama

Tek tek test yöntemlerini dahil etmek veya hariç tutmak için kod düzenleyicisi penceresini kullanabilirsiniz. Kod düzenleyicisi penceresinde test yönteminin imzasına sağ tıklayın ve ardından aşağıdaki seçeneklerden birini belirleyin:

- **Live Unit Testing**  >  **Dahil \<selected method> Etmek**
- **Live Unit Testing**  >  **Dışla \<selected method>**
- **Live Unit Testing**  >  **Hariç Tut \<selected method>**

### <a name=&quot;exclude-tests-programmatically&quot;></a>Testleri program aracılığıyla hariç tut

özniteliğini yöntemleri, sınıfları veya yapıları program aracılığıyla kapsamlarını raporlamadan dışlamak için <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> Live Unit Testing.

Yöntemlerin tek tek dışlamalarını dışlamak için aşağıdaki öznitelikleri Live Unit Testing:

- xUnit için: `[Trait(&quot;Category&quot;, &quot;SkipWhenLiveUnitTesting")]`
- NUnit için: `[Category("SkipWhenLiveUnitTesting")]`
- MSTest için: `[TestCategory("SkipWhenLiveUnitTesting")]`

Test derlemelerinin tamamını bir derlemenin dışında tutmak için aşağıdaki öznitelikleri Live Unit Testing:

- xUnit için: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- NUnit için: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- MSTest için: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Ayrıca bkz.

- [Kod testi araçları](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing blog](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Live Unit Testing SSS](live-unit-testing-faq.yml)
- [Channel 9 videosu: Live Unit Testing'Visual Studio](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
