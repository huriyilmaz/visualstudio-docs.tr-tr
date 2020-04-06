---
title: Visual Studio için Kompozit Desenler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 500ea8ffe7c33c1d747590ea074bff43fa1a3ab3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698625"
---
# <a name="composite-patterns-for-visual-studio"></a>Visual Studio İçin Bileşik Desenler
Bileşik desenler etkileşim ve tasarım öğelerini farklı yapılandırmalarda birleştirir. Tutarlılık açısından Visual Studio'daki en önemli kompozit desenlerden bazıları şunlardır:

- [Veri görselleştirme](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Nesne üzerinde ui ve gözetleme](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Seçim modelleri](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Kalıcılık ve kaydetme ayarları](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Dokunma girişi](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a>Veri görselleştirme

### <a name="overview"></a>Genel Bakış
 Grafikler, karar verme yi geliştirmek için verileri toplamanın ve görselleştirmenin görsel bir yoludur. Onlar kullanıcıların veri çok ama çok az anlamı ne dikkat hak ve ne bir eylem gerekebilir görmek karşı karşıya yardımcı olabilir.

 Aşağıdaki koşullardan herhangi biri doğruysa, kullanıcı bir grafikten yararlanacaktır:

- Grafik, kullanıcıların hareket edebilecekleri görevleri belirlemelerine yardımcı olur mu?

- Grafik, kullanıcıların olası değişikliklerin sonuçlarını tahmin etmesini sağlayacak mı?

- Grafik, kullanıcıların eğilimleri keşfetmesine ve desenleri belirlemesine yardımcı olacak mı?

- Grafik kullanıcıların daha iyi kararlar almasına izin verecek mi?

- Grafik, kullanıcıların belirli bir bağlamda sahip olabileceği belirli bir soruyu yanıtlamaya yardımcı olur mu?

#### <a name="general-rules-for-charts"></a>Grafikler için genel kurallar

- Verileri açıkça etiketle. Açıklama olmadan Çizimler sadece güzel resimler.

- Eğrilme oranlarını önlemek için eksenleri sıfırdan başlatın. Satır uzunluğu ve çubuk boyutu, veri noktaları arasındaki ilişkileri anlamak için önemli görsel ipuçlarıdır.

- Bilgi grafikleri değil, grafikler oluşturun. Infographics verilerin sanatsal temsilleri ve birincil hedefi görsel hikaye anlatımı olduğunu. Grafikler görsel olarak çekici olabilir (ve olmalıdır), ancak verilerin kendisi için konuşmasına izin verin.

- Skeumorphism kaçının, resimsel çubuk grafikler, kontrast hashmarks, ve diğer infografik dokunuşlar.

- Dekoratif bir unsur olarak 3D efektler kullanmayın. Bunları yalnızca kullanıcının bilgileri kavrama becerisinin ayrılmaz bir parçası ysa kullanın.

- İkiden fazla renk bu grafik türünü doğru okunmasını ve yorumlamasını zorlaştırabileceğinden, birden çok satır ve dolgu kullanmaktan kaçının.

- Bir kavramı anlamanın veya verilerle etkileşimkurmanın tek yolu olarak bir grafik (veya herhangi bir çizim) kullanmayın. Bu görme engelli kullanıcılar için zorluklar sunar.

- Grafikleri bir sayfada gereksiz veya dekoratif öğeler olarak kullanmayın. Başka bir deyişle, bir grafik herhangi bir değer katmıyorsa veya kullanıcıların bir sorunu çözmesinde yardımcı olmuyorsa, bunu kullanmayın.

### <a name="chart-types"></a>Grafik türleri
 Visual Studio'da kullanılan grafik türleri arasında çubuk grafikler, çizgi grafikler, halka grafiği veya "donut grafiği" olarak bilinen değiştirilmiş bir pasta grafiği, zaman çizelgeleri, dağılım çizimleri ("küme grafikleri" olarak da adlandırılır) ve Gantt grafikleri yer almaktadır. Her grafik türü, farklı bir bilgi türünü iletmek için yararlıdır.

### <a name="other-charting-considerations"></a>Diğer grafik hususlar

#### <a name="color"></a>Renk
 Visual Studio'da kullanılmak üzere tanımlanmış belirli bir grafik renkleri paleti vardır. Palet renk körlüğü önemli türleri için erişilebilir ve renk renk çok dar dilimler olarak kullanıldığında bile ayırt edilebilir. Bu renkleri, ui'nizdeki herhangi bir grafik veya grafik türü için herhangi bir kombinasyonda kullanabilirsiniz. Bu kadar farklı renk gerekmez eğer tüm yedi renk kullanmanız gerekmez. Bu renkler herhangi bir ön plan öğeleri ile kullanılmak üzere tasarlanmaz, bu nedenle bu renklerin üstüne metin veya glifler yerleştirmeyin. Bu tonlar sabit kodlanmış olmalı ve Araçlar **> Seçenekleri** altında kullanıcı özelleştirmesine maruz bırakılmalıdır (bkz. [son kullanıcılar için renkleri açığa çıkarma).](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

|Swatch|Onaltılık|RGB|
|------------|---------|---------|
|![Swatch 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Swatch BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Swatch FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Swatch 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Swatch 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Swatch 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Swatch B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a>Nesne üzerinde ui ve gözetleme
 Bu bölümde, Visual Studio'ya özgü nesne tabanlı bir ui türü olan kod peek görünümü olarak da bilinen gözetleme bağlamı verir.

### <a name="overview"></a>Genel Bakış

- On-object UI, kullanıcıya ana görevinden uzak kalmadan daha fazla bilgi veya etkileşim vermelidir.

- Visual Studio on-object UI için ana desen "dikkat noktasında bilgi" olarak bilinir.

- Visual Studio'daki nesne altı ui, satır içi veya kayan ve dayanıklı veya geçicidir.

  - Visual Studio'da nesne üzerinde bir tür ui türü olan kod görünümü satır içi ve dayanıklıdır.

  - Visual Studio'da nesne üzerinde bir tür ui olan CodeLens, kayan ve geçici

  Bir kodun nasıl çalıştığını anlamak veya bu kodla ilgili ayrıntıları bulmak genellikle bir geliştiricinin bağlam ı değiştirmesive başka bir içeriğe veya başka bir pencereye gitmesini gerektirir. Bu bağlam değişimleri rahatsız edici olabilir, çünkü kullanıcılar ana pencerelerinden ayrılırlarsa özgün görevlerine odaklanmayı kaybedebilirler. Ayrıca, özellikle windows'un değiştirilmesi özgün kodlarının diğer UI'ler tarafından gizlenmelerine neden olduysa, bu orijinal bağlamı geri almak zor olabilir.

  On-object UI "dikkat noktasında bilgi" olarak adlandırılan bir desen izler. Bu iletiler, açılır pencereler ve iletişim kutuları, kullanıcılara ana görevlerine odaklanmadan açıklama veya etkileşim ekleyen ek, alakalı bilgiler sağlar. Nesne deki Kullanıcı Cai'ye örnek olarak, kullanıcı işaretçisini bildirim alanındaki bir simgenin üzerinde gezindiğinde görünen açılır pencereler, yanlış yazılmış bir sözcüğün altındaki kırmızı dalgalı lık ve Visual Studio 2013'te tanıtılan peek görünümü verilebilir.

### <a name="decision-points"></a>Karar noktaları
 Visual Studio içinde, dikkat noktasında bilgi bu desen kullanmak için çeşitli yolları vardır. Doğru mekanizmanın seçilmesi ve tutarlı ve öngörülebilir bir şekilde uygulanması, genel deneyim için çok önemlidir. Aksi takdirde, kullanıcılara içeriğin kendisinden odağı bozan kafa karıştırıcı veya tutarsız bir deneyim sunulabilir.

#### <a name="relationships-between-master-and-detail-content"></a>Ana ve ayrıntı içeriği arasındaki ilişkiler
 Dikkat noktasındaki bilgiler, kullanıcının odaklandığı içerik ("asıl" içerik) ve ek ilgili içerik ("ayrıntı" içeriği) arasındaki ilişkiyi görüntülemek için kullanılır. Bu desende, ayrıntı içeriği açıkça kullanıcının çalıştığı içerikle ilgilidir ve ana içeriğe yakın görüntülenebilir. Ana içeriği ezmeden özetlenemeyen tamamlayıcı bilgiler veya bilgiler, araç penceresi gibi başka bir deseni izlemelidir.

- Ayrıntı içeriğini **her zaman** ana içeriğe yakın bir şekilde görüntüleyin.

- **Her zaman** ayrıntı içeriğinin bir kullanıcının ana içeriğe odaklanmasını sağladığından emin olun. Çoğu zaman, bunu başaranın en iyi yolu, ayrıntı içeriğini ana içeriğe mümkün olduğunca yakın hale getirmektir. Bu, ayrıntı içeriğini ana içeriğin yanındaki açılır pencerede işleyerek veya ana içeriğin altındaki ayrıntı içeriğini satır satıra alarak yapılabilir.

- **Kullanıcıyı** ana içerikten uzaklaştıran dikkat noktasında asla bilgi kullanmayın. Kullanıcıların ayrıntı içeriğini ayrı olarak görüntülemesi gerekiyorsa, kullanıcının bunu yapmasını sağlayan açık bir eylemi ortaya çıkarın.

#### <a name="design-details"></a>Tasarım detayları
 Nesne üzerinde ui'nin doğru seçim olduğunu belirledikten sonra, dört ana tasarım hususu vardır:

1. **Kalıcılık:** içeriğin dayanıklı veya geçici olması bekleniyor mu?
   Kullanıcılar, başvurmak veya etkileşimde bulunmak için bilgileri görünür tutmak ister mi? Ya da kullanıcılar hızlı bir şekilde bilgilere bakmak ve daha sonra ana görevleri ile devam etmek isteyecektir?

2. **İçerik türü:** İçerik bilgilendirilebilir, işlem yapılabilir veya seyir olacak mı?
   Kullanıcının ana içerik le ilgili ek ayrıntılara ihtiyacı var mı? Kullanıcının ana içeriği etkileyen bir görevi tamamlaması gerekiyor mu? Yoksa kullanıcının başka bir kaynağa yönlendirilmesi mi gerekiyor?

3. **Gösterge türü:** ortam göstergesi mantıklı mı?
   Bilgiler yararlı bir şekilde özetlenebilir ve ana içeriği ezmeden görüntülenebilir mi?

4. **Jestler:** Kullanıcı UI'yi çağırmak ve reddetmek için hangi jestler kullanılacaktır?
   Kullanıcı ayrıntı içeriğini nasıl gündeme getirip gönderecek? Geçici ve dayanıklı durumlar arasında geçiş yapmak için sabitleme gibi bir hareket eklemenin değeri var mıdır?

   Bu dört karar noktasının her biri, nesne üzerinde ui ana bileşenleri üzerinde bir etkiye sahip olacaktır.

### <a name="on-object-ui-components"></a>Nesne üzerinde UI bileşenleri

1. Kapsayıcı (içerik sunucusu) türü

    - Yüzen

    - Satır içi

2. İçerik türü

    - Bilgilendirme: statik veya dinamik olabilecek veriler

    - Eyleme Geçirilebilir: ana içeriği değiştiren komutlar

    - Gezinme: Kullanıcıyı MSDN gibi başka bir pencereye veya uygulamaya alan bağlantılar

3. Hareketler

    - Çağırma

    - Işten çıkarma

    - Sabitleme

    - Diğer etkileşimler

4. Kalıcılık ve işleme modeli

    - Geçi -ci

    - Dayanıklı

    - Automatic

    - İsteğe bağlı

5. Ortam göstergeleri (isteğe bağlı)

    - Dalgalı altı çizili

    - Akıllı etiket simgesi

    - Diğer ortam göstergeleri

#### <a name="container-content-presenter-type"></a>Kapsayıcı (içerik sunucusu) türü
 Dikkat çekici noktada içeriği sunmak için iki ana seçenek vardır:

1. **Inline:** Visual Studio 2013 Code Editor'da tanıtılan peek görünümü gibi sıralı bir sunucu, varolan içeriği değiştirerek yeni içeriğe yer sağlar.

    - Kullanıcıların, sunduğunuz içeriğe atıfta bulunarak veya bunlarla etkileşimde bulunarak önemli miktarda zaman geçirmek isteyeceklerini bekliyorsanız, sıralı sunum yapanları **tercih** edin.

    - Kullanıcıların sunduğunuz bilgilere göz atmak isteyeceğini bekliyorsanız satır başında sunuculardan **kaçının,** ardından ana görevlerine en az kesintiyle devam edin.

2. **Kayan:** Kayan bir sunucu seçili içeriğe mümkün olduğunca yakın konumlandırılır, ancak varolan içeriğin düzenini değiştirmez. Seçili sembole en yakın kullanılabilir beyaz alan üzerinde kayan bir içerik paneli görüntülemek gibi çeşitli stratejiler kullanılabilir.

    - Kullanıcıların sunduğunuz bilgilere göz atmak isteyeceğini zedelemeli sunum yapanları **tercih edin,** ardından ana görevlerine en az kesintiyle devam edin.

    - Kullanıcıların, sunduğunuz içeriğe atıfta bulunarak veya bunlarla etkileşimde bulunarak önemli miktarda zaman geçirmek isteyeceklerini bekliyorsanız, kayan sunuculardan **kaçının.**

#### <a name="content-type"></a>İçerik türü
 Herhangi bir nesne kullanıcı birliş birimi kapsayıcısının içinde görüntülenebilen üç ana içerik türü vardır. Bu tür bilgilerin herhangi bir birleşimi gösterilebilir. Üç tür şunlardır:

1. **Bilgilendirme:** Nesne üzerindeki çoğu kullanıcı arabirimi kapsayıcısı bir tür bilgilendirme içeriği görüntüler. İçerik, ortamın mevcut durumu hakkındaki bilgileri temsil edebilir veya gelecekteki olası bir ortam durumu hakkında bilgi gösterebilir. Örneğin, varolan kod üzerinde yeniden düzenleme gibi belirli bir komutun etkisini göstermek için kullanılabilir.

    - **Her zaman** görüntülediğiniz bilgilerin kanonik gösterimini kullanın. Örneğin, kod kod gibi, sözdizimi vurgulama ile tam olarak görünmeli ve kullanıcının belirlediği yazı tipi ve diğer ortam ayarlarına saygı göstermelidir.

    - **Aynı** bilgiler ana içerik olarak sunulduğunda, bilgilendirme içeriği üzerinde her türlü eylemi her zaman desteklemeyi düşünün. Örneğin, nesne üzerinde bir Web Hizmeti ara birimi kapsayıcısının içinde varolan kodu sunuyorsanız, bu koda göz atma ve değiştirme yeteneğini güçlü bir şekilde desteklemeyi düşünün.

    - Gelecekteki olası bir durumu temsil eden bilgilendirici içerik sunarken **her zaman** farklı bir arka plan rengi kullanmayı düşünün.

2. İşlenebilir: Bazı nesne kullanıcı arabirimi kapsayıcıları, yeniden düzenleme işlemi gerçekleştirmek gibi ana içerik üzerinde bazı eylem gerçekleştirme olanağı sağlar.

    - **İşleme** tabi komutları her zaman bilgi içeriğinden ayrı konumlandırın.

    - **Uygun** olduğunda eylemleri her zaman etkinleştirin ve devre dışı edin.

    - **Her zaman** iletişim kutuları içinde komutları temsil etmek için standart yönergelere bakın.

    - **Nesne** üzerinde bir Kullanıcı Aracı kapsayıcısında maruz kalan eylem sayısını her zaman en aza indirir. On-object UI ile etkileşim hafif, hızlı bir deneyim olmalıdır. Kullanıcı, nesne üzerindeki Kullanıcı Aracı kapsayıcısını yönetmek için enerji harcamak zorunda kalmamalıdır.

    - **Nesne** üzerinde bir Kullanıcı Bira Birimi kapsayıcının nasıl ve ne zaman kapatılacağını veya kapatılacağını her zaman göz önünde bulundurun. En iyi uygulama olarak, ana ve ayrıntı içeriği arasındaki iletişimi sonuçlandıran herhangi bir eylem, bu eylem çağrıldığızaman nesne deki Kullanıcı Arabirimi kapsayıcısını da kapatmalıdır.

3. **Gezinti:** Bazı nesne kullanıcı arabirimi kapsayıcıları, kullanıcıyı başka bir pencereye veya uygulamaya götüren (örneğin, kullanıcının web tarayıcısında bir MSDN makalesi açma gibi) bağlantılar içerir.

    - **Her zaman** "Aç" ile herhangi bir navigasyon bağlantısı prepend böylece kullanıcıların başka bazı içerik için gezinen tarafından sürpriz olmayacaktır.

    - Gezinme bağlantılarını **her zaman** işlem edilebilir bağlantılardan ayırın.

#### <a name="ambient-indicators-optional"></a>Ortam göstergeleri (isteğe bağlı)
 Ortam göstergeleri, kodun geri kalanından zıt bir renkte sunulan metin veya dalgalı alt çizgi ve akıllı etiket simgeleri gibi işaretleyici sembolleri de dahil olmak üzere açık olabilir. Ortam göstergeleri ek, ilgili bilgilerin kullanılabilirliğini bildirir. İdeal olarak, kullanıcının onlarla etkileşimkurmasını gerektirmeden bile yararlı bilgiler sağlarlar.

- **Ortam** göstergesini her zaman kullanıcının dikkatini dağıtmaması veya bunaltmayacak şekilde yerleştirin. Bir ortam göstergesini bu şekilde konumlandırmak mümkün değilse, başka bir çözüm düşünün.

- Ortam göstergesini **her zaman** ilişkili içeriğe mümkün olduğunca yakın konumlandırın.

- **Her zaman** kullanılabilir kılan bilgileri özetleyen bir gösterge oluşturmaya çalışın. Kullanılabilir veri öğesi sayısının sayısını (örneğin, yalnızca "Başvurular" yerine "3 başvuru") sağlamayı veya verileri özetlemek için başka bir yol düşünmeyi düşünün.

  - Bir gösterge için verilerin her zaman hesaplanamadığı ve görüntülenemediği durumlarda, değerler hesaplanırken hemen aşamalı geri bildirim sağlamayı düşünün. Örneğin, okunmamış e-posta ların sayısı arttıkça Windows Phone'daki e-postanın yeniden canlanmasına benzer şekilde, kullanılabilir verilerdeki güncelleştirmeleri yansıtan değişiklikleri canlandırmayı düşünün.

- **Asla** bir kullanıcının belirli bir içerik parçası için makul olarak kabul edebileceğinden daha fazla gösterge eklemeyin. Ortam göstergeleri, kullanıcıdan herhangi bir etkileşim gerektirmeden yararlı olmalıdır. Göstergeler, taşma ve diğer yönetim denetimlerini gerektirdikleri takdirde ortamlarını kaybederler.

#### <a name="gestures"></a>Hareketler
 Kullanıcının ana içeriğe odaklanmasını sağlamanın önemli bir yönü, ek ayrıntı içeriğini açmak ve reddetmek için doğru hareketleri desteklemektir.

- **Ek** içeriği açmak için kullanıcının her zaman müstehcen bir hareket gerçekleştirmesini zorunlu kılın. Sık kullanılan açık hareketler şunlardır:

  - **Hover:** araç ipuçları veya etkileşimli olmayan bilgilendirme içeriği

  - **Açık komut:** satır içinde sunucu

  - **Ortam göstergesini çift tıklatın:** CodeLens açılır pencere

- Kullanıcı Esc tuşuna bastığında **her zaman** ayrıntı içeriğini kapatın.

- **Nesne** deki Kullanıcı Gİyi'nin bağlamını her zaman göz önünde bulundurun. Kapsayıcı içinde etkileşime izin veren içerik sunum yapan kişiler için, kullanıcının iş akışına zarar verme olasılığı yüksek olan gezinme hakkında ek bilgi gösterip göstermemeyi dikkatlice düşünün.

- **Düzenleme** yapılabilir gibi görünen veya kullanıcı etkileşimini davet eden içeriği asla gezinmede görüntülemeyin. Bir araç ipucu için standart davranış imleci üreten ana içerik üzerinde artık olduğunda hemen kapatmak için olduğu gibi, bu davranış, imleci ayrıntı içeriği üzerinde taşımak için çalışırsanız kullanıcıları hayal kırıklığına uğratabilir.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a>Seçim modelleri

### <a name="overview"></a>Genel Bakış
 Seçim modeli, kullanıcı arabirimi içindeki bir veya daha fazla ilgi çekici nesneüzerindeki işlemleri belirtmek ve onaylamak için kullanılan mekanizmadır. Bu konu Visual Studio belge editörleri içinde seçim etkileşim desenleri tartışır: metin editörleri, tasarım yüzeyleri ve modelleme yüzeyleri.

 Kullanıcılar Visual Studio'ya ne üzerinde çalıştıklarını belirtmenin bir yolunu bulabilmeli ve Visual Studio'nun kullanıcılara ne üzerinde çalıştığı hakkında geri bildirimle tahmin edilebilir bir şekilde yanıt vermesi gerekir. Kullanıcı ile kullanıcı arabirimi arasındaki farklar veya iletişim sizlik, kullanıcının istenmeyen sonuçlardoğurabilecek bir eylemi fark etmemelerine neden olabilir. Genellikle, kullanıcı bir şeyin eksik olduğunu veya değiştiğini görene kadar hata fark edilmez. Seçim modelleri bu nedenle kullanıcı arabirimi tasarımının en kritik parçalarından biridir. Visual Studio'daki seçim modelleri Windows ile tutarlı olsa da, küçük varyasyonlar vardır.

 Visual Studio'da, Windows'da olduğu gibi, seçim modelleri etkileşimin oluştuğu bağlama bağlı olarak değişir. Seçimler dört nesne türünde oluşabilir:

- Metin

- Grafik nesneleri

- Listeler ve ağaçlar

- Kılavuzlar

  Bu nesneler içinde üç tür seçim vardır:

- Bitişik

- Ayrık

- Bölge

#### <a name="scope"></a>Kapsam
 Seçimin en önemli bileşeni, kullanıcının hangi pencerede çalıştığını (etkinleştirme) ve odak noktasının (seçim) nerede bulunduğunu bilmesini sağlamaktır. Visual Studio, Windows'ta pencere yönetimi işlevini genişletir, ancak etkinleştirme düzeni aynıdır: bir pencereyle etkileşim etüt etmek pencereye odak getirir. Visual Studio'nun etkinleştirme için iki göstergesi vardır: biri belge pencereleri için, diğeri de araç pencereleri için.

 Belge pencereleri için etkin pencere, ön plana gelen ve arka plan rengini değiştiren bir belge penceresi sekmesiyle gösterilir:

 ![Visual Studio'da etkin sekme seçimi](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Etkin sekme seçimi**

 Araç pencereleri için etkin pencere, araç penceresinin başlık çubuğu alanının renginde yapılan bir değişiklikle gösterilir:

 ![Visual Studio'da etkin araç penceresi seçimi](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Bir düğümün birincil seçimini gösteren etkin araç penceresi**

 ![Visual Studio'da etkin olmayan araç penceresi seçimi](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Düğüm gizli seçimini gösteren etkin olmayan araç penceresi**

 Bir pencere etkin olduğunda, odak noktası yönergelerin bu bölümünde özetlenen seçim modellerine göre gösterilir.

#### <a name="context"></a>Bağlam
 Visual Studio, kullanıcının nerede çalıştığını takip eden güçlü bir bağlam konseptini korumak için tasarlanmıştır. Bir araç veya belge penceresi olsun, yalnızca bir pencere etkindir. Ancak, en üstteki belge penceresi her zaman gizli bir seçim tutar. Odak bir araç penceresinde olsa da, en son etkin olan belge penceresi, etkin olmayan bir durumda bile bir seçim görüntüler. Bu, kullanıcının düzenleme yaptıkları belgedeki bağlamını korumak için yapılır ve Visual Studio'nun araç pencereleri ile belge pencereleri arasında sorunsuz bir şekilde dönebilmeleri ve geçiş yapabilmeleri için durumlarını koruduğunu gösterir.

### <a name="text-selection"></a>Metin seçimi
 Yerleşik metin düzenleyicisi gibi metin seli olan Visual Studio düzenleyicileri, MSDN'deki Windows Kullanıcı Deneyimi Etkileşim Yönergeleri'nin [Fare ve İşaretçiler](/windows/desktop/uxguide/inter-mouse) sayfasında açıklanan metin seçim modelini ve görünümünü kullanır. Metin düzenleyicisindeki giriş odağı ekleme noktası olarak adlandırılan dikey bir çubukla gösterilir. Ekleme noktası, arkasında görünen her şeyin tersi olarak tek bir piksel kalınlığında ve renklidir. Denetim Masası'ndaki **Klavye** elmasının **Hız** sekmesinde **Imleç göz kırpma hızı** ayarına göre yanıp söner.

#### <a name="contiguous-and-disjoint-selection"></a>Bitişik ve ayrık seçim
 Metin düzenleyicisi içindeki seçim yalnızca bitişiktir. Ayrık metin seçimlerine izin verilmez, ancak grafik nesne sivertörlerinde ele alınmalıdır. Kullanıcının fare işaretçisi bir metin alanı üzerindeyken imleç I-ışınına dönüşür. Tek bir tıklama, ekleme noktasını metin düzenleyicisindeki tıklama konumuna yerleştirir. Fare düğmesini basılı tutmak seçim vurgusu başlatır ve fare düğmesini serbest bırakmak seçim vurgusu sona erer.

#### <a name="region-selection-box-selection"></a>Bölge seçimi (kutu seçimi)
 Visual Studio metin düzenleyicisindeki bölge seçimlerini destekler ve buna kutu seçimi denir. Kutu seçimi, kullanıcının normal metin akışını izlemeyen bir metin bölgesi seçmesine olanak tanır. Standart metin seçiminde olduğu gibi, seçim bitişik olmalıdır. Kutu seçimi fare ile sürüklerken Alt tuşunu basılı tutarak başlatılır. Kutu seçimi, seçim bölgesini belirtmek için ok tuşlarını kullanırken Alt ve Shift tuşlarını basılı tutarak da başlatılabilir. Kutu seçimi normal seçim vurgusu kullanır ve ekleme noktası imlecini seçim alanının sonunda yanıp söner.

 ![Visual Studio'da bölgesel &#40;kutusu&#41; seçimi](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Visual Studio'da bölge (kutu) seçimi**

#### <a name="text-selection-appearance"></a>Metin seçimi görünümü
 Düzenleyicide etkin ve etkin olmayan seçim için kullanılan renkler özelleştirilebilir. Editörün görsel görünümünü özelleştirmek için, bir kullanıcı **Araçlar > Seçenekleri'ne**gidebilir ve ardından **Metin Düzenleyicisi'> Çevre > Yazı Tipleri ve Renkler'in**altına bakabilir.

### <a name="graphical-selection"></a>Grafik seçimi

#### <a name="interaction"></a>Etkileşim
 Grafik nesne seçimi karmaşık olabilir ve bir dizi etkene bağlıdır:

- **Editörün birincil seçim modeli.** Grafik nesneleri içeren düzenleyiciler, metni veya ızgaraları da kullanılabilir. Örneğin, düzenleyici, Visual Studio XAML tasarımcısı gibi grafik nesnelerin yerleşimini de destekleyen metin tabanlı bir düzenleyici olabilir. Birden çok nesne türünü desteklemek, kullanıcının farklı nesne türlerinden oluşan grupları seçme şeklini etkileyebilir.

- **Birincil ve ikincil seçim durumları için destek.** Düzenleyici, nesnelerin bir arada düzenlenebilmesi, birbiriyle hizalanabilmesi, birlikte yeniden boyutlandırılabilmeleri ve benzerleri için birincil ve ikincil seçim durumları sağlayabilir.

- **Yerinde düzenleme desteği.** Düzenleyiciler ayrıca grafik nesnelerinin içeriğinin düzenlenmesine de izin verebilir. Örneğin, dikdörtgen şekli de kullanıcı tarafından değiştirilebilir içinde metin içerebilir. Ayrıca, bu metin ortalanmış veya haklı olabilir. Yerinde düzenleme, kullanıcı etkileşiminin daha ayrıntılı bir düzeyini içerir ve bu nedenle duruma durum bilgilerini kullanıcıya sunmak için uygun bir görsel ipucu kümesi gerektirir.

#### <a name="mouse-interaction"></a>Fare etkileşimi

|Giriş|Sonuç|
|-----------|------------|
|Seçili olmayan bir nesneyi tıklatın|Nesne yeniden boyutlandırılabilirse nesneyi seçer ve kesik çizgili bir çizgi ve seçim tutamaçları görüntüler.|
|Seçili nesneyi tıklatın|Nesne destekliyorsa yerinde düzenlemeyi etkinleştirir. Nesnenin dışında tıklatıldığında, yerinde düzenleme modu devre dışı bırakılır.|
|Nesneyi çift tıklatma|Düzenleme için nesnenin arkasındaki kodu açar ve uygunsa varsayılan olay işleyicisi ekleyebilirsiniz.|
|Nesneye işaret etme|İşaretçiyi hareket imleciyle değiştirir. Nesnenin parlaklığı veya rengi gibi görünümü değişebilir.|
|Seçim tutamacını işaret etme|İşaretçiyi yeniden boyutlandırma imleciyle değiştirir. Döndürmeyi destekleyen nesneler için, bazı seçim tutamaçları, işaretçi seçim tanıtıcısına göre farklı olarak konumlandırılınca (örneğin, daha uzağa taşındı) işaretçiyi döndürebilir imleç olarak değiştirebilir.|
|Sürükleyin|Nesne önceden seçilmemiş olsa bile, işaretçiyi hareket imlecine değiştirir ve nesneyi hareket ettirir.|
|Editör odak kaybeder|Nesne son işlem/seçim durumu sırasında sahip olduğu içeriği ve görünümü korusa da yerinde düzenleme modunu devre dışı bırakır.|
|Nesne seçimi|Nesnenin sınırını vurgulamak için kenarlık, noktalı çizgi veya diğer görsel olarak farklı bir işlemle gösterilir.|
|Seçili nesneyi yeniden boyutlandırma|Seçim tutamaçlarıyla gösterilir.<br /><br /> Yeniden boyutlandırılabilir nesnenin yeniden boyutlandırılabildiği her yönü temsil eden sekiz tutamağı vardır. Nesne yalnızca belirli yönlerde yeniden boyutlandırılabilirse, daha az tanıtıcı kullanılabilir. Kullanıcı bir nesneyi sekiz tutamacın etkileşimli olmadığı bir yere küçülttüğünde, dört tutamaç kullanılabilir. Tanıtıcı **boyutları, GetSystemMetrics** API işleviyle ekran çözünürlüğüyle orantılı boyuta göre pencere kenarve kenar ölçümlerine bağlanmalıdır.<br /><br /> ![Tutamaçları yeniden boyutlandırma](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Seçili nesneyi döndürme|![Tutamaçları döndürme](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Klavye etkileşimi

|Giriş|Sonuç|
|-----------|------------|
|Tab|Odak göstergesini düzenleyicideki nesnelerin mantıksal sırası arasında taşır. Bu, **TabIndex** (veya eşdeğeri) özellik değerine, nesne oluşturma sırasına ve düzenleyicinin genel amacına bağlı olarak soldan sağa veya yukarıdan aşağıya olabilir. Shift+Tab, odak göstergesinin yönünü tersine çevirir.|
|Boşluk çubuğu|Tuş vuruşu korunurken kaydırma modunu etkinleştirir. Viewport konumunu kaydırmak için ek fare girişi gereklidir.|
|Ctrl+Ara Çubuğu|Tuş vuruşu korunurken yakınlaştırma modunu etkinleştirir. Yakınlaştırma faktörlerini artırmak ve azaltmak için ek fare girişi gereklidir.|
|Ctrl+Alt+Eksi İşareti|Yakınlaştırma faktörlerini bir seviye azaltır.|
|Ctrl+Alt+Artı İşareti|Yakınlaştırma faktörlerini bir seviye artırır.|
|Shift VEYA Ctrl|Nesneyi seçim grubuna ekler. Ctrl ayrıca nesneleri seçim grubundan tek tek kaldırmanızı sağlar.|
|Enter|Nesne için varsayılan komutu gerçekleştirir (genellikle Aç veya Edit).|
|F2|Nesne için yerinde düzenlemeyi etkinleştirir.|
|Ok tuşları|Seçili nesne(ler) ok tuşuna basıldığında, küçük artışlarla (örneğin, bir seferde 1 piksel) doğru hareket ettirir|
|Ctrl+ok tuşları|Seçili nesne(ler) ok tuşuna basıldığında, daha büyük artışlarla (örneğin, bir seferde 10 piksel) doğru hareket ettirir|
|Shift+ok tuşları|Seçili nesne(ler) küçük artışlarla (örneğin, bir seferde 1 piksel) ilgili yönde yeniden boyutlar|
|Ctrl+Shift+ok tuşları|Seçili nesne(ler) ilgili yönde, daha büyük artışlarla (örneğin, bir seferde 10 piksel) yeniden boyutlar|

 Kullanıcılar denetimleri yerinde olarak edindiğinde, nesnelerin kullanıcı girişiyle otomatik olarak yeniden boyutlandırması mantıklı olabilir. Örneğin, kullanıcı bir etiket denetimini yeniden kurarsa, etiketin kullanıcının yazdığı metni görüntülemek için büyümesi gerekir. Bu yapılmazsa, kullanıcı metni düzenlemeden sonra denetimi el ile yeniden boyutlandırmalıdır. Kullanıcının çok fazla denetimi varsa, bu bir çürük ve verimsiz bir görev haline gelir.

#### <a name="graphical-containers"></a>Grafik kaplar
 Bazı durumlarda, grafik düzenleyiciler, HTML tasarımcısındaki Windows Forms Panel denetimi veya Izgara Düzeni denetimi gibi diğer grafik nesneler için kapsayıcılar sağlar. Düzenleyiciniz diğer grafik nesneler için kapsayıcılar sağlıyorsa, yalnızca kapsayıcı için aşağıdaki seçim modeli kullanılmalıdır (kapsayıcıiçindeki nesneler yukarıda açıklandığı gibi standart modeli izler):

|Giriş|Sonuç|
|-----------|------------|
|Konteynerin üzerine tek tıklama|İçerdiği nesnelerden herhangi birini doğrudan seçmeden kapsayıcı nesnesini seçer. Kapsayıcı taşınabilir ve/veya standart fare ve klavye girişiyle yeniden boyutlandırılabilir (yukarıda açıklandığı gibi). İçe bulunan nesneler kapsayıcıya göre taşınır, ancak içerdiği nesneler de doğrudan seçilmedikçe yeniden boyutlandırılmez.|
|Konteynerin sınır bölgesinin üzerinde gezinme|Fareyi, kapsayıcının hareket ettirebileceğini belirten hareket imlecine dönüştürür.|
|Kapsayıcının sınır bölgesini sürükleyin|Fareyi hareket imleciyle değiştirir ve kapsayıcıyı (ve içindeki nesneleri) hareket ettirir. Kapsayıcı ilk tek bir tıklama ile seçilmeden hareket ettirilemez.|
|Kapsayıcı içindeki bir nesneye tek tıklama|Kapsayıcıyı (seçilirse) seçer ve yalnızca tıklatılan nesneyi seçer.|
|Shift+click OR Ctrl+tıklatıldığında bulunan bir nesneye ve/veya kapsayıcıya|Tıklatılan nesneyi varolan bir seçim veya seçim grubuna ekler. Tıklatılan nesne zaten seçim grubunun bir üyesiyse, seçim grubundan kaldırılır.|

 İçerdiği nesneler, önceki bölümde açıklandığı gibi temel seçim modeline uymalıdır. Windows Forms tasarımcısının kullanılabilirlik testinden, kullanıcılar dahil edilen nesnelere müdahale adımları olmadan (çevreleme nesnesi tarafından dayatılan) sorunsuz erişim beklerler.

#### <a name="disjoint-and-region-selections"></a>Ayrışma ve bölge seçimleri
 Grafik nesne düzenleyicileri ayrık seçimleri desteklemelidir. Bu grafiğin Visual Studio için kontrol görünümünü göstermediğini lütfen unutmayın. Ayrıntılı görsel özellikler için [Grafik nesne seçimi görünümüne](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) bakın.

 ![Ayrık ve bölge seçicileri](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Ayrık seçimi**

 Grafik düzenleyiciler de bir seçim çerçevesi türü seçim göstergesi ile bölge seçimleri sağlamalıdır. Grafik düzenleyicidiğer nesne türlerini (metin gibi) destekliyorsa, bu diğer nesne türlerinin kısıtlamalarına bağlı olarak bölge seçimleri mümkün olmayabilir.

 ![Seçim çerçevesi seçimi](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Seçim çerçevesi seçimi**

#### <a name="primary-and-secondary-selections"></a>Birincil ve ikincil seçimler
 Bazı grafik nesne düzenleyicileri, kullanıcının nesneleri gruplar halinde düzenlenmesine veya hizalayabilmesine olanak sağlar. Bu durumda, birincil ve ikincil seçimler kavramının tanıtılması gerekir. Birincil seçim, diğer tüm nesnelerin grup işlemleri için yanıtladığı nesnedir. Kullanıcının ilk seçtiği nesne birincil denetim olur ve sonraki seçimler ikincil seçimler olur. Birincil seçim, hangi nesnenin birincil olduğunu belirtmek için ikincil seçimden(ler) farklı bir görsel tedaviye sahiptir:

 ![Birincil ve ikincil seçim](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **İki ikincil seçkiile birincil seçim**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a>Grafiksel nesne seçimi görünümü
 Seçim tutamaçları, nesnenin sınırlayıcı kutusunun etrafında dikdörtgen bir desenle çizilmiş karelerdir. Aşağıdaki grafikte, grafik nesnesinin tutamaç, boyutlandırma ve yerinde düzenleme görünümüyle sahip olabileceği çeşitli durumların örnekleri gösterilmektedir. Tanıtıcıların **boyutu, GetSystemMetrics** API kullanılarak pencere kenarlığı ve kenar ölçümlerine bağlanmalıdır.

| Durum | Görünüm | Görsel ayrıntılar |
|-------------------------|---------------| - |
| **Seçili** | Varsayılan | ![Varsayılan düğme durumu](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Birincil seçim** | Resizable | ![Yeniden boyutlandırma tutamaçlarına sahip birincil seçim](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Birincil seçim** | Yeniden boyutlandırılamaz | ![Yeniden boyutlandırma tutamaçları olmadan birincil seçim](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Birincil seçim** | Kilitli | ![Birincil seçim kilitlendi](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **İkincil seçim** | Resizable | ![Yeniden boyutlandırma tutamaçları yla ikincil seçim](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **İkincil seçim** | Yeniden boyutlandırılamaz | ![Yeniden boyutlandırma tutamaçları olmadan ikincil seçim](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **İkincil seçim** | Kilitli | ![İkincil seçim kilitlendi](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **UI etkin** | Varsayılan | ![UI etkin durumu](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Seçim modellerini görüntüleme

#### <a name="tree-view"></a>Ağaç görünümü
 Ağaç görünümünde seçim basit bir vurguyla gösterilir. Kullanıcı bir düğüm adını veya düğüm simgesini tıklatırsa, düğüm seçilir. Düğümün solundaki üçgen glifler ağaç denetimini genişletir veya daraltır, ancak bir istisna dışında kullanıcının seçimini etkilemez: seçim düğümün bir alt öğesi üzerindeyken bir üst düğümün daraltLanması üzerine, seçim üst öğeye taşınır.

 ![Visual Studio'da tipik ağaç görünümü](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Visual Studio'da tipik ağaç görünümü**

 Ağaç görünümleri bitişik ve ayrık seçimleri destekleyebilir, hatta ağaçtaki birden çok düzeyde bile. Bitişik veya ayrık birden fazla seçim görünür ağaç düğümleri üzerinde yapılmalıdır. Bir düğüm daraltılırsa, ayrık seçim kaybolur ve daraltılen düğüm seçimi elde eder. Bu şekilde, kullanıcı bir işlemden etkilenecek düğümleri görebilir. Düğümler daraltıldığında, hangi düğümlerin etkilenebileceği belirsizleşir.

 Bir üst düğüm seçildiğinde, bir işlemin üst öğeye ve tüm çocuklarına uygulanmasının mantıklı olduğu durumlar olsa da, işlem üst öğeiçin geçerli olmalıdır. Bu durumda, "tüm çocuklara uygula" seçeneğini kullanıcıya açık hale getirmek için işlem sırasında onay kutusu veya onay iletişim kutusu gibi ek kullanıcı arası bilgi aracı sağlayın.

##### <a name="renaming"></a>Yeni -den adlandırma
 Ağaçtaki düğümler yeniden adlandırmayı destekliyorsa, yeniden adlandırma yerinde yapılmalıdır. Yerinde çalışma Visual Studio tüm ağaç kontrolleri arasında standart olmalıdır. Kullanıcı girişini kabul etmeye hazır, düğümün tüm adını kapsayan metin seçimiyle yerinde düzenleme modunu hemen etkinleştiren bir yeniden adlandırma komutu sağlayın. Düğüm bir dosyayı temsil ederse, dosya adı uzantıyı içermelidir. Seçim vurgusu uzantıyı değil, yalnızca dosya adının gövdesini içermelidir.

|Giriş|Sonuç|
|-----------|------------|
|Enter tuşu|Yeniden adlandırma işlemini işler|
|Esc tuşu|Yeniden adlandırma işlemini iptal eder|
|Yerinde edit bölgesinin dışında tıklatma|Yeniden adlandırma işlemini işler|
|Geri al|Yeniden adlandırma işlemini iptal etmek için kolay geri al sağlama|

#### <a name="selection-within-lists-and-grid-controls"></a>Listeler ve ızgara denetimleri içinde seçim
 Liste seçiminde anahtar kavram satır tabanlı olmasıdır, yani bir seçim yapıldığında tüm satır birim olarak seçilir. Bunun aksine, ızgaralar satırın başka bir yönünü etkilemeden belirli hücrelerin seçilmesine izin verebilir. Izgaralar, hiyerarşinin tüm dallarının ana satırlarla etkileşim edilince seçilip seçilmemesine izin veren iç içe doğru sıralar (TreeGrid gibi) bir hiyerarşi de içerebilir. Listelerdeki seçim, tüm veri satırında basit bir vurgu rengiyle gösterilir. Odak, geçerli editable satır veya hücre etrafında tek piksel noktalı kenarlık tarafından gösterilir (tüm hücreler okunursa satır).

> [!NOTE]
> **Odak** ve **seçim** farklı kavramlardır. *Odak,* ui öğesinin açıkça başka bir nesneye yönlendirilmeyen girdi almayı hedeflediği bir göstergeyken, *seçim,* bir nesnenin sonraki işlemlerin gerçekleşebileceği bir nesne kümesine dahil edilmesinin durumuna işaret eder.

 Listelerdeki seçimler bitişik, ayrı kıvranan veya bölge olabilir. Birden çok seçime izin verildiğinde, bitişik ve ayrık seçim her zaman desteklenmelidir, bölge (kutu) seçimleri için destek isteğe bağlıdır. Bölge seçimleri, liste gövdesinin beyaz alanında sürükleyerek başlatılır.

| Nesne | Seçim |
|--------|------------|
| Liste | Bitişik |
| Liste | Ayrık |
| Liste | Bölge |

 Listede bir kez tıklattığınızda, tıklamanın oluştuğu satır seçilir. Kullanıcı yerinde düzenlemeyi destekleyen bir liste hücresinde tıklarsa, hücre yerinde düzenleme için de hemen etkinleştirilir. Aksi takdirde, tüm satır hemen seçilir ve bir vurgu gösterir.

 Liste gövdesinde sürüklemek üç şeyden birini yapar:

- Liste destekliyorsa ve fare aşağı beyaz boşluktaysa bölge seçimini başlatır

- Liste hücresi veya satır sürükleme kaynağı olmayı destekliyorsa sürükle/bırak işlemini başlatır

- Geçerli satırı seçer

##### <a name="in-place-editing"></a>Yerinde düzenleme
 Yerinde düzenlemeye izin verildiğinde, iki temel model vardır: basit düzenleme denetimi ve özellik seçici. Basit bir düzenleme denetimi yle içerik vurgulanır ve yerinde düzenleme etkinleştirilir etkinleştirilmez kullanıcı girişine hazır hale getirilir. Bir özellik seçicinin uygulandığı durumlarda, yerinde düzenleme modu etkinleştirildiğinde özellik seçiciyi çağıran düğme görüntülenir ve geçerli seçim vurgulanmaz. Toplayıcı düğmesi hücrede doğru olarak doğru olmalıdır. Yerinde düzenleme örnekleri için Visual Studio'daki **Özellikler Penceresi** ve **Görev Listesi'ne** bakın.

##### <a name="keyboard-support"></a>Klavye desteği
 Listelerde ve ızgaralarda seçim için klavye desteği standart Windows kurallarını izler:

- Ok tuşları, odak hareket ettikçe her satır/hücreyi seçerek listede gezinir.

- Shift + ok ok tuşları yönünde bitişik bir seçim gerçekleştirir.

- Ctrl + ok ardından Spacebar, liste öğelerini seçimden ekleme ve kaldırma arasında geçiş yaparak ayrı bir seçim oluşturur.

- İç içe hiyerarşileri içeren ızgaralar için Sağ Ok tuşu üst satırı genişletir ve Sol Ok tuşu bir satırı daraltılır.

- Sekme tuşu, hücreler değiştirilebilirse, geçerli satırdaki hücreler arasında odağı taşır.

- Enter tuşu listedeki öğedeki varsayılan komutu gerçekleştirir (genellikle **Aç).**

- F2 tuşu, seçili hücre için yerinde düzenlemeyi etkinleştirir.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a>Kalıcılık ve kaydetme ayarları

### <a name="overview"></a>Genel Bakış
 Visual Studio'daki her yazılım bileşeni genellikle kendi durumundan ve kalıcılığından sorumlu olsa da, Visual Studio bazı durumlarda pencere boyutları ve konumları gibi ayarları otomatik olarak kaydeder. Aşağıdaki tablo, otomatik olarak kaydedilen ayarların ve açık bir kullanıcının veya programlanmış bir eylemin yapılmasını gerektiren ayarların bir birleşimidir.

|Nesne|Kaydetmek için gerekenler|Ne zaman kaydedebilirsiniz|Nerede kaydedebilirsiniz|
|------------|------------------|------------------|-------------------|
|Seçilebilir nesne (örneğin, bir kod satırı)|Kod satırında kesme noktası<br /><br /> Kod satırı ile ilişkili bir kullanıcı kısayolu|Proje kaydedildiğinde|Proje için **kullanıcı seçenekleri (.suo)** dosyası|
|Iletişim|Taşınmışsa iletişim kutusunun konumu<br /><br /> Kullanıcının iletişim kutusunda en son kullandığı görünüm|İletişim kapatıldığında<br /><br /> Visual Studio oturumu sona erdiğinde|Bellekte<br /><br /> **HKEY_Current_User'da** kayıt defteri|
|Pencere|Pencerenin boyutu ve konumu|Pencere kapandığında<br /><br /> Visual Studio modu değiştiğinde<br /><br /> Visual Studio oturumu sona erdiğinde|Proje için **kullanıcı seçenekleri (.suo)** dosyası<br /><br /> Pencere ayarları için özel seçenekler dosyası|
|Belge|Belgedeki geçerli seçim<br /><br /> Belgenin görünümü<br /><br /> Kullanıcının ziyaret ettiği son birkaç yer|Belge kaydedildiğinde|Proje için **kullanıcı seçenekleri (.suo)** dosyası|
|Project|Dosyalara başvurular<br /><br /> Diskteki dizinlere başvurular<br /><br /> Diğer yazılımlara yapılan atıflar<br /><br /> Bileşenler<br /><br /> Projenin kendisi hakkında devlet bilgileri|Proje kaydedildiğinde|Proje dosyası|
|Çözüm|Projelere yapılan atıflar<br /><br /> Dosyalara başvurular|Proje veya çözüm kaydedildiğinde|**Çözüm (.sln)** dosyası|
|**Araçlardaki** Ayarlar > Seçenekleri|Klavye özelleştirmeleri<br /><br /> Araç çubuğu özelleştirmeleri<br /><br /> Renk şemaları|Araçlar **> Seçenekleri** iletişim kutusu kapandığında<br /><br /> Visual Studio oturumu sona erdiğinde|**HKEY_Current_User'da** kayıt defteri|

 Kullanıcının ne yaptığı ve bunu yaparken, bir ayarın bellekte (oturum sırasında) kaydedilip kaydedilmediğini, diske kaydedilip kaydedilmeyeceğini (kayıt defteri ayarı olarak oturumlar arasında), proje veya çözüm dosyasının bir parçası olarak, **çözüm seçenekleri (.suo)** dosyasının bir parçası olarak mı yoksa yalnızca yazılım bileşeninin bildiği özel ayarlar dosyası olarak mı belirler. Yukarıdaki tabloda ayarların kaydedilebildiği çeşitli olaylar gösterilmektedir. Ancak, durumu kaydetmek isteyebileceğin başka zamanlar da vardır:

- Kullanıcı bir iletişim kutusu veya pencere içinde konumunu değiştirdiğinde

- Kullanıcı odağı başka bir pencereye aktardığında

- Kullanıcı tasarımdan hata ayıklama moduna geçtiğinde

- Kullanıcı hesabını kapattığınızda

- Bilgisayar hazırda beklemeye girdiğinde veya kapandığında

- Bilgisayar/sabit disk yeniden biçimlendirilip yeniden kurulmak üzereyken

### <a name="window-configurations"></a>Pencere yapılandırmaları
 Pencere yapılandırması geliştirme ortamının temel sunumudur - mevcut araç pencerelerinin listesini ve bunların düzenlenme biçimini içeren bir şemadır. IDE (IDE pencereleri) tarafından yönetilen pencereleriçin, düzen bilgileri kullanıcı başına kalıcıdır, böylece bir kullanıcı IDE'yi başlattığında, pencere düzeni Visual Studio'dan son çıktıkları zamanki yle aynı görünür. IDE pencerelerinin durumu ve konumu XML biçiminde özel bir seçenek dosyasında kalıcıdır. IDE'ye yüklenen paketler tarafından oluşturulan araç pencereleri, durum bilgilerini kayıt defterinde devam ettirir ve kullanıcı başına olabilir veya olmayabilir.

#### <a name="profile-specific-layouts"></a>Profile özel düzenler
 Her profil, belirli geliştirici kişiliklerine tanıdık şekilde düzenlenmiş araç penceresi düzenleri içerir (Visual C++ geliştiricileri IDE'nin sol tarafında **Çözüm Gezgini'ni** görmeyi beklerken, C# geliştiricileri sol tarafta Çözüm **Gezgini'ni** görmeyi beklerler). Kullanıcı başlangıç profili seçtikten sonra profile özel pencere düzenleri yüklenir. Paket yazarı, kullanıcının pencere yapılandırmasına yaptığı değişikliklerin daha sonra kalıcı olacağını bilerek, müşterilerinin deneyimine en uygun pencere düzenini belirlemelidir.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a>Dokunma girişi
 Kullanıcılar dokunma cihazlarında Microsoft geliştirme ürünlerini giderek daha fazla kullanıyor. Ancak, dokunma aygıtlarında geliştirme araçlarının kullanılmasını zorlaştıran engeller vardır. Kullanıcılar ürünlerimizin güvenilir ve hassas bir dokunma deneyimi sağlamasını bekleyecektir. Bu yönergelerin amacı, Visual Studio ve ilgili ürünler de tutarlı bir dokunma deneyimi sağlamak ve hangi dokunmatik yetenekleri dahil etmek hakkında kararları bilgilendirmektir.

### <a name="levels-of-experience"></a>Deneyim düzeyleri
 Aşağıdaki deneyim düzeyleri, ekiplerin iletişimde istedikleri yatırım ilgisine bağlı olarak hangi dokunma yeteneklerini sunacaklarına karar vermelerine yardımcı olmak için bir kılavuz olarak tasarlanmıştır.

- **Temel deneyim,** çalışmaları boyunca çıkmaz alabilmeniz için dokunma özellikleri sağlamak isteyen ekipler içindir.

- **En iyi duruma getirilmiş deneyim,** en yaygın dokunma özelliklerini sağlamak isteyen takımlar içindir (örneğin, bunlar genellikle internet tarayıcısı uygulamalarında kullanılabilir).

- **Yükseltilmiş deneyim,** hareketlerini veya uygulamalarını ilk önce dostu hale getirebilecek diğer isteğe bağlı özellikler gibi özellikler eklemek isteyen ekipler içindir.

||Temel deneyim|Optimize edilmiş deneyim|Yüksek deneyim|
|-|----------------------|--------------------------|-------------------------|
|Kullanıcıların ...|Çıkmaz olmadan kodu ve çözüm/proje düzeyinde okumayı düzeltme|Bakım, refaktör ve gezinme görevlerini gerçekleştirin|Tutarlı, sezgisel ve akıcı bir deneyimle güvenle çalışır|
|Düzenleyici|Dokunma kaydırma ve seçim<br /><br /> Atlamak ve +sürükleme tuşuna basmak için scrollbar dokunuşu|Sıkıştırma yakınlaştırma<br /><br /> Hızlı kaydırma<br /><br /> Seçim<br /><br /> Bağlam menüsünün kolay kullanımı||
|Üst takım pencereleri|Liste kaydırma<br /><br /> Madde seçimi<br /><br /> Atlamak ve +sürükleme tuşuna basmak için scrollbar dokunuşu|Kolay öğe kaydırma ve seçim||
|Pencereleme||Pencereyi yeniden boyutlandırma<br /><br /> Hızlı erişim||
|Belge iyi||Açık dosyalar arasında kolay gezinme||
|Hareketler||IDE genelinde yaygın hareketlerin çalışmasını sağlayın|Hareket tabanlı eylemler<br /><br /> Sürükle ve bırak ve tasarımcıları destekle|
|Diğer konular|||Özel ekran klavyesi|

#### <a name="gestures"></a>Hareketler
 Hareketler, kullanıcılara aksi takdirde daha karmaşık bir etkileşim gerektirebilecek komutlar için bir kısayol sağlar. Masaüstü Uygulamaları için [ortak dokunma hareketleri](/windows/desktop/wintouch/windows-touch-gestures-overview)yle ilgili Windows yönergelerine bakın ve kaydırma ve yakınlaştırma gibi basit hareketler de dahil olmak üzere çoğu hareket için bu kılavuzu izleyin.
