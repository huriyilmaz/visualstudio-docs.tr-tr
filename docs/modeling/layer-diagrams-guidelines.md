---
title: 'Bağımlılık Diyagramları: Yönergeler'
description: Visual Studio ' de bağımlılık diyagramları oluşturarak uygulamanızın mimarisini yüksek düzeyde nasıl tanımlacağınızı öğrenin.
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
ms.openlocfilehash: 69d32acfb5f21250ca0a4edc296bd0221da205cf
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131127162"
---
# <a name="dependency-diagrams-guidelines"></a>Bağımlılık diyagramları: yönergeler

Visual Studio ' de *bağımlılık diyagramları* oluşturarak uygulamanızın mimarisini yüksek düzeyde tanıtın. Kodunuzu bir bağımlılık diyagramı ile doğrulayarak kodunuzun bu tasarımla tutarlı kalmasını sağlayın. Yapı sürecinizdeki katman doğrulamasını da dahil edebilirsiniz. Bkz. [Channel 9 videosu: bağımlılık diyagramlarını kullanarak mimarinizi tasarlama ve doğrulama](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

hangi Visual Studio sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları için sürüm desteği](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

> [!NOTE]
> .net Core projeleri için bağımlılık diyagramları Visual Studio 2019 sürüm 16,2 ' den başlayarak desteklenir.

## <a name="what-is-a-dependency-diagram"></a>Bağımlılık diyagramı nedir?

Geleneksel mimari diyagramı gibi bir bağımlılık diyagramı, tasarımın ana bileşenlerini veya işlevsel birimlerini ve bunların bağımlılıklarını tanımlar. Diyagramdaki *Katman* olarak adlandırılan her düğüm, bir dizi ad alanı, proje veya diğer yapıtları temsil eder. Tasarımınızda bulunması gereken bağımlılıkları çizebilirsiniz. Geleneksel mimari diyagramlarından farklı olarak, kaynak kodundaki gerçek bağımlılıkların belirttiğiniz hedeflenen bağımlılıklara uygun olduğunu doğrulayabilirsiniz. Üzerinde düzenli bir yapılandırmanın doğrulama parçasını yaparak [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] , program kodunun sonraki değişikliklerle sistem mimarisine uymaya devam etmesini sağlayabilirsiniz. Bkz. [bağımlılık diyagramları: başvuru](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Uygulamanızı bağımlılık diyagramlarıyla tasarlama veya güncelleştirme

Aşağıdaki adımlarda, geliştirme sürecinde bağımlılık diyagramlarının nasıl kullanılacağına ilişkin bir genel bakış sağlanmaktadır. Bu konunun sonraki bölümlerinde, her adımla ilgili daha fazla ayrıntı açıklanmıştır. Yeni bir tasarım geliştiriyorsanız, varolan koda başvuran adımları atlayın.

> [!NOTE]
> Bu adımlar yaklaşık sırada görüntülenir. Büyük olasılıkla görevlerin çakışmasını, bunları kendi durumunuza uyacak şekilde yeniden sıralamak ve projenizdeki her yinelemenin başlangıcında tekrar ziyaret etmek isteyeceksiniz.

1. Tüm uygulama için veya içindeki bir katman için [bir bağımlılık diyagramı oluşturun](#Create) .

2. [Birincil işlevsel alanların veya uygulamanızın bileşenlerinin temsil edilebilmesi için katmanları tanımlayın](#CreateLayers) . Bu katmanları işlevine göre adlandırın, örneğin, "sunum" veya "Hizmetler". Visual Studio çözümünüz varsa, her katmanı projeler, ad alanları, dosyalar vb. gibi *yapıtlar* koleksiyonuyla ilişkilendirebilirsiniz.

3. Katmanlar arasında [var olan bağımlılıkları bulur](#Generate) .

4. Kod yansıtmasını istediğiniz güncelleştirilmiş tasarımı göstermek için [katmanları ve bağımlılıkları düzenleyin](#EditArchitecture) .

5. Asıl mimari blokları veya bileşenleri temsil eden Katmanlar oluşturarak ve her katmanın diğerlerini nasıl kullandığını göstermek için bağımlılıklar tanımlayarak [uygulamanızın yeni bölümlerini tasarlayın](#NewAreas) .

6. İş arkadaşlarınızla tartışmanıza yardımcı olması için [diyagramın yerleşimini ve görünümünü düzenleyin](#EditLayout) .

7. Kod ve ihtiyacınız olan mimari arasındaki çakışmaların vurgulanmasını sağlamak için [kodu bağımlılık diyagramına göre doğrulayın](#Validate) .

8. [Kodu Yeni mimarinize uyacak şekilde güncelleştirin](#UpdateCode). Doğrulama çakışma gösterene kadar kodu tekrarlayarak geliştirin ve yeniden düzenleyin.

9. Kodun tasarımınıza uygun olmaya devam ettiğinden emin olmak için [yapı işlemine katman doğrulamayı dahil edin](#BuildValidation) .

## <a name="create-a-dependency-diagram"></a><a name="Create"></a> Bağımlılık diyagramı oluşturma

Bir modelleme projesi içinde bir bağımlılık diyagramı oluşturulması gerekir. Varolan bir modelleme projesine yeni bir bağımlılık diyagramı ekleyebilir, bağımlılık diyagramı için yeni bir modelleme projesi oluşturabilir veya var olan bir bağımlılık diyagramını aynı modelleme projesi içinde kopyalayabilirsiniz.

> [!IMPORTANT]
> Varolan bir bağımlılık diyagramını bir modelleme projesinden başka bir modelleme projesine veya çözümdeki başka bir konuma eklemeyin, sürüklemeyin veya kopyalamayın. Bu şekilde kopyalanmış bir bağımlılık diyagramı, diyagramı değiştirseniz bile özgün diyagramla aynı başvurulara sahip olacaktır. Bu, katman doğrulamasının düzgün çalışmasını engeller ve diyagramı açmaya çalışırken eksik öğeler veya diğer hatalar gibi başka sorunlara neden olabilir.

Bkz. [kodunuzda bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> İşlevsel alan veya bileşenleri temsil etmek için katmanları tanımlama

Katmanlar, projeler, kod dosyaları, ad alanları, sınıflar ve yöntemler gibi mantıksal *yapıt* gruplarını temsil eder. Visual C# ve Visual Basic projelerinden yapıtlardan katmanlar oluşturabilir veya Word dosyaları veya PowerPoint sunumları gibi belgeleri bağlayarak bir katmana özellikler veya planlar ekleyebilirsiniz. Her katman diyagramda dikdörtgen olarak görünür ve onunla bağlantılı yapıların sayısını gösterir. Katman, daha belirli görevleri tanımlayan iç içe katmanlar içerebilir.

Genel bir kılavuz olarak, "sunum" veya "Hizmetler" gibi işlevleri işlevine göre adlandırın. Yapıtlar yakından bağımlıysa, bunları aynı katmana yerleştirin. Yapıtlar ayrı ayrı güncelleştirilebiliyorsanız veya ayrı uygulamalarda kullanılıyorsa, bunları farklı katmanlara yerleştirin.

> [!TIP]
> Katmanlara bağlayabileceğiniz ancak bağımlılık diyagramına karşı doğrulamayı desteklemeyen belirli türde yapıtlar vardır. Yapının doğrulamayı destekleyip desteklemediğini görmek için, yapıt bağlantısının **doğrulamayı destekler** özelliğini Incelemek üzere **Katman Gezgini** ' ni açın. Bkz. [katmanlar arasında var olan bağımlılıkları bulma](#Generate).

Tanıdık bir uygulamayı güncelleştirirken kod haritaları da oluşturabilirsiniz. Bu diyagramlar, kodu araştırırken desenleri ve bağımlılıkları keşfetmenize yardımcı olabilir. Ad alanlarını ve sınıfları araştırmak için Çözüm Gezgini kullanın. Bu, genellikle var olan katmanlara de karşılık gelir. Bu kod yapılarını katmanlara Çözüm Gezgini, bağımlılık diyagramlarına sürükleyerek atayın. Daha sonra kodu güncelleştirmenize ve tasarımla tutarlı tutmaya yardımcı olması için bağımlılık diyagramlarını kullanabilirsiniz.

Bkz.

- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)

- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Katmanlar arasında var olan bağımlılıkları bulma

Bir bağımlılık, bir katman ile ilişkili yapının başka bir katman ile ilişkili bir yapıya başvurusu olduğu yerde var olur. Örneğin, bir katmandaki sınıf başka bir katmanda sınıfı olan değişkeni bildirir. Mevcut bağımlılıkları tersine mühendislik yaparak keşfedebilirsiniz.

> [!NOTE]
> Bağımlılıklarda belirli türdeki yapılar için ters mühendislik uygulanamaz. Örneğin, hiçbir bağımlılıkta metin dosyasına bağlı katmandan veya katmana ters mühendislik uygulanmaz. Hangi yapıların tersine mühendislik uygulayabileceğiniz bağımlılıklara sahip olduğunu görmek için, bir veya birden fazla katmana sağ tıklayıp **bağlantıları görüntüle**' ye tıklayın. **Katman Gezgini**' nde **doğrulamayı destekler** sütununu inceleyin. Bağımlılıklar, bu sütunun **yanlış** gösterdiği yapıtlar için ters mühendislik uygulanmaz.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Katmanlar arasında varolan bağımlılıklara ters mühendislik uygulamak için

Bir katman veya birden çok katman seçin, seçili katmana sağ tıklayın ve ardından **Bağımlılıklar Oluştur**' a tıklayın.

Genellikle var olmaması gereken bazı bağımlılıklar göreceksiniz. Bu bağımlılıkları hedeflenen tasarım ile uyumlu hale getirmek için düzenleyebilirsiniz.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> Tasarlanan tasarımı göstermek için katmanları ve bağımlılıkları düzenleyin

Sisteminizde veya amaçlanan mimaride yapmayı planladığınız değişiklikleri anlatmak için, bağımlılık diyagramını düzenlemek üzere aşağıdaki adımları kullanın. Ayrıca, kod yapısını genişletmeden önce geliştirmek için bazı yeniden düzenleme değişiklikleri yapmayı düşünebilirsiniz. Bkz. [kodun yapısını geliştirme](#Improving).

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Olmaması gereken bir bağımlılığı silme|Bağımlılığa tıklayın ve ardından **Delete** tuşuna basın.|
|Bağımlılık yönünü değiştirme veya kısıtlama|**Direction** özelliğini ayarlayın.|
|Yeni bağımlılıklar oluşturma|**Bağımlılık** ve **çift yönlü bağımlılık** araçlarını kullanın.<br /><br /> Çoklu bağımlılıklar çizmek için araca çift tıklayın. İşiniz bittiğinde **işaretçi** aracına tıklayın veya **ESC** tuşuna basın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtme|Katmanın **yasak ad alanı bağımlılıkları** özelliğindeki ad alanlarını yazın. Ad alanlarını ayırmak için noktalı virgül (**;**) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtme|Katmanın **yasak ad alanları** özelliğindeki ad alanlarını yazın. Ad alanlarını ayırmak için noktalı virgül (**;**) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarından birine ait olması gerektiğini belirtme|Katmanın **gerekli ad alanları** özelliğindeki ad alanını yazın. Ad alanlarını ayırmak için noktalı virgül (**;**) kullanın.|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> Kod yapısını geliştirme

Değişiklikleri yeniden düzenleme, uygulamanın davranışını etkilemeyen geliştirmelerdir, ancak gelecekte değiştirilmesini ve genişletmeyi daha kolay hale getirmeye yardımcı olur. İyi yapılandırılmış kod, bağımlılık diyagramına soyutlamak kolay bir tasarıma sahiptir.

Örneğin, kodda her ad alanı için bir katman oluşturur ve ardından bağımlılıkların tersine mühendisliklerini oluşturursanız, katmanlar arasında en az bir tek yollu bağımlılık kümesi olması gerekir. Katmanlarınız olarak sınıfları veya yöntemleri kullanarak daha ayrıntılı bir diyagram oluşturmanız, sonucun da aynı özelliklere sahip olması gerekir.

Böyle bir durum yoksa, kodun ömrü boyunca değişmesi daha zor olur ve bağımlılık diyagramlarını kullanarak doğrulama için daha az uygun olur.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Uygulamanıza yeni alanlar tasarlama

Yeni bir proje veya yeni bir projede yeni bir alan geliştirmeye başlarız, kodu geliştirmeye başlamadan önce ana bileşenlerin belirlenmesine yardımcı olmak için katmanlar ve bağımlılıklar çizebilirsiniz.

- **Mümkünse bağımlılık diyagramlarınızda** tanımlanabilir mimari desenleri gösterme. Örneğin, bir masaüstü uygulamasını açıklayan bağımlılık diyagramı Sunu, Etki Alanı Mantığı ve Veri Deposu gibi katmanlar içerebilir. Uygulama içindeki tek bir özelliği kapsayan bağımlılık diyagramında Model, Görünüm ve Denetleyici gibi katmanlar olabilir.

- **Ad alanı, sınıf veya bileşen gibi** her katman için bir kod yapıt oluşturun. Bu, kodu takip etme ve kod yapıtlarını katmanlara bağlamayı kolaylaştırır. Her yapıyı oluşturur oluşturmaz uygun katmana bağlamanız gerekir.

- **Çoğu sınıfı ve diğer yapıtları** katmanlara bağlamanız gerek yok çünkü bunlar zaten katmanlara bağlı olan ad alanları gibi daha büyük yapıtlar içinde yer almaktadır.

- **Yeni bir özellik için yeni bir diyagram oluşturun.** Genellikle, uygulamanın tamamını açıklayan bir veya daha fazla bağımlılık diyagramı olur. Uygulama içinde yeni bir özellik tasarıyorsanız mevcut diyagramlara ekleme veya mevcut diyagramları değiştirme. Bunun yerine, kodun yeni bölümlerini yansıtan kendi diyagramınızı oluşturun. Yeni diyagramda yer alan katmanlar, yeni özellik için sunu, etki alanı mantığı ve veritabanı katmanlarını içerebilir.

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
> Kodu geliştirirken veya yeniden düzenlemeye devam ettikçe, bağımlılık diyagramına bağlantı için yeni yapıtlara sahip olabilirsiniz. Ancak, örneğin, mevcut ad alanlarını temsil eden katmanlarınız olduğunda ve yeni kod bu ad alanlarına yalnızca daha fazla malzeme eklerse, bu gerekli değildir.

Geliştirme işlemi sırasında, doğrulama esnasında bildirilen çakışmaların bazılarını gizlemek isteyebilirsiniz. Örneğin, zaten çözdüğünüz veya özel senaryonuzla ilgili olmayan hataları gizlemek isteyebilirsiniz. Bir hatayı bastırdıysanız, Team Foundation'da bir iş öğesini günlüğe kayıt etmek iyi bir uygulamadır. Bu görevi gerçekleştirmek için [bkz. Bağımlılık diyagramları ile kodu doğrulama.](../modeling/validate-code-with-layer-diagrams.md)

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Derleme sürecine katman doğrulaması ekleme

Kodda gelecekte yapılan değişikliklerin bağımlılık diyagramlarına uygun olduğundan emin olmak için çözüme standart derleme işlemi için katman doğrulamayı dahil etmek gerekir. Diğer ekip üyeleri çözümü her derlemesinde, kodda ve bağımlılık diyagramındaki bağımlılıklar arasındaki farklar derleme hataları olarak rapor eder. Derleme sürecine katman doğrulaması ekleme hakkında daha fazla bilgi için [bkz. Bağımlılık diyagramları ile kodu doğrulama.](../modeling/validate-code-with-layer-diagrams.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Kodunuz aracılığıyla bağımlılık diyagramları oluşturma](../modeling/create-layer-diagrams-from-your-code.md)
