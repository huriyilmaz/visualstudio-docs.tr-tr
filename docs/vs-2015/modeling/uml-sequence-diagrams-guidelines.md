---
title: 'UML sıralı diyagramlar: yönergeler | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cdd853307bdea28c48762a6a3f0416e698b577ff
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850132"
---
# <a name="uml-sequence-diagrams-guidelines"></a>UML Sıralı Diyagramlar: Yönergeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da bir etkileşimi göstermek için bir *sıra diyagramı* çizebilirsiniz. Etkileşim, sınıfların, bileşenlerin, alt sistemlerin veya aktörlerin tipik örnekleri arasındaki bir ileti dizisidir.

 UML sıralı diyagramları bir UML modelinin parçasıdır ve yalnızca UML modelleme projeleri içinde mevcuttur. UML sıralı diyagramı oluşturmak için **mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın. [UML sıralı diyagram öğeleri](../modeling/uml-sequence-diagrams-reference.md) veya genel olarak [UML modelleme diyagramları](../modeling/edit-uml-models-and-diagrams.md) hakkında daha fazla bilgi edinin. Video gösterimi için bkz. [sıralı diyagramlar (2010) kullanarak](https://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams)taslağı oluşturma etkileşimleri.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>Bu konuda
 [UML sıralı diyagramlarını kullanma](#Using)

 [Çizim sırası diyagramları için temel adımlar](#BasicSteps)

 [Basit sıralı diyagramlar oluşturma ve kullanma](#Simple)

 [Sınıflar ve yaşam çizgileri](#ClassesAndLifelines)

 [Yeniden kullanılabilir etkileşim sıraları oluşturma](#Multiple)

 [Yaşam çizgileri gruplarını daraltma](#Collapse)

 [Denetim yapılarını parçalar ile açıklama](#Fragments)

## <a name="Using"></a>UML sıralı diyagramlarını kullanma
 Farklı program ayrıntısı düzeylerinde çeşitli amaçlar için sıralı diyagramlar kullanabilirsiniz. Sıralı diyagram çizmek için tipik durumlar aşağıdaki gibidir:

- Sisteminizin kullanıcılarını ve amaçlarını özetleyen bir kullanım örneği diyagramınız varsa, sistemin ana bileşenlerinin her kullanım örneğinin hedefini yerine getirmek için nasıl etkileşime gireceğini betimleyen sıralı diyagramlar çizebilirsiniz. Daha fazla bilgi için bkz. [UML Kullanım örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).

- Bir bileşenin arabirimine ulaşan iletileri belirlediyseniz, bileşenin iç bölümlerinin her gelen ileti için gereken sonuca ulaşmak üzere nasıl etkileşime gireceğini betimleyen sıralı diyagramlar çizebilirsiniz. Daha fazla bilgi için bkz. [UML Bileşen diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md).

  Çizim sırası diyagramlarında birçok avantaj vardır:

- Görevlerin bileşenler arasında nasıl dağıtıldığını kolayca görebilirsiniz.

- Yazılımın güncelleştirilmesini zorlaştıran etkileşim düzenlerini tanımlayabilirsiniz.

## <a name="relationship-to-other-diagrams"></a>Diğer diyagramlarla ilişki
 UML sıralı diyagramlarını, Diğer diyagramlarla birlikte çeşitli yollarla kullanabilirsiniz.

#### <a name="lifelines-and-types"></a>Yaşam çizgileri ve türleri
 Sıralı diyagramda çizdiğiniz yaşam çizgileri, sisteminizdeki bileşenlerin veya sınıfların tipik örneklerini temsil edebilir. Türlerden yaşam çizgilerini ve yaşam çizgilerinden türleri oluşturabilir ve UML sınıf diyagramlarında ve UML bileşen diyagramlarında türleri gösterebilirsiniz. Daha fazla bilgi için bkz. [sınıflar ve yaşam çizgileri](#ClassesAndLifelines).

#### <a name="parameter-types"></a>Parametre türleri
 UML sınıf diyagramında parametre türlerini ve yaşam çizgileri arasında gönderilen iletilerde kullanılan döndürülen değerleri de tanımlayabilirsiniz.

#### <a name="use-case-details"></a>Kullanım örneği ayrıntıları
 Kullanım durumu, bir kullanıcının hedefini, hedefi elde etmek için bir adım dizisiyle birlikte temsil eder. Adımların sırası çeşitli yollarla açıklanabilir. Bir seçenek, kullanıcılar ve sistemin ana bileşenleri arasındaki etkileşimleri gösteren bir sıra diyagramı çizmektir. Daha fazla bilgi için bkz. [UML Kullanım örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Çizim sırası diyagramları için temel adımlar
 Sıralı diyagramlarda öğelerin tüm listesi için bkz. [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md).

> [!NOTE]
> Modelleme diyagramlarından herhangi birini oluşturma hakkında ayrıntılı adımlar [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md)bölümünde açıklanmıştır.

#### <a name="to-create-a-sequence-diagram"></a>Sıralı diyagram oluşturmak için

1. **Mimari** menüsünde **Yeni UML veya katman diyagramı**' na tıklayın.

2. **Şablonlar**altında **UML sıralı diyagramı**' na tıklayın.

3. Diyagrama ad verin.

4. **Modelleme projesine ekle**' de, çözümünüzde mevcut bir modelleme projesi seçin veya **Yeni bir modelleme projesi oluşturun**ve ardından **Tamam**' a tıklayın.

    **Sıralı diyagram** araç kutusu ile yeni bir sıra diyagramı görüntülenir. Araç kutusu gereken öğeleri ve bağlayıcıları içerir.

   ![Sıralı diyagramın parçaları](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>Sıralı diyagram çizmek için

1. Sınıf, bileşen, aktör veya cihaz örneklerini göstermek için **araç** çubuğundan **yaşam çizgilerini** (1) diyagram üzerine sürükleyin.

    > [!NOTE]
    > Ayrıca, varolan bir sınıf, arabirim, aktör veya bileşeni **UML Model Gezgini** 'nden diyagram üzerine sürükleyerek bir yaşam çizgisi oluşturabilirsiniz. Bu, seçilen türün bir örneğini temsil eden bir yaşam çizgisi oluşturur.

2. Yaşam çizgilerinin belirli bir amaca ulaşmak için nasıl işbirliği kullandığını gösteren iletiler çizin.

     Bir ileti oluşturmak için (3, 4, 6, 7) bir ileti aracına tıklayın. Sonra iletinin başlamasını istediğiniz noktada gönderme yaşam çizgisine tıklayın ve sonra alma yaşam çizgisine tıklayın.

     Alıcı yaşam çizgisinde bir yürütme oluşumu (5) görünür. Yürütme oluşumu, örneğin bir yöntemi yürüten bir süreyi temsil eder. Bir yürütme örneğinden başlayan diğer iletileri oluşturabilirsiniz.

3. Bilinmeyen bir olay kaynağından (9) veya bilinmeyen alıcılara yayınlar (10) gelen bir iletiyi göstermek için, diyagramda veya boş alana bir zaman uyumsuz ileti çizin. Bu iletiler *bulunan iletiler* (9) ve *kayıp iletiler* (10) olarak adlandırılır.

    > [!NOTE]
    > Kayıp veya bulunan iletileri olan bir yaşam çizgisi grubunu taşımak için, bunları taşımadan önce yaşam çizgilerini seçmek üzere aşağıdaki adımları izleyin: Bu yaşam çizgilerinin çevresine bir dikdörtgen çizin veya her bir yaşam çizgisine tıkladığınızda **CTRL** tuşunu basılı tutun. Tüm yaşam çizgilerini **seçmek Için** **Tümünü seç** veya **CTRL**+' i kullanırsanız ve sonra bunları taşırsanız, bu yaşam çizgilerine eklenen kayıp veya bulunan iletiler hareket etmez. Bu senaryo ortaya çıkarsa, bu iletileri ayrı olarak taşıyabilirsiniz.

4. Aynı bileşene veya sisteme her bir ana ileti için sıralı diyagramlar çizin.

#### <a name="to-change-the-order-of-messages"></a>İleti sırasını değiştirmek için

- Bir iletiyi yaşam çizgisinde yukarı veya aşağı sürükleyin. Başka iletilerin üzerine veya bir yürütme bloğunun içine veya dışına sürükleyebilirsiniz.

     \- veya -

- İleti konumlarını ayarlamak için iletiye tıklayın ve **yukarı ok** ve **aşağı ok** tuşlarını kullanın. İletilerin sırasını değiştirmek için **SHIFT + yukarı ok** ve **SHIFT + aşağı ok** tuşlarını kullanın.

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Sıralı diyagramda ileti dizilerini taşımak veya kopyalamak için

1. Bir iletiye (3, 4) sağ tıklayın ve ardından **Kopyala**' ya tıklayın.

2. Yürütme oluşumuna (5) veya yeni iletinin gönderilmesini istediğiniz yaşam çizgisine (1) sağ tıklayın ve ardından **Yapıştır**' a tıklayın. İsterseniz yeni Gönderici farklı bir diyagram üzerinde olabilir.

     İletinin bir kopyası ve tüm yan kendi iletileri yürütme oluşumunun sonuna veya yaşam çizgisinin sonuna eklenir.

    > [!NOTE]
    > Yapıştırılan ileti her zaman yürütme oluşumunun veya yaşam çizgisinin sonunda görüntülenir. Yapıştırdıktan sonra, daha önceki bir konuma sürükleyebilirsiniz.

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Bir iletinin imza metnini görüntüleme ve düzenleme

- Hedef yaşam çizgisi, imza metninin görünür olması için bağlanmalıdır veya türlerle eşlenmelidir. Bu görevi gerçekleştirmek için aşağıdaki adımlardan birini gerçekleştirin:

  - Yaşam çizgisine sağ tıkladıktan sonra **Sınıf Oluştur**' u seçin.

     veya

  - Yaşam çizgisini seçin, **F4**tuşuna basın ve ardından **Özellikler** penceresinde, **tür** özelliğini varolan bir tür olarak ayarlayın veya yeni bir tür için adı belirtin. İleti etiketine sağ tıklayın ve sonra **Işlem oluştur**' u seçin.

    İmza metni ileti etiketinin altında görünür. Artık imza metnini düzenleyebilirsiniz. Daha fazla bilgi için bkz. [sınıflar ve yaşam çizgileri](#ClassesAndLifelines).

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Sıralı diyagramın yerleşimini geliştirmek için

- Diyagramın boş bir kısmına sağ tıklayın ve sonra **düzeni yeniden Düzenle**' ye tıklayın.

- İşlemi geri almak için, **Düzenle**' ye tıklayın ve ardından **geri al**' a tıklayın.

#### <a name="to-change-the-package-that-owns-the-interaction"></a>Etkileşimin sahibi olan paketi değiştirmek için

1. **UML Model Gezgini**' nde, sıralı diyagramın gösterdiği Etkileşimi bulun.

    > [!NOTE]
    > İlk yaşam çizgisini sıralı diyagrama ekleyene kadar etkileşim **UML Model Gezgini** ' nde görünmez.

2. Etkileşimi pakete sürükleyin.

     \- veya -

     Etkileşime sağ tıklayın ve ardından **Kes**' e tıklayın. Pakete sağ tıklayın ve ardından **Yapıştır**' a tıklayın.

## <a name="Simple"></a>Basit sıralı diyagramlar oluşturma ve kullanma
 En basit ve en yaygın olarak kullanılan sıralı diyagram formu yalnızca yaşam çizgilerini ve iletileri içerir. Bu tür bir diyagram, tasarımınızda nesneler arasındaki ya da sisteminiz ile kullanıcıları arasında tipik bir etkileşim sırasını açıkça göstermenizi sağlar. Bu, tasarımınızı tartışmanıza ve iletmanıza yardımcı olmak için genellikle yeterlidir.

 Basit bir sıra diyagramı çizerken göz önünde bulundurmanız gereken bazı noktalar aşağıda verilmiştir.

### <a name="types-of-message"></a>İleti türleri
 İleti oluşturmak için kullanabileceğiniz üç araç vardır.

- Gönderenin alıcının bir yanıt döndürmesini (3) beklediği bir etkileşimi anlatmak için **zaman uyumlu** aracını kullanın.

     **<\<> >** ok, yürütme oluşumunun sonunda gösterilir. Bu, denetimin göndericiye dönmesini gösterir.

- Gönderenin alıcıyı beklemeden hemen devam edebildiği bir etkileşimi anlatmak için **zaman uyumsuz** aracı kullanın (4).

- Gönderenin alıcıyı (8) oluşturduğu bir etkileşimi anlatmak için **Oluştur** aracını kullanın.

     Bir oluşturma iletisi, alıcının aldığı ilk ileti olmalıdır.

### <a name="annotating-the-interactions"></a>Etkileşimleri açıklama ekleme
 Sıra hakkında daha fazla ayrıntı için, diyagram üzerinde herhangi bir yere bir **Açıklama** yerleştirebilirsiniz.

 **Açıklama bağlantılarını**kullanarak bir yorumu yaşam çizgileri, yürütmeler, etkileşim kullanımları ve parçalara bağlayabilirsiniz.

> [!CAUTION]
> Dizideki belirli bir noktaya bir açıklama iliştirmek istediğinizde, bir yürütme oluşumuna, etkileşim kullanımına veya parçaya bağlayın. Bir yaşam çizgisine bağlamayın, bu durumda dizideki doğru noktada bağlı kalmaz.

 Şu şekilde bir açıklama kullanın:

- Dizideki anahtar noktalarında ne elde edildiğini aklınızda edin. Bu, okuyucuların etkileşimlerin amaçlarını görmesini sağlar.

- Tüm sıranın genel hedefini açıkla. Yorumu ilk yürütme oluşumuna ekleyin veya eklenmemiş olarak bırakın. Örneğin, "müşteri, menüden öğe seçti ve bir fiyat verdi."

- Her bir yaşam çizgisinin sorumluluklarını açıkla. Yorumu yaşam çizgisine iliştirin. Örneğin, "sıralama Yöneticisi müşterinin menü seçimlerini toplar."

- Gösterilen tipik sıra için alternatif olarak gerçekleştirilebilecek özel durumları veya alternatifleri göz önünde bulabilirsiniz. Örneğin, "müşteri bu sıranın geri kalanını atlamak için seçim yapabilir."

  - Parçaları bu tür bir nota daha resmi bir alternatif olarak kullanmayı düşünün. Bkz. [parçaların bulunduğu denetim yapılarını açıklama](#Fragments)

## <a name="deciding-the-scope-of-the-diagram"></a>Diyagram kapsamına karar verme
 Diyagramın neyi göstermek için düşünülmesinin net olması önemlidir.

#### <a name="initiating-event"></a>Olay başlatılıyor
 Her diyagramda, bir Başlatan olaydan kaynaklanan etkileşimlerin sırası gösterilmelidir. Bu durum, örneğin:

- Örneğin, bir yemek satın alma için Web sayfasını açan bir kullanım örneğini başlatan kullanıcı.

- Bir sistem bileşeninden diğerine ileti, örneğin bir müşterinin satın almak istediği öğelerin kullanılabilirliğini sorgulama.

- Durum değişikliği tarafından tetiklenen bir olay, örneğin bir öğenin hisse senedi eşiğin altına düşme.

#### <a name="level-of-detail"></a>Ayrıntı düzeyi
 Sıralı diyagramlar farklı ayrıntı düzeyleri gösterebilir. Ayrıntı düzeyine neredeyse bağımsız olarak iki ayrı boyutta karar verebilirsiniz:

 Yaşam çizgileri bu ayrıntı düzeylerinden birini temsil edebilir:

- Program kodundaki, varsa veya geliştirdiğiniz nesneler.

- Bileşenler veya alt bileşenleri, genellikle Facades, proxy 'ler ve diğer yönetim mekanizmalarını hariç olur.

- Sisteminiz ve dış aktörler

  İletiler bu ayrıntı düzeylerinden birini temsil edebilir:

- Program kodundaki, bir API veya Web arabirimindeki yazılım iletileri.

- İşlemler veya alt işlemler (örneğin, kullanıcılar ve sistem arasında veya kod ile veritabanı arasında).

- Kullanım durumları-kullanıcılar ve sistem arasındaki önemli etkileşimler.

  Mevcut kodu keşfederken ya da yeni bir tasarımı açıklayadığınız durumlarda, daha az ayrıntılı görünümleri çizmek ve tartışmak genellikle yararlı olur.

## <a name="describing-variations"></a>Çeşitlemeleri açıklama
 Diyagramda tek ve tipik bir olay dizisi gösterilmektedir. Hata senaryoları gibi alternatif olanaklar göstermek istiyorsanız, şu seçeneklerden birini kullanabilirsiniz:

- Bu senaryoları anlatmak için ayrı sıralı diyagramlar çizin

- Döngüleri, alternatifleri ve benzerlerini göstermek için, [parçalarla denetim yapılarını açıklama](#Fragments) kullanın.

## <a name="assessing-the-design"></a>Tasarım değerlendiriliyor
 Diyagram, nesneleri veya bileşenleri arasında görevlerin dağıtımını değerlendirmek için kullanabilirsiniz. Bu desenleri görürseniz yeniden düzenlemeyi düşünün:

- Tek bir yaşam çizgisi her şeyi yapar, başka her şeye çağrı yapar, ancak diğer yaşam çizgileri de yoğun bir şekilde yanıt verir.

- Birçok ileti çarpı yaşam çizgileri. Her yaşam çizgisi yalnızca birkaç komşa ileti göndermelidir ve komşular komşuları ile iletişim kurmamalıdır. Genellikle, iletilerin yaşam çizgilerinden yalnızca birkaç yerde olması için yaşam çizgilerini düzenlemek mümkün olmalıdır; Ayrıca, hedef yaşam çizgisi çapraz yaşam çizgilerine sahip iletileri de değiş tokuş etmelidir.

- Bazı yaşam çizgileri birden fazla görev türünü ele geçiriyor gibi görünüyor. Her bir yaşam çizgisinin sorumluluklarını açıklayan ve aldığı her iletiye yanıt olarak yaptığı işi özetleyen bir kısa cümlesini bulmanın kolay olması gerekir.

## <a name="ClassesAndLifelines"></a>Sınıflar ve yaşam çizgileri
 Sıra diyagramlarındaki yaşam çizgileri sınıfların veya bileşen arabirimlerinin örneklerini gösterir. Bir yaşam çizgisine iki şekilde ad verebilirsiniz:

|**Bu amaçla**|**Bu biçimi kullan**|
|--------------------------|-------------------------|
|Bir türün anonim örneği.<br /><br /> Her türden yalnızca bir yaşam çizgisi varsa bunu kullanın.|*'Ta*|
|Bir türün adlandırılmış örneği.<br /><br /> Aynı türde birden fazla örneği içeren bir sıra göstermek istiyorsanız bunu kullanın.|*ObjectName*:*TypeName*|

### <a name="creating-lifelines-from-types"></a>Türlerden yaşam çizgileri oluşturma
 Zaten tanımladığınız sınıflardan, örneğin bir sınıf diyagramında yeni yaşam çizgileri oluşturabilirsiniz.

> [!NOTE]
> Bu görevi gerçekleştirmeden önce var olan bir sıralama diyagramına sahip olduğunuzdan emin olun.

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Varolan bir türden yaşam çizgisi oluşturmak için

- UML Model Gezgini 'nden bir sınıf, bileşen veya arabirimi sıralı diyagram üzerine sürükleyin.

   \- veya -

  1. İlgili diyagramda sınıf, bileşen veya arabirime sağ tıklayın ve ardından **yaşam çizgisi oluştur**' a tıklayın.

  2. **Yaşam çizgisi oluştur** iletişim kutusunda bir sıra diyagramı seçin ve ardından **Tamam**' a tıklayın.

     Yeni bir adlandırılmış örnek yaşam çizgisi, türü sürüklediğiniz tür olan olarak görüntülenir.

  > [!NOTE]
  > Bu eylemi dilediğiniz sayıda tekrarlayabilirsiniz. Bu işlem, farklı örnek adlarıyla yaşam çizgileri oluşturur.

##### <a name="to-change-the-type-of-a-lifeline"></a>Bir yaşam çizgisinin türünü değiştirmek için

1. Bir yaşam çizgisine sağ tıklayın ve ardından **Özellikler**' e tıklayın.

2. **Özellikler** penceresinde, **tür** özelliğini ayarlayın. Açılır menüden bir tür seçebilir veya yeni bir ad yazabilirsiniz.

### <a name="creating-classes-from-lifelines"></a>Yaşam çizgilerinden sınıflar oluşturma
 Bir veya daha fazla sıralı diyagram oluşturduğunuzda, onlardan sınıflar veya arabirimler oluşturarak yaşam çizgilerini özetleyebilirsiniz.

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Yaşam çizgisinden bir sınıf veya arabirim oluşturmak için

1. Yaşam çizgisine sağ tıklayın ve ardından **Sınıf Oluştur** veya **Arabirim Oluştur**' a tıklayın.

     UML Model Gezgini 'nde yeni bir sınıf veya arabirim görüntülenir.

2. Yaşam çizgisinin aldığı her ileti için sınıfta veya arabirimde işlemler oluşturun:

    1. Dahil etmek istediğiniz tüm iletileri seçin.

    2. İletilerden birine sağ tıklayın ve ardından **Yöntem Oluştur**' a tıklayın.

         Yeni sınıf veya arabirimde seçili her ileti için işlemler vardır.

         İşlem adı her ileti okunun altında ve iletinin **Operation** özelliğinde görüntülenir.

         İletiniz "(parametre: tür)" biçiminde parametreler içeriyorsa, bu, yeni işlemin parametre listesinde görünür.

        > [!NOTE]
        > Sıralı diyagramda yeni iletiler eklerseniz bu adımı tekrarlamalısınız.

3. Yeni sınıfı veya arabirimi ayrıntılı olarak görüntülemek için bir sınıfa veya bileşen diyagramına ekleyin.

    1. Bir sınıf veya bileşen diyagramı açın veya oluşturun.

    2. Yeni sınıfı veya arabirimi **UML Model Gezgini** 'nden sınıf diyagramına sürükleyin.

         Sınıf veya arabirim sınıf diyagramında görüntülenir.

         \- veya -

    3. Yeni arabirimi **UML Model Gezgini** ' nden bileşen diyagramında bir bileşene veya bağlantı noktasına sürükleyin.

         Arabirim, bileşende lolipop olarak görünür.

### <a name="creating-classes-for-parameters"></a>Parametreler için sınıflar oluşturma
 İletilere bir sıralı diyagramda parametreler ekleyebilirsiniz. Parametre türlerini anlatmak için UML sınıf diyagramı kullanabilirsiniz.

## <a name="Multiple"></a>Yeniden kullanılabilir etkileşim sıraları oluşturma
 Ayırmak istediğiniz ayrıntı içeren bir diziyi veya çeşitli diyagramlar arasında ortak olan bir sırayı betimleyen ayrı bir diyagram kullanabilirsiniz.

 Bir diyagramda, başka bir diyagramdaki ayrıntılara işaret eden bir etkileşim kullanım dikdörtgeni (12) oluşturabilirsiniz.

 Bir etkileşim kullanımına çift tıklayarak onunla bağlantılı sıralı diyagramı açın.

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Mevcut yaşam çizgilerinden yeniden kullanılabilir bir etkileşim sırası oluşturmak için

1. **Araç kutusunda** **etkileşim kullanımı**' na tıklayın.

2. Sıralı diyagramda, yeniden kullanılabilir diziye dahil etmek istediğiniz yaşam çizgileri arasında sürükleme yaparken fare düğmesini aşağı basılı tutun. Etkileşim kullanımını eklemek istediğiniz dikey konumdan başlayın.

     Bir etkileşim kullanımı, Sıralı diyagramdaki seçili yaşam çizgileri arasında görüntülenir.

3. Etkileşim kullanımıyla ilgili ada çift tıklayın ve bu diyagramda yeniden kullanılabilir sıranın etkisini tanımlayacak şekilde yeniden adlandırın.

     \- veya -

     Parametresi ile bir işlev çağrısı gibi bir ad yazın.

4. Etkileşim kullanımını başka bir sıra diyagramına bağlayın. Etkileşim kullanımına sağ tıklayın ve sonra şunlardan birini yapın:

     Yeni sıralı diyagram oluşturmak için **yeni dizi oluştur** 'a tıklayın

     \- veya -

     Var olan bir diyagrama bağlamak için **sıralama bağlantısı** ' na tıklayın.

     Visual Studio, etkileşim kullanımı ve yeni etkileşim sırası arasında bir bağlantı oluşturur.

     Çözümünüzde yeni bir sıralı diyagram görüntülenir. Etkileşim kullanımını oluşturmak için kullandığınız yaşam çizgilerini içerir.

    > [!NOTE]
    > Yalnızca etkileşim kullanımı oluşturmak için kullandığınız yaşam çizgileri dahil edilir. Yeni Diyagram, etkileşim kullanımı artık bunları kapsasa bile, etkileşim kullanımı sonrasında oluşturduğunuz yaşam çizgilerini içermez.

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Varolan iletilerden yeniden kullanılabilir bir sıra oluşturmak için

- Taşımak istediğiniz iletiye sağ tıklayın ve sonra **diyagrama taşı**' ya tıklayın.

  Visual Studio:

  - Bir etkileşim ile değiştirir Seçili iletiyi ve tüm yan iletileri kullanır.

  - Değiştirilmiş iletileri yeni bir sıralı diyagrama taşıdır.

  - Etkileşim kullanımı ve yeni sıra diyagramı arasında bir bağlantı oluşturur.

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Bir etkileşim kullanımı tarafından başvurulan sıraya gitmek için

- Etkileşim kullanımına çift tıklayın.

     \- veya -

     Etkileşim kullanımına sağ tıklayın ve ardından **Diziye Git ' e**tıklayın.

### <a name="creating-a-placeholder-with-an-interaction-use"></a>Etkileşim kullanımı ile yer tutucu oluşturma
 Bir etkileşim kullanımını başka bir diyagrama bağlamadan oluşturabilirsiniz. Bu, ayrıntıları henüz çalışılmakta olan dizinin bir parçası için bir yer tutucu olarak kullanabilirsiniz. İstediğiniz sonucu belirtmek için etkileşim kullanımı adını kullanın.

## <a name="Collapse"></a>Yaşam çizgileri gruplarını daraltma
 Bir yaşam çizgisi kümesini birlikte daraltabilir, böylece grup bir yaşam çizgisi olarak görünür. Bu, bir nesne grubunu tek bir bileşen olarak görselleştirmenize yardımcı olur. Daraltılmış bir gruptaki yaşam çizgileri arasındaki iletiler ve etkileşim kullanımları gizlidir. Diğer yaşam çizgilerini içeren iletiler ve etkileşim sıraları gösterilir.

#### <a name="to-collapse-a-group-of-lifelines-together"></a>Bir yaşam çizgisi grubunu birlikte daraltmak için

1. İki veya daha fazla yaşam çizgisi seçin.

2. Bunlardan birine sağ tıklayın ve ardından **Daralt**' a tıklayın.

     Ayrı yaşam çizgileri tek bir yaşam çizgisine göre değişir.

     Yalnızca Grup üyelerini içeren iletiler ve etkileşim kullanımları gizlenir.

3. Grubu yeniden adlandırmak için ada tıklayın.

    > [!NOTE]
    > Grubu genişlettiğinizde grup adı kaybedilir.

#### <a name="to-expand-a-collapsed-group"></a>Daraltılmış bir grubu genişletmek için

- Daraltılan yaşam çizgisine sağ tıklayıp **Genişlet**' e tıklayın.

    > [!NOTE]
    > Grubun adı, gruptaki tüm bağlantılarla birlikte yorumlara veya iş öğelerine kaybolacaktır.

## <a name="Fragments"></a>Denetim yapılarını parçalar ile açıklama
 Birleşik parçaları (13) kullanarak bir sıralı diyagramda döngüleri, dalları ve eşzamanlı işlemeyi tanımlayabilirsiniz. Alternatif olarak, bunun yerine bir etkinlik diyagramı kullanmayı düşünün. Etkinlik diyagramı, aktörler arasındaki iletileri göstermek için yararlı değildir, ancak bazı durumlarda döngüler, dallar ve eşzamanlılık gösterme konusunda daha iyi bir seçenektir.

 Parça türlerinin tam listesi için bkz. [UML sıralı diyagramlarında parçaların bulunduğu denetim akışını açıklama](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).

#### <a name="to-create-a-combined-fragment"></a>Birleşik bir parça oluşturmak için

1. Aynı yürütme oluşumunda veya yaşam çizgisinden başlayarak bir ileti veya bir dizi ileti seçin.

    > [!NOTE]
    > İletilerin işaret eden yürütme tekrarlarından değil, ileti oklarını seçin.

2. İletilerden birine sağ tıklayın, şununla **çevreye**gelin ve ardından ihtiyacınız olan parça türüne tıklayın.

     Yeni bir parça belirir. Seçtiğiniz iletileri içerir.

     Birleşik parça türü birden çok parçaya izin veriyorsa boş bir parça da görünür.

3. Bir parçanın korumasını ayarlamak için parça kenarlığını sağ tıklatın ve ardından **Özellikler**' i tıklatın. **Guard** özelliğini ayarlayın.

     Koruyucu, bir dalın veya bir döngünün koşulunu tanımlamak için kullanılır.

4. Birden çok parçaya izin veren bir türe yeni bir parça eklemek için bir parçanın sınırına sağ tıklayın ve **Ekle**' ye gelin. Sonrasında ya da **etkileşim Işleneninden** **önce etkileşim işleneni** ' ne tıklayın.

5. Bir parçaya yeni iletiler eklemek için ileti araçlarını kullanın veya kopyalayıp yapıştırın.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML sıralı diyagramlar: başvuru](../modeling/uml-sequence-diagrams-reference.md) [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md) [UML Kullanım örneği diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md) [UML sınıf diyagramları](../modeling/uml-class-diagrams-reference.md) : başvuru [UML Bileşen diyagramları](../modeling/uml-component-diagrams-reference.md) : başvuru UML [Bileşen diyagramları](../modeling/uml-component-diagrams-reference.md) : başvuru [video: sıralı diyagramlar kullanılarak taslak etkileşimleri](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases)
