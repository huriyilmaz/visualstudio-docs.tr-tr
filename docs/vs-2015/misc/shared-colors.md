---
title: Paylaşılan renkler | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 9d3186f3-07d2-441f-b33e-435e95d8a0b8
caps.latest.revision: 11
ms.author: brgeorge
ms.openlocfilehash: 421ff85831bb611b655de2bc35f01423b61921a2
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302408"
---
# <a name="shared-colors"></a>Paylaşılan renkler
Açıklamayı buraya ekleyin.  
  
## <a name="shared-colors"></a>Paylaşılan renkler  
 Ortak Visual Studio kabuk öğelerini kullanan kullanıcı arabirimi tasarlarken veya arabirim öğenizin benzer özelliklerle tutarlı olmasını istediğinizde, renkleri seçmek ve atamak için paket tanım dosyalarındaki mevcut belirteç adlarını kullanın. Bu, uI'nizin genel Visual Studio ortamıyla tutarlı kalmasını ve temalar eklendiğinde veya güncelleştirildiğinde otomatik olarak güncelolmasını sağlar.  
  
 Bu makalede, benzer kullanıcı aracı kullanırken başvuruda bulunabileceğiniz yaygın Kullanıcı Aracı öğeleri ve kullandıkları belirteç adları açıklanmaktadır. Bu renk belirteçlerine nasıl erişilisürüp erişilenler hakkında özel bilgiler için [VSColor Hizmeti'ne](../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)bakın.  
  
 Belirteç adlarını doğru kullandığınızdan emin olun:  
  
- **Renk kendisi değil, işlevine göre belirteç adlarını kullanın.** Ortak paylaşılan renkler belirli arabirim öğeleriyle ilişkilidir ve yalnızca aynı veya benzer özellikler için kullanılmak üzere tasarlanmıştır. Örneğin, sırf rengi beğendiğiniz için, döndürülen bir açılan kutunun rengini döndürme ilerleme animasyonu için yeniden kullanmayın. Açılan kutunun ve animasyonun işlevleri farklıdır ve açılan kutuyla ilişkili renk değişirse, animasyon öğeniz için artık uygun bir renk olmayabilir. Tutarlı renk kullanımı, kullanıcılarınızı yönlendirmeye ve karışıklığı önlemeye yardımcı olur.  
  
- **Doğru kombinasyonda arka plan ve metin renklerini kullanın.** Metinle birlikte kullanılması amaçlanan arka plan renkleri ilişkili bir metin renge sahip olur. Metin renklerini, bu arka plan için belirtilenler dışında kullanmayın. İlişkili bir metin rengi yoksa, metni görüntülemeyi beklediğiniz herhangi bir yüzey için bu arka plan rengini kullanmayın. Diğer metin ve arka plan renkleri birleşimleri okunamayan bir arabirimle sonuçlanabilir.  
  
- **Konumlarına uygun denetim renklerini kullanın.** Bazı eyaletlerde, bazı Visual Studio denetimlerinin ayrı kenarlık ve arka plan renkleri yoktur. Bunun yerine, arkalarındaki yüzeylerden bu renkleri alırlar. Denetimi yerleştirdiğiniz konuma her zaman uygun belirteç adlarını kullandığınızdan emin olun.  
  
> [!IMPORTANT]
> "Başlangıç Sayfası" veya "Elma Şarabı" kategorilerinde bulunan jetonları kullanmayın!  
  
### <a name="command-structures"></a>Komut yapıları  
  
#### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menü  
 Menüler Visual Studio 2013 içinde çeşitli yerlerde oluşabilir: ana menü çubuğu, belge veya araç pencerelerine gömülü, ya da IDE boyunca çeşitli yerlerde sağ tıklama. Diğer UI öğeleriile ilişkili menülerin uygulamaları ilgili öğe için bölümde ele alınmıştır. Visual Studio ortamı tarafından sağlanan standart menü uygulamasını her zaman kullanmalısınız. Ancak, bazı nadir durumlarda standart Visual Studio menülerine erişiminiz olmayabilir. Bu gibi durumlarda, kullanıcı bir kullanıcı yanınızın Visual Studio'daki diğer menülerle tutarlı olduğundan emin olmak için aşağıdaki belirteç adlarını kullanın.  
  
 ![Menüler redline](../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
Kullanın...  
- özel bir menü oluşturmanız gerektiğinde.  
  
- Visual Studio menülerini eşleştirmek istediğiniz yeni bir UI bileşenine sahip olduğunuzda.  
  
Kullanmayın ...  
tek başına arka plan rengi. Her zaman belirtildiği gibi arka plan/ön plan kombinasyonunu kullanın.  
  
##### <a name="menu-title"></a>Menü başlığı  
 Menü başlıkları bir arka plan, kenarlık ve başlık metninin yanı sıra genellikle menü bir komut çubuğunda bulunduğunda isteğe bağlı bir sözcükten oluşur.  
  
 ![Menü başlığı redline](../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
Kullanın...  
özel bir menü başlığı oluşturduğunuzda.  
  
Kullanmayın...  
- her zaman menü başlığı nı eşleştirmek istemediğiniz herhangi bir şey için.  
  
- belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda.  
  
  **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü başlığı varsayılan](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Menü başlığı**|Arka plan|None|  
|![Menü başlığı varsayılan](../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")<br /><br /> **Menü başlığı**|Ön Plan (Metin)|`Environment.CommandBarTextActive`|  
|![Glyph varsayılanlı menü başlığı](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Glyph ile menü başlığı**|Ön Plan (Glyph)|`Environment.CommandBarMenuGlyph`|  
|![Glyph varsayılanlı menü başlığı](../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br /><br /> **Glyph ile menü başlığı**|Kenarlık|None|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hover üzerinde Menü başlığı](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Menü başlığı**|Arka plan|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Hover üzerinde Menü başlığı](../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")<br /><br /> **Menü başlığı**|Ön Plan (Metin)|`Environment.CommandBarTextHover`|  
|![Hover üzerinde glyph ile Menü başlığı](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Glyph ile menü başlığı**|Ön Plan (Glyph)|`Environment.CommandBarMenuMouseOverGlyph`|  
|![Hover üzerinde glyph ile Menü başlığı](../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br /><br /> **Glyph ile menü başlığı**|Kenarlık|`Environment.CommandBarBorder`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü başlığı basıldığında](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Menü başlığı**|Arka plan|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Menü başlığı basıldığında](../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")<br /><br /> **Menü başlığı**|Ön Plan (Metin)|`Environment.CommandBarTextActive`|  
|![Glyph basılı menü başlığı](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Glyph ile menü başlığı**|Ön Plan (Glyph)|`Environment.CommandBarMenuMouseDownGlyph`|  
|![Glyph basılı menü başlığı](../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br /><br /> **Glyph ile menü başlığı**|Kenarlık|`Environment.CommandBarMenuBorder`<br /><br /> Sadece sol, üst ve sağ taraf.|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Glyph engelli menü başlığı](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Glyph ile menü başlığı**|Arka plan|None|  
|![Glyph engelli menü başlığı](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Glyph ile menü başlığı**|Ön Plan (Metin)|`Environment.CommandBarTextInactive`|  
|![Glyph engelli menü başlığı](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Glyph ile menü başlığı**|Ön Plan (Glyph)|`Environment.CommandBarTextInactive`|  
|![Glyph engelli menü başlığı](../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br /><br /> **Glyph ile menü başlığı**|Kenarlık|None|  
  
##### <a name="menu"></a>Menü  
 Tek bir menü öğesi menü metninden ve isteğe bağlı bir simge, onay kutusu veya alt menü glyph'den oluşur. Onun arka plan ve metin renk değişikliği hover üzerinde. Bu renk belirteci bir arka plan/ön plan çiftidir.  
  
 ![Menü öğeleri redline](../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 Kullanın...  
 menü çubuğundan veya komut çubuğundan başlatılan açılır liste için.  
  
Kullanmayın...  
- başka bir bağlamda oluşan herhangi bir açılır liste için.  

- belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda.  
  
  **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Arka plan|`Environment.CommandBarMenuBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Ön Plan (Metin)|`Environment.CommandBarTextActive`|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Ön plan (Submenu glyph)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Kenarlık|`Environment.CommandBarMenuBorder`|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Simge kanal arka planı|`Environment.CommandBarMenuIconBackground`|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Ayırıcı|`Environment.CommandBarMenuSeparator`|  
|![Menü varsayılan](../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")<br /><br /> **Menü**|Gölge|`Environment.DropShadowBackground`|  
|![Menü işaretli](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **İşaretli**|Onay işareti|`Environment.CommandBarCheckBox`|  
|![Menü işaretli](../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")<br /><br /> **İşaretli**|İşaret arka planı|`Environment.CommandBarSelectedIcon`|  
|![Seçili menü](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Seçildi**|Simge arka plan|`Environment.CommandBarSelected`|  
|![Seçili menü](../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")<br /><br /> **Seçildi**|Simge kenarlığı|`Environment.CommandBarSelectedBorder`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü gezinme](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Menü öğesi**|Arka plan|`Environment.CommandBarMenuItemMouseOver`|  
|![Menü gezinme](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Menü öğesi**|Ön Plan (Metin)|`Environment.CommandBarMenuItemMouseOver`|  
|![Menü gezinme](../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")<br /><br /> **Menü öğesi**|Ön plan (Submenu glyph)|`Environment.CommandBarMenuMouseOverSubmenuGlyph`|  
|![Menü gezinme kontrol](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **İşaretli**|Onay işareti|`Environment.CommandBarCheckBoxMouseOver`|  
|![Menü gezinme kontrol](../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")<br /><br /> **İşaretli**|İşaret arka planı|`Environment.CommandBarHoverOverSelectedIcon`|  
|![Menü gezinmek seçili](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Seçildi**|Simge arka plan|`Environment.CommandBarHoverOverSelected`|  
|![Menü gezinmek seçili](../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")<br /><br /> **Seçildi**|Simge kenarlığı|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Menü devre dışı](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Menü öğesi|Ön Plan (Metin)|`Environment.CommandBarTextInactive`|  
|![Menü devre dışı](../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")<br /><br /> Menü öğesi|Ön plan (Submenu glyph)|`Environment.CommandBarMenuSubmenuGlyph`|  
|![Menü devre dışı bırakılmış](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> İşaretli|Onay işareti|`Environment.CommandBarCheckBoxDisabled`|  
|![Menü devre dışı bırakılmış](../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")<br /><br /> İşaretli|İşaret arka planı|`Environment.CommandBarSelectedIconDisabled`|  
  
#### <a name="command-bar"></a>Komut çubuğu  
 Komut çubuğu Visual Studio IDE içinde birden çok yerde görünebilir, en önemlisi komut rafı ve araç veya belge pencerelerine gömülü.  
  
 Genel olarak, Visual Studio ortamı tarafından sağlanan standart komut çubuğu uygulamasını her zaman kullanın. Standart mekanizmanın kullanılması, tüm görsel ayrıntıların doğru görünmesini ve etkileşimli öğelerin diğer Visual Studio komut çubuğu denetimleriyle tutarlı bir şekilde hareket edecektir. Ancak, kendi komut çubuğunuzu oluşturmanız gerekiyorsa, aşağıdaki belirteç adlarını kullanarak komutu doğru şekilde şekillendirdiğinizden emin olun.  
  
 ![Komut çubuğu redline](../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![Taşma düğmesi redline](../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 Kullanın...  
 gömülü bir komut çubuğuna ihtiyacınız olan ancak standart Visual Studio komut çubuğu uygulamasını kullanamadığınız yerlerde.  
  
Kullanmayın...  
- komut çubuğuna benzemeyen UI öğeleri için.  

- belirteç adlarının belirtildiği olanlar dışındaki komut çubuğu bileşenleri için.  
  
##### <a name="command-bar-group"></a>Komut çubuğu grubu  
 Komut çubuğu grubu ilgili bir komut çubuğu denetim kümesinden oluşur ve herhangi bir sayıda düğme, bölme düğmesi, açılır menüler, açılan kutular veya menüler içerebilir. Bu denetimler için renkler ayrı belirteç adlarıyla düzenlenir ve bu kılavuzda başka bir yerde ayrı ayrı tartışılır. Bir ayırıcı satır, komut çubuğu grubunu ilgili alt gruplara bölmek için kullanılır.  
  
 ![Komut çubuğu grubu redline](../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 Kullanın...  
 gömülü bir komut çubuğuna ihtiyacınız olan ancak standart Visual Studio komut çubuğu uygulamasını kullanamadığınız yerlerde.  
  
Kullanmayın...  
- komut çubuğuna benzemeyen UI öğeleri için.  

- belirteç adlarının belirtildiği olanlar dışındaki komut çubuğu bileşenleri için.  
  
  **Varsayılan** (başka durum yok)  
  
|Öğe|Belirteç adı: Category.color|  
|-------------|--------------------------------|  
|Arka plan|`Environment.CommandBarGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|Kenarlık|`Environment.CommandBarToolBarBorder`|  
|Sürükleme kolu|`Environment.CommandBarDragHandle`|  
|Ayırıcı|`Environment.CommandBarToolBarSeparator`<br /><br /> `Environment.CommandBarToolBarSeparatorHighlight`|  
  
##### <a name="command-icons"></a>Komut simgeleri  
 ![Komut simgesi redline](../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![Komut simgesi redline](../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 Kullanın...  
 komut çubuğuna yerleştirilecek tüm düğmeler için.  
  
Kullanmayın...  
- kendi belirteç adlarına sahip denetimler için.  

- belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda.  
  
  **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Komut simgesi varsayılan](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Varsayılan**|Arka plan|N/A (komut çubuğu arka planından devralır)|  
|![Komut simgesi varsayılan](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Varsayılan**|Ön Plan (Metin)|`Environment.CommandBarTextActive`|  
|![Komut simgesi varsayılan](../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")<br /><br /> **Varsayılan**|Kenarlık|Yok|  
|![Komut simgesi varsayılan seçili](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Seçildi**|Arka plan|`Environment.CommandBarSelected`|  
|![Komut simgesi varsayılan seçili](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Seçildi**|Ön Plan (Metin)|`Environment.CommandBarTextSelected`|  
|![Komut simgesi varsayılan seçili](../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br /><br /> **Seçildi**|Kenarlık|`Environment.CommandBarSelectedBorder`|  
  
 **Hover ve klavye odaklı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Komut simgesi gezinme](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Hover standart**|Arka plan|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Komut simgesi gezinme](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Hover standart**|Ön Plan (Metin)|`Environment.CommandBarTextHover`|  
|![Komut simgesi gezinme](../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")<br /><br /> **Hover standart**|Kenarlık|`Environment.CommandBarBorder`|  
|![Komut simgesi gezinmek seçili](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Hover'da seçildi**|Arka plan|`Environment.CommandBarHoverOverSelected`|  
|![Komut simgesi gezinmek seçili](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Hover'da seçildi**|Ön Plan (Metin)|`Environment.CommandBarTextHoverOverSelected`|  
|![Komut simgesi gezinmek seçili](../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br /><br /> **Hover'da seçildi**|Kenarlık|`Environment.CommandBarHoverOverSelectedIconBorder`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Komut simgesi basılı](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Basılı komut simgesi**|Arka plan|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Komut simgesi basılı](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Basılı komut simgesi**|Ön Plan (Metin)|`Environment.CommandBarTextMouseDown`|  
|![Komut simgesi basılı](../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")<br /><br /> **Basılı komut simgesi**|Kenarlık|`Environment.CommandBarBorder`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Komut simgesi devre dışı](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Devre dışı bırakılmış komut simgesi**|Arka plan|N/A (komut çubuğu arka planından devralır)|  
|![Komut simgesi devre dışı](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Devre dışı bırakılmış komut simgesi**|Ön Plan (Metin)|`Environment.CommandBarTextInactive`|  
|![Komut simgesi devre dışı](../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")<br /><br /> **Devre dışı bırakılmış komut simgesi**|Kenarlık|Yok|  
  
##### <a name="combo-box"></a><a name="BKMK_CommandComboBox"></a>Açılan kutu  
  
> [!IMPORTANT]
> Açılan kutular açılır düşüşlere benzer, ancak editable metin bölgesi içerir. Açılır bırakmanızda editable metin bölgesi bulunmuyorsa, [Açılan](../misc/shared-colors.md#BKMK_CommandDropDown)metin altında bulunan renk belirteçlerini kullanın.  
  
 ![Açılan kutu redline](../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
Kullanın...  
- özel açılan kutular inşa ederken.  

- açılan kutuya benzer bir komut çubuğu denetimi oluştururken.  

Kullanmayın ...  
- her zaman komut çubuğu Kullanıcı Arabirimi maç istemediğiniz bir şey için.  

- stildeki bir açılan kutuya erişebildiğinizde.  
  
  **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Açılan kutu giriş alanı](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Giriş alanı**|Arka plan|`Environment.ComboBoxBackground`|  
|![Açılan kutu giriş alanı](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Giriş alanı**|Ön Plan (Metin)|`Environment.ComboBoxText`|  
|![Açılan kutu giriş alanı](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Giriş alanı**|Kenarlık|`Environment.ComboBoxBorder`|  
|![Açılan kutu giriş alanı](../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")<br /><br /> **Giriş alanı**|Ayırıcı|Ayırıcı yok|  
|![Açılan kutu açılır&#45;aşağı düğmesi](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Açılır düğme**|Arka plan|N/A (devralır)|  
|![Açılan kutu açılır&#45;aşağı düğmesi](../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`Environment.ComboBoxGlyph`|  
|![Açılan kutu&#47;açılır&#45;aşağı liste](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Açılır liste**|Arka plan|`Environment.ComboBoxPopupBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Açılan kutu&#47;açılır&#45;aşağı liste](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Açılır liste**|Ön Plan (Metin)|`Environment.ComboBoxItemText`|  
|![Açılan kutu&#47;açılır&#45;aşağı liste](../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br /><br /> **Açılır liste**|Kenarlık|`Environment.ComboBoxPopupBorder`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Combo kutu giriş alanı hover üzerinde](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Giriş alanı**|Arka plan|`Environment.ComboBoxMouseOverBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Combo kutu giriş alanı hover üzerinde](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Giriş alanı**|Ön Plan (Metin)|`Environment.ComboBoxMouseOverText`|  
|![Combo kutu giriş alanı hover üzerinde](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Giriş alanı**|Kenarlık|`Environment.ComboBoxMouseOverBorder`|  
|![Combo kutu giriş alanı hover üzerinde](../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br /><br /> **Giriş alanı**|Ayırıcı|`Environment.ComboBoxMouseOverSeparator`|  
|![Açılan kutu&#47;bırak&#45;aşağı düğmesini havada](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Açılır düğme**|Arka plan|`Environment.ComboBoxButtonMouseOverBackground`|  
|![Açılan kutu&#47;bırak&#45;aşağı düğmesini havada](../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`Environment.ComboBoxMouseOverGlyph`|  
|![Açılan kutu&#47;&#45;aşağı hover üzerinde liste bırakın](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Açılır liste**|Arka plan (Menü öğesi)|`Environment.ComboBoxItemMouseOverBackground`|  
|![Açılan kutu&#47;&#45;aşağı hover üzerinde liste bırakın](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Açılır liste**|Ön Plan (Metin)|`Environment.ComboBoxItemMouseOverText`|  
|![Açılan kutu&#47;&#45;aşağı hover üzerinde liste bırakın](../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br /><br /> **Açılır liste**|Kenarlık (Menü öğesi)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Odaklı**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![Combo kutu giriş alanı odaklı](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Giriş alanı**|Arka plan|`Environment.ComboBoxFocusedBackground`|  
|![Combo kutu giriş alanı odaklı](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Giriş alanı**|Ön Plan (Metin)|`Environment.ComboBoxFocusedText`|  
|![Combo kutu giriş alanı odaklı](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Giriş alanı**|Kenarlık|`Environment.ComboBoxFocusedBorder`|  
|![Combo kutu giriş alanı odaklı](../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br /><br /> **Giriş alanı**|Ayırıcı|`Environment.ComboBoxFocusedButtonSeparator`|  
|![Açılan kutu&#47;açılan&#45;aşağı düğmesi odaklı](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Açılır düğme**|Arka plan|`Environment.ComboBoxFocusedButtonBackground`|  
|![Açılan kutu&#47;açılan&#45;aşağı düğmesi odaklı](../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`Environment.ComboBoxFocusedGlyph`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![Combo kutu giriş alanı basıldığında](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Giriş alanı**|Arka plan|`Environment.ComboBoxMouseDownBackground`|  
|![Combo kutu giriş alanı basıldığında](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Giriş alanı**|Ön Plan (Metin)|`Environment.ComboBoxMouseDownText`|  
|![Combo kutu giriş alanı basıldığında](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Giriş alanı**|Kenarlık|`Environment.ComboBoxMouseDownBorder`|  
|![Combo kutu giriş alanı basıldığında](../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br /><br /> **Giriş alanı**|Ayırıcı|`Environment.ComboBoxMouseDownSeparator`|  
|![Açılan kutu&#47;açılır&#45;aşağı düğmesine basıldığında](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Açılır düğme**|Arka plan|`Environment.ComboBoxButtonMouseDownBackground`|  
|![Açılan kutu&#47;açılır&#45;aşağı düğmesine basıldığında](../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`Environment.ComboBoxMouseDownGlyph`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![Açılan kutu giriş alanı devre dışı](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Giriş alanı**|Arka plan|`Environment.ComboBoxDisabledBackground`|  
|![Açılan kutu giriş alanı devre dışı](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Giriş alanı**|Ön Plan (Metin)|`Environment.ComboBoxDisabledText`|  
|![Açılan kutu giriş alanı devre dışı](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Giriş alanı**|Kenarlık|`Environment.ComboBoxDisabledBorder`|  
|![Açılan kutu giriş alanı devre dışı](../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br /><br /> **Giriş alanı**|Ayırıcı|Ayırıcı yok|  
|![Açılan kutu&#47;açılır&#45;düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Açılır düğme**|Arka plan|None|  
|![Açılan kutu&#47;açılır&#45;düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`Environment.ComboBoxDisabledGlyph`|  
  
##### <a name="drop-down"></a><a name="BKMK_CommandDropDown"></a>Açılır  
  
> [!IMPORTANT]
> Açılan düşüşler açılan kutulara benzer, ancak kullanılabilir metin bölgeleri yok. Açılır bırakmanızda editable metin bölgesi varsa, [Combo kutusunun](../misc/shared-colors.md#BKMK_CommandComboBox)altında bulunan renk belirteçlerini kullanın.  
  
 ![&#45;kırmızı çizgiye düşür](../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 Kullanın...  
 özel açılır liste denetimleri oluştururken.  
  
Kullanmayın ...  
- açılır listeye benzer olmayan herhangi bir şey için.  

- açılan kutular veya bölünmüş düğmeler için.  
  
  **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![seçim alanını&#45;aşağı bırakma](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Seçim alanı**|Arka plan|`Environment.DropDownBackground`|  
|![seçim alanını&#45;aşağı bırakma](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Seçim alanı**|Ön Plan (Metin)|`DropDownText`|  
|![seçim alanını&#45;aşağı bırakma](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Seçim alanı**|Kenarlık|`DropDownBorder`|  
|![seçim alanını&#45;aşağı bırakma](../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")<br /><br /> **Seçim alanı**|Ayırıcı|Ayırıcı yok|  
|![&#45;aşağı düğmesini bırak](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Açılır düğme**|Arka plan|None|  
|![&#45;aşağı düğmesini bırak](../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`Environment.DropDownGlyph`|  
|![&#45;açılan liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Açılır liste**|Arka plan|`Environment.DropDownPopupBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![&#45;açılan liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Açılır liste**|Ön Plan (Metin)|`Environment.ComboBoxItemText`|  
|![&#45;açılan liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Açılır liste**|Kenarlık|`Environment.DropDownPopupBorder`|  
|![&#45;açılan liste](../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")<br /><br /> **Açılır liste**|Gölge|`Environment.DropShadowBackground`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;'ı havada seçim alanına bırak](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Seçim alanı**|Arka plan|`Environment.DropDownMouseOverBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![&#45;'ı havada seçim alanına bırak](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Seçim alanı**|Ön Plan (Metin)|`Environment.DropDownMouseOverText`|  
|![&#45;'ı havada seçim alanına bırak](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Seçim alanı**|Kenarlık|`Environment.DropDownMouseOverBorder`|  
|![&#45;'ı havada seçim alanına bırak](../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br /><br /> **Seçim alanı**|Ayırıcı|`Environment.DropDownButtonMouseOverSeparator`|  
|![Gezinme de&#45;aşağı düğmesini bırak](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Açılır düğme**|Arka plan|`Environment.DropDownButtonMouseOverBackground`|  
|![Gezinme de&#45;aşağı düğmesini bırak](../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`Environment.DropDownMouseOverGlyph`|  
|![&#45;aşağı listesini havada bırak](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Açılır liste**|Arka plan (Menü öğesi)|`Environment.ComboBoxItemMouseOverBackground`|  
|![&#45;aşağı listesini havada bırak](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Açılır liste**|Ön Plan (Metin)|`Environment.ComboBoxItemMouseOverText`|  
|![&#45;aşağı listesini havada bırak](../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")<br /><br /> **Açılır liste**|Kenarlık (Menü öğesi)|`Environment.ComboBoxItemMouseOverBorder`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;aşağı seçim alanına basılı bırakma](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Seçim alanı**|Arka plan|`Environment.DropDownMouseDownBackground`|  
|![&#45;aşağı seçim alanına basılı bırakma](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Seçim alanı**|Ön Plan (Metin)|`Environment.DropDownMouseDownText`|  
|![&#45;aşağı seçim alanına basılı bırakma](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Seçim alanı**|Kenarlık|`Environment.DropDownMouseDownBorder`|  
|![&#45;aşağı seçim alanına basılı bırakma](../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br /><br /> **Seçim alanı**|Ayırıcı|`Environment.DropDownButtonMouseDownSeparator`|  
|![&#45;aşağı düğmesine basılı bırak](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Açılır düğme**|Arka plan|`Environment.DropDownButtonMouseDownBackground`|  
|![&#45;aşağı düğmesine basılı bırak](../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`Environment.DropDownMouseDownGlyph`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;aşağı seçim alanını devre dışı bırakma](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Arka plan|`Environment.DropDownDisabledBackground`|  
|![&#45;aşağı seçim alanını devre dışı bırakma](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Ön Plan (Metin)|`Environment.DropDownDisabledText`|  
|![&#45;aşağı seçim alanını devre dışı bırakma](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Kenarlık|`Environment.DropDownDisabledBorder`|  
|![&#45;aşağı seçim alanını devre dışı bırakma](../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")|Ayırıcı|Ayırıcı yok|  
|![&#45;aşağı düğmesini devre dışı bırakma](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Arka plan|Yok|  
|![&#45;aşağı düğmesini devre dışı bırakma](../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")|Ön Plan (Glyph)|`Environment.DropDownDisabledGlyph`|  
  
##### <a name="split-button"></a>Bölme düğmesi  
 Bölme düğmeleri, düğmeler, menüler ve komut çubuğu metni gibi diğer komut çubuğu denetimleriyle birçok belirteç adını paylaşır. Tüm gerekli eylem ve açılır düğme belirteç adları kolaylık sağlamak için burada tekrarlanır. Split düğmesi açılır listeleri komut çubuğu [Menüleri'nin](../misc/shared-colors.md#BKMK_CommandMenus)uygulamalarıdır.  
  
 ![Bölme düğmesi redline](../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 Kullanın...  
 özel bir bölme düğmesi oluşturuyorsanız.  
  
Kullanmayın ...  
- düğmeleri diğer türleri için.  

- belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda.  
  
  **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bölme düğmesi](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Bölme düğmesi (varsayılan)**|Arka plan|None|  
|![Bölme düğmesi](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Bölme düğmesi (varsayılan)**|Ön Plan (Metin)|`Environment.CommandBarTextActive`|  
|![Bölme düğmesi](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Bölme düğmesi (varsayılan)**|Ön Plan (Glyph)|`Environment.CommandBarSplitButtonGlyph`|  
|![Bölme düğmesi](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Bölme düğmesi (varsayılan)**|Kenarlık|Yok|  
|![Bölme düğmesi](../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")<br /><br /> **Bölme düğmesi (varsayılan)**|Ayırıcı|Yok|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hover üzerinde Split düğmesi](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Bölme düğmesi (gezinme de)**|Arka plan|`Environment.CommandBarMouseOverBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Hover üzerinde Split düğmesi](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Bölme düğmesi (gezinme de)**|Ön Plan (Metin)|`Environment.CommandBarTextHover`|  
|![Hover üzerinde Split düğmesi](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Bölme düğmesi (gezinme de)**|Ön Plan (Glyph)|`Environment.CommandBarSplitButtonMouseOverGlyph`|  
|![Hover üzerinde Split düğmesi](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Bölme düğmesi (gezinme de)**|Kenarlık|`Environment.CommandBarBorder`|  
|![Hover üzerinde Split düğmesi](../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")<br /><br /> **Bölme düğmesi (gezinme de)**|Ayırıcı|`Environment.CommandBarSplitButtonSeparator`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bölme düğmesine basıldı](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Bölme düğmesi (basılı)**|Arka plan|`Environment.CommandBarMouseDownBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Bölme düğmesine basıldı](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Bölme düğmesi (basılı)**|Ön Plan (Metin)|`Environment.CommandBarTextMouseDown`|  
|![Bölme düğmesine basıldı](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Bölme düğmesi (basılı)**|Ön Plan (Glyph)|`Environment.CommandBarSplitButtonMouseDownGlyph`|  
|![Bölme düğmesine basıldı](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Bölme düğmesi (basılı)**|Kenarlık|`Environment.CommandBarBorder`|  
|![Bölme düğmesine basıldı](../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")<br /><br /> **Bölme düğmesi (basılı)**|Ayırıcı|Yok|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bölme düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Bölme düğmesi (devre dışı)**|Arka plan|Yok|  
|![Bölme düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Bölme düğmesi (devre dışı)**|Ön Plan (Metin)|`Environment.ComboBoxItemTextInactive`|  
|![Bölme düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Bölme düğmesi (devre dışı)**|Ön Plan (Glyph)|`Environment.CommandBarTextInactive`|  
|![Bölme düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Bölme düğmesi (devre dışı)**|Kenarlık|Yok|  
|![Bölme düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br /><br /> **Bölme düğmesi (devre dışı)**|Ayırıcı|Yok|  
  
##### <a name="more-options-and-overflow-buttons"></a>'Daha fazla seçenek' ve 'Taşma' düğmeleri  
 Bir komut çubuğu grubu ilgili komut çubuğu düğmelerini ekleyerek veya kaldırarak özelleştirilebilir olduğunda "Daha fazla seçenek" düğmesi kullanılır. Yatay boşluk olmadığı için komut çubuğu kesildiğinde "Taşma" düğmesi görüntülenir ve tıklatıldığında görüntülenemeyen komut çubuğu düğmelerini içeren bir menü gösterilir. Bu iki düğmenin renkleri aynı belirteç adları kümesi tarafından denetlenir.  
  
 ![Daha fazla seçenek redline](../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 Kullanın...  
 özel 'Daha fazla seçenek' veya 'Taşma' düğmeleri için.  
  
 Kullanmayın ...  
 'Daha fazla seçenek' veya 'Taşma' düğmesine benzer işlevselliği olmayan düğmeler için.  
  
 **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Daha fazla seçenek](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Daha fazla seçenek**|Arka plan|`Environment.CommandBarOptionsBackground`|  
|![Daha fazla seçenek](../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")<br /><br /> **Daha fazla seçenek**|Ön Plan (Glyph)|`Environment.CommandBarOptionsGlyph`|  
|![Taşma düğmesi](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Taşma**|Arka plan|`Environment.CommandBarOptionsBackground`|  
|![Taşma düğmesi](../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")<br /><br /> **Taşma**|Ön Plan (Glyph)|`Environment.CommandBarOptionsGlyph`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hover hakkında daha fazla seçenek](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Daha fazla seçenek**|Arka plan|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Hover hakkında daha fazla seçenek](../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")<br /><br /> **Daha fazla seçenek**|Ön Plan (Glyph)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Havada taşma](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Taşma**|Arka plan|`Environment.CommandBarOptionsMouseOverBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Havada taşma](../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")<br /><br /> **Taşma**|Ön Plan (Glyph)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Daha fazla seçenek basılı](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Daha fazla seçenek**|Arka plan|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Daha fazla seçenek basılı](../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")<br /><br /> **Daha fazla seçenek**|Ön Plan (Glyph)|`Environment.CommandBarOptionsMouseDownGlyph`|  
|![Taşması basıldığında](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Taşma**|Arka plan|`Environment.CommandBarOptionsMouseDownBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Taşması basıldığında](../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")<br /><br /> **Taşma**|Ön Plan (Glyph)|`Environment.CommandBarOptionsMouseDownGlyph`|  
  
### <a name="document-windows"></a>Belge pencereleri  
 Visual Studio ortamı tarafından sağlandığı için belge pencerelerini çoğaltmaya gerek yoktur. Ancak, kullanıcı ui'nizin Her zaman Visual Studio ortamının bu bölümüyle tutarlı görünmesi için belge pencerelerinde kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.  
  
 Belge penceresi renk belirteçlerini kullanırken, bunları yalnızca benzer öğeler ve her zaman çiftler halinde kullanmaya dikkat etmelisiniz. Bunu yapmazsanız, uI'nizde beklenmeyen sonuçlar elde elabilirsiniz.  
  
#### <a name="document-window-frame"></a>Belge penceresi çerçevesi  
 Belge pencereleri IDE'ye sabitlenebilir veya ayrı bir pencere olarak kayar. Bir belge penceresi IDE dışında yüzer, hala iyi bir belge oturur ve arka plan, kenarlık, metin ve sekme renkleri IDE bir parçası olduğu zaman aynıdır. Ancak, belge kendi arka planı, kenarlık ve metin renkleri olan bir çerçeve içinde oturur. Araç pencereleri belgeye iyi sabitlendiğinde, sekmelerinin davranışını ve rengini belge penceresi belirteç adlarından devralır.  
  
 ![Sabitlenmiş belge penceresi redline](../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **Sabitlenmiş belge penceresi**  
  
 ![Kayan belge penceresi redline](../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **Kayan belge penceresi**  
  
 Kullanın...  
 belge penceresiyle eşleştirmek istediğiniz herhangi bir yerde UI oluşturursanız.  
  
 Kullanmayın ...  
 kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için.  
  
 **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|Belge: kenetlenmiş veya kayan|Arka plan|Belge türüne bağlıdır|  
|Belge: kenetlenmiş veya kayan|Ön Plan (Metin)|Belge türüne bağlıdır|  
|Belge: kenetlenmiş veya kayan|Kenarlık|`Environment.ToolWindowBorder`|  
|![Çerçeve odaklı](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Çerçeve: kayan, odaklanmış**|Arka plan|`Environment.ToolWindowFloatingFrame`|  
|![Çerçeve odaklı](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Çerçeve: kayan, odaklanmış**|Ön Plan (Metin)|`Environment.ToolWindowFloatingFrame`|  
|![Çerçeve odaklı](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Çerçeve: kayan, odaklanmış**|Ön Plan (Glyph)|`Environment.RaftedWindowButtonActiveGlyph`|  
|![Çerçeve odaklı](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Çerçeve: kayan, odaklanmış**|Kenarlık|`Environment.MainWindowActiveDefaultBorder`|  
|![Çerçeve odaklı](../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")<br /><br /> **Çerçeve: kayan, odaklanmış**|Kenarlık (Glyph)|`Environment.RaftedWindowButtonActiveBorder`<br /><br /> Saydam olarak ayarlayın|  
|![Çerçeve odaklanmamış](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Çerçeve: kayan, odaklanmamış**|Arka plan|`Environment.ToolWindowFloatingFrameInactive`|  
|![Çerçeve odaklanmamış](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Çerçeve: kayan, odaklanmamış**|Ön Plan (Metin)|`Environment.ToolWindowFloatingFrameInactive`|  
|![Çerçeve odaklanmamış](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Çerçeve: kayan, odaklanmamış**|Ön Plan (Glyph)|`Environment.RaftedWindowButtonInactiveGlyph`|  
|![Çerçeve odaklanmamış](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Çerçeve: kayan, odaklanmamış**|Kenarlık|`Environment.MainWindowInactiveBorder`|  
|![Çerçeve odaklanmamış](../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")<br /><br /> **Çerçeve: kayan, odaklanmamış**|Kenarlık (Glyph)|`Environment.RaftedWindowButtonInactiveBorder`<br /><br /> Saydam olarak ayarlayın|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Çerçeve hover odaklanmış](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Çerçeve: kayan, odaklanmış**|Arka Plan (Glyph)|`Environment.RaftedWindowButtonHoverActive`|  
|![Çerçeve hover odaklanmış](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Çerçeve: kayan, odaklanmış**|Ön Plan (Glyph)|`Environment.RaftedWindowButtonHoverActiveGlyph`|  
|![Çerçeve hover odaklanmış](../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")<br /><br /> **Çerçeve: kayan, odaklanmış**|Kenarlık (Glyph)|`Environment.RaftedWindowButtonHoverActiveBorder`|  
|![Çerçeve hover üzerinde odaklanmamış](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Çerçeve: kayan, odaklanmamış**|Arka Plan (Glyph)|`EnvironmentRaftedWindowButtonHoverInactive`|  
|![Çerçeve hover üzerinde odaklanmamış](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Çerçeve: kayan, odaklanmamış**|Ön Plan (Glyph)|`Environment.RaftedWindowButtonHoverInactiveGlyph`|  
|![Çerçeve hover üzerinde odaklanmamış](../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br /><br /> **Çerçeve: kayan, odaklanmamış**|Kenarlık (Glyph)|`Environment.RaftedWindowButtonHoverInactiveBorder`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Çerçeve odaklı basılı](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Çerçeve: kayan, odaklanmış**|Arka Plan (Glyph)|`Environment.RaftedWindowButtonDown`|  
|![Çerçeve odaklı basılı](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Çerçeve: kayan, odaklanmış**|Ön Plan (Glyph)|`Environment.RaftedWindowButtonDownGlyph`|  
|![Çerçeve odaklı basılı](../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")<br /><br /> **Çerçeve: kayan, odaklanmış**|Kenarlık (Glyph)|`Environment.RaftedWindowButtonDownBorder`|  
  
#### <a name="document-tabs"></a>Belge sekmeleri  
 Belge sekmeleri, hangi belgelerin şu anda açık olduğunu ve hangisinin geçerli seçili veya etkin belge olduğunu belirtmek için sekme kanalında yer alacaktır. Araç pencereleri, kullanıcı bunları oraya yerleştirirse belge sekmesi kanalına da sabitlenebilir. Bu durumda, belge pencereleri ile aynı sekme renklerini kullanırlar. Belge penceresi renklerini her zaman eşleştirmek istediğiniz kullanıcı aracı oluşturuyorsanız (tema güncelleştirmeleri veya yeni temalar yüklenmişse), bu renk belirteçlerine başvurun.  
  
 ![Belge sekmesi redline](../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 Kullanın...  
 belge sekmelerini eşleştirmek ve otomatik olarak tema güncelleştirmeleri veya yeni tema renkleri almak istediğiniz ui oluşturuyorsanız her yerde.  
  
 Kullanmayın ...  
 kabuk bir tema güncelleştirmesi olduğunda otomatik olarak değiştirmek istemediğiniz herhangi bir Kullanıcı Arabirimi için.  
  
##### <a name="open-document-tabs"></a>Belge sekmelerini açma  
 Her açık belgenin, belge sekmesi kanalında adını görüntüleyen bir sekme vardır. Belgeler arka planda seçilebilir veya açılabilir ve sekmeleri şu durumları yansıtır:  
  
- Seçili sekme, belgede şu anda iyi görüntülenen belgeyi temsil eder. Seçili sekmede, belgenin üst kenarına kadar uzanan bir belge kenarlığı vardır.  
  
- Arka plan sekmeleri, şu anda seçili sekme olmayan belge sekmeleridir. Tıklatıldıktan sonra, seçili sekme olurlar ve bu belirteç adlarından tüm arka plan, kenarlık ve metin renklerini elde ederler.  
  
  ![Belge sekmesini kırmızı çizgide açma](../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  Kullanın...  
  özel belge sekmeleri oluştururken.  
  
  Kullanmayın ...  
  - geçici (önizleme) sekmeleri için.  
  
- kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için.  
  
##### <a name="selected-tab"></a>Seçili sekme  
 **Odaklı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Seçili sekme odaklı](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Seçili belge sekmesi, odaklanmış**|Arka plan|`Environment.FileTabSelectedGradientTop`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Seçili sekme odaklı](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Seçili belge sekmesi, odaklanmış**|Ön Plan (Metin)|`Environment.FileTabSelectedText`|  
|![Seçili sekme odaklı](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Seçili belge sekmesi, odaklanmış**|Kenarlık|`Environment.FileTabSelectedBorder`<br /><br /> Arka planla aynı renge ayarlayın.|  
|![Seçili sekme odaklı](../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")<br /><br /> **Seçili belge sekmesi, odaklanmış**|Belge kenarlığı|`Environment.FileTabDocumentBorderBackground`|  
  
 **Odaklanmamış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Seçili sekme odaklanmamış](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Seçili belge sekmesi, odaklanmamış**|Arka plan|`Environment.FileTabInactiveGradientTop`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Seçili sekme odaklanmamış](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Seçili belge sekmesi, odaklanmamış**|Ön Plan (Metin)|`Environment.FileTabInactiveText`|  
|![Seçili sekme odaklanmamış](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Seçili belge sekmesi, odaklanmamış**|Kenarlık|`Environment.FileTabInactiveBorder`<br /><br /> Arka planla aynı renge ayarlayın.|  
|![Seçili sekme odaklanmamış](../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br /><br /> **Seçili belge sekmesi, odaklanmamış**|Belge kenarlığı|`Environment.FileTabInactiveDocumentBorderBackground`|  
  
##### <a name="background-tab"></a>Arka plan sekmesi  
 **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![Arka plan sekmesi](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Arka plan sekmesi varsayılan**|Arka plan|`Environment.FileTabBackground`|  
|![Arka plan sekmesi](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Arka plan sekmesi varsayılan**|Ön Plan (Metin)|`Environment.FileTabText`|  
|![Arka plan sekmesi](../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")<br /><br /> **Arka plan sekmesi varsayılan**|Kenarlık|`Environment.FileTabBorder`<br /><br /> Arka planla aynı renge ayarlayın.|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![Hover üzerinde arka plan sekmesi](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Hover üzerinde arka plan sekmesi**|Arka plan|`Environment.FileTabHotGradientTop`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Hover üzerinde arka plan sekmesi](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Hover üzerinde arka plan sekmesi**|Ön Plan (Metin)|`Environment.FileTabHotText`|  
|![Hover üzerinde arka plan sekmesi](../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")<br /><br /> **Hover üzerinde arka plan sekmesi**|Kenarlık|`Environment.FileTabHotBorder`<br /><br /> Arka planla aynı renge ayarlayın.|  
  
##### <a name="preview-tab"></a>Önizleme sekmesi  
 Kullanıcı Çözüm Gezgini araç penceresinde bir öğeyi tıklattığında önizleme sekmesi belge sekmesi kanalının sağ tarafında görünür. Belgenin önizlemesi görevi görür ve kullanıcıya belgeyi belge sekmesi kanalının sol tarafında açık tutma seçeneği de verir. Aynı anda yalnızca bir önizleme sekmesi açılabilir. Önizleme sekmeleri hem arka plana hem de açık sekmeler gibi seçili durumlara sahiptir ve etkin durumlarında odaklanmış veya odaklanmamış olabilir.  
  
 ![Önizleme sekmesi redline](../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 Kullanın...  
 geçici önizleme oluşturduğunuz her yerde ve bazı öğenin geçerli önizleme sekmesi rengiyle eşleşmesini ister.  
  
Kullanmayın ...  
- geçici olmayan herhangi bir belge veya sekme için (önizleme).  

- kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için.  
  
  **Seçili önizleme sekmesi: Odaklanmış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Önizleme sekmesi odaklı](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Odaklanmış önizleme sekmesi**|Arka plan|`Environment.FileTabProvisionalSelectedActive`|  
|![Önizleme sekmesi odaklı](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Odaklanmış önizleme sekmesi**|Ön Plan (Metin)|`Environment.FileTabProvisionalSelectedActiveForeground`|  
|![Önizleme sekmesi odaklı](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Odaklanmış önizleme sekmesi**|Kenarlık|`Environment.FileTabProvisionalSelectedActiveBorder`<br /><br /> Arka planla aynı renge ayarlayın.|  
|![Önizleme sekmesi odaklı](../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")<br /><br /> **Odaklanmış önizleme sekmesi**|Belge kenarlığı|`Environment.FileTabProvisionalSelectedActiveBorder`|  
  
 **Seçili önizleme sekmesi: Odaklanmamış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Önizleme sekmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Odaklanmamış önizleme sekmesi**|Arka plan|`Environment.FileTabProvisionalSelectedInactive`|  
|![Önizleme sekmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Odaklanmamış önizleme sekmesi**|Ön Plan (Metin)|`Environment.FileTabProvisionalSelectedInactiveForeground`|  
|![Önizleme sekmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Odaklanmamış önizleme sekmesi**|Kenarlık|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
|![Önizleme sekmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br /><br /> **Odaklanmamış önizleme sekmesi**|Belge kenarlığı|`Environment.FileTabProvisionalSelectedInactiveBorder`|  
  
 **Arka plan önizleme sekmesi: Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Arka plan sekmesini önizleme](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Önizleme sekmesi arka plan sekmesi**|Arka plan|`Environment.FileTabProvisionalInactive`|  
|![Arka plan sekmesini önizleme](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Önizleme sekmesi arka plan sekmesi**|Ön Plan (Metin)|`Environment.FileTabProvisionalInactiveForeground`|  
|![Arka plan sekmesini önizleme](../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br /><br /> **Önizleme sekmesi arka plan sekmesi**|Kenarlık|`Environment.FileTabProvisionalInactiveBorder`<br /><br /> Arka planla aynı renge ayarlayın.|  
  
 **Arka plan önizleme sekmesi: Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Gezinme üzerinde önizleme arka plan sekmesi](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Gezinme sekmesinde önizleme sekmesi**|Arka plan|`Environment.FileTabProvisionalHover`|  
|![Gezinme üzerinde önizleme arka plan sekmesi](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Gezinme sekmesinde önizleme sekmesi**|Ön Plan (Metin)|`Environment.FileTabProvisionalHoverForeground`|  
|![Gezinme üzerinde önizleme arka plan sekmesi](../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br /><br /> **Gezinme sekmesinde önizleme sekmesi**|Kenarlık|`Environment.FileTabProvisionalHoverBorder`<br /><br /> Arka planla aynı renge ayarlayın.|  
  
##### <a name="document-overflow-button"></a>Belge taşması düğmesi  
 Geçerli yapılandırmada tüm belge sekmelerine uyacak dikey boşluk olup olmadığına bakılmaksızın, açık bir veya daha fazla belge varsa belge taşması düğmesi bulunur. **CommandBarMenu** renkleri (bkz. [Menüler)](../misc/shared-colors.md#BKMK_CommandMenus)tarafından denetlenir belge taşma açılır menüsü, hem görünür hem de gizli tüm açık belgelerin listesini görüntüler ve tüm açık belgelerin sekme kanalında görüntülenip görüntülenmediğine bağlı olarak taşma glifleri değişir.  
  
 ![Taşma kırmızı çizgi](../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
Kullanın...  
özel bir belge taşma düğmesi oluştururken.  

Kullanmayın ...  
- taşma düğmesine benzemeyen UI için.  

- komut çubuğu taşma düğmeleri için.  
  
  **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Taşma](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Belge taşması düğmesi**|Arka plan|`Environment.DocWellOverflowButtonBackground`|  
|![Taşma](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Belge taşması düğmesi**|Ön Plan (Glyph)|`Environment.DocWellOverflowButtonGlyph`|  
|![Taşma](../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")<br /><br /> **Belge taşması düğmesi**|Kenarlık|Yok|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Havada taşma](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Gezinme üzerinde belge taşması düğmesi**|Arka plan|`Environment.DocWellOverflowButtonMouseOverBackground`|  
|![Havada taşma](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Gezinme üzerinde belge taşması düğmesi**|Ön Plan (Glyph)|`Environment.DocWellOverflowButtonMouseOverGlyph`|  
|![Havada taşma](../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")<br /><br /> **Gezinme üzerinde belge taşması düğmesi**|Kenarlık|`Environment.DocWellOverflowButtonMouseOverBorder`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Taşması basıldığında](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Basılı belge taşması düğmesi**|Arka plan|`Environment.DocWellOverflowButtonMouseDownBackground`|  
|![Taşması basıldığında](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Basılı belge taşması düğmesi**|Ön Plan (Glyph)|`Environment.DocWellOverflowButtonMouseDownGlyph`|  
|![Taşması basıldığında](../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")<br /><br /> **Basılı belge taşması düğmesi**|Kenarlık|`Environment.DocWellOverflowButtonMouseDownBorder`|  
  
### <a name="tool-windows"></a>Araç pencereleri  
 Araç pencerelerini çoğaltmaya gerek yoktur, çünkü Bunlar Visual Studio ortamı tarafından sağlanır. Ancak, kullanıcı arabirimi'nizin Visual Studio ortamının bu bölümüyle tutarlı görünmesi için araç pencerelerinde kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.  
  
 ![Araç penceresi redline](../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 Kullanın...  
 araç pencerelerini eşleştirmek istediğiniz her yerde ui oluşturursanız.  
  
 Kullanmayın ...  
 kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için.  
  
#### <a name="tool-window-frame"></a>Araç pencere çerçevesi  
 Visual Studio'daki araç pencereleri birçok farklı görev için kullanılır ve birkaç farklı durumdan birinde bulunabilir. Bir araç penceresi açıksa, belge alanının dört tarafından herhangi biri atanabilir. Araç pencereleri, kullanıcının ekranı içinde herhangi bir yerde yeniden konumlandırılmak üzere IDE'nin dışında da yüzebilir. Yüzen pencereler her zaman IDE üstüne oturun. Son olarak, araç pencereleri belge pencereleri olarak sabitlenebilir ve belgede bir sekme olarak iyi görünebilir. Belge penceresi olarak sabitlenmiş araç pencereleri belge penceresi belirteç adlarını kullanarak kısmen renklenir.  
  
 ![Araç penceresi çerçevesi redline](../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 Kullanın...  
 araç pencerelerini eşleştirmek istediğiniz her yerde ui oluşturursanız.  
  
 Kullanmayın ...  
 kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için.  
  
 **Yerleşik**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi sabitlendi](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Arka plan|`Environment.ToolWindowBackground`|  
|![Araç penceresi sabitlendi](../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")|Kenarlık|`Environment.ToolWindowBorder`|  
  
 **Kayan: odaklanmış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi odaklı](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Arka plan|`Environment.ToolWindowBackground`|  
|![Araç penceresi odaklı](../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")|Kenarlık|`Environment.MainWindowActiveDefaultBorder`|  
  
 **Kayan: odaklanmamış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi odaklanmamış](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Arka plan|`Environment.ToolWindowBackground`|  
|![Araç penceresi odaklanmamış](../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")|Kenarlık|`Environment.MainWindowInactiveBorder`|  
  
#### <a name="tool-window-title-bar"></a>Araç penceresi başlık çubuğu  
 Başlık çubuğu kenarlığı gerçek bir kenarlık değil, başlık çubuğunun üst kısmında kalın bir çizgidir. Onun odaklanmış durumu için bir belirteç adı yok.  
  
 ![Araç penceresi başlık çubuğu redline](../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 Kullanın...  
 araç pencerelerini eşleştirmek istediğiniz her yerde ui oluşturursanız.  
  
 Kullanmayın ...  
 kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için.  
  
 **Odaklı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Başlık çubuğu odaklı](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Odaklanmış başlık çubuğu**|Arka plan|`Environment.TitleBarActiveGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Başlık çubuğu odaklı](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Odaklanmış başlık çubuğu**|Ön Plan (Metin)|`Environment.TitleBarActiveText`|  
|![Başlık çubuğu odaklı](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Odaklanmış başlık çubuğu**|Kenarlık|`Environment.TitleBarActiveBorder`<br /><br /> Arka planla aynı renge ayarlayın.|  
|![Başlık çubuğu odaklı](../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")<br /><br /> **Odaklanmış başlık çubuğu**|Sürükleme kolu|`Environment.TitleBarDragHandleActive`|  
  
 **Odaklanmamış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Başlık çubuğu odaklanmamış](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Odaklanmamış başlık çubuğu**|Arka plan|`Environment.TitleBarInactiveGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Başlık çubuğu odaklanmamış](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Odaklanmamış başlık çubuğu**|Ön Plan (Metin)|`Environment.TitleBarInactiveText`|  
|![Başlık çubuğu odaklanmamış](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Odaklanmamış başlık çubuğu**|Kenarlık|Yok|  
|![Başlık çubuğu odaklanmamış](../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")<br /><br /> **Odaklanmamış başlık çubuğu**|Sürükleme kolu|`Environment.TitleBarDragHandle`|  
  
##### <a name="title-bar-buttons"></a>Başlık çubuğu düğmeleri  
 ![Başlık çubuğu düğmesi redline](../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 Kullanın...  
 araç penceresi başlık çubuklarından renk belirteçleri kullanan UI'de görünen düğmeler için.  
  
Kullanmayın ...  
- diğer konumlarda görünen düğmeler için.  

- belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda.  
  
  **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Başlık çubuğu düğmesi odaklı](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Odaklı**|Arka plan|Yok|  
|![Başlık çubuğu düğmesi odaklı](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Odaklı**|Ön Plan (Glyph)|`Environment.ToolWindowButtonActiveGlyph`|  
|![Başlık çubuğu düğmesi odaklı](../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br /><br /> **Odaklı**|Kenarlık|Yok|  
|![Başlık çubuğu düğmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Odaklanmamış**|Arka plan|Yok|  
|![Başlık çubuğu düğmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Odaklanmamış**|Ön Plan (Glyph)|`Environment.ToolWindowButtonInactiveGlyph`|  
|![Başlık çubuğu düğmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br /><br /> **Odaklanmamış**|Kenarlık|Yok|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Başlık çubuğu düğmesi hover odaklanmış](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Odaklı**|Arka plan|`Environment.ToolWindowButtonHoverActive`|  
|![Başlık çubuğu düğmesi hover odaklanmış](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Odaklı**|Ön Plan (Glyph)|`Environment.ToolWindowButtonHoverActiveGlyph`|  
|![Başlık çubuğu düğmesi hover odaklanmış](../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br /><br /> **Odaklı**|Kenarlık|`Environment.ToolWindowButtonHoverActiveBorder`|  
|![Başlık çubuğu düğmesi gezinmeye odaklanmamış](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Odaklanmamış**|Arka plan|`Environment.ToolWindowButtonHoverInactive`|  
|![Başlık çubuğu düğmesi gezinmeye odaklanmamış](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Odaklanmamış**|Ön Plan (Glyph)|`Environment.ToolWindowButtonHoverInactiveGlyph`|  
|![Başlık çubuğu düğmesi gezinmeye odaklanmamış](../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br /><br /> **Odaklanmamış**|Kenarlık|`Environment.ToolWindowButtonHoverInactiveBorder`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Başlık çubuğu düğmesi odaklanmış ve basıldığında](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Odaklı**|Arka plan|`Environment.ToolWindowButtonDown`|  
|![Başlık çubuğu düğmesi odaklanmış ve basıldığında](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Odaklı**|Ön Plan (Glyph)|`Environment.ToolWindowButtonDownActiveGlyph`|  
|![Başlık çubuğu düğmesi odaklanmış ve basıldığında](../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br /><br /> **Odaklı**|Kenarlık|`Environment.ToolWindowButtonDownBorder`|  
|![Başlık çubuğu düğmesi odaklanmadı ve basıldı](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Odaklanmamış**|Arka plan|`Environment.ToolWindowButtonDown`|  
|![Başlık çubuğu düğmesi odaklanmadı ve basıldı](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Odaklanmamış**|Ön Plan (Glyph)|`Environment.ToolWindowButtonDownInactiveGlyph`|  
|![Başlık çubuğu düğmesi odaklanmadı ve basıldı](../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br /><br /> **Odaklanmamış**|Kenarlık|`Environment.ToolWindowButtonDownBorder`|  
  
#### <a name="tool-window-tabs"></a>Araç penceresi sekmeleri  
 ![Araç penceresi sekmesi redline](../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 Kullanın...  
 araç pencerelerini eşleştirmek istediğiniz her yerde ui oluşturursanız.  
  
 Kullanmayın ...  
 kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için.  
  
 **Seçili sekme**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi sekmesi odaklı](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Seçili, odaklanmış araç penceresi sekmesi**|Arka plan|`Environment.ToolWindowTabSelectedTab`|  
|![Araç penceresi sekmesi odaklı](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Seçili, odaklanmış araç penceresi sekmesi**|Ön Plan (Metin)|`Environment.ToolWindowTabSelectedActiveText`|  
|![Araç penceresi sekmesi odaklı](../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br /><br /> **Seçili, odaklanmış araç penceresi sekmesi**|Kenarlık|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Arka planla aynı renge ayarlayın.|  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi sekmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Seçili, odaklanılmamış araç penceresi sekmesi**|Arka plan|`Environment.ToolWindowTabSelectedTab`|  
|![Araç penceresi sekmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Seçili, odaklanılmamış araç penceresi sekmesi**|Ön Plan (Metin)|`Environment.ToolWindowTabSelectedText`|  
|![Araç penceresi sekmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br /><br /> **Seçili, odaklanılmamış araç penceresi sekmesi**|Kenarlık|`Environment.ToolWindowTabSelectedBorder`<br /><br /> Arka planla aynı renge ayarlayın.|  
  
 **Arka plan sekmesi**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç penceresi arka plan sekmesi](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Arka plan aracı penceresi sekmesi**|Arka plan|`Environment.ToolWindowTabGradientBegin`<br /><br /> Visual Studio 2013'te degrade durakları aynı renk değerine ayarlanmış.<br /><br /> `Environment.ToolWindowTabGradientEnd`<br /><br /> Visual Studio 2013'te degrade durakları aynı renk değerine ayarlanmış.|  
|![Araç penceresi arka plan sekmesi](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Arka plan aracı penceresi sekmesi**|Ön Plan (Metin)|`Environment.ToolWindowTabText`|  
|![Araç penceresi arka plan sekmesi](../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br /><br /> **Arka plan aracı penceresi sekmesi**|Kenarlık|`Environment.ToolWindowTabBorder`|  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hover üzerinde araç penceresi arka plan sekmesi](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Hover üzerinde arka plan aracı pencere sekmesi**|Arka plan|`Environment.ToolWindowTabMouseOverBackgroundBegin`<br /><br /> Visual Studio 2013'te degrade durakları aynı renk değerine ayarlanmış.<br /><br /> `Environment.ToolWindowTabMouseOverBackgroundEnd`<br /><br /> Visual Studio 2013'te degrade durakları aynı renk değerine ayarlanmış.|  
|![Hover üzerinde araç penceresi arka plan sekmesi](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Hover üzerinde arka plan aracı pencere sekmesi**|Ön Plan (Metin)|`Environment.ToolWindowTabMouseOverText`|  
|![Hover üzerinde araç penceresi arka plan sekmesi](../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br /><br /> **Hover üzerinde arka plan aracı pencere sekmesi**|Kenarlık|`Environment.ToolWindowTabMouseOverBorder`<br /><br /> Arka planla aynı renge ayarlayın.|  
  
#### <a name="auto-hide-tabs"></a>Otomatik gizleme sekmeleri  
 ![Otomatik&#45;redline gizlemek](../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 Kullanın...  
 otomatik olarak gizlenmiş araç pencere sekmelerini eşleştirmek istediğiniz ui'yi oluşturduğunuz her yerde.  
  
 Kullanmayın ...  
 kabuk bir tema güncelleştirmesi varsa otomatik olarak değiştirmek istemiyorum herhangi bir Kullanıcı Arabirimi için.  
  
 **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Otomatik&#45;gizleme sekmesi](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Varsayılan otomatik gizle sekmesi**|Arka plan|`Environment.AutoHideTabBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Otomatik&#45;gizleme sekmesi](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Varsayılan otomatik gizle sekmesi**|Ön Plan (Metin)|`Environment.AutoHideTabText`|  
|![Otomatik&#45;gizleme sekmesi](../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")<br /><br /> **Varsayılan otomatik gizle sekmesi**|Kenarlık|`Environment.AutoHideTabBorder`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Otomatik&#45;gover üzerinde sekme gizlemek](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Gezinme üzerinde otomatik gizleme sekmesi**|Arka plan|`Environment.AutoHideTabMouseOverBackgroundBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Otomatik&#45;gover üzerinde sekme gizlemek](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Gezinme üzerinde otomatik gizleme sekmesi**|Ön Plan (Metin)|`Environment.AutoHideTabMouseOverText`|  
|![Otomatik&#45;gover üzerinde sekme gizlemek](../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")<br /><br /> **Gezinme üzerinde otomatik gizleme sekmesi**|Kenarlık|`Environment.AutoHideTabMouseOverBorder`|  
  
### <a name="common-shared-controls"></a>Ortak paylaşılan denetimler  
 Özelliğinizde standart bir Visual Studio komut çubuğu kullandığınızda, stilize edilmiş kabuk denetimlerine erişebilirsiniz ve bu ortak denetimleri yeniden şablona almamalısınız. Ancak, özel bir komut çubuğu oluşturmanız gerekiyorsa, özel denetimler oluşturmanız da gerekebilir. Bu durumda, kullanıcı arabiriminizin Visual Studio'nun geri kalanıyla tutarlı olması için aşağıdaki denetimlerin her biri için doğru belirteç adlarını kullandığınızdan emin olun.  
  
#### <a name="search-box"></a>Arama kutusu  
 Mümkün olduğunda, Visual Studio ortamı tarafından sağlanan ortak arama denetimini kullanın. Arama kutusu renkleri, giriş alanı, eylem düğmesi, açılır açma düğmesi ve açılır menü için belirteç adlarını içeren **ShellColors.pkgdef** dosyasındaki "SearchControl" kategorisinde bulunur.  
  
 Arama kutusu, bazıları birbirini dışlayan birkaç eyaletten biri olabilir:  
  
- "Odaklanmış" veya "odaklanmamış", imlecin metin kutusunda olup olmadığını ifade eder.  
  
- "Etkin" veya "etkin olmayan" kullanıcının metin kutusuna bir arama sorgusu giriş yapıp etmediğini ifade eder.  
  
- "Hover", kullanıcının arama kutusunun üzerinde fareyle birlikte kullandığı anlamına gelir (bu durum diğer tüm durumları geçersiz kılar).  
  
- "Devre dışı" arama işlevinin geçerli bağlam için kapalı olduğu anlamına gelir.  
  
  ![Arama kutusu redline](../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  Kullanın...  
  özel bir arama kutusu tasarlarken.  
  
  Kullanmayın ...  
  - bir arama kutusu olmayan bir şey için.  
  
- her zaman arama kutusu Kullanıcı Arabirimi maç istemediğiniz bir şey için.  
  
  **Odaklı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Arama giriş alanı odaklı](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Giriş alanı**|Arka plan|`SearchControl.FocusedBackground`|  
|![Arama giriş alanı odaklı](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Giriş alanı**|Ön Plan (Metin)|`SearchControl.FocusedBackground`|  
|![Arama giriş alanı odaklı](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Giriş alanı**|Kenarlık|`SearchControl.FocusedBorder`|  
|![Arama giriş alanı odaklı](../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br /><br /> **Giriş alanı**|Ayırıcı|`SearchControl.FocusedDropDownSeparator`|  
|![Arama eylem düğmesi odaklı](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Eylem düğmesi**|Arka plan|None|  
|![Arama eylem düğmesi odaklı](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Eylem düğmesi**|Ön Plan (Arama glyph)|`SearchControl.SearchGlyph`|  
|![Arama eylem düğmesi odaklı](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Eylem düğmesi**|Ön plan (Glyph'yi durdur)|`SearchControl.StopGlyph`|  
|![Arama eylem düğmesi odaklı](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Eylem düğmesi**|Ön plan (Açık glyph)|`SearchControl.ClearGlyph`|  
|![Arama eylem düğmesi odaklı](../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br /><br /> **Eylem düğmesi**|Kenarlık|Yok|  
|![Arama bırakma&#45;aşağı düğmesi odaklanmış](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Açılır düğme**|Arka plan|`SearchControl.FocusedDropDownButton`|  
|![Arama bırakma&#45;aşağı düğmesi odaklanmış](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`SearchControl.FocusedDropDownButtonGlyph`|  
|![Arama bırakma&#45;aşağı düğmesi odaklanmış](../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br /><br /> **Açılır düğme**|Kenarlık|`SearchControl.FocusedDropDownButtonBorder`|  
  
 **Odaklanmamış**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Giriş alanını odaklanmadan arama](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Etkin giriş alanı**|Arka plan|`SearchControl.SearchActiveBackground`|  
|![Giriş alanını odaklanmadan arama](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Etkin giriş alanı**|Ön Plan (Metin)|`SearchControl.SearchActiveBackground`|  
|![Giriş alanını odaklanmadan arama](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Etkin giriş alanı**|Kenarlık|`SearchControl.UnfocusedBorder`|  
|![Giriş alanını odaklanmadan arama](../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br /><br /> **Etkin giriş alanı**|Ayırıcı|`SearchControl.DropDownSeparator`|  
|![Giriş alanını odaklanmamış ve etkin olmayan arama](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Etkin olmayan giriş alanı**|Arka plan|`SearchControl.Unfocused`|  
|![Giriş alanını odaklanmamış ve etkin olmayan arama](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Etkin olmayan giriş alanı**|Ön Plan (Metin)|`SearchControl.Unfocused`|  
|![Giriş alanını odaklanmamış ve etkin olmayan arama](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Etkin olmayan giriş alanı**|Kenarlık|`SearchControl.UnfocusedBorder`|  
|![Giriş alanını odaklanmamış ve etkin olmayan arama](../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br /><br /> **Etkin olmayan giriş alanı**|Ayırıcı|`SearchControl.DropDownSeparator`|  
|![Arama eylem düğmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Eylem düğmesi**|Arka plan|Yok|  
|![Arama eylem düğmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Eylem düğmesi**|Ön Plan (Arama glyph)|`SearchControl.SearchGlyph`|  
|![Arama eylem düğmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Eylem düğmesi**|Ön plan (Glyph'yi durdur)|`SearchControl.StopGlyph`|  
|![Arama eylem düğmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Eylem düğmesi**|Ön plan (Açık glyph)|`SearchControl.ClearGlyph`|  
|![Arama eylem düğmesi odaklanmamış](../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br /><br /> **Eylem düğmesi**|Kenarlık|Yok|  
|![Açılan&#45;aşağı düğmesine odaklanmadan arama](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Açılır düğme**|Arka plan|`SearchControl.UnfocusedDropDownButton`|  
|![Açılan&#45;aşağı düğmesine odaklanmadan arama](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`SearchControl.UnfocusedDropDownButtonGlyph`|  
|![Açılan&#45;aşağı düğmesine odaklanmadan arama](../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br /><br /> **Açılır düğme**|Kenarlık|`SearchControl.UnfocusedDropDownButtonBorder`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Arama eylem düğmesine basıldığında](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Eylem düğmesi**|Arka plan|`SearchControl.ActionButtonMouseDown`|  
|![Arama eylem düğmesine basıldığında](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Eylem düğmesi**|Ön Plan (Glyph)|`SearchControl.ActionButtonMouseDownGlyph`|  
|![Arama eylem düğmesine basıldığında](../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br /><br /> **Eylem düğmesi**|Kenarlık|`SearchControl.ActionButtonMouseDownBorder`|  
|![Arama bırak&#45;aşağı düğmesine basıldığında](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Açılır düğme**|Arka plan|`SearchControl.MouseDownDropDownButton`|  
|![Arama bırak&#45;aşağı düğmesine basıldığında](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`SearchControl.MouseDownDropDownButtonGlyph`|  
|![Arama bırak&#45;aşağı düğmesine basıldığında](../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br /><br /> **Açılır düğme**|Kenarlık|`SearchControl.MouseDownDropDownButtonBorder`|  
  
 **Vurgulanan (yalnızca Metin)**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Giriş alanı vurgusu](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Metin vurgulanmış giriş alanı**|Arka plan|`SearchControl.Selection`|  
|![Giriş alanı vurgusu](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Metin vurgulanmış giriş alanı**|Ön Plan (Metin)|`SearchControl.FocusedBackground`|  
|![Giriş alanı vurgusu](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Metin vurgulanmış giriş alanı**|Kenarlık|None|  
|![Giriş alanı vurgusu](../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br /><br /> **Metin vurgulanmış giriş alanı**|Ayırıcı|`SearchControl.FocusedDropDownSeparator`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Giriş alanını devre dışı arama](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Giriş alanı**|Arka plan|`SearchControl.Disabled`|  
|![Giriş alanını devre dışı arama](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Giriş alanı**|Ön Plan (Metin)|`SearchControl.Disabled`|  
|![Giriş alanını devre dışı arama](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Giriş alanı**|Kenarlık|`SearchControl.DisabledBorder`|  
|![Giriş alanını devre dışı arama](../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br /><br /> **Giriş alanı**|Ayırıcı|`SearchControl.DropDownSeparator`|  
|![Arama eylem düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Eylem düğmesi**|Arka plan|None|  
|![Arama eylem düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Eylem düğmesi**|Ön Plan (Glyph)|`SearchControl.ActionButtonDisabledGlyph`|  
|![Arama eylem düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br /><br /> **Eylem düğmesi**|Kenarlık|None|  
|![Arama bırak&#45;aşağı düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Açılır düğme**|Arka plan|None|  
|![Arama bırak&#45;aşağı düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Açılır düğme**|Ön Plan (Glyph)|`SearchControl.DisabledDownButtonGlyph`|  
|![Arama bırak&#45;aşağı düğmesi devre dışı](../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br /><br /> **Açılır düğme**|Kenarlık|None|  
  
##### <a name="search-drop-down-lists"></a>Açılan listelerde arama  
 Arama kutusu açılır menüsü Visual Studio'daki diğer açılır menülerden biraz daha karmaşık olma potansiyeline sahiptir. "Önerilen aramalar" ve "arama seçenekleri" bölümleri tek başına veya birlikte menüde görünebilir ve her biri ayrı ayrı renklenir. Bir satır, birlikte göründüklerinde bu iki bölümü de ayırır ve bir kenarlık açılır menüyü n için ilerler.  
  
 ![Redline&#45;arama bırak](../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
Kullanın...  
- özel bir arama açılır listesi oluştururken.  

- doğru liste bileşenleri için doğru belirteç adları.  

Kullanmayın ...  
- diğer bağlamlarda görünen açılır listeler için.  

- belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda.  
  
  **Varsayılan (başka durum yok)**  
  
|Öğe|Belirteç adı: Category.color|  
|-------------|--------------------------------|  
|Kenarlık|`SearchControl.PopupBorder`|  
|Ayırıcı|`SearchControl.PopupSectionHeaderSeparator`|  
|Gölge|`Environment.DropShadowBackground`|  
  
 **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Önerilen arama](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Önerilen aramalar**|Arka plan|`SearchControl.PopupItemsListBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Önerilen arama](../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")<br /><br /> **Önerilen aramalar**|Ön Plan (Metin)|`SearchControl.PopupItemText`|  
|![Arama onay kutusu](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Arama seçenekleri (onay kutusu)**|Arka plan|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Arama seçenekleri](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Arama seçenekleri (bağlantı)**|Arka plan|`SearchControl.PopupSectionBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Arama onay kutusu](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Arama seçenekleri (onay kutusu)**|Ön plan (Onay kutusu metni)|`SearchControl.PopupCheckboxText`|  
|![Arama seçenekleri](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Arama seçenekleri (bağlantı)**|Ön plan (Onay kutusu metni)|`SearchControl.PopupCheckboxText`|  
|![Arama onay kutusu](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Arama seçenekleri (onay kutusu)**|Ön plan (Bağlantı metni)|`SearchControl.PopupButtonText`|  
|![Arama seçenekleri](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Arama seçenekleri (bağlantı)**|Ön plan (Bağlantı metni)|`SearchControl.PopupButtonText`|  
|![Arama onay kutusu](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Arama seçenekleri (onay kutusu)**|Üstbilgi arka planı|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Arama seçenekleri](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Arama seçenekleri (bağlantı)**|Üstbilgi arka planı|`SearchControl.PopupSectionHeaderGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Arama onay kutusu](../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")<br /><br /> **Arama seçenekleri (onay kutusu)**|Ön plan (Üstbilgi metni)|`SearchControl.PopupSectionHeaderText`|  
|![Arama seçenekleri](../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")<br /><br /> **Arama seçenekleri (bağlantı)**|Ön plan (Üstbilgi metni)|`SearchControl.PopupSectionHeaderText`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Gezinme üzerinde önerilen arama](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Önerilen aramalar**|Arka plan|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Gezinme üzerinde önerilen arama](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Önerilen aramalar**|Ön Plan (Metin)|`SearchControl.PopupMouseOverItemText`|  
|![Gezinme üzerinde önerilen arama](../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br /><br /> **Önerilen aramalar**|Kenarlık|`SearchControl.PopupControlMouseOverBorder`|  
|![Havada arama onay kutusunu](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Önerilen aramalar (onay kutusu)**|Arka plan|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Gezinme üzerinde arama seçenekleri](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Arama seçenekleri**|Arka plan|`SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Havada arama onay kutusunu](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Önerilen aramalar (onay kutusu)**|Ön plan (Onay kutusu metni)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Gezinme üzerinde arama seçenekleri](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Arama seçenekleri**|Ön plan (Onay kutusu metni)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Havada arama onay kutusunu](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Önerilen aramalar (onay kutusu)**|Ön plan (Bağlantı metni)|`SearchControl.PopupButtonMouseDownText`|  
|![Gezinme üzerinde arama seçenekleri](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Arama seçenekleri**|Ön plan (Bağlantı metni)|`SearchControl.PopupButtonMouseDownText`|  
|![Havada arama onay kutusunu](../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br /><br /> **Önerilen aramalar (onay kutusu)**|Kenarlık|`SearchControl.PopupControlMouseOverBorder`|  
|![Gezinme üzerinde arama seçenekleri](../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")<br /><br /> **Arama seçenekleri**|Kenarlık|`SearchControl.PopupControlMouseOverBorder`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Önerilen arama basılı](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Önerilen aramalar (onay kutusu)**|Kutu arka planını denetleme|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Arama seçenekleri basılı](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Arama seçenekleri**|Kutu arka planını denetleme|`SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Önerilen arama basılı](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Önerilen aramalar (onay kutusu)**|Kutu arka planını denetleme|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Arama seçenekleri basılı](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Arama seçenekleri**|Kutu arka planını denetleme|`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Önerilen arama basılı](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Önerilen aramalar (onay kutusu)**|Ön plan (Onay kutusu metni)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Arama seçenekleri basılı](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Arama seçenekleri**|Ön plan (Onay kutusu metni)|`SearchControl.PopupCheckboxMouseDownText`|  
|![Önerilen arama basılı](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Önerilen aramalar (onay kutusu)**|Bağlantı arka planı|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Arama seçenekleri basılı](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Arama seçenekleri**|Bağlantı arka planı|`SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br /><br /> Modern temalı ui kullanılmaz iken, bu arka plan için degrade durakları ve değerleri vardır.|  
|![Önerilen arama basılı](../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br /><br /> **Önerilen aramalar (onay kutusu)**|Ön plan (Bağlantı metni)|`SearchControl.PopupButtonMouseDownText`|  
|![Arama seçenekleri basılı](../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")<br /><br /> **Arama seçenekleri**|Ön plan (Bağlantı metni)|`SearchControl.PopupButtonMouseDownText`|  
  
#### <a name="hyperlink"></a>Köprü  
 Köprü, ön plan/arka plan çifti olmayan bir denetimdir. Her durumda, koyu, gri ve beyaz arka planlarda doğru görünecek ön plan köprü rengini kullanın. Köprü denetimi için renk belirteci kullanmazsanız, kırmızı yanıp sönen "pressed" için varsayılan sistem rengini görürsünüz. Bu, denetimin doğru ortam renk belirteci kullanmadığının sinyalidir.  
  
 ![Köprü kırmızısı](../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 Kullanın...  
 özel bir köprü oluşturmanız gerektiğinde.  
  
 Kullanmayın ...  
 köprü olmayan herhangi bir şey için.  
  
 **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Köprü varsayılanı](../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")|Ön Plan (Metin)|`Environment.PanelHyperlink`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hover üzerinde Köprü](../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")|Ön Plan (Metin)|`Environment.PanelHyperlinkHover`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Köprü basıldığında](../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")|Ön Plan (Metin)|`Environment.PanelHyperlinkPressed`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Köprü devre dışı](../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")|Ön Plan (Metin)|`Environment.PanelHyperlinkDisabled`|  
  
#### <a name="infobar"></a>Bilgi Çubuğu  
 Bilgi çubukları belirli bir bağlam hakkında daha fazla bilgi sağlamak için kullanılır ve her zaman bir belge penceresinin veya araç penceresinin üst kısmında görünür.  
  
 ![Bilgi çubuğu redline](../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 Kullanın...  
 özel bilgi çubukları oluştururken.  
  
 Kullanmayın ...  
 bilgi çubuğuna benzemeyen UI öğeleri için.  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Bilgi Çubuğu](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Bilgi Çubuğu**|Arka plan|`Environment.InfoBackground`|  
|![Bilgi Çubuğu](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Bilgi Çubuğu**|Ön Plan (Metin)|`Environment.InfoText`|  
|![Bilgi Çubuğu](../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")<br /><br /> **Bilgi Çubuğu**|Kenarlık|`Environment.ToolWindowBorder`|  
  
#### <a name="scroll-bar"></a>Kaydırma çubuğu  
 Kaydırma çubukları Visual Studio ortamı tarafından şekillendirilir ve temalı olması gerekmez. Ancak, kullanıcı bilgilerinizin Visual Studio ortamının bu bölümüyle tutarlı görünmesi için kaydırma çubuklarında kullanılan renklerden yararlanmak istediğinize karar verebilirsiniz.  
  
 ![Kaydırma çubuğu redline](../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 Kullanın...  
 Visual Studio kaydırma çubuklarıyla eşleştirmek istediğiniz uI oluştururken.  
  
 Kullanmayın ...  
 her zaman scrollbar UI eşleştirmek istemiyorum şey için.  
  
 **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Kaydırma çubuğu](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Scrollbar|`Environment.ScrollBarBackground`|  
|![Kaydırma çubuğu](../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")<br /><br /> **Scrollbar**|Ön Plan (Başparmak)|`Environment.ScrollBarThumbBackground`|  
|![Çubuk oku kaydırma](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Kaydırma oku**|Arka plan|`Environment.ScrollBarArrowBackground`<br /><br /> Kaydırma çubuğuyla aynı renge ayarlayın.|  
|![Çubuk oku kaydırma](../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")<br /><br /> **Kaydırma oku**|Ön Plan (Glyph)|`Environment.ScrollBarArrowGlyph`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Gezinme çubuğu](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Scrollbar|`Environment.ScrollBarBackground`|  
|![Gezinme çubuğu](../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")<br /><br /> **Scrollbar**|Ön Plan (Başparmak)|`Environment.ScrollBarThumbMouseOverBackground`|  
|![Gezinme üzerinde çubuk oku kaydırma](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Kaydırma oku**|Arka plan|`Environment.ScrollBarArrowMouseOverBackground`<br /><br /> Kaydırma çubuğuyla aynı renge ayarlayın.|  
|![Gezinme üzerinde çubuk oku kaydırma](../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br /><br /> **Kaydırma oku**|Ön Plan (Glyph)|`Environment.ScrollBarArrowGlyphMouseOver`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Kaydırma çubuğu basılı](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Scrollbar|`Environment.ScrollBarBackground`|  
|![Kaydırma çubuğu basılı](../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")<br /><br /> **Scrollbar**|Ön Plan (Başparmak)|`Environment.ScrollBarThumbPressedBackground`|  
|![Çubuk okunu kaydır](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Kaydırma oku**|Arka plan|`Environment.ScrollBarArrowPressedBackground`<br /><br /> Kaydırma çubuğuyla aynı renge ayarlayın.|  
|![Çubuk okunu kaydır](../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br /><br /> **Kaydırma oku**|Ön Plan (Glyph)|`Environment.ScrollBarArrowGlyphPressed`|  
  
#### <a name="tree-view"></a><a name="BKMK_TreeView"></a>Ağaç görünümü  
 Çözüm Gezgini, Sunucu Gezgini ve Sınıf Görünümü de dahil olmak üzere çeşitli araç pencereleri, renkleri TreeView kategorisinderenk adlarıyla denetlenen hiyerarşik bir kuruluş düzeni uygular. Ağaç görünümündeki tüm öğelerin arka planı ve metin renkleri vardır. İç içe alt öğeleri olan öğeler, öğenin genişletilip genişletilmediğini veya daraltılıp yıkılmadığını gösteren gliflere de sahiptir.  
  
 ![Ağaç görünümü redline](../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 Kullanın...  
 hiyerarşik bir örgütsel görünüm uygulamak için gereken her yerde.  
  
Kullanmayın ...  
- bir ağaç görünümüne benzemeyen herhangi bir şey için.  

- belirtilenler dışında herhangi bir arka plan/ön plan kombinasyonunda.  
  
  **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ağaç görünümü](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Arka plan|`TreeView.Background`|  
|![Ağaç görünümü](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Ön Plan (Metin)|`TreeView.Background`|  
|![Ağaç görünümü](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Ön Plan (Glyph)|`TreeView.Glyph`|  
|![Ağaç görünümü](../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")|Kenarlık|None|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hover üzerinde ağaç görünümü](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Arka plan|`TreeView.Background`|  
|![Hover üzerinde ağaç görünümü](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Ön Plan (Metin)|`TreeView.Background`|  
|![Hover üzerinde ağaç görünümü](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Ön Plan (Glyph)|`TreeView.GlyphMouseOver`|  
|![Hover üzerinde ağaç görünümü](../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")|Kenarlık|None|  
  
 **Sürükle**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ağaç görünümü sürükleme](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Arka plan|`TreeView.DragOverItem`|  
|![Ağaç görünümü sürükleme](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Ön Plan (Metin)|`TreeView.DragOverItem`|  
|![Ağaç görünümü sürükleme](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Ön Plan (Glyph)|`TreeView.DragOverItemGlyph`|  
|![Ağaç görünümü sürükleme](../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")|Kenarlık|None|  
  
 **Seçildi**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ağaç görünümü odaklı](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Odaklı**|Arka plan|`TreeView.SelectedItemActive`|  
|![Ağaç görünümü odaklı](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Odaklı**|Ön Plan (Metin)|`TreeView.SelectedItemActive`|  
|![Ağaç görünümü odaklı](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Odaklı**|Ön Plan (Glyph)|`TreeView.SelectedItemActiveGlyph`|  
|![Ağaç görünümü odaklı](../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")<br /><br /> **Odaklı**|Kenarlık|`TreeView.FocusVisualBorder`|  
|![Ağaç görünümü odaklanmamış](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Odaklanmamış**|Arka plan|`TreeView.SelectedItemInactive`|  
|![Ağaç görünümü odaklanmamış](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Odaklanmamış**|Ön Plan (Metin)|`TreeView.SelectedItemInactive`|  
|![Ağaç görünümü odaklanmamış](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Odaklanmamış**|Ön Plan (Glyph)|`TreeView.SelectedItemInactiveGlyph`|  
|![Ağaç görünümü odaklanmamış](../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")<br /><br /> **Odaklanmamış**|Kenarlık|None|  
  
 **Seçili üzerinde gezinme**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Ağaç görünümü hover odaklanmış](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Odaklı**|Arka plan|`TreeView.SelectedItemActive`|  
|![Ağaç görünümü hover odaklanmış](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Odaklı**|Ön Plan (Metin)|`TreeView.SelectedItemActive`|  
|![Ağaç görünümü hover odaklanmış](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Odaklı**|Ön Plan (Glyph)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Ağaç görünümü hover odaklanmış](../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br /><br /> **Odaklı**|Kenarlık|Hiçbiri`TreeView.FocusVisualBorder`|  
|![Ağaç görünümü gezinmeye odaklanmamış](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Odaklanmamış**|Arka plan|`TreeView.SelectedItemInactive`|  
|![Ağaç görünümü gezinmeye odaklanmamış](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Odaklanmamış**|Ön Plan (Metin)|`TreeView.SelectedItemInactive`|  
|![Ağaç görünümü gezinmeye odaklanmamış](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Odaklanmamış**|Ön Plan (Glyph)|`TreeView.SelectedItemActiveGlyphMouseOver`|  
|![Ağaç görünümü gezinmeye odaklanmamış](../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br /><br /> **Odaklanmamış**|Kenarlık|None|  
  
#### <a name="button-controls"></a>Düğme denetimleri  
 ![Düğme denetimi redline](../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 Kullanın...  
 Visual Studio temaları (Açık, Koyu, Mavi veya bir sistem Yüksek Kontrast teması) ile entegre etmek istediğiniz belgedeki düğmeler için iyi.  
  
 Kullanmayın ...  
 Visual Studio temasının bir parçası olmayan özel bir arka plana karşı görüntülenecek düğmeler için.  
  
 **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Düğme](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Düğme|`CommonControls.Button`|  
|![Düğme](../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")|Düğme kenarlığı|`CommonControls.ButtonBorder`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Düğme devre dışı](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Düğme|`CommonControls.ButtonDisabled`|  
|![Düğme devre dışı](../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")|Düğme kenarlığı|`CommonControls.ButtonBorderDisabled`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hover üzerinde düğme](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Düğme|`CommonControls.ButtonHover`|  
|![Hover üzerinde düğme](../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")|Düğme kenarlığı|`CommonControls.ButtonBorderHover`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Düğmeye basıldı](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Düğme|`CommonControls.ButtonPressed`|  
|![Düğmeye basıldı](../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")|Düğme kenarlığı|`CommonControls.ButtonBorderPressed`|  
  
 **Odaklı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Düğme odaklı](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Düğme|`CommonControls.ButtonFocused`|  
|![Düğme odaklı](../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")|Düğme kenarlığı|`CommonControls.ButtonBorderFocused`|  
  
#### <a name="check-box-controls"></a>Kutu denetimlerini denetleme  
 ![Onay kutusu redline](../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 Kullanın...  
 belgenin içinde bulunan onay kutusu denetimleri için iyi.  
  
 Kullanmayın ...  
 bir onay kutusu denetimi olmayan herhangi bir UI için.  
  
 **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Onay kutusu](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Arka plan|`CommonControls.CheckBoxBackground`|  
|![Onay kutusu](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Kenarlık|`CommonControls.CheckBoxBorder`|  
|![Onay kutusu](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Metin|`CommonControls.CheckBoxText`|  
|![Onay kutusu](../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")|Glif|`CommonControls.CheckBoxGlyph`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Onay kutusu devre dışı](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Arka plan|`CommonControls.CheckBoxBackgroundDisabled`|  
|![Onay kutusu devre dışı](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Kenarlık|`CommonControls.CheckBoxBorderDisabled`|  
|![Onay kutusu devre dışı](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Metin|`CommonControls.CheckBoxTextDisabled`|  
|![Onay kutusu devre dışı](../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")|Glif|`CommonControls.CheckBoxGlyphDisabled`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hover üzerinde onay kutusu](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Arka plan|`CommonControls.CheckBoxBackgroundHover`|  
|![Hover üzerinde onay kutusu](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Kenarlık|`CommonControls.CheckBoxBorderHover`|  
|![Hover üzerinde onay kutusu](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Metin|`CommonControls.CheckBoxTextHover`|  
|![Hover üzerinde onay kutusu](../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")|Glif|`CommonControls.CheckBoxGlyphHover`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Onay kutusuna basıldığında](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Arka plan|`CommonControls.CheckBoxBackgroundPressed`|  
|![Onay kutusuna basıldığında](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Kenarlık|`CommonControls.CheckBoxBorderPressed`|  
|![Onay kutusuna basıldığında](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Metin|`CommonControls.CheckBoxTextPressed`|  
|![Onay kutusuna basıldığında](../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")|Glif|`CommonControls.CheckBoxGlyphPressed`|  
  
 **Odaklı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Onay kutusu odaklı](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Arka plan|`CommonControls.CheckBoxBackgroundFocused`|  
|![Onay kutusu odaklı](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Kenarlık|`CommonControls.CheckBoxBorderFocused`|  
|![Onay kutusu odaklı](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Metin|`CommonControls.CheckBoxTextFocused`|  
|![Onay kutusu odaklı](../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")|Glif|`CommonControls.CheckBoxGlyphFocused`|  
  
#### <a name="drop-boxcombo-box-controls"></a>Açılan kutu/açılan kutu denetimleri  
 ![açılan kutu redline&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
Kullanın...  
iyi belgenin bir parçası olan açılır ve açılan kutular için.  

Kullanmayın ...  
- bir açılır veya açılan kutu olmayan herhangi bir UI için.  

- komut çubuğundaki [açılır](../misc/shared-colors.md#BKMK_CommandDropDown) veya [Açılan kutu](../misc/shared-colors.md#BKMK_CommandComboBox) için.  
  
  **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![açılan kutuyu&#45;&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Arka plan|`CommonControls.ComboBoxBackground`|  
|![açılan kutuyu&#45;&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Kenarlık|`CommonControls.ComboBoxBorder`|  
|![açılan kutuyu&#45;&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Metin|`CommonControls.ComboBoxText`|  
|![açılan kutuyu&#45;&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Ayırıcı|`CommonControls.ComboBoxSeparator`|  
|![açılan kutuyu&#45;&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Glif|`CommonControls.ComboBoxGlyph`|  
|![açılan kutuyu&#45;&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")|Glyph arka plan|`CommonControls.ComboBoxGlyphBackground`|  
  
 **Devre dışı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;açılan kutudevre&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Arka plan|`CommonControls.ComboBoxBackgroundDisabled`|  
|![&#45;açılan kutudevre&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Kenarlık|`CommonControls.ComboBoxBorderDisabled`|  
|![&#45;açılan kutudevre&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Metin|`CommonControls.ComboBoxTextDisabled`|  
|![&#45;açılan kutudevre&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Ayırıcı|`CommonControls.ComboBoxSeparatorDisabled`|  
|![&#45;açılan kutudevre&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Glif|`CommonControls.ComboBoxGlyphDisabled`|  
|![&#45;açılan kutudevre&#47;aşağı bırak](../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")|Glyph arka plan|`CommonControls.ComboBoxGlyphBackgroundDisabled`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![&#45;'ı&#47;açılan kutuyu aşağı indirin](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Arka plan|`CommonControls.ComboBoxBackgroundHover`|  
|![&#45;'ı&#47;açılan kutuyu aşağı indirin](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Kenarlık|`CommonControls.ComboBoxBorderHover`|  
|![&#45;'ı&#47;açılan kutuyu aşağı indirin](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Metin|`CommonControls.ComboBoxTextHover`|  
|![&#45;'ı&#47;açılan kutuyu aşağı indirin](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Ayırıcı|`CommonControls.ComboBoxSeparatorHover`|  
|![&#45;'ı&#47;açılan kutuyu aşağı indirin](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Glif|`CommonControls.ComboBoxGlyphHover`|  
|![&#45;'ı&#47;açılan kutuyu aşağı indirin](../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")|Glyph arka plan|`CommonControls.ComboBoxGlyphBackgroundHover`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Açılan kutu basılı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Arka plan|`CommonControls.ComboBoxBackgroundPressed`|  
|![Açılan kutu basılı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Kenarlık|`CommonControls.ComboBoxBorderPressed`|  
|![Açılan kutu basılı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Metin|`CommonControls.ComboBoxTextPressed`|  
|![Açılan kutu basılı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Ayırıcı|`CommonControls.ComboBoxSeparatorPressed`|  
|![Açılan kutu basılı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Glif|`CommonControls.ComboBoxGlyphPressed`|  
|![Açılan kutu basılı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")|Glyph arka plan|`CommonControls.ComboBoxGlyphBackgroundPressed`|  
  
 **Odaklı**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Açılan kutu odaklı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Arka plan|`CommonControls.ComboBoxBackgroundFocused`|  
|![Açılan kutu odaklı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Kenarlık|`CommonControls.ComboBoxBorderFocused`|  
|![Açılan kutu odaklı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Metin|`CommonControls.ComboBoxTextFocused`|  
|![Açılan kutu odaklı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Ayırıcı|`CommonControls.ComboBoxSeparatorFocused`|  
|![Açılan kutu odaklı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Glif|`CommonControls.ComboBoxGlyphFocused`|  
|![Açılan kutu odaklı&#47;aşağı&#45;bırak](../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")|Glyph arka plan|`CommonControls.ComboBoxGlyphBackgroundFocused`|  
  
 **Metin giriş seçimi**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![açılan kutu metin girişi&#47;&#45;aşağı bırakma](../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")|Vurgula|`CommonControls.ComboBoxTextInputSelection`|  
  
 **Basılı – Liste öğesi görünümü**  
  
|Bileşen|Öğe|Belirteç adı: Color.category|  
|---------------|-------------|--------------------------------|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Arka plan|`CommonControls.ComboBoxListBackground`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Arka plan|`CommonControls.ComboBoxListBackgroundHover`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Arka plan|`CommonControls.ComboBoxListItemBackgroundPressed`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Arka plan|`CommonControls.ComboBoxListItemBackgroundFocused`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Kenarlık|`CommonControls.ComboBoxListBorder`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Kenarlık|`CommonControls.ComboBoxListBorderHover`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Kenarlık|`CommonControls.ComboBoxListBorderPressed`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Kenarlık|`CommonControls.ComboBoxListBorderFocused`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Öğe metni|`CommonControls.ComboBoxListItemText`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Öğe metni|`CommonControls.ComboBoxListItemTextHover`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Öğe metni|`CommonControls.ComboBoxListItemTextPressed`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Öğe metni|`CommonControls.ComboBoxListItemTextFocused`|  
|![açılan&#47;kutu listesi görünümünü&#45;aşağı bırak](../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")|Arka plan gölgesi|`CommonControls.ComboBoxListBackgroundShadow`|  
  
#### <a name="tabular-data-grid-controls"></a>Tabular veri (ızgara) kontrolleri  
 Izgara denetimleri olarak da bilinen tabular veri denetimleri, Visual Studio için birden çok sütunda büyük miktarda veri sunmak için kullanılabilecek ortak denetimlerdir. Standart tabular veri denetimleri Visual Studio içinde birden çok yerde bulunabilir: Hata Listesi araç penceresi, IntelliTrace raporları ve bellek yığını görünümü, diğerleri arasında. Her zaman sağlanan standart tabular veri denetimlerini kullanın. Bazı nadir durumlarda, standart tabular veri denetimlerine erişiminiz olmayabilir. Bu gibi durumlarda, Kullanıcı Arabirimi'nizin Visual Studio'daki diğer tabular veri denetimleriyle tutarlı olduğundan emin olmak için aşağıdaki belirteç adlarını kullanın.  
  
 ![&#41; ızgara kontrolü &#40;tabular veri](../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 Kullanın...  
 tabular veya ızgara kontrolleri için.  
  
 Kullanmayın ...  
 bir tabular veya ızgara denetimi olmayan herhangi bir UI için.  
  
##### <a name="column-headers"></a>Sütun başlıkları  
 Sütun üstbilgileri bir arka plan, kenarlık, başlık metni ve genellikle bir ızgara bu sütuna göre sıralandığında kullanılan isteğe bağlı bir glyph oluşur.  
  
|Durum|Öğe|Belirteç adı: Category.color|  
|-----------|-------------|--------------------------------|  
|Varsayılan|Arka plan|`Header.Default`|  
|Varsayılan|Ön Plan (Metin)|`Environment.CommandBarTextActive`|  
|Varsayılan|Ön Plan (Glyph)|`Header.Glyph`|  
|Varsayılan|Kenarlık|`Header.SeparatorLine`|  
|Hover|Arka plan|`Header.MouseOver`|  
|Hover|Ön Plan (Metin)|`Environment.CommandBarTextHover`|  
|Hover|Ön Plan (Glyph)|`Header.MouseOverGlyph`|  
|Hover|Kenarlık|`Header.SeparatorLine`|  
|Pressed|Arka plan|`CommonControls.CheckBoxBackgroundPressed`|  
|Pressed|Ön Plan (Metin)|`CommonControls.CheckBoxBorderPressed`|  
|Pressed|Ön Plan (Glyph)|`CommonControls.CheckBoxTextPressed`|  
|Pressed|Kenarlık|`CommonControls.CheckBoxGlyphPressed`|  
  
##### <a name="list-view-items"></a>Liste görünümü öğeleri  
 Liste görünümü öğeleri arka plan ve içerikten oluşur. İçerik metin, simge veya her ikisi olabilir.  
  
|Durum|Öğe|Belirteç adı: Category.color|  
|-----------|-------------|--------------------------------|  
|Varsayılan|Arka plan|Geçirgen|  
|Varsayılan|Ön Plan (Metin)|`Environment.CommandBarTextActive`|  
|Varsayılan|Kenarlık|None|  
|Seçili (etkin)|Arka plan|`TreeView.SelectedItemActive`|  
|Seçili (etkin)|Ön Plan (Metin)|`TreeView.SelectedItemActiveText`|  
|Seçili (etkin)|Kenarlık|None|  
|Seçili (etkin olmayan)|Arka plan|`TreeView.SelectedItemInactive`|  
|Seçili (etkin olmayan)|Ön Plan (Metin)|`TreeView.SelectedItemInactiveText`|  
|Seçili (etkin olmayan)|Kenarlık|None|  
  
### <a name="manifest-designer"></a>Bildirim Tasarımcısı  
 Manifest Designer, Windows 8 ve Windows Phone 8 projelerinde manifesto dosyasını daha kolay bir şekilde yeniden yapılandırın. Tüketim için kullanılabilir paylaşılan bir çerçeve olmamasına gerek yok, ancak yön/gezinti sekmelerinin tasarım düzeni ve renkleri yle ve genel yapıyla eşleşmeniz uygun olabilir. Düzen ayrıntıları hakkında daha fazla bilgi için [Visual Studio için Düzen'e](../extensibility/ux-guidelines/layout-for-visual-studio.md)bakın.  
  
 ![Manifest Tasarımcı redline](../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
Kullanın...  
- Manifest Designer benzer tasarımcılar için.  

- belge içinde bir düzenleyicinin üst kısmında ortak sekme denetimleri kullanarak yerine iyi.  

Kullanmayın ...  
- altıdan fazla sekmeniz varsa.  

- Manifest Designer gibi yapılandırılan herhangi bir UI için.  
  
|Durum|Bileşen|Öğe|Belirteç adı: Category.color|  
|-----------|---------------|-------------|--------------------------------|  
|Varsayılan (seçili)|Tab|Arka plan|`ManifestDesigner.TabActive`|  
|Varsayılan (seçili)|Tab|Kenarlık|None|  
|Varsayılan (seçili)|Açıklama bölmesi|Arka plan|`ManifestDesigner.DescriptionPane`|  
|Varsayılan (seçili)|İçerik sayfası|Arka plan|`ManifestDesigner.Background`|  
|Varsayılan (seçili)|İçerik sayfası|İletişim yardımcı metni|`ManifestDesigner.WatermarkText`<br /><br /> Bu belirteç adı işleviyle eşleşmiyor.|  
|Seçilmemiş|Tab|Arka plan|`ManifestDesigner.Tab.Inactive`|  
|Hover|Tab|Arka plan|`ManifestDesigner.Tab.Mouseover`|  
  
### <a name="tagging"></a>Etiketleme  
 Visual Studio etiketlemeyi destekler, bu da kullanıcının izleme amacıyla aranabilir anahtar kelimeleri beyan etmesine olanak tanır. Örneğin, proje yöneticileri ve geliştiriciler iş öğelerini etiketlemek için Team Foundation Server'ı (TFS) kullanabilir. Aşağıdaki tablolar, hem etiketin kendisi hem de gezinme ve seçili durumlarda görünen "yakın simge" glyph için renk adları verir.  
  
 ![Redline etiketleme](../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 Kullanın...  
 etiketlemeyi destekleyen UI için.  
  
 Kullanmayın ...  
 ui başka bir tür için.  
  
#### <a name="tag"></a>Etiket  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Etiket](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Varsayılan**|Arka plan|`Tag.Background`|  
|![Etiket](../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")<br /><br /> **Varsayılan**|Ön Plan (Metin)|`Tag.Background`|  
|![Hover etiketi](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Hover**|Arka plan|`Tag.HoverBackground`|  
|![Hover etiketi](../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")<br /><br /> **Hover**|Ön Plan (Metin)|`Tag.HoverBackgroundText`|  
|![Etiket basılı](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Pressed**|Arka plan|`Tag.PressedBackground`|  
|![Etiket basılı](../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")<br /><br /> **Pressed**|Ön Plan (Metin)|`Tag.PressedBackgroundText`|  
|![Etiket seçili](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Seçildi**|Arka plan|`Tag.SelectedBackground`|  
|![Etiket seçili](../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")<br /><br /> **Seçildi**|Ön Plan (Metin)|`Tag.SelectedBackgroundText`|  
  
#### <a name="glyph-close-icon"></a>Glyph (yakın simge)  
 **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag &#40;glyph&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Varsayılan (etiket varsayılanı)**|Arka plan|Yok|  
|![Tag &#40;glyph&#41;](../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")<br /><br /> **Varsayılan (etiket varsayılanı)**|Ön Plan (Glyph)|`Tag.TagHoverGlyph`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag &#40;glyph&#41; üzerinde hover](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Hover (etiket varsayılan)**|Arka plan|`Tag.TagHoverGlyphHoverBackground`|  
|![Tag &#40;glyph&#41; üzerinde hover](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Hover (etiket varsayılan)**|Ön Plan (Glyph)|`Tag.TagHoverGlyphHover`|  
|![Tag &#40;glyph&#41; üzerinde hover](../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")<br /><br /> **Hover (etiket varsayılan)**|Kenarlık|`Tag.TagHoverGlyphHoverBorder`|  
  
 **Pressed**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Tag &#40;glyph&#41; basıldığında](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Basılı (etiket varsayılanı)**|Arka plan|`Tag.TagHoverGlyphPressedBackground`|  
|![Tag &#40;glyph&#41; basıldığında](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Basılı (etiket varsayılanı)**|Ön Plan (Glyph)|`Tag.TagHoverGlyphPressed`|  
|![Tag &#40;glyph&#41; basıldığında](../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")<br /><br /> **Basılı (etiket varsayılanı)**|Kenarlık|`Tag.TagHoverGlyphPressedBorder`|  
  
 **Seçili/glyph varsayılan etiketi**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Etiket seçili](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Varsayılan (etiket seçili)**|Arka plan|Yok|  
|![Etiket seçili](../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")<br /><br /> **Varsayılan (etiket seçili)**|Ön Plan (Glyph)|`Tag.TagSelectedGlyph`|  
  
 **Etiket seçili/glyph hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hover'da seçilen etiket](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hover (etiket seçili)**|Arka plan|`Tag.TagSelectedGlyphHoverBackground`|  
|![Hover'da seçilen etiket](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hover (etiket seçili)**|Ön Plan (Glyph)|`Tag.TagSelectedGlyphHover`|  
|![Hover'da seçilen etiket](../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")<br /><br /> **Hover (etiket seçili)**|Kenarlık|`Tag.TagSelectedGlyphHoverBorder`|  
  
 **Seçili/glyph basılı etiketi**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Seçili basılı etiketi](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Basılı (etiket seçili)**|Arka plan|`Tag.TagSelectedGlyphPressedBackground`|  
|![Seçili basılı etiketi](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Basılı (etiket seçili)**|Ön Plan(Glyph)|`Tag.TagSelectedGlyphPressed`|  
|![Seçili basılı etiketi](../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")<br /><br /> **Basılı (etiket seçili)**|Kenarlık|`Tag.TagSelectedGlyphPressedBorder`|  
  
### <a name="shell"></a>Kabuk  
  
#### <a name="background"></a>Arka plan  
 Ortam arka planı iki katmandan oluşur. Alt tabaka, tüm IDE'yi kapsayan düz bir renktir. Üst katman komut rafının altına ve IDE'nin sol ve sağ kenarlarındaki araç penceresi nin otomatik olarak gizlediği kanalların arasına sığar. Visual Studio 2013 itibariyle, üst ve alt arka plan katmanları Açık ve Koyu temalarda aynı renge ayarlanır.  
  
 ![Kabuk arka plan redline](../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 Kullanın...  
 Visual Studio ortamının arka planını eşleştirmek istediğiniz yerler için.  
  
Kullanmayın ...  
- arka plan yüzeyleri olmayan yerler için bir dolgu olarak.  

- ön plan öğeleri yerleştirmek istediğiniz bir arka plan olarak.  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|Alt katman|Arka plan|`Environment.EnvironmentBackground`|  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|Üst katman|Arka plan<br /><br /> *Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.*|`Environment.EnvironmentBackgroundGradientBegin`|  
|Üst katman|Arka plan<br /><br /> *Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.*|`Environment.EnvironmentBackgroundGradientEnd`|  
|Üst katman|Arka plan<br /><br /> *Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.*|`Environment.EnvironmentBackgroundGradientMiddle1`|  
|Üst katman|Arka plan<br /><br /> *Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.*|`Environment.EnvironmentBackgroundGradientMiddle2`|  
  
#### <a name="command-shelf"></a>Komut rafı  
 Komut rafı arka planlar için iki belirteç adı kümesi kullanılır: biri menü çubuğunun bulunduğu yer için bir küme, diğeri de komut çubuklarının oturduğu yer için. Tek bir komut çubuğu grubunun kendi arka plan renk değerleri vardır ve bu değerler "komut çubuğu" bölümünde daha ayrıntılı olarak tartışılır. Menü çubuğu ve komut çubuğu metni sırasıyla menü ve komut çubuğu bölümlerinde ele alınmıştır.  
  
 ![Komut raf redline](../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
Kullanın...  
- menüleri veya araç çubuklarını yerleştirdiğiniz alanlar için.  

- doğru arka plan / ön plan belirteç adı kombinasyonu ile.  
  
  Kullanmayın ...  
  komut rafına benzemeyen alanlar için.  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|Menü çubuğu|Arka plan<br /><br /> *Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.*|`Environment.CommandShelfHighlightGradientBegin`|  
|Menü çubuğu|Arka plan<br /><br /> *Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.*|`Environment.CommandShelfHighlightGradientMiddle`|  
|Menü çubuğu|Arka plan<br /><br /> *Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.*|`Environment.CommandShelfHighlightGradientEnd`|  
|Komut çubuğu|Arka plan<br /><br /> *Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.*|`Environment.CommandShelfBackgroundGradientBegin`|  
|Komut çubuğu|Arka plan<br /><br /> *Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.*|`Environment.CommandShelfBackgroundGradientMiddle`|  
|Komut çubuğu|Arka plan<br /><br /> *Visual Studio 2013 Işık ve Karanlık temalarında degrade durakları aynı renk değerine ayarlanmıştır.*|`Environment.CommandShelfBackgroundGradientEnd`|  
  
### <a name="toolbox"></a>Araç Kutusu  
 Araç kutusu, Visual Studio'da en sık kullanılan ortak araç pencerelerinden biridir. Aslında özel bir tema ve stil uygulanan bir ağaç kontrolüdür.  
  
 ![Araç kutusu redline](../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 Kullanın...  
 her zaman kabuk araç kutusu ile tutarlı olmak istediğiniz bir araç penceresi tasarlarken.  
  
 Kullanmayın ...  
 araç kutusu ui benzer olmayan bir şey için, ya da kabuk araç kutusu renkleri değişirse ui sorun olup olmayacağından emin değilseniz.  
  
 **Varsayılan**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç kutusu üst düğümü](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Üst düğüm**|Arka plan|`Environment.ToolboxContent`<br /><br /> Başlıklar<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Kullanılabilir denetim yoksa tek tek öğeler veya pencerenin tamamı|  
|![Araç kutusu alt düğümü](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Alt düğüm**|Arka plan|`Environment.ToolboxContent`<br /><br /> Başlıklar<br /><br /> `Environment.ToolWindowBackground`<br /><br /> Kullanılabilir denetim yoksa tek tek öğeler veya pencerenin tamamı|  
|![Araç kutusu üst düğümü](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Üst düğüm**|Kenarlık|None|  
|![Araç kutusu alt düğümü](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Alt düğüm**|Kenarlık|None|  
|![Araç kutusu üst düğümü](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Üst düğüm**|Ön Plan (Glyph)|`Environment.ToolboxContent`|  
|![Araç kutusu alt düğümü](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Alt düğüm**|Ön Plan (Glyph)|`Environment.ToolboxContent`|  
|![Araç kutusu üst düğümü](../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")<br /><br /> **Üst düğüm**|Ön Plan (Metin)|`Environment.ToolboxContent`|  
|![Araç kutusu alt düğümü](../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")<br /><br /> **Alt düğüm**|Ön Plan (Metin)|`Environment.ToolboxContent`|  
  
 **Hover**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Hover üzerinde araç kutusu alt düğüm](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Araç kutusu çocuk düğümünde gezinme**|Arka plan|`Environment.ToolboxContentMouseOver`<br /><br /> Yalnızca tek tek öğeler|  
|![Hover üzerinde araç kutusu alt düğüm](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Araç kutusu çocuk düğümünde gezinme**|Kenarlık|None|  
|![Hover üzerinde araç kutusu alt düğüm](../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br /><br /> **Araç kutusu çocuk düğümünde gezinme**|Ön Plan (Metin)|`Environment.ToolboxContentMouseOver`<br /><br /> Yalnızca tek tek öğeler|  
  
 **Seçildi**  
  
|Bileşen|Öğe|Belirteç adı: Category.color|  
|---------------|-------------|--------------------------------|  
|![Araç kutusu üst düğüm odaklı](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Odaklanmış üst düğüm**|Arka plan|`TreeView.SelectedItemActive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu alt düğüm odaklı](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Odaklanmış alt düğüm**|Arka plan|`TreeView.SelectedItemActive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu üst düğüm odaklı](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Odaklanmış üst düğüm**|Kenarlık|`TreeView.FocusVisualBorder`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu alt düğüm odaklı](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Odaklanmış alt düğüm**|Kenarlık|`TreeView.FocusVisualBorder`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu üst düğüm odaklı](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Odaklanmış üst düğüm**|Ön Plan (Glyph)|`TreeView.SelectedItemActive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu alt düğüm odaklı](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Odaklanmış alt düğüm**|Ön Plan (Glyph)|`TreeView.SelectedItemActive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu üst düğüm odaklı](../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br /><br /> **Odaklanmış üst düğüm**|Ön Plan (Metin)|`TreeView.SelectedItemActive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu alt düğüm odaklı](../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br /><br /> **Odaklanmış alt düğüm**|Ön Plan (Metin)|`TreeView.SelectedItemActive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu üst düğümü odaklanmamış](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Odaklanmamış üst düğüm**|Arka plan|`TreeView.SelectedItemInactive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu alt düğümü odaklanmamış](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Odaklanmamış alt düğüm**|Arka plan|`TreeView.SelectedItemInactive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu üst düğümü odaklanmamış](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Odaklanmamış üst düğüm**|Kenarlık|None|  
|![Araç kutusu alt düğümü odaklanmamış](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Odaklanmamış alt düğüm**|Kenarlık|None|  
|![Araç kutusu üst düğümü odaklanmamış](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Odaklanmamış üst düğüm**|Ön Plan (Glyph)|`TreeView.SelectedItemInactive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu alt düğümü odaklanmamış](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Odaklanmamış alt düğüm**|Ön Plan (Glyph)|`TreeView.SelectedItemInactive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu üst düğümü odaklanmamış](../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br /><br /> **Odaklanmamış üst düğüm**|Ön Plan (Metin)|`TreeView.SelectedItemInactive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
|![Araç kutusu alt düğümü odaklanmamış](../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br /><br /> **Odaklanmamış alt düğüm**|Ön Plan (Metin)|`TreeView.SelectedItemInactive`<br /><br /> [Ağaç görünümü](../misc/shared-colors.md#BKMK_TreeView) kategorisinden|  
  
## <a name="color-value-reference"></a>Renk değeri başvurusu  
  
|||||||||  
|-|-|-|-|-|-|-|-|  
|Bileşen|Bölüm|Öğe|Durum|Açık|Koyu|Mavi|Yüksek Kontrast|  
|Bölücü çizgileri|||Varsayılan|FFEEEEF2|FF2D2D30|FFEEEEF2|ControlDark|  
|Genişletici glyph||Ön plan|Varsayılan|||||  
|Genişletici glyph||Ön plan|Hover|||||  
|Genişletici glyph||Arka plan|Varsayılan|||||  
|Genişletici glyph||Arka plan|Hover|||||  
|Genişletici glyph||Kenarlık|Varsayılan|||||  
|Genişletici glyph||Kenarlık|Hover|||||