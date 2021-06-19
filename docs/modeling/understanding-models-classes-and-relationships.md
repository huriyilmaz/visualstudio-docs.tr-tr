---
title: Modelleri, Sınıfları ve İlişkileri Anlama
description: Etki alanına özgü bir dilin (DSL) DSL Tanım dosyası tarafından nasıl tanımlandığı ve DSL çözümünde program kodunun büyük bir çoğunun bu dosyadan nasıl oluşturulu olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b086f21b466863c3498ce15c15f7077b358c6d39
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388626"
---
# <a name="understanding-models-classes-and-relationships"></a>Modelleri, Sınıfları ve İlişkileri Anlama
Etki alanına özgü bir dil (DSL), yaz olabileceğiniz özel program koduyla birlikte DSL Tanım dosyası tarafından tanımlanır. DSL çözümünde program kodunun çoğu bu dosyadan oluşturulur.

 Bu konuda DSL tanımının merkezi özellikleri açıklanmıştır.

## <a name="the-dsl-definition"></a>DSL Tanımı
 'i `Dsl\DslDefinition.dsl` Visual Studio pencereniz aşağıdaki resme benzer.

 ![dsl tasarımcısı](../modeling/media/dsl_designer.png)

 DSL Tanımı'nın en önemli bilgileri DSL Tanımı diyagramında görüntülenir. DslDefinition.dsl'nin de bir parçası olan ek bilgiler, genellikle diyagramın tarafında görünen DSL Gezgini'nde görüntülenir. En sık kullanılan görevler için diyagram ve daha gelişmiş özelleştirmeler için DSL Gezgini ile birlikte çalışırsınız.

 DSL Tanımı diyagramı, model öğelerini tanımlayan etki alanı sınıflarını ve model öğeleri arasındaki bağlantıları tanımlayan ilişkileri gösterir. Ayrıca model öğelerini kullanıcıya göstermek için kullanılan şekiller ve bağlayıcılar da gösterilir.

 ![kullana sahip dsl tasarımcısı](../modeling/media/dsl_desinger.png)

 DSL tanımında diyagramda veya DSL Gezgini'nde bir öğeyi seçerek ilgili bilgiler Özellikler penceresi. DSL Ayrıntıları penceresinde ek bilgiler görüntülenebilir.

### <a name="models-are-instances-of-dsls"></a>Modeller, DSL örnekleridir
 *Model,* bir kullanıcı tarafından oluşturulan DSL örneğidir. Model, tanımladığınız etki alanı sınıflarının örnekleri olan model öğelerini ve tanımladığınız etki alanı ilişkilerinin örnekleri olan öğeler arasındaki bağlantıları içerir. Modelde ayrıca diyagramda model öğelerini ve bağlantılarını görüntü alan şekiller ve bağlayıcılar da olabilir. DSL tanımı şekil sınıflarını, bağlayıcı sınıflarını ve diyagram için bir sınıfı içerir.

 DSL Tanımı, etki alanı modeli *olarak da bilinir.* DSL Tanımı veya etki alanı modeli, etki alanına özgü dilin tasarım zamanı gösterimidir, model ise etki alanına özgü dilin çalışma zamanı örneğidir.

## <a name="domain-classes-define-model-elements"></a>Etki Alanı Sınıfları Model Öğelerini Tanımlar
 Etki alanı sınıfları etki alanındaki çeşitli öğeleri oluşturmak için kullanılır ve etki alanı ilişkileri, öğeler arasındaki bağlantılardır. Bunlar, modellerini oluşturduklarında tasarıma özgü dilin kullanıcıları tarafından örneği oluşturulacak öğelerin ve bağlantıların tasarım zamanı gösterimidir.

 Bu çizimde, DSL müzik kitaplığının kullanıcısı tarafından oluşturulmuş bir model gösterilmiştir. Müzik müzikleri, şarkı listelerini içeren kutularla temsil edildi. Ressamlar, yuvarlak köşeli kutularla temsil edilmiştir ve katkıda bulunmak için katkıda bulundukları köşeli kutulara bağlanır.

 ![Oluşturulan DSL'nin örnek modeli](../modeling/media/music_instance.png)

 DSL Tanımı iki yönü birbirinden ayrıdır. Model öğelerinin model diyagramında görünümü, şekil sınıfları ve bağlayıcı sınıfları kullanılarak tanımlanır. Modelde yürütülen bilgiler etki alanı sınıfları ve etki alanı ilişkileri kullanılarak tanımlanır.

 Aşağıdaki çizimde Müzik Kitaplığı'nın DSL Tanımı'nın etki alanı sınıfları ve ilişkileri gösterilmiştir.

 ![Ekleme ve Başvuru ilişkileri](../modeling/media/music_classes.png)

 Çizimde dört etki alanı sınıfı gösterilmiştir: Music, Artist ve Song. Etki alanı sınıfları Ad, Başlık gibi etki alanı özelliklerini tanımlar. Örnek modelinde bu özelliklerden bazılarının değerleri diyagramda görüntülenir.

 Sınıflar arasında etki alanı ilişkileri vardır: MusicHasAlbums, MusicHasArtists, ArtistbHasSongs ve ArtistAppearedOnAlbums. İlişkilerin 1...1, 0..* gibi çoklulıkları vardır. Örneğin, her Şarkı, TamamHasSongs ilişkisi aracılığıyla tam olarak tek bir Müzikle ilgili olması gerekir. Her Every Every'da herhangi bir sayıda Şarkı olabilir.

### <a name="rearranging-the-dsl-definition-diagram"></a>DSL Tanım Diyagramını Yeniden Düzenleme
 Bu resimde olduğu gibi, dsl tanımı diyagramında bir etki alanı sınıfının birkaç kez görünebilirsiniz. Her zaman bir ana görünüm vardır ve bazı başvuru *görünümleri* olabilir.

 DSL Tanımı diyagramını yeniden düzenlemek için şunları yapabilirsiniz:

- Ağacı Buraya Getir ve Ağacı Böl **komutlarını kullanarak ana görünümleri ve** başvuru **görünümlerini** değiştirin. Bu komutları görmek için tek bir etki alanı sınıfına sağ tıklayın.

- Ctrl+Yukarı ve Ctrl+Aşağı tuşlarına basarak etki alanı sınıflarını ve şekil sınıflarını yeniden sırala.

- Her şeklin sağ üst köşesindeki simgeyi kullanarak sınıfları daraltın veya genişletin.

- Bir etki alanı sınıfının en altındaki eksi işaretine (-) tıklayarak ağacın parçalarını daraltın.

## <a name="inheritance"></a>Devralma
 Etki alanı sınıfları devralma kullanılarak tanımlanabilir. Devralma türetme oluşturmak için Devralma aracına tıklayın, türetilmiş sınıfa tıklayın ve ardından temel sınıfa tıklayın. Model öğesi, temel sınıftan devralınan tüm özelliklerle birlikte kendi etki alanı sınıfında tanımlanan tüm özelliklere sahiptir. Ayrıca ilişkilerdeki rollerini devralıyor.

 Devralma İlişkiler, Şekiller ve Bağlayıcılar arasında da kullanılabilir. Devralma aynı grupta kalıtımda kalıtımda kalıtım gerekir. Şekil bir etki alanı sınıfından devralamaz.

## <a name="domain-relationships"></a>Etki Alanı İlişkileri
 Model öğeleri ilişkilerle bağlantılı olabilir. Bağlantılar her zaman ikilidir; tam olarak iki öğeye bağlantı sağlar. Ancak, herhangi bir öğenin diğer nesnelere birçok bağlantısı olabilir ve aynı öğe çifti arasında birden fazla bağlantı bile olabilir.

 Aynı farklı öğe sınıflarını tanımladığınız gibi, farklı bağlantı sınıfları da tanımlayabilirsiniz. Bir bağlantının sınıfına etki alanı *ilişkisi adı ve denir.* Etki alanı ilişkisi, örneklerinin hangi öğe sınıflarına bağlanageleceğini belirtir. Bir ilişkinin her sonu rol *olarak adlandırılan* bir ilişkidir ve etki alanı ilişkisi, hem iki rolün hem de ilişkinin adını tanımlar.

 İki tür etki alanı ilişkisi vardır: ekleme ilişkileri ve başvuru ilişkileri. DSL Tanımı diyagramında ekleme ilişkilerinin her rolde düz çizgileri, başvuru ilişkilerinin ise kesikli çizgileri vardır.

### <a name="embedding-relationships"></a>ekleme ilişkileri
 Bir modeldeki kökü dışında her öğe, bir ekleme bağlantısının hedefidir. Bu nedenle modelin tamamı, ekleme bağlantılarının tek bir ağacını oluşturur. Ekleme ilişkisi, içeriği veya sahipliği temsil eder. Bu şekilde ilişkili iki model öğesi üst ve alt öğe olarak da bilinir. Alt öğenin üst öğeye ekli olduğu ifade edildi.

 Ekleme bağlantıları genellikle diyagramda bağlayıcılar olarak açıkça gösterilmez. Bunun yerine, bunlar genellikle bir karşıtlık ile temsil edilenlerdir. Modelin kökü diyagram tarafından temsil edilen ve içine eklenmiş öğeler diyagramda şekil olarak görüntülenir.

 Örnekte, Music kök sınıfının MusicHasAlbums ile MusicHasAlbums to Music ekleme ilişkisi vardır. Bu, MusicHasSongs to Song eklemeye sahip. Şarkı, her BirIns'in içindeki bir listede öğeler olarak görüntülenir. Music ayrıca örnekleri diyagramda şekil olarak görünen MusicHasArtists'ı Artist sınıfına da ekleyştiren bir sınıfa sahiptir.

 Varsayılan olarak, eklenmiş öğeler, ebeveynleri silindiğinde otomatik olarak silinir.

 Bir model XML biçiminde dosyaya kaydedilirken, serileştirmeyi özelleştirmedikçe katıştırılmış öğeler, alt öğelerinin içine iç içe yerleştirilmiş olur.

> [!NOTE]
> Ekleme devralma ile aynı değildir. Ekleme ilişkisi içindeki alt öğe, üst öğenin özelliklerini devralmaz. Ekleme, model öğeleri arasındaki bir bağlantı t t'dır. Devralma, sınıflar arasında bir ilişkidir ve model öğeleri arasında bağlantı oluşturmaz.

### <a name="embedding-rules"></a>Ekleme kuralları
 Örnek modeldeki her öğe, modelin kökü dışında tam olarak bir ekleme bağlantısının hedefi olması gerekir.

 Bu nedenle, kök sınıf dışında soyut olmayan her etki alanı sınıfı en az bir ekleme ilişkisinin hedefi olmalıdır veya bir temel sınıftan ekleme devralması gerekir. Bir sınıf iki veya daha fazla eklemenin hedefi olabilir, ancak örnek modeli öğelerinin aynı anda yalnızca bir üst öğesi olabilir. Hedeften kaynaka çokluğun 0...1 veya 1..1 olması gerekir.

### <a name="the-explorer-displays-the-embedding-tree"></a>Gezgin Ekleme Ağacını Görüntüler
 DSL Tanımınız, kullanıcıların model diyagramıyla birlikte göreceği bir gezgin de oluşturur.

 ![DSL'nin oluşturulan gezgini](../modeling/media/music_explorer.png)

 Gezgin, modelde herhangi bir şekil tanımlanmamış olanlar bile tüm öğeleri gösterir. Öğeleri ve ekleme ilişkilerini gösterir, ancak başvuru ilişkilerini gösterir.

 Kullanıcı, bir öğenin etki alanı özelliklerinin değerlerini görmek için model diyagramında veya model gezgininde bir öğe seçer ve bir öğeyi Özellikler penceresi. Diyagramda görüntülenmeenler de dahil olmak üzere tüm etki alanı özelliklerini görüntüler. Örnekte her şarkının hem Title hem de Genre değerleri vardır ancak diyagramda yalnızca Title değeri gösterilir.

## <a name="reference-relationships"></a>Başvuru İlişkileri
 Başvuru ilişkisi, eklemeyen her tür ilişkiyi temsil eder.

 Başvuru ilişkileri genellikle diyagramda şekiller arasındaki bağlayıcılar olarak görüntülenir.

 Modelin XML gösteriminde, bilinen adlar kullanılarak iki öğe arasındaki bir başvuru *bağlantısı temsil edildi.* Diğer bir ifadeyle bilinen adlar, modeldeki her öğeyi benzersiz olarak tanımlamak için kullanılır. Her model öğesinin XML düğümü, ilişkinin adını ve diğer öğenin bilinen adını belirten bir düğüm içerir.

## <a name="roles"></a>Roller
 Her etki alanı ilişkisinin iki rolü vardır: kaynak rol ve hedef rol.

 Aşağıdaki resimde, Yayımcı etki alanı sınıfı ile **PublisherCatalog** etki alanı ilişkisi arasındaki satır kaynak rol olur.  Etki alanı ilişkisi ile Etki Alanı etki **alanı sınıfı** arasındaki çizgi hedef roldür.

 ![Roller ve özellikler.](../modeling/media/propertycode.png)

 Bir ilişkiyle ilişkili adlar özellikle modelden geçen program kodu yazmanız açısından önemlidir. Örneğin DSL çözümünü derlemek için oluşturulan Publisher sınıfının Bir Koleksiyon olan Bir Özellik Kataloğu vardır. Sınıf, Publisher sınıfının tek bir örneği olan Publisher özelliğine sahip.

 DSL Tanımında ilişki sanız, özellik ve ilişki adlara varsayılan değerler verilir. Ancak bunları değiştirebilirsiniz.

## <a name="multiplicities"></a>Çoklulıklar
 Çoklulıklar, bir etki alanı ilişkisinde kaç öğenin aynı role sahip olduğunu belirtir. Örnekte, Katalog rolünde sıfır-çok (0.. ) çokluğu ayarı, Yayımcı etki alanı sınıfının herhangi bir örneğine vermek istediğiniz sayıda \* **PublisherCatalog**  ilişkisi bağlantısına sahip olduğunu belirtir. 

 Diyagrama yazarak veya Özellikler penceresinde özelliğini değiştirerek rolün `Multiplicity` çokluğu **yapılandırabilirsiniz.** Aşağıdaki tabloda bu özelliğin ayarları açıkmektedir.

|Çok şehirlilik türü|Açıklama|
|-|-|
|0..* (Sıfırdan çoka)|Etki alanı sınıfının her örneği, ilişkinin birden çok örneğine sahip olabilir veya ilişki örneğine sahip değildir.|
|0..1 (Sıfırdan bire)|Etki alanı sınıfının her örneği, ilişkinin birden fazla örneğine veya ilişki örneğine sahip olabilir.|
|1..1 (Bir)|Etki alanı sınıfının her örneği, ilişkinin bir örneğine sahip olabilir. Rol sınıfının herhangi bir örneğinden bu ilişkinin birden fazla örneğini oluşturamazsiniz. Doğrulama etkinleştirilirse, rol sınıfının herhangi bir örneğinin ilişki örneği yoksa doğrulama hatası görüntülenir.|
|1..* (Bire çok)|Bu çokluğu olan rolde sınıfının her örneği, ilişkinin birden çok örneğine sahip olabilir ve her örneğin en az bir ilişki örneği olması gerekir. Doğrulama etkinleştirilirse, rol sınıfının herhangi bir örneğinin ilişki örneği yoksa doğrulama hatası görüntülenir.|

## <a name="domain-relationships-as-classes"></a>Sınıf olarak Etki Alanı İlişkileri
 Store'da bir bağlantı, ModelElement'in türetilmiş bir sınıfı olan LinkElement örneği olarak temsil edildi. Bu özellikleri etki alanı ilişkileriyle ilgili etki alanı modeli diyagramında tanımlayabilirsiniz.

 Bir ilişkiyi diğer ilişkilerin kaynağı veya hedefi de hale de siniz. Etki alanı modeli diyagramında etki alanı ilişkisine sağ tıklayın ve ardından Sınıf Olarak **Göster'e tıklayın.** Ek bir sınıf kutusu görüntülenir. Daha sonra ilişkileri buna bağlanarak bu bağlantılara bağlanarak bu bağlantılara bağlanarak bağlantı kur

 Etki alanı sınıflarında olduğu gibi bir ilişkiyi devralmaya göre kısmen tanımlayabilirsiniz. Türetilmiş ilişkiyi seçin ve veri **kümesinde** Temel İlişki Özellikler penceresi.

 Türetilmiş ilişki, temel ilişkisini özeller. Bağlantılarının olduğu etki alanı sınıfları, temel ilişkiyle bağlantılı sınıflardan veya sınıflarından türetilen sınıflarla aynı olmalıdır. Bir modelde türetilmiş ilişkinin bağlantısı oluşturulduğunda, hem türetilmiş hem de temel ilişkilerin bir örneğidir. Program kodunda, temel veya türetilmiş sınıf tarafından oluşturulan özellikleri kullanarak bağlantının ters sona ulaşabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları Sözlüğü](/previous-versions/bb126564(v=vs.100))