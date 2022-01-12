---
title: Kod eşlemeleri ile bağımlılıkları görselleştirme
description: Kod haritalarının, dosyaları ve kod satırlarını okumadan kodun nasıl bir araya sığduğunu görmenize nasıl yardımcı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/16/2021
ms.topic: how-to
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 49cce1da3473f4f5f6490edd1702007cc7ece265
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517504"
---
# <a name="map-dependencies-with-code-maps"></a>Bağımlılıkları kod eşlemeleriyle eşleme

Bu makalede kod eşlemeleri ile kodunuz genelinde bağımlılıkları görselleştirmeyi öğrenirsiniz.

## <a name="what-are-code-maps"></a>Kod eşlemeleri nedir?

Kod Visual Studio, dosya ve kod satırlarını okumadan program kodunuzun nasıl uyum içinde olduğunu daha hızlı bir şekilde görmenizi sağlar.  Bu haritalarla kodunuzda yapısını ve bağımlılıklarını, nasıl güncelleştireceğini ve önerilen değişikliklerin maliyetini tahmin etmek gibi organizasyonları ve ilişkileri kodunuzla birlikte görebilirsiniz.

![Kod eşlemeleriyle bağımlılıkları Visual Studio](../modeling/media/codemapsmainintro.png)

Kod bağımlılıklarını şu dillerde eşlersiniz:

- Bir çözümde veya Visual Basic Visual C# veya.dll *veya* *.exe*)

- Projelerde, üst bilgi dosyalarında (*.h* veya ) Visual C++ veya ikili dosyalarda yerel veya yönetilen C++ `#include` kodu

- Microsoft Dynamics AX için .NET modüllerinden yapılan X++ projeleri ve derlemeleri

> [!NOTE]
> C# veya Visual Basic projeler için, kod eşlemesi başlatma veya mevcut kod haritasına öğe ekleme seçenekleri daha azdır. Örneğin, bir C++ projesinin metin düzenleyicisinde bir nesneye sağ tıklar ve bir kod eşlemesi eklersiniz. Ancak, tek tek kod öğelerini veya dosyalarını Çözüm Gezgini **,** **Sınıf Görünümü** ve **Object Browser'dan sürükleyip bırakın.**

## <a name="prerequisites"></a>Önkoşullar

Kod Eşlemesi'Visual Studio için önce [Kod Eşlemesi **ve Canlı** Bağımlılık Doğrulama **bileşenlerini** yükleyin](install-architecture-tools.md)

Kod eşlemeleri oluşturmak ve düzenlemek için Visual Studio Enterprise **gerekir.** Ancak Visual Studio Community Professional sürümlerinde Enterprise diyagramları açabilirsiniz ancak düzenleyemezsiniz.

> [!NOTE]
> Visual Studio Enterprise'da oluşturulan haritaları Visual Studio Professional diğer kullanıcılarla paylaşmadan önce, haritadaki tüm öğelerin (gizli öğeler, genişletilmiş gruplar ve gruplar arası bağlantılar gibi) görünür olduğundan emin olun.

## <a name="add-a-code-map"></a>Kod haritası ekleme

Derleme başvuruları, dosyalar ve klasörler de dahil olmak üzere boş bir kod haritası oluşturabilir ve öğeleri buna sürükleyebilirsiniz ya da çözüme yönelik bir kod haritası oluşturabilirsiniz.

Boş bir kod eşlemesi eklemek için:

1. Bu **Çözüm Gezgini** üst düzey çözüm düğümünün kısayol menüsünü açın. Yeni **Öğe**  >  **Ekle'yi seçin.**

2. Yeni Öğe **Ekle iletişim** kutusunun Yüklü **altında Genel** **kategorisini** seçin.

3. **Directed Graph Document(.dgml) şablonunu** ve ardından Ekle'yi **seçin.**

   > [!TIP]
   > Bu şablon alfabetik olarak görünmeyebilirsiniz, bu nedenle görmüyorsanız sayfayı aşağı kaydırarak şablon listesinin en altına kaydırın.

   Çözüm öğenizin Çözüm Öğeleri klasöründe boş **bir harita** görüntülenir.

Benzer şekilde, Mimari Yeni Kod Eşlemesi veya Dosya Yeni Dosya seçeneğini belirterek bunu çözümünüze eklemeden yeni bir kod  >  **eşleme**   >  **dosyası**  >  **oluşturabilirsiniz.**

Daha fazla bilgi edinin:
- [Kod haritalarını paylaşma](share-code-maps.md)
- [C++ için kod eşlemeleri oluşturma](code-maps-for-cpp.md)
- [Kod eşlemesi performansını geliştirme](code-maps-performance.md)

## <a name="generate-a-code-map-for-your-solution"></a>Çözümünüz için kod haritası oluşturma

Çözümünüzde tüm bağımlılıkları görmek için:

1. Menü çubuğunda Çözüm için Mimari Kod **Haritası**  >  **Oluştur'a tıklayın.** Kodunuz en son oluşturmandan sonra değişmemişse, Bunun yerine Mimari Oluşturmadan Çözüm Için Kod Haritası  >  **Oluştur'a tıklayın.**

   ![Kod eşlemesi komutu oluşturma](../modeling/media/codemapsarchitecturemenu.png)

   Üst düzey derlemeleri ve bu derlemeler arasındaki toplu bağlantıları gösteren bir harita oluşturulur. Toplama bağlantısı ne kadar geniş ise temsil ettiği bağımlılıklar o kadar fazladır.

2. Proje **türü** simgelerinin (Test, Web ve Telefon Project gibi), kod öğelerinin (Sınıflar, Yöntemler ve Özellikler gibi) ve ilişki türlerinin (Devralan, Uygulananlar ve Çağrılar gibi) listesini göstermek veya gizlemek için kod haritası araç çubuğundaki Gösterge düğmesini kullanın.

   ![Derlemelerin en üst düzey bağımlılık grafiği](../modeling/media/dependencygraph_toplevelassemblies.png)

   Bu örnek çözüm Çözüm Klasörleri ( Testler **ve** **Bileşenler),** Test Projelerini, Web Projelerini ve derlemeleri içerir. Varsayılan olarak, tüm içerme ilişkileri gruplar olarak *görünür ve* bunu genişleterek daraltın. **Externals grubu,** platform bağımlılıkları dahil olmak üzere çözümünüz dışındaki her şeyi içerir. Dış derlemeler yalnızca kullanılan öğeleri gösterir. Sistem temel türleri varsayılan olarak dağınıklığı azaltmak için haritada gizlenir.

3. Haritada detaya inecek şekilde, projeleri ve derlemeleri temsil eden grupları genişletin. Tüm düğümleri seçmek için **CTRL+A tuşlarına** basarak ve ardından kısayol menüsünden **Grupla**, Genişlet'i **seçerek her** şeyi genişletebilirsiniz.

   ![Kod haritasındaki tüm grupları genişletme](../modeling/media/codemapsexpandallgroups.png)

4. Ancak, bu büyük bir çözüm için kullanışlı olabilir. Aslında, karmaşık çözümler için bellek sınırlamaları tüm grupları genişletmeyi önlenebilir. Bunun yerine, tek bir düğümün içinde görmek için genişletin. Fare işaretçinizi düğümün üst kısmında hareket ettirin ve göründüğünde köşeli çift ayraç (aşağı ok) işaretine tıklayın.

   ![Kod haritasındaki düğümü genişletme](../modeling/media/dependencygraph_containment.png)

   Veya öğeyi seçerek ve ardından artı tuşuna () basarak klavyeyi **+** kullanın. Daha derin kod düzeylerini keşfetmek için ad alanları, türler ve üyeler için de aynı şeyi kullanın.

   > [!TIP]
   > Fare, klavye ve dokunma kullanarak kod eşlemeleriyle çalışma hakkında daha fazla bilgi için bkz. Kod [eşlemelerini göz atma ve yeniden düzenleme.](../modeling/browse-and-rearrange-code-maps.md)

5. Haritayı basitleştirmek ve tek tek  parçalara odaklanmak için kod haritası araç çubuğunda Filtreler'i seçin ve yalnızca ilgilendiğiniz düğüm türlerini ve bağlantıları seçin. Örneğin, tüm Çözüm Klasörü ve Derleme kapsayıcılarını gizleyebilirsiniz.

   ![Kapsayıcıları filtreleerek haritayı basitleştirme](../modeling/media/codemapsfilterfoldersassemblies.png)

   Ayrıca, temel çözüm kodunu etkilemeden tek tek grupları ve öğeleri gizleerek veya kaldırarak haritayı basitleştirebilirsiniz.

6. Öğeler arasındaki ilişkileri görmek için bunları haritada seçin. Bağlantıların renkleri, Gösterge bölmesinde gösterildiği gibi ilişki **türlerini** gösterir.

   ![Çözümleriniz genelinde bağımlılıkları görüntüleme](../modeling/media/codemapsmainintro.png)

   Bu örnekte mor bağlantılar çağrı, noktalı bağlantılar başvuru, açık mavi bağlantılar ise alan erişimidir. Yeşil bağlantılar devralma olabilir veya birden fazla ilişki *türünü* (veya kategorisini) gösteren toplu bağlantılar *olabilir.*

   > [!TIP]
   > Yeşil bir bağlantı görüyorsanız yalnızca devralma ilişkisi olduğu anlamına geliyor olabilir. Yöntem çağrıları da olabilir, ancak bunlar devralma ilişkisi tarafından gizlenir. Belirli bağlantı türlerini görmek için Filtreler bölmesindeki  onay kutularını kullanarak ilgilendiğiniz türleri gizleyebilirsiniz.

7. Bir öğe veya bağlantı hakkında daha fazla bilgi almak için bir araç ipucu görünene kadar işaretçiyi üzerine sürükleyin. Bu, kod öğesinin ayrıntılarını veya bağlantının temsil ettiği kategorileri gösterir.

   ![bir ilişkinin kategorilerini gösterme](../modeling/media/codemapsshowlinkcatgories.png)

8. Toplama bağlantısıyla temsil edilen öğeleri ve bağımlılıkları incelemek için önce bağlantıyı seçin ve ardından kısayol menüsünü açın. Katkıda **Bulunan Bağlantıları Göster 'i** (veya Yeni Kod **Haritasında Katkıda Bulunan Bağlantıları Göster) seçin.** Bu, bağlantının her iki ucundaki grupları genişletiyor ve yalnızca bağlantıya katılan öğeleri ve bağımlılıkları gösteriyor.

9. Haritanın belirli bölümlerine odaklanmak için ilgilendiğiniz öğeleri kaldırmaya devam edersiniz. Örneğin, sınıf ve üye görünümünün detayını görmek için Filtreler bölmesindeki tüm ad alanı düğümlerini **filtrelemeniz** gerekir.

   ![Sınıf ve üye düzeyine inerek](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Karmaşık bir çözüm haritasına odaklanmanın bir diğer yolu da mevcut bir haritadan seçilen öğeleri içeren yeni bir harita oluşturmaktır. Odaklanmak istediğiniz öğeleri seçerken **Ctrl** tuşunu basılı tutun, kısayol menüsünü açın ve Seçim **menüsünden Yeni Graph'yi seçin.**

    ![Seçilen öğeleri yeni bir kod haritasında gösterme](../modeling/media/codemapsshowonnewmap.png)

11. İçeren bağlam yeni haritaya iletir. Filtreler bölmesini kullanarak Çözüm Klasörlerini ve görmek istemeyebilirsiniz diğer **kapsayıcıları** gizleyebilirsiniz.

    ![Görünümü basitleştirmek için kapsayıcıları filtreleme](../modeling/media/codemapsexpandnewgroups.png)

12. İlişkileri görüntülemek için grupları genişletin ve haritadaki öğeleri seçin.

    ![İlişkileri görüntülemek için öğeleri seçme](../modeling/media/codemapsviewnewrelationships.png)

Ayrıca bkz:

- [Kod eşlemelerine göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Çözümleyici çalıştırarak kodunda [olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-dependencies"></a>Bağımlılıkları görüntüleme

Bekleyen değişikliklere sahip bazı dosyalarda gerçekleştirmek için bir kod incelemeniz olduğunu varsayalım. Bu değişikliklerde bağımlılıkları görmek için bu dosyalardan bir kod eşlemesi oluşturabilirsiniz.

   ![Kod haritasında belirli bağımlılıkları gösterme](../modeling/media/codemapsspecificdependenciesintro.png)

1. Bu **Çözüm Gezgini,** eşlemek istediğiniz projeleri, derleme başvurularını, klasörleri, dosyaları, türleri veya üyeleri seçin.

   ![Eşlemek istediğiniz öğeleri seçin](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Uygulama araç **Çözüm Gezgini,** Kod **Haritasında Göster** Yeni Oluştur'Graph ![ Düğümlerden Düğmesi'ne ](../modeling/media/createnewgraphfromselectedbutton.gif) tıklayın. Veya bir veya bir öğe grubunun kısayol menüsünü açın ve Kod Haritasında **Göster'i seçin.**

   Öğeleri , veya Çözüm Gezgini **Sınıf Görünümü** Tarayıcı'dan yeni **veya** mevcut bir kod [haritasına](#add-a-code-map) sürükleyebilirsiniz.  Öğeleriniz için üst hiyerarşiyi dahil etmek üzere öğeleri sürüklerken **Ctrl**  tuşuna basın ve basılı tutun veya varsayılan eylemi belirtmek için kod haritası araç çubuğundaki Üst Öğeleri Dahil Tut düğmesini kullanın. Derleme dosyalarını, örneğin Windows **Gezgini'Visual Studio dışından sürükleyebilirsiniz.**

   > [!NOTE]
   > Windows Phone veya Microsoft Store gibi birden çok uygulama arasında paylaşılan bir projeden öğe eklerken, bu öğeler o anda etkin olan uygulama projesiyle haritada görünür. Bağlamı başka bir uygulama projesi olarak değiştirirseniz ve paylaşılan projeden daha fazla öğe eklerseniz, bu öğeler yeni etkin olan uygulama projesiyle görünür. Eşleme üzerinde bir öğeyle gerçekleştirdiğiniz işlemler, yalnızca aynı bağlamı paylaşılan öğeler için geçerlidir.

3. Harita, seçilen öğeleri içeren derlemeler içinde gösterir.

   ![Haritada grup olarak gösterilen seçili öğeler](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Öğeleri keşfetmek için genişletin. Fare işaretçisini bir öğenin üzerine hareket ettirin, ardından göründüğünde köşeli çift ayraç (aşağı ok) simgesine tıklayın.

   ![Kod haritasındaki düğümü genişletme](../modeling/media/dependencygraph_containment.png)

   Tüm öğeleri genişletmek için **Ctrl** A tuşlarını kullanarak + **seçin,** ardından haritanın kısayol menüsünü açın ve Genişlet'i **Grupla'yı**  >  **seçin.** Ancak, tüm grupların genişletilmesi kullanılamaz bir eşleme veya bellek sorunları oluşturursa bu seçenek kullanılamaz.

5. İlgilenilen öğeleri gerekirse sınıf ve üye düzeyine kadar genişletmeye devam eder.

   ![Grupları sınıf ve üye düzeyine genişletme](../modeling/media/codemapsexpandtoclassandmember.png)

   Kodda yer alan ancak haritada görünmeen üyeleri görmek için, grubun sol üst köşesindeki AltLarı Yeniden Başlat simgesiNesneleri Geri Ekle  ![ ](../modeling/media/dependencygraph_deletednodesicon.png) Simgesine tıklayın.

6. Haritadaki öğelerle ilgili daha fazla öğe görmek  için birini seçin ve kod haritası araç çubuğunda İlişkilileri Göster'i seçin, sonra da haritaya eklemek istediğiniz ilgili öğe türünü seçin. Alternatif olarak, bir veya daha fazla öğe seçin,  kısayol menüsünü açın ve ardından haritaya eklemek istediğiniz ilgili öğe türü için Göster seçeneğini belirleyin. Örneğin:

    Bir derleme **için** şunları seçin:

    |Seçenek|Açıklama|
    |-|-|
    |**Derlemeleri Göster Bu Başvurular**|Bu derlemenin başvurduğu derlemeleri ekleyin. Dış derlemeler Dışlar **grubunda** görünür.|
    |**Buna Başvuran Derlemeleri Göster**|Çözümde bu derlemeye başvuran derlemeleri ekleyin.|

    Bir ad **alanı** için, **görünür durumda değilse** İçeren Derlemeyi Göster'i seçin.

    Bir sınıf **veya** arabirim **için** şunları seçin:

    |Seçenek|Açıklama|
    |-|-|
    |**Temel Türleri Göster**|Bir sınıf için taban sınıfı ve uygulanan arabirimleri ekleyin.<br /><br /> Bir arabirim için temel arabirimleri ekleyin.|
    |**Türetilmiş Türleri Göster**|Bir sınıf için türetilmiş sınıfları ekleyin.<br /><br /> Bir arabirim için türetilmiş arabirimleri ve uygulama sınıflarını veya yapılarını ekleyin.|
    |**Türleri Göster Bu Başvurular**|Tüm sınıfları ve bu sınıfın kullandığı üyeleri ekleyin.|
    |**Buna Başvuran Türleri Göster**|Tüm sınıfları ve bu sınıfı kullanan üyelerini ekleyin.|
    |**İçeren Ad Alanını Göster**|Üst ad alanını ekleyin.|
    |**İçeren Ad Alanını ve Derlemeyi Göster**|Üst kapsayıcı hiyerarşisini ekleyin.|
    |**Tüm Temel Türleri Göster**|Yinelemeli olarak taban sınıf veya arabirim hiyerarşisi ekleyin.|
    |**Türetilen Tüm Türleri Göster**|Bir sınıf için tüm türetilmiş sınıfları yinelemeli olarak ekleyin.<br /><br /> Bir arabirim için türetilmiş tüm arabirimleri ve uygulama sınıflarını veya yapılarını yinelemeli olarak ekleyin.|

     Bir yöntem **için** şunları seçin:

    |Seçenek|Açıklama|
    |-|-|
    |**Bu Çağrıların Yöntemlerini Göster**|Bu yöntemin çağırdığı yöntemleri ekleyin.|
    |**Alanları Göster Bu Başvurular**|Bu yöntemin başvurduğu alanları ekleyin.|
    |**İçeren Türü Göster**|Üst türü ekleyin.|
    |**İçeren Türü, Ad Alanını ve Derlemeyi Göster**|Üst kapsayıcı hiyerarşisini ekleyin.|
    |**Geçersiz Kılınan Yöntemleri Göster**|Diğer yöntemleri geçersiz kılan veya bir arabirimin yöntemini uygulayan bir yöntem için geçersiz kılınan taban sınıflardaki tüm soyut ya da sanal yöntemleri ve varsa arabirimin uygulanan yöntemini ekleyin.|

     Bir alan **veya** özellik **için** şunları seçin:

    |Seçenek|Açıklama|
    |-|-|
    |**İçeren Türü Göster**|Üst türü ekleyin.|
    |**İçeren Türü, Ad Alanını ve Derlemeyi Göster**|Üst kapsayıcı hiyerarşisini ekleyin.|

    ![Bu üye tarafından çağrılan yöntemleri göster](../modeling/media/codemapsshowrelatedmethods.png)

7. Haritada ilişkiler gösterilir. Bu örnekte harita, yöntemi tarafından çağrılan yöntemleri ve çözümde veya harici `Find` olarak konumlarını gösterir.

   ![Kod haritasında belirli bağımlılıkları gösterme](../modeling/media/codemapsspecificdependenciesintro.png)

8. Haritayı basitleştirmek ve tek tek  parçalara odaklanmak için kod haritası araç çubuğunda Filtreler'i seçin ve yalnızca ilgilendiğiniz düğüm türlerini ve bağlantıları seçin. Örneğin, Çözüm Klasörleri, Derlemeler ve Ad Alanlarının görüntülemeyi kapatın.

   ![Ekranı basitleştirmek için Filtre bölmesini kullanma](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod haritalarını paylaşma](share-code-maps.md)
- [C++ için kod eşlemeleri oluşturma](code-maps-for-cpp.md)
- [Kod eşlemesi performansını geliştirme](code-maps-performance.md)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Kod eşlemelerine göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
