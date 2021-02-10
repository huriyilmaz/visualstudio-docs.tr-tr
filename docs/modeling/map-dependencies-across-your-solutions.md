---
title: Kod eşlemeleri
description: Kod eşlemelerinin dosya ve kod satırları arasında okuma yapmadan nasıl bir araya oturduğunu görmenizi nasıl yardımcı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9723fd44aedf4950b99a49b62d421230b43d55fc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946533"
---
# <a name="map-dependencies-with-code-maps"></a>Bağımlılıkları kod eşlemeleriyle eşleyin

Kod Haritası oluşturarak kodunuzun içindeki bağımlılıkları görselleştirebilirsiniz. Kod haritaları, kodun dosyalar ve kod satırları arasında okuma yapmadan nasıl bir araya oturduğunu görmenizi sağlamaya yardımcı olur.

![Visual Studio 'da kod eşlemeleriyle bağımlılıkları görüntüleme](../modeling/media/codemapsmainintro.png)

Kod haritaları oluşturmak ve düzenlemek için Visual Studio Enterprise sürümüne ihtiyacınız vardır. Visual Studio Community ve Professional sürümlerinde, Enterprise Edition 'da oluşturulan diyagramları açabilir, ancak düzenleyemezsiniz.

> [!NOTE]
> Visual Studio Enterprise içinde oluşturulan haritaları, Visual Studio Professional kullanan kullanıcılarla paylaşmadan önce, haritadaki tüm öğelerin (gizli öğeler, genişletilmiş gruplar ve çapraz grup bağlantıları gibi) göründüğünden emin olun.

Bu dillerdeki kod bağımlılıklarını eşleyebilirsiniz:

- Visual C# veya çözüm veya derlemelerde Visual Basic (*. dll* veya *. exe*)

- Visual C++ projelerinde yerel veya yönetilen C veya C++ kodu, üst bilgi dosyaları (*. h* veya `#include` ) ya da ikili dosyalar

- X + + projeleri ve Microsoft Dynamics AX için .NET modüllerinden oluşturulan derlemeler

> [!NOTE]
> C# veya Visual Basic dışındaki projeler için, bir kod eşlemesi başlatmak veya varolan bir kod eşlemesine öğe eklemek için daha az seçenek vardır. Örneğin, bir C++ projesinin metin düzenleyicisinde bir nesneye sağ tıklayıp bir kod haritasına ekleyebilirsiniz. Ancak, **Çözüm Gezgini**, **sınıf görünümü** ve **nesne tarayıcısı** bağımsız kod öğelerini veya dosyalarını sürükleyip bırakabilirsiniz.

## <a name="install-code-map-and-live-dependency-validation"></a>Kod haritasını ve canlı bağımlılık doğrulamasını yükler

Visual Studio 'da bir kod haritası oluşturmak için önce **kod haritasını** ve **canlı bağımlılık doğrulama** bileşenlerini yüklemeniz gerekir:

1. **Visual Studio yükleyicisi** açın. Windows Başlat menüsünden veya Visual Studio içinde **Araçlar**  >  **Al araçlar ve Özellikler**' i seçerek açabilirsiniz.

1. **Ayrı bileşenler** sekmesini seçin.

1. **Kod araçları** bölümüne gidin ve **kod Haritası** ve **canlı bağımlılık doğrulaması**' nı seçin.

   ![Visual Studio Yükleyicisi 'de kod Haritası ve canlı bağımlılık doğrulama bileşenleri](media/modeling-components.png)

1. **Değiştir**'i seçin.

   **Kod Haritası** ve **canlı bağımlılık doğrulama** bileşenleri yüklemeye başlar. Visual Studio 'Yu kapatmanız istenebilir.

## <a name="add-a-code-map"></a>Kod Eşlemesi Ekle

Derleme başvuruları, dosyalar ve klasörler de dahil olmak üzere boş bir kod Haritası oluşturabilir ve öğeleri üzerine sürükleyebilirsiniz veya çözümünüzün tümü veya bir kısmı için bir kod Haritası oluşturabilirsiniz.

Boş bir kod eşlemesi eklemek için:

1. **Çözüm Gezgini**' de, en üst düzey çözüm Düğümünüzün kısayol menüsünü açın.   >  **Yeni öğe** Ekle ' yi seçin.

2. **Yeni öğe Ekle** iletişim kutusunda, **yüklü** altında **genel** kategorisini seçin.

3. **Yönlendirilmiş grafik belgesi (. dgml)** şablonunu seçin ve ardından **Ekle**' yi seçin.

   > [!TIP]
   > Bu şablon alfabetik görüntülenmeyebilir, bu nedenle listede görmüyorsanız şablon listesinin en altına gidin.

   Çözümünüzün **Çözüm öğeleri** klasöründe boş bir harita görüntülenir.

Benzer şekilde, **mimari**  >  **Yeni kod eşlemesi** veya **Dosya**  >  **Yeni**  >  **Dosya dosyası** seçerek çözümünüze eklemeden yeni bir kod eşleme dosyası oluşturabilirsiniz.

## <a name="generate-a-code-map-for-your-solution"></a>Çözümünüz için bir kod Haritası oluşturma

Çözümünüzdeki tüm bağımlılıkları görmek için:

1. Menü çubuğunda, **mimari**  >  **çözüm için kod Haritası Oluştur**' u seçin. Kodunuz son kez derlenmeden bu yana değiştirilmediyse,   >  bunun yerine **Yapı olmadan çözüm için kod Haritası üret** ' i seçebilirsiniz.

   ![Kod Haritası komutu oluştur](../modeling/media/codemapsarchitecturemenu.png)

   Üst düzey derlemeleri ve bunlar arasındaki toplanmış bağlantıları gösteren bir harita oluşturulur. Toplama bağlantısı ne kadar geniş olursa, temsil ettiği daha fazla bağımlılıklardır.

2. Proje türü simgelerinin listesini (örneğin, test, Web ve telefon Projesi), kod öğelerini (sınıflar, Yöntemler ve özellikler gibi) ve ilişki türlerini (örneğin, devralır, Implements ve çağrılar) göstermek veya gizlemek için kod Haritası araç çubuğundaki **gösterge** düğmesini kullanın.

   ![Derlemelerin en üst düzey bağımlılık grafiği](../modeling/media/dependencygraph_toplevelassemblies.png)

   Bu örnek çözüm, Çözüm klasörlerini (**testler** ve **Bileşenler**), test projelerini, Web projelerini ve derlemeleri içerir. Varsayılan olarak, tüm kapsama ilişkileri *Grup* olarak görünür ve bu, genişletebilir ve daraltabilirsiniz. **Dışlar** grubu, platform bağımlılıkları da dahil olmak üzere çözümünüzün dışındaki her şeyi içerir. Dış derlemeler yalnızca kullanılan öğeleri gösterir. Varsayılan olarak, sistem tabanlı türler, dağınıklığı azaltmak için haritada gizlidir.

3. Haritanın detayına gitmek için, projeleri ve derlemeleri temsil eden grupları genişletin. Tüm düğümleri seçmek için **CTRL + A** tuşlarına basarak her şeyi genişletebilir ve ardından **Grup**' u seçerek kısayol menüsünden ' i **genişletin** .

   ![Kod eşlemesindeki tüm grupları genişletme](../modeling/media/codemapsexpandallgroups.png)

4. Ancak bu, büyük bir çözüm için yararlı olmayabilir. Aslında, karmaşık çözümler için bellek sınırlamaları tüm grupları genişletmesinin engellenmesini sağlayabilir. Bunun yerine, tek bir düğümün içini görmek için genişletin. Fare işaretçinizi düğümün üzerine taşıyın ve göründüğünde köşeli çift ayraca (aşağı ok) tıklayın.

   ![Kod haritasında düğüm genişletme](../modeling/media/dependencygraph_containment.png)

   Ya da öğeyi seçip artı tuşuna () basarak klavyeyi kullanın **+** . Daha derin kod düzeylerini araştırmak için ad alanları, türler ve Üyeler için de aynısını yapın.

   > [!TIP]
   > Fare, klavye ve dokunma kullanarak kod eşlemeleriyle çalışma hakkında daha fazla ayrıntı için bkz. [kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md).

5. Haritayı basitleştirmek ve tek tek bölümlere odaklanmak için, kod Haritası araç çubuğunda **Filtreler** ' i seçin ve yalnızca ilgilendiğiniz düğümlerin ve bağlantıların türlerini seçin. Örneğin, tüm çözüm klasörünü ve derleme kapsayıcılarını gizleyebilirsiniz.

   ![Kapsayıcıları filtreleyerek eşlemeyi basitleştirme](../modeling/media/codemapsfilterfoldersassemblies.png)

   Ayrıca, temel çözüm kodunu etkilemeden haritalardan ayrı grupları ve öğeleri gizleyerek veya kaldırarak Haritayı basitleştirebilirsiniz.

6. Öğeler arasındaki ilişkileri görmek için haritada seçin. Bağlantıların renkleri, **gösterge** bölmesinde gösterildiği gibi ilişki türlerini gösterir.

   ![Çözümlerinizi genelinde bağımlılıkları görüntüleme](../modeling/media/codemapsmainintro.png)

   Bu örnekte, mor bağlantılar çağrılardır, noktalı bağlantılar başvurudur ve açık mavi bağlantıları alan erişimdir. Yeşil bağlantılar devralma yapabilir veya birden fazla ilişki türü (veya *kategorisi*) gösteren *Birleşik bağlantılar* olabilir.

   > [!TIP]
   > Yeşil bir bağlantı görürseniz yalnızca bir devralma ilişkisi olduğu anlamına gelebilir. Yöntem çağrıları da olabilir, ancak bunlar devralma ilişkisi tarafından gizlenir. Belirli bağlantı türlerini görmek için, ilgilendiğiniz türleri gizlemek için **Filtreler** bölmesindeki onay kutularını kullanın.

7. Bir öğe veya bağlantı hakkında daha fazla bilgi edinmek için, bir araç ipucu görünene kadar işaretçiyi en üstüne taşıyın. Bu, bir kod öğesinin ayrıntılarını veya bir bağlantının temsil ettiği kategorileri gösterir.

   ![İlişki kategorilerini göster](../modeling/media/codemapsshowlinkcatgories.png)

8. Bir toplama bağlantısıyla temsil edilen öğeleri ve bağımlılıkları incelemek için, önce bağlantıyı seçin ve ardından kısayol menüsünü açın. **Katkıda bulunan bağlantıları göster** ' i seçin (veya **Yeni kod haritasında katkıda bulunan bağlantıları göster**). Bu,, bağlantının her iki ucunda da grupları genişletir ve yalnızca bağlantıya katılan öğe ve bağımlılıkları gösterir.

9. Haritanın belirli bölümlerine odaklanmak için, ilgilendiğiniz öğeleri kaldırmaya devam edebilirsiniz. Örneğin, sınıf ve üye görünümü detayına gitmek için **Filtreler** bölmesindeki tüm ad alanı düğümlerini filtrelemeniz yeterlidir.

   ![Sınıf ve üye düzeyinde detaya gitme](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Karmaşık bir çözüm eşlemesine odaklanmak için başka bir yol da var olan bir haritadan seçili öğeleri içeren yeni bir eşleme oluşturmak. Odaklanmak istediğiniz öğeleri seçerken **CTRL** tuşunu basılı tutun, kısayol menüsünü açın ve **seçimden yeni grafik**' i seçin.

    ![Seçili öğeleri yeni kod haritasında göster](../modeling/media/codemapsshowonnewmap.png)

11. İçeren bağlam, yeni haritaya taşınır. **Filtre** bölmesini kullanarak görmek Istemediğiniz Çözüm klasörlerini ve diğer kapsayıcıları gizleyin.

    ![Görünümü basitleştirmek için kapsayıcıları filtreleyin](../modeling/media/codemapsexpandnewgroups.png)

12. İlişkileri görüntülemek için grupları genişletin ve haritadaki öğeleri seçin.

    ![İlişkileri görüntülemek için öğeleri seçin](../modeling/media/codemapsviewnewrelationships.png)

Ayrıca bkz:

- [Kod eşlemelerine göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Çözümleyici çalıştırarak](../modeling/find-potential-problems-using-code-map-analyzers.md) kodunuzda olası sorunları bulma

## <a name="view-specific-dependencies-in-a-code-map"></a>Kod haritasında belirli bağımlılıkları görüntüleme

Bekleyen değişikliklerle bazı dosyalarda gerçekleştirilecek bir kod incelemesinin olduğunu varsayalım. Bu değişikliklerle ilgili bağımlılıkları görmek için, bu dosyalardan bir kod Haritası oluşturabilirsiniz.

   ![Kod haritasında belirli bağımlılıkları göster](../modeling/media/codemapsspecificdependenciesintro.png)

1. **Çözüm Gezgini**, eşlemek istediğiniz projeleri, derleme başvurularını, klasörleri, dosyaları, türleri veya üyeleri seçin.

   ![Eşlemek istediğiniz öğeleri seçin](../modeling/media/codemapsselectinsolutionexplorer.png)

1. **Çözüm Gezgini** araç çubuğunda, **kod eşlemesinde göster** ' i seçerek ![ seçili düğümlerden yeni grafik oluştur düğmesini seçin ](../modeling/media/createnewgraphfromselectedbutton.gif) . Ya da bir grup öğe için kısayol menüsünü açın ve **kod eşlemesinde göster '** i seçin.

   Ayrıca **Çözüm Gezgini**, **sınıf görünümü** veya **nesne tarayıcısı** öğeleri [Yeni](#add-a-code-map) veya varolan bir kod haritasına sürükleyebilirsiniz. Öğelerinizin üst hiyerarşisini dahil etmek için, öğeleri sürüklerken **CTRL** tuşuna basın ve basılı tutun ya da varsayılan eylemi belirtmek için kod Haritası araç çubuğundaki **üst öğeleri dahil et** düğmesini kullanın. Ayrıca, derleme dosyalarını **Windows Gezgini** gibi Visual Studio 'nun dışından da sürükleyebilirsiniz.

   > [!NOTE]
   > Birden çok uygulama genelinde paylaşılan bir projeden (Windows Phone veya Microsoft Store gibi) öğeler eklediğinizde, bu öğeler geçerli etkin uygulama projesiyle haritada görüntülenir. Bağlamı başka bir uygulama projesi olarak değiştirirseniz ve paylaşılan projeden daha fazla öğe eklerseniz, bu öğeler yeni etkin olan uygulama projesiyle görünür. Eşleme üzerinde bir öğeyle gerçekleştirdiğiniz işlemler, yalnızca aynı bağlamı paylaşılan öğeler için geçerlidir.

3. Eşleme, seçili öğeleri kapsayan derlemeler içinde gösterir.

   ![Haritada gruplar olarak gösterilen seçili öğeler](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Öğeleri araştırmak için bunları genişletin. Fare işaretçisini bir öğenin üzerine taşıyın ve göründüğünde çift köşeli ayraç (aşağı ok) simgesine tıklayın.

   ![Kod haritasında bir düğümü genişletme](../modeling/media/dependencygraph_containment.png)

   Tüm öğeleri genişletmek için, **CTRL** + **A**'yı kullanarak bunları seçin, sonra haritanın kısayol menüsünü açın ve **Grup**  >  **Genişlet**' i seçin. Ancak, tüm grupların genişletilmesi kullanılamaz bir eşleme veya bellek sorunları oluşturursa, bu seçenek kullanılamaz.

5. İlgilendiğiniz öğeleri genişletmeye devam edin, gerekirse sınıf ve üye düzeyine doğru bir şekilde geçin.

   ![Grupları sınıfa ve üye düzeyine Genişlet](../modeling/media/codemapsexpandtoclassandmember.png)

   Koddaki, ancak haritada görünmeyen üyeleri görmek için,  ![ ](../modeling/media/dependencygraph_deletednodesicon.png) bir grubun sol üst köşesindeki tekrar al Children Icon tekrar al Children simgesine tıklayın.

6. Haritadaki öğelerle ilgili daha fazla öğe görmek için, bir tane seçin ve kod Haritası araç çubuğunda **ilgili öğe göster** ' i seçin, ardından haritaya eklenecek ilgili öğelerin türünü seçin. Alternatif olarak, bir veya daha fazla öğe seçin, kısayol menüsünü açın ve ardından haritaya eklenecek ilgili öğelerin türünün **göster** seçeneğini seçin. Örneğin:

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

- [Video: Visual Studio 2015 kod haritaları ile koddan tasarımı anlama](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Kod eşlemelerine göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)
- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
