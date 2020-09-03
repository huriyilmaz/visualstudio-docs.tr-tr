---
title: Paylaşılan Renkler
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 87520a7e17d194d7f5cc28665a6f23466bface65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154655"
---
# <a name="shared-colors-for-visual-studio"></a>Visual Studio İçin Paylaşılan Renkler

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ortak Visual Studio Kabuk öğelerini kullanan kullanıcı arabirimini tasarlarken veya arabirim öğenizin benzer özelliklerle tutarlı olmasını istiyorsanız, renkleri seçmek ve atamak için paket tanımlama dosyalarında mevcut belirteç adlarını kullanın. Bu, UI 'nizin genel Visual Studio ortamı ile tutarlı kalmasını ve Temalar eklendiğinde veya güncelleştirildiğinde otomatik olarak güncelleştirilmesini sağlar.

Bu makalede, benzer kullanıcı arabirimi oluştururken başvurbileceğiniz ortak kullanıcı arabirimi öğeleri ve kullandıkları belirteç adları açıklanır. Bu renk belirteçlerine erişme hakkında daha fazla bilgi için bkz. [Vsccolor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Belirteç adlarını doğru kullandığınızdan emin olun:

- **Belirteç adlarını, rengin kendisinde değil, işleve göre kullanın.** Ortak paylaşılan renkler, belirli arabirim öğeleriyle ilişkilendirilir ve yalnızca aynı veya benzer özellikler için kullanılmak üzere tasarlanmıştır. Örneğin, rengi beğenmeniz nedeniyle dönen ilerleme animasyonu için basılan Birleşik giriş kutusunun rengini yeniden kullanmayın. Birleşik giriş kutusu ve animasyonun işlevleri farklıdır ve Birleşik giriş kutusuyla ilişkili renk değişirse animasyon elemanı için uygun bir renk olmayabilir. Rengin tutarlı kullanımı kullanıcılarınıza yöneme ve karışıklığı önlemeye yardımcı olur.

- **Arka plan ve metin renklerini doğru birleşimde kullanın.** Metinle birlikte kullanılması amaçlanan arka plan renkleri ilişkili bir metin rengine sahip olur. Bu arka plan için belirtilenden farklı metin renkleri kullanmayın. İlişkili bir metin rengi yoksa, metin görüntülemeyi düşündüğünüz herhangi bir yüzey için bu arka plan rengini kullanmayın. Metin ve arka plan renklerinin diğer birleşimleri okunamaz bir arabirimle sonuçlanabilir.

- **Konumları için uygun olan denetim renklerini kullanın.** Bazı durumlarda, bazı Visual Studio denetimlerinde ayrı kenarlık ve arka plan renkleri yoktur. Bunun yerine, bunların arkasındaki yüzeylerden bu renkleri alırlar. Her zaman, denetimi yerleştirmekte olduğunuz konuma uygun belirteç adlarını kullandığınızdan emin olun.

> [!IMPORTANT]
> "Başlangıç sayfası" veya "Cıder" kategorilerinde bulunan belirteçleri kullanmayın.

## <a name="command-structures"></a>Komut yapıları

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Menülerden

Menüler Visual Studio içinde birkaç yerde gerçekleşebilir: Ana menü çubuğu, belge veya araç pencereleri içine eklenmiş veya IDE genelinde çeşitli konumlara sağ tıklama. Diğer Kullanıcı arabirimi öğeleriyle ilişkili menülerin uygulamaları ilgili öğesi için bölümünde ele alınmıştır. Visual Studio ortamı tarafından sunulan standart menü uygulamasını her zaman kullanmanız gerekir. Ancak, nadir bazı örneklerde standart Visual Studio menülerine erişiminiz olmayabilir. Bu durumlarda, UI 'nizin Visual Studio 'daki diğer menülerle tutarlı olduğundan emin olmak için aşağıdaki belirteç adlarını kullanın.

![Menüler Redline](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")

Kullan...
- Her ne kadar özel bir menü oluşturmanız gerekir.

- Visual Studio menülerini eşleştirmek istediğiniz yeni bir kullanıcı arabirimi bileşenine sahip olduğunuzda.

Kullanma...
yalnızca arka plan rengi. Her zaman belirtilen şekilde arka plan/ön plan birleşimini kullanın.

#### <a name="menu-title"></a>Menü başlığı

Menü başlıkları bir arka plan, kenarlık ve başlık metninin yanı sıra, genellikle menü bir komut çubuğunda bulunduğunda isteğe bağlı bir glifi içerir.

![Menü başlığı Redline](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")

Kullan...
özel bir menü başlığı oluşturduğunuz zaman.

Kullanma...
- her zaman menü başlığıyla eşleştirmek istemediğiniz her şey için.

- belirtilen dışında bir arka plan/ön plan birleşimi.

  **Varsayılanını**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Menü başlığı varsayılanı](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")

  **Menü başlığı**

  Arka Plan

  Hiçbiri

  Ön plan (metin)

  `Environment.CommandBarTextActive`

  ![Karakter varsayılanı olan menü başlığı](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")

  **Glifle menü başlığı**

  Ön plan (karakter)

  `Environment.CommandBarMenuGlyph`

  Kenarlık

  Hiçbiri

  **Hover**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Üzerine gelindiğinde menü başlığı](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")

  **Menü başlığı**

  Arka Plan

  `Environment.CommandBarMouseOverBackgroundBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `Environment.CommandBarTextHover`

  ![Vurgu üzerinde glifi olan menü başlığı](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")

  **Glifle menü başlığı**

  Ön plan (karakter)

  `Environment.CommandBarMenuMouseOverGlyph`

  Kenarlık

  `Environment.CommandBarBorder`

  **Pressed**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Menü başlığı basıldı](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")

  **Menü başlığı**

  Arka Plan

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `Environment.CommandBarTextActive`

  ![Glifi basılan menü başlığı](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")

  **Glifle menü başlığı**

  Ön plan (karakter)

  `Environment.CommandBarMenuMouseDownGlyph`

  Kenarlık

  `Environment.CommandBarMenuBorder`

  Yalnızca sol, üst ve sağ kenarlar.

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Glifi devre dışı olan menü başlığı](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")

  **Glifle menü başlığı**

  Arka Plan

  Hiçbiri

  Ön plan (metin)

  `Environment.CommandBarTextInactive`

  Ön plan (karakter)

  `Environment.CommandBarTextInactive`

  Kenarlık

  Hiçbiri

#### <a name="menu"></a>Menü

Tek bir menü öğesi menü metnini ve isteğe bağlı bir simge, onay kutusu ya da alt menü glifinden oluşur. Arka planı ve metin rengi, üzerine gidilme üzerinde değişir. Bu renk belirteci bir arka plan/ön plan çiftidir.

![Menü öğeleri Redline](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")

Kullan...
bir menü çubuğundan veya komut çubuğundan başlatılan açılan liste için.

Kullanma...
- başka bir bağlamda oluşan herhangi bir açılan liste için.

- belirtilen dışında bir arka plan/ön plan birleşimi.

  **Varsayılanını**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Menü varsayılanı](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")

  **Menü**

  Arka Plan

  `Environment.CommandBarMenuBackgroundGradientBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `Environment.CommandBarTextActive`

  Ön plan (alt menü karakteri)

  `Environment.CommandBarMenuSubmenuGlyph`

  Kenarlık

  `Environment.CommandBarMenuBorder`

  Simge kanalı arka planı

  `Environment.CommandBarMenuIconBackground`

  Ayırıcı

  `Environment.CommandBarMenuSeparator`

  Gölgeli

  `Environment.DropShadowBackground`

  ![Menü işaretlendi](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")

  **Edildikten**

  Onay işareti

  `Environment.CommandBarCheckBox`

  İşaret arkaplanını denetle

  `Environment.CommandBarSelectedIcon`

  ![Menü seçildi](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")

  **Seçili**

  Simge arka planı

  `Environment.CommandBarSelected`

  Simge kenarlığı

  `Environment.CommandBarSelectedBorder`

  **Hover**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Menü üzerine gelme](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")

  **Menü öğesi**

  Arka Plan

  `Environment.CommandBarMenuItemMouseOver`

  Ön plan (metin)

  `Environment.CommandBarMenuItemMouseOver`

  Ön plan (alt menü karakteri)

  `Environment.CommandBarMenuMouseOverSubmenuGlyph`

  ![Menü üzerine gelme işaretlendi](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")

  **Edildikten**

  Onay işareti

  `Environment.CommandBarCheckBoxMouseOver`

  İşaret arkaplanını denetle

  `Environment.CommandBarHoverOverSelectedIcon`

  ![Menü üzerine gelme seçildi](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")

  **Seçili**

  Simge arka planı

  `Environment.CommandBarHoverOverSelected`

  Simge kenarlığı

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Menü devre dışı](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")

  Menü öğesi

  Ön plan (metin)

  `Environment.CommandBarTextInactive`

  Ön plan (alt menü karakteri)

  `Environment.CommandBarMenuSubmenuGlyph`

  ![Menü devre dışı işaretlendi](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")

  İşaretli

  Onay işareti

  `Environment.CommandBarCheckBoxDisabled`

  İşaret arkaplanını denetle

  `Environment.CommandBarSelectedIconDisabled`

### <a name="command-bar"></a>Komut çubuğu

Komut çubuğu, Visual Studio IDE içinde birden fazla yerde görünebildiğinden, en önemlisi komut rafı ve araç ya da belge pencereleri ile Embedded.

Genel olarak, her zaman Visual Studio ortamı tarafından sunulan standart komut çubuğu uygulamasını kullanın. Standart mekanizmanın kullanılması, tüm görsel ayrıntıların doğru görünmesini ve Etkileşimli öğelerin diğer Visual Studio komut çubuğu denetimleriyle tutarlı bir şekilde davranmasını sağlar. Ancak, kendi komut çubuğunuzu oluşturmanız gerekiyorsa, aşağıdaki belirteç adlarını kullanarak doğru şekilde stillediğinizden emin olun.

![Komut çubuğu Redline](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")

![Taşma düğmesi Redline](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")

Kullan...
Katıştırılmış bir komut çubuğuna ihtiyacınız olan ancak standart Visual Studio komut çubuğu uygulamasını kullanılamayan yerlerde.

Kullanma...
- komut çubuğuna benzer olmayan UI öğeleri için.

- belirteç adlarının belirtildiklerinin dışındaki komut çubuğu bileşenleri için.

#### <a name="command-bar-group"></a>Komut çubuğu grubu

Bir komut çubuğu grubu, ilgili bir komut çubuğu denetimleri kümesinden oluşur ve herhangi bir sayıda düğme, bölünmüş düğme, açılan menü, Birleşik giriş kutusu veya menü içerebilir. Bu denetimlerin renkleri ayrı belirteç adlarına göre düzenlenebilir ve bu kılavuzun başka bir yerinde ele alınmıştır. Bir ayırıcı çizgi, bir komut çubuğu grubunu ilgili alt gruplara bölmek için kullanılır.

![Komut çubuğu grubu Redline](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")

Kullan...
Katıştırılmış bir komut çubuğuna ihtiyacınız olan ancak standart Visual Studio komut çubuğu uygulamasını kullanılamayan yerlerde.

Kullanma...
- komut çubuğuna benzer olmayan UI öğeleri için.

- belirteç adlarının belirtildiklerinin dışındaki komut çubuğu bileşenleri için.

  **Varsayılan** (başka durumlar yok)

  Öğe

  Belirteç adı: category. Color

  Arka Plan

  `Environment.CommandBarGradientBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Kenarlık

  `Environment.CommandBarToolBarBorder`

  Sürükleme tutamacı

  `Environment.CommandBarDragHandle`

  Ayırıcı

  `Environment.CommandBarToolBarSeparator`

  `Environment.CommandBarToolBarSeparatorHighlight`

#### <a name="command-icons"></a>Komut simgeleri

![Komut simgesi Redline](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")

![Komut simgesi Redline](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")

Kullan...
bir komut çubuğuna yerleştirilecek düğmeler için.

Kullanma...
- kendi belirteç adlarına sahip denetimler için.

- belirtilen dışında bir arka plan/ön plan birleşimi.

  **Varsayılanını**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Komut simgesi varsayılan](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")

  **Varsayılanını**

  Arka Plan

  Yok (komut çubuğu arka planıyla devralır)

  Ön plan (metin)

  `Environment.CommandBarTextActive`

  Kenarlık

  Yok

  ![Komut simgesi varsayılan seçildi](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")

  **Seçili**

  Arka Plan

  `Environment.CommandBarSelected`

  Ön plan (metin)

  `Environment.CommandBarTextSelected`

  Kenarlık

  `Environment.CommandBarSelectedBorder`

  **Üzerine gelme ve klavye odaklı**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Komut simgesi üzerine gelme](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")

  **Üzerine gelindiğinde standart**

  Arka Plan

  `Environment.CommandBarMouseOverBackgroundBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `Environment.CommandBarTextHover`

  Kenarlık

  `Environment.CommandBarBorder`

  ![Komut simgesi üzerine gelme seçildi](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")

  **Üzerine gelindiğinde seçildi**

  Arka Plan

  `Environment.CommandBarHoverOverSelected`

  Ön plan (metin)

  `Environment.CommandBarTextHoverOverSelected`

  Kenarlık

  `Environment.CommandBarHoverOverSelectedIconBorder`

  **Pressed**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Komut simgesine basıldı](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")

  **Basılan komut simgesi**

  Arka Plan

  `Environment.CommandBarMouseDownBackgroundBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `Environment.CommandBarTextMouseDown`

  Kenarlık

  `Environment.CommandBarBorder`

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Komut simgesi devre dışı](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")

  **Devre dışı komut simgesi**

  Arka Plan

  Yok (komut çubuğu arka planıyla devralır)

  Ön plan (metin)

  `Environment.CommandBarTextInactive`

  Kenarlık

  Yok

#### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a> Birleşik giriş kutusu

> [!IMPORTANT]
> Birleşik giriş kutuları, açılan kutularla benzerdir, ancak düzenlenebilir bir metin bölgesi içerir. Açılır metniniz düzenlenebilir bir metin bölgesi içermiyorsa [açılan kutuda](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown)bulunan renk belirteçlerini kullanın.

![Birleşik giriş kutusu Redline](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")

Kullan...
- Özel Birleşik giriş kutuları oluştururken.

- Birleşik giriş kutusuna benzer bir komut çubuğu denetimi oluştururken.

  Kullanma...
  - her zaman komut çubuğu kullanıcı arabirimiyle eşleştirmek istemediğiniz her şey için.

- Stil eklenmiş bir Birleşik giriş kutusuna erişiminiz olduğunda.

  **Varsayılanını**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Birleşik giriş kutusu giriş alanı](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")

  **Giriş alanı**

  Arka Plan

  `Environment.ComboBoxBackground`

  Ön plan (metin)

  `Environment.ComboBoxText`

  Kenarlık

  `Environment.ComboBoxBorder`

  Ayırıcı

  Ayırıcı yok

  ![Birleşik giriş kutusu açılan&#45;aşağı düğmesi](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")

  **Açılan düğme**

  Arka Plan

  Yok (devralır)

  Ön plan (karakter)

  `Environment.ComboBoxGlyph`

  ![Birleşik giriş kutusu&#47;&#45;aşağı açılan liste](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")

  **Açılan liste**

  Arka Plan

  `Environment.ComboBoxPopupBackgroundBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `Environment.ComboBoxItemText`

  Kenarlık

  `Environment.ComboBoxPopupBorder`

  **Hover**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Üzerine gelindiğinde açılan kutu giriş alanı](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")

  **Giriş alanı**

  Arka Plan

  `Environment.ComboBoxMouseOverBackgroundBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `Environment.ComboBoxMouseOverText`

  Kenarlık

  `Environment.ComboBoxMouseOverBorder`

  Ayırıcı

  `Environment.ComboBoxMouseOverSeparator`

  ![Açılan kutu&#47;&#45;aşağı açılan düğmeyi üzerine gelme](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")

  **Açılan düğme**

  Arka Plan

  `Environment.ComboBoxButtonMouseOverBackground`

  Ön plan (karakter)

  `Environment.ComboBoxMouseOverGlyph`

  ![Birleşik giriş kutusu&#47;&#45;aşağı açılan listeyi üzerine gelme](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")

  **Açılan liste**

  Arka plan (menü öğesi)

  `Environment.ComboBoxItemMouseOverBackground`

  Ön plan (metin)

  `Environment.ComboBoxItemMouseOverText`

  Kenarlık (menü öğesi)

  `Environment.ComboBoxItemMouseOverBorder`

  **Odaklı**

  Bileşen

  Öğe

  Belirteç adı: Color. category

  ![Birleşik giriş kutusu giriş alanı odaklı](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")

  **Giriş alanı**

  Arka Plan

  `Environment.ComboBoxFocusedBackground`

  Ön plan (metin)

  `Environment.ComboBoxFocusedText`

  Kenarlık

  `Environment.ComboBoxFocusedBorder`

  Ayırıcı

  `Environment.ComboBoxFocusedButtonSeparator`

  ![Birleşik giriş kutusu&#47;bırakma&#45;aşağı düğmesine odaklanmış](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")

  **Açılan düğme**

  Arka Plan

  `Environment.ComboBoxFocusedButtonBackground`

  Ön plan (karakter)

  `Environment.ComboBoxFocusedGlyph`

  **Pressed**

  Bileşen

  Öğe

  Belirteç adı: Color. category

  ![Birleşik giriş kutusu giriş alanı basıldı](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")

  **Giriş alanı**

  Arka Plan

  `Environment.ComboBoxMouseDownBackground`

  Ön plan (metin)

  `Environment.ComboBoxMouseDownText`

  Kenarlık

  `Environment.ComboBoxMouseDownBorder`

  Ayırıcı

  `Environment.ComboBoxMouseDownSeparator`

  ![Açılan kutu&#47;&#45;aşağı düğmesine basıldığında açılan kutusu](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")

  **Açılan düğme**

  Arka Plan

  `Environment.ComboBoxButtonMouseDownBackground`

  Ön plan (karakter)

  `Environment.ComboBoxMouseDownGlyph`

  **Devre dışı**

  ![Birleşik giriş kutusu giriş alanı devre dışı](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")

  **Giriş alanı**

  Arka Plan

  `Environment.ComboBoxDisabledBackground`

  Ön plan (metin)

  `Environment.ComboBoxDisabledText`

  Kenarlık

  `Environment.ComboBoxDisabledBorder`

  Ayırıcı

  Ayırıcı yok

  ![Birleşik giriş kutusu&#47;&#45;aşağı açılan düğme devre dışı](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")

  **Açılan düğme**

  Arka Plan

  Hiçbiri

  Ön plan (karakter)

  `Environment.ComboBoxDisabledGlyph`

#### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a> Açılır liste

> [!IMPORTANT]
> Açılan kutulamalar, Birleşik giriş kutularına benzerdir, ancak düzenlenebilir metin bölgelerine benzer. Açılır metniniz düzenlenebilir bir metin bölgesi içeriyorsa, [Birleşik giriş kutusu](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)altında bulunan renk belirteçlerini kullanın.

![&#45;aşağı Redline bırak](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")

Kullan...
özel açılan liste denetimleri oluştururken.

Kullanma...
- açılan listeye benzer olmayan her şey için.

- Birleşik giriş kutuları veya bölme düğmeleri için.

  **Varsayılanını**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Seçim alanını&#45;bırak](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")

  **Seçim alanı**

  Arka Plan

  `Environment.DropDownBackground`

  Ön plan (metin)

  `DropDownText`

  Kenarlık

  `DropDownBorder`

  Ayırıcı

  Ayırıcı yok

  ![&#45;aşağı düğmesine bırak](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")

  **Açılan düğme**

  Arka Plan

  Hiçbiri

  Ön plan (karakter)

  `Environment.DropDownGlyph`

  ![&#45;aşağı açılan listesini bırak](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")

  **Açılan liste**

  Arka Plan

  `Environment.DropDownPopupBackgroundBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `Environment.ComboBoxItemText`

  Kenarlık

  `Environment.DropDownPopupBorder`

  Gölgeli

  `Environment.DropShadowBackground`

  **Hover**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![&#45;aşağı açılan seçim alanını üzerine gelme](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")

  **Seçim alanı**

  Arka Plan

  `Environment.DropDownMouseOverBackgroundBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `Environment.DropDownMouseOverText`

  Kenarlık

  `Environment.DropDownMouseOverBorder`

  Ayırıcı

  `Environment.DropDownButtonMouseOverSeparator`

  ![&#45;aşağı açılan düğmeyi üzerine gelme](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")

  **Açılan düğme**

  Arka Plan

  `Environment.DropDownButtonMouseOverBackground`

  Ön plan (karakter)

  `Environment.DropDownMouseOverGlyph`

  ![Üzerine gelme&#45;aşağı açılan liste](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")

  **Açılan liste**

  Arka plan (menü öğesi)

  `Environment.ComboBoxItemMouseOverBackground`

  Ön plan (metin)

  `Environment.ComboBoxItemMouseOverText`

  Kenarlık (menü öğesi)

  `Environment.ComboBoxItemMouseOverBorder`

  **Pressed**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![&#45;aşağı açılan seçim alanını basılmış](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")

  **Seçim alanı**

  Arka Plan

  `Environment.DropDownMouseDownBackground`

  Ön plan (metin)

  `Environment.DropDownMouseDownText`

  Kenarlık

  `Environment.DropDownMouseDownBorder`

  Ayırıcı

  `Environment.DropDownButtonMouseDownSeparator`

  ![&#45;aşağı düğmesine basıldığında bırak](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")

  **Açılan düğme**

  Arka Plan

  `Environment.DropDownButtonMouseDownBackground`

  Ön plan (karakter)

  `Environment.DropDownMouseDownGlyph`

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![&#45;aşağı açılan seçim alanı devre dışı](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")

  Arka Plan

  `Environment.DropDownDisabledBackground`

  Ön plan (metin)

  `Environment.DropDownDisabledText`

  Kenarlık

  `Environment.DropDownDisabledBorder`

  Ayırıcı

  Ayırıcı yok

  ![&#45;aşağı düğmesi devre dışı bırak](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")

  Arka Plan

  Yok

  Ön plan (karakter)

  `Environment.DropDownDisabledGlyph`

#### <a name="split-button"></a>Bölünmüş düğme

Bölünmüş düğmeler, birçok belirteç adını düğmeler, menüler ve komut çubuğu metni gibi diğer komut çubuğu denetimleriyle paylaşır. Gerekli tüm eylem ve açılan düğme belirteci adları kolaylık sağlaması için burada yinelenir. Bölünmüş düğme açılan listeleri komut çubuğu [menülerinin](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)uygulamalarıdır.

![Bölünmüş düğme Redline](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")

Kullan...
özel bir bölünmüş düğme oluştururken.

Kullanma...
- diğer tür düğmeleri için.

- belirtilen dışında bir arka plan/ön plan birleşimi.

  **Varsayılanını**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Bölünmüş düğme](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")

  **Böl düğmesi (varsayılan)**

  Arka Plan

  Hiçbiri

  Ön plan (metin)

  `Environment.CommandBarTextActive`

  Ön plan (karakter)

  `Environment.CommandBarSplitButtonGlyph`

  Kenarlık

  Yok

  Ayırıcı

  Yok

  **Hover**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Üzerine gelindiğinde Böl düğmesi](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")

  **Böl düğmesi (üzerine gidilme)**

  Arka Plan

  `Environment.CommandBarMouseOverBackgroundBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `Environment.CommandBarTextHover`

  Ön plan (karakter)

  `Environment.CommandBarSplitButtonMouseOverGlyph`

  Kenarlık

  `Environment.CommandBarBorder`

  Ayırıcı

  `Environment.CommandBarSplitButtonSeparator`

  **Pressed**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Böl düğmesine basıldığında](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")

  **Böl düğmesi (basılmış)**

  Arka Plan

  `Environment.CommandBarMouseDownBackgroundBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `Environment.CommandBarTextMouseDown`

  Ön plan (karakter)

  `Environment.CommandBarSplitButtonMouseDownGlyph`

  Kenarlık

  `Environment.CommandBarBorder`

  Ayırıcı

  Yok

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Bölünmüş düğme devre dışı](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")

  **Bölünmüş düğme (devre dışı)**

  Arka Plan

  Yok

  Ön plan (metin)

  `Environment.ComboBoxItemTextInactive`

  Ön plan (karakter)

  `Environment.CommandBarTextInactive`

  Kenarlık

  Yok

  Ayırıcı

  Yok

#### <a name="more-options-and-overflow-buttons"></a>' Diğer seçenekler ' ve ' taşma ' düğmeleri
 "Diğer seçenekler" düğmesi, bir komut çubuğu grubu ilgili komut çubuğu düğmeleri ekleyerek veya kaldırarak özelleştirilebilir olduğunda kullanılır. "Taşma" düğmesi, bir komut çubuğu yatay boşluk eksikliği nedeniyle kesilmediğinde ve tıklama ' de görüntülenemeyecek komut çubuğu düğmelerini içeren bir menü gösteriyorsa, "taşma" düğmesi görünür. Bu iki düğmenin renkleri aynı belirteç adları kümesiyle denetlenir.

 ![Daha fazla seçenek Redline](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")

 Kullan...
Özel ' diğer seçenekler ' veya ' overflow ' düğmeleri için.

 Kullanma...
' daha fazla seçenek ' veya ' taşma ' düğmesine benzer işlevlere sahip olmayan düğmeler için.

 **Varsayılanını**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Daha fazla seçenek](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")

 **Daha fazla seçenek**

 ![Taşma düğmesi](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")

 **Taşma**

 Arka Plan

 `Environment.CommandBarOptionsBackground`

 Ön plan (karakter)

 `Environment.CommandBarOptionsGlyph`

 **Hover**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Üzerine gelindiğinde daha fazla seçenek](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")

 **Daha fazla seçenek**

 ![Üzerine gelindiğinde taşma](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")

 **Taşma**

 Arka Plan

 `Environment.CommandBarOptionsMouseOverBackgroundBegin`

 Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

 Ön plan (karakter)

 `Environment.CommandBarOptionsMouseDownGlyph`

 **Pressed**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Daha fazla seçeneğe basıldığında](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")

 **Daha fazla seçenek**

 ![Taşma](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")

 **Taşma**

 Arka Plan

 `Environment.CommandBarOptionsMouseDownBackgroundBegin`

 Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

 Ön plan (karakter)

 `Environment.CommandBarOptionsMouseDownGlyph`

## <a name="document-windows"></a>Belge pencereleri
 Visual Studio ortamı tarafından sağlandıklarından belge pencerelerini çoğaltmaya gerek yoktur. Ancak, Kullanıcı arabirimi her zaman Visual Studio ortamının bu bölümüyle tutarlı şekilde görünmesi için belge penceresinde kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.

 Belge penceresi renk belirteçleri kullanılırken, bunları yalnızca benzer öğeler için ve her zaman çiftler halinde kullanmak için dikkatli olmanız gerekir. Bunu yapmazsanız, Kullanıcı arabiriminde beklenmedik sonuçlara sahip olursunuz.

### <a name="document-window-frame"></a>Belge penceresi çerçevesi
 Belge pencereleri IDE 'ye yerleştirilmiş ya da ayrı bir pencere olarak kayan olabilir. Bir belge penceresi IDE dışında olduğunda, yine de bir belge kutusu içinde yer alır ve IDE 'nin bir parçası olduğu gibi arka plan, kenarlık, metin ve sekme renkleri vardır. Ancak, belge kendi arka planına, kenarlığına ve metin rengine sahip bir çerçevenin içinde yer alır. Araç pencereleri belge kutusuna yerleştirildiğinde, belge penceresi belirteç adlarından sekmelerin davranışını ve rengini alırlar.

 ![Yerleşik belge penceresi Redline](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")

 **Sabitlenmiş belge penceresi**

 ![Kayan belge penceresi Redline](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")

 **Kayan belge penceresi**

 Kullan...
Belge penceresiyle eşleştirmek istediğiniz her yerde Kullanıcı arabirimi oluşturursunuz.

 Kullanma...
herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz.

 **Varsayılanını**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 Belge: sabitlenmiş veya kayan

 Arka Plan

 Belge türüne bağlıdır

 Ön plan (metin)

 Belge türüne bağlıdır

 Kenarlık

 `Environment.ToolWindowBorder`

 ![Çerçeve odaklı](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")

 **Çerçeve: kayan, odaklanmış**

 Arka Plan

 `Environment.ToolWindowFloatingFrame`

 Ön plan (metin)

 `Environment.ToolWindowFloatingFrame`

 Ön plan (karakter)

 `Environment.RaftedWindowButtonActiveGlyph`

 Kenarlık

 `Environment.MainWindowActiveDefaultBorder`

 Kenarlık (karakter)

 `Environment.RaftedWindowButtonActiveBorder`

 Saydam olarak ayarla

 ![Çerçeve odaklı değil](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")

 **Çerçeve: kayan, odaklanmış değil**

 Arka Plan

 `Environment.ToolWindowFloatingFrameInactive`

 Ön plan (metin)

 `Environment.ToolWindowFloatingFrameInactive`

 Ön plan (karakter)

 `Environment.RaftedWindowButtonInactiveGlyph`

 Kenarlık

 `Environment.MainWindowInactiveBorder`

 Kenarlık (karakter)

 `Environment.RaftedWindowButtonInactiveBorder`

 Saydam olarak ayarla

 **Hover**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Üzerine gelme üzerine odaklanan çerçeve](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")

 **Çerçeve: kayan, odaklanmış**

 Arka plan (karakter)

 `Environment.RaftedWindowButtonHoverActive`

 Ön plan (karakter)

 `Environment.RaftedWindowButtonHoverActiveGlyph`

 Kenarlık (karakter)

 `Environment.RaftedWindowButtonHoverActiveBorder`

 ![Üzerine gidilme durumunda çerçeve](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")

 **Çerçeve: kayan, odaklanmış değil**

 Arka plan (karakter)

 `EnvironmentRaftedWindowButtonHoverInactive`

 Ön plan (karakter)

 `Environment.RaftedWindowButtonHoverInactiveGlyph`

 Kenarlık (karakter)

 `Environment.RaftedWindowButtonHoverInactiveBorder`

 **Pressed**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Çerçeveye odaklanmış basıldığında](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")

 **Çerçeve: kayan, odaklanmış**

 Arka plan (karakter)

 `Environment.RaftedWindowButtonDown`

 Ön plan (karakter)

 `Environment.RaftedWindowButtonDownGlyph`

 Kenarlık (karakter)

 `Environment.RaftedWindowButtonDownBorder`

### <a name="document-tabs"></a>Belge sekmeleri
 Belge sekmeleri, o anda hangi belgelerin açık olduğunu, hangi belgenin seçili ya da etkin belgeyi nerede açık olduğunu göstermek için sekme kanalında oturlar. Araç pencereleri, Kullanıcı oraya yerleştirse de belge sekmesi kanalına yerleştirilebilir. Bu durumda, belge pencereleri ile aynı sekme renklerini kullanırlar. Belge pencere renkleriyle (Tema güncelleştirmeleri dahil olmak üzere veya yeni temalar yüklüyse) her zaman eşleştirmek istediğiniz kullanıcı arabirimini oluşturuyorsanız, bu renk belirteçlerine başvurun.

 ![Belge sekmesi Redline](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")

 Kullan...
Belge sekmelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimi oluşturun ve otomatik olarak tema güncelleştirmelerini veya yeni tema renklerini seçin.

 Kullanma...
kabuğun bir tema güncelleştirmesi olduğunda otomatik olarak değiştirilmesini istemediğiniz herhangi bir kullanıcı arabirimi için.

#### <a name="open-document-tabs"></a>Belge sekmelerini aç
 Her açık belge, belge sekmesi kanalında adını görüntüleyen bir sekmeye sahiptir. Belgeler, arka planda seçilebilir veya açılabilir ve sekmeleri şu durumları yansıtır:

- Seçilen sekme, şu anda belge kutusu 'nda görüntülenen belgeyi temsil eder. Seçili bir sekmede, belge alanının üst kenarına genişleyen bir belge kenarlığı bulunur.

- Arka plan sekmeleri, şu anda seçili olan sekme olmayan herhangi bir belge sekmeleridir. Tıklandıktan sonra, seçili sekme olur ve bu belirteç adlarından tüm arka plan, kenarlık ve metin renklerini elde ederler.

  ![Belge sekmesini aç Redline](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")

  Kullan...
  özel belge sekmeleri oluştururken.

  Kullanma...
  - geçici (Önizleme) sekmeleri için.

- herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz.

#### <a name="selected-tab"></a>Seçili sekme
 **Odaklı**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Seçilen sekme odaklanmış](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")

 **Seçili belge sekmesi, odaklanmış**

 Arka Plan

 `Environment.FileTabSelectedGradientTop`

 Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

 Ön plan (metin)

 `Environment.FileTabSelectedText`

 Kenarlık

 `Environment.FileTabSelectedBorder`

 Arka plan ile aynı renge ayarlanır.

 Belge kenarlığı

 `Environment.FileTabDocumentBorderBackground`

 **Odaklanmadan gözetle**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Seçili sekme odaklanmış değil](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")

 **Seçili belge sekmesi, odaklanmış değil**

 Arka Plan

 `Environment.FileTabInactiveGradientTop`

 Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

 Ön plan (metin)

 `Environment.FileTabInactiveText`

 Kenarlık

 `Environment.FileTabInactiveBorder`

 Arka plan ile aynı renge ayarlanır.

 Belge kenarlığı

 `Environment.FileTabInactiveDocumentBorderBackground`

#### <a name="background-tab"></a>Arka plan sekmesi
 **Varsayılanını**

 ![Arka plan sekmesi](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")

 **Arka plan sekmesi varsayılan**

 Arka Plan

 `Environment.FileTabBackground`

 Ön plan (metin)

 `Environment.FileTabText`

 Kenarlık

 `Environment.FileTabBorder`

 Arka plan ile aynı renge ayarlanır.

 **Hover**

 ![Üzerine gelindiğinde arka plan sekmesi](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")

 **Üzerine gelindiğinde arka plan sekmesi**

 Arka Plan

 `Environment.FileTabHotGradientTop`

 Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

 Ön plan (metin)

 `Environment.FileTabHotText`

 Kenarlık

 `Environment.FileTabHotBorder`

 Arka plan ile aynı renge ayarlanır.

#### <a name="preview-tab"></a>Önizleme sekmesi

Kullanıcı Çözüm Gezgini araç penceresinde bir öğeye tıkladığında, belge sekmesi kanalının sağ tarafında Önizleme sekmesi görünür. Belgenin bir önizlemesi görevi görür ve kullanıcıya belgeyi belge sekmesi kanalının sol tarafında açık tutma seçeneğini de sağlar. Tek seferde yalnızca bir Önizleme sekmesi açık olabilir. Önizleme sekmeleri, açık sekmeler gibi hem arka plan hem de seçili durumlara sahiptir ve etkin durumlarına odaklanmış veya odaklaneklenebilir.

![Önizleme sekmesi Redline](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")

Kullan...
geçici önizleme oluşturduğunuz her yerde, bazı öğelerinin geçerli Önizleme sekmesi rengiyle eşleşmesini istiyorsunuz.

Kullanma...
- her türlü belge veya sekme için geçici olmayan (Önizleme).

- herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz.

  **Seçili Önizleme sekmesi: odaklanmış**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Önizleme sekmesi odaklanmış](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")

  **Odaklanmış Önizleme sekmesi**

  Arka Plan

  `Environment.FileTabProvisionalSelectedActive`

  Ön plan (metin)

  `Environment.FileTabProvisionalSelectedActiveForeground`

  Kenarlık

  `Environment.FileTabProvisionalSelectedActiveBorder`

  Arka plan ile aynı renge ayarlanır.

  Belge kenarlığı

  `Environment.FileTabProvisionalSelectedActiveBorder`

  **Seçili Önizleme sekmesi: odaklanmış değil**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Önizleme sekmesi odaklanmış değil](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")

  **Odaklanmış Önizleme sekmesi**

  Arka Plan

  `Environment.FileTabProvisionalSelectedInactive`

  Ön plan (metin)

  `Environment.FileTabProvisionalSelectedInactiveForeground`

  Kenarlık

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  Belge kenarlığı

  `Environment.FileTabProvisionalSelectedInactiveBorder`

  **Arka plan Önizleme sekmesi: varsayılan**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Önizleme arka planı sekmesi](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")

  **Önizleme sekmesi arka plan sekmesi**

  Arka Plan

  `Environment.FileTabProvisionalInactive`

  Ön plan (metin)

  `Environment.FileTabProvisionalInactiveForeground`

  Kenarlık

  `Environment.FileTabProvisionalInactiveBorder`

  Arka plan ile aynı renge ayarlanır.

  **Arka plan Önizleme sekmesi: üzerine gelme**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Üzerine gelindiğinde önizleme arka planı sekmesi](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")

  **Üzerine gelindiğinde Önizleme sekmesi arka plan sekmesi**

  Arka Plan

  `Environment.FileTabProvisionalHover`

  Ön plan (metin)

  `Environment.FileTabProvisionalHoverForeground`

  Kenarlık

  `Environment.FileTabProvisionalHoverBorder`

  Arka plan ile aynı renge ayarlanır.

#### <a name="document-overflow-button"></a>Belge taşması düğmesi

Geçerli yapılandırmada tüm belge sekmelerine sığacak şekilde bir veya daha fazla belge açıksa, belge taşma düğmesi vardır. **Commandbarmenu** renkleriyle (bkz. [menülere](../../misc/shared-colors.md#BKMK_CommandMenus)) denetlenen belge taşması açılır menüsü, tüm açık belgelerin bir listesini görüntüler, hem görünür ve gizli, hem de tüm açık belgelerin sekme kanalında görüntülenip görüntülenmediğine bağlı olarak taşma karakteri değişir.

![Taşma Redline](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")

Kullan...
özel bir belge taşması düğmesi oluştururken.

Kullanma...
- taşma düğmesine benzer olmayan kullanıcı arabirimi için.

- komut çubuğu taşma düğmeleri için.

  **Varsayılanını**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Taşma](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")

  **Belge taşması düğmesi**

  Arka Plan

  `Environment.DocWellOverflowButtonBackground`

  Ön plan (karakter)

  `Environment.DocWellOverflowButtonGlyph`

  Kenarlık

  Yok

  **Hover**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Üzerine gelindiğinde taşma](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")

  **Üzerine gelindiğinde belge taşması düğmesi**

  Arka Plan

  `Environment.DocWellOverflowButtonMouseOverBackground`

  Ön plan (karakter)

  `Environment.DocWellOverflowButtonMouseOverGlyph`

  Kenarlık

  `Environment.DocWellOverflowButtonMouseOverBorder`

  **Pressed**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Taşma](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")

  **Basılan belge taşma düğmesi**

  Arka Plan

  `Environment.DocWellOverflowButtonMouseDownBackground`

  Ön plan (karakter)

  `Environment.DocWellOverflowButtonMouseDownGlyph`

  Kenarlık

  `Environment.DocWellOverflowButtonMouseDownBorder`

## <a name="tool-windows"></a>Araç pencereleri
 Visual Studio ortamı tarafından sağlandıklarından araç pencerelerini çoğaltmaya gerek yoktur. Ancak, Kullanıcı arabirimi her zaman Visual Studio ortamının bu bölümüyle tutarlı şekilde göründüğünden, araç pencereleri için kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.

 ![Araç penceresi Redline](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")

 Kullan...
araç pencerelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimini oluşturduğunuz her yerde.

 Kullanma...
herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz.

### <a name="tool-window-frame"></a>Araç penceresi çerçevesi
 Visual Studio 'daki araç pencereleri birçok farklı görev için kullanılır ve birçok farklı durumdan birinde bulunabilir. Bir araç penceresi açıksa, belge alanının dört taraflarından herhangi birine atanabilir. Araç pencereleri Ayrıca IDE dışında kaydırılabilir, bu da kullanıcının ekranındaki herhangi bir yerde yeniden konumlandırılabilirler. Kayan pencereler her zaman IDE 'nin üstüne yaslanıp. Son olarak, araç pencereleri belge pencereleri olarak sabitlenebilir ve belge kutusunda bir sekme olarak görünebilir. Belge pencereleri olarak yerleştirilmiş olan araç pencereleri, belge penceresi belirteç adları kullanılarak kısmen renklendirilir.

 ![Araç penceresi çerçevesi Redline](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")

 Kullan...
araç pencerelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimini oluşturduğunuz her yerde.

 Kullanma...
herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz.

 **Abileceği**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Araç penceresi yerleştirildi](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")

 Arka Plan

 `Environment.ToolWindowBackground`

 Kenarlık

 `Environment.ToolWindowBorder`

 **Kayan: odaklanmış**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Araç penceresi odaklı](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")

 Arka Plan

 `Environment.ToolWindowBackground`

 Kenarlık

 `Environment.MainWindowActiveDefaultBorder`

 **Kayan: odaklanmış değil**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Araç penceresi odaklanmış değil](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")

 Arka Plan

 `Environment.ToolWindowBackground`

 Kenarlık

 `Environment.MainWindowInactiveBorder`

### <a name="tool-window-title-bar"></a>Araç penceresi başlık çubuğu
 Başlık çubuğu kenarlığı gerçek bir kenarlık değildir, ancak başlık çubuğunun üst kısmında kalın bir çizgi olur. Onun odaklanmış olmayan durumu için bir belirteç adı yok.

 ![Araç penceresi başlık çubuğu Redline](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")

 Kullan...
araç pencerelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimini oluşturduğunuz her yerde.

 Kullanma...
herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz.

 **Odaklı**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Başlık çubuğu odaklı](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")

 **Odaklanmış başlık çubuğu**

 Arka Plan

 `Environment.TitleBarActiveGradientBegin`

 Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

 Ön plan (metin)

 `Environment.TitleBarActiveText`

 Kenarlık

 `Environment.TitleBarActiveBorder`

 Arka plan ile aynı renge ayarlanır.

 Sürükleme tutamacı

 `Environment.TitleBarDragHandleActive`

 **Odaklanmadan gözetle**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Başlık çubuğu odaklanmış değil](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")

 **Odaklanmış olmayan başlık çubuğu**

 Arka Plan

 `Environment.TitleBarInactiveGradientBegin`

 Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

 Ön plan (metin)

 `Environment.TitleBarInactiveText`

 Kenarlık

 Yok

 Sürükleme tutamacı

 `Environment.TitleBarDragHandle`

#### <a name="title-bar-buttons"></a>Başlık çubuğu düğmeleri

![Başlık çubuğu düğme Redline](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")

Kullan...
araç penceresi başlık çubuklarından renk belirteçleri kullanan kullanıcı arabiriminde görünen düğmeler için.

Kullanma...
- diğer konumlarda görünen düğmeler için.

- belirtilen dışında bir arka plan/ön plan birleşimi.

  **Varsayılanını**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Başlık çubuğu düğmesi odaklı](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")

  **Odaklı**

  Arka Plan

  Yok

  Ön plan (karakter)

  `Environment.ToolWindowButtonActiveGlyph`

  Kenarlık

  Yok

  ![Başlık çubuğu düğmesi odaklanmış değil](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")

  **Odaklanmadan gözetle**

  Arka Plan

  Yok

  Ön plan (karakter)

  `Environment.ToolWindowButtonInactiveGlyph`

  Kenarlık

  Yok

  **Hover**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Üzerine gelme üzerine odaklanan başlık çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")

  **Odaklı**

  Arka Plan

  `Environment.ToolWindowButtonHoverActive`

  Ön plan (karakter)

  `Environment.ToolWindowButtonHoverActiveGlyph`

  Kenarlık

  `Environment.ToolWindowButtonHoverActiveBorder`

  ![Üzerine gelme üzerine odaklanmadan başlık çubuğu düğmesi](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")

  **Odaklanmadan gözetle**

  Arka Plan

  `Environment.ToolWindowButtonHoverInactive`

  Ön plan (karakter)

  `Environment.ToolWindowButtonHoverInactiveGlyph`

  Kenarlık

  `Environment.ToolWindowButtonHoverInactiveBorder`

  **Pressed**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Başlık çubuğu düğmesine odaklanmış ve basılan](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")

  **Odaklı**

  Arka Plan

  `Environment.ToolWindowButtonDown`

  Ön plan (karakter)

  `Environment.ToolWindowButtonDownActiveGlyph`

  Kenarlık

  `Environment.ToolWindowButtonDownBorder`

  ![Başlık çubuğu düğmesi odaklanmış değil ve basıldı](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")

  **Odaklanmadan gözetle**

  Arka Plan

  `Environment.ToolWindowButtonDown`

  Ön plan (karakter)

  `Environment.ToolWindowButtonDownInactiveGlyph`

  Kenarlık

  `Environment.ToolWindowButtonDownBorder`

### <a name="tool-window-tabs"></a>Araç penceresi sekmeleri
 ![Araç penceresi sekmesi Redline](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")

 Kullan...
araç pencerelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimini oluşturduğunuz her yerde.

 Kullanma...
herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz.

 **Seçili sekme**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Araç penceresi Tab odaklı](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")

 **Seçilen, odaklanmış araç penceresi sekmesi**

 Arka Plan

 `Environment.ToolWindowTabSelectedTab`

 Ön plan (metin)

 `Environment.ToolWindowTabSelectedActiveText`

 Kenarlık

 `Environment.ToolWindowTabSelectedBorder`

 Arka plan ile aynı renge ayarlanır.

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Araç penceresi sekmesi odaklanmış değil](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")

 **Seçili, odaklanmış olmayan araç penceresi sekmesi**

 Arka Plan

 `Environment.ToolWindowTabSelectedTab`

 Ön plan (metin)

 `Environment.ToolWindowTabSelectedText`

 Kenarlık

 `Environment.ToolWindowTabSelectedBorder`

 Arka plan ile aynı renge ayarlanır.

 **Arka plan sekmesi**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Araç penceresi arka plan sekmesi](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")

 **Arka plan araç penceresi sekmesi**

 Arka Plan

 `Environment.ToolWindowTabGradientBegin`

 Gradyan duraklarının Visual Studio 2013 aynı renk değerine ayarlanır.

 `Environment.ToolWindowTabGradientEnd`

 Gradyan duraklarının Visual Studio 2013 aynı renk değerine ayarlanır.

 Ön plan (metin)

 `Environment.ToolWindowTabText`

 Kenarlık

 `Environment.ToolWindowTabBorder`

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Üzerine gelindiğinde araç penceresi arka plan sekmesi](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")

 **Üzerine gelme sırasında arka plan araç penceresi sekmesi**

 Arka Plan

 `Environment.ToolWindowTabMouseOverBackgroundBegin`

 Gradyan duraklarının Visual Studio 2013 aynı renk değerine ayarlanır.

 `Environment.ToolWindowTabMouseOverBackgroundEnd`

 Gradyan duraklarının Visual Studio 2013 aynı renk değerine ayarlanır.

 Ön plan (metin)

 `Environment.ToolWindowTabMouseOverText`

 Kenarlık

 `Environment.ToolWindowTabMouseOverBorder`

 Arka plan ile aynı renge ayarlanır.

### <a name="auto-hide-tabs"></a>Sekmeleri otomatik gizle
 ![Otomatik&#45;Redline gizle](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")

 Kullan...
Otomatik gizli araç penceresi sekmelerini eşleştirmek istediğiniz her yerde Kullanıcı arabirimini oluşturduğunuz her yerde.

 Kullanma...
herhangi bir kullanıcı arabirimi için, kabuğun bir tema güncelleştirmesi varsa otomatik olarak değiştirilmesini istemezsiniz.

 **Varsayılanını**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Otomatik&#45;sekmeyi gizle](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")

 **Varsayılan otomatik gizleme sekmesi**

 Arka Plan

 `Environment.AutoHideTabBackgroundBegin`

 Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

 Ön plan (metin)

 `Environment.AutoHideTabText`

 Kenarlık

 `Environment.AutoHideTabBorder`

 **Hover**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Otomatik&#45;, üzerine gelindiğinde sekmeyi gizle](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")

 **Üzerine gelindiğinde sekmeyi otomatik gizle**

 Arka Plan

 `Environment.AutoHideTabMouseOverBackgroundBegin`

 Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

 Ön plan (metin)

 `Environment.AutoHideTabMouseOverText`

 Kenarlık

 `Environment.AutoHideTabMouseOverBorder`

## <a name="common-shared-controls"></a>Ortak paylaşılan denetimler
 Özelliğinizdeki standart bir Visual Studio komut çubuğunu kullandığınızda, stillendirilmiş kabuk denetimlerine erişiminiz olur ve bu ortak denetimleri yeniden şablonunuz gerekir. Ancak, özel bir komut çubuğu oluşturmanız gerekiyorsa, özel denetimler de oluşturmanız gerekebilir. Bu durumda, UI 'nizin Visual Studio 'nun geri kalanı ile tutarlı olması için aşağıdaki denetimlerin her biri için doğru belirteç adlarını kullandığınızdan emin olun.

### <a name="search-box"></a>Arama kutusu
 Mümkün olan her durumda, Visual Studio ortamı tarafından sunulan genel arama denetimini kullanın. Arama kutusu renkleri, giriş alanı, eylem düğmesi, açılan düğme ve açılan menünün belirteç adlarını içeren **Shellcolors. pkgdef** dosyasındaki "SearchControl" kategorisinde bulunur.

 Bir arama kutusu, bazıları birbirini dışlamalı birkaç durumdan biri olabilir:

- "Odaklanmış" veya "odaklanmış olmayan" imleci, imlecin metin kutusunda olup olmadığı anlamına gelir.

- "Etkin" veya "etkin değil", kullanıcının metin kutusunda bir arama sorgusu girmediğini belirtir.

- "Üzerine gelme", kullanıcının fare ile arama kutusu üzerinde molediği anlamına gelir (Bu durum diğer tüm durumları geçersiz kılar).

- "Devre dışı", geçerli bağlam için arama işlevinin kapalı olduğu anlamına gelir.

  ![Arama kutusu Redline](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")

  Kullan...
  özel bir arama kutusu tasarlarken.

  Kullanma...
  - Arama kutusu olmayan her şey için.

- Arama kutusu kullanıcı arabiriminden her zaman eşleşmek istemediğiniz her şey için.

  **Odaklı**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Arama girişi alanı odaklı](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")

  **Giriş alanı**

  Arka Plan

  `SearchControl.FocusedBackground`

  Ön plan (metin)

  `SearchControl.FocusedBackground`

  Kenarlık

  `SearchControl.FocusedBorder`

  Ayırıcı

  `SearchControl.FocusedDropDownSeparator`

  ![Arama eylemi düğmesi odaklı](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")

  **Eylem düğmesi**

  Arka Plan

  Hiçbiri

  Ön plan (karakter ara)

  `SearchControl.SearchGlyph`

  Ön plan (glifi Durdur)

  `SearchControl.StopGlyph`

  Ön plan (glifi temizle)

  `SearchControl.ClearGlyph`

  Kenarlık

  Yok

  ![Arama bırakma&#45;aşağı düğme odaklı](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")

  **Açılan düğme**

  Arka Plan

  `SearchControl.FocusedDropDownButton`

  Ön plan (karakter)

  `SearchControl.FocusedDropDownButtonGlyph`

  Kenarlık

  `SearchControl.FocusedDropDownButtonBorder`

  **Odaklanmadan gözetle**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Arama girişi alanı odaklanmış değil](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")

  **Etkin giriş alanı**

  Arka Plan

  `SearchControl.SearchActiveBackground`

  Ön plan (metin)

  `SearchControl.SearchActiveBackground`

  Kenarlık

  `SearchControl.UnfocusedBorder`

  Ayırıcı

  `SearchControl.DropDownSeparator`

  ![Arama girişi alanı odaklanmış değil ve etkin değil](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")

  **Etkin olmayan giriş alanı**

  Arka Plan

  `SearchControl.Unfocused`

  Ön plan (metin)

  `SearchControl.Unfocused`

  Kenarlık

  `SearchControl.UnfocusedBorder`

  Ayırıcı

  `SearchControl.DropDownSeparator`

  ![Arama eylemi düğmesi odaklanmış değil](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")

  **Eylem düğmesi**

  Arka Plan

  Yok

  Ön plan (karakter ara)

  `SearchControl.SearchGlyph`

  Ön plan (glifi Durdur)

  `SearchControl.StopGlyph`

  Ön plan (glifi temizle)

  `SearchControl.ClearGlyph`

  Kenarlık

  Yok

  ![Arama bırakma&#45;aşağı düğmesi odaklanmış değil](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")

  **Açılan düğme**

  Arka Plan

  `SearchControl.UnfocusedDropDownButton`

  Ön plan (karakter)

  `SearchControl.UnfocusedDropDownButtonGlyph`

  Kenarlık

  `SearchControl.UnfocusedDropDownButtonBorder`

  **Pressed**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Arama eylemi düğmesi basılı](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")

  **Eylem düğmesi**

  Arka Plan

  `SearchControl.ActionButtonMouseDown`

  Ön plan (karakter)

  `SearchControl.ActionButtonMouseDownGlyph`

  Kenarlık

  `SearchControl.ActionButtonMouseDownBorder`

  ![Açılan&#45;aşağı düğmesine basıldığında ara](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")

  **Açılan düğme**

  Arka Plan

  `SearchControl.MouseDownDropDownButton`

  Ön plan (karakter)

  `SearchControl.MouseDownDropDownButtonGlyph`

  Kenarlık

  `SearchControl.MouseDownDropDownButtonBorder`

  **Vurgulanmış (yalnızca metin)**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Arama girişi alanı vurgusu](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")

  **Vurgulanmış metin içeren giriş alanı**

  Arka Plan

  `SearchControl.Selection`

  Ön plan (metin)

  `SearchControl.FocusedBackground`

  Kenarlık

  Hiçbiri

  Ayırıcı

  `SearchControl.FocusedDropDownSeparator`

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Arama girişi alanı devre dışı](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")

  **Giriş alanı**

  Arka Plan

  `SearchControl.Disabled`

  Ön plan (metin)

  `SearchControl.Disabled`

  Kenarlık

  `SearchControl.DisabledBorder`

  Ayırıcı

  `SearchControl.DropDownSeparator`

  ![Arama eylemi düğmesi devre dışı](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")

  **Eylem düğmesi**

  Arka Plan

  Hiçbiri

  Ön plan (karakter)

  `SearchControl.ActionButtonDisabledGlyph`

  Kenarlık

  Hiçbiri

  ![Arama bırakma&#45;aşağı düğmesi devre dışı](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")

  **Açılan düğme**

  Arka Plan

  Hiçbiri

  Ön plan (karakter)

  `SearchControl.DisabledDownButtonGlyph`

  Kenarlık

  Hiçbiri

#### <a name="search-drop-down-lists"></a>Arama açılan listeleri

Arama kutusu açılan menüsünün, Visual Studio 'daki diğer açılan menülerden biraz daha karmaşık olma olasılığı vardır. "Önerilen aramalar" ve "arama seçenekleri" bölümleri tek başına veya menüde birlikte görünebilir ve her biri ayrı olarak renklendirilir. Bir satır, birlikte görüntülendiklerinde bu iki bölümü de ayırır ve bir kenarlık, tüm açılan menüyü çevreler.

![Arama açılan&#45;aşağı doğru aşağı](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")

Kullan...
- Özel arama açılan listesi oluştururken.

- doğru liste bileşenleri için doğru belirteç adları.

  Kullanma...
  - diğer bağlamlarda görünen aşağı açılan listeler için.

- belirtilen dışında bir arka plan/ön plan birleşimi.

  **Varsayılan (başka durumlar yok)**

  Öğe

  Belirteç adı: category. Color

  Kenarlık

  `SearchControl.PopupBorder`

  Ayırıcı

  `SearchControl.PopupSectionHeaderSeparator`

  Gölgeli

  `Environment.DropShadowBackground`

  **Varsayılanını**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Önerilen arama](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")

  **Önerilen aramalar**

  Arka Plan

  `SearchControl.PopupItemsListBackgroundGradientBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `SearchControl.PopupItemText`

  ![Arama onay kutusu](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")

  **Arama seçenekleri (onay kutusu)**

  ![Arama seçenekleri](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")

  **Arama seçenekleri (bağlantı)**

  Arka Plan

  `SearchControl.PopupSectionBackgroundGradientBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (onay kutusu metni)

  `SearchControl.PopupCheckboxText`

  Ön plan (bağlantı metni)

  `SearchControl.PopupButtonText`

  Üst bilgi arka planı

  `SearchControl.PopupSectionHeaderGradientBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (üst bilgi metni)

  `SearchControl.PopupSectionHeaderText`

  **Hover**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Arama üzerine gelme önerisi](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")

  **Önerilen aramalar**

  Arka Plan

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (metin)

  `SearchControl.PopupMouseOverItemText`

  Kenarlık

  `SearchControl.PopupControlMouseOverBorder`

  ![Üzerine gelindiğinde ara onay kutusu](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")

  **Önerilen aramalar (onay kutusu)**

  ![Üzerine gelindiğinde arama seçenekleri](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")

  **Arama seçenekleri**

  Arka Plan

  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (onay kutusu metni)

  `SearchControl.PopupCheckboxMouseDownText`

  Ön plan (bağlantı metni)

  `SearchControl.PopupButtonMouseDownText`

  Kenarlık

  `SearchControl.PopupControlMouseOverBorder`

  **Pressed**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Önerilen arama](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")

  **Önerilen aramalar (onay kutusu)**

  ![Arama seçenekleri basıldı](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")

  **Arama seçenekleri**

  Onay kutusu arka planı

  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (onay kutusu metni)

  `SearchControl.PopupCheckboxMouseDownText`

  Bağlantı arka planı

  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`

  Modern temalı Kullanıcı arabiriminde kullanılmamış olsa da, bu arka plan için gradyan duraklar ve değerler vardır.

  Ön plan (bağlantı metni)

  `SearchControl.PopupButtonMouseDownText`

### <a name="hyperlink"></a>Köprü
 Köprü, ön plan/arka plan çiftine sahip olmayan bir denetimdir. Her durumda, koyu renkli, gri ve beyaz arka planlar üzerinde doğru şekilde görünecek ön plan köprü rengini kullanın. Köprü denetimi için renk belirtecini kullanmıyorsanız, "basılmış" için varsayılan sistem rengini görürsünüz ve bu, kırmızı olarak yanıp sönecektir. Bu, denetimin doğru ortam renk belirtecini kullanmayan sinyaltir.

 ![Köprü Redline](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")

 Kullan...
özel bir köprü oluşturmanız gerektiğinde.

 Kullanma...
Köprü olmayan her şey için.

 **Varsayılanını**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Varsayılan köprü](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")

 Ön plan (metin)

 `Environment.PanelHyperlink`

 **Hover**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Üzerine gelindiğinde köprü](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")

 Ön plan (metin)

 `Environment.PanelHyperlinkHover`

 **Pressed**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Köprü basıldı](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")

 Ön plan (metin)

 `Environment.PanelHyperlinkPressed`

 **Devre dışı**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Köprü devre dışı](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")

 Ön plan (metin)

 `Environment.PanelHyperlinkDisabled`

### <a name="infobar"></a>Üstündeki
 Popüler bir bağlam hakkında daha fazla bilgi sağlamak için ve her zaman bir belge penceresinin ya da araç penceresinin en üstünde görüntülenecek olan engelleri kullanır.

 ![Bilgi çubuğu Redline](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")

 Kullan...
Özel Engelliler oluştururken.

 Kullanma...
bilgi çubuğu 'na benzer olmayan UI öğeleri için.

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Üstündeki](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")

 **Üstündeki**

 Arka Plan

 `Environment.InfoBackground`

 Ön plan (metin)

 `Environment.InfoText`

 Kenarlık

 `Environment.ToolWindowBorder`

### <a name="scroll-bar"></a>Kaydırma çubuğu
 Kaydırma çubukları Visual Studio ortamı tarafından Stillendirilir ve temalı olması gerekmez. Ancak, UI 'nizin Visual Studio ortamının bu bölümüyle tutarlı şekilde görünmesi için, kaydırma çubuklarında kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.

 ![Kaydırma çubuğu Redline](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")

 Kullan...
Visual Studio kaydırma çubuklarını eşleştirmek istediğiniz kullanıcı arabirimini oluştururken.

 Kullanma... her zaman ScrollBar Kullanıcı arabirimini eşleştirmek istemediğiniz her şey için.

 **Varsayılanını**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Kaydırma çubuğu](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")

 **Kaydırma çubuğu**

 Kaydırma çubuğu

 `Environment.ScrollBarBackground`

 Ön plan (Thumb)

 `Environment.ScrollBarThumbBackground`

 ![Kaydırma çubuğu oku](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")

 **Kaydırma oku**

 Arka Plan

 `Environment.ScrollBarArrowBackground`

 Kaydırma çubuğu ile aynı renge ayarlanır.

 Ön plan (karakter)

 `Environment.ScrollBarArrowGlyph`

 **Hover**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Üzerine gelindiğinde kaydırma çubuğu](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")

 **Kaydırma çubuğu**

 Kaydırma çubuğu

 `Environment.ScrollBarBackground`

 Ön plan (Thumb)

 `Environment.ScrollBarThumbMouseOverBackground`

 ![Üzerine gelindiğinde kaydırma çubuğu oku](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")

 **Kaydırma oku**

 Arka Plan

 `Environment.ScrollBarArrowMouseOverBackground`

 Kaydırma çubuğu ile aynı renge ayarlanır.

 Ön plan (karakter)

 `Environment.ScrollBarArrowGlyphMouseOver`

 **Pressed**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Kaydırma çubuğu basıldı](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")

 **Kaydırma çubuğu**

 Kaydırma çubuğu

 `Environment.ScrollBarBackground`

 Ön plan (Thumb)

 `Environment.ScrollBarThumbPressedBackground`

 ![Kaydırma çubuğu okuna basıldığında](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")

 **Kaydırma oku**

 Arka Plan

 `Environment.ScrollBarArrowPressedBackground`

 Kaydırma çubuğu ile aynı renge ayarlanır.

 Ön plan (karakter)

 `Environment.ScrollBarArrowGlyphPressed`

### <a name="tree-view"></a><a name="BKMK_TreeView"></a> Ağaç görünümü

Çözüm Gezgini, Sunucu Gezgini ve Sınıf Görünümü dahil çeşitli araç pencereleri, renkleri TreeView kategorisindeki renk adlarıyla denetlenen hiyerarşik bir kurumsal düzen uygular. Ağaç görünümündeki tüm öğelerin arka plan ve metin renkleri vardır. İç içe alt öğelerine sahip olan öğeler, öğenin genişletildiğini veya daraltılıp daraltılmadığını belirten glifleri de vardır.

![Ağaç görünümü Redline](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")

Kullan...
hiyerarşik bir kurumsal görünüm uygulamanız gereken her yerde.

Kullanma...
- ağaç görünümüne benzer olmayan her şey için.

- belirtilen dışında bir arka plan/ön plan birleşimi.

  **Varsayılanını**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Ağaç görünümü](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")

  Arka Plan

  `TreeView.Background`

  Ön plan (metin)

  `TreeView.Background`

  Ön plan (karakter)

  `TreeView.Glyph`

  Kenarlık

  Hiçbiri

  **Hover**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Üzerine gelindiğinde ağaç görünümü](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")

  Arka Plan

  `TreeView.Background`

  Ön plan (metin)

  `TreeView.Background`

  Ön plan (karakter)

  `TreeView.GlyphMouseOver`

  Kenarlık

  Hiçbiri

  **Üzerine sürükleyin**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Ağaç görünümü üzerinde Drag](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")

  Arka Plan

  `TreeView.DragOverItem`

  Ön plan (metin)

  `TreeView.DragOverItem`

  Ön plan (karakter)

  `TreeView.DragOverItemGlyph`

  Kenarlık

  Hiçbiri

  **Seçili**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Ağaç görünümü odaklanmış](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")

  **Odaklı**

  Arka Plan

  `TreeView.SelectedItemActive`

  Ön plan (metin)

  `TreeView.SelectedItemActive`

  Ön plan (karakter)

  `TreeView.SelectedItemActiveGlyph`

  Kenarlık

  `TreeView.FocusVisualBorder`

  ![Ağaç görünümü odaklanmış değil](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")

  **Odaklanmadan gözetle**

  Arka Plan

  `TreeView.SelectedItemInactive`

  Ön plan (metin)

  `TreeView.SelectedItemInactive`

  Ön plan (karakter)

  `TreeView.SelectedItemInactiveGlyph`

  Kenarlık

  Hiçbiri

  **Seçili üzerine gelme**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![Üzerine odaklanmış ağaç görünümü](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")

  **Odaklı**

  Arka Plan

  `TreeView.SelectedItemActive`

  Ön plan (metin)

  `TreeView.SelectedItemActive`

  Ön plan (karakter)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Kenarlık

  Seçim`TreeView.FocusVisualBorder`

  ![Üzerine gelme üzerine odaklanılmış ağaç görünümü](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")

  **Odaklanmadan gözetle**

  Arka Plan

  `TreeView.SelectedItemInactive`

  Ön plan (metin)

  `TreeView.SelectedItemInactive`

  Ön plan (karakter)

  `TreeView.SelectedItemActiveGlyphMouseOver`

  Kenarlık

  Hiçbiri

### <a name="button-controls"></a>Düğme denetimleri
 ![Düğme denetimi Redline](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")

 Kullan...
belgedeki düğmeler için, Visual Studio temaları (açık, koyu, mavi veya sistem Yüksek Karşıtlık teması) ile tümleştirilebilir.

 Kullanma...
bir Visual Studio temasının parçası olmayan özel bir arka planda görüntülenecek düğmeler için.

 **Varsayılanını**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Düğme](../../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")

 Düğme

 `CommonControls.Button`

 Düğme kenarlığı

 `CommonControls.ButtonBorder`

 **Devre dışı**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Düğme devre dışı](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")

 Düğme

 `CommonControls.ButtonDisabled`

 Düğme kenarlığı

 `CommonControls.ButtonBorderDisabled`

 **Hover**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Üzerine gelindiğinde düğme](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")

 Düğme

 `CommonControls.ButtonHover`

 Düğme kenarlığı

 `CommonControls.ButtonBorderHover`

 **Pressed**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Düğmeye basıldı](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")

 Düğme

 `CommonControls.ButtonPressed`

 Düğme kenarlığı

 `CommonControls.ButtonBorderPressed`

 **Odaklı**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Düğme odaklı](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")

 Düğme

 `CommonControls.ButtonFocused`

 Düğme kenarlığı

 `CommonControls.ButtonBorderFocused`

### <a name="check-box-controls"></a>Onay kutusu denetimleri
 ![Onay kutusu Redline](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")

 Kullan...
Belge kutusu içinde bulunan onay kutusu denetimleri için.

 Kullanma...
onay kutusu denetimi olmayan herhangi bir kullanıcı arabirimi için.

 **Varsayılanını**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Onay kutusu](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")

 Arka Plan

 `CommonControls.CheckBoxBackground`

 Kenarlık

 `CommonControls.CheckBoxBorder`

 Metin

 `CommonControls.CheckBoxText`

 Simge

 `CommonControls.CheckBoxGlyph`

 **Devre dışı**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Onay kutusu devre dışı](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")

 Arka Plan

 `CommonControls.CheckBoxBackgroundDisabled`

 Kenarlık

 `CommonControls.CheckBoxBorderDisabled`

 Metin

 `CommonControls.CheckBoxTextDisabled`

 Simge

 `CommonControls.CheckBoxGlyphDisabled`

 **Hover**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Üzerine gelindiğinde onay kutusu](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")

 Arka Plan

 `CommonControls.CheckBoxBackgroundHover`

 Kenarlık

 `CommonControls.CheckBoxBorderHover`

 Metin

 `CommonControls.CheckBoxTextHover`

 Simge

 `CommonControls.CheckBoxGlyphHover`

 **Pressed**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Onay kutusu basılı](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")

 Arka Plan

 `CommonControls.CheckBoxBackgroundPressed`

 Kenarlık

 `CommonControls.CheckBoxBorderPressed`

 Metin

 `CommonControls.CheckBoxTextPressed`

 Simge

 `CommonControls.CheckBoxGlyphPressed`

 **Odaklı**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Odaklanmış onay kutusu](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")

 Arka Plan

 `CommonControls.CheckBoxBackgroundFocused`

 Kenarlık

 `CommonControls.CheckBoxBorderFocused`

 Metin

 `CommonControls.CheckBoxTextFocused`

 Simge

 `CommonControls.CheckBoxGlyphFocused`

### <a name="drop-boxcombo-box-controls"></a>Bırakma kutusu/birleşik giriş kutusu denetimleri

![&#45;aşağı açılan&#47;açılan kutu Redline](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")

Kullan...
Belge alanının parçası olan açılan kutular ve Birleşik giriş kutuları için.

Kullanma...
- açılır liste veya açılan kutu olmayan herhangi bir kullanıcı arabirimi.

- komut çubuğunda [açılan liste](../../misc/shared-colors.md#BKMK_CommandDropDown) veya [Birleşik giriş kutusu](../../misc/shared-colors.md#BKMK_CommandComboBox) için.

  **Varsayılanını**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![&#45;aşağı açılan&#47;açılan kutusu](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")

  Arka Plan

  `CommonControls.ComboBoxBackground`

  Kenarlık

  `CommonControls.ComboBoxBorder`

  Metin

  `CommonControls.ComboBoxText`

  Ayırıcı

  `CommonControls.ComboBoxSeparator`

  Simge

  `CommonControls.ComboBoxGlyph`

  Glif arka planı

  `CommonControls.ComboBoxGlyphBackground`

  **Devre dışı**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![&#45;aşağı açılan&#47;açılan kutusu devre dışı bırak](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")

  Arka Plan

  `CommonControls.ComboBoxBackgroundDisabled`

  Kenarlık

  `CommonControls.ComboBoxBorderDisabled`

  Metin

  `CommonControls.ComboBoxTextDisabled`

  Ayırıcı

  `CommonControls.ComboBoxSeparatorDisabled`

  Simge

  `CommonControls.ComboBoxGlyphDisabled`

  Glif arka planı

  `CommonControls.ComboBoxGlyphBackgroundDisabled`

  **Hover**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![&#45;aşağı&#47;açılan kutunun üzerine gelme](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")

  Arka Plan

  `CommonControls.ComboBoxBackgroundHover`

  Kenarlık

  `CommonControls.ComboBoxBorderHover`

  Metin

  `CommonControls.ComboBoxTextHover`

  Ayırıcı

  `CommonControls.ComboBoxSeparatorHover`

  Simge

  `CommonControls.ComboBoxGlyphHover`

  Glif arka planı

  `CommonControls.ComboBoxGlyphBackgroundHover`

  **Pressed**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![&#45;aşağı açılan&#47;açılan kutu tuşuna basıldığında](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")

  Arka Plan

  `CommonControls.ComboBoxBackgroundPressed`

  Kenarlık

  `CommonControls.ComboBoxBorderPressed`

  Metin

  `CommonControls.ComboBoxTextPressed`

  Ayırıcı

  `CommonControls.ComboBoxSeparatorPressed`

  Simge

  `CommonControls.ComboBoxGlyphPressed`

  Glif arka planı

  `CommonControls.ComboBoxGlyphBackgroundPressed`

  **Odaklı**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![&#45;aşağı açılan&#47;açılan kutu odaklı](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")

  Arka Plan

  `CommonControls.ComboBoxBackgroundFocused`

  Kenarlık

  `CommonControls.ComboBoxBorderFocused`

  Metin

  `CommonControls.ComboBoxTextFocused`

  Ayırıcı

  `CommonControls.ComboBoxSeparatorFocused`

  Simge

  `CommonControls.ComboBoxGlyphFocused`

  Glif arka planı

  `CommonControls.ComboBoxGlyphBackgroundFocused`

  **Metin girişi seçimi**

  Bileşen

  Öğe

  Belirteç adı: category. Color

  ![&#45;aşağı açılan&#47;açılan kutu metin girişi](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")

  Vurgula

  `CommonControls.ComboBoxTextInputSelection`

  **Basılan – liste öğesi görünümü**

  ![&#45;aşağı açılan&#47;açılan kutusu liste görünümünü bırak](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")

  Arka Plan

  `CommonControls.ComboBoxListBackground`

  `CommonControls.ComboBoxListBackgroundHover`

  `CommonControls.ComboBoxListItemBackgroundPressed`

  `CommonControls.ComboBoxListItemBackgroundFocused`

  Kenarlık

  `CommonControls.ComboBoxListBorder`

  `CommonControls.ComboBoxListBorderHover`

  `CommonControls.ComboBoxListBorderPressed`

  `CommonControls.ComboBoxListBorderFocused`

  Öğe metni

  `CommonControls.ComboBoxListItemText`

  `CommonControls.ComboBoxListItemTextHover`

  `CommonControls.ComboBoxListItemTextPressed`

  `CommonControls.ComboBoxListItemTextFocused`

  Arka plan gölgesi

  `CommonControls.ComboBoxListBackgroundShadow`

### <a name="tabular-data-grid-controls"></a>Tablo verileri (kılavuz) denetimleri
 Grid denetimleri olarak da bilinen tablosal veri denetimleri, Visual Studio için ortak denetimlerdir ve çok sayıda sütunda büyük miktarlarda veri sunmak için kullanılabilir. Standart tablo veri denetimleri, Visual Studio içinde birden çok yerde bulunabilir: Hata Listesi araç penceresi, IntelliTrace raporları ve bellek yığın görünümü, diğerleri arasında. Her zaman sunulan standart tablo veri denetimlerini kullanın. Nadir bazı örneklerde standart tablo veri denetimlerine erişiminiz olmayabilir. Bu durumlarda, UI 'nizin Visual Studio 'daki diğer tablolu veri denetimleriyle tutarlı olduğundan emin olmak için aşağıdaki belirteç adlarını kullanın.

 ![Tablo verileri &#40;kılavuz denetimi&#41; Redline](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")

 Kullan...
tablosal veya kılavuz denetimleri için.

 Kullanma...
Tablo veya kılavuz denetimi olmayan herhangi bir kullanıcı arabirimi için.

#### <a name="column-headers"></a>Sütun başlıkları
 Sütun üst bilgileri, bir arka plan, kenarlık, başlık metni ve genellikle bir kılavuz bu sütuna göre sıralandığında kullanılan isteğe bağlı bir glifden oluşur.

 Durum

 Öğe

 Belirteç adı: category. Color

 Varsayılan

 Arka Plan

 `Header.Default`

 Ön plan (metin)

 `Environment.CommandBarTextActive`

 Ön plan (karakter)

 `Header.Glyph`

 Kenarlık

 `Header.SeparatorLine`

 Hover

 Arka Plan

 `Header.MouseOver`

 Ön plan (metin)

 `Environment.CommandBarTextHover`

 Ön plan (karakter)

 `Header.MouseOverGlyph`

 Kenarlık

 `Header.SeparatorLine`

 Pressed

 Arka Plan

 `CommonControls.CheckBoxBackgroundPressed`

 Ön plan (metin)

 `CommonControls.CheckBoxBorderPressed`

 Ön plan (karakter)

 `CommonControls.CheckBoxTextPressed`

 Kenarlık

 `CommonControls.CheckBoxGlyphPressed`

#### <a name="list-view-items"></a>Liste görünümü öğeleri
 Liste görünümü öğeleri bir arka plan ve içerikten oluşur. İçerik metin, simge veya her ikisi olabilir.

 Durum

 Öğe

 Belirteç adı: category. Color

 Varsayılan

 Arka Plan

 Geçirgen

 Ön plan (metin)

 `Environment.CommandBarTextActive`

 Kenarlık

 Hiçbiri

 Seçili (etkin)

 Arka Plan

 `TreeView.SelectedItemActive`

 Ön plan (metin)

 `TreeView.SelectedItemActiveText`

 Kenarlık

 Hiçbiri

 Seçili (etkin değil)

 Arka Plan

 `TreeView.SelectedItemInactive`

 Ön plan (metin)

 `TreeView.SelectedItemInactiveText`

 Kenarlık

 Hiçbiri

## <a name="manifest-designer"></a>Bildirim Tasarımcısı

Bildirim Tasarımcısı, Windows 8 ve Windows Phone 8 projelerinde bildirim dosyasını düzenlemeyi kolaylaştırmak için bir yol olarak tasarlanmıştır. Tüketim için kullanılabilen bir paylaşılan çerçeve olmasa da, yönlendirme/gezinti sekmelerinin ve genel yapının tasarım düzen ve renklerini eşleştirmek uygun olabilir. Düzen ayrıntıları hakkında daha fazla bilgi için bkz. [Visual Studio Için düzen](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Bildirim Tasarımcısı Redline](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")

Kullan...
- Bildirim tasarımcısına benzer tasarımcılar için.

- Belge kutusu içindeki bir düzenleyicinin en üstünde ortak sekme denetimleri kullanma yerine.

Kullanma...
- Altıdan fazla sekmeniz varsa.

- Bildirim Tasarımcısı gibi yapılandırılmamış herhangi bir kullanıcı arabirimi için.

  Durum

  Bileşen

  Öğe

  Belirteç adı: category. Color

  Varsayılan (seçili)

  Tab

  Arka Plan

  `ManifestDesigner.TabActive`

  Kenarlık

  Hiçbiri

  Açıklama bölmesi

  Arka Plan

  `ManifestDesigner.DescriptionPane`

  İçerik sayfası

  Arka Plan

  `ManifestDesigner.Background`

  İletişim kutusu Yardımcısı metni

  `ManifestDesigner.WatermarkText`

  Bu belirteç adı işlevle eşleşmiyor.

  Seçilmeyen

  Tab

  Arka Plan

  `ManifestDesigner.Tab.Inactive`

  Hover

  Tab

  Arka Plan

  `ManifestDesigner.Tab.Mouseover`

## <a name="tagging"></a>Etiketleme
 Visual Studio, bir kullanıcının izleme amacıyla aranabilir anahtar sözcükleri bildirmesine olanak sağlayan etiketlemeyi destekler. Örneğin, proje yöneticileri ve geliştiriciler iş öğelerini etiketlemek için Team Foundation Server (TFS) kullanabilir. Aşağıdaki tablolarda hem etiketin kendisi için renk adları hem de üzerine gelme ve seçili durumlarda görüntülenen "Kapat simgesi" karakteri verilmiştir.

 ![Redline etiketleme](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")

 Kullan...
etiketlemeyi destekleyen kullanıcı arabirimi için.

 Kullanma...
Diğer Kullanıcı arabirimi türleri için.

### <a name="tag"></a>Etiket
 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Tag](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")

 **Varsayılanını**

 Arka Plan

 `Tag.Background`

 Ön plan (metin)

 `Tag.Background`

 ![Üzerine gelindiğinde etiketle](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")

 **Hover**

 Arka Plan

 `Tag.HoverBackground`

 Ön plan (metin)

 `Tag.HoverBackgroundText`

 ![Basılan etiketi](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")

 **Pressed**

 Arka Plan

 `Tag.PressedBackground`

 Ön plan (metin)

 `Tag.PressedBackgroundText`

 ![Etiket seçildi](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")

 **Seçili**

 Arka Plan

 `Tag.SelectedBackground`

 Ön plan (metin)

 `Tag.SelectedBackgroundText`

### <a name="glyph-close-icon"></a>Glif (Kapat simgesi)
 **Varsayılanını**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![&#40;karakter&#41;etiketi ](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")

 **Varsayılan (etiket varsayılanı)**

 Arka Plan

 Yok

 Ön plan (karakter)

 `Tag.TagHoverGlyph`

 **Hover**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Vurgulu &#40;karakter&#41; etiketi](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")

 **Üzerine gelme (varsayılan etiket)**

 Arka Plan

 `Tag.TagHoverGlyphHoverBackground`

 Ön plan (karakter)

 `Tag.TagHoverGlyphHover`

 Kenarlık

 `Tag.TagHoverGlyphHoverBorder`

 **Pressed**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![&#40;karakter&#41; basıldığında etiketle](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")

 **Basılan (varsayılan etiket)**

 Arka Plan

 `Tag.TagHoverGlyphPressedBackground`

 Ön plan (karakter)

 `Tag.TagHoverGlyphPressed`

 Kenarlık

 `Tag.TagHoverGlyphPressedBorder`

 **Seçili/karakter varsayılanı etiketi**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Etiket seçildi](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")

 **Varsayılan (etiket seçildi)**

 Arka Plan

 Yok

 Ön plan (karakter)

 `Tag.TagSelectedGlyph`

 **Seçili etiket/karakter üzerine gelme**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Üzerine gelindiğinde etiket seçildi](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")

 **Üzerine gelme (etiket seçildi)**

 Arka Plan

 `Tag.TagSelectedGlyphHoverBackground`

 Ön plan (karakter)

 `Tag.TagSelectedGlyphHover`

 Kenarlık

 `Tag.TagSelectedGlyphHoverBorder`

 **Seçili etiket/karakter basıldı**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Etiket seçiliyken basılan](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")

 **Basılan (etiket seçildi)**

 Arka Plan

 `Tag.TagSelectedGlyphPressedBackground`

 Ön plan (karakter)

 `Tag.TagSelectedGlyphPressed`

 Kenarlık

 `Tag.TagSelectedGlyphPressedBorder`

## <a name="shell"></a>Kabuk

### <a name="background"></a>Arka Plan

Ortam arka planı iki katmandan oluşur. Alt katman, tüm IDE 'yi içeren düz bir renktir. En üstteki katman, komut rafı altına ve araç penceresi arasında IDE 'nin sol ve sağ kenarlarındaki kanalları otomatik olarak gizler. Visual Studio 2013 itibariyle, üst ve alt arka plan katmanları açık ve koyu temalarda aynı renge ayarlanır.

![Kabuk arka plan Redline](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")

Kullan...
Visual Studio ortamının arka planıyla eşleştirmek istediğiniz konumlar için.

Kullanma...
- arka plan yüzeyleri olmayan yerleri için bir Fill.

- ön plan öğelerini yerleştirmek istediğiniz arka plan olarak.

  Bileşen

  Öğe

  Belirteç adı: category. Color

  Alt katman

  Arka Plan

  `Environment.EnvironmentBackground`

  Bileşen

  Öğe

  Belirteç adı: category. Color

  Üst katman

  Arka Plan

  *Gradyan duraklarının Visual Studio 2013 ışığı ve koyu temalarda aynı renk değerine ayarlanır.*

  `Environment.EnvironmentBackgroundGradientBegin`

  `Environment.EnvironmentBackgroundGradientEnd`

  `Environment.EnvironmentBackgroundGradientMiddle1`

  `Environment.EnvironmentBackgroundGradientMiddle2`

### <a name="command-shelf"></a>Komut rafı

Komut raf planları için iki belirteç adı kümesi kullanılır: menü çubuğunun bulunduğu bir küme ve komut çubuklarının bulunduğu konum. Tek bir komut çubuğu grubu, "komut çubuğu" bölümünde daha ayrıntılı olarak ele alınan kendi arka plan rengi değerlerine sahiptir. Menü çubuğu ve komut çubuğu metni sırasıyla menü ve komut çubuğu bölümlerinde ele alınmıştır.

![Komut rafı Redline](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")

Kullan...
- Menüleri veya araç çubuklarını yerleştirdiğiniz alanlarda.

- arka plan/? ön plan belirteci adı birleşimi doğru.

Kullanma...
bir komut rafı ile benzer olmayan alanlarda.

  Bileşen

  Öğe

  Belirteç adı: category. Color

  Menü çubuğu

  Arka Plan

  *Gradyan duraklarının Visual Studio 2013 ışığı ve koyu temalarda aynı renk değerine ayarlanır.*

  `Environment.CommandShelfHighlightGradientBegin`

  `Environment.CommandShelfHighlightGradientMiddle`

  `Environment.CommandShelfHighlightGradientEnd`

  Komut çubuğu

  Arka Plan

  *Gradyan duraklarının Visual Studio 2013 ışığı ve koyu temalarda aynı renk değerine ayarlanır.*

  `Environment.CommandShelfBackgroundGradientBegin`

  `Environment.CommandShelfBackgroundGradientMiddle`

  `Environment.CommandShelfBackgroundGradientEnd`

## <a name="toolbox"></a>Araç Kutusu
 Araç kutusu, Visual Studio 'da en sık kullanılan ortak araç pencerelerini biridir. Aslında özel tema ve stil uygulanmış bir ağaç denetimidir.

 ![Araç kutusu Redline](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")

 Kullan...
her zaman kabuk araç kutusu ile tutarlı olmasını istediğiniz bir araç penceresi tasarladığınızda.

 Kullanma...
Araç kutusu kullanıcı arabirimine benzer olmayan veya kabuk araç kutusu renkleri değiştiğinde Kullanıcı arabiriminde sorun olup olmadığından emin değilseniz.

 **Varsayılanını**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Araç kutusu üst düğümü](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")

 **Üst düğüm**

 ![Araç kutusu alt düğümü](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")

 **Alt düğüm**

 Arka Plan

 `Environment.ToolboxContent`

 Bölüm başlıkları

 `Environment.ToolWindowBackground`

 Bireysel öğeler veya kullanılabilir denetim yoksa tüm pencere

 Kenarlık

 Hiçbiri

 Ön plan (karakter)

 `Environment.ToolboxContent`

 Ön plan (metin)

 `Environment.ToolboxContent`

 **Hover**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Bağlantı kutusu üzerinde alt düğüm](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")

 **Alt düğümde üzerine gelme araç kutusu**

 Arka Plan

 `Environment.ToolboxContentMouseOver`

 Yalnızca bireysel öğeler

 Kenarlık

 Hiçbiri

 Ön plan (metin)

 `Environment.ToolboxContentMouseOver`

 Yalnızca bireysel öğeler

 **Seçili**

 Bileşen

 Öğe

 Belirteç adı: category. Color

 ![Araç kutusu üst düğümü odaklı](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")

 **Odaklanmış üst düğüm**

 ![Araç kutusu alt düğümü odaklı](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")

 **Odaklanmış alt düğüm**

 Arka Plan

 `TreeView.SelectedItemActive`

 [Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden

 Kenarlık

 `TreeView.FocusVisualBorder`

 [Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden

 Ön plan (karakter)

 `TreeView.SelectedItemActive`

 [Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden

 Ön plan (metin)

 `TreeView.SelectedItemActive`

 [Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden

 ![Araç kutusu üst düğümü odaklanmış değil](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")

 **Odaklanmış olmayan üst düğüm**

 ![Araç kutusu alt düğümü odaklanmış değil](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")

 **Odaklanmış olmayan alt düğüm**

 Arka Plan

 `TreeView.SelectedItemInactive`

 [Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden

 Kenarlık

 Hiçbiri

 Ön plan (karakter)

 `TreeView.SelectedItemInactive`

 [Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden

 Ön plan (metin)

 `TreeView.SelectedItemInactive`

 [Ağaç görünümü](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) kategorisinden
