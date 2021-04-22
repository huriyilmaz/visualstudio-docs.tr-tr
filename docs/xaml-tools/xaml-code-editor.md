---
title: XAML kod düzenleyici
description: Visual Studio 'da XAML kod Düzenleyicisi turuna katılın
ms.date: 06/16/2020
ms.topic: overview
f1_keywords:
- VS.XamlEditor
monikerRange: vs-2019
ms.custom: contperf-fy21q4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 672bfa6b28e364351f262cb2a2c6e2258ecd9746
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879401"
---
# <a name="xaml-code-editor"></a>XAML kod düzenleyici

[Visual STUDIO IDE](../get-started/visual-studio-ide.md) 'deki xaml kod Düzenleyicisi, Windows platformu ve [Xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/)için WPF ve UWP uygulamaları oluşturmak için ihtiyacınız olan tüm araçları içerir. Bu makalede, XAML tabanlı uygulamalar geliştirirken kod düzenleyicisinin oynadığı rol ve Visual Studio 2019 ' deki XAML kod Düzenleyicisi için benzersiz olan özellikler özetlenmektedir.

Başlamak için, açık bir WPF projesiyle IDE (tümleşik geliştirme ortamı) konusuna göz atalım. Aşağıdaki görüntüde, XAML kod Düzenleyicisi ile birlikte kullanacağınız anahtar IDE araçlarından bazıları gösterilmektedir.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="XAML 'de açık bir WPF projesiyle Visual Studio 2019 IDE" lightbox="media/xaml-code-editor-overview-lrg.png":::

Görüntünün sol alt kısmından saat yönünde, anahtar IDE araçları aşağıdaki gibidir:

- **[Xaml kod Düzenleyicisi](#xaml-code-editor-ui)** penceresi &mdash; &mdash; kodunuzu oluşturduğunuz ve düzenlediğiniz bu makalenin konusu.
- Kullanıcı arabiriminizi tasarlayabileceğiniz **[XAML Tasarımcısı](creating-a-ui-by-using-xaml-designer-in-visual-studio.md)** pencere.
- Kullanıcı arabirimine denetim eklediğiniz **[araç kutusu](../ide/reference/toolbox.md)** yerleştirilebilir penceresi.
- Kodunuzu çalıştırdığınız ve hata ayıklamanın bulunduğu **[hata ayıklama](../debugger/debugger-feature-tour.md)** düğmesi. <br>( [Xaml sık yeniden yükleme](xaml-hot-reload.md)ile hata ayıklarken, kodunuzu gerçek zamanlı olarak da düzenleyebilirsiniz.)
- Dosyalarınızı, projelerinizi ve çözümlerinizi yönettiğiniz **[Çözüm Gezgini](../ide/solutions-and-projects-in-visual-studio.md)** pencere.
- Kullanıcı arabirimlerinizin görünüşünü ve Kullanıcı arabirimi denetimlerinin nasıl çalıştığını değiştirdiğiniz **[Özellikler](../ide/reference/properties-window.md)** penceresi.

Devam etmek için XAML kod Düzenleyicisi hakkında daha fazla bilgi edinin.

## <a name="xaml-code-editor-ui"></a>XAML kod Düzenleyicisi Kullanıcı arabirimi

XAML uygulamaları için kod Düzenleyicisi penceresi ayrıca standart IDE 'imizde görüntülenen bazı Kullanıcı arabirimi (Kullanıcı arabirimi) öğelerini paylaşır, ancak XAML uygulamalarını geliştirmeyi kolaylaştırmak için bazı benzersiz özellikler de içerir.

XAML kod Düzenleyicisi penceresinin kendisi için bir görünüm aşağıda verilmiştir.

![Visual Studio 'da XAML kod Düzenleyicisi penceresi](media/xaml-code-editor-window.png "Visual Studio 2019 ' de XAML kod Düzenleyicisi penceresinin ekran görüntüsü")

Daha sonra, kod Düzenleyicisi 'ndeki Kullanıcı arabirimi öğelerinin her birinin işlevlerine göz atalım.

### <a name="first-row"></a>İlk satır

XAML kodu penceresinin en üstündeki ilk satırda, sol taraftaki bir **Tasarım** sekmesi, **takas bölmeleri** düğmesi, **XAML** sekmesi ve bir **açılan xaml** düğmesi bulunur.

![Visual Studio 'daki XAML kod Düzenleyicisi penceresinin en üstteki iki satırı, vurgulanan ilk satırın sol tarafıdır](media/xaml-code-editor-top-row-left.png "Visual Studio 2019 ' deki XAML kod Düzenleyicisi penceresinin ilk iki üst satırı ekran görüntüsü, sol taraftaki Kullanıcı arabirimi öğeleri vurgulanır")

Şu şekilde çalışır:

- **Tasarım** SEKMESI, xaml kod düzenleyicisinden odak XAML Tasarımcısı olarak değiştirir.
- **Bölmeleri Değiştir** düğmesi, XAML Tasarımcısı konumunu ve xaml kod düzenleyicisini IDE 'de tersine çevirir.
- **Xaml** sekmesi, odağı xaml kod düzenleyicisine geri dönüştürür.
- **Aç xaml** Button, IDE dışında olan ayrı bir xaml kod Düzenleyicisi penceresi oluşturur.

Sağ tarafta devam eden **dikey bir bölme** düğmesi, **yatay bölme** düğmesi ve **bölmeleri Daralt** düğmesi vardır.

![Visual Studio 'daki XAML kod Düzenleyicisi penceresinin en üstteki iki satırı, vurgulanan ilk satırın sağ tarafından önce](media/xaml-code-editor-top-row-right.png "Visual Studio 2019 ' de XAML kod Düzenleyicisi penceresinin ilk iki üst satırı, sağdaki Kullanıcı arabirimi öğelerinin vurgulandığı ekran görüntüsü")

Şu şekilde çalışır:

- **Dikey bölme** düğmesi, XAML Tasarımcısı konumunu ve IDE 'deki xaml kod düzenleyicisini yatay hizalamadan dikey hizalamasına dönüştürür.
- **Yatay bölme** düğmesi, XAML Tasarımcısı konumunu ve IDE 'deki xaml kod düzenleyicisini dikey hizalamadan yatay hizalamasına dönüştürür.
- **Bölmeyi daralt** düğmesi, alt bölmedeki, kod Düzenleyicisi mi yoksa tasarımcı olsun ne olduğunu daraltmanızı sağlar. (Alt bölmeyi geri yüklemek için, şimdi **Genişlet bölmesi** düğmesi olarak adlandırılan aynı düğmeyi yeniden seçin.)

<!-- [!TIP]
> You can run two parallel instances of the XAML code editor concurrently by using both the **Pop Out XAML** button and the **Expand Pane** button.
>
> You might find it useful to have one larger window open that reveals more of your code in context and a smaller pane open that has its focus directly on the code that you're working on. -->

### <a name="second-row"></a>İkinci satır

XAML kod penceresinin en üstündeki ikinci satırda, iki pencere açılan listesi bulunur. Ancak, bu kullanıcı arabirimi öğeleri için araç Ipucunu görüntülediğinizde, bunları daha sonra "öğe: pencere" ve "üye: pencere" olarak tanımlar.

![Visual Studio 'da, her iki pencere açılan listesinin de görünür olduğu, XAML kod Düzenleyicisi penceresinin ikinci en üst satırı](media/xaml-code-editor-top-row-windows.png "Visual Studio 2019 ' deki XAML kod Düzenleyicisi penceresinin iki üst satırı, her iki pencere açılan listesinin de görünür olduğu ekran görüntüsü")

Pencere açılan listeleri, aşağıdaki gibi farklı işlevlere sahiptir:

- Sol taraftaki **pencere öğesi** , eşdüzey veya üst öğeleri görüntülemenize ve gezinmenize yardımcı olur.

  Özellikle, kodunuzun etiket yapısını ortaya çıkaran bir anahat benzeri görünüm gösterir. Listeden seçim yaptığınızda, kod düzenleyicisine odaklanmanız seçtiğiniz öğeyi içeren kod satırına yaslanacak.

    ![Öğe: Visual Studio 'da pencere açılan listesi](media/xaml-element-window-dropdown.png "Öğenin ekran görüntüsü: Visual Studio 2019 'de pencere açılan listesi")

- Sağ taraftaki **üye: pencere** , öznitelik veya alt öğeleri görüntülemenizi ve bu öğelere gitmenizi sağlar.

    Özellikle, kodunuzda özelliklerin bir listesini gösterir. Listeden seçim yaptığınızda, kod düzenleyicisine odaklanmanız seçtiğiniz özelliği içeren kod satırına yaslanacak.

    ![Üye: Visual Studio 'da pencere açılan listesi](media/xaml-member-window-dropdown.png "Üyenin ekran görüntüsü Visual Studio 2019 ' de pencere açılan listesi")

### <a name="middle-pane-code-editor"></a>Orta bölme, kod Düzenleyicisi

Orta bölme, XAML kod düzenleyicisinin "Code" kısmıdır. [IDE kod düzenleyicisinde](../get-started/tutorial-editor.md)bulacağınız özelliklerin çoğunu içerir. XAML kodunuzu geliştirmenize yardımcı olabilecek birçok evrensel IDE özelliği ile iletişime geçeceğiz. Ayrıca, IDE içindeki benzersiz XAML özelliklerini de vurgulayacağız.

![Visual Studio 'da yalnızca orta bölme olan XAML kod Düzenleyicisi](media/xaml-code-editor-middle.png "Visual Studio 2019 ' de yalnızca orta bölme olan XAML kod Düzenleyicisi 'nin ekran görüntüsü")

#### <a name="quick-actions"></a>Hızlı Eylemler

Tek bir eylem ile kodu yeniden düzenlemek, oluşturmak veya başka şekilde değiştirmek için [Hızlı işlemleri](../ide/quick-actions.md) kullanabilirsiniz.

Örneğin, hızlı eylemleri kullanarak gerçekleştirebileceğiniz yararlı bir görev, **MainWindow. xaml. cs** sekmesindeki C# kodundan **gereksiz kullanımlar kaldırmak** içindir.

Aşağıdaki adımları uygulayın:

1. Bir using ifadesinin üzerine gelin, ampul simgesini seçin ve ardından açılan listeden gereksiz kullanımları **Kaldır** ' ı seçin.

    ![Hızlı Eylemler menüsünde IDE düzenleyicisinin "gereksiz kullanımları kaldır" seçeneği](media/xaml-code-editor-remove-usings.png "Hızlı Eylemler menüsünde IDE düzenleyicisinin gereksiz kullanımları kaldırma seçeneğinin ekran görüntüsü")

1. **Belge**, **Proje** veya **çözüm** içindeki tüm oluşumları mı onarmak istediğinizi seçin.
1. **Önizleme** iletişim kutusunu görüntüleyin ve ardından **Uygula**' yı seçin.

Bu özelliğe menü çubuğundan de erişebilirsiniz. Bunu yapmak için,   >  **IntelliSense**'i  >  **Kaldır ve Sırala deyimlerini** Düzenle ' yi seçin.

Using ayarları hakkında daha fazla bilgi için bkz. [using using](../ide/reference/sort-usings.md) Page. IntelliSense hakkında daha fazla bilgi için bkz. [Visual Studio 'Da IntelliSense](../ide/using-intellisense.md) sayfası. Geliştiricilerin hızlı eylemleri kullandığı tipik bazı yollarla ilgili daha fazla bilgi için bkz. [ortak hızlı eylemler](../ide/common-quick-actions.md) sayfası.

#### <a name="change-tracking"></a>Değişiklik izleme

Sol kenar boşluğunun rengi, bir dosyada yaptığınız değişiklikleri izlemenize olanak sağlar. Renklerin, aldığınız eylemlerle nasıl ilişkilendirileceğiyle ilgilidir:

- Dosya açıldığı ancak kaydedilmediği için yaptığınız değişiklikler sol kenar boşluğunda (seçim kenar boşluğu olarak bilinir) **sarı** bir çubukla gösterilir.

    ![Sarı çubukla kod düzenleyici düzenleme](media/code-editor-edit-yellow.png "Seçim kenar boşluğunda sarı çubukla işaretlenmiş bir değişikliği olan kod düzenleyicisinin ekran görüntüsü.")

- Değişiklikleri kaydettikten sonra (ancak dosyayı kapatmadan önce), çubuk **yeşile** döner.

    ![Yeşil çubukla kod Düzenleyicisi düzenleme](media/code-editor-edit-green.png "Seçim kenar boşluğunda yeşil çubukla işaretlenmiş bir değişikliği olan kod düzenleyicisinin ekran görüntüsü.")

Bu özelliği devre dışı bırakmak ve açmak için **metin Düzenleyicisi** ayarları 'ndaki (**Araçlar**   >  **Seçenekler**  >  **metin Düzenleyicisi**) değişiklikleri izle seçeneğini değiştirin.

&mdash;Kod dizeleri altında görünen dalgalı çizgileri ("dalgalı çizgiler" olarak da bilinir) içerecek şekilde değişiklik izleme hakkında daha fazla bilgi için, &mdash; [Visual Studio kod Düzenleyicisi sayfasının özelliklerinin](../ide/writing-code-in-the-code-and-text-editor.md) **[Düzenleyici özellikleri](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** bölümüne bakın.

#### <a name="right-click-context-menu"></a>Sağ tıklama bağlam menüsü

Kodunuzu XAML kod düzenleyicisinde düzenlediğinizde, sağ tıklama bağlam menüsünü kullanarak erişebileceğiniz çeşitli özellikler vardır. Bu özelliklerin çoğu, Visual Studio IDE 'de evrensel olarak kullanılabilir, ancak bazıları bir tasarım penceresiyle birlikte kod Düzenleyicisi kullanmaya özgüdür.

![Visual Studio 2019 ' de XAML kod Düzenleyicisi 'nin sağ tıklama bağlam menüsünün ekran görüntüsü.](media/xaml-code-editor-right-click-menu.png)

Her bir özelliğin ne olduğu ve nasıl yararlı olduğu aşağıda verilmiştir:

- **Kodu görüntüle** -tasarım PENCERESINI ve xaml kod düzenleyicisini içeren varsayılan görünümün yanında sekmeli olan programlama dili kodu penceresini açar.
- **Görünüm Tasarımcısı** -tasarım PENCERESINI ve xaml kod düzenleyicisini içeren varsayılan görünümü açar. (Zaten varsayılan görünümlerde varsa, hiçbir şey yapmaz.)
- **Hızlı Eylemler ve yeniden düzenlemeler** -şunların, tek bir eylem ile kodu oluşturur veya başka bir şekilde değiştirir. Kodun üzerine geldiğinizde, hızlı bir eylem veya yeniden düzenleme kullanılabilir olduğunda bir ampul simgesi görürsünüz. <br>Ayrıca bkz: [hızlı eylemler](../ide/quick-actions.md) ve yeniden [düzenleme kodu](../ide/refactoring-in-visual-studio.md).
- **Yeniden adlandır...** -Yalnızca ad alanlarını yeniden adlandırır. Yeniden adlandırılacak bir ad alanınız yoksa, "yalnızca ad alanı önekleri yeniden adlandırılabilir" ifadesini içeren bir hata iletisi alırsınız.
- **Ad alanlarını kaldırma ve sıralama** -kullanılmayan ad alanlarını kaldırır ve kalan ad alanlarını sıralar.
- **Göz atma** -bir türün tanımını düzenleyicide geçerli konumundan çıkmadan önizleme. <br>Ayrıca [bkz. göz atma ve açıklama](../ide/go-to-and-peek-definition.md#peek-definition) [tanımı kullanarak kodu görüntüleme ve düzenleme](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).
- **Tanıma Git** -bir tür veya üyenin kaynağına gider ve sonucu yeni bir sekmede açar. <br>Ayrıca bkz: [Tanıma Git](../ide/go-to-and-peek-definition.md#go-to-definition).
- Şununla **çevrele...** -Seçili bir kod bloğu etrafında eklenen kod parçacıkları ile surround kullanın. <br>Ayrıca bkz: [genişletme parçacıkları ve surround-kod parçacıkları](../ide/code-snippets.md#expansion-snippets-and-surround-with-snippets).
- **Kod parçacığı Ekle** -imleç konumuna bir kod parçacığı ekler.
- **Kesin** -açıklama
- Kendini Açıklama **Kopyala**
- Kendini Açıklama **Yapıştır**
- **Anahat oluşturma** -kodun bölümlerini genişletme ve daraltma. <br>Ayrıca bkz: Ana [hat](../ide/outlining.md).
- **Kaynak denetimi** -açık kaynaklı bir depoya kod katkıları geçmişini görüntüleyin.

### <a name="middle-pane-scroll-bar"></a>Orta bölme, kaydırma çubuğu

Kaydırma çubuğu, kodunuzda ilerleyerek daha fazlasını yapabilir. Başka bir kod Düzenleyicisi bölmesi açmak için de kullanabilirsiniz. Ayrıca, buna ek açıklamalar ekleyerek veya farklı görüntüleme modlarını kullanarak daha verimli bir şekilde kod sağlamanıza yardımcı olması için kaydırma çubuğunu kullanabilirsiniz.

#### <a name="split-the-code-window"></a>Kod penceresini bölme

Kod düzenleyicisinin kaydırma çubuğunda, sağ üst kısımdaki bir **bölünmüş** düğme vardır. Bunu seçtiğinizde, başka bir kod Düzenleyicisi bölmesi açabilirsiniz. Bu, birbirinden bağımsız olarak çalıştıkları için yararlıdır, böylece bunları farklı konumlarda kod üzerinde çalışmak için kullanabilirsiniz.

![Bölmenin sağ üst köşesinde bulunan bölünmüş düğme ile Visual Studio 2019 ' de XAML kod düzenleyicisinin orta bölmesini gösteren ekran görüntüsü.](media/code-editor-split-window-button.png)

Bir düzenleyici penceresinin nasıl bölüneceği hakkında daha fazla bilgi için, [düzenleyici pencerelerini yönetme](../ide/how-to-manage-editor-windows.md) sayfasına bakın.

#### <a name="use-annotations-or-map-mode"></a>Ek açıklamaları veya eşleme modunu kullan

Ayrıca, kaydırma çubuğunun görünümünü ve içerdiği ek özellikleri değiştirebilirsiniz. Örneğin, çok sayıda kişi, kod değişiklikleri, kesme noktaları, yer işaretleri, hatalar ve giriş işareti konumu gibi görsel ipuçları sağlayan kaydırma çubuğuna *ek açıklamalar* eklemek gibi.

Diğerleri, kaydırma çubuğunda küçük bir kod satırını görüntüleyen *harita modunu* kullanarak daha fazla teşekkür ederiz. Bir dosyada çok fazla kod bulunan geliştiriciler, eşleme modunun, varsayılan kaydırma çubuğunu kullanmaktan daha etkili şekilde kod satırlarına izlemelerinin ne olduğunu fark edebilir.

Kaydırma çubuğunun varsayılan ayarlarının nasıl değiştirileceği hakkında daha fazla bilgi için,  [kaydırma çubuğunu özelleştirme](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) sayfasına bakın.

## <a name="xaml-specific-features"></a>XAML 'e özgü özellikler

Aşağıdaki özelliklerin çoğu, Visual Studio IDE 'de evrensel olarak sunulmaktadır, ancak bunları XAML geliştiricileri için kodlamayı daha kolay hale getirir.

### <a name="xaml-code-snippets"></a>XAML kod parçacıkları

Kod parçacıkları, sağ tıklama bağlam menüsü komut **parçacığını** veya klavye kısayollarının bir birleşimini (**CTRL** + **K**, **CTRL** + **X**) kullanarak bir kod dosyasına ekleyebileceğiniz yeniden kullanılabilir kod bloklarıdır. IntelliSense 'in hem yerleşik kod parçacıkları hem de el ile eklediğiniz tüm özel kod parçacıkları için çalışan XAML kod parçacıklarını göstermesini desteklediğinden, [IntelliSense](../ide/using-intellisense.md) 'i geliştirdik. Bazı kullanıma hazır xaml parçacıkları,,, `#region` `Column definition` ve içerir `Row definition` `Setter` `Tag` .

![IntelliSense 'de gösterilen XAML kod parçacığı seçenekleri ile XAML kod Düzenleyicisi](media/xaml-code-snippets.png "IntelliSense 'de gösterilen XAML kod parçacığı seçenekleri ile XAML kod Düzenleyicisi ekran görüntüsü")

Daha fazla bilgi için bkz. [kod parçacıkları](../ide/code-snippets.md) ve [C# kod parçacıkları](../ide/visual-csharp-code-snippets.md) sayfaları.

### <a name="xaml-region-support"></a>XAML #region desteği

Visual Studio 2015 ' den itibaren, WPF ve UWP 'de XAML geliştiricileri ve daha yeni bir deyişle [Xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/)içinde çok daha fazla destek sunuyoruz #region. Visual Studio 2019 ' de #region destek için artımlı geliştirmeler yapmaya devam ediyoruz. Örneğin, [sürüm 16,4](/visualstudio/releases/2019/release-notes-v16.4/) ve üzeri sürümlerde #region seçenekler, yazma işlemine başladığınızda gösterilmektedir `<!` .

![IntelliSense 'de gösterilen #region seçenekleri olan XAML kod Düzenleyicisi](media/code-editor-xaml-region.png "IntelliSense 'de gösterilen #region seçenekleri olan XAML kod düzenleyicisinin ekran görüntüsü")

Kodunuzu genişletmek veya daraltmak istediğiniz bölümlerini gruplandırmak istediğinizde, bölgeleri kullanabilirsiniz.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Bölgeler hakkında daha fazla bilgi için [#region (C# Başvurusu)](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) sayfasına bakın. Kod bölümlerini genişletme ve daraltma hakkında daha fazla bilgi için, bkz. [anahat](../ide/outlining.md) sayfası.

### <a name="xaml-comments"></a>XAML açıklamaları

Geliştiriciler genellikle yorumlarını kullanarak kodlarını belgelemek tercih eder. **MainWindow. xaml** sekmesindeki xaml koduna aşağıdaki yollarla açıklama ekleyebilirsiniz:

- `<!--`Açıklamadan önce girin ve `-->` açıklamadan sonra ekleyin.
- `<!`Seçenekler listesinden öğesini girip seçin `!--` .

  ![XAML kod Düzenleyicisi Açıklama Ekle iletişim kutusunu sağ tıklatın](media/xaml-code-editor-comments.png "XAML kod düzenleyicisine yorum eklemek için sağ tıklama kısayol menüsünün ekran görüntüsü")

- Bir açıklama ile çevrelemek istediğiniz kodu seçin ve ardından IDE 'deki araç çubuğundan **yorum** düğmesini seçin. Eylemi tersine çevirmek için, **Açıklama** Kaldır düğmesini seçin.

  ![IDE araç çubuğundaki yorum düğmesi ve Açıklama Ekle düğmesi](media/comment-undo-comment-buttons.png "IDE araç çubuğundaki yorum düğmesinin ve açıklama düğmesinin ekran görüntüsü")

- Bir yorum ile çevrelemek istediğiniz kodu seçin ve ardından **CTRL** + **K**, **CTRL** + **C** tuşlarına basın. Seçili kodun açıklamasını eklemek için **CTRL** + **K**, **CTRL** + **U** tuşlarına basın.

**MainWindow. xaml. cs** sekmesindeki C# kodunda açıklamaları kullanma hakkında daha fazla bilgi Için, [belge açıklamaları](/dotnet/csharp/language-reference/language-specification/documentation-comments/) sayfasına bakın.

### <a name="xaml-lightbulbs"></a>XAML lightbs

XAML kodunuzda görünen ampul simgeleri, kodu yeniden düzenlemek, oluşturmak veya başka bir şekilde değiştirmek için kullanabileceğiniz [hızlı eylemlerin](../ide/quick-actions.md) bir parçasıdır.

XAML kodlama deneyiminize nasıl yararlanabileceği hakkında birkaç örnek aşağıda verilmiştir:

- **Gereksiz ad alanlarını kaldırın**. XAML kod düzenleyicisinde, gereksiz ad alanları soluk metin halinde görünür. İşaretçinizi kullanarak imlecinizi gereksiz yere getirdiğinizde bir ampul görüntülenir. Açılan listeden **gereksiz ad alanlarını kaldır** seçeneğini belirlediğinizde, kaldırabilmeniz için bir önizleme görürsünüz.

  ![XAML kod Düzenleyicisi 'nin gereksiz ad alanlarını kaldırma hızlı eylem ampul seçeneğinden](media/xaml-code-editor-dimmed-namespaces-preview.png "Hızlı eylem ampul kullanılarak görüntülenen XAML kod düzenleyicisinin gereksiz ad alanlarını kaldır seçeneğinin ekran görüntüsü")

- **Ad alanını yeniden adlandır**. Bir ad alanını vurguladıktan sonra sağ tıklama bağlam menüsünde bulunan bu özellik, bir ayarın birden çok örneğini tek seferde değiştirmeyi kolaylaştırır. Bu özelliğe ayrıca menü çubuğunu kullanarak, yeniden düzenleme   >    >  **yeniden adlandırma**' yı düzenleyerek veya **CTRL** + **r** tuşuna basarak ve sonra da **CTRL** + **r** tuşuna basarak erişebilirsiniz.

  ![Sağ tıklama bağlam menüsünden XAML kod düzenleyicisinin ad alanını yeniden adlandır seçeneği](media/code-editor-rename-namespace.png "Sağ tıklama bağlam menüsü kullanılarak görüntülenen XAML kod Düzenleyicisi 'nin ad alanı değiştirme seçeneğinin ekran görüntüsü")

  Daha fazla bilgi için bkz. [kod sembolünü yeniden düzenleme](../ide/reference/rename.md) sayfası.

### <a name="conditional-xaml-for-uwp"></a>UWP için koşullu XAML

Koşullu XAML, XAML biçimlendirmesinde [Apiınformation. ısaicontractsun](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) metodunu kullanmak için bir yol sağlar. Bu, arka plan kodu kullanmaya gerek kalmadan, bir API 'nin varlığına göre biçimlendirme içinde özellikleri ayarlamanıza ve nesnelerin örneklendirietmenize olanak tanır.

Daha fazla bilgi için bkz. [koşullu xaml](/windows/uwp/debug-test-perf/conditional-xaml/) sayfası ve [Masaüstü uygulamaları (XAML Adaları) SAYFASıNDA konak UWP XAML denetimleri](/windows/apps/desktop/modernize/xaml-islands/) .

### <a name="xaml-structure-visualizer"></a>XAML yapı görselleştiricisi

Kod düzenleyicisindeki yapı görselleştiricisi özelliği, kodunuzda açık ve kapalı etiket öğelerini eşleşen, dikey kesikli çizgiler olan yapı Kılavuzu çizgilerini gösterir. Bu dikey çizgiler, mantıksal blokların nerede başlayıp bitmekte olduğunu görmeyi kolaylaştırır.

Daha fazla bilgi için bkz. [gezinme kodu](../ide/navigating-code.md) sayfası.

### <a name="intellicode-for-xaml"></a>XAML için ıntellicode

Kodunuza bir XAML etiketi eklediğinizde, genellikle sol açılı köşeli ayraç ile başlar `<` . Bu açılı ayraç yazdığınızda, daha popüler XAML etiketlerinin birkaçını listeleyen bir ıntellicode menüsü belirir. Kodunuza hızlıca eklemek istediğiniz birini seçin.

Intellicode seçimlerini, listenin en üstünde göründüğünden ve başlangıçlar olduğundan tanıyabilirsiniz.

![XAML metin Düzenleyicisi için ıntellicode listesi](media/xaml-intellicode-selection.png "XAML metin Düzenleyicisi için ıntellicode listesinin ekran görüntüsü")

Daha fazla bilgi için bkz. [ıntellicode 'A genel bakış](/visualstudio/intellicode/overview/) sayfası.

### <a name="settings"></a>Ayarlar

Visual Studio IDE 'deki *Tüm* ayarlar hakkında daha fazla bilgi için, bkz. [Kod Düzenleyicisi sayfasının özellikleri](../ide/writing-code-in-the-code-and-text-editor.md) .

## <a name="xaml-optional-settings"></a>XAML isteğe bağlı ayarları

XAML kod Düzenleyicisi için varsayılan ayarları değiştirmek üzere [Seçenekler](../ide/reference/options-dialog-box-visual-studio.md) iletişim kutusunu kullanabilirsiniz. Ayarları görüntülemek için **Araçlar**  >  **Seçenekler**  >  **metin düzenleyici**  >  **xaml**' yi seçin.

![XAML metin Düzenleyicisi için seçenekler listesi](media/xaml-tools-options.png "XAML metin Düzenleyicisi için seçenekler listesinin ekran görüntüsü")

> [!NOTE]
> Ayrıca, Seçenekler iletişim kutusuna erişmek için klavye kısayollarını da kullanabilirsiniz. Şöyle açıklanmaktadır:  + IDE aramak için CTRL **Q** tuşlarına basın, **Seçenekler** yazın ve ardından **ENTER** tuşuna basın. Sonra,  + Seçenekler iletişim kutusunda CTRL **E** ' ye basın, **metin düzenleyici** yazın, **ENTER** tuşuna basın, **xaml** yazın ve ardından **ENTER** tuşuna basın.
>
> Klavye kısayolları hakkında daha fazla bilgi için bkz. [Visual Studio Için kısayol ipuçları](../ide/productivity-shortcuts.md#code-editor) sayfası.

### <a name="universal-text-editor-options"></a>Evrensel metin düzenleyici seçenekleri

XAML için [Seçenekler](../ide/reference/options-text-editor-xaml-formatting.md) iletişim kutusunda, aşağıdaki ilk üç öğe, VISUAL Studio IDE 'nin desteklediği tüm programlama dillerinde evrendir. Bu seçenekler ve bunların nasıl kullanılacağı hakkında daha fazla bilgi edinmek için aşağıdaki tablodaki bağlantılı bilgileri ziyaret edin.

|Name  |Daha fazla bilgi  |
|---------|---------|
|Genel  | [Seçenekler iletişim kutusu: tüm diller > metin Düzenleyicisi](../ide/reference/options-text-editor-all-languages.md) |
|Kaydırma çubukları | [Seçenekler, metin düzenleyici, tüm diller, kaydırma çubukları](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Sekmeler  |  [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>XAML 'e özgü metin düzenleyici seçenekleri

Aşağıdaki tabloda, XAML tabanlı uygulamalar geliştirirken, düzen deneyiminizi geliştirebileceğiniz [Seçenekler](../ide/reference/options-text-editor-xaml-formatting.md) iletişim kutusundaki ayarlar listelenmektedir. Bu seçenekler ve bunların nasıl kullanılacağı hakkında daha fazla bilgi edinmek için bağlantılı bilgileri ziyaret edin.

|Name  |Daha fazla bilgi  |
|---------|---------|
|Biçimlendirme | [Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme](../ide/reference/options-text-editor-xaml-formatting.md) |
|Çeşitli |  [Seçenekler, metin düzenleyici, XAML, çeşitli](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> **Çeşitli** bölümde **olay işleyicisi yöntem adı** ayarı, özellikle xaml geliştiricileri için yararlıdır. Bu ayar, yeni olduğu için varsayılan olarak *kapalıdır* , ancak kodunuzda doğru büyük/küçük harfleri desteklemek için bunu *Açık* olarak ayarlamanızı öneririz.

## <a name="next-steps"></a>Sonraki adımlar

Uygulamanızı hata ayıklama modunda çalıştırırken kodunuzun gerçek zamanlı olarak nasıl düzenleneceği hakkında daha fazla bilgi edinmek için bkz. [xaml Hot Reload yükleme](xaml-hot-reload.md) sayfası.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio kod Düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [UWP uygulamalarında XAML](/windows/uwp/xaml-platform/xaml-overview/)
- [Xamarin. Forms uygulamalarındaki XAML](/xamarin/xamarin-forms/xaml/)
- [Xamarin mobil uygulama geliştirme (Mac)](/visualstudio/mac/xamarin/)
- [Mac için Visual Studio 2019-IDE turu (Mac)](/visualstudio/mac/ide-tour/)
