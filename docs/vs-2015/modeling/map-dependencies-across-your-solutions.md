---
title: Çözümleriniz genelinde bağımlılıkları eşleyin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code exploration, dependency graphs
- dependency graphs, exporting
- code exploration, relationships
- DGML
- graph documents
- code visualization [Visual Studio ALM]
- graph documents, saving
- dependencies, visualizing
- dependency graphs, saving
- Visual Studio Ultimate, code visualization
- code, visualizing
- dependency graphs, creating
- dependency graphs
- graph documents, exporting
- code exploration, visualizing
ms.assetid: e04850a2-17c5-459b-93ec-6c74143b3292
caps.latest.revision: 245
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b25d23b7c65742ffddadbe178d7550dc1794414a
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296324"
---
# <a name="map-dependencies-across-your-solutions"></a>Çözümlerinizdeki bağımlılıkları eşleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodunuzun içindeki bağımlılıkları anlamak istediğinizde kod haritaları oluşturarak bunları görselleştirin. Bu, kodun dosyalar ve kod satırları arasında okuma yapmadan nasıl bir araya oturduğunu görmenizi sağlar.

 ![Çözümlerinizi genelinde bağımlılıkları görüntüleme](../modeling/media/codemapsmainintro.png "Codemapsmaintanıtım")

 **Bazı videolar aşağıda verilmiştir**:

- [Görselleştirme aracılığıyla kod bağımlılıklarınızı anlayın](https://go.microsoft.com/fwlink/?LinkID=252065)

- [Değişikliğin etkisini görselleştirin](https://go.microsoft.com/fwlink/?LinkID=252068)

- [Kod eşlemeleriyle karmaşık kodu anlama](https://go.microsoft.com/fwlink/?LinkID=259869)

## <a name="GetStarted"></a>Kod eşlemeleriyle çalışmaya başlama
 **Kod eşlemelerini kullanmak için aşağıdakilerden birini yapmanız gerekir**:

- Visual Studio Enterprise: kod düzenleyicisinden, Çözüm Gezgini, Sınıf Görünümü veya Nesne Tarayıcısı kod haritaları oluşturun.

- Visual Studio Professional: kod haritalarını açın, sınırlı düzenlemeler yapın ve koda gidin.

> [!WARNING]
> Visual Studio Enterprise içinde oluşturulan haritaları, Visual Studio Professional kullanan diğer kullanıcılarla paylaşmadan önce, haritadaki tüm öğelerin (gizli öğeler, genişletilmiş gruplar ve çapraz grup bağlantıları gibi) görünür hale geldiğinden emin olun.

 **Bu dillerdeki kod bağımlılıklarını eşleyebilirsiniz**:

- Visual C# .NET veya çözüm ya da derlemelerde .NET Visual Basic (. dll veya. exe)

- Visual C++ projelerinde yerel veya yönetilen C++ C veya kod, üst bilgi dosyaları (. h veya `#include`) veya ikili dosyalar

- X + + projeleri ve Microsoft Dynamics AX için .NET modüllerinden oluşturulan derlemeler

  **Note:** C# Veya Visual Basic .net dışındaki projeler için, bir kod eşlemesi başlatmak veya varolan bir kod eşlemesine öğe eklemek için daha az seçenek vardır. Örneğin, bir C++ projenin metin düzenleyicisinde bir nesneye sağ tıklayıp bir kod haritasına ekleyebilirsiniz. Ancak, Çözüm Gezgini, Sınıf Görünümü ve Nesne Tarayıcısı bağımsız kod öğelerini veya dosyalarını sürükleyip bırakabilirsiniz.

#### <a name="to-see-the-overall-dependencies-across-your-solution"></a>Çözümünüz genelinde genel bağımlılıkları görmek için

1. **Mimari** menüsünü açın.

2. Yalnızca çözümü açtıysanız ve henüz yayımlamadıysanız veya kodunuz son kez derlenmesinden bu yana değiştirilmişse, **çözüm Için kod Haritası Oluştur**' u seçin.

3. Kodunuz son kez derlenmeden bu yana değiştirilmediyse, Haritayı oluştururken daha hızlı performans sağlamak için **derleme olmadan çözüm Için kod Haritası Oluştur** ' u seçin.

4. Çözümünüzde genel bağımlılıkları görüntülemek için kod eşlemelerini nasıl kullanabileceğinizi anlamak için [genel bağımlılıklara bakın](#SeeOverviewSource) .

#### <a name="to-see-specific-dependencies-within-your-solution"></a>Çözümünüzdeki belirli bağımlılıkları görmek için

1. Çözümünüz yüklendikten sonra **Çözüm Gezgini**açın.

2. Eşlemek istediğiniz tüm projeler, derleme başvuruları, klasörler, dosyalar, türler veya Üyeler ' i seçin.

3. **Çözüm Gezgini** araç çubuğunda, **kod eşlemesinde göster**' i seçerek![seçili düğümlerden yeni grafik oluştur düğmesini](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton")seçin. Veya kısayol menüsünü açın ve **kod eşlemesinde göster**' i seçin. Ayrıca, Sınıf Görünümü veya Nesne Tarayıcısı öğeleri yeni veya varolan bir kod haritasına sürükleyebilirsiniz.

4. Çözümünüzdeki belirli bağımlılıkları görüntülemek için kod eşlemelerini nasıl kullanabileceğinizi anlamak için [belirli bağımlılıklara bakın](#SeeSpecificSource) .

### <a name="CreateEmptyMap"></a>Çözümünüze yeni bir boş kod eşlemesi eklemek için

1. **Çözüm Gezgini**' de, en üst düzey çözüm Düğümünüzün kısayol menüsünü açın. **Ekle** ' yi ve ardından **Yeni öğe**' yi seçin.

2. **Yüklü**altında **genel**' i seçin.

3. Sağ bölmede, **yönlendirilmiş grafik belgesi** ' ni seçin ve ardından **Ekle**' yi seçin.

     Artık çözümünüzün **Çözüm öğeleri** klasöründe görüntülenen boş bir haritanız vardır.

#### <a name="to-create-a-new-empty-code-map-without-adding-it-to-your-solution"></a>Çözümünüze eklemeden yeni bir boş kod haritası oluşturmak için

1. **Mimari** menüsünü açın ve **Yeni kod Haritası**' nı seçin.

     \- veya-

2. **Dosya** menüsünü açın ve **Yeni** ' yi seçip **Dosya**' yı seçin.

3. **Yüklü**altında **genel**' i seçin.

4. Sağ bölmede, **yönlendirilmiş grafik belgesi** ' ni seçin ve sonra **Aç**' ı seçin.

     Artık çözümünüz klasörlerinde görünmeyen boş bir haritanız var.

## <a name="SeeOverviewSource"></a>Genel bağımlılıklara bakın

### <a name="OverviewSource"></a>Çözümünüz genelinde bağımlılıklara bakın

1. **Mimari** menüsünde **çözüm Için kod Haritası Oluştur**' u seçin.

    ![Kod Haritası komutu oluştur](../modeling/media/codemapsarchitecturemenu.png "Codemapsmimari menü")

    Üst düzey derlemeleri ve bunlar arasındaki toplanmış bağlantıları gösteren bir harita alırsınız. Toplama bağlantısı ne kadar geniş olursa, temsil ettiği daha fazla bağımlılıklardır.

2. Proje türü simgelerinin listesini (örneğin, test, Web ve telefon Projesi), kod öğelerini (sınıflar, Yöntemler ve özellikler gibi) ve ilişki türlerini (örneğin, devralır, Implements ve çağrılar) göstermek veya gizlemek için kod Haritası araç çubuğundaki **gösterge** düğmesini kullanın.

    ![Derlemelerin&#45;en üst düzey bağımlılık grafiği](../modeling/media/dependencygraph-toplevelassemblies.png "DependencyGraph_TopLevelAssemblies")

    Bu örnek çözüm, Çözüm klasörlerini (**testler** ve **Bileşenler**), test projelerini, Web projelerini ve derlemeleri içerir. Varsayılan olarak, tüm kapsama ilişkileri *Grup*olarak görünür ve bu, genişletebilir ve daraltabilirsiniz. **Dışlar** grubu, platform bağımlılıkları da dahil olmak üzere çözümünüzün dışındaki her şeyi içerir. Dış derlemeler yalnızca kullanılan öğeleri gösterir. Varsayılan olarak, sistem tabanlı türler, dağınıklığı azaltmak için haritada gizlidir.

3. Haritanın detayına gitmek için, projeleri ve derlemeleri temsil eden grupları genişletin. Tüm düğümleri seçmek için **CTRL + A** tuşlarına basarak her şeyi genişletebilir ve ardından **Grup**' u seçerek kısayol menüsünden ' i **genişletin** .

    ![Kod eşlemesindeki tüm grupları genişletme](../modeling/media/codemapsexpandallgroups.png "CodeMapsExpandAllGroups")

4. Ancak bu, büyük bir çözüm için yararlı olmayabilir. Aslında, karmaşık çözümler için bellek sınırlamaları tüm grupları genişletmesinin engellenmesini sağlayabilir. Bunun yerine, tek bir düğümün içini görmek için genişletin. Fare işaretçinizi düğümün üzerine taşıyın ve göründüğünde köşeli çift ayraca (aşağı ok) tıklayın.

    ![Kod haritasında düğüm genişletme](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")

    Ya da öğeyi seçip artı tuşuna basarak ( **+** ) klavyeyi kullanın. Daha derin kod düzeylerini araştırmak için ad alanları, türler ve Üyeler için de aynısını yapın.

   > [!TIP]
   > Fare, klavye ve dokunma kullanarak kod eşlemeleriyle çalışma hakkında daha fazla bilgi için bkz. [kod haritalarını inceleyin ve yeniden düzenleyin](../modeling/browse-and-rearrange-code-maps.md).

5. Haritayı basitleştirmek ve tek tek bölümlere odaklanmak için, kod Haritası araç çubuğunda **Filtreler** ' i seçin ve yalnızca ilgilendiğiniz düğümlerin ve bağlantıların türlerini seçin. Örneğin, tüm çözüm klasörünü ve derleme kapsayıcılarını gizleyebilirsiniz.

    ![Kapsayıcıları filtreleyerek eşlemeyi basitleştirme](../modeling/media/codemapsfilterfoldersassemblies.png "CodeMapsFilterFoldersAssemblies")

    Ayrıca, temel çözüm kodunu etkilemeden haritalardan ayrı grupları ve öğeleri gizleyerek veya kaldırarak Haritayı basitleştirebilirsiniz.

6. Öğeler arasındaki ilişkileri görmek için haritada seçin. Bağlantıların renkleri, **gösterge** bölmesinde gösterildiği gibi ilişki türlerini gösterir.

    ![Çözümlerinizi genelinde bağımlılıkları görüntüleme](../modeling/media/codemapsmainintro.png "Codemapsmaintanıtım")

    Bu örnekte, mor bağlantılar çağrılardır, noktalı bağlantılar başvurudur ve açık mavi bağlantıları alan erişimdir. Yeşil bağlantılar devralma yapabilir veya birden fazla ilişki türü (veya *kategorisi*) gösteren *Birleşik bağlantılar* olabilir.

   > [!TIP]
   > Yeşil bir bağlantı görürseniz yalnızca bir devralma ilişkisi olduğu anlamına gelebilir. Yöntem çağrıları da olabilir, ancak bunlar devralma ilişkisi tarafından gizlenir. Belirli bağlantı türlerini görmek için, ilgilendiğiniz türleri gizlemek için **Filtreler** bölmesindeki onay kutularını kullanın.

7. Bir öğe veya bağlantı hakkında daha fazla bilgi edinmek için, bir araç ipucu görünene kadar işaretçiyi en üstüne taşıyın. Bu, bir kod öğesinin ayrıntılarını veya bir bağlantının temsil ettiği kategorileri gösterir.

    ![İlişki kategorilerini göster](../modeling/media/codemapsshowlinkcatgories.png "CodeMapsShowLinkCatgories")

8. Bir toplama bağlantısıyla temsil edilen öğeleri ve bağımlılıkları incelemek için, önce bağlantıyı seçin ve ardından kısayol menüsünü açın. **Katkıda bulunan bağlantıları göster** ' i seçin (veya **Yeni kod haritasında katkıda bulunan bağlantıları göster**). Bu,, bağlantının her iki ucunda da grupları genişletir ve yalnızca bağlantıya katılan öğe ve bağımlılıkları gösterir.

9. Haritanın belirli bölümlerine odaklanmak için, ilgilendiğiniz öğeleri kaldırmaya devam edebilirsiniz. Örneğin, sınıf ve üye görünümü detayına gitmek için **Filtreler** bölmesindeki tüm ad alanı düğümlerini filtrelemeniz yeterlidir.

     ![Sınıf ve üye düzeyinde detaya gitme](../modeling/media/dependencygraph-expandedselectedgroups-2012.png "DependencyGraph_ExpandedSelectedGroups_2012")

10. Karmaşık bir çözüm eşlemesine odaklanmak için başka bir yol da var olan bir haritadan seçili öğeleri içeren yeni bir eşleme oluşturmak. Odaklanmak istediğiniz öğeleri seçerken **CTRL** tuşunu basılı tutun, kısayol menüsünü açın ve **seçimden yeni grafik**' i seçin.

     ![Seçili öğeleri yeni kod haritasında göster](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

11. İçeren bağlam, yeni haritaya taşınır. **Filtre** bölmesini kullanarak görmek Istemediğiniz Çözüm klasörlerini ve diğer kapsayıcıları gizleyin.

     ![Görünümü basitleştirmek için kapsayıcıları filtreleyin](../modeling/media/codemapsexpandnewgroups.png "CodeMapsExpandNewGroups")

12. İlişkileri görüntülemek için grupları genişletin ve haritadaki öğeleri seçin.

     ![İlişkileri görüntülemek için öğeleri seçin](../modeling/media/codemapsviewnewrelationships.png "CodeMapsViewNewRelationships")

    Ayrıca bkz:

- [Kod haritalarına göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)

- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

- [Bir çözümleyici çalıştırarak](../modeling/find-potential-problems-using-code-map-analyzers.md)kodunuzda olası sorunları bulun.

### <a name="OverviewCompiled"></a>Derlemelerin veya ikili dosyaların üzerindeki bağımlılıklara bakın

1. [Boş bir kod haritası oluşturun](#GetStarted)veya var olan bir kod haritasını (. dgml dosyası) açın.

2. Visual Studio dışında eşlemek istediğiniz derlemeleri veya ikili dosyaları haritaya sürükleyin. Örneğin, Windows Gezgini veya dosya Gezgini 'nden derlemeleri veya ikili dosyaları sürükleyin.

> [!NOTE]
> Derlemeleri veya ikili dosyaları yalnızca Visual Studio 'Yu aynı Kullanıcı Access Control (UAC) izinleri düzeyinde çalıştırıyorsanız Windows Gezgini veya dosya Gezgini 'nden sürükleyebilirsiniz. Örneğin, UAC açıksa ve Visual Studio 'Yu yönetici olarak çalıştırıyorsanız, Windows Gezgini veya dosya Gezgini sürükleme işlemini engelleyecektir. Bu sorunu geçici olarak çözmek için, her ikisinin de aynı izin düzeyiyle çalıştığından emin olun veya UAC 'yi kapatın.

## <a name="SeeSpecificSource"></a>Belirli bağımlılıklara bakın
 Örneğin, bekleyen değişikliklerle bazı dosyalarda gerçekleştirilecek bir kod incelemesinin olduğunu varsayalım. Bu değişikliklerle ilgili bağımlılıkları görmek için, bu dosyalardan bir kod Haritası oluşturabilirsiniz.

 ![Kod haritasında belirli bağımlılıkları göster](../modeling/media/codemapsspecificdependenciesintro.png "Codemapsspecificbağımlıcıesgirişi")

### <a name="see-specific-dependencies-in-your-solution"></a>Çözümünüzde belirli bağımlılıklara bakın

1. **Çözüm Gezgini**açın. Projeler, derleme başvuruları, klasörler, dosyalar, türler ve ilgilendiğiniz Üyeler ' i seçin. Türler veya Üyeler üzerinde bağımlılıkları olan öğeleri bulmak için **Çözüm Gezgini**' den tür veya üyenin kısayol menüsünü açın. Bağımlılık türünü seçin ve ardından sonuçları seçin.

2. Öğelerinizi ve üyelerini eşleyin. **Çözüm Gezgini** araç çubuğunda, **kod eşlemesinde göster**' e tıklayarak![seçili düğümlerden yeni grafik oluştur düğmesine](../modeling/media/createnewgraphfromselectedbutton.gif "CreateNewGraphFromSelectedButton")tıklayın.

     ![Eşlemek istediğiniz öğeleri seçin](../modeling/media/codemapsselectinsolutionexplorer.png "Codemapsselectınsolutionexplorer")

3. Eşleme, seçili öğeleri kapsayan derlemeler içinde gösterir.

     ![Haritada gruplar olarak gösterilen seçili öğeler](../modeling/media/codemapsshowitemsfromsolnexplorer.png "CodeMapsShowItemsFromSolnExplorer")

     Ayrıca Çözüm Gezgini, Sınıf Görünümü veya Nesne Tarayıcısı öğeleri boş veya varolan bir kod haritasına sürükleyebilirsiniz. Boş bir eşleme oluşturmak için bkz. [boş kod eşlemesi oluşturma](#GetStarted). Öğelerinizin üst hiyerarşisini dahil etmek için, öğeleri sürüklerken **CTRL** tuşuna basın ve basılı tutun ya da varsayılan eylemi belirtmek için kod Haritası araç çubuğundaki **üst öğeleri dahil et** düğmesini kullanın.

    > [!NOTE]
    > Windows Phone veya Windows Mağazası gibi birden fazla uygulama arasında paylaşılan bir projeden öğeler eklediğinizde, bu öğeler etkin olan projeyle eşlemede görünür. Bağlamı başka bir uygulama projesi olarak değiştirirseniz ve paylaşılan projeden daha fazla öğe eklerseniz, bu öğeler yeni etkin olan uygulama projesiyle görünür. Eşleme üzerinde bir öğeyle gerçekleştirdiğiniz işlemler, yalnızca aynı bağlamı paylaşılan öğeler için geçerlidir.

4. Öğeleri araştırmak için bunları genişletin. Fare işaretçisini bir öğenin üzerine taşıyın ve göründüğünde çift köşeli ayraç (aşağı ok) simgesine tıklayın.

     ![Kod haritasında düğüm genişletme](../modeling/media/dependencygraph-containment.png "DependencyGraph_Containment")

     Tüm öğeleri genişletmek için **CTRL + A**kullanarak bunları seçin, sonra haritanın kısayol menüsünü açın ve **Grup**, **Genişlet**' i seçin. Ancak, tüm grupların genişletilmesi kullanılamaz bir eşleme veya bellek sorunları oluşturursa, bu seçenek kullanılamaz.

5. İlgilendiğiniz öğeleri genişletmeye devam edin, gerekirse sınıfa ve üye düzeyine doğru bir şekilde geçin.

     ![Grupları sınıfa ve üye düzeyine Genişlet](../modeling/media/codemapsexpandtoclassandmember.png "CodeMapsExpandToClassAndMember")

     Koddaki, ancak haritada görünmeyen üyeleri görmek için, bir grubun sol üst köşesindeki **tekrar al Children** Icon ![tekrar al Children simgesine](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") tıklayın.

6. Haritadaki öğelerle ilgili daha fazla öğe görmek için, bir tane seçin ve kod Haritası araç çubuğunda **ilgili öğe göster** ' i seçin, ardından haritaya eklenecek ilgili öğelerin türünü seçin. Alternatif olarak, bir veya daha fazla öğe seçin, kısayol menüsünü açın ve ardından **göster...** öğesini seçin eşlemeye eklenecek ilgili öğelerin türü için seçeneği. Örneğin:

     Bir **derleme**için şunları seçin:

    |||
    |-|-|
    |**Bu başvuruların derlemelerini göster**|Bu derlemenin başvurduğu derlemeleri ekleyin. Dış derlemeler **dışlar** grubunda görünür.|
    |**Buna başvuran derlemeleri göster**|Çözümde bu derlemeye başvuran derlemeleri ekleyin.|

     Bir **ad alanı**için, görünür değilse, **içerilen derlemeyi göster**' i seçin.

     Bir **sınıf** veya **arabirim**için şunları seçin:

    |||
    |-|-|
    |**Temel türleri göster**|Bir sınıf için taban sınıfı ve uygulanan arabirimleri ekleyin.<br /><br /> Bir arabirim için temel arabirimleri ekleyin.|
    |**Türetilmiş türleri göster**|Bir sınıf için türetilmiş sınıfları ekleyin.<br /><br /> Bir arabirim için türetilmiş arabirimleri ve uygulama sınıflarını veya yapılarını ekleyin.|
    |**Bu başvuru türlerini göster**|Tüm sınıfları ve bu sınıfın kullandığı üyeleri ekleyin.|
    |**Buna başvuran türleri göster**|Tüm sınıfları ve bu sınıfı kullanan üyelerini ekleyin.|
    |**Içerilen ad alanını göster**|Üst ad alanını ekleyin.|
    |**Kapsayan ad alanını ve derlemeyi göster**|Üst kapsayıcı hiyerarşisini ekleyin.|
    |**Tüm temel türleri göster**|Yinelemeli olarak taban sınıf veya arabirim hiyerarşisi ekleyin.|
    |**Tüm türetilmiş türleri göster**|Bir sınıf için tüm türetilmiş sınıfları yinelemeli olarak ekleyin.<br /><br /> Bir arabirim için türetilmiş tüm arabirimleri ve uygulama sınıflarını veya yapılarını yinelemeli olarak ekleyin.|

     Bir **Yöntem**için şunları seçin:

    |||
    |-|-|
    |**Bu çağrıların yöntemlerini göster**|Bu yöntemin çağırdığı yöntemleri ekleyin.|
    |**Bu başvuruların alanlarını göster**|Bu yöntemin başvurduğu alanları ekleyin.|
    |**Kapsayan türü göster**|Üst türü ekleyin.|
    |**Kapsayan türü, ad alanını ve derlemeyi göster**|Üst kapsayıcı hiyerarşisini ekleyin.|
    |**Geçersiz kılınan yöntemleri göster**|Diğer yöntemleri geçersiz kılan veya bir arabirimin yöntemini uygulayan bir yöntem için geçersiz kılınan taban sınıflardaki tüm soyut ya da sanal yöntemleri ve varsa arabirimin uygulanan yöntemini ekleyin.|

     Bir **alan** veya **özellik**için şunları seçin:

    |||
    |-|-|
    |**Kapsayan türü göster**|Üst türü ekleyin.|
    |**Kapsayan türü, ad alanını ve derlemeyi göster**|Üst kapsayıcı hiyerarşisini ekleyin.|

     ![Bu üye tarafından çağrılan yöntemleri göster](../modeling/media/codemapsshowrelatedmethods.png "Codemapsshowrelatedmetotları")

7. Haritada ilişkiler gösterilmektedir. Bu örnekte, `Find` yöntemi tarafından çağrılan yöntemler ve çözüm ya da harici olarak.

     ![Kod haritasında belirli bağımlılıkları göster](../modeling/media/codemapsspecificdependenciesintro.png "Codemapsspecificbağımlıcıesgirişi")

8. Haritayı basitleştirmek ve tek tek bölümlere odaklanmak için, kod Haritası araç çubuğunda **Filtreler** ' i seçin ve yalnızca ilgilendiğiniz düğümlerin ve bağlantıların türlerini seçin. Örneğin, çözüm klasörlerinin, derlemelerin ve ad alanlarının görüntülenmesini devre dışı bırakın.

     ![Ekranı basitleştirmek için Filtre bölmesini kullanın](../modeling/media/almcodemapfilterpane.png "ALMCodeMapFilterPane")

## <a name="SeeSourceHeader"></a>Bkz. C ve C++ kaynak dosyaları ve üstbilgi dosyaları arasındaki bağımlılıklar
 Projeler için C++ daha fazla kapsamlı haritalar oluşturmak istiyorsanız, bu projelerde tarama bilgileri derleyici seçeneğini ( **/fr**) ayarlayın. Bkz [./fr,/fr (oluştur. Sbr dosyası)](https://msdn.microsoft.com/library/3fd8f88b-3924-4feb-9393-287036a28896). Aksi durumda, bir ileti görüntülenir ve bu seçeneği ayarlamanızı ister. **Tamam**' ı seçerseniz, bu seçeneği yalnızca geçerli harita için ayarlar. İletiyi sonraki tüm haritalar için gizlemeyi seçebilirsiniz. Bu iletiyi gizlerseniz, yeniden görünmesini sağlayabilirsiniz. Anahtarı `0` veya silmek için aşağıdaki kayıt defteri anahtarını ayarlayın:

 **HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0\NativeProvider: oto Enablesbr**

 Visual C++ projeleri içeren bir çözümü açtığınızda, IntelliSense veritabanını güncelleştirmek biraz zaman alabilir. Bu süre boyunca, IntelliSense veritabanı güncelleştirmeyi bitirene kadar üstbilgi (. h veya `#include`) dosyaları için kod haritaları oluşturmeyebilirsiniz. Visual Studio durum çubuğunda güncelleştirme ilerleme durumunu izleyebilirsiniz. Bazı IntelliSense ayarları devre dışı bırakıldığı için görünen sorunları veya iletileri çözümlemek için bkz. [C ve C++ Code Maps Ile ilgili sorun giderme](#Troubleshooting).

- Çözümünüzdeki tüm kaynak dosyaları ve üstbilgi dosyaları arasındaki bağımlılıkları görmek için **mimari** menüsünde, **Içerme dosyaları grafiğini oluştur**' u seçin.

     ![Yerel kod için bağımlılık grafiği](../modeling/media/dependencygraphgeneral-nativecode.png "DependencyGraphGeneral_NativeCode")

- Şu anda açık olan dosya ile ilgili kaynak dosyaları ve üstbilgi dosyaları arasındaki bağımlılıkları görmek için kaynak dosyayı veya üstbilgi dosyasını açın. Dosya kısayol menüsünü dosyanın içinde herhangi bir yerde açın. **Ekleme dosyalarının grafiğini oluştur**' ı seçin.

     ![.&#45;H dosyası için ilk düzey bağımlılık grafiği](../modeling/media/dependencygraph-native-firstlevel.png "DependencyGraph_Native_FirstLevel")

### <a name="Troubleshooting"></a>C ve C++ Code haritaları sorunlarını giderme
 Bu öğeler C ve C++ Code için desteklenmez:

- Temel türler, üst hiyerarşiyi içeren haritalar üzerinde görünmez.

- Çoğu **göster** menü öğesi C ve C++ Code için kullanılamaz.

  Bu sorunlar, C ve C++ Code için kod haritaları oluşturduğunuzda oluşabilir:

|**Konuda**|**Olası neden**|**Çözünürlüğüne**|
|---------------|------------------------|--------------------|
|Kod eşlemesi oluşturulamadı.|Çözümdeki hiçbir proje başarıyla oluşturulmadı.|Oluşan yapı hatalarını giderip eşlemeyi yeniden oluşturun.|
|**mimari** menüsünden bir kod Haritası oluşturmaya çalıştığınızda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yanıt vermemeye başladı.|Program veritabanı (.pdb) dosyası bozulmuş olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|Çözümü yeniden oluşturun ve tekrar deneyin.|
|IntelliSense göz atma veritabanı için belirli ayarlar devre dışı bırakılır.|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**seçenekleri** iletişim kutusunda belirli IntelliSense ayarları devre dışı bırakılabilir.|Bunları etkinleştirmek için ayarları etkinleştirin.<br /><br /> Bkz. [Seçenekler, metin düzenleyici, CC++/, gelişmiş](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|**Bilinmeyen Yöntemler** bir yöntem düğümünde görünür.<br /><br /> Yöntemin adı çözümlenemediği için bu sorun oluşur.|İkili dosya temel konum değişikliği tablosuna sahip olmayabilir.|Bağlayıcının **/fixed: No** seçeneğini açın.<br /><br /> Bkz. [/Fixed (sabit temel adres)](https://msdn.microsoft.com/library/929bba5e-b7d8-40ed-943e-056aa3710fc5).|
||Program veritabanı (.pdb) dosyası oluşturulmamış olabilir.<br /><br /> .pdb dosyası; tür, yöntem ve kaynak dosya bilgileri gibi hata ayıklama bilgilerini depolar.|Bağlayıcının **/Debug** seçeneğini açın.<br /><br /> Bkz. [/Debug (hata ayıklama bilgisi oluştur)](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103).|
||.pdb dosyasını beklenen konumda açamıyor veya bulamıyor.|.pdb dosyasının beklenen konumlarda var olduğundan emin olun.|
||Hata ayıklama bilgileri, .pdb dosyasından çıkarıldı.|Bağlayıcı içinde **/Pdbçıkarıldı** seçeneği kullanıldıysa, bunun yerine tüm. pdb dosyasını dahil edin.<br /><br /> Bkz. [/Pdbçıkarıldı (özel sembolleri Strip)](https://msdn.microsoft.com/library/9b9e0070-6a13-4142-8180-19c003fbbd55).|
||Arayan bir işlev değildir ve ikili dosyada bir dönüştürücü ya da veri bölümünde bir işaretçidir.|Çağıran bir dönüştürücü olduğunda, dönüştürücü kullanmaktan kaçınmak için `_declspec(dllimport)` kullanmayı deneyin.<br /><br /> Bkz.<br /><br /> -   [genel kurallar ve sınırlamalar](https://msdn.microsoft.com/library/6c48902d-4259-4761-95d4-e421d69aa050)<br />[__declspec (dllimport) kullanarak Işlev çağrılarını Içeri aktarmaya](https://msdn.microsoft.com/library/6b53c616-0c6d-419a-8e2a-d2fff20510b3) -   <br />-   [dllexport, dllimport](https://msdn.microsoft.com/library/ff95b645-ef55-4e72-b848-df44657b3208)|

## <a name="RenderMoreQuickly"></a>Kod eşlemelerinin daha hızlı işlemesini sağlama
 İlk kez bir eşleme oluşturduğunuzda, Visual Studio bulduğu tüm bağımlılıkların dizinini oluşturur. Özellikle büyük çözümler için bu işlem biraz zaman alabilir, ancak performansı daha sonra iyileştirir. Kodunuz değişirse, Visual Studio yalnızca güncelleştirilmiş kodu yeniden dizinler. Haritanın işlemeyi tamamlaması için geçen süreyi en aza indirmek için aşağıdakileri göz önünde bulundurun:

- [Yalnızca ilgilendiğiniz bağımlılıkları eşleyin.](#SeeSpecificSource)

- Tüm çözüm için Haritayı oluşturmadan önce çözüm kapsamını azaltın.

- Kod Haritası araç çubuğunda **derlemeyi atla** düğmesine sahip çözüm için otomatik derlemeyi devre dışı bırakın.

- Kod Haritası araç çubuğundaki üst öğeleri **dahil et** düğmesine sahip otomatik ekleme özelliğini devre dışı bırakın.

- İhtiyacınız olmayan düğümleri ve bağlantıları kaldırmak için doğrudan kod eşleme dosyasını düzenleyin. Haritanın değiştirilmesi temeldeki kodu etkilemez. Bkz. [dgml dosyalarını düzenleyerek kod eşlemelerini özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

  ![Derleme ve ekleme üst öğeleri düğmelerini atla](../modeling/media/codemapsfilterskipbuildicons.png "CodeMapsFilterSkipBuildIcons")

  Visual Studio, 1 GB bellekle çalışabilse de, Visual Studio kod dizinini oluştururken ve Haritayı oluştururken uzun gecikmeleri önlemek için bilgisayarınızın en az 2 GB belleğe sahip olmasını öneririz.

  Bir proje öğesinin **Çıkış Dizinine Kopyala** özelliği **her zaman Kopyala**olarak ayarlandığında, haritalar oluşturmak veya Çözüm Gezgini haritaya öğe eklemek daha fazla zaman alabilir. Bu, artımlı yapılarla ve Visual Studio'nun projeyi her seferinde yeniden oluşturmasıyla ilgili sorunlara neden olabilir. Performansı artırmak için bu özelliği, **daha yeniyse** veya `PreserveNewest`kopyalamak üzere değiştirin. Bkz. [Artımlı derlemeler](../msbuild/incremental-builds.md).

  Tamamlanan eşleme yalnızca başarıyla oluşturulmuş kod için bağımlılıkları gösterir. Belirli bileşenler için yapı hataları oluşursa, bu hatalar haritada görüntülenir. Harita üzerinde mimari kararlar vermeden önce bir bileşenin gerçekten oluşturup bu bağımlılıkları kullandığından emin olun.

## <a name="SavingExporting"></a>Kod eşlemelerini paylaşma

### <a name="share-the-map-with-other-visual-studio-users"></a>Eşlemeyi diğer Visual Studio kullanıcılarıyla paylaşma
 Haritayı kaydetmek için **Dosya** menüsünü kullanın.

 veya

 Haritayı belirli projenin bir parçası olarak kaydetmek için harita araç çubuğunda, **paylaşma**, \<*codemapname*> **. dgml** **' i** seçin ve ardından Haritayı kaydetmek istediğiniz projeyi seçin.

 ![Haritayı başka bir projeye taşıma](../modeling/media/codemapsmovemapmenu.png "CodeMapsMoveMapMenu")

 Visual Studio, Haritayı Visual Studio Enterprise ve Visual Studio Professional diğer kullanıcılarıyla paylaşabileceğiniz bir. dgml dosyası olarak kaydeder.

> [!NOTE]
> Visual Studio Professional kullananlarla bir Haritayı paylaşmadan önce, herhangi bir grubu genişlettikten, gizli düğümleri ve çapraz grup bağlantılarını gösterdiğinizden ve başkalarının haritada görmesini istediğiniz silinmiş düğümleri aldığınızdan emin olun. Aksi takdirde, diğer kullanıcıların bu öğeleri görmesi mümkün olmayacaktır.
>
> Modelleme projesinde olan veya bir modelleme projesinden başka bir konuma kopyalanmış olan bir Haritayı kaydettiğinizde aşağıdaki hata ortaya çıkabilir:
>
> " *Dosya adı* proje dizininin dışına kaydedilemez. Bağlantılı öğeler desteklenmez."
>
> Visual Studio hatayı gösterir, ancak kaydedilen sürümü de oluşturur. Hatayı önlemek için Haritayı modelleme projesinin dışında oluşturun. Ardından istediğiniz konuma kaydedebilirsiniz. Yalnızca çözümdeki başka bir konuma dosya kopyalama ve onu kaydetmeye çalışmak başarısızlıkla sonuçlanacaktır.

### <a name="export-the-map-as-an-image-so-you-can-copy-it-into-other-applications-such-as-microsoft-word-or-powerpoint"></a>Haritayı, Microsoft Word veya PowerPoint gibi diğer uygulamalara kopyalayabilmeniz için bir görüntü olarak dışarı aktarın

1. Kod Haritası araç çubuğunda, **paylaşma**, **e-posta olarak görüntü** veya **görüntü kopyalama**' yı seçin.

2. Görüntüyü başka bir uygulamaya yapıştırın.

### <a name="export-the-map-as-an-xps-file-so-you-can-see-it-in-xml-or-xaml-viewers-like-internet-explorer"></a>Internet Explorer gibi XML veya XAML görüntüleyicilerde görebilmeniz için Haritayı XPS dosyası olarak dışarı aktarın

1. Kod Haritası araç çubuğunda, **paylaşma**, **e-posta ' ı taşınabilir XPS** veya **Taşınabilir XPS olarak kaydet**' i seçin.

2. Dosyayı kaydetmek istediğiniz yere gidin.

3. Kod eşlemesini adlandırın. **Farklı kaydet türü** kutusunun **XPS dosyaları (\*. XPS)** olarak ayarlandığından emin olun. **Kaydet**' i seçin.

## <a name="what-else-can-i-do"></a>Başka ne yapabilirim?

- [Uygulamalarınızda hata ayıklamak için kod haritalarını kullanma](../modeling/use-code-maps-to-debug-your-applications.md)

- [Hata ayıklarken çağrı yığınında eşleştirme yöntemleri](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)

- [Kod haritası çözümleyicilerini kullanarak olası sorunları bulma](../modeling/find-potential-problems-using-code-map-analyzers.md)

- [Kod haritalarına göz atma ve bunları yeniden düzenleme](../modeling/browse-and-rearrange-code-maps.md)

- [DGML dosyalarını düzenleyerek kod haritalarını özelleştirme](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
