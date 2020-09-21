---
title: Modelleri, Sınıfları ve İlişkileri Anlama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, models
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08981e4f63c84d19d4086c75fe33a8b19a515ccf
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809982"
---
# <a name="understanding-models-classes-and-relationships"></a>Modelleri, Sınıfları ve İlişkileri Anlama
Bir etki alanına özgü dil (DSL), yazılabilir olabilecek özel program kodları ile birlikte DSL tanım dosyası tarafından tanımlanır. DSL çözümünde program kodunun çoğu bu dosyadan oluşturulur.

 Bu konuda, DSL tanımının merkezi özellikleri açıklanmaktadır.

## <a name="the-dsl-definition"></a>DSL tanımı
 Açtığınızda `Dsl\DslDefinition.dsl` , Visual Studio pencereniz aşağıdaki resme benzer.

 ![DSL Tasarımcısı](../modeling/media/dsl_designer.png)

 DSL tanımındaki en önemli bilgiler DSL tanımı diyagramında görüntülenir. DslDefinition. dsl 'nin da bir parçası olan ek bilgiler, genellikle diyagramın yanında görünen DSL Gezgini 'nde görüntülenir. En sık kullanılan görevler için diyagram ile ve daha gelişmiş özelleştirmeler için DSL Gezgini ile çalışırsınız.

 DSL tanımı diyagramı model öğelerini tanımlayan etki alanı sınıflarını ve model öğeleri arasındaki bağlantıları tanımlayan ilişkileri gösterir. Ayrıca, kullanıcıya model öğelerini göstermek için kullanılan şekilleri ve bağlayıcıları gösterir.

 ![Kulvar ile DSL Tasarımcısı](../modeling/media/dsl_desinger.png)

 DSL tanımındaki bir öğeyi diyagram üzerinde ya da DSL Gezgini 'nde seçtiğinizde, onunla ilgili bilgiler Özellikler penceresi görüntülenir. Ek bilgiler DSL ayrıntıları penceresinde görüntülenebilir.

### <a name="models-are-instances-of-dsls"></a>Modeller DSLs örnekleridir
 *Model* , bir kullanıcı tarafından oluşturulan DSL 'nin bir örneğidir. Bir model, tanımladığınız etki alanı sınıflarının örnekleri olan model öğelerini ve tanımladığınız etki alanı ilişkilerinin örnekleri olan öğeler arasındaki bağlantıları içerir. Bir modelde model öğeleri ve bir diyagram üzerinde bağlantıları görüntüleyen şekiller ve bağlayıcılar da bulunabilir. DSL tanımı, şekil sınıfları, bağlayıcı sınıfları ve diyagram için bir sınıf içerir.

 Bir DSL tanımı, *etki alanı modeli*olarak da bilinir. DSL tanımı veya etki alanı modeli, etki alanına özgü dilin tasarım zamanı gösterimidir, ancak model alana özgü dilin çalışma zamanı örneklemedir.

## <a name="domain-classes-define-model-elements"></a>Etki alanı sınıfları model öğelerini tanımlar
 Etki alanı sınıfları, etki alanındaki çeşitli öğeleri oluşturmak için kullanılır ve etki alanı ilişkileri, öğeler arasındaki bağlantılardır. Bunlar, modellerini oluştururken tasarıma özgü dilin kullanıcıları tarafından örneklendirilecektir öğelerin ve bağlantıların tasarım zamanı gösterimidir.

 Bu çizimde, bir müzik kitaplığı DSL kullanıcısı tarafından oluşturulmuş bir model gösterilmektedir. Müzik albümleri, şarkıların listesini içeren kutular tarafından temsil edilir. Sanatçılar yuvarlak köşeli kutular tarafından temsil edilir ve katkıda bulundukları albümlere bağlanır.

 ![Oluşturulan DSL örnek modeli](../modeling/media/music_instance.png)

 DSL tanımı iki yönü ayırır. Model diyagramındaki model öğelerinin görünümü Şekil sınıfları ve bağlayıcı sınıfları kullanılarak tanımlanır. Modelde taşınan bilgiler, etki alanı sınıfları ve etki alanı ilişkileri kullanılarak tanımlanır.

 Aşağıdaki çizimde, müzik kitaplığının DSL tanımındaki etki alanı sınıfları ve ilişkileri gösterilmektedir.

 ![Ekleme ve başvuru ilişkileri](../modeling/media/music_classes.png)

 Çizimde dört etki alanı sınıfı gösterilmektedir: müzik, albüm, sanatçı ve şarkı. Etki alanı sınıfları ad, başlık vb. gibi etki alanı özelliklerini tanımlar. Örnek modelinde, bu özelliklerden bazılarının değerleri diyagramda görüntülenir.

 Sınıflar arasında etki alanı ilişkileri vardır: MusicHasAlbums, MusicHasArtists, albümde Hasşarkılar ve Artistappearedonalbümler. İlişkiler, 1.. 1, 0.. * gibi çeşitlilimler vardır. Örneğin, her şarkının albümle ilişkili bir albümle ilişkili olması gerekir. Her albümün herhangi bir sayıda şarkıyı olabilir.

### <a name="rearranging-the-dsl-definition-diagram"></a>DSL tanımı diyagramını yeniden düzenleme
 Bu resimde albüm olarak bir etki alanı sınıfının DSL tanımı diyagramında birkaç kez görünebileceğini unutmayın. Her zaman bir ana görünüm vardır ve bazı *başvuru* görünümleri olabilir.

 DSL tanımı diyagramını yeniden düzenlemek için şunları yapabilirsiniz:

- **Ağacı buraya getir** ve **bölmeyi Böl** komutlarını kullanarak ana ve başvuru görünümlerini takas edin. Bu komutları görmek için tek bir etki alanı sınıfına sağ tıklayın.

- Ctrl + yukarı ve Ctrl + aşağı tuşlarına basarak etki alanı sınıflarını ve şekil sınıflarını yeniden sıralayın.

- Her şeklin sağ üst köşesindeki simgeyi kullanarak sınıfları daraltın veya genişletin.

- Bir etki alanı sınıfının altındaki eksi işaretine (-) tıklayarak ağacın parçalarını daraltın.

## <a name="inheritance"></a>Devralma
 Etki alanı sınıfları devralma kullanılarak tanımlanabilir. Devralma türetmesi oluşturmak için, devralma aracına tıklayın, türetilmiş sınıfa tıklayın ve ardından temel sınıfa tıklayın. Model öğesi, kendi etki alanı sınıfında tanımlanmış tüm özelliklere sahiptir ve temel sınıftan devralınan tüm özelliklerle birlikte. Ayrıca, ilişkilerde rollerini devralır.

 Devralma Ayrıca Ilişkiler, şekiller ve bağlayıcılar arasında da kullanılabilir. Devralma aynı grup içinde tutmalıdır. Bir şekil, bir etki alanı sınıfından devralınabilir.

## <a name="domain-relationships"></a>Etki alanı Ilişkileri
 Model öğeleri ilişkilerle bağlanabilir. Bağlantılar her zaman binary; tam olarak iki öğe bağlar. Ancak, herhangi bir öğe diğer nesnelere birçok bağlantıya sahip olabilir ve aynı öğe çifti arasında birden fazla bağlantı bile olabilir.

 Farklı öğe sınıfları tanımlayabileceğiniz gibi, farklı bağlantı sınıfları tanımlayabilirsiniz. Bir bağlantının sınıfına *etki alanı ilişkisi*denir. Bir etki alanı ilişkisi, örneklerinin hangi öğe sınıflarının bağlanabileceği belirler. Bir ilişkinin her ucuna *rol*adı verilir ve etki alanı ilişkisi, ilişkinin kendisi için ve olmak üzere iki rolün adlarını tanımlar.

 İki tür etki alanı ilişkisi vardır: ilişkileri ve başvuru ilişkilerini katıştırma. DSL tanımı diyagramında, katıştırma ilişkilerinin her bir rolde düz satırları vardır ve başvuru ilişkilerinde kesikli çizgiler vardır.

### <a name="embedding-relationships"></a>Ilişkiler katıştırma
 Bir modeldeki her öğe kök hariç, tek bir gömme bağlantısının hedefidir. Bu nedenle, modelin tamamı ekleme bağlantılarının tek bir ağacını oluşturur. Bir katıştırma ilişkisi, kapsama veya sahipliği temsil eder. Bu şekilde ilgili iki model öğesi de üst ve alt öğe olarak bilinir. Alt öğeye gömülme denir.

 Ekleme bağlantıları genellikle bir diyagramda bağlayıcı olarak açıkça gösterilmez. Bunun yerine, genellikle kapsama göre temsil edilir. Modelin kökü diyagram tarafından temsil edilir ve içine katıştırılmış öğeler diyagramda şekil olarak görüntülenir.

 Örnekte, kök sınıf müziğiniz, albüme karşı bir ekleme ilişkisine sahiptir. Bu, şarkının albümüne bir katıştırılması için bir katıştırma ilişkisine sahiptir. Şarkılar her albümün içindeki bir listede öğe olarak görüntülenir. Müziğin aynı zamanda, örnekleri diyagramda şekil olarak görünen sanatçı sınıfına bir katıştırma MusicHasArtists de vardır.

 Varsayılan olarak, katıştırılmış öğeler, üst öğeleri silindiğinde otomatik olarak silinir.

 Bir model XML biçiminde dosyaya kaydedildiğinde, serileştirme özelleştirmediğiniz müddetçe gömülü öğeler üst öğelerinin içine yuvalanır.

> [!NOTE]
> Ekleme, devralma ile aynı değildir. Bir katıştırma ilişkisindeki alt öğeler, üst öğenin özelliklerini almıyor. Ekleme, model öğeleri arasındaki bir bağlantı türüdür. Devralma sınıflar arasında bir ilişkidir ve model öğeleri arasında bağlantı oluşturmaz.

### <a name="embedding-rules"></a>Ekleme kuralları
 Bir örnek modelindeki her öğe, modelin kökü dışında tam olarak bir katıştırma bağlantısının hedefi olmalıdır.

 Bu nedenle, kök sınıf hariç, soyut olmayan her etki alanı sınıfı, en az bir katıştırma ilişkisinin hedefi olmalıdır veya temel sınıftan bir katıştırma devralması gerekir. Bir sınıf iki veya daha fazla katıştırın hedefi olabilir, ancak örnek modeli öğeleri aynı anda yalnızca bir üst öğeye sahip olabilir. Hedeften kaynağa kadar olan çokluk 0.. 1 veya 1.. 1 olmalıdır.

### <a name="the-explorer-displays-the-embedding-tree"></a>Gezgin ekleme ağacını görüntüler
 DSL tanımınız ayrıca kullanıcıların kendi model diyagramlarıyla birlikte göreceği bir gezgin de oluşturur.

 ![DSL Gezgini oluşturuldu](../modeling/media/music_explorer.png)

 Gezgin, model içinde herhangi bir şekil tanımlamadığınıza dahil olmak üzere modeldeki tüm öğeleri gösterir. Öğeleri ve katıştırma ilişkilerini gösterir, ancak başvuru ilişkileri içermez.

 Bir öğenin etki alanı özelliklerinin değerlerini görmek için, Kullanıcı model diyagramında veya model Gezgininde bir öğe seçer ve Özellikler penceresi açar. Diyagramda görüntülenenlerden dahil olmak üzere tüm etki alanı özelliklerini görüntüler. Örnekte, her şarkının hem bir başlığı hem de tarzı vardır, ancak diyagramda yalnızca başlığın değeri gösterilir.

## <a name="reference-relationships"></a>Başvuru Ilişkileri
 Başvuru ilişkisi, katıştırma olmayan her türlü ilişkiyi temsil eder.

 Başvuru ilişkileri genellikle, şekiller arasında bağlayıcı olarak diyagramda görüntülenir.

 Modelin XML gösteriminde, iki öğe arasındaki bir başvuru bağlantısı, *bilinen adlar* kullanılarak temsil edilir. Diğer bir deyişle, adlar modeldeki her öğeyi benzersiz bir şekilde tanımlayan adlardır. Her model öğesi için XML düğümü, ilişkinin adını ve diğer öğenin bilinen adını belirten bir düğüm içerir.

## <a name="roles"></a>Roller
 Her etki alanı ilişkisinde, bir kaynak rol ve bir hedef rol olmak üzere iki rol bulunur.

 Aşağıdaki resimde, **Yayımcı** etki alanı sınıfı ve **PublisherCatalog** etki alanı ilişkisi arasındaki çizgi, kaynak roldür. Etki alanı ilişkisi ve **Albüm** etki alanı sınıfı arasındaki çizgi hedef roldür.

 ![Roller ve Özellikler.](../modeling/media/propertycode.png)

 Bir ilişkiyle ilişkili adlar özellikle modelden geçen program kodunu yazdığınızda önemlidir. Örneğin, DSL çözümünü yapılandırdığınızda, oluşturulan sınıf yayımcısının Albümler koleksiyonu olan bir özellik kataloğu vardır. Sınıf albümünün, sınıf yayımcısının tek bir örneği olan bir özellik yayımcısı vardır.

 Bir DSL tanımında ilişki oluşturduğunuzda, özellik ve ilişki adlarına varsayılan değerler verilir. Ancak, bunları değiştirebilirsiniz.

## <a name="multiplicities"></a>Çeşitlilimler
 Çoğullılıklar, bir etki alanı ilişkisinde kaç öğenin aynı role sahip olduğunu belirtir. Örnekte, Katalog rolünde bulunan sıfırdan çok (0.. \* ) çoğulluk ayarı, **Yayımcı** etki alanı **Catalog** sınıfının herhangi bir örneğinin, vermek istediğiniz kadar çok **PublisherCatalog** ilişki bağlantılarına sahip olduğunu belirtir.

 Diyagram üzerine yazarak veya `Multiplicity` **Özellikler** penceresinde özelliğini değiştirerek bir rolün çoğulluğu yapılandırın. Aşağıdaki tabloda bu özelliğin ayarları açıklanmaktadır.

|Çokluk türü|Açıklama|
|-|-|
|0.. * (sıfırdan fazla)|Alan sınıfının her örneği, ilişkinin birden fazla örneğine veya ilişkinin örneklerine sahip olabilir.|
|0.. 1 (sıfır-bir)|Alan sınıfının her örneği, ilişkinin birden fazla örneğine veya ilişkinin örneklerine sahip olamaz.|
|1.. 1 (bir)|Alan sınıfının her bir örneği ilişkinin bir örneğine sahip olabilir. Rol sınıfının herhangi bir örneğinden bu ilişkinin birden fazla örneğini oluşturamazsınız. Doğrulama etkinleştirilirse, rol sınıfının herhangi bir örneğinde ilişki örneği olmadığında bir doğrulama hatası görüntülenir.|
|1.. * (bire çok)|Bu çokluğa sahip olan roldeki her sınıfın örneği, ilişkinin birden fazla örneğine sahip olabilir ve her örnek ilişkinin en az bir örneğine sahip olmalıdır. Doğrulama etkinleştirilirse, rol sınıfının herhangi bir örneğinde ilişki örneği olmadığında bir doğrulama hatası görüntülenir.|

## <a name="domain-relationships-as-classes"></a>Sınıflar olarak etki alanı Ilişkileri
 Bir bağlantı, depoda bir ModelElement sınıfının türetilmiş bir sınıfı olan LinkElement örneği olarak temsil edilir. Bu özellikleri etki alanı ilişkilerinde etki alanı modeli diyagramında tanımlayabilirsiniz.

 Ayrıca, diğer ilişkilerin kaynağını veya hedefini bir ilişki haline getirebilirsiniz. Etki alanı modeli diyagramında, etki alanı ilişkisine sağ tıklayın ve ardından **sınıf olarak göster**' e tıklayın. Ek bir sınıf kutusu görünür. Daha sonra bu ilişkiye ilişkiler bağlayabilirsiniz.

 Etki alanı sınıflarıyla yapabildiğiniz gibi, kısmen devralma yoluyla bir ilişki tanımlayabilirsiniz. Türetilmiş ilişkiyi seçin ve Özellikler penceresi **temel ilişkiyi** ayarlayın.

 Türetilmiş bir ilişki, temel ilişkisini uzmanlaşmış hale getirir. Bağlandığı etki alanı sınıfları, temel ilişkiyle bağlantılı sınıflarla aynı veya ondan türetilmelidir. Türetilmiş ilişkinin bir bağlantısı modelde oluşturulduğunda, hem türetilmiş hem de temel ilişkilerin bir örneğidir. Program kodu ' nda, temel ya da türetilmiş sınıf tarafından oluşturulan özellikleri kullanarak bağlantının ters ucuna gidebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Alana Özgü Dil Araçları sözlüğü](/previous-versions/bb126564(v=vs.100))