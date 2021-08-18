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
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 387f34b3ff9b81a81cd50c1528357d4216e6298a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040157"
---
# <a name="dependency-diagrams-guidelines"></a>Bağımlılık diyagramları: yönergeler

Uygulamanızda bağımlılık diyagramları oluşturarak yüksek düzeyde *uygulama mimarisini Visual Studio.* Kodunuzu bağımlılık diyagramıyla doğrularken kodunuzun bu tasarımla tutarlı olduğundan emin olun. Derleme işleminize katman doğrulaması da dahildir. Bkz. [Channel 9 Video: Bağımlılık diyagramlarını kullanarak mimarinizi tasarlama ve doğrulama.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)

Bu özelliği destekleyen Visual Studio için bkz. Mimari ve [modelleme araçları için sürüm desteği.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

> [!NOTE]
> .NET Core projeleri için bağımlılık diyagramları, Visual Studio 2019 sürüm 16.2'den başlayarak de destek almaktadır.

## <a name="what-is-a-dependency-diagram"></a>Bağımlılık diyagramı nedir?

Geleneksel mimari diyagramı gibi bağımlılık diyagramı da tasarımın ana bileşenlerini veya işlevsel birimlerini ve bunların bağımlılıklarını tanımlar. Diyagramda katman adı verilen her *düğüm, ad* alanlarının, projelerin veya diğer yapıtların mantıksal bir grubunu temsil eder. Tasarımınız içinde mevcut olması gereken bağımlılıkları çizin. Geleneksel mimari diyagramından farklı olarak, kaynak kodundaki gerçek bağımlılıkların belirttiğiniz hedeflenen bağımlılıklara uygun olduğunu doğrularsiniz. üzerinde normal bir derlemenin doğrulama bölümünü yaparak, program kodunun gelecekteki değişikliklerle sistemin mimarisine bağlı [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] kalmaya devam eder. Bkz. [Bağımlılık Diyagramları: Başvuru.](../modeling/layer-diagrams-reference.md)

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

Genel bir kılavuz olarak ad, işlevine göre katmanlarını (örneğin, "Sunum" veya "Hizmetler"). Yapıtlar birbirine yakınsa, bunları aynı katmana yer. Yapıtlar ayrı olarak güncelleştirilebilir veya ayrı uygulamalarda kullanılabilirse, bunları farklı katmanlara yer edin. Katmanlama desenleri hakkında bilgi edinmek için patterns & Practices sitesini ziyaret [http://go.microsoft.com/fwlink/?LinkId=145794](https://archive.codeplex.com/?p=apparch) edin.

> [!TIP]
> Katmanlara bağ yalnızca bağımlılık diyagramına karşı doğrulamayı desteklemeen belirli yapıt türleri vardır. Yapının doğrulamayı destekleyip destekleme olmadığını görmek için Katman **Gezgini'ni** açıp yapıt **bağlantısının Doğrulamayı** Destekler özelliğini inceleyin. Bkz. [Katmanlar arasındaki mevcut bağımlılıkları bulma.](#Generate)

Yabancı bir uygulamayı güncelleştiriyorken, kod eşlemeleri de oluşturabilirsiniz. Bu diyagramlar, siz kodu keşfedirken desenleri ve bağımlılıkları keşfetmeye yardımcı olabilir. Genellikle Çözüm Gezgini iyi karşılık gelen ad alanlarını ve sınıfları keşfetmek için Çözüm Gezgini'i kullanın. Bu kod yapıtlarını bağımlılık diyagramlarına sürükleyerek Çözüm Gezgini attayın. Daha sonra kodu güncelleştirmenize ve tasarımınıza uygun şekilde tutmanıza yardımcı olması için bağımlılık diyagramlarını kullanabilirsiniz.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Katmanlar arasındaki mevcut bağımlılıkları bulma

Bir bağımlılık, bir katman ile ilişkili yapının başka bir katman ile ilişkili bir yapıya başvurusu olduğu yerde var olur. Örneğin, bir katmandaki sınıf başka bir katmanda sınıfı olan değişkeni bildirir. Mevcut bağımlılıkları tersine mühendislik ile keşfedersiniz.

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

Değişiklikleri yeniden düzenleme, uygulamanın davranışını etkilemeden, kodun daha kolay değişmesini ve daha sonra genişletilene yardımcı olan geliştirmelerdir. İyi yapılandırılmış kod, bağımlılık diyagramına soyutlamak kolay bir tasarıma sahiptir.

Örneğin, koddaki her ad alanı için bir katman oluşturur ve ardından bağımlılıklara ters mühendislik yaparsanız katmanlar arasında tek yönlü bir bağımlılık kümesi olmalıdır. Katmanlarınız olarak sınıflar veya yöntemler kullanarak daha ayrıntılı bir diyagram oluşturursanız, sonuç aynı özelliklere de sahip olmalıdır.

Bu durum bu değilse, kodun ömrü boyunca değiştirilmesi daha zordur ve bağımlılık diyagramları kullanılarak doğrulama için daha az uygundur.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Uygulamanızın yeni bölgelerini tasarlama

Yeni bir proje veya yeni bir projedeki yeni bir alan geliştirmeyi başlattığınızda, kodu geliştirmeye başlamadan önce ana bileşenleri belirlemenize yardımcı olmak için Katmanlar ve bağımlılıklar çizebilirsiniz.

- Mümkünse, bağımlılık diyagramlarınızda **tanımlanabilir mimari desenleri gösterin** . Örneğin, bir masaüstü uygulamasını açıklayan bir bağımlılık diyagramı, sunum, etki alanı mantığı ve veri deposu gibi katmanları içerebilir. Bir uygulamadaki tek bir özelliği kaplayan bir bağımlılık diyagramı, model, görünüm ve denetleyici gibi katmanlara sahip olabilir. Bu tür desenler hakkında daha fazla bilgi için bkz. [desenler & uygulamalar: uygulama mimarisi](https://archive.codeplex.com/?p=apparch).

- Ad alanı, sınıf veya bileşen gibi **her katman için bir kod yapıtı oluşturun** . Bu, kodu izlemenizi ve kod yapıtlarını katmanlara bağlamayı kolaylaştırır. Her yapıyı oluşturur almaz, uygun katmana bağlayın.

- **Birçok sınıfı ve diğer yapıtları** katmanlara bağladığınız ad alanları gibi daha büyük yapıtlar içinde yer aldığı için katmanlara bağlamanız gerekmez.

- **Yeni bir özellik için yeni bir diyagram oluşturun**. Genellikle, uygulamanın tamamını açıklayan bir veya daha fazla bağımlılık diyagramı olacaktır. Uygulama içinde yeni bir özellik tasarlıyorsanız, mevcut diyagramları eklemeyin veya değiştirmeyin. Bunun yerine, kodun yeni parçalarını yansıtan kendi diyagramınızı oluşturun. Yeni diyagramdaki katmanlar, yeni özellik için sunum, etki alanı mantığı ve veritabanı katmanları içerebilir.

     Uygulamayı yapılandırdığınızda, kodunuz her ikisi de genel diyagramda ve daha ayrıntılı özellik diyagramınızla karşılaştırılarak onaylanır.

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> Sununun ve tartışmanın yerleşimini düzenleme

Katmanları ve bağımlılıkları belirlemenize veya bunları takım üyeleriyle tartışmanıza yardımcı olmak için, diyagramın görünüm ve yerleşimini aşağıdaki yollarla düzenleyin:

- Katmanların boyutlarını, şekillerini ve konumlarını değiştirin.

- Katmanların ve bağımlılıkların renklerini değiştirin.

  - Bir veya daha fazla katmanı veya bağımlılığı seçin, sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Özellikler** penceresinde, **Color** özelliğini düzenleyin.

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> Kodu diyagrama karşı doğrulama

Diyagramı düzenlediğinizde, bu kodu istediğiniz zaman el ile veya her derleme sırasında otomatik olarak doğrulayabilirsiniz.

Bkz.

- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

- [Yapı Işlemine katman doğrulamasını dahil et](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> Kodu yeni mimariye uyacak şekilde güncelleştirin

Genellikle, güncelleştirilmiş bir bağımlılık diyagramına göre kodu doğrulaışınızda hatalar ilk kez görünür. Bu hataların çeşitli nedenleri olabilir:

- Yapı yanlış katmana atanmış. Bu durumda, yapıyı taşıyın.

- Sınıf gibi bir yapı, başka bir sınıfı mimarinizle çakışacak şekilde kullanıyor. Bu durumda, bağımlılığı kaldırmak için kodu yeniden düzenleyin.

Bu hataları çözmek için doğrulama sırasında daha fazla hata görünmeyene kadar kodu güncelleştirin. Bu genellikle yinelemeli bir işlemdir. Bu hatalar hakkında daha fazla bilgi için bkz. [bağımlılık diyagramlarında kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Kodu geliştirirken veya yeniden düzenleme yaparken, bağımlılık diyagramına bağlanacak yeni yapıtlar olabilir. Ancak, bu gerekli olmayabilir, örneğin, varolan ad alanlarını temsil eden katmanlarınız varsa ve yeni kod yalnızca bu ad alanlarına daha fazla malzeme ekler.

Geliştirme işlemi sırasında, doğrulama esnasında bildirilen çakışmaların bazılarını gizlemek isteyebilirsiniz. Örneğin, zaten çözdüğünüz veya özel senaryonuzla ilgili olmayan hataları gizlemek isteyebilirsiniz. Bir hatayı bastırdığınızda, bir iş öğesini Team Foundation 'da günlüğe kaydetmek iyi bir uygulamadır. Bu görevi gerçekleştirmek için bkz. [bağımlılık diyagramlarında kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md).

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Yapı işlemine katman doğrulamasını dahil et

Koddaki gelecekteki değişikliklerin bağımlılık diyagramlarına uyduğundan emin olmak için, çözümünüzün standart yapı işlemine katman doğrulaması dahil edin. Diğer takım üyeleri çözümü oluştururken, koddaki bağımlılıklar ve bağımlılık diyagramı arasındaki herhangi bir farklılık derleme hatası olarak bildirilir. Yapı sürecinde katman doğrulaması ekleme hakkında daha fazla bilgi için bkz. [bağımlılık diyagramlarında kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)
