---
title: Live Unit Testing
ms.date: 03/07/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
ms.openlocfilehash: 1e1a0ec1fd6f2fbdf4f016b1d22db5a6929b5e24
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851439"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Live Unit Testing yapılandırma ve kullanma

Bir uygulama geliştirirken, Live Unit Testing etkilenen birim testlerini arka planda otomatik olarak çalıştırır ve sonuçları ve kod kapsamını gerçek zamanlı olarak gösterir. Kodunuzu değiştirmeniz gibi Live Unit Testing değişikliklerinizi mevcut testleri nasıl etkilenen geri bildirim sağlar ve bir veya daha fazla var olan testlerin kapsadığını olup yeni kod ekledik. Bu, hata düzeltmeleri yaparken veya yeni özellikler eklerken birim testlerini yazmanızı ister.

> [!NOTE]
> Live Unit Testing, Visual Studio C# Enterprise sürümünde .NET Core veya .NET Framework hedefleyen projeleri ve Visual Basic kullanılabilir.

Testleriniz için Live Unit Testing kullandığınızda, testlerin durumu hakkında verileri sürdürür. Kalıcı verilerin kullanılması, kod değişikliklerine yanıt olarak testlerinizi dinamik olarak çalıştırırken Live Unit Testing üstün performans sunmasına olanak tanır.

## <a name="supported-test-frameworks"></a>Desteklenen test çerçeveleri

Live Unit Testing aşağıdaki tabloda listelenen üç popüler birim test çerçeveleri ile çalışır. Bağdaştırıcılarının en düşük desteklenen sürümü ve çerçeveleri de gösterilir. Birim testi çerçevelerini NuGet.org adresinden tüm kullanılabilir.

|Test çerçevesi  |Visual Studio bağdaştırıcısı en düşük sürüm  |Framework en düşük sürüm  |
|---------|---------|---------|
|{1&gt;{2&gt;xUnit.net&lt;2}&lt;1} |xunit.Runner.VisualStudio sürüm 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |3\.5.1 NUnit3TestAdapter sürümü |NUnit 3.5.0 sürümü |
|MSTest |MSTest.TestAdapter 1.1.4-preview |MSTest.TestFramework 1.0.5-preview |

Microsoft. VisualStudio. QualityTools. UnitTestFramework 'e başvuran daha önceden MSTest tabanlı test projelerine sahipseniz ve yeni MSTest NuGet paketlerine geçmek istemiyorsanız, Visual Studio 2019 veya Visual Studio 2017 sürümüne yükseltin.

Bazı durumlarda, Live Unit Testing çalışması için bir proje tarafından başvurulan NuGet paketlerini açıkça geri yüklemeniz gerekebilir. Bunu, çözümün açık bir derlemesini yaparak (en üst düzey Visual Studio menüsünden **derle** > **yeniden derle** ) ya da çözümdeki paketleri geri yükleyerek yapabilirsiniz (çözüme sağ tıklayıp **NuGet paketlerini geri yükle**' yi seçin).

## <a name="configure"></a>Yapılandır

Üst düzey Visual Studio menü çubuğunda **araçlar** > **Seçenekler** ' i ve ardından **seçenekler** iletişim kutusunun sol bölmesinde **Live Unit Testing** ' yı seçerek Live Unit Testing yapılandırın.

> [!TIP]
> Live Unit Testing etkinleştirildikten sonra (bkz. bir sonraki bölüm, [başlatma, duraklatma ve durdurma Live Unit Testing](#start-pause-and-stop)), **Seçenekler** iletişim kutusunu da **Test** > **Live Unit Testing** > **seçeneklerini**belirleyerek açabilirsiniz.

Aşağıdaki görüntüde iletişim kutusunda kullanılabilen Live Unit Testing yapılandırma seçenekleri gösterilmektedir:

![Live Unit Testing yapılandırma seçenekleri](./media/lut-options.png)

Yapılandırılabilir seçeneklerin şunlardır:

- Bir çözüm oluşturulan ve hata ayıklama mı Live Unit Testing duraklatır.

- Sistemin pili belirtilen eşiğin altına düştüğünde olup Live Unit Testing duraklatır.

- Bir çözümü açtığınızda olup Live Unit Testing otomatik olarak çalıştırılır.

- Etkinleştirilip etkinleştirilmeyeceğini sembol ve XML belgesi açıklama oluşturma hatalarını ayıklayın.

- Kalıcı veri depolanacağı dizin.

- Tüm kalıcı veri silme yeteneği. Live Unit Testing, kalıcı olmayan veya beklenmedik bir şekilde davranmışsa, kalıcı verilerin bozulmasından etkileneceği durumlarda faydalıdır.

- Bir test çalışmasının zaman aşımına uğramadan zaman aralığı. Varsayılan değer 30 saniyedir.

- Live Unit Testing oluşturan test işlemlerinin maksimum sayısı.

- Live Unit Testing işler maksimum belleğin kullanabilir.

- Live Unit Testing için yazılan bilgi düzeyini **çıkış** penceresi.

   Seçenekleriniz günlüğünü (**hiçbiri**), yalnızca hata iletileri (**hata**), hata ve bilgilendirici iletileri (**bilgileri**, varsayılan), ya da tüm ayrıntıları (**ayrıntılı** ).

   Live Unit Testing içinde ayrıntılı çıkış görüntüleyebilirsiniz **çıkış** değerini "1" adlı bir kullanıcı düzeyinde ortam değişkenine atayarak penceresi `VS_UTE_DIAGNOSTICS`ve ardından Visual Studio'yu yeniden başlatmayı.

   Live Unit Testing dosyasındaki öğesinden ayrıntılı MSBuild günlük iletilerini yakalamak için `LiveUnitTesting_BuildLog` kullanıcı düzeyinde ortam değişkenine günlük içerecek dosyanın adı.

## <a name="start-pause-and-stop"></a>Başlat, Duraklat ve durdur

Live Unit Testing etkinleştirmek için, en üst düzey Visual Studio menüsünden **Test** > **Live Unit Testing** > **Başlat** ' ı seçin. Live Unit Testing etkinleştirildiğinde, **Live Unit Testing** menüdeki seçenekler tek bir öğeden değişir, **başlatılır**, **duraklatılır** ve **durdurulur**:

- **Duraklatma** Live Unit Testing geçici olarak askıya alır.

  Live Unit Testing duraklatıldığında, kapsam görselleştirmesi düzenleyicide görünmez, ancak toplanan tüm veriler korunur. Live Unit Testing sürdürmek için seçin **devam** Live Unit Testing menüsünde. Live Unit Testing, duraklatıldığı sırada yapılan tüm düzenlemeleri yakalamak ve glifleri uygun şekilde güncelleştirirken gerekli işi yapar.

- Live Unit Testing **tamamen durdurulur** . Live Unit Testing, toplanan tüm verileri atar.

> [!NOTE]
> Bir birim testi projesi içermeyen bir çözümde Live Unit Testing başlatırsanız, **Duraklat** ve **Durdur** seçenekleri **Live Unit Testing** menüsünde görünür, ancak Live Unit Testing başlamaz. **Çıkış** penceresinde, "Bu çözüm tarafından desteklenmeyen test bağdaştırıcılarına başvurulmuyor..." iletisi görüntülenir.

Herhangi bir zamanda geçici olarak duraklatabilir veya tamamen Live Unit Testing durdurun. Bunu yapmak isteyebilirsiniz, örneğin bir yeniden düzenleme ortasındaysa ve testlerinizin bir süre için bölüneceği hakkında bilgi sahibi olun.

## <a name="view-coverage-visualization"></a>Kapsam görselleştirmesini görüntüle

Etkinleştirildikten sonra, yazmakta olduğunuz kodun birim testlerin kapsamında olup olmadığını ve bunu kapsayan testlerin geçtiğini göstermek üzere Visual Studio Düzenleyicisi 'ndeki her kod satırını güncelleştirir Live Unit Testing. Aşağıdaki görüntüde hem geçen hem de başarısız testlerin bulunduğu kod satırları ve testlerin kapsamadığı kod satırları gösterilmektedir. Yeşil "✓" ile düzenlenmiş satırları yalnızca testleri geçirerek ele alınmaktadır satırları "x" kırmızı ile donatılmış bir veya birden çok başarısız olan testler tarafından ele alınmaktadır ve mavi "➖" tarafından düzenlenmiş satırları tarafından herhangi bir test kapsamında değildir.

![Visual Studio 'da kod kapsamı](./media/lut-codewindow.png)

Live Unit Testing kapsam görselleştirmesi, kod düzenleyicisinde kodu değiştirirken hemen güncelleştirilir. Düzenleme işlemleri sırasında, aşağıdaki görüntüde gösterildiği gibi, yuvarlama, başarısız ve kapsanmayan sembollerin altına bir yuvarlak Zamanlayıcı görüntüsü ekleyerek, verilerin güncel olmadığını belirtmek için görselleştirme değişiklikleri.

![Zamanlayıcı simgesiyle Visual Studio 'da kod kapsamı](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Test durumu hakkında bilgi al

Kod penceresinde başarılı veya başarısız simgenin üzerine gelerek, kaç tane test satırdaki karşılaştınız demektir görebilirsiniz. Bireysel testlerin durumunu görmek için, simgesini seçin:

![Visual Studio 'da bir sembolün test durumu](./media/lut-failedinfo.png)

Araç ipucu, testlerin adlarını ve sonuçlarını sağlamanın yanı sıra testlerin kümesini yeniden çalıştırmanıza veya hata ayıklamanıza olanak tanır. Araç çubuğuna bir veya daha fazla testin seçerseniz, çalıştırmak veya yalnızca bu Testlerde Hata Ayıkla. Bu kod penceresinde ayrılmak zorunda kalmadan testlerinizi ayıklamanızı sağlar. Hata ayıklarken, önceden ayarlamış olduğunuz kesme noktalarını gözlemlemenin yanı sıra, hata ayıklayıcı beklenmeyen bir sonuç döndüren bir <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> yöntemi yürüttüğünde program yürütme duraklatılır.

Başarısız bir test araç ipucunda üzerine geldiğinizde, bu hata hakkında ek bilgi sağlamak için aşağıdaki görüntüde gösterildiği gibi genişletir. Doğrudan başarısız teste gitmek için araç ipucunda çift tıklayın.

![Visual Studio 'da başarısız test araç ipucu bilgileri](./media/lut-failedmsg.png)

Başarısız teste gittiğinizde, Live Unit Testing Yöntem imzasında görsel olarak belirtir:

- geçti (yeşil bir "✓" ile birlikte yarı dolu bir Beaker ile gösterilir)
- başarısız oldu (kırmızı "🞩" ile birlikte yarı dolu bir Beaker)
- Live Unit Testing (mavi bir "➖" ile birlikte yarı dolu bir Beaker) dahil değildir

Olmayan test yöntemleri bir simge ile donatılmış değil. Aşağıdaki görüntüde dört tür yöntem gösterilmektedir.

![Pass veya fail simgesiyle Visual Studio 'daki test yöntemleri](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Tanılama ve test hataları düzeltin

Başarısız testten, ürün kodunda kolayca hata ayıklayın, düzenleme yapabilir ve uygulamanızı geliştirmeye devam edebilirsiniz. Live Unit Testing arka planda çalıştığından, hata ayıklama, düzenleme ve devam etme sürecinde Live Unit Testing durdurup yeniden başlatmanız gerekmez.

Örneğin, önceki görüntüde gösterilen test hatası, <xref:System.Char.IsLower%2A?displayProperty=fullName> yöntemine geçirildiğinde alfabetik olmayan karakterlerin `true` döndürdüğü test yönteminde yanlış bir varsayım nedeniyle oluştu. Test yöntemini düzelttikten sonra, tüm testlerin geçmesi gerekir. Live Unit Testing duraklatıp durdurmanız gerekmez.

## <a name="test-explorer"></a>Test Gezgini

**Test Gezgini** , testleri çalıştırmanızı ve hatalarını ayıklamanızı ve test sonuçlarını çözümlemeyi sağlayan bir arabirim sağlar. Live Unit Testing ile tümleştirilir **Test Gezgini**. Live Unit Testing etkin değil ya da durdurulmuş, **Test Gezgini** birim testleri bir test çalıştırma son kez durumunu görüntüler. Testleri yeniden çalıştırın, kaynak kodu değişiklikleri gerektirir. Live Unit Testing etkin olduğunda, buna karşılık, birim durumu içinde testleri **Test Gezgini** hemen güncelleştirilir. Birim testlerini açıkça çalıştırmanız gerekmez.

> [!TIP]
> En üst düzey Visual Studio menüsünden **test > ** **Windows** > **Test Gezgini** ' ni seçerek **Test Gezgini** 'ni açın.

**Test Gezgini** penceresinde bazı testlerin sık kullanıma hazır olduğunu fark edebilirsiniz. Örneğin, daha önce kaydedilen bir projeyi açtıktan sonra Live Unit Testing etkinleştirdiğinizde, **Test Gezgini** penceresi, aşağıdaki görüntüde gösterildiği gibi, başarısız olan teste göre daha fazla zaman aşımına uğrar. Bu durumda, Live Unit Testing başarısız testi yeniden çalıştırmıştır, ancak başarılı testleri yeniden çalıştırmaz. Bunun nedeni Live Unit Testing kalıcı verilerinin, testlerin son kez başarıyla çalıştırılmasından bu yana hiçbir değişiklik olmadığını gösterir.

![Test Gezgininde başarısız test](media/lut-test-explorer.png)

**Test Gezgini** menüsünden **Tümünü Çalıştır** veya **Çalıştır** seçeneklerini belirleyerek, beliden görüntülenen tüm testleri yeniden çalıştırabilirsiniz. Ya da **Test Gezgini** menüsünde bir veya daha fazla test seçin, sağ tıklayın ve ardından **Seçilen Testleri Çalıştır** veya açılan menüden **Seçili testlerin hatalarını ayıkla** ' yı seçin. Testler çalışırken, Yukarı üst Kabarcık.

Live Unit Testing otomatik olarak çalıştırarak test sonuçları güncelleştiriliyor ve açıkça çalışan test eder. arasında bazı farklar vardır **Test Gezgini**. Bu farklar şunlardır:

- Live Unit Testing izleme eklenmiş ikili dosyalar çalıştırılır çalıştırma veya testleri Test Gezgini penceresinden hata ayıklama normal ikili dosyaları, çalışır.
- Live Unit Testing testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, ancak bunun yerine varsayılan etki alanından testleri çalıştırır. Testleri çalıştırın **Test Gezgini** penceresi, yeni bir uygulama etki alanı oluşturun.
- Live Unit Testing testler sırayla her bir test derlemesindeki çalıştırır. **Test Gezgini** penceresinde, paralel olarak birden çok test çalıştırmayı seçebilirsiniz.

## <a name="large-solutions"></a>Büyük çözümler

Çözümünüz 10 veya daha fazla proje içeriyorsa, Visual Studio şunları yaptığınızda aşağıdaki iletişim kutusunu görüntüler:

- Live Unit Testing başlatın ve kalıcı veri yok
-  > **araç** **seçeneklerini** belirleyin > **kalıcı verileri Sil** **Live Unit Testing** > 

![Büyük projeleri için Live Unit Testing iletişim](media/lut-large-project.png)

İletişim kutusu, büyük projelerdeki çok sayıda test için dinamik yürütmenin performansı ciddi ölçüde etkileyebileceğini uyarır. Seçerseniz **Tamam**, Live Unit Testing, Çözümdeki tüm testleri yürütür. Seçerseniz **iptal**, yürütülecek testleri seçebilirsiniz. Aşağıdaki bölümde bunun nasıl yapılacağı açıklanmaktadır.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Test projeleri hariç içerir ve test yöntemleri

Birçok test projesi içeren çözümler için, bir projedeki hangi projelerin ve bireysel yöntemlerin Live Unit Testing katılmasını denetleyebilirsiniz. Örneğin, test projeleri yüzlerce bir çözümünüz varsa, test projeleri Live Unit Testing katılmak için hedeflenen bir dizi seçebilirsiniz. Proje veya Çözümdeki tüm testleri dışlamak, çoğu testi dahil etmek veya hariç tutmak veya tek testleri dışlamak istediğinize bağlı olarak bunu yapmanız için çeşitli yollar vardır. Live Unit Testing içerme/dışlama durumunu bir kullanıcı ayarı olarak kaydeder ve bir çözüm kapatılıp yeniden olduğunda bunu hatırlar.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Bir proje veya Çözümdeki tüm testleri hariç tut

Tek tek projeler birim testleri seçmek için Live Unit Testing başlatıldıktan sonra aşağıdakileri yapın:

1. Çözüme sağ **Çözüm Gezgini** ve **Canlı testleri** > **hariç** çözümün tamamını dışlanacak.
1. Sağ tıklayın ve testler eklemek istediğiniz her bir test projesi **Canlı testleri** > **Ekle**.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Kod Düzenleyicisi penceresinden bireysel testleri hariç tut

Kod Düzenleyicisi penceresi, dahil etmek veya bireysel test yöntemleri hariç tutmak için kullanabilirsiniz. Kod Düzenleyicisi penceresindeki test yönteminin imzasına sağ tıklayın ve sonra aşağıdaki seçeneklerden birini seçin:

- **Canlı testler** >  **\<seçili yöntemi içerir >**
- **Canlı testler** **\<seçili metodu hariç > **
- **Canlı testler** > **Tüm \<seçili yöntemi hariç tut >**

### <a name="exclude-tests-programmatically"></a>Testleri programlı olarak hariç tut

Uygulayabileceğiniz <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute> programlı olarak yöntemler, sınıflar veya yapılar kendi kapsamı içinde Live Unit Testing bildirimden hariç tutulacak özniteliği.

Live Unit Testing bireysel yöntemleri dışlamak için aşağıdaki öznitelikleri kullanın:

- XUnit için: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
- NUnit için: `[Category("SkipWhenLiveUnitTesting")]`
- MSTest için: `[TestCategory("SkipWhenLiveUnitTesting")]`

Live Unit Testing tüm testlerin bir derlemesini dışlamak için aşağıdaki öznitelikleri kullanın:

- XUnit için: `[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- NUnit için: `[assembly: Category("SkipWhenLiveUnitTesting")]`
- MSTest için: `[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Ayrıca bkz.

- [Kod test araçları](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Live Unit Testing blogu](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Live Unit Testing SSS](live-unit-testing-faq.md)
- [Channel 9 videosu: Visual Studio 'da Live Unit Testing](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
