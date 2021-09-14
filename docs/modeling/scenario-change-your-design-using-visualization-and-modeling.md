---
title: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme
description: Visual Studio içindeki görselleştirme ve modelleme araçları hakkında bilgi edinin ve tasarımınızı değiştirmek için bu araçları nasıl kullanacağınızı öğrenin.
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
ms.openlocfilehash: ce1a760bd51a9d3476354cdd63fdcebcad311552
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637473"
---
# <a name="scenario-change-your-design-using-visualization-and-modeling"></a>Senaryo: Görselleştirme ve modelleme kullanarak tasarımınızı değiştirme

Yazılım sisteminizin, Visual Studio ' de görselleştirme ve modelleme araçlarını kullanarak kullanıcıların ihtiyaçlarını karşıladığından emin olun.
Kod haritaları, bağımlılık diyagramları ve sınıf diyagramları gibi araçları kullanarak şunları yapın:

hangi Visual Studio sürümlerinin her bir aracı desteklediğini görmek için bkz. [mimari ve modelleme araçları için sürüm desteği](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

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

her iki ekip, kullanıcıların ihtiyaçlarını karşılayan sistemler geliştirmeye yardımcı olmak için Visual Studio 'de modelleme diyagramları kullanır. bunlar, işlerini planlamaya, düzenlemenize ve yönetmesine yardımcı olması için diğer araçlarla birlikte Team Foundation Server kullanırlar.

Team Foundation Server hakkında daha fazla bilgi için bkz.:

- [İşi planlayın ve izleyin](#plan-and-track-work)

- [Test, doğrulama ve güncelleştirilmiş kodu iade etme](#TestValidateCheckInCode)

## <a name="roles-of-architecture-and-modeling-diagrams-in-software-development"></a><a name="ModelingDiagramsTools"></a> Yazılım geliştirmede mimari ve modelleme diyagramları rolleri

Aşağıdaki tabloda, bu araçların yazılım geliştirme yaşam döngüsünün birden çok ve çeşitli aşamaları sırasında oynayabileceği roller açıklanmaktadır:

|Araç/rol|Kullanıcı gereksinimleri Modelleme|İş süreci modelleme|Sistem mimarisi & tasarımı|Kod görselleştirme & araştırması|Doğrulama|
|------|-|-|-|-|-|
|Domain-Specific Language (DSL) diyagramı|Yes|Yes|Yes|||
|Bağımlılık diyagramı, katman doğrulama|||Yes|Yes|Yes|
|Kod eşlemesi|||Yes|Yes|Yes|
|Sınıf Tasarımcısı (kod tabanlı)||||Yes||

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
> Visual Studio bazı sürümleri, bağımlılık doğrulamasını ve görselleştirme ve modelleme için kod eşlemelerinin salt okunurdur sürümlerini destekler. hangi Visual Studio sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları için sürüm desteği](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

## <a name="understand-and-communicate-information-about-the-system"></a>Sistemle ilgili bilgileri anlayın ve iletişim kurun

Visual Studio modelleme diyagramlarının kullanılması için önceden tanımlanmış bir sıra yoktur, bu nedenle bunları gereksinimlerinize veya yaklaşımlarınıza uygun şekilde kullanabilirsiniz. Genellikle takımlar modellerini bir proje boyunca tekrarlayarak ve sık sık yeniden ziyaret edin. Her diyagram, geliştirme aşamasındaki sistemin farklı yönlerini anlamanıza, açıklamanıza ve iletmede size yardımcı olmak için belirli güçler sunar.

Şimdi akşam yemeği ve Lucerne, ortak dil olarak diyagramlar kullanarak birbirleriyle ve proje hissedarlarıyla iletişim kurar. Örneğin, şimdi akşam yemeği bu görevleri gerçekleştirmek için diyagramlar kullanmaktadır:

- Mevcut kodu görselleştirin.

- Yeni veya güncelleştirilmiş Kullanıcı hikayeleri hakkında Lucerne ile iletişim kurun.

- Yeni veya güncelleştirilmiş kullanıcı hikayelerini desteklemek için gereken değişiklikleri belirler.

Lucerne bu görevleri gerçekleştirmek için diyagramlar kullanır:

- Şimdi akşam yemeği iş süreci hakkında bilgi edinin.

- Sistemin tasarımını anlayın.

- Yeni veya güncelleştirilmiş kullanıcı gereksinimleri hakkında şimdi akşam yemeği ile iletişim kurun.

- Sisteme belge güncelleştirmeleri.

diyagramlar Team Foundation Server ile tümleşiktir, böylece takımlar işlerini daha kolay bir şekilde planlayabilir, yönetebilir ve izleyebilir. Örneğin, test çalışmalarını ve geliştirme görevlerini tanımlamak ve bunların çalışmalarını tahmin etmek için modeller kullanırlar. Lucerne bağlantıları, ilerlemeyi izleyebilmek ve sistemin kullanıcı gereksinimlerini karşıladığından emin olmak için iş öğelerini model öğelerine Team Foundation Server. Örneğin, tüm testler başarılı olduğunda kullanım örneklerinin yerine getirildiğini görebilmesi için kullanım örneklerini test çalışması iş öğelerine bağlar.

Ekipler değişikliklerini iade etmeden önce, bağımlılık doğrulama ve otomatikleştirilmiş testler içeren derlemeler çalıştırarak test ve tasarıma karşı kodu doğrular. Bu, güncelleştirilmiş kodun tasarım ve daha önce çalışan işlevlerle çakışmadığından emin olmanıza yardımcı olur.

### <a name="identify-changes-to-the-existing-system"></a>Mevcut sistemdeki değişiklikleri tanımla

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

Şimdi Akşam Yemeği'nin neredeyse hepsi geçerli olduğu için Lucerne'ın yeniden kullanacı olan çok sayıda otomatikleştirilmiş test koleksiyonu vardır. Lucerne ayrıca bu testler üzerinde derlemeler ve yeni işlevleri kapsayacak yeni testler ekleyebilir. Her ikisi de el Visual Studio testleri çalıştırmak için de Visual Studio kullanır.

Kodun tasarıma uygun olduğundan emin olmak için ekipler derlemelerini Azure DevOps doğrulamayı içerecek şekilde yapılandırabilir. Herhangi bir çakışma oluşursa, ayrıntılarla birlikte bir rapor oluşturulur.

Bkz.

- [Uygulamayı test etme](/azure/devops/test/overview?view=vsts&preserve-view=true)

- [Geliştirme sırasında sisteminizi doğrulama](../modeling/validate-your-system-during-development.md)

- [Sürüm denetimi kullanma](/azure/devops/repos/tfvc/overview?view=azure-devops&preserve-view=true)

- [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true)

## <a name="update-the-system-using-visualization-and-modeling"></a>Görselleştirme ve Modelleme Kullanarak Sistemi Güncelleştirme

Lucerne ve Dinner Now'ın ödeme sistemlerini tümleştir olması gerekir. Aşağıdaki bölümlerde, bu görevi gerçekleştirmelerine yardımcı olmak Visual Studio modelleme diyagramları yer almaktadır:

- [Mevcut Kodu Görselleştirme: Kod Haritalar](#VisualizeCode)

- [Türler Sözlüğü Tanımlama: Sınıf Diyagramları](#DefineClasses)

- [Mantıksal Mimariyi Açıklama: Bağımlılık Diyagramları](#DescribeLayers)

Bkz.

- [Kodu görselleştirme](../modeling/visualize-code.md)

- [Geliştirme sürecinizde modelleri kullanma](../modeling/use-models-in-your-development-process.md)

- [Uygulama mimarinizi modelleme](../modeling/model-your-app-s-architecture.md)

### <a name="visualize-existing-code-code-maps"></a><a name="VisualizeCode"></a>Mevcut Kodu Görselleştirme: Kod Haritalar

Kod eşlemeleri, kodda geçerli kuruluşu ve ilişkileri gösterir. Öğeler, *eşlemedeki düğümler* ve ilişkiler bağlantılarıyla temsil *edildi.* Kod eşlemeleri aşağıdaki tür görevleri gerçekleştirmeye yardımcı olabilir:

- Yabancı kodu keşfedin.

- Önerilen bir değişikliğin mevcut kodu nerede ve nasıl etkileyeceğini anlama.

- Karmaşıklık alanlarını, doğal bağımlılıkları veya desenleri ya da geliştirmeden yararlanabilecek diğer alanları bulun.

Örneğin, Şimdi Akşam Yemeği'nin PaymentProcessing bileşenini güncelleştirme maliyetini tahmin etmek gerekir. Bu, kısmen bu değişikliğin sistemin diğer bölümlerini ne kadar etkileyeceğini etkiler. Bunu anlamalarına yardımcı olmak için Şimdi Akşam Yemeği geliştiricilerinden biri koddan kod haritaları üretir ve kapsam odağını değişiklikten etkilenecek alanlara ayarlar.

Aşağıdaki harita PaymentProcessing sınıfı ile Şimdi Akşam Yemeği sisteminin seçili görünen diğer bölümleri arasındaki bağımlılıkları gösterir:

![Şimdi Akşam Yemeği ödeme sistemi için bağımlılık grafiği](../modeling/media/dep_dnpayment.png)

**Şimdi Akşam Yemeği ödeme sistemi için kod haritası**

Geliştirici, PaymentProcessing sınıfını genişleterek ve üyelerini seçerek etkilenen alanları görerek haritayı keşfeder:

![PaymentProcessing içindeki yöntemler ve bağımlılıklar](../modeling/media/depgraph_expandeddn.png)

**PaymentProcessing sınıfının içindeki yöntemler ve bağımlılıkları**

Sınıflarını, yöntemlerini ve bağımlılıklarını incelemek için Lucerne Ödeme Sistemi için aşağıdaki haritayı üretir. Takım, Lucerne sisteminin Şimdi Akşam Yemeği'nin diğer bölümleriyle etkileşim kurmak için de çalışma gerektir olabileceğini görüyor:

![Lucerne ödeme sistemi için bağımlılık grafiği](../modeling/media/depgraph_lucernepay.png)

**Lucerne Ödeme Sistemi için kod haritası**

İki ekip de birlikte çalışarak iki sistemi tümleştirecek değişiklikleri belirler. Güncelleştirmenin daha kolay olması için bazı kodu yeniden düzenlemeye karar veriyor. PaymentApprover sınıfı DinnerNow.Business ad alanına taşınacak ve bazı yeni yöntemler gerektirecektir. İşlemleri işlemek için Şimdi Akşam Yemeği sınıfları kendi ad alanına sahip olacaktır. Ekipler, çalışmalarını planlamak, düzenlemek ve izlemek için iş öğeleri oluşturabilir ve kullanabilir. İş öğelerini yararlı olduğu model öğelerine bağlar.

Kod yeniden düzenlendikten sonra ekipler güncelleştirilmiş yapıyı ve ilişkileri görmek için yeni bir kod haritası üretir:

![Yeniden düzenlenmiş kodla bağımlılık grafiği](../modeling/media/depgraph_integrated.png)

**Yeniden düzenlenmiş kodla kod haritası**

Bu harita PaymentApprover sınıfının artık DinnerNow.Business ad alanı içinde olduğunu ve bazı yeni yöntemlere sahip olduğunu gösterir. Şimdi Akşam Yemeği işlem sınıflarının kendi PaymentSystem ad alanı vardır ve bu da bu kodla daha sonra ilgilenebilirsiniz.

#### <a name="creating-a-code-map"></a>Kod Eşlemesi Oluşturma

- Kaynak koduna hızlı bir genel bakış için kod eşlemesi oluşturmak için şu adımları izleyin:

     Mimari menüsünde **Çözüm** için Kod **Eşlemesi Oluştur'a tıklayın.**

     Derlenmiş koda hızlı bir genel bakış için boş bir kod eşlemesi oluşturun ve ardından derleme dosyalarını veya ikili dosyaları harita yüzeyine sürükleyin.

- Belirli kod veya çözüm öğelerini keşfetmek için Çözüm Gezgini kullanarak görselleştirmek istediğiniz öğeleri ve ilişkileri seçin. Daha sonra yeni bir harita oluşturabilir veya seçili öğeleri mevcut bir haritaya eklemek için kullanabilirsiniz. Bkz. [Çözümleriniz genelinde bağımlılıkları eşleme.](../modeling/map-dependencies-across-your-solutions.md)

- Haritayı keşfetmeye yardımcı olmak için düzeni, gerçekleştirmek istediğiniz görev türlerine uygun şekilde yeniden düzenleyebilirsiniz.

     Örneğin, kodda katmanlama görselleştirmek için bir ağaç düzeni seçin. Bkz. [Kod eşlemelerini göz atma ve yeniden düzenleme.](../modeling/browse-and-rearrange-code-maps.md)

#### <a name="summary-strengths-of-code-maps"></a>Özet: Kod Kodunun Haritalar
 Kod haritaları size yardımcı olur:

- Mevcut kodda kuruluş ve ilişkiler hakkında bilgi alın.

- Önerilen bir değişiklikten etkilenecek alanları belirleme.

- Kodun bakımını, değiştirmesini ve yeniden kullanımı kolaylaştırmak için geliştirebilirsiniz karmaşıklık alanlarını, desenleri, katmanları veya diğer alanları bulun.

#### <a name="relationship-to-other-diagrams"></a>Diğer Diyagramlarla İlişki

|**Diyagram**|**Açıklanır**|
|-|-|
|Bağımlılık diyagramı|Sistemin mantıksal mimarisi. Kodun tasarımla tutarlı kalmasını sağlamak için bağımlılık doğrulamasını kullanın.<br /><br /> Mevcut bağımlılıkları veya hedeflenen bağımlılıkları tanımlamanıza yardımcı olmak için bir kod eşlemesi oluşturun ve ilgili öğeleri gruplayın. Bağımlılık diyagramı oluşturmak için bkz:<br /><br /> - [Kodunuzdan bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)|
|Sınıf diyagramı (kod tabanlı)|Belirli bir proje için kodda mevcut sınıflar.<br /><br /> Kodda var olan bir sınıfı görselleştirmek ve değiştirmek için Sınıf Tasarımcısı.<br /><br /> Bkz. [Nasıl: Projelere Sınıf Diyagramları Ekleme (Sınıf Tasarımcısı)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md).|

### <a name="define-a-glossary-of-types-class-diagrams"></a><a name="DefineClasses"></a> Türler Sözlüğü Tanımlama: Sınıf Diyagramları
 Sınıf diyagramları sisteme katılan varlıkları, terimleri veya kavramları ve bunların bir diğerleriyle ilişkilerini tanımlar. Örneğin, uygulama dili veya stiline bakılmaksızın her sınıfın özniteliklerini ve işlemlerini açıklamak için geliştirme sırasında bu diyagramları kullanabilirsiniz.

 Lucerne'ın İşlem Ödemesi kullanım durumuna katılan varlıkları açıklamasına ve tartışmalarına yardımcı olmak için aşağıdaki sınıf diyagramını çizmektedir:

 ![Sınıf diyagramında Ödeme varlıklarını işleme](../modeling/media/uml_payentities.png)

 **Sınıf diyagramında Ödeme varlıklarını işleme**

 Bu diyagramda bir Müşterinin çok sayıda siparişi ve siparişler için ödeme yapmak için farklı yolları olabilir. BankAccount ve CreditCard ödemeden devralınabilir.

 Geliştirme sırasında Lucerne, her sınıfın ayrıntılarını açıklamak ve tartışmak için aşağıdaki sınıf diyagramını kullanır:

 ![Sınıf diyagramında Ödeme varlığı ayrıntılarını işleme](../modeling/media/uml_payment.png)

 **Sınıf diyagramında Ödeme ayrıntılarını işleme**

#### <a name="drawing-a-class-diagram"></a>Sınıf Diyagramı Çizme

Sınıf diyagramı aşağıdaki önemli özelliklere sahiptir:

- Sınıflar, arabirimler ve numaralar gibi türler:

  - *Sınıf,* belirli yapısal veya davranışsal özelliklerine sahip nesnelerin tanımıdır.

  - *Arabirim,* bir nesnenin dışarıdan görünen davranışının bir bölümünü tanımlar.

  - Sabit *listesi, değişmez* değer listesini içeren bir sınıflandırıcıdır.

- *Öznitelikler,* bir sınıflandırıcının her örneğini açıklayan belirli bir *türe sahip değerlerdir.* Sınıflandırıcı türler, bileşenler, kullanım örnekleri ve hatta aktörler için genel bir addır.

- *İşlemler,* bir sınıflandırıcının örneklerinin gerçekleştirebilirsiniz yöntemler veya işlevlerdir.

- *İlişki,* iki sınıflandırıcı arasında bir ilişki olduğunu gösterir.

  - Toplama, *sınıflandırıcılar* arasında paylaşılan sahipliği gösteren bir ilişkilendirmedir.

  - *Bileşim,* sınıflandırıcılar arasındaki tam parça ilişkisini gösteren bir ilişkilendirmedir.

    Toplamaları veya bileşimleri göstermek için bir **ilişkilendirmede** Toplama özelliğini ayarlayın. **Paylaşılan** toplamaları, Bileşik ise **bileşimleri** gösterir.

- *Bağımlılık,* bir sınıflandırıcının tanımının değiştirilmesinin başka bir sınıflandırıcının tanımını değiştire olabileceğini gösterir.

- *Genelleştirme,* belirli bir sınıflandırıcının tanımının bir kısmını genel sınıflandırıcıdan devralınan olduğunu gösterir. Bir *gerçekleştirme,* bir sınıfın bir arabirim tarafından sunulan işlemleri ve öznitelikleri uygulaydığını gösterir.

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
 Bağımlılık diyagramları, çözümünüzdeki yapıtları soyut gruplar veya katmanlar halinde düzenleyerek sistemin mantıksal mimarisini *açıklar.* Artifacts alanları, projeler, sınıflar, yöntemler gibi birçok şey olabilir. Katmanlar, yapıtların sistemde gerçekleştirecekleri rolleri veya görevleri temsil edebilir ve açıklar. Kodun tasarımıyla tutarlı kalmasını sağlamak için derlemenize ve iade işlemlerinize katman doğrulaması da dahildir.

 Kodu tasarımla tutarlı tutmak için Şimdi Akşam Yemeği ve Lucerne aşağıdaki bağımlılık diyagramını kullanarak kodu geliştikçe doğrular:

 ![Tümleşik ödeme sisteminin bağımlılık diyagramı](../modeling/media/layer_integrated_dnlucerne.png)

 **Şimdi Lucerne ile tümleştirilmiş Akşam Yemeği için bağımlılık diyagramı**

 Bu diyagramda yer alan katmanlar, karşılık gelen Şimdi Akşam Yemeği ve Lucerne çözüm yapıtlarına bağlantı sağlar. Örneğin, İş katmanı Artık PaymentApprover sınıfını içeren DinnerNow.Business ad alanına ve üyelerine bağlantı verir. Kaynak Erişimi katmanı, DinnerNow.Data ad alanına bağlantı verir. Oklar veya *bağımlılıklar,* Kaynak Erişimi katmanında işlevselliği yalnızca İş katmanının kullanabileceğini belirtir. Takımlar kodunu güncelleştirdiğinde, çakışmaları ortaya çıktıklarında yakalamak ve ekiplerin bunları hemen çözümlemelerine yardımcı olmak için düzenli olarak katman doğrulaması gerçekleştirilir.

 Ekipler, iki sistemi artımlı olarak tümleştirin ve test etmek için birlikte çalışır. Önce PaymentApprover ve Akşam Yemeği'nin geri kalanının PaymentProcessing'i işlemeden önce başarıyla birlikte çalışmasına yardımcı olur.

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

     Katmanda bulunan sayı, katmana bağlı yapıt sayısını gösterir. Bu yapıtlar ad alanları, projeler, sınıflar, yöntemler gibi olabilir. Bir katmanda yapıt sayısını yorumlarken şunları unutmayın:

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