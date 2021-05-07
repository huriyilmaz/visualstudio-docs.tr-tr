---
title: Live Unit Testing
description: Desteklenen çerçeveler ve Live Unit Testing yapılandırma dahil olmak üzere uygulama geliştirme sırasında Live Unit Testing hakkında bilgi edinin.
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
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798628"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Live Unit Testing yapılandırma ve kullanma

Bir uygulama geliştirirken, Live Unit Testing etkilenen birim testlerini arka planda otomatik olarak çalıştırır ve sonuçları ve kod kapsamını gerçek zamanlı olarak gösterir. Kodunuzu değiştirirken Live Unit Testing, değişikliklerinizin mevcut testleri nasıl etkilediği ve eklediğiniz yeni kodun bir veya daha fazla var olan testlerin kapsamında olup olmadığı hakkında geri bildirim sağlar. Bu, hata düzeltmeleri yaparken veya yeni özellikler eklerken birim testlerini yazmanızı ister.

> [!NOTE]
> Live Unit Testing, Visual Studio Enterprise sürümünde .NET Core veya .NET Framework hedefleyen C# ve Visual Basic projeleri için kullanılabilir.

Testleriniz için Live Unit Testing kullandığınızda, testlerin durumu hakkında verileri sürdürür. Kalıcı verilerin kullanılması, kod değişikliklerine yanıt olarak testlerinizi dinamik olarak çalıştırırken Live Unit Testing üstün performans sunmasına olanak tanır.

## <a name="supported-test-frameworks"></a>Desteklenen test çerçeveleri

Live Unit Testing, aşağıdaki tabloda listelenen üç popüler birim testi çerçevesi ile birlikte kullanılabilir. Bağdaştırıcılarının en düşük desteklenen sürümü ve çerçeveleri de gösterilir. Birim test çerçevelerinin tümü NuGet.org adresinden kullanılabilir.

|Test çerçevesi  |Visual Studio bağdaştırıcısı en düşük sürüm  |Framework minimum sürümü  |
|---------|---------|---------|
|xUnit.net |xUnit. Runner. VisualStudio sürüm 2.2.0-Beta3-build1187 |xUnit 1.9.2 |
|NUnit |NUnit3TestAdapter sürümü 3.5.1 |NUnit sürümü 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Microsoft.VisualStudio.QualityTools.UnitTestFramework'e başvurulan eski MSTest tabanlı test projeleriniz varsa ve daha yeni MSTest NuGet paketlerine taşımak zorunda değilsanız, Visual Studio 2019 veya Visual Studio 2017'ye yükseltin.

Bazı durumlarda, proje tarafından başvurulan NuGet paketlerinin çalışması için açıkça geri Live Unit Testing gerekir. Bunu yapmak için çözümün açık bir derlemesini (üst düzey Visual Studio menüsünden Çözümü Yeniden Derleme'yi seçin) veya çözümde paketleri geri yükleyerek (çözüme sağ tıklayın ve NuGet Paketlerini Geri Yükle'yi  >   seçin) yapabilirsiniz. 

## <a name="configure"></a>Yapılandırma

Üst Live Unit Testing menü **çubuğundan** Araçlar Seçenekleri'ni Visual Studio ve ardından Seçenekler iletişim kutusunun sol bölmesinde Live Unit Testing'yi seçerek bu seçeneği  >   **belirleyin.** 

> [!TIP]
> Bu Live Unit Testing etkinleştirildikten sonra (sonraki bölüme bakın, Başlat, duraklat ve durdur  [Live Unit Testing),](#start-pause-and-stop)Seçenekler iletişim kutusunu Açmak için **Test**  >  **Seçenekleri'Live Unit Testing**  >  **açabilirsiniz.**

Aşağıdaki görüntüde iletişim Live Unit Testing yapılandırma seçenekleriyle ilgili bilgiler ve bilgiler yer alıyor:

![Live Unit Testing yapılandırma seçenekleri](./media/lut-options.png)

Yapılandırılabilir seçenekler şunlardır:

- Bir Live Unit Testing ve hata ayıklarken bu sorunun duraklatıp duraklatmayıp duraklatılamayyıp çalışmay olmadığı.

- Sistemin pil Live Unit Testing belirtilen eşiğin altına düştüğünde sistemin duraklatıp duraklamayıp çalışmay olmadığı.

- Çözüm Live Unit Testing otomatik olarak çalıştırıp çalıştırmama.

- Hata ayıklama sembolünü ve XML belge açıklaması oluşturmanın etkinleştirip etkinleştirmey olmadığı.

- Kalıcı verilerin depolan olduğu dizin.

- Kalıcı olan tüm verileri silme özelliği. Bu, Live Unit Testing tahmin edilemeyen veya beklenmeyen bir şekilde davranış gösteriyorsa ve bu da kalıcı verilerin bozulmuş olduğunu gösterir.

- Test sonrasındaki zaman aralığı. Varsayılan değer 30 saniyedir.

- Live Unit Testing oluşturduğu test işlemlerinin maksimum sayısı.

- Live Unit Testing işlemlerin tüketebileceği maksimum bellek miktarı.

- Live Unit Testing **Çıkış** penceresine yazılan bilgi düzeyi.

   Seçenekler, günlüğe kaydetme (**yok**), yalnızca hata Iletileri (**hata**), hata ve bilgilendirici iletiler (**bilgi**, varsayılan) veya tüm ayrıntılar (**verbose**) içerir.

   Ayrıca, adlı bir Kullanıcı düzeyi ortam değişkenine "  1" değeri atayarak `VS_UTE_DIAGNOSTICS` ve ardından Visual Studio 'yu yeniden başlatarak Live Unit Testing çıkış penceresinde ayrıntılı çıkış görüntüleyebilirsiniz.

   Bir dosyadaki Live Unit Testing ayrıntılı MSBuild günlük iletilerini yakalamak için, `LiveUnitTesting_BuildLog` Kullanıcı düzeyi ortam değişkenini, günlüğü içeren dosyanın adına ayarlayın.

## <a name="start-pause-and-stop"></a>Başlat, Duraklat ve durdur

Live Unit Testing etkinleştirmek için,   >    >  en üst düzey Visual Studio menüsünden test Live Unit Testing **Başlat** ' ı seçin. Live Unit Testing etkinleştirildiğinde, **Live Unit Testing** menüdeki seçenekler tek bir öğeden değişir, **başlatılır**, **duraklatılır** ve **durdurulur**:

- **Duraklatma** Live Unit Testing geçici olarak askıya alır.

  Live Unit Testing duraklatıldığında, kapsam görselleştirmesi düzenleyicide görünmez, ancak toplanan tüm veriler korunur. Live Unit Testing sürdürmek için Live Unit Testing menüsünden **devam** ' ı seçin. Live Unit Testing, duraklatıldığı sırada yapılan tüm düzenlemeleri yakalamak ve glifleri uygun şekilde güncelleştirirken gerekli işi yapar.

- Live Unit Testing **tamamen durdurulur** . Live Unit Testing, topladığı tüm verileri atar.

> [!NOTE]
> Bir birim testi projesi içermeyen bir çözümde Live Unit Testing başlatırsanız, **Duraklat** ve **Durdur** seçenekleri **Live Unit Testing** menüsünde görünür, ancak Live Unit Testing başlamaz. **Çıkış** penceresinde, "Bu çözüm tarafından desteklenmeyen test bağdaştırıcılarına başvurulmuyor..." iletisi görüntülenir.

Herhangi bir zamanda, herhangi bir alanı geçici olarak duraklatabilir veya tamamen Live Unit Testing. Örneğin, yeniden düzenlemenin ortasındaysanız ve testlerinizi bir süre bozuk olacağını biliyorsanız bunu yapmak istiyor olabilirsiniz.

## <a name="view-coverage-visualization"></a>Kapsam görselleştirmesini görüntüleme

Etkinleştirildikten sonra Live Unit Testing, Visual Studio düzenleyicisinde kod satırlarından her biri, yazdığın kodun birim testlerinin kapsamına alınıp alınamay). Aşağıdaki görüntüde hem başarılı hem de başarısız olan kod satırlarının yanı sıra test kapsamında yer alan kod satırları da yer aleladedir. Yeşil "×" ile dekore edilmiş çizgiler yalnızca testlerden geçerek, kırmızı "x" ile dekore edilmiş çizgiler bir veya daha fazla başarısız test kapsamındadır ve mavi "➖" ile dekore edilmiş çizgiler hiçbir test kapsamında değildir.

![Visual Studio'de kod kapsamı](./media/lut-codewindow.png)

Live Unit Testing kapsamı görselleştirmesi, kod düzenleyicisinde kod değiştirdiğinde hemen güncelleştirilir. Düzenlemeler işleme sırasında görselleştirme, aşağıdaki görüntüde gösterilen şekilde geçiş, başarısız ve kapsama altındaki sembollerin altına yuvarlak zamanlayıcı görüntüsü ekleyerek verilerin güncel olmadığını belirtmek için değişir.

![Zamanlayıcı simgesi Visual Studio kod kapsamı](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Test durumu hakkında bilgi al

Kod penceresinde başarılı veya başarısız sembolünü üzerine gelerek bu satıra kaç test isabet edeni görebilirsiniz. Tek tek testlerin durumunu görmek için simgesini seçin:

![Visual Studio'de bir simgenin durumunu test Visual Studio](./media/lut-failedinfo.png)

Araç ipucu, testlerin adlarını ve sonucu sağlamanın yanı sıra test kümesinde yeniden çalıştırma veya hata ayıklama da sağlar. Araç ipucunda bir veya daha fazla test seçersiniz, yalnızca bu testleri de çalıştırabilirsiniz veya hata ayıkabilirsiniz. Bu, kod penceresinden ayrılmak zorunda kalmadan testlerde hata ayıklamanıza olanak sağlar. Hata ayıklarken, önceden ayarlamış olabilir herhangi bir kesme noktası gözlemleye ek olarak, hata ayıklayıcı beklenmeyen bir sonuç döndüren bir yöntem yürütürken program yürütme <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> duraklatılır.

Araç ipucunda başarısız bir testin üzerine geldiğinizde, aşağıdaki görüntüde gösterildiği gibi, hata hakkında ek bilgi sağlamak için genişler. Doğrudan başarısız teste gitmek için araç ipucunda çift tıklayın.

![Visual Studio 'da başarısız test araç ipucu bilgileri](./media/lut-failedmsg.png)

Başarısız teste gittiğinizde, Live Unit Testing Yöntem imzasında görsel olarak belirtir:

- geçti (yeşil bir "✓" ile birlikte yarı dolu bir Beaker ile gösterilir)
- başarısız oldu (kırmızı bir "" ile birlikte yarı dolu bir Beaker 🞩 )
- Live Unit Testing (mavi bir "➖" ile birlikte yarı dolu bir Beaker) dahil değildir

Test dışı yöntemler bir sembol ile birlikte tasarlanmaz. Aşağıdaki görüntüde dört tür yöntem gösterilmektedir.

![Pass veya fail simgesiyle Visual Studio 'daki test yöntemleri](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Test başarısızlıklarını tanılama ve düzeltme

Başarısız testten, ürün kodunda kolayca hata ayıklayın, düzenleme yapabilir ve uygulamanızı geliştirmeye devam edebilirsiniz. Live Unit Testing arka planda çalıştığından, hata ayıklama, düzenleme ve devam etme sürecinde Live Unit Testing durdurup yeniden başlatmanız gerekmez.

Örneğin, önceki görüntüde gösterilen test hatası, yönteme geçirildiğinde alfabetik olmayan karakterlerin döndürdüğü test yönteminde yanlış bir varsayım nedeniyle oluştu `true` <xref:System.Char.IsLower%2A?displayProperty=fullName> . Test yöntemini düzelttikten sonra, tüm testlerin geçmesi gerekir. Live Unit Testing duraklatıp durdurmanız gerekmez.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Test Gezgini

**Test Gezgini** , testleri çalıştırmanızı ve hatalarını ayıklamanızı ve test sonuçlarını çözümlemeyi sağlayan bir arabirim sağlar. Live Unit Testing, **Test Gezgini** ile tümleşir. Live Unit Testing etkinleştirilmediği veya durdurulduğunda **Test Gezgini** , bir testin son çalıştırıldığı zaman birim testlerinin durumunu görüntüler. Kaynak kodu değişiklikleri testleri yeniden çalıştırmanız gerekir. Buna karşılık, Live Unit Testing etkinleştirildiğinde Test Gezgini'nde birim **testlerinin durumu hemen** güncelleştirilir. Birim testlerini açıkça çalıştırmaya gerek yok.

> [!TIP]
> Üst **Live Unit Testing** üst **düzey** test gezgini  >  **menüsünden Windows** Test  >  **Gezgini'ni** test Visual Studio açın.

Test Gezgini penceresinde **bazı testlerin** soluk olduğunu görebilirsiniz. Örneğin, daha önce Live Unit Testing bir projeyi açtıktan sonra test penceresini etkinleştirdikten sonra, aşağıdaki görüntüde olduğu gibi **Test** Gezgini penceresi başarısız test dışında tüm görüntüler soluk görüntüde belirdi. Bu durumda, Live Unit Testing testi yeniden çalıştırdı ama başarılı testleri yeniden çalıştırmadı. Bunun nedeni Live Unit Testing kalıcı verilerin testlerin son çalıştırmadan bu yana hiçbir değişiklik olmadığının işaret etmesidir.

![Test Gezgini'nde başarısız test](media/lut-test-explorer.png)

Test Gezgini menüsünden Hepsini Çalıştır veya Çalıştır seçeneklerini  seçerek soluk **görünen** testleri **yeniden çalıştırabilirsiniz.** Ya da, **Test** Gezgini menüsünde bir veya daha fazla test  seçin,  sağ tıklayın ve ardından açılan menüden Seçili Testleri Çalıştır veya Seçili Testlerde Hata Ayıkla'yı seçin. Testler çalıştırılırken en üstte kabarcığı olur.

Test sonuçlarını otomatik olarak çalıştırma Live Unit Testing güncelleştirme ve Test Gezgini'nde testleri açıkça çalıştırma arasında bazı **farklar vardır.** Bu farklar şunlardır:

- Test Gezgini penceresinden testleri çalıştırma veya hata ayıklama normal ikililer çalıştırırken, Live Unit Testing ikililer çalıştırır.
- Live Unit Testing, testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, varsayılan etki alanındaki testleri çalıştırır. Test Gezgini penceresinden **çalıştır olunan** testler yeni bir uygulama etki alanı oluştur.
- Live Unit Testing her test derlemesinde testleri sırayla çalıştırır. Test **Gezgini penceresinde** birden çok testi paralel olarak çalıştırmayı seçebilirsiniz.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Live Unit Testing penceresi

**Test Gezgini** ile benzer **Live Unit Testing**, testleri çalıştırmanıza ve hata ayıklamanıza ve test sonuçlarını çözümlemenize imkan tanıyan bir arabirim sağlar. Live Unit Testing etkinleştirildiğinde, **Test Gezgini** 'ndeki birim testlerinin durumu hemen güncelleştirilir. Birim testlerini açıkça çalıştırmanız gerekmez. Live Unit Testing etkinleştirilmediği veya durdurulduğunda, **Live Unit Testing** bir testin son çalıştırıldığı zaman birim testlerinin durumunu görüntüler. Live Unit Testing yeniden başlattıktan sonra, testleri yeniden çalıştırmak için bir kaynak kodu değişikliği gerekir.

> [!TIP]
>   >    >  En üst düzey Visual Studio menüsünden test Live Unit Testing **Başlat** seçeneğini belirleyerek Live Unit Testing başlatın. Ayrıca,    >  **diğer Windows**  >  **Live Unit Testing görüntüle penceresini** kullanarak Live Unit Testing penceresini açabilirsiniz.

**Live Unit Testing** penceresinde bazı testlerin sık kullanıma hazır olduğunu fark edebilirsiniz. Örneğin, Live Unit Testing durdurup yeniden başlattığınızda, aşağıdaki görüntüde gösterildiği gibi, **Live Unit Testing** pencere tüm testleri soluklaştırır. Perded-Out test sonuçları, testin en son canlı birim testi çalıştırmasının bir parçası olmadığını gösterir. Testler yalnızca testteki bir değişiklik veya testin bağımlılıkları algılandığında çalışır. Değişiklik yoksa testi gereksiz şekilde çalıştırmayı önler. Bu durumda, en son çalıştırmanın bir parçası olmasa da gri giden test sonucu "güncel" olmaya devam etmektedir.

![Test Gezgini 'nde perded Out testleri](media/vs-2019/lut-test-explorer.png)

Bir kod değişikliği yaparak, belileyerek görüntülenen testleri yeniden çalıştırabilirsiniz.

Live Unit Testing otomatik olarak çalıştırma ve güncelleştirme, **Test Gezgini**'nden testleri açıkça çalıştırma arasında bazı farklılıklar vardır. Bu farklar şunlardır:

- Test Gezgini penceresinde testleri çalıştırmak veya hata ayıklamak, düzenli ikili dosyalar çalıştırlarken Live Unit Testing, işaretlenmiş ikililer çalıştırır.
- Live Unit Testing, testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, bunun yerine varsayılan etki alanından testleri çalıştırır. Test Gezgini penceresinden **çalıştır olunan** testler yeni bir uygulama etki alanı oluştur.
- Live Unit Testing her test derlemesinde testleri sırayla çalıştırır. Test **Gezgini penceresinde** birden çok testi paralel olarak çalıştırmayı seçebilirsiniz.
::: moniker-end

## <a name="large-solutions"></a>Büyük çözümler

Çözümde 10 veya daha fazla proje varsa Visual Studio aşağıdaki iletişim kutusu görüntülenir:

- başlatma Live Unit Testing ve kalıcı veri yok
- Kalıcı **Verileri**  >  **Silmek**  >  **Live Unit Testing** Araçlar  >  **Seçenekleri'ne tıklayın**

![Live Unit Testing projeler için iletişim kutusu](media/lut-large-project.png)

İletişim kutusu, büyük projelerde çok sayıda testin dinamik olarak yürütülmesinin performansı ciddi ölçüde etkileyeceni konusunda sizi uyarıyor. Tamam 'ı **seçer** Live Unit Testing çözümde tüm testleri yürütür. **İptal'i seçerse** yürütülecek testleri seçin. Aşağıdaki bölümde bunun nasıl gerçekleştir adımları açık bir şekilde açık almaktadır.

## <a name="include-and-exclude-test-projects-and-test-methods&quot;></a>Test projelerini ve test yöntemlerini dahil etmek ve hariç tutmak

Birçok test projesine sahip çözümler için, bir projede yer alan projelerin ve tek tek yöntemlerin hangi projelerde ve Live Unit Testing. Örneğin, yüzlerce test projesine sahip bir çözümünüz varsa, hedefli bir test projesi kümesi seçerek bu projelere Live Unit Testing. Proje veya çözümde yer alan tüm testleri hariç tutmak, çoğu testi dahil etmek veya hariç tutmak ya da tek tek testleri dışlamak istemenize bağlı olarak bunu yapmak için çeşitli yollar vardır. Live Unit Testing dahil/dışlama durumunu kullanıcı ayarı olarak kaydeder ve bir çözüm kapatılan ve yeniden açılan zaman bunu anımsar.

### <a name=&quot;exclude-all-tests-in-a-project-or-solution&quot;></a>Proje veya çözümde tüm testleri dışlama

Birim testlerinde projeleri ayrı ayrı seçmek için, proje başlatıldıktan sonra Live Unit Testing yapın:

1. Çözümün tamamını dışlamak için **Çözüm Gezgini** sağ tıklayın **ve Live Unit Testing**  >  **Dışla'yı** seçin.
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
- [Channel 9 videosu: Visual Studio 'da Live Unit Testing](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
