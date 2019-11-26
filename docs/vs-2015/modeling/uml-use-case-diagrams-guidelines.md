---
title: 'UML Kullanım örneği diyagramları: yönergeler | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: b1ae8ed0-d00b-4f9b-8e23-733e09e81e9b
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c9ccd5285f9a2744704c0ee13094a1dac31c53b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302840"
---
# <a name="uml-use-case-diagrams-guidelines"></a>UML Kullanım Durumu Diyagramları: Yönergeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da, uygulamanızı veya sisteminizi kimin kullanacağını ve onunla neler yapabileceğini özetlemek için bir *kullanım durumu diyagramı* çizebilirsiniz. UML Kullanım örneği diyagramı oluşturmak için **mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın.

 Video gösterimi için bkz. [özellikleri kullanım örneklerine düzenleme](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases).

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Kullanım durumu diyagramı yardımıyla, tartışabilir ve iletişim kurabilirsiniz:

- Sisteminizin veya uygulamanızın kişilerle, kuruluşlara veya dış sistemlerle etkileşime girdiği senaryolar.

- Bu aktörlerin elde etmesine yardımcı olan hedefler.

- Sisteminizin kapsamı.

  Kullanım durumu diyagramı kullanım örneklerinin ayrıntılarını göstermez: yalnızca kullanım durumları, aktörler ve sistemler arasındaki ilişkilerin bazılarını özetler. Özellikle, diyagram her kullanım örneğinin hedeflerini elde etmek için adımların gerçekleştirildiği sırayı göstermez. Bu ayrıntıları diğer diyagramlarda ve belgelerde, her kullanım örneğine bağlayabileceğiniz bir şekilde tanımlayabilirsiniz. Daha fazla bilgi için bu konudaki [kullanım örneklerini ayrıntılı olarak açıklama](#Details) bölümüne bakın.

  Kullanım örnekleri için sağladığınız açıklamalar, sistemin çalıştığı etki alanı ile ilgili satış, menü, müşteri gibi çeşitli terimleri kullanacaktır. Bu terimleri ve bunların ilişkilerini açıkça tanımlamak önemlidir ve bunu UML sınıf diyagramı yardımıyla yapabilirsiniz. Daha fazla bilgi için bkz. [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md).

  Kullanım örnekleri yalnızca bir sistem için işlevsel gereksinimlerde ele. İş kuralları, hizmet kalitesi gereksinimleri ve uygulama kısıtlamaları gibi diğer gereksinimler ayrı olarak temsil etmelidir. Mimari ve iç Ayrıntılar ayrıca ayrı olarak açıklanmalıdır. Kullanıcı gereksinimlerinin nasıl tanımlanacağı hakkında daha fazla bilgi için bkz. [model Kullanıcı gereksinimleri](../modeling/model-user-requirements.md).

  Bu konu başlığında kullanılan örnekler, müşterilerin yerel restoranların ınals bilgilerini sipariş verebileceği bir Web sitesiyle ilgilidir.

  ![Kullanım örneği diyagramındaki öğeler](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

- *Aktör* (1), sisteminizle etkileşen bir kişi, kuruluş, cihaz veya dış yazılım bileşeni sınıfıdır. Örnek aktörler **Müşteri**, **Restoran**, **sıcaklık algılayıcısı**, **kredi kartı Yetkilendiricisi.**

- *Kullanım durumu* (2), belirli bir hedefin takip ettiği bir veya daha fazla aktör tarafından gerçekleştirilen eylemleri temsil eder. Örnek kullanım örnekleri, yemek, **güncelleştirme menüsü**, **işlem ödemesini** **sıralarlardır**.

   Kullanım durumu diyagramında kullanım örnekleri, bunları gerçekleştiren aktörlerle ilişkilendirilir (3).

- *Sisteminiz (4)* , geliştirmekte olduğunuz her şey. Aktör yalnızca diğer yazılım bileşenleriyle olan küçük bir yazılım bileşeni olabilir; ya da tamamen bir uygulama olabilir; ya da birçok bilgisayar ve cihaz üzerinde dağıtılan büyük bir dağıtılmış uygulamalar paketi olabilir. Örnek alt sistemler **yemek siparişi Web sitesi**, **yemek teslimatı iş**, **Web sitesi sürüm 2**' dir.

   Kullanım durumu diyagramı, sisteminiz veya alt sistemleri tarafından hangi kullanım örneklerinin desteklendiğini gösterebilir.

## <a name="BasicSteps"></a>Kullanım örneği diyagramları çizmek için temel adımlar

> [!NOTE]
> Modelleme diyagramlarından herhangi birini oluşturmaya yönelik ayrıntılı adımlar [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md)bölümünde açıklanmıştır.

#### <a name="to-create-a-new-use-case-diagram"></a>Yeni bir kullanım durumu diyagramı oluşturmak için

1. **Mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın.

2. **Şablonlar**altında, **Umluse Case Diyagramı**' na tıklayın.

3. Diyagrama ad verin.

4. **Modelleme projesine ekle**' de, çözümünüzde mevcut bir modelleme projesi seçin veya **Yeni bir modelleme projesi oluşturun**ve ardından **Tamam**' a tıklayın.

#### <a name="to-draw-a-use-case-diagram"></a>Kullanım durumu diyagramı çizmek için

1. Tüm sisteminizi veya onun ana bileşenlerini göstermek için **alt sistem** sınırlarını araç kutusundan diyagram üzerine sürükleyin.

    - Sisteminiz veya bileşenleri tarafından hangi kullanım örneklerinin desteklendiğini belirtmek istemiyorsanız, sistem sınırları olmadan kullanım durumu diyagramı çizebilirsiniz.

    - Gerekirse, bir sistemin köşesini sürükleyerek daha büyük bir hale getirin.

    - Uygun şekilde yeniden adlandırın.

2. Araç kutusundan **aktörleri** diyagrama sürükleyin (bunları herhangi bir sistem sınırının dışına yerleştirerek).

    - Aktörler, sistemlerinizle etkileşime geçen Kullanıcı, kuruluş ve dış sistemler sınıflarını temsil eder.

    - Yeniden adlandırın. Örneğin: **Müşteri, Restoran, kredi kartı kurumu.**

3. Araç kutusundan **kullanım örneklerini** uygun sistemlere sürükleyin.

    - Kullanım örnekleri, aktörlerin sisteminizin yardımıyla gerçekleştirdiği etkinlikleri temsil eder.

    - Aktörlerin anlayabilmesi için başlıkları kullanarak yeniden adlandırın. Kodunuz ile ilgili olan başlıkları kullanmayın. Örneğin: **yemek siparişi, yemek Için ödeme yapın ve yemek sunun**.

    - **Yemek siparişi**, daha sonra **menü öğesi seçme**gibi daha az etkileşimler bırakarak çıkış gibi önemli işlemler ile başlayın.

    - Her kullanım örneğini onu destekleyen sisteme veya birincil alt sisteme yerleştirin (yalnızca kullanıcıya bağlanmakla ilgili olan tüm façlade veya bileşenleri yok sayar).

    - Sistem sınırının dışında, belirli bir sürümde veya yayında sisteminizde desteklenmediğini göstermek için bir kullanım durumu çizebilirsiniz.

4. Araç kutusunda **Association** ' a ve ardından kullanım örneği ' ne ve ardından kullanım örneğine katılan bir aktöre tıklayın. Her aktöri bu şekilde kullanım örneklerine bağlayın.

5. Kullanım örneklerini **Include**, **Extend** ve **Genelleştirme** ilişkilerle yapı. Bu bağlantıların her birini oluşturmak için araca, ardından kaynak kullanım örneğine ve ardından hedefe tıklayın. [Kullanım örneklerini yapılandırma](#Structuring)başlıklı aşağıdaki bölüme bakın.

6. Kullanım örneklerini daha ayrıntılı olarak tanıtın. [Kullanım örneklerini ayrıntılı olarak açıklayan](#Details)aşağıdaki bölüme bakın.

7. Farklı alt sistemlere veya ilgili kullanım durumlarının farklı gruplarına odaklanmak için ayrı diyagramlar çizin. Tek bir modelleme projesindeki tüm diyagramlar aynı modelin görünümleridir.

## <a name="Actors"></a>Aktör ve kullanım durumları çizme
 Kullanım örneği diyagramının ana amacı, sisteminizle etkileşen kişileri ve bu uygulamayla elde ettikleri ana hedefleri göstersağlamaktır.

- Sistem veya alt sistemlerinizle etkileşime geçen kişi, kuruluş, diğer sistem, yazılım veya cihaz sınıflarını temsil eden **aktörler** oluşturun.

  - Aktörlerin ve diğer öğelerin nasıl çizileceğini öğrenmek için bkz. [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md).

  - Her farklı amaç kümesi için, fiziksel kişiler veya varlıklar aynı olsa bile, aktörleri türlerine veya rolüne göre belirleyin. Örneğin, Restoran ve müşteri farklı aktörlerdir, ancak Restoran çalışanı bazen bir müşteri olabilir.

- Her bir aktörün sistemle elde etmek için arama yapan hedeflerin her biri için **kullanım örnekleri** oluşturun.

  - Uygulama koşulları yerine aktörün anlayabileceği sözcüklerdeki kullanım örneklerini adlandırın ve tanıtın.

- Aktörleri kullanım örneklerine bağlamak için **ilişkilendirmeleri** kullanın.

### <a name="inheritance-between-actors"></a>Aktörler arasında devralma
 ![Devralmayı gösteren kullanım örneği diyagramı](../modeling/media/uml-ucguideinherit.png "UML_UCGuideInherit")

 Aktörler arasında **Genelleştirme** bağlantısı çizebilirsiniz. Örnekteki kulüp müşterisi gibi özelleştirilmiş aktör, müşteri gibi Genelleştirilmiş aktörün kullanım durumlarını devralır. Ok ucu, müşteri gibi daha genel aktöre işaret etmelidir. Bağlantıyı oluşturduğunuzda, ilk olarak daha özelleştirilmiş aktörün üzerine gelin.

 Özelleştirilmiş aktör, diğer aktörler tarafından kullanılamayan kendi ek kullanım örneklerine sahip olabilir.

> [!CAUTION]
> Bir aktörün kendisini genelleştirmeye neden olan genelleştirme ilişkilerinin döngülerini yapmamalıdır. Döngüler hata verebilir.

### <a name="alternative-actor-icons"></a>Alternatif aktör simgeleri
 Standart çubuk şekli yerine bir aktör göstermek için özel simgeler kullanabilirsiniz. Örneğin, bunu bir cihaza, restorana, bankaya benzer şekilde değiştirebilirsiniz.

##### <a name="to-change-the-appearance-of-an-actor"></a>Aktörün görünüşünü değiştirmek için

1. Aktör öğesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

     **Özellikler** penceresi görüntülenir.

2. **Görüntü yolu** özelliğini bir resim dosyasının konumuna ayarlayın.

    - . Gif,. jpg ve. bmp gibi birçok görüntü biçiminden birini kullanabilirsiniz.

    - Çözüm taşındığında veya kopyalandığında hala kullanılabilir olması için çözüm veya proje kaynak denetiminde bulunan bir dosyayı kullanın.

3. Bu görünümü başka kullanım örneği diyagramlarında çoğaltmak için aktöri kopyalayın ve başka bir diyagrama yapıştırın.

    - Görüntü değişikliği yalnızca belirli bir diyagramdaki görünüm için geçerlidir. Temel alınan model öğesi için uygulanmaz. Aktöri UML Model Gezgini 'nden başka bir diyagrama sürüklerseniz, Standart çubuk şekli olarak görünür.

### <a name="multiplicities-between-actors-and-use-cases"></a>Aktörler ve kullanım örnekleri arasındaki çeşitlilikler
 Aktör ve kullanım durumu arasındaki ilişki her uçta bir *çoğulluk* gösterebilir.

 ![Aktör ile bire bir kullanın](../modeling/media/uml-ucguidemulti1.png "UML_UCGuideMulti1")

> [!NOTE]
> Kullanım durumu diyagramında bir ilişkinin çarpanlarından ikisi de **1**ise gizlenir.

 Varsayılan olarak, her çeşitlilik **1**' dir. Modelin sıkı bir şekilde yorumlanması halinde 1 çokluğu, örneğin yalnızca bir müşterinin her yemeğin sıralanmasında yer aldığı ve her müşterinin tek seferde yalnızca bir yemek siparişi veren anlamına gelir.

 Bu çeşitlilikleri değiştirebilirsiniz.

 Örneğin:

 ![Birçok çokluğa çok çokluğu gösteren kullanım örneği](../modeling/media/uml-ucguidemulti2.png "UML_UCGuideMulti2")

- Aynı sınıfın kaç aktörlerin tek bir kullanım durumunun tek bir yerinde bir parçasını ele geçirmesine olanak sağlamak için, ilişkilendirmenin aktör sonundaki çokluğu **1..\*** olarak ayarlayın.

   Çizimde, bir veya daha fazla restoran aynı yemek siparişini yerine getirmek için bir parçası alabilir.

- Her bir aktörün bir kullanım örneğinin birkaç tekrarışında aynı anda katılacaklarını göstermek için, ilişkinin kullanım örneği sonunda çoğulluğu **\*** olarak ayarlayın.

   Çizimde, her restoran aynı anda birden fazla siparişi yerine getirmek için çalışabilir.

##### <a name="to-set-multiplicities-on-an-association"></a>Bir ilişkilendirmede çeşitlilimleri ayarlamak için

1. İlişkiye sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Birinci rolü** veya **ikinci rolü**genişletin.

    *Rol* , ilişkinin bir sonundaki öğe anlamına gelir.

3. Listeden seçim yaparak çokluk özelliğini ayarlayın:

   - **1** bu rolün tam olarak bir örneğinin her bir bağlantıya katıldığı durum.

   - **1..** bu rolün bir veya daha fazla örneğinin her bir bağlantıya katılmasını sağlamak için\*.

   - **0.. 1** katılımın isteğe bağlı olması durumunda.

   - Bu rolün sıfır veya daha fazla örneğinin bağlantıya katılacağı durumu **\*** .

> [!NOTE]
> Birçok ekip kullanım örneği diyagramlarında çoğullanlarını varsayılan değer olan 1 ' de bırakarak çeşitlilik bilgileri yerleştirmez. Bunun yerine, kullanım örneklerinin ayrı açıklamalarıyla bilgileri sağlarlar. Bu durumda, kullanım durumu diyagramlarındaki tüm çeşitlilimler gizlenir.

### <a name="using-an-actor-or-use-case-on-multiple-diagrams"></a>Birden çok diyagramda aktör veya kullanım örneği kullanma
 Aynı aktörleri ve kullanım örneklerini birkaç diyagramda gösterebilirsiniz. Örneğin:

- Farklı diyagramlarda, tek bir aktörün dahil olduğu farklı kullanım durumları tanımlayabilirsiniz.

- Tek bir diyagramı kullanarak, bir kullanım örneğinin ilişkilendirildiği aktörleri ve alt sistemleri gösterebilir ve kullanım durumunun dahil ve Genişletilmiş kullanım durumlarında nasıl yapılandırıldığını göstermek için başka bir diyagram kullanabilirsiniz.

##### <a name="to-show-the-same-actor-or-use-case-on-different-diagrams"></a>Aynı aktör veya kullanım örneğini farklı diyagramlarda göstermek için

1. Tek bir diyagramda aktör veya kullanım örneğini oluşturun.

2. Başka bir kullanım durumu diyagramı oluşturun.

3. Bir aktör veya **Model Gezgini** 'ni yeni diyagram üzerine sürükleyin.

    > [!NOTE]
    > Yeni diyagrama bir aktör ve zaten ilişkilendirilmiş bir kullanım durumu yerleştirirseniz, bunlar arasındaki ilişki yeni diyagramda otomatik olarak görünür.

## <a name="Details"></a>Kullanım örneklerini ayrıntılı olarak açıklama
 Kullanım örneği şunu temsil eder:

- Bir oyuncu **satın alma**gibi sistemi kullanan bir aktör hedefi; '

- Bir veya daha fazla *senaryo*, diğer bir deyişle, hedefin Peşte gerçekleştirilen adım dizileri, örneğin: {**yemek yiyecek, ödeme, sunma**}. Başarı senaryolarına ek olarak, **kredi kartı reddedildiğinde**birkaç özel durum veya hata senaryosu olabilir.

  Kullanım örneği, farklı ayrıntı düzeylerinde açıklanabilir. Tasarımın erken bir aşamasında, yalnızca kullanım örneği diyagramındaki ad yeterlidir.  Daha sonra senaryoların daha ayrıntılı açıklamaları yazılabilir.

  Visual Studio Ultimate, bir kullanım örneğini ayrı ayrı veya birlikte kullanılabilecek çeşitli yollarla tanımlayabilirsiniz:

- Kullanım durumunu projedeki başka bir diyagrama veya diyagramlara bağlayın.

  - Bir etkinlik diyagramı, döngüler, dallar ve paralel iş parçacıklarının bulunduğu daha karmaşık bir süreci açıklamanıza yardımcı olur. Ayrıca, işlemin parçaları arasındaki veri akışını da gösterebilir. Daha fazla bilgi için bkz. [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).

  - Sıralı diyagram, farklı aktörler arasındaki karmaşık bir etkileşim serisini açıklamanıza yardımcı olur. Ayrıca, her kullanım örneğine yanıt olarak sistem içinde neler olduğunu göstermek için de kullanabilirsiniz. Daha fazla bilgi için bkz. [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).

- Kullanım örneğini, kullanım örneğini ayrıntılı olarak açıklayan bir OneNote sayfasına, bölümüne veya paragrafa bağlayın.

- Kullanım örneğini, kullanım örneği senaryolarını anlatmak için metin, ekran görüntüleri vb. kullandığınız bir Word belgesine bağlayın. Daha fazla bilgi için bkz. [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md).

#### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Bir kullanım durumunu aynı çözümdeki bir diyagrama veya dosyaya bağlamak için

1. Kullanım durumunun bir senaryosunu göstermek için sıralı diyagram veya etkinlik diyagramı gibi bir diyagram çizin.

2. Kullanım durumu diyagramına geri dönün.

3. Çözüm Gezgini diyagramı veya dosyayı kullanım durumu diyagramının boş bir bölümüne sürükleyin.

4. Bir **bağımlılığı**kullanarak yapıtın kullanım örneğine bağlanın.

#### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Word belgesi veya PowerPoint sunusu gibi bir çözüm dosyasına bağlantı sağlamak için

1. Kullanım durumunun senaryosunu betimleyen metin, ekran görüntüsü ve benzeri bir belge yazın.

2. Belgeyi çözüme ekleyin.

    1. Word belgesini çözümle aynı Windows klasörüne taşıyın.

    2. Çözüm Gezgini, çözüme sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **var olan öğe**' ye tıklayın.

    3. Word belgesine gidin ve **Ekle**' ye tıklayın.

         Word belgesi, Çözüm Gezgini bir çözüm klasöründe görüntülenir.

3. Word belgesini Çözüm Gezgini ' den kullanım durumu diyagramının boş bir bölümüne sürükleyin.

     Yeni bir yapıt görüntülenir.

4. Bir **bağımlılığı**kullanarak yapıtın kullanım örneğine bağlanın.

#### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Paylaşılan bir belgeye, OneNote öğesine veya Web sayfasına bağlamak için

1. Paylaşılan öğenin URL 'sini alın. Bu, örneğin, '\\\\' veya bir Web sayfası veya SharePoint URL 'SI ' http://' ile başlayan bir ağ dosyası yolu ya da ' OneNote: ' başlangıcında bir OneNote bölümü, sayfası veya paragrafı bağlantısı olabilir.

2. Araç kutusunda **yapıt** ' ye ve ardından kullanım durumu diyagramında ' a tıklayın.

3. Seçilen yeni yapıt ile URL 'YI yazın veya **köprü** özelliğine yapıştırın.

> [!NOTE]
> Bir yapıya çift tıklayarak, bağlandığı diyagramı veya belgeyi açabilirsiniz.

### <a name="linking-use-cases-to-work-items"></a>Kullanım örneklerini iş öğelerine bağlama
 Projeniz [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)] kullanıyorsa ve [!INCLUDE[esprtfc](../includes/esprtfc-md.md)]sahipseniz, her kullanım örneğini [!INCLUDE[esprfound](../includes/esprfound-md.md)]bir iş öğesine bağlayabilirsiniz. Bu bağlantıları nasıl yapacağınızı öğrenmek için bkz. [bağlantı modeli öğeleri ve iş öğeleri](../modeling/link-model-elements-and-work-items.md).

 Bu şunları yapmanızı sağlar:

- Bağlantılı iş öğesinde kullanım durumunu açıkla. Özellikle, projeniz Visual Studio biçimsel Işlem şablonunu kullanıyorsa, kullanım örneği Iş öğesine bağlayabilirsiniz. Bu iş öğesi türü, kullanım durumunun amaçlarını ve senaryolarını açıklamak için alanlar sağlar.

- Test çalışmalarını kullanım örneğine bağlayın, böylece, geliştirmekte olan kodun ne kadar ilerlediğini kullanım durumunu uygular.

- Geliştirme işinin ilerlemesini izleyebilmek için, görevleri kullanım örneğine bağlayın.

## <a name="Structuring"></a>Kullanım örneklerini yapılandırma
 Yalnızca birkaç önemli kullanım durumu ile sisteminizin davranışını açıklamaya çalışırsınız. Her büyük kullanım örneği, bir aktörün bir ürün satın alma, satıcının görünüm noktasından, satış için ürünler sağlayan bir büyük hedefi tanımlar.

 Bu hedefleri açık hale getirdiğiniz zaman, her hedefin nasıl elde edildiğini ve temel hedeflerdeki Çeşitlemeler hakkında daha fazla ayrıntıya geçebilirsiniz.

 Kullanım durumlarını çok fazla ayrıntılandırmaktan kaçının. Kullanım örnekleri, iç işleyişi yerine, kullanıcıların sistem deneyimiyle ilgilidir. Ayrıca, genellikle kodun erken çalışma sürümlerini oluşturmak daha üretken bir şekilde öğrenirsiniz, bu da kullanım örneklerini ayrıntılı bir şekilde yapılandırmak için zaman harcamayı sağlar.

 Büyük ve daha ayrıntılı kullanım durumları arasındaki ilişkileri kullanım örneği diyagramında özetleyebilirsiniz. Aşağıdaki bölümlerde bu açıklanır:

- [Dahil bir kullanım durumunun ayrıntılarını gösterme](#Include)

- [Genelleştirme ile hedefleri paylaşma](#Inheritance)

- [Genişletme ile değişken durumları ayırma](#Extend)

### <a name="Include"></a>Dahil bir kullanım durumunun ayrıntılarını gösterme
 Bir kullanım durumunun başka bir ayrıntıyı açıklar olduğunu göstermek için bir **dahil etme** ilişkisi kullanın. Çizimde, **yemek siparişi** **ödeyerek**, **menüyü seçin**ve **menü öğesi**' ni seçin. Dahil edilen ve daha ayrıntılı kullanım örneklerinin her biri, aktör veya aktörlerin, dahil kullanım durumunun genel amacını elde etmek için gerçekleştirmesi gerekebilecek bir adımdır. Ok, daha ayrıntılı, dahil edilen kullanım durumuna işaret etmelidir.

> [!CAUTION]
> Kendisi de dahil olmak üzere kullanım örneğine neden olan ilişkiler dahil etme döngüleri kullanmamalısınız. Döngüler hata oluşturabilir.

 Dahil edilen kullanım örneklerini paylaşabilirsiniz. Örnekte, **yemek siparişi** ve **Incelemeleri incelemeye abone olma** durumları her ikisi de **ödeme**içerir.

 ![İçerme ile oluşan kullanım örnekleri](../modeling/media/uml-ucguideinclude.png "UML_UCGuideInclude")

 Dahil edilen kullanım durumunun hedefi ve senaryoları, daha sonra tasarlanan kullanım örneklerine dahil edilmesini sağlamak için bağımsız olarak anlamlı hale gelmelidir.

 Kullanım durumlarını dahil etme ve dahil edilen bölümleri ayırma, aşağıdaki hedeflere ulaşmak için yararlıdır:

- Kullanım örneği tanımlarınızı farklı ayrıntı katmanlarında yapısal hale ekleyin.

- Farklı kullanım durumlarında paylaşılan senaryolarınızı tekrarlamadan kaçının.

#### <a name="Steps"></a>Ayrıntılı adımların sırasını tanımlama
 Kullanım durumu diyagramı, daha ayrıntılı adımların gerçekleştirilmesi gereken sıra veya her birinin her zaman gerekli olup olmadığı hakkında hiçbir şey söylemez.

 Adımların sırasını açık hale getirmek için, dahil olan kullanım örneğine ayrı bir belge iliştirmek üzere bir **yapıtı** kullanabilirsiniz. Aşağıdaki örnekte, bir yiyecek kullanım örneğine iliştirilmiş bir etkinlik diyagramı. Alternatif olarak, bir adım listesi veya ekran görüntüsü sırası içeren bir metin belgesi kullanabilirsiniz. Daha fazla bilgi için bkz. [kullanım örneklerini ayrıntılı olarak açıklama](#Details).

 Bir etkinlik diyagramı kullandığınızda bu adlandırma kurallarına dikkat edin:

- Tüm etkinliğin adı, dahil olan kullanım durumuyla aynıdır.

- Etkinlik diyagramındaki eylemler, dahil edilen kullanım durumları ile aynı adlara sahiptir.

  Daha fazla bilgi için bkz. [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).

  ![Bağlantılı etkinlik diyagramında gösterilen kullanım örneği adımları](../modeling/media/uml-ucguidesteps.png "UML_UCGuideSteps")

### <a name="Inheritance"></a>Genelleştirme ile hedefleri paylaşma
 *Özel* kullanım durumunun, başka bir *genel* kullanım örneği tarafından ifade edilen hedeflere ulaşmak için belirli bir yol olduğunu göstermek için bir Genelleştirme ilişkisi kullanın. Açık ok ucu, daha genel kullanım durumuna işaret etmelidir.

 ![Genelleştirme ilişkisini gösteren kullanım örnekleri](../modeling/media/uml-ucguidegeneral.png "UML_UCGuideGeneral")

 Örneğin **ödeme** , **kredi kartıyla öde** ve **nakit olarak**ödeme yapar.

> [!CAUTION]
> Bir aktörün kendisini genelleştirerek Genelleştirme ilişkilerinin döngülerini yapmamalıdır. Döngüler hata oluşturabilir.

 Özelleştirilmiş kullanım örnekleri, sisteminizin aynı hedefe ulaşabilmesinin farklı yollarını göstermenizin sağlanmasına yardımcı olabilir.

 Özelleştirilmiş kullanım örnekleri, genel kullanım durumunun hedeflerini ve aktörlerini devralacak şekilde değerlendirilir. Genel kullanım durumunun kendi senaryoları olması gerekmez; uzmanlık, hedefleri elde etmenin farklı yollarını anlatmaktadır.

##### <a name="to-refactor-common-goals-from-two-or-more-use-cases"></a>İki veya daha fazla kullanım durumundan ortak hedefleri yeniden düzenleme

1. Yeni genel kullanım durumunu oluşturun ve adlandırın.

2. Yeni genel kullanım örneğine işaret eden büyük oklu bir **Genelleştirme** ilişkisi oluşturun.

    1. Araç kutusunda **Genelleştirme** ' ye tıklayın.

    2. Özelleştirilmiş kullanım örneğine tıklayın (örnekteki**kredi kartına göre öde** ).

    3. Genel kullanım örneğine tıklayın (örnekte**ödeme** yapın).

3. Özelleştirilmiş kullanım örneklerinin hedeflerini açıkladıysanız, ortak bölümleri genel kullanım durumunun açıklamasına taşıyın.

4. Özelleştirilmiş kullanım örnekleri arasında paylaşılan aktörler genel kullanım örneğine taşınabilir.

### <a name="Extend"></a>Değişken durumları genişletme ile ayırma
 Bir kullanım durumunun belirli koşullar altında başka bir kullanım örneğine işlevsellik ekleyeolabileceğini göstermek için genişletme bağlantısını kullanın. Ok, ana, Genişletilmiş kullanım örneğine işaret etmelidir.

 ![Bir kullanım örneği başka bir genişletme](../modeling/media/uml-ucguideextend.png "UML_UCGuideExtend")

> [!CAUTION]
> Genişletmenin kendisini genelleştirmeye neden olan, genişletme ilişkilerinin döngülerini yapmamalıdır. Döngüler hata oluşturabilir.

 Örneğin, tipik bir Web sitesinin **oturum açma** kullanım durumu, **Yeni Kullanıcı Kaydet** ' i (yalnızca kullanıcının hesabı yoksa) içerebilir.

##### <a name="to-separate-a-use-case-into-main-and-extending-parts"></a>Bir kullanım durumunu ana ve genişletme bölümlerine ayırmak için

1. Yeni uzantı kullanım durumunu oluşturun ve adlandırın.

2. Genişletilmiş kullanım örneğine işaret eden oklu bir **uzatma** ilişkisi oluşturun.

   1. Araç kutusunda **Genişlet** ' e tıklayın.

   2. Genişletme kullanım örneğine tıklayın (örnekteki**Yeni Kullanıcı Kaydet** ).

   3. Genişletilmiş kullanım örneğine tıklayın (örnekteki**oturum açın** ).

       > [!NOTE]
       > Diyagramda bir genişletilmiş ilişki döngüsü oluşturmaktan kaçının. Bir kullanım durumunun kendisinin uzantısı olması yanlıştır.

3. Genişletilmiş kullanım durumu için zaten senaryolar oluşturduysanız ilgili adımları uzantının senaryosuna taşıyın.

4. Uzantının açıklaması (örnekteki**yeni kullanıcıyı kaydet** ), ana kullanım örneği senaryolarında nerede gerçekleşeceğini ve hangi koşullarda yapılacağını içermelidir. Bunu, ana örneğin açıklamasını değiştirme olarak düşünün.

   Uzantı kullanım örneği, aksi takdirde ana kullanım örneğinin senaryolarının bir parçası olacak senaryo adımlarını temsil eder. Uzantının senaryosu ve hedefi, ana kullanım durumu bağlamında her zaman okunacaktır, bu nedenle bağımsız olarak yararlı olmaları gerekmez.

   Uzantıları ayırmak, bu durumları anlatmak için yararlı olabilir:

- Yalnızca uzantı kullanım durumunda olan ek aktörler vardır. Örneğin, bir yöneticinin Web sitesinde bir müşterinin kaydını onaylaması gerekir.

- Ayrı bir alt sistem, uzantı kullanım durumuyla ilgilenir.

- Bu uzantı yalnızca sistemin belirli sürümlerinde kullanılabilir olacaktır. Kullanım durumu diyagramında her sürümü ayrı bir alt sistem olarak gösterebilirsiniz.

## <a name="Subsystems"></a>Alt sistem sınırlarını kullanma
 Sisteminizin kapsamındaki kullanım örneklerinin ne olduğunu göstermek için bir alt sistem sınırı kullanın.

#### <a name="to-draw-a-subsystem-boundary"></a>Alt sistem sınırı çizmek için

1. Araç kutusunda **alt sistem**' e ve ardından diyagrama tıklayın.

    Diyagramda bir alt sistem görüntülenir.

2. Boyutunu ayarlamak için alt sistemin köşelerini sürükleyin.

3. İçeriğini ayarlamak için mevcut kullanım çalışmalarını alt sistem içine veya dışına sürükleyin.

   \- veya-

   Doğrudan bir alt sistemde yeni bir kullanım durumu oluşturmak için, araç kutusunda **kullanım örneği** ' ne tıklayın ve ardından alt sistem içine tıklayın.

> [!NOTE]
> Kullanım durumunun **konular** özelliği, içinde bulunduğu alt sistemi gösterir.

### <a name="use-cases-outside-the-system-scope"></a>Sistem kapsamı dışındaki kullanım durumları
 İş parçası olan ancak geliştirmekte olduğunuz sistem tarafından ele verilmeyen diyagram kullanım örneklerine dahil etmek sık sık yararlıdır. Bu, geliştiricilerin çalışma bağlamını anlamalarına yardımcı olur. Örneğin, yemek sunma, aktörlerin ve müşterinin, ancak yemek siparişi Web sitesinin sorumluluğunun dışında bir kullanım durumu olarak görüntülenebilir.

### <a name="multiple-subsystems"></a>Birden çok alt sistemi
 Farklı kullanım örneklerinin sistemin farklı bileşenleriyle nasıl ele alınacağını göstermek için çeşitli alt sistem sınırları oluşturabilirsiniz. Örneğin, **restoran değerlendirmesi ekleyerek** ayrı bir Forum Web sitesinde ele alınabilir. Kullanım durumu diyagramının Kullanıcı tarafından görülüp uğraşması gerektiğini unutmayın. Sistemde iş bölümünün iç bölümünü belirtmek isterseniz, bir bileşen diyagramı kullanmayı düşünün.

### <a name="system-versions"></a>Sistem sürümleri
 Sistemin farklı sürümlerini göstermek için farklı alt sistem sınırları kullanabilirsiniz. Örneğin, ödeme kullanım durumu Web sitesi sürüm 2 ' ye dahil edilebilir, ancak sürüm 1 ' de yer alabilir. Bu, sistemin siparişlerinin sipariş etmesine yardımcı olması anlamına gelir. Ancak, Restoran 'yı doğrudan ödemeleri gerekir.

 Farklı sürümleri ve çeşitleri temsil eden alt sistemleri bağlamak için **bağımlılık** ilişkilerini kullanın.

 ![Alt sistemler bir sistemin farklı sürümlerini gösterir](../modeling/media/uml-ucguidesystem.png "UML_UCGuideSystem")

## <a name="see-also"></a>Ayrıca Bkz.
 [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md) [UML sıralı DIYAGRAMLARı: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md) [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md) [UML Kullanım örneği diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md) [UML sınıf diyagramları](../modeling/uml-class-diagrams-reference.md) : başvuru UML [Bileşen diyagramları](../modeling/uml-component-diagrams-reference.md) : başvuru UML [etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md) [video: özellikleri kullanım örneklerine düzenleme](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-2-organizing-features-into-use-cases)
