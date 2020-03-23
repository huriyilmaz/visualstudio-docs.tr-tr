---
title: Kod eşlemelerine göz atma ve bunları yeniden düzenleme
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e38308c5bb94028fa17e78740da2b0df2779447
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302968"
---
# <a name="browse-and-rearrange-code-maps"></a>Kod eşlemelerine göz atma ve bunları yeniden düzenleme

Öğeleri kod eşlemlerindeki yeniden düzenleyerek okumalarını ve performanslarını artırmalarını kolaylaştırın.

Bir çözümde temel kodu etkilemeden kod eşlemlerini özelleştirebilirsiniz. Bu, anahtar kod öğelerine odaklanmak veya kod la ilgili fikirleri iletmek istediğinizde yararlıdır. Örneğin, ilginç alanları vurgulamak için haritadaki kod öğelerini seçebilir ve filtreleyebilir, kod öğelerinin ve bağlantıların stilini değiştirebilir, kod öğelerini gizleyebilir veya silebilir ve özellikleri, kategorileri veya grupları kullanarak kod öğelerini düzenleyebilirsiniz.

 **Gereksinimler**

- Kod eşlemleri oluşturmak için Visual Studio Enterprise'a sahip olmalısınız.

- Visual Studio Professional'da kod eşlemlerini görüntüleyebilir ve kod eşlemlerinde sınırlı sayıda edinebilirsiniz.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a>Kod haritaları yla çalışmaya başlayın

Bir kod eşlemi oluşturun (daha fazla ayrıntı için [çözümlerinizde Harita bağımlılıklarına](../modeling/map-dependencies-across-your-solutions.md) bakın). Haritanın oluşturma işlemini bitirmesini beklemek istemiyorsanız, oluşturma işlemini durdurmak için istediğiniz zaman **İptal** bağlantısını tıklatın. Ancak, bunu yaparsanız tüm bağımlılıkların ve bağlantıların ayrıntılarını görmezsiniz.

Haritayı oluşturduktan sonra, kodunuzu gözden geçirmek için aşağıdaki ipuçlarını almaya başlayın:

- Koddaki doğal bağımlılık kümelerine bakın. Harita araç çubuğunda Düzen **,** Hızlı Kümeler Hızlı **Kümeler**![düğmesini grafik araç çubuğunda](../modeling/media/quickclustersicon.gif)seçin. Bkz. [Harita düzenini değiştir.](#Selecting)

     ![Bağımlılık grafiği &#45; Hızlı Kümeler düzeni](../modeling/media/dependencygraph_quickclusters.png)

- İlgili düğümleri gruplayarak haritayı daha küçük alanlara düzenleyin. Yalnızca otomatik olarak görünen gruplar arası bağımlılıkları görmek için bu grupları daraltın. [Bkz. Grup düğümleri.](#OrganizeGroups)

- Haritayı basitleştirmek ve ilgilendiğiniz düğüm türlerine veya bağlantılara odaklanmak için filtreleri kullanın. [Bkz. Filtre düğümleri ve bağlantılar.](#FilterNodes)

- Büyük haritaların performansını en üst düzeye çıkarın. Daha fazla bilgi için [çözümlerinizdeki harita bağımlılıklarına](../modeling/map-dependencies-across-your-solutions.md) bakın. Örneğin, Görsel Stüdyo'nun haritadaki öğeleri güncellediğinizde çözümünüzü yeniden oluşturmaması için harita araç çubuğunda **Atla Yapı'yı** açın.

## <a name="change-the-map-layout"></a><a name="Selecting"></a>Harita düzenini değiştirme

|**Hedef**|**Bu adımları gerçekleştirin**|
|-|-|
|Tüm harita için bağımlılık akışını belirli bir yönde düzenleyin. Bu, koddaki mimari katmanları görmenize yardımcı olabilir.|Harita araç çubuğunda **Düzen'i**seçin ve ardından:<br /><br /> -   **Üstte Altüstgrafik** ![düğmesi](../modeling/media/topbottomgraphbutton.gif)<br />-   **Aşağıdan Yukarıya Üst** ![grafik düğmesi](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Soldan Sağa** ![Sola, Sağa düzen düğmesi](../modeling/media/leftrightgraphbutton.gif)<br />-   **Sağdan Sola,** ![Soldan Grafik düğmesi](../modeling/media/rightleftgraphbutton.gif)|
|Kümelerin merkezinde en bağımlı düğümler ve bu kümelerin dışında en az bağımlı düğümleri ile koddaki doğal bağımlılık kümelerini görün.|Harita araç çubuğunda **Düzen'i**ve ardından grafik araç çubuğundaki](../modeling/media/quickclustersicon.gif) **Hızlı Kümeler**![Hızlı Kümeler düğmesini seçin.|
|Haritada bir veya daha fazla düğüm seçin.|Seçmek için düğümü n için tıklatın. Birden fazla düğümü seçmek veya seçmek için tıklatırken **CTRL'yi** basılı tutun.<br /><br /> Klavye: **TAB** tuşuna basın veya noktalı odak dikdörtgenini düğüme taşımak için ok tuşlarını kullanın ve seçmek için **SPACE** tuşuna basın. Düğümleri çok seçmek veya seçmek için **CTRL** + **SPACE** tuşuna basın.|
|Belirli düğümleri haritaüzerinde hareket ettirin.|Düğümleri hareket ettirecek şekilde sürükleyin. Düğümleri sürüklerken diğer düğümleri ve bağlantıları yoldan çıkarmak için **SHIFT** tuşuna basın ve basılı tutun.<br /><br /> Klavye: **CTRL** tuşuna basın ve ok tuşlarına basın.|
|Haritadaki diğer düğümlerden ve gruplardan bağımsız olarak bir grup içindeki düzeni değiştirin.|Bir düğüm seçin ve kısayol menüsünü açın. **Düzen'i** seçin ve bir düzen stili seçin.<br /><br /> - veya -<br /><br /> Bir düğüm seçin ve alt düğümleri göstermek için genişletin. Grup açılır araç çubuğunu göstermek için düğüm başlığını tıklatın ve grup![Bağımlılık grafiği&#45; grup araç](../modeling/media/dependencygraph_grouptoolbar.gif) çubuğu &#45; düzen **listesinin düzen stilini değiştir'i**açın. Ağaç düzenlerinden birini, **Hızlı Kümeleri**veya **Liste Görünümü'nü** (grubun içeriğini bir listeye düzenleyen) seçin.<br /><br /> Daha fazla ayrıntı için [Grup düğümlerine](#OrganizeGroups) bakın.|
|Haritadaki bir eylemi geri ala.|**CTRL** + **Z** tuşuna basın veya Visual Studio **Geri Ala** komutunu kullanın.|

## <a name="browse-the-map"></a><a name="Explore"></a>Haritaya göz atın

|**Hedef**|**Bu adımları gerçekleştirin**|
|-|-|
|Haritayı taz.yasla.|Fareyi kullanarak haritayı herhangi bir yöne sürükleyin.<br /><br /> - veya -<br /><br /> **SHIFT'i** basılı tutun ve yatay kaydırmak için fare tekerleğini döndürün. **SHIFT** + **CTRL'yi** basılı tutun ve yatay kaydırmak için fare tekerleğini döndürün.|
|Haritayı yakınlaştırın veya uzaklaştırın.|Fare tekerleğidöndürül.<br /><br /> - veya -<br /><br /> Kod haritası araç çubuğundaki **Yakınlaştırma** açılır listesini kullanın.<br /><br /> - veya -<br /><br /> Klavye kısayollarını kullanın. Yakınlaştırmak için **CTRL + SHIFT + tuşuna basın.** (dönem). Uzaklaştırmak için **CTRL + SHIFT + ,** (virgül) tuşuna basın.|
|Fareyi kullanarak belirli bir alanı yakınlaştırın.|İlgilendiğiniz alanın etrafına dikdörtgen çizerken sağ fare düğmesini basılı tutun.|
|Haritayı yeniden boyutlandırın ve penceresine sığdırın.|Kod eşlemi araç çubuğundaki **Yakınlaştırma** listesinden **Yakınlaştırma'yı yakınlaştır'ı** seçin.<br /><br /> - veya -<br /><br /> Harita eşaraç çubuğundaki harita araç](../modeling/media/almcodemapzoomicon.png) çubuğundaki simge yakınlaştırma simgesine ![ **sığdırmak için Yakınlaştır'ı** tıklatın. Klavye: **CTRL + 0** (sıfır) tuşuna basın.|
|Haritada adına göre bir düğüm bulun. **İpucu:**  Bu yalnızca haritadaki öğeler için çalışır. Çözümünüzdeki ancak haritada olmayan öğeleri bulmak için, **bunları Çözüm Gezgini'nde**bulun ve ardından haritaya sürükleyin. (Seçiminizi sürükleyin veya **Çözüm Gezgini** araç çubuğunda **Kod Haritasında Göster'i**tıklatın).|1. **Haritanın** ![sağ üst köşesindeki](../modeling/media/almcodemapfindicon.png) arama kutusunu göstermek için kod haritası araç çubuğundaki (Klavye: **CTRL + F)** üzerindeki harita araç çubuğundaki bul simgesini seçin.<br />2. Öğe adını yazın ve **Return** tuşuna basın veya "büyüteç" simgesine tıklayın. Aramanızla eşleşen ilk öğe haritada seçili görünür.<br />3. Aramanızı özelleştirmek için açılır listeyi açın ve bir arama seçeneği seçin. Seçenekler **Sonraki'ni Bul**, **Önceki'yi Bul**ve **Tümünü Seç'** tir. Ardından arama metin kutusunun yanındaki ilgili düğmeyi tıklatın.<br />     ![Arama seçenekleri&#45;aşağı listeye bırakın](../modeling/media/almcodemapssearchdropdown.png)<br />     Alternatif olarak, klavyeyi kullanın: önceki eşleşen düğümü seçmek için bir sonraki eşleşen düğümü veya **SHIFT + F3'ü** seçmek için **F3** tuşuna basın.<br />4. Arama metin kutusunun altındaki simgelere tıklayarak arama terimlerinin nasıl işleneceğini belirten seçeneklerden birini seçin.<br />     ![Eşleşim seçeneklerini ara](../modeling/media/almcodemapssearchmatchicons.png)<br />     Seçenekler, soldan sağa, büyük/küçük harf duyarlı eşleştirme, yalnızca tam sözcükleri eşleştirme, .NET normal ifade sözdizimini kullanmak, kapalı öğelere eşleşmeleri göstermek için grupları otomatik olarak genişletmektir. **Önemli:**  Yalnızca bu gruplar daha önce genişletildiyse, daraltılmış gruplardaki eşleşmeleri bulmak için arama kutusunu kullanabilirsiniz. Bu eşleşmeleri bulmak ve üst gruplarını otomatik olarak genişletmek için arama kutusunun altındaki bu seçeneği seçin.|
|Seçili olmayan tüm düğümleri seçin.|Seçili düğümlerin kısayol menüsünü açın. **Seç**, **Seçimi Tersine**Çevir'i seçin.|
|Seçili düğümlere bağlantı veren ek düğümleri seçin.|Seçili düğümlerin kısayol menüsünü açın. **Seç'i** ve bunlardan birini seçin:<br /><br /> - Doğrudan seçili düğüme bağlantı veren ek düğümleri seçmek için **Gelen Bağımlılıklar'ı**seçin.<br />- Doğrudan seçili düğümden bağlantı veren ek düğümleri seçmek için **Giden Bağımlılıklar'ı**seçin.<br />- Seçili düğüme doğrudan ve seçili düğümden bağlantı veren ek düğümleri seçmek için **Her Ikisi'yi**seçin.<br />- Seçili düğüme ve bağlantıdan gelen tüm düğümleri seçmek için **Bağlı Alt Grafik'i**seçin.<br />- Seçili düğümün tüm alt çocuklarını seçmek için **Çocuklar'ı**seçin.|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a>Filtre düğümleri ve bağlantılar

|**Hedef**|**Bu adımları gerçekleştirin**|
|-|-|
|Filtreler bölmesini göster veya gizle.|Kod haritası araç çubuğundaki **Filtreler** düğmesini seçin. **Filtreler** bölmesi varsayılan olarak **Solution Explorer'da**sekmeli bir sayfa olarak görüntülenir.|
|Haritada gösterilen düğüm türlerini filtreleyin.|Filtreler bölmesindeki **Kod Öğeleri** listesindeki onay kutularını ayarlayın veya temizleyin.|
|Haritada gösterilen bağlantı türlerini filtreleyin.|Filtreler bölmesinde **İlişkiler** listesindeki onay kutularını ayarlayın veya temizleyin.|
|Test proje düğümlerini haritada göster veya gizle.|Filtreler bölmesindeki **Çeşitli** listedeki **Test Varlıkları** onay kutusunu ayarlayın veya temizleyin.|

Haritanın Gösterge panelinde gösterilen simgeler, listedeki ayarları nızı yansıtır. Gösterge panelini göstermek veya gizlemek için, kod haritası araç çubuğundaki **Gösterge** düğmesini tıklatın.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a>Düğümleri ve bağlantıları inceleyin

Kod haritaları bu tür bağlantıları gösterir:

- Tek bir bağlantı iki düğüm arasındaki tek bir ilişkiyi temsil eder.

- Gruplar arası bağlantı, farklı gruplardaki iki düğüm arasındaki ilişkiyi temsil eder.

- Toplu bağlantı, iki grup arasında aynı yönde işaret eden tüm ilişkileri temsil eder.

> [!TIP]
> Varsayılan olarak, harita yalnızca seçili düğümler için çapraz grup bağlantılarını gösterir. Gruplar arasında toplu bağlantıları göstermek veya gizlemek için bu davranışı değiştirmek için, kod eşlemi araç çubuğunda **Düzen'i** tıklatın ve **Gelişmiş'i**seçin, ardından **Tüm Çapraz Grup Bağlantılarını Göster** veya Tüm Çapraz Grup **Bağlantılarını Gizle'yi**seçin. Daha fazla ayrıntı için [düğümleri ve bağlantıları gizle veya göster'](#HidingShowing) e bakın.

|**Hedef**|**Bu adımları gerçekleştirin**|
|-|-|
|Düğüm veya bağlantı hakkında daha fazla bilgi görün.|Fare işaretçisini bir araç ipucu görünene kadar düğümün veya bağlantının üstüne taşıyın.<br /><br /> Toplu bir bağlantı için araç ipucu, temsil ettiği tek tek bağımlılıkları listeler.<br /><br /> - veya -<br /><br /> Düğüm veya bağlantı için kısayol menüsünü açın. **Edit**seçin , **Özellikler**.|
|Bir grubun içeriğini gösterin veya gizleyin.|- Grubu genişletmek için düğüm için kısayol menüsünü açın ve **Grup**, **Genişlet'i**seçin.<br />     - veya -<br />     Köşeli ayraç (aşağı ok) düğmesi görünene kadar fare işaretçisini düğümün üstünde taşıyın. Grubu genişletmek için bu düğmeyi tıklatın. Klavye: seçili grubu genişletmek veya daraltmak**+** için **PLUS** tuşuna ( ) veya **MINUS** tuşuna ().**-**<br />- Bir grubu daraltmak için düğüm için kısayol menüsünü açın ve **Grup**, **Daralt**'ı seçin.<br />     - veya -<br />     Fare işaretçisini, köşeli ayraç (yukarı ok) düğmesi görünene kadar grubun üstünde taşıyın. Grubu daraltmak için bu düğmeyi tıklatın.<br />- Tüm grupları genişletmek için, tüm düğümleri seçmek için **CTRL** + **A** tuşuna basın. Harita için kısayol menüsünü açın ve **Grup**, **Genişlet'i**seçin. **Not:**      Tüm grupları genişletmek kullanılamaz bir eşlemi veya bellek sorunları oluşturuyorsa, bu komut kullanılamaz. Haritayı yalnızca önemsediğiniz ayrıntı düzeyine genişletmeniz önerilir.<br />- Tüm grupları daraltmak için düğüm veya harita için kısayol menüsünü açın. **Grup**seçin , **Tümünü Daralt**.|
|Ad alanı, tür veya üyenin kod tanımına bakın.|Düğüm için kısayol menüsünü açın ve **Tanıma Git'i**seçin.<br /><br /> -veya-<br /><br /> Düğümü çift tıklatın. Genişletilmiş gruplar için, grupüstle ilgili üstbilginin iki katına tıklayın.<br /><br /> -veya-<br /><br /> Düğümü seçin ve **F12 tuşuna**basın.<br /><br /> Örnek:<br /><br /> - Bir sınıf içeren bir ad alanı için, sınıfın kod dosyası o sınıfın tanımını göstermek için açılır. Diğer durumlarda, **Simge Yi bul sonuçları** penceresi kod dosyalarının listesini gösterir. **Not:**      Bu görevi Visual Basic ad alanında gerçekleştirdiğiniz zaman, ad alanının arkasındaki kod dosyası açılmaz. Bu sorun, Visual Basic ad alanı içeren seçili düğümler grubunda bu görevi gerçekleştirdiğiniz zaman da oluşur. Bu sorunu çözmek için ad alanının arkasındaki kod dosyasına el ile göz atın veya seçiminizden ad alanı düğümlerini atlayın.<br />- Bir sınıf veya kısmi sınıf için, sınıf tanımını göstermek için bu sınıfın kod dosyası açılır.<br />- Bir yöntem için, yöntem tanımını göstermek için ana sınıfın kod dosyası açılır.|
|Bağımlılıkları ve toplu bağlantıya katılan öğeleri inceleyin.|İlgilendiğiniz bağlantıları seçin ve seçiminiz için kısayol menüsünü açın. **Katkıda Bulunan Bağlantıları Göster'i** veya Yeni Kod **Haritasında Katkıda Bulunan Bağlantıları Göster'i**seçin.<br /><br /> Visual Studio, bağlantının her iki ucunda da grupları genişletir ve yalnızca bağlantıya katılan öğe ve bağımlılıkları gösterir. **Not:**  Kısmi gruplardaki öğeler arasındaki bağımlılıkları incelediğinizde, şu davranışı görebilirsiniz: <ul><li>Sınavınıza katılmayan öğelere bağlantılar, bu bağlantılar hala mevcut olsa bile haritadan kaybolur.</li><li>Kısmi bir gruptaki bir öğeye bağlantı incelediğinizi ve daha sonra aynı öğeye farklı bir bağlantıyı incelediğinizi varsayalım. İkinci muayeneniz sırasında, hedef kısmi grup sadece ilk muayenenizden bazı öğeleri gösterir. İlk sınavınıza katılmayan ancak ikinci sınava katılmayan bağlantılar ve hedef öğeler görünmez.</li></ul> Bir gruptan eksik öğeleri görmek için, **Çocukları**![Yeniden](../modeling/media/dependencygraph_deletednodesicon.png) Getir Simgesini seçin (bir grubun tüm üyelerinin haritada görünmediğini gösterir). Ayrıca eylemlerinizi geri almaya da çalışabilir (Klavye: **CTRL+Z**tuşuna basın) ve yeni bir haritadaki bağımlılıkları inceleyebilirsiniz.|
|Farklı gruplardaki birden çok düğümdeki bağımlılıkları inceleyin.|Tüm çocuklarını görebilmek için grupları genişletin. Çocukları da dahil olmak üzere ilginizi çeken tüm düğümleri seçin. Harita, seçili düğümler arasındaki çapraz grup bağlantılarını gösterir.<br /><br /> Bir gruptaki tüm düğümleri seçmek için **SHIFT** SHIFT ve sol fare düğmesine basArak grubun etrafına bir dikdörtgen çizin. Haritadaki tüm düğümleri seçmek için **CTRL**+**A tuşuna**basın. **İpucu:**  Her zaman çapraz grup bağlantılarını göstermek için harita araç çubuğunda **Düzen,** **Gelişmiş**, **Tüm Çapraz Grup Bağlantılarını Göster'i**seçin.|
|Düğümün veya bağlantının başvuruldığı öğelere bakın.|Düğüm için kısayol menüsünü açın ve **Tüm Başvuruları Bul'u**seçin. **Not:**  Bu, yalnızca eşin `Reference` .dgml dosyasındaki düğüm veya bağlantı için öznitelik ayarlandığında geçerlidir. Düğümlerden veya bağlantılardaki öğelere başvuru eklemek için, [DGML dosyalarını düzenleyerek kod eşlemlerini özelleştir'e](../modeling/customize-code-maps-by-editing-the-dgml-files.md)bakın.|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a>Düğümleri ve bağlantıları gizleme veya gösterme

Düğümlerin gizlenmesi, düzen algoritmasına katılmalarını engeller. Varsayılan olarak, çapraz grup bağlantıları gizlidir. Çapraz grup bağlantıları, düğümleri gruplar arasında bağlayan tek bağlantılardır. Gruplar daraltıldığında, harita tüm gruplar arası bağlantıları gruplar arasında tek bağlantılarhalinde toplar. Bir grubu genişlettiğinizde veya grup içindeki düğümleri seçtiğinizde, çapraz grup bağlantıları görünür ve o gruptaki bağımlılıkları gösterir.

> [!CAUTION]
> Visual Studio Enterprise'da oluşturulan bir haritayı Visual Studio Professional kullananlarla paylaşmadan önce, başkalarının görmesini istediğiniz düğümleri veya çapraz grup bağlantılarını gizlediğinden emin olun. Aksi takdirde, bu kullanıcılar bu öğelerin gizliliğini kaldıramayacaktır.

### <a name="to-hide-or-show-nodes"></a>Düğümleri gizlemek veya göstermek için

|**Hedef**|**Bu adımları gerçekleştirin**|
|-|-|
|Seçili düğümleri gizleyin.|1. Gizlemek istediğiniz düğümleri seçin.<br />2. Seçili düğümler veya harita için kısayol menüsünü açın. Seç ' **i**seçin , **Seçili Gizle**.|
|Seçilmemiş düğümleri gizleyin.|1. Görünür kalmasını istediğiniz düğümleri seçin.<br />2. Seçili düğümler veya harita için kısayol menüsünü açın. **Seç**, **Seçilmemiş Gizle'yi**seçin.|
|Gizli düğümleri göster.|- Bir grup içindeki tüm gizli düğümleri göstermek için, önce grubun genişletildiğinden emin olun. Kısayol menüsünü açın ve **Çocukları Seç'i** **seçin.**<br />     - veya -<br />     Grubun sol üst köşesindeki](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) **Unhide Children**![Unhide Çocuk Simgesi simgesini tıklatın (bu yalnızca gizli alt düğümler olduğunda görünür).<br />- Tüm gizli düğümleri göstermek için, harita veya düğüm için kısayol menüsünü açın ve **Tümünü** **Seç ,Tümünü Al**seçeneğini seçin.|

### <a name="to-hide-or-show-links"></a>Bağlantıları gizlemek veya göstermek için

|**Hedef**|**Harita araç çubuğunda Düzen, Gelişmiş'i seçin ve ardından**|
|-|-|
|Her zaman çapraz grup bağlantılarını göster.|**Tüm Çapraz Grup Bağlantılarını Göster.** Bu, gruplar arasında toplanmış bağlantıları gizler.|
|Grup lar arası bağlantıları her zaman gizleyin.|**Tüm Çapraz Grup Bağlantılarını Gizle**|
|Seçili düğümler için yalnızca grup lar arası bağlantıları gösterin.|**Seçili Düğümlerde Çapraz Grup Bağlantılarını Göster**|
|Tüm bağlantıları gizleyin.|**Tüm Bağlantıları Gizle**. Bağlantıları yeniden göstermek için, yukarıda listelenen seçeneklerden birini seçin.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a>Grup düğümleri

|**Hedef**|**Bu adımları gerçekleştirin**|
|-|-|
|Kapsayıcı düğümlerini grup düğümleri veya yaprak düğümleri olarak gösterin.|Kap düğümlerini yaprak düğümleri olarak göstermek için: düğümleri seçin, seçiminiz için kısayol menüsünü açın ve **Grup**, **Yaprakdönüştür'ü**seçin.<br /><br /> Kapsayıcı düğümlerini grup düğümleri olarak göstermek için: düğümleri seçin, seçiminiz için kısayol menüsünü açın ve **Grup,** **Gruba Dönüştür'ü**seçin.|
|Bir grubun içindeki düzeni değiştirin.|Grubu seçin, kısayol menüsünü açın, **Düzen'i**seçin ve istediğiniz düzen stilini seçin.<br /><br /> - veya -<br /><br /> 1. Grubu seçin ve genişletildiğinden emin olun.<br />2. Grup üstbilgisini yeniden tıklatın ve grup araç çubuğu görüntülenir.<br />     ![Bağımlılık grafiği &#45; grup araç çubuğu](../modeling/media/dependencygraph_group.png)<br />3. Grup listesi ![Bağımlılık **grafiğinin düzen stilini** &#45; grup](../modeling/media/dependencygraph_grouptoolbar.gif) araç çubuğu &#45;nu değiştir'i açın ve istediğiniz düzen stilini seçin.<br /><br /> **Liste Görünümü,** grubun üyelerini listeye yeniden düzenler. **Grafik Varsayılan,** grup düzenini eşvarsayılan düzene sıfırlar. Diğer seçenekler için [bkz.](#Selecting)|
|Gruba düğüm ekleyin.|Düğümü gruba sürükleyin.<br /><br /> Düğümü sürüklerken, Visual Studio düğümü hareket ettirdiğinizi gösteren bir gösterge görüntüler.<br /><br /> Düğümleri grubun dışına da sürükleyebilirsiniz.|
|Grup olmayan bir düğüme düğüm ekleyin.|Düğümü hedef düğüme sürükleyin. Herhangi bir hedef düğüme düğüm ekleyerek bir gruba dönüştürebilirsiniz.|
|Seçilen düğümleri grupla.|1. Gruplandırmak istediğiniz düğümleri seçin. Seçtiğiniz son düğümün üzerinde açılır araç çubuğu görünür.<br />     ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)<br />2. Araç çubuğunda, seçilen **düğümleri gruplandırın** (düğüm genişletilirse, dört simge yerine beş simge olacaktır). Yeni grubun adını yazın ve **Return**tuşuna basın.<br />     - veya -<br />     Gruplandırmak istediğiniz düğümleri seçin ve seçiminiz için kısayol menüsünü açın. **Grup**seçin , **Üst Grup Ekle,** yeni grup için adı yazın ve **Return**tuşuna basın.<br /><br /> Bir grubu yeniden adlandırabilirsiniz. Grup için kısayol menüsünü açın ve Visual Studio Properties penceresini açmak **için** **Özellikleri Edit'i**seçin. **Etiket** özelliğinde, grubu gerektiği gibi yeniden adlandırın.|
|Grupları kaldırın.|Kaldırmak istediğiniz grup veya grupları seçin. Seçiminiz için kısayol menüsünü açın ve **Grup**, **Grubu Kaldır'ı**seçin.|
|Düğümleri üst gruplarından kaldırın.|Taşımak istediğiniz düğümleri seçin. Seçiminiz için kısayol menüsünü açın ve **Grup**, **Üst Öğeyi Kaldır'ı**seçin. Bu, büyükanne ve büyükbabalarına veya büyükanne ve büyükbaba grubu yoksa grubun dışına kadar düğümleri kaldırır.<br /><br /> - veya -<br /><br /> Düğümleri seçin ve grubun dışına sürükleyin.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a>Düğümleri, bağlantıları ve açıklamaları ekleme, kaldırma veya yeniden adlandırma

Haritayı ayrıntıya almak veya basitleştirmek için haritaüzerinde daha fazla veya daha az öğe görüntüleyebilirsiniz. Öğeleri yeniden adlandırabilir ve öğelere yorum ekleyebilirsiniz.

> [!CAUTION]
> Visual Studio Enterprise kullanılarak oluşturulan bir haritayı Visual Professional kullananlarla paylaşmadan önce, başkalarının görmesini istediğiniz kod öğelerinin haritada görünür olduğundan emin olun. Aksi takdirde, bu kullanıcılar silinen kod öğelerini geri alamaz.

### <a name="add-a-node-for-a-code-element"></a>Kod öğesi için düğüm ekleme

|**Hedef**|**Bu adımları gerçekleştirin**|
|-|-|
|Geçerli fare işaretçisi konumunda yeni bir genel düğüm ekleyin.|1. Fare işaretçisini yeni kod öğesini koymak istediğiniz haritadaki yere taşıyın ve **Ekle'ye**basın.<br />     - veya -<br />     Harita için kısayol menüsünü açın ve **Edit**, **Ekle**, **Genel Düğüm**seçin.<br />2. Yeni düğümün adını yazın ve **Return**tuşuna basın.|
|Geçerli fare işaretçisi konumunda belirli bir kod öğesi düğümü türü ekleyin.|1. Fare işaretçisini yeni kod öğesini koymak istediğiniz yere taşıyın ve haritanın kısayol menüsünü açın.<br />2. **Edit,** **Ekle'yi**seçin ve istediğiniz düğüm türünü seçin.<br />3. Yeni düğümün adını yazın ve **Return**tuşuna basın.|
|Bir gruba genel veya belirli bir kod öğesi düğümü ekleyin.|1. Grup düğümünü seçin ve kısayol menüsünü açın.<br />2. **Edit,** **Ekle'yi**seçin ve istediğiniz düğüm türünü seçin.<br />3. Yeni düğümün adını yazın ve **Return**tuşuna basın.|
|Aynı türde yeni bir düğüm ekleyin ve varolan bir düğümden bağlantı.|1. Kod öğesini seçin. Üzerinde açılır araç çubuğu görünür.<br />     ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)<br />2. Araç çubuğunda, ikinci **simgeyi seçin Bu düğümle aynı kategoriye sahip bir düğüm oluşturun ve yeni bir bağlantı ekleyin.**<br />3. Yeni kod öğesini koymak için haritada bir yer seçin ve sol fare düğmesini tıklatın.<br />4. Yeni düğümün adını yazın ve **Return**tuşuna basın.|
|Odak noktası olan varolan bir kod öğesinden bağlı yeni bir genel düğüm ekleyin.|1. Klavyeyi kullanarak, bağlantı için kod öğesi odak (noktalı dikdörtgen) olana kadar **Sekme** tuşuna basın.<br />2. **Alt**+**Ekle tuşuna**basın.<br />3. Yeni düğümün adını yazın ve **Return**tuşuna basın.|
|Odak noktası olan varolan bir kod öğesine bağlantı veren yeni bir genel düğüm ekleyin.|1. Klavyeyi kullanarak, bağlantı için kod öğesi odak (noktalı dikdörtgen) olana kadar **Sekme** tuşuna basın.<br />2. **Alt**+**Shift**+**Ekle**tuşuna basın.<br />3. Yeni düğümün adını yazın ve **Return**tuşuna basın.|

|**Için kod öğeleri eklemek için**|**Bu adımları gerçekleştirin**|
|-|-|
|Çözümdeki kod öğeleri.|1. **Çözüm Gezgini'nde**kod öğesini bulun. Çözüm **Gezgini** arama kutusunu kullanın veya çözüme göz atın. **İpucu:**      Bir türe veya üyeye bağlı bağımlıları olan kod öğelerini bulmak için, **Çözüm Gezgini'ndeki**tür veya üye için kısayol menüsünü açın. Sizi ilgilendiren ilişkiyi seçin. **Çözüm Gezgini** yalnızca belirtilen bağımlılıkları olan kod öğelerini gösterir.<br />2. İlginizi çeken kod öğelerini harita yüzeyine sürükleyin. Kod öğelerini Sınıf Görünümü'nden veya Nesne Tarayıcısından da sürükleyebilirsiniz.<br />     - veya -<br />     **Çözüm Gezgini'nde,** eşleşmek istediğiniz kod öğelerini seçin. Ardından, **Çözüm Gezgini** araç **çubuğunda Kod Haritası'nda Göster'i**tıklatın.<br /><br /> Varsayılan olarak, yeni kod öğeleri için üst kapsayıcı hiyerarşisi haritada gösterilir. Bu davranışı değiştirmek için kod eşlemi araç çubuğundaki **Ebeveyn Ekle** düğmesini kullanın. Kapatıldığında, eşe yalnızca kod öğesi eklenir. Bu davranışı tek bir sürükleme ve bırakma eylemi için tersine çevirmek için, kod öğelerini eşmeye sürüklerken **CTRL** tuşuna basın ve basılı tutun.<br /><br /> Visual Studio, seçiminizdeki üst düzey kod öğeleri için kod öğeleri ekler. Kod öğesinin diğer kod öğelerini içerip içermediğini görmek için, fare işaretçisini kod öğesinin üstündeki köşeli ayraç (aşağı ok) görünecek şekilde hareket ettirin. Kod öğesini genişletmek için köşeli ayraç seçin. Tüm kod öğelerini genişletmek için tüm öğeleri seçmek için **CTRL**+**A** tuşuna basın, harita için kısayol menüsünü açın ve **Grup**, **Genişlet'i**seçin. Tüm grupları genişletmek kullanılamaz bir eş oluşturmaya veya bellek sorunlarının azlığına neden olacaksa, bu komut kullanılamaz.|
|Haritadaki kod öğeleriyle ilgili kod öğeleri.|Kod haritası araç çubuğundaki **İlgiliyi Göster** düğmesini tıklatın ve ilgilendiğiniz ilgili öğelerin türünü seçin.<br /><br /> - veya -<br /><br /> Kod öğesi için kısayol menüsünü açın. İlginizi çeken ilişkinin türüne bağlı olarak menüdeki **Göster ...** öğelerinden birini seçin. Örneğin, geçerli madde başvuruları, geçerli madde, temel ve sınıflar için türemiş türler, yöntem arayanlar ve içeren sınıflar, ad alanları ve derlemeler için başvuru öğeleri öğeleri görebilirsiniz.<br /><br /> Daha fazla bilgi için [bu konuya](../modeling/map-dependencies-across-your-solutions.md)bakın.|
|Derlenmiş .NET derlemeleri (.dll veya .exe) veya ikililer.|Derlemeleri veya ikilileri Visual Studio'nun dışından bir haritaya sürükleyin.<br /><br /> Windows Gezgini'nden veya Dosya Gezgini'nden yalnızca aynı Kullanıcı Erişim Denetimi (UAC) izinleri düzeyinde çalıştırıyorsanız sürükleyebilirsiniz. Örneğin, UAC açıksa ve Visual Studio'yu Yönetici, Windows Explorer veya File Explorer olarak çalıştırıyorsanız sürükleme işlemini engeller.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Varolan kod öğeleri arasında bağlantı ekleme

1. Kaynak kodu öğesini seçin. Kod öğesinin üzerinde bir araç çubuğu görüntülenir.

    ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)

2. Araç çubuğunda, ilk simgeyi seçin, **Bu düğümden sonraki netle tıkladığınız düğüme yeni bağlantı oluşturun.**

3. Hedef kod öğesini seçin. İki kod öğesi arasında bir bağlantı görüntülenir.

**Veya**

1. Haritadaki kaynak kod öğesini seçin.

2. Fare niz yüklüyse, fare işaretçisini haritanın sınırlarının dışına taşıyın.

3. Kod öğesinin kısayol menüsünü açın ve**Genel Bağlantı****Ekle'yi** >  **seçin.** > 

4. Bağlantının hedef kodu öğesini sekme ve seç.

5. **Enter**'a basın.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Haritada varolan bir düğüme açıklama ekleme

1. Kod öğesini seçin. Üstünde bir araç çubuğu görünür.

     ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)

2. Araç çubuğunda, üçüncü simgeyi seçin, **seçili düğüme yeni bir bağlantı içeren yeni bir açıklama düğümü oluşturun.**

     \-veya -

     Kod öğesi için kısayol menüsünü açın ve**Yeni Yorumu** **Edit'i** > seçin.

3. Açıklamalarınızı yazın. Yeni bir satıra yazmak için **Shift** + **Enter**tuşuna basın.

#### <a name="add-a-comment-to-the-map-itself"></a>Haritanın kendisine yorum ekleme

1. Harita için kısayol menüsünü açın ve**Yeni Yorumu** **Edit'i** > seçin.

2. Açıklamalarınızı yazın. Yeni bir satıra yazmak için **Shift** + **Enter**tuşuna basın.

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Kod öğesini veya bağlantıyı yeniden adlandır

1. Kod öğesini veya yeniden adlandırmak istediğiniz bağlantıyı seçin.

2. **F2**tuşuna basın veya kısayol menüsünü açın ve Yeniden > **Rename** **Adlandır'ı Edit'i**seçin.

3. Eşöğede edin kutusu göründüğünde, kod öğesini veya bağlantıyı yeniden adlandırın.

**Veya**

1. Kısayol menüsünü açın ve**Özellikleri** **Edit'i** > seçin.

2. Visual Studio Properties penceresinde **Etiket** özelliğini edin.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Kod öğesini veya bağlantıyı haritadan kaldırma

1. Kod öğesini veya bağlantısını seçin ve **Sil** tuşuna basın.

     \-veya -

     Kod öğesi veya bağlantı için kısayol menüsünü açın ve**Kaldır'ı** **Edit'i** > seçin.

2. Öğe veya bağlantı bir grubun parçasıysa, Grubun ![içinde Çocukları](../modeling/media/dependencygraph_deletednodesicon.png) **Yeniden Getir** düğmesi görüntülenir. Eksik öğeleri ve bağlantıları almak için bunu tıklatın.

- Temel kodu etkilemeden kod öğelerini ve bağlantıları haritadan kaldırabilirsiniz. Bunları sildiğinizde, tanımları DGML (.dgml) dosyasından kaldırılır.

- DGML'yi düzenleyerek, tanımlanmamış kod öğeleri ekleyerek veya Visual Studio'nun bazı önceki sürümlerini kullanarak oluşturulan haritalar bu özelliği desteklemez.

#### <a name="flag-a-code-element-for-follow-up"></a>İzleme için kod öğesini işaretleme

1. İzleme için işaretlemek istediğiniz kod öğesini veya bağlantıyı seçin.

2. Kısayol menüsünü açın ve**İzleme için Bayrağı** **Edit'i** > seçin.

- Varsayılan olarak, kod öğesi kırmızı bir arka plan kazanır. Uygun takip bilgileriyle yorum [eklemeyi](#AddComments) düşünün.

- Öğenin arka plan rengini değiştirin veya**Diğer Bayrak Renklerini** **Edit'i** > seçerek izleme bayrağını temizleyin.

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a>Kod öğesinin veya bağlantının stilini değiştirme

Önceden tanımlanmış simgeleri ve renkleri kullanarak kod öğeleri ve kod öğeleri ve bağlantıların renklerini değiştirebilirsiniz. Örneğin, belirli bir kategori ye veya özelliğe sahip kod öğelerini ve bağlantıları vurgulamak için bir renk seçebilirsiniz. Bu, haritanın belirli alanlarını belirlemenize ve bunlara odaklanmanıza olanak tanır. Haritanın .dgml dosyasını düzenleyerek özel simgeler ve renkler belirtebilirsiniz; bkz. [DGML dosyalarını düzenleyerek kod eşlemlerini özelleştirin.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Belirli bir kategori ye veya özelliğe sahip kod öğelerine veya bağlantılara önceden tanımlanmış bir renk veya simge uygulamak için

1. Harita araç çubuğunda **Gösterge'yi**seçin.

2. **Gösterge** kutusunda, kod öğesi kategorisinin veya özelliğinin listede zaten görünip görünmediğini görün.

3. Listede **+** kategori veya özellik yoksa, **Gösterge** kutusuna seçin, ardından **Düğüm Özelliği, Düğüm** **Kategorisi,** **Bağlantı Özelliği**veya **Bağlantı Kategorisi'ni**seçin. Ardından özelliği veya kategoriyi seçin. Kategori veya özellik artık **Gösterge** kutusunda görünür.

    > [!NOTE]
    > Bir kategori veya özellik oluşturmak ve bir kod öğesine özellik atamak için, haritanın .dgml dosyasını değiştirebilirsiniz; bkz. [DGML dosyalarını düzenleyerek kod eşlemlerini özelleştirin.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

4. **Gösterge** kutusunda, eklediğiniz veya değiştirmek istediğiniz kategori veya özelliğin yanındaki simgeyi tıklatın.

5. Değiştirmek istediğiniz stili seçmek için aşağıdaki tabloyu kullanın:

    |**Değiştirmek için**|**Seçin:**|
    |-|-|
    |Arka plan rengi|**Arka plan**|
    |Anahat rengi|**Kontur**|
    |Metin rengi (sonucu göstermek için "f" harfi görüntülenir)|**Ön plan**|
    |Simge|**Simgeler**|

     **Renk Kümesi Seçici** veya Simge Seti **Seçici** iletişim kutusu bir renk veya simge seçmeniz için görüntülenir.

6. Renk **Kümesi Seçici** veya **Simge Seti Seçici** iletişim kutusunda aşağıdakilerden birini yapın:

    |**Bir uygulamak için**|**Bu adımları gerçekleştirin**|
    |-|-|
    |Renk veya simgeler kümesi|Renk **Seç** (veya **simge)** **ayar** listesini açın. Bir renk veya simge kümesi seçin.|
    |Belirli renk veya simge|Kategori veya özellik değer listesini açın. Bir renk veya simge seçin.|

    > [!NOTE]
    > **Gösterge** kutusunda stilleri yeniden düzenleyebilir, silebilir veya geçici olarak devre dışı bırakabilirsiniz. Bkz. [Legend kutusunu Edit](#ModifyLegend).

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a>Gösterge kutusunu edin

**Gösterge** kutusunda stilleri yeniden düzenleyebilir, silebilir veya geçici olarak devre dışı bırakabilirsiniz:

1. **Gösterge** kutusunda bir stil için kısayol menüsünü açın.

2. Aşağıdaki görevlerden birini uygulayın:

    |**Hedef**|**Seçin:**|
    |-|-|
    |Kod öğesini devre dışı bırakma|**Devre Dışı Bırak**|
    |Kod öğesini silme|**Sil**|
    |Stili yukarı taşıyın|**Yukarı Taşı**|
    |Kod öğesini aşağı taşıma|**Aşağı Taşı**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a>Stilleri bir haritadan diğerine kopyalama

1. **Gösterge** kutusunun kaynak haritada göründüğünden emin olun. Görünür değilse, harita araç çubuğunda **Gösterge'yi**tıklatın.

2. **Legend** kutusunun kısayol menüsünü açın. **Kopya Göstergesi'ni**seçin.

3. Efsaneyi hedef haritaya yapıştırın.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a>Kod eşlemlerini birleştirme

Kod öğelerini haritalar arasında kopyalayıp yapıştırarak haritaları birleştirebilirsiniz. Kod öğesi tanımlayıcıları eşleşirse, kod öğelerini yapıştırma birleştirme işlemi gibi işlev görür. Bu görevi kolaylaştırmak için, görüntülemek istediğiniz tüm derlemeleri veya ikilileri aynı klasöre koyun, böylece her derlemenin veya ikilinin tam yolunun birleştirmek istediğiniz her harita için aynı olmasını sağlayabilirsiniz.

Alternatif olarak, bu derlemeleri veya ikilileri bu klasörden aynı haritaya sürükleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Yönlendirilmiş Grafik İşaretleme Dili (DGML) başvurusu](../modeling/directed-graph-markup-language-dgml-reference.md)
