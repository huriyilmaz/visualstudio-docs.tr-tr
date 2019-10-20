---
title: 'Bağımlılık Diyagramları: Yönergeler'
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39da24dd0d8b7372c63609124ee0b9427fccb03d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661501"
---
# <a name="dependency-diagrams-guidelines"></a>Bağımlılık diyagramları: yönergeler

Visual Studio 'da *bağımlılık diyagramları* oluşturarak uygulamanızın mimarisini yüksek düzeyde tanıtın. Kodunuzu bir bağımlılık diyagramı ile doğrulayarak kodunuzun bu tasarımla tutarlı kalmasını sağlayın. Yapı sürecinizdeki katman doğrulamasını da dahil edebilirsiniz. Bkz. [Channel 9 videosu: bağımlılık diyagramlarını kullanarak mimarinizi tasarlama ve doğrulama](http://go.microsoft.com/fwlink/?LinkID=252073).

Hangi Visual Studio sürümlerini bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> .NET Core projeleri için bağımlılık diyagramları, Visual Studio 2019 sürüm 16,2 ' den itibaren desteklenmektedir.

## <a name="what-is-a-dependency-diagram"></a>Bağımlılık diyagramı nedir?

Geleneksel mimari diyagramı gibi bir bağımlılık diyagramı, tasarımın ana bileşenlerini veya işlevsel birimlerini ve bunların bağımlılıklarını tanımlar. Diyagramdaki *Katman*olarak adlandırılan her düğüm, bir dizi ad alanı, proje veya diğer yapıtları temsil eder. Tasarımınızda bulunması gereken bağımlılıkları çizebilirsiniz. Geleneksel mimari diyagramlarından farklı olarak, kaynak kodundaki gerçek bağımlılıkların belirttiğiniz hedeflenen bağımlılıklara uygun olduğunu doğrulayabilirsiniz. @No__t_0 düzenli bir yapılandırmanın doğrulama parçasını yaparak, program kodunun sonraki değişikliklerle sistem mimarisine uymaya devam ettiğinden emin olabilirsiniz. Bkz. [bağımlılık diyagramları: başvuru](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Uygulamanızı bağımlılık diyagramlarıyla tasarlama veya güncelleştirme

Aşağıdaki adımlarda, geliştirme sürecinde bağımlılık diyagramlarının nasıl kullanılacağına ilişkin bir genel bakış sağlanmaktadır. Bu konunun sonraki bölümlerinde, her adımla ilgili daha fazla ayrıntı açıklanmıştır. Yeni bir tasarım geliştiriyorsanız, varolan koda başvuran adımları atlayın.

> [!NOTE]
> Bu adımlar yaklaşık sırada görüntülenir. Büyük olasılıkla görevlerin çakışmasını, bunları kendi durumunuza uyacak şekilde yeniden sıralamak ve projenizdeki her yinelemenin başlangıcında tekrar ziyaret etmek isteyeceksiniz.

1. Tüm uygulama için veya içindeki bir katman için [bir bağımlılık diyagramı oluşturun](#Create) .

2. [Birincil işlevsel alanların veya uygulamanızın bileşenlerinin temsil edilebilmesi için katmanları tanımlayın](#CreateLayers) . Bu katmanları işlevine göre adlandırın, örneğin, "sunum" veya "Hizmetler". Visual Studio çözümünüz varsa, her katmanı projeler, ad alanları, dosyalar vb. gibi *yapıtlar*koleksiyonuyla ilişkilendirebilirsiniz.

3. Katmanlar arasında [var olan bağımlılıkları bulur](#Generate) .

4. Kod yansıtmasını istediğiniz güncelleştirilmiş tasarımı göstermek için [katmanları ve bağımlılıkları düzenleyin](#EditArchitecture) .

5. Asıl mimari blokları veya bileşenleri temsil eden Katmanlar oluşturarak ve her katmanın diğerlerini nasıl kullandığını göstermek için bağımlılıklar tanımlayarak [uygulamanızın yeni bölümlerini tasarlayın](#NewAreas) .

6. İş arkadaşlarınızla tartışmanıza yardımcı olması için [diyagramın yerleşimini ve görünümünü düzenleyin](#EditLayout) .

7. Kod ve ihtiyacınız olan mimari arasındaki çakışmaların vurgulanmasını sağlamak için [kodu bağımlılık diyagramına göre doğrulayın](#Validate) .

8. [Kodu Yeni mimarinize uyacak şekilde güncelleştirin](#UpdateCode). Doğrulama çakışma gösterene kadar kodu tekrarlayarak geliştirin ve yeniden düzenleyin.

9. Kodun tasarımınıza uygun olmaya devam ettiğinden emin olmak için [yapı işlemine katman doğrulamayı dahil edin](#BuildValidation) .

## <a name="Create"></a>Bağımlılık diyagramı oluşturma

Bir modelleme projesi içinde bir bağımlılık diyagramı oluşturulması gerekir. Varolan bir modelleme projesine yeni bir bağımlılık diyagramı ekleyebilir, bağımlılık diyagramı için yeni bir modelleme projesi oluşturabilir veya var olan bir bağımlılık diyagramını aynı modelleme projesi içinde kopyalayabilirsiniz.

> [!IMPORTANT]
> Varolan bir bağımlılık diyagramını bir modelleme projesinden başka bir modelleme projesine veya çözümdeki başka bir konuma eklemeyin, sürüklemeyin veya kopyalamayın. Bu şekilde kopyalanmış bir bağımlılık diyagramı, diyagramı değiştirseniz bile özgün diyagramla aynı başvurulara sahip olacaktır. Bu, katman doğrulamasının düzgün çalışmasını engeller ve diyagramı açmaya çalışırken eksik öğeler veya diğer hatalar gibi başka sorunlara neden olabilir.

Bkz. [kodunuzda bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a>İşlevsel alan veya bileşenleri temsil etmek için katmanları tanımlama

Katmanlar, projeler, kod dosyaları, ad alanları, sınıflar ve yöntemler gibi mantıksal *yapıt*gruplarını temsil eder. Görsel C# ve Visual Basic projelerden yapıtlardan katmanlar oluşturabilir veya Word dosyaları ya da PowerPoint sunuları gibi belgeleri bağlayarak bir katmana özellikler veya planlar ekleyebilirsiniz. Her katman diyagramda dikdörtgen olarak görünür ve onunla bağlantılı yapıların sayısını gösterir. Katman, daha belirli görevleri tanımlayan iç içe katmanlar içerebilir.

Genel bir kılavuz olarak, "sunum" veya "Hizmetler" gibi işlevleri işlevine göre adlandırın. Yapıtlar yakından bağımlıysa, bunları aynı katmana yerleştirin. Yapıtlar ayrı ayrı güncelleştirilebiliyorsanız veya ayrı uygulamalarda kullanılıyorsa, bunları farklı katmanlara yerleştirin. Katman desenleri hakkında bilgi edinmek için [http://go.microsoft.com/fwlink/?LinkId=145794](http://go.microsoft.com/fwlink/?LinkId=145794)konumundaki desenler & Uygulamalar sitesini ziyaret edin.

> [!TIP]
> Katmanlara bağlayabileceğiniz ancak bağımlılık diyagramına karşı doğrulamayı desteklemeyen belirli türde yapıtlar vardır. Yapının doğrulamayı destekleyip desteklemediğini görmek için, yapıt bağlantısının **doğrulamayı destekler** özelliğini Incelemek üzere **Katman Gezgini** ' ni açın. Bkz. [katmanlar arasında var olan bağımlılıkları bulma](#Generate).

Tanıdık bir uygulamayı güncelleştirirken kod haritaları da oluşturabilirsiniz. Bu diyagramlar, kodu araştırırken desenleri ve bağımlılıkları keşfetmenize yardımcı olabilir. Ad alanlarını ve sınıfları araştırmak için Çözüm Gezgini kullanın. Bu, genellikle var olan katmanlara de karşılık gelir. Bu kod yapılarını katmanlara Çözüm Gezgini, bağımlılık diyagramlarına sürükleyerek atayın. Daha sonra kodu güncelleştirmenize ve tasarımla tutarlı tutmaya yardımcı olması için bağımlılık diyagramlarını kullanabilirsiniz.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a>Katmanlar arasında var olan bağımlılıkları bulma

Bir bağımlılık, bir katman ile ilişkili yapının başka bir katman ile ilişkili bir yapıya başvurusu olduğu yerde var olur. Örneğin, bir katmandaki sınıf başka bir katmanda sınıfı olan değişkeni bildirir. Mevcut bağımlılıkları tersine mühendislik yaparak keşfedebilirsiniz.

> [!NOTE]
> Bağımlılıklarda belirli türdeki yapılar için ters mühendislik uygulanamaz. Örneğin, hiçbir bağımlılıkta metin dosyasına bağlı katmandan veya katmana ters mühendislik uygulanmaz. Hangi yapıların tersine mühendislik uygulayabileceğiniz bağımlılıklara sahip olduğunu görmek için, bir veya birden fazla katmana sağ tıklayıp **bağlantıları görüntüle**' ye tıklayın. **Katman Gezgini**' nde **doğrulamayı destekler** sütununu inceleyin. Bağımlılıklar, bu sütunun **yanlış**gösterdiği yapıtlar için ters mühendislik uygulanmaz.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Katmanlar arasında varolan bağımlılıklara ters mühendislik uygulamak için

Bir katman veya birden çok katman seçin, seçili katmana sağ tıklayın ve ardından **Bağımlılıklar Oluştur**' a tıklayın.

Genellikle var olmaması gereken bazı bağımlılıklar göreceksiniz. Bu bağımlılıkları hedeflenen tasarım ile uyumlu hale getirmek için düzenleyebilirsiniz.

## <a name="EditArchitecture"></a>Tasarlanan tasarımı göstermek için katmanları ve bağımlılıkları düzenleyin

Sisteminizde veya amaçlanan mimaride yapmayı planladığınız değişiklikleri anlatmak için, bağımlılık diyagramını düzenlemek üzere aşağıdaki adımları kullanın. Ayrıca, kod yapısını genişletmeden önce geliştirmek için bazı yeniden düzenleme değişiklikleri yapmayı düşünebilirsiniz. Bkz. [kodun yapısını geliştirme](#Improving).

|**Hedef**|**Bu adımları gerçekleştirin**|
|-|-|
|Olmaması gereken bir bağımlılığı silme|Bağımlılığa tıklayın ve ardından **Delete**tuşuna basın.|
|Bağımlılık yönünü değiştirme veya kısıtlama|**Direction** özelliğini ayarlayın.|
|Yeni bağımlılıklar oluşturma|**Bağımlılık** ve **çift yönlü bağımlılık** araçlarını kullanın.<br /><br /> Çoklu bağımlılıklar çizmek için araca çift tıklayın. İşiniz bittiğinde **işaretçi** aracına tıklayın veya **ESC** tuşuna basın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtme|Katmanın **yasak ad alanı bağımlılıkları** özelliğindeki ad alanlarını yazın. Ad alanlarını ayırmak için noktalı virgül ( **;** ) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtme|Katmanın **yasak ad alanları** özelliğindeki ad alanlarını yazın. Ad alanlarını ayırmak için noktalı virgül ( **;** ) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarından birine ait olması gerektiğini belirtme|Katmanın **gerekli ad alanları** özelliğindeki ad alanını yazın. Ad alanlarını ayırmak için noktalı virgül ( **;** ) kullanın.|

### <a name="Improving"></a>Kod yapısını geliştirme

Değişiklikleri yeniden düzenleme, uygulamanın davranışını etkilemeyen geliştirmelerdir, ancak gelecekte değiştirilmesini ve genişletmeyi daha kolay hale getirmeye yardımcı olur. İyi yapılandırılmış kod, bağımlılık diyagramına soyutlamak kolay bir tasarıma sahiptir.

Örneğin, koddaki her ad alanı için bir katman oluşturur ve ardından bağımlılıklara ters mühendislik yaparsanız katmanlar arasında tek yönlü bir bağımlılık kümesi olmalıdır. Katmanlarınız olarak sınıflar veya yöntemler kullanarak daha ayrıntılı bir diyagram oluşturursanız, sonuç aynı özelliklere de sahip olmalıdır.

Bu durum bu değilse, kodun ömrü boyunca değiştirilmesi daha zordur ve bağımlılık diyagramları kullanılarak doğrulama için daha az uygundur.

## <a name="NewAreas"></a>Uygulamanızın yeni bölgelerini tasarlama

Yeni bir proje veya yeni bir projedeki yeni bir alan geliştirmeyi başlattığınızda, kodu geliştirmeye başlamadan önce ana bileşenleri belirlemenize yardımcı olmak için Katmanlar ve bağımlılıklar çizebilirsiniz.

- Mümkünse, bağımlılık diyagramlarınızda **tanımlanabilir mimari desenleri gösterin** . Örneğin, bir masaüstü uygulamasını açıklayan bir bağımlılık diyagramı, sunum, etki alanı mantığı ve veri deposu gibi katmanları içerebilir. Bir uygulamadaki tek bir özelliği kaplayan bir bağımlılık diyagramı, model, görünüm ve denetleyici gibi katmanlara sahip olabilir. Bu tür desenler hakkında daha fazla bilgi için bkz. [desenler & uygulamalar: uygulama mimarisi](http://go.microsoft.com/fwlink/?LinkId=145794).

- Ad alanı, sınıf veya bileşen gibi **her katman için bir kod yapıtı oluşturun** . Bu, kodu izlemenizi ve kod yapıtlarını katmanlara bağlamayı kolaylaştırır. Her yapıyı oluşturur almaz, uygun katmana bağlayın.

- **Birçok sınıfı ve diğer yapıtları** katmanlara bağladığınız ad alanları gibi daha büyük yapıtlar içinde yer aldığı için katmanlara bağlamanız gerekmez.

- **Yeni bir özellik için yeni bir diyagram oluşturun**. Genellikle, uygulamanın tamamını açıklayan bir veya daha fazla bağımlılık diyagramı olacaktır. Uygulama içinde yeni bir özellik tasarlıyorsanız, mevcut diyagramları eklemeyin veya değiştirmeyin. Bunun yerine, kodun yeni parçalarını yansıtan kendi diyagramınızı oluşturun. Yeni diyagramdaki katmanlar, yeni özellik için sunum, etki alanı mantığı ve veritabanı katmanları içerebilir.

     Uygulamayı yapılandırdığınızda, kodunuz her ikisi de genel diyagramda ve daha ayrıntılı özellik diyagramınızla karşılaştırılarak onaylanır.

## <a name="EditLayout"></a>Sununun ve tartışmanın yerleşimini düzenleme

Katmanları ve bağımlılıkları belirlemenize veya bunları takım üyeleriyle tartışmanıza yardımcı olmak için, diyagramın görünüm ve yerleşimini aşağıdaki yollarla düzenleyin:

- Katmanların boyutlarını, şekillerini ve konumlarını değiştirin.

- Katmanların ve bağımlılıkların renklerini değiştirin.

  - Bir veya daha fazla katmanı veya bağımlılığı seçin, sağ tıklayın ve ardından **Özellikler**' e tıklayın. **Özellikler** penceresinde, **Color** özelliğini düzenleyin.

## <a name="Validate"></a>Kodu diyagrama karşı doğrulama

Diyagramı düzenlediğinizde, bu kodu istediğiniz zaman el ile veya her derleme sırasında otomatik olarak doğrulayabilirsiniz.

Bkz.

- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)

- [Yapı Işlemine katman doğrulamasını dahil et](#BuildValidation)

## <a name="UpdateCode"></a>Kodu yeni mimariye uyacak şekilde güncelleştirin

Genellikle, güncelleştirilmiş bir bağımlılık diyagramına göre kodu doğrulaışınızda hatalar ilk kez görünür. Bu hataların çeşitli nedenleri olabilir:

- Yapı yanlış katmana atanmış. Bu durumda, yapıyı taşıyın.

- Sınıf gibi bir yapı, başka bir sınıfı mimarinizle çakışacak şekilde kullanıyor. Bu durumda, bağımlılığı kaldırmak için kodu yeniden düzenleyin.

Bu hataları çözmek için doğrulama sırasında daha fazla hata görünmeyene kadar kodu güncelleştirin. Bu genellikle yinelemeli bir işlemdir. Bu hatalar hakkında daha fazla bilgi için bkz. [bağımlılık diyagramlarında kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Kodu geliştirirken veya yeniden düzenleme yaparken, bağımlılık diyagramına bağlanacak yeni yapıtlar olabilir. Ancak, bu gerekli olmayabilir, örneğin, varolan ad alanlarını temsil eden katmanlarınız varsa ve yeni kod yalnızca bu ad alanlarına daha fazla malzeme ekler.

Geliştirme işlemi sırasında, doğrulama esnasında bildirilen çakışmaların bazılarını gizlemek isteyebilirsiniz. Örneğin, zaten çözdüğünüz veya özel senaryonuzla ilgili olmayan hataları gizlemek isteyebilirsiniz. Bir hatayı bastırdığınızda, bir iş öğesini Team Foundation 'da günlüğe kaydetmek iyi bir uygulamadır. Bu görevi gerçekleştirmek için bkz. [bağımlılık diyagramlarında kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a>Yapı işlemine katman doğrulamasını dahil et

Koddaki gelecekteki değişikliklerin bağımlılık diyagramlarına uyduğundan emin olmak için, çözümünüzün standart yapı işlemine katman doğrulaması dahil edin. Diğer takım üyeleri çözümü oluştururken, koddaki bağımlılıklar ve bağımlılık diyagramı arasındaki herhangi bir farklılık derleme hatası olarak bildirilir. Yapı sürecinde katman doğrulaması ekleme hakkında daha fazla bilgi için bkz. [bağımlılık diyagramlarında kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)
