---
title: Visual Studio için Paylaşılan Renkler | Microsoft Dokümanlar
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699939"
---
# <a name="shared-colors-for-visual-studio"></a>Visual Studio için paylaşılan renkler
Ortak Visual Studio kabuk öğelerini kullanan kullanıcı arabirimi tasarlarken veya arabirim öğenizin benzer özelliklerle tutarlı olmasını istediğinizde, renkleri seçmek ve atamak için paket tanım dosyalarındaki mevcut belirteç adlarını kullanın. Bu, uI'nizin genel Visual Studio ortamıyla tutarlı kalmasını ve temalar eklendiğinde veya güncelleştirildiğinde otomatik olarak güncelolmasını sağlar.

Bu makalede, benzer kullanıcı aracı kullanırken başvuruda bulunabileceğiniz yaygın Kullanıcı Aracı öğeleri ve kullandıkları belirteç adları açıklanmaktadır. Bu renk belirteçlerine nasıl erişilisürüp erişilenler hakkında özel bilgiler için [VSColor Hizmeti'ne](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)bakın.

Belirteç adlarını doğru kullandığınızdan emin olun:

- **Renk kendisi değil, işlevine göre belirteç adlarını kullanın.** Ortak paylaşılan renkler belirli arabirim öğeleriyle ilişkilidir ve yalnızca aynı veya benzer özellikler için kullanılmak üzere tasarlanmıştır. Örneğin, sırf rengi beğendiğiniz için, döndürülen bir açılan kutunun rengini döndürme ilerleme animasyonu için yeniden kullanmayın. Açılan kutunun ve animasyonun işlevleri farklıdır ve açılan kutuyla ilişkili renk değişirse, animasyon öğeniz için artık uygun bir renk olmayabilir. Tutarlı renk kullanımı, kullanıcılarınızı yönlendirmeye ve karışıklığı önlemeye yardımcı olur.

- **Doğru kombinasyonda arka plan ve metin renklerini kullanın.** Metinle birlikte kullanılması amaçlanan arka plan renkleri ilişkili bir metin renge sahip olur. Metin renklerini, bu arka plan için belirtilenler dışında kullanmayın. İlişkili bir metin rengi yoksa, metni görüntülemeyi beklediğiniz herhangi bir yüzey için bu arka plan rengini kullanmayın. Diğer metin ve arka plan renkleri birleşimleri okunamayan bir arabirimle sonuçlanabilir.

- **Konumlarına uygun denetim renklerini kullanın.** Bazı eyaletlerde, bazı Visual Studio denetimlerinin ayrı kenarlık ve arka plan renkleri yoktur. Bunun yerine, arkalarındaki yüzeylerden bu renkleri alırlar. Denetimi yerleştirdiğiniz konuma her zaman uygun belirteç adlarını kullandığınızdan emin olun.

> [!IMPORTANT]
> "Başlangıç Sayfası" veya "Elma Şarabı" kategorilerinde bulunan jetonları kullanmayın.

## <a name="common-shared-controls"></a>Ortak paylaşılan denetimler

Özelliğinizde standart bir Visual Studio komut çubuğu kullandığınızda, stilize edilmiş kabuk denetimlerine erişebilirsiniz. Bu ortak denetimleri yeniden şablona almamalısınız. Ancak, özel bir komut çubuğu oluşturmanız gerekiyorsa, özel denetimler oluşturmanız da gerekebilir. Bu durumda, kullanıcı arabiriminizin Visual Studio'nun geri kalanıyla tutarlı olması için aşağıdaki denetimlerin her biri için doğru belirteç adlarını kullandığınızdan emin olun.

### <a name="button-controls"></a>Düğme denetimleri

![Düğme denetimi redline](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... Visual Studio temaları (Açık, Koyu, Mavi veya bir sistem Yüksek Kontrast teması) ile entegre etmek istediğiniz belgedeki düğmeler için iyi. | ... Visual Studio temasının bir parçası olmayan özel bir arka plana karşı görüntülenecek düğmeler için. |

**Düğme: standart durum**

![Standart düğme](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standart")<br />Standart düğme

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Düğme | `CommonControls.Button` |
| Düğme kenarlığı | `CommonControls.ButtonBorder` |

**Düğme: varsayılan durum**

![Varsayılan düğme](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Varsayılan düğme

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Düğme | `CommonControls.ButtonDefault` |
| Düğme kenarlığı | `CommonControls.ButtonBorderDefault` |

**Düğme: devre dışı durum**

![Devre dışı bırakma düğmesi](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Devre dışı bırakma düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Düğme | `CommonControls.ButtonDisabled` |
| Düğme kenarlığı | `CommonControls.ButtonBorderDisabled` |

**Düğme: hover durumu**

![Hover üzerinde düğme](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Hover üzerinde düğme

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Düğme | `CommonControls.ButtonHover` |
| Düğme kenarlığı | `CommonControls.ButtonBorderHover` |

**Düğme: düğmeye basılmış durum**

![Düğmeye basıldı](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Tuşuna Basıldı")<br />Düğmeye basıldı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Düğme | `CommonControls.ButtonPressed` |
| Düğme kenarlığı | `CommonControls.ButtonBorderPressed` |

**Düğme: odaklanmış durum**

![Odaklanmış düğme](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Odaklanmış düğme

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Düğme | `CommonControls.ButtonFocused` |
| Düğme kenarlığı | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Kutu denetimlerini denetleme
![Onay kutusu (redline)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Onay kutusu (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... belgenin içinde bulunan onay kutusu denetimleri için iyi. | ... bir onay kutusu denetimi olmayan herhangi bir UI için. |

**Onay kutusu: varsayılan durum**

![Onay kutusu](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Varsayılan onay kutusu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.CheckBoxBackground` |
| Kenarlık | `CommonControls.CheckBoxBorder` |
| Metin | `CommonControls.CheckBoxText` |
| Glif | `CommonControls.CheckBoxGlyph` |

**Onay kutusu: devre dışı durum**

![Devre dışı bırakılmış onay kutusu](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Devre dışı bırakılmış onay kutusu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.CheckBoxBackgroundDisabled` |
| Kenarlık | `CommonControls.CheckBoxBorderDisabled` |
| Metin | `CommonControls.CheckBoxTextDisabled` |
| Glif | `CommonControls.CheckBoxGlyphDisabled` |

**Onay kutusu: hover durumu**

 ![Hover üzerinde onay kutusu](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Hover üzerinde onay kutusu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.CheckBoxBackgroundHover` |
| Kenarlık | `CommonControls.CheckBoxBorderHover` |
| Metin | `CommonControls.CheckBoxTextHover` |
| Glif | `CommonControls.CheckBoxGlyphHover` |

**Onay kutusu: basıldığında durum**

![Basılı onay kutusu](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Basılı onay kutusu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.CheckBoxBackgroundPressed` |
| Kenarlık | `CommonControls.CheckBoxBorderPressed` |
| Metin | `CommonControls.CheckBoxTextPressed` |
| Glif | `CommonControls.CheckBoxGlyphPressed` |

**Onay kutusu: odaklanmış durum**

![Odaklanmış onay kutusu](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Odaklanmış onay kutusu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.CheckBoxBackgroundFocused` |
| Kenarlık | `CommonControls.CheckBoxBorderFocused` |
| Metin | `CommonControls.CheckBoxTextFocused` |
| Glif | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Açılır ve açılan kutular
![Açılır/açılan kutu (redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Açılır/açılan kutu (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... iyi belgede açılır ve açılan kutular için. | ... açılır veya açılan kutu olmayan herhangi bir UI için. |
| | ... komut çubuğu [açılır bırakma veya](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) açılan [kutular](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)için. |

**Açılan düşüşler ve açılan kutular: varsayılan durum**

![Varsayılan açılır/açılan kutu](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Varsayılan açılır/açılan kutu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.ComboBoxBackground` |
| Kenarlık | `CommonControls.ComboBoxBorder` |
| Metin | `CommonControls.ComboBoxText` |
| Ayırıcı | `CommonControls.ComboBoxSeparator` |
| Glif | `CommonControls.ComboBoxGlyph` |
| Glyph arka plan | `CommonControls.ComboBoxGlyphBackground` |

**Açılır ve açılan kutular: devre dışı bırakma durumu**

![Devre dışı bırakma/açılan kutu](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Devre dışı bırakma/açılan kutu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.ComboBoxBackgroundDisabled` |
| Kenarlık | `CommonControls.ComboBoxBorderDisabled` |
| Metin | `CommonControls.ComboBoxTextDisabled` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorDisabled` |
| Glif | `CommonControls.ComboBoxGlyphDisabled` |
| Glyph arka plan | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Açılır düşüşler ve açılan kutular: hover durumu**

![Açılır/açılan kutu](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Açılır/açılan kutu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.ComboBoxBackgroundHover` |
| Kenarlık | `CommonControls.ComboBoxBorderHover` |
| Metin | `CommonControls.ComboBoxTextHover` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorHover` |
| Glif | `CommonControls.ComboBoxGlyphHover` |
| Glyph arka plan | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Açılır ve açılan kutular: basılmış durum**

![Basılı açılır/açılan kutu](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Basılı açılır/açılan kutu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.ComboBoxBackgroundPressed` |
| Kenarlık | `CommonControls.ComboBoxBorderPressed` |
| Metin | `CommonControls.ComboBoxTextPressed` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorPressed` |
| Glif | `CommonControls.ComboBoxGlyphPressed` |
| Glyph arka plan | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Açılan ve açılan kutular liste öğesi görünümü: basılı durum**

 ![Açılır/açılan kutu basılı liste öğesi görünümü](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Açılır/açılan kutu basılı liste öğesi görünümü

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Kenarlık | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Öğe metni | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Arka plan gölgesi | `CommonControls.ComboBoxListBackgroundShadow` |

**Açılır ve açılan kutular: odaklanmış durum**

![Odaklanmış açılır/açılan kutu](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Odaklanmış açılır/açılan kutu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.ComboBoxBackgroundFocused` |
| Kenarlık | `CommonControls.ComboBoxBorderFocused` |
| Metin | `CommonControls.ComboBoxTextFocused` |
| Ayırıcı | `CommonControls.ComboBoxSeparatorFocused` |
| Glif | `CommonControls.ComboBoxGlyphFocused` |
| Glyph arka plan | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Açılan düşüşler ve açılan kutular: metin giriş seçimi**

![Açılır/açılan kutu metin giriş seçimi](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Açılır/açılan kutu metin giriş seçimi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Vurgula | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Tabular veri (ızgara) kontrolleri
Izgara denetimleri olarak da bilinen tabular veri denetimleri, Visual Studio için birden çok sütunda büyük miktarda veri sunmak için kullanılabilecek ortak denetimlerdir. Standart tabular veri denetimleri Visual Studio içinde birden çok yerde bulunabilir: Hata Listesi araç penceresi, IntelliTrace raporları ve bellek yığını görünümü, diğerleri arasında. Her zaman sağlanan standart tabular veri denetimlerini kullanın. Bazı nadir durumlarda, standart tabular veri denetimlerine erişiminiz olmayabilir. Bu gibi durumlarda, Kullanıcı Arabirimi'nizin Visual Studio'daki diğer tabular veri denetimleriyle tutarlı olduğundan emin olmak için aşağıdaki belirteç adlarını kullanın.

![Tabular veri/ızgara kontrolü (redline)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Tabular veri/ızgara kontrolü (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... tabular veya ızgara kontrolleri için. | ... bir tabular veya ızgara denetimi olmayan herhangi bir UI için. |

#### <a name="column-headers"></a>Sütun başlıkları
Sütun üstbilgileri bir arka plan, kenarlık, başlık metni ve genellikle bir ızgara bu sütuna göre sıralandığında kullanılan isteğe bağlı bir glyph oluşur.

**Sütun üstbilgi: varsayılan durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Header.Default` |
| Ön Plan (Metin) | `Environment.CommandBarTextActive` |
| Ön Plan (Glyph) | `Header.Glyph` |
| Kenarlık | `Header.SeparatorLine` |

**Sütun üstbilgi: gezinme durumu**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Header.MouseOver` |
| Ön Plan (Metin) | `Environment.CommandBarTextHover` |
| Ön Plan (Glyph) | `Header.MouseOverGlyph` |
| Kenarlık | `Header.SeparatorLine` |

**Sütun üstbilgi: basılı durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `CommonControls.CheckBoxBackgroundPressed` |
| Ön Plan (Metin) | `CommonControls.CheckBoxBorderPressed` |
| Ön Plan (Glyph) | `CommonControls.CheckBoxTextPressed` |
| Kenarlık | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Liste görünümü öğeleri
 Liste görünümü öğeleri arka plan ve içerikten oluşur. İçerik metin, simge veya her ikisi olabilir.

**Liste görünümü öğeleri: varsayılan durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | Geçirgen |
| Ön Plan (Metin) | `Environment.CommandBarTextActive` |
| Kenarlık | None |

**Liste görünümü öğeleri: etkin durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `TreeView.SelectedItemActive` |
| Ön Plan (Metin) | `TreeView.SelectedItemActiveText` |
| Kenarlık | None |

**Liste görünümü öğeleri: etkin olmayan durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `TreeView.SelectedItemInactive` |
| Ön Plan (Metin) | `TreeView.SelectedItemInactiveText` |
| Kenarlık | None |

### <a name="ui-text"></a>Kullanıcı Bira sımetin

#### <a name="instructional-text"></a>Öğretim metni
Öğretici metin, iletişim veya belge sayfasında ne yapılacının üst üst üst ününe ait belirgin bir ana açıklama verir.

![Varsayılan öğretim metni](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Varsayılan öğretim metni

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>İkincil öğretim metni
Çok sayıda metin ve denetimiçeren belge sayfalarında, bazı öğretim metinleri farklı bir renk değeri kullanır. Bu, hangi bilgilerin en önemli olduğunu iletmeye ve Kullanıcı Bira öğelerinin genel yoğunluğunu azaltmaya yardımcı olur. (İpucu metni yle ilgili aşağıdaki bölüme de bakınız.)

![İkincil öğretim metni](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />İkincil öğretim metni

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>İpucu metni
İpucu metni boş bir denetimde, denetimin altında veya kullanıcıya ne yapacağını göstermek için boş bir belge yüzeyinde görünür. Pencere veya Denetim arka planlarile ipucu metni kullanabilirsiniz.

**Varsayılan ipucu metni**

![Varsayılan ipucu metni](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Varsayılan ipucu metni

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlEditHintText` |

**Gerekli ipucu metni**

![Gerekli ipucu metni](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Gerekli ipucu metni

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Environment.ControlRequiredHintText` |
| Arka plan | `Environment.ControlRequiredBackground` |

**Arama kutusu denetim metni**

> Arama denetimiyle ilgili diğer renk belirteçleri için [Arama kutularına](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) bakın.

![Arama kutusu denetim metni](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Arama kutusu denetim metni

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Köprü
Köprü, ön plan/arka plan çifti olmayan bir denetimdir. Her durumda, koyu, gri ve beyaz arka planlarda doğru görünecek ön plan köprü rengini kullanın. Köprü denetimi için renk belirteci kullanmazsanız, kırmızı yanıp sönen "pressed" için varsayılan sistem rengini görürsünüz. Bu, denetimin doğru ortam renk belirteci kullanmadığının sinyalidir.

![Köprü (redline)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Köprü (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel bir köprü oluşturmanız gerektiğinde. | ... köprü olmayan her şey için. |

**Köprü: varsayılan durum**

![Varsayılan köprü](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Varsayılan köprü

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön Plan (Metin) | `Environment.PanelHyperlink` |

**Köprü: hover durumu**

![Hover üzerinde Köprü](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Hover üzerinde Köprü

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön Plan (Metin) | `Environment.PanelHyperlinkHover` |

**Köprü: basılmış durum**

![Sıkıştırılmış köprü](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Sıkıştırılmış köprü

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön Plan (Metin) | `Environment.PanelHyperlinkPressed` |

**Köprü: devre dışı durum**

![Devre dışı bırakılmış köprü](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Devre dışı bırakılmış köprü

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön Plan (Metin) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Bilgi Çubukları
Bilgi çubukları belirli bir bağlam hakkında daha fazla bilgi sağlamak için kullanılır ve her zaman bir belge penceresinin veya araç penceresinin üst kısmında görünür.

![Bilgi Çubuğu (redline)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Bilgi Çubuğu (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel bilgi çubukları oluştururken. | ... bilgi çubuğuna benzemeyen UI öğeleri için. |

**Bilgi çubuğu: varsayılan durum**

![Varsayılan bilgi çubuğu](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Varsayılan bilgi çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `InfoBar.InfoBarBackground` |
| Ön Plan (Metin) | `InfoBar.InfoBar` |
| Kenarlık | `InfoBar.InfoBarBorder` |

**Bilgi Çubuğu&times;Kapat ( ) düğmesi: varsayılan durum**

![Varsayılan bilgi çubuğu&times;Kapat ( ) düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Varsayılan bilgi çubuğu&times;Kapat ( ) düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `InfoBar.CloseButton` |
| Kenarlık | `InfoBar.CloseButtonBorder` |
| Glif | `InfoBar.CloseButtonGlyph` |

**Bilgi Çubuğu&times;Kapat ( ) düğmesi: hover durumu**

![Bilgi Çubuğu&times;Kapat ( ) düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Bilgi Çubuğu&times;Kapat ( ) düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `InfoBar.CloseButtonHover` |
| Kenarlık | `InfoBar.CloseButtonHoverBorder` |
| Glif | `InfoBar.CloseButtonHoverGlyph` |

**Bilgi Çubuğu&times;Kapat ( ) düğmesi: düğmeye basıldığında durum**

![Basıldığında bilgi&times;çubuğu Kapat ( ) düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Basıldığında bilgi&times;çubuğu Kapat ( ) düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `InfoBar.CloseButtonDown` |
| Kenarlık | `InfoBar.CloseButtonDownBorder` |
| Glif | `InfoBar.CloseButtonDownGlyph` |

**Bilgi çubuğu köprü düğmesi: varsayılan durum**

![Varsayılan bilgi çubuğu köprü düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Varsayılan bilgi çubuğu köprü düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `InfoBar.Hyperlink` |

**Bilgi çubuğu köprü düğmesi: hover durumu**

![Hover üzerinde Infobar köprü düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Hover üzerinde Infobar köprü düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseOver`<br />(Altı çizili) |

**Bilgi çubuğu köprü düğmesi: basıldığında durum**

![Basıldığında infobar köprü düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Basıldığında infobar köprü düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseDown`<br />(Altı çizili) |

**Infobar satır içi köprü (cümle içinde): varsayılan durum**

![Varsayılan satır bilgisi çubuğu köprü düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Varsayılan satır bilgisi çubuğu köprü düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `InfoBar.Hyperlink` |

**Infobar satır içi köprü (bir cümle içinde): hover durumu**

![Bilgi çubuğu inline köprü düğmesi hover üzerinde](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Bilgi çubuğu inline köprü düğmesi hover üzerinde

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseOver`<br />(Altı çizili) |

**Infobar satır içi köprü (bir cümle içinde): basılmış durum**

![Basıldığında infobar satır içinde köprü düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Basıldığında infobar satır içinde köprü düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön plan (metin) | `Infobar.HyperlinkMouseDown`<br />(Altı çizili) |

**Bilgi çubuğu düğmesi: varsayılan durum**

![Varsayılan bilgi çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Varsayılan bilgi çubuğu düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `InfoBar.Button` |
| Ön plan (metin) | `InfoBar.Button` |
| Kenarlık | `InfoBar.ButtonBorder` |

**Bilgi çubuğu düğmesi: hover durumu**

![Hover üzerinde Bilgi Çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Hover üzerinde Bilgi Çubuğu düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `InfoBar.ButtonMouseOver` |
| Ön plan (metin) | `InfoBar.ButtonMouseOver` |
| Kenarlık | `InfoBar.ButtonMouseOverBorder` |

**Bilgi Çubuğu düğmesi: düğmeye basıldığında durum**

![Basıldığında bilgi çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Basıldığında bilgi çubuğu düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `InfoBar.ButtonMouseDown` |
| Ön plan (metin) | `InfoBar.ButtonMouseDown` |
| Kenarlık | `InfoBar.ButtonMouseDownBorder` |

**Bilgi çubuğu düğmesi: devre dışı durum**

![Devre dışı bırakılmış bilgi çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Devre dışı bırakılmış bilgi çubuğu düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `InfoBar.ButtonDisabled` |
| Ön plan (metin) | `InfoBar.ButtonDisabled` |
| Kenarlık | `InfoBar.ButtonDisabledBorder` |

**Bilgi çubuğu düğmesi: odaklanmış durum**

![Odaklanmış bilgi çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Odaklanmış bilgi çubuğu düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `InfoBar.ButtonFocus` |
| Ön plan (metin) | `InfoBar.ButtonFocus` |
| Kenarlık | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Çubukları kaydırma
Kaydırma çubukları Visual Studio ortamı tarafından şekillendirilir ve temalı olması gerekmez. Ancak, kullanıcı bilgilerinizin Visual Studio ortamının bu bölümüyle tutarlı görünmesi için kaydırma çubuklarında kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.

![Kaydırma çubuğu (redline)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Kaydırma çubuğu (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... Visual Studio kaydırma çubuklarıyla eşleştirmek istediğiniz ui'yi oluştururken. | ... her zaman kaydırma çubuğu Kullanıcı Arabirimi eşleştirmek istemiyorum şey için. |

**Kaydırma çubuğu: varsayılan durum**

![Varsayılan kaydırma çubuğu](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Varsayılan kaydırma çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Kaydırma çubuğu | `Environment.ScrollBarBackground` |
| Ön Plan (Başparmak) | `Environment.ScrollBarThumbBackground` |

**Kaydırma çubuğu: hover durumu**

![Gezinme çubuğu](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Gezinme çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Kaydırma çubuğu | `Environment.ScrollBarBackground` |
| Ön Plan (Başparmak) | `Environment.ScrollBarThumbMouseOverBackground` |

*Kaydırma çubuğu: basılı durum**

![Basılı kaydırma çubuğu](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Basılı kaydırma çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Kaydırma çubuğu | `Environment.ScrollBarBackground` |
| Ön Plan (Başparmak) | `Environment.ScrollBarThumbPressedBackground` |

**Kaydırma çubuğu oku: varsayılan durum**

![Varsayılan kaydırma çubuğu oku](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Varsayılan kaydırma çubuğu oku

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ScrollBarArrowBackground`<br />(Kaydırma çubuğuyla aynı renge ayarlayın.) |
| Ön Plan (Glyph) | `Environment.ScrollBarArrowGlyph` |

**Kaydırma çubuğu oku: hover durumu**

![Gezinme üzerinde çubuk oku kaydırma](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Gezinme üzerinde çubuk oku kaydırma

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ScrollBarArrowMouseOverBackground`<br />(Kaydırma çubuğuyla aynı renge ayarlayın.) |
| Ön Plan (Glyph) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Kaydırma çubuğu oku: basılı durum**

![Basılı kaydırma çubuğu oku](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Basılı kaydırma çubuğu oku

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ScrollBarArrowPressedBackground`<br />(Kaydırma çubuğuyla aynı renge ayarlayın.) |
| Ön Plan (Glyph) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Arama kutuları
Mümkün olduğunda, Visual Studio ortamı tarafından sağlanan ortak arama denetimini kullanın. Arama kutusu renkleri, giriş alanı, eylem düğmesi, açılır açma düğmesi ve açılır menü için belirteç adlarını içeren **ShellColors.pkgdef** dosyasındaki "SearchControl" kategorisinde bulunur.

Arama kutusu, bazıları birbirini dışlayan birkaç eyaletten biri olabilir:

- "Odaklanmış" veya "odaklanmamış", imlecin metin kutusunda olup olmadığını ifade eder.

- "Etkin" veya "etkin olmayan" kullanıcının metin kutusuna bir arama sorgusu giriş yapıp etmediğini ifade eder.

- "Hover", kullanıcının arama kutusunun üzerinde fareyle birlikte kullandığı anlamına gelir (bu durum diğer tüm durumları geçersiz kılar).

- "Devre dışı" arama işlevinin geçerli bağlam için kapalı olduğu anlamına gelir.

![Arama kutusu (redline)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Arama kutusu (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel bir arama kutusu tasarlarken. | ... Arama kutusu olmayan her şey için. |
| | ... her zaman arama kutusu Kullanıcı Arabirimi maç istemiyorum bir şey için. |

**Odaklanmış arama giriş alanı**

![Odaklanmış arama giriş alanı](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Odaklanmış arama giriş alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.FocusedBackground` |
| Ön Plan (Metin) | `SearchControl.FocusedBackground` |
| Kenarlık | `SearchControl.FocusedBorder` |
| Ayırıcı | `SearchControl.FocusedDropDownSeparator` |

**Odaklanmamış, etkin arama giriş alanı**

![Giriş alanını odaklanmadan arama](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Odaklanmamış, etkin arama giriş alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.SearchActiveBackground` |
| Ön Plan (Metin) | `SearchControl.SearchActiveBackground` |
| Kenarlık | `SearchControl.UnfocusedBorder` |
| Ayırıcı | `SearchControl.DropDownSeparator` |

**Odaklanmamış, etkin olmayan arama giriş alanı**

![Odaklanmamış, etkin olmayan arama giriş alanı](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Odaklanmamış, etkin olmayan arama giriş alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.Unfocused` |
| Ön Plan (Metin) | `SearchControl.Unfocused` |
| Kenarlık | `SearchControl.UnfocusedBorder` |
| Ayırıcı | `SearchControl.DropDownSeparator` |

**Vurgulanan arama giriş alanı (yalnızca metin)**

![Vurgulanan arama giriş alanı](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Vurgulanan arama giriş alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.Selection` |
| Ön Plan (Metin) | `SearchControl.FocusedBackground` |
| Kenarlık | None |
| Ayırıcı | `SearchControl.FocusedDropDownSeparator` |

**Devre dışı bırakılmış arama giriş alanı**

![Devre dışı bırakılmış arama giriş alanı](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Devre dışı bırakılmış arama giriş alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.Disabled` |
| Ön Plan (Metin) | `SearchControl.Disabled` |
| Kenarlık | `SearchControl.DisabledBorder` |
| Ayırıcı | `SearchControl.DropDownSeparator` |

**Odaklanmış arama eylem düğmesi**

![Arama eylem düğmesi odaklı](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Odaklanmış arama eylem düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | None |
| Ön Plan (Arama glyph) | `SearchControl.SearchGlyph` |
| Ön plan (Glyph'yi durdur) | `SearchControl.StopGlyph` |
| Ön plan (Açık glyph) | `SearchControl.ClearGlyph` |
| Kenarlık | Yok |

**Odaklanmamış arama eylem düğmesi**

![Odaklanmamış arama eylem düğmesi](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Odaklanmamış arama eylem düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | Yok |
| Ön Plan (Arama glyph) | `SearchControl.SearchGlyph` |
| Ön plan (Glyph'yi durdur) | `SearchControl.StopGlyph` |
| Ön plan (Açık glyph) | `SearchControl.ClearGlyph` |
| Kenarlık | Yok |

**Arama eylem düğmesine basıldı**

![Arama eylem düğmesine basıldı](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Arama eylem düğmesine basıldı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.ActionButtonMouseDown` |
| Ön Plan (Glyph) | `SearchControl.ActionButtonMouseDownGlyph` |
| Kenarlık | `SearchControl.ActionButtonMouseDownBorder` |

**Devre dışı bırakılmış arama eylem düğmesi**

![Arama eylem düğmesi devre dışı](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Devre dışı bırakılmış arama eylem düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | None |
| Ön Plan (Glyph) | `SearchControl.ActionButtonDisabledGlyph` |
| Kenarlık | None |

**Odaklanmış arama açılır düğmesi**

![Odaklanmış arama açılır düğmesi](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Odaklanmış arama açılır düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.FocusedDropDownButton` |
| Ön Plan (Glyph) | `SearchControl.FocusedDropDownButtonGlyph` |
| Kenarlık | `SearchControl.FocusedDropDownButtonBorder` |

**Odaklanmamış arama açılır düğmesi**

![Odaklanmamış arama açılır düğmesi](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Odaklanmamış arama açılır düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.UnfocusedDropDownButton` |
| Ön Plan (Glyph) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Kenarlık | `SearchControl.UnfocusedDropDownButtonBorder` |

**Basılı arama açılır düğmesi**

![Basılı arama açılır düğmesi](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Basılı arama açılır düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.MouseDownDropDownButton` |
| Ön Plan (Glyph) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Kenarlık | `SearchControl.MouseDownDropDownButtonBorder` |

**Devre dışı bırakma düğmesi**

![Devre dışı bırakma düğmesi](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Devre dışı bırakma düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | None |
| Ön Plan (Glyph) | `SearchControl.DisabledDownButtonGlyph` |
| Kenarlık | None |

#### <a name="search-drop-down-lists"></a>Açılan listelerde arama
Arama kutusu açılır menüsü Visual Studio'daki diğer açılır menülerden biraz daha karmaşık olma potansiyeline sahiptir. "Önerilen aramalar" ve "arama seçenekleri" bölümleri tek başına veya menüde birlikte görünebilir ve her biri ayrı ayrı renklenir. Bir satır, birlikte göründüklerinde bu iki bölümü de ayırır ve bir kenarlık açılır menüyü n için ilerler.

![Açılan listeyi ara (redline)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Açılan listeyi ara (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel bir arama açılır listesi oluştururken. | ... diğer bağlamlarda görünen açılır listeler için. |
| ... doğru liste bileşenleri için doğru belirteç adları. | ... belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda. |

**Açılan liste öğelerini arama**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Kenarlık | `SearchControl.PopupBorder` |
| Ayırıcı | `SearchControl.PopupSectionHeaderSeparator` |
| Gölge | `Environment.DropShadowBackground` |

**Önerilen aramalar: varsayılan durum**

![Varsayılan önerilen aramalar](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Varsayılan önerilen aramalar

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `SearchControl.PopupItemText` |

**Önerilen aramalar: hover state**

![Gezinme de önerilen aramalar](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Gezinme de önerilen aramalar

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `SearchControl.PopupMouseOverItemText` |
| Kenarlık | `SearchControl.PopupControlMouseOverBorder` |

**Arama seçenekleri: varsayılan durum**

![Arama onay kutusu](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Varsayılan arama seçenekleri (onay kutusu)

![Arama seçenekleri](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Varsayılan arama seçenekleri (bağlantı)

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön plan (Onay kutusu metni) | `SearchControl.PopupCheckboxText` |
| Ön plan (Bağlantı metni) | `SearchControl.PopupButtonText` |
| Üstbilgi arka planı | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön plan (Üstbilgi metni) | `SearchControl.PopupSectionHeaderText` |

**Arama seçenekleri: hover durumu**

![Gezinme üzerinde arama seçenekleri (onay kutusu)](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Gezinme üzerinde arama seçenekleri (onay kutusu)

![Gezinme üzerinde arama seçenekleri (bağlantı)](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Gezinme üzerinde arama seçenekleri (bağlantı)

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön plan (Onay kutusu metni) | `SearchControl.PopupCheckboxMouseDownText` |
| Ön plan (Bağlantı metni) | `SearchControl.PopupButtonMouseDownText` |
| Kenarlık | `SearchControl.PopupControlMouseOverBorder` |

**Arama seçenekleri: basılı durum**

![Basılı arama seçenekleri (onay kutusu)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Basılı arama seçenekleri (onay kutusu)

![Basılı arama seçenekleri (bağlantı)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Basılı arama seçenekleri (bağlantı)

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Kutu arka planını denetleme | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön plan (Onay kutusu metni) | `SearchControl.PopupCheckboxMouseDownText` |
| Bağlantı arka planı | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön plan (Bağlantı metni) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a>Ağaç görünümleri
Çözüm Gezgini, Sunucu Gezgini ve Sınıf Görünümü de dahil olmak üzere çeşitli araç pencereleri, `TreeView` renkleri kategorideki renk adlarıyla denetlenen hiyerarşik bir kuruluş düzeni uygular. Ağaç görünümündeki tüm öğelerin arka planı ve metin renkleri vardır. İç içe alt öğeleri olan öğeler, öğenin genişletilip genişletilmediğini veya daraltılıp yıkılmadığını gösteren gliflere de sahiptir.

![Ağaç görünümü (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Ağaç görünümü (kırmızı çizgi)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... hiyerarşik bir örgütsel görünüm uygulamak için gereken her yerde. | ... ağaç görünümüne benzemeyen herhangi bir şey için. |
| | ... belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda. |

**Ağaç görünümü öğesi: varsayılan durum**

![Varsayılan ağaç görünümü öğesi](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Varsayılan ağaç görünümü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `TreeView.Background` |
| Ön Plan (Metin) | `TreeView.Background` |
| Ön Plan (Glyph) | `TreeView.Glyph` |
| Kenarlık | None |

**Ağaç görünümü öğesi: gezinme durumu**

![Gezinme üzerinde ağaç görünümü öğesi](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Gezinme üzerinde ağaç görünümü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `TreeView.Background` |
| Ön Plan (Metin) | `TreeView.Background` |
| Ön Plan (Glyph) | `TreeView.GlyphMouseOver` |
| Kenarlık | None |

**Ağaç görünümü öğesi: durum üzerinde sürükleyin**

![Sürükleme üzerine ağaç görünümü öğesi](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Sürükleme üzerine ağaç görünümü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `TreeView.DragOverItem` |
| Ön Plan (Metin) | `TreeView.DragOverItem` |
| Ön Plan (Glyph) | `TreeView.DragOverItemGlyph` |
| Kenarlık | None |

**Ağaç görünümü öğesi: seçili, odaklanmış durum**

![Seçili ve odaklanmış ağaç görünümü öğesi](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Seçili ve odaklanmış ağaç görünümü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `TreeView.SelectedItemActive` |
| Ön Plan (Metin) | `TreeView.SelectedItemActive` |
| Ön Plan (Glyph) | `TreeView.SelectedItemActiveGlyph` |
| Kenarlık | `TreeView.FocusVisualBorder` |

**Ağaç görünümü öğesi: seçili, odaklanmamış durum**

![Seçili ve odaklanılmamış ağaç görünümü öğesi](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Seçili ve odaklanılmamış ağaç görünümü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `TreeView.SelectedItemInactive` |
| Ön Plan (Metin) | `TreeView.SelectedItemInactive` |
| Ön Plan (Glyph) | `TreeView.SelectedItemInactiveGlyph` |
| Kenarlık | None |

**Ağaç görünümü öğesi: havada gezinilmiş, seçili ve odaklanmış durum**

![Gezinme üzerinde seçili ve odaklanmış ağaç görünümü öğesi](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Gezinme üzerinde seçili ve odaklanmış ağaç görünümü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `TreeView.SelectedItemActive` |
| Ön Plan (Metin) | `TreeView.SelectedItemActive` |
| Ön Plan (Glyph) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Kenarlık | `TreeView.FocusVisualBorder` |

**Ağaç görünümü öğesi: havada gezinilmiş, seçili ve odaklanmamış durum**

![Gezinme üzerinde seçili ve odaklanmamış ağaç görünümü öğesi](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Gezinme üzerinde seçili ve odaklanmamış ağaç görünümü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `TreeView.SelectedItemInactive` |
| Ön Plan (Metin) | `TreeView.SelectedItemInactive` |
| Ön Plan (Glyph) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Kenarlık | None |

## <a name="shell-appearance"></a>Kabuk görünümü

### <a name="background"></a>Arka plan
Ortam arka planı iki katmandan oluşur. Alt tabaka, tüm IDE'yi kapsayan düz bir renktir. Üst katman komut rafının altına ve IDE'nin sol ve sağ kenarlarındaki araç penceresi nin otomatik olarak gizlediği kanalların arasına sığar. Üst ve alt arka plan katmanları, Açık ve Koyu temalarda aynı renge ayarlanır.

![Visual Studio kabuk arka planı (redline)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Visual Studio kabuk arka planı (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... Visual Studio ortamının arka planını eşleştirmek istediğiniz yerler için. | ... arka plan yüzeyleri olmayan yerler için bir dolgu olarak. |
| | ... ön plan öğeleri ni yerleştirmek için bir arka plan olarak. |

**Alt katman kabuk görünümü**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.EnvironmentBackground` |

**Üst katman kabuk görünümü**

> Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Komut rafı
Komut rafı arka planlar için iki belirteç adı kümesi kullanılır: biri menü çubuğunun bulunduğu yer için bir küme, diğeri de komut çubuklarının oturduğu yer için. Tek bir komut çubuğu grubunun kendi arka plan renk değerleri vardır ve bu değerler "komut çubuğu" bölümünde daha ayrıntılı olarak tartışılır. Menü çubuğu ve komut çubuğu metni sırasıyla menü ve komut çubuğu bölümlerinde ele alınmıştır.

![Visual Studio komut rafı (redline)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Visual Studio komut rafı (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... menüleri veya araç çubuklarını yerleştirdiğiniz alanlar için. | ... komut rafına benzemeyen alanlar için. |
|... doğru arka plan/ön plan belirteç adı kombinasyonu ile. | |

**Komut raf menü çubuğu**

> Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Komut raf komut çubuğu**

> Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Bildirim Tasarımcısı
Manifest Designer, Windows 8 ve Windows Phone 8 projelerinde manifesto dosyasını daha kolay bir şekilde yeniden yapılandırın. Tüketim için kullanılabilir paylaşılan bir çerçeve olmamasına gerek yok, ancak yön/gezinti sekmelerinin tasarım düzeni ve renkleri yle ve genel yapıyla eşleşmeniz uygun olabilir. Düzen ayrıntıları hakkında daha fazla bilgi için [Visual Studio için Düzen'e](../../extensibility/ux-guidelines/layout-for-visual-studio.md)bakın.

![Manifesto Tasarımcısı (redline)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Manifesto Tasarımcısı (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... Manifest Designer benzer tasarımcılar için. | ... altıdan fazla sekmeniz varsa. |
| ... belge içinde bir düzenleyicinin üst kısmında ortak sekme denetimleri kullanarak yerine iyi. | ... Manifest Designer gibi yapılandırılan herhangi bir UI için. |

**Manifest Designer seçili sekmesi: varsayılan durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `ManifestDesigner.TabActive` |
| Kenarlık | None |

**Manifest Designer seçili açıklama bölmesi: varsayılan durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `ManifestDesigner.DescriptionPane` |

**Manifest Designer seçili içerik sayfası: varsayılan durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `ManifestDesigner.Background` |
| İletişim yardımcı metni | `ManifestDesigner.WatermarkText`<br />(Bu belirteç adı işleviyle eşleşmiyor.) |

**Manifest Designer sekmesi: seçilmemiş durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `ManifestDesigner.Tab.Inactive` |

**Manifest Designer sekmesi: hover durumu**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Komut yapıları

### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menü
Menüler Visual Studio içinde çeşitli yerlerde oluşabilir: ana menü çubuğu, belge veya araç pencereleri gömülü, ya da IDE boyunca çeşitli yerlerde sağ tıklatın. Diğer UI öğeleriile ilişkili menülerin uygulamaları ilgili öğe için bölümde ele alınmıştır. Visual Studio ortamı tarafından sağlanan standart menü uygulamasını her zaman kullanmalısınız. Ancak, bazı nadir durumlarda standart Visual Studio menülerine erişiminiz olmayabilir. Bu gibi durumlarda, kullanıcı bir kullanıcı yanınızın Visual Studio'daki diğer menülerle tutarlı olduğundan emin olmak için aşağıdaki belirteç adlarını kullanın.

![Visual Studio menüsü (redline)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Visual Studio menüsü (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel bir menü oluşturmanız gerektiğinde.| ... tek başına arka plan rengi. Her zaman belirtildiği gibi arka plan/ön plan kombinasyonunu kullanın. |
| ... Visual Studio menülerini eşleştirmek istediğiniz yeni bir UI bileşenine sahip olduğunuzda.| |

#### <a name="menu-titles"></a>Menü başlıkları
Menü başlıkları bir arka plan, kenarlık ve başlık metninin yanı sıra genellikle menü bir komut çubuğunda bulunduğunda isteğe bağlı bir sözcükten oluşur.

![Menü başlığı (redline)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Menü başlığı (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel bir menü başlığı oluşturduğunuzda. | ... her zaman menü başlığı nı eşleştirmek istemediğiniz herhangi bir şey için. |
| | ... belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda. |

**Menü başlığı: varsayılan durum**

![Varsayılan menü başlığı](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Varsayılan menü başlığı

![Glyph ile varsayılan menü başlığı](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Glyph ile varsayılan menü başlığı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | None |
| Ön plan (metin) | `Environment.CommandBarTextActive` |
| Ön plan (glyph) | `Environment.CommandBarMenuGlyph` |
| Kenarlık | None |

**Menü başlığı: hover state**

![Hover üzerinde Menü başlığı](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Hover üzerinde Menü başlığı

![Hover üzerinde glyph ile Menü başlığı](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Hover üzerinde glyph ile Menü başlığı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön plan (metin) | `Environment.CommandBarTextHover` |
| Ön plan (glyph) | `Environment.CommandBarMenuMouseOverGlyph` |
| Kenarlık | `Environment.CommandBarBorder` |

**Menü başlığı: basıldığında durum**

![Basılı menü başlığı](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Basılı menü başlığı

![Glyph ile basılı menü başlığı](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Glyph ile basılı menü başlığı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.CommandBarTextActive` |
| Ön Plan (Glyph) | `Environment.CommandBarMenuMouseDownGlyph` |
| Kenarlık | `Environment.CommandBarMenuBorder`<br />(Yalnızca sol, üst ve sağ taraf.) |

**Menü başlığı: engelli durumu**

![Glyph ile devre dışı menü başlığı](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Glyph ile devre dışı menü başlığı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | None |
| Ön Plan (Metin) | `Environment.CommandBarTextInactive` |
| Ön Plan (Glyph) | `Environment.CommandBarTextInactive` |
| Kenarlık | None |

#### <a name="menu-items"></a>Menü öğeleri
Tek bir menü öğesi menü metninden ve isteğe bağlı bir simge, onay kutusu veya alt menü glyph'den oluşur. Onun arka plan ve metin renk değişikliği hover üzerinde. Bu renk belirteci bir arka plan/ön plan çiftidir.

![Menü öğeleri redline](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Kullanın... | Kullanmayın ... |
|---|---|
| ... menü çubuğundan veya komut çubuğundan başlatılan açılır liste için. | ... başka bir bağlamda herhangi bir açılır liste için. |
| | ... belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda. |

**Menü öğeleri: varsayılan durum**

![Varsayılan menü öğeleri](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Varsayılan menü öğeleri

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.CommandBarTextActive` |
| Ön plan (Submenu glyph) | `Environment.CommandBarMenuSubmenuGlyph` |
| Kenarlık | `Environment.CommandBarMenuBorder` |
| Simge kanal arka planı | `Environment.CommandBarMenuIconBackground` |
| Ayırıcı | `Environment.CommandBarMenuSeparator` |
| Gölge | `Environment.DropShadowBackground` |

**Menü öğeleri: işaretli ve seçili durumlar**

![Menü işaretli](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Kontrol edilen menü öğesi

![Seçili menü](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Seçili menü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Onay işareti | `Environment.CommandBarCheckBox` |
| İşaret arka planı | `Environment.CommandBarSelectedIcon` |
| Simge arka plan | `Environment.CommandBarSelected` |
| Simge kenarlığı | `Environment.CommandBarSelectedBorder` |

**Menü öğeleri: hover durumu**

![Menü gezinme](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Hover üzerinde menü öğesi

![Menü gezinme kontrol](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Gezinme üzerinde kontrol edilen menü öğesi

![Menü gezinmek seçili](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Havada seçili menü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarMenuItemMouseOver` |
| Ön Plan (Metin) | `Environment.CommandBarMenuItemMouseOverText` |
| Ön plan (Submenu glyph) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Onay işareti | `Environment.CommandBarCheckBoxMouseOver` |
| İşaret arka planı | `Environment.CommandBarHoverOverSelectedIcon` |
| Simge arka plan | `Environment.CommandBarHoverOverSelected` |
| Simge kenarlığı | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Menü öğeleri: devre dışı durum**

![Menü devre dışı](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Devre dışı bırakılmış menü öğesi

![Menü devre dışı bırakılmış](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Onay işareti olan engelli menü öğesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Ön Plan (Metin) | `Environment.CommandBarTextInactive` |
| Ön plan (Submenu glyph) | `Environment.CommandBarMenuSubmenuGlyph` |
| Onay işareti | `Environment.CommandBarCheckBoxDisabled` |
| İşaret arka planı | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Komut çubukları
Komut çubuğu Visual Studio IDE içinde birden çok yerde görünebilir, en önemlisi komut rafı ve araç veya belge pencerelerine katıştırılmış.

Genel olarak, Visual Studio ortamı tarafından sağlanan standart komut çubuğu uygulamasını her zaman kullanın. Standart mekanizmanın kullanılması, tüm görsel ayrıntıların doğru görünmesini ve etkileşimli öğelerin diğer Visual Studio komut çubuğu denetimleriyle tutarlı bir şekilde hareket edecektir. Ancak, kendi komut çubuğunuzu oluşturmanız gerekiyorsa, aşağıdaki belirteç adlarını kullanarak komutu doğru şekilde şekillendirdiğinizden emin olun.

![Komut çubuğu redline](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Komut çubuğu (redline)

![Taşma düğmesi redline](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Taşma düğmesi (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... gömülü bir komut çubuğuna ihtiyacınız olan, ancak standart Visual Studio komut çubuğu uygulamasını kullanamadığınız yerlerde. | ... komut çubuğuna benzemeyen UI öğeleri için. |
| | ... belirteç adlarının belirtildiği olanlar dışındaki komut çubuğu bileşenleri için. |

#### <a name="command-bar-groups"></a>Komut çubuğu grupları
Komut çubuğu grubu ilgili bir komut çubuğu denetim kümesinden oluşur ve herhangi bir sayıda düğme, bölme düğmesi, açılır menüler, açılan kutular veya menüler içerebilir. Bu denetimler için renkler ayrı belirteç adlarıyla düzenlenir ve bu kılavuzda başka bir yerde ayrı ayrı tartışılır. Bir ayırıcı satır, komut çubuğu grubunu ilgili alt gruplara bölmek için kullanılır.

![Komut çubuğu grubu redline](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Komut çubuğu grubu (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... gömülü bir komut çubuğuna ihtiyacınız olan, ancak standart Visual Studio komut çubuğu uygulamasını kullanamadığınız yerlerde. | ... komut çubuğuna benzemeyen UI öğeleri için. |
| | ... belirteç adlarının belirtildiği olanlar dışındaki komut çubuğu bileşenleri için. |

**Komut çubuğu grubu: varsayılan durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarGradientBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Kenarlık | `Environment.CommandBarToolBarBorder` |
| Sürükleme kolu | `Environment.CommandBarDragHandle` |
| Ayırıcı | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Komut simgeleri
![Komut simgesi redline](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Komut simgesi (redline)

![Metin redline ile komut simgesi](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Metinli komut simgesi (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... komut çubuğuna yerleştirilecek tüm düğmeler için. | ... kendi belirteç adlarına sahip denetimler için. |
| | ... belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda. |

**Komut simgesi: varsayılan durum**

![Komut simgesi varsayılan](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Varsayılan komut simgesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | N/A (komut çubuğu arka planından devralır) |
| Ön Plan (Metin) | `Environment.CommandBarTextActive` |
| Kenarlık | Yok |

**Komut simgesi: varsayılan durum, seçili**

![Varsayılan, seçili komut simgesi](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Varsayılan, seçili komut simgesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarSelected` |
| Ön Plan (Metin) | `Environment.CommandBarTextSelected` |
| Kenarlık | `Environment.CommandBarSelectedBorder` |

**Komut simgesi: gezinme veya odak durumları**

![Gezinme veya odak üzerindeki komut simgesi](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Gezinme veya odak üzerindeki komut simgesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.CommandBarTextHover` |
| Kenarlık | `Environment.CommandBarBorder` |

**Komut simgesi: gezinme veya odak durumları, seçili**

![Gezinme veya odak üzerinde seçili komut simgesi](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Gezinme veya odak üzerinde seçili komut simgesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarHoverOverSelected` |
| Ön Plan (Metin) | `Environment.CommandBarTextHoverOverSelected` |
| Kenarlık | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Komut simgesi: basılı durum**

![Basılı komut simgesi](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Basılı komut simgesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.CommandBarTextMouseDown` |
| Kenarlık | `Environment.CommandBarBorder` |

**Komut simgesi: devre dışı durum**

![Devre dışı bırakılmış komut simgesi](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Devre dışı bırakılmış komut simgesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | N/A (komut çubuğu arka planından devralır) |
| Ön Plan (Metin) | `Environment.CommandBarTextInactive` |
| Kenarlık | Yok |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a>Komut çubuğu açılan kutular

> [!IMPORTANT]
> Açılan kutular açılır düşüşlere benzer, ancak editable metin bölgesi içerir. Açılır bırakmanızda editable metin bölgesi yoksa, komut çubuğu açılır [bırakmaları](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)için renk belirteçlerini kullanın.

![Komut çubuğu açılan kutu redline](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Komut çubuğu açılan kutusu (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel açılan kutular inşa ederken. | ... her zaman komut çubuğu Kullanıcı Arabirimi maç istemediğiniz bir şey için. |
| ... açılan kutuya benzer bir komut çubuğu denetimi oluştururken. | ... stildeki bir açılan kutuya erişebildiğinizde. |

**Komut çubuğu açılan kutu giriş alanı: varsayılan durum**

![Komut çubuğu açılan kutu giriş alanı](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Komut çubuğu açılan kutu giriş alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ComboBoxBackground` |
| Ön Plan (Metin) | `Environment.ComboBoxText` |
| Kenarlık | `Environment.ComboBoxBorder` |
| Ayırıcı | Ayırıcı yok |

**Komut çubuğu açılır düğmesi: varsayılan durum**

![Açılan kutu açılır&#45;aşağı düğmesi](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | N/A (komut çubuğu arka planından devralır) |
| Ön Plan (Glyph) | `Environment.ComboBoxGlyph` |

**Komut çubuğu açılır listesi: varsayılan durum**

![Komut çubuğu açılır listesi](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Komut çubuğu açılır listesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ComboBoxPopupBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.ComboBoxItemText` |
| Kenarlık | `Environment.ComboBoxPopupBorder` |

**Komut çubuğu açılan kutu giriş alanı: hover durumu**

![Hover komut çubuğu açılan kutu giriş alanı](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Hover komut çubuğu açılan kutu giriş alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.ComboBoxMouseOverText` |
| Kenarlık | `Environment.ComboBoxMouseOverBorder` |
| Ayırıcı | `Environment.ComboBoxMouseOverSeparator` |

 **Komut çubuğu açılır düğme: gezinme durumu**

![Kumanda çubuğu açılır düğme](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Kumanda çubuğu açılır düğme

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ComboBoxButtonMouseOverBackground` |
| Ön Plan (Glyph) | `Environment.ComboBoxMouseOverGlyph` |

**Komut çubuğu açılır listesi: hover durumu**

 ![Komut çubuğu açılır listesi](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Komut çubuğu açılır listesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan (Menü öğesi) | `Environment.ComboBoxItemMouseOverBackground` |
| Ön Plan (Metin) | `Environment.ComboBoxItemMouseOverText` |
| Kenarlık (Menü öğesi) | `Environment.ComboBoxItemMouseOverBorder` |

 **Komut çubuğu açılan kutu giriş alanı: odaklanmış durum**

![Odaklanmış komut çubuğu açılan kutu giriş alanı](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Odaklanmış komut çubuğu açılan kutu giriş alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ComboBoxFocusedBackground` |
| Ön Plan (Metin) | `Environment.ComboBoxFocusedText` |
| Kenarlık | `Environment.ComboBoxFocusedBorder` |
| Ayırıcı | `Environment.ComboBoxFocusedButtonSeparator` |

**Komut çubuğu açılır düğmesi: odaklanmış durum**

![Odaklanmış komut çubuğu açılır düğmesi](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Odaklanmış komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ComboBoxFocusedButtonBackground` |
| Ön Plan (Glyph) | `Environment.ComboBoxFocusedGlyph` |

 **Komut çubuğu açılan kutu giriş alanı: basılmış durum**

![Basıldığında komut çubuğu açılan kutu giriş alanı](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Basıldığında komut çubuğu açılan kutu giriş alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ComboBoxMouseDownBackground` |
| Ön Plan (Metin) | `Environment.ComboBoxMouseDownText` |
| Kenarlık | `Environment.ComboBoxMouseDownBorder` |
| Ayırıcı | `Environment.ComboBoxMouseDownSeparator` |

**Komut çubuğu açılır düğmesi: düğmeye basılmış durum**

![Basılı komut çubuğu açılır düğmesi](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Basılı komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ComboBoxButtonMouseDownBackground` |
| Ön Plan (Glyph) | `Environment.ComboBoxMouseDownGlyph` |

**Komut çubuğu açılan kutu giriş alanı: devre dışı durum**

![Devre dışı bırakılmış komut çubuğu açılan kutu giriş alanı](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Devre dışı bırakılmış komut çubuğu açılan kutu giriş alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ComboBoxDisabledBackground` |
| Ön Plan (Metin) | `Environment.ComboBoxDisabledText` |
| Kenarlık | `Environment.ComboBoxDisabledBorder` |
| Ayırıcı | Ayırıcı yok |

**Komut çubuğu açılır düğmesi: devre dışı bırakma durumu**

![Devre dışı bırakılmış komut çubuğu açılır düğmesi](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Devre dışı bırakılmış komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | None |
| Ön Plan (Glyph) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a>Komut çubuğu açılır bırakma

> [!IMPORTANT]
> Açılan düşüşler açılan kutulara benzer, ancak kullanılabilir metin bölgeleri yok. Açılır bırakmanızda editable metin bölgesi varsa, komut çubuğu [açılan kutuları](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)için renk belirteçlerini kullanın.

![Komut çubuğu açılır (redline)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Komut çubuğu açılır (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel açılır liste denetimleri oluştururken. | ... açılır listeye benzemeyen herhangi bir şey için. |
| | ... açılan kutular veya bölünmüş düğmeler için. |

**Komut çubuğu açılır seçim alanı: varsayılan durum**

![Varsayılan komut çubuğu açılır seçim alanı](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Varsayılan komut çubuğu açılır seçim alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.DropDownBackground` |
| Ön Plan (Metin) | `DropDownText` |
| Kenarlık | `DropDownBorder` |
| Ayırıcı | Ayırıcı yok |

**Komut çubuğu açılır düğmesi: varsayılan durum**

![Varsayılan komut çubuğu açılır düğmesi](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Varsayılan komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | None |
| Ön Plan (Glyph) | `Environment.DropDownGlyph` |

**Komut çubuğu açılır listesi: varsayılan durum**

![Varsayılan komut çubuğu açılır listesi](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Varsayılan komut çubuğu açılır listesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.DropDownPopupBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.ComboBoxItemText` |
| Kenarlık | `Environment.DropDownPopupBorder` |
| Gölge | `Environment.DropShadowBackground` |

**Komut çubuğu açılır seçim alanı: gezinme durumu**

![Gezinme üzerinde komut çubuğu açılır seçim alanı](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Gezinme üzerinde komut çubuğu açılır seçim alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.DropDownMouseOverBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.DropDownMouseOverText` |
| Kenarlık | `Environment.DropDownMouseOverBorder` |
| Ayırıcı | `Environment.DropDownButtonMouseOverSeparator` |

**Komut çubuğu açılır düğme: gezinme durumu**

![Kumanda çubuğu açılır düğme](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Kumanda çubuğu açılır düğme

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.DropDownButtonMouseOverBackground` |
| Ön Plan (Glyph) | `Environment.DropDownMouseOverGlyph` |

**Komut çubuğu açılır listesi: hover durumu**

![Komut çubuğu açılır listesi](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Komut çubuğu açılır listesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan (Menü öğesi) | `Environment.ComboBoxItemMouseOverBackground` |
| Ön Plan (Metin) | `Environment.ComboBoxItemMouseOverText` |
| Kenarlık (Menü öğesi) | `Environment.ComboBoxItemMouseOverBorder` |

 **Komut çubuğu açılır seçim alanı: basılı durum**

![&#45;aşağı seçim alanına basılı bırakma](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Basılı komut çubuğu açılır seçim alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.DropDownMouseDownBackground` |
| Ön Plan (Metin) | `Environment.DropDownMouseDownText` |
| Kenarlık | `Environment.DropDownMouseDownBorder` |
| Ayırıcı | `Environment.DropDownButtonMouseDownSeparator` |

**Komut çubuğu açılır düğmesi: düğmeye basılmış durum**

![Basılı komut çubuğu açılır düğmesi](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Basılı komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.DropDownButtonMouseDownBackground` |
| Ön Plan (Glyph) | `Environment.DropDownMouseDownGlyph` |

**Komut çubuğu açılır seçim alanı: devre dışı durum**

![Devre dışı bırakılmış komut çubuğu açılır seçim alanı](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Devre dışı bırakılmış komut çubuğu açılır seçim alanı

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.DropDownDisabledBackground` |
| Ön Plan (Metin) | `Environment.DropDownDisabledText` |
| Kenarlık | `Environment.DropDownDisabledBorder` |
| Ayırıcı | Ayırıcı yok |

**Komut çubuğu açılır düğmesi: devre dışı bırakma durumu**

![Devre dışı bırakılmış komut çubuğu açılır düğmesi](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Devre dışı bırakılmış komut çubuğu açılır düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | Yok |
| Ön Plan (Glyph) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Komut çubuğu bölme düğmeleri
Bölme düğmeleri, düğmeler, menüler ve komut çubuğu metni gibi diğer komut çubuğu denetimleriyle birçok belirteç adını paylaşır. Tüm gerekli eylem ve açılır düğme belirteç adları kolaylık sağlamak için burada tekrarlanır. Split düğmesi açılır listeleri komut [çubuğu menülerinin](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)uygulamalarıdır.

![Bölme düğmesi redline](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Komut çubuğu bölme düğmesi (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel bir bölme düğmesi oluştururken. | ... düğmeleri diğer türleri için. |
| | ... belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda. |

**Komut çubuğu bölme düğmesi: varsayılan durum**

![Varsayılan komut çubuğu bölme düğmesi](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Varsayılan komut çubuğu bölme düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | None |
| Ön Plan (Metin) | `Environment.CommandBarTextActive` |
| Ön Plan (Glyph) | `Environment.CommandBarSplitButtonGlyph` |
| Kenarlık | Yok |
| Ayırıcı | Yok |

**Komut çubuğu bölme düğmesi: hover durumu**

![Kumanda çubuğu bölme düğmesi havada](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Kumanda çubuğu bölme düğmesi havada

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.CommandBarTextHover` |
| Ön Plan (Glyph) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Kenarlık | `Environment.CommandBarBorder` |
| Ayırıcı | `Environment.CommandBarSplitButtonSeparator` |

**Komut çubuğu bölme düğmesi: düğmeye basılmış durum**

![Basılı komut çubuğu bölme düğmesi](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Basılı komut çubuğu bölme düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.CommandBarTextMouseDown` |
| Ön Plan (Glyph) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Kenarlık | `Environment.CommandBarBorder` |
| Ayırıcı | Yok |

**Komut çubuğu bölme düğmesi: devre dışı bırakma durumu**

![Devre dışı bırakılmış komut çubuğu bölme düğmesi](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Devre dışı bırakılmış komut çubuğu bölme düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | Yok |
| Ön Plan (Metin) | `Environment.ComboBoxItemTextInactive` |
| Ön Plan (Glyph) | `Environment.CommandBarTextInactive` |
| Kenarlık | Yok |
| Ayırıcı | Yok |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Komut çubuğu 'Diğer seçenekler' ve 'Taşma' düğmeleri
Bir komut çubuğu grubu ilgili komut çubuğu düğmelerini ekleyerek veya kaldırarak özelleştirilebilir olduğunda "Daha fazla seçenek" düğmesi kullanılır. Yatay boşluk olmadığı için komut çubuğu kesildiğinde "Taşma" düğmesi görüntülenir ve tıklatıldığında görüntülenemeyen komut çubuğu düğmelerini içeren bir menü gösterilir. Bu iki düğmenin renkleri aynı belirteç adları kümesi tarafından denetlenir.

![Komut çubuğu 'Daha fazla seçenek' düğmesi (redline)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Komut çubuğu 'Daha fazla seçenek' düğmesi (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel 'Daha fazla seçenek' veya 'Taşma' düğmeleri için. | ... 'Daha fazla seçenek' veya 'Taşma' düğmesine benzer işlevselliği olmayan düğmeler için. |

**Komut çubuğu 'Diğer seçenekler' ve 'Taşma' düğmeleri: varsayılan durum**

![Varsayılan komut çubuğu 'Daha fazla seçenek' düğmesi](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Varsayılan komut çubuğu 'Daha fazla seçenek' düğmesi

![Varsayılan komut çubuğu 'Taşma' düğmesi](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Varsayılan komut çubuğu 'Taşma' düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarOptionsBackground` |
| Ön Plan (Glyph) | `Environment.CommandBarOptionsGlyph` |

**Komut çubuğu 'Diğer seçenekler' ve 'Taşma' düğmeleri: gezinme durumu**

![Komut çubuğu 'Daha fazla seçenek' düğmesi havada](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Komut çubuğu 'Daha fazla seçenek' düğmesi havada

![Kumanda çubuğu 'Taşma' düğmesi](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Kumanda çubuğu 'Taşma' düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Glyph) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Komut çubuğu 'Diğer seçenekler' ve 'Taşma' düğmeleri: düğmeye basıldığında durum**

![Komut çubuğuna basıldığında 'Daha fazla seçenek' düğmesi](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Komut çubuğuna basıldığında 'Daha fazla seçenek' düğmesi

![Taşması basıldığında](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />'Taşma' düğmesine basıldığında komut çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Glyph) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Belge pencereleri
Belge pencerelerini çoğaltmaya gerek yoktur, çünkü bunlar Visual Studio ortamı tarafından sağlanır. Ancak, kullanıcı ui'nizin Her zaman Visual Studio ortamının bu bölümüyle tutarlı görünmesi için belge pencerelerinde kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.

Belge penceresi renk belirteçlerini kullanırken, bunları yalnızca benzer öğeler ve her zaman çiftler halinde kullanmaya dikkat edin. Bunu yapmazsanız, uI'nizde beklenmeyen sonuçlar alabilirsiniz.

### <a name="document-window-frames"></a>Belge pencere çerçeveleri
Belge pencereleri IDE'ye sabitlenebilir veya ayrı bir pencere olarak kayar. Bir belge penceresi IDE dışında yüzer, hala iyi bir belge oturur ve arka plan, kenarlık, metin ve sekme renkleri IDE bir parçası olduğu gibi aynıdır. Ancak, belge kendi arka planı, kenarlık ve metin renkleri olan bir çerçeve içinde oturur. Araç pencereleri belgeye iyi sabitlendiğinde, sekmelerinin davranışını ve rengini belge penceresi belirteç adlarından devralır.

![Sabitlenmiş belge penceresi (redline)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Sabitlenmiş belge penceresi (redline)

![Kayan belge penceresi (redline)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Kayan belge penceresi (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... belge penceresiyle eşleştirmek istediğiniz herhangi bir yerde UI oluşturursanız. | ...  kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için. |

**Sabitlenmiş veya kayan belge penceresi: varsayılan durum**

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | Belge türüne bağlıdır |
| Ön Plan (Metin) | Belge türüne bağlıdır |
| Kenarlık | `Environment.ToolWindowBorder` |

**Odaklanmış, kayan belge pencere çerçevesi: varsayılan durum**

![Varsayılan odaklı, kayan belge pencere çerçevesi](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Varsayılan odaklı, kayan belge pencere çerçevesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowFloatingFrame` |
| Ön Plan (Metin) | `Environment.ToolWindowFloatingFrame` |
| Ön Plan (Glyph) | `Environment.RaftedWindowButtonActiveGlyph` |
| Kenarlık | `Environment.MainWindowActiveDefaultBorder` |
| Kenarlık (Glyph) | `Environment.RaftedWindowButtonActiveBorder`<br />(Saydam olarak ayarlayın) |

**Odaklanmamış, kayan belge pencere çerçevesi: varsayılan durum**

![Varsayılan odaklanmamış, kayan belge pencere çerçevesi](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Varsayılan odaklanmamış, kayan belge pencere çerçevesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowFloatingFrameInactive` |
| Ön Plan (Metin) | `Environment.ToolWindowFloatingFrameInactive` |
| Ön Plan (Glyph) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Kenarlık | `Environment.MainWindowInactiveBorder` |
| Kenarlık (Glyph) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Saydam olarak ayarlayın) |

**Odaklanmış, kayan belge pencere çerçevesi: gezinme durumu**

![Odaklanmış, kayan belge pencere çerçevesi](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Odaklanmış, kayan belge pencere çerçevesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan (Glyph) | `Environment.RaftedWindowButtonHoverActive` |
| Ön Plan (Glyph) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Kenarlık (Glyph) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Odaklanmamış, kayan belge pencere çerçevesi: gezinme durumu**

![Gezinmeüzerine odaklanmamış, kayan belge pencere çerçevesi](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Gezinmeüzerine odaklanmamış, kayan belge pencere çerçevesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan (Glyph) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Ön Plan (Glyph) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Kenarlık (Glyph) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Odaklanmış, kayan belge pencere çerçevesi: basılı durum**

![Basında odaklanmış, kayan belge pencere çerçevesi](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Basında odaklanmış, kayan belge pencere çerçevesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka Plan (Glyph) | `Environment.RaftedWindowButtonDown` |
| Ön Plan (Glyph) | `Environment.RaftedWindowButtonDownGlyph` |
| Kenarlık (Glyph) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Belge sekmeleri
Belge sekmeleri, hangi belgelerin şu anda açık olduğunu ve hangisinin geçerli seçili veya etkin belge olduğunu belirtmek için sekme kanalında yer alacaktır. Araç pencereleri, kullanıcı bunları oraya yerleştirirse belge sekmesi kanalına da sabitlenebilir. Bu durumda, belge pencereleri ile aynı sekme renklerini kullanırlar. Belge penceresi renklerini her zaman eşleştirmek istediğiniz kullanıcı aracı oluşturuyorsanız (tema güncelleştirmeleri veya yeni temalar yüklenmişse), bu renk belirteçlerine başvurun.

![Belge sekmeleri (redline)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Belge sekmeleri (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... belge sekmelerini eşleştirmek ve tema güncelleştirmelerini veya yeni tema renklerini otomatik olarak almak istediğiniz ui'yi oluşturduğunuz her yerde. | ... kabuk bir tema güncelleştirmesi olduğunda otomatik olarak değiştirmek istemediğiniz herhangi bir Kullanıcı Arabirimi için. |

#### <a name="open-document-tabs"></a>Belge sekmelerini açma
Her açık belgenin, belge sekmesi kanalında adını görüntüleyen bir sekme vardır. Belgeler arka planda seçilebilir veya açılabilir ve sekmeleri şu durumları yansıtır:

- Seçili sekme, belgede şu anda iyi görüntülenen belgeyi temsil eder. Seçili sekmede, belgenin üst kenarına kadar uzanan bir belge kenarlığı vardır.

- Arka plan sekmeleri, şu anda seçili sekme olmayan belge sekmeleridir. Tıklatıldıktan sonra, seçili sekme olurlar ve bu belirteç adlarından tüm arka plan, kenarlık ve metin renklerini elde ederler.

![Belge sekmesini aç (redline)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Belge sekmesini aç (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel belge sekmeleri oluştururken. | ... geçici (önizleme) sekmeleri için. |
| | ... kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için. |

**Seçili, odaklanmış belge sekmesi**

![Seçili, odaklanmış belge sekmesi](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Seçili, odaklanmış belge sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.FileTabSelectedGradientTop`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.FileTabSelectedText` |
| Kenarlık | `Environment.FileTabSelectedBorder`<br />(Arka planla aynı renge ayarlayın.) |
| Belge kenarlığı | `Environment.FileTabDocumentBorderBackground` |

**Seçili, odaklanmamış belge sekmesi**

![Seçili, odaklanmamış belge sekmesi](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Seçili, odaklanmamış belge sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.FileTabInactiveGradientTop`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.FileTabInactiveText` |
| Kenarlık | `Environment.FileTabInactiveBorder`<br />(Arka planla aynı renge ayarlayın.) |
| Belge kenarlığı | `Environment.FileTabInactiveDocumentBorderBackground` |

**Arka plan belge sekmesi: varsayılan durum**

![Varsayılan arka plan belge sekmesi](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Varsayılan arka plan belge sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.FileTabBackground` |
| Ön Plan (Metin) | `Environment.FileTabText` |
| Kenarlık | `Environment.FileTabBorder`<br />(Arka planla aynı renge ayarlayın.) |

**Arka plan belge sekmesi: hover durumu**

![Gezinme üzerinde arka plan belge sekmesi](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Gezinme üzerinde arka plan belge sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.FileTabHotGradientTop`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.FileTabHotText` |
| Kenarlık | `Environment.FileTabHotBorder`<br />(Arka planla aynı renge ayarlayın.) |

#### <a name="preview-tab"></a>Önizleme sekmesi
"Geçici" sekmesi olarak da adlandırılır. Kullanıcı Çözüm Gezgini araç penceresinde bir öğeyi tıklattığında önizleme sekmesi belge sekmesi kanalının sağ tarafında görünür. Belgenin önizlemesi görevi görür ve kullanıcıya belgeyi belge sekmesi kanalının sol tarafında açık tutma seçeneği de verir. Aynı anda yalnızca bir önizleme sekmesi açılabilir. Önizleme sekmeleri hem arka plana hem de açık sekmeler gibi seçili durumlara sahiptir ve etkin durumlarında odaklanmış veya odaklanmamış olabilir.

![Önizleme sekmesi (redline)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Önizleme sekmesi (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... geçici önizleme oluşturduğunuz ve bazı öğenin geçerli önizleme sekmesi rengiyle eşleşmesini istediğiniz her yerde. | ... geçici olmayan herhangi bir belge veya sekme için (önizleme). |
| | ... kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için. |

**Odaklanmış, seçili önizleme sekmesi**

![Odaklanmış, seçili önizleme sekmesi](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Odaklanmış, seçili önizleme sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.FileTabProvisionalSelectedActive` |
| Ön Plan (Metin) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Kenarlık | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Arka planla aynı renge ayarlayın.) |
| Belge kenarlığı | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Odaklanmamış, seçili önizleme sekmesi**

![Odaklanmamış, seçili önizleme sekmesi](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Odaklanmamış, seçili önizleme sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.FileTabProvisionalSelectedInactive` |
| Ön Plan (Metin) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Kenarlık | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Belge kenarlığı | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Arka plan önizleme sekmesi: varsayılan durum**

![Varsayılan arka plan önizleme sekmesi](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Varsayılan arka plan önizleme sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.FileTabProvisionalInactive` |
| Ön Plan (Metin) | `Environment.FileTabProvisionalInactiveForeground` |
| Kenarlık | `Environment.FileTabProvisionalInactiveBorder`<br />(Arka planla aynı renge ayarlayın.) |

**Arka plan önizleme sekmesi: gezinme durumu**

![Hover üzerinde arka plan önizleme sekmesi](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Hover üzerinde arka plan önizleme sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.FileTabProvisionalHover` |
| Ön Plan (Metin) | `Environment.FileTabProvisionalHoverForeground` |
| Kenarlık | `Environment.FileTabProvisionalHoverBorder`<br />(Arka planla aynı renge ayarlayın.) |

#### <a name="document-overflow-button"></a>Belge taşması düğmesi
Geçerli yapılandırmada tüm belge sekmelerine uyacak dikey boşluk olup olmadığına bakılmaksızın, açık bir veya daha fazla belge varsa belge taşması düğmesi bulunur. [Komut çubuğu menü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) renkleri tarafından denetlenir belge taşma açılır menüsü, görünür ve gizli tüm açık belgelerin bir listesini görüntüler ve tüm açık belgelerin sekme kanalında görüntülenip görüntülenmediğine bağlı olarak taşma glyph değişiklikleri.

![Belge taşması düğmesi (redline)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Belge taşması düğmesi (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... özel bir belge taşma düğmesi oluştururken. | ... taşma düğmesine benzemeyen UI için. |
| | ... komut çubuğu taşma düğmeleri için. |

**Belge taşması düğmesi: varsayılan durum**

![Varsayılan belge taşması düğmesi](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Varsayılan belge taşması düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.DocWellOverflowButtonBackground` |
| Ön Plan (Glyph) | `Environment.DocWellOverflowButtonGlyph` |
| Kenarlık | Yok |

**Belge taşması düğmesi: gezinme durumu**

![Gezinme üzerinde belge taşması düğmesi](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Gezinme üzerinde belge taşması düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Ön Plan (Glyph) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Kenarlık | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Belge taşması düğmesi: düğmeye basılmış durum**

![Basılı belge taşması düğmesi](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Basılı belge taşması düğmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Ön Plan (Glyph) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Kenarlık | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Etiketleme
Visual Studio etiketlemeyi destekler, bu da kullanıcının izleme amacıyla aranabilir anahtar kelimeleri beyan etmesine olanak tanır. Örneğin, proje yöneticileri ve geliştiriciler iş öğelerini etiketlemek için Team Foundation Server'ı (TFS) kullanabilir. Aşağıdaki tablolar, hem etiketin kendisi hem de gezinme ve seçili durumlarda görünen "yakın simge" glyph için renk adları verir.

![Visual Studio'da Etiketleme (redline)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Visual Studio'da Etiketleme (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... etiketlemeyi destekleyen UI için. | ... ui başka bir tür için. |

#### <a name="tags"></a>Etiketler

**Etiket: varsayılan durum**

![Varsayılan etiket](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Varsayılan etiket

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Tag.Background` |
| Ön Plan (Metin) | `Tag.Background` |

**Etiket: hover devlet**

![Hover etiketi](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Hover etiketi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Tag.HoverBackground` |
| Ön Plan (Metin) | `Tag.HoverBackgroundText` |

**Etiket: basılmış durum**

![Basılı etiket](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Basılı etiket

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Tag.PressedBackground` |
| Ön Plan (Metin) | `Tag.PressedBackgroundText` |

**Etiket: seçilen durum**

![Seçili etiket](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Seçili etiket

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Tag.SelectedBackground` |
| Ön Plan (Metin) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Kapat&times;( ) etiketi glyph

**Kapat&times;( ) etiketi glyph: varsayılan durum**

![Varsayılan Kapat&times;( ) etiketi glyph](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Varsayılan Kapat&times;( ) etiketi glyph

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | Yok |
| Ön Plan (Glyph) | `Tag.TagHoverGlyph` |

**Kapat&times;( ) etiketi glyph: hover durumu**

![&times;() etiketi glyph'yi hover üzerinde kapat](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />&times;() etiketi glyph'yi hover üzerinde kapat

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Tag.TagHoverGlyphHoverBackground` |
| Ön Plan (Glyph) | `Tag.TagHoverGlyphHover` |
| Kenarlık | `Tag.TagHoverGlyphHoverBorder` |

**Kapat&times;( ) etiketi glyph: basılmış durum**

![Sıkıştırılmış&times;Kapat ( ) etiketi glyph](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Sıkıştırılmış&times;Kapat ( ) etiketi glyph

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Tag.TagHoverGlyphPressedBackground` |
| Ön Plan (Glyph) | `Tag.TagHoverGlyphPressed` |
| Kenarlık | `Tag.TagHoverGlyphPressedBorder` |

**Close (&times;) glyph ile seçili etiket: varsayılan durum**

![Kapat (&times;) glyph ile varsayılan seçili etiket](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Kapat (&times;) glyph ile varsayılan seçili etiket

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | Yok |
| Ön Plan (Glyph) | `Tag.TagSelectedGlyph` |

**Close (&times;) glyph ile seçili etiket: hover durumu**

![Hover üzerinde&times;Close ( ) glyph ile seçili etiket](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Hover üzerinde&times;Close ( ) glyph ile seçili etiket

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Tag.TagSelectedGlyphHoverBackground` |
| Ön Plan (Glyph) | `Tag.TagSelectedGlyphHover` |
| Kenarlık | `Tag.TagSelectedGlyphHoverBorder` |

**Close (&times;) glyph ile seçili etiket: basılmış durum**

![Seçili, sıkıştırılmış&times;etiket ile Kapat ( ) glyph](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Seçili, sıkıştırılmış&times;etiket ile Kapat ( ) glyph

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Tag.TagSelectedGlyphPressedBackground` |
| Ön Plan(Glyph) | `Tag.TagSelectedGlyphPressed` |
| Kenarlık | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Araç pencereleri
Araç pencerelerini çoğaltmaya gerek yoktur, çünkü bunlar Visual Studio ortamı tarafından sağlanır. Ancak, kullanıcı arabirimi'nizin Visual Studio ortamının bu bölümüyle tutarlı görünmesi için araç pencerelerinde kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.

![Araç penceresi (redline)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Araç penceresi (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... araç pencerelerini eşleştirmek istediğiniz herhangi bir yerde ui oluşturursanız. | ... kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için. |

### <a name="tool-window-frame"></a>Araç pencere çerçevesi
Visual Studio'daki araç pencereleri birçok farklı görev için kullanılır ve birkaç farklı durumdan birinde bulunabilir. Bir araç penceresi açıksa, belge alanının dört tarafından herhangi biri atanabilir. Araç pencereleri, kullanıcının ekranı içinde herhangi bir yerde yeniden konumlandırılmak üzere IDE'nin dışında da yüzebilir. Yüzen pencereler her zaman IDE üstüne oturun. Son olarak, araç pencereleri belge pencereleri olarak sabitlenebilir ve belgede bir sekme olarak iyi görünebilir. Belge penceresi olarak sabitlenmiş araç pencereleri belge penceresi belirteç adlarını kullanarak kısmen renklenir.

![Araç pencere çerçevesi (redline)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Araç pencere çerçevesi (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ...  araç pencerelerini eşleştirmek istediğiniz herhangi bir yerde ui oluşturursanız. | ... kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için. |

**Sabitlenmiş araç penceresi**

![Sabitlenmiş araç penceresi](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Sabitlenmiş araç penceresi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowBackground` |
| Kenarlık | `Environment.ToolWindowBorder` |

**Kayan, odaklanmış takım penceresi**

![Kayan, odaklanmış takım penceresi](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Kayan, odaklanmış takım penceresi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowBackground` |
| Kenarlık | `Environment.MainWindowActiveDefaultBorder` |

**Kayan, odaklanmamış takım penceresi**

![Kayan, odaklanmamış takım penceresi](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Kayan, odaklanmamış takım penceresi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowBackground` |
| Kenarlık | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Araç kutusu benzeri pencereler
Araç kutusu Visual Studio'da en sık kullanılan araç pencerelerinden biridir. Aslında özel bir tema ve stil uygulanan bir ağaç kontrolü.

![Araç kutusu benzeri pencere (redline)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Araç kutusu benzeri pencere (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... her zaman kabuk araç kutusu ile tutarlı olmasını istediğiniz bir araç penceresi tasarlarken. | ... araç kutusu ui benzer olmayan bir şey için, ya da kabuk araç kutusu renkleri değişirse UI sorun olup olmayacağından emin değilseniz. |

**Araç kutusu düğümleri: varsayılan durum**

![Varsayılan araç kutusu üst düğümü](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Varsayılan araç kutusu üst düğümü

![Varsayılan araç kutusu alt düğüm](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Varsayılan araç kutusu alt düğüm

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolboxContent`<br />(Başlıklar) |
| Arka plan | `Environment.ToolWindowBackground`<br />(Tek tek öğeler veya kullanılabilir denetim yoksa pencerenin tamamı) |
| Kenarlık | None |
| Ön Plan (Glyph) | `Environment.ToolboxContent` |
| Ön Plan (Metin) | `Environment.ToolboxContent` |

**Araç kutusu alt düğümleri: gezinme durumu**

![Hover üzerinde araç kutusu alt düğüm](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Hover üzerinde araç kutusu alt düğüm

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolboxContentMouseOver`<br />(Yalnızca tek tek öğeler) |
| Kenarlık | None |
| Ön Plan (Metin) | `Environment.ToolboxContentMouseOver`<br />(Yalnızca tek tek öğeler) |

**Seçili araç kutusu düğümleri: odaklanmış durum**

![Odaklanmış, seçili araç kutusu üst düğümü](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Odaklanmış, seçili araç kutusu üst düğümü

![Odaklanmış, seçili araç kutusu alt düğümü](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Odaklanmış, seçili araç kutusu alt düğümü

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `TreeView.SelectedItemActive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |
| Kenarlık | `TreeView.FocusVisualBorder`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |
| Ön Plan (Glyph) | `TreeView.SelectedItemActive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |
| Ön Plan (Metin) | `TreeView.SelectedItemActive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |

**Seçili araç kutusu düğümleri: odaklanmamış durum**

![Seçili, odaklanmamış araç kutusu üst düğümü](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Seçili, odaklanmamış araç kutusu üst düğümü

![Seçili, odaklanmamış araç kutusu alt düğüm](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Seçili, odaklanmamış araç kutusu alt düğüm

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `TreeView.SelectedItemInactive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |
| Kenarlık | None |
| Ön Plan (Glyph) | `TreeView.SelectedItemInactive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |
| Ön Plan (Metin) | `TreeView.SelectedItemInactive`<br />[Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden |

### <a name="tool-window-title-bar"></a>Araç penceresi başlık çubuğu
Başlık çubuğu kenarlığı gerçek bir kenarlık değil, başlık çubuğunun üst kısmında kalın bir çizgi. Odaklanmamış durumu için bir belirteç adı yok.

![Araç penceresi başlık çubuğu (redline)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Araç penceresi başlık çubuğu (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... araç pencerelerini eşleştirmek istediğiniz herhangi bir yerde ui oluşturursanız. | ... kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için. |

**Odaklanmış başlık çubuğu**

![Odaklanmış başlık çubuğu](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Odaklanmış başlık çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.TitleBarActiveGradientBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.TitleBarActiveText` |
| Kenarlık | `Environment.TitleBarActiveBorder`<br />(Arka planla aynı renge ayarlayın.) |
| Sürükleme kolu | `Environment.TitleBarDragHandleActive` |

**Odaklanmamış başlık çubuğu**

![Başlık çubuğu odaklanmamış](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Odaklanmamış başlık çubuğu

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.TitleBarInactiveGradientBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.TitleBarInactiveText` |
| Kenarlık | Yok |
| Sürükleme kolu | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Araç penceresi başlık çubuğu düğmeleri
![Başlık çubuğu düğmesi (redline)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Başlık çubuğu düğmesi (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... araç penceresi başlık çubuklarından renk belirteçleri kullanan UI'de görünen düğmeler için. | ... diğer konumlarda görünen düğmeler için. |
| | ... belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda. |

**Odaklanmış başlık çubuğu düğmeleri: varsayılan durum**

![Varsayılan, odaklanmış başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Varsayılan, odaklanmış başlık çubuğu düğmeleri

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | Yok |
| Ön Plan (Glyph) | `Environment.ToolWindowButtonActiveGlyph` |
| Kenarlık | Yok |

**Odaklanmamış başlık çubuğu düğmeleri: varsayılan durum**

![Varsayılan, odaklanmamış başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Varsayılan, odaklanmamış başlık çubuğu düğmeleri

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | Yok |
| Ön Plan (Glyph) | `Environment.ToolWindowButtonInactiveGlyph` |
| Kenarlık | Yok |

**Odaklanmış başlık çubuğu düğmeleri: gezinme durumu**

![Hover üzerinde odaklanmış başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Hover üzerinde odaklanmış başlık çubuğu düğmeleri

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowButtonHoverActive` |
| Ön Plan (Glyph) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonHoverActiveBorder` |

**Odaklanmamış başlık çubuğu düğmeleri: gezinme durumu**

![Gezinme üzerinde odaklanmış başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Gezinme üzerinde odaklanmış başlık çubuğu düğmeleri

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowButtonHoverInactive` |
| Ön Plan (Glyph) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Odaklanmış başlık çubuğu düğmeleri: düğmeye basılmış durum**

![Basılı başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Basılı başlık çubuğu düğmeleri

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowButtonDown` |
| Ön Plan (Glyph) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonDownBorder` |

**Odaklanmamış başlık çubuğu düğmeleri: basıldığında durum**

![Basılı olmayan başlık çubuğu düğmeleri](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Basılı olmayan başlık çubuğu düğmeleri

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowButtonDown` |
| Ön Plan (Glyph) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Kenarlık | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Araç penceresi sekmeleri
![Araç penceresi sekmesi (redline)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Araç penceresi sekmesi (redline)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... araç pencerelerini eşleştirmek istediğiniz herhangi bir yerde ui oluşturursanız. | ... kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için. |

**Seçili, odaklanmış araç penceresi sekmesi**

![Seçili, odaklanmış araç penceresi sekmesi](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Seçili, odaklanmış araç penceresi sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowTabSelectedTab` |
| Ön Plan (Metin) | `Environment.ToolWindowTabSelectedActiveText` |
| Kenarlık | `Environment.ToolWindowTabSelectedBorder`<br />(Arka planla aynı renge ayarlayın.) |

**Seçili, odaklanılmamış araç penceresi sekmesi**

![Seçili, odaklanılmamış araç penceresi sekmesi](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Seçili, odaklanılmamış araç penceresi sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowTabSelectedTab` |
| Ön Plan (Metin) | `Environment.ToolWindowTabSelectedText` |
| Kenarlık | `Environment.ToolWindowTabSelectedBorder`<br />(Arka planla aynı renge ayarlayın.) |

**Arka plan aracı penceresi sekmesi: varsayılan durum**

![Varsayılan arka plan araç penceresi sekmesi](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Varsayılan arka plan araç penceresi sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Visual Studio 2013'te degrade durakları aynı renk değerine ayarlanmıştır.) |
| Ön Plan (Metin) | `Environment.ToolWindowTabText` |
| Kenarlık | `Environment.ToolWindowTabBorder` |

**Arka plan aracı pencere sekmesi: gezinme durumu**

![Hover üzerinde arka plan aracı pencere sekmesi](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Hover üzerinde arka plan aracı pencere sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Visual Studio 2013'te degrade durakları aynı renk değerine ayarlanmıştır.) |
| Ön Plan (Metin) | `Environment.ToolWindowTabMouseOverText` |
| Kenarlık | `Environment.ToolWindowTabMouseOverBorder`<br />(Arka planla aynı renge ayarlayın.) |

### <a name="auto-hide-tabs"></a>Otomatik gizleme sekmeleri

![Otomatik gizleme sekmeleri (kırmızı çizgi)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Otomatik gizleme sekmeleri (kırmızı çizgi)

| Kullanın... | Kullanmayın ... |
| --- | --- |
| ... otomatik olarak gizlenmiş araç pencere sekmelerini eşleştirmek istediğiniz web'de ui oluştururken. | ... kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için. |

**Otomatik gizleme sekmeleri: varsayılan durum**

![Varsayılan otomatik gizle sekmesi](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Varsayılan otomatik gizle sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.AutoHideTabBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.AutoHideTabText` |
| Kenarlık | `Environment.AutoHideTabBorder` |

**Otomatik gizleme sekmeleri: gezinme durumu**

![Gezinme üzerinde otomatik gizleme sekmesi](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Gezinme üzerinde otomatik gizleme sekmesi

| Öğe | Belirteç adı: Category.color |
| --- | --- |
| Arka plan | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Temalı UI'de kullanılmayan bu belirteç için gradyan durur.) |
| Ön Plan (Metin) | `Environment.AutoHideTabMouseOverText` |
| Kenarlık | `Environment.AutoHideTabMouseOverBorder` |
