---
title: Uygulamanızın&#39;mimarisini modelleyin
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e87759206f6d05267e2be5be25fdb8c3e9b70df
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747533"
---
# <a name="model-your-app39s-architecture"></a>Uygulamanızın&#39;mimarisini modelleyin
Yazılım sisteminizin veya uygulamanızın kullanıcılarınızın ihtiyaçlarını karşıladığından emin olmak için, yazılım sisteminizin veya uygulamanızın genel yapısı ve davranışı açıklamasının bir parçası olarak Visual Studio 'da modeller oluşturabilirsiniz. Modelleri kullanarak, tasarımın tamamında kullanılan desenleri de tanımlayabilirsiniz. Bu modeller mevcut mimariyi anlamanıza, değişiklikleri tartışmanıza ve amaclarınızı açık bir şekilde iletmanıza yardımcı olur.

 Hangi Visual Studio sürümlerini bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Bir modelin amacı, doğal dil açıklamalarında gerçekleşen belirsizlikleri azaltmaktır ve tasarımı görselleştirmenize ve alternatif tasarımları tartışmanıza yardımcı olur. Model diğer belge veya tartışmalarla birlikte kullanılmalıdır. Tek başına bir model, mimarinin tamamen bir belirtimini temsil etmez.

> [!NOTE]
> Bu konuda, "sistem", geliştirmekte olduğunuz yazılımı gösterir. Birçok yazılım ve donanım bileşeni ya da tek bir uygulama ya da bir uygulamanın bir parçası olan büyük bir koleksiyon olabilir.

 Bir sistemin mimarisi iki alana ayrılabilir:

- [Üst düzey tasarım](#Structure). Bu, önemli bileşenleri ve bunların her gereksinimi karşılamak için birbirleriyle nasıl etkileşime gireceğini açıklar. Sistem büyükse, her bileşenin daha küçük bileşenlerden nasıl oluştuğunu gösteren kendi üst düzey tasarımı olabilir.

- Bileşenlerin tasarımları boyunca kullanılan [tasarım desenleri](#Patterns) ve kuralları. Bir model, programlama hedefini elde etmeye yönelik belirli bir yaklaşımı açıklar. Tasarımın tamamında aynı desenleri kullanarak ekibiniz, değişiklik yapma ve yeni yazılım geliştirme maliyetini azaltabilir.

## <a name="Structure"></a>Üst düzey tasarım
 Üst düzey bir tasarım, sisteminizin ana bileşenlerini ve tasarımın hedeflerine ulaşmak için birbirleriyle nasıl etkileşime gireceğini açıklar. Aşağıdaki listede yer alan etkinlikler, belirli bir dizide olması gerekmese de, üst düzey tasarımı geliştirmeye dahil edilir.

 Mevcut kodu güncelleştiriyorsanız, ana bileşenleri açıklayarak başlayabilirsiniz. Kullanıcı gereksinimlerinde yapılan tüm değişiklikleri anladığınızdan emin olun ve ardından bileşenler arasındaki etkileşimleri ekleyin veya değiştirin. Yeni bir sistem geliştiriyorsanız, kullanıcı gereksinimlerinin ana özelliklerini anlamak için ' ı başlatın. Daha sonra ana kullanım örnekleri için etkileşim dizilerini keşfedebilirsiniz ve sonra dizileri bir bileşen tasarımında birleştirebilirsiniz.

 Her durumda, farklı etkinliklerin paralel olarak geliştirilmesi ve erken bir aşamada kod ve testler geliştirilmesi yararlı olur. Bir başkasına başlamadan önce bu yönlerden birini tamamlamaya çalışmaktan kaçının. Genellikle, hem gereksinimler hem de sistemi tasarlamak için en iyi yöntem, kodu yazarken ve test edilirken değişir. Bu nedenle, gereksinimlerin ve tasarımınızın ana özelliklerini anlamak ve kodlayarak başlamanız gerekir. Ayrıntıları projenin sonraki yinelemeleriyle doldurur.

- [Gereksinimleri anlama](#Requirements). Herhangi bir tasarımın başlangıç noktası, kullanıcıların ihtiyaçlarını net bir şekilde anlayabiliyor.

- [Mimari desenler](#BigDecisions). Sistemin temel teknolojileri ve mimari öğeleri hakkında yaptığınız seçimler.

- Bileşenlerin ve arabirimlerin veri modeli. Bileşenler arasında geçirilen ve bileşenlerin içinde depolanan bilgileri anlatmak için sınıf diyagramları çizebilirsiniz.

## <a name="Requirements"></a>Gereksinimleri anlama
 Tam bir uygulamanın üst düzey tasarımı, bir gereksinim modeli veya kullanıcı gereksinimlerinin diğer açıklamasıyla birlikte en etkili şekilde geliştirilmiştir. Gereksinim modelleri hakkında daha fazla bilgi için bkz. [model Kullanıcı gereksinimleri](../modeling/model-user-requirements.md).

 Geliştirmekte olduğunuz sistem daha büyük bir sistemdeki bir bileşen ise, gereksinimlerinizin bir kısmı veya tümü programlı arabirimlerde bulunabilir.

 Gereksinimler modeli bu önemli bilgi parçalarını sağlar:

- Sunulan arabirimler. Bir belirtilen arabirim, kullanıcıların veya bileşenin kullanıcılarına sağlaması gereken hizmet veya işlemleri, insan kullanıcıları veya diğer yazılım bileşenleri olup olmadıkları şekilde listeler.

- Gerekli arabirimler. Gerekli bir arabirim, sistem veya bileşenin kullanabileceği Hizmetleri veya işlemleri listeler. Bazı durumlarda, tüm bu hizmetleri kendi sisteminizin bir parçası olarak tasarlayacaksınız. Diğer durumlarda, özellikle de birçok yapılandırmada diğer bileşenlerle birleştirilebilecek bir bileşen tasarlıyorsanız, gerekli arabirim dış hususlar tarafından ayarlanır.

- Hizmet kalitesi gereksinimleri. Sistemin uyması gereken performans, güvenlik, sağlamlık ve diğer hedefler ve kısıtlamalar.

  Gereksinimler modeli, ister kişiler, ister diğer yazılım bileşenleri olsun, sistem kullanıcılarınızın görünüm noktasından yazılır. Bunlar, sisteminizin iç işleyişini hiç bir şey bilmez. Buna karşılık, bir mimari modelde hedefiniz iç işleyişi ve kullanıcıların ihtiyaçlarını nasıl karşıladığını gösterir.

  Gereksinimler ve mimari modellerin ayrı tutulması yararlı olduğundan, gereksinimleri kullanıcılarla tartışmak daha kolay hale gelir. Ayrıca, tasarımı yeniden düzenlemenize ve gereksinimleri değişmeden tutarken alternatif mimarilere göz önünde bulundurmanıza de yardımcı olur.

  Bir gereksinimlere veya mimari modele yerleştirmeniz gereken ayrıntı miktarı projenin ölçeğine ve takımın boyutuna ve dağıtımına bağlıdır. Kısa bir proje üzerinde küçük bir ekip, iş kavramlarının ve bazı Tasarım desenlerinin bir sınıf diyagramına göre taslağı oluşturma özelliğinden daha fazla çalışmayabilir; birden fazla bölgeye dağıtılmış büyük bir proje, önemli ölçüde daha ayrıntılı olmalıdır.

## <a name="BigDecisions"></a>Mimari Desenler
 Geliştirmede erken olarak, tasarımın bağlı olduğu ana teknolojileri ve öğeleri seçmeniz gerekir. Bu seçimlerin yapılması gereken alanlara aşağıdakiler dahildir:

- Bir veritabanı ve dosya sistemi arasındaki seçim ve ağa bağlı bir uygulama ile Web istemcisi arasındaki seçim gibi temel teknoloji seçimleri.

- Windows Workflow Foundation veya ADO.NET Entity Framework arasında seçim gibi çerçeveler seçimleri.

- Tümleştirme yöntemi seçimleri, örneğin bir kurumsal hizmet veri yolu veya noktadan noktaya kanal.

  Bu seçimler sıklıkla ölçek ve esneklik gibi hizmet gereksinimlerinin kalitesi tarafından belirlenir ve ayrıntılı gereksinimler bilinerek yapılabilir. Büyük bir sistemde, donanım ve yazılım yapılandırması kesinlikle birbirleriyle ilişkilidir.

  Yaptığınız seçimler, mimari modeli nasıl kullanacağınızı ve yorumlayacağını etkiler. Örneğin, bir veritabanı kullanan bir sistemde, bir sınıf diyagramındaki ilişkilendirmeler, veritabanındaki ilişkileri veya yabancı anahtarları temsil edebilir, ancak XML dosyalarını temel alan bir sistemde, ilişkilendirmeler XPath kullanan çapraz başvuruları belirtebilir. Dağıtılmış bir sistemde, Sıralı diyagramdaki iletiler bir hattaki iletileri temsil edebilir; kendi içinde bulunan bir uygulamada, işlev çağrılarını temsil edebilirler.

## <a name="Patterns"></a>Tasarım desenleri
 Tasarım düzeni, yazılımın, özellikle de sistemin farklı bölümlerinde yinelenen belirli bir yönün nasıl tasarlanacağını gösteren bir ana hatlarıyla oluşur. Proje genelinde tek bir yaklaşımı benimseerek, tasarımın maliyetini azaltabilir, Kullanıcı arabiriminde tutarlılığı güvence altına alabilir ve kodu anlama ve değiştirme maliyetini azaltabilirsiniz.

 Gözlemci gibi bazı genel tasarım desenleri iyi bilinmektedir ve yaygın olarak uygulanabilir. Ayrıca, yalnızca projeniz için geçerli olan desenler vardır. Örneğin, bir web satış sisteminde, kodda bir müşterinin sırasıyla değişiklikler yapıldığı birkaç işlem olacaktır. Siparişin durumunun her aşamada doğru şekilde görüntülendiğinden emin olmak için, bu işlemlerin veritabanının güncelleştirilmesi için belirli bir protokolü izlemesi gerekir.

 Yazılım mimarisi işinin bir parçası, tasarımın tamamında hangi desenlerin benimsenmesi gerektiğini belirlemektir. Bu genellikle devam eden bir görevdir, çünkü mevcut desenlere yönelik yeni modeller ve iyileştirmeler proje ilerledikçe keşfedilir. Geliştirme planını düzenlemek faydalı olur, böylece ilk aşamada önemli tasarım desenlerinizin her birini gerçekleştirebilirsiniz.

 Çoğu tasarım deseni çerçeve koduna kısmen eklenebilir. Düzenin, veritabanının doğru şekilde işlenmesini sağlayan bir veritabanı erişim katmanı gibi belirli sınıfları veya bileşenleri kullanmasını gerektirecek şekilde, düzenin bir bölümü azaltılabilir.

 Tasarım alanı bir belge içinde tanımlanır ve genellikle şu parçaları içerir:

- ada.

- Geçerli olduğu bağlamın açıklaması. Bir geliştirici bu düzenin uygulanmasını ne planlıyor?

- Çözdüğü sorunun kısa açıklaması.

- Ana parçaların ve bunların ilişkilerinin modeli. Bunlar arasındaki ilişkilendirmeler ve bağımlılıklarla birlikte sınıflar veya bileşenler ve arabirimler olabilir. Öğeler genellikle iki kategoriye ayrılır:

- Adlandırma kuralları.

- Düzenin sorunu nasıl çözdüğü hakkında açıklama.

- Geliştiricilerin benimseyebileceği çeşitlemelerin açıklaması.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)
- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)
- [Model aracılığıyla test geliştirme](../modeling/develop-tests-from-a-model.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)