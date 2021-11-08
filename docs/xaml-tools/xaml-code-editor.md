---
title: XAML kod düzenleyici
description: Visual Studio XAML kod Düzenleyicisi turuna katılın
ms.date: 06/16/2020
ms.topic: overview
f1_keywords:
- VS.XamlEditor
monikerRange: '>=vs-2019'
ms.custom: contperf-fy21q4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: 92b95174862d7d0a601c4083347ef44d2203ec8e
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132001344"
---
# <a name="xaml-code-editor"></a>XAML kod düzenleyici

[Visual Studio ıde](../get-started/visual-studio-ide.md) 'deki XAML kod düzenleyicisi, Windows platformu ve [Xamarin. Forms](/xamarin/xamarin-forms/user-interface/text/editor/)için WPF ve UWP uygulamaları oluşturmak için ihtiyacınız olan tüm araçları içerir. bu makalede, xaml tabanlı uygulamalar geliştirirken kod düzenleyicisinin oynadığı rol ve Visual Studio 2019 ' deki xaml kod düzenleyicisi için benzersiz olan özellikler özetlenmektedir.

Başlamak için, açık bir WPF projesiyle IDE (tümleşik geliştirme ortamı) konusuna göz atalım. Aşağıdaki görüntüde, XAML kod Düzenleyicisi ile birlikte kullanacağınız anahtar IDE araçlarından bazıları gösterilmektedir.

:::image type="content" source="media/xaml-code-editor-overview-sml.png" alt-text="XAML 'de açık bir WPF projesiyle Visual Studio 2019 ıde" lightbox="media/xaml-code-editor-overview-lrg.png":::

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

![Visual Studio XAML kod Düzenleyicisi penceresi](media/xaml-code-editor-window.png "Visual Studio 2019 ' de XAML kod düzenleyicisi penceresinin ekran görüntüsü")

Daha sonra, kod Düzenleyicisi 'ndeki Kullanıcı arabirimi öğelerinin her birinin işlevlerine göz atalım.

### <a name="first-row"></a>İlk satır

XAML kodu penceresinin en üstündeki ilk satırda, sol taraftaki bir **Tasarım** sekmesi, **takas bölmeleri** düğmesi, **XAML** sekmesi ve bir **açılan xaml** düğmesi bulunur.

![Visual Studio ' deki XAML kod düzenleyicisi penceresinin en üstteki iki satırı, vurgulanan ilk satırın sol tarafından birincidir](media/xaml-code-editor-top-row-left.png "Visual Studio 2019 ' deki XAML kod düzenleyicisi penceresinin ilk iki üst satırı ekran görüntüsü, sol taraftaki kullanıcı arabirimi öğeleri vurgulanır")

Şu şekilde çalışır:

- **Tasarım** SEKMESI, xaml kod düzenleyicisinden odak XAML Tasarımcısı olarak değiştirir.
- **Bölmeleri Değiştir** düğmesi, XAML Tasarımcısı konumunu ve xaml kod düzenleyicisini IDE 'de tersine çevirir.
- **Xaml** sekmesi, odağı xaml kod düzenleyicisine geri dönüştürür.
- **Aç xaml** Button, IDE dışında olan ayrı bir xaml kod Düzenleyicisi penceresi oluşturur.

Sağ tarafta devam eden **dikey bir bölme** düğmesi, **yatay bölme** düğmesi ve **bölmeleri Daralt** düğmesi vardır.

![Visual Studio içindeki XAML kod düzenleyicisi penceresinin en üstteki iki satırı, vurgulanan ilk satırın sağ tarafıyla](media/xaml-code-editor-top-row-right.png "Visual Studio 2019 ' deki XAML kod düzenleyicisi penceresinin ilk iki üst satırı ekran görüntüsü, sağdaki kullanıcı arabirimi öğeleri vurgulanır")

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

![her iki pencere açılan listesinin de görünür olduğu Visual Studio XAML kod düzenleyicisi penceresinin iki üst satırı için ikinci satır.](media/xaml-code-editor-top-row-windows.png "Visual Studio 2019 ' deki XAML kod düzenleyicisi penceresinin iki üst satırı için, her iki pencere açılan listesinin de görünür olduğu ekran görüntüsü")

Pencere açılan listeleri, aşağıdaki gibi farklı işlevlere sahiptir:

- Sol taraftaki **pencere öğesi** , eşdüzey veya üst öğeleri görüntülemenize ve gezinmenize yardımcı olur.

  Özellikle, kodunuzun etiket yapısını ortaya çıkaran bir anahat benzeri görünüm gösterir. Listeden seçim yaptığınızda, kod düzenleyicisine odaklanmanız seçtiğiniz öğeyi içeren kod satırına yaslanacak.

    ![Öğe: Visual Studio içindeki pencere açılan listesi](media/xaml-element-window-dropdown.png "öğenin ekran görüntüsü: Visual Studio 2019 ' de pencere açılan listesi")

- Sağ taraftaki **üye: pencere** , öznitelik veya alt öğeleri görüntülemenizi ve bu öğelere gitmenizi sağlar.

    Özellikle, kodunuzda özelliklerin bir listesini gösterir. Listeden seçim yaptığınızda, kod düzenleyicisine odaklanmanız seçtiğiniz özelliği içeren kod satırına yaslanacak.

    ![Üye: Visual Studio içindeki pencere açılan listesi](media/xaml-member-window-dropdown.png "Visual Studio 2019 ' de üye: pencere açılan listesinin ekran görüntüsü")

### <a name="middle-pane-code-editor"></a>Orta bölme, kod Düzenleyicisi

Orta bölme, XAML kod düzenleyicisinin "Code" kısmıdır. [IDE kod düzenleyicisinde](../get-started/tutorial-editor.md)bulacağınız özelliklerin çoğunu içerir. XAML kodunuzu geliştirmenize yardımcı olabilecek birçok evrensel IDE özelliği ile iletişime geçeceğiz. Ayrıca, IDE içindeki benzersiz XAML özelliklerini de vurgulayacağız.

![XAML kod Düzenleyicisi, yalnızca orta bölme, Visual Studio](media/xaml-code-editor-middle.png "Visual Studio 2019 ' de yalnızca orta bölme olan XAML kod düzenleyicisi 'nin ekran görüntüsü")

#### <a name="quick-actions"></a>Hızlı Eylemler

Tek bir eylem ile kodu yeniden düzenlemek, oluşturmak veya başka şekilde değiştirmek için [Hızlı işlemleri](../ide/quick-actions.md) kullanabilirsiniz.

Örneğin, hızlı eylemleri kullanarak gerçekleştirebileceğiniz yararlı bir görev, **MainWindow. xaml. cs** sekmesindeki C# kodundan **gereksiz kullanımlar kaldırmak** içindir.

Aşağıdaki adımları uygulayın:

1. Bir using ifadesinin üzerine gelin, ampul simgesini seçin ve ardından açılan listeden gereksiz kullanımları **Kaldır** ' ı seçin.

    ![Hızlı Eylemler menüsünde IDE düzenleyicisinin "gereksiz kullanımları kaldır" seçeneği](media/xaml-code-editor-remove-usings.png "Hızlı Eylemler menüsünde IDE düzenleyicisinin gereksiz kullanımları kaldırma seçeneğinin ekran görüntüsü")

1. **belge**, **Project** veya **çözüm** içindeki tüm oluşumları mı onarmak istediğinizi seçin.
1. **Önizleme** iletişim kutusunu görüntüleyin ve ardından **Uygula**' yı seçin.

Bu özelliğe menü çubuğundan de erişebilirsiniz. Bunu yapmak için,   >  **IntelliSense**'i  >  **Kaldır ve Sırala deyimlerini** Düzenle ' yi seçin.

Using ayarları hakkında daha fazla bilgi için bkz. [using using](../ide/reference/sort-usings.md) Page. ıntellisense hakkında daha fazla bilgi için Visual Studio sayfasındaki [ıntellisense](../ide/using-intellisense.md) bölümüne bakın. Geliştiricilerin hızlı eylemleri kullandığı tipik bazı yollarla ilgili daha fazla bilgi için bkz. [ortak hızlı eylemler](../ide/common-quick-actions.md) sayfası.

#### <a name="change-tracking"></a>Değişiklik izleme

Sol kenar boşluğunun rengi, bir dosyada yaptığınız değişiklikleri izlemenize olanak sağlar. Renklerin, aldığınız eylemlerle nasıl ilişkilendirileceğiyle ilgilidir:

- Dosya açıldığı ancak kaydedilmediği için yaptığınız değişiklikler sol kenar boşluğunda (seçim kenar boşluğu olarak bilinir) **sarı** bir çubukla gösterilir.

    ![Sarı çubukla kod düzenleyici düzenleme](media/code-editor-edit-yellow.png "Seçim kenar boşluğunda sarı çubukla işaretlenmiş bir değişikliği olan kod düzenleyicisinin ekran görüntüsü.")

- Değişiklikleri kaydettikten sonra (ancak dosyayı kapatmadan önce), çubuk **yeşile** döner.

    ![Yeşil çubukla kod Düzenleyicisi düzenleme](media/code-editor-edit-green.png "Seçim kenar boşluğunda yeşil çubukla işaretlenmiş bir değişikliği olan kod düzenleyicisinin ekran görüntüsü.")

Bu özelliği devre dışı bırakmak ve açmak için **metin Düzenleyicisi** ayarları 'ndaki (**Araçlar**   >  **Seçenekler**  >  **metin Düzenleyicisi**) değişiklikleri izle seçeneğini değiştirin.

&mdash;kod dizeleri altında görünen dalgalı çizgileri ("dalgalı çizgiler" olarak da bilinir) içerecek şekilde değişiklik izleme hakkında daha fazla bilgi için, &mdash; [Visual Studio kod düzenleyicisi sayfasının özelliklerinin](../ide/writing-code-in-the-code-and-text-editor.md) **[düzenleyici özellikleri](../ide/writing-code-in-the-code-and-text-editor.md#editor-features)** bölümüne bakın.

#### <a name="right-click-context-menu"></a>Sağ tıklama bağlam menüsü

Kodunuzu XAML kod düzenleyicisinde düzenlediğinizde, sağ tıklama bağlam menüsünü kullanarak erişebileceğiniz çeşitli özellikler vardır. bu özelliklerin çoğu, Visual Studio ıde 'de evrensel olarak kullanılabilir, bazıları da bir tasarım penceresiyle birlikte kod düzenleyicisi kullanmaya özgüdür.

![Visual Studio 2019 ' de XAML kod düzenleyicisinin sağ tıklama bağlam menüsünün ekran görüntüsü.](media/xaml-code-editor-right-click-menu.png)

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
- **Kopyalama** - Kendi kendine açıklayıcı
- **Yapıştırma** - Kendi kendine açıklayıcı
- **Outlining** - Kod bölümlerini genişletin ve daraltın. <br>Ayrıca bkz. [Outlining](../ide/outlining.md).
- **Kaynak Denetimi** - Açık kaynak depoya yapılan kod katkılarının geçmişini görüntüleme.

### <a name="middle-pane-scroll-bar"></a>Orta bölme, kaydırma çubuğu

Kaydırma çubuğu, kodunuzu kaydırmaktan daha fazlasını yapar. Başka bir kod düzenleyicisi bölmesini açmak için de kullanabilirsiniz. Ayrıca kaydırma çubuğunu kullanarak ek açıklamalar ekleyerek veya farklı görüntü modları kullanarak daha verimli kodlar kodlayabilirsiniz.

#### <a name="split-the-code-window"></a>Kod penceresini bölme

Kod düzenleyicisinin kaydırma çubuğunda sağ üstte bir **Böl** düğmesi vardır. Bunu seçtiğiniz zaman başka bir kod düzenleyicisi bölmesi açabilirsiniz. Bu, birbirinden bağımsız olarak çalıştırılaları için yararlıdır, bu nedenle bunları farklı konumlarda kod üzerinde çalışmak için kullanabilirsiniz.

![Visual Studio 2019'da bölmenin sağ üst kısmında Böl düğmesi vurgulanmış şekilde XAML kod düzenleyicisinin ortadaki bölmesini gösteren ekran görüntüsü.](media/code-editor-split-window-button.png)

Düzenleyici penceresini bölme hakkında daha fazla bilgi için Düzenleyici pencerelerini [yönetme sayfasına](../ide/how-to-manage-editor-windows.md) bakın.

#### <a name="use-annotations-or-map-mode"></a>Ek açıklamaları veya eşleme modunu kullanma

Kaydırma çubuğunun nasıl göründüğünü ve hangi ek özellikleri içerdiğini de değiştirebilirsiniz. Örneğin, birçok kişi kaydırma  çubuğuna ek açıklamalar eklemek isteyebilir. Bu çubukta kod değişiklikleri, kesme noktaları, yer işaretleri, hatalar ve dikkat işareti konumu gibi görsel ipuçları yer almaktadır.

Diğerleri ise kaydırma *çubuğunda kod* satırlarının görüntü olduğu harita modunu kullanmayı takdir eder. Bir dosyada çok fazla koda sahip olan geliştiriciler, eşleme modunun varsayılan kaydırma çubuğuna göre daha etkili bir şekilde kod satırlarına eşle olduğunu bulabilir.

Kaydırma çubuğunun varsayılan ayarlarını değiştirme hakkında daha fazla bilgi için kaydırma çubuğunu  [özelleştirme sayfasına](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md) bakın.

## <a name="xaml-specific-features"></a>XAML'ye özgü özellikler

Aşağıdaki özelliklerin çoğu Visual Studio IDE'de evrensel olarak kullanılabilir, ancak bazılarına XAML geliştiricileri için kodlamayı kolaylaştıran boyutlar eklenmiştir.

### <a name="xaml-code-snippets"></a>XAML kod parçacıkları

Kod parçacıkları, sağ tıklama bağlam menüsü komutu Kod parçacığı ekle veya klavye kısayollarının birleşimini (**Ctrl** K ,  Ctrl X ) kullanarak kod dosyasına ek olarak yeniden kullanılabilir kodun küçük +   + **bloklarıdır.** [IntelliSense'i,](../ide/using-intellisense.md) hem yerleşik kod parçacıklarında hem de el ile ekleyilen özel kod parçacıklarında çalışacak şekilde XAML kod parçacıklarını göstermeyi desteklemektedir. Bazı ilk gelen XAML kod parçacıkları arasında `#region` , , , ve yer `Column definition` `Row definition` `Setter` `Tag` almaktadır.

![IntelliSense'te gösterilen XAML kod parçacığı seçenekleriyle XAML kod düzenleyicisi](media/xaml-code-snippets.png "IntelliSense 'de gösterilen XAML kod parçacığı seçenekleri ile XAML kod Düzenleyicisi ekran görüntüsü")

Daha fazla bilgi için Kod parçacıkları [ve](../ide/code-snippets.md) [C# kod parçacıkları sayfalarına](../ide/visual-csharp-code-snippets.md) bakın.

### <a name="xaml-region-support"></a>XAML #region desteği

2015'Visual Studio başlayarak WPF ve UWP'de XAML geliştiricileri için #region desteği ve daha yakın zamanda [Xamarin.Forms'da](/xamarin/xamarin-forms/user-interface/text/editor/)da kullanılabilir hale getirildi. 2019 Visual Studio'da, destek için artımlı geliştirmeler #region devam edeceğiz. Örneğin, sürüm [16.4](/visualstudio/releases/2019/release-notes-v16.4/) ve #region, siz yazmaya başlanacak şekilde seçenekleri `<!` gösterir.

![IntelliSense'te gösterilen #region XAML kod düzenleyicisi](media/code-editor-xaml-region.png "IntelliSense 'de gösterilen #region seçenekleri olan XAML kod düzenleyicisinin ekran görüntüsü")

Kodunuzun genişletmek veya daraltmak istediğiniz bölümlerini grup olarak kullanmak istediğiniz bölgeleri kullanabilirsiniz.

```xaml
    <!--#region NameOfRegion-->
    Your code is here
    <!--#endregion-->
```

Bölgeler hakkında daha fazla bilgi için #region [(C# Başvurusu) sayfasına](/dotnet/csharp/language-reference/preprocessor-directives/preprocessor-region/) bakın. Ayrıca kodun bölümlerini genişletme ve daraltma hakkında daha fazla bilgi için [Bkz. Ana SatırLama](../ide/outlining.md) sayfası.

### <a name="xaml-comments"></a>XAML yorumları

Geliştiriciler genellikle açıklama kullanarak kendi kodunu belgelemeyi tercih eder. **MainWindow.xaml** sekmesindeki XAML koduna açıklama eklemek için aşağıdaki yöntemleri kullanabilirsiniz:

- Bir `<!--` açıklamadan önce girin ve `-->` açıklamanın ardından ekleyin.
- Girin `<!` ve ardından seçenek `!--` listesinden seçim yapabilirsiniz.

  ![XAML kod düzenleyicisi açıklama ekle iletişim kutusuna sağ tıklayın](media/xaml-code-editor-comments.png "XAML kod düzenleyicisine yorum eklemek için sağ tıklama kısayol menüsünün ekran görüntüsü")

- Bir açıklamanın çevresini almak istediğiniz kodu  seçin ve ardından IDE'nin araç çubuğundan Açıklama düğmesini seçin. Eylemi tersine çevirmek için, **Uncomment düğmesini** seçin.

  ![IDE araç çubuğundaki Açıklama düğmesi ve Açıklamayı Geri Alma düğmesi](media/comment-undo-comment-buttons.png "IDE araç çubuğundaki yorum düğmesinin ve açıklama düğmesinin ekran görüntüsü")

- Açıklama eklemek istediğiniz kodu seçin ve ardından **Ctrl** K , Ctrl + C **tuşlarına** + **basın.** Seçili kodu açıklamadan kaldırmak için **Ctrl** + **K**, **Ctrl** + **U tuşlarına basın.**

**MainWindow.xaml.cs** sekmesindeki C# kodunda açıklama kullanma hakkında daha fazla bilgi için Belgeler [açıklamalar sayfasına](/dotnet/csharp/language-reference/language-specification/documentation-comments/) bakın.

### <a name="xaml-lightbulbs"></a>XAML ampulleri

XAML kodunda görünen ampul simgeleri, kodu [](../ide/quick-actions.md) yeniden düzenleme, oluşturma veya başka bir şekilde değiştirme için kullanabileceğiniz Hızlı Eylemler'in bir parçasıdır.

Aşağıda, XAML kodlama deneyiminize nasıl fayda sabilecekleri hakkında birkaç örnek verilmiştir:

- **Gereksiz ad alanlarını kaldırın.** XAML kod düzenleyicisinde gereksiz ad alanları soluk metin olarak görünür. kullanarak imlecinizi gereksiz bir üzerine alırsanız bir ampul görünür. Açılan listeden **Gereksiz Ad** Alanlarını Kaldır seçeneğini tercih ettiyseniz, kaldırabilirsiniz seçeneğinin önizlemesini görebilirsiniz.

  ![Hızlı Eylemler ampulden XAML kod düzenleyicisinin Gereksiz Ad Alanlarını Kaldır seçeneği](media/xaml-code-editor-dimmed-namespaces-preview.png "Hızlı eylem ampul kullanılarak görüntülenen XAML kod düzenleyicisinin gereksiz ad alanlarını kaldır seçeneğinin ekran görüntüsü")

- **Ad alanını yeniden adlandır.** Ad alanını vurguladikten sonra sağ tıklama bağlam menüsünden kullanılabilen bu özellik, bir ayarın birden çok örneğini aynı anda değiştirmenizi kolaylaştırır. Ayrıca menü çubuğunu, Yeniden Düzenleme Yeniden DüzenlemeYi Düzenle seçeneğini veya Ctrl R tuşlarına ve ardından yeniden Ctrl R tuşlarına basarak da bu  >    >    +   + **özele erişebilirsiniz.**

  ![Sağ tıklama bağlam menüsünden XAML kod düzenleyicisinin Ad Alanını Yeniden Adlandır seçeneği](media/code-editor-rename-namespace.png "Sağ tıklama bağlam menüsü kullanılarak görüntülenen XAML kod Düzenleyicisi 'nin ad alanı değiştirme seçeneğinin ekran görüntüsü")

  Daha fazla bilgi için Kod [sembolünü yeniden düzenleme sayfasını yeniden adlandırma sayfasına](../ide/reference/rename.md) bakın.

### <a name="conditional-xaml-for-uwp"></a>UWP için koşullu XAML

Koşullu XAML, XAML işaretlemesinde [ApiInformation.IsApiContractPresent](/uwp/api/windows.foundation.metadata.apiinformation.isapicontractpresent/) yöntemini kullanmanın bir yolunu sağlar. Bu, arkadaki kodu kullanmaya gerek kalmadan bir API'nin varlığına göre özellikleri ayarlamaya ve işaretlemedeki nesnelerin örneğini oluşturmana olanak sağlar.

Daha fazla bilgi için Bkz. [Koşullu XAML](/windows/uwp/debug-test-perf/conditional-xaml/) sayfası ve Masaüstü uygulamalarında [Konak UWP XAML denetimleri (XAML Adaları)](/windows/apps/desktop/modernize/xaml-islands/) sayfası.

### <a name="xaml-structure-visualizer"></a>XAML Yapı Görselleştiricisi

Kod düzenleyicisinde Yapı Görselleştiricisi özelliği, kodda eşleşen açık ve kapalı etiket öğelerini gösteren dikey kesikli çizgiler olan yapı kılavuz çizgilerini gösterir. Bu dikey çizgiler, mantıksal blokların nereden başlayacağını ve sona erer olduğunu görmeyi kolaylaştırır.

Daha fazla bilgi için [Kodda gezinme sayfasına](../ide/navigating-code.md) bakın.

### <a name="intellicode-for-xaml"></a>XAML için IntelliCode

Kodunuz için bir XAML etiketi eklerken genellikle sol açılı ayraç ile `<` başlar. Bu açılı ayraç yazarak, daha popüler XAML etiketlerinden birkaçı listeleye bir IntelliCode menüsü görüntülenir. Kodunuza hızla eklemek istediğiniz örneği seçin.

IntelliCode seçimlerini tanıyabilirsiniz çünkü bunlar listenin en üstünde görünür ve sıralandı.

![XAML metin düzenleyicisi için IntelliCode listesi](media/xaml-intellicode-selection.png "XAML metin Düzenleyicisi için ıntellicode listesinin ekran görüntüsü")

Daha fazla bilgi için [IntelliCode'a Genel Bakış sayfasına](/visualstudio/intellicode/overview/) bakın.

### <a name="settings"></a>Ayarlar

IDE'de *tüm* ayarlar hakkında daha Visual Studio için kod [düzenleyicisinin özellikler sayfasına](../ide/writing-code-in-the-code-and-text-editor.md) bakın.

## <a name="xaml-optional-settings"></a>XAML isteğe bağlı ayarları

XAML [kod düzenleyicisinin](../ide/reference/options-dialog-box-visual-studio.md) varsayılan ayarlarını değiştirmek için Seçenekler iletişim kutusunu kullanabilirsiniz. Ayarları görüntülemek için Araçlar Seçenekler Metin **Düzenleyici**  >    >    >  **XAML'yi seçin.**

![XAML metin düzenleyicisi için Seçenekler listesi](media/xaml-tools-options.png "XAML metin Düzenleyicisi için seçenekler listesinin ekran görüntüsü")

> [!NOTE]
> Seçenekler iletişim kutusuna erişmek için klavye kısayollarını da kullanabilirsiniz. Şöyle yapabilirsiniz: IDE'de **arama yapmak için Ctrl** Q tuşlarına basın, Seçenekler yazın +  ve Enter tuşuna **basın.**  Ardından, **Seçenekler iletişim kutusunu aramak için Ctrl** E tuşlarına basın, Metin Düzenleyici yazın, Enter tuşuna +  basın, **XAML yazın** ve enter tuşuna **basın.**  
>
> Klavye kısayolları hakkında daha fazla bilgi için Bkz. Kısayol [ipuçları Visual Studio.](../ide/productivity-shortcuts.md#code-editor)

### <a name="universal-text-editor-options"></a>Evrensel metin düzenleyici seçenekleri

XAML [için](../ide/reference/options-text-editor-xaml-formatting.md) Seçenekler iletişim kutusunda, aşağıdaki ilk üç öğe, IDE'nin desteklediği tüm programlama dillerinde Visual Studio evrenseldir. Bu seçenekler ve bunların kullanımı hakkında daha fazla bilgi edinmek için aşağıdaki tabloda yer alan bağlantılı bilgileri ziyaret edin.

|Name  |Daha fazla bilgi  |
|---------|---------|
|Genel  | [Seçenekler iletişim kutusu: Metin Düzenleyici > Tüm Diller](../ide/reference/options-text-editor-all-languages.md) |
|Kaydırma çubukları | [Seçenekler, Metin Düzenleyici, Tüm Diller, Kaydırma Çubukları](../ide/reference/options-text-editor-all-languages-scroll-bars.md) |
|Sekmeler  |  [Seçenekler, Metin Düzenleyici, Tüm Diller, Sekmeler](../ide/reference/options-text-editor-all-languages-tabs.md) |

### <a name="xaml-specific-text-editor-options"></a>XAML'ye özgü metin düzenleyici seçenekleri

Aşağıdaki tabloda, Seçenekler iletişim [](../ide/reference/options-text-editor-xaml-formatting.md) kutusundaki XAML tabanlı uygulamalar geliştirirken düzenleme deneyiminizi geliştirecek ayarlar listele. Bu seçenekler ve bunların nasıl kullanılacağı hakkında daha fazla bilgi edinmek için bağlantılı bilgileri ziyaret edin.

|Name  |Daha fazla bilgi  |
|---------|---------|
|Biçimlendirme | [Seçenekler, Metin Düzenleyici, XAML, Biçimlendirme](../ide/reference/options-text-editor-xaml-formatting.md) |
|Çeşitli |  [Seçenekler, metin düzenleyici, XAML, çeşitli](../ide/reference/options-text-editor-xaml-miscellaneous.md) |

> [!TIP]
> **Çeşitli** bölümde **olay işleyicisi yöntem adı** ayarı, özellikle xaml geliştiricileri için yararlıdır. Bu ayar, yeni olduğu için varsayılan olarak *kapalıdır* , ancak kodunuzda doğru büyük/küçük harfleri desteklemek için bunu *Açık* olarak ayarlamanızı öneririz.

## <a name="next-steps"></a>Sonraki adımlar

Uygulamanızı hata ayıklama modunda çalıştırırken kodunuzun gerçek zamanlı olarak nasıl düzenleneceği hakkında daha fazla bilgi edinmek için bkz. [xaml Hot Reload yükleme](xaml-hot-reload.md) sayfası.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio kod düzenleyicisi özellikleri](../ide/writing-code-in-the-code-and-text-editor.md)
- [UWP uygulamalarında XAML](/windows/uwp/xaml-platform/xaml-overview/)
- [Xamarin. Forms uygulamalarındaki XAML](/xamarin/xamarin-forms/xaml/)
