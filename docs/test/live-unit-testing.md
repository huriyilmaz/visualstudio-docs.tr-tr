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
ms.openlocfilehash: b9b78771c36dce26744ba74af63922cf1efa48e2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628101"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Live Unit Testing'i yapılandırma ve kullanma

Bir uygulama geliştirilirken, Live Unit Testing birim testlerini arka planda otomatik olarak çalıştırır ve sonuçları ve kod kapsamayı gerçek zamanlı olarak sunar. Kodunuzu değiştirirken, Live Unit Testing değişikliklerinizin mevcut testleri nasıl etkileyene ve eklenen yeni kodun bir veya daha fazla mevcut testin kapsamında olup olmadığı hakkında geri bildirim sağlar. Bu size hata düzeltmeleri yaparken veya yeni özellikler eklerken birim testleri yazmanız anımsatıyor.

> [!NOTE]
> Live Unit Testing, .NET Core'Visual Basic veya .NET Framework'ın Enterprise sürümünü hedef alan C# ve Visual Studio.

Testlerinizi Live Unit Testing, testlerinin durumuyla ilgili verileri kalıcı olarak kullanır. Kalıcı verilerin kullanımı, Live Unit Testing değişikliklerine yanıt olarak testlerinizi dinamik olarak çalıştırma sırasında üstün performans sunabilirsiniz.

## <a name="supported-test-frameworks"></a>Desteklenen test çerçeveleri

Live Unit Testing, aşağıdaki tabloda listelenen üç popüler birim testi çerçevesiyle birlikte çalışır. Bağdaştırıcılarının ve çerçevelerinin desteklenen en düşük sürümü de gösterilir. Birim testi çerçeveleri NuGet.org adresinden edinebilirsiniz.

|Test Çerçevesi  |Visual Studio Bağdaştırıcı en düşük sürümü  |Çerçeve en düşük sürümü  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio sürüm 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter sürüm 3.5.1 |NUnit sürüm 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Microsoft.VisualStudio.QualityTools.UnitTestFramework'e başvurulan eski MSTest tabanlı test projeleriniz varsa ve yeni MSTest NuGet paketlerine taşımak zorunda değilsanız, Visual Studio 2019 veya Visual Studio 2017'ye yükseltin.

Bazı durumlarda, proje tarafından başvurulan NuGet paketlerin çalışması için açıkça geri Live Unit Testing gerekir. Bunu, çözümün açık bir derlemesini yaparak (üst düzey Visual Studio menüsünden Çözümü Yeniden Derleme'yi seçin) veya çözümde paketleri geri yükleyerek (çözüme sağ tıklayın ve Geri  >   **Yükle'yi** seçin) NuGet Yapabilirsiniz.

## <a name="configure"></a>Yapılandırma

Üst Live Unit Testing menü çubuğundan Araçlar Seçenekleri'ni Visual Studio ve ardından Seçenekler iletişim kutusunun sol bölmesinde Live Unit Testing'yi seçerek bu seçeneği  >   **belirleyin.** 

> [!TIP]
> Bu Live Unit Testing etkinleştirildikten sonra (sonraki bölüme bakın, [Başlat,](#start-pause-and-stop)duraklatma ve durdurma  Live Unit Testing), Seçenekler iletişim kutusunu Da Aç'ı **seçerek Test** Live Unit Testing  >    >  **açabilirsiniz.**

Aşağıdaki görüntüde, iletişim Live Unit Testing yapılandırma seçeneklerinin nasıl görüntüll olduğu gösterir:

![Live Unit Testing yapılandırma seçenekleri](./media/lut-options.png)

Yapılandırılabilir seçenekler şunlardır:

- Bir Live Unit Testing ve hata ayıklarken bu sorunun duraklatıp duraklatmayıp duraklatılamay olmadığı.

- Sistemin pil Live Unit Testing belirtilen eşiğin altına düştüğünde sistemin duraklatıp duraklatılamayyıp çalışmay olmadığı.

- Çözüm Live Unit Testing otomatik olarak çalıştırıp çalıştırmama.

- Hata ayıklama sembolünü ve XML belge açıklaması oluşturmanın etkinleştirip etkinleştirmey karara varmamasına dikkat edin.

- Kalıcı verilerin depolan olduğu dizin.

- Kalıcı olan tüm verileri silme özelliği. Bu, Live Unit Testing tahmin edilemeyen veya beklenmeyen bir şekilde davranış gösteriyorsa ve bu da kalıcı verilerin bozulmuş olduğunu gösterir.

- Test sonrasındaki zaman aralığı. Varsayılan değer 30 saniyedir.

- En fazla test işlemi sayısı Live Unit Testing.

- Bu işlemlerin tükettiği Live Unit Testing bellek miktarı.

- Çıkış penceresine yazılan Live Unit Testing **düzeyi.**

   Seçenekler arasında günlüğe kaydetme yok (**Yok),** yalnızca hata iletileri (**Hata),** hata ve bilgilendirme iletileri (**Bilgi**, varsayılan) veya tüm ayrıntılar (**Ayrıntılı**).

   Ayrıca , adlı kullanıcı düzeyinde bir ortam  değişkenine "1" değeri ataarak ve ardından bu değeri yeniden başlatarak Live Unit Testing Çıktı penceresinde ayrıntılı çıkışı `VS_UTE_DIAGNOSTICS` Visual Studio.

   Bir dosyada MSBuild günlük iletilerini Live Unit Testing için kullanıcı düzeyinde ortam değişkenlerini, günlüğü içeren `LiveUnitTesting_BuildLog` dosyanın adına ayarlayın.

## <a name="start-pause-and-stop"></a>Başlatma, duraklatma ve durdurma

Bu Live Unit Testing üst **düzey** Live Unit Testing  >    >  **Başlat'ı** seçin Visual Studio seçin. Bu Live Unit Testing etkinleştirildiğinde, Live Unit Testing menüsündeki  seçenekler tek bir öğe (Başlat) olarak değiştirildiğinde **Duraklat** ve Durdur **olarak** **değişir:**

- **Duraklatma** geçici olarak askıya Live Unit Testing.

  Bir Live Unit Testing duraklatılırsa, kapsam görselleştirmesi düzenleyicide görünmez, ancak toplanan tüm veriler korunur. Bu Live Unit Testing devam etmek **için,** Live Unit Testing seçin. Live Unit Testing duraklatılırken yapılan tüm düzenlemeleri yakalamak için gerekli çalışmaları yapar ve uygun şekilde glyph'leri ler.

- **Durdur tamamen** Live Unit Testing. Live Unit Testing topladığı tüm verileri atar.

> [!NOTE]
> Birim testi Live Unit Testing bir çözümde başlatmaya başlarsanız, Live Unit Testing menüsünde  Duraklat ve  Durdur seçenekleri görünür ancak Live Unit Testing başlamaz.  Çıkış **penceresinde** "Bu çözüm tarafından desteklenen test bağdaştırıcılarına başvurulmadı..." şeklinde bir ileti görüntülenir.

Herhangi bir zamanda, bu hizmeti geçici olarak duraklatabilir veya tamamen Live Unit Testing. Örneğin, yeniden düzenlemenin ortasındaysanız ve testlerinizi bir süre bozuk olacağını biliyorsanız bunu yapmak istiyor olabilirsiniz.

## <a name="view-coverage-visualization"></a>Kapsam görselleştirmesini görüntüleme

Etkinleştirildikten sonra Live Unit Testing, Visual Studio düzenleyicisinde kod satırlarından her biri, birim testlerinin kapsamına alınıp alınmay olmadığını gösterecek şekilde Visual Studio düzenleyicisinde her kod satırı etkinleştirilmiş olur. Aşağıdaki görüntüde hem geçen hem de başarısız olan testlere sahip kod satırlarının yanı sıra test kapsamında yer alan kod satırları da yer aleladedir. Yeşil "×" ile dekore edilmiş çizgiler yalnızca testlerden geçerek kapsıyor, kırmızı "x" ile dekore edilmiş çizgiler bir veya daha fazla başarısız test kapsamında ve mavi "➖" ile dekore edilmiş çizgiler hiçbir testin kapsamında değildir.

![Visual Studio'de kod kapsamı](./media/lut-codewindow.png)

Live Unit Testing kapsamı görselleştirmesi, kod düzenleyicisinde kod değiştirdiğinde hemen güncelleştirilir. Düzenlemeler işleme sırasında görselleştirme, aşağıdaki görüntüde gösterilen şekilde geçiş, başarısız ve kapsama altındaki sembollerin altına yuvarlak zamanlayıcı görüntüsü ekleyerek verilerin güncel olmadığını belirtmek için değişir.

![Zamanlayıcı simgesi Visual Studio kod kapsamı](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Test durumu hakkında bilgi al

Kod penceresinde başarılı veya başarısız sembolünü üzerine gelerek bu satıra kaç test isabet edeni görebilirsiniz. Tek tek testlerin durumunu görmek için simgesini seçin:

![Visual Studio'daki bir simgenin test Visual Studio](./media/lut-failedinfo.png)

Araç ipucu, testlerin adlarını ve sonucu sağlamanın yanı sıra test kümesinde yeniden çalıştırma veya hata ayıklama da sağlar. Araç ipucunda testlerden birini veya daha fazlasını seçerse, yalnızca bu testleri çalıştırabilirsiniz veya hata ayıkabilirsiniz. Bu, kod penceresinden ayrılmak zorunda kalmadan testlerde hata ayıklamanıza olanak sağlar. Hata ayıklarken, önceden ayarlamış olabilir herhangi bir kesme noktası gözlemleye ek olarak, hata ayıklayıcı beklenmeyen bir sonuç döndüren bir yöntem yürütürken program yürütme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> duraklatılır.

Araç ipucunda başarısız bir testin üzerine gelindiğinde, aşağıdaki görüntüde gösterildiği gibi hata hakkında ek bilgi sağlamak için genişletildi. Doğrudan başarısız olan bir teste gitmek için araç ipucunda bu teste çift tıklayın.

![Visual Studio'da test araç ipucu bilgileri başarısız oldu](./media/lut-failedmsg.png)

Başarısız teste gidilen zaman, Live Unit Testing aşağıdaki testlerin yöntem imzasını görsel olarak gösterir:

- geçirildi (yeşil "")ile birlikte yarı dolu bir beaker ile gösterilen
- başarısız (kırmızı " ile birlikte yarı dolu bir beaker 🞩 )
- bir Live Unit Testing (mavi "➖" ile birlikte)

Test dışı yöntemler bir sembolle birlikte dekore edilmiş değildir. Aşağıdaki görüntüde dört yöntem türü de göstermektedir.

![Geçiş veya Visual Studio ile test yöntemleri](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Test hatalarını tanılama ve düzeltme

Başarısız testten ürün kodunda kolayca hata ayıklayabilirsiniz, düzenlemeler yapabilirsiniz ve uygulama geliştirmeye devam edersiniz. Arka Live Unit Testing çalıştırılana kadar, hata ayıklama, düzenleme ve devam etme döngüsü Live Unit Testing yeniden başlatmanız ve durdurmanız gerek yok.

Örneğin, önceki görüntüde gösterilen test hatasının nedeni, test yönteminde alfabetik olmayan karakterlerin yöntemine geçirilen hatalı `true` bir <xref:System.Char.IsLower%2A?displayProperty=fullName> varsayımdan kaynaklanır. Test yöntemini düzelttikten sonra tüm testlerin geçmesi gerekir. Bu hizmeti duraklatma veya durdurma Live Unit Testing.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Test Gezgini

**Test Gezgini,** testleri çalıştırmaya, testlerde hata ayıklamaya ve test sonuçlarını analiz etmenize olanak sağlayan bir arabirim sağlar. Live Unit Testing Test Gezgini ile **tümleştirilmiştir.** Test Live Unit Testing etkinleştirilmediyse veya durdurulmuşsa, Test Gezgini bir **testin** son çalıştırılana kadar birim testlerinin durumunu görüntüler. Kaynak kodu değişiklikleri, testleri yeniden çalıştırmanız gerektirir. Buna karşılık, Live Unit Testing, Test Gezgini'nde birim testlerinin **durumu hemen** güncelleştirilir. Birim testlerini açıkça çalıştırmaya gerek yok.

> [!TIP]
>    >    >  üst düzey Visual Studio menüsünden test Windows test **gezgini** ' ni seçerek Live Unit Testing açın.

**Test Gezgini** penceresinde bazı testlerin sık kullanıma hazır olduğunu fark edebilirsiniz. Örneğin, daha önce kaydedilen bir projeyi açtıktan sonra Live Unit Testing etkinleştirdiğinizde, **Test Gezgini** penceresi, aşağıdaki görüntüde gösterildiği gibi, başarısız olan teste göre daha fazla zaman aşımına uğrar. Bu durumda, Live Unit Testing başarısız testi yeniden çalıştırmıştır, ancak başarılı testleri yeniden çalıştırmaz. Bunun nedeni Live Unit Testing kalıcı verilerinin, testlerin son kez başarıyla çalıştırılmasından bu yana hiçbir değişiklik olmadığını gösterir.

![Test Gezgininde başarısız test](media/lut-test-explorer.png)

**Test Gezgini** menüsünden **Tümünü Çalıştır** veya **Çalıştır** seçeneklerini belirleyerek, beliden görüntülenen tüm testleri yeniden çalıştırabilirsiniz. Ya da  **Test Gezgini** menüsünde bir veya daha fazla test seçin, sağ tıklayın ve ardından **Seçilen Testleri Çalıştır** veya açılan menüden **Seçili testlerin hatalarını ayıkla** ' yı seçin. Testler çalıştırıldığında, en üstteki kabarcılar.

Live Unit Testing otomatik olarak çalıştırma ve güncelleştirme, **Test Gezgini**'nden testleri açıkça çalıştırma arasında bazı farklılıklar vardır. Bu farklar şunlardır:

- Test Gezgini penceresinde testleri çalıştırmak veya hata ayıklamak, düzenli ikili dosyalar çalıştırlarken Live Unit Testing, işaretlenmiş ikililer çalıştırır.
- Live Unit Testing, testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, bunun yerine varsayılan etki alanından testleri çalıştırır. **Test Gezgini** penceresinden çalıştırılan testler yeni bir uygulama etki alanı oluşturur.
- Live Unit Testing her bir test derlemesindeki testleri sırayla çalıştırır. **Test Gezgini** penceresinde, paralel olarak birden çok test çalıştırmayı seçebilirsiniz.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Live Unit Testing penceresi

**Test Gezgini** ile benzer **Live Unit Testing**, testleri çalıştırmanıza ve hata ayıklamanıza ve test sonuçlarını çözümlemenize imkan tanıyan bir arabirim sağlar. Live Unit Testing etkinleştirildiğinde, **Test Gezgini** 'ndeki birim testlerinin durumu hemen güncelleştirilir. Birim testlerini açıkça çalıştırmanız gerekmez. Live Unit Testing etkinleştirilmediği veya durdurulduğunda, **Live Unit Testing** bir testin son çalıştırıldığı zaman birim testlerinin durumunu görüntüler. Live Unit Testing yeniden başlattıktan sonra, testleri yeniden çalıştırmak için bir kaynak kodu değişikliği gerekir.

> [!TIP]
>   >    >  en üst düzey Visual Studio menüsünden Test Live Unit Testing **başlat** seçeneğini belirleyerek Live Unit Testing başlatın. ayrıca,    >  **diğer Windows** görüntüle  >  **Live Unit Testing penceresini** kullanarak Live Unit Testing penceresini açabilirsiniz.

**Live Unit Testing** penceresinde bazı testlerin sık kullanıma hazır olduğunu fark edebilirsiniz. Örneğin, Live Unit Testing durdurup yeniden başlattığınızda, aşağıdaki görüntüde gösterildiği gibi, **Live Unit Testing** pencere tüm testleri soluklaştırır. Perded-Out test sonuçları, testin en son canlı birim testi çalıştırmasının bir parçası olmadığını gösterir. Testler yalnızca testteki bir değişiklik veya testin bağımlılıkları algılandığında çalışır. Değişiklik yoksa testi gereksiz şekilde çalıştırmayı önler. Bu durumda, en son çalıştırmanın bir parçası olmasa da gri giden test sonucu "güncel" olmaya devam etmektedir.

![Test Gezgini 'nde perded Out testleri](media/vs-2019/lut-test-explorer.png)

Bir kod değişikliği yaparak, belileyerek görüntülenen testleri yeniden çalıştırabilirsiniz.

Live Unit Testing otomatik olarak çalıştırma ve güncelleştirme, **Test Gezgini**'nden testleri açıkça çalıştırma arasında bazı farklılıklar vardır. Bu farklar şunlardır:

- Test Gezgini penceresinde testleri çalıştırmak veya hata ayıklamak, düzenli ikili dosyalar çalıştırlarken Live Unit Testing, işaretlenmiş ikililer çalıştırır.
- Live Unit Testing, testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, bunun yerine varsayılan etki alanından testleri çalıştırır. **Test Gezgini** penceresinden çalıştırılan testler yeni bir uygulama etki alanı oluşturur.
- Live Unit Testing her bir test derlemesindeki testleri sırayla çalıştırır. **Test Gezgini** penceresinde, paralel olarak birden çok test çalıştırmayı seçebilirsiniz.
::: moniker-end

## <a name="large-solutions"></a>Büyük çözümler

çözümünüz 10 veya daha fazla proje içeriyorsa, Visual Studio aşağıdaki iletişim kutusunu görüntüler:

- Live Unit Testing başlatın ve kalıcı veri yok
-   >    >    >  **kalıcı verileri silmek** Live Unit Testing araçlar seçeneklerini belirleyin

![Büyük projeler için Live Unit Testing iletişim kutusu](media/lut-large-project.png)

İletişim kutusu, büyük projelerdeki çok sayıda test için dinamik yürütmenin performansı ciddi ölçüde etkileyebileceğini uyarır. **Tamam**' ı seçerseniz, Çözümdeki tüm testleri yürütür Live Unit Testing. **İptal**' i seçerseniz, yürütülecek testleri seçebilirsiniz. Aşağıdaki bölümde bunun nasıl yapılacağı açıklanmaktadır.

## <a name="include-and-exclude-test-projects-and-test-methods&quot;></a>Test projelerini ve test yöntemlerini dahil etme ve hariç tutma

Birçok test projesi içeren çözümler için, bir projedeki hangi projelerin ve bireysel yöntemlerin Live Unit Testing katılmasını denetleyebilirsiniz. Örneğin, yüzlerce test projesi içeren bir çözümünüz varsa, Live Unit Testing katılmak için hedeflenen bir test projesi kümesi seçebilirsiniz. Proje veya Çözümdeki tüm testleri dışlamak, çoğu testi dahil etmek veya hariç tutmak veya tek testleri dışlamak istediğinize bağlı olarak bunu yapmanız için çeşitli yollar vardır. Live Unit Testing, bir Kullanıcı ayarı olarak dahil etme/hariç tutma durumunu kaydeder ve bir çözüm kapatılıp yeniden açıldığında onu anımsar.

### <a name=&quot;exclude-all-tests-in-a-project-or-solution&quot;></a>Bir proje veya Çözümdeki tüm testleri hariç tut

Birim testlerinde ayrı projeleri seçmek için Live Unit Testing başlatıldıktan sonra aşağıdakileri yapın:

1. **Çözüm Gezgini** çözüme sağ tıklayın ve   >  Tüm çözümün hariç tutulması için Live Unit Testing **hariç tut** ' u seçin.
1. Testlere eklemek istediğiniz her bir test projesine sağ tıklayın ve **Live Unit Testing**  >  **dahil et**' i seçin.

### <a name=&quot;exclude-individual-tests-from-the-code-editor-window&quot;></a>Kod Düzenleyicisi penceresinden bireysel testleri hariç tut

Bireysel test yöntemlerini dahil etmek veya hariç tutmak için kod Düzenleyicisi penceresini kullanabilirsiniz. Kod Düzenleyicisi penceresindeki test yönteminin imzasına sağ tıklayın ve sonra aşağıdaki seçeneklerden birini seçin:

- **Live Unit Testing**  >  **Dahil \<selected method> et**
- **Live Unit Testing**  >  **Hariç \<selected method> tut**
- **Live Unit Testing**  >  **Tümünü \<selected method> hariç tut** ,

### <a name=&quot;exclude-tests-programmatically&quot;></a>Testleri programlı olarak hariç tut

<xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute>Yöntemleri, sınıfları veya yapıları program aracılığıyla Live Unit Testing kapsamını raporlamaya göre hariç tutmak için özniteliği uygulayabilirsiniz.

Live Unit Testing bireysel yöntemleri dışlamak için aşağıdaki öznitelikleri kullanın:

- XUnit için: `[Trait(&quot;Category&quot;, &quot;SkipWhenLiveUnitTesting")]`
- NUnit için: `[Category("SkipWhenLiveUnitTesting")]`
- MSTest için: `[TestCategory("SkipWhenLiveUnitTesting")]`

Live Unit Testing tüm testlerin bir derlemesini dışlamak için aşağıdaki öznitelikleri kullanın:

- XUnit için: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- NUnit için: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- MSTest için: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Ayrıca bkz.

- [Kod testi araçları](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing blogu](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Live Unit Testing SSS](live-unit-testing-faq.yml)
- [Channel 9 videosu: Visual Studio Live Unit Testing](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
