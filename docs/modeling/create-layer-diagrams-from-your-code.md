---
title: Kodunuz aracılığıyla bağımlılık diyagramları oluşturma
description: Yazılım sisteminizin üst düzey, mantıksal mimarisini görselleştirmek Visual Studio bir bağımlılık diyagramı oluşturma hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: b07af93386d5062f28f19f01ce150fba8ec45dd2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389663"
---
# <a name="create-dependency-diagrams-from-your-code"></a>Kodunuz aracılığıyla bağımlılık diyagramları oluşturma

Yazılım sisteminizin üst düzey, mantıksal mimarisini görselleştirmek için, Visual Studio.  Kodunuzun bu tasarımla tutarlı olduğundan emin olmak için kodunuzu bağımlılık diyagramıyla doğrular. Visual C# için bağımlılık diyagramları oluşturabilir ve Visual Basic oluşturabilirsiniz. Bu özelliği destekleyen Visual Studio için bkz. Mimari ve [modelleme araçları için sürüm desteği.](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)

![Bağımlılık diyagramı oluşturma](../modeling/media/layerdiagramvisualizecode.png)

Bağımlılık diyagramı, çözüm öğelerini Visual Studio olarak adlandırılan mantıksal, soyut gruplar halinde düzenlemenize *olanak sağlar.* Bu yapıların gerçekleştirdiği temel görevleri veya sistemin ana bileşenlerini açıklamak için katmanları kullanabilirsiniz. Her katman, daha ayrıntılı görevleri açıklayan başka katmanlar içerebilir. Katmanlar arasında hedeflenen veya mevcut *bağımlılıkları da* belirtebilirsiniz. Oklar olarak temsil edilen bu bağımlılıklar, hangi katmanların diğer katmanlar tarafından temsil edilen işlevi kullanabileceğini veya kullanmakta olduğunu gösterir. Kodunun mimari denetimini sağlamak için diyagram üzerinde hedeflenen bağımlılıkları gösterin ve ardından kodu diyagrama karşı doğrulayın.

[Video: Mimari bağımlılıklarınızı gerçek zamanlı olarak doğrulama](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="create-a-dependency-diagram"></a><a name="CreateDiagram"></a> Bağımlılık diyagramı oluşturma

Bağımlılık diyagramı oluşturmadan önce çözümde bir modelleme projesi olduğundan emin olun.

> [!IMPORTANT]
> Mevcut bağımlılık diyagramını bir modelleme projesinden başka bir modelleme projesine veya çözümde başka bir yere ekleme, sürükleme veya kopyalamayın. Bu, diyagramı değiştirseniz bile orijinal diyagramdan yapılan başvuruları korur. Bu, katman doğrulamasının doğru çalışmasını da engeller ve siz diyagramı açmaya çalışırken kayıp öğeler veya başka hatalar gibi diğer sorunlara da neden olabilir.
>
> Bunun yerine modelleme projesine yeni bir bağımlılık diyagramı ekleyin. Öğeleri kaynak diyagramdan yeni diyagrama kopyalayın. Hem modelleme projesini hem de yeni bağımlılık diyagramını kaydedin.

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>Modelleme projesine yeni bağımlılık diyagramı ekleme

> [!NOTE]
> .NET Core projeleri için bağımlılık diyagramları, 2019 Visual Studio 16.2 sürümünden itibaren de destekleni.

1. Mimari menüsünde **Yeni** Bağımlılık **Diyagramı'ı seçin.**

2. **Şablonlar'ın** altında bağımlılık **diyagramını seçin.**

3. Diyagrama ad verin.

4. Modelleme **Projesine Ekle'de,** çözümünüzde var olan bir modelleme projesine gidin ve seçin.

     -veya-

     Çözüme **yeni bir modelleme projesi eklemek** için Yeni modelleme projesi oluştur'a tıklayın.

    > [!NOTE]
    > Bağımlılık diyagramı bir modelleme projesinin içinde mevcut olması gerekir. Bununla birlikte, bunu çözümün herhangi bir yerindeki öğelere bağlayabilirsiniz.

5. Hem modelleme projesini hem de bağımlılık diyagramını kaydetmeyi emin olun.

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Kod Haritasından sürükleyip bırakma veya kopyalama ve yapıştırma

1. Mimari menüsünü kullanarak çözüm için bir Kod **Haritası** oluşturma.

2. Yalnızca ürün kodunda bağımlılıkları zorlamak için çözüm klasörlerini ve "Test Varlıklarını" kaldırmak için Kod Eşlemesi filtresi uygulamayı göz önünde bulundurabilirsiniz.

3. Oluşturulan Kod Eşlemesi'nin "Dış" düğümünü kaldırın veya ad alanı bağımlılıklarını zorlamak isteyip istemediklerine bağlı olarak dış derlemeleri gösterecek şekilde genişletin ve Kod Eşlemesi'ne gerekli olmayan derlemeleri silin.

4. Mimari menüsünü kullanarak çözüm için yeni bir Bağımlılık **Diyagramı** oluşturma

5. Kod Haritası'nın tüm düğümlerini seçin _(Ctrl_ A kullanın veya tıklamadan, sürüklemeden ve serbest bırakmadan önce Shift tuşuna basarak bant seçimini  +    kullanın).

6. Seçilen öğeleri sürükleyip bırakın veya kopyalayıp yeni Bağımlılık Doğrulama diyagramına yapıştırın.

7. Bu, geçerli uygulama mimarisini gösterir. Mimarinin ne olması istediğinize karar verin ve bağımlılık diyagramını uygun şekilde değiştirebilirsiniz.

![Kod Haritasından oluşturulan bağımlılık diyagramı](media/dependency-validation-01.png)

## <a name="create-layers-from-artifacts"></a><a name="CreateLayers"></a> Yapıtlardan katmanlar oluşturma
 Visual Studio çözüm öğelerinden projeler, kod dosyaları, ad alanları, sınıflar ve yöntemler gibi katmanlar oluşturabilirsiniz. Bu, katmanlar ve öğeler arasında otomatik olarak bağlantılar oluşturarak bunları katman doğrulama işlemine dahil eder.

 Katmanları Word belgeleri veya PowerPoint sunumları gibi doğrulamayı desteklemeyen öğelere de ekleyebilir ve böylece bir katmanı belirtimlerle veya planlarla ilişkilendirebilirsiniz. Katmanları birden fazla uygulama arasında paylaşılan projelerdeki dosyalara da bağlayabilirsiniz, ancak doğrulama işlemi "Katman 1" ve "Katman 2" gibi genel adlarla görünen bu katmanları içermez.

 Bağlantılı bir öğenin doğrulamayı destekleyip desteklemey olduğunu **görmek için** Katman Gezgini'ni açın **ve öğenin Doğrulamayı** Destekler özelliğini inceleyin. Bkz. [Yapıt bağlantılarını yönetme.](#Managing)

|**Kime**|**Buradaki adımları izleyin**|
|-|-|
|Tek bir yapı için katman oluşturma|<ol><li>Öğeyi şu kaynaklardan bağımlılık diyagramına sürükleyin:<br /><br /> <ul><li>**Çözüm Gezgini**<br /><br />         Örneğin, dosyaları veya projeleri sürükleyebilirsiniz.</li><li>Kod eşlemeleri<br /><br />         Bkz. [Çözümleriniz genelinde bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md) ve [Uygulamalarda hata ayıklamak için kod eşlemeleri kullanma.](../modeling/use-code-maps-to-debug-your-applications.md)</li><li>**Sınıf Görünümü** veya **Nesne Tarayıcısı**</li></ul><br />     Katman, diyagramda görünür ve yapıya bağlanır.</li><li>İlişkili kodun veya yapıların sorumluluklarını yansıtmak için katmanı yeniden adlandırın.</li></ol> **Önemli:**  İkili dosyaları bağımlılık diyagramına sürüklemek, başvurularını modelleme projesine otomatik olarak eklemez. Doğrulamak istediğiniz ikili dosyaları el ile modelleme projesine eklemeniz gerekir. **Modelleme projesine ikili dosyalar eklemek için** <ol><li>Bu **Çözüm Gezgini** modelleme projesinin kısayol menüsünü açın ve Var Olan Öğeyi **Ekle'yi seçin.**</li><li>Var Olan **Öğeyi Ekle iletişim** kutusunda ikili dosyalara göz atarak bunları seçin ve ardından Tamam'ı **seçin.**     İkili dosyalar modelleme projesinde görünür.</li><li>Bu **Çözüm Gezgini,** ekley istediğiniz ikili dosyayı seçin ve **ardından F4 tuşuna** basarak Özellikler **penceresini** açın.</li><li>Her ikili dosyada Derleme Eylemi **özelliğini Doğrula** olarak **ayarlayın.**</li></ol>|
|Seçilen tüm yapılar için tek bir katman oluşturma|Tüm yapıtları aynı anda bağımlılık diyagramına sürükleyin.<br /><br /> Katman diyagramda görünür ve tüm yapılara bağlıdır.|
|Seçilen her yapı için bir katman oluşturma|Tüm **yapıtları aynı** anda bağımlılık diyagramına sürüklerken SHIFT tuşuna basın ve basılı tutun. **Not:**  Bir öğe aralığı seçmek için **SHIFT** tuşunu kullanırsanız, yapıtları seçdikten sonra anahtarı bırakın. Yapıları diyagrama sürüklerken tuşu tekrar basılı tutun. <br /><br /> Katman her yapı için diyagramda görünür ve her yapıya bağlanır.|
|Katmana yapı ekleme|Yapıyı katmana sürükleyin.|
|Bağlantısız bir katman oluşturma|Araç **Kutusunda Bağımlılık** Diyagramı **bölümünü genişletin ve** bir Katman'ı **bağımlılık** diyagramına sürükleyin.<br /><br /> Çoklu katman eklemek için araca çift tıklayın. Bitirdikten sonra İşaretçi aracını **seçin** veya **ESC tuşuna** basın.<br /><br /> - veya -<br /><br /> Bağımlılık diyagramının kısayol menüsünü açın, Ekle'yi **ve ardından** Katman'ı **seçin.**|
|İç içe katmanlar oluşturma|Varolan katmanı başka bir katmanın üzerine sürükleyin.<br /><br /> - veya -<br /><br /> Bir katmanın kısayol menüsünü açın, **Ekle'yi ve** ardından Katman'ı **seçin.**|
|Varolan iki veya daha fazla katmanı içeren yeni bir katman oluşturma|Katmanları seçin, seçiminizin kısayol menüsünü açın ve ardından Grup'a **tıklayın.**|
|Katmanın rengini değiştirme|Color **özelliğini** istediğiniz renge ayarlayın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtme|Katmanın Yasak Ad Alanları özelliğine **ad alanlarını** yazın. Ad alanlarını ayırmak için **noktalı virgül**( ; ) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtme|Katmanın Yasak Ad Alanı Bağımlılıkları **özelliğine ad alanlarını** yazın. Ad alanlarını ayırmak için **noktalı virgül**( ; ) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarından birine ait olması gerektiğini belirtme|Katmanın Gerekli Ad Alanları **özelliğine ad alanını** yazın. Ad alanlarını ayırmak için **noktalı virgül**( ; ) kullanın.|

 Bir katmandaki sayı, katmana bağlı olan yapıların sayısını gösterir. Ancak, bu sayıyı okurken, aşağıdakileri unutmayın:

- Bir katman diğer yapıları içeren bir yapıya bağlanırsa, ancak katman doğrudan diğer yapılara bağlanmazsa, sayı yalnızca bağlı yapıyı içerir. Bununla birlikte, diğer yapılar katman doğrulanırken analiz için alınır.

     Örneğin, bir katman tek bir ad alanına bağlanırsa, ad alanı sınıflar içerse bile, bağlı yapıların sayısı 1'dir. Katmanın ad alanındaki her bir sınıfa da bağlantıları bulunuyorsa, sayı bağlantılı sınıfları da içerecektir.

- Bir katman yapılarla bağlantılı diğer katmanları içeriyorsa, kapsayıcı katman da üzerindeki sayı bu yapıları içermese bile bu yapılara bağlıdır.

## <a name="manage-links-between-layers-and-artifacts"></a><a name="Managing"></a> Katmanlar ve yapıtlar arasındaki bağlantıları yönetme

1. Bağımlılık diyagramında katmanın kısayol menüsünü açın ve Ardından Bağlantıları **Görüntüle'yi seçin.**

     **Katman Gezgini** seçilen katmanın yapıt bağlantılarını gösterir.

2. Bu bağlantıları yönetmek için aşağıdaki görevleri kullanın.

|**Kime**|**Katman Gezgini'nde**|
|-|-|
|Katman ve yapı arasındaki bağlantıyı silme|Yapıt bağlantısının kısayol menüsünü açın ve Sil'i **seçin.**|
|Bağlantıyı bir katmandan diğerine taşıma|Yapı bağlantısını diyagramda varolan bir katmana sürükleyin.<br /><br /> - veya -<br /><br /> 1. Yapıt bağlantısının kısayol menüsünü açın ve Ardından Kes'i **seçin.**<br />2. Bağımlılık diyagramında katmanın kısayol menüsünü açın ve Yapıştır'ı **seçin.**|
|Bağlantıyı bir katmandan diğerine kopyalama|1. Yapıt bağlantısının kısayol menüsünü açın ve Kopyala'yı **seçin.**<br />2. Bağımlılık diyagramında katmanın kısayol menüsünü açın ve Yapıştır'ı **seçin.**|
|Varolan yapı bağlantısından yeni bir katman oluşturma|Yapı bağlantısını diyagramdaki boş bir alana sürükleyin.|
|Bağlantılı yapıtların bağımlılık diyagramına karşı doğrulamayı desteklediğini doğrulayın.|Yapıt bağlantısı **için Doğrulamayı** Destekler sütununa bakın.|

## <a name="reverse-engineer-existing-dependencies"></a><a name="Discovering"></a> Mevcut bağımlılıklara ters mühendislik uygulama
 Bir bağımlılık, bir katman ile ilişkili yapının başka bir katman ile ilişkili bir yapıya başvurusu olduğu yerde var olur. Örneğin, bir katmandaki sınıf başka bir katmanda sınıfı olan değişkeni bildirir. Diyagramdaki katmanlara bağlanmış yapılar için varolan bağımlılıklara ters mühendislik uygulayabilirsiniz.

> [!NOTE]
> Bağımlılıklarda belirli türdeki yapılar için ters mühendislik uygulanamaz. Örneğin, hiçbir bağımlılıkta metin dosyasına bağlı katmandan veya katmana ters mühendislik uygulanmaz. Hangi yapıtlarda ters mühendislik oluşturabilirsiniz bağımlılıkları olduğunu görmek için, bir veya birden çok katmanın kısayol menüsünü açın ve ardından Bağlantıları **Görüntüle'yi seçin.** Katman **Gezgini'nde** Doğrulamayı **Destekler sütununu** inceleyin. Bağımlılıklar, bu sütunda False olarak gösteren yapıtlar için tersine mühendislik **sağlanmaz.**

- Bir veya birden çok katman seçin, seçili katmanın kısayol menüsünü açın ve bağımlılık **oluştur'a tıklayın.**

  Genellikle var olmaması gereken bazı bağımlılıklar göreceksiniz. Bu bağımlılıkları hedeflenen tasarım ile uyumlu hale getirmek için düzenleyebilirsiniz.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a> Hedeflenen tasarımı göstermek için katmanları ve bağımlılıkları düzenleme
 Sisteminize veya hedeflenen mimariye yapmayı plan yaptığınız değişiklikleri açıklamak için bağımlılık diyagramını düzenleyin:

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Bağımlılık yönünü değiştirme veya kısıtlama|**Direction** özelliğini ayarlayın.|
|Yeni bağımlılıklar oluşturma|Bağımlılık **ve Çift** **Yönlü Bağımlılık araçlarını** kullanın.<br /><br /> Çoklu bağımlılıklar çizmek için araca çift tıklayın. Bitirdikten sonra İşaretçi aracını **seçin** veya **ESC tuşuna** basın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtme|Katmanın Yasak Ad Alanı Bağımlılıkları **özelliğine ad alanlarını** yazın. Ad alanlarını ayırmak için **noktalı virgül**( ; ) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtme|Katmanın Yasak Ad Alanları özelliğine **ad alanlarını** yazın. Ad alanlarını ayırmak için **noktalı virgül**( ; ) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarından birine ait olması gerektiğini belirtme|Katmanın Gerekli Ad Alanları **özelliğine ad alanını** yazın. Ad alanlarını ayırmak için **noktalı virgül**( ; ) kullanın.|

## <a name="change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a> Öğelerin diyagramda görünme şekillerini değiştirme
 Özelliklerini düzenleyerek katmanların boyutunu, şeklini, rengini ve konumunu veya bağımlılıkların rengini değiştirebilirsiniz.

## <a name="discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a> Kod haritasındaki desenleri ve bağımlılıkları bulma
 Bağımlılık diyagramları oluştururken kod eşlemeleri de **oluşturabilirsiniz.** Bu diyagramlar, siz kodu keşfedirken desenleri ve bağımlılıkları keşfetmeye yardımcı olabilir. Genellikle Çözüm Gezgini, Sınıf Görünümü, ad alanlarını ve sınıfları keşfetmek için Çözüm Gezgini, Sınıf Görünümü veya Object Browser kullanın. Kod eşlemeleri hakkında daha fazla bilgi için bkz:

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)

- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)

- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Mimari ve modelleme araçları için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)
- [Video: Mimari bağımlılıklarınızı gerçek zamanlı olarak doğrulama](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
- [Bağımlılık Diyagramları: Başvuru](../modeling/layer-diagrams-reference.md)
- [Bağımlılık Diyagramları: Yönergeler](../modeling/layer-diagrams-guidelines.md)
- [Bağımlılık diyagramları ile kod doğrulama](../modeling/validate-code-with-layer-diagrams.md)
- [Kodu görselleştirme](../modeling/visualize-code.md)
