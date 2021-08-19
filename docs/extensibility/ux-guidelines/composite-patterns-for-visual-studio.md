---
title: Visual Studio | için Bileşik Desenler Microsoft Docs
description: Verilerde tutarlılık için önemli bileşik desenler hakkında Visual Studio. Bileşik desenler etkileşim ve tasarım öğelerini birleştirir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c32ff32a0462d38cfae66dbc9ec5c2566f18b1fc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158170"
---
# <a name="composite-patterns-for-visual-studio"></a>Visual Studio İçin Bileşik Desenler
Bileşik desenler, etkileşim ve tasarım öğelerini ayrı yapılandırmalarda birleştirir. Tutarlılık açısından en önemli bileşik Visual Studio bazıları şunlardır:

- [Veri görselleştirme](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Nesne kullanıcı arabirimi ve göz atma](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Seçim modelleri](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Kalıcılık ve ayarları kaydetme](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Dokunma girişi](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a> Veri görselleştirme

### <a name="overview"></a>Genel Bakış
 Grafikler, karar verme kararını geliştirmek için verileri toplamak ve görselleştirmek için görsel bir yol sağlar. Bu, kullanıcıların çok fazla veriyle karşı karşıya kalan ancak çok az anlamı olan dikkati ve eylem gerektirenleri görmelerini sağlar.

 Aşağıdaki koşullardan herhangi biri doğruysa kullanıcı grafikten yararlanabilir:

- Grafik, kullanıcıların eyleme geçecekleri görevleri tanımlamanıza yardımcı olacak mı?

- Grafik kullanıcıların olası değişikliklerin sonuçlarını tahmin değiştirmelerine olanak sağlayacak mı?

- Grafik kullanıcıların eğilimleri keşfetmelerini ve desenleri tanımlamalarını sağlar mı?

- Grafik kullanıcıların daha iyi kararlar almalarına izin verecek mi?

- Grafik, kullanıcıların belirli bir bağlamda sahip olduğu belirli bir soruyu yanıtlamaya yardımcı olacak mı?

#### <a name="general-rules-for-charts"></a>Grafikler için genel kurallar

- Verileri net bir şekilde etiketle. Açıklama olmayan çizimler yalnızca güzel resimlerdir.

- Eksenleri sıfırdan başlatarak orantılardan kaçının. Çizgi uzunluğu ve çubuk boyutu, veri noktaları arasındaki ilişkileri anlamanız için önemli görsel ipuçlarıdır.

- Bilgi grafiği değil grafik oluşturma. Bilgi grafiği, verilerin temsili temsilleridir ve asıl hedefi görsel hikaye anlatmadır. Grafikler görsel olarak çekici olabilir (ve öyle olmalı), ancak verilerin kendisi için konuşmasına izin ver.

- Skeumorphism, resimsel çubuk graflar, karşıtlık diyez işaretleri ve diğer bilgi grafiği dokunmalarından kaçının.

- 3D etkileri dekoratif bir öğe olarak kullanma. Bunları yalnızca kullanıcının bilgileri anlama becerisinin gerçekten ayrılmaz bir parçası ise kullanın.

- İkiden fazla renk bu tür grafiklerin doğru okunması ve yorumlanmasına neden olarak birden fazla çizgi ve dolgu kullanmaktan kaçının.

- Bir kavramı anlamanın veya verilerle etkileşim kurmanın tek anlamı olarak grafik (veya çizim) kullanmayın. Bu, görme bozukluğu olan kullanıcılar için zorluklara neden olur.

- Grafikleri sayfada gratuit veya dekoratif öğeler olarak kullanma. Başka bir deyişle grafik herhangi bir değer eklemez veya kullanıcıların bir sorunu çözmelerine yardımcı olursa bunu kullanmaz.

### <a name="chart-types"></a>Grafik türleri
 Visual Studio grafik türleri arasında çubuk grafikler, çizgi grafikler, halka grafik veya "halka grafik" olarak bilinen değiştirilmiş pasta grafiği, zaman çizelgeleri, dağılım çizimleri ("küme grafikleri" olarak da bilinir) ve Gantt grafikleri yer almaktadır. Her grafik türü, farklı türlerde bilgilerin iletişim kurması için kullanışlıdır.

### <a name="other-charting-considerations"></a>Grafikte dikkat edilmesi gereken diğer noktalar

#### <a name="color"></a>Renk
 Grafik renklerinin belirli bir paleti, grafik renklerinde kullanım için Visual Studio. Ana renk körlüğü türleri için palete erişilebilir ve çok dar renk dilimleri olarak kullanıla bile renkler birbirinden ayırt edilir. Bu renkleri kullanıcı arabiriminizin herhangi bir türü için herhangi bir grafik veya grafik birleşiminde kullanabilirsiniz. Bu kadar farklı renklere ihtiyacınız yoksa yedi rengin hepsini de kullanmak zorunda değildir. Bu renkler ön plan öğeleriyle birlikte kullanılacak şekilde tasarlanmayarak, bu renklerin üzerine metin veya yazı yazıları eklemez. Bu tonlar sabit kodlu olmalı ve Araçlar ve Seçenekler altında **kullanıcı özelleştirmesi > açık olmalı** (bkz. Son kullanıcılar için renkleri açığa [çıkarma).](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)

|Swatch|Onaltılık|RGB|
|------------|---------|---------|
|![Swatch 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113,178,82|
|![Swatch BF3F00](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191,63,0|
|![Swatch FCB714](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252,183,20|
|![Swatch 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144,63,139|
|![Swatch 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17,122,209|
|![Swatch 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121,215,242|
|![Swatch B5B5B5](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181,181,181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Nesne kullanıcı arabirimi ve göz atma
 Bu bölümde, koda göz atma görünümü olarak da bilinen göz atma bağlamı ve bu görünüme özel nesne kullanıcı arabirimi Visual Studio.

### <a name="overview"></a>Genel Bakış

- Nesne kullanıcı arabirimi, kullanıcıya ana görevinin dışında kalmadan daha fazla bilgi veya etkileşim ver olmalıdır.

- Kullanıcı arabiriminde nesne kullanıcı arabiriminin Visual Studio", "dikkat noktasındaki bilgiler" olarak bilinir.

- Uygulama içinde nesne kullanıcı Visual Studio satır içi veya kayan ve dayanıklı ya da geçicidir.

  - Bir nesne kullanıcı arabirimi türü olan koda göz atma görünümü Visual Studio ve dayanıklıdır.

  - Visual Studio nesne kullanıcı arabirimi türü olan CodeLens kayan ve geçici

  Bir kodun nasıl çalıştığını anlamak veya bu kodla ilgili ayrıntıları bulmak için genellikle bir geliştiricinin bağlamı değiştirmesi ve başka bir içeriğe veya başka bir pencereye gitmeleri gerekir. Bu bağlam değişimleri kesintiye neden olabilir çünkü kullanıcılar ana penceresinden çıksalar özgün görevlerine odaklanamaz. Ayrıca özgün bağlamı geri almak, özellikle de pencere değiştirmenin özgün kodunun diğer kullanıcı arabirimi tarafından karartmaya neden olması durumlarında zor olabilir.

  Nesne kullanıcı arabirimi " dikkat noktasında bilgi" adlı bir desen izler. Bu iletiler, açılır pencereler ve iletişim kutuları, kullanıcılara ana görevlerine odaklanmadan açıklama veya etkileşim ekleyen ek, ilgili bilgiler sağlar. Nesne kullanıcı arabirimi örnekleri arasında, bir kullanıcı işaretçisini bildirim alanında bir simgenin üzerine geldiğinde görünen açılır pencereler, yanlış yazılmış bir sözcüğün altındaki kırmızı çizgi ve kullanıcı arabiriminde ortaya Visual Studio 2013.

### <a name="decision-points"></a>Karar noktaları
 Bu Visual Studio, dikkat noktasında bu bilgi desenini kullanmanın birkaç yolu vardır. Doğru mekanizmayı seçmek ve tutarlı ve öngörülebilir bir şekilde uygulamak, genel deneyim için çok önemlidir. Aksi takdirde, kullanıcılara, odağı içeriğin kendisinden alan kafa karıştırıcı veya tutarsız bir deneyimle karşılanabilirsiniz.

#### <a name="relationships-between-master-and-detail-content"></a>Ana ve ayrıntı içeriği arasındaki ilişkiler
 Dikkat noktasındaki bilgiler, kullanıcının odaklanmış olduğu içerikler ("ana" içerik) ve diğer ilgili içerikler ("ayrıntı" içeriği) arasındaki ilişkiyi görüntülemek için kullanılır. Bu desende ayrıntı içeriği, kullanıcının üzerinde çalıştığı içerikle net bir şekilde ilişkili olur ve ana içeriğin yakınında görüntülenebilir. Ana içerik yoğun olmadan özetlemesi mümkün olmayan ek bilgiler veya bilgiler, araç penceresi gibi başka bir desene uyması gerekir.

- **Ayrıntı** içeriğini her zaman ana içeriğe yakın bir şekilde görüntüleme.

- **Ayrıntı** içeriğinin her zaman kullanıcının ana içeriğe odaklanmaya devamını sağlar. Bunu başarmanın en iyi yolu genellikle ayrıntı içeriğini ana içeriğe mümkün olduğunca yakın şekilde işlemektir. Bu, ayrıntı içeriğini ana içeriğin yanındaki bir açılır pencerede işerek veya ana içeriğin altında satır içi olarak işerek yapılabilir.

- **Hiçbir** zaman dikkat noktasında, kullanıcının ana içerikten uzaklaşan bilgileri kullanma. Kullanıcıların ayrıntı içeriğini ayrı olarak görüntülemesi gerekirse, kullanıcının bunu yapmalarına olanak sağlayan açık bir eylemi ortaya çıkarma.

#### <a name="design-details"></a>Tasarım ayrıntıları
 Nesne kullanıcı arabiriminin doğru seçim olduğunu belirlediniz mi, tasarımla ilgili dört önemli nokta vardır:

1. **Kalıcılık:** Dayanıklı olması beklenen içerik mi yoksa geçici mi?
   Kullanıcılar, başvurmak veya etkileşim kurmak için bilgileri görünür durumda tutmak ister mi? Yoksa kullanıcılar bilgilere hızlıca göz atarak ana görevlerine devam etmek mi istiyor?

2. **İçerik türü:** İçerik bilgilendirme, eyleme değiştirilebilir mi yoksa gezinti mi olacak?
   Kullanıcının ana içerik hakkında ek ayrıntıya ihtiyacı var mı? Kullanıcının ana içeriği etkileyen bir görevi tamamlaması gerekiyor mu? Veya kullanıcının başka bir kaynağa yönlendirilene ihtiyacı var mı?

3. **Gösterge türü:** Ortam göstergesi mantıklı mı?
   Bilgiler yararlı bir şekilde özetlenebilir ve ana içeriği yoğun olmadan görüntülenebilir mi?

4. **Hareket:** Kullanıcı arabirimini çağırmak ve yok etmek için hangi hareket kullanılacak?
   Kullanıcı ayrıntı içeriğini nasıl getirir ve gönderir? Geçici ve dayanıklı durumları değiştirmek için sabitleme gibi bir hareket eklemenin değeri var mı?

   Bu dört karar noktanın her biri, nesne kullanıcı arabiriminin ana bileşenleri üzerinde bir etkisi olur.

### <a name="on-object-ui-components"></a>Nesne kullanıcı arabirimi bileşenleri

1. Kapsayıcı (içerik sunucusu) türü

    - Yüzen

    - Satır içi

2. İçerik türü

    - Bilgi: Statik veya dinamik olan veriler

    - Eyleme değiştirilebilir: Ana içeriği değiştirecek komutlar

    - Gezinti: Kullanıcıyı MSDN gibi başka bir pencereye veya uygulamaya alan bağlantılar

3. Hareketler

    - Çağrı

    - Işten çıkarma

    - Sabitleme

    - Diğer etkileşimler

4. Kalıcılık ve işleme modeli

    - Geçi -ci

    - Dayanıklı

    - Automatic

    - isteğe bağlı

5. Ortam göstergeleri (isteğe bağlı)

    - Alt çizgiyi yalıtma

    - Akıllı etiket simgesi

    - Diğer çevresel göstergeler

#### <a name="container-content-presenter-type"></a>Kapsayıcı (içerik sunucusu) türü
 dikkat noktasında içerik sunmak için 2 önemli seçenek vardır:

1. **Satır içi:** Visual Studio 2013 Code Editor'da tanıtan göz atma görünümü gibi bir satır içi sunucu, mevcut içeriği kaydırarak yeni içerik için alan sağlar.

    - **Kullanıcıların,** mevcut içeriklere başvuran veya bu içerikle etkileşim kurmak için önemli miktarda zaman harcamayı tercih ederseniz satır içi sunumları tercih edersiniz.

    - **Kullanıcıların,** mevcut bilgilere göz atması ve en az kesintiyle ana görevlerine devam etmek istemesini bekliyorsanız satır içi sunumlardan kaçının.

2. **Kayan:** Kayan bir sunucu, seçilen içeriğe mümkün olduğunca yakın bir konuma sahiptir ancak mevcut içeriğin düzenini değiştirmez. Seçili simgeye en yakın kullanılabilir boşluğun üzerinde kayan içerik paneli görüntüleme gibi çeşitli stratejiler kullanılabilir.

    - **Kullanıcıların,** sunmayı beklediğiniz bilgilere göz atmayı tercih edeceğini bekliyorsanız kayan sunumları tercih edin ve en az kesintiyle ana görevlerine devam edin.

    - **Kullanıcıların,** mevcut içeriklere başvuran veya bu içerikle etkileşim kurmak için önemli miktarda zaman harcamalarını bekliyorsanız, kayan sunuculardan kaçının.

#### <a name="content-type"></a>İçerik türü
 Herhangi bir nesne içi kullanıcı arabirimi kapsayıcısı içinde görüntülenebilir üç ana içerik türü vardır. Bu tür bilgilerin herhangi bir birleşimi gösterebilirsiniz. Üç tür vardır:

1. **Bilgi:** Çoğu nesne kullanıcı arabirimi kapsayıcısı bir tür bilgi içeriği görüntüler. İçerik, ortamın mevcut durumuyla ilgili bilgileri veya ortamın gelecekteki olası durumuyla ilgili bilgileri temsil ediyor olabilir. Örneğin, yeniden düzenleme gibi belirli bir komutun mevcut kod üzerindeki etkisini göstermek için kullanılabilir.

    - **Her** zaman görüntüleyilen bilgilerin kurallı gösterimini kullanın. Örneğin, kod kod gibi olmalı, söz dizimi vurgulama ile birlikte olmalı ve kullanıcının ayarlayan yazı tipine ve diğer ortam ayarlarına uygun şekilde çalışmalı.

    - **Her** zaman aynı bilgiler ana içerik olarak sunulan bilgi içeriği üzerinde mümkün olacak tüm eylemleri desteklemeyi göz önünde bulundurabilirsiniz. Örneğin, mevcut kodu bir nesne içi kullanıcı arabirimi kapsayıcısı içinde sunmak, bu koda göz atma ve değiştirme yeteneğini desteklemeyi kesinlikle göz önünde bulundurabilirsiniz.

    - **Gelecekteki** olası bir durumu temsil eden bilgi içeriği sunmak için her zaman farklı bir arka plan rengi kullanmayı göz önünde bulundurabilirsiniz.

2. Eyleme değiştirilebilir: Bazı nesne kullanıcı arabirimi kapsayıcıları, yeniden düzenleme işlemi gerçekleştirme gibi ana içerik üzerinde bazı eylem gerçekleştirme olanağı sağlar.

    - **Eyleme** değiştirilebilir komutları her zaman bilgilendirme içeriğinden ayrı olarak konumlandırma.

    - **Uygun olduğunda** eylemleri her zaman etkinleştirin ve devre dışı bırakma.

    - **İletişim** kutularının içindeki komutları temsil etmek için her zaman standart yönergelere bakın.

    - **Bir** nesne kullanıcı arabirimi kapsayıcısı içinde ortaya çıkacak eylem sayısını her zaman en düşük düzeyde tutma. Nesne kullanıcı arabirimiyle etkileşim kurmak basit ve hızlı bir deneyim olabilir. Kullanıcının nesne kullanıcı arabirimi kapsayıcının kendisini yönetmek için enerjisini harcanmamalı.

    - **Nesne** kullanıcı arabirimi kapsayıcının nasıl ve ne zaman kapatılacaklarını veya kapatılacaklarını her zaman göz önünde bulundurabilirsiniz. En iyi uygulama olarak, ana içerik ve ayrıntı içeriği arasındaki iletişim kutusunu sonlandıran herhangi bir eylem, eylem çağrıldığında nesne kullanıcı arabirimi kapsayıcıyı da kapatması gerekir.

3. **Gezinti:** Bazı nesne kullanıcı arabirimi kapsayıcıları, bir MSDN makalesini kullanıcının web tarayıcısında açma gibi başka bir pencereye veya uygulamaya kullanıcı alan bağlantılar içerir.

    - **Kullanıcıların** başka bir içeriğe giderek şaşırmalarını için her zaman gezinti bağlantısını "Aç" ile hazırlayın.

    - **Gezinti** bağlantılarını her zaman eyleme değiştirilebilir bağlantılardan ayırabilirsiniz.

#### <a name="ambient-indicators-optional"></a>Ortam göstergeleri (isteğe bağlı)
 Ortam göstergeleri, kodun geri kalanından farklı bir renkle sunulan metinler de dahil olmak üzere ince olabilir veya alt çizgiler ve akıllı etiket simgeleri gibi tıklı çizgi simgeleri de dahil olmak üzere belirgin olabilir. Ortam göstergeleri ek, ilgili bilgilerin kullanılabilirliğini iletir. İdeal olarak, kullanıcının kendileriyle etkileşim kurması gerekmeden bile yararlı bilgiler sağlar.

- **Bir** ortam göstergesini her zaman kullanıcının dikkatini dağıtacak veya bunaltmayabilecek şekilde konumlandırma. Ortam göstergesini bu şekilde konumlandırmak mümkün değilse başka bir çözüm düşünün.

- **Ortam** göstergesini her zaman ilişkili olduğu içeriğe mümkün olduğunca yakın konuma getirin.

- **Her** zaman kullanılabilir olduğu bilgileri özetleyen bir gösterge oluşturmayı deneyin. Kullanılabilir veri öğelerinin sayısını ("Başvurular" yerine "3 başvuru" gibi) sağlamayı veya verileri özetlemenin başka bir yolunu düşünün.

  - Bir göstergenin verileri her zaman hesap ve görüntülenemiyorsa, değerler hesaplandı olarak hemen aşamalı geri bildirim sağlamayı göz önünde bulundurabilirsiniz. Örneğin, kullanılabilir verilerde yapılan güncelleştirmeleri yansıtan değişikliklere animasyonu ebilirsiniz. Örneğin, Windows Phone e-posta sayısı arttıkça e-posta canlı kutucuğunun yenilenmesine benzer.

- **Hiçbir** zaman, bir kullanıcının makul bir içerik parçası için kat daha fazla gösterge ekleme. Ortam göstergeleri, kullanıcıdan herhangi bir etkileşime gerek kalmadan yararlı olabilir. Göstergeler, bunları görünüme getirmek için taşma ve diğer yönetim denetimlerine ihtiyaçmaları durumuyla ilgili belirsizliklerini kaybeder.

#### <a name="gestures"></a>Hareketler
 Kullanıcının ana içeriğe odaklanmasına izin vermenin önemli bir yönü, ek ayrıntı içeriğini açıp silen doğru hareketleri desteklemektir.

- **Kullanıcının** ek içeriği açmak için her zaman açık bir hareket gerçekleştirmesi gerekir. Yaygın açık hareketleri şunlardır:

  - **Üzerine gelin:** araç ipucu veya etkileşimli olmayan bilgi içeriği

  - **Açık komut:** satır içi sunucu

  - **Ortam göstergesine çift tıklayın:** CodeLens açılır penceresi

- **Kullanıcı** Esc tuşuna her bassa her zaman ayrıntı içeriğinin kapalıdır.

- **Her** zaman nesne kullanıcı arabiriminin bağlamını göz önünde bulundurabilirsiniz. Kapsayıcı içinde etkileşime olanak sağlayan içerik sunumları için, üzerine gelindiğinde kullanıcının iş akışını kesintiye neden olacak ek bilgiler gösterip göstermeyebilirsiniz.

- **Üzerine** gelindiğinde, düzenlenebilir gibi görünen veya kullanıcı etkileşimi davet ediyor gibi görünen içeriği hiçbir zaman görüntüleme. İmleci ayrıntı içeriğinin üzerine taşımaya çalışmaları, bir araç ipucu için standart davranış, imleç artık onu üreten ana içerik üzerinde olmadığı zaman hemen işten çıkarılana kadar bu davranış kullanıcıları hayal kırıklığına uğratabilirsiniz.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a> Seçim modelleri

### <a name="overview"></a>Genel Bakış
 Seçim modeli, kullanıcı arabiriminde bir veya daha fazla ilgi alanı nesnesinde işlemleri göstermek ve onaylamak için kullanılan mekanizmadır. Bu konuda, metin düzenleyicileri, tasarım yüzeyleri Visual Studio modelleme yüzeyleri gibi belge düzenleyicileri içindeki seçim etkileşimi desenleri ele almaktadır.

 Kullanıcıların ne üzerinde çalıştığını belirten bir Visual Studio olması ve Visual Studio kullanıcılara ne üzerinde çalıştığına yönelik geri bildirimle tahmin edilebilir şekilde yanıt vermeleri gerekir. Kullanıcı ile kullanıcı arabirimi arasındaki farklar veya yanlış iletişimler, kullanıcının bir eylemi fark etmemeyle sonuçlansa da, bu da yanlış sonuçlar doğurabilir. Genellikle, kullanıcı bir şeyin eksik olduğunu veya değiştiğini görene kadar hata fark edilemez. Bu nedenle seçim modelleri, kullanıcı arabirimi tasarımının en kritik parçalarındandır. Visual Studio modellerinde Windows olsa da küçük farklılıklar vardır.

 Bu Visual Studio, Windows modellerinin etkileşimin oluştuğu bağlama bağlı olarak farklılık gösterir. Seçimler dört nesne türüyle oluşabilir:

- Metin

- Grafik nesneleri

- Listeler ve ağaçlar

- Kılavuzlar

  Bu nesnelerin içinde üç tür seçim vardır:

- Bitişik

- Ayrık

- Bölge

#### <a name="scope"></a>Kapsam
 Seçimin en önemli bileşeni, kullanıcının hangi pencerede çalıştığını (etkinleştirme) ve odağın nerede olduğunu (seçim) bilyesini sağlamaktır. Visual Studio, Windows pencere yönetimi işlevselliğini genişletmektedir, ancak etkinleştirme şeması aynıdır: bir pencereyle etkileşim kurmak odağı pencereye getirir. Visual Studio iki etkinleştirme göstergesi vardır: biri belge pencereleri için, biri de araç pencereleri için.

 Belge pencerelerinde etkin pencere, öne gelen ve arka plan rengini değiştiren bir belge penceresi sekmesiyle gösterilir:

 ![Visual Studio'da etkin sekme Visual Studio](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Etkin sekme seçimi**

 Araç pencereleri için etkin pencere, araç penceresinin başlık çubuğu alanında yapılan bir değişiklikle gösterilir:

 ![Araçta etkin araç penceresi Visual Studio](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Bir düğümün birincil seçimini gösteren etkin araç penceresi**

 ![Araçta etkin olmayan araç penceresi Visual Studio](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Düğümdeki gizli seçimi gösteren etkin olmayan araç penceresi**

 Bir pencere etkin olduktan sonra, odak yönergelerin bu bölümünde açıklanan seçim modellerine göre gösterilir.

#### <a name="context"></a>Bağlam
 Visual Studio, güçlü bir bağlam kavramını korumak ve kullanıcının nerede çalıştığını izlemek için tasarlanmıştır. İster araç ister belge penceresi olsun, yalnızca bir pencere etkindir. Ancak, en üstteki belge penceresi her zaman gizli bir seçim korur. Odak bir araç penceresinde olsa da, son etkin olan belge penceresinde etkin olmayan durumda bile bir seçim görüntülenir. Bu, düzenlemekte olduğu belgede kullanıcının bağlamını korumak için yapılır ve kullanıcıya Visual Studio araç pencereleri ile belge pencereleri arasında sorunsuz bir şekilde geri dönüp geçiş yapmaları için durumlarını korumalarını sağlar.

### <a name="text-selection"></a>Metin seçimi
 Visual Studio metin düzenleyici gibi tamamen metinsel olan düzenleyiciler, MSDN'de Windows Kullanıcı Deneyimi Etkileşim Yönergeleri'nin Fare ve İşaretçiler sayfasında açıklanan aynı metin seçimi modelini ve görünümünü kullanır. [](/windows/desktop/uxguide/inter-mouse) Metin düzenleyicisinde giriş odağı, ekleme noktası olarak adlandırılan dikey çubukla belirtilmiştir. Ekleme noktası, arkasında görünenin tersi olarak tek piksel kalın ve renklidir. Bu, Denetim Masası'daki Klavye uygulama  ayarının **Hız** sekmesindeki İmleç yanıp sönme hızı ayarı tarafından ayarlanmış hıza göre yanıp Denetim Masası. 

#### <a name="contiguous-and-disjoint-selection"></a>Bitişik ve ayrık seçim
 Metin düzenleyicisinde seçim yalnızca bitişiktir. Ayrık metin seçimlerini izin verilmez, ancak grafik nesne düzenleyicilerde ele alın gerekir. Kullanıcının fare işaretçisi bir metin alanı üzerinde olduğunda, imleç bir I-pointer olarak değişir. Tek tıklamayla ekleme noktası, tıklama konumu olan metin düzenleyicisine yer verir. Fare düğmesini aşağı tutmak bir seçim vurgulaması başlatır ve fare düğmesini serbest bıraktığınızda seçim vurgusu sona erer.

#### <a name="region-selection-box-selection"></a>Bölge seçimi (kutu seçimi)
 Visual Studio düzenleyicide bölge seçimlerini destekler ve buna kutu seçimi adı ve verir. Kutu seçimi kullanıcının normal metin akışını takip etmeyen bir metin bölgesi seçmesini sağlar. Standart metin seçiminde olduğu gibi, seçim bitişik olması gerekir. Kutu seçimi, fareyle sürüklenirken Alt tuşu basılı tutarak başlatılır. Kutu seçimi, seçim bölgesi belirtmek için ok tuşları kullanılarak Alt ve Shift tuşları basılı tutarak da başlatabilirsiniz. Kutu seçimi normal seçim vurgulamayı kullanır ve ekleme noktası imlecini seçim alanı sonunda yanıp sönen şekilde gösterir.

 ![Yerel &#40;bölgesel&#41; kutusu Visual Studio](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Visual Studio'da bölge (kutu) seçimi**

#### <a name="text-selection-appearance"></a>Metin seçimi görünümü
 Düzenleyicide etkin ve etkin olmayan seçim için kullanılan renkler özelleştirilebilir. Bir kullanıcı, düzenleyicinin görsel görünümünü özelleştirmek için Araçlar **> Seçenekler'e** gidip Ortam görünümü'ne > Yazı Tipleri ve **Renkler > Metin Düzenleyici'ye gidebilir.**

### <a name="graphical-selection"></a>Grafik seçimi

#### <a name="interaction"></a>Etkileşim
 Grafik nesne seçimi karmaşık olabilir ve çeşitli faktörlere bağlıdır:

- **Düzenleyicinin birincil seçim modeli.** Grafik nesneleri içeren düzenleyiciler, metinleri veya kılavuzları düzenlemek için de kullanılabilir. Örneğin düzenleyici, XAML tasarımcısı gibi grafik nesnelerinin yerleştirilmesini de destekleyen metin tabanlı Visual Studio olabilir. Birden çok nesne türü desteklemek, kullanıcının farklı nesne türlerinden yapılmış grupları seçmesini etkileyebilir.

- **Birincil ve ikincil seçim durumları için destek.** Düzenleyici, birincil ve ikincil seçim durumları sağlar; böylece nesneler birlikte düzenlenebilir, birbirine hizalanır, birlikte yeniden boyutlandırılabilir ve bu şekilde devam eder.

- **Yerinde düzenleme desteği.** Düzenleyiciler, grafik nesnelerinin içeriğinin düzenlensine de olanak sağlar. Örneğin dikdörtgen şekil, içinde kullanıcı tarafından değiştirilene metinler de içerebilir. Ayrıca, bu metin orta veya doğru olabilir. Yerinde düzenleme, kullanıcı etkileşiminin daha ayrıntılı bir düzeyini içerir ve bu nedenle kullanıcıya durum bilgilerini sunmak için uygun bir görsel ipuçları kümesi gerektirir.

#### <a name="mouse-interaction"></a>Fare etkileşimi

|Giriş|Sonuç|
|-----------|------------|
|Seçilmemiş bir nesneye tıklayın|Nesneyi seçer ve nesnenin yeniden boyutlandırılabilir olduğu bir kesikli çizgi ve seçim tutamaçları görüntüler.|
|Seçili bir nesneye tıklayın|Nesne destekliyorsa yerinde düzenlemeyi etkinleştirir. Nesnenin dışına tıklarken yerinde düzenleme modu devre dışı bırakılır.|
|Bir nesneye çift tıklayın|Düzenlemek için nesnesinin arkasındaki kodu açar ve uygunsa varsayılan olay işleyicisi ekler.|
|Bir nesneye işaret eder|İşaretçiyi taşıma imlecine değiştirir. Nesnenin parlaklığı veya rengi gibi görünümü değişebilir.|
|Bir seçim tutamacına işaret|İşaretçiyi yeniden boyutlandırma imlecine değiştirir. Döndürmeyi destekleyen nesneler için bazı seçim tutamaçları, işaretçi seçim tanıtıcısı ile farklı şekilde konumlandık (örneğin, daha uzaklara taşındı) olarak bir döndürme imlecinin işaretçisini değiştirebilir.|
|Sürükleyin|Nesne daha önce seçilmemiş olsa bile işaretçiyi taşıma imlecine değiştirir ve nesneyi taşır.|
|Düzenleyici odağı kaybeder|Nesne, son işlem/seçim durumu sırasında sahip olduğu içeriği ve görünümü koruysa da yerinde düzenleme modunu devre dışı bırakılır.|
|Nesne seçimi|Nesnenin sınırını vurgulamak için kenarlık, noktalı çizgi veya görsel olarak farklı bir şekilde gösterilen başka bir ifade.|
|Seçili nesneyi yeniden boyutlandırma|Seçim tanıtıcıları ile belirtilmiştir.<br /><br /> Yeniden boyutlandırılabilir bir nesnenin yeniden boyutlandırılma yönünü temsil eden sekiz tanıtıcısı vardır. Nesne yalnızca belirli yönlerde yeniden boyutlandırılabilirse daha az tanıtıcı kullanılabilir. Kullanıcı bir nesneyi sekiz tanıtıcının etkileşimli olmayacak şekilde aşağı doğru boyuta indirse, dört tanıtıcı kullanılabilir. Tanıtıcı boyutları, ekran çözünürlüğüyle orantılı olarak boyut olarak **GetSystemMetrics** API işleviyle pencere kenarlığı ve kenar ölçümlerine bağlanarak belirlenebilir.<br /><br /> ![Tanıtıcıları yeniden boyutlandırma](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Seçili nesneyi döndürme|![Tutamaçları döndürme](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Klavye etkileşimi

|Giriş|Sonuç|
|-----------|------------|
|Tab|Odak göstergesini düzenleyicideki nesnelerin mantıksal sırası arasında taşır. Bu, **TabIndex** (veya eşdeğer) özellik değerine, nesne oluşturma sırasına ve düzenleyicinin genel amacına bağlı olarak soldan sağa veya üstten aşağıya doğru olabilir. Shift+Sekme, odak göstergesinin yönünü tersine çevirer.|
|Boşluk çubuğu|Tuş vuruşu korunurken kaydırma modunu etkinleştirir. Görünüm açısı konumunu kaydırmak için ek fare girişi gerekir.|
|Ctrl+Ara Çubuğu|Tuş vuruşu korunurken yakınlaştırma modunu etkinleştirir. Yakınlaştırma faktörlerini artırmak ve azaltmak için ek fare girişi gerekir.|
|Ctrl+Alt+Eksi İşareti|Yakınlaştırma faktörlerini bir düzey azaltıyor.|
|Ctrl+Alt+Plus İşareti|Yakınlaştırma faktörünün düzeyini artırır.|
|Shift OR Ctrl|Nesneyi seçim grubuna ekler. Ctrl tuşunu basılı tutarak nesneleri seçim grubundan tek tek kaldırmanız da gerekir.|
|Enter|Nesne için varsayılan komutu gerçekleştirir (genellikle Aç veya Düzenle).|
|F2|Nesne için yerinde düzenlemeyi etkinleştirir.|
|Ok tuşları|Seçilen nesneyi, küçük artışlarla (örneğin, bir defada 1 piksel) basılan ok tuşunun yönünde taşır|
|Ctrl+ok tuşları|Seçilen nesneyi, daha büyük artışlarla (örneğin, bir defada 10 piksel) basılan ok tuşunun yönünde taşır|
|Shift+ok tuşları|Seçilen nesnelerini küçük artışlarla (örneğin, bir defada 1 piksel) ilgili yönde yeniden boyutlandırılır|
|Ctrl+Shift+ok tuşları|Seçilen nesnelerini ilgili yönde daha büyük artışlarla (örneğin, bir defada 10 piksel) yeniden boyutlandırır|

 Kullanıcılar denetimleri düzenlerken, nesnelerin kullanıcı girişiyle otomatik olarak yeniden boyutlandırması mantıklı olabilir. Örneğin, kullanıcı bir etiket denetimi düzenlerse, etiketin, kullanıcının az önce yazarak yazacak metni görüntülemesi için etiketin büyümesi gerekir. Bu yapılmazsa, kullanıcının metni düzenledikten sonra denetimi el ile yeniden boyutlandırması gerekir. Kullanıcının çok sayıda denetimi varsa bu, kötü ve verimsiz bir görev haline gelir.

#### <a name="graphical-containers"></a>Grafik kapsayıcılar
 Bazı durumlarda grafik düzenleyiciler, HTML tasarımcısında Windows Forms Paneli denetimi veya Kılavuz Düzeni denetimi gibi diğer grafik nesneleri için kapsayıcılar sağlar. Düzenleyiciniz diğer grafik nesneler için kapsayıcılar sağlarsa, aşağıdaki seçim modeli yalnızca kapsayıcı için kullanılmalıdır (kapsayıcı içindeki nesneler yukarıda açıklandığı gibi standart modeli takip eder):

|Giriş|Sonuç|
|-----------|------------|
|Kapsayıcıya tek tıklama|Kapsayıcı nesnesini, içerdiği nesnelerden herhangi birini doğrudan seçmeden seçer. Kapsayıcı standart fare ve klavye girişiyle (yukarıda açıklandığı gibi) taşınabilir ve/veya yeniden boyutlandırılabilir. Kapsamış nesneler kapsayıcıyla ilişkili olarak taşınır, ancak kapsamış nesneler de doğrudan seçilmedikçe yeniden boyutlandırılmaz.|
|Kapsayıcının sınır bölgesi üzerine gelin|Fareyi taşıma imlecine dönüştürerek kapsayıcının taşına olduğunu gösterir.|
|Kapsayıcının sınır bölgelerini sürükleyin|Fareyi taşıma imlecine değiştirir ve kapsayıcıyı (ve içindeki kap içindeki nesneleri) taşır. Kapsayıcı, tek tıklamayla seçilmeden taşınamaz.|
|Kapsayıcı içindeki bir nesneye tek tıklama|Kapsayıcının seçimini kaldırın (seçiliyse) ve yalnızca tıklı nesneyi seçer.|
|Veya Ctrl tuşunu basılı tutarak kapta bulunan bir nesneye ve/veya kapsayıcıya shift tuşunu basılı tutarak tıklayın|Tıkilen nesneyi var olan bir seçime veya seçim grubuna ekler. Tıkılan nesne zaten seçim grubunun bir üyesi ise, seçim grubundan kaldırılır.|

 Bir önceki bölümde açıklandığı gibi, içerdiği nesneler temel seçim modeline bağlı kalmalı. Windows Forms tasarımcısının kullanılabilirlik testlerinden, kullanıcılar müdahale etmeden (içerme nesnesi tarafından dayatılan) içerdiği nesnelere sorunsuz erişim beklemiştir.

#### <a name="disjoint-and-region-selections"></a>Ayrık ve bölge seçimleri
 Grafik nesne düzenleyicileri ayrık seçimleri desteklemeli. Bu grafikte, uygulamanın denetim görünümünün Visual Studio. Ayrıntılı [görsel belirtimler için bkz.](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) Grafik nesne seçimi görünümü.

 ![Ayrık ve bölge seçicileri](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Ayrık seçim**

 Grafik düzenleyiciler ayrıca seçim çerçevesi türü seçim göstergesiyle birlikte bölge seçimleri de sağlanabilecektir. Grafik düzenleyicisi diğer nesne türlerini (metin gibi) destekliyorsa, bu diğer nesne türlerinin kısıtlamalarına bağlı olarak bölge seçimleri mümkün olmayacaktır.

 ![Seçim çerçevesi](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Seçim çerçevesi**

#### <a name="primary-and-secondary-selections"></a>Birincil ve ikincil seçimler
 Bazı grafik nesne düzenleyicileri, kullanıcının gruplar halinde nesneleri düzenlemesine veya hizalamasına olanak sağlar. Bu durumda, birincil ve ikincil seçimler kavramının tanıt yapılması gerekir. Birincil seçim, diğer tüm nesnelerin grup işlemlerine yanıt veren nesnesidir. Kullanıcının ilk olarak seçen nesnesi birincil denetim olur ve sonraki seçimler ikincil seçim olur. Birincil seçimin, birincil nesneyi belirtmek için ikincil seçimlerden farklı bir görsele sahip olması gerekir:

 ![Birincil ve ikincil seçim](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **İki ikincil seçimle birincil seçim**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Grafik nesne seçimi görünümü
 Seçim tutamaçları, nesnenin sınırlayıcı kutusunun çevresinde dikdörtgen bir desende çizilen karelerdir. Aşağıdaki grafikte, bir grafik nesnesinin tanıtıcı, boyutlandırma ve yerinde düzenleme görünümü ile sahip olduğu çeşitli durumların örnekleri gösterilmiştir. **Tanıtıcıların boyutu, GetSystemMetrics** API'sini kullanarak pencere kenarlığı ve uç ölçümlerine bağlı olması gerekir.

| Durum | Görünüm | Görsel ayrıntılar |
|-------------------------|---------------| - |
| **Seçili** | Varsayılan | ![Varsayılan düğme durumu](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Birincil seçim** | Resizable | ![Yeniden boyutlandırma tutamaçları ile birincil seçim](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Birincil seçim** | Yeniden boyutlandırılamaz | ![Yeniden boyutlandırma tutamaçları olmadan birincil seçim](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Birincil seçim** | Kilitli | ![Birincil seçim kilitli](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **İkincil seçim** | Resizable | ![Yeniden boyutlandırma tutamaçları ile ikincil seçim](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **İkincil seçim** | Yeniden boyutlandırılamaz | ![Yeniden boyutlandırma tutamaçları olmadan ikincil seçim](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **İkincil seçim** | Kilitli | ![İkincil seçim kilitli](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **Kullanıcı arabirimi etkin** | Varsayılan | ![Kullanıcı arabirimi etkin durumu](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Seçim modellerini görüntüleme

#### <a name="tree-view"></a>Ağaç görünümü
 Ağaç görünümündeki seçim, basit bir vurgu ile gösterilir. Kullanıcı bir düğüm adına veya düğüm simgesine tıklarsa düğüm seçilir. Düğümün sol tarafından gelen üçgen glyph'ler ağaç denetimlerini genişleterek veya daraltır ancak kullanıcının seçimini etkilemez. Tek istisna, seçim o düğümün alt öğesinde olduğunda üst düğümün daraltılmalarından sonra seçim üst düğüme taşınır.

 ![Genel görünümde tipik Visual Studio](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Genel görünümde tipik Visual Studio**

 Ağaç görünümleri, ağaçtaki birden çok düzeyde bile bitişik ve ayrık seçimleri desteklemektedir. Görünür ağaç düğümlerde bitişik veya ayrık birden çok seçim yapılmış olmalıdır. Bir düğüm daraltılırsa, ayrık seçim kaybedilir ve daraltılmış düğüm seçimi elde edilir. Bu şekilde, kullanıcı bir işlemden etkilenecek düğümleri görebilir. Düğümler daraltılmışsa, hangi düğümlerin etkilendiğinin belirsiz olması.

 Üst düğüm seçildiğinde, işlem üst düğüme uygulanacak olsa da, bir işlemi üst düğüme ve tüm alt öğeye uygulamanın mantıklı olduğu durumlar olabilir. Bu durumda, "tüm çocuklarına uygula" seçeneğini kullanıcıya açık hale etmek için işlem sırasında bir onay kutusu veya onay iletişim kutusu gibi ek kullanıcı arabirimi belirtin.

##### <a name="renaming"></a>Yeni -den adlandırma
 Ağaçtaki düğümler yeniden adı yeniden adı desteğine sahipse, yeniden adı yerinde yeniden adı yapılması gerekir. Yerinde işlem, tüm ağaç denetimler genelinde standart olması gerekir Visual Studio. Kullanıcı girişini kabul etmeye hazır, düğüm adının tamamını kapsayan metin seçimiyle, yerinde düzenleme modunu hemen etkinleştiren bir yeniden adlandırma komutu girin. Düğüm bir dosyayı temsil ediyorsa, dosya adı uzantıyı içermeli. Seçim vurgusu uzantıyı değil yalnızca dosya adı gövdelerini içermeli.

|Giriş|Sonuç|
|-----------|------------|
|Enter tuşu|Yeniden adlandırma işlemi işler|
|Esc tuşu|Yeniden adlandırma işlemini iptal eder|
|Yerinde düzenleme bölgesi dışına tıklama|Yeniden adlandırma işlemi işler|
|Geri Al|Yeniden adlandırma işlemini iptal etmek için kolay geri alma sağlama|

#### <a name="selection-within-lists-and-grid-controls"></a>Listeler ve kılavuz denetimleri içinde seçim
 Liste seçiminde temel kavram, satır tabanlı olduğu, yani bir seçim yapılırken satırın tamamının birim olarak seçilecek olduğudır. Buna karşılık kılavuzlar, satırın diğer herhangi bir yönünü etkilemeden belirli hücrelerin seçilmesini sağlar. Kılavuzlar ayrıca, üst satırlarla etkileşim kurarak hiyerarşinin tüm dallarının seçilip seçiminin kaldırılmış olmasına olanak sağlayan iç içe geçmiş satırlardan (TreeGrid'de olduğu gibi) bir hiyerarşi de içerebilir. Listelerde seçim, veri satırın tamamına basit bir vurgulama rengiyle gösterilir. Odak, geçerli düzenlenebilir satırın veya hücrenin (tüm hücreler salt okunursa satır) etrafında tek piksel noktalı kenarlıkla gösterilir.

> [!NOTE]
> **Odak** ve **seçim** farklı kavramlardır. *Odak,* girişin başka bir nesneye açıkça yönlendirilemeden hangi kullanıcı arabirimi  öğesinin hedefli olduğunu gösterirken, seçim sonraki işlemlerin hangi nesneler kümesine dahil edilmesinin durumunu ifade eder.

 Listelerde seçimler bitişik, ayrık veya bölge olabilir. Birden çok seçime izin verilmiyorsa, bitişik ve ayrık seçim her zaman destekleneken bölge (kutu) seçimleri için destek isteğe bağlıdır. Bölge seçimleri, liste gövdesinin boşluğuna sürüklenerek başlatılır.

| Nesne | Seçim |
|--------|------------|
| Liste | Bitişik |
| Liste | Ayrık |
| Liste | Bölge |

 Listeye bir kez tıklar, tıklamanın meydana geldiği satırı seçer. Kullanıcı yerinde düzenlemeyi destekleyen bir liste hücresine tıklarsa, hücre yerinde düzenleme için de hemen etkinleştirilir. Aksi takdirde satırın tamamı hemen seçilir ve vurgu görüntülenir.

 Liste gövdesine sürüklemek şu üç şeyi yapar:

- Liste destekliyorsa ve fareyle aşağı doğru boşlukta yer alıyorsa bir bölge seçimi başlatılır

- Liste hücresi veya satırı sürükleme kaynağı olmayı destekliyorsa bir sürükleme/bırakma işlemi başlatma

- Geçerli satırı seçer

##### <a name="in-place-editing"></a>Yerinde düzenleme
 Yerinde düzenlemeye izin verilmiyorsa iki temel model vardır: basit düzenleme denetimi ve özellik seçici. Basit bir düzenleme denetimiyle içerik vurgulanır ve yerinde düzenleme etkinleştirildikten hemen sonra kullanıcı girişi için hazır hale gelir. Bir özellik seçicinin gerçekleştirildiğinde, özellik seçiciyi çağıran düğme yerinde düzenleme modu etkinleştirildikten sonra görüntülenir ve geçerli seçim vurgulanmaz. Seçici düğmesinin hücrede doğru şekilde doğru olması gerekir. Yerinde düzenleme örnekleri için özellikler penceresine **bakın ve** **Görev Listesi** Visual Studio.

##### <a name="keyboard-support"></a>Klavye desteği
 Listelerde ve kılavuzlarda klavye desteği standart seçim Windows izler:

- Ok tuşları listede gezinerek odak taşınırken her satırı/hücreyi seçer.

- Shift + ok, ok tuşlarının yönünde bitişik bir seçim gerçekleştirir.

- Ctrl + ok ve ardından liste öğelerini ekleme ve seçimden kaldırma arasında Boşluk çubuğu geçişleri ve ayrık bir seçim oluşturma.

- İç içe geçmiş hiyerarşiler içeren kılavuzlar için, Sağ Ok tuşu bir üst satırı genişletiyor ve Sol Ok tuşu bir satırı daraltıyor.

- Sekme tuşu, hücreler düzenlenebilir durumda ise odağı geçerli satırdaki hücreler arasında taşır.

- Enter tuşu, listede yer alan öğede varsayılan komutu gerçekleştirir (genellikle **Aç).**

- F2 anahtarı, seçili olan hücre için yerinde düzenlemeyi etkinleştirir.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Kalıcılık ve ayarları kaydetme

### <a name="overview"></a>Genel Bakış
 Visual Studio yazılım bileşenleri genellikle kendi durumu ve kalıcılığından sorumlu olsa Visual Studio pencere boyutları ve konumlar gibi bazı durumlarda ayarları otomatik olarak kaydeder. Aşağıdaki tablo, otomatik olarak kaydedilen ayarların ve açık bir kullanıcı veya programlanmış eylemin gerekli olduğu ayarların bir birleşimidir.

|Nesne|Kaydedilenler|Kaydedilen zaman|Kaydedilen yer|
|------------|------------------|------------------|-------------------|
|Seçilebilir nesne (örneğin, bir kod satırı)|Bir kod satırı üzerinde kesme noktası<br /><br /> Kod satırıyla ilişkili bir kullanıcı kısayolu|Proje kaydedilebilir|Proje **için kullanıcı seçenekleri (.suo)** dosyası|
|Iletişim|Taşınmışsa iletişim kutusunun konumu<br /><br /> Kullanıcının iletişim kutusunda son kullandığı görünüm|İletişim kutusu kapanıyor<br /><br /> Oturum Visual Studio bittiğinde|Bellek içinde<br /><br /> **HKEY_Current_User'de kayıt defteri**|
|Pencere|Pencerenin boyutu ve konumu|Pencere kapandığında<br /><br /> Visual Studio modu değiştiğinde<br /><br /> Visual Studio oturumu sona erdiğinde|Projenin **Kullanıcı seçenekleri (. suo)** dosyası<br /><br /> Pencere ayarları için özel seçenekler dosyası|
|Belge|Belgedeki geçerli seçim<br /><br /> Belgenin görünümü<br /><br /> Kullanıcının ziyaret ettiği son birkaç yer|Belge kaydedildiğinde|Projenin **Kullanıcı seçenekleri (. suo)** dosyası|
|Project|Dosyalara başvurular<br /><br /> Disk üzerindeki dizinlere başvurular<br /><br /> Diğer yazılıma başvurular<br /><br /> Bileşenler<br /><br /> Projenin kendisiyle ilgili durum bilgileri|Proje kaydedildiğinde|Proje dosyası|
|Çözüm|Projelere başvurular<br /><br /> Dosyalara başvurular|Proje veya çözüm kaydedildiğinde|**Çözüm (. sln)** dosyası|
|**araç > seçeneklerinde** Ayarlar|Klavye özelleştirmeleri<br /><br /> Araç çubuğu özelleştirmeleri<br /><br /> Renk şemaları|**Araçlar > seçenekleri** iletişim kutusu kapandığında<br /><br /> Visual Studio oturumu sona erdiğinde|**HKEY_Current_User** kayıt defteri|

 Kullanıcının ne yaptığını ve ne zaman yaptığına göre, bir ayarın bellekte (oturum sırasında) kaydedilip kaydedilmediğini (oturum sırasında), **çözüm seçenekleri (. suo)** dosyasının bir parçası olarak veya yalnızca yazılım bileşeninin bildiği özel bir ayar dosyası olarak, projenin veya çözüm dosyasının kendisinin bir parçası olarak (kayıt defteri ayarı olarak oturumlar arasında) kaydedilip kaydedilmediğini belirler. Yukarıdaki tabloda, ayarların kaydedilebileceği çeşitli olaylar gösterilmektedir. Ancak, durumu kaydetmek isteyebileceğiniz başka zamanlar da vardır:

- Kullanıcı bir iletişim kutusu veya pencere içindeki konumu değiştirdiğinde

- Kullanıcı odağı başka bir pencereye aktarsın

- Kullanıcı tasarımdan hata ayıklama moduna geçtiğinde

- Kullanıcı hesabının oturumunu kapattığında

- Bilgisayar hazırda beklemeye girdiğinde veya kapandığında

- Bilgisayar/sabit sürücü yeniden biçimlendirilme ve tekrar ayarlama hakkında

### <a name="window-configurations"></a>Pencere yapılandırması
 Bir pencere yapılandırması, geliştirme ortamının temel sunumudur. Bu, araç pencerelerinin ve düzenlenme şeklini içeren bir şemadır. IDE (IDE pencereleri) tarafından yönetilen Windows için, düzen bilgileri Kullanıcı başına kalıcı hale getirilir. bu nedenle, Kullanıcı IDE 'yi başlattığında pencere düzeni Visual Studio en son ne zaman ile aynı görüntülenir. IDE pencerelerinin durum ve konumu, XML biçimindeki özel bir seçenekler dosyasında kalıcıdır. IDE 'ye yüklenen paketler tarafından oluşturulan araç pencereleri, kayıt defterindeki durum bilgilerini kalıcı hale getirerek, Kullanıcı başına olabilir veya olmayabilir.

#### <a name="profile-specific-layouts"></a>Profile özgü düzenler
 Her profil, belirli bir geliştirici personbuna tanıdık bir şekilde düzenlenmiş (Visual C++ geliştiricilerin IDE 'nin sol tarafında **Çözüm Gezgini** görmeyi beklediği, ancak C# geliştiricileri sağ tarafta **Çözüm Gezgini** görmeyi beklediği) araç penceresi düzenlerini içerir. Profile özgü pencere düzenleri, Kullanıcı başlangıçta bir profil seçtikten sonra yüklenir. Bir paket yazarı, kullanıcının pencere yapılandırmasına yaptığı değişikliklerin kalıcı hale gelmesini sağlamak için müşterinin deneyimine en uygun pencere yerleşimini belirlemelidir.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a> Dokunma girişi
 Kullanıcılar, dokunmatik cihazlarda Microsoft geliştirme ürünlerini giderek daha fazla kullanmaktadır. Ancak, dokunmatik cihazlarda geliştirme araçlarını kullanmayı zorlaştırmaya yönelik engelleri vardır. Kullanıcılar, ürünlerimizi güvenilir ve kesin bir dokunmatik deneyim sağlayacak şekilde beklecektir. bu yönergelerin amacı, hangi dokunma özelliklerine dahil etmek ve Visual Studio ve ilgili ürünler genelinde tutarlı bir dokunma deneyimini teşvik etmek için kararlara bilgi almaktır.

### <a name="levels-of-experience"></a>Deneyim düzeyleri
 Aşağıdaki deneyim düzeyleri, ekiplerin, iletişim kutusunda istenen yatırım düzeylerine dayanarak hangi dokunma özelliklerini sunacağına karar vermesine yardımcı olacak bir kılavuz olarak sunmaya yöneliktir.

- **Temel deneyim** , daha fazla iletişim sağlamak isteyen takımlar için, işleri genelinde hiç atılacak bir sona kalmaz.

- En **iyi duruma getirilmiş deneyim** , en yaygın dokunma özelliklerini (örneğin, Internet tarayıcı uygulamalarında kullanılabilir olanlar) sağlamak isteyen ekipler içindir.

- **Yükseltilmiş deneyim** , davranışlarını daha kolay hale getirmek için hareketler veya diğer isteğe bağlı yetenekler gibi yetenekler eklemek isteyen ekipler içindir.

||Temel deneyim|İyileştirilmiş deneyim|Yükseltilmiş deneyim|
|-|----------------------|--------------------------|-------------------------|
|**Kullanıcıların şunları yapmasına olanak sağlar...**|Kod ve çözüm/proje düzeyinde okumayı, ölü uçlar olmadan çözme|Bakım, şunların ve gezinti görevlerini gerçekleştirme|Güvenle tutarlı, sezgisel ve akıcı bir deneyimde çalışır|
|**Düzenleyici**|Dokunma kaydırma ve seçim<br /><br /> Kaydırma çubuğu dokunarak zıplamaya dokunun ve + sürükle tuşlarına basın|Pinç zoom<br /><br /> Hızlı kaydırma<br /><br /> Seçim<br /><br /> Bağlam menüsünün kolay kullanımı||
|**Popüler araç pencereleri**|Liste kaydırma<br /><br /> Öğe seçimi<br /><br /> Kaydırma çubuğu dokunarak zıplamaya dokunun ve + sürükle tuşlarına basın|Kolay öğe kaydırma ve seçim||
|**Protokolüdür**||Pencereyi yeniden boyutlandır<br /><br /> Hızlı erişim||
|**Belge kutusu**||Açık dosyalar arasında kolay gezinti||
|**Hareketler**||IDE genelinde ortak hareketlerin çalıştığından emin olun|Hareket tabanlı eylemler<br /><br /> Sürükleme ve bırakma ve tasarımcıları destekleme|
|**Diğer önemli noktalar**|||Özel ekran klavyesi|

#### <a name="gestures"></a>Hareketler
 Hareketler kullanıcılara, aksi takdirde daha karmaşık bir etkileşim gerektiren komutlara yönelik bir kısayol sağlar. [masaüstü uygulamaları için sık kullanılan dokunma hareketlerinde](/windows/desktop/wintouch/windows-touch-gestures-overview)Windows yönergelere bakın ve kaydırma ve yakınlaştırma gibi basit hareketler de dahil olmak üzere çoğu hareket için bu yönergeleri izleyin.
