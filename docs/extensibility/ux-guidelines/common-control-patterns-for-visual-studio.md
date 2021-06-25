---
title: Genel Denetim Desenleri Visual Studio | Microsoft Docs
description: Yaygın denetimlerin windows Visual Studio yönergelerini nasıl takip eder ve bu yönergeleri geliştiren özel durumlar hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12d514bdc0aa37598ad57e0466bf57ba75ed2601
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899309"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio İçin Yaygın Denetim Desenleri
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Ortak denetimler

### <a name="overview"></a>Genel Bakış
Ortak denetimler, Visual Studio'da kullanıcı arabiriminin çoğunu Visual Studio. Visual Studio arabiriminde kullanılan en yaygın denetimlerin Windows Masaüstü etkileşim [yönergelerine uyması gerekir.](/windows/desktop/uxguide/controls) Bu konu, windows Visual Studio ve bu Windows yönergelerini geliştiren özel durumlar veya ayrıntıları kapsar.

#### <a name="common-controls-in-this-topic"></a>Bu konudaki yaygın denetimler

- [Kaydırma çubukları](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Giriş alanları](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Birleşik giriş kutuları ve açılan listeler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Onay kutuları](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Radyo düğmeleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Grup çerçeveleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Metin denetimleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Düğmeler ve köprüler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Ağaç görünümleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Görsel stili
Denetimlerin stil oluşturması için dikkate gereken ilk şey, denetimlerin themed ui'da kullanılamayacak olmasıdır. Standart kullanıcı arabiriminde denetimler, pencereli olmayan kullanıcı arabirimidir ve [normal Windows Masaüstü](/windows/desktop/uxguide/controls)stiline uyması gerekir; başka bir anlama gelir, bunlar yeniden şablonlanmaz ve varsayılan denetim görünümlerinde görünler.

- **Standart (yardımcı program) iletişim kutuları:** themed değil. Yeniden şablon oluşturma. Temel denetim stili varsayılanlarını kullanın.

- **Araç pencereleri, belge düzenleyicileri, tasarım yüzeyleri ve themed iletişim kutuları:** Renk hizmetini kullanarak özelleştirilmiş, themed görünümünü kullanın.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> Kaydırma çubukları
 Kaydırma çubukları, [kod düzenleyicisinde olduğu gibi](/windows/desktop/Controls/about-scroll-bars) içerik bilgileriyle artırılmış olmadıkça Windows kaydırma çubukları için yaygın etkileşim desenlerini izlemeli.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Giriş alanları
 Tipik etkileşim davranışı için, metin kutuları [için Windows Masaüstü yönergelerini izleyin.](/windows/desktop/uxguide/ctrl-text-boxes)

#### <a name="visual-style"></a>Görsel stili

- Giriş alanları yardımcı program iletişim kutusunda stile sahip olmaması gerekir. Denetimin temel stil iç stilini kullanın.

- Themed input fields be only be used in themed dialogs and tool windows.

#### <a name="specialized-interactions"></a>Özel etkileşimler

- Salt okunur alanlar gri (devre dışı) arka plana ancak varsayılan (etkin) ön plana sahip olur.

- Gerekli alanların içinde **\<Required>** filigranlar olması gerekir. Nadir durumlar dışında arka plan rengini değiştirmeyin.

- Hata doğrulama: [Bkz. Bildirim ve İlerleme Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Giriş alanları, gösterilen pencerenin genişliğine sığmayacak şekilde değil içeriğe sığacak şekilde boyutlandırılamayacak ve yol gibi uzun bir alanın uzunluğuyla rastgele eşleşmez. Uzunluk, kullanıcıya alanda izin verilen karakter sayısıyla ilgili sınırlamaların göstergesi olabilir.

     ![Yanlış giriş alanı uzunluğu: Adın bu kadar uzun olması pek olası değildir.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Yanlış giriş alanı uzunluğu: Adın bu kadar uzun olması pek olası değildir.

     ![Doğru giriş alanı uzunluğu: Giriş alanı beklenen içerik için makul bir genişliktir.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Doğru giriş alanı uzunluğu: Giriş alanı beklenen içerik için makul bir genişliktir.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Birleşik giriş kutuları ve açılan listeler
Tipik etkileşim davranışı için, açılan listeler [ve birleşik giriş kutuları için Windows Masaüstü yönergelerini izleyin.](/windows/desktop/uxguide/ctrl-drop)

#### <a name="visual-style"></a>Görsel stili

- Yardımcı program iletişim kutularında denetimi yeniden şablona ekleme. Denetimin temel stil iç stilini kullanın.

- Themed UI'de, birleşik giriş kutuları ve açılan listelerde denetimler için standart theming takip eder.

#### <a name="layout"></a>Layout
Birleşik giriş kutuları ve açılan liste, gösterilen pencerenin genişliğine sığmayacak şekilde boyutlandırılamayacak ve yol gibi uzun bir alanın uzunluğuyla rastgele eşleşmez.

![Yanlış: Açılan genişlik, görüntülenecek içerik için çok uzun.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Yanlış: Açılan genişlik, görüntülenecek içerik için çok uzun.

![Doğru: Açılan liste, çevirinin büyümesine izin verecek şekilde boyutlandır ancak gereksiz yere uzun değil.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Doğru: Açılan liste, çevirinin büyümesine izin verecek şekilde boyutlandır ancak gereksiz yere uzun değil.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Onay kutuları
Tipik etkileşim davranışı için, onay kutuları [için Windows Masaüstü yönergelerini izleyin.](/windows/desktop/uxguide/ctrl-check-boxes)

#### <a name="visual-style"></a>Görsel stili

- Yardımcı program iletişim kutularında denetimi yeniden şablona ekleme. Denetimin temel stil iç stilini kullanın.

- Themed UI'de onay kutuları, denetimler için standart theming'i takip eder.

#### <a name="specialized-interactions"></a>Özel etkileşimler

- Bir onay kutusuyla etkileşim hiçbir zaman bir iletişim kutusu açmalı veya başka bir alana gitmek zorunda değil.

- Onay kutularını ilk metin satırı taban çizgisiyle hizalar.

     ![Yanlış: Onay kutusu metnin üzerine ortalanmış.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Yanlış: Onay kutusu metnin üzerine ortalanmış.

     ![Doğru: Onay kutusu metnin ilk satırıyla hizalanır.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Doğru: Onay kutusu metnin ilk satırıyla hizalanır.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Radyo düğmeleri
Tipik etkileşim davranışı için, radyo düğmeleri [için Windows Masaüstü yönergelerini izleyin.](/windows/desktop/uxguide/ctrl-radio-buttons)

#### <a name="visual-style"></a>Görsel stili
Yardımcı program iletişim kutularında radyo düğmelerine stil uygulama. Denetimin temel stil iç stilini kullanın.

#### <a name="specialized-interactions"></a>Özel etkileşimler
Grup ayrımlarını sıkı bir düzende sürdürmeniz gerekdikçe, radyo seçimlerini kapsayan bir grup çerçevesi kullanmak gerekli değildir.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Grup çerçeveleri
Tipik etkileşim davranışı için, grup [çerçeveleri için Windows Masaüstü yönergelerini izleyin.](/windows/desktop/uxguide/ctrl-group-boxes)

#### <a name="visual-style"></a>Görsel stili
Yardımcı program iletişim kutularında grup çerçeveleri stiline sahip değildir. Denetimin temel stil iç stilini kullanın.

#### <a name="layout"></a>Layout

- Grup ayrımlarını sıkı bir düzende sürdürmeniz gerekdikçe, radyo seçimlerini kapsayan bir grup çerçevesi kullanmak gerekli değildir.

- Hiçbir zaman tek bir denetim için grup çerçevesi kullanma.

- Bazen grup çerçevesi kapsayıcısı yerine yatay bir kural kullanmak kabul edilebilir.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Metin denetimleri

### <a name="static-text-fields"></a>Statik metin alanları

Statik metin alanı salt okunur bilgiler sunar ve kullanıcı tarafından seçilenemz. Kullanıcının panoya kopyalamak istemesi gereken herhangi bir metin için bunu kullanmaktan kaçının. Ancak salt okunur statik metin, durum değişikliğini yansıtacak şekilde değişebilir. Aşağıdaki örnekte, Bilgi grubu altındaki Çıkış Adı statik metni, üzerindeki Kök Ad Alanı metin kutusunda yapılan değişiklikleri yansıtacak şekilde değişir.

Statik metin bilgilerini görüntülemenin iki yolu vardır.

Herhangi bir gruplama çakışması olduğunda statik metin bir iletişim kutusunda kendi başına olabilir. Bir kutunun fazladan satırlarının gerçekten gerekli olup olduğuna karar verin. Aşağıda gösterildiği gibi, bir grup satırı tarafından oluşturulan bir bölümün altındaki dizin yolunun görüntüsü örnek olarak verilmiştir:

![Metin denetimlerde statik metin bilgileri](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Metin denetimlerde statik metin bilgileri

Diğer gruplanmış alanların bulunduğu ve bilgilerin içermesi okunabilirliği yardımcı olur. Bir bölüm gizlenebilir veya gösterilirken **(Özellikler penceresi** açıklama bölmesinde olduğu gibi) ya da benzer kullanıcı arabirimiyle tutarlı olmak istediğiniz bir iletişim kutusunda statik metni bir kutunun içine ekleyin. Bu grup kutusu tek bir kural olmalı ve ile `ButtonShadow` renklendirilmiştir:

![Metinde statik Özellikler penceresi](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Metinde statik Özellikler penceresi

### <a name="read-only-text-box"></a>Salt okunur metin kutusu

Bu, kullanıcının alanın içindeki metni seçmesini sağlar ancak düzenlemesini sağlar. Bu metin kutuları, her zamanki 3-D keski ile kenarlıklı bir dolgu `ButtonShadow` ile birlikte.

Kullanıcı ilişkili bir denetimi değiştirerek onay kutusunu işaretle/işaretini kaldır ya da radyo düğmesini seçme/seçimini kaldır gibi bir metin kutusu etkin hale (düzenlenebilir) olabilir. Örneğin, aşağıda gösterilen **Araçlar &gt; Seçenekleri** sayfasında, **Varsayılanı** Kullan onay  kutusu işaretlenmezse Giriş Sayfası metin kutusu etkin hale gelir.

![Etkin olmayan ve etkin durumları gösteren salt okunur metin kutusu](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Etkin olmayan ve etkin durumları gösteren salt okunur metin kutusu

### <a name="using-text-in-dialogs"></a>İletişim kutularında metin kullanma

İletişim kutularında metin için önemli yönergeler:

- Metin kutuları, liste kutuları vethemed olmayan iletişim kutularında çerçeveler için etiketler bir fiil ile başlar, yalnızca ilk sözcükte ilk büyük harfe sahip olur ve iki nokta üst üste ile sona erer.

    > Masaüstleri olan iletişim kutularına metin denetimleri [Windows masaüstü UX](/windows/desktop/uxguide/top-violations) yönergelerini izler ve Yardım bağlantılarında soru işaretleri dışında noktalama işaretlerini sona erer.

- Onay kutuları ve seçenek düğmelerinin etiketleri bir fiil ile başlar, yalnızca ilk sözcükte bir ilk büyük harf ile başlar ve bitiş noktalama işaretleri yoktur.

- Düğmeler, menüler, menü öğeleri ve sekmeler için etiketler her sözcükte (başlık durumu) ilk büyük harfe sahiptir.

- Etiket terminolojisi diğer iletişim kutularına benzer etiketlerle tutarlı olmalıdır.

- Mümkünse, uygulama için geliştiriciye gitmeden önce bir yazıcının/düzenleyicinin metni yazması veya onaylaması gerekir.

- Sekmenin yeterli olduğu özel durumlar dışında tüm denetimlerin etiketleri olmalıdır.
Uygun olduğunda yardımcı metni kullanın.

### <a name="helper-text"></a>Yardımcı metni

Kullanıcının iletişim kutusunun amacını anlamanıza veya hangi eylemin içinde yer alacaklarını anlamanıza yardımcı olmak için iletişim kutularına dahil edilir. Yardımcı metinler yalnızca basit iletişim kutularının karmaşıklıklarını önlemek için gerektiğinde kullanılmalıdır. Yardımcı metnin iki varyasyonu iletişim kutusu ve filigrandır.

Yardımcı metinler için ortak konumları izleyin ve yeni alanların tanıtılmasında seçici olun. Yardımcı metinler için yaygın senaryolar:

- Karmaşık bir iletişim kutusuyla etkileşim kurma hakkında ek yön vermek için iletişim kutularına yardımcı metin.

- Hiçbir içeriğin neden görünür olmadığını açıklamak için boş araç pencere veya iletişim kutularına filigran metni.

- Açıklama bölmesinin alt kısmında olduğu gibi **Özellikler penceresi.**

- Kullanıcının çalışmaya başlamada hangi eylemi at gerektiğini açıklamak için boş bir düzenleyicide filigran metni.

### <a name="dialog-helper-text"></a>İletişim kutusu yardımcı metni

Kullanıcı deneyimi tasarımcısı, yardımcı metnin uygun olup olmadığını belirlemeye yardımcı olabilir. Tasarımcı hem yardımcı metnin hem de genel içeriğinin nerede görüntülendiğinden tanımlayabilir. Kullanıcı yardımı gerçek metni yazabilir/düzenleyebilir.

### <a name="watermarks"></a>Filigranlar

İletişim kutuları biraz farklı filigran yönergelerinden yararlanabilir. Birçok kullanıcı arabirimi öğesinin (etiketler, ipucu metni, düğmeler ve metin içeren diğer kapsayıcı denetimleri) yoğun olduğu bir iletişim kutusu görüne bilse de filigranlar koyu gri renkte daha iyi görünür (VSColor: `ButtonShadow` ). Genellikle bir filigran, beyaz arka plana sahip bir liste kutusu gibi bir denetim içinde görünür (VSColor: `Window` ).

- Metin koyu gri renkte görünür (VSColor: `ButtonShadow` ). Ancak, filigran orta gri veya diğer renkli (VSColor: ) arka planda görünüyorsa ve okunabilirliğiyle ilgili bir endişe varsa, siyah `ButtonFace` metinle (VSColor: ) `WindowText` gidin.

- Filigranlar orta veya sola doğru temiz olabilir. Hizalama kararları almada standart tasarım kuralları uygulama. Filigran arka planda seçilenemsizdir.

![Filigran metni örneği](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Filigran metni örneği

### <a name="context-specific-dynamic-text"></a>Bağlama özgü (dinamik) metin

Dinamik metin, iletişim kutusunda veya kullanıcı arabiriminde iki şekilde kullanılabilir: dinamik etiket olarak veya dinamik içerik olarak.

- Dinamik etiket: Dinamik metnin yaygın kullanımı, seçilen öğe için daha fazla bilgi sunan açıklayıcı panellerdedir. Örneğin, sağ bir kılavuzda görüntülenen bu öğelerin öğelerinin ve özelliklerinin listesini içeren bir iletişim kutusunda. Özellik kılavuzu etiketi dinamik olabilir, böylece sol tarafta bir öğe seçildiğinde, sağ tarafta yer alan kılavuzda ilgili öğeye ilişkin bilgiler görüntülenir.

- Dinamik metin: Bu şekilde genel bilgileri değil, belirli bilgileri görüntülemeniz gereken örneklerde yararlı olabilir, ancak aşırıya alınmamaları için dikkat gerekir.

Kullanıcıların bilgileri kopyalama olanağına sahip olması için dinamik metnin salt okunur metin alanında olması gerekir.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Düğmeler ve köprüler

### <a name="overview"></a>Genel Bakış
Düğmeler ve bağlantı denetimleri (köprüler), kullanım, ifade, boyutlandırma ve boşluk köprüleri ile ilgili temel [Windows Masaüstü](/windows/desktop/uxguide/ctrl-links) yönergelerini izlemeli.

### <a name="choosing-between-buttons-and-links"></a>Düğmeler ve bağlantılar arasında seçim
Eskiden eylemler için düğmeler kullanılmıştır ve köprüler gezinti için ayrılmıştır. Düğmeler her durumda kullanılabilir, ancak bazı durumlarda düğmelerin ve bağlantıların daha Visual Studio şekilde bağlantıların rolü genişletilmiştir.

Komut düğmelerinin ne zaman kullanımı gerekir:

- Birincil komutlar

- İkincil komut olsalar bile giriş toplamak veya seçim yapmak için kullanılan pencereleri görüntüleme

- Yıkıcı veya geri alınamaz eylemler

- Sihirbazlar ve sayfa akışları içindeki taahhüt düğmeleri

Araç pencerelerde komut düğmelerini veya etiket için ikiden fazla kelimeye ihtiyacınız varsa bu düğmelerden kaçının. Bağlantıların etiketleri daha uzun olabilir.

 Bağlantıların ne zaman kullanımı gerekir:

- Başka bir pencereye, belgeye veya web sayfasına gezinme

- Eylemin amacını açıklamak için daha uzun bir etiket veya kısa cümle gerektiren durumlar

- Eylemin yıkıcı veya geri alınamaz durumda olduğu şartıyla, bir düğmenin kullanıcı arabirimini zora sokan dar boşluklar

- Çok sayıda komutun bulunduğu durumlarda ikincil komutların vurgularını gerileme

#### <a name="examples"></a>Örnekler
![Durum iletisinin ardından InfoBar'da kullanılan komut bağlantıları](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Durum iletisinin ardından InfoBar'da kullanılan komut bağlantıları

![CodeLens açılan menüsünde kullanılan bağlantılar](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />CodeLens açılan menüsünde kullanılan bağlantılar

![Düğmelerin çok fazla dikkat çekmesi gereken ikincil komutlar için kullanılan bağlantılar](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Düğmelerin çok fazla dikkat çekmesi gereken ikincil komutlar için kullanılan bağlantılar

### <a name="common-buttons"></a>Ortak düğmeler

#### <a name="text"></a>Metin
Kullanıcı arabirimi metni ve [terminolojisinde yazma yönergelerini izleyin.](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)

#### <a name="visual-style"></a>Görsel stili

##### <a name="standard-unthemed"></a>Standart (themed)
Visual Studio düğmelerinin çoğu yardımcı program iletişim kutusunda görünür ve stile sahip değildir. İşletim sistemi tarafından dikte edilen düğmelerin standart görünümünü yansıtmaları gerekir.

##### <a name="themed"></a>Temalı
Bazı durumlarda düğmeler stilli kullanıcı arabiriminde kullanılabilir ve bu düğmelerin uygun şekilde stile sahip olması gerekir. Denetimler [hakkında bilgi](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) için bkz. İletişim kutuları.

### <a name="special-buttons"></a>Özel düğmeler

#### <a name="browse-buttons"></a>Gözat... Düğme
**[Gözat...]** düğmeleri kılavuzlarda, iletişim kutularında ve araç pencerelerde ve diğer modsuz kullanıcı arabirimi öğelerinde kullanılır. Kullanıcıya bir değeri denetime doldurmada yardımcı olan bir seçici görüntüler. Bu düğmenin uzun ve kısa olmak için iki farklı varyasyonu vardır.

![Uzun [Gözat...] düğmesi](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Uzun [Gözat...] düğmesi

![Üç noktanın yalnızca kısası geçerli olan geçerli düğme](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Üç noktanın yalnızca kısası geçerli olan geçerli düğme

Yalnızca üç nokta kısa düğmesinin ne zaman kullanımı gerekir:

- Bir iletişim kutusunda birden fazla uzun **[Gözat...]** düğmesi varsa, örneğin birkaç alan göz atmanıza izin verdi. Bu durum tarafından **oluşturulan karmaşık** erişim anahtarlarını önlemek için her biri için kısa () düğmesini kullanın (**&** gözat ve **B&** aynı iletişim kutusunda satırlar ekleyin).

- Sıkı bir iletişim kutusunda veya uzun düğmeyi koymak için makul bir yer yoksa.

- Düğme bir kılavuz denetiminde görünecekse.

Düğmeyi kullanma yönergeleri:

- Erişim anahtarı kullanma. Klavyeyi kullanarak erişmek için kullanıcının bitişik denetimden sekmeyle sekmesine sahip olması gerekir. Sekme sırası, herhangi bir göz atma düğmesinin, alanın dolacak hemen sonra denk gelecek şekilde olduğundan emin olun. hiçbir zaman ilk dönemin altında bir alt çizgi kullanma.

- Microsoft Active Accessibility (MSAA) **Ad** özelliğini **Gözat...** (üç nokta dahil) olarak ayarlayın; böylece ekran okuyucular "dot-dot" veya "period-period" olarak değil "Gözat" olarak okur. Yönetilen denetimler için bu, **AccessibleName özelliğini ayarlama anlamına** gelir.

- Göz atma eylemi dışında hiçbir şey için üç nokta **/** düğmeyi hiçbir zaman kullanma. Örneğin, bir **[New...]** düğmesine ihtiyacınız varsa ancak metin için yeterli yer yoksa, iletişim kutusunun yeniden tasarlanması gerekir.

##### <a name="sizing-and-spacing"></a>Boyutlandırma ve aralık
![Boyutlandırma [Gözat...] düğmeleri: standart sürüm 75x23 piksel, kısa sürüm 26x23 piksel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Boyutlandırma [Gözat...] düğmeleri

![Aralık [Gözat...] düğmeleri: ilgili denetim ile standart Gözat düğmesi arasındaki boşluk 7 piksel, ilgili denetim ile kısa Gözat düğmesi 5 piksel arasındaki boşluk](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Aralık [Gözat...] düğmeleri

#### <a name="graphical-buttons"></a>Grafik düğmeleri
Bazı düğmeler her zaman bir grafik görüntüsü kullanmalı ve alan tasarrufu yapmak ve yerelleştirme sorunlarından kaçınmak için hiçbir zaman metin eklemez. Bunlar genellikle alan seçicilerde ve diğer sıralanabilir listelerde kullanılır.

> [!NOTE]
> Kullanıcıların bu düğmelere (erişim anahtarı yoktur) sekmeyle erişmesi gerekir, bu nedenle bunları mantıklı bir sırada bırakın. Ekran `name` okuyucularının düğme eylemlerini doğru yorumlaması için düğmenin özelliğini eylemiyle eşler.

| İşlev | Düğme |
| --- | --- |
| Ekle | ![Grafik "Ekle" düğmesi](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Kaldır | ![Grafik "Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Hepsini Ekle | ![Grafik "Hepsini Ekle" düğmesi](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Hepsini Kaldır | ![Grafik "Hepsini Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Yukarı Taşı | ![Grafik "Yukarı Taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Aşağı Taşı | ![Grafik "Aşağı Taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Sil | ![Grafik "Sil" düğmesi](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Boyutlandırma ve aralık
Grafik düğmeleri için boyutlandırma, **[Gözat...]** düğmesinin kısa sürümüyle aynıdır (26x23 piksel):

![Saydam renk göstermeden ve göstermeden, düğmede grafiksel bir görüntünün görünümü](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Saydam renk göstermeden ve göstermeden, düğmede grafiksel bir görüntünün görünümü

### <a name="hyperlinks"></a>Köprüler
Köprüler, Yardım konusu, kalıcı iletişim kutusu veya sihirbaz açma gibi gezinti tabanlı eylemler için çok uygun olabilir. Bir komut için köprü kullanılıyorsa, her zaman kullanıcı arabiriminde görünür ve fark edilebilir bir değişiklik görüntülemesi gerekir. Genel olarak, bir eylemi işleyen eylemler (Kaydet, İptal ve Sil gibi) bir düğme kullanılarak daha iyi iletilebilir.

#### <a name="writing-style"></a>Yazma stili
Kullanıcı arabirimi [metni için Windows Masaüstü yönergelerini izleyin.](/windows/desktop/uxguide/text-ui) "Daha fazla bilgi" "Bana daha fazla bilgi ver" veya "Bu konuda yardım al" ifadesini kullanmayın. Bunun yerine Yardım bağlantısı metni, Yardım içeriği tarafından yanıtlandı birincil soru olarak ifade eder. Örneğin, "**Nasıl yaparım? sunucuyu sunucuya Sunucu Gezgini?**"

#### <a name="visual-style"></a>Görsel stili

- Köprüler her zaman [VSColor Hizmetini kullandır.](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService) Köprü doğru şekilde stile sahip değilse etkin olduğunda kırmızı yanıp söner veya ziyaret edildikten sonra farklı bir renk gösterir.

- Bağlantı, filigranda olduğu gibi tam tümce içindeki bir tümce parçası değilse denetim resting durumuna alt çizgi dahil etme.

- Üzerine gelindiğinde alt çizgiler görünmez. Bunun yerine, kullanıcıya bağlantının etkin olduğuyla ilgili geri bildirim küçük bir renk değişikliği ve uygun bağlantı imlecidir.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Ağaç görünümleri

Ağaç görünümleri, karmaşık listeleri üst-alt gruplar halinde düzenlemenin bir yolunu sağlar. Bir kullanıcı, temel alınan alt öğeleri ortaya çıkarmak veya gizlemek için üst grupları genişletebilirsiniz veya daraltabilirsiniz. Bir ağaç görünümündeki her öğe, daha fazla eylem sağlamak için seçilebilir.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Ağaç görünümü görsel stili

#### <a name="expanders"></a>Genişleticiler
Ağaç görünümü denetimleri, Windows ve Windows tarafından kullanılan genişletici tasarımına uygun Visual Studio. Her düğüm, temel alınan öğeleri ortaya çıkarmak veya gizlemek için bir genişletici denetimi kullanır. Genişletici denetimi kullanmak, Windows ve Windows'da farklı ağaç görünümleri ile karşılaşan kullanıcılar için tutarlılık Visual Studio.

![Doğru: genişletici denetimi kullanarak ağaç görünümü düğümünün düzgün stili](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Doğru: genişletici denetimi kullanarak ağaç görünümü düğümünün düzgün stili

![Yanlış: ağaç görünümü düğümünün yanlış stili](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Yanlış: ağaç görünümü düğümünün yanlış stili

#### <a name="selection"></a>Seçim
Ağaç görünümünde bir düğüm seçildiğinde vurgu, ağaç görünümü denetiminde tam genişliğe genişletilmelidir. Bu, kullanıcıların hangi öğeyi seçtiklerini net bir şekilde belirlemesine yardımcı olur. Seçim renkleri, geçerli Visual Studio yansıtacak.

![Doğru: Seçilen düğümün vurgusu ağaç görünümü denetimi genişliğinin tamamına uyar.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Doğru: Seçilen düğümün vurgusu ağaç görünümü denetimi genişliğinin tamamına uyar.

![Yanlış: Seçilen düğümün vurgulanmış olması ağaç görünümü denetimi genişliğinin tamamına sığmıyor.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Yanlış: Seçilen düğümün vurgulanmış olması ağaç görünümü denetimi genişliğinin tamamına sığmıyor.

#### <a name="icons"></a>Simgeler
Simgeler yalnızca öğeler arasındaki farkları görsel olarak belirlemeye yardımcı olması için ağaç görünümü denetimlerde kullanılmalıdır. Genel olarak, simgeler yalnızca öğe türlerini ayırt etmek için Simgeler'in bilgi taşıdığı heterojen listelerde kullanılmalıdır. Simgeler kullanan homojen bir listede genellikle gürültü olarak görülebilir ve kaçınılmalıdır. Bu durumda, grup simgesi (üst) içindeki öğelerin türünü iletebilirsiniz. Simge dinamikse ve durumu belirtmek için kullanılırsa bu kuralın istisnası olur.

#### <a name="scroll-bars"></a>Kaydırma çubukları
İçerik ağaç görünümü denetimine sığarsa kaydırma çubukları her zaman gizlenir. Kaydırma çubuklarının kaydırılabilir bir pencerede gizlenip yarı saydam olması ve ağaç görünümünü içeren pencerenin odağı olduğunda veya ağaç görünümünün üzerine gelindiğinde görünmesi kabul edilebilir.

![İçerikler ağaç görünümü denetimi sınırlarını aştıklarında hem dikey hem de yatay kaydırma çubukları görüntülenir.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />İçerikler ağaç görünümü denetimi sınırlarını aştıklarında hem dikey hem de yatay kaydırma çubukları görüntülenir.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Ağaç görünümü etkileşimleri

#### <a name="context-menus"></a>Bağlam menüleri
Ağaç görünümü düğümü, bir bağlam menüsünde alt menü seçeneklerini ortaya çıkarabilirsiniz. Genellikle, kullanıcı bir öğeye sağ tıklamış veya Bir Windows klavyesi üzerinde öğe seçiliyken Menü tuşuna basmışsa bu durum oluşur. Düğümün odaklanması ve seçili durumda yer almaları önemlidir. Bu, kullanıcının alt menüye ait olan öğeyi belirlemesine yardımcı olur.

![Bağlam menüsünü oluşturan öğe, kullanıcıya hangi öğenin seç olduğunu bildirmeye odaklanır.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />Bağlam menüsünü oluşturan öğe, kullanıcıya hangi öğenin seç olduğunu bildirmeye odaklanır.

#### <a name="keyboard"></a>Klavye
Ağaç görünümü, klavyeyi kullanarak öğeleri seçme ve düğümleri genişletme/daraltma olanağı sağlamış olması gerekir. Bu, gezintinin erişilebilirlik gereksinimlerimizi karşılamalarını sağlar.

##### <a name="tree-view-control"></a>Ağaç görünümü denetimi
Visual Studio ağaç denetimleri yaygın klavye gezintisini izlemeli:

- **Yukarı Ok:** Ağacı yukarı doğru hareket ettirerek öğeleri seçin

- **Aşağı Ok:** Ağacı aşağı doğru hareket ettirerek öğeleri seçin

- **Sağ Ok:** Ağaçtaki bir düğümü genişletme

- **Sol Ok:** Ağaçtaki bir düğümü daralt

- **Anahtarı girin:** Seçili öğeyi başlatma, yükleme, yürütme

##### <a name="trid-tree-view-and-grid-view"></a>Trid (ağaç görünümü ve kılavuz görünümü)
Trid denetimi, bir kılavuz içinde ağaç görünümü içeren karmaşık bir denetimdir. Ağacı genişletmek, daraltmak ve gezinmek, aşağıdaki eklemelerle ağaç görünümüyle aynı klavye komutlarına uygun olması gerekir:

- **Sağ Ok:** Bir düğümü genişletin. Düğüm genişletildikten sonra sağdan en yakın sütuna doğru gezinmeye devam edecektir. Gezinti, satırın sonunda duracak.

- **Sekme:** Sağdan en yakın hücreye gidin.  Satırın sonunda gezinti bir sonraki satıra devam eder.

- **Shift + Sekme:** Sol tarafta en yakın hücreye gidin.  Satırın başında gezinti, önceki satırdaki en sağdaki hücreye devam eder.

![Visual Studio'da bir trid denetimi](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Visual Studio'da bir trid denetimi
