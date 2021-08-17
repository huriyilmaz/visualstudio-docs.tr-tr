---
title: Model aracılığıyla test geliştirme
description: Sistem ve bileşenlerinin testlerini düzenlemeye yardımcı olmak için gereksinimleri ve mimari modelleri nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tests and requirements
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b1d4d2d1d30c21bcfd7b6ee47eba9a4ed97f26e67f768779f474c9e2f33dbfa8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386152"
---
# <a name="develop-tests-from-a-model"></a>Model aracılığıyla test geliştirme
Sistem ve bileşenlerinin testlerini düzenlemenize yardımcı olmak için gereksinimleri ve mimari modelleri kullanabilirsiniz. Bu uygulama, kullanıcılar ve diğer paydaşlar için önemli olan gereksinimleri test etmenizi sağlar ve gereksinimler değiştiklerinde testleri hızla güncelleştirmenizi sağlar. [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)]kullanıyorsanız, modeller ve testler arasındaki bağlantıları da koruyabilirsiniz.

 Bu özellikleri destekleyen Visual Studio için bkz. [Mimari ve modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="system-and-subsystem-testing"></a>Sistem ve Alt Sistem Testi
 *Kabul testi olarak* da bilinen *sistem testi,* kullanıcıların ihtiyaçlarının karşılanıp karşılanmayacaklarını test etmek anlamına gelir. Bu tür testler, iç tasarım yerine sistemin dışarıdan görünen davranışıyla ilgili endişeye sahiptir.

 Sistem testleri, bir sistemi genişleterek veya yeniden tasarlarken çok değerlidir. Bunlar, kodu değiştirirken hatalardan kaçınmanıza yardımcı olur.

 Bir sistemde herhangi bir değişiklik veya uzantı planlasanız, mevcut sistemde çalıştırilen bir dizi sistem testiyle başlamak yararlı olur. Ardından, yeni gereksinimleri test etmek için testleri genişletebilirsiniz veya ayarlayabilir, kodda değişiklikler yapabilirsiniz ve tüm test kümelerini yeniden çalıştırabilirsiniz.

 Yeni bir sistem geliştirirken, geliştirme başlar başlamaz test oluşturmaya başlayabilirsiniz. Her özelliği geliştirmeden önce testleri tanımlayarak, gereksinimler tartışmalarını çok özel bir şekilde yakalayabilirsiniz.

 Alt sistem testi, sistemin ana bileşenlerine aynı ilkeleri uygular. Her bileşen diğer bileşenlerden ayrı olarak test edilir. Alt sistem testleri, bileşenin kullanıcı arabirimlerinde veya API'lerinde görünen davranışa odaklanır.

## <a name="deriving-system-tests-from-a-requirements-model"></a>Gereksinimler Modelinden Sistem Testleri Türetme
 Sistem testleri ile gereksinimler modeli arasında ilişki oluşturabilir ve sürdürebilirsiniz. Bu ilişkiyi kurmak için, gereksinimler modelinin ana öğelerine karşılık gelen testler yazarsiniz. Visual Studio, test ve modelin bölümleri arasında bağlantı oluşturmanıza izin vererek bu ilişkiyi korumanıza yardımcı olur. Gereksinimler modelleri hakkında daha fazla bilgi için bkz. [Model kullanıcı gereksinimleri.](../modeling/model-user-requirements.md)

### <a name="write-tests-for-each-use-case"></a>Her Kullanım Durumu için Test Yazma
 [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)]kullanıyorsanız, gereksinimler modelde tanımlandığı her kullanım durumu için bir test grubu oluşturabilirsiniz. Örneğin Sipariş Oluştur ve Siparişe Öğe Ekle'yi içeren Bir Yemek SiparişIni SiparişLe kullanım örneğiniz varsa, bu kullanım örnekleriyle ilgili hem genel hem de daha ayrıntılı testler oluşturabilirsiniz.

 Bu yönergeler yararlı olabilir:

- Her kullanım örneğinin ana yollar ve olağanüstü sonuçlar için çeşitli testleri olması gerekir.

- Gereksinimler modelinde bir kullanım durumu açıklanıyorsa, kullanıcının hedefe ulaşmak için takip eden yordamları ayrıntılı olarak açıklamaktan çok, elde edilen hedefin sonkoşullarını tanımlamak daha önemlidir. Örneğin Order a Yemek sonkoşulları, Restoran'ın müşteri için yemek hazırlaması ve Müşterinin ödemesi olabilir. Son koşul, testlerinizi doğrulamanız gereken ölçüttir.

- Ayrı testleri sonkoşulların ayrı yan tümcelerine temel. Örneğin, siparişi restorana bildirmek ve müşteriden ödeme almak için ayrı testler oluşturun. Bu ayrım şu avantajlara sahiptir:

  - Gereksinimlerin farklı yönlerinden değişiklikler sıklıkla bağımsız olarak gerçekleşir. Bu şekilde testleri farklı yönlere ayırarak, gereksinimler değiştiklerinde testleri güncelleştirmeyi kolaylaştırırsınız.

  - Geliştirme planı kullanım durumundan bir yönü diğerine uygulayıyorsa, geliştirme ilerledikçe testleri ayrı ayrı etkinleştirebilirsiniz.

- Testleri tasarlarken, son koşula ulaşıp ulaşı olmadığını belirleyen test verileri seçimlerini koddan veya betikten ayırabilirsiniz. Örneğin, basit bir aritmetik işlevin testi şöyle olabilir: Giriş 4; çıkışın 2 olduğunu doğrulayın. Bunun yerine betiği şu şekilde tasarla: Bir giriş seçin; çıkışı kendisiyle çarpın ve sonucun özgün giriş olduğunu doğrulayın. Bu stil, testin ana gövdesini değiştirmeden test girişlerini değiştirmene olanak sağlar.

#### <a name="linking-tests-to-use-cases"></a>Testleri kullanım örneklerine bağlama
 Testlerinizi tasarlamak [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] ve çalıştırmak için kullanıyorsanız, testlerinizi gereksinim, kullanım durumu veya kullanıcı hikayesi iş öğeleri altında düzenleyebilirsiniz. Bu iş öğelerini modelinizin kullanım örneklerine bağabilirsiniz. Bu, testlerde yapılan gereksinimler değişikliklerini hızla izlemenizi sağlar ve her kullanım durumu için ilerlemeyi izlemenizi sağlar.

###### <a name="to-link-tests-to-a-use-case"></a>Testleri bir kullanım durumuna bağlama

1. içinde, [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] bir gereksinim oluşturun ve bir test paketini temel alan bir paket oluşturun.

    Oluşturma gereksinimi, içinde bir iş [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)] öğesidir. Projenizin Team Foundation ile kullandığı işlem şablonuna bağlı olarak bir Kullanıcı Hikayesi, Gereksinim veya Kullanım Durumu iş öğesi olabilir. Daha fazla bilgi için [bkz. Çevik araçlar ve Çevik proje yönetimi hakkında.](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)

2. Gereksinim iş öğesini modelinizin bir veya daha fazla kullanım örneklerine bağlama.

    Kullanım durumu diyagramında bir kullanım durumuna sağ tıklayın ve ardından İş **Öğesine Bağlantı'ya tıklayın.**

3. Kullanım durumlarını doğru kullanan test paketine, test test durumlarını ekleyin.

   Genellikle, her bir kullanıcı hikayesi veya gereksinim iş öğesi, modelinizin çeşitli kullanım örneklerine ve her kullanım örnekleri de çeşitli kullanıcı hikayelerine veya gereksinimlerine bağlantı sağlar. Bunun nedeni, her bir kullanıcı hikayesi veya gereksiniminin çeşitli kullanım örnekleri geliştiren bir dizi görevi kapsar. Örneğin, projenizin erken bir yinelemesinde, müşterinin katalogdan öğeleri seçe ve teslimini olabileceği temel kullanıcı hikayesini geliştirebilirsiniz. Daha sonraki bir yinelemede, hikaye kullanıcının siparişi tamamladıktan sonra ödemesi ve tedarikçinin ürünleri gönderdikten sonra para aldığı olabilir.  Her hikaye, Order Goods kullanım durumu son koşula bir yan tümcesi ekler.

   Kullanım durumu diyagramında bu yan tümceleri ayrı açıklamalara yazarak gereksinimlerden son koşulların yan tümcelerine ayrı bağlantılar oluşturabilirsiniz. Her bir açıklamayı bir gereksinim iş öğesine, açıklamayı da diyagramda kullanım durumuna bağabilirsiniz.

### <a name="base-tests-on-the-requirements-types"></a>Gereksinimler Türlerine Göre Temel Testler
 Gereksinimler modelinin sınıfları, arabirimleri ve numaralarıyla ilgili türler, kullanıcıların işletmeleri hakkında nasıl düşünmeleri ve iletişim kurmaları açısından kavramları ve ilişkileri açıklar. Yalnızca sistemin iç tasarımıyla ilgili türleri dışlar.

 Testlerinizi bu gereksinimler türüne göre tasarlar. Bu uygulama, gereksinimlerde yapılan değişiklikler tartışılırken değişiklikleri testlerde gerekli değişikliklerle ilişkilendirmenin kolay olduğundan emin olur. Testleri ve amaçlanan sonuçları doğrudan son kullanıcılarla ve diğer proje katılımcılarıyla tartışmayı mümkün yapar. Bu, kullanıcıların ihtiyaçlarının geliştirme sürecinin dışında korunulması ve tasarımda olası kusurlar ile ilgili testlerin yanlışlıkla tasarılmasından kaçınılması anlamına gelir.

 El ile yapılan testler için bu uygulama, test betiklerinde gereksinimler modelinin sözlüğüne uygun olarak gereksinimlerini içerir. Otomatikleştirilmiş testler için bu uygulama, test kodunuz için temel olarak gereksinimler sınıfı diyagramlarını kullanmayı ve gereksinim modelini koda bağlamaya yardımcı olacak erişimci ve güncelleştiren işlevleri oluşturmayı içerir.

 Örneğin, bir gereksinimler modeli Menü, Menü Öğesi, Sipariş ve aralarındaki ilişkilendirmeleri içerebilir. Bu model, yemek siparişi sistemi tarafından depolanan ve ele alınan bilgileri temsil eder, ancak uygulamasının karmaşıklıklarını temsil etmemektedir. Çalışma sisteminde veritabanlarında, kullanıcı arabirimleri ve API'lerde her türün birkaç farklı gerçekleştirilmesi olabilir. Dağıtılmış bir sistemde, her örneğin aynı anda sistemin farklı kısımlarında depolanan çeşitli varyantları olabilir.

 Siparişe Öğe Ekle gibi bir kullanım örneği test etmek için bir test yöntemi aşağıdakine benzer bir kod içerebilir:

```
Order order = ... ; // set up an order
// Store prior state:
int countBefore = order.MenuItems.Count;
// Perform use case:
MenuItem chosenItem = ...; // choose an item
AddItemToOrder (chosenItem, order);
// Verify part of postcondition:
int countAfter = order.MenuItems.Count;
Assert (countAfter == countBefore = 1);
```

 Bu test yönteminin gereksinimler modelinin sınıflarını kullandığına dikkat edin. İlişki ve öznitelikler .NET özellikleri olarak gerçekleştirildi.

 Bunu yapmak için sınıfların özellikleri, geçerli durumu hakkında bilgi almak için sisteme erişen salt okunur işlevler veya erişimciler olarak tanımlanmalıdır. AddItemToOrder gibi kullanım durumlarının benzetimini yapmak için sistemi API'si aracılığıyla veya kullanıcı arabiriminin altındaki bir katman aracılığıyla desteklemesi gerekir. Order ve MenuItem gibi test nesnelerinin oluşturucuları, sistemin içinde karşılık gelen öğeleri oluşturmak için sistemi de kullanmalıdır.

 Erişimcilerin ve güncelleştirenlerin çoğu, uygulamanın normal API'si aracılığıyla zaten kullanılabilir. Ancak testleri etkinleştirmek için bazı ek işlevlerin yazıldığı da olabilir. Bu ek erişimciler ve güncelleştirciler bazen 'test araçları' olarak da bilinir. Sistemin iç tasarımına bağlı olduğundan, bunları sağlamak sistem geliştiricilerinin sorumluluğundadır, ancak testçiler testlerin kodunu gereksinimler modeli açısından yazar.

 Otomatikleştirilmiş testler yazarken, erişimcileri ve güncelleştirenleri sarmak için Genel Testler'i kullanabilirsiniz.

### <a name="tests-for-business-rules"></a>Business Rules için testler
 Bazı gereksinimler herhangi bir kullanım durumuyla doğrudan ilgili değildir. Örneğin, DinnerNow işletmesi müşterilerin birçok Menüyü seçmesine olanak sağlar, ancak her Siparişte seçilen tüm Öğelerin tek bir Menüden olması gerekir. Bu iş kuralı, gereksinimler sınıf modelinde Siparişler, Menüler ve Öğeler arasındaki ilişkilendirmeler hakkında sabit olarak ifade olabilir.

 Bu tür sabit bir kural yalnızca şu anda tanımlanmış olan tüm kullanım durumlarını değil, daha sonra tanımlanacak diğer kullanım durumlarını da yönetir. Bu nedenle, herhangi bir kullanım örneğinden ayrı olarak yazmak ve kullanım örneklerinden ayrı olarak test etmek yararlıdır.

## <a name="deriving-subsystem-tests-from-models"></a>Modellerden Alt Sistem Testleri Türetme
 Büyük bir sistemin üst düzey tasarımında bileşenleri veya alt sistemleri tanımlayabilirsiniz. Bunlar ayrı olarak tasarlanabilir veya farklı bilgisayarlarda bulunan veya birçok şekilde yeniden birleştirilebilir yeniden kullanılabilir modüller olan parçaları temsil eder.

 Her ana bileşene, tam sistem için kullanmakta olduğu gibi aynı ilkeleri uygulayabilirsiniz. Büyük bir projede her bileşenin kendi gereksinimler modeli olabilir. Daha küçük projelerde, ana bileşenleri ve bunların etkileşimlerini göstermek için bir mimari model veya üst düzey tasarım oluşturulabilir. Daha fazla bilgi için [bkz. Uygulama mimarinizi modelleme.](../modeling/model-your-app-s-architecture.md)

 Her iki durumda da, gereksinimler modeli ile sistem testleri arasında olduğu gibi model öğeleriyle alt sistem testleri arasında bir ilişki kurebilirsiniz.

### <a name="isolate-components-with-provided-and-required-interfaces"></a>Sağlanan ve Gerekli Arabirimlerle Bileşenleri Yalıtma
 Bir bileşenin sisteminizin veya dış hizmetlerinizin diğer bölümlerine sahip olduğu tüm bağımlılıkları belirlemek ve bunları gerekli arabirimler olarak göstermek yararlıdır. Bu alıştırma genellikle, tasarımın geri kalanından çok daha fazla ayrılmış ve kolayca ayrılabilir bir şekilde yeniden tasarlamasına yol açar.

 Bu ayrılma avantajı, bileşenin genellikle kullandığı hizmetlerin sahte nesneleriyle değiştirilerek test için yürütülemeidir. Bunlar, test amaçları için ayarlanan bileşenlerdir. Bir sahte bileşen, bileşeninizin gerektirdiği arabirimi sağlar ve bunları benzetimli verilerle sorgular. Sahte bileşenler, bileşenin tüm arabirimlerine bağlanabilmiş olan bir bütün test bandı parçasını oluşturur.

 Sahte testin bir avantajı, bileşeninizin kullanacağı diğer bileşenler hala geliştirme aşamasında olduğundan, bileşenlerinizi geliştirebileceğiniz bir avantajdır.

## <a name="maintain-the-relationships-between-tests-and-model"></a>Testler ve model arasındaki Ilişkileri koruma
 Birkaç haftada bir yineleme gerçekleştiren tipik bir projede, gereksinim incelemesi her yinelemenin başlangıcında yakınında tutulur. Toplantıda bir sonraki yinelemede teslim edilecek özellikler ele alınmaktadır. Gereksinimler modeli, geliştirilecek eylem kavramlarını, senaryoları ve işlem dizilerini tartışmak için kullanılabilir. İş hissedarları öncelikleri, geliştiriciler tahminleri yapar ve test ediciler her bir özelliğin beklenen davranışının doğru yakalandığından emin olur.

 Sınama yazma, bir gereksinimi tanımlamanın en etkili yoludur ve ayrıca bir kişinin gerekli olanları anlayacağından emin olmanın etkili bir yoludur. Ancak, bir belirtim atölyesi sırasında testlerin yazılması çok uzun sürer, model oluşturma işlemi çok daha hızlı bir şekilde yapılabilir.

 Bir test noktasından, gereksinimler modeli testler için bir toplu değer olarak görülebilir. Bu nedenle, proje genelinde testler ve modeller arasındaki ilişkinin korunması önemlidir.

## <a name="attaching-test-cases-to-model-elements"></a><a name="Attaching"></a> Model öğelerine test durumları iliştirme
 Projeniz kullanıyorsa [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] , testlerinizi modelinizdeki öğelere bağlayabilirsiniz. Bu, gereksinimlerdeki bir değişiklikten etkilenen testleri hızlı bir şekilde bulmanıza olanak sağlar ve bir gereksinimin gerçekleştirilme kapsamını izlemenize yardımcı olur.

 Testleri tüm öğe türlerine bağlayabilirsiniz. İşte bazı örnekler:

- Kullanım örneğini, onu uygulayan testlere bağlayın.

- Kullanım örneği sonkoşulun yan tümcesini veya hedefini, kullanım örneğine bağlı açıklamaların üzerine yazın ve ardından her açıklamaya test bağlayın.

- Sınıf diyagramlarındaki veya Etkinlik diyagramlarındaki açıklamalarda sabit kurallar yazın ve bunları testlerle ilişkilendirin.

- Testleri bir etkinlik diyagramına veya tek tek etkinliklere bağlayın.

- Bir test paketini bileşene bağlayın veya sınar.

#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Testleri model öğesine veya ilişkiye bağlamak için

1. İçinde [!INCLUDE[TCMlong](../modeling/includes/tcmlong_md.md)] , bir gereksinim oluşturun ve üzerinde bir test paketi temel alır.

    Oluşturduğunuz gereksinim içindeki bir iş öğesidir [!INCLUDE[vstsTfsShort](../modeling/includes/vststfsshort_md.md)] . Projenizin Team Foundation ile kullandığı işlem şablonuna bağlı olarak, bir kullanıcı hikayesi, gereksinim veya kullanım örneği iş öğesi olabilir. Daha fazla bilgi için bkz. [Çevik Araçlar ve çevik proje yönetimi hakkında](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true).

2. Gereksinim iş öğesini modelinizdeki bir veya daha fazla öğeye bağlayın.

    Modelleme diyagramında bir öğeye, açıklamaya veya ilişkiye sağ tıklayın ve sonra **Iş öğesine bağla**' ya tıklayın.

3. Test paketine, model öğesinde ifade edilen gereksinimi doğrulayan test çalışmalarına ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)
- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)
- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)
- [Mimariyi Çözümleme ve Mimarinin Modelini Oluşturma](../modeling/analyze-and-model-your-architecture.md)
