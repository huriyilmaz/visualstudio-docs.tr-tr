---
title: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme
description: Visual Studio 'da görselleştirme ve modelleme araçlarına genel bakış.
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
author: JoshuaPartlow
ms.author: joshuapa
ms.custom: SEO-VS-2020
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6ad330c083a97e8a098f05a9e0398a806a9153b
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189139"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme

Yazılım sisteminizin, Visual Studio 'da görselleştirme ve modelleme araçlarını kullanarak kullanıcıların ihtiyaçlarını karşıladığından emin olun.
Kod haritaları, bağımlılık diyagramları ve sınıf diyagramları gibi araçları kullanarak şunları yapın:

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

## <a name="scenario-overview"></a>Senaryoya genel bakış

Bu senaryo, iki kurgusal şirketin yazılım geliştirme yaşam döngülerine ait bölümleri açıklar: şimdi akşam yemeği ve Lucerne Publishing. Şimdi akşam yemeği Seattle 'da Web tabanlı bir yiyecek teslim hizmeti sağlar. Müşteriler şimdi akşam yemeği Web sitesinde yemekleri sipariş edebilir ve ödeyebilir. Daha sonra siparişler teslim için uygun yerel restora gönderilir. New York 'ta bir şirket olan Lucerne Publishing, hem kapalı hem de Web üzerinde çalışan birkaç işletme. Örneğin, müşterilerin Restoran İncelemeleri nakledebileceği bir Web sitesi çalıştırırlar.

Kısa süre önce Dinner Now alındı ve aşağıdaki değişiklikleri yapmak istiyor:

- Şimdi akşam yemeği 'e Restoran gözden geçirme özellikleri ekleyerek Web sitelerini tümleştirin.

- Dinner Now 'ın ödeme sistemini Lucerne 'ın sistemiyle değiştirin.

- Şimdi akşam yemeği hizmetini bölge genelinde genişletin.

Şimdi Akşam Yemeği SCRUM ve eXtreme programlama kullanıyor. Bunlar çok yüksek test kapsamına ve çok az desteklenmeyen koda sahiptir. Bir sistemin küçük ancak çalışan sürümlerini oluşturup daha sonra işlevselliği artımlı olarak ekleyerek riskleri en aza indirirler. Bunlar, kodlarını kısa ve sık sık yinelemeler üzerinde geliştirir. Bu, hafif bir şekilde değişiklik yapmayı, kodu sık yeniden düzenlemenizi ve "büyük tasarım önünden" kaçınmasını sağlar.

Lucerne, bazıları 40 yılı aşkın olan büyük ölçüde daha büyük ve karmaşık bir sistem koleksiyonunu tutar. Eski kodların karmaşıklığı ve kapsamı nedeniyle değişiklik yapma konusunda çok dikkatli olurlar. Daha kapsamlı bir geliştirme sürecini izleyerek, ayrıntılı çözümler tasarlamayı ve geliştirme sırasında oluşan tasarımı ve değişiklikleri belgelemeyi tercih ederler.

Her iki ekip, kullanıcıların ihtiyaçlarını karşılayan sistemler geliştirmeye yardımcı olmak için Visual Studio 'da modelleme diyagramları kullanır. Bunlar, işlerini planlamaya, düzenlemenize ve yönetmesine yardımcı olması için diğer araçlarla birlikte Team Foundation Server kullanırlar.

Team Foundation Server hakkında daha fazla bilgi için bkz.:

- [İşi planlayın ve izleyin](#plan-and-track-work)

- [Test, doğrulama ve güncelleştirilmiş kodu iade etme](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a> Yazılım geliştirmede mimari ve modelleme diyagramları rolleri

Aşağıdaki tabloda, bu araçların yazılım geliştirme yaşam döngüsünün birden çok ve çeşitli aşamaları sırasında oynayabileceği roller açıklanmaktadır:

|Araç/rol|Kullanıcı gereksinimleri Modelleme|İş süreci modelleme|Sistem mimarisi & tasarımı|Kod görselleştirme & araştırması|Doğrulama|
|------|-|-|-|-|-|
|Domain-Specific Language (DSL) diyagramı|Evet|Evet|Evet|||
|Bağımlılık diyagramı, katman doğrulama|||Evet|Evet|Evet|
|Kod eşlemesi|||Evet|Evet|Evet|
|Sınıf Tasarımcısı (kod tabanlı)||||Evet||

Bağımlılık diyagramları çizmek için, mevcut bir çözümün parçası olarak bir modelleme projesi oluşturmanız veya yeni bir tane oluşturmanız gerekir. Bu diyagramların modelleme projesinde oluşturulması gerekir.
Bağımlılık diyagramlarındaki öğeler, modelleme projesinde bulunur, ancak ortak modelde depolanmaz. Kod haritaları ve koddan oluşturulan .NET sınıf diyagramları, modelleme projesi dışında bulunur.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

- [Visual Studio için Modelleme SDK'sı - Etki Alanına Özgü Diller](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Her iki ekip de, geliştirme aşamasındaki kodun tasarımla tutarlı kalmasını sağlamak için bağımlılık doğrulaması kullanır. Bkz.

- [Kodu tasarımla tutarlı tutma](#ValidatingCode)

- [Mantıksal mimariyi açıkla: bağımlılık diyagramları](#DescribeLayers)

- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Visual Studio 'nun bazı sürümleri, bağımlılık doğrulamayı ve görselleştirme ve modelleme için kod eşlemelerinin salt okunurdur sürümlerini destekler. Hangi Visual Studio sürümlerini bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="understand-and-communicate-information-about-the-system"></a>Sistemle ilgili bilgileri anlayın ve iletişim kurun

Visual Studio Modelleme diyagramlarının kullanılması için önceden tanımlanmış bir sıra yoktur, bu sayede gereksinimlerinize veya yaklaşımlarınıza uygun şekilde kullanabilirsiniz. Genellikle takımlar modellerini bir proje boyunca tekrarlayarak ve sık sık yeniden ziyaret edin. Her diyagram, geliştirme aşamasındaki sistemin farklı yönlerini anlamanıza, açıklamanıza ve iletmede size yardımcı olmak için belirli güçler sunar.

Şimdi akşam yemeği ve Lucerne, ortak dil olarak diyagramlar kullanarak birbirleriyle ve proje hissedarlarıyla iletişim kurar. Örneğin, şimdi akşam yemeği bu görevleri gerçekleştirmek için diyagramlar kullanmaktadır:

- Mevcut kodu görselleştirin.

- Yeni veya güncelleştirilmiş Kullanıcı hikayeleri hakkında Lucerne ile iletişim kurun.

- Yeni veya güncelleştirilmiş kullanıcı hikayelerini desteklemek için gereken değişiklikleri belirler.

Lucerne bu görevleri gerçekleştirmek için diyagramlar kullanır:

- Şimdi akşam yemeği iş süreci hakkında bilgi edinin.

- Sistemin tasarımını anlayın.

- Yeni veya güncelleştirilmiş kullanıcı gereksinimleri hakkında şimdi akşam yemeği ile iletişim kurun.

- Sisteme belge güncelleştirmeleri.

Diyagramlar Team Foundation Server ile tümleşiktir, böylece takımlar işlerini daha kolay bir şekilde planlayabilir, yönetebilir ve izleyebilir. Örneğin, test çalışmalarını ve geliştirme görevlerini tanımlamak ve bunların çalışmalarını tahmin etmek için modeller kullanırlar. Lucerne bağlantıları, ilerlemeyi izleyebilmek ve sistemin Kullanıcı gereksinimlerini karşıladığından emin olmak için iş öğelerini model öğelerine Team Foundation Server. Örneğin, tüm testler başarılı olduğunda kullanım örneklerinin yerine getirildiğini görebilmesi için kullanım örneklerini test çalışması iş öğelerine bağlar.

Ekipler değişikliklerini iade etmeden önce, bağımlılık doğrulama ve otomatikleştirilmiş testler içeren derlemeler çalıştırarak test ve tasarıma karşı kodu doğrular. Bu, güncelleştirilmiş kodun tasarım ve daha önce çalışan işlevlerle çakışmadığından emin olmanıza yardımcı olur.

### <a name="identify-changes-to-the-existing-system"></a>Mevcut sistemdeki değişiklikleri tanımla

Şimdi akşam yemeği yeni gereksinimin toplantısının maliyetini tahmin etmelidir. Bu, kısmen bu değişikliğin sistemin diğer bölümlerini ne kadar etkileyeceğini gösterir. Bunu anlamalarına yardımcı olmak için Dinner Now geliştiricilerinden biri mevcut koddan bu haritaları ve diyagramları oluşturur:

|**Harita veya diyagram**|**Diziler**|
|-|-|
|*Kod eşlemesi*<br /><br /> Bkz.<br /><br /> - [Çözümleriniz genelinde bağımlılıkları eşleyin](../modeling/map-dependencies-across-your-solutions.md)<br />- [Kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md)<br />- [DGML dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Koddaki bağımlılıklar ve diğer ilişkiler.<br /><br /> Örneğin, şimdi akşam yemeği derlemeler ve bağımlılıklarına genel bir bakış için derleme kodu eşlemelerini inceleyerek başlayabilir. Bu derlemelerdeki ad alanlarını ve sınıfları araştırmak için Eşlemlerde detaya gidebilirler.<br /><br /> Şimdi akşam yemeği, belirli alanların ve koddaki diğer ilişki türlerinin araştırıp haritalarını da oluşturabilir. Bunları ilgilendiren alanları ve ilişkileri bulmak ve seçmek için Çözüm Gezgini kullanırlar.|
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme (sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Koddaki mevcut sınıflar|

 Örneğin, geliştirici bir kod haritası oluşturur. Yeni senaryodan etkilenecek alanlara odaklanmak için kapsamını ayarlar. Bu bölgeler seçili ve haritada vurgulandı:

 ![Ad alanı bağımlılık grafiği](../modeling/media/namespace_reviewsystem.png)

 **Ad alanı kod eşlemesi**

 Geliştirici, sınıflarını, yöntemlerini ve ilişkilerini görmek için seçili ad alanlarını genişletir:

 ![Genişletilmiş ad alanı bağımlılık grafiği](../modeling/media/dep_reviewsystem.png)

 **Görünür çapraz grup bağlantılarıyla genişletilmiş ad alanı kod Haritası**

 Geliştirici, etkilenen sınıfları ve yöntemleri bulmak için kodu inceler. Her bir değişikliğin yaptığınız etkileri görmek için her değişiklikten sonra kod haritalarını yeniden oluşturun. Bkz. [Kodu görselleştirme](../modeling/visualize-code.md).

 Bileşenler veya etkileşimler gibi, sistemin diğer bölümlerine yapılan değişiklikleri anlatmak için, takım bu öğeleri beyaz tahtalara çizebilir. Ayrıca ayrıntılar yakalanabilmesi, yönetilmesi ve her iki ekiple anlaşılabilmesi için Visual Studio 'da aşağıdaki diyagramları çizmiş olabilirler:

|**Diyagram**|**Anlatır**|
|-|-|
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme (sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Koddaki mevcut sınıflar.|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a> Kodu tasarımla tutarlı tutun
 Şimdi akşam yemeği, güncelleştirilmiş kodun tasarımla tutarlı kaldığından emin olmalıdır. Bunlar, sistemdeki işlevlerin katmanlarını tanımlayan bağımlılık diyagramları oluşturur, aralarında izin verilen bağımlılıkları belirtir ve çözüm yapıtları bu katmanlarla ilişkilendirin.

|**Diyagram**|**Anlatır**|
|-|-|
|*Bağımlılık diyagramı*<br /><br /> Bkz.<br /><br /> - [Kodunuzda bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|Kodun mantıksal mimarisi.<br /><br /> Bir bağımlılık diyagramı, Visual Studio çözümündeki yapıları düzenler ve *Katmanlar* adlı soyut gruplar halinde eşler. Bu katmanlar, Bu yapıtların sistemde gerçekleştirdiği rolleri, görevleri veya işlevleri belirler.<br /><br /> Bağımlılık diyagramları, sistemin amaçlanan tasarımını açıklamak ve bu tasarıma karşı gelişen kodu doğrulamak için kullanışlıdır.<br /><br /> Katmanlar oluşturmak için Çözüm Gezgini, kod haritaları, Sınıf Görünümü ve Nesne Tarayıcısı öğelerini sürükleyin. Yeni Katmanlar çizmek için araç kutusunu kullanın veya Diyagram yüzeyine sağ tıklayın.<br /><br /> Mevcut bağımlılıkları görüntülemek için bağımlılık diyagramı yüzeyine sağ tıklayın ve ardından **Bağımlılıklar Oluştur**' a tıklayın. Hedeflenen bağımlılıkları belirtmek için yeni bağımlılıklar çizin.|

Örneğin, aşağıdaki bağımlılık diyagramı katmanlar ve her katmanla ilişkili yapıt sayısı arasındaki bağımlılıkları açıklar:

![Tümleşik ödeme sisteminin bağımlılık diyagramı](../modeling/media/layer_integrated_dnlucerne.png)

 **Bağımlılık diyagramı**

Tasarım ile çakışmaların kod geliştirme sırasında gerçekleşmediğinden emin olmak için takımlar, Azure DevOps üzerinde çalıştırılan yapılarda bağımlılık doğrulaması kullanır. Ayrıca, iade etme işlemlerinde bağımlılık doğrulaması gerektiren özel bir MSBuild görevi oluşturur. Doğrulama hatalarını toplamak için yapı raporları kullanırlar.

Bkz.

- [Görsel tasarımcıyı kullanma](/azure/devops/pipelines/get-started-designer)

- [TFVC geçitli iade etme](/azure/devops/pipelines/build/triggers)

- [Derleme ve yayınlama görevleri](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>Model oluşturma ve kullanma hakkında genel Ipuçları

- Çoğu diyagram satırlara göre bağlanmış düğümlerden oluşur. Her diyagram türü için araç kutusu farklı türlerde düğüm ve satır sağlar.

   Araç kutusunu açmak için, **Görünüm** menüsünden, **araç kutusu**' na tıklayın.

- Bir düğüm oluşturmak için araç kutusundan diyagrama sürükleyin. Belirli düğüm türleri mevcut düğümlere sürüklenmesi gerekir. Örneğin, bir bileşen diyagramında, var olan bir bileşene yeni bir bağlantı noktası eklenmelidir.

- Bir hat veya bağlantı oluşturmak için, araç kutusunda ilgili araca tıklayın, kaynak düğümüne tıklayın ve ardından hedef düğüme tıklayın. Bazı satırlar yalnızca belirli düğüm türleri arasında oluşturulabilir. İşaretçiyi olası bir kaynağın veya hedefin üzerine getirdiğinizde, işaretçi bir bağlantı oluşturup oluşturamayacağını gösterir.

### <a name="plan-and-track-work"></a>İşi planlayın ve izleyin

Visual Studio modelleme diyagramları, daha kolay çalışmanızı planlamak, yönetmek ve izlemek için Team Foundation Server ile tümleşiktir. Her iki ekip, test çalışmalarını ve geliştirme görevlerini tanımlamak ve bunların çalışmalarını tahmin etmek için modeller kullanır. Lucerne, kullanım durumları veya bileşenleri gibi model öğelerine Team Foundation Server iş öğeleri oluşturur ve bağlar. Bu, bunların ilerlemesini izlemelerine ve çalışmalarını kullanıcıların gereksinimlerine geri izlemesine yardımcı olur. Bu, onların değişikliklerinin bu gereksinimleri karşılamak için devam etmesini sağlamaya yardımcı olur.

Çalışmaları ilerledikçe takımlar, iş öğelerini görevlerinde harcadıkları süreyi yansıtacak şekilde güncelleştirir. Ayrıca, aşağıdaki Team Foundation Server özelliklerini kullanarak çalışmalarını izler ve bunlarla ilgili durumu raporlar:

- Günlük olarak, planlanan çalışmanın beklenen sürede tamamlanıp tamamlanmayacağını gösteren *raporlar* . Bunlar, hataların ilerlemesini izlemek için Team Foundation Server başka benzer raporlar oluşturur.

- Ekibin üyeleri arasındaki iş yükünü izlemesine ve dengelemeye yardımcı olmak için Microsoft Excel kullanan bir *yineleme çalışma sayfası* . Bu çalışma sayfası Team Foundation Server bağlanır ve normal ilerleme toplantıları sırasında tartışmayı odaklamayı sağlar.

- Ekibin önemli proje bilgileri hakkında bilgi sahibi olmasını sağlamak için Office Project kullanan bir *geliştirme panosu* .

Bkz.

- [Çevik Araçlar ve çevik proje yönetimi hakkında](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)

- [Grafikler, panolar ve pencere öğeleri (Azure DevOps Services)](/azure/devops/report/dashboards/overview?view=vsts&preserve-view=true)

- [Projeyi kullanarak kapsamınızı ve görevlerinizi oluşturma](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a> Kodu test edin, doğrulayın ve Iade edin

Takımlar her görevi tamamlarsa, bunların kodlarını kaynak denetimine denetler ve Team Foundation Server, unutduklarında anımsatıcıları alırlar. Team Foundation Server, iadelerini kabul etmeden önce, ekip, kodu test çalışmalarına ve tasarıma karşı doğrulamak için birim testleri ve bağımlılık doğrulaması çalıştırır. Derlemeler, otomatik birim testleri ve bağımlılık doğrulamasını düzenli olarak çalıştırmak için Team Foundation Server kullanırlar. Bu, kodun aşağıdaki ölçütlere uyduğundan emin olmanıza yardımcı olur:

- İşe yarar.

- Daha önce çalışan kodu bozmaz.

- Tasarım ile çakışmaz.

Şimdi akşam yemeği, neredeyse hepsi hala uygulandığı için Lucerne 'ın yeniden kullanılabilir olduğu büyük bir otomatik test koleksiyonuna sahiptir. Lucerne ayrıca bu testleri oluşturabilir ve yeni işlevleri kapsayacak yeni işlevler ekleyebilir. Ayrıca, el ile testleri çalıştırmak için Visual Studio 'Yu da kullanabilirsiniz.

Kodun tasarıma uyduğundan emin olmak için takımlar Azure DevOps 'daki derlemeleri bağımlılık doğrulaması içerecek şekilde yapılandırır. Herhangi bir çakışma oluşursa, ayrıntılarla birlikte bir rapor oluşturulur.

Bkz.

- [Uygulamayı test etme](/azure/devops/test/overview?view=vsts&preserve-view=true)

- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)

- [Sürüm denetimini kullanma](/azure/devops/repos/tfvc/overview?view=azure-devops&preserve-view=true)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)

## <a name="update-the-system-using-visualization-and-modeling"></a>Görselleştirme ve modelleme kullanarak sistemi güncelleştirme

Lucerne ve Dinner Now ödeme sistemlerini tümleştirmelidir. Aşağıdaki bölümlerde, Visual Studio 'daki modelleme diyagramları bu görevi gerçekleştirmelerine yardımcı olur:

- [Mevcut kodu görselleştirin: kod haritaları](#VisualizeCode)

- [Türler sözlüğü tanımlayın: sınıf diyagramları](#DefineClasses)

- [Mantıksal mimariyi açıkla: bağımlılık diyagramları](#DescribeLayers)

Bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)

- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a> Mevcut kodu görselleştirin: kod haritaları

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

#### <a name="summary-strengths-of-code-maps"></a>Özet: kod eşlemelerinin güçleri
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
 Bağımlılık diyagramları, çözümünüzdeki yapıtları soyut gruplar veya *Katmanlar* halinde düzenleyerek sistemin mantıksal mimarisini anlatmaktadır. Yapıtlar, ad alanları, projeler, sınıflar, yöntemler vb. gibi birçok şey olabilir. Katmanlar, yapıların sistemde gerçekleştirdiği rolleri veya görevleri temsil eder ve tanımlarlar. Ayrıca, kodun tasarımıyla tutarlı kalmasını sağlamak için yapı ve iade işlemlerinizin katman doğrulamasını da dahil edebilirsiniz.

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
|**Forumlar**|- [Visual Studio görselleştirme & modelleme araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio görselleştirme & modelleme SDK (DSL araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Ayrıca bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
- [Çevik geliştirmede modelleri kullanma](/previous-versions/ff398061(v=vs.140))
- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)