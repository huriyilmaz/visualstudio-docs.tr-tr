---
title: 'Senaryo: Görselleştirme ve modelleme yi kullanarak tasarımınızı değiştirin | Microsoft Dokümanlar'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
ms.assetid: ccc80825-a4a0-44fa-a0bb-f95254785a3b
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70cc3c81c426ec55d0afb36360155786ec97d937
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302317"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'daki görselleştirme ve modelleme araçlarını kullanarak yazılım sisteminizin kullanıcıların gereksinimlerini karşıladığından emin olun. Birleşik Modelleme Dili (UML) diyagramları, kod eşlemleri, katman diyagramları ve sınıf diyagramları gibi araçları kullanarak şunları yapın:

 Visual Studio'nun hangi sürümlerinin her aracı desteklediğini görmek [için mimari ve modelleme araçları için Sürüm desteğine](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)bakın.

- Kullanıcıların gereksinimlerini ve iş süreçlerini netleştirin.

- Varolan kodu görselleştirin ve keşfedin.

- Varolan bir sistemdeki değişiklikleri açıklayın.

- Sistemin gereksinimlerini karşıladığını doğrulayın.

- Kodu tasarımla tutarlı tutun.

  Bu walkthrough:

- Bu araçların yazılım projenize nasıl fayda sağlayacağını açıklar.

- Geliştirme yaklaşımınız ne olursa olsun, bu araçları örnek bir senaryoyla nasıl kullanabileceğinizi gösterir.

  Bu araçlar ve destekledikleri senaryolar hakkında daha fazla bilgi edinmek için bkz:

- [Mimariyi Çözümleme ve Mimarinin Modelini Oluşturma](../modeling/analyze-and-model-your-architecture.md)

- [Kodu görselleştirme](../modeling/visualize-code.md)

- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)

## <a name="scenario-overview"></a><a name="ScenarioOverview"></a>Senaryoya Genel Bakış
 Bu senaryo, iki hayali şirketin yazılım geliştirme yaşam döngülerinden bölümleri açıklar: Dinner Now ve Lucerne Publishing. Dinner Now, Seattle'da Web tabanlı yemek dağıtım hizmeti sunmaktadır. Müşteriler yemek siparişi verebilir ve şimdi akşam yemeği web sitesinden ödeme yapabilir. Siparişler daha sonra teslimat için uygun yerel restorana gönderilir. New York'ta bir şirket olan Lucerne Publishing, web'de ve kapalı birçok işletme yi işletmektedir. Örneğin, müşterilerin restoran incelemeleri gönderebileceği bir Web sitesi çalıştırın.

 Lucerne son zamanlarda Dinner Now'ı satın aldı ve aşağıdaki değişiklikleri yapmak istiyor:

- Şimdi Akşam Yemeği'ne restoran inceleme özellikleri ekleyerek Web sitelerini entegre edin.

- Dinner Now'ın ödeme sistemini Lucerne'in sistemiyle değiştirin.

- Akşam Yemeği Şimdi servisini bölge genelinde genişletin.

  Akşam Yemeği Şimdi SCRUM ve eXtreme Programlama kullanır. Onlar çok yüksek test kapsamı ve çok az desteklenmeyen kod var. Bir sistemin küçük ancak çalışan sürümlerini oluşturarak ve işlevselliği artımlı olarak ekleyerek riskleri en aza indirirler. Kodlarını kısa ve sık yinelemeler üzerinde geliştirirler. Bu, değişimi güvenle benimsemelerini, kodu sık sık yeniden düzenlemelerini ve "öndeki büyük tasarımdan" kaçınmalarını sağlar.

  Lucerne, bazıları 40 yıldan daha eski olan çok daha büyük ve karmaşık bir sistem koleksiyonuna sahip. Eski kodun karmaşıklığı ve kapsamı nedeniyle değişiklik yapma konusunda çok dikkatlidirler. Daha titiz bir geliştirme süreci izlerler, ayrıntılı çözümler tasarlamayı ve geliştirme sırasında meydana gelen tasarım ve değişiklikleri belgelemeyi tercih ederler.

  Her iki takım da Visual Studio'da kullanıcıların gereksinimlerini karşılayan sistemler geliştirmelerine yardımcı olmak için modelleme diyagramları kullanır. Çalışmalarını planlamalarına, düzenlemelerine ve yönetmelerine yardımcı olmak için Team Foundation Server'ı diğer araçların yanında kullanırlar.

  Team Foundation Server hakkında daha fazla bilgi için bkz:

- [İş planlama ve izleme](#PlanningTracking)

- [Güncelleştirilmiş kodu sınama, doğrulama ve denetleme](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a>Yazılım Geliştirmede Mimari ve Modelleme Diyagramlarının Rolleri
 Aşağıdaki tabloda, bu araçların yazılım geliştirme yaşam döngüsünün birden çok ve çeşitli aşamalarında oynayabileceği roller açıklanmaktadır:

||**Kullanıcı Gereksinimleri Modelleme**|**İş Süreci Modelleme**|**Sistem Mimarisi & Tasarımı**|**Kod Görselleştirme & Keşif**|**Doğrulama**|
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|
|Kullanım örneği diyagramı (UML)|√|√|||√|
|Etkinlik diyagramı (UML)|√|√|√||√|
|Sınıf diyagramı (UML)|√|√|√||√|
|Bileşen diyagramı (UML)|√|√|√||√|
|Sıralı diyagram (UML)|√|√|√||√|
|Etki Alanına Özgü Dil (DSL) diyagramı|√|√|√|||
|Katman diyagramı, katman doğrulama|||√|√|√|
|Kod haritası|||√|√|√|
|Sınıf Tasarımcısı (kod tabanlı)||||√||

 UML diyagramları ve katman diyagramları çizmek için, varolan bir çözümün veya yeni bir çözümün parçası olarak bir modelleme projesi oluşturmanız gerekir. Bu diyagramlar modelleme projesinde oluşturulmalıdır. UML diyagramları üzerindeki öğeler ortak bir modelin parçasıdır ve UML diyagramları bu modelin görünümleridir. Katman diyagramları üzerindeki öğeler modelleme projesinde bulunur, ancak ortak modelde depolanmaz. Kod eşlemleri ve koddan oluşturulan .NET sınıf diyagramları modelleme projesinin dışında bulunur.

 Bkz.

- [UML modelleme projeleri ve diyagramları oluşturma](../modeling/create-uml-modeling-projects-and-diagrams.md)

- [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

  Mimarinin alternatif görünümlerini göstermek için, aynı modeldeki belirli öğeleri birden çok veya farklı diyagramlarda yeniden kullanabilirsiniz. Örneğin, bir bileşeni başka bir bileşen diyagramına veya bir dizi diyagramına sürükleyip aktör olarak çalışabilirsiniz. Bkz. [UML modellerini ve diyagramlarını edit.](../modeling/edit-uml-models-and-diagrams.md)

  Her iki takım da geliştirilmekte olan kodun tasarımla tutarlı kalmasını sağlamak için katman doğrulama kullanır.

  Bkz.

- [Kodu Tasarımla Tutarlı Tutma](#ValidatingCode)

- [Mantıksal Mimariyi Açıkla: Katman Diyagramları](#DescribeLayers)

- [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

  > [!NOTE]
  > Visual Studio'nun bazı sürümleri, görselleştirme ve modelleme için katman doğrulamasını ve kod eşlemlerinin ve UML diyagramlarının salt okunur sürümlerini destekler. Visual Studio'nun hangi sürümlerinin bu özelliği desteklediğini görmek [için mimari ve modelleme araçları için Sürüm desteğine](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)bakın.

## <a name="understanding-and-communicating-information-about-the-system"></a><a name="UnderstandingCommunicating"></a>Sistem Hakkında Bilgi Nin Anlaşılması ve Iletilmesi
 Visual Studio modelleme diyagramlarını kullanmak için öngörülen bir sipariş yoktur, bu nedenle bunları ihtiyaçlarınıza veya yaklaşımınıza uygun olarak kullanabilirsiniz. Genellikle, takımlar bir proje boyunca modellerini yinelemeli ve sık sık yeniden ziyaret ederler. Her diyagram, geliştirilmekte olan sistemin farklı yönlerini anlamanıza, tanımlamanıza ve iletişim kurmanıza yardımcı olacak belirli güçlü yönler sunar.

 Şimdi Akşam Yemeği ve Lucerne, diyagramları ortak dilleri olarak kullanarak birbirleriyle ve proje paydaşlarıyla iletişim kurarlar. Örneğin, Şimdi Akşam Yemeği bu görevleri gerçekleştirmek için diyagramları kullanır:

- Varolan kodu görselleştirin.

- Lucerne ile yeni veya güncelleştirilmiş kullanıcı hikayeleri hakkında iletişim kurun.

- Yeni veya güncelleştirilmiş kullanıcı öykülerini desteklemek için gereken değişiklikleri tanımlayın.

  Lucerne bu görevleri gerçekleştirmek için diyagramlar kullanır:

- Şimdi Akşam Yemeği iş süreci hakkında bilgi edinin.

- Sistemin tasarımını anlayın.

- Yeni veya güncelleştirilmiş kullanıcı gereksinimleri hakkında Dinner Now ile iletişim kurun.

- Sistemdeki belge güncelleştirmeleri.

  Diyagramlar Team Foundation Server ile tümleştirilir, böylece takımlar çalışmalarını daha kolay planlayabilir, yönetebilir ve izleyebilir. Örneğin, test örneklerini ve geliştirme görevlerini tanımlamak ve çalışmalarını tahmin etmek için modelleri kullanırlar. Lucerne, Team Foundation Server iş öğelerini, ilerlemeyi izleyebilmeleri ve sistemin kullanıcıların gereksinimlerini karşıladığından emin olmak için öğeleri modellemeye bağlar. Örneğin, tüm testler geçerken kullanım örneklerinin yerine getirildiğini görebilmeleri için kullanım örneklerini test etmek için kullanım örneklerini bağlarlar.

  Takımlar değişikliklerini iade etmeden önce, katman doğrulama ve otomatik testler içeren yapılar çalıştırarak kodu testlere ve tasarıma karşı doğrularlar. Bu, güncelleştirilmiş kodun tasarımla çakışmamasını ve daha önce çalışan işlevselliği kesmesini sağlamaya yardımcı olur.

  Bkz.

- [Sistemin iş sürecindeki rolünü anlama](#UnderstandingBPMandSystemDesign)

- [Yeni veya güncelleştirilmiş kullanıcı gereksinimlerini açıklama](#DescribingURM)

- [Modellerden testler oluşturma](#CreatingTests)

- [Varolan sistemdeki değişiklikleri tanımlama](#DeterminingChanges)

- [Kodu tasarımla tutarlı tutma](#ValidatingCode)

- [Modeller oluşturmak ve kullanmak için genel ipuçları](#GeneralTips)

- [İş planlama ve izleme](#PlanningTracking)

- [Güncelleştirilmiş kodu sınama, doğrulama ve denetleme](#TestValidateCheckInCode)

### <a name="understanding-the-role-of-the-system-in-the-business-process"></a><a name="UnderstandingBPMandSystemDesign"></a>Sistemin İş Sürecindeki Rolünü Anlamak
 Lucerne Şimdi Akşam Yemeği iş süreci hakkında daha fazla bilgi edinmek istiyor. Şimdi Akşam Yemeği ile anlayışlarını daha kolay netleştirmek için aşağıdaki diyagramları oluştururlar:

|**Diyagram**|**Açıklanır**|
|-----------------|-------------------|
|*Kullanım örneği diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Kullanım Örneği Diyagramları: Referans](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML Kullanım Örneği Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|- Şimdi Akşam Yemeği sisteminin desteklediği etkinlikler<br />- Faaliyetleri gerçekleştiren kişi ve dış sistemler<br />- Her etkinliği destekleyen sistemin ana bileşenleri<br />- Mevcut sistemin kapsamı dışında olan iş sürecinin parçaları, örneğin, gıda teslimatı|
|*Etkinlik diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Etkinlik Diyagramları: Referans](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|Müşteri sipariş oluşturduğunda oluşan adımların akışı|
|*Sınıf diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)|Tartışmada kullanılan iş varlıkları ve terimler ve bu varlıklar arasındaki ilişkiler. Örneğin, Sipariş ve Menü Öğesi bu senaryodaki sözcük dağarcığının bir parçasıdır.|

 Örneğin, Lucerne Şimdi Akşam Yemeği Web sitesinde gerçekleştirilen görevleri ve bunları kimlerin gerçekleştirdiğini anlamak için aşağıdaki kullanım örneği diyagramını oluşturur:

 ![UML Kullanım Örneği Diyagramı](../modeling/media/uml-usecase.png "UML_UseCase")

 **UML Kullanım Örneği Diyagramı**

 Aşağıdaki etkinlik diyagramı, bir müşteri Şimdi Akşam Yemeği Web sitesinde bir sipariş oluşturduğunda adım akışını açıklar. Bu sürümde, yorum öğeleri rolleri tanımlar ve satırlar rolleri ne göre adımları düzenlemek *şeritoluşturmak:*

 ![UML Etkinlik Diyagramı](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")

 **UML Etkinlik Diyagramı**

 Aşağıdaki sınıf diyagramı, sipariş işlemine katılan varlıkları açıklar:

 ![UML Sınıf Diyagramı](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")

 **UML Sınıf Diyagramı**

### <a name="describing-new-or-updated-user-requirements"></a><a name="DescribingURM"></a>Yeni veya Güncelleştirilmiş Kullanıcı Gereksinimlerini Açıklama
 Lucerne, müşterilerin restoran yorumlarını okuyup katkıda bulunabilmeleri için Şimdi Akşam Yemeği sistemine işlevsellik eklemek istiyor. Bu yeni gereksinimi Şimdi Akşam Yemeği ile açıklayabilmeleri ve tartışabilmeleri için aşağıdaki diyagramları güncellerler:

|**Diyagram**|**Açıklanır**|
|-----------------|-------------------|
|*Kullanım örneği diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Kullanım Örneği Diyagramları: Referans](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML Kullanım Örneği Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|"Restoran incelemesi yaz" için yeni bir kullanım örneği|
|*Etkinlik diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Etkinlik Diyagramları: Referans](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|Müşteri restoran incelemesi yazmak istediğinde oluşan adımlar|
|*Sınıf diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)|Gözden geçirme depolamak için gereken veriler|

 Örneğin, aşağıdaki kullanım örneği diyagramı, yeni gereksinimi temsil etmek için yeni bir "Gözden Geçirme Yaz" kullanım örneği içerir. Daha kolay tanımlama için diyagramda turuncu renkle vurgulanır:

 ![UML Kullanım Örneği Diyagramı](../modeling/media/uml-writerev.png "UML_WriteRev")

 **UML kullanım örneği diyagramı**

 Aşağıdaki etkinlik diyagramı, yeni kullanım durumundaki adımların akışını açıklamak için turuncu renkte yeni öğeler içerir:

 ![UML Etkinlik Diyagramı](../modeling/media/uml-writereview.png "UML_WriteReview")

 **UML etkinlik diyagramı**

 Aşağıdaki sınıf diyagramı, takımların ayrıntılarını tartışabilmeleri için yeni bir Gözden Geçirme sınıfı ve diğer sınıflara olan ilişkilerini içerir. Bir Müşteri ve Bir Restoran'da birden çok Yorum olabileceğine dikkat edin:

 ![UML Sınıf Diyagramı](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")

 **UML sınıf diyagramı**

### <a name="creating-tests-from-models"></a><a name="CreatingTests"></a>Modellerden Testler Oluşturma
 Her iki takım da herhangi bir değişiklik yapmadan önce sistem ve bileşenleri için tam bir test kümesine ihtiyaç duydukları konusunda hemfikirdir. Lucerne'in sistem ve bileşen düzeyinde test gerçekleştiren özel bir ekibi vardır. Dinner Now tarafından oluşturulan testleri yeniden kullanırlar ve uml diyagramlarını kullanarak bu testleri yapılatırlar:

- Her kullanım örneği bir veya birden çok testle temsil edilir. Kullanım örneği diyagramındaki öğeler, Team Foundation Server'daki Test Case iş öğelerine bağlanır.

- Bir etkinlik diyagramı veya sistem düzeyinde sıralı diyagramdaki her akış en azından bir teste bağlanır. Test ekibi, etkinlik diyagramı aracılığıyla mümkün olan her yolu test ettiklerinden sistematik olarak emin olur.

- Testleri açıklamak için kullanılan terimler, kullanım durumu, sınıf ve etkinlik diyagramları tarafından tanımlanan terimleri temel alınarak kullanılır.

  Gereksinimler değiştikçe ve diyagramlar bu değişiklikleri yansıtacak şekilde güncelleştirildikçe, testler de güncelleştirilir. Bir gereksinim, yalnızca testler geçtiğinde yerine getirildiği kabul edilir. Mümkün veya pratik olduğunda, testler tanımlanır ve uygulama başlamadan önce UML diyagramları esas alınır.

  Bkz.

- [Model aracılığıyla test geliştirme](../modeling/develop-tests-from-a-model.md)

- [UML modelinizi doğrulama](../modeling/validate-your-uml-model.md)

### <a name="identifying-changes-to-the-existing-system"></a><a name="DeterminingChanges"></a>Varolan Sistemdeki Değişiklikleri Tanımlama
 Akşam Yemeği Şimdi yeni gereksinimi karşılama maliyetini tahmin etmelidir. Bu, kısmen bu değişikliğin sistemin diğer bölümlerini ne kadar etkileyeceğine bağlıdır. Bunu anlamalarına yardımcı olmak için, Şimdi Akşam Yemeği geliştiricilerinden biri varolan koddan bu haritaları ve diyagramları oluşturur:

|**Harita veya diyagram**|**Diziler**|
|------------------------|---------------|
|*Kod haritası*<br /><br /> Bkz.<br /><br /> -   [Çözümlerinizde bağımlılıkları haritala](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Kod haritalarına göz atın ve yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)<br />-   [DGML dosyalarını düzenleyerek kod eşlemlerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Bağımlılıklar ve koddaki diğer ilişkiler.<br /><br /> Örneğin, Şimdi Akşam Yemeği derlemeleri ve bağımlılıkları genel bir bakış için derleme kodu eşlemleri gözden geçirerek başlayabilir. Bu derlemelerde isim alanlarını ve sınıfları keşfetmek için haritaları inceleyebilirler.<br /><br /> Şimdi Akşam Yemeği, koddaki belirli alanları ve diğer ilişki türlerini keşfetmek için haritalar da oluşturabilir. İlgilerini çeken alanları ve ilişkileri bulmak ve seçmek için Solution Explorer'ı kullanırlar.|
|*Kod tabanlı sınıf diyagramı*<br /><br /> [Bkz. Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Koddaki varolan sınıflar|

 Örneğin, geliştirici bir kod eşlemi oluşturur. Kapsamını, yeni senaryodan etkilenecek alanlara odaklanacak şekilde ayarlar. Bu alanlar seçilir ve haritada vurgulanır:

 ![Ad Alanı Bağımlılık Grafiği](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")

 **Namespace kod haritası**

 Geliştirici sınıflarını, yöntemlerini ve ilişkilerini görmek için seçili ad alanlarını genişletir:

 ![Genişletilmiş ad alanı bağımlılık grafiği](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")

 **Görünür grup lar arası bağlantılarla genişletilmiş ad alanı kodu haritası**

 Geliştirici etkilenen sınıfları ve yöntemleri bulmak için kodu inceler. Yaptığınız da her değişikliğin etkilerini görmek için, her değişiklikten sonra kod eşlemlerini yeniden oluşturun. Bkz. [Görselleştir kodu.](../modeling/visualize-code.md)

 Bileşen veya etkileşim ler gibi sistemin diğer bölümlerindeyapılan değişiklikleri açıklamak için, takım bu öğeleri beyaz tahtalara çizebilir. Ayrıca, ayrıntıların her iki takım tarafından da yakalanıp yönetilebilmeleri ve anlaşılabilmesi için Visual Studio'da aşağıdaki diyagramları çizebilirler:

|**Diyagramları**|**Açıklanır**|
|------------------|-------------------|
|*Etkinlik diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Etkinlik Diyagramları: Referans](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|Sistem, bir müşterinin bir restorandan tekrar sipariş verdiğini fark ettiğinde ortaya çıkan adımların akışı, müşterinin bir inceleme yazmasına neden olur.|
|*Sınıf diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)|Mantıksal sınıflar ve ilişkileri. Örneğin, **Gözden Geçirme'yi** ve **Restoran,** **Menü**ve **Müşteri**gibi diğer varlıklarla olan ilişkilerini açıklamak için yeni bir sınıf eklenir.<br /><br /> İncelemeleri bir müşteriyle ilişkilendirmek için sistemin müşteri ayrıntılarını depolaması gerekir. UML sınıf diyagramı bu ayrıntıları nnetlenebiliyor.|
|*Kod tabanlı sınıf diyagramı*<br /><br /> [Bkz. Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Koddaki varolan sınıflar.|
|*Bileşen diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: Referans](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)|Şimdi Akşam Yemeği Web sitesi ve bunların arayüzleri gibi sistemin üst düzey bölümleri. Bu arabirimler, bileşenlerin sağladıkları ve tükettikleri yöntemler veya hizmetler aracılığıyla birbirleriyle nasıl etkileşimde bulunabileceklerini tanımlar.|
|*Sıralı diyagram (UML)*<br /><br /> Bkz.<br /><br /> -   [UML Sıra Diyagramları: Referans](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML Sıra Diyagramları: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|Örnekler arasındaki etkileşimsırası.|

 Örneğin, aşağıdaki bileşen diyagramı, Şimdi Akşam Yemeği Web Sitesi bileşeninin bir parçası olan yeni bileşeni gösterir. İncelemeİşleme bileşeni, inceleme oluşturma işlevini işler ve turuncu renkle vurgulanmış görünür:

 ![UML Bileşen Diyagramı](../modeling/media/uml-internal.png "UML_Internal")

 **UML bileşen diyagramı**

 Aşağıdaki sıralı diyagram, Şimdi Akşam Yemeği Web Sitesi müşterinin daha önce bir restorandan sipariş verip vermediğini kontrol ettiğinde oluşan etkileşimlerin sırasını gösterir. Bu doğruysa, müşteriden restorana gönderilen ve Web sitesi tarafından yayınlanan bir inceleme oluşturmasını ister:

 ![UML Sıralı Diyagramı](../modeling/media/uml-revsystem.png "UML_RevSystem")

 **UML sıralı diyagramı**

### <a name="keeping-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>Kodu Tasarımla Tutarlı Tutma
 Şimdi Akşam Yemeği Güncelleştirilmiş kodun tasarımla tutarlı kaldığından emin olmalıdır. Sistemdeki işlevsellik katmanlarını açıklayan, aralarında izin verilen bağımlılıkları belirten ve çözüm yapılarını bu katmanlarla ilişkilendiren katman diyagramları oluştururlar.

|**Diyagram**|**Açıklanır**|
|-----------------|-------------------|
|*Katman diyagramı*<br /><br /> Bkz.<br /><br /> -   [Kodunuzdan katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)<br />-   [Kodu katman diyagramlarıyla doğrulama](../modeling/validate-code-with-layer-diagrams.md)|Kodun mantıksal mimarisi.<br /><br /> Katman diyagramı, yapıları *katman*adı [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verilen soyut gruplarla bir çözümde düzenler ve eşler. Bu katmanlar, bu yapılarsistemde gerçekleştirdiği rolleri, görevleri veya işlevleri tanımlar.<br /><br /> Katman diyagramları, sistemin amaçlanan tasarımını açıklamak ve bu tasarıma karşı gelişen kodu doğrulamak için yararlıdır.<br /><br /> Katmanlar oluşturmak için, Öğeleri Çözüm Gezgini, kod eşlemleri, Sınıf Görünümü ve Nesne Tarayıcısı'ndan sürükleyin. Yeni katmanlar çizmek için araç kutusunu kullanın veya diyagram yüzeyine sağ tıklayın.<br /><br /> Varolan bağımlılıkları görüntülemek için katman diyagramı yüzeyini sağ tıklatın ve sonra **Bağımlılıkları Oluştur'u**tıklatın. Amaçlanan bağımlılıkları belirtmek için yeni bağımlılıklar çizin.|

 Örneğin, aşağıdaki katman diyagramı katmanlar arasındaki bağımlılıkları ve her katmanla ilişkili yapı ların sayısını açıklar:

 ![Entegre ödeme sisteminin katman diyagramı](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Katman Diyagramı**

 Takım, kod geliştirme sırasında tasarımla çakışma oluşmadığından emin olmak için, Team Foundation Build'te çalıştırılabilen yapılarda katman doğrulaması kullanır. Ayrıca, iade işlemlerinde katman doğrulaması gerektiren özel bir MSBuild görevi de oluştururlar. Doğrulama hatalarını toplamak için yapı raporları kullanırlar.

 Bkz.

- [Yapı işleminizi tanımlayın](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)

- [Değişiklikleri doğrulamak için geçitli iade oluşturma işlemi kullanma](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)

- [Yapı işlem şablonunuzu özelleştirme](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

### <a name="general-tips-for-creating-and-using-models"></a><a name="GeneralTips"></a>Modeller Oluşturmak ve Kullanmak Için Genel İpuçları

- Çoğu diyagram, çizgilerle bağlanan düğümlerden oluşur. Her diyagram türü için araç kutusu farklı türde düğümler ve çizgiler sağlar.

   Araç kutusunu açmak için **Görünüm** menüsünde **Araç Kutusu'nu**tıklatın.

- Düğüm oluşturmak için, onu araç kutusundan diyagrama sürükleyin. Belirli türdeki düğümler varolan düğümlere sürülmelidir. Örneğin, bileşen diyagramında varolan bir bileşene yeni bir bağlantı noktası eklenmelidir.

- Bir satır veya bağlantı oluşturmak için, araç kutusundaki uygun aracı tıklatın, kaynak düğüm'e tıklayın ve ardından hedef düğümü tıklatın. Bazı satırlar yalnızca belirli türde düğümler arasında oluşturulabilir. İşaretçiyi olası bir kaynak veya hedef üzerinde taşıdığınızda, işaretçi bir bağlantı oluşturup oluşturamayacağınızı gösterir.

- UML diyagramlarında öğeler oluşturduğunuzda, bunları ortak bir modele de eklersiniz. Modelleme projesindeki UML diyagramları bu modelin görünümleridir. Katman diyagramındaki öğeler, ortak modelde depolanmasalar bile modelleme projesinin bir parçasıdır.

   Modeli görmek için **Mimari** menüsünde, **Windows'u**işaret edin ve ardından **UML Model Explorer'ı**tıklatın.

- Bazı durumlarda, **uml model explorer'dan uml** diyagramına belirli öğeleri sürükleyebilirsiniz. Aynı modeldeki bazı öğeler, mimarinin alternatif görünümlerini göstermek için birden çok veya farklı diyagramda kullanılabilir. Örneğin, bir bileşeni başka bir bileşen diyagramına veya aktör olarak kullanmak üzere bir dizi diyagramına sürükleyebilirsiniz.

- Visual Studio UML 2.1.2 destekler. Bu genel bakış, bu sürümde UML diyagramlarının yalnızca önemli özelliklerini açıklar, ancak UML ve ayrıntılı olarak kullanımını tartışmak birçok kitap vardır.

  Uygulamanız [için modelleri oluştur'a](../modeling/create-models-for-your-app.md)bakın.

### <a name="planning-and-tracking-work"></a><a name="PlanningTracking"></a>Planlama ve İzleme Çalışmaları
 Visual Studio modelleme diyagramları, çalışmayı daha kolay planlayabilmeniz, yönetebilmeniz ve izleyebilmeniz için Team Foundation Server ile entegre edilmiştir. Her iki takım da test örneklerini ve geliştirme görevlerini belirlemek ve çalışmalarını tahmin etmek için modelleri kullanır. Lucerne, Team Foundation Server iş öğelerini kullanım örnekleri veya bileşenler gibi model öğelerine bağlar ve oluşturur. Bu, ilerlemelerini izlemelerine ve çalışmalarını kullanıcıların gereksinimlerine kadar izlemelerine yardımcı olur. Bu, değişikliklerinin bu gereksinimleri karşılamaya devam etmesini sağlamalarına yardımcı olur.

 Çalışmaları ilerledikçe, takımlar görevlerinde harcadıkları zamanı yansıtacak şekilde iş öğelerini güncelleştirir. Ayrıca, aşağıdaki Team Foundation Server özelliklerini kullanarak çalışmalarının durumunu izler ve bildirirler:

- Günlük *tükenmişlik raporları,* planlanan çalışmayı beklenen süre içinde tamamlayıp tamamlamayacaklarını gösteriyor. Hataların ilerlemesini izlemek için Team Foundation Server'dan benzer raporlar oluştururlar.

- Ekibin üyeleri arasındaki iş yükünü izlemesine ve dengelemesine yardımcı olmak için Microsoft Excel'i kullanan bir *yineleme çalışma sayfası.* Bu çalışma sayfası Team Foundation Server'a bağlıdır ve düzenli ilerleme toplantıları sırasında tartışmaya odaklanmayı sağlar.

- Ekibi önemli proje bilgileri hakkında bilgilendirmek için Office Project'i kullanan bir *geliştirme panosu.*

  Bkz.

- [Visual Studio Ekip Hizmetleri veya Team Foundation Server'ı kullanarak çalışmayı izleme](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)

- [Model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md)

- [Visual Studio ALM için grafikler, panolar ve raporlar](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)

- [Project'i kullanarak biriktirme listenizi ve görevlerinizi oluşturun](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)

### <a name="testing-validating-and-checking-in-code"></a><a name="TestValidateCheckInCode"></a>Kodu Test Etme, Doğrulama ve Denetleme
 Takımlar her görevi tamamlayarken, kodlarını Team Foundation sürüm denetimine kontrol ederler ve unuturlarsa Team Foundation Server'dan anımsatıcılar alırlar. Team Foundation Server iadelerini kabul etmeden önce, takımlar kodu test örneklerine ve tasarıma karşı doğrulamak için birim testleri ve katman doğrulama sıyrıkları çalıştırın. Oluşturmaları, otomatik birim testlerini ve katman doğrulamayı düzenli olarak çalıştırmak için Team Foundation Server'ı kullanırlar. Bu, kodun aşağıdaki ölçütleri karşıladığından emin olunmasınıza yardımcı olur:

- İşe yarıyor.

- Daha önce çalışma kodunu bozmaz.

- Tasarımla çakışmaz.

  Dinner Now, Lucerne'nin yeniden kullanabileceği büyük bir otomatik test koleksiyonuna sahiptir, çünkü neredeyse hepsi hala geçerlidir. Lucerne ayrıca bu testleri oluşturabilir ve yeni işlevleri kapsayacak şekilde yenilerini ekleyebilir. Her ikisi de el ile testler çalıştırmak için Visual Studio kullanın.

  Kodun tasarıma uydugundan emin olmak için, takımlar yapılarını Team Foundation Build' de katman doğrulamayı içerecek şekilde yapılandırır. Herhangi bir çakışma oluşursa, ayrıntılarla birlikte bir rapor oluşturulur.

  Bkz.

- [Uygulamayı test etme](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)

- [Sürüm denetimini kullanma](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Uygulama oluşturma](/azure/devops/pipelines/index)

## <a name="updating-the-system-using-visualization-and-modeling"></a><a name="UpdatingSystem"></a>Görselleştirme ve Modelleme Kullanarak Sistemin Güncellenmesi
 Lucerne ve Dinner Now ödeme sistemlerini entegre etmeli. Aşağıdaki bölümler, Visual Studio'daki modelleme diyagramlarını göstererek bu görevi gerçekleştirmelerine yardımcı olur:

- [Kullanıcı Gereksinimlerini Anlama: Büyük/Küçük Harf Diyagramları Kullanın](#UnderstandUseCases)

- [İş Sürecini Anlama: Etkinlik Diyagramları](#UnderstandActivities)

- [Sistem Yapısını Açıklayın: Bileşen Diyagramları](#DescribeComponents)

- [Etkileşimleri Açıklayın: Sıralı Diyagramlar](#DescribeSequence)

- [Varolan Kodu Görselleştir: Kod Haritaları](#VisualizeCode)

- [Türler Sözlüğü Tanımla: Sınıf Diyagramları](#DefineClasses)

- [Mantıksal Mimariyi Açıkla: Katman Diyagramları](#DescribeLayers)

  Bkz.

- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)

- [Kodu görselleştirme](../modeling/visualize-code.md)

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)

- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)

- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)

### <a name="understand-the-user-requirements-use-case-diagrams"></a><a name="UnderstandUseCases"></a>Kullanıcı Gereksinimlerini Anlama: Büyük/Küçük Harf Diyagramları Kullanın
 Kullanım örneği diyagramları, sistemin desteklediği ve bu etkinlikleri kimin gerçekleştirdiğini özetler. Lucerne, Şimdi Akşam Yemeği sistemi hakkında aşağıdakileri öğrenmek için bir kullanım örneği diyagramı kullanır:

- Müşteriler sipariş oluşturur.

- Restoranlar sipariş alır.

- Dinner Now Payment System'in ödemeleri doğrulamak için kullandığı Dış Ödeme İşlemcisi Ağ Geçidi, Web sitesinin kapsamı dışındadır.

  Diyagram ayrıca, bazı büyük kullanım örneklerinin nasıl daha küçük kullanım örneklerine bölünür olduğunu da gösterir. Lucerne kendi ödeme sistemini kullanmak istiyor. Değişiklik gerektirdiğini belirtmek için İşlem Ödemesi kullanım örneğini farklı bir renkte vurgularlar:

  ![Kullanım örneği diyagramında İşlem Ödeme'yi vurgulama](../modeling/media/uml-processpay.png "UML_ProcessPay")

  **Kullanım örneği diyagramında Proses Ödemesini Vurgulama**

  Geliştirme süresi kısaysa, ekip müşterilerin restoranlara doğrudan ödeme ödemesine izin vermek isteyip istemediklerini tartışabilir. Bunu göstermek için, İşlem Ödemesi kullanım örneğini Şimdi Akşam Yemeği sistemi sınırının dışında olan bir işlem le değiştirirler. Daha sonra Müşteri'yi doğrudan Restoran'a bağlayarak, Şimdi Akşam Yemeği'nin yalnızca siparişleri işlemeyeceğini belirtirler:

  ![Pay Restaurant'ı kullanım örneği diyagramında yeniden kullanma](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")

  **Pay Restaurant'ı kullanım örneği diyagramında yeniden kullanma**

  Bkz.

- [UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)

- [UML Kullanım Durumu Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="drawing-a-use-case-diagram"></a>Kullanım Örneği Diyagramı Çizimi
 Kullanım örneği diyagramı aşağıdaki temel özelliklere sahiptir:

- *Aktörler* kişiler, kuruluşlar, makineler veya yazılım sistemleri tarafından oynanan rolleri temsil eder. Örneğin, Müşteri, Restoran ve Şimdi Akşam Yemeği Ödeme Sistemi aktörlerdir.

- *Kullanım örnekleri,* aktörler ve geliştirilmekte olan sistem arasındaki etkileşimleri temsil eder.  Tek bir fare tıklamasından veya iletiden günler direnen bir işlem için herhangi bir etkileşim ölçeğini temsil edebilirler.

- *Çağrışımlar,* durumları kullanmak için aktörleri birbirine bağlar.

- Daha büyük bir kullanım örneği daha küçük olanları *içerebilir,* örneğin, Sipariş Oluştur Restoran Seç içerir. Genişletilmiş kullanım örneğine hedefler ve adımlar ekleyen bir kullanım örneğini, kullanım örneğinin yalnızca belirli koşullar altında oluştuğunu belirtmek için *genişletebilirsiniz.* Kullanım örnekleri de birbirinden devralabilir.

- Bir *alt sistem,* geliştirilmekte olan yazılım sistemini veya bileşenlerinden birini temsil eder. Kullanım örnekleri içeren büyük bir kutudur. Kullanım örneği diyagramı, alt sistem sınırının içinde veya dışında ne olduğunu açıklar. Kullanıcının belirli hedefleri başka şekillerde gerçekleştirmesi gerektiğini belirtmek için, bu kullanım durumlarını alt sistem sınırının dışına çizin.

- *Yapılar* diyagramdaki öğeleri diğer diyagramlara veya belgelere bağlar.

  Bkz.

- [UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)

- [UML Kullanım Durumu Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="summary-strengths-of-use-case-diagrams"></a>Özet: Kullanım Güçlü Örnek Diyagramları
 Büyük/küçük harf diyagramlarını kullanma, görselleştirmenize yardımcı olur:

- Bir sistemin desteklediği veya desteklemediği etkinlikler

- Bu faaliyetleri gerçekleştiren kişiler ve dış sistemler

- Üst sistemin içinde iç içe olan alt sistemler olarak temsil edebileceğiniz her etkinliği destekleyen sistemin ana bileşenleri

- Bir kullanım örneği daha küçük olanlara veya varyasyonlara nasıl bölünebilir?

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklanır**|
|-----------------|-------------------|
|Etkinlik diyagramı|Kullanım durumundaki adımların akışı ve bu kullanım örneğinde bu adımları gerçekleştirenler.<br /><br /> Kullanım örneklerinin adları sık sık bir etkinlik diyagramındaki adımları yansıtılır. Etkinlik diyagramları kararlar, birleştirmeler, girdiler ve çıktılar, eşzamanlı akışlar ve benzeri öğeleri destekler.<br /><br /> Bkz.<br /><br /> -   [UML Etkinlik Diyagramları: Referans](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|
|Sıralı diyagram|Bir kullanım örneğindeki katılımcılar arasındaki etkileşimsırası.<br /><br /> Bkz.<br /><br /> -   [UML Sıra Diyagramları: Referans](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML Sıra Diyagramları: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|
|Sınıf diyagramı (UML)|Kullanım örneğine katılan varlıklar veya türler.<br /><br /> Bkz.<br /><br /> -   [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)|

### <a name="understand-the-business-process-activity-diagrams"></a><a name="UnderstandActivities"></a>İş Sürecini Anlama: Etkinlik Diyagramları
 Etkinlik diyagramları, iş sürecindeki adımların akışını açıklar ve iş akışını iletmek için basit bir yol sağlar. Geliştirme projesinde birden çok etkinlik diyagramı olabilir. Genellikle, bir etkinlik yemek siparişi verme, menüyü güncelleme veya işletmeye yeni bir restoran ekleme gibi tek bir dış eylemden kaynaklanan tüm eylemleri kapsar. Bir etkinlik, karmaşık bir eylemin ayrıntılarını da açıklayabilir.

 Lucerne, Lucerne'nin ödemeyi işlediğini ve restorana ödeme ödediğini göstermek için aşağıdaki etkinlik diyagramını güncelleştirir. Onlar vurgulandığı gibi Lucerne Ödeme Sistemi ile Dinner Now Ödeme Sistemi yerine:

 ![Etkinlik diyagramında Lucerne ödeme sistemi](../modeling/media/uml-lucerne.png "UML_Lucerne")

 **Etkinlik diyagramında Şimdi Akşam Yemeği Ödeme Sistemi'nin değiştirilmesi**

 Güncelleştirilmiş diyagram, Lucerne Ödeme Sistemi'nin iş sürecine uygun olduğu yeri Lucerne ve Dinner Now görselleştirmesine yardımcı olur. Bu sürümde, açıklamalar adımları gerçekleştiren rolleri tanımlamak için kullanılır. Çizgiler, adımları role göre düzenleyen *kulvarlar*oluşturmak için kullanılır.

 Ekipler ayrıca, sipariş teslim edildikten sonra müşterinin restorana ödeme yaptığı alternatif bir hikayeyi tartışmayı da düşünebilir. Bu, yazılım sistemi için farklı gereksinimler oluşturur.

 Daha önce, Dinner Now bu diyagramları beyaz tahtaya veya PowerPoint'e çizer. Artık visual studio'yu kullanarak bu diyagramları çizerler, böylece her iki takım da ayrıntıları yakalayabilir, anlayabilir ve yönetebilir.

 Bkz.

- [UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)

- [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="drawing-an-activity-diagram"></a>Etkinlik Diyagramı Çizme
 Etkinlik diyagramı aşağıdaki temel özelliklere sahiptir:

- Etkinliğin ilk eylemini gösteren bir *ilk düğüm.*

   Diyagramda her zaman bu düğümlerden biri olmalıdır.

- Kullanıcının veya yazılımın bir görevi gerçekleştirdiği adımları açıklayan *eylemler.*

- Eylemler arasındaki akışı gösteren *denetim akışları.*

- Akıştaki koşullu dalları temsil eden *karar düğümleri.*

- Tek akışları eşzamanlı akışlara bölen *çatal düğümleri.*

- Etkinliğin sona erdiğini gösteren *etkinlik son düğümleri.*

   Bu düğümler isteğe bağlı olsa da, etkinliğin nerede bittiğini göstermek için bunları diyagrama eklemek yararlıdır.

  Bkz.

- [UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)

- [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="summary-strengths-of-activity-diagrams"></a>Özet: Etkinlik Diyagramlarının Güçlü Yönleri
 Etkinlik diyagramları, bir işletmenin, sistemin veya programın eylemleri arasındaki denetim ve bilgi akışını görselleştirmenize ve açıklamanıza yardımcı olur. Bu, diğer kişilerle iletişim kurarken iş akışını tanımlamanın basit ve kullanışlı bir yoludur.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklama**|
|-----------------|---------------------|
|Kullanım örneği diyagramı|Her aktörün gerçekleştirdiği etkinlikleri özetleyin.<br /><br /> Bkz.<br /><br /> -   [UML Kullanım Örneği Diyagramları: Referans](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML Kullanım Örneği Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|
|Bileşen diyagramı|Sistemi, iyi tanımlanmış bir arabirim kümesi aracılığıyla davranış sağlayan veya tüketen yeniden kullanılabilir parçalar topluluğu olarak görselleştirin.<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: Referans](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)|

### <a name="describe-the-system-structure-component-diagrams"></a><a name="DescribeComponents"></a>Sistem Yapısını Açıklayın: Bileşen Diyagramları
 Bileşen diyagramları, bir sistemi iyi tanımlanmış bir arabirim kümesi aracılığıyla davranış sağlayan veya tüketen payada parçaların bir koleksiyonu olarak tanımlar. Parçalar herhangi bir ölçekte olabilir ve herhangi bir şekilde bağlanabilir.

 Lucerne ve Dinner Now'un sistemin bileşenlerini ve arabirimlerini görselleştirmesine ve tartışmasına yardımcı olmak için aşağıdaki bileşen diyagramlarını oluştururlar:

 ![Ödeme sistemindeki dış bileşenler](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")

 **Şimdi Akşam Yemeği ödeme sisteminin bileşenleri**

 Bu diyagram, farklı bileşen türlerini ve *bunların bağımlılıklarını*gösterir. Örneğin, hem Şimdi Akşam Yemeği Web Sitesi hem de Lucerne Ödeme Sistemi, ödemeleri doğrulamak için Harici Ödeme İşlemcisi Ağ Geçidi'ni gerektirir. Bileşenler arasındaki oklar, hangi bileşenlerin diğer bileşenlerin işlevselliğini gerektirdiğini gösteren bağımlılıkları temsil eder.

 Lucerne Ödeme Sistemi'ni kullanmak için, Şimdi Akşam Yemeği Web Sitesi, Lucerne Ödeme Sistemi'ndeki Ödeme Onayı ve PayableInekleme arayüzlerini kullanmak için güncelleştirilmelidir.

 Aşağıdaki diyagram, Şimdi Akşam Yemeği Web Sitesi için bileşenlerin belirli bir yapılandırmasını gösterir. Bu yapılandırma, Web sitesinin herhangi bir örneğinin dört *bölümden*oluştuğunu gösterir:

- Müşteri İşleme

- Sipariş İşlemi

- İncelemeİşlem

- Paymentprocessing

  Bu parçalar belirtilen bileşen türlerinin örnekleridir ve aşağıdaki gibi bağlanır:

  ![Dinner Now Web sitesinin içindeki bileşenler](../modeling/media/uml-dinnernow.png "UML_DinnerNow")

  **Şimdi Akşam Yemeği Web Sitesi İçindeki Bileşenler**

  Şimdi Akşam Yemeği Web Sitesi, davranışlarını Web sitesinin işlevlerini yürüten bu bölümlere devreder. Üst bileşen ve üye bileşenleri arasındaki oklar, üst biriminin arabirimleri aracılığıyla hangi parçaların aldığı veya gönderdiği iletileri işleyeceğini belirten *delegasyonlar* gösterir.

  Bu yapılandırmada, PaymentProcessing bileşeni müşteri ödemelerini işler. Bu nedenle, Lucerne ödeme sistemi ile entegre etmek için güncelleştirilmelidir. Diğer senaryolarda, bileşen türünün birden çok örneği aynı üst bileşende bulunabilir.

  Bkz.

- [UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)

- [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="drawing-a-component-diagram"></a>Bileşen Diyagramı Çizme
 Bileşen diyagramı aşağıdaki temel özelliklere sahiptir:

- Sistem işlevselliğinin ayrılmaz parçalarını temsil eden *bileşenler.*

- Bileşenlerin uyguladığı ve diğer bileşenler veya dış sistemler tarafından kullanıldığı ileti veya çağrı gruplarını temsil eden *sağlanan arabirim bağlantı noktaları.*

- İleti veya çağrı gruplarını temsil eden, bileşenlerin diğer bileşenlere veya dış sistemlere gönderdiği *gerekli arabirim bağlantı noktaları.* Bu tür bir bağlantı noktası, bir bileşenin en azından diğer bileşenlerden veya dış sistemlerden beklediği işlemleri açıklar.

- *Parçalar* bileşenlerin üyeleridir ve genellikle diğer bileşenlerin örnekleridir. Bir parça, üst bileşenin iç tasarımının bir parçasıdır.

- Bileşenleri gösteren *bağımlılıklar* diğer bileşenlerin işlevselliğini gerektirir.

- Bileşenin bölümlerini gösteren *temsilcilikler,* üst bileşenden gönderilen veya alınan iletileri işler.

  Bkz.

- [UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)

- [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="summary-strengths-of-component-diagrams"></a>Özet: Bileşen Diyagramlarının Güçlü Yönleri
 Bileşen diyagramları görselleştirmenize yardımcı olur:

- Uygulama dili veya stiline bakılmaksızın, ayrılmaz parçalardan oluşan bir koleksiyon olarak sistem.

- İyi tanımlanmış arabirimlere sahip bileşenler, gereksinimlerin değişmesiyle tasarımın anlaşılmasını ve güncellendirin.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklama**|
|-----------------|---------------------|
|Kod haritası|Varolan kodda organizasyonu ve ilişkileri görselleştirin.<br /><br /> Bileşenler için adayları belirlemek için bir kod eşlemi oluşturun ve öğeleri sistemdeki işlevlerine göre gruplayın.<br /><br /> Bkz.<br /><br /> -   [Çözümlerinizde bağımlılıkları haritala](../modeling/map-dependencies-across-your-solutions.md)|
|Sıralı diyagram|Bileşenler veya bileşenin içindeki parçalar arasındaki etkileşim sırasını görselleştirin.<br /><br /> Bileşenden bir dizi diyagramında yaşam çizgisi oluşturmak için bileşeni sağ tıklatın ve ardından **Yaşam Çizgisi Oluştur'u**tıklatın.<br /><br /> Bkz.<br /><br /> -   [UML Sıra Diyagramları: Referans](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML Sıra Diyagramları: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|
|Sınıf diyagramı (UML)|Sağlanan veya gerekli bağlantı noktalarındaki arabirimleri ve bileşenlerin işlevselliğini uygulayan sınıfları tanımlayın.<br /><br /> Bkz.<br /><br /> -   [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)|
|Katman diyagramı|Bileşenlerle ilgili olarak sistemin mantıksal mimarisini açıklayın. Kodun tasarımla tutarlı kalmasını sağlamak için katman doğrulamayı kullanın.<br /><br /> Bkz.<br /><br /> -   [Kodunuzdan katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)<br />-   [Kodu katman diyagramlarıyla doğrulama](../modeling/validate-code-with-layer-diagrams.md)|
|Etkinlik diyagramı|Bileşenlerin gelen iletilere yanıt olarak gerçekleştirdiği dahili işlemeyi görselleştirin.<br /><br /> Bkz.<br /><br /> -   [UML Etkinlik Diyagramları: Referans](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Varolan Kodu Görselleştir: Kod Haritaları
 Kod eşlemleri, koddaki geçerli organizasyonu ve ilişkileri gösterir. Öğeler haritada *düğümlerle* temsil edilir ve ilişkiler *bağlantılarla*gösterilir. Kod eşlemleri aşağıdaki tür görevleri gerçekleştirmenize yardımcı olabilir:

- Yabancı kodu keşfedin.

- Önerilen değişikliğin varolan kodu nerede ve nasıl etkileyebileceğini anlayın.

- Karmaşıklık alanları, doğal katmanlar veya desenler veya iyileştirmeden yararlanabilecek diğer alanları bulun.

  Örneğin, Şimdi Akşam Yemeği, PaymentProcessing bileşenini güncelleştirme maliyetini tahmin etmelidir. Bu, kısmen bu değişikliğin sistemin diğer bölümlerini ne kadar etkileyeceğine bağlıdır. Bunu anlamalarına yardımcı olmak için, Şimdi Akşam Yemeği geliştiricilerinden biri koddan kod eşlemleri oluşturur ve değişiklikten etkilenebilecek alanlara yönelik kapsam odağı ayarlar.

  Aşağıdaki harita, PaymentProcessing sınıfı ile Seçili görünen Şimdi Akşam Yemeği sisteminin diğer bölümleri arasındaki bağımlılıkları gösterir:

  ![Dinner Now ödeme sistemi için bağımlılık grafiği](../modeling/media/dep-dnpayment.png "Dep_DNPayment")

  **Akşam Yemeği Şimdi ödeme sistemi için kod haritası**

  Geliştirici, PaymentProcessing sınıfını genişleterek ve etkilenen alanları görmek için üyelerini seçerek haritayı inceler:

  ![Ödeme İşlemi ve bağımlılıkları içindeki yöntemler](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")

  **Ödemeİşleme sınıfı içindeki yöntemler ve bunların bağımlılıkları**

  Lucerne Ödeme Sistemi'nin sınıflarını, yöntemlerini ve bağımlılıklarını incelemesi için aşağıdaki haritayı oluştururlar. Ekip, Lucerne sisteminin Şimdi Akşam Yemeği'nin diğer bölümleriyle etkileşime geçmesi için de çalışma gerektirebileceğini görür:

  ![Lucerne ödeme sistemi için bağımlılık grafiği](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")

  **Lucerne Ödeme Sistemi için kod haritası**

  Her iki takım da iki sistemi tümleştirmek için gereken değişiklikleri belirlemek için birlikte çalışır. Güncelleştirmenin daha kolay olması için kodun bir kısmını yeniden düzenlemeye karar verirler. PaymentApprover sınıfı DinnerNow.Business ad alanına taşınır ve bazı yeni yöntemler gerektirir. İşlemleri işleyen Şimdi Akşam Yemeği sınıflarının kendi ad alanı olacaktır. Takımlar, çalışmalarını planlamak, düzenlemek ve izlemek için iş öğeleri oluşturur ve kullanır. Çalışma öğelerini yararlı olduğu öğeleri modellemek için bağlarlar.

  Kodu yeniden düzenledikten sonra, takımlar güncelleştirilmiş yapıyı ve ilişkileri görmek için yeni bir kod eşlemi oluşturur:

  ![Yeniden düzenlenmiş kodlu bağımlılık grafiği](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")

  **Yeniden düzenlenmiş kodlu kod eşlemi**

  Bu harita, PaymentApprover sınıfının artık DinnerNow.Business ad alanında olduğunu ve bazı yeni yöntemleri olduğunu gösterir. Şimdi Akşam Yemeği işlem sınıflarının artık kendi PaymentSystem ad alanına sahip olması, bu kodun daha sonra ele alabilen bir şekilde ele alabilen bir ad alanına sahiptir.

#### <a name="creating-a-code-map"></a>Kod Haritası Oluşturma

- Kaynak koduna hızlı bir genel bakış için, bir kod eşlemi oluşturmak için aşağıdaki adımları izleyin:

     **Mimari** menüsünde Çözüm **Için Kod Haritası Oluştur'u**tıklatın.

     Derlenen kodun hızlı bir özeti için boş bir kod eşlemi oluşturun ve ardından derleme dosyalarını veya ikili dosyaları harita yüzeyine sürükleyin.

- Belirli kod veya çözüm öğelerini keşfetmek için, görselleştirmek istediğiniz öğeleri ve ilişkileri seçmek için Solution Explorer'ı kullanın. Ardından, yeni bir harita oluşturabilir veya varolan bir haritaya seçili öğeler ekleyebilirsiniz. Çözümlerinizde [Harita bağımlılıklarına](../modeling/map-dependencies-across-your-solutions.md)bakın.

- Haritayı keşfetmenize yardımcı olmak için düzeni gerçekleştirmek istediğiniz görev türlerine uygun olacak şekilde yeniden düzenleyin.

     Örneğin, koddaki katmanlamayı görselleştirmek için bir ağaç düzeni seçin. Bkz. [Gözat ve yeniden düzenle kod eşlemleri.](../modeling/browse-and-rearrange-code-maps.md)

#### <a name="summary-strengths-of-code-maps"></a>Özet: Kod Haritalarının Güçlü Yönleri
 Kod haritaları size yardımcı olur:

- Varolan koddaki kuruluş ve ilişkiler hakkında bilgi edinin.

- Önerilen değişikliktan etkilenebilecek alanları belirleyin.

- Kodun korunmasını, değiştirilmesini ve yeniden kullanılmasını kolaylaştırmak için geliştirebileceğin karmaşıklık alanları, desenler, katmanlar veya diğer alanları bulun.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklanır**|
|-----------------|-------------------|
|Katman diyagramı|Sistemin mantıksal mimarisi. Kodun tasarımla tutarlı kalmasını sağlamak için katman doğrulamayı kullanın.<br /><br /> Varolan katmanları veya amaçlanan katmanları belirlemenize yardımcı olmak için bir kod eşlemi oluşturun ve ilgili öğeleri gruplayın. Katman diyagramı oluşturmak için bkz:<br /><br /> -   [Kodunuzdan katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)|
|Bileşen diyagramı|Bileşenler, arayüzleri ve ilişkileri.<br /><br /> Bileşenleri belirlemenize yardımcı olmak için bir kod eşlemi oluşturun ve öğeleri sistemdeki işlevlerine göre gruplayın.<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: Referans](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)|
|Sınıf diyagramı (UML)|Sınıflar, öznitelikleri ve işlemleri ve ilişkileri.<br /><br /> Bu öğeleri tanımlamanıza yardımcı olmak için, bu öğeleri gösteren bir UML sınıfı diyagramı oluşturun.<br /><br /> Bkz.<br /><br /> -   [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)|
|Sınıf diyagramı (kod tabanlı)|Belirli bir proje için koddaki varolan sınıflar.<br /><br /> Varolan bir sınıfı kodda görselleştirmek ve değiştirmek için Sınıf Tasarımcısı'nı kullanın.<br /><br /> [Bkz. Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="describe-the-interactions-sequence-diagrams"></a><a name="DescribeSequence"></a>Etkileşimleri Açıklayın: Sıralı Diyagramlar
 Sıralı diyagramlar, sistemin bölümleri arasındaki bir dizi etkileşimi açıklar. Parçalar herhangi bir ölçekte olabilir. Örneğin, bir programdaki tek tek nesnelerden büyük alt sistemlere veya dış aktörlere kadar değişebilirler. Etkileşimler herhangi bir ölçek ve türde olabilir. Örneğin, tek tek iletilerden genişletilmiş hareketlere kadar değişebilir ve işlev çağrıları veya Web hizmeti iletileri olabilir.

 Lucerne ve Dinner Now'un İşlem Ödemesi kullanım durumundaki adımları tanımlamasına ve tartışmasına yardımcı olmak için bileşen diyagramından aşağıdaki sıralı diyagramı oluştururlar. Yaşam çizgileri Şimdi Akşam Yemeği Web Sitesi bileşenini ve parçalarını yansıtmaktadır. Yaşam çizgileri arasında görünen iletiler bileşen diyagramları üzerindeki bağlantıları izler:

 ![İşlem Ödemesi kullanım örneği için sıralı diyagram](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")

 **İşlem Ödemesi kullanım örneği için sıralı diyagram**

 Sıralı diyagram, müşteri bir sipariş oluşturduğunda, Şimdi Akşam Yemeği Web Sitesi'nin Sipariş İşlemi örneğinde ProcessOrder'ı çağırdığını gösterir. Ardından, OrderProcessing, Ödeme İşleminde ProcessPayment'ı çağırır. Bu, Dış Ödeme İşlemcisi Ağ Geçidi ödemeyi doğrulayana kadar devam eder. Ancak o zaman denetim Şimdi Akşam Yemeği Web Sitesine geri döner.

 Lucerne, Şimdi Akşam Yemeği sistemiyle entegre olmak için ödeme sistemini güncelleştirmenin maliyetini tahmin etmelidir. Bunu anlamalarına yardımcı olmak için, etkilenen kodu görselleştirmek için kod eşlemleri de oluşturabilirler.

 Bkz.

- [UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)

- [UML Sıralı Diyagramlar: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

#### <a name="drawing-a-sequence-diagram"></a>Sıralı Diyagram Çizme
 Bir sıralı diyagram aşağıdaki ana özelliklere sahiptir:

- Dikey *yaşam çizgileri,* yazılım nesnelerinin aktörlerini veya örneklerini temsil eder.

   Bir katılımcının geliştirilmekte olan sistemin dışında olduğunu gösteren bir aktör simgesi eklemek için yaşam çizgisini tıklatın. **Özellikler** penceresinde, **Aktör'u** **True**olarak ayarlayın. **Özellikler** penceresi açık değilse, **F4**tuşuna basın.

- Yatay *iletiler* yöntem çağrılarını, Web hizmeti iletilerini veya başka bir iletişimi temsil eder. *Yürütme oluşumları,* yaşam çizgilerinde görünen ve nesneleri işleme çağrılarısırasındaki dönemleri temsil eden dikey gölgeli dikdörtgenlerdir.

- *Senkron* ileti sırasında, gönderen nesne normal bir işlev \<çağrısında olduğu gibi>> dönmek <denetim bekler. Bir *eşzamanlı* ileti sırasında, gönderen hemen devam edebilir.

- Nesnelerin \<diğer nesneler tarafından yapılmasını belirtmek için>> iletileri oluşturmak <kullanın. Nesneye gönderilen ilk ileti olmalıdır.

  Bkz.

- [UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)

- [UML Sıralı Diyagramlar: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)

#### <a name="summary-strengths-of-sequence-diagrams"></a>Özet: Dizi Diyagramlarının Güçlü Yönleri
 Sıralı diyagramlar görselleştirmenize yardımcı olur:

- Kullanım örneğinin yürütülmesi sırasında aktörler veya nesneler arasında aktarımlar denetim akışı.

- Yöntem çağrısı veya iletisinin uygulanması.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklama**|
|-----------------|---------------------|
|Sınıf diyagramı (UML)|Yaşam çizgilerinin temsil ettiği sınıfları ve yaşam çizgileri arasında gönderilen iletilerde kullanılan parametreleri ve iade değerlerini tanımlayın.<br /><br /> Yaşam çizgisinden bir sınıf oluşturmak için yaşam çizgisine sağ tıklayın ve ardından **Sınıf Oluştur** veya **Arabirim Oluştur'u**tıklatın. Sınıf diyagramındaki bir türden yaşam çizgisi oluşturmak için türü sağ tıklatın ve ardından **Yaşam Çizgisi Oluştur'u**tıklatın.<br /><br /> Bkz.<br /><br /> -   [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)|
|Bileşen diyagramı|Yaşam çizgilerinin temsil ettiği bileşenleri ve iletilerle temsil edilen davranışı sağlayan ve tüketen arabirimleri açıklayın.<br /><br /> Bileşen diyagramından bir yaşam çizgisi oluşturmak için bileşeni sağ tıklatın ve ardından **Yaşam Çizgisi Oluştur'u**tıklatın.<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: Referans](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)|
|Kullanım örneği diyagramı|Bir dizi diyagramındaki kullanıcılar ve bileşenler arasındaki etkileşimleri, kullanıcının hedefini temsil eden bir kullanım örneği olarak özetleyin.<br /><br /> Bkz.<br /><br /> -   [UML Kullanım Örneği Diyagramları: Referans](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML Kullanım Örneği Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a>Türler Sözlüğü Tanımla: Sınıf Diyagramları
 Sınıf diyagramları, sisteme katılan varlıkları, terimleri veya kavramları ve bunların birbirleriyle olan ilişkilerini tanımlar. Örneğin, uygulama dillerinden veya stillerinden bağımsız olarak, her sınıfın özniteliklerini ve işlemlerini açıklamak için geliştirme sırasında bu diyagramları kullanabilirsiniz.

 Lucerne'in İşlem Ödemesi kullanım örneğine katılan varlıkları tanımlamasına ve tartışmasına yardımcı olmak için aşağıdaki sınıf diyagramını çizerler:

 ![Sınıf diyagramında Ödeme varlıklarını işleme](../modeling/media/uml-payentities.png "UML_PayEntities")

 **Sınıf diyagramında Ödeme varlıklarını işleme**

 Bu diyagram, müşterinin siparişler için ödeme yapmak için birçok siparişe ve farklı yöntemlerine sahip olabileceğini gösterir. BankAccount ve CreditCard'ın her ikisi de Ödeme'den devralır.

 Geliştirme sırasında Lucerne, her sınıfın ayrıntılarını açıklamak ve tartışmak için aşağıdaki sınıf diyagramını kullanır:

 ![Sınıf diyagramında Ödeme birimi ayrıntılarını işleme](../modeling/media/uml-payment.png "UML_Payment")

 **Sınıf diyagramında Ödeme yi işleme**

 Bkz.

- [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)

- [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)

#### <a name="drawing-a-class-diagram"></a>Sınıf Diyagramı Çizme
 Sınıf diyagramı aşağıdaki temel özelliklere sahiptir:

- Sınıflar, arabirimler ve sayısallaştırmalar gibi türler:

  - *Sınıf,* belirli yapısal veya davranışsal özellikleri paylaşan nesnelerin tanımıdır.

  - *Arabirim,* nesnenin dışarıdan görünen davranışının bir bölümünü tanımlar.

  - *Numaralandırma,* gerçek değerlerin listesini içeren bir sınıflandırıcıdır.

- *Öznitelikler,* bir *sınıflandırıcının*her örneğini açıklayan belirli bir türdeki değerlerdir. Sınıflandırıcı türleri, bileşenleri, kullanım örnekleri ve hatta aktörler için genel bir addır.

- *İşlemler,* sınıflandırıcı örneklerinin gerçekleştirebileceği yöntemler veya işlevlerdir.

- *İlişkilendirme,* iki sınıflandırıcı arasında bir tür ilişki gösterir.

  - *Toplama,* sınıflandırıcılar arasında paylaşılan bir sahipliği gösteren bir ilişkilendirmedir.

  - *Kompozisyon,* sınıflandırıcılar arasındaki tam bir parça ilişkisini gösteren bir ilişkidir.

    Toplamaları veya kompozisyonları göstermek **için, Toplama** özelliğini bir ilişkilendirme üzerine ayarlayın. **Paylaşılan** toplamaları gösterir ve **Bileşik** kompozisyonları gösterir.

- *Bağımlılık,* bir sınıflandırıcının tanımını değiştirmenin başka bir sınıflandırıcının tanımını değiştirebileceğini gösterir.

- *Genelleme,* belirli bir sınıflandırıcının tanımının bir kısmını genel bir sınıflandırıcıdan devraldığına işaret eder. *Gerçekleştirme,* bir sınıfın bir arabirim tarafından sunulan işlemleri ve öznitelikleri uyguladığını gösterir.

   Bu ilişkileri oluşturmak için **Devralma** aracını kullanın. Alternatif olarak, bir gerçekleştirme bir *lolipop*olarak temsil edilebilir.

- *Paketler* sınıflandırıcılar, ilişkilendirmeler, yaşam çizgileri, bileşenler ve diğer paketler den oluşan gruplardır. *Alma* ilişkileri, bir paketin başka bir paketin tüm tanımlarını içerdiğini gösterir.

  Varolan sınıfları keşfetmek ve tartışmak için bir başlangıç noktası olarak, koddan sınıf diyagramları oluşturmak için Sınıf Tasarımcısı'nı kullanabilirsiniz.

  Bkz.

- [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)

- [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Özet: Sınıf Diyagramlarının Güçlü Yönleri
 Sınıf diyagramları tanımlamanıza yardımcı olur:

- Kullanıcıların gereksinimlerini ve sisteme katılan varlıkları tartışırken kullanılacak ortak bir terimler sözlüğü. [Bkz. Model kullanıcı gereksinimleri.](../modeling/model-user-requirements.md)

- Uygulamalarından bağımsız olarak, bileşenler gibi sistemin parçaları tarafından kullanılan türler. Uygulamanızın [mimarisini modelle'ye](../modeling/model-your-app-s-architecture.md)bakın.

- Türler arasındaki bağımlılıklar gibi ilişkiler. Örneğin, bir türün başka bir türün birden çok örneğiyle ilişkilendirilebileceğini gösterebilirsiniz.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklama**|
|-----------------|---------------------|
|Kullanım örneği diyagramı|Kullanım örneklerindeki hedefleri ve adımları açıklamak için kullanılan türleri tanımlayın.<br /><br /> Bkz.<br /><br /> -   [UML Kullanım Örneği Diyagramları: Referans](../modeling/uml-use-case-diagrams-reference.md)<br />-   [UML Kullanım Örneği Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|
|Etkinlik diyagramı|Nesne düğümlerinden, giriş pimlerinden, çıkış pinlerinden ve etkinlik parametre düğümlerinden geçen veri türlerini tanımlayın.<br /><br /> Bkz.<br /><br /> -   [UML Etkinlik Diyagramları: Referans](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|
|Bileşen diyagramı|Bileşenleri, arabirimlerini ve ilişkilerini açıklayın. Bir sınıf da tam bir bileşeni açıklayabilir.<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: Referans](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)|
|Katman diyagramı|Sınıflarla ilgili olarak sistemin mantıksal mimarisini tanımlayın.<br /><br /> Kodun tasarımla tutarlı kalmasını sağlamak için katman doğrulamayı kullanın.<br /><br /> Bkz.<br /><br /> -   [Kodunuzdan katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)<br />-   [Kodu katman diyagramlarıyla doğrulama](../modeling/validate-code-with-layer-diagrams.md)|
|Sıralı diyagram|Yaşam çizgisinin alabileceği tüm iletiler için yaşam çizgilerinin ve işlemlerin, parametrelerin ve iade değerlerini tanımlayın.<br /><br /> Sınıf diyagramındaki bir türden yaşam çizgisi oluşturmak için türü sağ tıklatın ve ardından **Yaşam Çizgisi Oluştur'u**tıklatın.<br /><br /> Bkz.<br /><br /> -   [UML Sıra Diyagramları: Referans](../modeling/uml-sequence-diagrams-reference.md)<br />-   [UML Sıra Diyagramları: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|
|Kod haritası|Varolan kodda organizasyonu ve ilişkileri görselleştirin.<br /><br /> Sınıfları, ilişkilerini ve yöntemlerini tanımlamak için, bu öğeleri gösteren bir kod eşlemi oluşturun.<br /><br /> Bkz.<br /><br /> -   [Çözümlerinizde bağımlılıkları haritala](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-layer-diagrams"></a><a name="DescribeLayers"></a>Mantıksal Mimariyi Açıkla: Katman Diyagramları
 Katman diyagramları, çözümünüzdeki yapıları soyut gruplar veya *katmanlar*halinde düzenleyerek bir sistemin mantıksal mimarisini açıklar. Eserler ad alanları, projeler, sınıflar, yöntemler ve benzeri birçok şey olabilir. Katmanlar, yapıtların sistemde gerçekleştirdiği rolleri veya görevleri temsil eder ve açıklar. Kodun tasarımıyla tutarlı kaldığından emin olmak için yapı ve iade işlemlerinize katman doğrulama da ekleyebilirsiniz.

 Kodu tasarımla tutarlı tutmak için, Şimdi Akşam Yemeği ve Lucerne, kodları geliştikçe doğrulamak için aşağıdaki katman diyagramını kullanır:

 ![Entegre ödeme sisteminin katman diyagramı](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Şimdi Lucerne ile entegre Akşam Yemeği için Katman diyagramı**

 Bu diyagramdaki katmanlar, karşılık gelen Şimdi Akşam Yemeği ve Lucerne çözüm yapılarına bağlanır. Örneğin, İş katmanı DinnerNow.Business ad alanına ve şimdi PaymentApprover sınıfını içeren üyelerine bağlanır. Kaynak Erişimi katmanı DinnerNow.Data ad alanına bağlanır. Oklar veya *bağımlılıklar,* Kaynak Erişim katmanındaki işlevselliği yalnızca İş katmanının kullanabileceğini belirtir. Takımlar kodlarını güncellerken, çakışmaları oluştukları anda yakalamak ve ekiplerin bunları hemen çözmesine yardımcı olmak için katman doğrulama düzenli olarak gerçekleştirilir.

 Ekipler, iki sistemi aşamalı olarak tümleştirmek ve test etmek için birlikte çalışır. Onlar ilk PaymentApprover ve Dinner Now geri kalanı onlar PaymentProcessing ile uğraşmadan önce birbirleriyle başarılı bir şekilde çalışmak emin olun.

 Aşağıdaki kod haritası, Şimdi Akşam Yemeği ve PaymentApprover arasındaki yeni aramaları gösterir:

 ![Entegre sistemile güncelleştirilmiş bağımlılık grafiği](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")

 **Güncelleştirilmiş yöntem çağrıları ile kod haritası**

 Sistemin beklendiği gibi çalıştığını doğruladıktan sonra, Dinner Now Ödeme İşlemi kodunu yorumlar. Katman doğrulama raporları temizdir ve ortaya çıkan kod eşlemi, başka Ödeme İşleme bağımlılığı olmadığını gösterir:

 ![PaymentProcessing olmadan bağımlılık grafiği](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")

 **PaymentProcessing olmadan kod haritası**

#### <a name="drawing-a-layer-diagram"></a>Katman Diyagramı Çizme
 Katman diyagramı aşağıdaki temel özelliklere sahiptir:

- *Katmanlar* mantıksal yapı gruplarını açıklar.

- *Bağlantı,* katman ve yapı arasındaki ilişkidir.

   Yapılardan katmanlar oluşturmak için, Öğeleri Çözüm Gezgini'nden, kod eşlerinden, Sınıf Görünümü'nden veya Nesne Tarayıcısından sürükleyin. Yeni katmanlar çizmek ve bunları yapılara bağlamak için, katmanları oluşturmak için araç kutusunu kullanın veya diyagram yüzeyini sağ tıklatın ve sonra öğeleri bu katmanlara sürükleyin.

   Katmandaki sayı, katmana bağlı yapıların sayısını gösterir. Bu yapılar ad alanları, projeler, sınıflar, yöntemler ve benzeri olabilir. Katmandaki yapıt sayısını yorumlarken aşağıdakileri unutmayın:

  - Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.

     Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.

  - Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.

    Katmana bağlı yapıları görmek için katmana sağ tıklayın ve ardından **Katman Gezgini'ni**açmak için **Bağlantıları Görüntüle'yi** tıklatın.

- *Bağımlılık,* bir katmanın işlevselliği başka bir katmanda kullanabileceğini, ancak tam tersi olmadığını gösterir. *Çift yönlü bağımlılık,* bir katmanın işlevselliği başka bir katmanda kullanabileceğini gösterir ve bunun tersi de geçerlidir.

   Katman diyagramında varolan bağımlılıkları görüntülemek için diyagram yüzeyini sağ tıklatın ve sonra **Bağımlılıkları Oluştur'u**tıklatın. Amaçlanan bağımlılıkları açıklamak için yenilerini çizin.

  Bkz.

- [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)

- [Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)

- [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-layer-diagrams"></a>Özet: Katman Diyagramlarının Güçlü Yönleri
 Katman diyagramları size yardımcı olur:

- Bir sistemin mantıksal mimarisini yapıl›n› eserlerinin işlevselliğine göre tan›mlay›n.

- Geliştirme aşamasındaki kodun belirtilen tasarıma uydur emin olun.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklama**|
|-----------------|---------------------|
|Kod haritası|Varolan kodda organizasyonu ve ilişkileri görselleştirin.<br /><br /> Katmanlar oluşturmak için bir kod eşlemi oluşturun ve ardından haritadaki öğeleri olası katmanlar olarak gruplayın. Grupları haritadan katman diyagramına sürükleyin.<br /><br /> Bkz.<br /><br /> -   [Çözümlerinizde bağımlılıkları haritala](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Kod haritalarına göz atın ve yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)|
|Bileşen diyagramı|Bileşenleri, arabirimlerini ve ilişkilerini açıklayın.<br /><br /> Katmanları görselleştirmek için, sistemdeki farklı bileşenlerin işlevselliğini açıklayan bir bileşen diyagramı oluşturun.<br /><br /> Bkz.<br /><br /> -   [UML Bileşen Diyagramları: Referans](../modeling/uml-component-diagrams-reference.md)<br />-   [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)|

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Bağlantılar**|
|------------------|---------------|
|**Forumlar**|-   [Visual Studio Visualization & Modelleme Araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualization & Modelleme SDK (DSL Araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Ayrıca Bkz.
 [Görselleştir kod](../modeling/visualize-code.md) [Uygulamanız için modelleri oluşturun](../modeling/create-models-for-your-app.md) Geliştirme [sürecinizde modelleri çevik](../modeling/use-models-in-your-development-process.md) [geliştirmede kullanın](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) Geliştirme sırasında [sisteminizi doğrulayın](../modeling/validate-your-system-during-development.md) [UML modellerini ve diyagramlarını genişletin](../modeling/extend-uml-models-and-diagrams.md)
