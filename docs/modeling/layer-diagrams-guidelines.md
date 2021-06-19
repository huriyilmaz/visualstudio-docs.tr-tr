---
title: 'Bağımlılık Diyagramları: Yönergeler'
description: Visual Studio'da bağımlılık diyagramları oluşturarak, uygulama mimarinizi yüksek düzeyde Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f46e2b774cd4da2ef9cdb9ddef7efd19f731ade7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391029"
---
# <a name="dependency-diagrams-guidelines"></a>Bağımlılık diyagramları: yönergeler

Uygulamanızda bağımlılık diyagramları oluşturarak yüksek *düzeyde uygulama mimarisini Visual Studio.* Kodunuzu bağımlılık diyagramıyla doğrularken kodunuzun bu tasarımla tutarlı olduğundan emin olun. Derleme işleminize katman doğrulaması da dahil edersiniz. Bkz. [Channel 9 Video: Bağımlılık diyagramlarını kullanarak mimarinizi tasarlama ve doğrulama.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)

Bu özelliği destekleyen Visual Studio için bkz. Mimari ve [modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

> [!NOTE]
> .NET Core projeleri için bağımlılık diyagramları, 2019 Visual Studio 16.2 sürümünden itibaren de destekleni.

## <a name="what-is-a-dependency-diagram"></a>Bağımlılık diyagramı nedir?

Geleneksel mimari diyagramı gibi bağımlılık diyagramı da tasarımın ana bileşenlerini veya işlevsel birimlerini ve bunların bağımlılıklarını tanımlar. Diyagramda katman adı verilen her *düğüm, ad* alanlarının, projelerin veya diğer yapıtların mantıksal bir grubunu temsil eder. Tasarımınız içinde mevcut olması gereken bağımlılıkları çizin. Geleneksel mimari diyagramından farklı olarak, kaynak kodda yer alan gerçek bağımlılıkların belirttiğiniz hedeflenen bağımlılıklara uygun olduğunu doğrularsiniz. üzerinde normal bir derlemenin doğrulama bölümünü yaparak, program kodunun gelecekteki değişikliklerle sistemin mimarisine bağlı [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] kalmaya devam eder. Bkz. [Bağımlılık Diyagramları: Başvuru.](../modeling/layer-diagrams-reference.md)

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Bağımlılık diyagramları ile uygulama tasarlama veya güncelleştirme

Aşağıdaki adımlar, geliştirme sürecinde bağımlılık diyagramlarının nasıl kullanımına genel bir bakış sağlar. Bu konudaki sonraki bölümlerde her adım hakkında daha fazla ayrıntı açıklanmaktadır. Yeni bir tasarım geliştiriyorsanız, mevcut koda başvuran adımları atlar.

> [!NOTE]
> Bu adımlar yaklaşık sırada görüntülenir. Büyük olasılıkla görevleri çakışmak, kendi durumunuzla aynı olacak şekilde yeniden sıralamak ve projenizin her yinelemesi başında bunları yeniden ziyaret etmek istemeniz gerekir.

1. [Uygulamanın tamamı veya](#Create) içindeki bir katman için bir bağımlılık diyagramı oluşturun.

2. [Birincil işlevsel alanları veya uygulama bileşenlerinizi temsil edecek](#CreateLayers) katmanları tanımlayın. Bu katmanları işlevine (örneğin, "Sunum" veya "Hizmetler" gibi) göre adlar. Bir Visual Studio çözümünüz varsa, her katmanı projeler, ad alanları, dosyalar gibi bir yapıt koleksiyonuyla ilişkilendirilebilirsiniz.

3. [Katmanlar arasındaki mevcut bağımlılıkları](#Generate) keşfedin.

4. [Kodun yansıtması istediğiniz](#EditArchitecture) güncelleştirilmiş tasarımı göstermek için katmanları ve bağımlılıkları düzenleyin.

5. [Temel mimari blokları veya bileşenleri temsil](#NewAreas) eden katmanlar oluşturarak ve her katmanın diğerlerini nasıl kullandığını göstermek için bağımlılıkları tanımlayarak uygulamanıza yeni alanlar tasarlayarak.

6. [İş arkadaşlarınızla tartışmanıza yardımcı olmak](#EditLayout) için diyagramın düzenini ve görünümünü düzenleyin.

7. [Kodla gereken mimari arasındaki çakışmaları](#Validate) vurgulamak için kodu bağımlılık diyagramına göre doğrulayın.

8. [Kodu yeni mimarinize uygun olacak şekilde güncelleştirin.](#UpdateCode) Doğrulama hiçbir çakışmayı gösterene kadar kodu tekrarlı olarak geliştirin ve yeniden düzenleme.

9. [Kodun tasarımınıza bağlı kalmasını](#BuildValidation) sağlamak için derleme sürecine katman doğrulamayı dahil etmek.

## <a name="create-a-dependency-diagram"></a><a name="Create"></a> Bağımlılık diyagramı oluşturma

Bir modelleme projesinin içinde bağımlılık diyagramı oluşturulacak. Mevcut modelleme projesine yeni bir bağımlılık diyagramı ekleyebilir, bağımlılık diyagramı için yeni bir modelleme projesi oluşturabilir veya aynı modelleme projesi içindeki mevcut bağımlılık diyagramını kopyaabilirsiniz.

> [!IMPORTANT]
> Mevcut bağımlılık diyagramını bir modelleme projesinden başka bir modelleme projesine veya çözümde başka bir konuma ekleme, sürükleme veya kopyalamayın. Bu şekilde kopyalanan bağımlılık diyagramı, diyagramı değiştirse bile özgün diyagramla aynı başvurulara sahip olur. Bu, katman doğrulamasının doğru şekilde çalışmasını önler ve diyagramı açmaya çalışırken eksik öğeler veya diğer hatalar gibi başka sorunlara neden olabilir.

Bkz. [Kodunuzdan bağımlılık diyagramları oluşturma.](../modeling/create-layer-diagrams-from-your-code.md)

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> İşlevsel alanları veya bileşenleri temsil edecek katmanları tanımlama

Katmanlar, projeler, kod *dosyaları,* ad alanları, sınıflar ve yöntemler gibi mantıksal yapıt gruplarını temsil ediyor. Visual C# ve Visual Basic projelerinden yapıtlardan katmanlar oluşturabilir veya Word dosyaları veya PowerPoint sunumları gibi belgeleri bağarak belirtimleri veya planları katmana iliştirebilirsiniz. Her katman diyagramda dikdörtgen olarak görünür ve buna bağlı yapıt sayısını gösterir. Bir katman, daha belirli görevleri açıklayan iç içe katmanlar içerebilir.

Genel bir kılavuz olarak, ad katmanları işlevine göre (örneğin, "Sunum" veya "Hizmetler"). Yapıtlar birbirine yakınsa, bunları aynı katmana yer. Yapıtlar ayrı olarak güncelleştirilebilir veya ayrı uygulamalarda kullanılabilirse, bunları farklı katmanlara yer edin. Katmanlama desenleri hakkında bilgi edinmek için patterns & Practices sitesini ziyaret [http://go.microsoft.com/fwlink/?LinkId=145794](https://archive.codeplex.com/?p=apparch) edin.

> [!TIP]
> Katmanlara bağlabilirsiniz ancak bağımlılık diyagramına karşı doğrulamayı desteklemez bazı yapıt türleri vardır. Yapının doğrulamayı destekleyip destekleme olmadığını görmek için Katman **Gezgini'ni** açıp yapıt **bağlantısının Doğrulamayı** Destekler özelliğini inceleyin. Bkz. [Katmanlar arasındaki mevcut bağımlılıkları bulma.](#Generate)

Yabancı bir uygulamayı güncelleştiriyorken, kod eşlemeleri de oluşturabilirsiniz. Bu diyagramlar, siz kodu keşfedirken desenleri ve bağımlılıkları keşfetmeye yardımcı olabilir. Genellikle Çözüm Gezgini iyi karşılık gelen ad alanlarını ve sınıfları keşfetmek için Çözüm Gezgini'i kullanın. Bu kod yapıtlarını bağımlılık diyagramlarına sürükleyerek Çözüm Gezgini attayın. Daha sonra kodu güncelleştirmenize ve tasarımınıza uygun şekilde tutmanıza yardımcı olması için bağımlılık diyagramlarını kullanabilirsiniz.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Katmanlar arasındaki mevcut bağımlılıkları bulma

Bir bağımlılık, bir katman ile ilişkili yapının başka bir katman ile ilişkili bir yapıya başvurusu olduğu yerde var olur. Örneğin, bir katmandaki sınıf başka bir katmanda sınıfı olan değişkeni bildirir. Mevcut bağımlılıkları ters mühendislikle keşfedersiniz.

> [!NOTE]
> Bağımlılıklarda belirli türdeki yapılar için ters mühendislik uygulanamaz. Örneğin, hiçbir bağımlılıkta metin dosyasına bağlı katmandan veya katmana ters mühendislik uygulanmaz. Hangi yapıtların ters mühendislik için bağımlılıkları olduğunu görmek için, bir veya birden çok katmana sağ tıklayın ve ardından Bağlantıları **Görüntüle'ye tıklayın.** Katman **Gezgini'nde** Doğrulamayı **Destekler sütununu** inceleyin. Bağımlılıklar, bu sütunda False olarak gösteren yapıtlar için tersine mühendislik **sağlanmaz.**

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Katmanlar arasındaki mevcut bağımlılıklarda ters mühendislik yapmak için

Bir katman veya birden çok katman seçin, seçili bir katmana sağ tıklayın ve ardından Bağımlılık **oluştur'a tıklayın.**

Genellikle var olmaması gereken bazı bağımlılıklar göreceksiniz. Bu bağımlılıkları hedeflenen tasarım ile uyumlu hale getirmek için düzenleyebilirsiniz.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> Hedeflenen tasarımı göstermek için katmanları ve bağımlılıkları düzenleme

Sisteminize veya hedeflenen mimariye yapmayı plan yaptığınız değişiklikleri açıklamak için bağımlılık diyagramını düzenlemek için aşağıdaki adımları kullanın. Kodu genişletmeden önce kodun yapısını geliştirmek için bazı yeniden düzenleme değişiklikleri de yapabilirsiniz. Bkz. [Kodun yapısını geliştirme.](#Improving)

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Mevcut olmayan bir bağımlılığı silme|Bağımlılığına tıklayın ve DELETE tuşuna **basın.**|
|Bağımlılık yönünü değiştirme veya kısıtlama|**Direction** özelliğini ayarlayın.|
|Yeni bağımlılıklar oluşturma|Bağımlılık **ve Çift** **Yönlü Bağımlılık araçlarını** kullanın.<br /><br /> Çoklu bağımlılıklar çizmek için araca çift tıklayın. Bitirdikten sonra İşaretçi **aracına tıklayın** veya **ESC tuşuna** basın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtme|Katmanın Yasak Ad Alanı Bağımlılıkları **özelliğine ad alanlarını** yazın. Ad alanlarını ayırmak için **noktalı virgül**( ; ) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtme|Katmanın Yasak Ad Alanları özelliğine **ad alanlarını** yazın. Ad alanlarını ayırmak için **noktalı virgül**( ; ) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarından birine ait olması gerektiğini belirtme|Katmanın Gerekli Ad Alanları **özelliğine ad alanını** yazın. Ad alanlarını ayırmak için **noktalı virgül**( ; ) kullanın.|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> Kodun yapısını geliştirme

Değişiklikleri yeniden düzenleme, uygulamanın davranışını etkilemeden, kodun daha kolay değişmesini ve daha sonra genişletilene yardımcı olan geliştirmelerdir. İyi yapılandırılmış kod, bağımlılık diyagramına soyutlamanın kolay olduğu bir tasarıma sahiptir.

Örneğin, kodda her ad alanı için bir katman oluşturur ve ardından bağımlılıkların tersine mühendisliklerini oluşturursanız, katmanlar arasında en az tek yollu bağımlılıklar kümesi olması gerekir. Katmanlarınız olarak sınıfları veya yöntemleri kullanarak daha ayrıntılı bir diyagram oluşturmanız, sonucun da aynı özelliklere sahip olması gerekir.

Böyle bir durum yoksa, kodun ömrü boyunca değişmesi daha zor olur ve bağımlılık diyagramlarını kullanarak doğrulama için daha az uygun olur.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Uygulamanıza yeni alanlar tasarlama

Yeni bir proje veya yeni bir projede yeni bir alan geliştirmeye başlarız, kodu geliştirmeye başlamadan önce ana bileşenleri tanımlamaya yardımcı olmak için katmanlar ve bağımlılıklar çizebilirsiniz.

- **Mümkünse bağımlılık diyagramlarınızda** tanımlanabilir mimari desenleri gösterme. Örneğin, bir masaüstü uygulamasını açıklayan bağımlılık diyagramı Sunu, Etki Alanı Mantığı ve Veri Deposu gibi katmanları içerebilir. Uygulama içindeki tek bir özelliği kapsayan bağımlılık diyagramında Model, Görünüm ve Denetleyici gibi katmanlar olabilir. Bu tür desenler hakkında daha fazla bilgi için [bkz. & Uygulamaları: Uygulama Mimarisi.](https://archive.codeplex.com/?p=apparch)

- **Ad alanı, sınıf veya bileşen gibi** her katman için bir kod yapıt oluşturun. Bu, kodu takip etme ve kod yapıtlarını katmanlara bağlamayı kolaylaştırır. Her yapıyı oluşturur oluşturmaz uygun katmana bağlamanız gerekir.

- **Çoğu sınıfı ve diğer yapıtları** katmanlara bağlamanız gerek yok çünkü bunlar katmanlara zaten bağlı olan ad alanları gibi daha büyük yapıtların içinde yer almaktadır.

- **Yeni bir özellik için yeni bir diyagram oluşturun.** Genellikle, uygulamanın tamamını açıklayan bir veya daha fazla bağımlılık diyagramı olur. Uygulama içinde yeni bir özellik tasarıyorsanız mevcut diyagramlara ekleme veya mevcut diyagramları değiştirme. Bunun yerine, kodun yeni bölümlerini yansıtan kendi diyagramınızı oluşturun. Yeni diyagramda yer alan katmanlar, yeni özelliğin sunu, etki alanı mantığı ve veritabanı katmanlarını içerebilir.

     Uygulamayı derlemek için kodunuz hem genel diyagramda hem de daha ayrıntılı özellik diyagramınızda doğrulanır.

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> Sunu ve tartışma düzenini düzenleme

Katmanları ve bağımlılıkları tanımlamanıza veya bunları ekip üyeleriyle tartışmanıza yardımcı olmak için diyagramın görünümünü ve düzenini aşağıdaki yollarla düzenleyin:

- Katmanların boyutlarını, şekillerini ve konumlarını değiştirme.

- Katmanların ve bağımlılıkların renklerini değiştirme.

  - Bir veya daha fazla katman veya bağımlılık seçin, sağ tıklayın ve ardından Özellikler'e **tıklayın.** Özellikler **penceresinde** **Color** özelliğini düzenleyin.

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> Kodu diyagrama göre doğrulama

Diyagramı düzenleyebilirsiniz. Bunu koda göre istediğiniz zaman el ile veya her derlemede otomatik olarak doğrularsınız.

Bkz.

- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

- [Derleme İşleme Katman Doğrulama ekleme](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> Kodu yeni mimariye uygun olacak şekilde güncelleştirme

Genellikle, güncelleştirilmiş bağımlılık diyagramına karşı kodu ilk kez doğrulayan hatalar görüntülenir. Bu hataların çeşitli nedenleri olabilir:

- Yapı yanlış katmana atanmış. Bu durumda, yapıyı taşıyın.

- Sınıf gibi bir yapı, başka bir sınıfı mimarinizle çakışacak şekilde kullanıyor. Bu durumda, bağımlılığı kaldırmak için kodu yeniden düzenleyin.

Bu hataları çözmek için doğrulama sırasında daha fazla hata görünmeyene kadar kodu güncelleştirin. Bu genellikle bir iterative işlemdir. Bu hatalar hakkında daha fazla bilgi için [bkz. Bağımlılık diyagramları ile kodu doğrulama.](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Kodu geliştirirken veya yeniden düzenlemeye devam ettikçe, bağımlılık diyagramına bağlantı için yeni yapıtlar edinebilirsiniz. Ancak, mevcut ad alanlarını temsil eden katmanlarınız olduğunda ve yeni kod yalnızca bu ad alanlarına daha fazla malzeme eklerse, bu gerekli değildir.

Geliştirme işlemi sırasında, doğrulama esnasında bildirilen çakışmaların bazılarını gizlemek isteyebilirsiniz. Örneğin, zaten çözdüğünüz veya özel senaryonuzla ilgili olmayan hataları gizlemek isteyebilirsiniz. Bir hatayı bastırdıysanız, Team Foundation'da bir iş öğesini günlüğe kayıt etmek iyi bir uygulamadır. Bu görevi gerçekleştirmek için [bkz. Bağımlılık diyagramları ile kodu doğrulama.](../modeling/validate-code-with-layer-diagrams.md)

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Derleme sürecine katman doğrulaması ekleme

Kodda gelecekte yapılan değişikliklerin bağımlılık diyagramlarına uygun olduğundan emin olmak için çözüme standart derleme işlemi için katman doğrulamayı dahil etmek gerekir. Diğer ekip üyeleri çözümü her derlemesinde, kod ve bağımlılık diyagramındaki bağımlılıklar arasındaki farklar derleme hataları olarak rapor eder. Derleme sürecine katman doğrulaması ekleme hakkında daha fazla bilgi için [bkz. Bağımlılık diyagramları ile kodu doğrulama.](../modeling/validate-code-with-layer-diagrams.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)
