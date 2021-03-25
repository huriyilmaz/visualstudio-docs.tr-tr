---
title: Visual Studio için paylaşılan renkler | Microsoft Docs
description: Visual Studio ortamıyla tutarlı olan kendi özel kullanıcı arabiriminizi tasarlamak için ortak Visual Studio Kabuk öğelerini ve temalarını nasıl kullanacağınızı öğrenin.
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8edd16744a6c094ece00ee5e4b8239f3d4f5a92e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054042"
---
# <a name="shared-colors-for-visual-studio"></a>Visual Studio için paylaşılan renkler
Ortak Visual Studio Kabuk öğelerini kullanan kullanıcı arabirimini tasarlarken veya arabirim öğenizin benzer özelliklerle tutarlı olmasını istiyorsanız, renkleri seçmek ve atamak için paket tanımlama dosyalarında mevcut belirteç adlarını kullanın. Bu, UI 'nizin genel Visual Studio ortamı ile tutarlı kalmasını ve Temalar eklendiğinde veya güncelleştirildiğinde otomatik olarak güncelleştirilmesini sağlar.

Bu makalede, benzer kullanıcı arabirimi oluştururken başvurbileceğiniz ortak kullanıcı arabirimi öğeleri ve kullandıkları belirteç adları açıklanır. Bu renk belirteçlerine erişme hakkında daha fazla bilgi için bkz. [Vsccolor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Belirteç adlarını doğru kullandığınızdan emin olun:

- **Belirteç adlarını, rengin kendisinde değil, işleve göre kullanın.** Ortak paylaşılan renkler, belirli arabirim öğeleriyle ilişkilendirilir ve yalnızca aynı veya benzer özellikler için kullanılmak üzere tasarlanmıştır. Örneğin, rengi beğenmeniz nedeniyle dönen ilerleme animasyonu için basılan Birleşik giriş kutusunun rengini yeniden kullanmayın. Birleşik giriş kutusu ve animasyonun işlevleri farklıdır ve Birleşik giriş kutusuyla ilişkili renk değişirse animasyon elemanı için uygun bir renk olmayabilir. Rengin tutarlı kullanımı kullanıcılarınıza yöneme ve karışıklığı önlemeye yardımcı olur.

- **Arka plan ve metin renklerini doğru birleşimde kullanın.** Metinle birlikte kullanılması amaçlanan arka plan renkleri ilişkili bir metin rengine sahip olur. Bu arka plan için belirtilenden farklı metin renkleri kullanmayın. İlişkili bir metin rengi yoksa, metin görüntülemeyi düşündüğünüz herhangi bir yüzey için bu arka plan rengini kullanmayın. Metin ve arka plan renklerinin diğer birleşimleri okunamaz bir arabirimle sonuçlanabilir.

- **Konumları için uygun olan denetim renklerini kullanın.** Bazı durumlarda, bazı Visual Studio denetimlerinde ayrı kenarlık ve arka plan renkleri yoktur. Bunun yerine, bunların arkasındaki yüzeylerden bu renkleri alırlar. Her zaman, denetimi yerleştirmekte olduğunuz konuma uygun belirteç adlarını kullandığınızdan emin olun.

> [!IMPORTANT]
> "Başlangıç sayfası" veya "Cıder" kategorilerinde bulunan belirteçleri kullanmayın.

## <a name="common-shared-controls"></a>Ortak paylaşılan denetimler

Özelliğinizdeki standart bir Visual Studio komut çubuğunu kullandığınızda, stillendirilmiş kabuk denetimlerine erişebilirsiniz. Bu ortak denetimleri yeniden şablonunuz gerekmez. Ancak, özel bir komut çubuğu oluşturmanız gerekiyorsa, özel denetimler de oluşturmanız gerekebilir. Bu durumda, UI 'nizin Visual Studio 'nun geri kalanı ile tutarlı olması için aşağıdaki denetimlerin her biri için doğru belirteç adlarını kullandığınızdan emin olun.

### <a name="button-controls"></a>Düğme denetimleri

![Düğme denetimi Redline](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Kullan... | Kullanma... |
| --- | --- |
| ... belgedeki düğmeler için, Visual Studio temaları (açık, koyu, mavi veya sistem Yüksek Karşıtlık teması) ile tümleştirilebilir. | ... bir Visual Studio temasının parçası olmayan özel bir arka planda görüntülenecek düğmeler için. |

**Düğme: Standart durum**

![Standart düğme](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03. Button. Standard")<br />Standart düğme

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Düğme | `CommonControls.Button` |
| Düğme kenarlığı | `CommonControls.ButtonBorder` |

**Düğme: varsayılan durum**

![Varsayılan düğme](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03. Button. Default")<br />Varsayılan düğme

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Düğme | `CommonControls.ButtonDefault` |
| Düğme kenarlığı | `CommonControls.ButtonBorderDefault` |

**Düğme: devre dışı durumu**

![Devre dışı düğmesi](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03. Button. Disabled")<br />Devre dışı düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Düğme | `CommonControls.ButtonDisabled` |
| Düğme kenarlığı | `CommonControls.ButtonBorderDisabled` |

**Düğme: üzerine gelme durumu**

![Üzerine gelindiğinde düğme](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03. Button. vurgulu")<br />Üzerine gelindiğinde düğme

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Düğme | `CommonControls.ButtonHover` |
| Düğme kenarlığı | `CommonControls.ButtonBorderHover` |

**Düğme: basılmış durumu**

![Basılan düğme](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03. Button. basılan")<br />Basılan düğme

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Düğme | `CommonControls.ButtonPressed` |
| Düğme kenarlığı | `CommonControls.ButtonBorderPressed` |

**Düğme: odaklanmış durum**

![Odaklanmış düğme](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03. Button. odaklanmış")<br />Odaklanmış düğme

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Düğme | `CommonControls.ButtonFocused` |
| Düğme kenarlığı | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Onay kutusu denetimleri
![Onay kutusu (Redline)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Onay kutusu (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Belge kutusu içinde bulunan onay kutusu denetimleri için. | ... onay kutusu denetimi olmayan herhangi bir kullanıcı arabirimi için. |

**Onay kutusu: varsayılan durum**

![Onay kutusu](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Varsayılan onay kutusu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackground` |
| Kenarlık | `CommonControls.CheckBoxBorder` |
| Metin | `CommonControls.CheckBoxText` |
| Simge | `CommonControls.CheckBoxGlyph` |

**Onay kutusu: devre dışı durumu**

![Devre dışı onay kutusu](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Devre dışı onay kutusu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackgroundDisabled` |
| Kenarlık | `CommonControls.CheckBoxBorderDisabled` |
| Metin | `CommonControls.CheckBoxTextDisabled` |
| Simge | `CommonControls.CheckBoxGlyphDisabled` |

**Onay kutusu: üzerine gelme durumu**

 ![Üzerine gelindiğinde onay kutusu](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Üzerine gelindiğinde onay kutusu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackgroundHover` |
| Kenarlık | `CommonControls.CheckBoxBorderHover` |
| Metin | `CommonControls.CheckBoxTextHover` |
| Simge | `CommonControls.CheckBoxGlyphHover` |

**Onay kutusu: basılı durum**

![Basılan onay kutusu](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Basılan onay kutusu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackgroundPressed` |
| Kenarlık | `CommonControls.CheckBoxBorderPressed` |
| Metin | `CommonControls.CheckBoxTextPressed` |
| Simge | `CommonControls.CheckBoxGlyphPressed` |

**Onay kutusu: odaklanmış durum**

![Odaklanmış onay kutusu](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Odaklanmış onay kutusu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackgroundFocused` |
| Kenarlık | `CommonControls.CheckBoxBorderFocused` |
| Metin | `CommonControls.CheckBoxTextFocused` |
| Simge | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Açılan kutular ve Birleşik giriş kutuları
![Açılan/aşağı açılan kutu (Redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Açılan/aşağı açılan kutu (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Belge kutusu içindeki açılır kutular ve Birleşik giriş kutuları için. | ... açılır liste veya açılan kutu olmayan herhangi bir kullanıcı arabirimi. |
| | ... komut çubuğu [açılır listeleri](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) veya [Birleşik giriş kutuları](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)için. |

**Açılan kutular ve Birleşik giriş kutuları: varsayılan durum**

![Varsayılan açılan/aşağı açılan kutusu](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Varsayılan açılan/aşağı açılan kutusu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxBackground` |
| Kenarlık | `CommonControls.ComboBoxBorder` |
| Metin | `CommonControls.ComboBoxText` |
| Ayırıcı | `CommonControls.ComboBoxSeparator` |
| Simge | `CommonControls.ComboBoxGlyph` |
| Glif arka planı | `CommonControls.ComboBoxGlyphBackground` |

**Açılan kutular ve Birleşik giriş kutuları: devre dışı durumu**

![Devre dışı açılan/açılan kutu kutusu](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Devre dışı açılan/açılan kutu kutusu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxBackgroundDisabled` |
| Kenarlık | `CommonControls.ComboBoxBorderDisabled` |
| Metin | `CommonControls.ComboBoxTextDisabled` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorDisabled` |
| Simge | `CommonControls.ComboBoxGlyphDisabled` |
| Glif arka planı | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Açılan kutular ve Birleşik giriş kutuları: üzerine gelme durumu**

![Üzerine gelindiğinde açılan/Birleşik giriş kutusu](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Üzerine gelindiğinde açılan/Birleşik giriş kutusu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxBackgroundHover` |
| Kenarlık | `CommonControls.ComboBoxBorderHover` |
| Metin | `CommonControls.ComboBoxTextHover` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorHover` |
| Simge | `CommonControls.ComboBoxGlyphHover` |
| Glif arka planı | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Açılan kutular ve Birleşik giriş kutuları: basılmış durumu**

![Basılan açılan/aşağı açılan kutusu](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Basılan açılan/aşağı açılan kutusu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxBackgroundPressed` |
| Kenarlık | `CommonControls.ComboBoxBorderPressed` |
| Metin | `CommonControls.ComboBoxTextPressed` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorPressed` |
| Simge | `CommonControls.ComboBoxGlyphPressed` |
| Glif arka planı | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Açılan kutular ve Birleşik giriş kutuları liste öğesi görünümü: basılmış durumu**

 ![Açılır/açılan kutu kutusu basılı liste öğesi görünümü](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Açılır/açılan kutu kutusu basılı liste öğesi görünümü

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Kenarlık | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Öğe metni | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Arka plan gölgesi | `CommonControls.ComboBoxListBackgroundShadow` |

**Açılan kutular ve Birleşik giriş kutuları: odaklanmış durum**

![Odaklanılmış açılan/aşağı açılan kutu](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Odaklanılmış açılan/aşağı açılan kutu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.ComboBoxBackgroundFocused` |
| Kenarlık | `CommonControls.ComboBoxBorderFocused` |
| Metin | `CommonControls.ComboBoxTextFocused` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorFocused` |
| Simge | `CommonControls.ComboBoxGlyphFocused` |
| Glif arka planı | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Açılan kutular ve Birleşik giriş kutuları: metin girişi seçimi**

![Aşağı açılan/Birleşik giriş kutusu metin girişi seçimi](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Aşağı açılan/Birleşik giriş kutusu metin girişi seçimi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Vurgula | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Tablo verileri (kılavuz) denetimleri
Grid denetimleri olarak da bilinen tablosal veri denetimleri, Visual Studio için ortak denetimlerdir ve çok sayıda sütunda büyük miktarlarda veri sunmak için kullanılabilir. Standart tablo veri denetimleri, Visual Studio içinde birden çok yerde bulunabilir: Hata Listesi araç penceresi, IntelliTrace raporları ve bellek yığın görünümü, diğerleri arasında. Her zaman sunulan standart tablo veri denetimlerini kullanın. Nadir bazı örneklerde standart tablo veri denetimlerine erişiminiz olmayabilir. Bu durumlarda, UI 'nizin Visual Studio 'daki diğer tablolu veri denetimleriyle tutarlı olduğundan emin olmak için aşağıdaki belirteç adlarını kullanın.

![Tablo verisi/kılavuz denetimi (Redline)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Tablo verisi/kılavuz denetimi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... tablosal veya kılavuz denetimleri için. | ... Tablo veya kılavuz denetimi olmayan herhangi bir kullanıcı arabirimi için. |

#### <a name="column-headers"></a>Sütun başlıkları
Sütun üst bilgileri, bir arka plan, kenarlık, başlık metni ve genellikle bir kılavuz bu sütuna göre sıralandığında kullanılan isteğe bağlı bir glifden oluşur.

**Sütun başlığı: varsayılan durum**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Header.Default` |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Ön plan (karakter) | `Header.Glyph` |
| Kenarlık | `Header.SeparatorLine` |

**Sütun üst bilgisi: üzerine gelme durumu**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Header.MouseOver` |
| Ön plan (metin) | `Environment.CommandBarTextHover` |
| Ön plan (karakter) | `Header.MouseOverGlyph` |
| Kenarlık | `Header.SeparatorLine` |

**Sütun başlığı: basılan durum**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `CommonControls.CheckBoxBackgroundPressed` |
| Ön plan (metin) | `CommonControls.CheckBoxBorderPressed` |
| Ön plan (karakter) | `CommonControls.CheckBoxTextPressed` |
| Kenarlık | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Liste görünümü öğeleri
 Liste görünümü öğeleri bir arka plan ve içerikten oluşur. İçerik metin, simge veya her ikisi olabilir.

**Liste görünümü öğeleri: varsayılan durum**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Geçirgen |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Kenarlık | Yok |

**Liste görünümü öğeleri: etkin durum**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemActive` |
| Ön plan (metin) | `TreeView.SelectedItemActiveText` |
| Kenarlık | Yok |

**Liste görünümü öğeleri: etkin olmayan durum**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemInactive` |
| Ön plan (metin) | `TreeView.SelectedItemInactiveText` |
| Kenarlık | Yok |

### <a name="ui-text"></a>UI metni

#### <a name="instructional-text"></a>Yönerge metni
Yönerge metni, iletişim kutusunda veya belge sayfasında ne yapacaklarınız için önemli bir açıklama sağlar.

![Varsayılan yönerge metni](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Varsayılan yönerge metni

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>İkincil yönerge metni
Çok sayıda metin ve denetim içeren belge sayfalarında, bazı eğitici metinler farklı bir renk değeri kullanır. Bu, hangi bilgilerin en önemli olduğunu ve Kullanıcı arabirimi öğelerinin genel yoğunluğunu korumanıza yardımcı olur. (İpucu metni üzerinde ayrıca aşağıdaki bölüme bakın.)

![İkincil yönerge metni](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />İkincil yönerge metni

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>İpucu metni
İpucu metni boş bir denetimde, denetimin altında veya boş bir belge yüzeyinde görünür ve kullanıcıyı bir sonraki adımda gösterir. İpucu metnini pencere ya da denetim arka planlarını kullanarak kullanabilirsiniz.

**Varsayılan ipucu metni**

![Varsayılan ipucu metni](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Varsayılan ipucu metni

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlEditHintText` |

**Gerekli ipucu metni**

![Gerekli ipucu metni](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Gerekli ipucu metni

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlRequiredHintText` |
| Arka Plan | `Environment.ControlRequiredBackground` |

**Arama kutusu denetim metni**

> Arama denetimiyle ilgili diğer renk belirteçleri için bkz. [arama kutuları](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) .

![Arama kutusu denetim metni](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Arama kutusu denetim metni

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Köprü
Köprü, ön plan/arka plan çiftine sahip olmayan bir denetimdir. Her durumda, koyu, gri ve beyaz arka planlar üzerinde doğru görünecek olan ön plan köprü rengini kullanın. Köprü denetimi için renk belirtecini kullanmıyorsanız, "basılmış" için varsayılan sistem rengini görürsünüz ve bu, kırmızı olarak yanıp sönecektir. Bu, denetimin doğru ortam renk belirtecini kullanmayan sinyaltir.

![Köprü (Redline)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Köprü (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... özel bir köprü oluşturmanız gerektiğinde. | ... Köprü olmayan her şey için. |

**Köprü: varsayılan durum**

![Varsayılan köprü](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Varsayılan köprü

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Environment.PanelHyperlink` |

**Köprü: üzerine gelme durumu**

![Üzerine gelindiğinde köprü](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Üzerine gelindiğinde köprü

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Environment.PanelHyperlinkHover` |

**Köprü: basılan durum**

![Basılan köprü](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Basılan köprü

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Environment.PanelHyperlinkPressed` |

**Köprü: devre dışı durumu**

![Devre dışı köprü](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Devre dışı köprü

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Çocuk
Popüler bir bağlam hakkında daha fazla bilgi sağlamak için ve her zaman bir belge penceresinin ya da araç penceresinin en üstünde görüntülenecek olan engelleri kullanır.

![Bilgi çubuğu (Redline)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Bilgi çubuğu (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Özel Engelliler oluştururken. | ... bir bilgi çubuğu ile benzer olmayan kullanıcı arabirimi öğeleri için. |

**Bilgi çubuğu: varsayılan durum**

![Varsayılan bilgi çubuğu](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Varsayılan bilgi çubuğu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `InfoBar.InfoBarBackground` |
| Ön plan (metin) | `InfoBar.InfoBar` |
| Kenarlık | `InfoBar.InfoBarBorder` |

**Bilgi çubuğu kapat ( &times; ) düğmesi: varsayılan durum**

![Varsayılan bilgi çubuğu kapat ( &times; ) düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Varsayılan bilgi çubuğu kapat ( &times; ) düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `InfoBar.CloseButton` |
| Kenarlık | `InfoBar.CloseButtonBorder` |
| Simge | `InfoBar.CloseButtonGlyph` |

**Bilgi çubuğu kapat ( &times; ) düğmesi: üzerine gelme durumu**

![Vurgu sayfasında bilgi çubuğu kapat ( &times; ) düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Vurgu sayfasında bilgi çubuğu kapat ( &times; ) düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `InfoBar.CloseButtonHover` |
| Kenarlık | `InfoBar.CloseButtonHoverBorder` |
| Simge | `InfoBar.CloseButtonHoverGlyph` |

**Bilgi çubuğu kapat ( &times; ) düğmesi: basılmış durumu**

![Basılan bilgi çubuğu kapat ( &times; ) düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Basılan bilgi çubuğu kapat ( &times; ) düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `InfoBar.CloseButtonDown` |
| Kenarlık | `InfoBar.CloseButtonDownBorder` |
| Simge | `InfoBar.CloseButtonDownGlyph` |

**Bilgi çubuğu köprü düğmesi: varsayılan durum**

![Varsayılan bilgi çubuğu köprü düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Varsayılan bilgi çubuğu köprü düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `InfoBar.Hyperlink` |

**Bilgi çubuğu köprü düğmesi: üzerine gelme durumu**

![Vurgu sayfasında bilgi çubuğu köprü düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Vurgu sayfasında bilgi çubuğu köprü düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseOver`<br />(Altı çizili) |

**Bilgi çubuğu köprü düğmesi: basılan durum**

![Basılan bilgi çubuğu köprü düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Basılan bilgi çubuğu köprü düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseDown`<br />(Altı çizili) |

**Bilgi çubuğu satır içi köprü (tümce içinde): varsayılan durum**

![Varsayılan satır içi bilgi çubuğu köprü düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Varsayılan satır içi bilgi çubuğu köprü düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `InfoBar.Hyperlink` |

**Bilgi çubuğu satır içi köprü (tümce içinde): üzerine gelme durumu**

![Vurgu çubuğunda bilgi çubuğu satır içi köprü düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Vurgu çubuğunda bilgi çubuğu satır içi köprü düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseOver`<br />(Altı çizili) |

**Bilgi çubuğu satır içi köprü (tümce içinde): basılmış durumu**

![Basılan bilgi çubuğu satır içi köprü düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Basılan bilgi çubuğu satır içi köprü düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseDown`<br />(Altı çizili) |

**Bilgi çubuğu düğmesi: varsayılan durum**

![Varsayılan bilgi çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Varsayılan bilgi çubuğu düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `InfoBar.Button` |
| Ön plan (metin) | `InfoBar.Button` |
| Kenarlık | `InfoBar.ButtonBorder` |

**Bilgi çubuğu düğmesi: üzerine gelme durumu**

![Üzerine gelindiğinde bilgi çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Üzerine gelindiğinde bilgi çubuğu düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `InfoBar.ButtonMouseOver` |
| Ön plan (metin) | `InfoBar.ButtonMouseOver` |
| Kenarlık | `InfoBar.ButtonMouseOverBorder` |

**Bilgi çubuğu düğmesi: basılan durum**

![Basılan bilgi çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Basılan bilgi çubuğu düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `InfoBar.ButtonMouseDown` |
| Ön plan (metin) | `InfoBar.ButtonMouseDown` |
| Kenarlık | `InfoBar.ButtonMouseDownBorder` |

**Bilgi çubuğu düğmesi: devre dışı durumu**

![Devre dışı bilgi çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Devre dışı bilgi çubuğu düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `InfoBar.ButtonDisabled` |
| Ön plan (metin) | `InfoBar.ButtonDisabled` |
| Kenarlık | `InfoBar.ButtonDisabledBorder` |

**Bilgi çubuğu düğmesi: odaklanmış durum**

![Odaklanmış bilgi çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Odaklanmış bilgi çubuğu düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `InfoBar.ButtonFocus` |
| Ön plan (metin) | `InfoBar.ButtonFocus` |
| Kenarlık | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Kaydırma çubukları
Kaydırma çubukları, Visual Studio ortamı tarafından stillendirilerek temalı olması gerekmez. Ancak, UI 'nizin Visual Studio ortamının bu bölümüyle tutarlı şekilde görünmesi için, kaydırma çubuklarında kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.

![Kaydırma çubuğu (Redline)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Kaydırma çubuğu (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Visual Studio kaydırma çubuklarını eşleştirmek istediğiniz kullanıcı arabirimini oluştururken. | ... her zaman kaydırma çubuğu kullanıcı arabirimine eşleştirmek istemediğiniz her şey için. |

**Kaydırma çubuğu: varsayılan durum**

![Varsayılan kaydırma çubuğu](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Varsayılan kaydırma çubuğu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Kaydırma çubuğu | `Environment.ScrollBarBackground` |
| Ön plan (Thumb) | `Environment.ScrollBarThumbBackground` |

**Kaydırma çubuğu: üzerine gelme durumu**

![Üzerine gelindiğinde kaydırma çubuğu](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Üzerine gelindiğinde kaydırma çubuğu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Kaydırma çubuğu | `Environment.ScrollBarBackground` |
| Ön plan (Thumb) | `Environment.ScrollBarThumbMouseOverBackground` |

*Kaydırma çubuğu: basılmış durumu**

![Basılan kaydırma çubuğu](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Basılan kaydırma çubuğu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Kaydırma çubuğu | `Environment.ScrollBarBackground` |
| Ön plan (Thumb) | `Environment.ScrollBarThumbPressedBackground` |

**Kaydırma çubuğu oku: varsayılan durum**

![Varsayılan kaydırma çubuğu oku](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Varsayılan kaydırma çubuğu oku

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ScrollBarArrowBackground`<br />(Kaydırma çubuğu ile aynı renge ayarlanır.) |
| Ön plan (karakter) | `Environment.ScrollBarArrowGlyph` |

**Kaydırma çubuğu oku: üzerine gelme durumu**

![Üzerine gelindiğinde kaydırma çubuğu oku](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Üzerine gelindiğinde kaydırma çubuğu oku

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ScrollBarArrowMouseOverBackground`<br />(Kaydırma çubuğu ile aynı renge ayarlanır.) |
| Ön plan (karakter) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Kaydırma çubuğu oku: basılmış durumu**

![Basılan kaydırma çubuğu oku](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Basılan kaydırma çubuğu oku

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ScrollBarArrowPressedBackground`<br />(Kaydırma çubuğu ile aynı renge ayarlanır.) |
| Ön plan (karakter) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Arama kutuları
Mümkün olan her durumda, Visual Studio ortamı tarafından sunulan genel arama denetimini kullanın. Arama kutusu renkleri, giriş alanı, eylem düğmesi, açılan düğme ve açılan menünün belirteç adlarını içeren **Shellcolors. pkgdef** dosyasındaki "SearchControl" kategorisinde bulunur.

Bir arama kutusu, bazıları birbirini dışlamalı birkaç durumdan biri olabilir:

- "Odaklanmış" veya "odaklanmış olmayan" imleci, imlecin metin kutusunda olup olmadığı anlamına gelir.

- "Etkin" veya "etkin değil", kullanıcının metin kutusunda bir arama sorgusu girmediğini belirtir.

- "Üzerine gelme", kullanıcının fare ile arama kutusu üzerinde molediği anlamına gelir (Bu durum diğer tüm durumları geçersiz kılar).

- "Devre dışı", geçerli bağlam için arama işlevinin kapalı olduğu anlamına gelir.

![Arama kutusu (Redline)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Arama kutusu (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... özel bir arama kutusu tasarlıyorsunuz. | ... Arama kutusu olmayan her şey için. |
| | ... Arama kutusu kullanıcı arabirimine her zaman eşleşmek istemediğiniz her şey için. |

**Odaklanmış arama giriş alanı**

![Odaklanmış arama giriş alanı](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Odaklanmış arama giriş alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.FocusedBackground` |
| Ön plan (metin) | `SearchControl.FocusedBackground` |
| Kenarlık | `SearchControl.FocusedBorder` |
| Ayırıcı | `SearchControl.FocusedDropDownSeparator` |

**Odaklanmış olmayan, etkin arama giriş alanı**

![Arama girişi alanı odaklanmış değil](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Odaklanmış olmayan, etkin arama giriş alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.SearchActiveBackground` |
| Ön plan (metin) | `SearchControl.SearchActiveBackground` |
| Kenarlık | `SearchControl.UnfocusedBorder` |
| Ayırıcı | `SearchControl.DropDownSeparator` |

**Odaklanmadan, etkin olmayan arama giriş alanı**

![Odaklanmadan, etkin olmayan arama giriş alanı](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Odaklanmadan, etkin olmayan arama giriş alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.Unfocused` |
| Ön plan (metin) | `SearchControl.Unfocused` |
| Kenarlık | `SearchControl.UnfocusedBorder` |
| Ayırıcı | `SearchControl.DropDownSeparator` |

**Vurgulanan arama girişi alanı (yalnızca metin)**

![Vurgulanan arama girişi alanı](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Vurgulanan arama girişi alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.Selection` |
| Ön plan (metin) | `SearchControl.FocusedBackground` |
| Kenarlık | Yok |
| Ayırıcı | `SearchControl.FocusedDropDownSeparator` |

**Devre dışı arama girişi alanı**

![Devre dışı arama girişi alanı](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Devre dışı arama girişi alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.Disabled` |
| Ön plan (metin) | `SearchControl.Disabled` |
| Kenarlık | `SearchControl.DisabledBorder` |
| Ayırıcı | `SearchControl.DropDownSeparator` |

**Odaklanmış arama eylemi düğmesi**

![Arama eylemi düğmesi odaklı](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Odaklanmış arama eylemi düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter ara) | `SearchControl.SearchGlyph` |
| Ön plan (glifi Durdur) | `SearchControl.StopGlyph` |
| Ön plan (glifi temizle) | `SearchControl.ClearGlyph` |
| Kenarlık | Yok |

**Odaklanmış olmayan arama eylemi düğmesi**

![Odaklanmış olmayan arama eylemi düğmesi](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Odaklanmış olmayan arama eylemi düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter ara) | `SearchControl.SearchGlyph` |
| Ön plan (glifi Durdur) | `SearchControl.StopGlyph` |
| Ön plan (glifi temizle) | `SearchControl.ClearGlyph` |
| Kenarlık | Yok |

**Basılan arama eylemi düğmesi**

![Basılan arama eylemi düğmesi](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Basılan arama eylemi düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.ActionButtonMouseDown` |
| Ön plan (karakter) | `SearchControl.ActionButtonMouseDownGlyph` |
| Kenarlık | `SearchControl.ActionButtonMouseDownBorder` |

**Devre dışı arama eylemi düğmesi**

![Arama eylemi düğmesi devre dışı](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Devre dışı arama eylemi düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `SearchControl.ActionButtonDisabledGlyph` |
| Kenarlık | Yok |

**Odaklanmış arama açılan düğmesi**

![Odaklanmış arama açılan düğmesi](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Odaklanmış arama açılan düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.FocusedDropDownButton` |
| Ön plan (karakter) | `SearchControl.FocusedDropDownButtonGlyph` |
| Kenarlık | `SearchControl.FocusedDropDownButtonBorder` |

**Odaklanmış olmayan arama açılan düğmesi**

![Odaklanmış olmayan arama açılan düğmesi](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Odaklanmış olmayan arama açılan düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.UnfocusedDropDownButton` |
| Ön plan (karakter) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Kenarlık | `SearchControl.UnfocusedDropDownButtonBorder` |

**Basılan arama açılan düğmesi**

![Basılan arama açılan düğmesi](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Basılan arama açılan düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.MouseDownDropDownButton` |
| Ön plan (karakter) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Kenarlık | `SearchControl.MouseDownDropDownButtonBorder` |

**Devre dışı arama açılan düğmesi**

![Devre dışı arama açılan düğmesi](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Devre dışı arama açılan düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `SearchControl.DisabledDownButtonGlyph` |
| Kenarlık | Yok |

#### <a name="search-drop-down-lists"></a>Arama açılan listeleri
Arama kutusu açılan menüsü, Visual Studio 'daki diğer açılan menülerden biraz daha karmaşık olma olasılığını içerir. "Önerilen aramalar" ve "arama seçenekleri" bölümleri, tek başına veya menüde birlikte görünebilir ve her biri ayrı olarak renklendirilir. Bir satır, birlikte görüntülendiklerinde bu iki bölümü de ayırır ve bir kenarlık, tüm açılan menüyü çevreler.

![Arama açılan listesi (Redline)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Arama açılan listesi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... özel bir arama açılan listesi oluştururken. | ... diğer bağlamlarda görünen açılan listeler için. |
| ... doğru liste bileşenleri için doğru belirteç adları. | ... belirtilen dışında bir arka plan/ön plan birleşimi. |

**Açılan liste öğelerini ara**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Kenarlık | `SearchControl.PopupBorder` |
| Ayırıcı | `SearchControl.PopupSectionHeaderSeparator` |
| Gölgeli | `Environment.DropShadowBackground` |

**Önerilen aramalar: varsayılan durum**

![Önerilen varsayılan aramalar](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Önerilen varsayılan aramalar

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `SearchControl.PopupItemText` |

**Önerilen aramalar: üzerine gelme durumu**

![Üzerine gelindiğinde önerilen aramalar](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Üzerine gelindiğinde önerilen aramalar

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `SearchControl.PopupMouseOverItemText` |
| Kenarlık | `SearchControl.PopupControlMouseOverBorder` |

**Arama seçenekleri: varsayılan durum**

![Arama onay kutusu](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Varsayılan arama seçenekleri (onay kutusu)

![Arama seçenekleri](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Varsayılan arama seçenekleri (bağlantı)

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (onay kutusu metni) | `SearchControl.PopupCheckboxText` |
| Ön plan (bağlantı metni) | `SearchControl.PopupButtonText` |
| Üst bilgi arka planı | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (üst bilgi metni) | `SearchControl.PopupSectionHeaderText` |

**Arama seçenekleri: üzerine gelme durumu**

![Arama seçenekleri (onay kutusu) üzerine gidilme](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Arama seçenekleri (onay kutusu) üzerine gidilme

![Arama seçenekleri (bağlantı) üzerine gidilme](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Arama seçenekleri (bağlantı) üzerine gidilme

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (onay kutusu metni) | `SearchControl.PopupCheckboxMouseDownText` |
| Ön plan (bağlantı metni) | `SearchControl.PopupButtonMouseDownText` |
| Kenarlık | `SearchControl.PopupControlMouseOverBorder` |

**Arama seçenekleri: basılan durum**

![Basılan arama seçenekleri (onay kutusu)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Basılan arama seçenekleri (onay kutusu)

![Basılan arama seçenekleri (bağlantı)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Basılan arama seçenekleri (bağlantı)

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Onay kutusu arka planı | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (onay kutusu metni) | `SearchControl.PopupCheckboxMouseDownText` |
| Bağlantı arka planı | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (bağlantı metni) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a> Ağaç görünümleri
Çözüm Gezgini, Sunucu Gezgini ve Sınıf Görünümü dahil çeşitli araç pencereleri, renkleri kategoride bulunan renk adlarıyla denetlenen hiyerarşik bir kurumsal düzen uygular `TreeView` . Ağaç görünümündeki tüm öğelerin arka plan ve metin renkleri vardır. İç içe alt öğelerine sahip olan öğeler, öğenin genişletildiğini veya daraltılıp daraltılmadığını belirten glifleri de vardır.

![Ağaç görünümü (Redline)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Ağaç görünümü (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... hiyerarşik bir kurumsal görünüm uygulamanız gereken her yerde. | ... ağaç görünümüne benzer olmayan her şey için. |
| | ... belirtilen dışında bir arka plan/ön plan birleşimi. |

**Ağaç görünümü öğesi: varsayılan durum**

![Varsayılan ağaç görünüm öğesi](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Varsayılan ağaç görünüm öğesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `TreeView.Background` |
| Ön plan (metin) | `TreeView.Background` |
| Ön plan (karakter) | `TreeView.Glyph` |
| Kenarlık | Yok |

**Ağaç görünümü öğesi: üzerine gelme durumu**

![Üzerine gelindiğinde ağaç görünüm öğesi](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Üzerine gelindiğinde ağaç görünüm öğesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `TreeView.Background` |
| Ön plan (metin) | `TreeView.Background` |
| Ön plan (karakter) | `TreeView.GlyphMouseOver` |
| Kenarlık | Yok |

**Ağaç görünümü öğesi: durumu üzerine sürükleyin**

![Yukarı sürükleme üzerinde ağaç görünüm öğesi](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Yukarı sürükleme üzerinde ağaç görünüm öğesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `TreeView.DragOverItem` |
| Ön plan (metin) | `TreeView.DragOverItem` |
| Ön plan (karakter) | `TreeView.DragOverItemGlyph` |
| Kenarlık | Yok |

**Ağaç görünümü öğesi: seçili, odaklanmış durum**

![Seçilen ve odaklanmış ağaç görünümü öğesi](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Seçilen ve odaklanmış ağaç görünümü öğesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemActive` |
| Ön plan (metin) | `TreeView.SelectedItemActive` |
| Ön plan (karakter) | `TreeView.SelectedItemActiveGlyph` |
| Kenarlık | `TreeView.FocusVisualBorder` |

**Ağaç görünümü öğesi: seçili, odaklanmış olmayan durum**

![Seçilen ve odaklanmış olmayan ağaç görünüm öğesi](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Seçilen ve odaklanmış olmayan ağaç görünüm öğesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemInactive` |
| Ön plan (metin) | `TreeView.SelectedItemInactive` |
| Ön plan (karakter) | `TreeView.SelectedItemInactiveGlyph` |
| Kenarlık | Yok |

**Ağaç Görünüm öğesi: vurgulanan, seçilen ve Odaklanmış durum**

![Seçilen ve odaklanmış ağaç görünüm öğesi üzerine gidilme](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Seçilen ve odaklanmış ağaç görünüm öğesi üzerine gidilme

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemActive` |
| Ön plan (metin) | `TreeView.SelectedItemActive` |
| Ön plan (karakter) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Kenarlık | `TreeView.FocusVisualBorder` |

**Ağaç görünümü öğesi: vurgulanan, seçilen ve odaklanmış olmayan durum**

![Seçilen ve odaklanmış olmayan ağaç görünüm öğesi üzerine gidilme](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Seçilen ve odaklanmış olmayan ağaç görünüm öğesi üzerine gidilme

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemInactive` |
| Ön plan (metin) | `TreeView.SelectedItemInactive` |
| Ön plan (karakter) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Kenarlık | Yok |

## <a name="shell-appearance"></a>Kabuk görünümü

### <a name="background"></a>Arka Plan
Ortam arka planı iki katmandan oluşur. Alt katman, tüm IDE 'yi içeren düz bir renktir. En üstteki katman, komut rafı altına ve araç penceresi arasında IDE 'nin sol ve sağ kenarlarındaki kanalları otomatik olarak gizler. Üst ve alt arka plan katmanları, açık ve koyu temalarda aynı renge ayarlanır.

![Visual Studio Kabuğu arka planı (Redline)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Visual Studio Kabuğu arka planı (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Visual Studio ortamının arka planıyla eşleştirmek istediğiniz konumlar için. | ... arka plan yüzeyleri olmayan yerleri için bir Fill. |
| | ... ön plan öğelerini üzerine yerleştirmek için bir arka plan olarak. |

**Alt katman kabuğu görünümü**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.EnvironmentBackground` |

**Üst katman kabuğu görünümü**

> Gradyan duraklarının Visual Studio 2013 ışığı ve koyu temalarda aynı renk değerine ayarlanır.

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Komut rafı
Komut raf planları için iki belirteç adı kümesi kullanılır: menü çubuğunun bulunduğu bir küme ve komut çubuklarının bulunduğu konum. Tek bir komut çubuğu grubu, "komut çubuğu" bölümünde daha ayrıntılı olarak ele alınan kendi arka plan rengi değerlerine sahiptir. Menü çubuğu ve komut çubuğu metni sırasıyla menü ve komut çubuğu bölümlerinde ele alınmıştır.

![Visual Studio komut rafı (Redline)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Visual Studio komut rafı (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Menüleri veya araç çubuklarını yerleştirdiğiniz alanlarda. | ... bir komut rafından benzer olmayan alanlarda. |
|... doğru arka plan/ön plan belirteci adı birleşimini kullanarak. | |

**Komut rafı menü çubuğu**

> Gradyan duraklarının Visual Studio 2013 ışığı ve koyu temalarda aynı renk değerine ayarlanır.

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Komut rafı komut çubuğu**

> Gradyan duraklarının Visual Studio 2013 ışığı ve koyu temalarda aynı renk değerine ayarlanır.

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Bildirim Tasarımcısı
Bildirim Tasarımcısı, Windows 8 ve Windows Phone 8 projelerinde bildirim dosyasını düzenlemeyi kolaylaştırmak için bir yol olarak tasarlanmıştır. Tüketim için kullanılabilen bir paylaşılan çerçeve olmasa da, yönlendirme/gezinti sekmelerinin ve genel yapının tasarım düzen ve renklerini eşleştirmek uygun olabilir. Düzen ayrıntıları hakkında daha fazla bilgi için bkz. [Visual Studio Için düzen](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Bildirim Tasarımcısı (Redline)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Bildirim Tasarımcısı (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Bildirim tasarımcısına benzer tasarımcılar için. | ... Altıdan fazla sekmeniz varsa. |
| ... Belge kutusu içindeki bir düzenleyicinin en üstünde ortak sekme denetimleri kullanma yerine. | ... Bildirim Tasarımcısı gibi yapılandırılmamış herhangi bir kullanıcı arabirimi için. |

**Bildirim Tasarımcısı Seçili sekmesi: varsayılan durum**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `ManifestDesigner.TabActive` |
| Kenarlık | Yok |

**Bildirim Tasarımcısı Seçili açıklama bölmesi: varsayılan durum**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `ManifestDesigner.DescriptionPane` |

**Bildirim Tasarımcısı Seçili içerik sayfası: varsayılan durum**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `ManifestDesigner.Background` |
| İletişim kutusu Yardımcısı metni | `ManifestDesigner.WatermarkText`<br />(Bu belirteç adı işlevle eşleşmiyor.) |

**Bildirim Tasarımcısı sekmesi: seçilmemiş durum**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `ManifestDesigner.Tab.Inactive` |

**Bildirim Tasarımcısı sekmesi: üzerine gelme durumu**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Komut yapıları

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Menülerden
Menüler Visual Studio içinde birkaç yerde gerçekleşebilir: Ana menü çubuğu, belge veya araç pencereleri içine eklenmiş veya IDE genelinde çeşitli konumlara sağ tıklama. Diğer Kullanıcı arabirimi öğeleriyle ilişkili menülerin uygulamaları ilgili öğesi için bölümünde ele alınmıştır. Visual Studio ortamı tarafından sunulan standart menü uygulamasını her zaman kullanmanız gerekir. Ancak, nadir bazı örneklerde standart Visual Studio menülerine erişiminiz olmayabilir. Bu durumlarda, UI 'nizin Visual Studio 'daki diğer menülerle tutarlı olduğundan emin olmak için aşağıdaki belirteç adlarını kullanın.

![Visual Studio menüsü (Redline)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Visual Studio menüsü (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... özel bir menü oluşturmanız gerektiğinde.| ... yalnızca arka plan rengi. Her zaman belirtilen şekilde arka plan/ön plan birleşimini kullanın. |
| ... Visual Studio menülerini eşleştirmek istediğiniz yeni bir kullanıcı arabirimi bileşenine sahip olduğunuzda.| |

#### <a name="menu-titles"></a>Menü başlıkları
Menü başlıkları bir arka plan, kenarlık ve başlık metninin yanı sıra, genellikle menü bir komut çubuğunda bulunduğunda isteğe bağlı bir glifi içerir.

![Menü başlığı (Redline)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Menü başlığı (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... özel bir menü başlığı oluşturduğunuz zaman. | ... her zaman menü başlığıyla eşleştirmek istemediğiniz her şey için. |
| | ... belirtilen dışında bir arka plan/ön plan birleşimi. |

**Menü başlığı: varsayılan durum**

![Varsayılan menü başlığı](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Varsayılan menü başlığı

![Glifi olan varsayılan menü başlığı](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Glifi olan varsayılan menü başlığı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Ön plan (karakter) | `Environment.CommandBarMenuGlyph` |
| Kenarlık | Yok |

**Menü başlığı: üzerine gelme durumu**

![Üzerine gelindiğinde menü başlığı](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Üzerine gelindiğinde menü başlığı

![Vurgu üzerinde glifi olan menü başlığı](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Vurgu üzerinde glifi olan menü başlığı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.CommandBarTextHover` |
| Ön plan (karakter) | `Environment.CommandBarMenuMouseOverGlyph` |
| Kenarlık | `Environment.CommandBarBorder` |

**Menü başlığı: basılan durum**

![Basılan menü başlığı](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Basılan menü başlığı

![Glifle basılan menü başlığı](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Glifle basılan menü başlığı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Ön plan (karakter) | `Environment.CommandBarMenuMouseDownGlyph` |
| Kenarlık | `Environment.CommandBarMenuBorder`<br />(Yalnızca sol, üst ve sağ kenarlar.) |

**Menü başlığı: devre dışı durumu**

![Karakter ile devre dışı menü başlığı](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Karakter ile devre dışı menü başlığı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (metin) | `Environment.CommandBarTextInactive` |
| Ön plan (karakter) | `Environment.CommandBarTextInactive` |
| Kenarlık | Yok |

#### <a name="menu-items"></a>Menü öğeleri
Tek bir menü öğesi menü metnini ve isteğe bağlı bir simge, onay kutusu ya da alt menü glifinden oluşur. Arka planı ve metin rengi, üzerine gidilme üzerinde değişir. Bu renk belirteci bir arka plan/ön plan çiftidir.

![Menü öğeleri Redline](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Kullan... | Kullanma... |
|---|---|
| ... bir menü çubuğundan veya komut çubuğundan başlatılan açılan herhangi bir liste için. | ... diğer bağlamdaki herhangi bir açılan liste için. |
| | ... belirtilen dışında bir arka plan/ön plan birleşimi. |

**Menü öğeleri: varsayılan durum**

![Varsayılan menü öğeleri](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Varsayılan menü öğeleri

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Ön plan (alt menü karakteri) | `Environment.CommandBarMenuSubmenuGlyph` |
| Kenarlık | `Environment.CommandBarMenuBorder` |
| Simge kanalı arka planı | `Environment.CommandBarMenuIconBackground` |
| Ayırıcı | `Environment.CommandBarMenuSeparator` |
| Gölgeli | `Environment.DropShadowBackground` |

**Menü öğeleri: işaretli ve seçili durumlar**

![Menü işaretlendi](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Menü öğesi işaretlendi

![Menü seçildi](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Seçilen menü öğesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Onay işareti | `Environment.CommandBarCheckBox` |
| İşaret arkaplanını denetle | `Environment.CommandBarSelectedIcon` |
| Simge arka planı | `Environment.CommandBarSelected` |
| Simge kenarlığı | `Environment.CommandBarSelectedBorder` |

**Menü öğeleri: üzerine gelme durumu**

![Menü üzerine gelme](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Üzerine gelindiğinde menü öğesi

![Menü üzerine gelme işaretlendi](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Üzerine gidildiğinde menü öğesi işaretlendi

![Menü üzerine gelme seçildi](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Üzerine gelindiğinde seçilen menü öğesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMenuItemMouseOver` |
| Ön plan (metin) | `Environment.CommandBarMenuItemMouseOverText` |
| Ön plan (alt menü karakteri) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Onay işareti | `Environment.CommandBarCheckBoxMouseOver` |
| İşaret arkaplanını denetle | `Environment.CommandBarHoverOverSelectedIcon` |
| Simge arka planı | `Environment.CommandBarHoverOverSelected` |
| Simge kenarlığı | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Menü öğeleri: devre dışı durumu**

![Menü devre dışı](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Devre dışı menü öğesi

![Menü devre dışı işaretlendi](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Onay işaretiyle devre dışı menü öğesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Ön plan (metin) | `Environment.CommandBarTextInactive` |
| Ön plan (alt menü karakteri) | `Environment.CommandBarMenuSubmenuGlyph` |
| Onay işareti | `Environment.CommandBarCheckBoxDisabled` |
| İşaret arkaplanını denetle | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Komut çubukları
Bir komut çubuğu, Visual Studio IDE içinde birden çok yerde görünebilir ve bu, özellikle de bir komut rafı ve araç ya da belge pencereleri ile katıştırılır.

Genel olarak, her zaman Visual Studio ortamı tarafından sunulan standart komut çubuğu uygulamasını kullanın. Standart mekanizmanın kullanılması, tüm görsel ayrıntıların doğru görünmesini ve Etkileşimli öğelerin diğer Visual Studio komut çubuğu denetimleriyle tutarlı bir şekilde davranmasını sağlar. Ancak, kendi komut çubuğunuzu oluşturmanız gerekiyorsa, aşağıdaki belirteç adlarını kullanarak doğru şekilde stillediğinizden emin olun.

![Komut çubuğu Redline](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Komut çubuğu (Redline)

![Taşma düğmesi Redline](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Taşma düğmesi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Katıştırılmış bir komut çubuğuna ihtiyacınız olan yerlerde, ancak standart Visual Studio komut çubuğu uygulamasını kullanamazsınız. | ... komut çubuğuna benzer olmayan UI öğeleri için. |
| | ... belirteç adlarının belirtildiklerinin dışındaki komut çubuğu bileşenleri için. |

#### <a name="command-bar-groups"></a>Komut çubuğu grupları
Bir komut çubuğu grubu, ilgili bir komut çubuğu denetimleri kümesinden oluşur ve herhangi bir sayıda düğme, bölünmüş düğme, açılan menü, Birleşik giriş kutusu veya menü içerebilir. Bu denetimlerin renkleri ayrı belirteç adlarına göre düzenlenebilir ve bu kılavuzun başka bir yerinde ele alınmıştır. Bir ayırıcı çizgi, bir komut çubuğu grubunu ilgili alt gruplara bölmek için kullanılır.

![Komut çubuğu grubu Redline](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Komut çubuğu grubu (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Katıştırılmış bir komut çubuğuna ihtiyacınız olan yerlerde, ancak standart Visual Studio komut çubuğu uygulamasını kullanamazsınız. | ... komut çubuğuna benzer olmayan UI öğeleri için. |
| | ... belirteç adlarının belirtildiklerinin dışındaki komut çubuğu bileşenleri için. |

**Komut çubuğu grubu: varsayılan durum**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarGradientBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Kenarlık | `Environment.CommandBarToolBarBorder` |
| Sürükleme tutamacı | `Environment.CommandBarDragHandle` |
| Ayırıcı | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Komut simgeleri
![Komut simgesi Redline](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Komut simgesi (Redline)

![Metin Redline ile komut simgesi](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Metinle birlikte komut simgesi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... bir komut çubuğuna yerleştirilecek düğmeler için. | ... kendi belirteç adlarına sahip denetimler için. |
| | ... belirtilen dışında bir arka plan/ön plan birleşimi. |

**Komut simgesi: varsayılan durum**

![Komut simgesi varsayılan](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Varsayılan komut simgesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok (komut çubuğu arka planıyla devralır) |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Kenarlık | Yok |

**Komut simgesi: varsayılan durum, seçili**

![Varsayılan, seçili komut simgesi](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Varsayılan, seçili komut simgesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarSelected` |
| Ön plan (metin) | `Environment.CommandBarTextSelected` |
| Kenarlık | `Environment.CommandBarSelectedBorder` |

**Komut simgesi: üzerine gelme veya odak durumları**

![Vurgu veya odak üzerinde komut simgesi](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Vurgu veya odak üzerinde komut simgesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.CommandBarTextHover` |
| Kenarlık | `Environment.CommandBarBorder` |

**Komut simgesi: üzerine gelme veya odak durumları, seçili**

![Vurgu veya odak üzerinde seçili komut simgesi](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Vurgu veya odak üzerinde seçili komut simgesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarHoverOverSelected` |
| Ön plan (metin) | `Environment.CommandBarTextHoverOverSelected` |
| Kenarlık | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Komut simgesi: basılan durum**

![Basılan komut simgesi](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Basılan komut simgesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.CommandBarTextMouseDown` |
| Kenarlık | `Environment.CommandBarBorder` |

**Komut simgesi: devre dışı durumu**

![Devre dışı komut simgesi](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Devre dışı komut simgesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok (komut çubuğu arka planıyla devralır) |
| Ön plan (metin) | `Environment.CommandBarTextInactive` |
| Kenarlık | Yok |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a> Komut çubuğu Birleşik giriş kutuları

> [!IMPORTANT]
> Birleşik giriş kutuları, açılan kutularla benzerdir, ancak düzenlenebilir bir metin bölgesi içerir. Açılır metniniz düzenlenebilir bir metin bölgesi içermiyorsa, [komut çubuğu açılır listeleri](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)için renk belirteçlerini kullanın.

![Komut çubuğu açılan kutusu Redline](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Komut çubuğu açılan kutusu (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Özel Birleşik giriş kutuları oluştururken. | ... her zaman komut çubuğu kullanıcı arabirimiyle eşleştirmek istemediğiniz her şey için. |
| ... Birleşik giriş kutusuna benzer bir komut çubuğu denetimi oluştururken. | ... Stil eklenmiş bir Birleşik giriş kutusuna erişiminiz olduğunda. |

**Komut çubuğu açılan kutusu giriş alanı: varsayılan durum**

![Komut çubuğu açılan kutusu giriş alanı](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Komut çubuğu açılan kutusu giriş alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxBackground` |
| Ön plan (metin) | `Environment.ComboBoxText` |
| Kenarlık | `Environment.ComboBoxBorder` |
| Ayırıcı | Ayırıcı yok |

**Komut çubuğu açılır düğmesi: varsayılan durum**

![Birleşik giriş kutusu açılan&#45;aşağı düğmesi](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok (komut çubuğu arka planıyla devralır) |
| Ön plan (karakter) | `Environment.ComboBoxGlyph` |

**Komut çubuğu açılan listesi: varsayılan durum**

![Komut çubuğu açılan listesi](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Komut çubuğu açılan listesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxPopupBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.ComboBoxItemText` |
| Kenarlık | `Environment.ComboBoxPopupBorder` |

**Komut çubuğu açılan kutusu giriş alanı: üzerine gelme durumu**

![Üzerine gelindiğinde komut çubuğu açılan kutusu giriş alanı](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Üzerine gelindiğinde komut çubuğu açılan kutusu giriş alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.ComboBoxMouseOverText` |
| Kenarlık | `Environment.ComboBoxMouseOverBorder` |
| Ayırıcı | `Environment.ComboBoxMouseOverSeparator` |

 **Komut çubuğu açılır düğmesi: üzerine gelme durumu**

![Üzerine gelindiğinde komut çubuğu açılan kutusu açılır düğmesi](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Vurgu üzerinde komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxButtonMouseOverBackground` |
| Ön plan (karakter) | `Environment.ComboBoxMouseOverGlyph` |

**Komut çubuğu açılır listesi: üzerine gelme durumu**

 ![Üzerine gelindiğinde komut çubuğu açılan kutusu açılan listesi](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Üzerine gelindiğinde komut çubuğu açılır listesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka plan (menü öğesi) | `Environment.ComboBoxItemMouseOverBackground` |
| Ön plan (metin) | `Environment.ComboBoxItemMouseOverText` |
| Kenarlık (menü öğesi) | `Environment.ComboBoxItemMouseOverBorder` |

 **Komut çubuğu açılan kutusu giriş alanı: odaklanmış durum**

![Odaklanmış komut çubuğu açılan kutusu giriş alanı](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Odaklanmış komut çubuğu açılan kutusu giriş alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxFocusedBackground` |
| Ön plan (metin) | `Environment.ComboBoxFocusedText` |
| Kenarlık | `Environment.ComboBoxFocusedBorder` |
| Ayırıcı | `Environment.ComboBoxFocusedButtonSeparator` |

**Komut çubuğu açılır düğmesi: odaklanmış durum**

![Odaklanmış komut çubuğu açılır düğmesi](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Odaklanmış komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxFocusedButtonBackground` |
| Ön plan (karakter) | `Environment.ComboBoxFocusedGlyph` |

 **Komut çubuğu açılan kutusu giriş alanı: basılı durum**

![Basılan komut çubuğu açılan kutusu giriş alanı](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Basılan komut çubuğu açılan kutusu giriş alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxMouseDownBackground` |
| Ön plan (metin) | `Environment.ComboBoxMouseDownText` |
| Kenarlık | `Environment.ComboBoxMouseDownBorder` |
| Ayırıcı | `Environment.ComboBoxMouseDownSeparator` |

**Komut çubuğu açılır düğmesi: basılı durum**

![Basılan komut çubuğu açılan kutusu açılan düğmesi](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Basılan komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxButtonMouseDownBackground` |
| Ön plan (karakter) | `Environment.ComboBoxMouseDownGlyph` |

**Komut çubuğu açılan kutusu giriş alanı: devre dışı durumu**

![Devre dışı komut çubuğu açılan kutusu giriş alanı](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Devre dışı komut çubuğu açılan kutusu giriş alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ComboBoxDisabledBackground` |
| Ön plan (metin) | `Environment.ComboBoxDisabledText` |
| Kenarlık | `Environment.ComboBoxDisabledBorder` |
| Ayırıcı | Ayırıcı yok |

**Komut çubuğu açılır düğmesi: devre dışı durumu**

![Devre dışı komut çubuğu açılan kutusu açılan düğmesi](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Devre dışı komut çubuğu açılan düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a> Komut çubuğu açılır listeleri

> [!IMPORTANT]
> Açılan kutulamalar, Birleşik giriş kutularına benzerdir, ancak düzenlenebilir metin bölgelerine benzer. Açılır metniniz düzenlenebilir bir metin bölgesi içeriyorsa, [komut çubuğu Birleşik giriş kutuları](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)için renk belirteçlerini kullanın.

![Komut çubuğu açılır (Redline)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Komut çubuğu açılır (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... özel açılan liste denetimleri oluştururken. | ... açılan listeye benzer olmayan her şey için. |
| | ... Birleşik giriş kutuları veya bölme düğmeleri için. |

**Komut çubuğu aşağı açılan seçim alanı: varsayılan durum**

![Varsayılan komut çubuğu aşağı açılan seçim alanı](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Varsayılan komut çubuğu aşağı açılan seçim alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.DropDownBackground` |
| Ön plan (metin) | `DropDownText` |
| Kenarlık | `DropDownBorder` |
| Ayırıcı | Ayırıcı yok |

**Komut çubuğu açılır düğmesi: varsayılan durum**

![Varsayılan komut çubuğu açılır düğmesi](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Varsayılan komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `Environment.DropDownGlyph` |

**Komut çubuğu açılan listesi: varsayılan durum**

![Varsayılan komut çubuğu açılan listesi](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Varsayılan komut çubuğu açılan listesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.DropDownPopupBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.ComboBoxItemText` |
| Kenarlık | `Environment.DropDownPopupBorder` |
| Gölgeli | `Environment.DropShadowBackground` |

**Komut çubuğu aşağı açılan seçim alanı: üzerine gelme durumu**

![Üzerine gelindiğinde komut çubuğu açılır seçme alanı](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Üzerine gelindiğinde komut çubuğu açılır seçme alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.DropDownMouseOverBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.DropDownMouseOverText` |
| Kenarlık | `Environment.DropDownMouseOverBorder` |
| Ayırıcı | `Environment.DropDownButtonMouseOverSeparator` |

**Komut çubuğu açılır düğmesi: üzerine gelme durumu**

![Vurgu üzerinde komut çubuğu açılır düğmesi](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Vurgu üzerinde komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.DropDownButtonMouseOverBackground` |
| Ön plan (karakter) | `Environment.DropDownMouseOverGlyph` |

**Komut çubuğu açılır listesi: üzerine gelme durumu**

![Üzerine gelindiğinde komut çubuğu açılır listesi](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Üzerine gelindiğinde komut çubuğu açılır listesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka plan (menü öğesi) | `Environment.ComboBoxItemMouseOverBackground` |
| Ön plan (metin) | `Environment.ComboBoxItemMouseOverText` |
| Kenarlık (menü öğesi) | `Environment.ComboBoxItemMouseOverBorder` |

 **Komut çubuğu aşağı açılan seçim alanı: basılı durum**

![&#45;aşağı açılan seçim alanını basılmış](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Basılan komut çubuğu aşağı açılan seçim alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.DropDownMouseDownBackground` |
| Ön plan (metin) | `Environment.DropDownMouseDownText` |
| Kenarlık | `Environment.DropDownMouseDownBorder` |
| Ayırıcı | `Environment.DropDownButtonMouseDownSeparator` |

**Komut çubuğu açılır düğmesi: basılı durum**

![Basılan komut çubuğu açılır düğmesi](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Basılan komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.DropDownButtonMouseDownBackground` |
| Ön plan (karakter) | `Environment.DropDownMouseDownGlyph` |

**Komut çubuğu aşağı açılan seçim alanı: devre dışı durumu**

![Devre dışı komut çubuğu açılan seçim alanı](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Devre dışı komut çubuğu açılan seçim alanı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.DropDownDisabledBackground` |
| Ön plan (metin) | `Environment.DropDownDisabledText` |
| Kenarlık | `Environment.DropDownDisabledBorder` |
| Ayırıcı | Ayırıcı yok |

**Komut çubuğu açılır düğmesi: devre dışı durumu**

![Devre dışı komut çubuğu açılan düğmesi](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Devre dışı komut çubuğu açılan düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Komut çubuğu bölme düğmeleri
Bölünmüş düğmeler, birçok belirteç adını düğmeler, menüler ve komut çubuğu metni gibi diğer komut çubuğu denetimleriyle paylaşır. Gerekli tüm eylem ve açılan düğme belirteci adları kolaylık sağlaması için burada yinelenir. Bölünmüş düğme açılan listeleri [komut çubuğu menülerinin](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)uygulamalarıdır.

![Bölünmüş düğme Redline](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Komut çubuğu bölme düğmesi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... özel bir bölünmüş düğme oluştururken. | ... diğer tür düğmeleri için. |
| | ... belirtilen dışında bir arka plan/ön plan birleşimi. |

**Komut çubuğu bölme düğmesi: varsayılan durum**

![Varsayılan komut çubuğu bölünmüş düğmesi](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Varsayılan komut çubuğu bölünmüş düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Ön plan (karakter) | `Environment.CommandBarSplitButtonGlyph` |
| Kenarlık | Yok |
| Ayırıcı | Yok |

**Komut çubuğu bölme düğmesi: üzerine gelme durumu**

![Üzerine gelindiğinde komut çubuğu Böl düğmesi](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Üzerine gelindiğinde komut çubuğu Böl düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.CommandBarTextHover` |
| Ön plan (karakter) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Kenarlık | `Environment.CommandBarBorder` |
| Ayırıcı | `Environment.CommandBarSplitButtonSeparator` |

**Komut çubuğu bölme düğmesi: basılmış durumu**

![Basılan komut çubuğu Böl düğmesi](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Basılan komut çubuğu Böl düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.CommandBarTextMouseDown` |
| Ön plan (karakter) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Kenarlık | `Environment.CommandBarBorder` |
| Ayırıcı | Yok |

**Komut çubuğu bölme düğmesi: devre dışı durumu**

![Devre dışı komut çubuğu bölünmüş düğmesi](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Devre dışı komut çubuğu bölünmüş düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (metin) | `Environment.ComboBoxItemTextInactive` |
| Ön plan (karakter) | `Environment.CommandBarTextInactive` |
| Kenarlık | Yok |
| Ayırıcı | Yok |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Komut çubuğu ' diğer seçenekler ' ve ' overflow ' düğmeleri
"Diğer seçenekler" düğmesi, bir komut çubuğu grubu ilgili komut çubuğu düğmeleri ekleyerek veya kaldırarak özelleştirilebilir olduğunda kullanılır. "Taşma" düğmesi, bir komut çubuğu yatay boşluk eksikliği nedeniyle kesilmediğinde ve tıklama ' de görüntülenemeyecek komut çubuğu düğmelerini içeren bir menü gösteriyorsa, "taşma" düğmesi görünür. Bu iki düğmenin renkleri aynı belirteç adları kümesiyle denetlenir.

![Komut çubuğu ' diğer seçenekler ' düğmesi (Redline)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Komut çubuğu ' diğer seçenekler ' düğmesi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Özel ' diğer seçenekler ' veya ' overflow ' düğmeleri için. | ... ' daha fazla seçenek ' veya ' taşma ' düğmesine benzer işlevlere sahip olmayan düğmeler için. |

**Komut çubuğu ' diğer seçenekler ' ve ' taşma ' düğmeleri: varsayılan durum**

![Varsayılan komut çubuğu ' diğer seçenekler ' düğmesi](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Varsayılan komut çubuğu ' diğer seçenekler ' düğmesi

![Varsayılan komut çubuğu ' overflow ' düğmesi](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Varsayılan komut çubuğu ' overflow ' düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarOptionsBackground` |
| Ön plan (karakter) | `Environment.CommandBarOptionsGlyph` |

**Komut çubuğu ' diğer seçenekler ' ve ' taşma ' düğmeleri: üzerine gelme durumu**

![Vurgu üzerinde komut çubuğu ' diğer seçenekler ' düğmesi](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Vurgu üzerinde komut çubuğu ' diğer seçenekler ' düğmesi

![Üzerine gelindiğinde komut çubuğu ' overflow ' düğmesi](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Üzerine gelindiğinde komut çubuğu ' overflow ' düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (karakter) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Komut çubuğu ' diğer seçenekler ' ve ' taşma ' düğmeleri: basılmış durumu**

![Basılan komut çubuğu ' diğer seçenekler ' düğmesi](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Basılan komut çubuğu ' diğer seçenekler ' düğmesi

![Taşma](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Basılan komut çubuğu ' overflow ' düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (karakter) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Belge pencereleri
Visual Studio ortamı tarafından sağlandıklarından belge pencerelerini çoğaltmaya gerek yoktur. Ancak, Kullanıcı arabirimi her zaman Visual Studio ortamının bu bölümüyle tutarlı şekilde görünmesi için belge penceresinde kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.

Belge penceresi renk belirteçleri kullanılırken, bunları yalnızca benzer öğeler için ve her zaman çiftler halinde kullanın. Bunu yapmazsanız, Kullanıcı arabiriminize beklenmedik sonuçlar elde edebilirsiniz.

### <a name="document-window-frames"></a>Belge penceresi çerçeveleri
Belge pencereleri IDE 'ye yerleştirilmiş ya da ayrı bir pencere olarak kayan olabilir. Bir belge penceresi IDE dışında olduğunda, yine de bir belge kutusu içinde yer alır ve IDE 'nin bir parçası olduğu gibi arka plan, kenarlık, metin ve sekme renkleri vardır. Ancak, belge kendi arka planına, kenarlığına ve metin rengine sahip bir çerçevenin içinde yer alır. Araç pencereleri belge kutusuna yerleştirildiğinde, belge penceresi belirteç adlarından sekmelerin davranışını ve rengini alırlar.

![Sabitlenmiş belge penceresi (Redline)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Sabitlenmiş belge penceresi (Redline)

![Kayan belge penceresi (Redline)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Kayan belge penceresi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Belge penceresiyle eşleştirmek istediğiniz her yerde Kullanıcı arabirimini oluşturun. | ...  herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz. |

**Yerleştirilmiş veya kayan belge penceresi: varsayılan durum**

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Belge türüne bağlıdır |
| Ön plan (metin) | Belge türüne bağlıdır |
| Kenarlık | `Environment.ToolWindowBorder` |

**Odaklanmış, kayan belge pencere çerçevesi: varsayılan durum**

![Varsayılan odaklanmış, kayan belge pencere çerçevesi](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Varsayılan odaklanmış, kayan belge pencere çerçevesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowFloatingFrame` |
| Ön plan (metin) | `Environment.ToolWindowFloatingFrame` |
| Ön plan (karakter) | `Environment.RaftedWindowButtonActiveGlyph` |
| Kenarlık | `Environment.MainWindowActiveDefaultBorder` |
| Kenarlık (karakter) | `Environment.RaftedWindowButtonActiveBorder`<br />(Saydamlığa ayarla) |

**Odaklanmış olmayan, kayan belge pencere çerçevesi: varsayılan durum**

![Varsayılan, odaklanmış olmayan, kayan belge pencere çerçevesi](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Varsayılan, odaklanmış olmayan, kayan belge pencere çerçevesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowFloatingFrameInactive` |
| Ön plan (metin) | `Environment.ToolWindowFloatingFrameInactive` |
| Ön plan (karakter) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Kenarlık | `Environment.MainWindowInactiveBorder` |
| Kenarlık (karakter) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Saydamlığa ayarla) |

**Odaklanmış, kayan belge penceresi çerçevesi: üzerine gelme durumu**

![Odaklanmış, kayan belge pencere çerçevesi üzerine gidilme](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Odaklanmış, kayan belge pencere çerçevesi üzerine gidilme

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka plan (karakter) | `Environment.RaftedWindowButtonHoverActive` |
| Ön plan (karakter) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Kenarlık (karakter) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Odaklanmış olmayan, kayan belge penceresi çerçevesi: üzerine gelme durumu**

![Odaklanmadan, üzerine gelme üzerine kayan belge pencere çerçevesi](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Odaklanmadan, üzerine gelme üzerine kayan belge pencere çerçevesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka plan (karakter) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Ön plan (karakter) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Kenarlık (karakter) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Odaklanmış, kayan belge penceresi çerçevesi: basılmış durumu**

![Odaklanmış, kayan belge penceresi kare basma](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Odaklanmış, kayan belge penceresi kare basma

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka plan (karakter) | `Environment.RaftedWindowButtonDown` |
| Ön plan (karakter) | `Environment.RaftedWindowButtonDownGlyph` |
| Kenarlık (karakter) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Belge sekmeleri
Belge sekmeleri, o anda hangi belgelerin açık olduğunu, hangi belgenin seçili ya da etkin belgeyi nerede açık olduğunu göstermek için sekme kanalında oturlar. Araç pencereleri, Kullanıcı oraya yerleştirse de belge sekmesi kanalına yerleştirilebilir. Bu durumda, belge pencereleri ile aynı sekme renklerini kullanırlar. Belge pencere renkleriyle (Tema güncelleştirmeleri dahil olmak üzere veya yeni temalar yüklüyse) her zaman eşleştirmek istediğiniz kullanıcı arabirimini oluşturuyorsanız, bu renk belirteçlerine başvurun.

![Belge sekmeleri (Redline)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Belge sekmeleri (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Belge sekmelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimi oluşturun ve tema güncelleştirmelerini veya yeni tema renklerini otomatik olarak seçin. | ... kabuğun bir tema güncelleştirmesi olduğunda otomatik olarak değiştirilmesini istemediğiniz herhangi bir kullanıcı arabirimi için. |

#### <a name="open-document-tabs"></a>Belge sekmelerini aç
Her açık belge, belge sekmesi kanalında adını görüntüleyen bir sekmeye sahiptir. Belgeler, arka planda seçilebilir veya açılabilir ve sekmeleri şu durumları yansıtır:

- Seçilen sekme, şu anda belge kutusu 'nda görüntülenen belgeyi temsil eder. Seçili bir sekmede, belge alanının üst kenarına genişleyen bir belge kenarlığı bulunur.

- Arka plan sekmeleri, şu anda seçili olan sekme olmayan herhangi bir belge sekmeleridir. Tıklandıktan sonra, seçili sekme olur ve bu belirteç adlarından tüm arka plan, kenarlık ve metin renklerini elde ederler.

![Belge sekmesini aç (Redline)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Belge sekmesini aç (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... özel belge sekmeleri oluştururken. | ... geçici (Önizleme) sekmeleri için. |
| | ... herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz. |

**Seçili, odaklanmış belge sekmesi**

![Seçili, odaklanmış belge sekmesi](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Seçili, odaklanmış belge sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.FileTabSelectedGradientTop`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.FileTabSelectedText` |
| Kenarlık | `Environment.FileTabSelectedBorder`<br />(Arka plan ile aynı renge ayarlanır.) |
| Belge kenarlığı | `Environment.FileTabDocumentBorderBackground` |

**Seçili, odaklanmış olmayan belge sekmesi**

![Seçili, odaklanmış olmayan belge sekmesi](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Seçili, odaklanmış olmayan belge sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.FileTabInactiveGradientTop`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.FileTabInactiveText` |
| Kenarlık | `Environment.FileTabInactiveBorder`<br />(Arka plan ile aynı renge ayarlanır.) |
| Belge kenarlığı | `Environment.FileTabInactiveDocumentBorderBackground` |

**Arka plan belgesi sekmesi: varsayılan durum**

![Varsayılan arka plan belgesi sekmesi](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Varsayılan arka plan belgesi sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.FileTabBackground` |
| Ön plan (metin) | `Environment.FileTabText` |
| Kenarlık | `Environment.FileTabBorder`<br />(Arka plan ile aynı renge ayarlanır.) |

**Arka plan belgesi sekmesi: üzerine gelme durumu**

![Üzerine gelme sırasında arka plan belgesi sekmesi](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Üzerine gelme sırasında arka plan belgesi sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.FileTabHotGradientTop`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.FileTabHotText` |
| Kenarlık | `Environment.FileTabHotBorder`<br />(Arka plan ile aynı renge ayarlanır.) |

#### <a name="preview-tab"></a>Önizleme sekmesi
"Geçici" sekme olarak da adlandırılır. Kullanıcı Çözüm Gezgini araç penceresinde bir öğeye tıkladığında, belge sekmesi kanalının sağ tarafında Önizleme sekmesi görünür. Belgenin bir önizlemesi görevi görür ve kullanıcıya belgeyi belge sekmesi kanalının sol tarafında açık tutma seçeneğini de sağlar. Tek seferde yalnızca bir Önizleme sekmesi açık olabilir. Önizleme sekmeleri, açık sekmeler gibi hem arka plan hem de seçili durumlara sahiptir ve etkin durumlarına odaklanmış veya odaklaneklenebilir.

![Önizleme sekmesi (Redline)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Önizleme sekmesi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... geçici önizleme oluşturduğunuz her yerde ve bazı öğelerinin geçerli Önizleme sekmesi rengiyle eşleşmesini istiyorsunuz. | ... her türlü belge veya sekme için geçici olmayan (Önizleme). |
| | ... herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz. |

**Odaklanmış, seçili Önizleme sekmesi**

![Odaklanmış, seçili Önizleme sekmesi](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Odaklanmış, seçili Önizleme sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.FileTabProvisionalSelectedActive` |
| Ön plan (metin) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Kenarlık | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Arka plan ile aynı renge ayarlanır.) |
| Belge kenarlığı | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Odaklanmış olmayan, seçili Önizleme sekmesi**

![Odaklanmış olmayan, seçili Önizleme sekmesi](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Odaklanmış olmayan, seçili Önizleme sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.FileTabProvisionalSelectedInactive` |
| Ön plan (metin) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Kenarlık | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Belge kenarlığı | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Arka plan Önizleme sekmesi: varsayılan durum**

![Varsayılan arka plan Önizleme sekmesi](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Varsayılan arka plan Önizleme sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.FileTabProvisionalInactive` |
| Ön plan (metin) | `Environment.FileTabProvisionalInactiveForeground` |
| Kenarlık | `Environment.FileTabProvisionalInactiveBorder`<br />(Arka plan ile aynı renge ayarlanır.) |

**Arka plan Önizleme sekmesi: üzerine gelme durumu**

![Üzerine gelme sırasında arka plan Önizleme sekmesi](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Üzerine gelme sırasında arka plan Önizleme sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.FileTabProvisionalHover` |
| Ön plan (metin) | `Environment.FileTabProvisionalHoverForeground` |
| Kenarlık | `Environment.FileTabProvisionalHoverBorder`<br />(Arka plan ile aynı renge ayarlanır.) |

#### <a name="document-overflow-button"></a>Belge taşması düğmesi
Geçerli yapılandırmada tüm belge sekmelerine sığacak şekilde bir veya daha fazla belge açıksa, belge taşma düğmesi vardır. [Komut çubuğu menü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) renkleri tarafından denetlenen belge taşması açılır menüsü, tüm açık belgelerin bir listesini, hem görünür hem de gizli ve taşma karakteri tüm açık belgelerin sekme kanalında görüntülenip görüntülenmediğini bağlı olarak değişir.

![Belge taşması düğmesi (Redline)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Belge taşması düğmesi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... özel bir belge taşması düğmesi oluştururken. | ... taşma düğmesine benzer olmayan kullanıcı arabirimi için. |
| | ... komut çubuğu taşma düğmeleri için. |

**Belge taşma düğmesi: varsayılan durum**

![Varsayılan belge taşması düğmesi](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Varsayılan belge taşması düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.DocWellOverflowButtonBackground` |
| Ön plan (karakter) | `Environment.DocWellOverflowButtonGlyph` |
| Kenarlık | Yok |

**Belge taşma düğmesi: üzerine gelme durumu**

![Üzerine gelindiğinde belge taşması düğmesi](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Üzerine gelindiğinde belge taşması düğmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Ön plan (karakter) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Kenarlık | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Belge taşma düğmesi: basılı durum**

![Belge taşma düğmesi basılı](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Belge taşma düğmesi basılı

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Ön plan (karakter) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Kenarlık | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Etiketleme
Visual Studio, bir kullanıcının izleme amacıyla aranabilir anahtar sözcükleri bildirmesine olanak sağlayan etiketlemeyi destekler. Örneğin, proje yöneticileri ve geliştiriciler iş öğelerini etiketlemek için Team Foundation Server (TFS) kullanabilir. Aşağıdaki tablolarda hem etiketin kendisi için renk adları hem de üzerine gelme ve seçili durumlarda görüntülenen "Kapat simgesi" karakteri verilmiştir.

![Visual Studio 'da etiketleme (Redline)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Visual Studio 'da etiketleme (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... etiketlemeyi destekleyen kullanıcı arabirimi için. | ... Diğer Kullanıcı arabirimi türleri için. |

#### <a name="tags"></a>Etiketler

**Etiket: varsayılan durum**

![Varsayılan etiket](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Varsayılan etiket

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Tag.Background` |
| Ön plan (metin) | `Tag.Background` |

**Etiket: üzerine gelme durumu**

![Üzerine gelindiğinde etiketle](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Üzerine gelindiğinde etiketle

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Tag.HoverBackground` |
| Ön plan (metin) | `Tag.HoverBackgroundText` |

**Etiket: basılan durum**

![Basılmış etiketi](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Basılmış etiketi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Tag.PressedBackground` |
| Ön plan (metin) | `Tag.PressedBackgroundText` |

**Etiket: Seçili durum**

![Seçili etiket](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Seçili etiket

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Tag.SelectedBackground` |
| Ön plan (metin) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Close ( &times; ) etiketi karakteri

**Close ( &times; ) etiketi karakteri: varsayılan durum**

![Varsayılan Close ( &times; ) etiketi karakteri](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Varsayılan Close ( &times; ) etiketi karakteri

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `Tag.TagHoverGlyph` |

**Close ( &times; ) etiketi karakteri: üzerine gelme durumu**

![&times;Üzerine gelindiğinde Close () etiketi karakteri](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />&times;Üzerine gelindiğinde Close () etiketi karakteri

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Tag.TagHoverGlyphHoverBackground` |
| Ön plan (karakter) | `Tag.TagHoverGlyphHover` |
| Kenarlık | `Tag.TagHoverGlyphHoverBorder` |

**Close ( &times; ) etiketi karakteri: basılmış durumu**

![Basılan Close ( &times; ) etiketi karakteri](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Basılan Close ( &times; ) etiketi karakteri

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Tag.TagHoverGlyphPressedBackground` |
| Ön plan (karakter) | `Tag.TagHoverGlyphPressed` |
| Kenarlık | `Tag.TagHoverGlyphPressedBorder` |

**Close () karakteri ile seçili etiket &times; : varsayılan durum**

![Close () karakteri ile seçili varsayılan etiket &times;](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Close () karakteri ile seçili varsayılan etiket &times;

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `Tag.TagSelectedGlyph` |

**Close () karakteri ile seçili etiket &times; : üzerine gelme durumu**

![&times;Üzerine gelme üzerinde Close () karakteri ile seçili etiket](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />&times;Üzerine gelme üzerinde Close () karakteri ile seçili etiket

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Tag.TagSelectedGlyphHoverBackground` |
| Ön plan (karakter) | `Tag.TagSelectedGlyphHover` |
| Kenarlık | `Tag.TagSelectedGlyphHoverBorder` |

**Close () karakteri ile seçili etiket &times; : basılan durum**

![Selected, basılan karakter with Close ( &times; ) karakteri](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Selected, basılan karakter with Close ( &times; ) karakteri

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Tag.TagSelectedGlyphPressedBackground` |
| Ön plan (karakter) | `Tag.TagSelectedGlyphPressed` |
| Kenarlık | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Araç pencereleri
Visual Studio ortamı tarafından sağlandıklarından araç pencerelerini çoğaltmanıza gerek yoktur. Ancak, Kullanıcı arabirimi her zaman Visual Studio ortamının bu bölümüyle tutarlı şekilde göründüğünden, araç pencereleri için kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.

![Araç penceresi (Redline)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Araç penceresi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... araç pencerelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimini oluşturun. | ... herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz. |

### <a name="tool-window-frame"></a>Araç penceresi çerçevesi
Visual Studio 'daki araç pencereleri birçok farklı görev için kullanılır ve birçok farklı durumdan birinde bulunabilir. Bir araç penceresi açıksa, belge alanının dört taraflarından herhangi birine atanabilir. Araç pencereleri Ayrıca IDE dışında kaydırılabilir, bu da kullanıcının ekranındaki herhangi bir yerde yeniden konumlandırılabilirler. Kayan pencereler her zaman IDE 'nin üstüne yaslanıp. Son olarak, araç pencereleri belge pencereleri olarak sabitlenebilir ve belge kutusunda bir sekme olarak görünebilir. Belge pencereleri olarak yerleştirilmiş olan araç pencereleri, belge penceresi belirteç adları kullanılarak kısmen renklendirilir.

![Araç penceresi çerçevesi (Redline)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Araç penceresi çerçevesi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ...  araç pencerelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimini oluşturun. | ... herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz. |

**Sabitlenmiş araç penceresi**

![Sabitlenmiş araç penceresi](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Sabitlenmiş araç penceresi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowBackground` |
| Kenarlık | `Environment.ToolWindowBorder` |

**Kayan, odaklanmış araç penceresi**

![Kayan, odaklanmış araç penceresi](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Kayan, odaklanmış araç penceresi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowBackground` |
| Kenarlık | `Environment.MainWindowActiveDefaultBorder` |

**Kayan, odaklanmış olmayan araç penceresi**

![Kayan, odaklanmış olmayan araç penceresi](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Kayan, odaklanmış olmayan araç penceresi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowBackground` |
| Kenarlık | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Araç kutusu-benzeri pencereler
Araç kutusu, Visual Studio 'da en sık kullanılan yaygın araç pencerelerini biridir. Bu aslında özel tema ve stil uygulanmış bir ağaç denetimidir.

![Araç kutusu benzeri pencere (Redline)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Araç kutusu benzeri pencere (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... her zaman kabuk araç kutusu ile tutarlı olmasını istediğiniz bir araç penceresi tasarlıyorsunuz. | ... Araç kutusu kullanıcı arabirimine benzer olmayan veya kabuk araç kutusu renkleri değiştiğinde Kullanıcı arabiriminde sorun olup olmadığından emin değilseniz. |

**Araç kutusu düğümleri: varsayılan durum**

![Varsayılan araç kutusu üst düğümü](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Varsayılan araç kutusu üst düğümü

![Varsayılan araç kutusu alt düğümü](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Varsayılan araç kutusu alt düğümü

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolboxContent`<br />Larınızı |
| Arka Plan | `Environment.ToolWindowBackground`<br />(Kullanılabilir denetim yoksa tek tek öğeler veya tüm pencere) |
| Kenarlık | Yok |
| Ön plan (karakter) | `Environment.ToolboxContent` |
| Ön plan (metin) | `Environment.ToolboxContent` |

**Araç kutusu alt düğümleri: üzerine gelme durumu**

![Bağlantı kutusu üzerinde alt düğüm](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Bağlantı kutusu üzerinde alt düğüm

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolboxContentMouseOver`<br />(Yalnızca ayrı öğeler) |
| Kenarlık | Yok |
| Ön plan (metin) | `Environment.ToolboxContentMouseOver`<br />(Yalnızca ayrı öğeler) |

**Seçili araç kutusu düğümleri: odaklanmış durum**

![Odaklanmış, seçili araç kutusu üst düğümü](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Odaklanmış, seçili araç kutusu üst düğümü

![Odaklanmış, seçili araç kutusu alt düğümü](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Odaklanmış, seçili araç kutusu alt düğümü

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemActive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |
| Kenarlık | `TreeView.FocusVisualBorder`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |
| Ön plan (karakter) | `TreeView.SelectedItemActive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |
| Ön plan (metin) | `TreeView.SelectedItemActive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |

**Seçili araç kutusu düğümleri: odaklanmış olmayan durum**

![Seçili, odaklanmış olmayan araç kutusu üst düğümü](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Seçili, odaklanmış olmayan araç kutusu üst düğümü

![Seçili, odaklanmış olmayan araç kutusu alt düğümü](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Seçili, odaklanmış olmayan araç kutusu alt düğümü

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `TreeView.SelectedItemInactive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |
| Kenarlık | Yok |
| Ön plan (karakter) | `TreeView.SelectedItemInactive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |
| Ön plan (metin) | `TreeView.SelectedItemInactive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |

### <a name="tool-window-title-bar"></a>Araç penceresi başlık çubuğu
Başlık çubuğu kenarlığı gerçek bir kenarlık değildir ve başlık çubuğunun üst kısmında kalın bir çizgi olur. Bu, odaklanmış olmayan durumu için bir belirteç adına sahip değil.

![Araç penceresi başlık çubuğu (Redline)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Araç penceresi başlık çubuğu (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... araç pencerelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimini oluşturun. | ... herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz. |

**Odaklanmış başlık çubuğu**

![Odaklanmış başlık çubuğu](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Odaklanmış başlık çubuğu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.TitleBarActiveGradientBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.TitleBarActiveText` |
| Kenarlık | `Environment.TitleBarActiveBorder`<br />(Arka plan ile aynı renge ayarlanır.) |
| Sürükleme tutamacı | `Environment.TitleBarDragHandleActive` |

**Odaklanmış olmayan başlık çubuğu**

![Başlık çubuğu odaklanmış değil](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Odaklanmış olmayan başlık çubuğu

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.TitleBarInactiveGradientBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.TitleBarInactiveText` |
| Kenarlık | Yok |
| Sürükleme tutamacı | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Araç penceresi başlık çubuğu düğmeleri
![Başlık çubuğu düğmesi (Redline)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Başlık çubuğu düğmesi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... araç penceresi başlık çubuklarından renk belirteçleri kullanan kullanıcı arabiriminde görünen düğmeler için. | ... diğer konumlarda görünen düğmeler için. |
| | ... belirtilen dışında bir arka plan/ön plan birleşimi. |

**Odaklanmış başlık çubuğu düğmeleri: varsayılan durum**

![Varsayılan, odaklanmış başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Varsayılan, odaklanmış başlık çubuğu düğmeleri

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `Environment.ToolWindowButtonActiveGlyph` |
| Kenarlık | Yok |

**Odaklanmış olmayan başlık çubuğu düğmeleri: varsayılan durum**

![Varsayılan, odaklanmış olmayan başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Varsayılan, odaklanmış olmayan başlık çubuğu düğmeleri

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | Yok |
| Ön plan (karakter) | `Environment.ToolWindowButtonInactiveGlyph` |
| Kenarlık | Yok |

**Odaklanmış başlık çubuğu düğmeleri: üzerine gelme durumu**

![Üzerine gelme üzerinde odaklanmış başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Üzerine gelme üzerinde odaklanmış başlık çubuğu düğmeleri

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowButtonHoverActive` |
| Ön plan (karakter) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonHoverActiveBorder` |

**Odaklanmış olmayan başlık çubuğu düğmeleri: üzerine gelme durumu**

![Üzerine gelme üzerinde odaklanmış başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Üzerine gelme üzerinde odaklanmış başlık çubuğu düğmeleri

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowButtonHoverInactive` |
| Ön plan (karakter) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Odaklanmış başlık çubuğu düğmeleri: basılan durum**

![Basılı kumandanızda odaklanmış başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Basılı kumandanızda odaklanmış başlık çubuğu düğmeleri

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowButtonDown` |
| Ön plan (karakter) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonDownBorder` |

**Odaklanmış olmayan başlık çubuğu düğmeleri: basılan durum**

![Basılı olmayan başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Basılı olmayan başlık çubuğu düğmeleri

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowButtonDown` |
| Ön plan (karakter) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Araç penceresi sekmeleri
![Araç penceresi sekmesi (Redline)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Araç penceresi sekmesi (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... araç pencerelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimini oluşturun. | ... herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz. |

**Seçilen, odaklanmış araç penceresi sekmesi**

![Seçilen, odaklanmış araç penceresi sekmesi](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Seçilen, odaklanmış araç penceresi sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowTabSelectedTab` |
| Ön plan (metin) | `Environment.ToolWindowTabSelectedActiveText` |
| Kenarlık | `Environment.ToolWindowTabSelectedBorder`<br />(Arka plan ile aynı renge ayarlanır.) |

**Seçili, odaklanmış olmayan araç penceresi sekmesi**

![Seçili, odaklanmış olmayan araç penceresi sekmesi](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Seçili, odaklanmış olmayan araç penceresi sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowTabSelectedTab` |
| Ön plan (metin) | `Environment.ToolWindowTabSelectedText` |
| Kenarlık | `Environment.ToolWindowTabSelectedBorder`<br />(Arka plan ile aynı renge ayarlanır.) |

**Arka plan araç penceresi sekmesi: varsayılan durum**

![Varsayılan arka plan araç penceresi sekmesi](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Varsayılan arka plan araç penceresi sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Gradyan duraklar Visual Studio 2013 aynı renk değerine ayarlanır.) |
| Ön plan (metin) | `Environment.ToolWindowTabText` |
| Kenarlık | `Environment.ToolWindowTabBorder` |

**Arka plan araç penceresi sekmesi: üzerine gelme durumu**

![Üzerine gelme sırasında arka plan araç penceresi sekmesi](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Üzerine gelme sırasında arka plan araç penceresi sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Gradyan duraklar Visual Studio 2013 aynı renk değerine ayarlanır.) |
| Ön plan (metin) | `Environment.ToolWindowTabMouseOverText` |
| Kenarlık | `Environment.ToolWindowTabMouseOverBorder`<br />(Arka plan ile aynı renge ayarlanır.) |

### <a name="auto-hide-tabs"></a>Sekmeleri otomatik gizle

![Sekmeleri otomatik gizle (Redline)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Sekmeleri otomatik gizle (Redline)

| Kullan... | Kullanma... |
| --- | --- |
| ... Otomatik gizli araç penceresi sekmelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimini oluşturun. | ... herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz. |

**Sekmeleri otomatik gizle: varsayılan durum**

![Varsayılan otomatik gizleme sekmesi](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Varsayılan otomatik gizleme sekmesi

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.AutoHideTabBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.AutoHideTabText` |
| Kenarlık | `Environment.AutoHideTabBorder` |

**Sekmeleri otomatik gizle: üzerine gelme durumu**

![Üzerine gelindiğinde sekmeyi otomatik gizle](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Üzerine gelindiğinde sekmeyi otomatik gizle

| Öğe | Belirteç adı: category. Color |
| --- | --- |
| Arka Plan | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Bu belirteç için gradyan duraklarının temalı Kullanıcı arabiriminde kullanılmıyor.) |
| Ön plan (metin) | `Environment.AutoHideTabMouseOverText` |
| Kenarlık | `Environment.AutoHideTabMouseOverBorder` |
