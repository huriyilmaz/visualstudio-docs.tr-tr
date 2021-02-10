---
title: Visual Studio için bileşik desenler | Microsoft Docs
description: Visual Studio 'da tutarlılık için önemli Birleşik desenler hakkında bilgi edinin. Bileşik desenler, etkileşim ve tasarım öğelerini birleştirir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e48ecfb2-f4b5-4d3a-b4a2-7a4d62fa4ec0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c8ac314a2ec49b805fc87badf6b63a719b8511e8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952102"
---
# <a name="composite-patterns-for-visual-studio"></a>Visual Studio İçin Bileşik Desenler
Bileşik desenler, etkileşim ve tasarım öğelerini ayrı yapılandırmalarda birleştirir. Tutarlılığa göre Visual Studio 'daki en önemli bileşik desenlerden bazıları şunlardır:

- [Veri görselleştirme](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_DataVisualization)

- [Nesne üzerinde kullanıcı arabirimi ve göz atma](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

- [Seçim modelleri](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

- [Kalıcılık ve kaydetme ayarları](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

- [Dokunma girişi](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

## <a name="data-visualization"></a><a name="BKMK_DataVisualization"></a> Veri görselleştirme

### <a name="overview"></a>Genel Bakış
 Grafikler, karar almanın geliştirilmesine yönelik verileri toplamanın ve görselleştirmenin görsel bir yoludur. Kullanıcıların çok fazla veri ile karşılaştığı, ne kadar önemli olduğunu ve ne tür bir eyleme ihtiyaç duydularını görbilecekleri çok büyük bir anlamı olan kullanıcılar.

 Aşağıdaki koşullardan herhangi biri doğru olduğunda Kullanıcı bir grafikten faydalanır:

- Grafik kullanıcıların üzerinde davranabilecekleri görevleri tanımlamasına yardımcı olur mu?

- Grafik, kullanıcıların olası değişikliklerin sonuçlarını tahmin etmek için izin veriyor mu?

- Grafik, kullanıcıların eğilimleri bulmasına ve desenleri belirlemesine yardımcı olur mu?

- Grafik, kullanıcıların daha iyi kararlar almasına izin veriyor mu?

- Grafik, kullanıcıların belirli bir bağlamda sahip olabileceği belirli bir soruyu yanıtlamaya yardımcı olur mu?

#### <a name="general-rules-for-charts"></a>Grafikler için genel kurallar

- Verilerin net bir şekilde etiketlenmesi. Açıklama içermeyen çizimler yalnızca güzel resimler.

- Orantıları eğrilmemek için eksenleri sıfırdan başlatın. Satır uzunluğu ve çubuk boyutu, veri noktaları arasındaki ilişkileri anlamak için önemli görsel ipuçları.

- Infographics değil, grafikler oluşturun. Infographics, verilerin sanatsal temsilleridir ve birincil hedefi görsel hikaye söytir. Grafikler (ve) görsel açıdan çekici olabilir, ancak verilerin kendisi için konuşmasına izin verir.

- Çatı, resimli grafikler, karşıtlık diyez işaretleri ve diğer Infographic dokunmaktan kaçının.

- 3B efektleri dekoratif bir öğe olarak kullanmayın. Onları yalnızca kullanıcının bilgileri anlarsınız özelliğini gerçekten integral olarak kullandıysanız kullanın.

- Birden çok çizgi ve dolgu kullanmaktan kaçının. bu tür bir grafik, doğru bir şekilde okunmasını ve yorumlamayı zorlaştırır.

- Bir kavramı anlamak veya verilerle etkileşim kurmak için tek bir grafik (veya herhangi bir çizim) kullanmayın. Bu, görsel sorunları olan kullanıcılar için zorluklar sunar.

- Grafikleri bir sayfada gereksiz ve dekoratif öğeler olarak kullanmayın. Diğer bir deyişle, grafik herhangi bir değer eklemez veya kullanıcıların bir sorunu çözmesine yardımcı olduysa, bunu kullanmayın.

### <a name="chart-types"></a>Grafik türleri
 Visual Studio 'da kullanılan grafik türleri çubuk grafikleri, çizgi grafikleri, halka grafiği olarak bilinen değiştirilmiş bir pasta grafiği veya "halka grafik," zaman çizelgeleri, dağılım çizimleri ("küme grafikleri" olarak da bilinir) ve Gantt grafikleri içerir. Her bir grafik türü, farklı bir bilgi türü iletişim kurmak için yararlıdır.

### <a name="other-charting-considerations"></a>Diğer grafik konuları

#### <a name="color"></a>Renk
 Visual Studio 'da kullanılmak üzere tanımlanan belirli bir grafik renkleri paleti vardır. Palet, renk değişimlerinin ana türleri için erişilebilir ve renklerin çok dar dilimleri olarak kullanılması durumunda bile renk yapılabilir. Bu renkleri, Kullanıcı arabiriminizdeki herhangi bir grafik veya grafik türü için herhangi bir bileşimde kullanabilirsiniz. Birçok farklı renge ihtiyacınız yoksa yedi rengin hepsini kullanmanız gerekmez. Bu renkler herhangi bir ön plan öğeleriyle kullanılmak üzere tasarlanmamıştır, bu nedenle metin veya glifleri bu renklerin üzerine yerleştirmeyin. Bu kuleler, **araçlar > seçenekleri** altında (bkz. [son kullanıcılar için renkleri gösterme](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_ExposingColorsForEndUsers)) sabit kodlanmış ve Kullanıcı özelleştirmesine açık olmalıdır.

|Basılı|Onaltılık|RGB|
|------------|---------|---------|
|![Renk örneği 71B252](../../extensibility/ux-guidelines/media/0711_71b252.png "0711_71B252")|#71B252|113178, 82|
|![BF3F00 örneği](../../extensibility/ux-guidelines/media/0711_bf3f00.png "0711_BF3F00")|#BF3F00|191, 63, 0|
|![FCB714 örneği](../../extensibility/ux-guidelines/media/0711_fcb714.png "0711_FCB714")|#FCB714|252183, 20|
|![Renk örneği 903F8B](../../extensibility/ux-guidelines/media/0711_903f8b.png "0711_903F8B")|#903F8B|144, 63139|
|![Renk örneği 117AD1](../../extensibility/ux-guidelines/media/0711_117ad1.png "0711_117AD1")|#117AD1|17.122.209|
|![Renk örneği 79D7F2](../../extensibility/ux-guidelines/media/0711_79d7f2.png "0711_79D7F2")|#79D7F2|121.215.242|
|![B5B5B5 örneği](../../extensibility/ux-guidelines/media/0711_b5b5b5.png "0711_B5B5B5")|#B5B5B5|181.181.181|

## <a name="on-object-ui-and-peeking"></a><a name="BKMK_OnObjectUI"></a> Nesne üzerinde kullanıcı arabirimi ve göz atma
 Bu bölüm, kod Özeti Görünümü olarak da bilinen, Visual Studio 'ya özgü bir nesne Kullanıcı arabirimi türü olarak göz atma bağlamı sağlar.

### <a name="overview"></a>Genel Bakış

- Nesne üzerinde kullanıcı ARABIRIMI, kullanıcıya ana görevden ayıracaktır olmadan daha fazla bilgi veya etkileşim vermelidir.

- Visual Studio 'daki nesne üzerindeki kullanıcı arabiriminin ana deseninin "dikkat çekici bir noktada bilgi" adı verilir.

- Visual Studio 'da nesne üzerinde kullanıcı arabirimi, satır içi veya kayan ve dayanıklı ya da geçici olabilir.

  - Visual Studio 'da nesne üzerindeki bir kullanıcı arabirimi türü kod Özeti Görünümü satır içi ve dayanıklı.

  - Visual Studio 'da nesne üzerindeki bir kullanıcı arabirimi olan CodeLens, kayan ve geçici

  Kod parçasının nasıl çalıştığını anlamak veya bu kodla ilgili ayrıntıları bulmak için, genellikle bir geliştiricinin bağlam değiştirme ve diğer içeriğe veya başka bir pencereye gitmesini gerektirir. Kullanıcılar Ana pencerenizi bırakılarsa, bu bağlam vardiyaları karışıklığa yol açabilir. Ayrıca, özellikle de değiştirme Windows 'un özgün koduna diğer kullanıcı arabirimi tarafından gizlenmesini neden olduysa, bu özgün içeriğin geri alınması zor olabilir.

  Nesne üzerinde kullanıcı arabirimi, "dikkat noktasındaki bilgiler" adlı bir model izler. Bu iletiler, açılır pencereler ve iletişim kutuları kullanıcılara ek, ana görevine odaklanmadan açıklama veya etkileşim ekleyen ilgili bilgileri sağlar. Nesne üzerine örnek UI örnekleri, bir Kullanıcı işaretçi bildirim alanındaki bir simgenin üzerine geldiğinde görünen açılır pencereleri, yanlış yazılmış bir kelime altındaki kırmızı dalgalı çizgi ve Visual Studio 2013 tanıtılan Özet görünümünü içerir.

### <a name="decision-points"></a>Karar noktaları
 Visual Studio 'da bu bilgi modelini dikkat çekici bir şekilde kullanmanın birkaç yolu vardır. Doğru mekanizmayı seçme ve bunu tutarlı, öngörülebilir bir şekilde uygulama, genel deneyim için önemlidir. Aksi takdirde, kullanıcılar içeriğin kendisinden odaklanıldığı kafa karıştırıcı veya tutarsız bir deneyim sunabilir.

#### <a name="relationships-between-master-and-detail-content"></a>Ana ve ayrıntı içeriği arasındaki ilişkiler
 İlgilenme noktasındaki bilgiler, kullanıcının odaklandığı içerik ("ana" içerik) ve ek ilgili içerik ("ayrıntı" içeriği) arasındaki ilişkiyi göstermek için kullanılır. Bu düzende, ayrıntı içeriği kullanıcının üzerinde çalıştığı içerikle ve Ana içeriğe yakın bir şekilde görüntülenebilirler. Ana içeriğin çok fazla olması gerekmeden özetlenememesi gereken ek bilgiler veya bilgiler, araç penceresi gibi başka bir Düzenle uymalıdır.

- Ayrıntı içeriğini **her zaman** asıl içeriğe yakın bir yerde görüntüleyin.

- **Her zaman** ayrıntı içeriğinin, kullanıcının ana içerikte odaklanmış kalmasını hala sağladığından emin olun. Genellikle, bunu başarmanın en iyi yolu, ayrıntı içeriğini mümkün olduğunca Ana içeriğe yakın bir şekilde işlemelidir. Bu, ayrıntı içeriğini ana içeriğin yanındaki bir açılan pencerede veya Ayrıntılar içeriğini ana içeriğin altında satır içi olarak işlenerek yapılabilir.

- Kullanıcı ana içerikten uzakta olan dikkat çekici bir noktada **hiçbir zaman** bilgi kullanmayın. Kullanıcıların ayrıntı içeriğini ayrı olarak görüntülemesi gerekiyorsa, kullanıcının bunu yapmasına olanak tanıyan açık bir eylem kullanıma sunun.

#### <a name="design-details"></a>Tasarım ayrıntıları
 Nesne üzerindeki kullanıcı arabiriminin doğru seçim olduğunu belirledikten sonra, dört ana tasarıma dikkat etmeniz gerekir:

1. **Kalıcılık:** içeriğin dayanıklı veya geçici olması bekleniyor mu?
   Kullanıcılar bilgileri görünür veya ile etkileşimde bulunmak için görünür durumda tutmak ister misiniz? Ya da kullanıcılar bilgilere hızlıca göz atma ve sonra ana görevine devam etmek istiyor musunuz?

2. **İçerik türü:** içerik bilgilendirici, eyleme dönüştürülebilir veya gezinmi olacak?
   Kullanıcının ana içerik hakkında ek ayrıntı mi gerekiyor? Kullanıcının ana içeriği etkileyen bir görevi tamamlaması mi gerekiyor? Ya da kullanıcının başka bir kaynağa yönlendirilmesi mi gerekiyor?

3. **Gösterge türü:** ortam göstergesi anlamlı mi?
   Bilgiler, ana içeriği temel alarak yararlı bir şekilde özetlenebilir ve görüntülenebilir mi?

4. **Hareketler:** Kullanıcı arabirimini çağırmak ve kapatmak için hangi hareketler kullanılacak?
   Kullanıcı ayrıntı içeriğini nasıl getirip bir yere gönderecektir? Geçici ve dayanıklı durumlar arasında geçiş için sabitleme gibi bir hareket eklemede bir değer var mı?

   Bu dört karar noktasının her biri, nesne içi kullanıcı arabiriminin ana bileşenleri üzerinde bir etkiye sahip olacaktır.

### <a name="on-object-ui-components"></a>Nesne üzerinde kullanıcı arabirimi bileşenleri

1. Kapsayıcı (içerik sunum) türü

    - Duyarlıklı

    - Satır içi

2. İçerik türü

    - Bilgilendirici: statik veya dinamik olabilecek veriler

    - Eylem yapılabilir: ana içeriği değiştiren komutlar

    - Gezinti: kullanıcıyı MSDN gibi başka bir pencere veya uygulamaya alan bağlantılar

3. Hareketler

    - Çağrı

    - Dismissal

    - Sabitleme

    - Diğer etkileşimler

4. Kalıcılık ve kayıt modeli

    - Larsa

    - Dayanıklı

    - Automatic

    - İsteğe bağlı

5. Çevresel göstergeler (isteğe bağlı)

    - Dalgalı çizgi altı çizili

    - Akıllı etiket simgesi

    - Diğer çevresel göstergeler

#### <a name="container-content-presenter-type"></a>Kapsayıcı (içerik sunum) türü
 Dikkat ederek içerik sunmak için kullanabileceğiniz iki önemli seçenek vardır:

1. **Satır içi:** Visual Studio 2013 kodu düzenleyicisinde tanıtılan Özet görünümü gibi bir satır içi sunucu, varolan içeriği değiştirerek yeni içerik için alan oluşturur.

    - Kullanıcıların, var olan içeriğe başvuruda bulunan veya bu içerikle etkileşime geçen önemli miktarda süre harcamalarını istiyorsanız satır içi sunucuları **tercih** edin.

    - Kullanıcıların, mevcut bilgilere göz önüne almak istiyorsanız satır içi sunucuları kullanmaktan kaçının, daha sonra ana göreviyle en düşük kesintiye **uğramaya** devam edin.

2. **Kayan:** bir kayan sunucu, seçilen içeriğe olabildiğince yakın şekilde konumlandırılır ancak mevcut içeriğin yerleşimini değiştirmez. Seçilen simgenin en yakın kullanılabilir boşluk üzerinde kayan bir içerik paneli görüntüleme gibi çeşitli stratejiler çalıştırılabilir.

    - Kullanıcıların, mevcut bilgilere göz atma izni vermek istiyorsanız kayan sunucuları **tercih** edin, ardından en düşük kesintiye uğramadan ana görevine devam edin.

    - Kullanıcıların, var olan içeriğe başvuruda bulunmak veya bu içerikle etkileşime geçmek için önemli miktarda süre harcamasını istiyorsanız kayan sunucuları **önleyin** .

#### <a name="content-type"></a>İçerik türü
 Herhangi bir nesne için Kullanıcı arabirimi kapsayıcısı içinde görüntülenebilen üç ana içerik türü vardır. Bu tür bilgilerin herhangi bir birleşimi görüntülenebilir. Üç tür şunlardır:

1. **Bilgilendirici:** çoğu nesne Kullanıcı arabirimi kapsayıcısı, bazı bilgilendirici içerik görüntüler. İçerik, ortamın mevcut durumuyla ilgili bilgileri temsil edebilir veya ortamın olası gelecekteki durumuyla ilgili bilgileri temsil edebilir. Örneğin, var olan koddaki yeniden düzenleme gibi belirli bir komutun etkisini göstermek için kullanılabilir.

    - **Her zaman** , görüntülenen bilgilerin kurallı gösterimini kullanın. Örneğin, kod gibi görünmelidir, söz dizimi vurgulaması ile tamamlandı ve kullanıcının ayarlamış olduğu yazı tipi ve diğer ortam ayarlarına göre.

    - Aynı bilgiler ana içerik olarak sunulursa, **her zaman** bilgilendirici içerik üzerinde her türlü eylemi desteklemeyi düşünün. Örneğin, var olan kodu bir nesne Kullanıcı arabirimi kapsayıcısı içinde sunliyorsanız, bu koda göz atmayı ve değiştirebilme özelliğini kesinlikle göz önünde bulundurun.

    - Potansiyel olarak gelecekteki bir durumu temsil eden bilgilendirici içerik sunarken, **her zaman** farklı bir arka plan rengi kullanmayı düşünün.

2. İşlem yapılabilir: bazı nesne içi kullanıcı arabirimi kapsayıcıları, bir yeniden düzenleme işlemi gerçekleştirme gibi, ana içerik üzerinde bazı eylemler gerçekleştirme yeteneği sağlar.

    - Eylem yapılabilir komutları **her zaman** bilgilendirici içerikten ayrı olarak konumlandırın.

    - Uygun olduğunda **her zaman** eylemleri etkinleştirin ve devre dışı bırakın.

    - İletişim kutularındaki komutları temsil etmek için **her zaman** standart yönergelere başvurun.

    - **Her zaman** bir nesne içi kullanıcı arabirimi kapsayıcısında sunulan eylemlerin sayısını mutlak en düşük bir değer olarak tutun. Nesne üzerine Kullanıcı arabirimi ile etkileşim kurmak hafif ve hızlı bir deneyim olmalıdır. Kullanıcının, nesne üzerindeki UI kapsayıcısının kendisini yönetme konusunda enerji almak zorunda olmaması gerekir.

    - Bir nesne üzerinde kullanıcı arabirimi kapsayıcısının nasıl ve ne zaman kapatılacağını **her zaman** düşünün. En iyi uygulama olarak, ana ve ayrıntı içeriği arasındaki iletişim kutusunu izleyen herhangi bir eylem, bu eylem çağrıldığında nesne içi kullanıcı arabirimi kapsayıcısını de kapatacaktır.

3. **Gezinti:** bazı nesneler arası kullanıcı arabirimi kapsayıcıları, kullanıcıyı kullanıcının Web TARAYıCıSıNDA bir MSDN makalesini açmak gibi başka bir pencere veya uygulamaya alan bağlantılar içerir.

    -  Tüm gezinme bağlantılarını "açık" olarak ekleyin, böylece kullanıcılar başka bir içeriğe gezinerek şaşırmaz.

    - Gezinti bağlantılarını **her zaman** eyleme dönüştürülebilir bağlantılardan ayırın.

#### <a name="ambient-indicators-optional"></a>Çevresel göstergeler (isteğe bağlı)
 Çevresel göstergeler, kodun geri kalanında bir karşıt renkle sunulan metin veya süslü çizgiler ve akıllı etiket simgeleri gibi Tickler sembolleri dahil olmak üzere daha hafif olabilir. Çevresel göstergeler, ek ve ilgili bilgilerin kullanılabilirliğini iletişim kurar. İdeal olarak, kullanıcının bunlarla etkileşime girmesini gerektirmeden bile faydalı bilgiler sağlar.

- Bir çevresel göstergeyi **her zaman** , kullanıcının dikkatini veya şaşırmaması için konumlandırır. Bir ortam göstergesini böyle bir şekilde konumlandırmak imkansız ise, başka bir çözüm düşünün.

- Çevresel göstergeyi, ilişkili olduğu içeriğe olabildiğince yakın bir **şekilde konumlandırın.**

- **Her zaman** kullanılabilir hale getiren bilgileri özetleyen bir gösterge oluşturmayı deneyin. Kullanılabilir veri öğelerinin sayısını (örneğin, yalnızca "Başvurular" yerine "3 başvuru") veya verileri özetlemek için başka bir yol kullanmayı düşünün.

  - Bir göstergedeki verilerin her zaman hesaplanamadığı ve gösterileceği durumlarda, değerler hesaplandıktan sonra hemen aşamalı geri bildirim sağlamayı düşünün. Örneğin, okunmamış e-postaların sayısı arttıkça, e-posta canlı kutucuğunun Windows Phone yenileme biçimine benzer şekilde, kullanılabilir verilere yönelik güncelleştirmeleri yansıtan değişiklikleri hareketlendirmek göz önünde bulundurun.

- Bir kullanıcının belirli bir içerik parçası için makul bir şekilde gidebileceğinden, **hiçbir zaman** daha fazla gösterge eklemeyin. Çevresel göstergeler, kullanıcıdan herhangi bir etkileşime gerek duymadan yararlı olmalıdır. Göstergeler, taşma ve diğer yönetim denetimlerinin görünüme getirilmesi için Ambience kaybeder.

#### <a name="gestures"></a>Hareketler
 Kullanıcının ana içerikte odak korumasına izin vermenin önemli bir yönü, ek ayrıntı içeriğini açmak ve kapatmak için doğru hareketleri desteklemelidir.

- Kullanıcının ek içeriği açmak için **her zaman** açık bir hareket gerçekleştirmesini isteyin. Ortak açık hareketler şunları içerir:

  - **Üzerine gelme:** araç ipuçları veya etkileşimli olmayan bilgilendirici içerik

  - **Açık komut:** satır içi sunucu

  - **Çevresel göstergeyi çift tıklatın:** CodeLens açılır penceresi

- Kullanıcı ESC tuşuna her bastığında ayrıntı içeriğini **her zaman** kapatın.

- **Her zaman** , nesne üzerindeki kullanıcı arabiriminin bağlamını düşünün. Kapsayıcı içinde etkileşime izin veren içerik sunucuları için, kullanıcının iş akışına kesintiye uğratan, üzerine gelme konusunda ek bilgi gösterilip gösterilmeyeceğini dikkatle düşünün.

- Düzenleme veya davet eden kullanıcı etkileşimi gibi görünen bir içeriği **hiçbir** şekilde gösterme. Bu davranış, imleci ayrıntı içeriğinin üzerine taşımaya çalışırlarsa, bir araç ipucu için standart davranış, imleç onu üreten ana içerik üzerinde olmadığında hemen yok etmek üzere, kullanıcıların bu davranışı ortaya çıkar.

## <a name="selection-models"></a><a name="BKMK_SelectionModels"></a> Seçim modelleri

### <a name="overview"></a>Genel Bakış
 Seçim modeli, Kullanıcı arabirimi içinde ilgilendiğiniz bir veya daha fazla nesnede işlemleri göstermek ve onaylamak için kullanılan mekanizmadır. Bu konu başlığı altında, Visual Studio belge düzenleyicilerinde seçim etkileşimi desenleri ele alınmaktadır: metin düzenleyicileri, tasarım yüzeyleri ve modelleme yüzeyleri.

 Kullanıcılar, Visual Studio 'Nun üzerinde çalıştıkları şeyi gösteren bir yola sahip olmalıdır ve Visual Studio 'nun, ne işe çalıştıkları hakkında kullanıcılara geri bildirimde bulunarak tahmine dayalı olarak yanıt vermesi gerekir. Kullanıcı ve Kullanıcı arabirimi arasındaki farklar veya bir iletişim, kullanıcının istenmeyen sonuçlara neden olabilecek bir eylem yaşıyorsanız. Genellikle, hata, Kullanıcı bir şeyin eksik olduğunu veya değiştiğini görene kadar fark edilmemiş olur. Bu nedenle, Kullanıcı arabirimi tasarımının en kritik parçalarından biri seçim modelleri. Visual Studio 'daki seçim modelleri Windows ile tutarlı olsa da, hafif çeşitlemeler vardır.

 Visual Studio 'da, Windows 'daki gibi seçim modelleri, etkileşimin gerçekleştiği içeriğe göre farklılık gösterir. Seçimler dört tür nesnede gerçekleşebilir:

- Metin

- Grafik nesneleri

- Listeler ve ağaçlar

- Kılavuzlar

  Bu nesneler içinde üç tür seçim vardır:

- Peşe

- Kopuk

- Region

#### <a name="scope"></a>Kapsam
 Seçimin en önemli bileşeni, kullanıcının hangi pencerede çalıştığını (etkinleştirme) ve odağın nerede bulunduğunu (seçim) bilmesini sağlamaktır. Visual Studio, Windows 'daki pencere yönetimi işlevselliğini genişletir, ancak etkinleştirme düzeni aynıdır: bir pencereyle etkileşim, odağı pencereye taşır. Visual Studio 'Da etkinleştirme için iki gösterge bulunur: bir belge penceresi, diğeri de araç pencereleri içindir.

 Belge pencereleri için etkin pencere, önde gelen ve arka plan rengini değiştiren bir belge penceresi sekmesi tarafından belirtilir:

 ![Visual Studio 'da etkin sekme seçimi](../../extensibility/ux-guidelines/media/0713-01_activetab.png "0713-01_ActiveTab")

 **Etkin sekme seçimi**

 Araç pencereleri için etkin pencere, araç penceresinin başlık çubuğu alanının renginizdeki bir değişiklik ile belirtilir:

 ![Visual Studio 'da etkin araç penceresi seçimi](../../extensibility/ux-guidelines/media/0713-02_activetoolwindow.png "0713-02_ActiveToolWindow")

 **Bir düğümün birincil seçimini gösteren etkin araç penceresi**

 ![Visual Studio 'da etkin olmayan araç penceresi seçimi](../../extensibility/ux-guidelines/media/0713-03_inactivetoolwindow.png "0713-03_InactiveToolWindow")

 **Etkin olmayan araç penceresi, düğümün görünmeyen seçimini gösterir**

 Bir pencere etkin olduktan sonra, odağı bu bölümde açıklanan seçim modellerine göre gösterilir.

#### <a name="context"></a>Bağlam
 Visual Studio, kullanıcının nerede çalıştığını izlemek için güçlü bir bağlam kavramı tutmak üzere tasarlanmıştır. Bir araç veya belge penceresi olup olmadığı tek bir pencere etkin olur. Ancak, en üstteki belge penceresi her zaman bir seçimi korur. Odak bir araç penceresinde olsa da, son etkin olan belge penceresi, etkin olmayan bir durumda bile bir seçim görüntüler. Bu, kullanıcının içeriğini düzenlemekte oldukları belgede bekletmek için yapılır, böylece araç pencereleri ve belge pencereleri arasında sorunsuz bir şekilde dönebilmeleri için Visual Studio 'Nun durumlarını korumuştur.

### <a name="text-selection"></a>Metin seçimi
 Yerleşik metin Düzenleyicisi gibi tamamen metin olan Visual Studio düzenleyicileri, MSDN 'deki Windows Kullanıcı deneyimi etkileşim yönergelerinin [fare ve işaretçiler](/windows/desktop/uxguide/inter-mouse) sayfasında açıklanan metin seçimi modelini ve görünümünü kullanır. Metin düzenleyicisinde giriş odağı, ekleme noktası olarak adlandırılan dikey bir çubukla belirtilir. Ekleme noktası tek bir piksel kalın ve arkasında görülen her şeyi ters çevir olarak renklendirilir. Denetim Masası 'ndaki **klavye** uygulamasının **hız** sekmesinde, **imleç yanıp sönme hızı** ayarıyla ayarlanan hıza göre yanıp söner.

#### <a name="contiguous-and-disjoint-selection"></a>Bitişik ve ayrık seçim
 Metin düzenleyici içindeki seçim yalnızca bitişik. Ayrık metin seçimlerine izin verilmez, ancak grafik nesne düzenleyicilerde değinilmesi gerekir. Kullanıcının fare işaretçisi bir metin alanının üzerindeyken, imleç bir I uçlu şekilde değişir. Tek bir tıklama, ekleme noktasını, tıklama konumundaki metin düzenleyicisine koyar. Fare düğmesi aşağı basılı tutulması bir seçim vurgulaması başlatır ve fare düğmesi serbest bırakıldığında seçim Vurgusu sona erer.

#### <a name="region-selection-box-selection"></a>Bölge seçimi (kutu seçimi)
 Visual Studio metin düzenleyicisinde bölge seçimlerini destekler ve bu seçenek kutu seçimi olarak adlandırılır. Kutu seçimi, kullanıcının normal metin akışını izleyen bir metin bölgesi seçmesine olanak sağlar. Standart metin seçiminde olduğu gibi seçim de bitişik olmalıdır. Kutu seçimi, fare ile sürüklerken Alt tuşunu basılı tutarak başlatılır. Kutu seçimi, seçim bölgesini göstermek için ok tuşlarını kullanırken alt ve SHIFT tuşlarını basılı tutarak da başlatılabilir. Kutu seçimi normal seçim vurgulamasını kullanır ve seçim alanının sonunda ekleme noktası imlecinin yanıp sönmesini gösterir.

 ![Bölgesel &#40;kutusu&#41; Visual Studio 'da seçimi](../../extensibility/ux-guidelines/media/0713-04_boxselection.png "0713-04_BoxSelection")

 **Visual Studio 'da bölge (Box) seçimi**

#### <a name="text-selection-appearance"></a>Metin seçimi görünümü
 Düzenleyicide etkin ve etkin olmayan seçim için kullanılan renkler özelleştirilebilir. Düzenleyicinin görsel görünümünü özelleştirmek için, bir Kullanıcı **araçlar > seçeneklere** gidebilir ve ardından **ortam > yazı tipi ve renkler > metin Düzenleyicisi**' ne bakın.

### <a name="graphical-selection"></a>Grafik seçimi

#### <a name="interaction"></a>Etkileşim
 Grafik nesnesi seçimi karmaşık olabilir ve bir dizi etkene bağlıdır:

- **Düzenleyicinin birincil seçim modeli.** Grafik nesneleri içeren düzenleyiciler, metin veya ızgaralar düzenlemek için de kullanılabilir. Örneğin, düzenleyici, Visual Studio XAML Tasarımcısı gibi grafik nesnelerin yerleşimini de destekleyen metin tabanlı bir düzenleyici olabilir. Birden çok nesne türünü desteklemek, kullanıcının farklı nesne türlerinden oluşan grupları nasıl seçeceğine ilişkin bir etkisi olabilir.

- **Birincil ve ikincil seçim durumları için destek.** Bir düzenleyici, birincil ve ikincil seçim durumları sağlayarak nesnelerin uyum içinde düzenlenebilmesini, birbirleriyle hizalı, birlikte yeniden boyutlandırılabilmesini sağlar.

- **Yerinde Düzenle desteği.** Düzenleyiciler ayrıca grafik nesnelerinin içeriğinin düzenlenmesine da izin verebilir. Örneğin, bir dikdörtgen şekli, içinde Kullanıcı tarafından değiştirilebilen metin de içerebilir. Ayrıca, bu metin ortalandı veya hizalı olabilir. Yerinde düzenleme, kullanıcı etkileşiminin daha ayrıntılı bir düzeyini içerir ve bu nedenle, kullanıcıya durum bilgilerini sunmak için uygun bir görsel ipucu kümesi gerektirir.

#### <a name="mouse-interaction"></a>Fare etkileşimi

|Giriş|Sonuç|
|-----------|------------|
|Seçilmemiş bir nesneye tıklayın|Nesneyi seçer ve nesne yeniden boyutlandırılabilir ise kesikli çizgi ve seçim tutamaçları görüntüler.|
|Seçili bir nesneye tıklayın|Nesne destekliyorsa, yerinde düzenlemesini etkinleştirir. Nesnenin dışına tıklamak yerinde Düzenle modunu devre dışı bırakır.|
|Bir nesneye çift tıklayın|Düzenlenmek üzere nesnenin arkasındaki kodu açar ve uygunsa varsayılan olay işleyicisini ekleyebilir.|
|Bir nesnenin üzerine gelin|İşaretçiyi taşıma imlecine dönüştürür. Nesnenin parlaklık veya rengi gibi görünümü değişebilir.|
|Seçim tutamacının üzerine gelin|İşaretçiyi yeniden boyutlandırma imlecine dönüştürür. Döndürmeyi destekleyen nesneler için, işaretçi farklı konumlandırılmış (örneğin, daha uzağa taşınmış) seçim tanıtıcısına göre işaretçiyi bir döndürme imlecine değiştirebilir.|
|Sürükleyin|Nesne daha önce seçili olmasa bile, işaretçiyi taşıma imlecine değiştirir ve nesneyi taşır.|
|Düzenleyici odağı kaybeder|Nesne, son işlem/seçim durumu sırasında bulunan içeriği ve görünümü koruyabilse de yerinde Düzenle modunu devre dışı bırakır.|
|Nesne seçimi|Nesnenin sınırını vurgulamak için bir kenarlık, noktalı çizgi veya diğer görsel olarak farklı bir işleme tarafından gösterilir.|
|Seçili nesneyi yeniden boyutlandır|Seçim tutamaçlarının gösterdiği.<br /><br /> Yeniden boyutlandırılabilir bir nesnenin sekiz tutamacı vardır ve bu, yeniden boyutlandırılabileceği her yönü temsil eder. Nesne yalnızca belirli yönlere yeniden boyutlandırılabileceği takdirde daha az işleyici kullanılabilir. Kullanıcı bir nesneyi sekiz tutamacı etkileşimli olmadığı yere doğru olarak boyutlandırır dört tanıtıcı kullanılabilir. İşleme boyutları, ekran çözünürlüğüyle orantılı bir şekilde boyutlanmak için **getsystemölçümlerini** API işleviyle birlikte pencere kenarlığına ve uç ölçümlerine bağlı olmalıdır.<br /><br /> ![Yeniden boyutlandırma tutamaçları](../../extensibility/ux-guidelines/media/0713-05_resizehandles.png "0713-05_ResizeHandles")|
|Seçilen nesneyi döndürün|![Tutamaçları döndürme](../../extensibility/ux-guidelines/media/0713-06_rotate.png "0713-06_Rotate")|

#### <a name="keyboard-interaction"></a>Klavye etkileşimi

|Giriş|Sonuç|
|-----------|------------|
|Tab|Odak göstergesini düzenleyicideki nesnelerin mantıksal sıralaması arasında kaydırır. Bu, **TabIndex** (veya eşdeğeri) özellik değerine, nesne oluşturma sırasına ve düzenleyicinin genel amacına bağlı olarak soldan sağa veya yukarıdan aşağıya doğru olabilir. SHIFT + TAB odak göstergesinin yönünü tersine çevirir.|
|Boşluk çubuğu|Tuş vuruşu korunurken kaydırma modunu etkinleştirir. Görünüm penceresinin konumunu kaydırmak için ek fare girişi gerekir.|
|Ctrl+Ara Çubuğu|Tuş vuruşu korunurken yakınlaştırma modunu etkinleştirir. Yakınlaştırma faktörünü artırmak ve azaltmak için ek fare girişi gerekir.|
|Ctrl + Alt + eksi Işareti|Yakınlaştırma faktörünü bir düzey azaltır.|
|Ctrl + Alt + artı Işareti|Yakınlaştırma faktörünü bir düzey artırır.|
|SHIFT veya CTRL|Nesneyi seçim grubuna ekler. CTRL, nesneleri seçim grubundan ayrı ayrı kaldırmanıza de olanak tanır.|
|Enter|Nesne için varsayılan komutu gerçekleştirir (genellikle açık veya düzenleme).|
|F2|Nesne için yerinde düzenlemeleri etkinleştirir.|
|Ok tuşları|Seçilen nesneleri ok tuşunun yönünde, küçük artışlarla (örneğin, bir kerede 1 piksel) taşır|
|CTRL + ok tuşları|Ok tuşunun yönündeki seçili nesneleri daha büyük artışlarla (örneğin, her seferinde 10 piksel) taşımalar|
|SHIFT + ok tuşları|Seçili nesneleri, küçük artışlarla (örneğin, her seferinde 1 piksel), ilgili yönde yeniden boyutlandırır|
|CTRL + SHIFT + ok tuşları|Seçili nesneleri, daha büyük artışlarla (örneğin, her seferinde 10 piksel), ilgili yönde yeniden boyutlandırır|

 Kullanıcılar denetimleri yerinde düzenliyorsa, nesnelerin Kullanıcı girişiyle otomatik olarak yeniden boyutlandırılması mantıklıdır. Örneğin, Kullanıcı bir etiket denetimini düzenlerse, kullanıcının yalnızca yazdığından metni görüntülemesi için etiketin büyümesi gerekir. Bu yapılmazsa, kullanıcının metni düzenledikten sonra denetimi el ile yeniden boyutlandırılması gerekir. Kullanıcının çok sayıda denetimi varsa bu, bir Rote ve üretken olmayan bir görev haline gelir.

#### <a name="graphical-containers"></a>Grafik kapsayıcıları
 Grafik düzenleyicileri, bazı durumlarda Windows Forms panel denetimi veya HTML Tasarımcısı içindeki kılavuz düzen denetimi gibi diğer grafik nesneleri için kapsayıcılar sağlar. Düzenleyiciniz diğer grafik nesneleri için kapsayıcılar sağlıyorsa, şu seçim modelinin yalnızca kapsayıcı için kullanılması gerekir (kapsayıcıdaki nesneler, yukarıda açıklandığı gibi standart modeli izler):

|Giriş|Sonuç|
|-----------|------------|
|Kapsayıcıya tek tıklama|Kapsanan nesnelerden hiçbirini doğrudan seçmeden kapsayıcı nesnesini seçer. Kapsayıcı, standart fare ve klavye girişi (yukarıda açıklandığı gibi) ile taşınabilir ve/veya yeniden boyutlandırılabilir. Kapsanan nesneler kapsayıcıya göre taşınır, ancak aynı zamanda doğrudan seçilmedikleri takdirde içerilen nesneler yeniden boyutlandırılmaz.|
|Kapsayıcının sınır bölgesinin üzerine gelme|Kapsayıcının taşınabileceğini belirten, fareyi taşıma imlecine dönüştürür.|
|Kapsayıcının sınır bölgesini sürükleyin|Fareyi taşıma imlecine dönüştürür ve kapsayıcıyı (ve kapsanan nesneleri içinde) taşır. Kapsayıcı, ilk olarak tek bir tıklama ile seçilmeden taşınamaz.|
|Kapsayıcı içindeki bir nesneye tek tıklama|Kapsayıcının seçimini kaldırır (seçilmişse) ve yalnızca tıklanan nesneyi seçer.|
|Kapsanan nesne ve/veya kapsayıcıya SHIFT + tıklama veya CTRL + tıklama|Tıklanan nesneyi varolan bir seçime veya seçim grubuna ekler. Tıklanan nesne zaten seçim grubunun bir üyesiyse, seçim grubundan kaldırılır.|

 Kapsanan nesneler, önceki bölümde açıklandığı gibi temel seçim modeline uymalıdır. Windows Forms tasarımcısının kullanılabilirlik testinde, kullanıcılar, adımları açmadan içerilen nesnelere sorunsuz erişim (kapsama nesnesi tarafından uygulanan) bekliyordu.

#### <a name="disjoint-and-region-selections"></a>Ayrık ve bölge seçimleri
 Grafik nesne düzenleyicileri ayrık seçimleri desteklemelidir. Lütfen bu grafiğin, Visual Studio 'nun denetim görünümünü göstermediğini unutmayın. Ayrıntılı görsel özellikler için bkz. [grafik nesnesi seçim görünümü](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_GraphicalObjectSelectionAppearance) .

 ![Ayrık ve bölge seçicileri](../../extensibility/ux-guidelines/media/0713-07_disjointregionselectors.png "0713-07_DisjointRegionSelectors")

 **Ayrık seçim**

 Grafik düzenleyiciler Ayrıca, bir kayan yazı türü seçim göstergesi olan bölge seçimleri de sağlamalıdır. Grafik düzenleyici diğer nesne türlerini (örneğin, metin) destekliyorsa, diğer nesne türlerinin kısıtlamalarına bağlı olarak bölge seçimleri mümkün olmayabilir.

 ![Seçim çerçevesi seçimi](../../extensibility/ux-guidelines/media/0713-08_marqueeselection.png "0713-08_MarqueeSelection")

 **Seçim çerçevesi seçimi**

#### <a name="primary-and-secondary-selections"></a>Birincil ve ikincil seçimler
 Bazı grafik nesne düzenleyicileri, kullanıcının gruplardaki nesneleri düzenlemesine veya hizalamaya izin verir. Bu durumda, birincil ve ikincil seçimlerin kavramının tanıtılması gerekir. Birincil seçim, tüm diğer nesnelerin grup işlemleri için yanıt verdiği nesnedir. Önce kullanıcının seçtiği nesne birincil denetim olur ve sonraki seçimler ikincil seçimler haline gelir. Birincil seçimin hangi nesnenin birincil olduğunu göstermek için ikincil seçimlerden ayrı bir görsel işleme sahiptir:

 ![Birincil ve ikincil seçim](../../extensibility/ux-guidelines/media/0713-09_primarysecondary.png "0713-09_PrimarySecondary")

 **İki ikincil seçim içeren birincil seçim**

#### <a name="graphical-object-selection-appearance"></a><a name="BKMK_GraphicalObjectSelectionAppearance"></a> Grafik nesnesi seçim görünümü
 Seçim tutamaçları, nesnenin sınırlayıcı kutusunun etrafında dikdörtgen bir düzende çizilmiş kareler. Aşağıdaki grafik, bir grafik nesnesinin tanıtıcı, boyutlandırma ve yerinde düzenlenme görünümü ile sahip olduğu çeşitli durumların örneklerini gösterir. Tanıtıcıların boyutu, **getsystemölçümlerini** API kullanılarak pencere kenarlığına ve Edge ölçümlerine bağlı olmalıdır.

| Durum | Görünüm | Görsel Ayrıntılar |
|-------------------------|---------------| - |
| **Değilken** | Varsayılan | ![Varsayılan düğme durumu](../../extensibility/ux-guidelines/media/0713-10_defaultstate.png "0713-10_DefaultState") |
| **Birincil seçim** | Boyutlandırılabilir | ![Yeniden boyutlandırma tutamaçlarıyla birincil seçim](../../extensibility/ux-guidelines/media/0713-11_primaryresize.png "0713-11_PrimaryResize") |
| **Birincil seçim** | Yeniden boyutlandırılabilir | ![Yeniden boyutlandırma tutamaçları olmadan birincil seçim](../../extensibility/ux-guidelines/media/0713-13_primarynoresize.png "0713-13_PrimaryNoResize") |
| **Birincil seçim** | Kilitli | ![Birincil seçim kilitli](../../extensibility/ux-guidelines/media/0713-15_primarylocked.png "0713-15_PrimaryLocked") |
| **İkincil seçim** | Boyutlandırılabilir | ![Yeniden boyutlandırma tutamaçlarıyla ikincil seçim](../../extensibility/ux-guidelines/media/0713-17_secondaryresize.png "0713-17_SecondaryResize") |
| **İkincil seçim** | Yeniden boyutlandırılabilir | ![Yeniden boyutlandırma tutamaçları olmadan ikincil seçim](../../extensibility/ux-guidelines/media/0713-19_secondarynoresize.png "0713-19_SecondaryNoResize") |
| **İkincil seçim** | Kilitli | ![İkincil seçim kilitli](../../extensibility/ux-guidelines/media/0713-21_secondarylocked.png "0713-21_SecondaryLocked") |
| **UI etkin** | Varsayılan | ![UI etkin durumu](../../extensibility/ux-guidelines/media/0713-23_uiactive.png "0713-23_UIActive") |

### <a name="view-selection-models"></a>Seçim modellerini görüntüle

#### <a name="tree-view"></a>Ağaç görünümü
 Ağaç görünümünde seçim basit bir vurgulamada gösterilir. Kullanıcı bir düğüm adına veya düğüm simgesine tıklarsa düğüm seçili hale gelir. Düğümün sol tarafındaki üçgen Glifler ağaç denetimini genişletir veya anlaşma sağlar, ancak bir özel durumla birlikte kullanıcının seçimini etkilemez: bir üst düğümü daraltdıktan sonra seçim bu düğümün alt öğesi üzerinde olduğunda seçim üst öğeye gider.

 ![Visual Studio 'da tipik ağaç görünümü](../../extensibility/ux-guidelines/media/0713-25_treeview.png "0713-25_TreeView")

 **Visual Studio 'da tipik ağaç görünümü**

 Ağaç görünümleri, ağaç içindeki birden çok düzeyde bile ardışık ve ayrık seçimleri destekleyebilir. Görünür ağaç düğümlerinde bitişik veya ayrık birden çok seçim yapılmalıdır. Düğüm daraltılmışsa ayrık seçim kaybolur ve daraltılan düğüm seçimi alır. Bu şekilde, Kullanıcı bir işlemden etkilenecek düğümleri görebilir. Düğümler daraltıldığında, bu, hangi düğümlerin etkilendiğine yönelik belirsiz hale gelir.

 Bir üst düğüm seçildiğinde, işlem üst öğeye uygulanır, ancak bir işlemin üst ve tüm alt öğelerine uygulanmasını mantıklı bir durum olabilir. Bu durumda, işlem sırasında, "tüm alt öğelere Uygula" seçeneğini kullanıcıya açık hale getirmek için bir onay kutusu veya onay iletişim kutusu gibi ek kullanıcı arabirimi sağlayın.

##### <a name="renaming"></a>Adlandırıl
 Ağaçtaki düğümler yeniden adlandırmayı destekliyorsa, yeniden adlandırma işlemi yerinde yapılmalıdır. Yerinde işlem, Visual Studio 'daki tüm ağaç denetimlerinde standart olmalıdır. Yerinde değiştirme modunu hemen etkinleştiren, Kullanıcı girişini kabul etmeye izin veren, düğüm adının tamamını kapsayan metin seçimiyle birlikte yeniden adlandırma komutu sağlayın. Düğüm bir dosyayı temsil ediyorsa, dosya adı uzantıyı içermelidir. Seçim vurgusu, uzantının değil yalnızca dosya adının gövdesini içermelidir.

|Giriş|Sonuç|
|-----------|------------|
|Enter tuşu|Yeniden adlandırma işlemini kaydeder|
|ESC tuşu|Yeniden adlandırma işlemini iptal eder|
|Yerinde düzenleme bölgesinin dışına tıklanın|Yeniden adlandırma işlemini kaydeder|
|Geri Al|Yeniden adlandırma işlemini iptal etmek için kolay geri alma sağlayın|

#### <a name="selection-within-lists-and-grid-controls"></a>Listeler ve kılavuz denetimleri içinde seçim
 Liste seçiminde anahtar kavram, satır tabanlı olduğundan, bir seçim yapıldığında satırın tamamı bir birim olarak seçilme anlamına gelir. Bunun aksine, ızgaralar belirli hücrelerin satırın diğer yönlerini etkilemeden seçilebilirler. Kılavuzlar Ayrıca, üst satırlarla etkileşime girerek hiyerarşinin tüm dallarının seçilemeyeceği ve seçiminin kaldırılmasına izin veren iç içe geçmiş satır (ağaç kılavuzunda olduğu gibi) hiyerarşisi de içerebilir. Listelerdeki seçim, tüm veri satırları üzerinde basit bir vurgulama rengiyle gösterilir. Odak, geçerli düzenlenebilir satır veya hücrenin çevresinde tek piksellik noktalı bir kenarlık ile gösterilir (tüm hücreler salt okunurdur, satır).

> [!NOTE]
> **Odak** ve **seçim** farklı kavramlardır. *Odak* , başka bir nesneye açıkça yönlendirilmeyen Kullanıcı arabirimini hangi UI öğesinin alacağını hedefleyen bir belirtidir, *seçim* sırasında, sonraki işlemlerin gerçekleştiği bir nesne kümesine dahil olan bir nesnenin durumunu ifade eder.

 Listelerdeki seçimler bitişik, ayrık veya bölge olabilir. Birden çok seçime izin verildiğinde, bitişik ve ayrık seçim her zaman desteklenmelidir, ancak bölge desteği (Box) seçimleri isteğe bağlıdır. Bölge seçimleri, liste gövdesinin beyaz alanında sürükleyerek başlatılır.

| Nesne | Seçim |
|--------|------------|
| Liste | Peşe |
| Liste | Kopuk |
| Liste | Region |

 Bir listede bir kez tıklamak, tıklama gerçekleştiği satırı seçer. Kullanıcı yerinde düzenlemeden desteklenen bir liste hücresinde tıklamaya çalışıyorsa, hücre yerinde düzenlemede de hemen etkinleştirilir. Aksi takdirde, tüm satır hemen seçilir ve bir vurgu gösterir.

 Liste gövdesinde sürüklemek üç işlemlerden birini yapar:

- Liste destekliyorsa ve fare tuşu beyaz boşludeyse bölge seçimini başlatır

- Liste hücresi veya satırı Sürükle kaynağı olmasını destekliyorsa sürükle/bırak işlemini başlatır

- Geçerli satırı seçer

##### <a name="in-place-editing"></a>Yerinde düzenleniyor
 Yerinde düzenlemeye izin verildiğinde, iki temel model vardır: basit düzenleme denetimi ve özellik Seçicisi. Basit bir düzenleme denetimiyle, içerik vurgulanmıştır ve yerinde düzenleme etkinleştirilir başlamaz Kullanıcı girişi için de kullanıma yöneliktir. Bir özellik seçicisinin uygulandığı yerde, özellik seçiciyi çağıran düğme, yerinde Düzenle modu etkinleştirildiğinde ve geçerli seçim vurgulanmamışsa görüntülenir. Seçici düğmesi hücrede sağa hizalı olmalıdır. Yerinde düzenlenen örnekler için bkz. **Özellikler penceresi** ve Visual Studio 'da **görev listesi** .

##### <a name="keyboard-support"></a>Klavye desteği
 Listelerde ve kılavuzlarda seçim için klavye desteği standart Windows kurallarını izler:

- Ok tuşları listede gezinin, odak taşındığında her bir satır/hücreyi seçerek.

- SHIFT + ok, ok tuşlarının yönünde bir bitişik seçim gerçekleştirir.

- CTRL + ok ve ardından boşluk çubuğu, seçimden liste öğeleri ekleme ve kaldırma arasında geçiş yapar ve ayrık seçim oluşturur.

- İç içe hiyerarşilerin bulunduğu kılavuzlar için sağ ok tuşu bir üst satırı genişletir ve sol ok tuşu bir tane daraltır.

- Hücreler düzenlenebilir ise Tab tuşu geçerli satırdaki hücreler arasında taşınır.

- ENTER tuşu, listedeki öğede varsayılan komutu gerçekleştirir (genellikle **Açık**).

- F2 tuşu, şu anda seçili olan hücre için yerinde düzenlemeleri etkinleştirir.

## <a name="persistence-and-saving-settings"></a><a name="BKMK_PersistenceAndSavingSettings"></a> Kalıcılık ve kaydetme ayarları

### <a name="overview"></a>Genel Bakış
 Visual Studio 'daki her yazılım bileşeni genellikle kendi durumu ve kalıcılığına karşı sorumludur, ancak Visual Studio, ayarları pencere boyutları ve pozisyonları gibi bazı durumlarda otomatik olarak kaydeder. Aşağıdaki tabloda, otomatik olarak kaydedilen ayarların bir birleşimi ve açık bir Kullanıcı ya da programlanmış eylem yapılması gereken ayarlar verilmiştir.

|Nesne|Ne kaydedilecek|Ne zaman kaydedileceği|Kaydedileceği yer|
|------------|------------------|------------------|-------------------|
|Seçilebilir nesne (örneğin, bir kod satırı)|Kod satırında bir kesme noktası<br /><br /> Kod satırıyla ilişkili bir Kullanıcı kısayolu|Proje kaydedildiğinde|Projenin **Kullanıcı seçenekleri (. suo)** dosyası|
|İletişim|İletişim kutusunun taşındığı konum<br /><br /> Kullanıcının iletişim kutusunda son kullandığı görünüm|İletişim kutusu kapandığında<br /><br /> Visual Studio oturumu sona erdiğinde|Bellek içinde<br /><br /> **HKEY_Current_User** kayıt defteri|
|Pencere|Pencerenin boyutu ve konumu|Pencere kapandığında<br /><br /> Visual Studio modu değiştiğinde<br /><br /> Visual Studio oturumu sona erdiğinde|Projenin **Kullanıcı seçenekleri (. suo)** dosyası<br /><br /> Pencere ayarları için özel seçenekler dosyası|
|Belge|Belgedeki geçerli seçim<br /><br /> Belgenin görünümü<br /><br /> Kullanıcının ziyaret ettiği son birkaç yer|Belge kaydedildiğinde|Projenin **Kullanıcı seçenekleri (. suo)** dosyası|
|Project|Dosyalara başvurular<br /><br /> Disk üzerindeki dizinlere başvurular<br /><br /> Diğer yazılıma başvurular<br /><br /> Bileşenler<br /><br /> Projenin kendisiyle ilgili durum bilgileri|Proje kaydedildiğinde|Proje dosyası|
|Çözüm|Projelere başvurular<br /><br /> Dosyalara başvurular|Proje veya çözüm kaydedildiğinde|**Çözüm (. sln)** dosyası|
|**Araçlar > seçeneklerindeki** ayarlar|Klavye özelleştirmeleri<br /><br /> Araç çubuğu özelleştirmeleri<br /><br /> Renk şemaları|**Araçlar > seçenekleri** iletişim kutusu kapandığında<br /><br /> Visual Studio oturumu sona erdiğinde|**HKEY_Current_User** kayıt defteri|

 Kullanıcının ne yaptığını ve ne zaman yaptığına göre, bir ayarın bellekte (oturum sırasında) kaydedilip kaydedilmediğini (oturum sırasında), **çözüm seçenekleri (. suo)** dosyasının bir parçası olarak veya yalnızca yazılım bileşeninin bildiği özel bir ayar dosyası olarak, projenin veya çözüm dosyasının kendisinin bir parçası olarak (kayıt defteri ayarı olarak oturumlar arasında) kaydedilip kaydedilmediğini belirler. Yukarıdaki tabloda, ayarların kaydedilebileceği çeşitli olaylar gösterilmektedir. Ancak, durumu kaydetmek isteyebileceğiniz başka zamanlar da vardır:

- Kullanıcı bir iletişim kutusu veya pencere içindeki konumu değiştirdiğinde

- Kullanıcı odağı başka bir pencereye aktarsın

- Kullanıcı tasarımdan hata ayıklama moduna geçtiğinde

- Kullanıcı hesabının oturumunu kapattığında

- Bilgisayar hazırda beklemeye girdiğinde veya kapandığında

- Bilgisayar/sabit sürücü yeniden biçimlendirilme ve tekrar ayarlama hakkında

### <a name="window-configurations"></a>Pencere yapılandırması
 Bir pencere yapılandırması, geliştirme ortamının temel sunumudur. Bu, araç pencerelerinin ve düzenlenme şeklini içeren bir şemadır. IDE (IDE pencereleri) tarafından yönetilen Windows için, düzen bilgileri Kullanıcı başına kalıcı hale getirilir. bu nedenle, Kullanıcı IDE 'yi başlattığında pencere düzeni, Visual Studio 'Nun son çıktıkları zaman ile aynı görüntülenir. IDE pencerelerinin durum ve konumu, XML biçimindeki özel bir seçenekler dosyasında kalıcıdır. IDE 'ye yüklenen paketler tarafından oluşturulan araç pencereleri, kayıt defterindeki durum bilgilerini kalıcı hale getirerek, Kullanıcı başına olabilir veya olmayabilir.

#### <a name="profile-specific-layouts"></a>Profile özgü düzenler
 Her profil, belirli bir geliştirici personbuna tanıdık bir şekilde düzenlenmiş (Visual C++ geliştiricilerin IDE 'nin sol tarafında **Çözüm Gezgini** görmeyi beklediği, ancak C# geliştiricileri sağ tarafta **Çözüm Gezgini** görmeyi beklediği) araç penceresi düzenlerini içerir. Profile özgü pencere düzenleri, Kullanıcı başlangıçta bir profil seçtikten sonra yüklenir. Bir paket yazarı, kullanıcının pencere yapılandırmasına yaptığı değişikliklerin kalıcı hale gelmesini sağlamak için müşterinin deneyimine en uygun pencere yerleşimini belirlemelidir.

## <a name="touch-input"></a><a name="BKMK_TouchInput"></a> Dokunma girişi
 Kullanıcılar, dokunmatik cihazlarda Microsoft geliştirme ürünlerini giderek daha fazla kullanmaktadır. Ancak, dokunmatik cihazlarda geliştirme araçlarını kullanmayı zorlaştırmaya yönelik engelleri vardır. Kullanıcılar, ürünlerimizi güvenilir ve kesin bir dokunmatik deneyim sağlayacak şekilde beklecektir. Bu yönergelerin amacı, Visual Studio ve ilgili ürünler arasında tutarlı bir dokunmatik deneyim dahil etmek ve bunlara yönelik dokunma özellikleri hakkında kararlara bilgi almaktır.

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
 Hareketler kullanıcılara, aksi takdirde daha karmaşık bir etkileşim gerektiren komutlara yönelik bir kısayol sağlar. [Masaüstü uygulamaları için genel dokunma hareketlerinde](/windows/desktop/wintouch/windows-touch-gestures-overview)Windows yönergelerine bakın ve kaydırma ve yakınlaştırma gibi basit hareketler de dahil olmak üzere çoğu hareket için bu yönergeleri izleyin.
