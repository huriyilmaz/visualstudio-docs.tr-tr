---
title: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme
description: Visual Studio görselleştirme ve modelleme araçları hakkında bilgi ve tasarımınızı değiştirmek için bu araçları nasıl kullanabileceğinizi öğrenin.
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- code visualization [Visual Studio ALM]
- modeling software [Visual Studio ALM]
- software modeling [Visual Studio ALM]
- walkthroughs [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], visualizing code
- walkthrough [Visual Studio ALM], modeling software
- walkthroughs [Visual Studio ALM], modeling software
author: mgoertz-msft
ms.author: mgoertz
ms.custom: SEO-VS-2020
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 4b396d1f348ef3fc002979026168b325341c691e
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635886"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme

Yazılım sisteminizin kullanıcıların ihtiyaçlarını karşılamaya yardımcı olmak için yazılım sistemlerinizin görselleştirme ve modelleme araçlarını Visual Studio.
Kod eşlemeleri, bağımlılık diyagramları ve sınıf diyagramları gibi araçları kullanarak şunları yapabilirsiniz:

Her aracı destekleyen Visual Studio için bkz. [Mimari ve modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

- Kullanıcıların gereksinimlerini ve iş sürecini netleştirin.

- Mevcut kodu görselleştirin ve keşfedin.

- Mevcut sistemde yapılan değişiklikleri açıklama.

- Sistemin gereksinimlerini karşılar olduğunu doğrulayın.

- Kodu tasarımla tutarlı tutma.

Bu kılavuz:

- Bu araçların yazılım projenize nasıl faydalı olduğunu açıklar.

- Örnek bir senaryoyla, geliştirme yaklaşımınıza bakılmaksızın bu araçları nasıl kullanabileceğinizi gösterir.

Bu araçlar ve desteklene senaryoları hakkında daha fazla bilgi için bkz:

- [Mimariyi Çözümleme ve Mimarinin Modelini Oluşturma](../modeling/analyze-and-model-your-architecture.md)

- [Kodu görselleştirme](../modeling/visualize-code.md)

## <a name="scenario-overview"></a>Senaryoya genel bakış

Bu senaryo, iki kurgusal şirketin yazılım geliştirme yaşam döngülerinden bölümleri açıklar: Şimdi Akşam Yemeği ve Lucerne Yayımlama. Akşam Yemeği Şimdi Seattle'da Web tabanlı bir yemek teslim hizmeti sağlar. Müşteriler şimdi Akşam Yemeği web sitesinde yemek siparişi ve ödemesi yapmaktadır. Siparişler daha sonra teslim için uygun yerel restorana gönderilir. New York'ta bir şirket olan Lucerne Publishing, hem kapalı hem de Web üzerinde çeşitli işletmeler çalıştırıyor. Örneğin, müşterilerin restoran incelemeleri yayınlandıracakları bir web sitesi çalıştırmaktadır.

Lucerne kısa süre önce Şimdi Akşam Yemeği'ne katıldı ve aşağıdaki değişiklikleri yapmak istiyor:

- Şimdi Akşam Yemeği'ne restoran inceleme özellikleri ekleyerek web sitelerini tümleştirin.

- Şimdi Akşam Yemeği'nin ödeme sistemini Lucerne'ın sistemiyle değiştirin.

- Şimdi Akşam Yemeği hizmetini bölge genelinde genişletin.

Şimdi Akşam Yemeği SCRUM ve eXtreme Programlama kullanıyor. Çok yüksek test kapsamına ve çok az desteklenmeyen koda sahipler. Sistemin küçük ama çalışan sürümlerini oluşturarak ve ardından artımlı işlevsellik ekleyerek riskleri en aza indirgerler. Kısa ve sık yinelemeler üzerinde kendi kodunu geliştirirler. Bu, değişikliği güvenle benimsemelerine, kodu sık sık yeniden düzenlemelerine ve "önden büyük tasarımdan" kaçınmalarına olanak sağlar.

Lucerne, bazıları 40'dan eski olan çok daha büyük ve karmaşık bir sistem koleksiyonuna sahiptir. Eski kodun karmaşıklığı ve kapsamı nedeniyle değişiklik yapma konusunda çok dikkatlidirler. Ayrıntılı çözümler tasarlamayı ve geliştirme sırasında oluşan tasarım ve değişiklikleri belgelemeyi tercih eden daha zorlu bir geliştirme sürecini takip eder.

Her iki ekip de kullanıcıların ihtiyaçlarını Visual Studio sistemleri geliştirmelerine yardımcı olmak için Visual Studio modelleme diyagramlarını kullanır. Bu Team Foundation Server planlama, düzenleme ve yönetmelerine yardımcı olmak için diğer araçlarla birlikte kullanır.

Daha fazla bilgi için Team Foundation Server bkz:

- [İşi planlayın ve izleyin](#plan-and-track-work)

- [Güncelleştirilmiş kodu test etme, doğrulama ve denetleme](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a> Yazılım Geliştirmede Mimari ve Modelleme Diyagramlarının Rolleri

Aşağıdaki tabloda, bu araçların yazılım geliştirme yaşam döngüsünün birden çok aşamasında ve çeşitli aşamalarında oynatabilirsiniz rolleri açıkmektedir:

|Araç / Rol|Kullanıcı Gereksinimleri Modellemesi|İş Süreci Modellemesi|Sistem Mimarisi & Tasarımı|Kod Görselleştirme & Keşfetme|Doğrulama|
|------|-|-|-|-|-|
|Domain-Specific Dili (DSL) diyagramı|Yes|Yes|Yes|||
|Bağımlılık diyagramı, katman doğrulaması|||Yes|Yes|Yes|
|Kod haritası|||Yes|Yes|Yes|
|Sınıf Tasarımcısı (kod tabanlı)||||Yes||

Bağımlılık diyagramları çizmek için mevcut bir çözümün veya yeni bir çözümün parçası olarak bir modelleme projesi oluşturmanız gerekir. Bu diyagramların modelleme projesinde oluşturulmuş olması gerekir.
Bağımlılık diyagramları öğeleri modelleme projesinde bulunur, ancak ortak modelde depolanmaz. Kod eşlemeleri ve koddan oluşturulan .NET sınıf diyagramları modelleme projesinin dışında yer almaktadır.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Her iki ekip de geliştirme aşamasındaki kodun tasarımla tutarlı kalmasını sağlamak için bağımlılık doğrulamasını kullanır. Bkz.

- [Kodu Tasarımla Tutarlı Tutma](#ValidatingCode)

- [Mantıksal Mimariyi Açıklama: Bağımlılık Diyagramları](#DescribeLayers)

- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Bazı sürümler Visual Studio ve modelleme için kod eşlemelerinin bağımlılık doğrulamasını ve salt okunur sürümlerini destekler. Bu özelliği destekleyen Visual Studio için bkz. Mimari ve [modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="understand-and-communicate-information-about-the-system"></a>Sistemle ilgili bilgileri anlama ve iletişim kurma

Veri modelleme diyagramlarını kullanmak için Visual Studio düzen yoktur, bu nedenle bunları ihtiyaçlarınıza veya yaklaşımınıza uygun şekilde kullanabilirsiniz. Ekipler genellikle bir proje boyunca modellerini tekrar tekrar ziyaret ediyor. Her diyagram, geliştirme aşamasındaki sistemin farklı yönlerini anlamanıza, açıklamanıza ve iletişim kurmanıza yardımcı olmak için belirli güçler sunar.

Şimdi Akşam Yemeği ve Lucerne, ortak dil olarak diyagramları kullanarak birbirleriyle ve proje katılımcılarıyla iletişim kurar. Örneğin, Şimdi Akşam Yemeği şu görevleri gerçekleştirmek için diyagramları kullanır:

- Mevcut kodu görselleştirme.

- Lucerne ile yeni veya güncelleştirilmiş kullanıcı hikayeleri hakkında iletişim kurma.

- Yeni veya güncelleştirilmiş kullanıcı hikayelerini desteklemek için gereken değişiklikleri belirleme.

Lucerne şu görevleri gerçekleştirmek için diyagramları kullanır:

- Şimdi Akşam Yemeği iş süreci hakkında bilgi edinmek.

- Sistemin tasarımını anlama.

- Şimdi Akşam Yemeği ile yeni veya güncelleştirilmiş kullanıcı gereksinimleri hakkında iletişim kurma.

- Sistem güncelleştirmelerini belgele.

Diyagramlar, ekiplerin çalışmalarını Team Foundation Server kolay bir şekilde planlamak, yönetmek ve izlemek için Team Foundation Server ile tümleştirilmiştir. Örneğin, test çalışmalarını ve geliştirme görevlerini tanımlamak ve çalışmalarını tahmin etmek için modelleri kullanır. Lucerne, Team Foundation Server izlemelerini ve sistemin kullanıcıların gereksinimlerini karşılay olduğundan emin olmak için iş öğelerini model öğelerine bağlar. Örneğin, tüm testler başarılı olduğunda kullanım durumlarının yerine getirilmesini görmek için kullanım çalışmalarını test çalışması iş öğelerine bağlar.

Ekipler değişikliklerini denetlemeden önce bağımlılık doğrulaması ve otomatikleştirilmiş testler içeren derlemeler çalıştırarak kodu testlere ve tasarıma göre doğrular. Bu, güncelleştirilmiş kodun tasarımla çakışmamalarını ve daha önce çalışan işlevselliği bozmalarını sağlar.

### <a name="identify-changes-to-the-existing-system"></a>Mevcut Sistemde Yapılan Değişiklikleri Tanımlama

Şimdi Akşam Yemeği, yeni gereksinimin karşılanma maliyetini tahmin etmek gerekir. Bu, kısmen bu değişikliğin sistemin diğer bölümlerini ne kadar etkileyeceğini etkiler. Bunu anlamalarına yardımcı olmak için Şimdi Akşam Yemeği geliştiricilerinden biri mevcut koddan şu haritaları ve diyagramları oluşturur:

|**Harita veya diyagram**|**Diziler**|
|-|-|
|*Kod haritası*<br /><br /> Bkz.<br /><br /> - [Çözümleriniz genelinde bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br />- [Kod haritalarına göz atma ve yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)<br />- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Kodda bağımlılıklar ve diğer ilişkiler.<br /><br /> Örneğin Şimdi Akşam Yemeği, derlemelere ve bağımlılıklarına genel bir bakış için derleme kod eşlemelerini gözden geçirerek başlayabilir. Bu derlemelerde ad alanlarını ve sınıfları keşfetmek için haritalarda detaya inerler.<br /><br /> Şimdi Akşam Yemeği, kodda belirli alanları ve diğer ilişki türlerini keşfetmek için haritalar da oluşturabilir. İlgi Çözüm Gezgini alanları ve ilişkileri bulmak ve seçmek için Çözüm Gezgini kullanırlar.|
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz. [Nasıl: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Kodda mevcut sınıflar|

 Örneğin geliştirici bir kod haritası oluşturur. Kapsamını, yeni senaryodan etkilenecek alanlara odaklanacak şekilde ayarlar. Bu alanlar haritada seçili ve vurgulanmış:

 ![Ad Alanı Bağımlılığı Graph](../modeling/media/namespace_reviewsystem.png)

 **Ad alanı kod eşlemesi**

 Geliştirici sınıflarını, yöntemlerini ve ilişkilerini görmek için seçilen ad alanlarını genişletmektedir:

 ![Genişletilmiş ad alanı bağımlılık grafiği](../modeling/media/dep_reviewsystem.png)

 **Görünür çapraz grup bağlantılarıyla genişletilmiş ad alanı kod eşlemesi**

 Geliştirici etkilenen sınıfları ve yöntemleri bulmak için kodu inceler. Her değişikliğin etkilerini siz oluşturken görmek için, her değişiklik sonrasında kod eşlemelerini yeniden üretin. Bkz. [Kodu görselleştirme.](../modeling/visualize-code.md)

 Takım, sistemin bileşenler veya etkileşimler gibi diğer kısımlarında yapılan değişiklikleri açıklamak için bu öğeleri beyaz tahtalara çizebilirsiniz. Ayrıntılar her iki ekip tarafından da yakalanıp Visual Studio için aşağıdaki diyagramları aşağıdaki diyagramlarda çizebilirsiniz:

|**Diyagramları**|**Açıklanır**|
|-|-|
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz. [Nasıl: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Kodda mevcut sınıflar.|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a> Tasarımla Kodu Tutarlı Tutma
 Şimdi Akşam Yemeği güncelleştirilmiş kodun tasarımla tutarlı olduğundan emin olmalıdır. Sistemdeki işlev katmanlarını açıklayan, aralarında izin verilen bağımlılıkları belirten ve çözüm yapıtlarını bu katmanlarla ilişkilendirilen bağımlılık diyagramları oluşturabilirler.

|**Diyagram**|**Açıklanır**|
|-|-|
|*Bağımlılık diyagramı*<br /><br /> Bkz.<br /><br /> - [Kodunuzdan bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|Kodun mantıksal mimarisi.<br /><br /> Bağımlılık diyagramı, bir çözümdeki yapıtları düzenler ve Visual Studio olarak adlandırılan soyut gruplara *eşler.* Bu katmanlar, bu yapıtların sistemde gerçekleştirecekleri rolleri, görevleri veya işlevleri tanımlayabilir.<br /><br /> Bağımlılık diyagramları sistemin hedeflenen tasarımını açıklama ve gelişen kodu bu tasarıma göre doğrulama için yararlıdır.<br /><br /> Katmanlar oluşturmak için öğeleri Çözüm Gezgini, kod eşlemeleri, Sınıf Görünümü ve Object Browser'dan sürükleyin. Yeni katmanlar çizmek için araç kutusunu kullanın veya diyagram yüzeyine sağ tıklayın.<br /><br /> Mevcut bağımlılıkları görüntülemek için bağımlılık diyagramı yüzeyine sağ tıklayın ve ardından Bağımlılıkları **Oluştur'a tıklayın.** Hedeflenen bağımlılıkları belirtmek için yeni bağımlılıklar çizin.|

Örneğin, aşağıdaki bağımlılık diyagramı katmanlar arasındaki bağımlılıkları ve her katmanla ilişkili yapıt sayısını açıklar:

![Tümleşik ödeme sisteminin bağımlılık diyagramı](../modeling/media/layer_integrated_dnlucerne.png)

 **Bağımlılık Diyagramı**

Kod geliştirme sırasında tasarımla çakışmaların oluşmay olduğundan emin olmak için ekipler, kod geliştirme sırasında çalıştırıldık derlemelerde bağımlılık doğrulamayı Azure DevOps. Ayrıca, iade MSBuild bağımlılık doğrulaması gerektirmek için özel bir özel görev oluşturma. Doğrulama hatalarını toplamak için derleme raporlarını kullanırlar.

Bkz.

- [Görsel tasarımcıyı kullanma](/azure/devops/pipelines/get-started-designer)

- [TFVC geçitli iade](/azure/devops/pipelines/build/triggers)

- [Derleme ve sürüm görevleri](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Modelleri İpuçları Kullanmaya Genel Uygulama

- Çoğu diyagram, satırlarla bağlanan düğümlerden oluşur. Her diyagram türü için araç kutusu farklı türde düğümler ve çizgiler sağlar.

   Araç kutusunu açmak için Görünüm menüsünde **Araç** Kutusu'na **tıklayın.**

- Bir düğüm oluşturmak için bu düğümü araç kutusundan diyagrama sürükleyin. Belirli düğüm türleri mevcut düğümlere sürüklenmeli. Örneğin, bir bileşen diyagramında var olan bir bileşene yeni bir bağlantı noktası eklenmiştir.

- Bir satır veya bağlantı oluşturmak için araç kutusunda uygun aracı tıklatın, kaynak düğüme tıklayın ve ardından hedef düğüme tıklayın. Bazı satırlar yalnızca belirli düğüm türleri arasında oluşturulabilir. İşaretçiyi olası bir kaynağın veya hedefin üzerine taşıyabilirsiniz, işaretçi bağlantı oluşturıp oluştura olmadığınızı gösterir.

### <a name="plan-and-track-work"></a>İşi planlayın ve izleyin

Visual Studio modelleme diyagramları, işi daha Team Foundation Server şekilde planlamak, yönetmek ve izlemek için Team Foundation Server ile tümleştirilmiştir. Her iki ekip de test çalışmalarını ve geliştirme görevlerini tanımlamak ve çalışmalarını tahmin etmek için modelleri kullanır. Lucerne, iş öğelerini Team Foundation Server örnekleri veya bileşenleri gibi model öğelerine bağlar ve bu öğeleri bağlar. Bu, ilerleme durumlarını izlemelerine ve çalışmalarını kullanıcıların gereksinimlerine göre izlemelerine yardımcı olur. Bu, değişikliklerinin bu gereksinimleri karşılamaya devam ettiğine emin olmaya yardımcı olur.

Ekipler, çalışmaları ilerledikçe iş öğelerini görevlerine harcadığı zamanı yansıtacak şekilde güncelleştiriyor. Ayrıca, aşağıdaki özellikleri kullanarak çalışmalarını izleyebilir ve durumlarını Team Foundation Server sunarlar:

- Planlanan *işi beklenen* zamanda tamamlamayacaklarını göstermek için günlük yazma raporları. Hataların ilerlemesini izlemek Team Foundation Server başka benzer raporlar da üretirler.

- Ekibin *iş* yükünü üyeleri Microsoft Excel ve dengelemesine yardımcı olmak için Microsoft Excel çalışma sayfasını kullanan yineleme çalışma sayfası. Bu çalışma sayfası, Team Foundation Server ve düzenli ilerleme toplantılarında tartışma odağı sağlar.

- Ekibi *önemli proje* bilgileri Office Project için bu panoyu kullanan geliştirme panosu.

Bkz.

- [Çevik araçlar ve Çevik proje yönetimi hakkında](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)

- [Grafikler, panolar ve pencere öğeleri (Azure DevOps Services)](/azure/devops/report/dashboards/overview?view=vsts&preserve-view=true)

- [Project kullanarak biriktirme Project](/previous-versions/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a> Kodu Test Edin, Doğrula ve Iade Edin

Ekipler her görevi tamamlayan ekipler, kodunu kaynak denetimine alır ve unutursa Team Foundation Server anımsatıcılar alır. Ekip Team Foundation Server girişlerini kabul etmeden önce ekipler birim testleri ve bağımlılık doğrulaması çalıştırarak kodu test çalışmalarına ve tasarıma göre doğrular. Derlemeleri, Team Foundation Server testleri ve bağımlılık doğrulamayı düzenli olarak çalıştırmak için Team Foundation Server kullanırlar. Bu, kodun aşağıdaki ölçütlere uygun olduğundan emin olunmanıza yardımcı olur:

- Çalışır.

- Daha önce çalışan kodu bozmaz.

- Tasarımla çakışmaz.

Şimdi akşam yemeği, neredeyse hepsi hala uygulandığı için Lucerne 'ın yeniden kullanılabilir olduğu büyük bir otomatik test koleksiyonuna sahiptir. Lucerne ayrıca bu testleri oluşturabilir ve yeni işlevleri kapsayacak yeni işlevler ekleyebilir. ayrıca, el ile testleri çalıştırmak için Visual Studio de kullanın.

kodun tasarıma uygun olduğundan emin olmak için takımlar Azure DevOps yapılarını bağımlılık doğrulamasını içerecek şekilde yapılandırır. Herhangi bir çakışma oluşursa, ayrıntılarla birlikte bir rapor oluşturulur.

Bkz.

- [Uygulamayı test etme](/azure/devops/test/overview?view=vsts&preserve-view=true)

- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)

- [Sürüm denetimini kullanma](/azure/devops/repos/tfvc/overview?view=azure-devops&preserve-view=true)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)

## <a name="update-the-system-using-visualization-and-modeling"></a>Görselleştirme ve modelleme kullanarak sistemi güncelleştirme

Lucerne ve Dinner Now ödeme sistemlerini tümleştirmelidir. aşağıdaki bölümlerde bu görevi gerçekleştirmelerine yardımcı olan Visual Studio modelleme diyagramları gösterilmektedir:

- [mevcut kodu görselleştirin: kod Haritalar](#VisualizeCode)

- [Türler sözlüğü tanımlayın: sınıf diyagramları](#DefineClasses)

- [Mantıksal mimariyi açıkla: bağımlılık diyagramları](#DescribeLayers)

Bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)

- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>mevcut kodu görselleştirin: kod Haritalar

Kod haritaları, koddaki geçerli organizasyonu ve ilişkileri gösterir. Öğeler haritadaki *düğümler* tarafından temsil edilir ve ilişkiler *bağlantılarla* temsil edilir. Kod haritaları aşağıdaki türde görevleri gerçekleştirmenize yardımcı olabilir:

- Bilmediğiniz kodu keşfet.

- Önerilen bir değişikliğin mevcut kodu nerede ve nasıl etkileyebileceğini anlayın.

- Karmaşıklığa, doğal bağımlılıklara veya desenlere ya da geliştirmelerden faydalanabilir diğer alanlara ilişkin alan bulun.

Örneğin, şimdi akşam yemeği PaymentProcessing bileşenini güncelleştirme maliyetini tahmin etmelidir. Bu, kısmen bu değişikliğin sistemin diğer bölümlerini ne kadar etkileyeceğini gösterir. Bunu anlamalarına yardımcı olmak için Dinner Now geliştiricilerinden biri koddan kod haritaları oluşturur ve bu değişiklik, değişikliğin etkilenmiş olabileceği alanlara odaklanarak kapsamını ayarlar.

Aşağıdaki haritada, PaymentProcessing sınıfı ve seçili görünen Dinner Now sisteminin diğer kısımları arasındaki bağımlılıklar gösterilmektedir:

![Dinner Now ödeme sistemi için bağımlılık grafiği](../modeling/media/dep_dnpayment.png)

**Dinner Now ödeme sistemi için kod Haritası**

Geliştirici,, potansiyel olarak etkilenebilecek olan bölgeleri görmek için PaymentProcessing sınıfını genişleterek ve üyelerini seçerek Haritayı araştırır:

![PaymentProcessing ve Dependencies içindeki Yöntemler](../modeling/media/depgraph_expandeddn.png)

**PaymentProcessing sınıfının ve bağımlılıklarındaki Yöntemler**

Bu kişiler, sınıflarını, yöntemlerini ve bağımlılıklarını incelemek için Lucerne ödeme sistemi için aşağıdaki eşlemeyi oluşturur. Ekip, Lucerne sisteminin şu anda akşam yemeği 'nin diğer bölümleriyle etkileşim kurması için de gerekli olabileceğini görür:

![Lucerne ödeme sistemi için bağımlılık grafiği](../modeling/media/depgraph_lucernepay.png)

**Lucerne ödeme sistemi için kod Haritası**

Her iki ekip de iki sistemi bütünleştirmek için gereken değişiklikleri belirlemede birlikte çalışır. Daha kolay güncelleştirilmesini sağlamak için bazı kodları yeniden düzenleme kararı verir. PaymentApprover sınıfı DinnerNow. Business ad alanına geçer ve bazı yeni yöntemler gerektirir. İşlemleri işleyen şimdi akşam yemeği sınıflarının kendi ad alanı olacaktır. Takımlar işlerini planlamak, düzenlemek ve izlemek için iş öğeleri oluşturup kullanır. İş öğelerini, yararlı olduğu yerde model öğelerine bağlar.

Kodu yeniden belirledikten sonra takımlar, güncelleştirilmiş yapıyı ve ilişkileri görmek için yeni bir kod haritası oluşturur:

![Yeniden düzenlenmiş kodla bağımlılık grafiği](../modeling/media/depgraph_integrated.png)

**Yeniden düzenlenmiş kodla kod Haritası**

Bu harita, PaymentApprover sınıfının artık DinnerNow. Business ad alanında olduğunu ve bazı yeni yöntemlere sahip olduğunu gösterir. Şimdi akşam yemeği işlem sınıflarının artık kendi PaymentSystem ad alanı vardır ve bu kod daha sonra bu kodla daha kolay bir şekilde uğraşmayı kolaylaştırır.

#### <a name="creating-a-code-map"></a>Kod Haritası oluşturma

- Kaynak koda hızlı bir genel bakış için, bir kod haritası oluşturmak için aşağıdaki adımları izleyin:

     **Mimari** menüsünde **çözüm Için kod Haritası Oluştur**' a tıklayın.

     Derlenmiş koda hızlı bir genel bakış için, boş bir kod haritası oluşturun ve ardından derleme dosyalarını veya ikili dosyaları harita yüzeyine sürükleyin.

- Belirli kod veya çözüm öğelerini araştırmak için, görselleştirmek istediğiniz öğeleri ve ilişkileri seçmek üzere Çözüm Gezgini kullanın. Daha sonra yeni bir eşleme oluşturabilir veya seçili öğeleri var olan bir haritaya ekleyebilirsiniz. Bkz. [çözümlerinizde harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md).

- Haritayı keşfetmenize yardımcı olması için düzeni, yapmak istediğiniz görev türlerine uygun olacak şekilde yeniden düzenleyin.

     Örneğin, koddaki katmanlamayı görselleştirmek için bir ağaç düzeni seçin. Bkz. [kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md).

#### <a name="summary-strengths-of-code-maps"></a>özet: kodun güçlü yönleri Haritalar
 Kod haritaları şunları yapmanıza yardımcı olur:

- Mevcut koddaki kuruluş ve ilişkiler hakkında bilgi edinin.

- Önerilen bir değişiklikten etkilenebilecek olan bölgeleri belirler.

- Kodun bakımını, değiştirilmesini ve yeniden kullanılmasını kolaylaştırmak için iyileştirebildiğiniz karmaşıklık, desen, katman veya diğer alanların bölgelerini bulun.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Anlatır**|
|-|-|
|Bağımlılık diyagramı|Sistemin mantıksal mimarisi. Kodun tasarımla tutarlı kalmasını sağlamak için bağımlılık doğrulaması ' nı kullanın.<br /><br /> Mevcut bağımlılıkları veya hedeflenen bağımlılıkları belirlemenize yardımcı olmak için bir kod haritası oluşturun ve ilişkili öğeleri gruplayın. Bağımlılık diyagramı oluşturmak için, bkz:<br /><br /> - [Kodunuzda bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)|
|Sınıf diyagramı (kod tabanlı)|Belirli bir proje için koddaki mevcut sınıflar.<br /><br /> Koddaki mevcut bir sınıfı görselleştirmek ve değiştirmek için Sınıf Tasarımcısı kullanın.<br /><br /> Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme (sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a> Türler sözlüğü tanımlayın: sınıf diyagramları
 Sınıf diyagramları, sisteme ve bunların ilişkilerine katılan varlıkları, terimleri veya kavramları bir diğeri ile tanımlar. Örneğin, uygulama dilinden veya tarzlarından bağımsız olarak her sınıfın özniteliklerini ve işlemlerini anlatmak için bu diyagramları geliştirme sırasında kullanabilirsiniz.

 Lucerne 'ın Işlem ödemesi kullanım örneğine katılan varlıkları açıklaması ve tartışmalarına yardımcı olmak için aşağıdaki sınıf diyagramını çizirler:

 ![Sınıf diyagramında işlem ödemesi varlıkları](../modeling/media/uml_payentities.png)

 **Bir sınıf diyagramında işlem ödemesi varlıkları**

 Bu diyagramda, bir müşterinin birçok siparişi ve siparişler için ödeme yapmak için farklı yolları olduğunu gösterir. BankAccount ve CreditCard her ikisi de ödemeden devralınır.

 Geliştirme sırasında Lucerne, her bir sınıfın ayrıntılarını açıklamak ve tartışmak için aşağıdaki sınıf diyagramını kullanır:

 ![Bir sınıf diyagramında ödeme varlığı ayrıntılarını işleme](../modeling/media/uml_payment.png)

 **Sınıf diyagramında işlem ödemesi ayrıntıları**

#### <a name="drawing-a-class-diagram"></a>Sınıf diyagramı çizme

Bir sınıf diyagramı aşağıdaki önemli özelliklere sahiptir:

- Sınıflar, arabirimler ve numaralandırmalar gibi türler:

  - *Sınıf* , belirli yapısal veya davranış özelliklerini paylaşan nesnelerin tanımıdır.

  - Bir *arabirim* , bir nesnenin dışarıdan görünür davranışının bir parçasını tanımlar.

  - *Sabit* listesi, değişmez değerlerin bir listesini içeren bir sınıflandırıcıdır.

- *Öznitelikler* , bir *sınıflandırıcının* her örneğini tanımlayan belirli bir türün değerleridir. Sınıflandırıcı, türler, bileşenler, kullanım örnekleri ve hatta aktörler için genel bir addır.

- *İşlemler* , bir sınıflandırıcı örneklerinin gerçekleştirebileceği Yöntemler veya işlevlerdir.

- *İlişki* , iki sınıflandırıcıda oluşan bazı ilişki türlerini gösterir.

  - *Toplama* , sınıflandırıcılar arasındaki paylaşılan sahipliği gösteren bir ilişkidir.

  - *Birleşim* , sınıflandırıcılar arasındaki bir bütün parçalı ilişkiyi gösteren bir ilişkidir.

    Toplamaları veya kompozisyonları göstermek için bir ilişkilendirmede **toplama** özelliğini ayarlayın. **Paylaşılan** toplamalar ve **bileşik** , bileşimler gösterir.

- *Bağımlılık* , bir sınıflandırıcının tanımını değiştirmenin başka bir sınıflandırıcının tanımını değiştirebileceğini gösterir.

- *Genelleştirme* , belirli bir sınıflandırıcının, genel sınıflandırıcının tanımının bir parçasını devraldığını gösterir. Bir *gerçekleştirme* , bir sınıfın bir arabirim tarafından sunulan işlemleri ve öznitelikleri uyguladığını gösterir.

     Bu ilişkileri oluşturmak için **Devralma** aracını kullanın. Alternatif olarak, bir gerçekleştirme *Lolipop* olarak temsil edilebilir.

- *Paketler* , Sınıflandırıcıların, ilişkilerin, Yaşam çizgilerinin, bileşenlerin ve diğer paketlerin gruplarıdır. *Içeri aktarma* ilişkileri bir paketin başka bir paketin tüm tanımlarını içerdiğini belirtir.

Mevcut sınıfları araştırmak ve tartışmak için bir başlangıç noktası olarak, koddan sınıf diyagramları oluşturmak için Sınıf Tasarımcısı kullanabilirsiniz.

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Özet: sınıf diyagramlarının güçleri
 Sınıf diyagramları şunları tanımlamanıza yardımcı olur:

- Kullanıcıların ihtiyaçlarını ve sisteme katılan varlıkları ele alırken kullanılacak koşulların ortak bir sözlüğü. Bkz. [model Kullanıcı gereksinimleri](../modeling/model-user-requirements.md).

- Uygulandıkları bağımsız olarak, sistem parçaları tarafından kullanılan türler. Bkz. [uygulamanızın mimarisini modelleme](../modeling/model-your-app-s-architecture.md).

- Türler arasında bağımlılıklar gibi ilişkiler. Örneğin, bir türün başka bir türün birden çok örneğiyle ilişkilendirilebilen gösterebilir.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklama**|
|-|-|
|Bağımlılık diyagramı|Sınıfların ilişkili olduğu şekliyle sistemin mantıksal mimarisini tanımlayın.<br /><br /> Kodun tasarımla tutarlı kalmasını sağlamak için bağımlılık doğrulaması ' nı kullanın.<br /><br /> Bkz.<br /><br /> - [Kodunuzda bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|
|Kod eşlemesi|Var olan koddaki organizasyonu ve ilişkileri görselleştirin.<br /><br /> Sınıfları, ilişkilerini ve yöntemlerini tanımlamak için, bu öğeleri gösteren bir kod haritası oluşturun.<br /><br /> Bkz.<br /><br /> - [Çözümleriniz genelinde bağımlılıkları eşleyin](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a> Mantıksal mimariyi açıkla: bağımlılık diyagramları
 Bağımlılık diyagramları, çözümünüzdeki yapıtları soyut gruplar veya *Katmanlar* halinde düzenleyerek sistemin mantıksal mimarisini anlatmaktadır. Artifacts, ad alanları, projeler, sınıflar, yöntemler vb. gibi çok sayıda şey olabilir. Katmanlar, yapıların sistemde gerçekleştirdiği rolleri veya görevleri temsil eder ve tanımlarlar. Ayrıca, kodun tasarımıyla tutarlı kalmasını sağlamak için yapı ve iade işlemlerinizin katman doğrulamasını da dahil edebilirsiniz.

 Kodu tasarımla tutarlı tutmak için şimdi akşam yemeği ve Lucerne, geliştikçe kodun doğrulanması için aşağıdaki bağımlılık diyagramını kullanır:

 ![Tümleşik ödeme sisteminin bağımlılık diyagramı](../modeling/media/layer_integrated_dnlucerne.png)

 **Artık Lucerne ile tümleştirilmiş akşam yemeği için bağımlılık diyagramı**

 Bu diyagramdaki Katmanlar ilgili akşam yemeği ve Lucerne çözüm yapıtlarına bağlanır. Örneğin, Iş katmanı, artık PaymentApprover sınıfını içeren DinnerNow. Business ad alanı ve üyelerine bağlanır. Kaynak erişim katmanı, DinnerNow. Data ad alanına bağlanır. Oklar veya *Bağımlılıklar*, yalnızca iş katmanının, kaynak erişim katmanındaki işlevselliği kullanmasını belirler. Takımlar kodlarını güncelleştirdiklerinde, çakışmalar olduğu gibi yakalamak ve ekiplerin bunları daha sonra çözmelerine yardımcı olmak için katman doğrulaması düzenli olarak gerçekleştirilir.

 Takımlar, iki sistemi artımlı olarak bütünleştirmek ve test etmek için birlikte çalışır. İlk olarak, PaymentApprover ve Dinner 'ın geri kalanının, PaymentProcessing ile uğraşmadan önce başarıyla bir kez daha çalışır durumda olduğundan emin olun.

 Aşağıdaki kod eşlemesinde Dinner Now ve PaymentApprover arasındaki yeni çağrılar gösterilmektedir:

 ![Tümleşik sistemle birlikte bağımlılık grafiği güncelleştirildi](../modeling/media/depgraph_intsystem.png)

 **Güncelleştirilmiş yöntem çağrılarında kod Haritası**

 Sistemin beklendiği gibi çalışmadığını doğruladıktan sonra, şimdi akşam yemeği PaymentProcessing kodunu yorumlar. Katman doğrulama raporları temiz ve sonuçta elde edilen kod haritasında başka bir PaymentProcessing bağımlılığı yok gösterilmektedir:

 ![PaymentProcessing olmadan bağımlılık grafiği](../modeling/media/depgraph_nomore.png)

 **PaymentProcessing olmadan kod Haritası**

#### <a name="drawing-a-dependency-diagram"></a>Bağımlılık diyagramı çizme

Bağımlılık diyagramı aşağıdaki önemli özelliklere sahiptir:

- *Katmanlar* , yapıların mantıksal gruplarını anlatmaktadır.

- *Bağlantı* , bir katman ve yapıt arasındaki ilişkidir.

     Yapıtlar arasından katmanlar oluşturmak için Çözüm Gezgini, kod haritaları, Sınıf Görünümü veya Nesne Tarayıcısı öğelerini sürükleyin. Yeni Katmanlar çizmek ve sonra yapıtları bağlamak için araç kutusunu kullanın veya katmanları oluşturmak için Diyagram yüzeyine sağ tıklayıp öğeleri bu katmanlara sürükleyin.

     Katmandaki sayı katmana bağlı yapıların sayısını gösterir. Bu yapıtlar ad alanları, projeler, sınıflar, yöntemler vb. olabilir. Bir katmandaki yapıt sayısını yorumladığınızda, aşağıdakileri unutmayın:

  - Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.

       Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.

  - Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.

    Bir katmana bağlı olan yapıtları görmek için bağımlılığa sağ tıklayın ve sonra **Katman Gezgini**'ni açmak Için **bağlantıları görüntüle** ' ye tıklayın.

- Bir *bağımlılık* , bir katmanın işlevselliği başka bir katmanda kullanabilir ancak tersi anlamına gelir. *Çift yönlü bağımlılık* , bir katmanın başka bir katmandaki işlevleri kullanacağını ve bunun tersini gösterir.

     Bağımlılık diyagramında mevcut bağımlılıkları göstermek için Diyagram yüzeyine sağ tıklayın ve ardından **Bağımlılıklar Oluştur**' a tıklayın. Hedeflenen bağımlılıkları betimleyen, yenilerini çizin.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)

- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)

- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Özet: bağımlılık diyagramlarından güçlü yönler

Bağımlılık diyagramları şunları yapmanıza yardımcı olur:

- Yapılarının işlevselliğine göre sistemin mantıksal mimarisini açıklama.

- Geliştirme aşamasındaki kodun belirtilen tasarıma uyduğundan emin olun.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklama**|
|-|-|
|Kod eşlemesi|Var olan koddaki organizasyonu ve ilişkileri görselleştirin.<br /><br /> Katmanlar oluşturmak için bir kod haritası oluşturun ve ardından haritadaki öğeleri olası Katmanlar olarak gruplayın. Grupları haritadan bağımlılık diyagramına sürükleyin.<br /><br /> Bkz.<br /><br /> - [Çözümleriniz genelinde bağımlılıkları eşleyin](../modeling/map-dependencies-across-your-solutions.md)<br />- [Kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Bağlantılar**|
|-|-|
|**Forumlar**|- [Visual Studio Görselleştirme & modelleme araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Görselleştirme & modelleme SDK 'Sı (DSL araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Ayrıca bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
- [Çevik geliştirmede modelleri kullanma](/previous-versions/ff398061(v=vs.140))
- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)
