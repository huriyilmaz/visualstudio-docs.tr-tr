---
title: 'Senaryo: görselleştirme ve modelleme kullanarak tasarımınızı değiştirme | Microsoft Docs'
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
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918977"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yazılım sisteminizin, Visual Studio 'da görselleştirme ve modelleme araçlarını kullanarak kullanıcıların ihtiyaçlarını karşıladığından emin olun. Birleşik Modelleme Dili (UML) diyagramları, kod haritaları, katman diyagramları ve sınıf diyagramları gibi araçları kullanarak şunları yapın:

 Visual Studio 'nun hangi sürümlerinin her bir aracı desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

- Kullanıcıların gereksinimlerini ve iş süreçlerini açıklığa kavuşturun.

- Mevcut kodu görselleştirin ve araştırın.

- Mevcut bir sistemdeki değişiklikleri açıkla.

- Sistemin gereksinimlerini karşıladığını doğrulayın.

- Kodu tasarımla tutarlı tutun.

  Bu izlenecek yol:

- Bu araçların yazılım projenize nasıl yararlanabileceği açıklanır.

- Geliştirme yaklaşımınıza bakılmaksızın bu araçları örnek bir senaryoyla nasıl kullanabileceğinizi gösterir.

  Bu araçlar ve destekledikleri senaryolar hakkında daha fazla bilgi edinmek için bkz.:

- [Mimariyi Çözümleme ve Mimarinin Modelini Oluşturma](../modeling/analyze-and-model-your-architecture.md)

- [Kodu görselleştirme](../modeling/visualize-code.md)

- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)

## <a name="ScenarioOverview"></a>Senaryoya genel bakış
 Bu senaryo, iki kurgusal şirketin yazılım geliştirme yaşam döngülerine ait bölümleri açıklar: şimdi akşam yemeği ve Lucerne Publishing. Şimdi akşam yemeği Seattle 'da Web tabanlı bir yiyecek teslim hizmeti sağlar. Müşteriler şimdi akşam yemeği Web sitesinde yemekleri sipariş edebilir ve ödeyebilir. Daha sonra siparişler teslim için uygun yerel restora gönderilir. New York 'ta bir şirket olan Lucerne Publishing, hem kapalı hem de Web üzerinde çalışan birkaç işletme. Örneğin, müşterilerin Restoran İncelemeleri nakledebileceği bir Web sitesi çalıştırırlar.

 Kısa süre önce Dinner Now alındı ve aşağıdaki değişiklikleri yapmak istiyor:

- Şimdi akşam yemeği 'e Restoran gözden geçirme özellikleri ekleyerek Web sitelerini tümleştirin.

- Dinner Now 'ın ödeme sistemini Lucerne 'ın sistemiyle değiştirin.

- Şimdi akşam yemeği hizmetini bölge genelinde genişletin.

  Şimdi Akşam Yemeği SCRUM ve eXtreme programlama kullanıyor. Bunlar çok yüksek test kapsamına ve çok az desteklenmeyen koda sahiptir. Bir sistemin küçük ancak çalışan sürümlerini oluşturup daha sonra işlevselliği artımlı olarak ekleyerek riskleri en aza indirirler. Bunlar, kodlarını kısa ve sık sık yinelemeler üzerinde geliştirir. Bu, hafif bir şekilde değişiklik yapmayı, kodu sık yeniden düzenlemenizi ve "büyük tasarım önünden" kaçınmasını sağlar.

  Lucerne, bazıları 40 yılı aşkın olan büyük ölçüde daha büyük ve karmaşık bir sistem koleksiyonunu tutar. Eski kodların karmaşıklığı ve kapsamı nedeniyle değişiklik yapma konusunda çok dikkatli olurlar. Daha kapsamlı bir geliştirme sürecini izleyerek, ayrıntılı çözümler tasarlamayı ve geliştirme sırasında oluşan tasarımı ve değişiklikleri belgelemeyi tercih ederler.

  Her iki ekip, kullanıcıların ihtiyaçlarını karşılayan sistemler geliştirmeye yardımcı olmak için Visual Studio 'da modelleme diyagramları kullanır. Bunlar, işlerini planlamaya, düzenlemenize ve yönetmesine yardımcı olması için diğer araçlarla birlikte Team Foundation Server kullanırlar.

  Team Foundation Server hakkında daha fazla bilgi için bkz.:

- [İşleri planlama ve izleme](#PlanningTracking)

- [Test, doğrulama ve güncelleştirilmiş kodu iade etme](#TestValidateCheckInCode)

## <a name="ModelingDiagramsTools"></a>Yazılım geliştirmede mimari ve modelleme diyagramları rolleri
 Aşağıdaki tabloda, bu araçların yazılım geliştirme yaşam döngüsünün birden çok ve çeşitli aşamaları sırasında oynayabileceği roller açıklanmaktadır:

||**Kullanıcı gereksinimleri Modelleme**|**İş süreci modelleme**|**Sistem mimarisi & tasarımı**|**Kod görselleştirme & araştırması**|**Doğrulamayı**|
|------|------------------------------------|-----------------------------------|--------------------------------------|------------------------------------------|----------------------|
|Kullanım durumu diyagramı (UML)|√|√|||√|
|Etkinlik diyagramı (UML)|√|√|√||√|
|Sınıf diyagramı (UML)|√|√|√||√|
|Bileşen diyagramı (UML)|√|√|√||√|
|Sıralı diyagram (UML)|√|√|√||√|
|Etki alanına özgü dil (DSL) diyagramı|√|√|√|||
|Katman diyagramı, katman doğrulama|||√|√|√|
|Kod eşlemesi|||√|√|√|
|Sınıf Tasarımcısı (kod tabanlı)||||√||

 UML diyagramları ve katman diyagramları çizmek için, mevcut bir çözümün parçası olarak bir modelleme projesi oluşturmanız veya yeni bir tane oluşturmanız gerekir. Bu diyagramların modelleme projesinde oluşturulması gerekir. UML diyagramlarındaki öğeler ortak bir modelin parçasıdır ve UML diyagramları bu modelin görünümleridir. Katman diyagramlarındaki öğeler modelleme projesinde bulunur, ancak ortak modelde depolanmaz. Kod haritaları ve koddan oluşturulan .NET sınıf diyagramları, modelleme projesi dışında bulunur.

 Bkz.

- [UML modelleme projeleri ve diyagramları oluşturma](../modeling/create-uml-modeling-projects-and-diagrams.md)

- [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

  Mimarinin alternatif görünümlerini göstermek için, aynı modeldeki belirli öğeleri birden çok veya farklı diyagramda yeniden kullanabilirsiniz. Örneğin, bir bileşeni bir aktör olarak işlev görebilmesi için başka bir bileşen diyagramına veya bir dizi diyagramına sürükleyebilirsiniz. Bkz. [UML modellerini ve diyagramlarını düzenleme](../modeling/edit-uml-models-and-diagrams.md).

  Her iki ekip de geliştirme aşamasındaki kodun tasarımla tutarlı kalmasını sağlamak için katman doğrulaması kullanır.

  Bkz.

- [Kodu tasarımla tutarlı tutma](#ValidatingCode)

- [Mantıksal mimariyi açıkla: katman diyagramları](#DescribeLayers)

- [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

  > [!NOTE]
  > Visual Studio 'nun bazı sürümleri, katman doğrulama ve kod eşlemelerinin salt okuma sürümlerini destekler ve görselleştirme ve modelleme için UML diyagramlarıdır. Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="UnderstandingCommunicating"></a>Sistemle ilgili bilgileri anlama ve Iletişim kurma
 Visual Studio Modelleme diyagramlarının kullanılması için önceden tanımlanmış bir sıra yoktur, bu sayede gereksinimlerinize veya yaklaşımlarınıza uygun şekilde kullanabilirsiniz. Genellikle takımlar modellerini bir proje boyunca tekrarlayarak ve sık sık yeniden ziyaret edin. Her diyagram, geliştirme aşamasındaki sistemin farklı yönlerini anlamanıza, açıklamanıza ve iletmede size yardımcı olmak için belirli güçler sunar.

 Şimdi akşam yemeği ve Lucerne, ortak dil olarak diyagramları kullanarak birbirleriyle ve proje hissedarlarıyla birlikte iletişim kurar. Örneğin, şimdi akşam yemeği bu görevleri gerçekleştirmek için diyagramlar kullanmaktadır:

- Mevcut kodu görselleştirin.

- Yeni veya güncelleştirilmiş Kullanıcı hikayeleri hakkında Lucerne ile iletişim kurun.

- Yeni veya güncelleştirilmiş kullanıcı hikayelerini desteklemek için gereken değişiklikleri belirler.

  Lucerne bu görevleri gerçekleştirmek için diyagramlar kullanır:

- Şimdi akşam yemeği iş süreci hakkında bilgi edinin.

- Sistemin tasarımını anlayın.

- Yeni veya güncelleştirilmiş kullanıcı gereksinimleri hakkında şimdi akşam yemeği ile iletişim kurun.

- Sisteme belge güncelleştirmeleri.

  Diyagramlar Team Foundation Server ile tümleşiktir, böylece takımlar işlerini daha kolay bir şekilde planlayabilir, yönetebilir ve izleyebilir. Örneğin, test çalışmalarını ve geliştirme görevlerini tanımlamak ve bunların çalışmalarını tahmin etmek için modeller kullanırlar. Lucerne bağlantıları, ilerlemeyi izleyebilmek ve sistemin Kullanıcı gereksinimlerini karşıladığından emin olmak için iş öğelerini model öğelerine Team Foundation Server. Örneğin, tüm testler başarılı olduğunda kullanım örneklerinin yerine getirildiğini görebilmesi için kullanım örneklerini test çalışması iş öğelerine bağlar.

  Ekipler değişikliklerini iade etmeden önce, katman doğrulama ve otomatikleştirilmiş testler içeren yapılar çalıştırarak, testleri ve tasarıma karşı kodu doğrular. Bu, güncelleştirilmiş kodun tasarım ve daha önce çalışan işlevlerle çakışmadığından emin olmanıza yardımcı olur.

  Bkz.

- [İş sürecinde sistemin rolünü anlama](#UnderstandingBPMandSystemDesign)

- [Yeni veya güncelleştirilmiş Kullanıcı gereksinimlerini açıklama](#DescribingURM)

- [Modellerden testler oluşturma](#CreatingTests)

- [Mevcut sistemde yapılan değişiklikleri tanımlama](#DeterminingChanges)

- [Kodu tasarımla tutarlı tutma](#ValidatingCode)

- [Model oluşturma ve kullanma hakkında genel ipuçları](#GeneralTips)

- [İşleri planlama ve izleme](#PlanningTracking)

- [Test, doğrulama ve güncelleştirilmiş kodu iade etme](#TestValidateCheckInCode)

### <a name="UnderstandingBPMandSystemDesign"></a>Iş sürecinde sistemin rolünü anlama
 Lucerne Şimdi akşam yemeği iş süreci hakkında daha fazla bilgi edinmek istiyor. Şimdi akşam yemeği ile daha kolay bir şekilde öğrenmelerini netleştirmek için aşağıdaki diyagramları oluşturırlar:

|**Çizimindeki**|**Anlatır**|
|-----------------|-------------------|
|*Kullanım durumu diyagramı (UML)*<br /><br /> Bkz.<br /><br /> [UML Kullanım örneği diyagramları -   : başvuru](../modeling/uml-use-case-diagrams-reference.md)<br />[UML Kullanım örneği diyagramları -   : yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|-Dinner Now sisteminin desteklediği etkinlikler<br />-Etkinlikleri gerçekleştiren insanlar ve dış sistemler<br />-Her etkinliği destekleyen sistemin ana bileşenleri<br />-İş sürecinin, geçerli sistemin kapsamı dışında olan kısımları, örneğin yiyecek teslimatı|
|*Etkinlik diyagramı (UML)*<br /><br /> Bkz.<br /><br /> [UML etkinlik diyagramları -   : başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|Bir müşteri sipariş oluşturduğunda ortaya çıkan adımların akışı|
|*Sınıf diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|Tartışmada kullanılan iş varlıkları ve şartlar ve bu varlıklar arasındaki ilişkiler. Örneğin, düzen ve menü öğesi Bu senaryodaki sözlük 'in bir parçasıdır.|

 Örneğin, Lucerne Şimdi akşam yemeği Web sitesinde gerçekleştirilen ve bunları gerçekleştiren görevleri anlamak için aşağıdaki kullanım örneği diyagramını oluşturur:

 ![UML Kullanım durumu diyagramı](../modeling/media/uml-usecase.png "UML_UseCase")

 **UML Kullanım durumu diyagramı**

 Aşağıdaki etkinlik diyagramı, bir müşteri şimdi akşam yemeği Web sitesinde bir sipariş oluşturduğunda adımların akışını açıklar. Bu sürümde, açıklamaları role göre düzenleyen, bu sürümde rolleri ve satır *kulvarları*oluştur öğelerini belirler:

 ![UML etkinlik diyagramı](../modeling/media/uml-dinnernowprocess.png "UML_DinnerNowProcess")

 **UML etkinlik diyagramı**

 Aşağıdaki sınıf diyagramı, sipariş işlemine katılan varlıkları açıklar:

 ![UML sınıf diyagramı](../modeling/media/uml-dinnerorders.png "UML_DinnerOrders")

 **UML sınıf diyagramı**

### <a name="DescribingURM"></a>Yeni veya güncelleştirilmiş Kullanıcı gereksinimlerini açıklama
 Lucerne, müşterilerin Restoran incelemelerini okuyabilmeleri ve katkıda bulunmak için şimdi akşam yemeği sistemine işlevsellik eklemek istemektedir. Bunlar, şimdi akşam yemeği ile bu yeni gereksinimi açıklayacak ve tartışabilmeleri için aşağıdaki diyagramları güncelleştirirler:

|**Çizimindeki**|**Anlatır**|
|-----------------|-------------------|
|*Kullanım durumu diyagramı (UML)*<br /><br /> Bkz.<br /><br /> [UML Kullanım örneği diyagramları -   : başvuru](../modeling/uml-use-case-diagrams-reference.md)<br />[UML Kullanım örneği diyagramları -   : yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|"Restoran incelemesi yaz" için yeni bir kullanım durumu|
|*Etkinlik diyagramı (UML)*<br /><br /> Bkz.<br /><br /> [UML etkinlik diyagramları -   : başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|Müşteri bir restoran incelemesi yazmak istediğinde oluşan adımlar|
|*Sınıf diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|Bir incelemeyi depolamak için gereken veriler|

 Örneğin, aşağıdaki kullanım durumu diyagramı yeni gereksinimi göstermek için yeni bir "Gözden geçirme yazma" kullanım durumu içerir. Daha kolay tanımlama için diyagramda Turuncu renkle vurgulanır:

 ![UML Kullanım durumu diyagramı](../modeling/media/uml-writerev.png "UML_WriteRev")

 **UML Kullanım örneği diyagramı**

 Aşağıdaki etkinlik diyagramı, yeni kullanım çalışmasında adımların akışını betimleyen turuncu içindeki yeni öğeleri içerir:

 ![UML etkinlik diyagramı](../modeling/media/uml-writereview.png "UML_WriteReview")

 **UML etkinlik diyagramı**

 Aşağıdaki sınıf diyagramı, ekiplerin ayrıntılarını tartışabilmesi için yeni bir gözden geçirme sınıfı ve diğer sınıflarla ilişkilerini içerir. Bir müşterinin ve restorana, birden çok gözden geçirdiğine dikkat edin:

 ![UML sınıf diyagramı](../modeling/media/uml-dinnerreviews.png "UML_DinnerReviews")

 **UML sınıf diyagramı**

### <a name="CreatingTests"></a>Modellerden testler oluşturma
 Her iki ekip, herhangi bir değişiklik yapmadan önce sistem ve bileşenleri için tüm testlerin bir test kümesine ihtiyacı olduğunu kabul eder. Lucerne, sistem ve bileşen düzeyinde test gerçekleştiren özelleştirilmiş bir ekibe sahiptir. Şimdi akşam yemeği tarafından oluşturulan testleri yeniden kullanır ve UML diyagramlarını kullanarak bu testleri yapısıdır:

- Her kullanım örneği bir veya birden çok test tarafından temsil edilir. Kullanım durumu diyagramı 'ndaki öğeler Team Foundation Server içindeki test çalışması iş öğelerine bağlanır.

- Bir etkinlik diyagramı veya sistem düzeyi sırası diyagramındaki her akış, en azından bir teste bağlanır. Test takımı sistematik olarak, etkinlik diyagramı aracılığıyla olası her yolu test etmelerini sağlar.

- Testleri tanımlamakta kullanılan terimler, kullanım örneği, sınıf ve etkinlik diyagramları tarafından tanımlanan koşullara dayanır.

  Gereksinimler değiştiğinde ve diyagramlar bu değişiklikleri yansıtacak şekilde güncelleştirildiğinden, testler de güncelleştirilir. Bir gereksinim yalnızca testler başarılı olduğunda yerine getirilir olarak değerlendirilir. Mümkün veya pratik olduğunda, uygulama başlamadan önce testler tanımlanır ve UML diyagramlarına dayalıdır.

  Bkz.

- [Model aracılığıyla test geliştirme](../modeling/develop-tests-from-a-model.md)

- [UML modelinizi doğrulama](../modeling/validate-your-uml-model.md)

### <a name="DeterminingChanges"></a>Mevcut sistemde yapılan değişiklikleri tanımlama
 Şimdi akşam yemeği yeni gereksinimin toplantısının maliyetini tahmin etmelidir. Bu, kısmen bu değişikliğin sistemin diğer bölümlerini ne kadar etkileyeceğini gösterir. Bunu anlamalarına yardımcı olmak için Dinner Now geliştiricilerinden biri mevcut koddan bu haritaları ve diyagramları oluşturur:

|**Harita veya diyagram**|**Gösterilir**|
|------------------------|---------------|
|*Kod eşlemesi*<br /><br /> Bkz.<br /><br /> [çözümlerinizin genelinde harita bağımlılıklarını](../modeling/map-dependencies-across-your-solutions.md) -   <br />-   [kod haritalarını gözden geçirme ve yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)<br />-   [dgml dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Koddaki bağımlılıklar ve diğer ilişkiler.<br /><br /> Örneğin, şimdi akşam yemeği derlemeler ve bağımlılıklarına genel bir bakış için derleme kodu eşlemelerini inceleyerek başlayabilir. Bu derlemelerdeki ad alanlarını ve sınıfları araştırmak için Eşlemlerde detaya gidebilirler.<br /><br /> Şimdi akşam yemeği, belirli alanların ve koddaki diğer ilişki türlerinin araştırıp haritalarını da oluşturabilir. Bunları ilgilendiren alanları ve ilişkileri bulmak ve seçmek için Çözüm Gezgini kullanırlar.|
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme (sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Koddaki mevcut sınıflar|

 Örneğin, geliştirici bir kod haritası oluşturur. Yeni senaryodan etkilenecek alanlara odaklanmak için kapsamını ayarlar. Bu bölgeler seçili ve haritada vurgulandı:

 ![Ad alanı bağımlılık grafiği](../modeling/media/namespace-reviewsystem.png "Namespace_ReviewSystem")

 **Ad alanı kod eşlemesi**

 Geliştirici, sınıflarını, yöntemlerini ve ilişkilerini görmek için seçili ad alanlarını genişletir:

 ![Genişletilmiş ad alanı bağımlılık grafiği](../modeling/media/dep-reviewsystem.png "Dep_ReviewSystem")

 **Görünür çapraz grup bağlantılarıyla genişletilmiş ad alanı kod Haritası**

 Geliştirici, etkilenen sınıfları ve yöntemleri bulmak için kodu inceler. Her bir değişikliğin yaptığınız etkileri görmek için her değişiklikten sonra kod haritalarını yeniden oluşturun. Bkz. [Kodu görselleştirme](../modeling/visualize-code.md).

 Bileşenler veya etkileşimler gibi, sistemin diğer bölümlerine yapılan değişiklikleri anlatmak için, takım bu öğeleri beyaz tahtalara çizebilir. Ayrıca ayrıntılar yakalanabilmesi, yönetilmesi ve her iki ekiple anlaşılabilmesi için Visual Studio 'da aşağıdaki diyagramları çizmiş olabilirler:

|**Diyagram**|**Anlatır**|
|------------------|-------------------|
|*Etkinlik diyagramı (UML)*<br /><br /> Bkz.<br /><br /> [UML etkinlik diyagramları -   : başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|Sistem bir müşterinin restorana kadar bir sipariş yerleştirmesini ve müşterinin bir gözden geçirme yazmasını isteyip istemediğini fark ettiğinin ortaya çıkan adımların akışı.|
|*Sınıf diyagramı (UML)*<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|Mantıksal sınıflar ve bunların ilişkileri. Örneğin, bir **gözden geçirmeyi** ve bu Ilişkiyi, **Restoran**, **menü**ve **Müşteri**gibi diğer varlıklarla ilişkilerini tanımlamaya yönelik yeni bir sınıf eklenir.<br /><br /> İncelemeleri bir müşteriyle ilişkilendirmek için, sistemin müşteri ayrıntılarını depolaması gerekir. UML sınıf diyagramı bu ayrıntıların açıklanmasına yardımcı olabilir.|
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme (sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|Koddaki mevcut sınıflar.|
|*Bileşen diyagramı (UML)*<br /><br /> Bkz.<br /><br /> [UML bileşen diyagramlarını -   : başvuru](../modeling/uml-component-diagrams-reference.md)<br />[UML bileşen diyagramlarını -   : yönergeler](../modeling/uml-component-diagrams-guidelines.md)|Sistemin, şimdi akşam yemeği Web sitesi ve arabirimleri gibi üst düzey parçaları. Bu arabirimler, bileşenlerinin, sağladıkları ve tükettiği Yöntemler veya hizmetler aracılığıyla birbirleriyle nasıl etkileşime gireceğini tanımlar.|
|*Sıralı diyagram (UML)*<br /><br /> Bkz.<br /><br /> [UML sıralı diyagramları -   : başvuru](../modeling/uml-sequence-diagrams-reference.md)<br />[UML sıralı diyagramları -   : yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|Örnekler arasındaki etkileşimlerin sırası.|

 Örneğin, aşağıdaki bileşen diyagramı, şimdi akşam yemeği Web sitesi bileşeninin bir parçası olan yeni bileşeni gösterir. Gözden geçirmeler Işleme bileşeni, incelemeler oluşturma işlevlerini işler ve Turuncu renkle vurgulanmış olarak görünür:

 ![UML bileşen diyagramı](../modeling/media/uml-internal.png "UML_Internal")

 **UML bileşen diyagramı**

 Aşağıdaki sıra diyagramı, şimdi akşam yemeği Web sitesi müşterinin bir restorandan önce sipariş edilip edilmeyeceğini denetlediğinde gerçekleşen etkileşimlerin sırasını gösterir. Bu değer doğru ise, müşteriyi restora gönderilen ve Web sitesi tarafından yayımlanan bir gözden geçirme oluşturmasını ister:

 ![UML sıralı diyagram](../modeling/media/uml-revsystem.png "UML_RevSystem")

 **UML sıralı diyagram**

### <a name="ValidatingCode"></a>Kodu tasarımla tutarlı tutma
 Şimdi akşam yemeği, güncelleştirilmiş kodun tasarımla tutarlı kaldığından emin olmalıdır. Bunlar, sistemdeki işlevlerin katmanlarını tanımlayan katman diyagramları oluşturur, aralarında izin verilen bağımlılıkları belirtir ve çözüm yapıtları bu katmanlarla ilişkilendirin.

|**Çizimindeki**|**Anlatır**|
|-----------------|-------------------|
|*Katman diyagramı*<br /><br /> Bkz.<br /><br /> -   [kodunuzda katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />[Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md) -   |Kodun mantıksal mimarisi.<br /><br /> Katman diyagramı, bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çözümündeki yapıtları, *Katmanlar*adlı soyut gruplar halinde düzenler ve eşler. Bu katmanlar, Bu yapıtların sistemde gerçekleştirdiği rolleri, görevleri veya işlevleri belirler.<br /><br /> Katman diyagramları, sistemin amaçlanan tasarımını açıklamak ve bu tasarıma karşı gelişen kodu doğrulamak için kullanışlıdır.<br /><br /> Katmanlar oluşturmak için Çözüm Gezgini, kod haritaları, Sınıf Görünümü ve Nesne Tarayıcısı öğelerini sürükleyin. Yeni Katmanlar çizmek için araç kutusunu kullanın veya Diyagram yüzeyine sağ tıklayın.<br /><br /> Mevcut bağımlılıkları görüntülemek için katman diyagramı yüzeyine sağ tıklayın ve ardından **Bağımlılıklar Oluştur**' a tıklayın. Hedeflenen bağımlılıkları belirtmek için yeni bağımlılıklar çizin.|

 Örneğin, aşağıdaki katman diyagramı katmanlar ve her katmanla ilişkili yapıt sayısı arasındaki bağımlılıkları açıklar:

 ![Tümleşik ödeme sisteminin katman diyagramı](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Katman diyagramı**

 Tasarım ile çakışmaların kod geliştirme sırasında gerçekleşmediğinden emin olmak için takımlar, Team Foundation yapısı üzerinde çalıştırılan yapılar üzerinde katman doğrulaması kullanır. Ayrıca, iade etme işlemlerinde katman doğrulaması gerektirmek için özel bir MSBuild görevi oluşturur. Doğrulama hatalarını toplamak için yapı raporları kullanırlar.

 Bkz.

- [Yapı işleminizi tanımlama](https://msdn.microsoft.com/library/61593e10-d24b-492f-b19a-af4d85abea6b)

- [Değişiklikleri doğrulamak için geçitli iade derleme işlemi kullanma](https://msdn.microsoft.com/library/9cfc8b9c-1023-40fd-8ab5-1b1bd9c172ec)

- [Yapı işlemi şablonunuzu özelleştirme](https://msdn.microsoft.com/library/b94c58f2-ae6f-4245-bedb-82cd114f6039)

### <a name="GeneralTips"></a>Model oluşturma ve kullanma hakkında genel Ipuçları

- Çoğu diyagram satırlara göre bağlanmış düğümlerden oluşur. Her diyagram türü için araç kutusu farklı türlerde düğüm ve satır sağlar.

   Araç kutusunu açmak için, **Görünüm** menüsünden, **araç kutusu**' na tıklayın.

- Bir düğüm oluşturmak için araç kutusundan diyagrama sürükleyin. Belirli düğüm türleri mevcut düğümlere sürüklenmesi gerekir. Örneğin, bir bileşen diyagramında, var olan bir bileşene yeni bir bağlantı noktası eklenmelidir.

- Bir hat veya bağlantı oluşturmak için, araç kutusunda ilgili araca tıklayın, kaynak düğümüne tıklayın ve ardından hedef düğüme tıklayın. Bazı satırlar yalnızca belirli düğüm türleri arasında oluşturulabilir. İşaretçiyi olası bir kaynağın veya hedefin üzerine getirdiğinizde, işaretçi bir bağlantı oluşturup oluşturamayacağını gösterir.

- UML diyagramlarında öğe oluşturduğunuzda, bunları ortak bir modele de eklersiniz. Modelleme projesindeki UML diyagramları söz konusu modelin görünümleridir. Bir katman diyagramındaki öğeler, ortak modelde depolanmasa bile modelleme projesinin bir parçasıdır.

   Modeli görmek için **mimari** menüsünde **Windows**' a gelin ve ardından **UML Model Gezgini**' ne tıklayın.

- Bazı durumlarda, belirli öğeleri **UML Model Gezgini** ' nden UML diyagramına sürükleyebilirsiniz. Aynı modelin içindeki bazı öğeler, mimarinin alternatif görünümlerini göstermek için birden çok veya farklı diyagramda kullanılabilir. Örneğin, bir bileşeni başka bir bileşen diyagramına veya aktör olarak kullanmak için bir dizi diyagramına sürükleyebilirsiniz.

- Visual Studio, UML 2.1.2 'yi 'yi destekler. Bu genel bakış, bu sürümdeki UML diyagramlarının yalnızca önemli özelliklerini açıklar, ancak UML ve kullanımını ayrıntılı olarak tartışan çok sayıda kitap vardır.

  Bkz. [uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md).

### <a name="PlanningTracking"></a>Işleri planlama ve Izleme
 Visual Studio modelleme diyagramları, daha kolay çalışmanızı planlamak, yönetmek ve izlemek için Team Foundation Server ile tümleşiktir. Her iki ekip, test çalışmalarını ve geliştirme görevlerini tanımlamak ve bunların çalışmalarını tahmin etmek için modeller kullanır. Lucerne, kullanım durumları veya bileşenleri gibi model öğelerine Team Foundation Server iş öğeleri oluşturur ve bağlar. Bu, bunların ilerlemesini izlemelerine ve çalışmalarını kullanıcıların gereksinimlerine geri izlemesine yardımcı olur. Bu, onların değişikliklerinin bu gereksinimleri karşılamak için devam etmesini sağlamaya yardımcı olur.

 Çalışmaları ilerledikçe takımlar, iş öğelerini görevlerinde harcadıkları süreyi yansıtacak şekilde güncelleştirir. Ayrıca, aşağıdaki Team Foundation Server özelliklerini kullanarak çalışmalarını izler ve bunlarla ilgili durumu raporlar:

- Günlük *burndown raporları* Planlanan çalışmanın beklenen sürede tamamlanıp tamamlanmayacağını gösterir. Bunlar, hataların ilerlemesini izlemek için Team Foundation Server başka benzer raporlar oluşturur.

- Ekibin üyeleri arasındaki iş yükünü izlemesine ve dengelemeye yardımcı olmak için Microsoft Excel kullanan bir *yineleme çalışma sayfası* . Bu çalışma sayfası Team Foundation Server bağlanır ve normal ilerleme toplantıları sırasında tartışmayı odaklamayı sağlar.

- Ekibin önemli proje bilgileri hakkında bilgi sahibi olmasını sağlamak için Office Project kullanan bir *geliştirme panosu* .

  Bkz.

- [Visual Studio Team Services veya Team Foundation Server kullanarak işi izleyin](https://msdn.microsoft.com/library/52aa8bc9-fc7e-4fae-9946-2ab255ca7503)

- [Model öğelerini ve iş öğelerini bağlama](../modeling/link-model-elements-and-work-items.md)

- [Visual Studio ALM için grafikler, panolar ve raporlar](https://msdn.microsoft.com/library/1f28ba6c-c5e5-46d3-9209-ede24ae78e48)

- [Projeyi kullanarak kapsamınızı ve görevlerinizi oluşturma](https://msdn.microsoft.com/library/be5cef4f-755f-4ffe-8dd7-876d1e02c330)

### <a name="TestValidateCheckInCode"></a>Kodu test etme, doğrulama ve Iade etme
 Takımlar her görevi tamamlarsa, bunların kodunu Team Foundation sürüm denetimine denetler ve Team Foundation Server, unutduklarında anımsatıcıları alır. Team Foundation Server, iadelerini kabul etmeden önce, ekip, kodu test çalışmalarına ve tasarıma karşı doğrulamak için birim testleri ve katman doğrulaması çalıştırır. Derlemeler, otomatik birim testleri ve katman doğrulamasını düzenli olarak çalıştırmak için Team Foundation Server kullanırlar. Bu, kodun aşağıdaki ölçütlere uyduğundan emin olmanıza yardımcı olur:

- İşe yarar.

- Daha önce çalışan kodu bozmaz.

- Tasarım ile çakışmaz.

  Şimdi akşam yemeği, neredeyse hepsi hala uygulandığı için Lucerne 'ın yeniden kullanılabilir olduğu büyük bir otomatik test koleksiyonuna sahiptir. Lucerne ayrıca bu testleri oluşturabilir ve yeni işlevleri kapsayacak yeni işlevler ekleyebilir. Ayrıca, el ile testleri çalıştırmak için Visual Studio 'Yu da kullanabilirsiniz.

  Kodun tasarıma uyduğundan emin olmak için takımlar Team Foundation Build 'teki yapılarını katman doğrulamasını içerecek şekilde yapılandırır. Herhangi bir çakışma oluşursa, ayrıntılarla birlikte bir rapor oluşturulur.

  Bkz.

- [Uygulamayı test etme](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac)

- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)

- [Sürüm denetimini kullanma](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Uygulamayı oluşturun](/azure/devops/pipelines/index)

## <a name="UpdatingSystem"></a>Görselleştirme ve modelleme kullanarak sistemi güncelleştirme
 Lucerne ve Dinner Now ödeme sistemlerini tümleştirmelidir. Aşağıdaki bölümlerde, Visual Studio 'daki modelleme diyagramları bu görevi gerçekleştirmelerine yardımcı olur:

- [Kullanıcı gereksinimlerini anlayın: kullanım örneği diyagramları](#UnderstandUseCases)

- [Iş sürecini anlayın: etkinlik diyagramları](#UnderstandActivities)

- [Sistem yapısını açıkla: Bileşen diyagramları](#DescribeComponents)

- [Etkileşimleri açıkla: sıralı diyagramlar](#DescribeSequence)

- [Mevcut kodu görselleştirin: kod haritaları](#VisualizeCode)

- [Türler sözlüğü tanımlayın: sınıf diyagramları](#DefineClasses)

- [Mantıksal mimariyi açıkla: katman diyagramları](#DescribeLayers)

  Bkz.

- [Uygulamanız için model oluşturma](../modeling/create-models-for-your-app.md)

- [Kodu görselleştirme](../modeling/visualize-code.md)

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)

- [Kullanıcı gereksinimlerini modelleme](../modeling/model-user-requirements.md)

- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)

### <a name="UnderstandUseCases"></a>Kullanıcı gereksinimlerini anlayın: kullanım örneği diyagramları
 Kullanım örneği diyagramları bir sistemin desteklediği etkinlikleri ve bu etkinlikleri kimin gerçekleştirdiğini özetler. Lucerne, şimdi akşam yemeği sistemi hakkında aşağıdakileri öğrenmek için bir kullanım durumu diyagramı kullanır:

- Müşteriler sipariş oluşturur.

- Restoranlar siparişleri alır.

- Dinner Now ödeme sisteminin ödemeleri doğrulamak için kullandığı dış ödeme Işlemcisi ağ geçidi, Web sitesi için kapsam dışındadır.

  Diyagramda Ayrıca, bazı önemli kullanım durumlarının daha küçük kullanım örneklerine nasıl bölüneceği gösterilmektedir. Lucerne kendi ödeme sistemini kullanmak istiyor. Değişiklik gerektirdiğini göstermek için Işlem ödemesi kullanım örneğini farklı bir renkle vurgularlar:

  ![Kullanım durumu diyagramında Işlem ödemesini vurgulama](../modeling/media/uml-processpay.png "UML_ProcessPay")

  **Kullanım durumu diyagramında Işlem ödemesini vurgulama**

  Geliştirme zamanı kısaysa, ekip müşterilerin restoranlar için doğrudan ödeme yapmasına izin vermek isteyip istemediğinizi tartışabilir. Bunu göstermek için, Işlem ödemesi kullanım durumunu Dinner Now sistem sınırının dışında olan bir ile değiştirir. Daha sonra Dinner Now 'un yalnızca siparişleri işleyeceğini belirten müşteriyi doğrudan restorana bağlantı altına bağlayabilirler:

  ![Kullanım durumu diyagramında ödeme restorana yeniden alınıyor](../modeling/media/uml-payrestaurant.png "UML_PayRestaurant")

  **Kullanım durumu diyagramında ödeme restorana yeniden alınıyor**

  Bkz.

- [UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)

- [UML Kullanım Durumu Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="drawing-a-use-case-diagram"></a>Kullanım durumu diyagramı çizme
 Kullanım durumu diyagramı aşağıdaki önemli özelliklere sahiptir:

- *Aktörler* kişiler, kuruluşlar, makineler veya yazılım sistemleri tarafından oynanan rolleri temsil eder. Örneğin, müşteri, Restoran ve şimdi akşam yemeği ödeme sistemi aktörlerdir.

- *Kullanım örnekleri* , aktörler ve geliştirme aşamasındaki sistem arasındaki etkileşimleri temsil eder.  Bu kişiler, tek bir fare tıklaması veya iletiden çok gün genişletilmiş bir işleme olan herhangi bir etkileşimi gösterebilir.

- *İlişkilendirmeler* aktörlerin kullanım örneklerine bağlanır.

- Daha büyük bir kullanım örneği, daha küçük olanlar *içerebilir* , örneğin, sipariş oluşturma, Restoran Seç ' i içerir. Kullanım durumunun yalnızca belirli koşullar altında oluştuğunu göstermek için, Genişletilmiş kullanım örneğine hedefler ve adımlar ekleyen bir kullanım durumunu *genişletebilirsiniz* . Kullanım örnekleri aynı zamanda bir diğerinden de devralınabilir.

- Bir *alt sistem* , geliştirme aşamasında olan yazılım sistemini veya bileşenlerinden birini temsil eder. Bu, kullanım durumlarını içeren büyük bir kutusudur. Kullanım durumu diyagramı, alt sistem sınırının içinde veya dışında ne olduğunu açıklar. Kullanıcının belirli hedefleri başka yollarla gerçekleştirmesi gerektiğini belirtmek için, bu kullanım durumlarını alt sistem sınırının dışında çizin.

- *Yapıtlar* , diyagramdaki öğeleri diğer diyagramlara veya belgelere bağlar.

  Bkz.

- [UML Kullanım Durumu Diyagramları: Başvuru](../modeling/uml-use-case-diagrams-reference.md)

- [UML Kullanım Durumu Diyagramları: Yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)

#### <a name="summary-strengths-of-use-case-diagrams"></a>Özet: kullanım örneği diyagramlarının güçleri
 Kullanım örneği diyagramları görselleştirmenize yardımcı olur:

- Bir sistemin desteklediği veya desteklemediği etkinlikler

- Bu etkinlikleri gerçekleştiren insanlar ve dış sistemler

- Üst sistemin içinde iç içe yerleştirilmiş alt sistemler olarak temsil ettiğiniz her etkinliği destekleyen sistemin ana bileşenleri

- Kullanım örneğinin, küçük olanlara veya çeşitlere nasıl bölünebileceği

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Çizimindeki**|**Anlatır**|
|-----------------|-------------------|
|Etkinlik diyagramı|Bir kullanım örneği ve bu kullanım durumunda bu adımları gerçekleştirenler içindeki adımların akışı.<br /><br /> Kullanım örneklerinin adları genellikle bir etkinlik diyagramındaki adımları yansıtır. Etkinlik diyagramları kararlar, birleştirmeler, girişler ve çıktılar, eşzamanlı akışlar vb. gibi öğeleri destekler.<br /><br /> Bkz.<br /><br /> [UML etkinlik diyagramları -   : başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|
|Sıralı diyagram|Bir kullanım durumunda katılımcılar arasındaki etkileşimlerin sırası.<br /><br /> Bkz.<br /><br /> [UML sıralı diyagramları -   : başvuru](../modeling/uml-sequence-diagrams-reference.md)<br />[UML sıralı diyagramları -   : yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|
|Sınıf diyagramı (UML)|Kullanım örneğine katılan varlıklar veya türler.<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|

### <a name="UnderstandActivities"></a>Iş sürecini anlayın: etkinlik diyagramları
 Etkinlik diyagramları bir iş işlemindeki adımların akışını anlatmaktadır ve iş akışını iletmek için basit bir yol sağlar. Geliştirme projesi birden çok etkinlik diyagramına sahip olabilir. Genellikle bir etkinlik, yemek siparişi verme, menüyü güncelleştirme veya işletmeye yeni bir restoran ekleme gibi bir dış eylemden kaynaklanan tüm eylemleri kapsar. Etkinlik, karmaşık bir eylemin ayrıntılarını da açıklayabilir.

 Lucerne, bu Lucerne 'ın ödemeyi işleyeceği ve restorana ödeyen olduğunu göstermek için aşağıdaki etkinlik diyagramını güncelleştirir. Dinner Now ödeme sistemini Lucerne ödeme sistemiyle vurgulandığı şekilde değiştirir:

 ![Etkinlik diyagramında Lucerne ödeme sistemi](../modeling/media/uml-lucerne.png "UML_Lucerne")

 **Etkinlik diyagramında şimdi akşam yemeği ödeme sistemini değiştirme**

 Güncelleştirilmiş diyagram Lucerne ödeme sisteminin iş sürecine uygun olduğu yeri görselleştirmek ve Dinner Now 'a yardımcı olur. Bu sürümde, adımları gerçekleştiren rolleri belirlemek için açıklamalar kullanılır. Satırlar, adımları role göre düzenleyen *kulvarlar*oluşturmak için kullanılır.

 Takımlar Ayrıca, sipariş teslim edildikten sonra müşterinin restorana ödeme yaptığı alternatif bir hikayeyi ele alabilir. Bu, yazılım sistemi için farklı gereksinimler oluşturacaktır.

 Daha önce akşam yemeği artık bu diyagramları bir beyaz tahta veya PowerPoint 'te çizmektedir. Ayrıca, her iki ekibin da ayrıntıları yakalayıp yönetebilmesi için Visual Studio 'Yu bu diyagramları çizmek için de kullanır.

 Bkz.

- [UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)

- [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="drawing-an-activity-diagram"></a>Etkinlik diyagramı çizme
 Bir etkinlik diyagramı aşağıdaki önemli özelliklere sahiptir:

- Etkinliğin ilk eylemini gösteren bir *başlangıç düğümü* .

   Diyagramda her zaman bu düğümlerden biri olmalıdır.

- Kullanıcı veya yazılımın bir görevi gerçekleştirdiği adımları tanımlayan *Eylemler* .

- Eylemler arasındaki akışı gösteren *denetim akışları* .

- Akıştaki koşullu dalları temsil eden *karar düğümleri* .

- Tek akışları, eş zamanlı akışlara ayıran *çatal düğümleri* .

- Etkinliğin uçlarını gösteren *etkinlik son düğümleri* .

   Bu düğümler isteğe bağlı olsa da, etkinliğin nerede bittiğini göstermek için bunları diyagrama eklemek yararlıdır.

  Bkz.

- [UML Etkinlik Diyagramları: Başvuru](../modeling/uml-activity-diagrams-reference.md)

- [UML Etkinlik Diyagramları: Yönergeler](../modeling/uml-activity-diagrams-guidelines.md)

#### <a name="summary-strengths-of-activity-diagrams"></a>Özet: etkinlik diyagramlarının güçleri
 Etkinlik diyagramları, bir işletmenin, sistemin veya programın eylemleri arasındaki denetim ve bilgi akışını görselleştirmenize ve açıklamanıza yardımcı olur. Bu, diğer kişilerle iletişim kurarken iş akışını tanımlamanın basit ve yararlı bir yoludur.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Çizimindeki**|**Açıklama**|
|-----------------|---------------------|
|Kullanım örneği diyagramı|Her aktörün gerçekleştirdiği etkinlikleri özetleyin.<br /><br /> Bkz.<br /><br /> [UML Kullanım örneği diyagramları -   : başvuru](../modeling/uml-use-case-diagrams-reference.md)<br />[UML Kullanım örneği diyagramları -   : yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|
|Bileşen diyagramı|Sistemi, iyi tanımlanmış bir arabirim kümesi aracılığıyla davranış sağlayan veya tüketen yeniden kullanılabilir bölümlerin bir koleksiyonu olarak görselleştirin.<br /><br /> Bkz.<br /><br /> [UML bileşen diyagramlarını -   : başvuru](../modeling/uml-component-diagrams-reference.md)<br />[UML bileşen diyagramlarını -   : yönergeler](../modeling/uml-component-diagrams-guidelines.md)|

### <a name="DescribeComponents"></a>Sistem yapısını açıkla: Bileşen diyagramları
 Bileşen diyagramları, iyi tanımlanmış bir arabirim kümesi aracılığıyla davranış sağlayan veya tüketen ayrılabilir parçalar koleksiyonu olarak bir sistemi anlatır. Parçalar herhangi bir ölçekte olabilir ve herhangi bir şekilde bağlanabilir.

 Lucerne ve Dinner Now 'ın, sistemin bileşenlerini ve bunların arabirimlerini görselleştirmesine ve tartışmalarına yardımcı olmak için aşağıdaki bileşen diyagramlarını oluşturmaları gerekir:

 ![Ödeme sistemindeki dış bileşenler](../modeling/media/uml-extdnpayment.png "UML_ExtDNPayment")

 **Şimdi akşam yemeği ödeme sisteminin bileşenleri**

 Bu diyagramda farklı bileşen türleri ve bunların *bağımlılıkları*gösterilmektedir. Örneğin, şimdi akşam yemeği Web sitesi ve Lucerne ödeme sistemi, ödemeleri doğrulamak için harici ödeme Işlemci ağ geçidi gerektirir. Bileşenler arasındaki oklar, hangi bileşenlerin diğer bileşenlere yönelik işlevselliği gerektirdiğini gösteren bağımlılıkları temsil eder.

 Lucerne ödeme sistemini kullanmak için, şimdi akşam yemeği Web sitesinin, Lucerne ödeme sisteminde PaymentApproval ve Payableekleme arabirimlerini kullanması için güncelleştirilmeleri gerekir.

 Aşağıdaki diyagramda şimdi akşam yemeği Web sitesi için bileşenlerin belirli bir yapılandırması gösterilmektedir. Bu yapılandırma, Web sitesinin herhangi bir örneğinin dört *bölümden*oluştuğunu gösterir:

- CustomerProcessing

- OrderProcessing

- Belgebir Işleme

- PaymentProcessing

  Bu parçalar, belirtilen bileşen türlerinin örnekleridir ve aşağıdaki gibi bağlanır:

  ![Şimdi akşam yemeği Web sitesi içindeki bileşenler](../modeling/media/uml-dinnernow.png "UML_DinnerNow")

  **Şimdi akşam yemeği Web sitesi içindeki bileşenler**

  Şimdi akşam yemeği Web sitesi, Web sitesinin işlevlerini işleyen davranışını bu bölümlerle devreder. Üst bileşen ve onun üye bileşenleri arasındaki oklar, hangi parçaların, üst öğenin arabirimleri aracılığıyla aldığı veya gönderdiği iletileri işleyeceğini belirten *Temsilciler* gösterir.

  Bu yapılandırmada, PaymentProcessing bileşeni müşteri ödemelerini işler. Bu nedenle, Lucerne 'ın ödeme sistemiyle tümleştirilecek şekilde güncelleştirilmeleri gerekir. Diğer senaryolarda, aynı üst bileşende bileşen türünde birden çok örnek bulunabilir.

  Bkz.

- [UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)

- [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="drawing-a-component-diagram"></a>Bileşen diyagramı çizme
 Bir bileşen diyagramı aşağıdaki önemli özelliklere sahiptir:

- Sistem işlevselliğinin ayrılabilir parçalarını temsil eden *Bileşenler* .

- Bileşenlerin, diğer bileşenler veya dış sistemler tarafından uygulandığı ve kullandığı ileti gruplarını veya çağrıları temsil eden *arabirim bağlantı noktaları* .

- Bileşenlerin diğer bileşenlere veya dış sistemlere gönderdikleri ileti gruplarını veya çağrıları temsil eden *gerekli arabirim bağlantı noktaları* . Bu tür bir bağlantı noktası, bir bileşenin en az diğer bileşenlerden veya dış sistemlerden beklediği işlemleri açıklar.

- *Parçalar* bileşen üyeleridir ve genellikle diğer bileşenlerin örnekleridir. Bölüm, ana bileşenin iç tasarımının bir parçasıdır.

- Bileşenleri belirten *Bağımlılıklar* , diğer bileşenlerin işlevselliğini gerektirir.

- Bir bileşenin parçalarını gösteren *Temsilciler* , üst bileşen tarafından gönderilen veya alınan iletileri işler.

  Bkz.

- [UML Bileşen Diyagramları: Başvuru](../modeling/uml-component-diagrams-reference.md)

- [UML Bileşen Diyagramları: Yönergeler](../modeling/uml-component-diagrams-guidelines.md)

#### <a name="summary-strengths-of-component-diagrams"></a>Özet: Bileşen diyagramlarının güçleri
 Bileşen diyagramları şunları görselleştirmenize yardımcı olur:

- Uygulama dilinden veya stiliyle bağımsız olarak ayrılabilir parçalar koleksiyonu olarak sistem.

- İyi tanımlanmış arabirimlerin bulunduğu bileşenler, tasarımı daha kolay anlamak ve gereksinimler değiştiğinde güncelleştirmek daha kolay hale getirir.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Çizimindeki**|**Açıklama**|
|-----------------|---------------------|
|Kod eşlemesi|Var olan koddaki organizasyonu ve ilişkileri görselleştirin.<br /><br /> Bileşenlerin adaylarını belirlemek için bir kod haritası oluşturun ve öğeleri sistemde işlevleriyle gruplayın.<br /><br /> Bkz.<br /><br /> [çözümlerinizin genelinde harita bağımlılıklarını](../modeling/map-dependencies-across-your-solutions.md) -   |
|Sıralı diyagram|Bileşenler veya bileşen içindeki parçalar arasındaki etkileşimlerin sırasını görselleştirin.<br /><br /> Bir bileşenden sıralı diyagramda bir yaşam çizgisi oluşturmak için bileşene sağ tıklayın ve ardından **yaşam çizgisi oluştur**' a tıklayın.<br /><br /> Bkz.<br /><br /> [UML sıralı diyagramları -   : başvuru](../modeling/uml-sequence-diagrams-reference.md)<br />[UML sıralı diyagramları -   : yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|
|Sınıf diyagramı (UML)|Belirtilen veya gerekli bağlantı noktalarında ve bileşenlerin işlevlerini uygulayan sınıflarda arabirimler tanımlayın.<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|
|Katman diyagramı|Bileşenlerle ilişkili olarak sistemin mantıksal mimarisini tanımlar. Kodun tasarımla tutarlı kalmasını sağlamak için katman doğrulamasını kullanın.<br /><br /> Bkz.<br /><br /> -   [kodunuzda katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />[Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md) -   |
|Etkinlik diyagramı|Gelen iletilere yanıt olarak bileşenlerin gerçekleştirdiği iç işlemeyi görselleştirin.<br /><br /> Bkz.<br /><br /> [UML etkinlik diyagramları -   : başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|

### <a name="VisualizeCode"></a>Mevcut kodu görselleştirin: kod haritaları
 Kod haritaları, koddaki geçerli organizasyonu ve ilişkileri gösterir. Öğeler haritadaki *düğümler* tarafından temsil edilir ve ilişkiler *bağlantılarla*temsil edilir. Kod haritaları aşağıdaki türde görevleri gerçekleştirmenize yardımcı olabilir:

- Bilmediğiniz kodu keşfet.

- Önerilen bir değişikliğin mevcut kodu nerede ve nasıl etkileyebileceğini anlayın.

- Karmaşıklığın, doğal katmanların veya desenlerin veya geliştirmelerden faydalanabilir diğer alanların bölgelerini bulun.

  Örneğin, şimdi akşam yemeği PaymentProcessing bileşenini güncelleştirme maliyetini tahmin etmelidir. Bu, kısmen bu değişikliğin sistemin diğer bölümlerini ne kadar etkileyeceğini gösterir. Bunu anlamalarına yardımcı olmak için Dinner Now geliştiricilerinden biri koddan kod haritaları oluşturur ve bu değişiklik, değişikliğin etkilenmiş olabileceği alanlara odaklanarak kapsamını ayarlar.

  Aşağıdaki haritada, PaymentProcessing sınıfı ve seçili görünen Dinner Now sisteminin diğer kısımları arasındaki bağımlılıklar gösterilmektedir:

  ![Dinner Now ödeme sistemi için bağımlılık grafiği](../modeling/media/dep-dnpayment.png "Dep_DNPayment")

  **Dinner Now ödeme sistemi için kod Haritası**

  Geliştirici,, potansiyel olarak etkilenebilecek olan bölgeleri görmek için PaymentProcessing sınıfını genişleterek ve üyelerini seçerek Haritayı araştırır:

  ![PaymentProcessing ve Dependencies içindeki Yöntemler](../modeling/media/depgraph-expandeddn.png "DepGraph_ExpandedDN")

  **PaymentProcessing sınıfının ve bağımlılıklarındaki Yöntemler**

  Bu kişiler, sınıflarını, yöntemlerini ve bağımlılıklarını incelemek için Lucerne ödeme sistemi için aşağıdaki eşlemeyi oluşturur. Ekip, Lucerne sisteminin şu anda akşam yemeği 'nin diğer bölümleriyle etkileşim kurması için de gerekli olabileceğini görür:

  ![Lucerne ödeme sistemi için bağımlılık grafiği](../modeling/media/depgraph-lucernepay.png "DepGraph_LucernePay")

  **Lucerne ödeme sistemi için kod Haritası**

  Her iki ekip de iki sistemi bütünleştirmek için gereken değişiklikleri belirlemede birlikte çalışır. Daha kolay güncelleştirilmesini sağlamak için bazı kodları yeniden düzenleme kararı verir. PaymentApprover sınıfı DinnerNow. Business ad alanına geçer ve bazı yeni yöntemler gerektirir. İşlemleri işleyen şimdi akşam yemeği sınıflarının kendi ad alanı olacaktır. Takımlar işlerini planlamak, düzenlemek ve izlemek için iş öğeleri oluşturup kullanır. İş öğelerini, yararlı olduğu yerde model öğelerine bağlar.

  Kodu yeniden belirledikten sonra takımlar, güncelleştirilmiş yapıyı ve ilişkileri görmek için yeni bir kod haritası oluşturur:

  ![Yeniden düzenlenmiş kodla bağımlılık grafiği](../modeling/media/depgraph-integrated.png "DepGraph_Integrated")

  **Yeniden düzenlenmiş kodla kod Haritası**

  Bu harita, PaymentApprover sınıfının artık DinnerNow. Business ad alanında olduğunu ve bazı yeni yöntemlere sahip olduğunu gösterir. Şimdi akşam yemeği işlem sınıflarının artık kendi PaymentSystem ad alanı vardır ve bu kod daha sonra bu kodla daha kolay bir şekilde uğraşmayı kolaylaştırır.

#### <a name="creating-a-code-map"></a>Kod Haritası oluşturma

- Kaynak koda hızlı bir genel bakış için, bir kod haritası oluşturmak için aşağıdaki adımları izleyin:

     **Mimari** menüsünde **çözüm Için kod Haritası Oluştur**' a tıklayın.

     Derlenmiş koda hızlı bir genel bakış için, boş bir kod haritası oluşturun ve ardından derleme dosyalarını veya ikili dosyaları harita yüzeyine sürükleyin.

- Belirli kod veya çözüm öğelerini araştırmak için, görselleştirmek istediğiniz öğeleri ve ilişkileri seçmek üzere Çözüm Gezgini kullanın. Daha sonra yeni bir eşleme oluşturabilir veya seçili öğeleri var olan bir haritaya ekleyebilirsiniz. Bkz: [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md).

- Haritayı keşfetmenize yardımcı olması için düzeni, yapmak istediğiniz görev türlerine uygun olacak şekilde yeniden düzenleyin.

     Örneğin, koddaki katmanlamayı görselleştirmek için bir ağaç düzeni seçin. Bkz. [kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>Özet: kod eşlemelerinin güçleri
 Kod haritaları şunları yapmanıza yardımcı olur:

- Mevcut koddaki kuruluş ve ilişkiler hakkında bilgi edinin.

- Önerilen bir değişiklikten etkilenebilecek olan bölgeleri belirler.

- Kodun bakımını, değiştirilmesini ve yeniden kullanılmasını kolaylaştırmak için iyileştirebildiğiniz karmaşıklık, desen, katman veya diğer alanların bölgelerini bulun.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Çizimindeki**|**Anlatır**|
|-----------------|-------------------|
|Katman diyagramı|Sistemin mantıksal mimarisi. Kodun tasarımla tutarlı kalmasını sağlamak için katman doğrulamasını kullanın.<br /><br /> Varolan katmanları veya hedeflenen katmanları belirlemenize yardımcı olmak için bir kod haritası oluşturun ve ilişkili öğeleri gruplayın. Katman diyagramı oluşturmak için, bkz.:<br /><br /> -   [kodunuzda katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)|
|Bileşen diyagramı|Bileşenler, arabirimler ve bunların ilişkileri.<br /><br /> Bileşenleri belirlemenize yardımcı olmak için bir kod haritası oluşturun ve öğeleri sistemde işlevleriyle gruplayın.<br /><br /> Bkz.<br /><br /> [UML bileşen diyagramlarını -   : başvuru](../modeling/uml-component-diagrams-reference.md)<br />[UML bileşen diyagramlarını -   : yönergeler](../modeling/uml-component-diagrams-guidelines.md)|
|Sınıf diyagramı (UML)|Sınıflar, öznitelikleri ve işlemleri ve bunların ilişkileri.<br /><br /> Bu öğeleri tanımlamanızı sağlamak için, bu öğeleri gösteren bir UML sınıf diyagramı oluşturun.<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|
|Sınıf diyagramı (kod tabanlı)|Belirli bir proje için koddaki mevcut sınıflar.<br /><br /> Koddaki mevcut bir sınıfı görselleştirmek ve değiştirmek için Sınıf Tasarımcısı kullanın.<br /><br /> Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme (sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).|

### <a name="DescribeSequence"></a>Etkileşimleri açıkla: sıralı diyagramlar
 Sıralı diyagramlar, bir sistemin bölümleri arasındaki bir dizi etkileşimi anlatmaktadır. Parçalar herhangi bir ölçeğe ait olabilir. Örneğin, bir programdaki tek nesnelerden büyük alt sistemler veya harici aktör arasında değişebilir. Etkileşimler herhangi bir ölçek ve türden olabilir. Örneğin, bireysel iletilerden genişletilmiş işlemlere göre değişebilir ve işlev çağrıları veya Web hizmeti iletileri olabilir.

 Lucerne ve Dinner Now 'ın Işlem ödemesi kullanım örneği 'ndeki adımları açıklaması ve tartışmasında, bileşen diyagramından aşağıdaki sıralı diyagramı oluşturamazlar. Yaşam çizgileri şimdi akşam yemeği Web sitesi bileşenini ve parçalarını yansıtır. Yaşam çizgileri arasında görünen iletiler bileşen diyagramlarındaki bağlantıları izler:

 ![Işlem ödemesi kullanım durumu için sıralı diyagram](../modeling/media/umlsequence-processpayment.png "UMLSequence_ProcessPayment")

 **Işlem ödemesi kullanım durumu için sıralı diyagram**

 Sıra diyagramı, müşteri bir sipariş oluşturduğunda, şimdi akşam yemeği Web sitesinin bir OrderProcessing örneği üzerinde ProcessOrder 'i çağırıyor olduğunu gösterir. Daha sonra, OrderProcessing, PaymentProcessing 'da ProcessPayment çağırır. Bu, dış ödeme Işlemcisi ağ geçidi ödemeyi doğrulaana kadar devam eder. Yalnızca, denetim şimdi akşam yemeği Web sitesine geri dönüş yapar.

 Lucerne, ödeme sistemini Dinner Now sistemiyle tümleştirilecek şekilde güncelleştirme maliyetini tahmin etmelidir. Bunu anlamalarına yardımcı olmak için, etkilenen kodu görselleştirmek üzere kod haritaları da oluşturabilir.

 Bkz.

- [UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)

- [UML Sıralı Diyagramlar: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

#### <a name="drawing-a-sequence-diagram"></a>Sıralı Diyagram çizme
 Sıra diyagramı aşağıdaki önemli özelliklere sahiptir:

- Dikey *yaşam çizgileri* , yazılım nesnelerinin aktörleri veya örneklerini temsil eder.

   Bir katılımcının geliştirme kapsamındaki sistem dışında olduğunu gösteren bir aktör sembolü eklemek için yaşam çizgisine tıklayın. **Özellikler** penceresinde **aktör** ' i **true**olarak ayarlayın. **Özellikler** penceresi açık değilse, **F4**tuşuna basın.

- Yatay *iletiler* Yöntem çağrılarını, Web hizmeti iletilerini veya başka bir iletişimi temsil eder. *Yürütme oluşumları* , yaşam çizgileri üzerinde görüntülenen dikey gölgeli dikdörtgenlerdir ve nesneler alma işleminin çağrı yaptığı dönemleri temsil eder.

- *Zaman uyumlu* bir ileti sırasında, Gönderen nesnesi denetimin <\<> bir normal işlev çağrısında olduğu gibi > döndürmesini bekler. *Zaman uyumsuz* bir ileti sırasında gönderici hemen devam edebilir.

- Nesnelerin diğer nesnelere göre oluşturulmasını göstermek için <\<> > iletileri oluşturma ' yı kullanın. Bu, nesnesine gönderilen ilk ileti olmalıdır.

  Bkz.

- [UML Sıralı Diyagramlar: Başvuru](../modeling/uml-sequence-diagrams-reference.md)

- [UML Sıralı Diyagramlar: Yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)

#### <a name="summary-strengths-of-sequence-diagrams"></a>Özet: sıralı diyagramların gücü
 Sıralı diyagramlar şunları görselleştirmenize yardımcı olur:

- Kullanım durumunun yürütülmesi sırasında aktörler veya nesneler arasında aktarım yapan denetim akışı.

- Bir yöntem çağrısının veya iletinin uygulanması.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Çizimindeki**|**Açıklama**|
|-----------------|---------------------|
|Sınıf diyagramı (UML)|Yaşam çizgilerinin gösterdiği sınıfları ve yaşam çizgileri arasında gönderilen iletilerde kullanılan parametreleri ve dönüş değerlerini tanımlayın.<br /><br /> Bir yaşam çizgisinden bir sınıf oluşturmak için, yaşam çizgisine sağ tıklayın ve ardından **Sınıf Oluştur** veya **Arabirim Oluştur**' a tıklayın. Bir sınıf diyagramında bir tür yaşam çizgisi oluşturmak için, türe sağ tıklayın ve sonra **yaşam çizgisi oluştur**' a tıklayın.<br /><br /> Bkz.<br /><br /> -   [UML sınıf diyagramları: başvuru](../modeling/uml-class-diagrams-reference.md)<br />-   [UML sınıf diyagramları: yönergeler](../modeling/uml-class-diagrams-guidelines.md)|
|Bileşen diyagramı|Yaşam çizgilerinin temsil ettiği bileşenleri ve iletilerle temsil edilen davranışı sağlayan ve kullanan arabirimleri tanıtın.<br /><br /> Bileşen diyagramından bir yaşam çizgisi oluşturmak için bileşene sağ tıklayın ve ardından **yaşam çizgisi oluştur**' a tıklayın.<br /><br /> Bkz.<br /><br /> [UML bileşen diyagramlarını -   : başvuru](../modeling/uml-component-diagrams-reference.md)<br />[UML bileşen diyagramlarını -   : yönergeler](../modeling/uml-component-diagrams-guidelines.md)|
|Kullanım örneği diyagramı|Bir kullanıcının hedefini temsil eden bir kullanım durumu olarak bir sıralı diyagramdaki kullanıcılar ve bileşenler arasındaki etkileşimleri özetleyin.<br /><br /> Bkz.<br /><br /> [UML Kullanım örneği diyagramları -   : başvuru](../modeling/uml-use-case-diagrams-reference.md)<br />[UML Kullanım örneği diyagramları -   : yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|

### <a name="DefineClasses"></a>Türler sözlüğü tanımlayın: sınıf diyagramları
 Sınıf diyagramları, sisteme ve bunların ilişkilerine katılan varlıkları, terimleri veya kavramları bir diğeri ile tanımlar. Örneğin, uygulama dilinden veya tarzlarından bağımsız olarak her sınıfın özniteliklerini ve işlemlerini anlatmak için bu diyagramları geliştirme sırasında kullanabilirsiniz.

 Lucerne 'ın Işlem ödemesi kullanım örneğine katılan varlıkları açıklaması ve tartışmalarına yardımcı olmak için aşağıdaki sınıf diyagramını çizirler:

 ![Sınıf diyagramında işlem ödemesi varlıkları](../modeling/media/uml-payentities.png "UML_PayEntities")

 **Bir sınıf diyagramında işlem ödemesi varlıkları**

 Bu diyagramda, bir müşterinin birçok siparişi ve siparişler için ödeme yapmak için farklı yolları olduğunu gösterir. BankAccount ve CreditCard her ikisi de ödemeden devralınır.

 Geliştirme sırasında Lucerne, her bir sınıfın ayrıntılarını açıklamak ve tartışmak için aşağıdaki sınıf diyagramını kullanır:

 ![Bir sınıf diyagramında ödeme varlığı ayrıntılarını işleme](../modeling/media/uml-payment.png "UML_Payment")

 **Sınıf diyagramında işlem ödemesi ayrıntıları**

 Bkz.

- [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)

- [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)

#### <a name="drawing-a-class-diagram"></a>Sınıf diyagramı çizme
 Bir sınıf diyagramı aşağıdaki önemli özelliklere sahiptir:

- Sınıflar, arabirimler ve numaralandırmalar gibi türler:

  - *Sınıf* , belirli yapısal veya davranış özelliklerini paylaşan nesnelerin tanımıdır.

  - Bir *arabirim* , bir nesnenin dışarıdan görünür davranışının bir parçasını tanımlar.

  - *Sabit* listesi, değişmez değerlerin bir listesini içeren bir sınıflandırıcıdır.

- *Öznitelikler* , bir *sınıflandırıcının*her örneğini tanımlayan belirli bir türün değerleridir. Sınıflandırıcı, türler, bileşenler, kullanım örnekleri ve hatta aktörler için genel bir addır.

- *İşlemler* , bir sınıflandırıcı örneklerinin gerçekleştirebileceği Yöntemler veya işlevlerdir.

- *İlişki* , iki sınıflandırıcıda oluşan bazı ilişki türlerini gösterir.

  - *Toplama* , sınıflandırıcılar arasındaki paylaşılan sahipliği gösteren bir ilişkidir.

  - *Birleşim* , sınıflandırıcılar arasındaki bir bütün parçalı ilişkiyi gösteren bir ilişkidir.

    Toplamaları veya kompozisyonları göstermek için bir ilişkilendirmede **toplama** özelliğini ayarlayın. **Paylaşılan** toplamalar ve **bileşik** , bileşimler gösterir.

- *Bağımlılık* , bir sınıflandırıcının tanımını değiştirmenin başka bir sınıflandırıcının tanımını değiştirebileceğini gösterir.

- *Genelleştirme* , belirli bir sınıflandırıcının, genel sınıflandırıcının tanımının bir parçasını devraldığını gösterir. Bir *gerçekleştirme* , bir sınıfın bir arabirim tarafından sunulan işlemleri ve öznitelikleri uyguladığını gösterir.

   Bu ilişkileri oluşturmak için **Devralma** aracını kullanın. Alternatif olarak, bir gerçekleştirme *Lolipop*olarak temsil edilebilir.

- *Paketler* , Sınıflandırıcıların, ilişkilerin, Yaşam çizgilerinin, bileşenlerin ve diğer paketlerin gruplarıdır. *Içeri aktarma* ilişkileri bir paketin başka bir paketin tüm tanımlarını içerdiğini belirtir.

  Mevcut sınıfları araştırmak ve tartışmak için bir başlangıç noktası olarak, koddan sınıf diyagramları oluşturmak için Sınıf Tasarımcısı kullanabilirsiniz.

  Bkz.

- [UML Sınıf Diyagramları: Başvuru](../modeling/uml-class-diagrams-reference.md)

- [UML Sınıf Diyagramları: Yönergeler](../modeling/uml-class-diagrams-guidelines.md)

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Özet: sınıf diyagramlarının güçleri
 Sınıf diyagramları şunları tanımlamanıza yardımcı olur:

- Kullanıcıların ihtiyaçlarını ve sisteme katılan varlıkları ele alırken kullanılacak koşulların ortak bir sözlüğü. Bkz. [model Kullanıcı gereksinimleri](../modeling/model-user-requirements.md).

- Uygulandıkları bağımsız olarak, sistem parçaları tarafından kullanılan türler. Bkz. [uygulamanızın mimarisini modelleme](../modeling/model-your-app-s-architecture.md).

- Türler arasında bağımlılıklar gibi ilişkiler. Örneğin, bir türün başka bir türün birden çok örneğiyle ilişkilendirilebilen gösterebilir.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Çizimindeki**|**Açıklama**|
|-----------------|---------------------|
|Kullanım örneği diyagramı|Kullanım durumlarında hedefleri ve adımları tanımlamak için kullanılan türleri tanımlayın.<br /><br /> Bkz.<br /><br /> [UML Kullanım örneği diyagramları -   : başvuru](../modeling/uml-use-case-diagrams-reference.md)<br />[UML Kullanım örneği diyagramları -   : yönergeler](../modeling/uml-use-case-diagrams-guidelines.md)|
|Etkinlik diyagramı|Nesne düğümleri, giriş PIN 'leri, çıkış sabitleyicileri ve etkinlik parametresi düğümleri aracılığıyla geçen veri türlerini tanımlayın.<br /><br /> Bkz.<br /><br /> [UML etkinlik diyagramları -   : başvuru](../modeling/uml-activity-diagrams-reference.md)<br />-   [UML etkinlik diyagramları: yönergeler](../modeling/uml-activity-diagrams-guidelines.md)|
|Bileşen diyagramı|Bileşenleri, arabirimlerini ve bunların ilişkilerini tanıtın. Bir sınıf Ayrıca, tamamen bir bileşen de tanımlayabilir.<br /><br /> Bkz.<br /><br /> [UML bileşen diyagramlarını -   : başvuru](../modeling/uml-component-diagrams-reference.md)<br />[UML bileşen diyagramlarını -   : yönergeler](../modeling/uml-component-diagrams-guidelines.md)|
|Katman diyagramı|Sınıfların ilişkili olduğu şekliyle sistemin mantıksal mimarisini tanımlayın.<br /><br /> Kodun tasarımla tutarlı kalmasını sağlamak için katman doğrulamasını kullanın.<br /><br /> Bkz.<br /><br /> -   [kodunuzda katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Katman diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />-   [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />[Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md) -   |
|Sıralı diyagram|Yaşam çizgisinin alabileceği tüm iletiler için yaşam çizgisi türlerini ve işlemleri, parametreleri ve dönüş değerlerini tanımlayın.<br /><br /> Bir sınıf diyagramında bir tür yaşam çizgisi oluşturmak için, türe sağ tıklayın ve sonra **yaşam çizgisi oluştur**' a tıklayın.<br /><br /> Bkz.<br /><br /> [UML sıralı diyagramları -   : başvuru](../modeling/uml-sequence-diagrams-reference.md)<br />[UML sıralı diyagramları -   : yönergeler](../modeling/uml-sequence-diagrams-guidelines.md)|
|Kod eşlemesi|Var olan koddaki organizasyonu ve ilişkileri görselleştirin.<br /><br /> Sınıfları, ilişkilerini ve yöntemlerini tanımlamak için, bu öğeleri gösteren bir kod haritası oluşturun.<br /><br /> Bkz.<br /><br /> [çözümlerinizin genelinde harita bağımlılıklarını](../modeling/map-dependencies-across-your-solutions.md) -   |

### <a name="DescribeLayers"></a>Mantıksal mimariyi açıkla: katman diyagramları
 Katman diyagramları, çözümünüzdeki yapıtları soyut gruplar veya *Katmanlar*halinde düzenleyerek sistemin mantıksal mimarisini anlatmaktadır. Yapıtlar, ad alanları, projeler, sınıflar, yöntemler vb. gibi birçok şey olabilir. Katmanlar, yapıların sistemde gerçekleştirdiği rolleri veya görevleri temsil eder ve tanımlarlar. Ayrıca, kodun tasarımıyla tutarlı kalmasını sağlamak için yapı ve iade işlemlerinizin katman doğrulamasını da dahil edebilirsiniz.

 Kodu tasarımla tutarlı tutmak için şimdi akşam yemeği ve Lucerne, geliştikçe kodun doğrulanması için aşağıdaki katman diyagramını kullanır:

 ![Tümleşik ödeme sisteminin katman diyagramı](../modeling/media/layer-integrated-dnlucerne.png "Layer_Integrated_DNLucerne")

 **Artık Lucerne ile tümleştirilmiş akşam yemeği için katman diyagramı**

 Bu diyagramdaki Katmanlar ilgili akşam yemeği ve Lucerne çözüm yapıtlarına bağlanır. Örneğin, Iş katmanı, artık PaymentApprover sınıfını içeren DinnerNow. Business ad alanı ve üyelerine bağlanır. Kaynak erişim katmanı, DinnerNow. Data ad alanına bağlanır. Oklar veya *Bağımlılıklar*, yalnızca iş katmanının, kaynak erişim katmanındaki işlevselliği kullanmasını belirler. Takımlar kodlarını güncelleştirdiklerinde, çakışmalar olduğu gibi yakalamak ve ekiplerin bunları daha sonra çözmelerine yardımcı olmak için katman doğrulaması düzenli olarak gerçekleştirilir.

 Takımlar, iki sistemi artımlı olarak bütünleştirmek ve test etmek için birlikte çalışır. İlk olarak, PaymentApprover ve Dinner 'ın geri kalanının, PaymentProcessing ile uğraşmadan önce başarıyla bir kez daha çalışır durumda olduğundan emin olun.

 Aşağıdaki kod eşlemesinde Dinner Now ve PaymentApprover arasındaki yeni çağrılar gösterilmektedir:

 ![Tümleşik sistemle birlikte bağımlılık grafiği güncelleştirildi](../modeling/media/depgraph-intsystem.png "DepGraph_IntSystem")

 **Güncelleştirilmiş yöntem çağrılarında kod Haritası**

 Sistemin beklendiği gibi çalışmadığını doğruladıktan sonra, şimdi akşam yemeği PaymentProcessing kodunu yorumlar. Katman doğrulama raporları temiz ve sonuçta elde edilen kod haritasında başka bir PaymentProcessing bağımlılığı yok gösterilmektedir:

 ![PaymentProcessing olmadan bağımlılık grafiği](../modeling/media/depgraph-nomore.png "DepGraph_NoMore")

 **PaymentProcessing olmadan kod Haritası**

#### <a name="drawing-a-layer-diagram"></a>Katman diyagramı çizme
 Katman diyagramı aşağıdaki önemli özelliklere sahiptir:

- *Katmanlar* , yapıların mantıksal gruplarını anlatmaktadır.

- *Bağlantı* , bir katman ve yapıt arasındaki ilişkidir.

   Yapıtlar arasından katmanlar oluşturmak için Çözüm Gezgini, kod haritaları, Sınıf Görünümü veya Nesne Tarayıcısı öğelerini sürükleyin. Yeni Katmanlar çizmek ve sonra yapıtları bağlamak için araç kutusunu kullanın veya katmanları oluşturmak için Diyagram yüzeyine sağ tıklayıp öğeleri bu katmanlara sürükleyin.

   Katmandaki sayı katmana bağlı yapıların sayısını gösterir. Bu yapıtlar ad alanları, projeler, sınıflar, yöntemler vb. olabilir. Bir katmandaki yapıt sayısını yorumladığınızda, aşağıdakileri unutmayın:

  - Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.

     Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.

  - Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.

    Bir katmana bağlı yapıtları görmek için katmana sağ tıklayın ve sonra **Katman Gezgini**' ni açmak Için **bağlantıları görüntüle** ' ye tıklayın.

- Bir *bağımlılık* , bir katmanın işlevselliği başka bir katmanda kullanabilir ancak tersi anlamına gelir. *Çift yönlü bağımlılık* , bir katmanın başka bir katmandaki işlevleri kullanacağını ve bunun tersini gösterir.

   Katman diyagramında mevcut bağımlılıkları göstermek için Diyagram yüzeyine sağ tıklayın ve ardından **Bağımlılıklar Oluştur**' a tıklayın. Hedeflenen bağımlılıkları betimleyen, yenilerini çizin.

  Bkz.

- [Kodunuz aracılığıyla katman diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Katman Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)

- [Katman Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)

- [Katman diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-layer-diagrams"></a>Özet: katman diyagramlarının güçleri
 Katman diyagramları şunları yapmanıza yardımcı olur:

- Yapılarının işlevselliğine göre sistemin mantıksal mimarisini açıklama.

- Geliştirme aşamasındaki kodun belirtilen tasarıma uyduğundan emin olun.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Çizimindeki**|**Açıklama**|
|-----------------|---------------------|
|Kod eşlemesi|Var olan koddaki organizasyonu ve ilişkileri görselleştirin.<br /><br /> Katmanlar oluşturmak için bir kod haritası oluşturun ve ardından haritadaki öğeleri olası Katmanlar olarak gruplayın. Grupları haritadan katman diyagramına sürükleyin.<br /><br /> Bkz.<br /><br /> [çözümlerinizin genelinde harita bağımlılıklarını](../modeling/map-dependencies-across-your-solutions.md) -   <br />-   [kod haritalarını gözden geçirme ve yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)|
|Bileşen diyagramı|Bileşenleri, arabirimlerini ve bunların ilişkilerini tanıtın.<br /><br /> Katmanları görselleştirmek için, sistemdeki farklı bileşenlerin işlevlerini açıklayan bir bileşen diyagramı oluşturun.<br /><br /> Bkz.<br /><br /> [UML bileşen diyagramlarını -   : başvuru](../modeling/uml-component-diagrams-reference.md)<br />[UML bileşen diyagramlarını -   : yönergeler](../modeling/uml-component-diagrams-guidelines.md)|

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Bağlantılar**|
|------------------|---------------|
|**Forumlar**|-   [Visual Studio görselleştirme & modelleme araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio görselleştirme & modelleme SDK (dsl araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod geliştirmeyi görselleştirme](../modeling/visualize-code.md) [uygulamanızın](../modeling/create-models-for-your-app.md) [geliştirme sürecinizdeki modellerini kullanma modelleri geliştirme sürecinde](../modeling/use-models-in-your-development-process.md) [kullanın çevik geliştirme](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f) [sırasında](../modeling/validate-your-system-during-development.md) [](../modeling/extend-uml-models-and-diagrams.md) modelleri geliştirme
