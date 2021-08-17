---
title: Kod eşlemelerine göz atma ve bunları yeniden düzenleme
description: Daha kolay okunmalarını ve performanslarını artırmalarını kolaylaştırmak için kod eşlemelerinde öğeleri yeniden düzenlemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 6271f52a98582dc15aea027ab56404d4f8329844524641bade512821be6a4c59
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121371130"
---
# <a name="browse-and-rearrange-code-maps"></a>Kod eşlemelerine göz atma ve bunları yeniden düzenleme

Daha kolay okunmalarını ve performanslarını geliştirmelerini kolaylaştırmak için kod eşlemelerinde öğeleri yeniden düzenleme.

Bir çözümdeki temel kodu etkilemeden kod haritalarını özelleştirebilirsiniz. Bu, önemli kod öğelerine odaklanmak veya kod hakkında fikirlerinizi iletebilirsiniz. Örneğin ilgi çekici alanları vurgulamak için haritada kod öğelerini seçerek bunları filtreabilir, kod öğelerinin ve bağlantıların stilini değiştirebilir, kod öğelerini gizleyebilirsiniz veya silebilir ve kod öğelerini özellikler, kategoriler veya gruplar kullanarak düzenleyebilirsiniz.

 **Gereksinimler**

- Kod eşlemeleri oluşturmak için bir Visual Studio Enterprise.

- Kod haritalarını görüntüleyemez ve kod eşlemeleri üzerinde sınırlı düzenlemeler Visual Studio Professional.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a> Kullanmaya başlayın eşlemeleriyle çalışma

Kod haritası oluşturma (daha [fazla ayrıntı için bkz. Çözümleriniz arasında](../modeling/map-dependencies-across-your-solutions.md) bağımlılıkları eşleme). Haritanın oluşturma işleminin bitip bitmesini beklemek  istemiyorsanız, oluşturma işlemini durdurmak için herhangi bir zamanda İptal bağlantısına tıklayın. Ancak, bunu yaparsanız tüm bağımlılıkların ve bağlantıların ayrıntılarını görmeyebilirsiniz.

Haritayı oluşturmanın ardından kodunuzu gözden geçirmeye yönelik şu ipuçlarıyla çalışmaya başlamanız gerekir:

- Kodda doğal bağımlılık kümelerini bakın. Harita araç çubuğunda, grafik araç **çubuğunda Düzen**, **Hızlı Kümeler** Hızlı ![ Kümeler düğmesini ](../modeling/media/quickclustersicon.gif) seçin. Bkz. [Harita düzenini değiştirme.](#Selecting)

     ![Hızlı Kümeler &#45; bağımlılık grafiği](../modeling/media/dependencygraph_quickclusters.png)

- İlgili düğümleri gruplara göre haritayı daha küçük alanlara göre düzenleme. Yalnızca otomatik olarak görünen gruplar arası bağımlılıkları görmek için bu grupları daraltabilirsiniz. Bkz. [Grup düğümleri.](#OrganizeGroups)

- Haritayı basitleştirmek ve ilgilendiğiniz düğüm türlerine veya bağlantılara odaklanmak için filtreleri kullanın. Bkz. [Düğümleri ve bağlantıları filtreleme.](#FilterNodes)

- Büyük haritaların performansını en üst düzeye çıkarma. Daha [fazla bilgi için bkz. Çözümleriniz genelinde](../modeling/map-dependencies-across-your-solutions.md) bağımlılıkları eşleme. Örneğin haritadaki öğeleri **güncelleştiren** Visual Studio yeniden derlemek için harita araç çubuğunda Derlemeyi Atla'ya tıklayın.

## <a name="change-the-map-layout"></a><a name="Selecting"></a> Harita düzenini değiştirme

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Bağımlılık akışını haritanın tamamı için belirli bir yönde düzenleme. Bu, kodda mimari katmanları görmene yardımcı olabilir.|Harita araç çubuğunda **Düzen'i seçin** ve ardından:<br /><br /> -   **Üstten Aşağıya** ![ Üstten Alta graf düğmesi](../modeling/media/topbottomgraphbutton.gif)<br />-   **Aşağıdan Yukarıya** ![ Aşağıdan Yukarıya graf düğmesi](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Soldan Sağa** ![ Soldan Sağa düzen düğmesi](../modeling/media/leftrightgraphbutton.gif)<br />-   **Sağdan Sola** ![ Sağdan Sola graf düğmesi](../modeling/media/rightleftgraphbutton.gif)|
|Kodda, kümelerin merkezinde en bağımlı düğümlere ve bu kümelerin dışında en az bağımlı düğüme sahip doğal bağımlılık kümelerini görme.|Harita araç çubuğunda **Düzen'i ve** ardından grafik araç **çubuğunda Hızlı** ![ Kümeler Hızlı Kümeler düğmesini ](../modeling/media/quickclustersicon.gif) seçin.|
|Haritada bir veya daha fazla düğüm seçin.|Seçmek için bir düğüme tıklayın. Birden fazla düğümü seçmek veya seçimini kaldırmak için tıklarken **CTRL tuşunu** basılı tutun.<br /><br /> Klavye: **SEKME tuşuna** basın veya ok tuşlarını kullanarak noktalı odak dikdörtgenini bir düğüme hareket ettirin ve **SPACE** tuşuna basın. Düğümleri çoklu seçmek veya seçimini kaldırmak için **CTRL** ARA  +   ÇUBUĞU'ya basın.|
|Belirli düğümleri haritada hareket ettirin.|Düğümleri sürükleyerek hareket ettirin. Düğümleri sürüklerken diğer düğümleri ve bağlantıları yolundan taşımak için **SHIFT** tuşuna basın ve basılı tutun.<br /><br /> Klavye: **CTRL tuşunu basılı** tutun ve ok tuşlarına basın.|
|Bir grubun içindeki düzeni, eşlemedeki diğer düğümlerden ve gruplardan bağımsız olarak değiştirme.|Bir düğüm seçin ve kısayol menüsünü açın. **Düzen'i** seçin ve bir düzen stili seçin.<br /><br /> - veya -<br /><br /> Bir düğüm seçin ve alt düğümleri gösterecek şekilde genişletin. Grup açılır araç çubuğunu göstermek için düğüm başlığına tıklayın ve Düzen listesinde grup araç çubuğu için Bağımlılık  ![ grafiğinin &#45; düzenini &#45; ](../modeling/media/dependencygraph_grouptoolbar.gif) açın. Ağaç düzenlerinden, Hızlı **Kümelerden veya** **Liste** Görünümünden birini seçin (grubun içeriklerini bir listede düzenler).<br /><br /> Diğer [ayrıntılar için bkz.](#OrganizeGroups) Grup düğümleri.|
|Eşlemede bir eylemi geri alma.|**CTRL**  +  **Z tuşlarına** basın veya Geri Al Visual Studio **kullanın.**|

## <a name="browse-the-map"></a><a name="Explore"></a> Haritaya göz atma

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Haritayı tarayın.|Fareyi kullanarak haritayı herhangi bir yöne sürükleyin.<br /><br /> - veya -<br /><br /> SHIFT **tuşunu basılı** tutun ve fare tekerleğini yatay olarak kaydırmak için döndürün. **SHIFT**  +  **CTRL tuşunu basılı tutun** ve fare tekerleğini yatay olarak kaydırmak için döndürün.|
|Haritayı yakınlaştırın veya uzaklaştırın.|Fare tekerleğini döndürün.<br /><br /> - veya -<br /><br /> Kod haritası **araç** çubuğunda Yakınlaştırma açılan listesini kullanın.<br /><br /> - veya -<br /><br /> Klavye kısayollarını kullanın. Yakınlaştırmak için **CTRL + SHIFT + tuşlarına basın.** (dönem). Uzaklaştırmak için **CTRL + SHIFT + ,** (virgül) tuşlarına basın.|
|Fareyi kullanarak belirli bir alanı yakınlaştırın.|İlgilenirken ilgilendiğiniz alanı çevrelerken sağ fare düğmesini basılı tutun.|
|Haritayı pencereye yeniden boyutlandırın ve sığdırın.|Kod **haritası araç çubuğundaki** **Yakınlaştırma listesinden** Sığdırmak için Yakınlaştır'ı seçin.<br /><br /> - veya -<br /><br /> Sığdırmak **için Yakınlaştır simgesine** ![ tıklayın Kod haritası araç çubuğunda harita araç çubuğunda ](../modeling/media/almcodemapzoomicon.png) yakınlaştır simgesi. Klavye: **CTRL + 0 (sıfır)** tuşlarına basın.|
|Harita üzerinde kendi adına göre bir düğüm bulun. **İpucu:**  Bu yalnızca haritadaki öğeler için çalışır. Çözümünüzdeki öğeleri bulmak ancak haritada değil, öğeleri **Çözüm Gezgini** içinde bulup haritaya sürükleyin. (Seçiminizi sürükleyin veya araç çubuğunda **Çözüm Gezgini** Kod Haritasında **Göster'e tıklayın).**|1. Haritanın sağ üst köşesindeki arama kutusunu göstermek için kod haritası araç çubuğunda Bul simgesini Bul simgesini seçin  ![ ](../modeling/media/almcodemapfindicon.png) (Klavye: **CTRL + F** tuşlarına basın).<br />2. Öğe adını yazın ve **Return tuşuna** basın veya "büyüteç" simgesine tıklayın. Aramanıza eşleşen ilk öğe haritada seçili olarak görünür.<br />3. Aramanızı özelleştirmek için açılan listeyi açın ve bir arama seçeneği belirleyin. Seçenekler Sonrakini **Bul,** **Öncekini Bul ve** Hepsini Seç **seçenekleridir.** Ardından arama metin kutusunun yanındaki ilgili düğmeye tıklayın.<br />     ![Arama seçenekleri açılan&#45;listesi](../modeling/media/almcodemapssearchdropdown.png)<br />     Alternatif olarak klavyeyi kullanın: Bir sonraki eşleşen düğümü **seçmek için F3** tuşuna basın veya **SHIFT + F3** tuşlarına basarak önceki eşleşen düğümü seçin.<br />4. Arama metin kutusunun altındaki simgelere tıklayarak arama terimlerinin nasıl işleniyor olduğunu belirten seçeneklerden birini seçin.<br />     ![Arama eşleşme seçenekleri](../modeling/media/almcodemapssearchmatchicons.png)<br />     Seçenekler şunlardır: Soldan sağa, büyük/küçük harfe duyarlı eşleştirme, yalnızca tam sözcükleri eşleştirme, .NET normal ifade söz dizimi kullanma, grupları otomatik olarak genişleterek içindeki öğelerle eşleşmeleri gösterme. **Önemli:**  Daraltılmış gruplarda eşleşmeleri bulmak için arama kutusunu yalnızca bu gruplar daha önce genişletilmişse kullanabilirsiniz. Bu eşleşmeleri bulmak ve üst gruplarını otomatik olarak genişletmek için arama kutusunun altında bu seçeneği belirleyin.|
|Seçili olmayan tüm düğümleri seçin.|Seçili düğümlerin kısayol menüsünü açın. Seç, **Seçimi** **Ters Çevir'i seçin.**|
|Seçili düğümlere bağlantı olan ek düğümleri seçin.|Seçili düğümlerin kısayol menüsünü açın. **Seç'i** ve bunlardan birini seçin:<br /><br /> - Doğrudan seçili düğüme bağlantı olan ek düğümler seçmek için Gelen **Bağımlılıklar'ı seçin.**<br />- Doğrudan seçili düğümden bağlantı olan ek düğümler seçmek için Giden **Bağımlılıklar'ı seçin.**<br />- Seçili düğüme doğrudan ve seçili düğümden bağlantı olan ek düğümler seçmek için Her İkisi'yi **seçin.**<br />- Seçili düğüme bağlanan ve bu düğümden gelen tüm düğümleri seçmek için Bağlı **AltGraf'ı seçin.**<br />- Seçili düğümün tüm altlarını seçmek için Alt öğesini **seçin.**|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a> Düğümleri ve bağlantıları filtreleme

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Filtreler bölmesini gösterme veya gizleme.|Kod haritası **araç** çubuğunda Filtreler düğmesini seçin. Filtreler **bölmesi,** varsayılan olarak , içinde **sekmeli Çözüm Gezgini** olarak görüntülenir.|
|Haritada gösterilen düğüm türlerini filtrele.|Filtreler bölmesindeki Kod Öğeleri listesinde **onay kutularını ayarlayın** veya temizleyin.|
|Haritada gösterilen bağlantı türlerini filtrele.|Filtreler bölmesindeki İlişkiler listesinde onay **kutularını ayarlayın** veya temizleyin.|
|Proje düğümlerini haritada göster veya gizle.|Filtreler bölmesindeki **Çeşitli** listede Test Varlıkları onay **kutusunu ayarlayın** veya temizleyin.|

Haritanın Gösterge panelinde gösterilen simgeler, listede yer alan ayarları gösterir. Gösterge panelini göstermek veya gizlemek için kod haritası **araç çubuğundaki** Gösterge düğmesine tıklayın.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a> Düğümleri ve bağlantıları inceleme

Kod eşlemeleri şu tür bağlantıları gösterir:

- Tek bir bağlantı, iki düğüm arasındaki tek bir ilişkiyi temsil eder.

- Çapraz grup bağlantısı, farklı gruplarda yer alan iki düğüm arasındaki ilişkiyi temsil eder.

- Toplama bağlantısı, iki grup arasında aynı yöne işaret eden tüm ilişkileri temsil eder.

> [!TIP]
> Varsayılan olarak, harita yalnızca seçili düğümler için çapraz grup bağlantılarını gösterir. Bu davranışı gruplar arasındaki toplu bağlantıları gösterecek veya  gizleyecek şekilde değiştirmek için  kod haritası araç çubuğunda Düzen'e tıklayın ve Gelişmiş'i **ve** ardından Tüm Çapraz Grup Bağlantılarını Göster veya Tüm Çapraz Grup Bağlantılarını Gizle'yi **seçin.** Daha [fazla ayrıntı için bkz. Düğümleri ve bağlantıları](#HidingShowing) gizleme veya gösterme.

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Düğüm veya bağlantı hakkında daha fazla bilgi için bkz.|Fare işaretçisini düğümün veya bağlantının üzerine bir araç ipucu görünene kadar hareket ettirin.<br /><br /> Toplu bağlantının araç ipucu, temsil ettiği bağımlılıkları listeler.<br /><br /> - veya -<br /><br /> Düğümün veya bağlantının kısayol menüsünü açın. Düzenle, **Özellikler'i seçin.** |
|Grubun içeriğini gösterme veya gizleme.|- Bir grubu genişletmek için düğümün kısayol menüsünü açın ve Grup , **Genişlet'i** **seçin.**<br />     - veya -<br />     Köşeli çift ayraç (aşağı ok) düğmesi görünene kadar fare işaretçisini düğümün üst kısmında hareket ettirin. Grubu genişletmek için bu düğmeye tıklayın. Klavye: Seçili grubu genişletmek veya daraltmak için **PLUS** tuşuna ( **+** ) veya MINUS tuşuna ( **)** **-** basın.<br />- Bir grubu daraltın, düğümün kısayol menüsünü açın ve Grup , **Daralt'ı** **seçin.**<br />     - veya -<br />     Köşeli çift ayraç (yukarı ok) düğmesi görünene kadar fare işaretçisini bir grubun üst kısmında hareket ettirin. Grubu daralt için bu düğmeye tıklayın.<br />- Tüm grupları genişletmek için **CTRL**  +  **A tuşlarına** basarak tüm düğümleri seçin. Haritanın kısayol menüsünü açın ve Grupla, **Genişlet'i** **seçin.** **Not:**      Tüm grupların genişletilmesi kullanılamaz bir eşleme veya bellek sorunları üretirse bu komut kullanılamaz. Haritayı yalnızca önemlediğiniz ayrıntı düzeyine genişletmenizi öneririz.<br />- Tüm grupları daraltın, bir düğümün veya haritanın kısayol menüsünü açın. Grup, **Hepsini** **Daralt'ı seçin.**|
|Ad alanı, tür veya üye için kod tanımına bakın.|Düğümün kısayol menüsünü açın ve Tanıma **Git'i seçin.**<br /><br /> -veya-<br /><br /> Düğüme çift tıklayın. Genişletilmiş gruplar için gruptaki üst bilgiye çift tıklayın.<br /><br /> -veya-<br /><br /> Düğümü seçin ve **F12 tuşuna basın.**<br /><br /> Örnek:<br /><br /> - Bir sınıf içeren bir ad alanı için, sınıfın kod dosyası bu sınıfın tanımını göstermek için açılır. Diğer durumlarda Sembol Sonuçlarını **Bul penceresinde** kod dosyalarının listesi gösterilir. **Not:**      Bu görevi bir ad Visual Basic gerçekleştirin, ad alanının arkasındaki kod dosyası açılmaz. Bu sorun ayrıca, bu görevi bir ad alanı adı içeren seçili düğümler grubunda gerçekleştir Visual Basic oluşur. Bu sorunu gidermek için ad alanının arkasındaki kod dosyasına el ile göz atabilir veya seçiminizi kullanarak ad alanı düğümünü atabilirsiniz.<br />- Bir sınıf veya kısmi bir sınıf için, bu sınıfın kod dosyası sınıf tanımını göstermek için açılır.<br />- Bir yöntem için, yöntem tanımını göstermek için üst sınıfın kod dosyası açılır.|
|Toplama bağlantısına katılan bağımlılıkları ve öğeleri inceleme.|İstediğiniz bağlantıları seçin ve seçiminizin kısayol menüsünü açın. Yeni **Kod Haritasında Katkıda Bulunan** Bağlantıları Göster veya Katkıda Bulunan Bağlantıları **Göster'i seçin.**<br /><br /> Visual Studio, bağlantının her iki ucunda da grupları genişletir ve yalnızca bağlantıya katılan öğe ve bağımlılıkları gösterir. **Not:**  Kısmi gruplarda yer alan öğeler arasındaki bağımlılıkları incelerken şu davranışı görebilirsiniz: <ul><li>İncelemenize katılmayan öğelerin bağlantıları, bu bağlantılar hala mevcut olsa bile haritadan kaybolur.</li><li>Kısmi gruptaki bir öğenin bağlantısını incelenin ve daha sonra aynı öğenin farklı bir bağlantısını incelenin. İkinci incelemeniz sırasında hedef kısmi grup yalnızca ilk incelemenizin öğelerini gösterir. İlk incelemenize katılmayan ancak ikinci incelemenize katılan bağlantılar ve hedef öğeler görünmez.</li></ul> Bir gruptaki eksik öğeleri görmek için, Alt Öğeleri Yeniden ÖğeYeniden Çıkar Simgesini (bir grubun tüm üyelerinin haritada görünme olmadığını ![ ](../modeling/media/dependencygraph_deletednodesicon.png) gösterir) seçin. Ayrıca, eylemlerinizi geri almayı deneme (Klavye: **CTRL+Z** tuşlarına basın) ve bağımlılıkları yeni bir harita üzerinde incelersiniz.|
|Farklı gruplarda birden çok düğümdeki bağımlılıkları inceleme.|Tüm alt gruplarını görmek için grupları genişletin. alt düğümleri de dahil olmak üzere ilgini alan tüm düğümleri seçin. Harita, seçilen düğümler arasındaki çapraz grup bağlantılarını gösterir.<br /><br /> Bir gruptaki tüm düğümleri seçmek için  shift tuşuna ve sol fare düğmesini basılı tutun ve bu grubun etrafında bir dikdörtgen çizin. Bir haritada tüm düğümleri seçmek için **CTRL** A tuşlarına + **basın.** **İpucu:**  Çapraz grup bağlantılarını her zaman göstermek  için harita araç çubuğunda Düzen,Gelişmiş **,** Tüm Çapraz Grup **Bağlantılarını Göster'i seçin.**|
|Bir düğümün veya bağlantının başvuracakları öğelere bakın.|Düğümün kısayol menüsünü açın ve Tüm Başvuruları **Bul'ı seçin.** **Not:**  Bu yalnızca, öznitelik `Reference` eşlemenin .dgml dosyasında düğüm veya bağlantı için ayar olduğunda geçerlidir. Düğümlerden veya bağlantılardan öğelere başvurular eklemek için bkz. DGML dosyalarını düzenleyerek [kod eşlemelerini özelleştirme.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a> Düğümleri ve bağlantıları gizleme veya gösterme

Düğümlerin gizlenmesi, düzen algoritmasına katılmalarını engeller. Varsayılan olarak, çapraz grup bağlantıları gizlidir. Çapraz grup bağlantıları, düğümleri gruplar arasında bağlayan tek bağlantılardır. Gruplar daraltılmış olduğunda, eşleme tüm çapraz grup bağlantılarını gruplar arasındaki tek bağlantılarda bir araya toplar. Bir grubu genişlettiğinizde veya grup içindeki düğümleri seçtiğinizde, çapraz grup bağlantıları görünür ve o gruptaki bağımlılıkları gösterir.

> [!CAUTION]
> Visual Studio Enterprise'da oluşturulan bir haritayı Visual Studio Professional, başkalarının görmelerini istediğiniz düğümleri veya çapraz grup bağlantılarını göstermeyi emin olun. Aksi takdirde, bu kullanıcılar bu öğelerin gizliliğini kaldıramayacaktır.

### <a name="to-hide-or-show-nodes"></a>Düğümleri gizlemek veya göstermek için

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Seçili düğümleri gizle.|1. Gizlemek istediğiniz düğümleri seçin.<br />2. Seçilen düğümlerin veya haritanın kısayol menüsünü açın. Seç, **Seçilini** **Gizle'yi seçin.**|
|Seçili olmayan düğümleri gizle.|1. Görünür kalmasını istediğiniz düğümleri seçin.<br />2. Seçilen düğümlerin veya haritanın kısayol menüsünü açın. Seç **,** Seçimi **Kaldır'ı seçin.**|
|Gizli düğümleri göster.|- Bir grubun içindeki tüm gizli düğümleri göstermek için önce grubun genişletilir olduğundan emin olun. Kısayol menüsünü açın ve Select **,** **Unhide Children seçeneğini belirleyin.**<br />     - veya -<br />     Grubun **sol üst köşesindeki Unhide Children Unhide** Children Icon simgesine tıklayın (bu yalnızca gizli alt ![ ](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) düğümler olduğunda görünür).<br />- Tüm gizli düğümleri göstermek için haritanın veya düğümün kısayol menüsünü açın ve Seç **'** i seçin, Tüm Öğeleri **Göster'i seçin.**|

### <a name="to-hide-or-show-links"></a>Bağlantıları gizlemek veya göstermek için

|**Kime**|**Harita araç çubuğunda Düzen, Gelişmiş'i ve ardından**|
|-|-|
|Her zaman çapraz grup bağlantılarını gösterir.|**Tüm Çapraz Grup Bağlantılarını Göster.** Bu, gruplar arasında toplanmış bağlantıları gizler.|
|Çapraz grup bağlantılarını her zaman gizler.|**Tüm Çapraz Grup Bağlantılarını Gizle**|
|Seçili düğümler için yalnızca çapraz grup bağlantılarını gösterir.|**Seçili Düğümlerde Çapraz Grup Bağlantılarını Gösterme**|
|Tüm bağlantıları gizle.|**Tüm Bağlantıları Gizle.** Bağlantıları yeniden göstermek için yukarıda listelenen seçeneklerden birini belirleyin.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a> Grup düğümleri

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Kapsayıcı düğümlerini grup düğümleri veya yaprak düğümler olarak gösterme.|Kapsayıcı düğümlerini yaprak düğümler olarak göstermek için: Düğümleri seçin, seçiminizin kısayol menüsünü açın ve Grupla **,** Yapraka Dönüştür **seçeneğini belirleyin.**<br /><br /> Kapsayıcı düğümlerini grup düğümleri olarak göstermek için: Düğümleri seçin, seçiminizin kısayol menüsünü açın ve **Grupla**, Gruba **Dönüştür'ü seçin.**|
|Grubun içindeki düzeni değiştirme.|Grubu seçin, kısayol menüsünü açın, **Düzen'i** seçin ve istediğiniz düzen stilini seçin.<br /><br /> - veya -<br /><br /> 1. Grubu seçin ve genişletilmiş olduğundan emin olun.<br />2. Yeniden grup üst bilgine tıklarsanız grup araç çubuğu görüntülenir.<br />     ![Bağımlılık grafiği &#45; araç çubuğu](../modeling/media/dependencygraph_group.png)<br />3. **Grup listesinin** düzen stilini değiştir Bağımlılık grafiği'&#45; araç çubuğunu &#45; ve istediğiniz düzen ![ stilini ](../modeling/media/dependencygraph_grouptoolbar.gif) seçin.<br /><br /> **Liste Görünümü,** grubun üyelerini listede yeniden düzenleyebilir. **Graph Varsayılan,** grup düzenini eşleme varsayılan düzenine sıfırlar. Diğer seçenekler için [bkz. Harita düzenini değiştirme.](#Selecting)|
|Bir gruba düğüm ekleyin.|Düğümü gruba sürükleyin.<br /><br /> Düğümü sürüklerken Visual Studio, düğümü hareket ettirirken gösteren bir gösterge görüntüler.<br /><br /> Düğümleri grubun dışına da sürükleyebilirsiniz.|
|Grup olmayan bir düğüme düğüm ekleyin.|Düğümü hedef düğüme sürükleyin. Herhangi bir hedef düğümü gruba düğüm ekleyerek bir gruba dönüştüresiniz.|
|Seçili düğümleri grupla.|1. Grup kullanmak istediğiniz düğümleri seçin. Son seçen düğümün üzerinde bir açılır araç çubuğu görüntülenir.<br />     ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)<br />2. Araç çubuğunda dördüncü simgeyi seçin **Seçili** düğümleri grupla (düğüm genişletilirse dört simge yerine beş tane olur). Yeni grubun adını yazın ve Return tuşuna **basın.**<br />     - veya -<br />     Grup oluşturmak istediğiniz düğümleri seçin ve seçiminizin kısayol menüsünü açın. Grup, Üst **Grup Ekle'yi** seçin, yeni grubun adını yazın ve Return tuşuna  **basın.**<br /><br /> Bir grubu yeniden adlandırarak yeniden adlandırarak. Grubun kısayol menüsünü açın ve Düzenle **,** **Özellikler'i seçarak** Visual Studio Özellikler penceresi. Etiket **özelliğinde** grubu gereken şekilde yeniden adlandırabilirsiniz.|
|Grupları kaldırın.|Kaldırmak istediğiniz grup veya grupları seçin. Seçiminizin kısayol menüsünü açın ve Grup , **Grubu** **Kaldır'ı seçin.**|
|Düğümleri üst gruplarından kaldırın.|Taşımak istediğiniz düğümleri seçin. Seçiminizin kısayol menüsünü açın ve Grup , Üst **Öğeden** **Kaldır'ı seçin.** Bu işlem, düğümlerin üstlerine kadar olan veya bir alt grubu yoksa grubun dışından kaldırır.<br /><br /> - veya -<br /><br /> Düğümleri seçin ve gruptan dışarı sürükleyin.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a> Düğüm, bağlantı ve açıklama ekleme, kaldırma veya yeniden adlandırma

Detaya inerek veya haritayı basitleştirmek için haritada daha fazla veya daha az öğe görüntüebilirsiniz. Ayrıca öğeleri yeniden adlandırarak öğelere açıklama abilirsiniz.

> [!CAUTION]
> Visual Studio Enterprise kullanılarak oluşturulmuş bir haritayı Visual Professional kullananlarla paylaşmadan önce, başkalarının da görmelerini istediğiniz kod öğelerinin haritada görünür olduğundan emin olun. Aksi takdirde, bu kullanıcılar silinen kod öğelerini alamayacaktır.

### <a name="add-a-node-for-a-code-element"></a>Kod öğesi için düğüm ekleme

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Geçerli fare işaretçisi konuma yeni bir genel düğüm ekleyin.|1. Fare işaretçisini harita üzerinde yeni kod öğesini koymak istediğiniz yere hareket ettirin ve Ekle'ye **basın.**<br />     - veya -<br />     Haritanın kısayol menüsünü açın ve Düzenle, **Ekle**, Genel **Düğüm'ü seçin.** <br />2. Yeni düğümün adını yazın ve Return tuşuna **basın.**|
|Geçerli fare işaretçisi konuma belirli bir kod öğesi düğümü türü ekleyin.|1. Fare işaretçisini harita üzerinde yeni kod öğesini koymak istediğiniz yere hareket ettirin ve haritanın kısayol menüsünü açın.<br />2. **Düzenle,** **Ekle'yi** seçin ve istediğiniz düğüm türünü seçin.<br />3. Yeni düğümün adını yazın ve Return tuşuna **basın.**|
|Gruba genel veya belirli bir kod öğesi düğümü türü ekleyin.|1. Grup düğümünü seçin ve kısayol menüsünü açın.<br />2. **Düzenle,** **Ekle'yi** seçin ve istediğiniz düğüm türünü seçin.<br />3. Yeni düğümün adını yazın ve Return tuşuna **basın.**|
|Aynı türde ve var olan bir düğümden bağlanan yeni bir düğüm ekleyin.|1. Kod öğesini seçin. Üstte bir açılır araç çubuğu görünür.<br />     ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)<br />2. Araç çubuğunda, bu düğümle aynı kategoriye sahip bir düğüm oluştur simgesini **seçin ve buna yeni bir bağlantı ekleyin.**<br />3. Yeni kod öğesini koymak için haritada bir yer seçin ve farenin sol düğmesine tıklayın.<br />4. Yeni düğümün adını yazın ve Return tuşuna **basın.**|
|Odağı olan mevcut bir kod öğesinden bağlanan yeni bir genel düğüm ekleyin.|1. Klavyeyi kullanarak, **bağlantı** verilecek kod öğesi odak (noktalı dikdörtgen) olana kadar Sekme tuşuna basın.<br />2. **Alt Insert** + **tuşuna basın.**<br />3. Yeni düğümün adını yazın ve Return tuşuna **basın.**|
|Odağı olan mevcut bir kod öğesine bağlantı olan yeni bir genel düğüm ekleyin.|1. Klavyeyi kullanarak, **bağlantının** odak noktası (noktalı dikdörtgen) olana kadar Sekme tuşuna basın.<br />2. **Alt** + **Shift Insert** + **tuşuna basın.**<br />3. Yeni düğümün adını yazın ve Return tuşuna **basın.**|

|**için kod öğeleri eklemek için**|**Bu adımları gerçekleştirin**|
|-|-|
|Çözümde kod öğeleri.|1. öğesinde kod **öğesini Çözüm Gezgini.** Çözüm Gezgini **arama** kutusunu kullanın veya çözüme göz atabilirsiniz. **İpucu:**      Bir türe veya üyeye bağımlılıkları olan kod öğelerini bulmak için, türün kısayol menüsünü veya öğesinde üyeyi **Çözüm Gezgini.** Sizi ilgilendiren ilişkiyi seçin. **Çözüm Gezgini** yalnızca belirtilen bağımlılıklara sahip kod öğelerini gösterir.<br />2. İlgini alan kod öğelerini harita yüzeyine sürükleyin. Ayrıca, kod öğelerini Sınıf Görünümü Tarayıcı'dan sürükleyebilirsiniz.<br />     - veya -<br />     Bu **Çözüm Gezgini,** eşlemek istediğiniz kod öğelerini seçin. Ardından, araç çubuğunda **Çözüm Gezgini** Kod **Haritası'nda Göster'e tıklayın.**<br /><br /> Varsayılan olarak, yeni kod öğelerinin üst kapsayıcı hiyerarşisi haritada gösterilir. Bu davranışı **değiştirmek için** kod haritası araç çubuğundaki Üst Bilgileri Dahil Etmek düğmesini kullanın. Kapalı olduğunda, eşlemeye yalnızca kod öğesinin kendisi eklenir. Bu davranışı yalnızca bir sürükle ve bırak eylemi için ters çevirmek için, kod öğelerini haritaya sürüklerken **CTRL** tuşuna basın ve basılı tutun.<br /><br /> Visual Studio, seçiminize en üst düzey kod öğeleri için kod öğeleri ekler. Bir kod öğesinin başka kod öğeleri içerdiğini görmek için fare işaretçisini kod öğesinin üzerine hareket ettirin, böylece köşeli çift ayraç (aşağı ok) görünür. Kod öğesini genişletmek için köşeli çift ayraç seçin. Tüm kod öğelerini genişletmek için **CTRL** A tuşlarına basarak tüm öğeleri seçin, haritanın kısayol menüsünü açın ve +  Grupla , **Genişlet'i** **seçin.** Tüm grupların genişletilmesi kullanılamaz bir eşleme üretirse veya yetersiz bellek sorunlarına neden olursa bu komut kullanılamaz.|
|Harita üzerinde kod öğeleriyle ilgili kod öğeleri.|Kod haritası **araç** çubuğunda İlişkilileri Göster düğmesine tıklayın ve ilgilendiğinizi ilgili öğelerin türünü seçin.<br /><br /> - veya -<br /><br /> Kod öğesinin kısayol menüsünü açın. sizi ilgilendiren **ilişkinin türüne** bağlı olarak menüdeki Göster ... öğeleri arasında seçim yapabilirsiniz. Örneğin, geçerli öğenin başvur aldığı öğeleri, geçerli öğeye başvuran öğeleri, sınıflar için temel ve türetilmiş türleri, yöntem çağıranlarını ve içeren sınıfları, ad alanlarını ve derlemeleri görebilir.<br /><br /> Diğer ayrıntılar için bu [konuya bakın.](../modeling/map-dependencies-across-your-solutions.md)|
|Derlenmiş .NET derlemeleri (.dll veya .exe) veya ikili dosyalar.|Derlemeleri veya ikili dosyaları dış Visual Studio eşlemeye sürükleyin.<br /><br /> Gezgin'den Windows veya Dosya Gezgini' Visual Studio Kullanıcı Access Control (UAC) izin düzeyine sahipse sürükleyebilirsiniz. Örneğin, UAC açıksa ve yönetici olarak Visual Studio çalışıyorsanız, Windows Explorer veya Dosya Gezgini sürükleme işlemi engellenir.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Mevcut kod öğeleri arasında bağlantı ekleme

1. Kaynak kod öğesini seçin. Kod öğesinin üzerinde bir araç çubuğu görünür.

    ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)

2. Araç çubuğunda, ilk simge olan Bu düğümden yeni oluştur bağlantısını seçin. Bu **düğümde sonraki simgesine tıklarsanız.**

3. Hedef kod öğesini seçin. İki kod öğeleri arasında bir bağlantı görünür.

**OR**

1. Haritada kaynak kod öğesini seçin.

2. Yüklü bir fareniz varsa, fare işaretçisini haritanın sınırlarının dışına sürükleyin.

3. Kod öğesinin kısayol menüsünü açın ve Düzenle Genel **Bağlantı**  >  **Ekle'yi**  >  **seçin.**

4. sekme tuşuna basın ve bağlantı için hedef kod öğesini seçin.

5.  **Enter** tuşuna basın.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Harita üzerinde var olan bir düğüme açıklama ekleme

1. Kod öğesini seçin. Üstte bir araç çubuğu görünür.

     ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)

2. Araç çubuğunda, seçilen düğüme yeni bir bağlantı ile **yeni açıklama düğümü oluştur üçüncü simgesini seçin.**

     \- veya -

     Kod öğesinin kısayol menüsünü açın ve Yeni Açıklamayı **Düzenle'yi**  >  **seçin.**

3. Açıklamalarınızı yazın. Yeni bir satıra girmek için Shift Enter **tuşuna**  +  **basın.**

#### <a name="add-a-comment-to-the-map-itself"></a>Haritanın kendisine açıklama ekleme

1. Haritanın kısayol menüsünü açın ve Yeni Açıklamayı **Düzenle'yi**  >  **seçin.**

2. Açıklamalarınızı yazın. Yeni bir satıra girmek için Shift Enter **tuşuna**  +  **basın.**

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Kod öğesini veya bağlantıyı yeniden adlandırma

1. Yeniden adlandırmak istediğiniz kod öğesini veya bağlantıyı seçin.

2. **F2 tuşuna** basın veya kısayol menüsünü açın ve Yeniden Adlandır'ı **Düzenle'yi**  >  **seçin.**

3. Haritada düzenleme kutusu göründüğünde kod öğesini veya bağlantıyı yeniden adlandırabilirsiniz.

**OR**

1. Kısayol menüsünü açın ve Özellikleri **Düzenle'yi**  >  **seçin.**

2. Dosyanın **Etiket** özelliğini Visual Studio Özellikler penceresi.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Kod öğesini veya bağlantıyı haritadan kaldırma

1. Kod öğesini veya bağlantıyı seçin ve Sil **tuşuna** basın.

     \- veya -

     Kod öğesinin kısayol menüsünü veya bağlantısını açın ve Kaldır'ı **düzenle'yi**  >  **seçin.**

2. Öğe veya bağlantı bir grubun parçası  ise, grubun içinde Alt ÖğeYi Geri Çıkar düğmesi Alt Öğe ![ Simgesini Yeniden ](../modeling/media/dependencygraph_deletednodesicon.png) İçe Çıkar simgesi görünür. Eksik öğeleri ve bağlantıları almak için buna tıklayın.

- Kod öğelerini ve bağlantıları, temel alınan kodu etkilemeden bir haritadan kaldırabilirsiniz. Bunları silebilirsiniz; bunların tanımları DGML (.dgml) dosyasından kaldırılır.

- Haritalar DGML düzenleyerek, tanımsız kod öğeleri ekleyerek veya önceki bazı Visual Studio kullanarak oluşturulan öğeler bu özelliği desteklemez.

#### <a name="flag-a-code-element-for-follow-up"></a>Takip için bir kod öğesini bayrakla bayrakla bayrakla izleme

1. Takip için bayrak eklemek istediğiniz kod öğesini veya bağlantıyı seçin.

2. Kısayol menüsünü açın ve Takip etmek **için**  >  **Bayrağı Düzenle'yi seçin.**

- Varsayılan olarak, kod öğesi kırmızı bir arka plan kazanır. Buna [uygun izleme](#AddComments) bilgileriyle bir açıklama eklemeyi düşünün.

- Öğenin arka plan rengini değiştirme veya Diğer Bayrak Renklerini Düzenle'yi **seçerek**  >  **izleme bayrağını temizleme.**

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a> Kod öğesinin veya bağlantının stilini değiştirme

Önceden tanımlanmış simgeleri ve renkleri kullanarak kod öğeleri ve kod öğelerinin ve bağlantıların renklerini değiştirebilirsiniz. Örneğin, belirli bir kategori veya özelli kod öğelerini ve bağlantıları vurgulamak için bir renk seçebilirsiniz. Bu, haritanın belirli alanlarını tanımlamanıza ve odaklanmanıza olanak sağlar. Haritanın .dgml dosyasını düzenleyerek özel simgeler ve renkler belirtebilirsiniz; Bkz. [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Kod öğelerine veya belirli bir kategori veya özelle ilgili bağlantılara önceden tanımlanmış bir renk veya simge uygulamak için

1. Harita araç çubuğunda Gösterge'yi **seçin.**

2. Gösterge **kutusunda** kod öğesi kategorisinin veya özelliğinin listede zaten görüntülendiğinden bkz.

3. Listede kategori veya özellik yoksa Gösterge kutusunda düğüm özelliği, Düğüm Kategorisi, Bağlantı Özelliği veya Bağlantı **+** Kategorisi'ne **tıklayın.**     Ardından özelliği veya kategoriyi seçin. Kategori veya özellik artık Gösterge **kutusunda** görünür.

    > [!NOTE]
    > Kod öğesine bir kategori veya özellik oluşturmak ve atamak için haritanın .dgml dosyasını düzenleyebilirsiniz; Bkz. [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

4. Gösterge **kutusunda,** eklenen veya değiştirmek istediğiniz kategori veya özelliğin yanındaki simgeye tıklayın.

5. Değiştirmek istediğiniz stili seçmek için aşağıdaki tabloyu kullanın:

    |<bpt id="p1">**</bpt>To change the<ept id="p1">**</ept>|**Seçin**|
    |-|-|
    |Arka plan rengi|**Arka Plan**|
    |Ana hat rengi|**Kontur**|
    |Metin rengi (sonucu göstermek için bir "f" harfi görüntülenir)|**Ön plan**|
    |Simge|**Simgeler**|

     Renk **Kümesi Seçicisi veya** Simge Ayar **Seçici** iletişim kutusu, bir renk veya simge seçmeniz için görüntülenir.

6. Renk **Kümesi Seçicisi veya** **Simge Kümesi Seçici** iletişim kutusunda, aşağıdakilerden birini yapın:

    |**Bir uygulamak için**|**Bu adımları gerçekleştirin**|
    |-|-|
    |Renk veya simge kümesi|Renk **seçin (veya** **simge**) küme **listesini** açın. Bir renk veya simge kümesi seçin.|
    |Belirli bir renk veya simge|Kategori veya özellik değer listesini açın. Bir renk veya simge seçin.|

    > [!NOTE]
    > Gösterge kutusunda stilleri yeniden düzenleyebilir, silebilir veya  geçici olarak etkinleştirebilirsiniz. Bkz. [Gösterge kutusunu düzenleme.](#ModifyLegend)

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a> Gösterge kutusunu düzenleme

Açıklama kutusunda stilleri yeniden düzenleyebilir, silebilir veya  geçici olarak etkinleştirebilirsiniz:

1. Gösterge kutusunda bir stilin kısayol **menüsünü** açın.

2. Aşağıdaki görevlerden birini uygulayın:

    |**Kime**|**Seçin**|
    |-|-|
    |Kod öğesini devre dışı bırakma|**Devre Dışı Bırak**|
    |Kod öğesini silme|**Silme**|
    |Stili yukarı taşıyın|**Yukarı Taşı**|
    |Kod öğesini aşağı taşıma|**Aşağı Taşı**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a> Stilleri bir eşlemeden diğerine kopyalama

1. Kaynak haritada **Gösterge** kutusunun göründüğünden emin olun. Görünmüyorsa, harita araç çubuğunda Gösterge'ye **tıklayın.**

2. Gösterge kutusunun kısayol **menüsünü** açın. Göstergeyi **Kopyala'ya seçin.**

3. Göstergeyi hedef haritaya yapıştırın.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a> Kod haritalarını birleştirme

Haritalar arasında kod öğelerini kopyalayıp yapıştırarak eşlemeleri birleştirebilirsiniz. Kod öğesi tanımlayıcıları eşleşiyorsa, kod öğelerini yapıştırarak birleştirme işlemi gibi bir işlem yapabilirsiniz. Bu görevi kolaylaştırmak için, her derlemenin veya ikili dosyanın tam yolunun birleştirmek istediğiniz her eşleme için aynı olması için görselleştirmek istediğiniz tüm derlemeleri veya ikili dosyaları aynı klasöre ekleyin.

Alternatif olarak, bu derlemeleri veya ikili dosyaları bu klasörden aynı eşlemeye sürükleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Yönlendirilmiş Grafik İşaretleme Dili (DGML) başvurusu](../modeling/directed-graph-markup-language-dgml-reference.md)
