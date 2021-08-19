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
ms.openlocfilehash: d4968cd181a05cdfabce5eb3ae772afe42423291
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047965"
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
> C# veya Visual Basic projeler için, kod eşlemesi başlatma veya mevcut kod haritasına öğe ekleme seçenekleri daha azdır. Örneğin, bir C++ projesinin metin düzenleyicisinde bir nesneye sağ tıklar ve bir kod eşlemesi eklersiniz. Ancak, tek tek kod öğelerini veya dosyalarını Çözüm Gezgini **,** **Sınıf Görünümü** ve Object Browser'dan **sürükleyip bırakın.**

## <a name="prerequisites"></a>Önkoşullar

Kod Eşlemesi'Visual Studio için önce [Kod Eşlemesi **ve Canlı** Bağımlılık Doğrulama **bileşenlerini** yükleyin](install-architecture-tools.md)

Kod eşlemeleri oluşturmak ve düzenlemek için bir **Visual Studio Enterprise gerekir.** Ancak Visual Studio Community Professional sürümlerinde Enterprise diyagramları açabilirsiniz ancak düzenleyemezsiniz.

> [!NOTE]
> Visual Studio Enterprise'de oluşturulan haritaları Visual Studio Professional diğer kullanıcılarla paylaşmadan önce, haritadaki tüm öğelerin (gizli öğeler, genişletilmiş gruplar ve gruplar arası bağlantılar gibi) görünür olduğundan emin olun.

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
   > Yeşil bir bağlantı görüyorsanız, bu yalnızca devralma ilişkisi olduğu anlamına geliyor olabilir. Yöntem çağrıları da olabilir, ancak bunlar devralma ilişkisi tarafından gizlenir. Belirli bağlantı türlerini görmek için Filtreler bölmesindeki  onay kutularını kullanarak ilgilendiğiniz türleri gizleyebilirsiniz.

7. Bir öğe veya bağlantı hakkında daha fazla bilgi almak için bir araç ipucu görünene kadar işaretçiyi üzerine sürükleyin. Bu, kod öğesinin ayrıntılarını veya bağlantının temsil ettiği kategorileri gösterir.

   ![bir ilişkinin kategorilerini gösterme](../modeling/media/codemapsshowlinkcatgories.png)

8. Toplama bağlantısıyla temsil edilen öğeleri ve bağımlılıkları incelemek için önce bağlantıyı seçin ve ardından kısayol menüsünü açın. Katkıda **Bulunan Bağlantıları Göster 'i** (veya Yeni Kod **Haritasında Katkıda Bulunan Bağlantıları Göster) seçin.** Bu, bağlantının her iki ucundaki grupları genişletiyor ve yalnızca bağlantıya katılan öğeleri ve bağımlılıkları gösteriyor.

9. Haritanın belirli bölümlerine odaklanmak için ilgilendiğiniz öğeleri kaldırmaya devam edersiniz. Örneğin, sınıf ve üye görünümünün detayını görmek için Filtreler bölmesindeki tüm ad alanı düğümlerini **filtrelemeniz** gerekir.

   ![Sınıf ve üye düzeyine inerek](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Karmaşık bir çözüm haritasına odaklanmanın bir diğer yolu da mevcut bir haritadan seçilen öğeleri içeren yeni bir harita oluşturmaktır. Odaklanmak istediğiniz öğeleri seçerken **Ctrl** tuşunu basılı tutun, kısayol menüsünü açın ve Seçim **menüsünden Yeni Graph'yi seçin.**

    ![Seçilen öğeleri yeni bir kod haritasında gösterme](../modeling/media/codemapsshowonnewmap.png)

11. İçeren bağlam yeni haritaya iletir. Filtreler bölmesini kullanarak Çözüm Klasörlerini ve görmek istemeyebilirsiniz diğer kapsayıcıları **gizleyebilirsiniz.**

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

1. Uygulama araç **Çözüm Gezgini,** Kod **Haritasında Göster'i seçin** ![ Yeni Graph Seçili Düğümlerden Oluştur ](../modeling/media/createnewgraphfromselectedbutton.gif) Düğmesi. Veya bir veya bir öğe grubunun kısayol menüsünü açın ve Kod Haritasında **Göster'i seçin.**

   Ayrıca **Çözüm Gezgini**, **sınıf görünümü** veya **nesne tarayıcısı** öğeleri [Yeni](#add-a-code-map) veya varolan bir kod haritasına sürükleyebilirsiniz. Öğelerinizin üst hiyerarşisini dahil etmek için, öğeleri sürüklerken **CTRL** tuşuna basın ve basılı tutun ya da varsayılan eylemi belirtmek için kod Haritası araç çubuğundaki **üst öğeleri dahil et** düğmesini kullanın. derleme dosyalarını, **Windows gezgini** gibi Visual Studio dışından da sürükleyebilirsiniz.

   > [!NOTE]
   > birden çok uygulama genelinde paylaşılan bir projeden (Windows Phone veya Microsoft Store gibi) öğeler eklediğinizde, bu öğeler geçerli etkin uygulama projesiyle haritada görüntülenir. Bağlamı başka bir uygulama projesi olarak değiştirirseniz ve paylaşılan projeden daha fazla öğe eklerseniz, bu öğeler yeni etkin olan uygulama projesiyle görünür. Eşleme üzerinde bir öğeyle gerçekleştirdiğiniz işlemler, yalnızca aynı bağlamı paylaşılan öğeler için geçerlidir.

3. Eşleme, seçili öğeleri kapsayan derlemeler içinde gösterir.

   ![Haritada gruplar olarak gösterilen seçili öğeler](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Öğeleri araştırmak için bunları genişletin. Fare işaretçisini bir öğenin üzerine taşıyın ve göründüğünde çift köşeli ayraç (aşağı ok) simgesine tıklayın.

   ![Kod haritasında bir düğümü genişletme](../modeling/media/dependencygraph_containment.png)

   Tüm öğeleri genişletmek için, **CTRL** + **A**'yı kullanarak bunları seçin, sonra haritanın kısayol menüsünü açın ve **Grup**  >  **Genişlet**' i seçin. Ancak, tüm grupların genişletilmesi kullanılamaz bir eşleme veya bellek sorunları oluşturursa, bu seçenek kullanılamaz.

5. İlgilendiğiniz öğeleri genişletmeye devam edin, gerekirse sınıf ve üye düzeyine doğru bir şekilde geçin.

   ![Grupları sınıfa ve üye düzeyine Genişlet](../modeling/media/codemapsexpandtoclassandmember.png)

   Koddaki, ancak haritada görünmeyen üyeleri görmek için,  ![ ](../modeling/media/dependencygraph_deletednodesicon.png) bir grubun sol üst köşesindeki tekrar al Children Icon tekrar al Children simgesine tıklayın.

6. Haritadaki öğelerle ilgili daha fazla öğe görmek için, bir tane seçin ve kod Haritası araç çubuğunda **ilgili öğe göster** ' i seçin, ardından haritaya eklenecek ilgili öğelerin türünü seçin. Alternatif olarak, bir veya daha fazla öğe seçin, kısayol menüsünü açın ve ardından haritaya eklenecek ilgili öğelerin türünün **göster** seçeneğini seçin. Örnek:

    Bir **derleme** için şunları seçin:

    |Seçenek|Açıklama|
    |-|-|
    |**Bu başvuruların derlemelerini göster**|Bu derlemenin başvurduğu derlemeleri ekleyin. Dış derlemeler **dışlar** grubunda görünür.|
    |**Buna başvuran derlemeleri göster**|Çözümde bu derlemeye başvuran derlemeleri ekleyin.|

    Bir **ad alanı** için, görünür değilse, **içerilen derlemeyi göster**' i seçin.

    Bir **sınıf** veya **arabirim** için şunları seçin:

    |Seçenek|Açıklama|
    |-|-|
    |**Temel türleri göster**|Bir sınıf için taban sınıfı ve uygulanan arabirimleri ekleyin.<br /><br /> Bir arabirim için temel arabirimleri ekleyin.|
    |**Türetilmiş türleri göster**|Bir sınıf için türetilmiş sınıfları ekleyin.<br /><br /> Bir arabirim için türetilmiş arabirimleri ve uygulama sınıflarını veya yapılarını ekleyin.|
    |**Bu başvuru türlerini göster**|Tüm sınıfları ve bu sınıfın kullandığı üyeleri ekleyin.|
    |**Buna başvuran türleri göster**|Tüm sınıfları ve bu sınıfı kullanan üyelerini ekleyin.|
    |**Içerilen ad alanını göster**|Üst ad alanını ekleyin.|
    |**Kapsayan ad alanını ve derlemeyi göster**|Üst kapsayıcı hiyerarşisini ekleyin.|
    |**Tüm temel türleri göster**|Yinelemeli olarak taban sınıf veya arabirim hiyerarşisi ekleyin.|
    |**Tüm türetilmiş türleri göster**|Bir sınıf için tüm türetilmiş sınıfları yinelemeli olarak ekleyin.<br /><br /> Bir arabirim için türetilmiş tüm arabirimleri ve uygulama sınıflarını veya yapılarını yinelemeli olarak ekleyin.|

     Bir **Yöntem** için şunları seçin:

    |Seçenek|Açıklama|
    |-|-|
    |**Bu çağrıların yöntemlerini göster**|Bu yöntemin çağırdığı yöntemleri ekleyin.|
    |**Bu başvuruların alanlarını göster**|Bu yöntemin başvurduğu alanları ekleyin.|
    |**Kapsayan türü göster**|Üst türü ekleyin.|
    |**Kapsayan türü, ad alanını ve derlemeyi göster**|Üst kapsayıcı hiyerarşisini ekleyin.|
    |**Geçersiz kılınan yöntemleri göster**|Diğer yöntemleri geçersiz kılan veya bir arabirimin yöntemini uygulayan bir yöntem için geçersiz kılınan taban sınıflardaki tüm soyut ya da sanal yöntemleri ve varsa arabirimin uygulanan yöntemini ekleyin.|

     Bir **alan** veya **özellik** için şunları seçin:

    |Seçenek|Açıklama|
    |-|-|
    |**Kapsayan türü göster**|Üst türü ekleyin.|
    |**Kapsayan türü, ad alanını ve derlemeyi göster**|Üst kapsayıcı hiyerarşisini ekleyin.|

    ![Bu üye tarafından çağrılan yöntemleri göster](../modeling/media/codemapsshowrelatedmethods.png)

7. Haritada ilişkiler gösterilmektedir. Bu örnekte, eşleme yöntemi tarafından çağrılan yöntemleri `Find` ve çözüm veya dışarıdan konumunu gösterir.

   ![Kod haritasında belirli bağımlılıkları göster](../modeling/media/codemapsspecificdependenciesintro.png)

8. Haritayı basitleştirmek ve tek tek bölümlere odaklanmak için, kod Haritası araç çubuğunda **Filtreler** ' i seçin ve yalnızca ilgilendiğiniz düğümlerin ve bağlantıların türlerini seçin. Örneğin, çözüm klasörlerinin, derlemelerin ve ad alanlarının görüntülenmesini devre dışı bırakın.

   ![Ekranı basitleştirmek için Filtre bölmesini kullanın](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod haritalarını paylaşma](share-code-maps.md)
- [C++ için kod eşlemeleri oluşturma](code-maps-for-cpp.md)
- [Kod Haritası performansını iyileştirme](code-maps-performance.md)
- [Video: Visual Studio 2015 kod haritaları ile koddan tasarımı anlama](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Video: Visual Studio 2015 kod haritaları ile koddan tasarımı anlama](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Kod eşlemelerine göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
