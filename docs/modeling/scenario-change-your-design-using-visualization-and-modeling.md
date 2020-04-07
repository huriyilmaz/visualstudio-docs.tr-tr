---
title: 'Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1400f6d5881d5340ec452297d3579306111391b6
ms.sourcegitcommit: 273b657e115c1756adb84e0e56b6f2c709bcee76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80759742"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme

Visual Studio'daki görselleştirme ve modelleme araçlarını kullanarak yazılım sisteminizin kullanıcıların gereksinimlerini karşıladığından emin olun.
Kod eşlemleri, bağımlılık diyagramları ve sınıf diyagramları gibi araçları kullanarak şunları yapın:

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

## <a name="scenario-overview"></a>Senaryoya genel bakış

Bu senaryo, iki hayali şirketin yazılım geliştirme yaşam döngülerinden bölümleri açıklar: Dinner Now ve Lucerne Publishing. Dinner Now, Seattle'da Web tabanlı yemek dağıtım hizmeti sunmaktadır. Müşteriler yemek siparişi verebilir ve Şimdi Akşam Yemeği web sitesinden ödeme yapabilir. Siparişler daha sonra teslimat için uygun yerel restorana gönderilir. New York'ta bir şirket olan Lucerne Publishing, web'de ve kapalı birçok işletme yi işletmektedir. Örneğin, müşterilerin restoran incelemeleri gönderebileceği bir web sitesi çalıştırın.

Lucerne son zamanlarda Dinner Now'ı satın aldı ve aşağıdaki değişiklikleri yapmak istiyor:

- Şimdi Akşam Yemeği'ne restoran inceleme özellikleri ekleyerek web sitelerini entegre edin.

- Dinner Now'ın ödeme sistemini Lucerne'in sistemiyle değiştirin.

- Akşam Yemeği Şimdi servisini bölge genelinde genişletin.

Akşam Yemeği Şimdi SCRUM ve eXtreme Programlama kullanır. Onlar çok yüksek test kapsamı ve çok az desteklenmeyen kod var. Bir sistemin küçük ancak çalışan sürümlerini oluşturarak ve işlevselliği artımlı olarak ekleyerek riskleri en aza indirirler. Kodlarını kısa ve sık yinelemeler üzerinde geliştirirler. Bu, değişimi güvenle benimsemelerini, kodu sık sık yeniden düzenlemelerini ve "öndeki büyük tasarımdan" kaçınmalarını sağlar.

Lucerne, bazıları 40 yıldan daha eski olan çok daha büyük ve karmaşık bir sistem koleksiyonuna sahip. Eski kodun karmaşıklığı ve kapsamı nedeniyle değişiklik yapma konusunda çok dikkatlidirler. Daha titiz bir geliştirme süreci izlerler, ayrıntılı çözümler tasarlamayı ve geliştirme sırasında meydana gelen tasarım ve değişiklikleri belgelemeyi tercih ederler.

Her iki takım da Visual Studio'da kullanıcıların gereksinimlerini karşılayan sistemler geliştirmelerine yardımcı olmak için modelleme diyagramları kullanır. Çalışmalarını planlamalarına, düzenlemelerine ve yönetmelerine yardımcı olmak için Team Foundation Server'ı diğer araçların yanında kullanırlar.

Team Foundation Server hakkında daha fazla bilgi için bkz:

- [İşi planlayın ve izleyin](#plan-and-track-work)

- [Güncelleştirilmiş kodu sınama, doğrulama ve denetleme](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a>Yazılım Geliştirmede Mimari ve Modelleme Diyagramlarının Rolleri

Aşağıdaki tabloda, bu araçların yazılım geliştirme yaşam döngüsünün birden çok ve çeşitli aşamalarında oynayabileceği roller açıklanmaktadır:

||**Kullanıcı Gereksinimleri Modelleme**|**İş Süreci Modelleme**|**Sistem Mimarisi & Tasarımı**|**Kod Görselleştirme & Keşif**|**Doğrulama**|
|------|-|-|-|-|-|
|Etki Alanına Özgü Dil (DSL) diyagramı|Evet|Evet|Evet|||
|Bağımlılık diyagramı, katman doğrulama|||Evet|Evet|Evet|
|Kod haritası|||Evet|Evet|Evet|
|Sınıf Tasarımcısı (kod tabanlı)||||Evet||

Bağımlılık diyagramları çizmek için, varolan bir çözümün veya yeni bir çözümün parçası olarak bir modelleme projesi oluşturmanız gerekir. Bu diyagramlar modelleme projesinde oluşturulmalıdır.
Bağımlılık diyagramlarında öğeler modelleme projesinde bulunur, ancak ortak modelde depolanmaz. Kod eşlemleri ve koddan oluşturulan .NET sınıf diyagramları modelleme projesinin dışında bulunur.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Her iki takım da, geliştirilmekte olan kodun tasarımla tutarlı kalmasını sağlamak için bağımlılık doğrulaması kullanır. Bkz.

- [Kodu Tasarımla Tutarlı Tutma](#ValidatingCode)

- [Mantıksal Mimariyi Açıkla: Bağımlılık Diyagramları](#DescribeLayers)

- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Visual Studio'nun bazı sürümleri, görselleştirme ve modelleme için bağımlılık doğrulamasını ve kod eşlemlerinin salt okunur sürümlerini destekler. Visual Studio'nun hangi sürümlerinin bu özelliği desteklediğini görmek [için mimari ve modelleme araçları için Edition desteğine](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)bakın.

## <a name="understand-and-communicate-information-about-the-system"></a>Sistem le ilgili bilgileri anlama ve iliştirme

Visual Studio modelleme diyagramlarını kullanmak için öngörülen bir sipariş yoktur, bu nedenle bunları ihtiyaçlarınıza veya yaklaşımınıza uygun olarak kullanabilirsiniz. Genellikle, takımlar bir proje boyunca modellerini yinelemeli ve sık sık yeniden ziyaret ederler. Her diyagram, geliştirilmekte olan sistemin farklı yönlerini anlamanıza, tanımlamanıza ve iletişim kurmanıza yardımcı olacak belirli güçlü yönler sunar.

Şimdi Akşam Yemeği ve Lucerne, ortak dilleri olarak diyagramlar kullanarak birbirleriyle ve proje paydaşlarıyla iletişim kurarlar. Örneğin, Şimdi Akşam Yemeği bu görevleri gerçekleştirmek için diyagramları kullanır:

- Varolan kodu görselleştirin.

- Lucerne ile yeni veya güncelleştirilmiş kullanıcı hikayeleri hakkında iletişim kurun.

- Yeni veya güncelleştirilmiş kullanıcı öykülerini desteklemek için gereken değişiklikleri tanımlayın.

Lucerne bu görevleri gerçekleştirmek için diyagramlar kullanır:

- Şimdi Akşam Yemeği iş süreci hakkında bilgi edinin.

- Sistemin tasarımını anlayın.

- Yeni veya güncelleştirilmiş kullanıcı gereksinimleri hakkında Dinner Now ile iletişim kurun.

- Sistemdeki belge güncelleştirmeleri.

Diyagramlar Team Foundation Server ile tümleştirilir, böylece takımlar çalışmalarını daha kolay planlayabilir, yönetebilir ve izleyebilir. Örneğin, test örneklerini ve geliştirme görevlerini tanımlamak ve çalışmalarını tahmin etmek için modelleri kullanırlar. Lucerne, Team Foundation Server iş öğelerini, ilerlemeyi izleyebilmeleri ve sistemin kullanıcıların gereksinimlerini karşıladığından emin olmak için öğeleri modellemeye bağlar. Örneğin, tüm testler geçerken kullanım örneklerinin yerine getirildiğini görebilmeleri için kullanım örneklerini test etmek için kullanım örneklerini bağlarlar.

Takımlar değişikliklerini iade etmeden önce, bağımlılık doğrulaması ve otomatik leştirilmiş testler içeren yapılar çalıştırarak kodu testlere ve tasarıma karşı doğrularlar. Bu, güncelleştirilmiş kodun tasarımla çakışmamasını ve daha önce çalışan işlevselliği kesmesini sağlamaya yardımcı olur.

### <a name="identify-changes-to-the-existing-system"></a>Varolan Sistemdeki Değişiklikleri Belirleme

Akşam Yemeği Şimdi yeni gereksinimi karşılama maliyetini tahmin etmelidir. Bu, kısmen bu değişikliğin sistemin diğer bölümlerini ne kadar etkileyeceğine bağlıdır. Bunu anlamalarına yardımcı olmak için, Şimdi Akşam Yemeği geliştiricilerinden biri varolan koddan bu haritaları ve diyagramları oluşturur:

|**Harita veya diyagram**|**Diziler**|
|-|-|
|*Kod haritası*<br /><br /> Bkz.<br /><br /> - [Çözümlerinizde bağımlılıkları haritala](../modeling/map-dependencies-across-your-solutions.md)<br />- [Kod haritalarına göz atın ve yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)<br />- [DGML dosyalarını düzenleyerek kod eşlemlerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Bağımlılıklar ve koddaki diğer ilişkiler.<br /><br /> Örneğin, Şimdi Akşam Yemeği derlemeleri ve bağımlılıkları genel bir bakış için derleme kodu eşlemleri gözden geçirerek başlayabilir. Bu derlemelerde isim alanlarını ve sınıfları keşfetmek için haritaları inceleyebilirler.<br /><br /> Şimdi Akşam Yemeği, koddaki belirli alanları ve diğer ilişki türlerini keşfetmek için haritalar da oluşturabilir. İlgilerini çeken alanları ve ilişkileri bulmak ve seçmek için Solution Explorer'ı kullanırlar.|
|*Kod tabanlı sınıf diyagramı*<br /><br /> [Bkz. Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Koddaki varolan sınıflar|

 Örneğin, geliştirici bir kod eşlemi oluşturur. Kapsamını, yeni senaryodan etkilenecek alanlara odaklanacak şekilde ayarlar. Bu alanlar seçilir ve haritada vurgulanır:

 ![Ad Alanı Bağımlılık Grafiği](../modeling/media/namespace_reviewsystem.png)

 **Namespace kod haritası**

 Geliştirici sınıflarını, yöntemlerini ve ilişkilerini görmek için seçili ad alanlarını genişletir:

 ![Genişletilmiş ad alanı bağımlılık grafiği](../modeling/media/dep_reviewsystem.png)

 **Görünür grup lar arası bağlantılarla genişletilmiş ad alanı kodu haritası**

 Geliştirici etkilenen sınıfları ve yöntemleri bulmak için kodu inceler. Yaptığınız da her değişikliğin etkilerini görmek için, her değişiklikten sonra kod eşlemlerini yeniden oluşturun. Bkz. [Görselleştir kodu.](../modeling/visualize-code.md)

 Bileşen veya etkileşim ler gibi sistemin diğer bölümlerindeyapılan değişiklikleri açıklamak için, takım bu öğeleri beyaz tahtalara çizebilir. Ayrıca, ayrıntıların her iki takım tarafından da yakalanıp yönetilebilmeleri ve anlaşılabilmesi için Visual Studio'da aşağıdaki diyagramları çizebilirler:

|**Diyagramları**|**Açıklanır**|
|-|-|
|*Kod tabanlı sınıf diyagramı*<br /><br /> [Bkz. Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Koddaki varolan sınıflar.|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a>Kodu Tasarımla Tutarlı Tutun
 Şimdi Akşam Yemeği Güncelleştirilmiş kodun tasarımla tutarlı kaldığından emin olmalıdır. Sistemdeki işlevsellik katmanlarını açıklayan, aralarında izin verilen bağımlılıkları belirten bağımlılık diyagramları oluştururlar ve çözüm yapılarını bu katmanlarla ilişkilendirerler.

|**Diyagram**|**Açıklanır**|
|-|-|
|*Bağımlılık diyagramı*<br /><br /> Bkz.<br /><br /> - [Kodunuzdan bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|Kodun mantıksal mimarisi.<br /><br /> Bağımlılık diyagramı, Visual Studio çözümündeki yapıları *katman*adı verilen soyut gruplarla düzenler ve eşler. Bu katmanlar, bu yapılarsistemde gerçekleştirdiği rolleri, görevleri veya işlevleri tanımlar.<br /><br /> Bağımlılık diyagramları, sistemin amaçlanan tasarımını açıklamak ve bu tasarıma karşı gelişen kodu doğrulamak için yararlıdır.<br /><br /> Katmanlar oluşturmak için, Öğeleri Çözüm Gezgini, kod eşlemleri, Sınıf Görünümü ve Nesne Tarayıcısı'ndan sürükleyin. Yeni katmanlar çizmek için araç kutusunu kullanın veya diyagram yüzeyine sağ tıklayın.<br /><br /> Varolan bağımlılıkları görüntülemek için bağımlılık diyagramı yüzeyini sağ tıklatın ve sonra **Bağımlılıkları Oluştur'u**tıklatın. Amaçlanan bağımlılıkları belirtmek için yeni bağımlılıklar çizin.|

Örneğin, aşağıdaki bağımlılık diyagramı katmanlar arasındaki bağımlılıkları ve her katmanla ilişkili yapı ların sayısını açıklar:

![Entegre ödeme sisteminin bağımlılık diyagramı](../modeling/media/layer_integrated_dnlucerne.png)

 **Bağımlılık Diyagramı**

Ekipler, kod geliştirme sırasında tasarımla çakışma oluşmadığından emin olmak için, Azure DevOps'lerde çalıştırılabilen yapılarda bağımlılık doğrulaması kullanır. Ayrıca, iade işlemlerinde bağımlılık doğrulaması gerektiren özel bir MSBuild görevi de oluştururlar. Doğrulama hatalarını toplamak için yapı raporları kullanırlar.

Bkz.

- [Görsel tasarımcıyı kullanma](/azure/devops/pipelines/get-started-designer)

- [TFVC kapılı check-in](/azure/devops/pipelines/build/triggers)

- [Oluşturma ve serbest bırakma görevleri](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Modeller Oluşturmak ve Kullanmak Için Genel İpuçları

- Çoğu diyagram, çizgilerle bağlanan düğümlerden oluşur. Her diyagram türü için araç kutusu farklı türde düğümler ve çizgiler sağlar.

   Araç kutusunu açmak için **Görünüm** menüsünde **Araç Kutusu'nu**tıklatın.

- Düğüm oluşturmak için, onu araç kutusundan diyagrama sürükleyin. Belirli türdeki düğümler varolan düğümlere sürülmelidir. Örneğin, bileşen diyagramında varolan bir bileşene yeni bir bağlantı noktası eklenmelidir.

- Bir satır veya bağlantı oluşturmak için, araç kutusundaki uygun aracı tıklatın, kaynak düğüm'e tıklayın ve ardından hedef düğümü tıklatın. Bazı satırlar yalnızca belirli türde düğümler arasında oluşturulabilir. İşaretçiyi olası bir kaynak veya hedef üzerinde taşıdığınızda, işaretçi bir bağlantı oluşturup oluşturamayacağınızı gösterir.

### <a name="plan-and-track-work"></a>İşi planlayın ve izleyin

Visual Studio modelleme diyagramları, çalışmayı daha kolay planlayabilmeniz, yönetebilmeniz ve izleyebilmeniz için Team Foundation Server ile entegre edilmiştir. Her iki takım da test örneklerini ve geliştirme görevlerini belirlemek ve çalışmalarını tahmin etmek için modelleri kullanır. Lucerne, Team Foundation Server iş öğelerini kullanım örnekleri veya bileşenler gibi model öğelerine bağlar ve oluşturur. Bu, ilerlemelerini izlemelerine ve çalışmalarını kullanıcıların gereksinimlerine kadar izlemelerine yardımcı olur. Bu, değişikliklerinin bu gereksinimleri karşılamaya devam etmesini sağlamalarına yardımcı olur.

Çalışmaları ilerledikçe, takımlar görevlerinde harcadıkları zamanı yansıtacak şekilde iş öğelerini güncelleştirir. Ayrıca, aşağıdaki Team Foundation Server özelliklerini kullanarak çalışmalarının durumunu izler ve bildirirler:

- Beklenen süre içinde planlanan çalışmayı tamamlayıp tamamlamayacaklarını gösteren *günlük raporlar yakıyor.* Hataların ilerlemesini izlemek için Team Foundation Server'dan benzer raporlar oluştururlar.

- Ekibin üyeleri arasındaki iş yükünü izlemesine ve dengelemesine yardımcı olmak için Microsoft Excel'i kullanan bir *yineleme çalışma sayfası.* Bu çalışma sayfası Team Foundation Server'a bağlıdır ve düzenli ilerleme toplantıları sırasında tartışmaya odaklanmayı sağlar.

- Ekibi önemli proje bilgileri hakkında bilgilendirmek için Office Project'i kullanan bir *geliştirme panosu.*

Bkz.

- [Çevik araçlar ve Çevik proje yönetimi hakkında](/azure/devops/boards/backlogs/backlogs-overview?view=vsts)

- [Grafikler, panolar ve widget'lar (Azure DevOps Hizmetleri)](/azure/devops/report/dashboards/overview?view=vsts)

- [Project'i kullanarak biriktirme listenizi ve görevlerinizi oluşturun](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a>Kodu Test Et, Doğrula ve İade Et

Takımlar her görevi tamamlayarken, kodlarını kaynak denetimine alır ve unuturlarsa Team Foundation Server'dan anımsatıcılar alırlar. Team Foundation Server iadelerini kabul etmeden önce, takımlar kodu test örneklerine ve tasarıma karşı doğrulamak için birim testleri ve bağımlılık doğrulaması çalıştırın. Yapılar, otomatik birim testleri ve bağımlılık doğrulamayı düzenli olarak çalıştırmak için Team Foundation Server'ı kullanırlar. Bu, kodun aşağıdaki ölçütleri karşıladığından emin olunmasınıza yardımcı olur:

- İşe yarıyor.

- Daha önce çalışma kodunu bozmaz.

- Tasarımla çakışmaz.

Dinner Now, Lucerne'nin yeniden kullanabileceği büyük bir otomatik test koleksiyonuna sahiptir, çünkü neredeyse hepsi hala geçerlidir. Lucerne ayrıca bu testleri oluşturabilir ve yeni işlevleri kapsayacak şekilde yenilerini ekleyebilir. Her ikisi de el ile testler çalıştırmak için Visual Studio kullanın.

Kodun tasarıma uydugundan emin olmak için, ekipler yapılarını Azure DevOps' te bağımlılık doğrulamayı içerecek şekilde yapılandırır. Herhangi bir çakışma oluşursa, ayrıntılarla birlikte bir rapor oluşturulur.

Bkz.

- [Uygulamayı test etme](/azure/devops/test/overview?view=vsts)

- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)

- [Sürüm denetimini kullanma](/azure/devops/repos/tfvc/overview?view=azure-devops)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts)

## <a name="update-the-system-using-visualization-and-modeling"></a>Görselleştirme ve Modelleme Kullanarak Sistemi Güncelleştirin

Lucerne ve Dinner Now ödeme sistemlerini entegre etmeli. Aşağıdaki bölümler, Visual Studio'daki modelleme diyagramlarını göstererek bu görevi gerçekleştirmelerine yardımcı olur:

- [Varolan Kodu Görselleştir: Kod Haritaları](#VisualizeCode)

- [Türler Sözlüğü Tanımla: Sınıf Diyagramları](#DefineClasses)

- [Mantıksal Mimariyi Açıkla: Bağımlılık Diyagramları](#DescribeLayers)

Bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)

- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Varolan Kodu Görselleştir: Kod Haritaları

Kod eşlemleri, koddaki geçerli organizasyonu ve ilişkileri gösterir. Öğeler haritada *düğümlerle* temsil edilir ve ilişkiler *bağlantılarla*gösterilir. Kod eşlemleri aşağıdaki tür görevleri gerçekleştirmenize yardımcı olabilir:

- Yabancı kodu keşfedin.

- Önerilen değişikliğin varolan kodu nerede ve nasıl etkileyebileceğini anlayın.

- Karmaşıklık alanları, doğal bağımlılıklar veya desenler veya iyileştirmeden yararlanabilecek diğer alanları bulun.

Örneğin, Şimdi Akşam Yemeği, PaymentProcessing bileşenini güncelleştirme maliyetini tahmin etmelidir. Bu, kısmen bu değişikliğin sistemin diğer bölümlerini ne kadar etkileyeceğine bağlıdır. Bunu anlamalarına yardımcı olmak için, Şimdi Akşam Yemeği geliştiricilerinden biri koddan kod eşlemleri oluşturur ve değişiklikten etkilenebilecek alanlara yönelik kapsam odağı ayarlar.

Aşağıdaki harita, PaymentProcessing sınıfı ile Seçili görünen Şimdi Akşam Yemeği sisteminin diğer bölümleri arasındaki bağımlılıkları gösterir:

![Dinner Now ödeme sistemi için bağımlılık grafiği](../modeling/media/dep_dnpayment.png)

**Akşam Yemeği Şimdi ödeme sistemi için kod haritası**

Geliştirici, PaymentProcessing sınıfını genişleterek ve etkilenen alanları görmek için üyelerini seçerek haritayı inceler:

![Ödeme İşlemi ve bağımlılıkları içindeki yöntemler](../modeling/media/depgraph_expandeddn.png)

**Ödemeİşleme sınıfı içindeki yöntemler ve bunların bağımlılıkları**

Lucerne Ödeme Sistemi'nin sınıflarını, yöntemlerini ve bağımlılıklarını incelemesi için aşağıdaki haritayı oluştururlar. Ekip, Lucerne sisteminin Şimdi Akşam Yemeği'nin diğer bölümleriyle etkileşime geçmesi için de çalışma gerektirebileceğini görür:

![Lucerne ödeme sistemi için bağımlılık grafiği](../modeling/media/depgraph_lucernepay.png)

**Lucerne Ödeme Sistemi için kod haritası**

Her iki takım da iki sistemi tümleştirmek için gereken değişiklikleri belirlemek için birlikte çalışır. Güncelleştirmenin daha kolay olması için kodun bir kısmını yeniden düzenlemeye karar verirler. PaymentApprover sınıfı DinnerNow.Business ad alanına taşınır ve bazı yeni yöntemler gerektirir. İşlemleri işleyen Şimdi Akşam Yemeği sınıflarının kendi ad alanı olacaktır. Takımlar, çalışmalarını planlamak, düzenlemek ve izlemek için iş öğeleri oluşturur ve kullanır. Çalışma öğelerini yararlı olduğu öğeleri modellemek için bağlarlar.

Kodu yeniden düzenledikten sonra, takımlar güncelleştirilmiş yapıyı ve ilişkileri görmek için yeni bir kod eşlemi oluşturur:

![Yeniden düzenlenmiş kodlu bağımlılık grafiği](../modeling/media/depgraph_integrated.png)

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
|-|-|
|Bağımlılık diyagramı|Sistemin mantıksal mimarisi. Kodun tasarımla tutarlı kalmasını sağlamak için bağımlılık doğrulaması kullanın.<br /><br /> Varolan bağımlılıkları veya amaçlanan bağımlılıkları belirlemenize yardımcı olmak için bir kod eşlemi oluşturun ve ilgili öğeleri gruplayın. Bağımlılık diyagramı oluşturmak için bkz:<br /><br /> - [Kodunuzdan bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)|
|Sınıf diyagramı (kod tabanlı)|Belirli bir proje için koddaki varolan sınıflar.<br /><br /> Varolan bir sınıfı kodda görselleştirmek ve değiştirmek için Sınıf Tasarımcısı'nı kullanın.<br /><br /> [Bkz. Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a>Türler Sözlüğü Tanımla: Sınıf Diyagramları
 Sınıf diyagramları, sisteme katılan varlıkları, terimleri veya kavramları ve bunların birbirleriyle olan ilişkilerini tanımlar. Örneğin, uygulama dillerinden veya stillerinden bağımsız olarak, her sınıfın özniteliklerini ve işlemlerini açıklamak için geliştirme sırasında bu diyagramları kullanabilirsiniz.

 Lucerne'in İşlem Ödemesi kullanım örneğine katılan varlıkları tanımlamasına ve tartışmasına yardımcı olmak için aşağıdaki sınıf diyagramını çizerler:

 ![Sınıf diyagramında Ödeme varlıklarını işleme](../modeling/media/uml_payentities.png)

 **Sınıf diyagramında Ödeme varlıklarını işleme**

 Bu diyagram, müşterinin siparişler için ödeme yapmak için birçok siparişe ve farklı yöntemlerine sahip olabileceğini gösterir. BankAccount ve CreditCard'ın her ikisi de Ödeme'den devralır.

 Geliştirme sırasında Lucerne, her sınıfın ayrıntılarını açıklamak ve tartışmak için aşağıdaki sınıf diyagramını kullanır:

 ![Sınıf diyagramında Ödeme birimi ayrıntılarını işleme](../modeling/media/uml_payment.png)

 **Sınıf diyagramında Ödeme yi işleme**

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

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Özet: Sınıf Diyagramlarının Güçlü Yönleri
 Sınıf diyagramları tanımlamanıza yardımcı olur:

- Kullanıcıların gereksinimlerini ve sisteme katılan varlıkları tartışırken kullanılacak ortak bir terimler sözlüğü. [Bkz. Model kullanıcı gereksinimleri.](../modeling/model-user-requirements.md)

- Uygulamalarından bağımsız olarak, bileşenler gibi sistemin parçaları tarafından kullanılan türler. Uygulamanızın [mimarisini modelle'ye](../modeling/model-your-app-s-architecture.md)bakın.

- Türler arasındaki bağımlılıklar gibi ilişkiler. Örneğin, bir türün başka bir türün birden çok örneğiyle ilişkilendirilebileceğini gösterebilirsiniz.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklama**|
|-|-|
|Bağımlılık diyagramı|Sınıflarla ilgili olarak sistemin mantıksal mimarisini tanımlayın.<br /><br /> Kodun tasarımla tutarlı kalmasını sağlamak için bağımlılık doğrulaması kullanın.<br /><br /> Bkz.<br /><br /> - [Kodunuzdan bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|
|Kod haritası|Varolan kodda organizasyonu ve ilişkileri görselleştirin.<br /><br /> Sınıfları, ilişkilerini ve yöntemlerini tanımlamak için, bu öğeleri gösteren bir kod eşlemi oluşturun.<br /><br /> Bkz.<br /><br /> - [Çözümlerinizde bağımlılıkları haritala](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a>Mantıksal Mimariyi Açıkla: bağımlılık Diyagramları
 Bağımlılık diyagramları, çözümünüzdeki yapıları soyut gruplar veya *katmanlar*halinde düzenleyerek bir sistemin mantıksal mimarisini açıklar. Eserler ad alanları, projeler, sınıflar, yöntemler ve benzeri birçok şey olabilir. Katmanlar, yapıtların sistemde gerçekleştirdiği rolleri veya görevleri temsil eder ve açıklar. Kodun tasarımıyla tutarlı kaldığından emin olmak için yapı ve iade işlemlerinize katman doğrulama da ekleyebilirsiniz.

 Kodu tasarımla tutarlı tutmak için, Şimdi Akşam Yemeği ve Lucerne, kodları geliştikçe doğrulamak için aşağıdaki bağımlılık diyagramını kullanır:

 ![Entegre ödeme sisteminin bağımlılık diyagramı](../modeling/media/layer_integrated_dnlucerne.png)

 **Şimdi Lucerne ile entegre Akşam Yemeği için Bağımlılık diyagramı**

 Bu diyagramdaki katmanlar, karşılık gelen Şimdi Akşam Yemeği ve Lucerne çözüm yapılarına bağlanır. Örneğin, İş katmanı DinnerNow.Business ad alanına ve şimdi PaymentApprover sınıfını içeren üyelerine bağlanır. Kaynak Erişimi katmanı DinnerNow.Data ad alanına bağlanır. Oklar veya *bağımlılıklar,* Kaynak Erişim katmanındaki işlevselliği yalnızca İş katmanının kullanabileceğini belirtir. Takımlar kodlarını güncellerken, çakışmaları oluştukları anda yakalamak ve ekiplerin bunları hemen çözmesine yardımcı olmak için katman doğrulama düzenli olarak gerçekleştirilir.

 Ekipler, iki sistemi aşamalı olarak tümleştirmek ve test etmek için birlikte çalışır. Onlar ilk PaymentApprover ve Dinner Now geri kalanı onlar PaymentProcessing ile uğraşmadan önce birbirleriyle başarılı bir şekilde çalışmak emin olun.

 Aşağıdaki kod haritası, Şimdi Akşam Yemeği ve PaymentApprover arasındaki yeni aramaları gösterir:

 ![Entegre sistemile güncelleştirilmiş bağımlılık grafiği](../modeling/media/depgraph_intsystem.png)

 **Güncelleştirilmiş yöntem çağrıları ile kod haritası**

 Sistemin beklendiği gibi çalıştığını doğruladıktan sonra, Dinner Now Ödeme İşlemi kodunu yorumlar. Katman doğrulama raporları temizdir ve ortaya çıkan kod eşlemi, başka Ödeme İşleme bağımlılığı olmadığını gösterir:

 ![PaymentProcessing olmadan bağımlılık grafiği](../modeling/media/depgraph_nomore.png)

 **PaymentProcessing olmadan kod haritası**

#### <a name="drawing-a-dependency-diagram"></a>Bağımlılık Diyagramı Çizme

Bağımlılık diyagramı aşağıdaki temel özelliklere sahiptir:

- *Katmanlar* mantıksal yapı gruplarını açıklar.

- *Bağlantı,* katman ve yapı arasındaki ilişkidir.

     Yapılardan katmanlar oluşturmak için, Öğeleri Çözüm Gezgini'nden, kod eşlerinden, Sınıf Görünümü'nden veya Nesne Tarayıcısından sürükleyin. Yeni katmanlar çizmek ve bunları yapılara bağlamak için, katmanları oluşturmak için araç kutusunu kullanın veya diyagram yüzeyini sağ tıklatın ve sonra öğeleri bu katmanlara sürükleyin.

     Katmandaki sayı, katmana bağlı yapıların sayısını gösterir. Bu yapılar ad alanları, projeler, sınıflar, yöntemler ve benzeri olabilir. Katmandaki yapıt sayısını yorumlarken aşağıdakileri unutmayın:

  - Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.

       Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.

  - Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.

    Katmana bağlı yapıları görmek için, bağımlılık sağ tıklatın ve sonra **Katman Gezgini'ni**açmak için **Bağlantıları Görüntüle'yi** tıklatın.

- *Bağımlılık,* bir katmanın işlevselliği başka bir katmanda kullanabileceğini, ancak tam tersi olmadığını gösterir. *Çift yönlü bağımlılık,* bir katmanın işlevselliği başka bir katmanda kullanabileceğini gösterir ve bunun tersi de geçerlidir.

     Bağımlılık diyagramındaki varolan bağımlılıkları görüntülemek için diyagram yüzeyini sağ tıklatın ve sonra **Bağımlılıkları Oluştur'u**tıklatın. Amaçlanan bağımlılıkları açıklamak için yenilerini çizin.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)

- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)

- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Özet: Bağımlılık Diyagramlarının Güçlü Yönleri

Bağımlılık diyagramları size yardımcı olur:

- Bir sistemin mantıksal mimarisini yapıl›n› eserlerinin işlevselliğine göre tan›mlay›n.

- Geliştirme aşamasındaki kodun belirtilen tasarıma uydur emin olun.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklama**|
|-|-|
|Kod haritası|Varolan kodda organizasyonu ve ilişkileri görselleştirin.<br /><br /> Katmanlar oluşturmak için bir kod eşlemi oluşturun ve ardından haritadaki öğeleri olası katmanlar olarak gruplayın. Grupları haritadan bağımlılık diyagramına sürükleyin.<br /><br /> Bkz.<br /><br /> - [Çözümlerinizde bağımlılıkları haritala](../modeling/map-dependencies-across-your-solutions.md)<br />- [Kod haritalarına göz atın ve yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Bağlantılar**|
|-|-|
|**Forumlar**|- [Visual Studio Visualization & Modelleme Araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Visualization & Modelleme SDK (DSL Araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Ayrıca bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
- [Çevik geliştirmede modelleri kullanma](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)
- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)
