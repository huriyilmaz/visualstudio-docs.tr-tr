---
title: Bir modelden test geliştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- tests and requirements
ms.assetid: 40f87192-ba85-4552-8804-314a678261ae
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2b9fec6954706fcecb1281650a8db3d85f08fbd0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669784"
---
# <a name="develop-tests-from-a-model"></a>Model aracılığıyla test geliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sistem ve bileşenlerinin testlerini düzenlemenize yardımcı olması için gereksinimleri ve mimari modelleri kullanabilirsiniz. Bu uygulama, kullanıcılar ve diğer paydaşlar için önemli olan gereksinimleri test etmenize yardımcı olur ve gereksinimler değiştiğinde testleri hızlı bir şekilde güncelleştirmenize yardımcı olur. Kullanıyorsanız [!INCLUDE[TCMext](../includes/tcmext-md.md)] , modeller ve testler arasındaki bağlantıları da koruyabilirsiniz.

 Visual Studio 'nun hangi sürümlerinin bu özellikleri desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="system-and-subsystem-testing"></a>Sistem ve alt sistem testi
 *Kabul testi*olarak da bilinen *sistem testi* , kullanıcıların ihtiyaçlarını karşılamakta olup olmadığını test ediyor demektir. Bu tür testler, iç tasarım yerine sistemin dışarıdan görünür davranışına ilişkin kaygılardır.

 Sistem testleri sistemi genişletirken veya yeniden tasarlarken çok değerlidir. Kodu değiştirirken hata getirmekten kaçınmanıza yardımcı olurlar.

 Bir sisteme herhangi bir değişiklik veya uzantı planlarken, var olan sistemde çalışan bir sistem testi kümesiyle başlamak yararlı olur. Ardından, yeni gereksinimleri test etmek, koddaki değişiklikleri yapmak ve tüm test kümesini yeniden çalıştırmak için testleri genişletebilir veya düzenleyebilirsiniz.

 Yeni bir sistem geliştirirken, geliştirme başladıktan hemen sonra test oluşturmaya başlayabilirsiniz. Her bir özelliği geliştirmeden önce testleri tanımlayarak, gereksinim tartışmalarını çok belirli bir şekilde yakalayabilirsiniz.

 Alt sistem testi, bir sistemin ana bileşenlerine aynı ilkeleri uygular. Her bileşen diğer bileşenlerden ayrı olarak test edilir. Alt sistem testleri, bileşenin kullanıcı arabirimlerinde veya API 'sinde görünen davranışa odaklanmaktadır.

 Testlerin nasıl çalıştırılacağı hakkında daha fazla bilgi için bkz. [uygulamayı test etme](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac).

## <a name="deriving-system-tests-from-a-requirements-model"></a>Gereksinimler modelinden Sistem testlerini türeten
 Sistem testleri ve gereksinimler modeli arasında bir ilişki oluşturabilir ve bakımını yapabilirsiniz. Bu ilişkiyi oluşturmak için, gereksinimler modelinin ana öğelerine karşılık gelen testleri yazarsınız. Visual Studio, modelin testleri ve bölümleri arasında bağlantılar oluşturmanıza izin vererek ilişkiyi korumanıza yardımcı olur. Gereksinim modelleri hakkında daha fazla bilgi için bkz. [model Kullanıcı gereksinimleri](../modeling/model-user-requirements.md).

### <a name="write-tests-for-each-use-case"></a>Her kullanım örneği için test yazma
 Kullanıyorsanız [!INCLUDE[TCMext](../includes/tcmext-md.md)] , gereksinim modelinizde tanımladığınız her kullanım örneği için bir test grubu oluşturabilirsiniz. Örneğin, sipariş oluştur ve sipariş Ekle öğelerini içeren bir yemek kullanım örneği siparişiniz varsa, bu kullanım örneklerinin her ikisi için de test oluşturabilirsiniz. Kullanım örnekleri hakkında daha fazla bilgi için bkz. [UML Kullanım örneği diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md).

 Bu yönergeler yararlı olabilir:

- Her kullanım örneğinin, ana yollar ve olağanüstü sonuçlar için birkaç testi olmalıdır.

- Gereksinimler modelinde bir kullanım durumu tanımlarken, hedefin hedefe ulaşmak için izlediği yordamları ayrıntılandırmak üzere, bu, elde edilen hedefi tanımlamak daha önemlidir. Örneğin, bir yemeğin siparişin sonkoşulu bir restoran 'nın müşteri için yemek hazırlamakta ve müşterinin ödediği bir şekilde olabilir. Sonkoşul, testlerinizin doğrulanması gereken ölçüttür.

- Sonkoşulun ayrı yan tümcelerinde ayrı test tabanlı testler. Örneğin, siparişi restorana bildirmek ve müşteriden ödeme yapmak için ayrı testler oluşturun. Bu ayrım şu avantajlara sahiptir:

  - Gereksinimlerin farklı yönlerinde yapılan değişiklikler genellikle bağımsız olarak gerçekleşir. Testleri bu şekilde farklı açılardan ayırarak, gereksinimler değiştiğinde testleri güncellemeyi daha kolay hale getirebilirsiniz.

  - Geliştirme planı, bir önceki kullanım durumunun bir yönünü daha önce uygularsa, geliştirme ilerledikçe testleri ayrı olarak etkinleştirebilirsiniz.

- Testleri tasarlarken, sonkoşulun gerçekleştirilip gerçekleştirilmediğini belirleyen koddan veya betikten test verilerinin seçimini ayırın. Örneğin, basit bir aritmetik işlevin testi şu şekilde olabilir: giriş 4; çıkışın 2 olduğunu doğrulayın. Bunun yerine betiği şu şekilde tasarlayın: bir giriş seçin; çıktıyı kendisiyle çarpın ve sonucun özgün giriş olduğunu doğrulayın. Bu stil, testin ana gövdesini değiştirmeden test girişlerinin değiştirilmesini sağlar.

#### <a name="linking-tests-to-use-cases"></a>Testleri kullanım örneklerine bağlama
 [!INCLUDE[TCMlong](../includes/tcmlong-md.md)]Testlerinizi tasarlamak ve çalıştırmak için kullanıyorsanız, testlerinizi gereksinim, kullanım durumu veya Kullanıcı hikayesi iş öğeleri altında düzenleyebilirsiniz. Bu iş öğelerini modelinizdeki kullanım taleplerine bağlayabilirsiniz. Bu, testlerin gereksinim değişikliklerini hızlıca izlemenizi sağlar ve her kullanım örneğinin ilerlemesini izlemenize yardımcı olur.

###### <a name="to-link-tests-to-a-use-case"></a>Testleri kullanım örneğine bağlamak için

1. İçinde [!INCLUDE[TCMlong](../includes/tcmlong-md.md)] , bir gereksinim oluşturun ve üzerinde bir test paketi temel alır. Bunun nasıl yapılacağını öğrenmek için bkz. [uygulamayı test etme](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac).

    Oluşturduğunuz gereksinim içindeki bir iş öğesidir [!INCLUDE[vstsTfsShort](../includes/vststfsshort-md.md)] . Projenizin kullandığı işlem şablonuna bağlı olarak, bir kullanıcı hikayesi, gereksinim veya kullanım örneği iş öğesi olabilir [!INCLUDE[esprfound](../includes/esprfound-md.md)] . Daha fazla bilgi için bkz. [Visual Studio Team Services veya Team Foundation Server kullanarak Işi izleme](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).

2. Gereksinim iş öğesini modelinizdeki bir veya daha fazla kullanım durumuna bağlayın.

    Kullanım durumu diyagramında, bir kullanım örneğine sağ tıklayın ve sonra **Iş öğesine bağla**' ya tıklayın. Daha fazla bilgi için bkz. [model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md).

3. Test paketine, kullanım durumlarını doğrulayan test çalışmalarına ekleyin.

   Genellikle, her kullanıcı hikayesi veya gereksinim çalışma öğesi modelinizdeki birkaç kullanım örneğine bağlanır ve her kullanım örneği, birkaç kullanıcı hikayesine veya gereksinimine bağlanır. Bunun nedeni, her kullanıcı hikayesi veya gereksinimi çeşitli kullanım durumları geliştiren bir görev kümesini kapsamadır. Örneğin, projenizin erken tekrarında, bir müşterinin bir katalogdan öğe seçebileceği ve teslim edileceği temel kullanıcı hikayesini geliştirebilirsiniz. Daha sonraki bir yinelemede hikaye, kullanıcının siparişi tamamlarken ödeme yaptığı ve tedarikçinin malları gönderdikten sonra para aldığı para ile ilgili olduğunu gösterebilir.  Her hikaye, malların kullanım durumunun sonkoşulun sonuna bir yan tümce ekler.

   Kullanım durumu diyagramında ayrı açıklamalarda bu yan tümceleri yazarak, gereksinimlerden sonkoşulun yan tümcelerine ayrı bağlantılar oluşturabilirsiniz. Her yorumu bir gereksinim iş öğesine bağlayabilir ve yorumu diyagramdaki kullanım örneğine bağlayabilirsiniz.

### <a name="base-tests-on-the-requirements-types"></a>Gereksinim türlerinde temel testler
 Gereksinimler modelinin sınıfları, arabirimleri ve numaralandırmalar, kullanıcıların işletmeyle ilgili olarak nasıl düşündüğünü ve iletişim kurduğunu betimleyen kavramları ve ilişkileri açıklamaktadır. Yalnızca sistemin dahili tasarımıyla ilgili türleri dışlar.

 Testlerinizi bu gereksinim türleri açısından tasarlayın. Bu uygulama, gereksinimlerdeki değişikliklerin tartışıldığı durumlarda, değişiklikleri sınamalarda gerekli değişikliklerle ilişkilendirmek çok kolay olur. Testleri ve amaçlanan sonuçları doğrudan son kullanıcılarla ve diğer hissedarlarla tartışmak mümkün kılar. Bu, kullanıcıların ihtiyaçlarını geliştirme süreci dışında korunabilir ve tasarımda olası kusurların yanlışlıkla tasarımını önler.

 El ile testler için, bu uygulama test betiklerinde gereksinimler modelinin sözlüğüne bağlama ile ilgilidir. Otomatikleştirilmiş testler için, bu uygulama, gereksinimler sınıfı diyagramlarını test kodunuzun temeli olarak kullanmayı ve gereksinim modelini koda bağlamak için erişimci ve Güncelleştirici işlevleri oluşturmayı içerir.

 Örneğin, bir gereksinim modeli, aralarında türler menüsü, menü öğesi, düzen ve ilişkilendirmeler içerebilir. Bu model, yemek siparişi sistemi tarafından depolanan ve ele gelen ve uygulamanın karmaşıklıklarını temsil eden bilgileri temsil eder. Çalışma sisteminde, veritabanlarında, kullanıcı arabirimlerinde ve API 'lerde bulunan her bir türün birkaç farklı Reali olabilir. Dağıtılmış bir sistemde, aynı anda sistemin farklı bölümlerinde depolanan her bir örneğin birkaç varyantı olabilir.

 Öğe ekleme gibi bir kullanım durumunu test etmek için bir test yöntemi şuna benzer bir kod içerebilir:

```
Order order = … ; // set up an order
// Store prior state:
int countBefore = order.MenuItems.Count;
// Perform use case:
MenuItem chosenItem = …; // choose an item
AddItemToOrder (chosenItem, order);
// Verify part of postcondition:
int countAfter = order.MenuItems.Count;
Assert (countAfter == countBefore = 1);
```

 Bu test yönteminin, gereksinimler modelinin sınıflarını kullandığına dikkat edin. İlişkilendirmeler ve öznitelikler .NET özellikleri olarak gerçekleştirilir.

 Bu işi yapmak için sınıfların özelliklerinin geçerli durumu hakkında bilgi almak üzere sisteme erişen salt okuma işlevleri veya erişimcileri olarak tanımlanması gerekir. AddItemToOrder gibi kullanım örneklerinin benzetimini yapan Yöntemler, sistemi API 'siyle veya Kullanıcı arabiriminin altındaki bir katmanda kullanmalıdır. Order ve MenuItem gibi test nesnelerinin oluşturucuları, sistem içinde karşılık gelen öğeleri oluşturmak için de sistemi de sağlamalıdır.

 Çoğu erişimci ve güncelleştiriciler, uygulamanın normal API 'SI aracılığıyla zaten kullanılabilir olacaktır. Ancak testlerin etkinleştirilmesi için bazı ek işlevlerin yazılması gerekebilir. Bu ek erişimciler ve güncelleştiriciler bazen ' test izleme ' olarak bilinir. Sistemin dahili tasarımına bağlı olduğundan, bu, sistemin geliştiricilerin bunları sağlama sorumluluğunda olduğundan, test ediciler, gereksinimler modeli açısından testlerin kodunu yazar.

 Otomatikleştirilmiş testler yazdığınızda, erişimcileri ve güncelleştiricileri kaydırmak için genel testleri kullanabilirsiniz. Daha fazla bilgi için bkz. [Genel testler kullanarak yürütülebilir bir dosya çalıştıran otomatikleştirilmiş test oluşturma](https://msdn.microsoft.com/library/b8dadaf4-4473-49c5-a0d9-46eca9e65d52).

### <a name="tests-for-business-rules"></a>Iş kuralları için testler
 Bazı gereksinimler, herhangi bir kullanım durumuyla doğrudan ilgili değildir. Örneğin, DinnerNow Business müşterilerin birçok menü arasından seçim yapmasına olanak tanır, ancak her sırada tüm seçili öğelerin tek bir menüden olması gerekir. Bu iş kuralı, gereksinimler sınıf modelindeki siparişler, menüler ve öğeler arasındaki ilişkilendirmeler hakkında bir sabit olarak ifade edilebilir.

 Bu türden sabit bir kural, şu anda tanımlanmış olan tüm kullanım örneklerini değil, daha sonra tanımlanacak diğer kullanım örneklerini de yönetir. Bu nedenle, herhangi bir kullanım durumundan ayrı olarak yazmak ve kullanım çalışmalarından ayrı olarak test etmek yararlı olur.

 Sabit bir iş kuralını, bir sınıf diyagramında yorum olarak yazabilirsiniz. Daha fazla bilgi için bkz. [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md).

 Yorumu bir gereksinim veya Kullanıcı hikayesi iş öğesine bağlayarak, içindeki bir test paketine bağlayabileceğiniz bir iş kuralına test bağlayabilirsiniz [!INCLUDE[TCMlong](../includes/tcmlong-md.md)] . Daha fazla bilgi için bkz. [model öğelerine test durumları ekleme](#Attaching).

 Kullanım örneği, etkinlik veya sıralı diyagramlar hakkındaki açıklamalarda performans ve diğer hizmet gereksinimlerinin kalitesi de belirtilecektir. Bunları, gereksinimler iş öğeleri ve onların test paketleri için de bağlayabilirsiniz.

### <a name="sequence-and-activity-diagrams-for-tests"></a>Testler için dizi ve etkinlik diyagramları
 Gereksinimleriniz veya mimari modelleriniz sıra veya etkinlik diyagramları içeriyorsa, diyagramları doğrudan izleyen testler yazabilirsiniz.

 Bazen diyagramdaki dallar ve döngüler aracılığıyla farklı yolları dinamik olarak seçme testleri tasarlamak yararlı olur.

 Her ileti veya eylemden sonra sistemin durumunu doğrulamaya çalışın. Bu, ek izleme gerektirebilir.

## <a name="deriving-subsystem-tests-from-models"></a>Modellerden alt sistem testleri türetme
 Büyük bir sistemin üst düzey tasarımında bileşenleri veya alt sistemleri tanımlayabilirsiniz. Bunlar, ayrı olarak tasarlanan veya farklı bilgisayarlarda bulunan veya birçok şekilde yeniden birleştirilebilen yeniden kullanılabilir modüllerden oluşan parçaları temsil eder. Daha fazla bilgi için bkz. [UML Bileşen diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md).

 Her bir ana bileşene, tüm sistem için kullandığınız ilkeler için de uygulayabilirsiniz. Büyük bir projede, her bileşen kendi Gereksinimler modeline sahip olabilir. Daha küçük projelerde, büyük bileşenleri ve bunların etkileşimlerini göstermek için bir mimari model veya üst düzey tasarım oluşturulabilir. Daha fazla bilgi için bkz. [uygulamanızın mimarisini modelleme](../modeling/model-your-app-s-architecture.md).

 Her iki durumda da, model öğeleri ile alt sistem testleri arasında, gereksinim modeli ve sistem testleri arasında yaptığınız şekilde aynı şekilde bir ilişki oluşturabilirsiniz.

### <a name="isolate-components-with-provided-and-required-interfaces"></a>Bileşenleri, belirtilen ve gerekli arabirimlere ayır
 Bir bileşenin sisteminizin veya dış hizmetlerinizin diğer bölümlerine sahip olduğu tüm bağımlılıkları belirlemek ve bunları gerekli arabirimler olarak göstermek yararlıdır. Bu alıştırma genellikle, tasarımın geri kalanından çok daha fazla ayrılmış ve kolayca ayrılabilir bir şekilde yeniden tasarlamasına yol açar.

 Bu ayrılma avantajı, bileşenin genellikle kullandığı hizmetlerin sahte nesneleriyle değiştirilerek test için yürütülemeidir. Bunlar, test amaçları için ayarlanan bileşenlerdir. Bir sahte bileşen, bileşeninizin gerektirdiği arabirimi sağlar ve bunları benzetimli verilerle sorgular. Sahte bileşenler, bileşenin tüm arabirimlerine bağlanabilmiş olan bir bütün test bandı parçasını oluşturur.

 Sahte testin bir avantajı, bileşeninizin kullanacağı diğer bileşenler hala geliştirme aşamasında olduğundan, bileşenlerinizi geliştirebileceğiniz bir avantajdır.

## <a name="maintain-the-relationships-between-tests-and-model"></a>Testler ve model arasındaki Ilişkileri koruma
 Birkaç haftada bir yineleme gerçekleştiren tipik bir projede, gereksinim incelemesi her yinelemenin başlangıcında yakınında tutulur. Toplantıda bir sonraki yinelemede teslim edilecek özellikler ele alınmaktadır. Gereksinimler modeli, geliştirilecek eylem kavramlarını, senaryoları ve işlem dizilerini tartışmak için kullanılabilir. İş hissedarları öncelikleri, geliştiriciler tahminleri yapar ve test ediciler her bir özelliğin beklenen davranışının doğru yakalandığından emin olur.

 Sınama yazma, bir gereksinimi tanımlamanın en etkili yoludur ve ayrıca bir kişinin gerekli olanları anlayacağından emin olmanın etkili bir yoludur. Ancak, bir belirtim atölyesi sırasında testlerin yazılması çok uzun sürer, model oluşturma işlemi çok daha hızlı bir şekilde yapılabilir.

 Bir test noktasından, gereksinimler modeli testler için bir toplu değer olarak görülebilir. Bu nedenle, proje genelinde testler ve modeller arasındaki ilişkinin korunması önemlidir.

## <a name="attaching-test-cases-to-model-elements"></a><a name="Attaching"></a> Model öğelerine test durumları iliştirme
 Projeniz kullanıyorsa [!INCLUDE[TCMlong](../includes/tcmlong-md.md)] , testlerinizi modelinizdeki öğelere bağlayabilirsiniz. Bu, gereksinimlerdeki bir değişiklikten etkilenen testleri hızlı bir şekilde bulmanıza olanak sağlar ve bir gereksinimin gerçekleştirilme kapsamını izlemenize yardımcı olur.

 Testleri tüm öğe türlerine bağlayabilirsiniz. İşte bazı örnekler:

- Kullanım örneğini, onu uygulayan testlere bağlayın.

- Kullanım örneği sonkoşulun yan tümcesini veya hedefini, kullanım örneğine bağlı açıklamaların üzerine yazın ve ardından her açıklamaya test bağlayın.

- Sınıf diyagramlarındaki veya Etkinlik diyagramlarındaki açıklamalarda sabit kurallar yazın ve bunları testlerle ilişkilendirin.

- Testleri bir etkinlik diyagramına veya tek tek etkinliklere bağlayın.

- Bir test paketini bileşene bağlayın veya sınar.

#### <a name="to-link-tests-to-a-model-element-or-relationship"></a>Testleri model öğesine veya ilişkiye bağlamak için

1. İçinde [!INCLUDE[TCMlong](../includes/tcmlong-md.md)] , bir gereksinim oluşturun ve üzerinde bir test paketi temel alır. Bunun nasıl yapılacağını öğrenmek için bkz. [uygulamayı test etme](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac).

     Oluşturduğunuz gereksinim içindeki bir iş öğesidir [!INCLUDE[vstsTfsShort](../includes/vststfsshort-md.md)] . Projenizin kullandığı işlem şablonuna bağlı olarak, bir kullanıcı hikayesi, gereksinim veya kullanım örneği iş öğesi olabilir [!INCLUDE[esprfound](../includes/esprfound-md.md)] . Daha fazla bilgi için bkz. [Visual Studio Team Services veya Team Foundation Server kullanarak Işi izleme](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503).

2. Gereksinim iş öğesini modelinizdeki bir veya daha fazla öğeye bağlayın.

     Modelleme diyagramında bir öğeye, açıklamaya veya ilişkiye sağ tıklayın ve sonra **Iş öğesine bağla**' ya tıklayın. Daha fazla bilgi için bkz. [model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md).

3. Test paketine, model öğesinde ifade edilen gereksinimi doğrulayan test çalışmalarına ekleyin.

## <a name="see-also"></a>Ayrıca Bkz.
 Uygulama modeliniz [için modeller oluşturma](../modeling/create-models-for-your-app.md) [Kullanıcı gereksinimleri](../modeling/model-user-requirements.md) [modeli uygulamanızın mimari](../modeling/model-your-app-s-architecture.md) [Analizi ve modelleme mimarisi](../modeling/analyze-and-model-your-architecture.md)
