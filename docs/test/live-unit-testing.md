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
ms.openlocfilehash: d7fc118de97fe2c898a414c16420e5e0fb642f03
ms.sourcegitcommit: 04fb8ba0f7ea73ba17baa88f10563c8600e7fd7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2021
ms.locfileid: "135121403"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Live Unit Testing yapılandırma ve kullanma

Bir uygulama geliştirirken, Live Unit Testing etkilenen birim testlerini arka planda otomatik olarak çalıştırır ve sonuçları ve kod kapsamını gerçek zamanlı olarak gösterir. Kodunuzu değiştirirken Live Unit Testing, değişikliklerinizin mevcut testleri nasıl etkilediği ve eklediğiniz yeni kodun bir veya daha fazla var olan testlerin kapsamında olup olmadığı hakkında geri bildirim sağlar. Bu, hata düzeltmeleri yaparken veya yeni özellikler eklerken birim testlerini yazmanızı ister.

> [!NOTE]
> Live Unit Testing, Visual Studio Enterprise sürümünde .net Core veya .NET Framework hedefleyen C# ve Visual Basic projeleri için kullanılabilir.

Testleriniz için Live Unit Testing kullandığınızda, testlerin durumu hakkında verileri sürdürür. Kalıcı verilerin kullanılması, kod değişikliklerine yanıt olarak testlerinizi dinamik olarak çalıştırırken Live Unit Testing üstün performans sunmasına olanak tanır.

## <a name="supported-test-frameworks"></a>Desteklenen test çerçeveleri

Live Unit Testing, aşağıdaki tabloda listelenen üç popüler birim testi çerçevesi ile birlikte kullanılabilir. Bağdaştırıcılarının en düşük desteklenen sürümü ve çerçeveleri de gösterilir. birim test çerçevelerinin hepsi NuGet. org öğesinden kullanılabilir.

|Test çerçevesi  |en düşük Visual Studio bağdaştırıcısı sürümü  |Framework minimum sürümü  |
|---------|---------|---------|
|xUnit.net |xUnit. Runner. VisualStudio sürüm 2.2.0-Beta3-build1187 |xUnit 1.9.2 |
|NUnit |NUnit3TestAdapter sürümü 3.5.1 |NUnit sürümü 3.5.0 |
|MSTest |MSTest. TestAdapter 1.1.4-Önizleme |MSTest. TestFramework 1.0.5-Önizleme |

Microsoft. VisualStudio. QualityTools. unittestframework 'e başvuran daha önceden mstest tabanlı test projelerine sahipseniz ve daha yeni mstest NuGet paketlerine geçmek istemiyorsanız, Visual Studio 2019 veya Visual Studio 2017 ' e yükseltin.

bazı durumlarda, Live Unit Testing çalışması için bir proje tarafından başvurulan NuGet paketlerini açıkça geri yüklemeniz gerekebilir. bunu, çözümün açık bir derlemesini yaparak (   >  en üst düzey Visual Studio menüsünden derleme **yeniden oluşturma çözümünü** seçin) ya da çözümdeki paketleri geri yükleyerek yapabilirsiniz (çözüme sağ tıklayıp **NuGet paketlerini geri yükle**' yi seçin).

## <a name="configure"></a>Yapılandırma

  >  üst düzey Visual Studio menü çubuğundan araçlar **seçeneklerini** belirleyip, ardından **seçenekler** iletişim kutusunun sol bölmesinde **Live Unit Testing** ' yı seçerek Live Unit Testing yapılandırın.

> [!TIP]
> Live Unit Testing etkinleştirildikten sonra (sonraki bölüme bakın, [başlatma, duraklatma ve durdurma Live Unit Testing](#start-pause-and-stop)), Ayrıca, **Test** Live Unit Testing seçeneklerini belirleyerek **Seçenekler** iletişim kutusunu açabilirsiniz  >    >  .

Aşağıdaki görüntüde iletişim kutusunda kullanılabilen Live Unit Testing yapılandırma seçenekleri gösterilmektedir:

![Live Unit Testing yapılandırma seçenekleri](./media/lut-options.png)

Yapılandırılabilir seçenekler şunlardır:

- Bir çözüm oluşturulup hata ayıklandığında Live Unit Testing duraklatılır.

- Sistemin pil gücü belirtilen eşiğin altına düştüğünde Live Unit Testing duraklayacağını belirtir.

- Bir çözüm açıldığında Live Unit Testing otomatik olarak çalışıp çalışmadığını belirtir.

- Hata ayıklama sembolü ve XML belge açıklaması oluşturma 'nın etkinleştirilip etkinleştirilmeyeceğini belirtir.

- Kalıcı verilerin depolandığı dizin.

- Tüm kalıcı verileri silme özelliği. Live Unit Testing, kalıcı olmayan veya beklenmedik bir şekilde davranmışsa, kalıcı verilerin bozulmasından etkileneceği durumlarda faydalıdır.

- Bir test çalışmasının zaman aşımına uğramadan zaman aralığı. Varsayılan değer 30 saniyedir.

- Live Unit Testing oluşturduğu test işlemlerinin maksimum sayısı.

- Live Unit Testing işlemlerin tüketebileceği maksimum bellek miktarı.

- Live Unit Testing **Çıkış** penceresine yazılan bilgi düzeyi.

   Seçenekler, günlüğe kaydetme (**yok**), yalnızca hata Iletileri (**hata**), hata ve bilgilendirici iletiler (**bilgi**, varsayılan) veya tüm ayrıntılar (**verbose**) içerir.

   Ayrıca, "1" değerini adlı kullanıcı düzeyindeki  bir ortam değişkenine atayarak `VS_UTE_DIAGNOSTICS` ve sonra Visual Studio yeniden başlatarak Live Unit Testing çıkış penceresinde ayrıntılı çıkış görüntüleyebilirsiniz.

   bir dosyadaki Live Unit Testing ayrıntılı MSBuild günlük iletilerini yakalamak için, `LiveUnitTesting_BuildLog` kullanıcı düzeyi ortam değişkenini, günlüğü içeren dosyanın adına ayarlayın.

## <a name="start-pause-and-stop"></a>Başlat, Duraklat ve durdur

Live Unit Testing etkinleştirmek için,   >    >  en üst düzey Visual Studio menüsünden Test Live Unit Testing **başlat** ' ı seçin. Live Unit Testing etkinleştirildiğinde, **Live Unit Testing** menüdeki seçenekler tek bir öğeden değişir, **başlatılır**, **duraklatılır** ve **durdurulur**:

- **Duraklatma** Live Unit Testing geçici olarak askıya alır.

  Live Unit Testing duraklatıldığında, kapsam görselleştirmesi düzenleyicide görünmez, ancak toplanan tüm veriler korunur. Live Unit Testing sürdürmek için Live Unit Testing menüsünden **devam** ' ı seçin. Live Unit Testing, duraklatıldığı sırada yapılan tüm düzenlemeleri yakalamak ve glifleri uygun şekilde güncelleştirirken gerekli işi yapar.

- Live Unit Testing **tamamen durdurulur** . Live Unit Testing, topladığı tüm verileri atar.

> [!NOTE]
> Bir birim testi projesi içermeyen bir çözümde Live Unit Testing başlatırsanız, **Duraklat** ve **Durdur** seçenekleri **Live Unit Testing** menüsünde görünür, ancak Live Unit Testing başlamaz. **Çıkış** penceresinde, "Bu çözüm tarafından desteklenmeyen test bağdaştırıcılarına başvurulmuyor..." iletisi görüntülenir.

Dilediğiniz zaman, Live Unit Testing geçici olarak duraklatabilir veya tamamen durdurabilirsiniz. Bunu yapmak isteyebilirsiniz, örneğin bir yeniden düzenleme ortasındaysa ve testlerinizin bir süre için bölüneceği hakkında bilgi sahibi olun.

## <a name="view-coverage-visualization"></a>Kapsam görselleştirmesini görüntüle

etkinleştirildikten sonra, yazmakta olduğunuz kodun birim testleri kapsamında olup olmadığını ve bunu kapsayan testlerin geçtiğini göstermek için Visual Studio düzenleyicideki her kod satırını güncelleştirir Live Unit Testing. Aşağıdaki görüntüde hem geçen hem de başarısız testlerin bulunduğu kod satırları ve testlerin kapsamadığı kod satırları gösterilmektedir. Yeşil "✓" ile donatılmış satırlar yalnızca testlerin geçirilerek, kırmızı bir "x" ile donatılmış satırlar bir veya daha fazla başarısız test tarafından ele alınmıştır ve mavi "➖" ile düzenlenmiş satırlar herhangi bir test tarafından kapsanmaz.

::: moniker range="<=vs-2019"
![Visual Studio kod kapsamı](./media/lut-codewindow.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Visual Studio kod kapsamı](./media/vs-2022/lut-code-window.png)
::: moniker-end

Live Unit Testing kapsam görselleştirmesi, kod düzenleyicisinde kodu değiştirirken hemen güncelleştirilir. Düzenleme işlemleri sırasında, aşağıdaki görüntüde gösterildiği gibi, yuvarlama, başarısız ve kapsanmayan sembollerin altına bir yuvarlak Zamanlayıcı görüntüsü ekleyerek, verilerin güncel olmadığını belirtmek için görselleştirme değişiklikleri.

::: moniker range="<=vs-2019"
![zamanlayıcı simgesiyle Visual Studio kod kapsamı](./media/lut-codeupdating.png)
::: moniker-end
::: moniker range=">=vs-2022"
![zamanlayıcı simgesiyle Visual Studio kod kapsamı](./media/vs-2022/lut-code-updating.png)
::: moniker-end

## <a name="get-information-about-test-status"></a>Test durumu hakkında bilgi al

Kod penceresinde başarılı veya başarısız sembolün üzerine gelindiğinde, bu satıra kaç tane testin vurmasına bakabilirsiniz. Bireysel testlerin durumunu görmek için, simgesini seçin:

::: moniker range="<=vs-2019"
![Visual Studio bir simgenin test durumu](./media/lut-failedinfo.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Visual Studio bir simgenin test durumu](./media/vs-2022/lut-failed-info.png)
::: moniker-end

Araç ipucu, testlerin adlarını ve sonuçlarını sağlamanın yanı sıra testlerin kümesini yeniden çalıştırmanıza veya hata ayıklamanıza olanak tanır. Araç ipucunda bir veya daha fazla testi seçerseniz, yalnızca bu testlerin da çalıştırılmasını veya hata ayıklamasını sağlayabilirsiniz. Bu, kod penceresi olmadan testlerinizin hatalarını ayıklamanıza olanak tanır. Hata ayıklarken, önceden ayarlamış olduğunuz kesme noktalarını gözlemlemenin yanı sıra, hata ayıklayıcı beklenmeyen bir sonuç döndüren bir yöntemi yürüttüğünde program yürütme duraklatılır <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> .

Araç ipucunda başarısız bir testin üzerine geldiğinizde, aşağıdaki görüntüde gösterildiği gibi, hata hakkında ek bilgi sağlamak için genişler. Doğrudan başarısız teste gitmek için araç ipucunda çift tıklayın.

::: moniker range="<=vs-2019"
![Visual Studio 'de test araç ipucu bilgisi başarısız oldu](./media/lut-failedmsg.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Visual Studio 'de test araç ipucu bilgisi başarısız oldu](./media/vs-2022/lut-failed-message.png)
::: moniker-end

Başarısız teste gittiğinizde, Live Unit Testing Yöntem imzasında görsel olarak belirtir:

- geçti (yeşil bir "✓" ile birlikte yarı dolu bir Beaker ile gösterilir)
- başarısız oldu (kırmızı bir "" ile birlikte yarı dolu bir Beaker 🞩 )
- Live Unit Testing (mavi bir "➖" ile birlikte yarı dolu bir Beaker) dahil değildir

Test dışı yöntemler bir sembol ile birlikte tasarlanmaz. Aşağıdaki görüntüde dört tür yöntem gösterilmektedir.

::: moniker range="<=vs-2019"
![pass veya fail simgesiyle Visual Studio Test yöntemleri](media/lut-testsource.png)
::: moniker-end
::: moniker range=">=vs-2022"
![pass veya fail simgesiyle Visual Studio Test yöntemleri](media/vs-2022/lut-test-source.png)
::: moniker-end

## <a name="diagnose-and-correct-test-failures"></a>Test başarısızlıklarını tanılama ve düzeltme

Başarısız testten, ürün kodunda kolayca hata ayıklayın, düzenleme yapabilir ve uygulamanızı geliştirmeye devam edebilirsiniz. Live Unit Testing arka planda çalıştığından, hata ayıklama, düzenleme ve devam etme sürecinde Live Unit Testing durdurup yeniden başlatmanız gerekmez.

Örneğin, önceki görüntüde gösterilen test hatası, yönteme geçirildiğinde alfabetik olmayan karakterlerin döndürdüğü test yönteminde yanlış bir varsayım nedeniyle oluştu `true` <xref:System.Char.IsLower%2A?displayProperty=fullName> . Test yöntemini düzelttikten sonra, tüm testlerin geçmesi gerekir. Live Unit Testing duraklatıp durdurmanız gerekmez.

::: moniker range="vs-2017"
## <a name="test-explorer"></a>Test Gezgini

**Test Gezgini** , testleri çalıştırmanızı ve hatalarını ayıklamanızı ve test sonuçlarını çözümlemeyi sağlayan bir arabirim sağlar. Live Unit Testing Test Gezgini ile **tümleştirildi.** Test Live Unit Testing etkinleştirilmediyse veya durdurulmuşsa, Test Gezgini bir **testin** son çalıştırıisinde birim testlerinin durumunu görüntüler. Kaynak kodu değişiklikleri, testleri yeniden çalıştırmanız gerektirir. Buna karşılık, Live Unit Testing, Test Gezgini'nde birim testlerinin **durumu hemen** güncelleştirilir. Birim testlerini açıkça çalıştırmaya gerek yok.

> [!TIP]
> Üst **Live Unit Testing** üst düzey Windows  >    >  **Test Gezgini'ni** seçerek test Visual Studio açın.

Test Gezgini penceresinde **bazı testlerin** soluk olduğunu görebilirsiniz. Örneğin, daha önce Live Unit Testing bir projeyi açtıktan sonra test penceresini etkinleştirdikten sonra, aşağıdaki görüntüde olduğu gibi **Test** Gezgini penceresi başarısız olan test dışında tüm görüntüler soluk görüntüye açıldı. Bu durumda, Live Unit Testing testi yeniden çalıştırdı ama başarılı testleri yeniden çalıştırmadı. Bunun nedeni Live Unit Testing kalıcı veriler, testlerin son çalıştırması başarıyla çalıştırılana kadar herhangi bir değişiklik olmadığını gösterir.

![Test Gezgini'nde başarısız test](media/lut-test-explorer.png)

Test Gezgini menüsünden Hepsini Çalıştır veya Çalıştır seçeneklerini  seçerek soluk **görünen** testleri **yeniden çalıştırabilirsiniz.** Ya da, **Test** Gezgini menüsünde bir veya daha fazla test  seçin,  sağ tıklayın ve ardından açılan menüden Seçili Testleri Çalıştır veya Seçili Testlerde Hata Ayıkla'yı seçin. Testler çalıştırılırken en üstte kabarcığı olur.

Test sonuçlarını otomatik olarak çalıştırma Live Unit Testing güncelleştirme ve Test Gezgini'nde testleri açıkça çalıştırma arasında bazı **farklar vardır.** Bu farklar şunlardır:

- Test Gezgini penceresinden testleri çalıştırma veya hata ayıklama normal ikililer çalıştırırken, Live Unit Testing ikililer çalıştırır.
- Live Unit Testing, testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, varsayılan etki alanındaki testleri çalıştırır. Test Gezgini penceresinden **çalıştır olunan** testler yeni bir uygulama etki alanı oluştur.
- Live Unit Testing her test derlemesinde testleri sırayla çalıştırır. Test **Gezgini penceresinde** birden çok testi paralel olarak çalıştırmayı seçebilirsiniz.
::: moniker-end

::: moniker range=">=vs-2019"
## <a name="live-unit-testing-window"></a>Live Unit Testing penceresi

**Live Unit Testing** Gezgini'ne benzer şekilde, **testleri** çalıştırmaya, testlerde hata ayıklamaya ve test sonuçlarını analiz etmenize olanak sağlayan bir arabirim sağlar. Bu Live Unit Testing etkinleştirildiğinde, Test Gezgini'nde birim **testlerinin durumu** hemen güncelleştirilir. Birim testlerini açıkça çalıştırmaya gerek yok. Bir Live Unit Testing etkin değilken veya **durdurulursa, Live Unit Testing** testlerin durumunu testin son çalıştır zamanı görüntüler. Testleri yeniden Live Unit Testing yeniden çalıştırmanız için bir kaynak kodu değişikliği gerekir.

> [!TIP]
> Üst Live Unit Testing **menüsünden Test**  >  **Live Unit Testing**  >  **Başlat'ı** seçerek Visual Studio başlatabilirsiniz. Windows'da Diğer **Live Unit Testing** **Görüntüle'Windows**  >  **Live Unit Testing**  >  **da açabilirsiniz.**

Bu pencerede bazı **Live Unit Testing** soluk olduğunu görebilirsiniz. Örneğin, aşağıdaki görüntüde Live Unit Testing Live Unit Testing penceresi  tüm testleri soluk gösterir. Soluk gösterilen test sonuçları, testin en son Live Unit Test çalıştırması kapsamında olmadığını gösteriyor. Testler yalnızca testte bir değişiklik algılandığında veya test bağımlılıkları algılandığında dolar. Değişiklik yoksa, testi gereksiz yere çalıştırmayı önler. Bu durumda, gri renkli test sonucu hala "günceldir" ancak en son çalıştırmanın parçası değildir.
::: moniker-end
::: moniker range="vs-2019"

![Test Gezgini'nde soluk testler](media/vs-2019/lut-test-explorer.png)
::: moniker-end
::: moniker range=">=vs-2022"
![Test Gezgini'nde soluk testler](media/vs-2022/lut-test-explorer.png)

::: moniker-end
::: moniker range=">=vs-2019"
Kod değişikliği yaparak soluk görünen tüm testleri yeniden çalıştırabilirsiniz.

Test sonuçlarını otomatik olarak çalıştırma Live Unit Testing güncelleştirme ve Test Gezgini'nde testleri açıkça çalıştırma arasında bazı **farklar vardır.** Bu farklar şunlardır:

- Test Gezgini penceresinden testleri çalıştırma veya hata ayıklama normal ikililer çalıştırırken, Live Unit Testing ikililer çalıştırır.
- Live Unit Testing, testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, varsayılan etki alanındaki testleri çalıştırır. Test Gezgini penceresinden **çalıştır olunan** testler yeni bir uygulama etki alanı oluştur.
- Live Unit Testing her test derlemesinde testleri sırayla çalıştırır. Test **Gezgini penceresinde** birden çok testi paralel olarak çalıştırmayı seçebilirsiniz.
::: moniker-end

## <a name="large-solutions"></a>Büyük çözümler

Çözümünüz 10 veya daha fazla proje Visual Studio aşağıdaki iletişim kutusunu görüntüler:

- başlatma Live Unit Testing ve kalıcı veri yok
- Kalıcı **Verileri**  >  **Silmek**  >  **Live Unit Testing** Araçlar  >  **Seçenekleri'ne tıklayın**

![Live Unit Testing projeler için iletişim kutusu](media/lut-large-project.png)

İletişim kutusu, büyük projelerde çok sayıda testin dinamik olarak yürütülmesinin performansı ciddi ölçüde etkileyeceni konusunda sizi uyarıyor. Tamam 'ı **seçer** Live Unit Testing çözümde tüm testleri yürütür. **İptal'i seçerse** yürütülecek testleri seçin. Aşağıdaki bölümde bunun nasıl gerçekleştir adımları açık bir şekilde açık almaktadır.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Test projelerini ve test yöntemlerini dahil etmek ve hariç tutmak

Birçok test projesine sahip çözümler için, bir projede yer alan projelerin ve tek tek yöntemlerin hangi projelerde ve Live Unit Testing. Örneğin, yüzlerce test projesine sahip bir çözümünüz varsa, bu projelere katılmak için hedeflenen test projeleri Live Unit Testing. Proje veya çözümde yer alan tüm testleri hariç tutmak, çoğu testi dahil etmek veya hariç tutmak ya da tek tek testleri dışlamak istemenize bağlı olarak bunu yapmak için çeşitli yollar vardır. Live Unit Testing dahil/dışlama durumunu kullanıcı ayarı olarak kaydeder ve bir çözüm kapatılan ve yeniden açılan zaman bunu anımsar.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Proje veya çözümde tüm testleri dışlama

Birim testlerinde projeleri ayrı ayrı seçmek için, proje başlatıldıktan sonra Live Unit Testing yapın:

1. Çözümün tamamını dışlamak için **Çözüm Gezgini** sağ **tıklayın ve Live Unit Testing**  >  **Dışla'yı** seçin.
1. Testlere eklemek istediğiniz her test projesine sağ tıklayın ve Ekle'yi Live Unit Testing  >  **seçin.**

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Tek tek testleri kod düzenleyicisi penceresinden dışlama

Tek tek test yöntemlerini dahil etmek veya hariç tutmak için kod düzenleyicisi penceresini kullanabilirsiniz. Kod düzenleyicisi penceresinde test yönteminin imzasına sağ tıklayın ve ardından aşağıdaki seçeneklerden birini belirleyin:

- **Live Unit Testing**  >  **Içerir \<selected method>**
- **Live Unit Testing**  >  **Dışlamak \<selected method>**
- **Live Unit Testing**  >  **Hariç Tut \<selected method>**

### <a name="exclude-tests-programmatically"></a>Testleri program aracılığıyla hariç tut

özniteliğini yöntemleri, sınıfları veya yapıları program aracılığıyla kapsamlarını raporlamadan dışlamak için <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> Live Unit Testing.

Yöntemlerin tek tek dışlamalarını dışlamak için aşağıdaki öznitelikleri Live Unit Testing:

- xUnit için: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
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
