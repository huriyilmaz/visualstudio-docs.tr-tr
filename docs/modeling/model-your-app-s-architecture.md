---
title: Uygulama &apos; mimarinizi modelleme
description: Yazılım sisteminizin veya Visual Studio genel yapısının ve davranışının açıklamasının bir parçası olarak bu modellerde nasıl model oluşturabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 0540c119cfd5b6f6a67b820c46e55539afe2e0244ee2e99db5891ba1d1f901a8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231541"
---
# <a name="model-your-app39s-architecture"></a>Uygulama mimarinizi&#39;modeli
Yazılım sisteminizin veya uygulamanın kullanıcılarının ihtiyaçlarını karşılamaya yardımcı olmak için, yazılım sisteminizin veya Visual Studio genel yapısının ve davranışının açıklamasının bir parçası olarak Visual Studio'de modeller oluşturabilirsiniz. Modelleri kullanarak, tasarım boyunca kullanılan desenleri de açıkabilirsiniz. Bu modeller mevcut mimariyi anlamanıza, değişiklikleri tartışmanıza ve amaçlarınızı net bir şekilde ifade etmeye yardımcı olur.

 Bu özelliği destekleyen Visual Studio için bkz. Mimari ve [modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

 Modelin amacı, doğal dil açıklamalarında oluşan belirsizlikleri azaltmak ve siz ve iş arkadaşlarınıza tasarımı görselleştirmenize ve alternatif tasarımları tartışmanıza yardımcı olmaktır. Model, diğer belgeler veya tartışmalarla birlikte kullanılmalıdır. Model tek başına mimarinin tam belirtimlerini temsil etmemektedir.

> [!NOTE]
> Bu konu boyunca "sistem", geliştirmekte olduğunuz yazılım anlamına gelir. Birçok yazılım ve donanım bileşeninden veya tek bir uygulamadan ya da bir uygulamanın parçasından büyük bir koleksiyon olabilir.

 Bir sistemin mimarisi iki bölüme ayrıl olabilir:

- [Üst Düzey Tasarım](#Structure). Bu, ana bileşenleri ve her gereksinimi karşılamak için birbirleriyle nasıl etkileşim kur olduklarını açıklar. Sistem büyükse, her bileşenin nasıl daha küçük bileşenlerden oluşan olduğunu gösteren kendi üst düzey tasarımı olabilir.

- [Bileşenlerin tasarımları](#Patterns) boyunca kullanılan Tasarım Desenleri ve kuralları. Desen, programlama hedefine ulaşmak için belirli bir yaklaşımı açıklar. Bir tasarım boyunca aynı desenleri kullanarak, takımınız değişiklik yapma ve yeni yazılım geliştirme maliyetini düşürerek.

## <a name="high-level-design"></a><a name="Structure"></a> Üst Düzey Tasarım
 Üst düzey bir tasarım, sisteminizin ana bileşenlerini ve tasarım hedeflerine ulaşmak için birbirleriyle nasıl etkileşim kuracaklarını açıklar. Aşağıdaki listede yer alan etkinlikler, belirli bir dizide olması gerekmasa da üst düzey tasarımın geliştirilmesinde yer almaktadır.

 Mevcut kodu güncelleştiriyorsanız, ana bileşenleri açıkleyerek başlayabilirsiniz. Kullanıcı gereksinimlerinde yapılan değişiklikleri anla ve ardından bileşenler arasındaki etkileşimleri ekle veya değiştir. Yeni bir sistem geliştiriyorsanız, kullanıcıların ihtiyaçlarının temel özelliklerini anarak başlayabilirsiniz. Daha sonra ana kullanım örnekleri için etkileşim dizilerini keşfedebilir ve ardından dizileri bir bileşen tasarımında birleştirebilirsiniz.

 Her durumda, farklı etkinlikleri paralel olarak geliştirmek ve erken bir aşamada kod ve test geliştirmek yararlı olur. Bir tane daha başlatmadan önce bu yönlerden birini tamamlamaya çalışmamak. Genellikle, kodu yazarken ve test ederken hem gereksinimler hem de sistemi tasarlamanın en iyi yolunu anlamanız değişir. Bu nedenle öncelikle gereksinimlerin ve tasarımının temel özelliklerini anlamanız ve kodlamanız gerekir. Projenin sonraki yinelemeleri için ayrıntıları doldurun.

- [Gereksinimleri Anlama.](#Requirements) Herhangi bir tasarımın başlangıç noktası, kullanıcıların ihtiyaçlarını net bir şekilde anlamaktır.

- [Mimari Desenler.](#BigDecisions) Temel teknolojiler ve sistemin mimari öğeleri hakkında yapmış olduğunuz seçimler.

- Bileşenlerin ve Arabirimlerin Veri Modeli. Bileşenler arasında geçirilen ve bileşenlerin içinde depolanan bilgileri açıklamak için sınıf diyagramları çizebilirsiniz.

## <a name="understanding-the-requirements"></a><a name="Requirements"></a> Gereksinimleri Anlama
 Eksiksiz bir uygulamanın üst düzey tasarımı, bir gereksinimler modeli veya kullanıcıların gereksinimlerinin diğer açıklamasıyla birlikte en etkili şekilde geliştirilmiştir. Gereksinimler modelleri hakkında daha fazla bilgi için bkz. [Model kullanıcı gereksinimleri.](../modeling/model-user-requirements.md)

 Geliştirdiğiniz sistem daha büyük bir sistemde bir bileşense, gereksinimlerinizin bir bölümü veya tüm bileşenleri program arabirimleri içinde yer almaktadır.

 Gereksinimler modeli şu temel bilgileri sağlar:

- Sağlanan arabirimler. Sağlanan arabirim, sistem veya bileşenin kullanıcılara sağlamaları gereken hizmetleri veya işlemleri (ister insan kullanıcılar ister diğer yazılım bileşenleri olsun) listeler.

- Gerekli arabirimler. Gerekli bir arabirim, sistemin veya bileşenin kullanabileceği hizmetleri veya işlemleri listeler. Bazı durumlarda, tüm bu hizmetleri kendi sisteminizin bir parçası olarak tasarabileceksiniz. Diğer durumlarda, özellikle de birçok yapılandırmada diğer bileşenlerle bir araya gelecek bir bileşen tasarlarsanız, gerekli arabirim dış konular tarafından ayarlanır.

- Hizmet kalitesi gereksinimleri. Sistemin karşılaması gereken performans, güvenlik, sağlamlık ve diğer hedefler ve kısıtlamalar.

  Gereksinimler modeli, ister insan ister diğer yazılım bileşenleri olsun, sistem kullanıcılarının bakış açısından yazılır. Bunlar, sisteminizin iç çalışmalarının hiçbir şeyi bilmiyor. Buna karşılık, mimari modelde amacınız iç çalışmalarınızı açıklamak ve kullanıcıların ihtiyaçlarını nasıl karşıla olduklarını göstermektir.

  Gereksinimleri ve mimari modelleri ayrı tutmak, gereksinimleri kullanıcılarla tartışmayı kolaylaştırma konusunda faydalıdır. Ayrıca, gereksinimleri değiştirmeden tasarımı yeniden düzenlemenizi ve alternatif mimarileri göz önünde bulundurmanıza yardımcı olur.

  Bir gereksinimlere veya mimari modele koymamız gereken ayrıntı miktarı, projenin ölçeğine ve ekibin boyutuna ve dağılımına bağlıdır. Kısa bir proje üzerinde küçük bir ekip, iş kavramlarının sınıf diyagramını ve bazı tasarım desenlerini çizmekten başka bir şey yapmak zorunda değildir; Birden fazla bölgeye dağıtılmış büyük bir projenin daha fazla ayrıntıya ihtiyacı olur.

## <a name="architectural-patterns"></a><a name="BigDecisions"></a> Mimari Desenler
 Geliştirmenin erken dönemleri için tasarımın bağlı olduğu başlıca teknolojileri ve öğeleri seçmeniz gerekir. Bu seçeneklerin hangi alanlarda olması gerektiğini şunlardır:

- Veritabanı ile dosya sistemi arasındaki seçim ve ağa bağlı bir uygulama ile web istemcisi arasındaki seçim gibi temel teknoloji seçimleri.

- Windows Workflow Foundation veya ADO.NET Entity Framework.

- Tümleştirme yöntemi seçenekleri, örneğin bir kurumsal hizmet veri verisi veya noktadan noktaya kanal arasında.

  Bu seçenekler genellikle ölçek ve esneklik gibi hizmet kalitesi gereksinimlerine göre belirlenir ve ayrıntılı gereksinimler bilinmeden önce bu seçeneklerden biri olabilir. Büyük bir sistemde, donanım ve yazılım yapılandırması kesinlikle birbiriyle ilişkilidir.

  Sizin seçimleriniz, mimari modeli nasıl kullanabileceğinizi ve yorumlaymanizi etkiler. Örneğin, veritabanı kullanan bir sistemde, sınıf diyagramında ilişkiler veritabanındaki ilişkileri veya yabancı anahtarları temsil ederken, XML dosyalarını temel alan bir sistemde ilişkilendirmeler XPath kullanan çapraz başvuruları gösteriyor olabilir. Dağıtılmış bir sistemde, sıralı diyagramda yer alan iletiler bir kabloda iletileri temsil eder; kendi içinde bir uygulamada işlev çağrılarını temsil ediyor olabilir.

## <a name="design-patterns"></a><a name="Patterns"></a> Tasarım Desenleri
 Tasarım düzeni, yazılımın belirli bir yönünün, özellikle de sistemin farklı kısımlarında tekrarlayan bir özelliğin nasıl tasarlan bir ana hatlarıdır. Proje genelinde tekdüz bir yaklaşım benimseerek tasarım maliyetini düşürebilirsiniz, kullanıcı arabiriminde tutarlılık s sağlanmasını ve kodu anlama ve değiştirme maliyetini azaltabilirsiniz.

 Gözlemci gibi bazı genel tasarım desenleri iyi bilinir ve yaygın olarak uygulanabilir. Ayrıca yalnızca projeniz için geçerli olan desenler de vardır. Örneğin, bir web satış sisteminde kodda müşterinin siparişte değişiklik yapılan birkaç işlem olacak. Siparişin durumunun her aşamada doğru şekilde görüntülendiğinden emin olmak için tüm bu işlemlerin veritabanını güncelleştirmek için belirli bir protokolü izlemesi gerekir.

 Yazılım mimarisinin çalışmalarının bir parçası, tasarım genelinde hangi desenlerin benimseneceklerini belirlemektir. Bu genellikle devam eden bir görevdir çünkü proje ilerledikçe mevcut desenlerde yeni desenler ve geliştirmeler keşfeder. Geliştirme planını düzenlemek, ana tasarım desenlerinizi erken bir aşamada alıştırmak için faydalıdır.

 Çoğu tasarım deseni, çerçeve kodunda kısmen yer almaktadır. Desenin bir kısmı, geliştiricinin veritabanının doğru şekilde işlen bir veritabanı erişim katmanı gibi belirli sınıfları veya bileşenleri kullanmasını gerektirmeye kadar azaltabilirsiniz.

 Tasarım deseni bir belgede açıklanmıştır ve genellikle şu bölümleri içerir:

- Adı.

- Geçerli olduğu bağlamın açıklaması. Bir geliştiricinin bu düzeni uygulama ölçütlerini göz önünde olması gerekir?

- Çözen sorunun kısa açıklaması.

- Ana parçaların ve ilişkilerinin modeli. Bunlar sınıflar veya bileşenler ve arabirimler olabilir ve bunlar arasındaki ilişkilendirmeler ve bağımlılıklar olabilir. Öğeler genellikle iki kategoriye ayrılır:

- Adlandırma kuralları.

- Desenin sorunu nasıl çözeceğinin açıklaması.

- Geliştiricilerin benimsemek mümkün olabileceği varyasyonların açıklaması.

## <a name="see-also"></a>Ayrıca bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)
- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)
- [Model aracılığıyla test geliştirme](../modeling/develop-tests-from-a-model.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
