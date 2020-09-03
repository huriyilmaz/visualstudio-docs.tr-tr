---
title: Kodunuzda katman diyagramları oluşturun | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eea557035ef4e5f1ffa2585e620a331fb6b5cce2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852074"
---
# <a name="create-layer-diagrams-from-your-code"></a>Kodunuz aracılığıyla katman diyagramları oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yazılım sisteminizin üst düzey, mantıksal mimarisini görselleştirmek için Visual Studio 'da bir *Katman diyagramı* oluşturun. Kodunuzun bu tasarımla tutarlı kaldığından emin olmak için kodunuzu bir katman diyagramı ile doğrulayın. Visual C# .NET ve Visual Basic .NET projeleri için katman diyagramları oluşturabilirsiniz. Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

 ![Katman diyagramı oluşturma](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

 Katman diyagramı, Visual Studio çözüm öğelerini *Katmanlar*olarak adlandırılan mantıksal, soyut gruplar halinde düzenlemenize olanak tanır. Bu yapıların gerçekleştirdiği temel görevleri veya sistemin ana bileşenlerini açıklamak için katmanları kullanabilirsiniz. Her katman, daha ayrıntılı görevleri açıklayan başka katmanlar içerebilir. Katmanlar arasında amaçlanan veya var olan *bağımlılıkları* da belirtebilirsiniz. Oklar olarak temsil edilen bu bağımlılıklar, hangi katmanların diğer katmanlar tarafından temsil edilen işlevi kullanabileceğini veya kullanmakta olduğunu gösterir. Kodunun mimari denetimini sağlamak için diyagram üzerinde hedeflenen bağımlılıkları gösterin ve ardından kodu diyagrama karşı doğrulayın.

## <a name="create-a-layer-diagram"></a><a name="CreateDiagram"></a> Katman diyagramı oluşturma
 Bir katman diyagramı oluşturmadan önce, çözümünüzde bir modelle projesi olduğundan emin olun. Bkz. [UML modelleme projeleri ve diyagramları oluşturma](../modeling/create-uml-modeling-projects-and-diagrams.md).

> [!IMPORTANT]
> Varolan katman diyagramını bir modelleme projesinden başka bir modelleme projesine veya çözüm içindeki başka bir yere eklemeyin, kopyalamayın veya sürüklemeyin. Bu, diyagramı değiştirseniz bile orijinal diyagramdan yapılan başvuruları korur. Bu, katman doğrulamasının doğru çalışmasını da engeller ve siz diyagramı açmaya çalışırken kayıp öğeler veya başka hatalar gibi diğer sorunlara da neden olabilir.
>
> Bunun yerine, modelleme projesine yeni bir katman diyagramı ekleyin. Öğeleri kaynak diyagramdan yeni diyagrama kopyalayın. Hem modelleme projesini hem de yeni katman diyagramını kaydedin.

#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Modelleme projesine yeni bir katman diyagramı eklemek için

1. **Mimari** menüsünde **Yeni UML veya katman diyagramı**' nı seçin.

2. **Şablonlar**altında **Katman diyagramı**' nı seçin.

3. Diyagrama ad verin.

4. **Modelleme projesine ekle**' de, çözümünüzde var olan bir modelleme projesine gidin ve seçin.

     -veya-

     Çözüme yeni modelleme projesi eklemek için **Yeni modelleme projesi oluştur** ' a tıklayın.

    > [!NOTE]
    > Katman diyagramı modelleme projesinin içinde olmalıdır. Bununla birlikte, bunu çözümün herhangi bir yerindeki öğelere bağlayabilirsiniz.

5. Hem modelleme projesini hem de katman diyagramını kaydettiğinizden emin olun.

## <a name="create-layers-from-artifacts"></a><a name="CreateLayers"></a> Yapıtlardan katmanlar oluşturma
 Visual Studio çözüm öğelerinden projeler, kod dosyaları, ad alanları, sınıflar ve yöntemler gibi katmanlar oluşturabilirsiniz. Bu, katmanlar ve öğeler arasında otomatik olarak bağlantılar oluşturarak bunları katman doğrulama işlemine dahil eder.

 Katmanları Word belgeleri veya PowerPoint sunumları gibi doğrulamayı desteklemeyen öğelere de ekleyebilir ve böylece bir katmanı belirtimlerle veya planlarla ilişkilendirebilirsiniz. Katmanları birden fazla uygulama arasında paylaşılan projelerdeki dosyalara da bağlayabilirsiniz, ancak doğrulama işlemi "Katman 1" ve "Katman 2" gibi genel adlarla görünen bu katmanları içermez.

 Bağlı bir öğenin doğrulamayı destekleyip desteklemediğini görmek için **Katman Gezgini** ' ni açın ve öğenin **doğrulamayı destekler** özelliğini inceleyin. Bkz. [yapıtlara bağlantıları yönetme](#Managing).

|**Amaç**|**Bu adımları izleyin**|
|------------|----------------------------|
|Tek bir yapı için katman oluşturma|<ol><li>Öğeyi şu kaynaklardaki katman diyagramına sürükleyin:<br /><br /> <ul><li>**Çözüm Gezgini**<br /><br />         Örneğin, dosyaları veya projeleri sürükleyebilirsiniz.</li><li>Kod eşlemeleri<br /><br />         Bkz. [çözümlerinizde harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md) ve [uygulamalarınızda hata ayıklamak Için kod haritaları kullanın](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Sınıf görünümü** veya **nesne tarayıcısı**</li></ul><br />     Katman, diyagramda görünür ve yapıya bağlanır.</li><li>İlişkili kodun veya yapıların sorumluluklarını yansıtmak için katmanı yeniden adlandırın.</li></ol> **Önemli:**  İkili dosyaları katman diyagramına sürüklemek, başvurularını otomatik olarak modelleme projesine eklemez. Doğrulamak istediğiniz ikili dosyaları el ile modelleme projesine eklemeniz gerekir. **Modelleme projesine ikili dosyalar eklemek için** <ol><li>**Çözüm Gezgini**, modelleme projesi için kısayol menüsünü açın ve ardından **Varolan öğe Ekle**' yi seçin.</li><li>**Varolan öğe Ekle** iletişim kutusunda, ikili dosyalar ' a gidin, bunları seçin ve ardından **Tamam**' ı seçin.     İkili dosyalar modelleme projesinde görünür.</li><li>**Çözüm Gezgini**, eklediğiniz bir ikili dosyayı seçin ve ardından **Özellikler** penceresini açmak için **F4** tuşuna basın.</li><li>Her ikili dosyada, **derleme eylemi** özelliğini **doğrulanacak**olarak ayarlayın.</li></ol>|
|Seçilen tüm yapılar için tek bir katman oluşturma|Tüm yapıları aynı anda katman diyagramına sürükleyin.<br /><br /> Katman diyagramda görünür ve tüm yapılara bağlıdır.|
|Seçilen her yapı için bir katman oluşturma|Tüm yapıtları aynı anda katman diyagramına sürüklerken **SHIFT** tuşuna basın ve basılı tutun. **Note:**  Bir dizi öğeyi seçmek için **SHIFT** tuşunu kullanırsanız, yapıtları seçtikten sonra anahtarı bırakın. Yapıları diyagrama sürüklerken tuşu tekrar basılı tutun. <br /><br /> Katman her yapı için diyagramda görünür ve her yapıya bağlanır.|
|Katmana yapı ekleme|Yapıyı katmana sürükleyin.|
|Bağlantısız bir katman oluşturma|**Araç kutusunda** **Katman diyagramı** bölümünü genişletin ve katman diyagramına bir **Katman** sürükleyin.<br /><br /> Çoklu katman eklemek için araca çift tıklayın. İşiniz bittiğinde **işaretçi** aracını seçin veya **ESC** tuşuna basın.<br /><br /> - veya -<br /><br /> Katman diyagramının kısayol menüsünü açın, **Ekle**' yi ve ardından **Katman**' ı seçin.|
|İç içe katmanlar oluşturma|Varolan katmanı başka bir katmanın üzerine sürükleyin.<br /><br /> - veya -<br /><br /> Katman için kısayol menüsünü açın, **Ekle**' yi ve ardından **Katman**' ı seçin.|
|Varolan iki veya daha fazla katmanı içeren yeni bir katman oluşturma|Katmanları seçin, seçiminizin kısayol menüsünü açın ve **Grup**' u seçin.|
|Katmanın rengini değiştirme|**Color** özelliğini istediğiniz renge ayarlayın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtme|Katmanın **yasak ad alanları** özelliğindeki ad alanlarını yazın. Ad alanlarını ayırmak için noktalı virgül (**;**) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtme|Katmanın **yasak ad alanı bağımlılıkları** özelliğindeki ad alanlarını yazın. Ad alanlarını ayırmak için noktalı virgül (**;**) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarından birine ait olması gerektiğini belirtme|Katmanın **gerekli ad alanları** özelliğindeki ad alanını yazın. Ad alanlarını ayırmak için noktalı virgül (**;**) kullanın.|

 Bir katmandaki sayı, katmana bağlı olan yapıların sayısını gösterir. Ancak, bu sayıyı okurken, aşağıdakileri unutmayın:

- Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.

     Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.

- Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.

## <a name="manage-links-between-layers-and-artifacts"></a><a name="Managing"></a> Katmanlar ve yapıtlar arasındaki bağlantıları yönetme

1. Katman diyagramında katmanın kısayol menüsünü açın ve **bağlantıları görüntüle**' yi seçin.

     **Katman Gezgini** seçili katman için yapıt bağlantılarını gösterir.

2. Bu bağlantıları yönetmek için aşağıdaki görevleri kullanın.

|**Amaç**|**Katman Gezgini 'nde**|
|------------|---------------------------|
|Katman ve yapı arasındaki bağlantıyı silme|Yapıt bağlantısının kısayol menüsünü açın ve **Sil**' i seçin.|
|Bağlantıyı bir katmandan diğerine taşıma|Yapı bağlantısını diyagramda varolan bir katmana sürükleyin.<br /><br /> - veya -<br /><br /> 1. yapıt bağlantısının kısayol menüsünü açın ve **Kes**' i seçin.<br />2. katman diyagramında katmanın kısayol menüsünü açın ve **Yapıştır**' ı seçin.|
|Bağlantıyı bir katmandan diğerine kopyalama|1. yapıt bağlantısının kısayol menüsünü açın ve **Kopyala**' yı seçin.<br />2. katman diyagramında katmanın kısayol menüsünü açın ve **Yapıştır**' ı seçin.|
|Varolan yapı bağlantısından yeni bir katman oluşturma|Yapı bağlantısını diyagramdaki boş bir alana sürükleyin.|
|Bağlantılı bir yapının, katman diyagramına karşı doğrulamayı desteklediğini onaylayın.|Yapıt bağlantısı için **doğrulama sütununu destekler** bölümüne bakın.|

## <a name="reverse-engineer-existing-dependencies"></a><a name="Discovering"></a> Mevcut bağımlılıklara ters mühendislik Uygula
 Bir bağımlılık, bir katman ile ilişkili yapının başka bir katman ile ilişkili bir yapıya başvurusu olduğu yerde var olur. Örneğin, bir katmandaki sınıf başka bir katmanda sınıfı olan değişkeni bildirir. Diyagramdaki katmanlara bağlanmış yapılar için varolan bağımlılıklara ters mühendislik uygulayabilirsiniz.

> [!NOTE]
> Bağımlılıklarda belirli türdeki yapılar için ters mühendislik uygulanamaz. Örneğin, hiçbir bağımlılıkta metin dosyasına bağlı katmandan veya katmana ters mühendislik uygulanmaz. Hangi yapıların tersine mühendislik uygulayabileceğiniz bağımlılıklara sahip olduğunu görmek için, bir veya birden çok katmanın kısayol menüsünü açın ve **bağlantıları görüntüle**' yi seçin. **Katman Gezgini**' nde **doğrulamayı destekler** sütununu inceleyin. Bağımlılıklar, bu sütunun **yanlış**gösterdiği yapıtlar için ters mühendislik uygulanmaz.

- Bir veya birden çok katman seçin, seçili katmanın kısayol menüsünü açın ve ardından **Bağımlılıklar Oluştur**' u seçin.

  Genellikle var olmaması gereken bazı bağımlılıklar göreceksiniz. Bu bağımlılıkları hedeflenen tasarım ile uyumlu hale getirmek için düzenleyebilirsiniz.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a> Tasarlanan tasarımı göstermek için katmanları ve bağımlılıkları düzenleyin
 Sisteminizde veya hedeflenen mimaride yapmayı planladığınız değişiklikleri açıklamak için katman diyagramını düzenleyin:

|**Amaç**|**Bu adımları gerçekleştirin**|
|------------|-----------------------------|
|Bağımlılık yönünü değiştirme veya kısıtlama|**Direction** özelliğini ayarlayın.|
|Yeni bağımlılıklar oluşturma|**Bağımlılık** ve **çift yönlü bağımlılık** araçlarını kullanın.<br /><br /> Çoklu bağımlılıklar çizmek için araca çift tıklayın. İşiniz bittiğinde **işaretçi** aracını seçin veya **ESC** tuşuna basın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtme|Katmanın **yasak ad alanı bağımlılıkları** özelliğindeki ad alanlarını yazın. Ad alanlarını ayırmak için noktalı virgül (**;**) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtme|Katmanın **yasak ad alanları** özelliğindeki ad alanlarını yazın. Ad alanlarını ayırmak için noktalı virgül (**;**) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarından birine ait olması gerektiğini belirtme|Katmanın **gerekli ad alanları** özelliğindeki ad alanını yazın. Ad alanlarını ayırmak için noktalı virgül (**;**) kullanın.|

## <a name="change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a> Öğelerin diyagramda görünme şeklini değiştirme
 Özelliklerini düzenleyerek katmanların boyutunu, şeklini, rengini ve konumunu veya bağımlılıkların rengini değiştirebilirsiniz.

## <a name="discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a> Kod haritasında desenleri ve bağımlılıkları bulma
 Katman diyagramları oluştururken, **kod haritaları**da oluşturabilirsiniz. Bu diyagramlar, kodu araştırırken desenleri ve bağımlılıkları keşfetmenize yardımcı olabilir. Derlemeleri, ad alanlarını ve sınıfları araştırmak için Çözüm Gezgini, Sınıf Görünümü veya Nesne Tarayıcısı kullanın; Bu, genellikle mevcut katmanlara iyi karşılık gelir. Kod eşlemeleri hakkında daha fazla bilgi için bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)

- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Channel 9 video: katman diyagramları katman diyagramlarını kullanarak mimarinizi tasarlama ve doğrulama](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture) [: başvuru](../modeling/layer-diagrams-reference.md) [Katman diyagramları: yönergeler](../modeling/layer-diagrams-guidelines.md) [Katman diyagramları ile kodu doğrulama](../modeling/validate-code-with-layer-diagrams.md) [kodu görselleştirin](../modeling/visualize-code.md)
