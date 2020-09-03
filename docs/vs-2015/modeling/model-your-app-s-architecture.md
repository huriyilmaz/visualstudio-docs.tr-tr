---
title: Uygulamanızın mimarisini&#39;modelleyin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
ms.assetid: aedce746-9df5-49e1-9662-67eb1b83d313
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41dbb7b996c32af10010694935cbd3660b462f73
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609646"
---
# <a name="model-your-app39s-architecture"></a>Uygulamanızın mimarisini modelleme&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yazılım sisteminizin veya uygulamanızın kullanıcılarınızın ihtiyaçlarını karşıladığından emin olmak için, yazılım sisteminizin veya uygulamanızın genel yapısı ve davranışı açıklamasının bir parçası olarak Visual Studio 'da modeller oluşturabilirsiniz. Modelleri kullanarak, tasarımın tamamında kullanılan desenleri de tanımlayabilirsiniz. Bu modeller mevcut mimariyi anlamanıza, değişiklikleri tartışmanıza ve amaclarınızı açık bir şekilde iletmanıza yardımcı olur.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Bir modelin amacı, doğal dil açıklamalarında gerçekleşen belirsizlikleri azaltmaktır ve tasarımı görselleştirmenize ve alternatif tasarımları tartışmanıza yardımcı olur. Model diğer belge veya tartışmalarla birlikte kullanılmalıdır. Tek başına bir model, mimarinin tamamen bir belirtimini temsil etmez.

> [!NOTE]
> Bu konuda, "sistem", geliştirmekte olduğunuz yazılımı gösterir. Birçok yazılım ve donanım bileşeni ya da tek bir uygulama ya da bir uygulamanın bir parçası olan büyük bir koleksiyon olabilir.

 Bir sistemin mimarisi iki alana ayrılabilir:

- [Üst düzey tasarım](#Structure). Bu, önemli bileşenleri ve bunların her gereksinimi karşılamak için birbirleriyle nasıl etkileşime gireceğini açıklar. Sistem büyükse, her bileşenin daha küçük bileşenlerden nasıl oluştuğunu gösteren kendi üst düzey tasarımı olabilir.

- Bileşenlerin tasarımları boyunca kullanılan [tasarım desenleri](#Patterns) ve kuralları. Bir model, programlama hedefini elde etmeye yönelik belirli bir yaklaşımı açıklar. Tasarımın tamamında aynı desenleri kullanarak ekibiniz, değişiklik yapma ve yeni yazılım geliştirme maliyetini azaltabilir.

## <a name="high-level-design"></a><a name="Structure"></a> Üst düzey tasarım
 Üst düzey bir tasarım, sisteminizin ana bileşenlerini ve tasarımın hedeflerine ulaşmak için birbirleriyle nasıl etkileşime gireceğini açıklar. Aşağıdaki listede yer alan etkinlikler, belirli bir dizide olması gerekmese de, üst düzey tasarımı geliştirmeye dahil edilir.

 Mevcut kodu güncelleştiriyorsanız, ana bileşenleri açıklayarak başlayabilirsiniz. Kullanıcı gereksinimlerinde yapılan tüm değişiklikleri anladığınızdan emin olun ve ardından bileşenler arasındaki etkileşimleri ekleyin veya değiştirin. Yeni bir sistem geliştiriyorsanız, kullanıcı gereksinimlerinin ana özelliklerini anlamak için ' ı başlatın. Daha sonra ana kullanım örnekleri için etkileşim dizilerini keşfedebilirsiniz ve sonra dizileri bir bileşen tasarımında birleştirebilirsiniz.

 Her durumda, farklı etkinliklerin paralel olarak geliştirilmesi ve erken bir aşamada kod ve testler geliştirilmesi yararlı olur. Bir başkasına başlamadan önce bu yönlerden birini tamamlamaya çalışmaktan kaçının. Genellikle, hem gereksinimler hem de sistemi tasarlamak için en iyi yöntem, kodu yazarken ve test edilirken değişir. Bu nedenle, gereksinimlerin ve tasarımınızın ana özelliklerini anlamak ve kodlayarak başlamanız gerekir. Ayrıntıları projenin sonraki yinelemeleriyle doldurur.

- [Gereksinimleri anlama](#Requirements). Herhangi bir tasarımın başlangıç noktası, kullanıcıların ihtiyaçlarını net bir şekilde anlayabiliyor.

- [Mimari desenler](#BigDecisions). Sistemin temel teknolojileri ve mimari öğeleri hakkında yaptığınız seçimler.

- [Bileşenler ve arabirimleri](#Components). Sistemin başlıca parçalarını göstermek için Bileşen diyagramları çizebilir ve üzerinden etkileşimde bulundukları arabirimleri gösterebilirsiniz. Her bileşenin arabirimleri, sıralı diyagramlarda tanımladığınız tüm iletileri içerir.

- [Bileşenler arasındaki etkileşimler](#Interactions). Her kullanım örneği, olay veya gelen ileti için, sistemin ana bileşenlerinin gerekli yanıtı elde etmek üzere nasıl etkileşime gireceğini gösteren bir sıra diyagramı çizebilirsiniz.

- [Bileşenlerin ve arabirimlerin veri modeli](#Data). Bileşenler arasında geçirilen ve bileşenlerin içinde depolanan bilgileri anlatmak için sınıf diyagramları çizebilirsiniz.

## <a name="understanding-the-requirements"></a><a name="Requirements"></a> Gereksinimleri anlama
 Tam bir uygulamanın üst düzey tasarımı, bir gereksinim modeli veya kullanıcı gereksinimlerinin diğer açıklamasıyla birlikte en etkili şekilde geliştirilmiştir. Gereksinim modelleri hakkında daha fazla bilgi için bkz. [model Kullanıcı gereksinimleri](../modeling/model-user-requirements.md).

 Geliştirmekte olduğunuz sistem daha büyük bir sistemdeki bir bileşen ise, gereksinimlerinizin bir kısmı veya tümü programlı arabirimlerde bulunabilir.

 Gereksinimler modeli bu önemli bilgi parçalarını sağlar:

- Sunulan arabirimler. Bir belirtilen arabirim, kullanıcıların veya bileşenin kullanıcılarına sağlaması gereken hizmet veya işlemleri, insan kullanıcıları veya diğer yazılım bileşenleri olup olmadıkları şekilde listeler.

- Gerekli arabirimler. Gerekli bir arabirim, sistem veya bileşenin kullanabileceği Hizmetleri veya işlemleri listeler. Bazı durumlarda, tüm bu hizmetleri kendi sisteminizin bir parçası olarak tasarlayacaksınız. Diğer durumlarda, özellikle de birçok yapılandırmada diğer bileşenlerle birleştirilebilecek bir bileşen tasarlıyorsanız, gerekli arabirim dış hususlar tarafından ayarlanır.

- Hizmet kalitesi gereksinimleri. Sistemin uyması gereken performans, güvenlik, sağlamlık ve diğer hedefler ve kısıtlamalar.

  Gereksinimler modeli, ister kişiler, ister diğer yazılım bileşenleri olsun, sistem kullanıcılarınızın görünüm noktasından yazılır. Bunlar, sisteminizin iç işleyişini hiç bir şey bilmez. Buna karşılık, bir mimari modelde hedefiniz iç işleyişi ve kullanıcıların ihtiyaçlarını nasıl karşıladığını gösterir.

  Gereksinimler ve mimari modellerin ayrı tutulması yararlı olduğundan, gereksinimleri kullanıcılarla tartışmak daha kolay hale gelir. Ayrıca, tasarımı yeniden düzenlemenize ve gereksinimleri değişmeden tutarken alternatif mimarilere göz önünde bulundurmanıza de yardımcı olur.

  Gereksinimleri ve mimari modelleri iki alternatif şekilde ayırabilirsiniz:

- Aynı çözümde, ancak farklı projelerde saklayın. UML Model Gezgini 'nde ayrı modeller olarak görünürler. Farklı takım üyeleri modeller üzerinde paralel olarak çalışabilir. Modeller arasında sınırlı sayıda izleme oluşturulabilir.

- Bunları aynı UML modeline, ancak farklı paketlere koyun. Bu, modeller arasındaki bağımlılıkları izlemeyi kolaylaştırır, ancak bir seferde birden fazla kişinin model üzerinde çalışmasını önler. Ayrıca, çok büyük bir modelin Visual Studio 'ya yüklenmesi daha uzun sürer. Bu yaklaşım bu nedenle büyük projeler için daha az uygundur.

  Bir gereksinimlere veya mimari modele yerleştirmeniz gereken ayrıntı miktarı projenin ölçeğine ve takımın boyutuna ve dağıtımına bağlıdır. Kısa bir proje üzerinde küçük bir ekip, iş kavramlarının ve bazı Tasarım desenlerinin bir sınıf diyagramına göre taslağı oluşturma özelliğinden daha fazla çalışmayabilir; birden fazla bölgeye dağıtılmış büyük bir proje, önemli ölçüde daha ayrıntılı olmalıdır.

## <a name="architectural-patterns"></a><a name="BigDecisions"></a> Mimari Desenler
 Geliştirmede erken olarak, tasarımın bağlı olduğu ana teknolojileri ve öğeleri seçmeniz gerekir. Bu seçimlerin yapılması gereken alanlara aşağıdakiler dahildir:

- Bir veritabanı ve dosya sistemi arasındaki seçim ve ağa bağlı bir uygulama ile Web istemcisi arasındaki seçim gibi temel teknoloji seçimleri.

- Windows Workflow Foundation veya ADO.NET Entity Framework arasında seçim gibi çerçeveler seçimleri.

- Tümleştirme yöntemi seçimleri, örneğin bir kurumsal hizmet veri yolu veya noktadan noktaya kanal.

  Bu seçimler sıklıkla ölçek ve esneklik gibi hizmet gereksinimlerinin kalitesi tarafından belirlenir ve ayrıntılı gereksinimler bilinerek yapılabilir. Büyük bir sistemde, donanım ve yazılım yapılandırması kesinlikle birbirleriyle ilişkilidir.

  Yaptığınız seçimler, mimari modeli nasıl kullanacağınızı ve yorumlayacağını etkiler. Örneğin, bir veritabanı kullanan bir sistemde, bir sınıf diyagramındaki ilişkilendirmeler, veritabanındaki ilişkileri veya yabancı anahtarları temsil edebilir, ancak XML dosyalarını temel alan bir sistemde, ilişkilendirmeler XPath kullanan çapraz başvuruları belirtebilir. Dağıtılmış bir sistemde, Sıralı diyagramdaki iletiler bir hattaki iletileri temsil edebilir; kendi içinde bulunan bir uygulamada, işlev çağrılarını temsil edebilirler.

## <a name="components-and-their-interfaces"></a><a name="Components"></a> Bileşenler ve arabirimleri
 Bu bölümün başlıca önerileri aşağıdaki gibidir:

- Sisteminizin ana parçalarını göstermek için Bileşen diyagramları oluşturun.

- Sistemin yapısını göstermek için bileşenler veya arabirimleri arasında bağımlılıklar çizin.

- Her bileşenin sağladığı veya gerektirdiği hizmetleri göstermek için bileşenlerde arabirimler kullanın.

- Büyük bir tasarımda, her bileşeni daha küçük parçalara ayırmak için ayrı diyagramlar çizebilirsiniz.

  Bu noktalara bu bölümün geri kalanında ayrıntılı.

### <a name="components"></a>Bileşenler
 Mimari modelinin Merkezi görünümleri, sistemin başlıca parçalarını ve bunların birbirine nasıl bağlı olduğunu gösteren bileşen diyagramlardır. Bileşen diyagramları hakkında daha fazla bilgi için bkz. [UML Bileşen diyagramları: başvuru](../modeling/uml-component-diagrams-reference.md).

 ![Bölümleri gösteren UML bileşen diyagramı](../modeling/media/uml-barecomponent.png "UML_BareComponent")

 Büyük bir sistem için tipik bir bileşen diyagramı, şunlar gibi bileşenler içerebilir:

- Sununuzda. Genellikle bir Web tarayıcısında çalışan, kullanıcıya erişim sağlayan bileşen.

- Web hizmeti bileşenleri. İstemciler ve sunucular arasında bağlantı sağlar.

- Kullanım örneği denetleyicileri. Her senaryonun adımlarında Kullanıcı gerçekleştirin.

- İş çekirdeği. Gereksinimler modelindeki sınıflara dayalı sınıfları içerir, önemli işlemleri uygular ve iş kısıtlamalarını uygular.

- Veritabanınızı. İş nesnelerini depolar.

- Günlüğe kaydetme ve hata işleme bileşenleri.

### <a name="dependencies-between-components"></a>Bileşenler arasındaki bağımlılıklar
 Bileşenlerin kendilerine ek olarak, aralarındaki bağımlılıkları gösterebilirsiniz. İki bileşen arasındaki bağımlılık oku, bir birinin tasarımındaki değişikliklerin diğerinin tasarımını etkileyebileceğini gösterir. Bu genellikle bir bileşen, diğer bileşen tarafından doğrudan veya dolaylı olarak sağlanmış olan hizmetleri veya işlevleri kullandığında meydana gelir.

 İyi yapılandırılmış bir mimaride, bu koşulların doğru olduğu açık bir bağımlılık düzenlemesi vardır:

- Kod eşlemesinde hiç döngü yok.

- Bileşenler, her bağımlılığın bir katmandaki bileşenden bir sonraki bir bileşene ulaştığı katmanlara düzenlenebilir. İki katman arasındaki tüm bağımlılıklar aynı yönde gider.

  Bağımlılıkları doğrudan bileşenler arasında gösterebilir veya bileşenlere iliştirilmiş gerekli ve sağlanmış arabirimler arasındaki bağımlılıkları gösterebilirsiniz. Arabirimleri kullanarak her bir bağımlılık için hangi işlemlerin kullanıldığını tanımlayabilirsiniz. Genellikle, diyagramlar ilk çizildiğinde bileşenler arasında bağımlılıklar gösterilir ve daha fazla bilgi eklendikçe arabirimler arasındaki bağımlılıklarla değiştirilmez. Her iki sürüm de yazılımın doğru açıklamalarıdır, ancak arabirimleri olan sürüm önceki sürümden daha fazla ayrıntı sağlar.

  Bağımlılıkları yönetmek, sürdürülebilir yazılımın üretimi için en önemdir. Bileşen diyagramları, kodunuzdaki tüm bağımlılıkları yansıtmalıdır. Kod zaten varsa, tüm bağımlılıkların diyagramlarda gösterildiğinden emin olun. Kod geliştiriliyorsa, bileşen diyagramında planlanmayan bağımlılıkları içermediğinden emin olun. Koddaki bağımlılıkları keşfetmenize yardımcı olması için katman diyagramları oluşturabilirsiniz. Planlı bağımlılık kısıtlamalarınızın karşılandığından emin olmanıza yardımcı olması için kodu katman diyagramlarına karşı doğrulayabilirsiniz. Daha fazla bilgi için bkz. [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md).

### <a name="interfaces"></a>Arabirimler
 Bileşenlerinizde arabirimler yerleştirerek her bir bileşen tarafından sunulan birincil işlem gruplarını ayırabilirsiniz ve ad verebilirsiniz. Örneğin, Web tabanlı bir satış sistemindeki bileşenler, müşterilerin mal satın aldığı bir arabirime, sağlayıcılarının kataloglarını güncelleştiren bir arabirime ve sistemin yönetildiği üçüncü bir arabirime sahip olabilir.

 Bir bileşen herhangi bir sayıda sağlanmış ve gerekli arabirime sahip olabilir. Sağlanan arabirimler, bileşenin diğer bileşenlerin kullanması için sağladığı Hizmetleri gösterir. Gerekli arabirimler, bileşenin diğer bileşenlerde kullandığı hizmetleri gösterir.

 Hem sağlanmış hem de gerekli arabirimleri tanımlarsanız, bu, bu teknikleri kullanabilmeniz için bileşeni tasarımın geri kalanından düzgün bir şekilde ayırmanıza yardımcı olur:

- Bileşeni, çevreleyen bileşenlerin test bandı tarafından benzetilen bir test bandı içine yerleştirin.

- Bileşeninizi diğer bileşenlerden bağımsız olarak geliştirin.

- Arabirimlerini farklı bileşenlere bağlayana diğer bağlamlarda bileşeni yeniden kullanın.

  Bir arabirimdeki işlemlerin listesini tanımlamak istediğinizde, bir UML sınıf diyagramında arabirimin başka bir görünümünü de oluşturabilirsiniz. Bunu yapmak için UML Model Gezgini ' nde arabirimi bulun ve bir sınıf diyagramına sürükleyin. Daha sonra arabirime işlem ekleyebilirsiniz.

  UML arabirimindeki bir işlem, bir bileşenin davranışının çağrılabileceği herhangi bir yolu temsil edebilir. Bir Web hizmeti isteğini, başka bir türdeki bir sinyali veya etkileşimi veya sıradan bir program işlevi çağrısını temsil edebilir.

  Hangi işlemlerin ekleneceğini belirlemek için, bileşenlerin birbirleriyle nasıl etkileşime gireceğini göstermek üzere sıralı diyagramlar oluşturun. [Bileşenler arasındaki etkileşimleri](#Interactions)inceleyin. Bu sıralı diyagramların her biri, farklı bir kullanım durumunda gerçekleşen etkileşimleri gösterir. Bu şekilde, kullanım örneklerini keşfederken, her bileşenin arabirimindeki işlemler listesine aşamalı olarak ekleyebilirsiniz.

### <a name="decomposing-a-component-into-parts"></a>Bir bileşeni parçalar halinde kaldırma
 Yukarıdaki bölümlerde açıklanan yordamı her bir bileşene uygulayabilirsiniz.

 Her bir bileşen içinde alt bileşenlerini parçalar halinde gösterebilirsiniz. Bir bölüm, bir sınıf türü olan üst bileşeninin etkin bir özniteliğidir. Her parçanın kendi türü vardır ve bu bir bileşen olabilir. Bu bileşeni bir diyagrama yerleştirebilir ve parçalarını gösterebilirsiniz. Daha fazla bilgi için bkz. [UML Bileşen diyagramları: yönergeler](../modeling/uml-component-diagrams-guidelines.md).

 Bu tekniği tüm sisteme uygulamak yararlı olur. Tek bir bileşen olarak çizin ve ana bileşenlerini parçalar halinde görüntüleyin. Bu, dışarıdaki dünya ile sisteminizin arabirimlerini açıkça belirlemenize yardımcı olur.

 Bir bileşen için tasarımınız başka bir bileşen kullandığında, genellikle onu bir parça olarak temsil etmeme veya bir arabirim gerektirir.

 Aşağıdaki durumlarda bölümler kullanın:

- Ana bileşenin tasarımının her zaman bölümün bileşen türünü kullanması gerekir. Bu nedenle, parçanın tasarımı üst bileşenin tasarımına göre tam olarak kullanılır.

- Üst bileşen kendi kendine ait somut bir varlığına sahip değildir. Örneğin, görünümleri ve kullanıcı etkileşimlerini işleyen gerçek bileşenlerin bir koleksiyonunu temsil eden sunum katmanı adlı kavramsal bir bileşeniniz olabilir.

  Bu durumlarda gerekli arabirimler aracılığıyla erişilen ayrı bileşenleri kullanın:

- Gerekli bileşen, çalışma zamanında çeşitli bileşenlere sahip olan arabirimleri aracılığıyla bağlanabilir.

- Tasarım, bir sağlayıcıyı başka bir sağlayıcıya değiştirmek kolay olacaktır.

  Gerekli arabirimlerin kullanımı genellikle parçaların kullanımı için tercih edilir. Tasarım uzun sürebilse de elde edilen sistem daha esnektir. Ayrıca, bileşenleri ayrı olarak test etmek de daha kolay. Bu, geliştirme planlarında daha az eşlenmeye olanak tanır.

## <a name="interactions-between-components"></a><a name="Interactions"></a> Bileşenler arasındaki etkileşimler
 Bu bölümün başlıca önerileri aşağıdaki gibidir:

- Sisteminizin kullanım durumlarını belirler.

- Her kullanım örneği için, sisteminizin bileşenlerinin birbirleriyle ve kullanıcılarla işbirliği yaparak gerekli sonucu nasıl elde etmelerini göstermek için bir veya daha fazla diyagram çizin. Genellikle bunlar sıralı diyagramlar veya etkinlik diyagramlardır.

- Her bileşen tarafından alınan iletileri belirtmek için arabirimler kullanın.

- Arabirimlerdeki Işlemlerin etkilerini açıkla.

- Her bileşen için, parçalarının nasıl etkileşime gireceğini gösteren yordamı tekrarlayın.

  Örneğin, Web tabanlı bir satış sisteminde, gereksinim modeli bir müşteri satın alımını kullanım örneği olarak tanımlayabilir. Müşterinin sunum katmanındaki bileşenlere sahip olduğu etkileşimleri göstermek ve ambar ve muhasebe bileşenleriyle sahip oldukları etkileşimleri göstermek için bir sıralı diyagram oluşturabilirsiniz.

### <a name="identifying-the-initiating-events"></a>Başlatma olaylarını tanımlama
 Çoğu yazılım sistemi tarafından gerçekleştirilen iş, farklı girişlere veya olaylara verdiği yanıtlara göre rahat bir şekilde ayrılabilir. Başlatma olayı aşağıdaki olaylardan biri olabilir:

- Kullanım örneği içindeki ilk eylem. Kullanım durumunda bir adım olarak veya bir etkinlik diyagramındaki bir eylem olarak gereksinimler modelinde görünebilir. Daha fazla bilgi için [UML Kullanım durumu diyagramları: yönergeler](../modeling/uml-use-case-diagrams-guidelines.md) ve [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).

- Programlama arabirimindeki bir ileti. Geliştirmekte olduğunuz sistem daha büyük bir sistemdeki bir bileşen ise, bileşenin arabirimlerinden birinde bir işlem olarak açıklanmalıdır. Bkz. [Bileşenler ve bunların arayüzleri](#Components).

- Sisteminiz tarafından izlenen belirli bir koşul veya günün saati gibi düzenli bir olay.

### <a name="describe-the-computations"></a>Hesaplamaları açıkla
 Bileşenlerin ilk olaya nasıl yanıt vereceğini göstermek için sıralı diyagramlar çizin.

 Tipik bir dizide bölüm alan her bileşen örneği için bir yaşam çizgisi çizin. Bazı durumlarda, her türde birden çok örnek olabilir. Tüm sisteminizi tek bir bileşen olarak açıkdıysanız, içerdiği her bölüm için bir yaşam çizgisi olmalıdır.

 Daha fazla bilgi için bkz. [UML sıralı diyagramlar: yönergeler](../modeling/uml-sequence-diagrams-guidelines.md).

 Etkinlik diyagramları, bazı durumlarda da yararlıdır. Örneğin, bileşenlerinizin sürekli bir veri akışı varsa, bunu bir nesne akışı olarak tanımlayabilirsiniz. Bileşeninizin karmaşık bir algoritması varsa, bunu bir denetim akışı olarak tanımlayabilirsiniz. Örneğin, Yorumları kullanarak, her bir eylemi gerçekleştirdiğinizden emin olun. Daha fazla bilgi için bkz. [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md).

### <a name="specify-the-operations"></a>İşlemleri belirtin
 Diyagramlar, her bileşen tarafından gerçekleştirilen işlemleri, sıralı diyagramda iletiler olarak veya bir etkinlik diyagramında eylemler olarak gösterir.

 Bu işlemleri her bir bileşen için birlikte toplayın. Bileşende sağlanmış arabirimler oluşturun ve işlemleri arayüzlere ekleyin. Genellikle, her istemci türü için ayrı bir arabirim kullanılır. İşlemler **UML Model Gezgini**' nde arabirimlere en kolay şekilde eklenir. Aynı şekilde, her bileşenin diğer bileşenlerden kullandığı işlemleri toplayın ve bileşene iliştirilmiş gerekli arabirimlere yerleştirin.

 Her işlemden sonra ne elde edildiğini aklınızda olmak için etkinlik veya Sıralı diyagramlara yorum eklemek yararlıdır. Her işlemin **Yerel Sonkoşul** özelliğindeki etkisini de yazabilirsiniz.

### <a name="data-model-of-the-components-and-interfaces"></a><a name="Data"></a> Bileşenlerin ve arabirimlerin veri modeli
 Bileşen arabirimlerindeki her bir işlemin parametrelerini ve dönüş değerlerini tanımlayın. İşlemler Web hizmeti istekleri gibi çağırmaları temsil ediyorsa, parametreler isteğin bir parçası olarak gönderilen bu bilgi parçalarından oluşur. Bir işlemden birkaç değer döndürüldüğünde, **Direction** özelliği **Out**olarak ayarlanan parametreleri kullanabilirsiniz.

 Her parametre ve dönüş değeri bir tür içerir. Bu türleri UML sınıf diyagramlarını kullanarak tanımlayabilirsiniz. Bu diyagramlarda uygulama ayrıntılarını temsil etmek zorunda değilsiniz. Örneğin, XML olarak aktarılan verileri açıkladıysanız, XML düğümleri arasında herhangi bir çapraz başvuru türünü temsil etmek için bir ilişkilendirme kullanabilirsiniz ve düğümleri temsil etmek için sınıfları kullanabilirsiniz.

 İlişkilendirmeler ve özniteliklerde iş kısıtlamalarını anlatmak için açıklamaları kullanın. Örneğin, bir müşterinin sırasındaki tüm öğelerin aynı tedarikçiden gelmesi gerekiyorsa, bunu sipariş öğeleri ve ürün kataloğundaki öğeler arasındaki ilişkilendirmelere ve Katalog öğesi ile tedarikçisine göre tanımlayabilirsiniz.

## <a name="design-patterns"></a><a name="Patterns"></a> Tasarım desenleri
 Tasarım düzeni, yazılımın, özellikle de sistemin farklı bölümlerinde yinelenen belirli bir yönün nasıl tasarlanacağını gösteren bir ana hatlarıyla oluşur. Proje genelinde tek bir yaklaşımı benimseerek, tasarımın maliyetini azaltabilir, Kullanıcı arabiriminde tutarlılığı güvence altına alabilir ve kodu anlama ve değiştirme maliyetini azaltabilirsiniz.

 Gözlemci gibi bazı genel tasarım desenleri iyi bilinmektedir ve yaygın olarak uygulanabilir. Ayrıca, yalnızca projeniz için geçerli olan desenler vardır. Örneğin, bir web satış sisteminde, kodda bir müşterinin sırasıyla değişiklikler yapıldığı birkaç işlem olacaktır. Siparişin durumunun her aşamada doğru şekilde görüntülendiğinden emin olmak için, bu işlemlerin veritabanının güncelleştirilmesi için belirli bir protokolü izlemesi gerekir.

 Yazılım mimarisi işinin bir parçası, tasarımın tamamında hangi desenlerin benimsenmesi gerektiğini belirlemektir. Bu genellikle devam eden bir görevdir, çünkü mevcut desenlere yönelik yeni modeller ve iyileştirmeler proje ilerledikçe keşfedilir. Geliştirme planını düzenlemek faydalı olur, böylece ilk aşamada önemli tasarım desenlerinizin her birini gerçekleştirebilirsiniz.

 Çoğu tasarım deseni çerçeve koduna kısmen eklenebilir. Düzenin, veritabanının doğru şekilde işlenmesini sağlayan bir veritabanı erişim katmanı gibi belirli sınıfları veya bileşenleri kullanmasını gerektirecek şekilde, düzenin bir bölümü azaltılabilir.

 Tasarım alanı bir belge içinde tanımlanır ve genellikle şu parçaları içerir:

- Ada.

- Geçerli olduğu bağlamın açıklaması. Bir geliştirici bu düzenin uygulanmasını ne planlıyor?

- Çözdüğü sorunun kısa açıklaması.

- Ana parçaların ve bunların ilişkilerinin modeli. Bunlar arasındaki ilişkilendirmeler ve bağımlılıklarla birlikte sınıflar veya bileşenler ve arabirimler olabilir. Öğeler genellikle iki kategoriye ayrılır:

  - Geliştiricinin, düzenin kullanıldığı kodun her bölümünde çoğaltılması gereken öğeler. Bunları anlatmak için şablon türlerini kullanabilirsiniz. Daha fazla bilgi için bkz. [UML Kullanım örneği diyagramları: başvuru](../modeling/uml-use-case-diagrams-reference.md).

  - Geliştiricinin kullanması gereken çerçeve sınıflarını açıklayan öğeler.

- Sıra veya etkinlik diyagramları kullanılarak parçalar arasındaki etkileşimlerin modeli.

- Adlandırma kuralları.

- Düzenin sorunu nasıl çözdüğü hakkında açıklama.

- Geliştiricilerin benimseyebileceği çeşitlemelerin açıklaması.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modellerini ve diyagramları düzenleme](../modeling/edit-uml-models-and-diagrams.md) [kod](../modeling/visualize-code.md) [modeli Kullanıcı gereksinimlerini](../modeling/model-user-requirements.md) görselleştirme [bir modelden test](../modeling/develop-tests-from-a-model.md) [geliştirme sürecinizdeki modelleri kullanma](../modeling/use-models-in-your-development-process.md)
