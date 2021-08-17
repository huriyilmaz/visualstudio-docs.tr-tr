---
title: Kodunuz aracılığıyla bağımlılık diyagramları oluşturma
description: yazılım sisteminizin üst düzey, mantıksal mimarisini görselleştirmek için Visual Studio bir bağımlılık diyagramı oluşturmayı öğrenin.
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
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: dbb9cf7f9c3d024a28c0726ff54e0f0a5a981cd3d2242527706a5716de996a02
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231723"
---
# <a name="create-dependency-diagrams-from-your-code"></a>Kodunuz aracılığıyla bağımlılık diyagramları oluşturma

Yazılım sisteminizin üst düzey, mantıksal mimarisini görselleştirmek için Visual Studio bir *bağımlılık diyagramı* oluşturun. Kodunuzun bu tasarımla tutarlı kaldığından emin olmak için kodunuzu bir bağımlılık diyagramı ile doğrulayın. Visual C# ve Visual Basic projeleri için bağımlılık diyagramları oluşturabilirsiniz. hangi Visual Studio sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools).

![Bağımlılık diyagramı oluşturma](../modeling/media/layerdiagramvisualizecode.png)

bağımlılık diyagramı, Visual Studio çözüm öğelerini *katman* olarak adlandırılan mantıksal, soyut gruplar halinde düzenlemenize olanak tanır. Bu yapıların gerçekleştirdiği temel görevleri veya sistemin ana bileşenlerini açıklamak için katmanları kullanabilirsiniz. Her katman, daha ayrıntılı görevleri açıklayan başka katmanlar içerebilir. Katmanlar arasında amaçlanan veya var olan *bağımlılıkları* da belirtebilirsiniz. Oklar olarak temsil edilen bu bağımlılıklar, hangi katmanların diğer katmanlar tarafından temsil edilen işlevi kullanabileceğini veya kullanmakta olduğunu gösterir. Kodunun mimari denetimini sağlamak için diyagram üzerinde hedeflenen bağımlılıkları gösterin ve ardından kodu diyagrama karşı doğrulayın.

[Video: mimari bağımlılıklarınızı gerçek zamanlı olarak doğrulama](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="create-a-dependency-diagram"></a><a name="CreateDiagram"></a> Bağımlılık diyagramı oluşturma

Bağımlılık diyagramı oluşturmadan önce çözümünüzün bir modelleme projesine sahip olduğundan emin olun.

> [!IMPORTANT]
> Varolan bir bağımlılık diyagramını bir modelleme projesinden başka bir modelleme projesine veya çözümdeki başka bir yere eklemeyin, sürüklemeden veya kopyalamayın. Bu, diyagramı değiştirseniz bile orijinal diyagramdan yapılan başvuruları korur. Bu, katman doğrulamasının doğru çalışmasını da engeller ve siz diyagramı açmaya çalışırken kayıp öğeler veya başka hatalar gibi diğer sorunlara da neden olabilir.
>
> Bunun yerine, modelleme projesine yeni bir bağımlılık diyagramı ekleyin. Öğeleri kaynak diyagramdan yeni diyagrama kopyalayın. Hem modelleme projesini hem de yeni bağımlılık diyagramını kaydedin.

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>Modelleme projesine yeni bir bağımlılık diyagramı ekleme

> [!NOTE]
> .net Core projeleri için bağımlılık diyagramları Visual Studio 2019 sürüm 16,2 ' den başlayarak desteklenir.

1. **Mimari** menüsünde **Yeni bağımlılık diyagramı**' nı seçin.

2. **Şablonlar** altında **bağımlılık diyagramı**' nı seçin.

3. Diyagrama ad verin.

4. **modelleme Project ekle**' de, çözümünüzde var olan bir modelleme projesine gidin ve seçin.

     -veya-

     Çözüme yeni modelleme projesi eklemek için **Yeni modelleme projesi oluştur** ' a tıklayın.

    > [!NOTE]
    > Bağımlılık diyagramı bir modelleme projesi içinde bulunmalıdır. Bununla birlikte, bunu çözümün herhangi bir yerindeki öğelere bağlayabilirsiniz.

5. Hem modelleme projesini hem de bağımlılık diyagramını kaydettiğinizden emin olun.

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Bir kod eşlemesinden sürükleyip bırakma veya kopyalama ve yapıştırma

1. **Mimari** menüsünü kullanarak çözüm Için bir kod haritası oluşturun.

2. Yalnızca ürün kodunda bağımlılıkları zorlamak istiyorsanız Çözüm klasörlerini ve "test varlıklarını" kaldırmak için bir kod Haritası filtresi uygulamayı düşünün.

3. Oluşturulan kod haritasında, "dış" düğümü kaldırın veya ad alanı bağımlılıklarını zorlamak isteyip istemediğiniz ve gerekli olmayan derlemeleri kod eşlemesinden silmek istediğinize bağlı olarak, dış derlemeleri göstermek için genişletin.

4. **Mimari** menüsünü kullanarak çözüm için yeni bir bağımlılık diyagramı oluşturun

5. Kod eşlemesindeki tüm düğümleri seçin ( _CTRL_  +  _A_ kullanın veya tıklamadan, sürüklemeden ve serbest bırakmadan önce _SHIFT_ tuşuna basarak lastik bant seçimini kullanın.

6. Seçilen öğeleri sürükleyip bırakma veya kopyalama ve yapıştırma yeni bağımlılık doğrulama diyagramına.

7. Bu, geçerli uygulama mimarisini gösterir. Mimarinin ne olmasını istediğinize karar verin ve bağımlılık diyagramını uygun şekilde değiştirin.

![Kod eşlemesinden oluşturulan bağımlılık diyagramı](media/dependency-validation-01.png)

## <a name="create-layers-from-artifacts"></a><a name="CreateLayers"></a> Yapıtlardan katmanlar oluşturma
 Visual Studio çözüm öğelerinden projeler, kod dosyaları, ad alanları, sınıflar ve yöntemler gibi katmanlar oluşturabilirsiniz. Bu, katmanlar ve öğeler arasında otomatik olarak bağlantılar oluşturarak bunları katman doğrulama işlemine dahil eder.

 Katmanları Word belgeleri veya PowerPoint sunumları gibi doğrulamayı desteklemeyen öğelere de ekleyebilir ve böylece bir katmanı belirtimlerle veya planlarla ilişkilendirebilirsiniz. Katmanları birden fazla uygulama arasında paylaşılan projelerdeki dosyalara da bağlayabilirsiniz, ancak doğrulama işlemi "Katman 1" ve "Katman 2" gibi genel adlarla görünen bu katmanları içermez.

 Bağlı bir öğenin doğrulamayı destekleyip desteklemediğini görmek için **Katman Gezgini** ' ni açın ve öğenin **doğrulamayı destekler** özelliğini inceleyin. Bkz. [yapıtlara bağlantıları yönetme](#Managing).

|**Kime**|**Buradaki adımları izleyin**|
|-|-|
|Tek bir yapı için katman oluşturma|<ol><li>Öğeyi şu kaynaklardaki bağımlılık diyagramına sürükleyin:<br /><br /> <ul><li>**Çözüm Gezgini**<br /><br />         Örneğin, dosyaları veya projeleri sürükleyebilirsiniz.</li><li>Kod eşlemeleri<br /><br />         Bkz. [çözümlerinizde harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md) ve [uygulamalarınızda hata ayıklamak Için kod haritaları kullanın](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Sınıf görünümü** veya **nesne tarayıcısı**</li></ul><br />     Katman, diyagramda görünür ve yapıya bağlanır.</li><li>İlişkili kodun veya yapıların sorumluluklarını yansıtmak için katmanı yeniden adlandırın.</li></ol> **Önemli:**  İkili dosyaları bağımlılık diyagramına sürüklemek, başvurularını otomatik olarak modelleme projesine eklemez. Doğrulamak istediğiniz ikili dosyaları el ile modelleme projesine eklemeniz gerekir. **Modelleme projesine ikili dosyalar eklemek için** <ol><li>**Çözüm Gezgini**, modelleme projesi için kısayol menüsünü açın ve ardından **Varolan öğe Ekle**' yi seçin.</li><li>**Varolan öğe Ekle** iletişim kutusunda, ikili dosyalar ' a gidin, bunları seçin ve ardından **Tamam**' ı seçin.     İkili dosyalar modelleme projesinde görünür.</li><li>**Çözüm Gezgini**, eklediğiniz bir ikili dosyayı seçin ve ardından **Özellikler** penceresini açmak için **F4** tuşuna basın.</li><li>Her ikili dosyada, **derleme eylemi** özelliğini **doğrulanacak** olarak ayarlayın.</li></ol>|
|Seçilen tüm yapılar için tek bir katman oluşturma|Tüm yapıtları aynı anda bağımlılık diyagramına sürükleyin.<br /><br /> Katman diyagramda görünür ve tüm yapılara bağlıdır.|
|Seçilen her yapı için bir katman oluşturma|Tüm yapıtları aynı anda bağımlılık diyagramına sürüklerken **SHIFT** tuşuna basın ve basılı tutun. **Note:**  Bir dizi öğeyi seçmek için **SHIFT** tuşunu kullanırsanız, yapıtları seçtikten sonra anahtarı bırakın. Yapıları diyagrama sürüklerken tuşu tekrar basılı tutun. <br /><br /> Katman her yapı için diyagramda görünür ve her yapıya bağlanır.|
|Katmana yapı ekleme|Yapıyı katmana sürükleyin.|
|Bağlantısız bir katman oluşturma|**Araç kutusunda**, **bağımlılık diyagramı** bölümünü genişletin ve ardından bir **katmanı** bağımlılık diyagramına sürükleyin.<br /><br /> Çoklu katman eklemek için araca çift tıklayın. İşiniz bittiğinde **işaretçi** aracını seçin veya **ESC** tuşuna basın.<br /><br /> - veya -<br /><br /> Bağımlılık diyagramının kısayol menüsünü açın, **Ekle**' yi ve ardından **Katman**' ı seçin.|
|İç içe katmanlar oluşturma|Varolan katmanı başka bir katmanın üzerine sürükleyin.<br /><br /> - veya -<br /><br /> Katman için kısayol menüsünü açın, **Ekle**' yi ve ardından **Katman**' ı seçin.|
|Varolan iki veya daha fazla katmanı içeren yeni bir katman oluşturma|Katmanları seçin, seçiminizin kısayol menüsünü açın ve **Grup**' u seçin.|
|Katmanın rengini değiştirme|**Color** özelliğini istediğiniz renge ayarlayın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına ait olmaması gerektiğini belirtme|Katmanın **yasak ad alanları** özelliğindeki ad alanlarını yazın. Ad alanlarını ayırmak için noktalı virgül (**;**) kullanın.|
|Bir katman ile ilişkili yapıların belirli ad alanlarına bağlı olamayacağını belirtme|Katmanın **yasak ad alanı bağımlılıkları** özelliğindeki ad alanlarını yazın. Ad alanlarını ayırmak için noktalı virgül (**;**) kullanın.|
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

## <a name="reverse-engineer-existing-dependencies"></a><a name="Discovering"></a> Mevcut bağımlılıklarda tersine mühendislik uygulama
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
 Bağımlılık diyagramları oluştururken kod eşlemeleri de **oluşturabilirsiniz.** Bu diyagramlar, siz kodu keşfedirken desenleri ve bağımlılıkları keşfetmeye yardımcı olabilir. Genellikle Çözüm Gezgini, Sınıf Görünümü ve sınıfları keşfetmek için Çözüm Gezgini, Sınıf Görünümü veya Object Browser kullanın. Kod eşlemeleri hakkında daha fazla bilgi için bkz:

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
