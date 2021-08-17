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
ms.openlocfilehash: b6cf4b8c941168f396c8beb80be8d6f7b824dfbd6dc1b0ae77a0c08ca5607677
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370706"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme

Yazılım sisteminizin, Visual Studio'daki görselleştirme ve modelleme araçlarını kullanarak kullanıcıların ihtiyaçlarını karşı Visual Studio.
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

Bu senaryo, iki kurgusal şirketin yazılım geliştirme yaşam döngülerinden bölümleri açıklar: Şimdi Akşam Yemeği ve Lucerne Yayımlama. Akşam Yemeği Şimdi Seattle'da Web tabanlı bir yemek teslim hizmeti sağlar. Müşteriler şimdi Akşam Yemeği web sitesinde yemek siparişi ve ödemesi yapmaktadır. Siparişler daha sonra teslim için uygun yerel restorana gönderilir. New York'ta bir şirket olan Lucerne Publishing, hem kapalı hem de Web üzerinde birkaç işletme çalıştırıyor. Örneğin, müşterilerin restoran incelemeleri yayınlandıracakları bir web sitesi çalıştırmaktadır.

Lucerne kısa süre önce Şimdi Akşam Yemeği'ne katıldı ve aşağıdaki değişiklikleri yapmak istiyor:

- Şimdi Akşam Yemeği'ne restoran inceleme özellikleri ekleyerek web sitelerini tümleştirin.

- Şimdi Akşam Yemeği'nin ödeme sistemini Lucerne'ın sistemiyle değiştirin.

- Şimdi Akşam Yemeği hizmetini bölge genelinde genişletin.

Şimdi Akşam Yemeği SCRUM ve eXtreme Programlama kullanıyor. Çok yüksek test kapsamına ve çok az desteklenmeyen koda sahipler. Sistemin küçük ancak çalışan sürümlerini oluşturarak ve ardından artımlı işlevsellik ekleyerek riskleri en aza indirgerler. Kısa ve sık yinelemeler üzerinde kendi kodunu geliştirirler. Bu, değişikliği güvenle benimsemelerine, kodu sık sık yeniden düzenlemelerine ve "önden büyük tasarımdan" kaçınmalarına olanak sağlar.

Lucerne, bazıları 40'dan eski olan çok daha büyük ve karmaşık bir sistem koleksiyonuna sahiptir. Eski kodun karmaşıklığı ve kapsamı nedeniyle değişiklik yapma konusunda çok dikkatlidirler. Ayrıntılı çözümler tasarlamayı ve geliştirme sırasında oluşan tasarım ve değişiklikleri belgelemeyi tercih eden daha zorlu bir geliştirme sürecini takip eder.

Her iki ekip de Visual Studio ihtiyaçlarına uygun sistemler geliştirmelerine yardımcı olmak için Visual Studio modelleme diyagramlarını kullanır. Bu Team Foundation Server planlama, düzenleme ve yönetmelerine yardımcı olmak için diğer araçlarla birlikte kullanır.

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

Bağımlılık diyagramları çizmek için, mevcut bir çözümün veya yeni bir çözümün parçası olarak bir modelleme projesi oluşturmanız gerekir. Bu diyagramların modelleme projesinde oluşturulmuş olması gerekir.
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

Veri modelleme diyagramlarını kullanmak için Visual Studio düzen yoktur, bu nedenle bunları ihtiyaçlarınıza veya yaklaşımınıza uygun şekilde kullanabilirsiniz. Ekipler genellikle proje boyunca modellerini tekrar tekrar ziyaret ediyor. Her diyagram, geliştirme aşamasındaki sistemin farklı yönlerini anlamanıza, açıklamanıza ve iletişim kurmanıza yardımcı olmak için belirli güçler sunar.

Şimdi Akşam Yemeği ve Lucerne, ortak dil olarak diyagramları kullanarak birbirleriyle ve proje katılımcılarıyla iletişim kurar. Örneğin, Şimdi Akşam Yemeği şu görevleri gerçekleştirmek için diyagramları kullanır:

- Mevcut kodu görselleştirme.

- Lucerne ile yeni veya güncelleştirilmiş kullanıcı hikayeleri hakkında iletişim kurma.

- Yeni veya güncelleştirilmiş kullanıcı hikayelerini desteklemek için gereken değişiklikleri belirleme.

Lucerne şu görevleri gerçekleştirmek için diyagramları kullanır:

- Şimdi Akşam Yemeği iş süreci hakkında bilgi edinmek.

- Sistemin tasarımını anlama.

- Şimdi Akşam Yemeği ile yeni veya güncelleştirilmiş kullanıcı gereksinimleri hakkında iletişim kurma.

- Sistem güncelleştirmelerini belgele.

Diyagramlar, ekiplerin çalışmalarını Team Foundation Server kolay bir şekilde planlamak, yönetmek ve izlemek için diyagramlarla tümleştirilmiştir. Örneğin, test çalışmalarını ve geliştirme görevlerini tanımlamak ve çalışmalarını tahmin etmek için modelleri kullanır. Lucerne, Team Foundation Server izlemeleri ve sistemin kullanıcıların gereksinimlerini karşılaması için iş öğelerini modellemektedir. Örneğin, tüm testler başarılı olduğunda kullanım durumlarının yerine getirilmesini görmek için kullanım çalışmalarını test çalışması iş öğelerine bağlar.

Ekipler değişikliklerini denetlemeden önce bağımlılık doğrulama ve otomatikleştirilmiş testler içeren derlemeleri çalıştırarak kodu testlere ve tasarıma göre doğrular. Bu, güncelleştirilmiş kodun tasarımla çakışmamalarını ve daha önce çalışan işlevselliği bozmalarını sağlar.

### <a name="identify-changes-to-the-existing-system"></a>Mevcut Sistemde Yapılan Değişiklikleri Tanımlama

Şimdi akşam yemeği yeni gereksinimin toplantısının maliyetini tahmin etmelidir. Bu, kısmen bu değişikliğin sistemin diğer bölümlerini ne kadar etkileyeceğini gösterir. Bunu anlamalarına yardımcı olmak için Dinner Now geliştiricilerinden biri mevcut koddan bu haritaları ve diyagramları oluşturur:

|**Harita veya diyagram**|**Diziler**|
|-|-|
|*Kod eşlemesi*<br /><br /> Bkz.<br /><br /> - [Çözümleriniz genelinde bağımlılıkları eşleyin](../modeling/map-dependencies-across-your-solutions.md)<br />- [Kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md)<br />- [DGML dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|Koddaki bağımlılıklar ve diğer ilişkiler.<br /><br /> Örneğin, şimdi akşam yemeği derlemeler ve bağımlılıklarına genel bir bakış için derleme kodu eşlemelerini inceleyerek başlayabilir. Bu derlemelerdeki ad alanlarını ve sınıfları araştırmak için Eşlemlerde detaya gidebilirler.<br /><br /> Şimdi akşam yemeği, belirli alanların ve koddaki diğer ilişki türlerinin araştırıp haritalarını da oluşturabilir. Bunları ilgilendiren alanları ve ilişkileri bulmak ve seçmek için Çözüm Gezgini kullanırlar.|
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme (sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Koddaki mevcut sınıflar|

 Örneğin, geliştirici bir kod haritası oluşturur. Yeni senaryodan etkilenecek alanlara odaklanmak için kapsamını ayarlar. Bu bölgeler seçili ve haritada vurgulandı:

 ![Ad alanı bağımlılığı Graph](../modeling/media/namespace_reviewsystem.png)

 **Ad alanı kod eşlemesi**

 Geliştirici, sınıflarını, yöntemlerini ve ilişkilerini görmek için seçili ad alanlarını genişletir:

 ![Genişletilmiş ad alanı bağımlılık grafiği](../modeling/media/dep_reviewsystem.png)

 **Görünür çapraz grup bağlantılarıyla genişletilmiş ad alanı kod Haritası**

 Geliştirici, etkilenen sınıfları ve yöntemleri bulmak için kodu inceler. Her bir değişikliğin yaptığınız etkileri görmek için her değişiklikten sonra kod haritalarını yeniden oluşturun. Bkz. [Kodu görselleştirme](../modeling/visualize-code.md).

 Bileşenler veya etkileşimler gibi, sistemin diğer bölümlerine yapılan değişiklikleri anlatmak için, takım bu öğeleri beyaz tahtalara çizebilir. ayrıca, ayrıntılar yakalanabilmesi, yönetilmesi ve her iki ekip tarafından anlaşılabilmesi için Visual Studio aşağıdaki diyagramları da çizebilir:

|**Diyagram**|**Anlatır**|
|-|-|
|*Kod tabanlı sınıf diyagramı*<br /><br /> Bkz. [nasıl yapılır: projelere sınıf diyagramları ekleme (sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|Koddaki mevcut sınıflar.|

### <a name="keep-code-consistent-with-the-design"></a><a name="ValidatingCode"></a> Kodu tasarımla tutarlı tutun
 Şimdi akşam yemeği, güncelleştirilmiş kodun tasarımla tutarlı kaldığından emin olmalıdır. Bunlar, sistemdeki işlevlerin katmanlarını tanımlayan bağımlılık diyagramları oluşturur, aralarında izin verilen bağımlılıkları belirtir ve çözüm yapıtları bu katmanlarla ilişkilendirin.

|**Diyagram**|**Anlatır**|
|-|-|
|*Bağımlılık diyagramı*<br /><br /> Bkz.<br /><br /> - [Kodunuzda bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık diyagramları: başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|Kodun mantıksal mimarisi.<br /><br /> bir bağımlılık diyagramı, Visual Studio çözümündeki yapıtları, *katmanlar* adlı soyut gruplar halinde düzenler ve eşler. Bu katmanlar, Bu yapıtların sistemde gerçekleştirdiği rolleri, görevleri veya işlevleri belirler.<br /><br /> Bağımlılık diyagramları, sistemin amaçlanan tasarımını açıklamak ve bu tasarıma karşı gelişen kodu doğrulamak için kullanışlıdır.<br /><br /> Katmanlar oluşturmak için Çözüm Gezgini, kod haritaları, Sınıf Görünümü ve Nesne Tarayıcısı öğelerini sürükleyin. Yeni Katmanlar çizmek için araç kutusunu kullanın veya Diyagram yüzeyine sağ tıklayın.<br /><br /> Mevcut bağımlılıkları görüntülemek için bağımlılık diyagramı yüzeyine sağ tıklayın ve ardından **Bağımlılıklar Oluştur**' a tıklayın. Hedeflenen bağımlılıkları belirtmek için yeni bağımlılıklar çizin.|

Örneğin, aşağıdaki bağımlılık diyagramı katmanlar ve her katmanla ilişkili yapıt sayısı arasındaki bağımlılıkları açıklar:

![Tümleşik ödeme sisteminin bağımlılık diyagramı](../modeling/media/layer_integrated_dnlucerne.png)

 **Bağımlılık diyagramı**

Tasarım ile çakışmaların kod geliştirme sırasında gerçekleşmediğinden emin olmak için, takımlar Azure DevOps çalıştırılan yapılarda bağımlılık doğrulaması kullanır. ayrıca, iade etme işlemlerinde bağımlılık doğrulaması gerektirmek için özel bir MSBuild görevi oluşturur. Doğrulama hatalarını toplamak için yapı raporları kullanırlar.

Bkz.

- [Görsel tasarımcıyı kullanma](/azure/devops/pipelines/get-started-designer)

- [TFVC geçitli iade etme](/azure/devops/pipelines/build/triggers)

- [Derleme ve yayınlama görevleri](/azure/devops/pipelines/tasks/index)

### <a name="general-tips-for-creating-and-using-models"></a>modeller oluşturmak ve kullanmak için genel İpuçları

- Çoğu diyagram satırlara göre bağlanmış düğümlerden oluşur. Her diyagram türü için araç kutusu farklı türlerde düğüm ve satır sağlar.

   Araç kutusunu açmak için, **Görünüm** menüsünden, **araç kutusu**' na tıklayın.

- Bir düğüm oluşturmak için araç kutusundan diyagrama sürükleyin. Belirli düğüm türleri mevcut düğümlere sürüklenmesi gerekir. Örneğin, bir bileşen diyagramında, var olan bir bileşene yeni bir bağlantı noktası eklenmelidir.

- Bir hat veya bağlantı oluşturmak için, araç kutusunda ilgili araca tıklayın, kaynak düğümüne tıklayın ve ardından hedef düğüme tıklayın. Bazı satırlar yalnızca belirli düğüm türleri arasında oluşturulabilir. İşaretçiyi olası bir kaynağın veya hedefin üzerine getirdiğinizde, işaretçi bir bağlantı oluşturup oluşturamayacağını gösterir.

### <a name="plan-and-track-work"></a>İşi planlayın ve izleyin

Visual Studio modelleme diyagramları, daha kolay çalışmanızı planlamak, yönetmek ve izlemek için Team Foundation Server ile tümleşiktir. Her iki ekip, test çalışmalarını ve geliştirme görevlerini tanımlamak ve bunların çalışmalarını tahmin etmek için modeller kullanır. Lucerne, kullanım durumları veya bileşenleri gibi model öğelerine Team Foundation Server iş öğeleri oluşturur ve bağlar. Bu, bunların ilerlemesini izlemelerine ve çalışmalarını kullanıcıların gereksinimlerine geri izlemesine yardımcı olur. Bu, onların değişikliklerinin bu gereksinimleri karşılamak için devam etmesini sağlamaya yardımcı olur.

Çalışmaları ilerledikçe takımlar, iş öğelerini görevlerinde harcadıkları süreyi yansıtacak şekilde güncelleştirir. ayrıca, aşağıdaki Team Foundation Server özelliklerini kullanarak çalışmalarını izler ve bunlarla ilgili durumu raporlar:

- Günlük olarak, planlanan çalışmanın beklenen sürede tamamlanıp tamamlanmayacağını gösteren *raporlar* . bunlar, hataların ilerlemesini izlemek için Team Foundation Server başka benzer raporlar oluşturur.

- ekibin üyeleri arasındaki iş yükünü izlemesine ve dengelemeye yardımcı olmak için Microsoft Excel kullanan bir *yineleme çalışma sayfası* . bu çalışma sayfası Team Foundation Server bağlanır ve normal ilerleme toplantıları sırasında tartışmayı odaklamayı sağlar.

- Project Office kullanan bir *geliştirme panosu* , takımın önemli proje bilgileri hakkında bilgi sahibi olmasını sağlar.

Bkz.

- [Çevik Araçlar ve çevik proje yönetimi hakkında](/azure/devops/boards/backlogs/backlogs-overview?view=vsts&preserve-view=true)

- [Grafikler, panolar ve pencere öğeleri (Azure DevOps Services)](/azure/devops/report/dashboards/overview?view=vsts&preserve-view=true)

- [Project kullanarak kapsamınızı ve görevlerinizi oluşturun](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)

### <a name="test-validate-and-check-in-code"></a><a name="TestValidateCheckInCode"></a> Kodu test edin, doğrulayın ve Iade edin

takımlar her görevi tamamlarsa, bunların kodlarını kaynak denetimine denetler ve Team Foundation Server, unutduklarında anımsatıcıları alırlar. Team Foundation Server, iadelerini kabul etmeden önce, ekip, kodu test çalışmalarına ve tasarıma karşı doğrulamak için birim testleri ve bağımlılık doğrulaması çalıştırır. derlemeler, otomatik birim testleri ve bağımlılık doğrulamasını düzenli olarak çalıştırmak için Team Foundation Server kullanırlar. Bu, kodun aşağıdaki ölçütlere uyduğundan emin olmanıza yardımcı olur:

- İşe yarar.

- Daha önce çalışan kodu bozmaz.

- Tasarım ile çakışmaz.

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

- *İlişki,* iki sınıflandırıcı arasında bir ilişki olduğunu gösterir.

  - Toplama, *sınıflandırıcılar* arasında paylaşılan sahipliği gösteren bir ilişkilendirmedir.

  - *Bileşim,* sınıflandırıcılar arasındaki tam parça ilişkisini gösteren bir ilişkilendirmedir.

    Toplamaları veya bileşimleri göstermek için bir **ilişkilendirmede** Toplama özelliğini ayarlayın. **Paylaşılan** toplamaları, Bileşik ise **bileşimleri** gösterir.

- *Bağımlılık,* bir sınıflandırıcının tanımının değiştirilmesinin başka bir sınıflandırıcının tanımını değiştire olabileceğini gösterir.

- *Genelleştirme,* belirli bir sınıflandırıcının tanımının bir kısmını genel bir sınıflandırıcıdan devralınan olduğunu gösterir. Bir *gerçekleştirme,* bir sınıfın bir arabirim tarafından sunulan işlemleri ve öznitelikleri uygulaydığını gösterir.

     Bu ilişkileri oluşturmak için Devralma **aracını** kullanın. Alternatif olarak, bir gerçekleştirme bir *lollipop olarak temsil olabilir.*

- *Paketler* sınıflandırıcı grupları, ilişkilendirmeler, yaşam çizgileri, bileşenler ve diğer paketlerdir. *İçeri* aktarma ilişkileri, bir paketin başka bir paketin tüm tanımlarını içerir.

Mevcut sınıfları keşfetmek ve tartışmak için başlangıç noktası olarak, Sınıf Tasarımcısı kullanarak koddan sınıf diyagramları oluşturabilirsiniz.

- [Nasıl Yapılır: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)

#### <a name="summary-strengths-of-class-diagrams"></a>Özet: Sınıf Diyagramlarının Güçlü yönleri
 Sınıf diyagramları şunları tanımlamanıza yardımcı olur:

- Kullanıcıların ihtiyaçlarını ve sisteme katılan varlıkları tartışırken ortak bir terim sözlüğü. Bkz. [Model kullanıcı gereksinimleri.](../modeling/model-user-requirements.md)

- Uygulamalarından bağımsız olarak sistemin bileşenleri gibi bölümleri tarafından kullanılan türler. Bkz. [Uygulama mimarinizi modelleme.](../modeling/model-your-app-s-architecture.md)

- Bağımlılıklar gibi türler arasındaki ilişkiler. Örneğin, bir türün başka bir türün birden çok örneğiyle ilişkilendirilene kadar gösteresiniz.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklama**|
|-|-|
|Bağımlılık diyagramı|Sistemin mantıksal mimarisini sınıflara göre tanımlayın.<br /><br /> Kodun tasarımla tutarlı kalmasını sağlamak için bağımlılık doğrulamasını kullanın.<br /><br /> Bkz.<br /><br /> - [Kodunuzdan bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)<br />- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)<br />- [Bağımlılık diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md)|
|Kod haritası|Mevcut kodda kuruluşu ve ilişkileri görselleştirin.<br /><br /> Sınıfları, ilişkilerini ve yöntemlerini tanımlamak için bu öğeleri gösteren bir kod haritası oluşturun.<br /><br /> Bkz.<br /><br /> - [Çözümleriniz genelinde bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)|

### <a name="describe-the-logical-architecture-dependency-diagrams"></a><a name="DescribeLayers"></a> Mantıksal Mimariyi Açıklama: Bağımlılık Diyagramları
 Bağımlılık diyagramları, çözümünüzdeki yapıtları soyut gruplar veya katmanlar halinde düzenleyerek sistemin mantıksal mimarisini *açıklar.* Artifacts ad alanları, projeler, sınıflar, yöntemler gibi birçok şey olabilir. Katmanlar, yapıtların sistemde gerçekleştirecekleri rolleri veya görevleri temsil edebilir ve açıklar. Kodun tasarımıyla tutarlı kalmasını sağlamak için derlemenize ve iade işlemlerinize katman doğrulaması da dahildir.

 Kodu tasarımla tutarlı tutmak için Şimdi Akşam Yemeği ve Lucerne aşağıdaki bağımlılık diyagramını kullanarak kodu geliştikçe doğrular:

 ![Tümleşik ödeme sisteminin bağımlılık diyagramı](../modeling/media/layer_integrated_dnlucerne.png)

 **Şimdi Lucerne ile tümleştirilmiş Akşam Yemeği için bağımlılık diyagramı**

 Bu diyagramda yer alan katmanlar, karşılık gelen Şimdi Akşam Yemeği ve Lucerne çözüm yapıtlarına bağlantı sağlar. Örneğin, İş katmanı Artık PaymentApprover sınıfını içeren DinnerNow.Business ad alanına ve üyelerine bağlantı verir. Kaynak Erişimi katmanı, DinnerNow.Data ad alanına bağlantı verir. Oklar veya *bağımlılıklar,* Kaynak Erişimi katmanında işlevselliği yalnızca İş katmanının kullanabileceğini belirtir. Takımlar kodunu güncelleştirdiğinde, çakışmaları ortaya çıktıklarına göre yakalamak ve ekiplerin bunları hemen çözümlemelerine yardımcı olmak için düzenli olarak katman doğrulaması gerçekleştirilir.

 Ekipler, iki sistemi artımlı olarak tümleştirin ve test etmek için birlikte çalışır. Önce PaymentApprover ve Akşam Yemeği'nin geri kalanının PaymentProcessing'i işlemeden önce başarıyla birlikte çalışa çalışmalarından emin olur.

 Aşağıdaki kod haritası, Şimdi Akşam Yemeği ile PaymentApprover arasındaki yeni çağrıları gösterir:

 ![Tümleşik sistemle güncelleştirilmiş bağımlılık grafiği](../modeling/media/depgraph_intsystem.png)

 **Güncelleştirilmiş yöntem çağrılarını kullanarak kod eşlemesi**

 Sistemin beklendiği gibi çalıştığını onaylayan Akşam Yemeği Şimdi PaymentProcessing kodunu açıklama olarak yorumlar. Katman doğrulama raporları temizdir ve sonuçta elde edilen kod haritası artık PaymentProcessing bağımlılıkları olmadığını gösterir:

 ![PaymentProcessing olmadan bağımlılık grafiği](../modeling/media/depgraph_nomore.png)

 **PaymentProcessing olmadan kod haritası**

#### <a name="drawing-a-dependency-diagram"></a>Bağımlılık Diyagramı Çizme

Bağımlılık diyagramı aşağıdaki önemli özelliklere sahiptir:

- *Katmanlar,* mantıksal yapıt gruplarını açıklar.

- *Bağlantı,* bir katman ile yapıt arasındaki ilişkidir.

     Yapıtlardan katmanlar oluşturmak için öğeleri Çözüm Gezgini, kod eşlemeleri, Sınıf Görünümü veya Object Browser'dan sürükleyin. Yeni katmanlar çizip bunları yapıtlara bağlamak için araç kutusunu kullanın veya diyagram yüzeyine sağ tıklayarak katmanları oluşturun ve öğeleri bu katmanlara sürükleyin.

     Katmanda yer alan sayı, katmana bağlı yapıt sayısını gösterir. Bu yapıtlar ad alanları, projeler, sınıflar, yöntemler gibi olabilir. Bir katmanda yapıt sayısını yorumlarken şunları unutmayın:

  - Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.

       Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.

  - Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.

    Bir katmana bağlı yapıtları görmek için, bağımlılığına sağ  tıklayın ve ardından Katman Gezgini'ni açmak için Bağlantıları **Görüntüle'ye tıklayın.**

- Bağımlılık, *bir* katmanın işlevselliği başka bir katmanda kullanabileceğini ancak tam tersinin olmadığını gösterir. Çift *yönlü bağımlılık, bir* katmanın işlevi başka bir katmanda kullanabileceğini gösterir ve tam tersi de geçerlidir.

     Bağımlılık diyagramında mevcut bağımlılıkları görüntülemek için diyagram yüzeyine sağ tıklayın ve ardından Bağımlılık **oluştur'a tıklayın.** Hedeflenen bağımlılıkları açıklamak için yenilerini çizin.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)

- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)

- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

#### <a name="summary-strengths-of-dependency-diagrams"></a>Özet: Bağımlılık Diyagramlarının Güçlü yönleri

Bağımlılık diyagramları size yardımcı olur:

- Yapıtlarının işlevselliğine göre bir sistemin mantıksal mimarisini açıklama.

- Geliştirme aşamasındaki kodun belirtilen tasarıma uygun olduğundan emin olun.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklama**|
|-|-|
|Kod haritası|Mevcut kodda kuruluşu ve ilişkileri görselleştirin.<br /><br /> Katman oluşturmak için bir kod haritası oluşturun ve ardından haritadaki öğeleri olası katmanlar olarak gruplayın. Grupları eşlemeden bağımlılık diyagramına sürükleyin.<br /><br /> Bkz.<br /><br /> - [Çözümleriniz genelinde bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)<br />- [Kod haritalarına göz atma ve yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)|

## <a name="external-resources"></a>Dış Kaynaklar

|**Kategori**|**Bağlantılar**|
|-|-|
|**Forumlar**|- [Visual Studio Görselleştirme & modelleme araçları](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />- [Visual Studio Görselleştirme & modelleme SDK 'Sı (DSL araçları)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Ayrıca bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)
- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)
- [Çevik geliştirmede modelleri kullanma](/previous-versions/ff398061(v=vs.140))
- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)