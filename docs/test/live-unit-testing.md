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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75851439"
---
# <a name="how-to-configure-and-use-live-unit-testing"></a>Canlı Birim Testi nasıl yapılandırılır ve kullanılır?

Bir uygulama geliştirirken, Canlı Birim Testi arka planda etkilenen birim testlerini otomatik olarak çalıştırAr ve sonuçları ve kod kapsamını gerçek zamanlı olarak sunar. Kodunuzu değiştirirken, Canlı Birim Testi değişikliklerinizin varolan testleri nasıl etkilediği ve eklediğiniz yeni kodun bir veya daha fazla varolan test tarafından karşılanıp karşılanmadığı hakkında geri bildirim sağlar. Bu, hata düzeltmeleri yaparken veya yeni özellikler eklerken birim testleri yazmanızı nazikçe hatırlatir.

> [!NOTE]
> Visual Studio'nun Enterprise sayısında .NET Core veya .NET Framework'ü hedefleyen C# ve Visual Basic projeleri için Canlı Birim Testi mevcuttur.

Testleriniz için Canlı Birim Testi'ni kullandığınızda, testlerinizin durumu yla ilgili verileri devam eder. Kalıcı verileri kullanmak, Canlı Birim Testi'nin kod değişikliklerine yanıt olarak testlerinizi dinamik olarak çalıştırırken üstün performans sunmasına olanak tanır.

## <a name="supported-test-frameworks"></a>Desteklenen test çerçeveleri

Canlı Birim Testi, aşağıdaki tabloda listelenen üç popüler birim test çerçevesi ile çalışır. Bağdaştırıcılarının ve çerçevelerinin en az desteklenen sürümü de gösterilir. Birim test çerçevelerinin tümü NuGet.org.

|Test Çerçevesi  |Visual Studio Adaptör minimum sürümü  |Çerçeve minimum sürümü  |
|---------|---------|---------|
|xUnit.net |xunit.runner.visualstudio sürümü 2.2.0-beta3-build1187 |xunit 1.9.2 |
|NUnit |NUnit3TestAdapter sürüm 3.5.1 |NUnit sürüm 3.5.0 |
|MSTest |MSTest.TestAdapter 1.1.4-önizleme |MSTest.TestFramework 1.0.5-önizleme |

Microsoft.VisualStudio.QualityTools.UnitTestFramework adresine başvuran eski MSTest tabanlı test projeleriniz varsa ve yeni MSTest NuGet paketlerine geçmek istemiyorsanız Visual Studio 2019 veya Visual Studio 2017'ye yükseltin.

Bazı durumlarda, Canlı Birim Testi'nin çalışması için proje tarafından başvurulan NuGet paketlerini açıkça geri yüklemeniz gerekebilir. Bunu, çözümün açık bir yapısını yaparak (üst düzey Visual Studio menüsünden **Yeniden** > **Oluştur Çözümünü** seçin) veya çözümdeki paketleri geri yükleyerek (çözüme sağ tıklayarak **NuGet Paketlerini Geri Yükle'yi**seçin).

## <a name="configure"></a>Yapılandırma

Üst düzey Visual Studio menü çubuğundan **Araçlar** > **Seçenekleri'ni** seçerek ve ardından **Seçenekler** iletişim kutusunun sol bölmesinde Canlı Birim Testi'ni seçerek Canlı Birim **Testi'ni** yapılandırın.

> [!TIP]
> Canlı Birim Testi etkinleştirildikten sonra (bir sonraki bölüme bakın, [Canlı Birim Testini Başlat, duraklatın ve durdurun),](#start-pause-and-stop) **Test** > **Canlı Birim Test** > **Seçenekleri'ni**seçerek **Seçenekler** iletişim kutusunu da açabilirsiniz.

Aşağıdaki resim, iletişim kutusunda bulunan Canlı Birim Testi yapılandırma seçeneklerini gösterir:

![Canlı Birim Test yapılandırma seçenekleri](./media/lut-options.png)

Yapılandırılabilir seçenekler şunlardır:

- Bir çözüm oluşturulup debugged zaman Canlı Birim Testi duraklar olsun.

- Bir sistemin pil gücü belirtilen eşiğin altına düştüğünde Canlı Birim Testi duraklatılıp duraklatılmayacağı.

- Bir çözüm açıldığında Canlı Birim Testinin otomatik olarak çalışıp çalışılmadığı.

- Hata ayıklama simgesi ve XML belgeleri yorum oluşturma etkinleştirmek için olsun.

- Kalıcı verilerin depolandığı dizin.

- Kalıcı tüm verileri silme yeteneği. Bu, Canlı Birim Testi öngörülemeyen veya beklenmeyen bir şekilde davranıyorsa, bu da kalıcı verilerin bozuk olduğunu düşündürmektedir.

- Bir test çalışması nın zamanlandığı aralık. Varsayılan değer 30 saniyedir.

- Canlı Birim Testi'nin oluşturduğu maksimum test işlemi sayısı.

- Canlı Birim Testi işlemlerinin tüketebileceği maksimum bellek miktarı.

- Canlı Birim Test **Çıktısı** penceresine yazılan bilgi düzeyi.

   Seçenekler arasında günlüğe kaydetme (**Yok**), yalnızca hata iletileri (**Hata**), hata ve bilgilendirme iletileri **(Bilgi,** varsayılan) veya tüm ayrıntılar **(Verbose)** yer alır.

   Ayrıca, Live Unit Test **Output** penceresinde, kullanıcı düzeyindeki bir ortam değişkenine `VS_UTE_DIAGNOSTICS`"1" değeri atayarak ve ardından Visual Studio'yu yeniden başlatarak ayrıntılı çıktı görüntüleyebilirsiniz.

   Bir dosyada Canlı Birim Testi'nden ayrıntılı MSBuild `LiveUnitTesting_BuildLog` günlük iletilerini yakalamak için, kullanıcı düzeyindeki ortam değişkenini günlüğü içerecek şekilde dosyanın adına ayarlayın.

## <a name="start-pause-and-stop"></a>Başlat, duraklatma ve durdurma

Canlı Birim Testini etkinleştirmek için, üst düzey Visual Studio menüsünden **Canlı** > **Birim Test** > **Başlat'ı** seçin. Canlı Birim Testi etkinleştirildiğinde, Canlı **Birim Testi** menüsünde bulunan seçenekler tek bir öğeden **başlat'tan** **Duraklat** ve **Durdura**değişir:

- **Duraklatma,** Canlı Birim Testini geçici olarak askıya aldı.

  Canlı Birim Testi duraklatıldığında, kapsam görselleştirmedüzenleyicisinde görünmez, ancak toplanan tüm veriler korunur. Canlı Birim Testine devam etmek için Canlı Birim Testi menüsünden **Devam** et'i seçin. Canlı Birim Testi, duraklatıldıksa yapılan tüm güncellemeleri yakalamak için gerekli çalışmaları yapar ve glifleri uygun şekilde güncelleştirir.

- **Stop** Tamamen Canlı Birim Testi durur. Canlı Birim Testi topladığı tüm verileri atar.

> [!NOTE]
> Birim test projesini içermeyen bir çözümde Canlı Birim Testi'ni başlatırsanız, **Canlı Birim Testi** menüsünde **Duraklat** ve **Durdur** seçenekleri görüntülenir, ancak Canlı Birim Testi başlamaz. **Çıktı** penceresi, "Bu çözüm tarafından desteklenen test bağdaştırıcısı başvurulmez..." diye başlayan bir ileti görüntüler.

İstediğiniz zaman, Canlı Birim Testini geçici olarak duraklatabilir veya tamamen durdurabilirsiniz. Bunu yapmak isteyebilirsiniz, örneğin, bir yeniden düzenlemenin ortasındaysanız ve testlerinizin bir süre bozulacağını biliyorsanız.

## <a name="view-coverage-visualization"></a>Kapsam görselleştirmeyi görüntüleyin

Etkinleştirildikten sonra, Canlı Birim Testi Visual Studio düzenleyicisindeki her kod satırını güncelleyerek yazdığınız kodun birim testleri kapsamında olup olmadığını ve bu kodu kaplayan testlerin geçip geçmediğini gösterir. Aşağıdaki resimde, hem geçen hem de başarısız olan testlerin yanı sıra testler tarafından kapsanmayan kod satırları gösterilmektedir. Yeşil "✓" ile süslenmiş çizgiler sadece geçer testlerle kaplanır, kırmızı "x" ile süslenmiş çizgiler bir veya daha fazla başarısız testle kaplanır ve mavi bir "➖" ile dekore edilmiş çizgiler herhangi bir testle kaplanmaz.

![Visual Studio'da kod kapsamı](./media/lut-codewindow.png)

Canlı Birim Test kapsamı görselleştirmesi, kod düzenleyicisinde kodu değiştirdiğinizde hemen güncelleştirilir. Düzenlemeyi işlerken, aşağıdaki resimde görüldüğü gibi, geçen, başarısız ve kapsanmayan sembollerin altına bir yuvarlak zamanlayıcı görüntüsü ekleyerek verilerin güncel olmadığını belirtmek için görselleştirme değişiklikleri.

![Zamanlayıcı simgesiyle Visual Studio'da kod kapsamı](./media/lut-codeupdating.png)

## <a name="get-information-about-test-status"></a>Test durumu hakkında bilgi alın

Kod penceresindeki başarılı veya başarısız sembolün üzerinde gezinerek, bu satıra kaç testin isabet ettiğini görebilirsiniz. Tek tek testlerin durumunu görmek için sembolü seçin:

![Visual Studio'da bir sembol için test durumu](./media/lut-failedinfo.png)

Araç ipucu, testlerin adlarını ve sonucunu sağlamanın yanı sıra, test kümesini yeniden çalıştırmanızı veya hata ayıklamanızı sağlar. Araç ipucundaki testlerden birini veya birkaçını seçerseniz, yalnızca bu testleri çalıştırabilir veya hata ayıklayabilirsiniz. Bu, kod penceresinden çıkmadan testlerinizi hata ayıklamanızı sağlar. Hata ayıklama yaparken, önceden ayarlamış olabileceğiniz kesme noktalarını gözlemlemenin yanı sıra, hata <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> ayıklayan beklenmeyen bir sonucu döndüren bir yöntem yürüttüğünde program yürütme duraklar.

Araç ucunda başarısız bir testin üzerinde gezinirken, aşağıdaki resimde gösterildiği gibi hata hakkında ek bilgi sağlamak için genişletir. Doğrudan başarısız bir teste gitmek için, araç ucunda çift tıklatın.

![Visual Studio'da başarısız test araç ipucu bilgisi](./media/lut-failedmsg.png)

Başarısız teste gidince, Canlı Birim Testi yöntem imzasında aşağıdaki testleri görsel olarak gösterir:

- geçti (yeşil bir "✓" ile birlikte yarım tam bir beher tarafından gösterilir)
- başarısız (kırmızı ile birlikte yarım tam bir🞩beher " ")
- Live Unit Testing (mavi bir "➖" ile birlikte yarım dolu bir beher dahil değildir)

Test dışı yöntemler bir sembolle dekore edilmez. Aşağıdaki resimde, dört yöntem türü de gösterilmiştir.

![Visual Studio'da geçiş veya başarısız sembolü ile test yöntemleri](media/lut-testsource.png)

## <a name="diagnose-and-correct-test-failures"></a>Test hatalarını tanılama ve düzeltme

Başarısız testten ürün kodunu kolayca ayıklayabilir, düzeltmeler yapabilir ve uygulamanızı geliştirmeye devam edebilirsiniz. Canlı Birim Testi arka planda çalıştığından, hata ayıklama, düzenlediği ve devam döngüsü sırasında Canlı Birim Testini durdurmanız ve yeniden başlatmanız gerekmez.

Örneğin, önceki resimde gösterilen test hatası, yönteme geçildiğinde `true` <xref:System.Char.IsLower%2A?displayProperty=fullName> alfabetik olmayan karakterlerin döndürdeğinin test yöntemindeki yanlış bir varsayımdan kaynaklandı. Test yöntemini düzelttikten sonra, tüm testler geçmelidir. Canlı Birim Testini duraklatmak veya durdurmak zorunda değilsiniz.

## <a name="test-explorer"></a>Test Gezgini

**Test Gezgini,** testleri çalıştırmanızı, hata ayıklamanızı ve test sonuçlarını çözümlemenizi sağlayan bir arabirim sağlar. Canlı Birim Testi **Test Explorer**ile entegre. Canlı Birim Testi etkinleştirilemediğinde veya durdurulduğunda, **Test Gezgini** birim testlerinin durumunu en son bir test çalıştırıldığında görüntüler. Kaynak kodu değişiklikleri, testleri yeniden çalıştırmanızı gerektirir. Buna karşılık, Canlı Birim Testi etkinleştirildiğinde, **Test Gezgini'ndeki** birim testlerinin durumu hemen güncelleştirilir. Birim testlerini açıkça çalıştırmanız gerekmez.

> [!TIP]
> Üst düzey Visual Studio menüsünden **Test** > **Windows** > **Test Gezgini'ni** seçerek Test **Gezgini'ni** açın.

**Test Gezgini** penceresinde bazı testlerin soluk olduğunu fark edebilirsiniz. Örneğin, daha önce kaydedilmiş bir projeyi açtıktan sonra Canlı Birim Testi'ni etkinleştirdiğinizde, Aşağıdaki resimde görüldüğü gibi **Test Gezgini** penceresi başarısız olan test dışında tüm solukla şolmuştu. Bu durumda, Canlı Birim Testi başarısız testi yeniden çalıştırdı, ancak başarılı testleri yeniden çalıştırmadı. Bunun nedeni, Canlı Birim Testi'nin kalıcı verilerinin testlerin en son başarıyla çalıştırıldığı için herhangi bir değişiklik olmadığını belirtmiş olmasıdır.

![Test Gezgini'nde başarısız olan test](media/lut-test-explorer.png)

**Test Gezgini** menüsünden **Tümünü Çalıştır** veya **Çalıştır** seçeneklerini seçerek soluk görünen tüm testleri yeniden çalıştırabilirsiniz. Veya, **Test Gezgini** menüsünden bir veya daha fazla test seçin, sağ tıklatın ve ardından açılan menüden **Seçili Testleri Çalıştır** veya Hata **Ayıklama Testlerini** seçin. Testler yapılırken, üstte kabarcıklar var.

Canlı Birim Testi otomatik olarak çalışan ve test sonuçlarını güncelleme ve **Test Gezgini**testleri açıkça çalışan arasında bazı farklılıklar vardır. Bu farklılıklar şunlardır:

- Test Gezgini penceresinden testleri çalıştırma veya hata ayıklama düzenli ikili çalışır, Canlı Birim Testi ise enstrümante ikili çalışır.
- Canlı Birim Sınaması testleri çalıştırmak için yeni bir uygulama etki alanı oluşturmaz, daha çok varsayılan etki alanından testleri çalışır. **Test Gezgini** penceresinden çalıştırılatan testler yeni bir uygulama etki alanı oluşturur.
- Canlı Birim Testi, her test tertibatında testleri sırayla çalışır. Test **Gezgini** penceresinde, birden çok testi paralel olarak çalıştırmayı seçebilirsiniz.

## <a name="large-solutions"></a>Büyük çözümler

Çözümünüzde 10 veya daha fazla proje varsa, Visual Studio aşağıdaki iletişim kutusunu görüntüler:

- Canlı Birim Testini başlatın ve kalıcı veri yok
- select **Tools** > **Options** > **Canlı Birim Testi** > **Kalıcı Verileri Silme**

![Büyük projeler için Canlı Birim Testi iletişim kutusu](media/lut-large-project.png)

İletişim, büyük projelerde çok sayıda testin dinamik olarak yürütülmesinin performansı ciddi şekilde etkileebileceği konusunda sizi uyarır. **Tamam'ı**seçerseniz, Canlı Birim Testi çözümdeki tüm testleri yürütür. **İptal'i**seçerseniz, yürütülecek testleri seçebilirsiniz. Aşağıdaki bölümde bunun nasıl yapılacağını açıklamaktadır.

## <a name="include-and-exclude-test-projects-and-test-methods"></a>Test projelerini ve test yöntemlerini ekleme ve hariç tutma

Birçok test projesine sahip çözümler için, bir projedeki projelerin ve tek tek yöntemlerin Canlı Birim Testi'ne katıldığını kontrol edebilirsiniz. Örneğin, yüzlerce test projesiiçeren bir çözümünüz varsa, Canlı Birim Testi'ne katılmak için hedeflenmiş bir test projesi kümesi seçebilirsiniz. Proje veya çözümdeki tüm testleri hariç tutmak, çoğu testi dahil etmek veya hariç tutmak veya tek tek testleri hariç tutmak isteyip istemediğiniz bağlı olarak, bunu yapmanın birkaç yolu vardır. Canlı Birim Testi kaydeder, kullanıcı ayarı olarak durumu içerir/hariç tutar ve bir çözüm kapatıldığında ve yeniden açıldığında bunu hatırlar.

### <a name="exclude-all-tests-in-a-project-or-solution"></a>Proje veya çözümdeki tüm testleri hariç tutma

Birim testlerinde tek tek projeleri seçmek için, Canlı Birim Testi başladıktan sonra aşağıdakileri yapın:

1. **Solution Explorer'da** çözüme sağ tıklayın ve tüm çözümü hariç tutmak için **Canlı Testler** > **Dışla'yı** seçin.
1. Testlere eklemek istediğiniz her test projesini sağ tıklatın ve **Canlı Testler** > **Ekle'yi**seçin.

### <a name="exclude-individual-tests-from-the-code-editor-window"></a>Kod düzenleyicisi penceresinden tek tek testleri hariç tutma

Tek tek test yöntemlerini eklemek veya hariç tutmak için kod düzenleyicisi penceresini kullanabilirsiniz. Kod düzenleyicisi penceresinde test yönteminin imzasına sağ tıklayın ve ardından aşağıdaki seçeneklerden birini seçin:

- **Canlı Testler** > ** \<Seçili yöntemi>**
- **Canlı Testler** > **Seçili yöntemi>hariç \<tutma**
- **Canlı Testler** > **Tüm \<Ama seçili yöntemi>hariç**

### <a name="exclude-tests-programmatically"></a>Testleri programlı olarak hariç tutma

Bu özniteliği, yöntemleri, sınıfları veya yapıları Canlı Birim Testi'nde kapsama larını raporlamaktan programlı olarak dışlamak için uygulayabilirsiniz. <xref:System.Diagnostics.CodeAnalysis.ExcludeFromCodeCoverageAttribute>

Canlı Birim Testi'nden tek tek yöntemleri hariç tutmak için aşağıdaki öznitelikleri kullanın:

- xUnit için:`[Trait("Category", "SkipWhenLiveUnitTesting")]`
- NUnit için:`[Category("SkipWhenLiveUnitTesting")]`
- MSTest için:`[TestCategory("SkipWhenLiveUnitTesting")]`

Canlı Birim Testi'nden tüm test derlemesini hariç tutmak için aşağıdaki öznitelikleri kullanın:

- xUnit için:`[assembly: AssemblyTrait("Category", "SkipWhenLiveUnitTesting")]`
- NUnit için:`[assembly: Category("SkipWhenLiveUnitTesting")]`
- MSTest için:`[assembly: TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Ayrıca bkz.

- [Kod test araçları](https://visualstudio.microsoft.com/vs/testing-tools/)
- [Canlı Birim Test blog](https://devblogs.microsoft.com/visualstudio/live-unit-testing-in-visual-studio-2017-enterprise/)
- [Live Unit Testing SSS](live-unit-testing-faq.md)
- [Kanal 9 video: Visual Studio Canlı Birim Testi](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T105)
