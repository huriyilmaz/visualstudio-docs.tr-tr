---
title: Kod eşlemelerine göz atma ve bunları yeniden düzenleme
description: Performansını okumayı ve geliştirmeyi kolaylaştırmak için kod eşlemlerinde öğeleri nasıl yeniden düzenleyebilir öğrenin.
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
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e579f62c24795ad99939fe10f68c42acaaa89b60
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861940"
---
# <a name="browse-and-rearrange-code-maps"></a>Kod eşlemelerine göz atma ve bunları yeniden düzenleme

Performansını okumayı ve geliştirmeyi kolaylaştırmak için kod eşlemlerinde öğeleri yeniden düzenleyin.

Bir çözümde temeldeki kodu etkilemeden kod haritalarını özelleştirebilirsiniz. Bu, anahtar kod öğelerine odaklanmak veya kodla ilgili fikirleri iletmek istediğinizde yararlıdır. Örneğin, ilginç alanlar vurgulamak için haritadaki kod öğelerini seçip filtreleyebilir, kod öğelerinin ve bağlantıların stilini değiştirebilir, kod öğelerini gizleyebilir veya silebilir ve özellikler, Kategoriler veya gruplar kullanarak kod öğelerini düzenleyebilirsiniz.

 **Gereksinimler**

- Kod eşlemeleri oluşturmak için Visual Studio Enterprise sahip olmanız gerekir.

- Kod haritalarını görüntüleyebilir ve Visual Studio Professional kod eşlemlerinde sınırlı düzenlemeler yapabilirsiniz.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a> Kod eşlemeleriyle çalışmaya başlama

Bir kod haritası oluşturun (daha fazla ayrıntı için [çözümlerinizde harita bağımlılıklarını](../modeling/map-dependencies-across-your-solutions.md) inceleyin). Haritanın oluşturmayı bitirmesini beklemek istemiyorsanız, oluşturma işlemini durdurmak için herhangi bir zamanda **iptal** bağlantısına tıklayın. Bununla birlikte, bunu yaparsanız tüm bağımlılıkların ve bağlantıların ayrıntılarını görmezsiniz.

Haritayı oluşturduktan sonra, kodunuzu gözden geçirmek için şu ipuçlarını kullanmaya başlayın:

- Koddaki doğal bağımlılık kümelerine bakın. Harita araç çubuğunda, grafik araç çubuğunda **Düzen**, **hızlı kümeler** ![ hızlı kümeler düğmesini seçin ](../modeling/media/quickclustersicon.gif) . Bkz. [harita yerleşimini değiştirme](#Selecting).

     ![Bağımlılık grafiği &#45; hızlı kümeler düzeni](../modeling/media/dependencygraph_quickclusters.png)

- İlgili düğümleri gruplandırarak Haritayı daha küçük alanlara düzenleyin. Bu grupları yalnızca, otomatik olarak görüntülenen Intergroup bağımlılıklarını görmek için daraltın. Bkz. [Grup düğümleri](#OrganizeGroups).

- Haritayı basitleştirmek ve ilgilendiğiniz düğümlerin veya bağlantıların türlerine odaklanmak için filtreleri kullanın. Bkz. [filtre düğümleri ve bağlantıları](#FilterNodes).

- Büyük eşlemelerin performansını en üst düzeye çıkarın. Daha fazla bilgi için bkz. [çözümlerinizde harita bağımlılıkları](../modeling/map-dependencies-across-your-solutions.md) . Örneğin harita araç çubuğunda **derlemeyi atla** ' yı açın, böylece haritadaki öğeleri güncelleştirdiğinizde Visual Studio çözümünüzü yeniden oluşturmaz.

## <a name="change-the-map-layout"></a><a name="Selecting"></a> Harita yerleşimini değiştirme

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Tüm haritanın bağımlılık akışını belirli bir yönde düzenleyin. Bu, koddaki mimari katmanları görbaşlamanıza yardımcı olabilir.|Harita araç çubuğunda **Düzen**' i seçin ve ardından:<br /><br /> -   **Yukarıdan aşağıya** ![ Üstten alta grafik düğmesi](../modeling/media/topbottomgraphbutton.gif)<br />-   **Aşağıdan yukarıya** ![ Alttan üste grafik düğmesi](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Soldan sağa** ![ Soldan sağa düzen düğmesi](../modeling/media/leftrightgraphbutton.gif)<br />-   **Sağdan sola** ![ Sağdan sola grafik düğmesi](../modeling/media/rightleftgraphbutton.gif)|
|Kümelerin merkezinde en bağımlı düğümleri ve bu kümelerin dışında en az bağımlı düğümleri içeren kodda doğal bağımlılık kümelerine bakın.|Harita araç çubuğunda **Düzen**' i ve sonra  ![ grafik araç çubuğunda hızlı kümeler hızlı kümeler düğmesini seçin ](../modeling/media/quickclustersicon.gif) .|
|Haritada bir veya daha fazla düğüm seçin.|Bir düğüme tıklayarak seçin. Birden fazla düğümü seçmek veya seçimini kaldırmak için, tıklarken **CTRL** tuşunu basılı tutun.<br /><br /> Klavye: noktalı odak dikdörtgenini bir düğüme **taşımak Için** **Tab** tuşuna basın veya ok tuşlarını kullanın.   +  Düğümleri çoklu seçmek veya seçimini kaldırmak için CTRL +**boşluk** tuşlarına basın.|
|Belirli düğümleri haritadaki etrafında taşıyın.|Düğümleri taşımak için sürükleyin. Düğümleri sürüklerken diğer düğümleri ve bağlantıları taşımak için **SHIFT** tuşunu basılı tutun.<br /><br /> Klavye: **CTRL** tuşunu basılı tutun ve ok tuşlarına basın.|
|Bir grup içindeki düzeni haritadaki diğer düğümlerden ve gruplardan bağımsız olarak değiştirin.|Bir düğüm seçin ve kısayol menüsünü açın. **Düzen** ' i seçin ve düzen stilini seçin.<br /><br /> - veya -<br /><br /> Bir düğüm seçin ve alt düğümleri göstermek için genişletin. Grup açılır araç çubuğunu göstermek için düğüm başlığına tıklayın ve grup bağımlılığı grafiğinin **Düzen stilini değiştir** ![ &#45; grup araç çubuğu &#45; düzen listesi ' ni açın ](../modeling/media/dependencygraph_grouptoolbar.gif) . Ağaç düzenleri, **hızlı kümeler** veya **liste görünümünden** birini seçin (grubun içeriğini bir liste olarak düzenler).<br /><br /> Daha fazla ayrıntı için bkz. [Grup düğümleri](#OrganizeGroups) .|
|Haritadaki bir eylemi geri alın.|**CTRL**  +  **Z** tuşuna basın veya Visual Studio **geri alma** komutunu kullanın.|

## <a name="browse-the-map"></a><a name="Explore"></a> Haritaya gözatamıyorum

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Haritayı tarayın.|Fareyi kullanarak Haritayı herhangi bir yöne sürükleyin.<br /><br /> - veya -<br /><br /> Yatay kaydırma yapmak için **SHIFT** tuşunu basılı tutun ve fare tekerleğini döndürün. **SHIFT** tuşuna basılı tutun  +   ve yatay olarak kaydırmak için fare tekerleğini döndürün.|
|Haritayı yakınlaştırın veya uzaklaştırın.|Fare tekerleğini döndürün.<br /><br /> - veya -<br /><br /> Kod Haritası araç çubuğundaki **Yakınlaştırma** açılan listesini kullanın.<br /><br /> - veya -<br /><br /> Klavye kısayollarını kullanın. Yakınlaştırmak için **CTRL + SHIFT +** tuşlarına basın. (nokta). Uzaklaştırmak için **CTRL + SHIFT +,** (virgül) tuşlarına basın.|
|Fareyi kullanarak belirli bir alanı yakınlaştırın.|İlgilendiğiniz alanın çevresine bir dikdörtgen çizerken sağ fare düğmesini basılı tutun.|
|Pencereyi penceresinde yeniden boyutlandırın ve eşleyin.|Kod Haritası araç çubuğundaki **Yakınlaştırma** listesinden **sığacak şekilde Yakınlaştır** ' ı seçin.<br /><br /> - veya -<br /><br /> Kod Haritası araç çubuğunda harita araç çubuğunda simgeye **uyacak şekilde Yakınlaştır** simgesine tıklayın ![ ](../modeling/media/almcodemapzoomicon.png) . Klavye: **CTRL + 0** (sıfır) tuşlarına basın.|
|Haritada adına göre bir düğüm bulun. **İpucu:**  Bu yalnızca haritadaki öğeler için geçerlidir. Çözümünüzde öğeleri bulmak, ancak haritada değil, **Çözüm Gezgini** bulun ve ardından bunları haritaya sürükleyin. (Seçiminizi sürükleyin veya **Çözüm Gezgini** araç çubuğunda **kod eşlemesinde göster**' e tıklayın).|1.  ![ ](../modeling/media/almcodemapfindicon.png) haritanın sağ üst köşesindeki arama kutusunu göstermek için kod Haritası araç çubuğundaki harita simgesini bul simgesini seçin (klavye: **CTRL + F** tuşlarına basın).<br />2. öğe adını yazın ve **Return** tuşuna basın veya "Büyüteç" simgesine tıklayın. Aramanızla eşleşen ilk öğe haritada seçili şekilde görünür.<br />3. Aramanızı özelleştirmek için açılan listeyi açın ve bir arama seçeneği belirleyin. Seçenekler **Sonrakini Bul**, **Öncekini Bul** ve **Tümünü Seç**. Ardından arama metin kutusunun yanındaki ilgili düğmeye tıklayın.<br />     ![Arama seçenekleri&#45;aşağı açılan liste](../modeling/media/almcodemapssearchdropdown.png)<br />     Alternatif olarak, klavyeyi kullanın: bir sonraki eşleşen düğümü seçmek için **F3** tuşuna basın veya önceki eşleşen düğümü seçmek için **SHIFT + F3** tuşlarına basın.<br />4. arama metin kutusunun altındaki simgelere tıklayarak arama koşullarının nasıl işleneceğini belirten seçeneklerden birini seçin.<br />     ![Arama eşleştirme seçenekleri](../modeling/media/almcodemapssearchmatchicons.png)<br />     Seçenekler, soldan sağa, büyük/küçük harfe duyarlı eşleştirme, yalnızca tam sözcükleri eşleştirme, .NET normal ifade söz dizimini kullanma, grupları otomatik olarak genişleterek eklenen öğelerle eşleşen öğeleri gösterir. **Önemli:**  Yalnızca bu gruplar daha önce genişletilmişse, daraltılan gruplardaki eşleşmeleri bulmak için arama kutusunu kullanabilirsiniz. Bu eşleşmeleri bulmak ve üst gruplarını otomatik olarak genişletmek için arama kutusu altında bu seçeneği belirleyin.|
|Tüm seçilmemiş düğümleri seçin.|Seçili düğümlerin kısayol menüsünü açın. **Seç**, **seçimi ters çevir**' i seçin.|
|Seçili olanları bağlayan ek düğümleri seçin.|Seçili düğümlerin kısayol menüsünü açın. **Seç** ' i ve bunlardan birini seçin:<br /><br /> -Seçili düğüme doğrudan bağlanan ek düğümleri seçmek için **gelen bağımlılıklar**' ı seçin.<br />-Seçili düğümden doğrudan bağlantı sağlayan ek düğümleri seçmek için **giden bağımlılıklar**' ı seçin.<br />-Seçili düğüme doğrudan ve öğesinden bağlanan ek düğümleri seçmek için **her Ikisini de** seçin.<br />-Seçili düğümden ve bu düğüme bağlanan tüm düğümleri seçmek için **bağlı alt grafik**' i seçin.<br />-Seçili düğümün tüm alt öğelerini seçmek için **alt öğeler**' i seçin.|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a> Düğümleri ve bağlantıları filtrele

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Filtreler bölmesini gösterin veya gizleyin.|Kod Haritası araç çubuğunda **Filtreler** düğmesini seçin. **Filtreler** bölmesi, varsayılan olarak **Çözüm Gezgini** sekmeli bir sayfa olarak görüntülenir.|
|Haritada gösterilen düğüm türlerini filtreleyin.|Filtreler bölmesindeki **kod öğeleri** listesinde onay kutularını işaretleyin veya temizleyin.|
|Haritada gösterilen bağlantı türlerini filtreleyin.|Filtreler bölmesindeki **ilişkiler** listesinden onay kutularını ayarlayın veya temizleyin.|
|Haritada test projesi düğümlerini göster veya gizle.|Filtreler bölmesindeki **çeşitli** listesinden **Test varlıkları** onay kutusunu işaretleyin veya temizleyin.|

Haritanın gösterge panelinde gösterilen simgeler, listede yaptığınız ayarları yansıtır. Gösterge panelini göstermek veya gizlemek için, kod Haritası araç çubuğundaki **gösterge** düğmesine tıklayın.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a> Düğümleri ve bağlantıları İnceleme

Kod haritaları bu tür bağlantıları gösterir:

- Tek bir bağlantı iki düğüm arasındaki tek bir ilişkiyi temsil eder.

- Çapraz grup bağlantısı, farklı gruplardaki iki düğüm arasındaki ilişkiyi temsil eder.

- Toplu bağlantı, iki grup arasındaki aynı yönde işaret eden tüm ilişkileri temsil eder.

> [!TIP]
> Varsayılan olarak, haritada yalnızca seçili düğümler için çapraz grup bağlantıları gösterilmektedir. Gruplar arasındaki toplanmış bağlantıları göstermek veya gizlemek üzere bu davranışı değiştirmek için, kod Haritası araç çubuğunda **Düzen** ' i tıklatın ve **Gelişmiş**' i seçin, sonra **tüm çapraz grup bağlantılarını gösterin** veya **tüm çapraz** grup bağlantılarını gizleyin. Daha fazla ayrıntı için bkz. [düğümleri ve bağlantıları gizleme veya gösterme](#HidingShowing) .

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Bir düğüm veya bağlantı hakkında daha fazla bilgi görüntüleyin.|Araç ipucu görünene kadar fare işaretçisini düğümün üst kısmına veya bağlantısına taşıyın.<br /><br /> Toplanmış bir bağlantının araç ipucu gösterdiği ayrı bağımlılıkları listeler.<br /><br /> - veya -<br /><br /> Düğüm veya bağlantı için kısayol menüsünü açın. **Düzenle**, **Özellikler**' i seçin.|
|Bir grubun içeriğini gösterin veya gizleyin.|-Bir grubu genişletmek için düğüm için kısayol menüsünü açın ve **Grup**, **Genişlet**' i seçin.<br />     - veya -<br />     Köşeli çift ayraç (aşağı ok) düğmesi görünene kadar fare işaretçisini düğümün üst kısmına taşıyın. Grubu genişletmek için bu düğmeye tıklayın. Klavye: Seçili Grubu genişletmek veya daraltmak için **artı** tuşuna ( **+** ) veya **eksi** tuşuna ( **-** ) basın.<br />-Bir grubu daraltmak için düğüm için kısayol menüsünü açın ve **Grup**, **Daralt**' ı seçin.<br />     - veya -<br />     Köşeli çift ayraç (yukarı ok) düğmesi görünene kadar fare işaretçisini bir grubun üstüne taşıyın. Grubu daraltmak için bu düğmeye tıklayın.<br />-Tüm grupları genişletmek için,   +  tüm düğümleri seçmek üzere CTRL **A** 'ya basın. Harita için kısayol menüsünü açın ve **Grup**, **Genişlet** seçeneğini belirleyin. **Note:**      Tüm grupların genişletilmesi, kullanılamayan bir eşleme veya bellek sorunları oluşturursa, bu komut kullanılamaz. Eşlemeyi yalnızca ilgilendiğiniz ayrıntı düzeyine genişletmenizi öneririz.<br />-Tüm grupları daraltmak için bir düğümün veya haritanın kısayol menüsünü açın. **Grup** seç, **Tümünü Daralt**.|
|Bir ad alanı, tür veya üye için kod tanımına bakın.|Düğüm için kısayol menüsünü açın ve **Tanıma Git**' i seçin.<br /><br /> -veya-<br /><br /> Düğüme çift tıklayın. Genişletilmiş gruplar için gruptaki üstbilgiye çift tıklayın.<br /><br /> -veya-<br /><br /> Düğümü seçin ve **F12** tuşuna basın.<br /><br /> Örneğin:<br /><br /> -Bir sınıf içeren bir ad alanı için, sınıfın kod dosyası, bu sınıfın tanımını göstermek için açılır. Diğer durumlarda, **simge sonuçlarını bul** penceresi, kod dosyalarının bir listesini gösterir. **Note:**      Bu görevi bir Visual Basic ad alanında gerçekleştirdiğinizde, ad alanı arkasındaki kod dosyası açılmaz. Bu sorun, bir Visual Basic ad alanı içeren seçili düğümlerin bir grubunda bu görevi gerçekleştirdiğinizde da oluşur. Bu sorunu geçici olarak çözmek için, ad alanının arkasındaki kod dosyasına el ile göz atın veya seçiminizden ad alanı için olan düğümü atlayın.<br />-Bir sınıf veya kısmi bir sınıf için, sınıf tanımını göstermek üzere bu sınıfın kod dosyası açılır.<br />-Bir yöntem için, üst sınıfa ait kod dosyası, yöntem tanımını göstermek için açılır.|
|Bir toplama bağlantısına katılan bağımlılıkları ve öğeleri inceleyin.|İlgilendiğiniz bağlantıları seçin ve seçiminiz için kısayol menüsünü açın. **Katkıda bulunan bağlantıları göster** veya **katkıda bulunan bağlantıları yeni kod haritasında göster '** i seçin.<br /><br /> Visual Studio, bağlantının her iki ucunda da grupları genişletir ve yalnızca bağlantıya katılan öğe ve bağımlılıkları gösterir. **Note:**  Kısmi gruplardaki öğeler arasındaki bağımlılıkları incelediğinizde şu davranışla karşılaşabilirsiniz: <ul><li>İncelemenize katılmayan öğelerin bağlantıları, bu bağlantılar hala mevcut olsa bile haritadan kaybolur.</li><li>Kısmi bir gruptaki bir öğenin bağlantısını incelemenizi ve daha sonra aynı öğeye ait farklı bir bağlantıyı incelemenizi varsayın. İkinci İnceleme sırasında, hedef kısmi Grup yalnızca ilk inceleyecek öğeleri gösterir. İlk inceleyecek katılmayan ancak ikinci inceinize katılan bağlantılar ve hedef öğeler görünmüyor.</li></ul> Bir gruptan eksik öğeleri görmek için **tekrar al alt** ![ tekrar al alt simgesini seçin ](../modeling/media/dependencygraph_deletednodesicon.png) (bir grubun tüm üyelerinin haritada göründüğünü gösterir). Ayrıca, eylemlerinizi geri almayı deneyebilirsiniz (klavye: **CTRL + Z** tuşlarına basın) ve yeni bir haritadaki bağımlılıkları inceleyebilirsiniz.|
|Farklı gruplardaki birden çok düğüm arasındaki bağımlılıkları inceleyin.|Tüm alt öğelerini görebilmeniz için grupları genişletin. Alt öğeleri dahil olmak üzere ilgilendiğiniz tüm düğümleri seçin. Haritada seçili düğümler arasındaki çapraz grup bağlantıları gösterilmektedir.<br /><br /> Bir gruptaki tüm düğümleri seçmek için, bu grubun çevresinde bir dikdörtgen çizerken **SHIFT** ve sol fare düğmesine basın ve basılı tutun. Bir haritadaki tüm düğümleri seçmek için **CTRL** + **a**'ya basın. **İpucu:**  Çapraz grup bağlantılarını her zaman göstermek için harita araç çubuğunda **Düzen** ' i seçin, **Gelişmiş**, **tüm çapraz grup bağlantılarını gösterin**.|
|Bir düğümün veya bağlantının başvurduğu öğelere bakın.|Düğüm için kısayol menüsünü açın ve **tüm başvuruları bul**' ı seçin. **Note:**  Bu, yalnızca `Reference` eşleme. dgml dosyasındaki düğüm veya bağlantı için özniteliği ayarlandığında geçerlidir. Düğümlerden veya bağlantılardan öğelere başvurular eklemek için bkz. [dgml dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a> Düğümleri ve bağlantıları gizleme veya gösterme

Düğümlerin gizlenmesi, düzen algoritmasına katılmalarını engeller. Varsayılan olarak, çapraz grup bağlantıları gizlidir. Çapraz grup bağlantıları, düğümleri gruplar arasında bağlayan tek bağlantılardır. Gruplar daraltıldığında, eşleme tüm çapraz grup bağlantılarını gruplar arasında tek bağlantılarla toplar. Bir grubu genişlettiğinizde veya grup içindeki düğümleri seçtiğinizde, çapraz grup bağlantıları görünür ve o gruptaki bağımlılıkları gösterir.

> [!CAUTION]
> Visual Studio Enterprise içinde oluşturulan bir eşlemeyi Visual Studio Professional kullananlarla paylaşmadan önce, başkalarının görmesini istediğiniz tüm düğümleri veya çapraz grup bağlantılarını gösterdiğinizden emin olun. Aksi takdirde, bu kullanıcılar bu öğelerin gizliliğini kaldıramayacaktır.

### <a name="to-hide-or-show-nodes"></a>Düğümleri gizlemek veya göstermek için

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Seçili düğümleri gizleyin.|1. gizlemek istediğiniz düğümleri seçin.<br />2. Seçili düğümlerin veya haritanın kısayol menüsünü açın. **Seç**, **Seçileni Gizle**' yi seçin.|
|Seçilmemiş düğümleri gizleyin.|1. görünür kalmasını istediğiniz düğümleri seçin.<br />2. Seçili düğümlerin veya haritanın kısayol menüsünü açın. **Seç**' i seçin, **Seçili seçimini gizleyin**.|
|Gizli düğümleri göster.|-Bir grup içindeki tüm gizli düğümleri göstermek için, önce grubun genişletildiğinden emin olun. Kısayol menüsünü açın ve **Seç**, **alt öğeleri göster**' i seçin.<br />     - veya -<br />      ![ Grubun sol üst köşesindeki alt öğeleri göster alt simge ](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) simgesine tıklayın (Bu yalnızca gizli alt düğümler olduğunda görünür).<br />-Tüm gizli düğümleri göstermek için harita veya düğüm için kısayol menüsünü açın ve **Seç**, **Tümünü göster**' i seçin.|

### <a name="to-hide-or-show-links"></a>Bağlantıları gizlemek veya göstermek için

|**Kime**|**Harita araç çubuğunda düzen ve Gelişmiş ' i seçin ve ardından**|
|-|-|
|Çapraz grup bağlantılarını her zaman gösterin.|**Tüm çapraz grup bağlantılarını göster**. Bu, gruplar arasında toplanmış bağlantıları gizler.|
|Çapraz grup bağlantılarını her zaman gizleyin.|**Tüm çapraz grup bağlantılarını gizle**|
|Seçili düğümler için yalnızca çapraz grup bağlantılarını göster.|**Seçili düğümlerde çapraz grup bağlantılarını göster**|
|Tüm bağlantıları gizleyin.|**Tüm bağlantıları gizleyin**. Bağlantıları yeniden göstermek için yukarıda listelenen seçeneklerden birini belirleyin.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a> Grup düğümleri

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Kapsayıcı düğümlerini grup düğümleri veya yaprak düğümleri olarak gösterin.|Kapsayıcı düğümlerini yaprak düğüm olarak göstermek için: düğümleri seçin, seçiminizin kısayol menüsünü açın ve **Grup**, **yaprağı Dönüştür**' ü seçin.<br /><br /> Kapsayıcı düğümlerini grup düğümleri olarak göstermek için: düğümleri seçin, seçiminiz için kısayol menüsünü açın ve **Grup**, **gruba Dönüştür**' ü seçin.|
|Bir grup içindeki düzeni değiştirin.|Grubu seçin, kısayol menüsünü açın, **Düzen**' i seçin ve istediğiniz düzen stilini seçin.<br /><br /> - veya -<br /><br /> 1. grubu seçin ve genişletildiğinden emin olun.<br />2. Grup başlığına yeniden tıklayın ve grup araç çubuğu görüntülenir.<br />     ![Bağımlılık grafiği &#45; grup araç çubuğu](../modeling/media/dependencygraph_group.png)<br />3. Grup listesi bağımlılık grafiğinin **Düzen stilini değiştirin** ![ &#45; grup araç çubuğu &#45; düzeni ](../modeling/media/dependencygraph_grouptoolbar.gif) ve istediğiniz düzen stilini seçin.<br /><br /> **Liste görünümü** grubun üyelerini listeye yeniden düzenler. **Grafik varsayılanı** , Grup yerleşimini varsayılan harita düzenine sıfırlar. Diğer seçenekler için bkz. [harita yerleşimini değiştirme](#Selecting).|
|Bir gruba düğüm ekleyin.|Düğümü gruba sürükleyin.<br /><br /> Düğümü sürüklerken, Visual Studio, düğümü taşımakta olduğunuz göstermek için bir gösterge görüntüler.<br /><br /> Düğümleri grubun dışına da sürükleyebilirsiniz.|
|Grup olmayan bir düğüme düğüm ekleyin.|Düğümü hedef düğüme sürükleyin. Düğüme düğüm ekleyerek herhangi bir hedef düğümü bir gruba dönüştürebilirsiniz.|
|Seçili düğümleri gruplandırın.|1. gruplandırmak istediğiniz düğümleri seçin. Seçtiğiniz son düğümün üzerinde açılan bir araç çubuğu görüntülenir.<br />     ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)<br />2. araç çubuğunda, **Seçili düğümleri** dördüncü simge grubunu seçin (düğüm genişletilmişse dört simge yerine beş tane olur). Yeni grubun adını yazın ve **Return** tuşuna basın.<br />     - veya -<br />     Gruplandırmak istediğiniz düğümleri seçin ve seçiminiz için kısayol menüsünü açın. **Grup**, **üst Grup Ekle** öğesini seçin, yeni grubun adını yazın ve **Return** tuşuna basın.<br /><br /> Bir grubu yeniden adlandırabilirsiniz. Grubun kısayol menüsünü açın ve **Düzenle**, **Özellikler** ' i seçerek Visual Studio Özellikler penceresi açın. **Label** özelliğinde, grubu gereken şekilde yeniden adlandırın.|
|Grupları kaldırın.|Kaldırmak istediğiniz grup veya grupları seçin. Seçiminiz için kısayol menüsünü açın ve **Grup**, **grubu kaldır**' ı seçin.|
|Düğümleri üst grubundan kaldırın.|Taşımak istediğiniz düğümleri seçin. Seçiminiz için kısayol menüsünü açın ve **Grup**, **üst öğeden kaldır**' ı seçin. Bu, düğümleri en üst öğesine kadar veya hiç alt grubu yoksa grubun dışına kaldırır.<br /><br /> - veya -<br /><br /> Düğümleri seçin ve gruptan sürükleyin.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a> Düğüm, bağlantı ve açıklama ekleme, kaldırma veya yeniden adlandırma

Haritada ayrıntıya geçmek veya Haritayı basitleştirmek için bir haritada daha fazla veya daha az öğe gösterebilirsiniz. Ayrıca öğeleri yeniden adlandırabilir ve maddelere açıklamalar ekleyebilirsiniz.

> [!CAUTION]
> Visual Studio Enterprise kullanılarak oluşturulan bir eşlemeyi, Visual Professional kullanan kişilerle paylaşmadan önce, başkalarının görmesini istediğiniz kod öğelerinin haritada görünür olduğundan emin olun. Aksi takdirde, bu kullanıcılar silinen kod öğelerini alamaz.

### <a name="add-a-node-for-a-code-element"></a>Kod öğesi için düğüm ekleme

|**Kime**|**Bu adımları gerçekleştirin**|
|-|-|
|Geçerli fare işaretçisi konumuna yeni bir genel düğüm ekleyin.|1. fare işaretçisini, haritada yeni kod öğesini yerleştirmek istediğiniz yere taşıyın ve **Ekle** tuşuna basın.<br />     - veya -<br />     Harita için kısayol menüsünü açın ve **Düzenle**, **Ekle**, **genel düğüm**' i seçin.<br />2. yeni düğümün adını yazın ve **Return** tuşuna basın.|
|Geçerli fare işaretçisi konumunda belirli bir kod öğesi düğümü türü ekleyin.|1. fare işaretçisini, harita üzerinde yeni kod öğesini yerleştirmek istediğiniz yere taşıyın ve haritanın kısayol menüsünü açın.<br />2. istediğiniz düğüm türünü **Düzenle**, **Ekle** ve Seç ' i seçin.<br />3. yeni düğümün adını yazın ve **Return** tuşuna basın.|
|Bir gruba genel veya belirli bir kod öğesi düğümü türü ekleyin.|1. Grup düğümünü seçin ve kısayol menüsünü açın.<br />2. istediğiniz düğüm türünü **Düzenle**, **Ekle** ve Seç ' i seçin.<br />3. yeni düğümün adını yazın ve **Return** tuşuna basın.|
|Aynı türde yeni bir düğüm ekleyin ve var olan bir düğüm ile bağlantılandırılır.|1. kod öğesini seçin. Üzerinde açılan bir araç çubuğu görünür.<br />     ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)<br />2. araç çubuğunda ikinci simgeyi seçin **ve bu düğüm ile aynı kategoriye sahip bir düğüm oluşturun ve buna yeni bir bağlantı ekleyin**.<br />3. yeni kod öğesini koymak için haritada bir yer seçin ve sol fare düğmesine tıklayın.<br />4. yeni düğümün adını yazın ve **Return** tuşuna basın.|
|Odağa sahip olan mevcut bir kod öğesinden bağlantılı yeni bir genel düğüm ekleyin.|1. klavyeyi kullanarak, bağlantı yapılacak kod öğesi odağa (noktalı dikdörtgen) sahip olana kadar **Tab** tuşuna basın.<br />2. **alt** + **Ekle**'ye basın.<br />3. yeni düğümün adını yazın ve **Return** tuşuna basın.|
|Odağa sahip varolan bir kod öğesine bağlanan yeni bir genel düğüm ekleyin.|1. klavyeyi kullanarak, bağlantı yapılacak kod öğesi odağa (noktalı dikdörtgen) sahip olana kadar **Tab** tuşuna basın.<br />2. **alt** + **SHIFT** + **Insert** tuşuna basın.<br />3. yeni düğümün adını yazın ve **Return** tuşuna basın.|

|**İçin kod öğeleri eklemek için**|**Bu adımları gerçekleştirin**|
|-|-|
|Çözümdeki kod öğeleri.|1. **Çözüm Gezgini** kod öğesini bulun. **Çözüm Gezgini** arama kutusunu kullanın veya çözüme gözatamazsınız. **İpucu:**      Bir tür veya üye üzerinde bağımlılıklara sahip kod öğelerini bulmak için, **Çözüm Gezgini** veya üye için kısayol menüsünü açın. Sizi ilgilendiren ilişkiyi seçin. **Çözüm Gezgini** yalnızca belirtilen bağımlılıklara sahip kod öğelerini gösterir.<br />2. ilgilendiğiniz kod öğelerini harita yüzeyine sürükleyin. Ayrıca, kod öğelerini Sınıf Görünümü veya Nesne Tarayıcısı sürükleyebilirsiniz.<br />     - veya -<br />     **Çözüm Gezgini**, eşlemek istediğiniz kod öğelerini seçin. Ardından, **Çözüm Gezgini** araç çubuğunda **kod eşlemesinde göster**' e tıklayın.<br /><br /> Varsayılan olarak, yeni kod öğeleri için üst kapsayıcı hiyerarşisi haritada gösterilir. Bu davranışı değiştirmek için kod Haritası araç çubuğundaki **üst öğeleri dahil et** düğmesini kullanın. Devre dışı bırakıldığında, haritaya yalnızca kod öğesi eklenir. Yalnızca bir sürükle ve bırak eylemi için bu davranışı tersine çevirmek için, kod öğelerini haritaya sürüklerken **CTRL** tuşunu basılı tutun.<br /><br /> Visual Studio, Seçiminizdeki en üst düzey kod öğeleri için kod öğeleri ekler. Bir kod öğesinin diğer kod öğelerini içerip içermemesi için, köşeli çift ayracın (aşağı ok) görünmesi için fare işaretçisini kod öğesinin üzerine taşıyın. Kod öğesini genişletmek için köşeli çift ayracı seçin. Tüm kod öğelerini genişletmek için **CTRL** + **A** 'ya basarak tüm öğeleri seçin, haritanın kısayol menüsünü açın ve **Grup**, **Genişlet**' i seçin. Tüm grupların genişletilmesi kullanılamaz bir eşleme üretebilir veya bellek sorunlarına yol açacağından bu komut kullanılamaz.|
|Haritadaki kod öğeleriyle ilgili kod öğeleri.|Kod Haritası araç çubuğunda **Ilişkili göster** düğmesine tıklayın ve ilgilendiğiniz ilgili öğelerin türünü seçin.<br /><br /> - veya -<br /><br /> Kod öğesi için kısayol menüsünü açın. İlgilendiğiniz ilişki türüne bağlı olarak menüdeki **göster...** öğelerinden birini seçin. Örneğin, geçerli öğenin başvurduğu öğeleri, geçerli öğeye başvuran öğeleri, sınıflar için temel ve türetilmiş türleri, yöntem çağıranları ve kapsayan sınıfları, ad alanlarını ve derlemeleri görebilirsiniz.<br /><br /> Daha ayrıntılı bilgi için [Bu konuya](../modeling/map-dependencies-across-your-solutions.md)bakın.|
|Derlenen .NET derlemeleri (. dll veya. exe) veya ikili dosyaları.|Derlemeleri veya ikili dosyaları Visual Studio dışında bir haritaya sürükleyin.<br /><br /> Yalnızca Visual Studio 'Yu aynı Kullanıcı Access Control (UAC) izinleri düzeyinde çalıştırıyorsanız, Windows Gezgini 'nden veya dosya Gezgini 'nden sürükleyebilirsiniz. Örneğin, UAC açıksa ve Visual Studio 'Yu yönetici olarak çalıştırıyorsanız, Windows Gezgini veya dosya Gezgini sürükleme işlemini engelleyecektir.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Varolan kod öğeleri arasına bir bağlantı ekle

1. Kaynak kodu öğesini seçin. Kod öğesinin üstünde bir araç çubuğu görüntülenir.

    ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)

2. Araç çubuğunda ilk simgeyi seçin, **Bu düğümden, ileri ' ye tıklayacağınız düğüme yeni bir bağlantı oluşturun**.

3. Hedef kod öğesini seçin. İki kod öğesi arasında bir bağlantı görünür.

**OR**

1. Haritada kaynak kodu öğesini seçin.

2. Bir fareniz yüklüyse, fare işaretçisini haritanın sınırlarının dışına taşıyın.

3. Kod öğesinin kısayol menüsünü açın ve **Düzenle**  >    >  **genel bağlantı** Ekle ' yi seçin.

4. Sekmesine tıklayın ve bağlantı için hedef kod öğesini seçin.

5.  **Enter** tuşuna basın.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Haritada varolan bir düğüme yorum ekleme

1. Kod öğesini seçin. Üzerinde bir araç çubuğu görüntülenir.

     ![Bağımlılık grafiği araç çubuğu](../modeling/media/depedencygraph_toolbar.png)

2. Araç çubuğunda, üçüncü simgeyi seçin, **Seçili düğüme yeni bir bağlantısı olan yeni bir açıklama düğümü oluşturun**.

     \- veya

     Kod öğesi için kısayol menüsünü açın ve   >  **Yeni yorumu** Düzenle ' yi seçin.

3. Açıklamalarınızı yazın. Yeni bir satıra yazmak için **SHIFT**  +  **ENTER** tuşuna basın.

#### <a name="add-a-comment-to-the-map-itself"></a>Haritaya bir açıklama ekleyin

1. Haritanın kısayol menüsünü açın ve   >  **Yeni yorumu** Düzenle ' yi seçin.

2. Açıklamalarınızı yazın. Yeni bir satıra yazmak için **SHIFT**  +  **ENTER** tuşuna basın.

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Bir kod öğesini veya bağlantıyı yeniden adlandırma

1. Kod öğesini veya yeniden adlandırmak istediğiniz bağlantıyı seçin.

2. **F2** tuşuna basın veya kısayol menüsünü açın ve   >  **yeniden adlandırmayı** Düzenle ' yi seçin.

3. Haritada düzenleme kutusu göründüğünde, kod öğesini veya bağlantıyı yeniden adlandırın.

**OR**

1. Kısayol menüsünü açın ve özellikleri **Düzenle**' yi seçin  >  .

2. Visual Studio Özellikler penceresi **etiket** özelliğini düzenleyin.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Bir kod öğesini veya bağlantıyı haritadan kaldır

1. Kod öğesini veya bağlantıyı seçin ve **Delete** tuşuna basın.

     \- veya

     Kod öğesi veya bağlantı için kısayol menüsünü açın ve Kaldır **Düzenle**' yi seçin  >  .

2. Öğe veya bağlantı bir grubun parçasıysa, grubun içinde **tekrar al Children** Button ![ tekrar al Children Icon ](../modeling/media/dependencygraph_deletednodesicon.png) belirir. Eksik öğeleri ve bağlantıları almak için bu öğeye tıklayın.

- Temel kodu etkilemeden, bir haritadan kod öğelerini ve bağlantıları kaldırabilirsiniz. Bunları sildiğinizde, tanımları DGML (. dgml) dosyasından kaldırılır.

- DGML 'i düzenleyerek, tanımsız kod öğeleri ekleyerek veya Visual Studio 'nun bazı önceki sürümlerini kullanarak oluşturulan haritalar bu özelliği desteklemez.

#### <a name="flag-a-code-element-for-follow-up"></a>İzleme için bir kod öğesini bayrakla işaretle

1. İzleme için bayrak eklemek istediğiniz kod öğesini veya bağlantıyı seçin.

2. Kısayol menüsünü açın ve   >  **izleme bayrağını** Düzenle ' yi seçin.

- Varsayılan olarak, kod öğesi kırmızı bir arka plan kazanır. Uygun izleme bilgileriyle buna [bir açıklama eklemeyi](#AddComments) düşünün.

- Öğenin arka plan rengini değiştirin veya   >  **diğer bayrak renklerini** Düzenle seçeneğini belirleyerek izleme bayrağını temizleyin.

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a> Kod öğesinin veya bağlantının stilini değiştirme

Kod öğelerindeki simgeleri ve kod öğelerinin renklerini ve önceden tanımlanmış simgeleri ve renkleri kullanarak bağlantıları değiştirebilirsiniz. Örneğin, belirli bir kategoriye veya özelliğe sahip kod öğelerini ve bağlantıları vurgulamak için bir renk seçebilirsiniz. Bu, eşlemenin belirli alanlarında tanımanıza ve odaklanmanıza olanak tanır. Haritanın. dgml dosyasını düzenleyerek özel simgeleri ve renkleri belirtebilirsiniz; bkz. [dgml dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Kod öğelerine veya belirli bir kategori veya özellik ile bağlantılara önceden tanımlanmış bir renk veya simge uygulamak için

1. Harita araç çubuğunda **gösterge**' yi seçin.

2. **Gösterge** kutusunda, kod öğesi kategorisi veya özelliğinin listede zaten göründüğünü görün.

3. Liste kategori veya özellik içermiyorsa, **+** **gösterge** kutusunda, **düğüm özelliği**, **düğüm kategorisi**, **bağlantı özelliği** veya **bağlantı kategorisi**' ni seçin. Sonra özellik veya kategoriyi seçin. Kategori veya özellik artık **gösterge** kutusunda görünür.

    > [!NOTE]
    > Bir kod öğesine kategori veya özellik oluşturup atamak için haritanın. dgml dosyasını düzenleyebilirsiniz; bkz. [dgml dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. **Gösterge** kutusunda, eklediğiniz veya değiştirmek istediğiniz kategorinin veya özelliğin yanındaki simgeye tıklayın.

5. Değiştirmek istediğiniz stili seçmek için aşağıdaki tabloyu kullanın:

    |**Bunu değiştirmek için**|**'Yu**|
    |-|-|
    |Arka plan rengi|**Arka Plan**|
    |Ana hat rengi|**Vuruş**|
    |Metin rengi (sonucu göstermek için "f" harfi görüntülenir)|**Ön plan**|
    |Simge|**Simgeler**|

     Renk veya simge seçmeniz için **renk kümesi Seçicisi** veya **simge kümesi seçici** iletişim kutusu görüntülenir.

6. **Renk kümesi Seçicisi** veya **simge kümesi seçici** iletişim kutusunda aşağıdakilerden birini yapın:

    |**Uygulamak için**|**Bu adımları gerçekleştirin**|
    |-|-|
    |Renk veya simge kümesi|**Renk seçin** (veya **simge**) **kümesi** listesini açın. Bir renk veya simge kümesi seçin.|
    |Belirli renk veya simge|Kategori veya özellik değer listesini açın. Bir renk veya simge seçin.|

    > [!NOTE]
    > **Gösterge** kutusunda stilleri yeniden düzenleyebilir, silebilir veya geçici olarak devre dışı bırakabilirsiniz. Bkz. [gösterge kutusunu düzenleme](#ModifyLegend).

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a> Gösterge kutusunu düzenleme

**Gösterge** kutusunda stilleri yeniden düzenleyebilir, silebilir veya geçici olarak devre dışı bırakabilirsiniz:

1. **Gösterge** kutusunda bir stilin kısayol menüsünü açın.

2. Aşağıdaki görevlerden birini uygulayın:

    |**Kime**|**'Yu**|
    |-|-|
    |Kod öğesini devre dışı bırak|**Devre Dışı Bırak**|
    |Kod öğesini Sil|**Silme**|
    |Stili yukarı taşıyın|**Yukarı Taşı**|
    |Kod öğesini aşağı taşı|**Aşağı Taşı**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a> Stilleri bir haritadan diğerine kopyalama

1. Kaynak eşlemesinde **gösterge** kutusunun göründüğünden emin olun. Görünür değilse, harita araç çubuğunda **gösterge**' ye tıklayın.

2. **Gösterge** kutusu için kısayol menüsünü açın. **Göstergeyi Kopyala**' yı seçin.

3. Göstergeyi hedef eşlemenin üzerine yapıştırın.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a> Kod eşlemelerini Birleştir

Haritalar arasında kod öğelerini kopyalayarak ve yapıştırarak haritaları birleştirebilirsiniz. Kod öğesi tanımlayıcıları eşleşiyorsa, kod öğeleri birleştirme işlemi gibi işlevleri yapıştırarak. Bu görevi kolaylaştırmak için, görselleştirmek istediğiniz tüm derlemeleri veya ikili dosyaları aynı klasöre yerleştirin, böylece her bir derlemenin veya ikilinin tam yolu birleştirmek istediğiniz her haritada aynı olur.

Alternatif olarak, bu derlemeleri veya ikili dosyaları o klasörden aynı haritaya sürükleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümlerinizdeki bağımlılıkları eşleme](../modeling/map-dependencies-across-your-solutions.md)
- [Uygulamalarınızda hata ayıklamak için kod eşlemelerini kullanma](../modeling/use-code-maps-to-debug-your-applications.md)
- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Yönlendirilmiş Grafik İşaretleme Dili (DGML) başvurusu](../modeling/directed-graph-markup-language-dgml-reference.md)
