---
title: Visual Studio için Ortak Kontrol Desenleri | Microsoft Dokümanlar
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5a1904c01f5688a00e45de7feed7ae326d9b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698709"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio İçin Yaygın Denetim Desenleri
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Ortak denetimler

### <a name="overview"></a>Genel Bakış
Ortak denetimler Visual Studio kullanıcı arabiriminin çoğunluğunu oluşturan. Visual Studio arabiriminde kullanılan en yaygın denetimler [Windows Desktop etkileşim yönergelerine](/windows/desktop/uxguide/controls)uymalıdır. Bu konu Visual Studio'ya özgüdür ve bu Windows yönergelerini artıran özel durumları veya ayrıntıları kapsar.

#### <a name="common-controls-in-this-topic"></a>Bu konuda ki ortak denetimler

- [Çubukları kaydırma](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Giriş alanları](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Açılan kutular ve açılır listeler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Onay kutuları](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Radyo düğmeleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Grup çerçeveleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Metin denetimleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Düğmeler ve köprüler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Ağaç görünümleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Görsel stil
Şekillendirme denetimleri yaparken göz önünde bulundurulması gereken ilk şey, denetimlerin temalı ui'de kullanılıp kullanılmayacağıdır. Standart UI'deki denetimler temalı olmayan ui'dir ve [normal Windows Masaüstü stilini](/windows/desktop/uxguide/controls)izlemeleri gerekir, yani yeniden şablonlandırılmalarına ve varsayılan denetim görünümlerinde görünmeleri gerekir.

- **Standart (yardımcı program) iletişim kutuları:** temalı değil. Yeniden şablon oluşturma. Temel denetim stili varsayılanlarını kullanın.

- **Araç pencereleri, belge düzenleyicileri, tasarım yüzeyleri ve temalı iletişim kutuları:** Renk hizmetini kullanarak özel temalı görünüm kullanın.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a>Çubukları kaydırma
 Kaydırma çubukları, kod düzenleyicisindeki gibi içerik bilgileriyle artırılmadığı sürece [Windows kaydırma çubukları için yaygın etkileşim desenlerini](/windows/desktop/Controls/about-scroll-bars) izlemelidir.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Giriş alanları
 Tipik etkileşim davranışı [için metin kutuları için Windows Masaüstü yönergelerini](/windows/desktop/uxguide/ctrl-text-boxes)izleyin.

#### <a name="visual-style"></a>Görsel stil

- Giriş alanları yardımcı program iletişim kutularında stile biş olmamalıdır. Kontrol için temel stili kullanın.

- Temalı giriş alanları yalnızca temalı iletişim kutularında ve araç pencerelerinde kullanılmalıdır.

#### <a name="specialized-interactions"></a>Özel etkileşimler

- Salt okunur alanlar gri (devre dengel) arka plana sahip, ancak varsayılan (etkin) ön plana çıkacaktır.

- Gerekli alanlar içlerinde filigran olarak ** \<gerekli>** olmalıdır. Nadir durumlar dışında arka planın rengini değiştirmemelisiniz.

- Hata doğrulama: [Visual Studio için Bildirimler ve İlerleme](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md) ye bakın

- Giriş alanları, gösterildiği pencerenin genişliğine sığmayacak veya bir yol gibi uzun bir alanın uzunluğuyla rasgele eşleşecek şekilde içeriğe uyacak şekilde boyutlandırılmalıdır. Uzunluk, kullanıcıiçin alana kaç karakterizin izin verildiğine dair sınırlamaların bir göstergesi olabilir.

     ![Yanlış giriş alanı uzunluğu: adın bu kadar uzun olması olası değildir.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Yanlış giriş alanı uzunluğu: adın bu kadar uzun olması olası değildir.

     ![Doğru giriş alanı uzunluğu: giriş alanı beklenen içerik için makul bir genişliktir.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Doğru giriş alanı uzunluğu: giriş alanı beklenen içerik için makul bir genişliktir.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Açılan kutular ve açılır listeler
Tipik etkileşim davranışı [için açılır listeler ve açılan kutular için Windows Masaüstü yönergelerini](/windows/desktop/uxguide/ctrl-drop)izleyin.

#### <a name="visual-style"></a>Görsel stil

- Yardımcı program iletişim kutularında denetimi yeniden şablona takmayın. Kontrol için temel stili kullanın.

- Temalı UI'de, açılan kutular ve açılır bırakmalar denetimler için standart temalı uygulamaları izler.

#### <a name="layout"></a>Düzen
Açılan kutular ve açılır düşmeler içeriğe uyacak şekilde boyutlandırılmalı, gösterildiği pencerenin genişliğine sığmayacak veya bir yol gibi uzun bir alanın uzunluğuyla rasgele eşleşecek şekilde boyutlandırılmalıdır.

![Yanlış: Açılır genişlik görüntülenecek içerik için çok uzundur.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Yanlış: Açılır genişlik görüntülenecek içerik için çok uzundur.

![Doğru: açılır bırakma, çeviri büyümesine izin verecek şekilde boyutlandırılır, ancak gereksiz yere uzun değildir.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Doğru: açılır bırakma, çeviri büyümesine izin verecek şekilde boyutlandırılır, ancak gereksiz yere uzun değildir.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Onay kutuları
Tipik etkileşim davranışı [için, onay kutuları için Windows Masaüstü yönergelerini](/windows/desktop/uxguide/ctrl-check-boxes)izleyin.

#### <a name="visual-style"></a>Görsel stil

- Yardımcı program iletişim kutularında denetimi yeniden şablona takmayın. Kontrol için temel stili kullanın.

- Temalı UI'de, onay kutuları denetimler için standart temalı temalı izlemeyi izler.

#### <a name="specialized-interactions"></a>Özel etkileşimler

- Onay kutusuyla etkileşim hiçbir zaman bir iletişim kutusu açmamalı veya başka bir alana gitmelidir.

- Onay kutularını ilk metin satırının taban çizgisiyle hizalayın.

     ![Yanlış: onay kutusu metne ortalanır.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Yanlış: onay kutusu metne ortalanır.

     ![Doğru: onay kutusu metnin ilk satırıyla hizalanır.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Doğru: onay kutusu metnin ilk satırıyla hizalanır.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Radyo düğmeleri
Tipik etkileşim davranışı [için, radyo düğmeleri için Windows Masaüstü yönergelerini](/windows/desktop/uxguide/ctrl-radio-buttons)izleyin.

#### <a name="visual-style"></a>Görsel stil
Yardımcı program iletişim kutularında, radyo düğmelerini stile demesin. Kontrol için temel stili kullanın.

#### <a name="specialized-interactions"></a>Özel etkileşimler
Grup ayrımını sıkı bir düzende korumanız gerekmediği sürece, radyo seçimlerini içine almak için bir grup çerçevesi kullanmanız gerekmez.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Grup çerçeveleri
Tipik etkileşim davranışı [için, grup çerçeveleri için Windows Masaüstü yönergelerini](/windows/desktop/uxguide/ctrl-group-boxes)izleyin.

#### <a name="visual-style"></a>Görsel stil
Yardımcı program iletişim kutularında, grup çerçevelerini stilleme. Kontrol için temel stili kullanın.

#### <a name="layout"></a>Düzen

- Grup ayrımını sıkı bir düzende korumanız gerekmediği sürece, radyo seçimlerini içine almak için bir grup çerçevesi kullanmanız gerekmez.

- Tek bir denetim için asla grup çerçevesi kullanmayın.

- Bazen grup çerçeve kapsayıcısı yerine yatay bir kural kullanmak kabul edilebilir.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Metin denetimleri

### <a name="static-text-fields"></a>Statik metin alanları

Statik metin alanı salt okunur bilgileri sunar ve kullanıcı tarafından seçilemez. Kullanıcının panoya kopyalamak isteyebileceği herhangi bir metin için kullanmaktan kaçının. Ancak, salt okunur statik metin durum değişikliğini yansıtacak şekilde değişebilir. Aşağıdaki örnekte, Bilgi grubunun altındaki Çıktı Adı statik metni, üzerindeki Kök Ad Alanı metin kutusunda yapılan değişiklikleri yansıtacak şekilde değişir.

Statik metin bilgilerini görüntülemenin iki yolu vardır.

Statik metin, gruplandırma çakışması olmadığında herhangi bir çevreleme olmadan bir iletişim kutusunda tek başına olabilir. Bir kutunun ekstra satırları gerçekten gerekli olup olmadığına karar verin. Aşağıda gösterildiği gibi, grup satırı tarafından oluşturulan bir bölümün altında dizin yolunun görüntülenmesi örnek:

![Metin denetimlerinde statik metin bilgisi](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "GörüntüleniyorStaticText.png")<br />Metin denetimlerinde statik metin bilgisi

Diğer gruplanmış alanların bulunduğu ve bilgilerin bulunduğu bir iletişim kutusunda okunabilirlik yardımcı olur ve bir bölüm gizlenebilir veya gösterilebilir **(Özellikler penceresi** açıklama bölmesinde olduğu gibi) veya benzer Kullanıcı Bira ile tutarlı olmak istediğinizde, statik metni bir kutunun içine yerleştirin. Bu grup kutusu tek bir kural `ButtonShadow`olmalı ve renkli:

![Özellikler penceresindeki statik metin](../../extensibility/ux-guidelines/media/PropertiesWindow.png "ÖzelliklerWindow.png")<br />Özellikler penceresindeki statik metin

### <a name="read-only-text-box"></a>Salt okunur metin kutusu

Bu, kullanıcının alan içindeki metni seçmesine, ancak onu atmasına izin verir. Bu metin kutuları bir `ButtonShadow` dolgu ile her zamanki 3-D keski ile sınırlanır.

Bir metin kutusu, kullanıcı onay kutusunu denetleme/denetleme yi denetleme veya radyo düğmesini seçme/silme gibi ilişkili denetimi değiştirdiğinde etkin (değiştirilebilir) olabilir. Örneğin, aşağıda gösterilen ** &gt; Araçlar Seçenekleri** sayfasında, Varsayılan **Kullan** onay kutusu işaretli olmadığında Ana **Sayfa** metin kutusu etkin hale gelir.

![Etkin olmayan ve etkin durumları gösteren salt okunur metin kutusu](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Etkin olmayan ve etkin durumları gösteren salt okunur metin kutusu

### <a name="using-text-in-dialogs"></a>İletişim kutularında metin kullanma

İletişim kutularındaki metin için temel yönergeler:

- Metin kutuları, liste kutuları ve temalı iletişim kutularındaki çerçeveler bir fiille başlar, yalnızca ilk sözcüğün baş harfi vardır ve bir üst üste ile biter.

    > Temalı iletişim kutularındaki metin denetimleri [Windows masaüstü UX yönergelerine](/windows/desktop/uxguide/top-violations) uyar ve Yardım bağlantılarındaki soru işaretleri dışında noktalama işaretlerini almaz.

- Onay kutuları ve seçenek düğmeleri için etiketler bir fiille başlar, yalnızca ilk sözcüğün başlangıç sermayesi ile başlar ve bitiş noktalaması yoktur.

- Düğmeler, menüler, menü öğeleri ve sekmeler için etiketlerin her sözcüğün (başlık örneği) ilk büyük harfleri vardır.

- Etiket terminolojisi diğer iletişim kutularındaki benzer etiketlerle tutarlı olmalıdır.

- Mümkünse, uygulama için geliştiriciye gitmeden önce bir yazar/editöre metni yazmasını veya onaylamasını önlayın.

- Sekmenin yeterli olduğu özel durumlar dışında tüm denetimlerde etiketler olmalıdır.
Uygun olduğunda yardımcı metni kullanın.

### <a name="helper-text"></a>Yardımcı metin

Kullanıcının iletişim kutusunun amacını anlamasına veya hangi eylemin gerçekleşsüreceğini belirtmesi için iletişim kutularına dahildir. Yardımcı metin yalnızca basit iletişim leri darmadağın önlemek için gerektiğinde kullanılmalıdır. Yardımcı metin iki varyasyonları iletişim ve filigran vardır.

Yardımcı metin için ortak konumları izleyin ve yeni alanlar tanıtırken seçici olun. Yardımcı metin için sık karşılaşılan senaryolar şunlardır:

- Karmaşık bir iletişim kutusuyla nasıl etkileşimde olunacakhakkında ek yön vermek için iletişim kutularındaki yardımcı metin.

- Boş araç pencerelerinde veya iletişim kutularındaki filigran metni, neden hiçbir içeriğin görünmeyiş olduğunu açıklar.

- **Özellikler penceresinin**altındaki gibi bir açıklama bölmesi.

- Boş bir düzenleyicideki filigran metni, kullanıcının başlamak için hangi eylemi yapması gerektiğini açıklar.

### <a name="dialog-helper-text"></a>İletişim yardımcı metni

Bir kullanıcı deneyimi tasarımcısı yardımcı metnin ne zaman uygun olduğunu belirlemede yardımcı olabilir. Tasarımcı, yardımcı metnin genel içeriğinin yanı sıra nerede göründüğünü de tanımlayabilir. Kullanıcı yardımı gerçek metni yazabilir/güncelleyebilir.

### <a name="watermarks"></a>Filigranlar

İletişim kutuları biraz farklı filigran yönergelerinden yararlanır. Bir iletişim kutusu birçok Kullanıcı Arabirimi öğesiyle (etiketler, ipucu metni, düğmeler ve metinle diğer kapsayıcı denetimleri) meşgul görünebildiği `ButtonShadow`için, özellikle bunlar siyah renkte göründüğünde, filigranlar koyu gri (VSColor: ) ile daha iyi görünür. Genellikle bir filigran beyaz arka plan (VSColor: `Window`) ile bir liste kutusu gibi bir denetim içinde görünür.

- Metin koyu gri (VSColor: `ButtonShadow`) görünür. Ancak, filigran orta gri veya diğer renkli (VSColor: `ButtonFace`) arka planda görünüyorsa ve okunabilirliği yle `WindowText`ilgili endişeler varsa, siyah metinle birlikte gidin (VSColor: ).

- Filigranlar ortalanabilir veya sola floş lanabilir. Hizalama kararları verirken standart tasarım kurallarını uygulayın. Filigran arka planda seçilemez.

![Filigran metin örneği](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Filigran metin örneği

### <a name="context-specific-dynamic-text"></a>İçerime özgü (dinamik) metin

Dinamik metin, iletişim kutusunda veya modsuz kullanıcı arabirimi'nde iki şekilde kullanılabilir: dinamik bir etiket veya dinamik içerik olarak.

- Dinamik etiket: Dinamik metnin yaygın kullanımı, seçili öğe için daha fazla bilgi sunan açıklayıcı panellerdedir (örneğin, sağda bir ızgarada görüntülenen öğeler ve özellikler listesi içeren bir iletişim kutusu gibi). Özellik ızgarasının etiketi dinamik olabilir, böylece solda bir öğe seçildiğinde, sağdaki ızgara söz konusu öğeye ait bilgileri gösterir.

- Dinamik metin: belirli bilgileri görüntülemeniz gereken durumlarda yararlı olabilir ve genel bilgileri bu şekilde görüntülemeniz gerekmez, ancak aşırı kullanılmamaya özen gösterilmelidir.

Kullanıcıların bilgileri kopyalama yeteneğine sahip olmasını istiyorsanız, dinamik metin salt okunur metin alanında olmalıdır.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Düğmeler ve köprüler

### <a name="overview"></a>Genel Bakış
Düğmeler ve bağlantı denetimleri (köprüler) kullanım, ifade verme, boyutlandırma ve boşluk landırma için [köprülerdeki temel Windows Masaüstü kılavuzunu](/windows/desktop/uxguide/ctrl-links) izlemelidir.

### <a name="choosing-between-buttons-and-links"></a>Düğmeler ve bağlantılar arasında seçim yapmak
Geleneksel olarak, düğmeler eylemler için kullanılır ve köprüler gezinme için ayrılmıştır. Düğmeler her durumda kullanılabilir, ancak düğmeler ve bağlantılar bazı koşullarda daha değiştirilebilir böylece Visual Studio bağlantıların rolü genişletildi.

Komut düğmelerinin ne zaman kullanılacağı:

- Birincil komutlar

- İkincil komutlar olsa lar bile giriş toplamak veya seçim yapmak için kullanılan pencereleri görüntüleme

- Yıkıcı veya geri dönüşü olmayan eylemler

- Sihirbazlar ve sayfa akışları içindeki bağlılık düğmeleri

Araç pencerelerinde veya etiket için ikiden fazla sözcük gerekiyorsa komut düğmelerinden kaçının. Bağlantıların daha uzun etiketleri olabilir.

 Bağlantıların ne zaman kullanılacağı:

- Başka bir pencereye, belgeye veya web sayfasına gezinme

- Eylemin amacını tanımlamak için daha uzun bir etiket veya kısa bir cümle gerektiren durumlar

- Eylemin yıkıcı veya geri döndürülemez olmaması koşuluyla, bir düğmenin UI'yi bastıracağı dar alanlar

- Birçok komutun olduğu durumlarda ikincil komutları vurgulama

#### <a name="examples"></a>Örnekler
![Durum iletisinden sonra InfoBar'da kullanılan komut bağlantıları](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Durum iletisinden sonra InfoBar'da kullanılan komut bağlantıları

![CodeLens açılır penceresinde kullanılan bağlantılar](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />CodeLens açılır penceresinde kullanılan bağlantılar

![Düğmelerin çok fazla dikkat çekeceği ikincil komutlar için kullanılan bağlantılar](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Düğmelerin çok fazla dikkat çekeceği ikincil komutlar için kullanılan bağlantılar

### <a name="common-buttons"></a>Ortak düğmeler

#### <a name="text"></a>Metin
[Kullanıcı Arabirimi metin ve terminolojisindeki](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)yazım yönergelerini izleyin.

#### <a name="visual-style"></a>Görsel stil

##### <a name="standard-unthemed"></a>Standart (temalı olmayan)
Visual Studio'daki çoğu düğme yardımcı program iletişim lerinde görünür ve tarzlandırılmamalıdır. İşletim sistemi tarafından dikte edilen düğmelerin standart görünümünü yansıtmalıdır.

##### <a name="themed"></a>Temalı
Bazı durumlarda, düğmeler stildeki UI içinde kullanılabilir ve bu düğmeler uygun şekilde şekillendirilmelidir. Temalı [denetimler](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) hakkında bilgi için İletişim Bilgileri'ne bakın.

### <a name="special-buttons"></a>Özel düğmeler

#### <a name="browse-buttons"></a>Gözat... Düğme
**[Gözatın...]** düğmeler ızgaralarda, iletişim kutularında ve araç pencerelerinde ve diğer modsuz ara birimi öğelerinde kullanılır. Kullanıcının bir değeri denetime doldurmasına yardımcı olan bir seçici görüntüler. Bu düğmenin uzun ve kısa olmak üzere iki çeşidiyi vardır.

![Uzun [Gözat...] düğmesi](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Uzun [Gözat...] düğmesi

![Elips-sadece kısa [...] düğmesi](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Elips-sadece kısa [...] düğmesi

Elipsler için kullanılan kısa düğme:

- Bir iletişim kutusunda birden fazla uzun **[Gözat...]** düğmesi varsa, örneğin birden fazla alanın gezinmeye izin verdiği gibi. Bu durumun yarattığı kafa karıştırıcı erişim anahtarlarını önlemek için her biri için kısa **[...]** düğmesini kullanın (aynı iletişim kutusunda** Gözat** ve **B&satır**&).

- Sıkı bir iletişim kutusunda veya uzun düğmeyi koymak için makul bir yer olmadığında.

- Düğme ızgara denetiminde görünürse.

Düğmeyi kullanma yönergeleri:

- Erişim anahtarı kullanmayın. Klavyeyi kullanarak erişmek için, kullanıcının bitişik denetimden sekmesi gerekir. Sekme sırasının, herhangi bir gözatma düğmesinin dolduracağı alandan hemen sonra düşmesini sağlayacak şekilde olduğundan emin olun. Asla ilk dönemin altında bir alt puan kullanmayın.

- Microsoft Active Accessibility (MSAA) **Adı** özelliğini **Gözat...** (elipsler dahil) olarak ayarlayın, böylece ekran okuyucuları "Nokta-nokta-nokta" veya "dönem dönemi" olarak okumaz. Yönetilen denetimler için bu, **Erişilebilir Ad** özelliğini ayarlamak anlamına gelir.

- Bir gözatma eylemi dışında bir şey için bir elips **[...]** düğmesini asla kullanmayın. Örneğin, **[Yeni...]** düğmesine ihtiyacınız varsa ancak metin için yeterli alan yoksa, iletişim kutusunun yeniden tasarlanması gerekir.

##### <a name="sizing-and-spacing"></a>Boyutlandırma ve aralık
![Boyutlandırma [Gözat...] düğmeleri: standart sürüm 75x23 piksel, kısa sürüm 26x23 piksel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Boyutlandırma [Gözat...] düğmeleri

![Aralık [Gözat...] düğmeleri: ilgili denetim ve standart Gözat düğmesi arasında boşluk 7 piksel, ilgili denetim ve kısa Gözat düğmesi 5 piksel arasında boşluk](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Aralık [Gözat...] düğmeleri

#### <a name="graphical-buttons"></a>Grafik düğmeleri
Bazı düğmeler her zaman bir grafik görüntüsü kullanmalı ve alanı korumak ve yerelleştirme sorunlarını önlemek için hiçbir zaman metin eklememelidir. Bunlar genellikle alan seçicilerde ve diğer sıralanabilir listelerde kullanılır.

> [!NOTE]
> Kullanıcıların bu düğmeleri sekmeleri (erişim tuşları yoktur) sekmesi gerekir, bu nedenle bunları mantıklı bir sıraya yerleştirin. Ekran `name` okuyucuların düğme eylemini doğru bir şekilde yorumlayabilmeleri için düğmenin özelliğini, aldığı eylemle eşleyin.

| İşlev | Düğme |
| --- | --- |
| Ekle | ![Grafiksel "Ekle" düğmesi](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Kaldır | ![Grafiksel "Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Tümlerini Ekle | ![Grafiksel "Tümleri Ekle" düğmesi](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Tümlerini Kaldır | ![Grafiksel "Tümlerini Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Yukarı Taşı | ![Grafiksel "Yukarı Taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Aşağı Taşı | ![Grafiksel "Aşağı Taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Sil | ![Grafiksel "Sil" düğmesi](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Boyutlandırma ve aralık
Grafik düğmeleri için boyutlandırma **, [Gözat...]** düğmesinin (26x23 piksel) kısa sürümüyle aynıdır:

![Saydam renk gösteren ve görünmeyen düğmeüzerinde grafik selin görünümü](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Saydam renk gösteren ve görünmeyen düğmeüzerinde grafik selin görünümü

### <a name="hyperlinks"></a>Köprüler
Köprüler, Yardım konusunu, modal iletişim kutusunu veya sihirbazı açma gibi gezinti tabanlı eylemlere çok uygundur. Bir komut için bir köprü kullanılıyorsa, kullanıcı arabirimi için her zaman görünür ve fark edilir bir değişiklik göstermelidir. Genel olarak, bir eyleme (Kaydet, İptal et ve Sil gibi) bağlanan eylemler bir düğme kullanılarak daha iyi iletilir.

#### <a name="writing-style"></a>Yazma stili
Kullanıcı [arabirimi metni için Windows Masaüstü kılavuzunu](/windows/desktop/uxguide/text-ui)izleyin. "Hakkında daha fazla bilgi edinin", "Bana daha fazla bilgi verin" veya "Bu konuda yardım alın" ifadelerini kullanmayın. Bunun yerine, Yardım içeriği tarafından yanıtlanan birincil soru açısından Yardım bağlantı metnini ifade edin. Örneğin, "**Sunucu Gezgini'ne nasıl sunucu eklerim?**"

#### <a name="visual-style"></a>Görsel stil

- Köprüler her zaman [VSColor Hizmetini](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)kullanmalıdır. Bir köprü doğru şekilde şekillendirilmemişse, etkin olduğunda kırmızı yanıp söner veya ziyaret edildikten sonra farklı bir renk gösterir.

- Bağlantı filigrandaki gibi tam bir cümle içinde bir cümle parçası olmadıkça, denetim dinlenme durumuna alt çizgi çizmeler eklemeyin.

- Altı çiziler havada görünmemelidir. Bunun yerine, kullanıcıya bağlantının etkin olduğu geri bildirimi hafif bir renk değişikliği ve uygun bağlantı imlecidir.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Ağaç görünümleri

Ağaç görünümleri, karmaşık listeleri üst alt gruplar halinde düzenlemenin bir yolunu sağlar. Kullanıcı, altta yatan alt öğeleri ortaya çıkarmak veya gizlemek için üst grupları genişletebilir veya daraltabilir. Ağaç görünümüiçindeki her öğe, daha fazla eylem sağlamak için seçilebilir.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Ağaç görünümü görsel stili

#### <a name="expanders"></a>Genişleticiler
Ağaç görünümü denetimleri, Windows ve Visual Studio tarafından kullanılan genişletici tasarımına uygun olmalıdır. Her düğüm, altta yatan öğeleri ortaya çıkarmak veya gizlemek için bir genişletici denetimi kullanır. Genişletici denetimi kullanmak, Windows ve Visual Studio'da farklı ağaç görünümleri ile karşılaşabilecek kullanıcılar için tutarlılık sağlar.

![Doğru: genişletici denetimi kullanarak ağaç görünümü düğümünün uygun stili](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Doğru: genişletici denetimi kullanarak ağaç görünümü düğümünün uygun stili

![Yanlış: ağaç görünümü düğümünün yanlış stili](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Yanlış: ağaç görünümü düğümünün yanlış stili

#### <a name="selection"></a>Seçim
Ağaç görünümünde bir düğüm seçildiğinde, vurgu, ağaç görünümü denetiminin tam genişliğine kadar genişletilmelidir. Bu, kullanıcıların seçtikleri öğeyi net bir şekilde belirlemelerine yardımcı olur. Seçim renkleri geçerli Visual Studio tesini yansıtmalıdır.

![Doğru: seçili düğümün vurgusu ağaç görünümü denetiminin tüm genişliğine uyar.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Doğru: seçili düğümün vurgusu ağaç görünümü denetiminin tüm genişliğine uyar.

![Yanlış: seçili düğümün vurgusu ağaç görünümü denetiminin tüm genişliğine sığmaz.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Yanlış: seçili düğümün vurgusu ağaç görünümü denetiminin tüm genişliğine sığmaz.

#### <a name="icons"></a>Simgeler
Simgeler yalnızca öğeler arasındaki farklılıkları görsel olarak tanımlamaya yardımcı olurlarsa ağaç görünümü denetimlerinde kullanılmalıdır. Genel olarak, simgeler yalnızca Simgeler öğe türlerini ayırt etmek için bilgi taşıyan heterojen listelerde kullanılmalıdır. Homojen bir listede simgeler kullanılarak sık sık gürültü olarak görülebilir ve kaçınılmalıdır. Bu durumda grup simgesi (üst) içindeki öğelerin türünü iletebilir. Simge dinamik sayılsa ve durumu belirtmek için kullanılıyorsa, bu kuralın istisnası olacaktır.

#### <a name="scroll-bars"></a>Çubukları kaydırma
İçerik ağaç görünümü denetimine uyuyorsa kaydırma çubukları her zaman gizlenmelidir. Kaydırma çubuklarının kaydırılabilir bir pencerede gizlenebilmesi veya yarı saydam olması ve ağaç görünümünü içeren pencere nin odağı olduğunda veya ağaç görünümünün üzerinde görünmesi kabul edilebilir.

![İçeriği ağaç görünümü denetiminin sınırlarını aştığından hem dikey hem de yatay kaydırma çubukları görüntülenir.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />İçeriği ağaç görünümü denetiminin sınırlarını aştığından hem dikey hem de yatay kaydırma çubukları görüntülenir.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a>Ağaç görünümü etkileşimleri

#### <a name="context-menus"></a>Bağlam menüleri
Bir ağaç görünümü düğümü bağlam menüsünde alt menü seçeneklerini ortaya çıkarabilir. Genellikle, bu durum, bir kullanıcı bir öğeyi sağ tıklattığında veya seçili öğeyle birlikte Windows klavyesindeki Menü tuşuna bastığında oluşur. Düğümün odak kazanması ve seçilmesi önemlidir. Bu, kullanıcının alt menünün hangi öğeye ait olduğunu belirlemesine yardımcı olur.

![Bağlam menüsünü oluşturan öğe, kullanıcıya hangi öğenin seçildiğini bildirmek için odak kazanır.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />Bağlam menüsünü oluşturan öğe, kullanıcıya hangi öğenin seçildiğini bildirmek için odak kazanır.

#### <a name="keyboard"></a>Klavye
Ağaç görünümü, klavyeyi kullanarak öğeleri seçme ve düğümleri genişletme/daraltma olanağı sağlamalıdır. Bu, gezinmenin erişilebilirlik gereksinimlerimizi karşılamasını sağlar.

##### <a name="tree-view-control"></a>Ağaç görünümü denetimi
Visual Studio ağaç denetimleri yaygın klavye gezintisi izlemelidir:

- **Yukarı Ok:** Ağaca taşıyarak öğeleri seçin

- **Aşağı Ok:** Ağaçten aşağı hareket ettirerek öğeleri seçme

- **Sağ Ok:** Ağaçtaki düğümü genişletme

- **Sol Ok:** Ağaçta düğümü daraltma

- **Enter tuşu:** Seçili öğeyi başlatın, yükleyin, çalıştırın

##### <a name="trid-tree-view-and-grid-view"></a>Trid (ağaç görünümü ve ızgara görünümü)
Üç leme denetimi, ızgara içinde ağaç görünümü içeren karmaşık bir denetimdir. Ağacı genişletme, daraltma ve gezinme, aşağıdaki eklemelerle aynı klavye komutlarına ağaç görünümüyle saygı göstermelidir:

- **Sağ Ok:** Düğümü genişletin. Düğüm genişletildikten sonra, sağdaki en yakın sütuna gezinmeye devam etmelidir. Gezinti satırın sonunda durmalıdır.

- **Sekme:** Sağdaki en yakın hücreye doğru iletin.  Satırın sonunda, gezinti sonraki satıra devam eder.

- **Shift + Sekmesi:** Soldaki en yakın hücreye doğru iletin.  Satırın başında, gezinti önceki satırdaki en sağdaki hücreye doğru devam eder.

![Visual Studio'da üç leme kontrolü](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Visual Studio'da üç leme kontrolü
