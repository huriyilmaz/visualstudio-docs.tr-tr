---
title: Visual Studio için ortak denetim desenleri | Microsoft Docs
description: Visual Studio ortak denetimlerinin Windows Masaüstü etkileşim yönergelerini nasıl izlediği ve bu yönergeleri geliştiren özel durumlar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e55bb5f4473971f99ce04f9e48b7e05ec13f94c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090115"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio İçin Yaygın Denetim Desenleri
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Ortak denetimler

### <a name="overview"></a>Genel Bakış
Ortak denetimler, Visual Studio 'daki Kullanıcı arabiriminin çoğunu yapar. Visual Studio arabiriminde kullanılan çoğu ortak denetim, [Windows Masaüstü etkileşim yönergeleri](/windows/desktop/uxguide/controls)' ni izlemelidir. Bu konu, Visual Studio 'ya özeldir ve bu Windows kılavuzlarını geliştiren özel durumları veya ayrıntıları içerir.

#### <a name="common-controls-in-this-topic"></a>Bu konudaki ortak denetimler

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
Stil oluşturma denetimlerinde göz önünde bulundurmanız gereken ilk şey, denetimlerin temalı Kullanıcı arabiriminde kullanılıp kullanılmayacağını belirtir. Standart Kullanıcı arabirimindeki denetimler, temalı Kullanıcı arabirimi ve [normal Windows Masaüstü stilini](/windows/desktop/uxguide/controls)izlemelidir, yani bu değerler yeniden Şablonsuz ve varsayılan denetim görünümünde görünür olmalıdır.

- **Standart (yardımcı program) iletişim kutuları:** temalı değildir. Yeniden şablon yapmayın. Temel denetim stili varsayılanlarını kullanın.

- **Araç pencereleri, belge düzenleyicileri, tasarım yüzeyleri ve temalı iletişim kutuları:** Renk hizmetini kullanarak özelleştirilmiş temalı görünümü kullanın.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> Kaydırma çubukları
 Kaydırma çubukları, kod Düzenleyicisi 'nde olduğu gibi içerik bilgileriyle genişletmedikleri takdirde, [Windows kaydırma çubuklarının ortak etkileşim düzenlerini](/windows/desktop/Controls/about-scroll-bars) izlemelidir.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Giriş alanları
 Tipik etkileşim davranışı için, [metin kutuları Için Windows Masaüstü yönergeleri](/windows/desktop/uxguide/ctrl-text-boxes)' ni izleyin.

#### <a name="visual-style"></a>Görsel stili

- Giriş alanları, yardımcı program iletişim kutularında stilleştirmemelidir. Denetimin iç temel stilini kullanın.

- Temalı giriş alanları yalnızca temalı iletişim kutularında ve araç penceresinde kullanılmalıdır.

#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimler

- Salt okuma alanları gri (devre dışı) bir arka plana, ancak varsayılan (etkin) ön plana sahip olacaktır.

- Gerekli alanlar, **\<Required>** içindeki filigranlara sahip olmalıdır. Nadir durumlar haricinde arka planın rengini değiştirmemelisiniz.

- Hata doğrulaması: bkz. [Visual Studio Için bildirimler ve Ilerleme durumu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Giriş alanları, gösterilen pencerenin genişliğine sığması için veya bir yol gibi uzun bir alanın uzunluğuna göre değil, içeriğe uyacak şekilde boyutlandırılmalıdır. Uzunluk, alanda kaç karaktere izin verileceğini gösteren sınırlamalar kullanıcısına bir gösterge olabilir.

     ![Hatalı giriş alanı uzunluğu: ad bu uzun olacaktır.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Hatalı giriş alanı uzunluğu: ad bu uzun olacaktır.

     ![Doğru giriş alanı uzunluğu: giriş alanı, beklenen içerik için makul bir genişliğidir.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Doğru giriş alanı uzunluğu: giriş alanı, beklenen içerik için makul bir genişliğidir.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Birleşik giriş kutuları ve açılan listeler
Tipik etkileşim davranışı için, [açılan listeler ve Birleşik giriş kutuları Için Windows Masaüstü yönergeleri](/windows/desktop/uxguide/ctrl-drop)' ni izleyin.

#### <a name="visual-style"></a>Görsel stili

- Yardımcı program iletişim kutularında denetimi yeniden şablon yapmayın. Denetimin iç temel stilini kullanın.

- Temalı Kullanıcı arabiriminde, Birleşik giriş kutuları ve açılan kutular, denetimlerin standart temalarını izler.

#### <a name="layout"></a>Layout
Birleşik giriş kutuları ve açılan kutulamalar, gösterilen pencerenin genişliğine sığması için veya bir yol gibi uzun bir alanın uzunlukla uyumlu olmak için içeriğe uyacak şekilde boyutlandırılmalıdır.

![Yanlış: aşağı açılan genişlik görüntülenecek içerik için çok uzun.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Yanlış: aşağı açılan genişlik görüntülenecek içerik için çok uzun.

![Doğru: açılan liste, çeviri büyümesi için, ancak gereksiz bir süre boyunca izin verecek şekilde boyutlandırılır.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Doğru: açılan liste, çeviri büyümesi için, ancak gereksiz bir süre boyunca izin verecek şekilde boyutlandırılır.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Onay kutuları
Tipik etkileşim davranışı için, [onay kutuları Için Windows Masaüstü yönergeleri](/windows/desktop/uxguide/ctrl-check-boxes)' ni izleyin.

#### <a name="visual-style"></a>Görsel stili

- Yardımcı program iletişim kutularında denetimi yeniden şablon yapmayın. Denetimin iç temel stilini kullanın.

- Temalı Kullanıcı arabiriminde, onay kutuları denetimlerin standart temalarını izler.

#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimler

- Onay kutusuyla etkileşim hiçbir koşulda bir iletişim kutusu içermemelidir veya başka bir alana gitmelidir.

- Metnin ilk satırının taban çizgisiyle birlikte onay kutularını hizalayın.

     ![Yanlış: onay kutusu metinde ortalanır.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Yanlış: onay kutusu metinde ortalanır.

     ![Doğru: onay kutusu, metnin ilk satırıyla hizalanır.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Doğru: onay kutusu, metnin ilk satırıyla hizalanır.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Radyo düğmeleri
Tipik etkileşim davranışı için, [radyo düğmeleri Için Windows Masaüstü yönergeleri](/windows/desktop/uxguide/ctrl-radio-buttons)' ni izleyin.

#### <a name="visual-style"></a>Görsel stili
Yardımcı program iletişim kutularında radyo düğmelerine stil kullanmayın. Denetimin iç temel stilini kullanın.

#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimler
Grup ayrımını sıkı bir düzende korumanız gerekmiyorsa, radyo seçeneklerini kapsamak için bir grup çerçevesinin kullanılması gerekli değildir.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Grup çerçeveleri
Tipik etkileşim davranışı için, [Grup çerçevelerine yönelik Windows Masaüstü yönergelerini](/windows/desktop/uxguide/ctrl-group-boxes)izleyin.

#### <a name="visual-style"></a>Görsel stili
Yardımcı program iletişim kutularında, Grup çerçevelerinden stil oluşturmayın. Denetimin iç temel stilini kullanın.

#### <a name="layout"></a>Layout

- Grup ayrımını sıkı bir düzende korumanız gerekmiyorsa, radyo seçeneklerini kapsamak için bir grup çerçevesinin kullanılması gerekli değildir.

- Hiç bir grup çerçevesini tek bir denetim için kullanmayın.

- Bazen grup çerçevesi kapsayıcısı yerine yatay bir kural kullanılması kabul edilebilir.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Metin denetimleri

### <a name="static-text-fields"></a>Statik metin alanları

Statik metin alanı salt okunurdur ve Kullanıcı tarafından seçilemez. Kullanıcının Pano 'ya kopyalamak isteyebileceğiniz herhangi bir metin için kullanmaktan kaçının. Ancak, salt okunurdur statik metin, durumdaki bir değişikliği yansıtacak şekilde değişebilir. Aşağıdaki örnekte, bilgi grubu altındaki statik metin çıkış adı, yukarıdaki kök ad alanı metin kutusunda yapılan tüm değişiklikleri yansıtacak şekilde değişir.

Statik metin bilgilerini görüntülemenin iki yolu vardır.

Bir gruplandırma çakışması olmadığında statik metin, herhangi bir kapsama olmadan bir iletişim kutusunda kendi kendine açık olabilir. Bir kutunun ek satırlarının gerçekten gerekli olup olmadığına karar verin. Aşağıda gösterildiği gibi, bir grup satırı tarafından oluşturulan bölüm altında dizin yolunun görüntülenmesinin bir örneğidir:

![Metin denetimlerinde statik metin bilgisi](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Metin denetimlerinde statik metin bilgisi

Diğer gruplandırılmış alanların mevcut ve bilgilerin kapsama açısından okunabilirlik ve bir bölümün gizli olabileceği ya da gösterilebileceği bir iletişim kutusunda ( **Özellikler penceresi** açıklama bölmesinde olduğu gibi) veya benzer kullanıcı arabirimi ile tutarlı olmasını istiyorsanız statik metni bir kutunun içine yerleştirin. Bu grup kutusu tek bir kural olmalı ve şu şekilde renklendirilir `ButtonShadow` :

![Özellikler penceresi statik metin](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Özellikler penceresi statik metin

### <a name="read-only-text-box"></a>Salt okunurdur metin kutusu

Bu, kullanıcının alanın içindeki metni seçmesini ancak düzenleyemediğinden düzenleme yapmasına izin verir. Bu metin kutuları, bir dolgusuna sahip olağan 3-b ucu tarafından bir arada bulunur `ButtonShadow` .

Bir Kullanıcı, bir onay kutusunu denetleme/kaldırma ya da radyo düğmesini seçme/kaldırma gibi bir denetimi değiştiren bir metin kutusu etkin (düzenlenebilir) hale gelebilir. Örneğin, aşağıda gösterilen **Araçlar &gt; Seçenekler** sayfasında, **varsayılan kullanım** onay kutusu işaretli olmadığında **giriş sayfası** metin kutusu etkin hale gelir.

![Etkin olmayan ve etkin durumları gösteren salt okunurdur metin kutusu](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Etkin olmayan ve etkin durumları gösteren salt okunurdur metin kutusu

### <a name="using-text-in-dialogs"></a>İletişim kutularında metin kullanma

İletişim kutularında metin için anahtar yönergeleri:

- Tema olmayan iletişim kutularında metin kutuları, liste kutuları ve çerçeveler için Etiketler bir fiil ile başlar, yalnızca ilk sözcüğe ilk sermaye ve iki nokta üst üste ile biter.

    > Temalı iletişim kutularındaki metin denetimleri [Windows Masaüstü UX kılavuzlarını](/windows/desktop/uxguide/top-violations) Izler ve yardım bağlantılarında soru işaretleri dışında son noktalama işareti almaz.

- Onay kutuları ve seçenek düğmeleri için Etiketler bir fiil ile başlar, yalnızca ilk kelimeden bir başlangıç büyük harfi ve sondaki noktalama yok.

- Düğmelerin, menülerin, menü öğelerinin ve sekmelerin etiketleri her bir sözcüğe (başlık durumu) ilk büyük harfe sahiptir.

- Etiket terimleri, diğer iletişim kutularındaki benzer etiketlerle tutarlı olmalıdır.

- Mümkünse, bir yazıcıya/düzenleyiciye, uygulamaya yönelik geliştiriciye geçmeden önce metni yazın veya onaylayın.

- Tüm denetimlerin, sekme 'nin yeterli olduğu özel durumlar dışında etiketleri olmalıdır.
Uygun olduğunda yardımcı metin kullanın.

### <a name="helper-text"></a>Yardımcı metin

Kullanıcının iletişim kutusunun amacını anlamasına veya hangi eylemin gerçekleştirilecek olduğunu belirtebilmesi için iletişim kutularına dahildir. Yardım metni yalnızca, basit iletişim kutularının karışıklık önüne geçmek için gerekli olduğunda kullanılmalıdır. Yardımcı metnin iki çeşidi iletişim kutusu ve filigranıdır.

Yardımcı metin için ortak konumları izleyin ve yeni alanlara giriş yapmak için seçici olun. Yardımcı metin için genel senaryolar şunlardır:

- İletişim kutularındaki yardımcı metin, karmaşık bir iletişim kutusuyla etkileşim kurma hakkında ek bir yön sağlar.

- Hiçbir içeriğin neden görünmediğini açıklamak için boş araç pencereleri veya iletişim kutularında filigran metni.

- **Özellikler penceresi** alt kısmında olduğu gibi bir açıklama bölmesi.

- Kullanıcının başlamak için yapması gereken eylemi açıklamak için boş bir düzenleyicide filigran metni.

### <a name="dialog-helper-text"></a>İletişim kutusu Yardımcısı metni

Kullanıcı deneyimi Tasarımcısı, yardımcı metnin ne zaman uygun olduğunu belirlemenize yardımcı olabilir. Tasarımcı, yardımcı metnin ve genel içeriğinin nerede göründüğünü tanımlayabilir. Kullanıcı Yardımı gerçek metni yazabilir/düzenleyebilir.

### <a name="watermarks"></a>Filigranlar

İletişim kutuları biraz farklı filigran yönergelerinden faydalanır. Bir iletişim kutusu çok sayıda UI öğesi (Etiketler, ipucu metni, düğmeler ve metin ile diğer kapsayıcı denetimleri) ile meşgul olabileceğinden, özellikle de siyah olarak görünmeleri durumunda filigranlar koyu gri (Vscgr:) ile daha iyi zaman alabilir `ButtonShadow` . Genellikle, bir denetim içinde beyaz arka plana sahip liste kutusu gibi bir denetimin içinde görünür (Vscbir: `Window` ).

- Metin koyu gri renkte (Vscton:) görünür `ButtonShadow` . Ancak, filigran orta gri veya diğer renkli (Vsctonum: `ButtonFace` ) arka planında görünürse ve okunabilirlik hakkında sorun yaşıyorsanız, siyah metinle (vscgr:) geçin `WindowText` .

- Filigranlar, sola doğru ortalanmış veya boşaltılanmalıdır. Hizalama kararları verirken standart tasarım kurallarını uygulayın. Filigran arka planda seçilemiyor.

![Filigran metin örneği](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Filigran metin örneği

### <a name="context-specific-dynamic-text"></a>İçeriğe özel (dinamik) metin

Dinamik metin, bir iletişim kutusunda ya da etkin olmayan bir kullanıcı arabiriminde iki farklı şekilde kullanılabilir: dinamik etiket veya dinamik içerik olarak.

- Dinamik etiket: dinamik metnin yaygın kullanımı, seçili öğe için, sağdaki bir kılavuzda görüntülenen öğelerin ve özelliklerin bir listesini içeren bir iletişim kutusunda olduğu gibi açıklayıcı panellerde bulunur. Özellik kılavuzunun etiketi dinamik olabilir, böylece sol tarafta bir öğe seçildiğinde, sağdaki kılavuz o belirli öğe için bilgileri gösterir.

- Dinamik metin: Bu şekilde genel bilgileri değil, belirli bilgileri görüntülemesi gereken durumlarda yararlı olabilir, ancak bu şekilde dikkat edilmelidir.

Kullanıcıların bilgileri kopyalama yeteneğine sahip olmasını istiyorsanız, dinamik metin salt okunurdur metin alanında olmalıdır.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Düğmeler ve köprüler

### <a name="overview"></a>Genel Bakış
Düğmeler ve bağlantı denetimleri (köprüler), kullanım, ifade, boyutlandırma ve aralığa yönelik [köprülerde temel Windows Masaüstü kılavuzumuzu](/windows/desktop/uxguide/ctrl-links) izlemelidir.

### <a name="choosing-between-buttons-and-links"></a>Düğmeler ve bağlantılar arasında seçim yapma
Geleneksel olarak, işlemler için düğmeler ve köprüler gezinme için ayrılmıştır. Düğmeler her durumda kullanılabilir, ancak düğmelerin ve bağlantıların bazı koşullarda daha değiştirilebilir olmasını sağlamak için bağlantıların rolü Visual Studio 'da genişletilir.

Komut düğmelerinin ne zaman kullanılacağı:

- Birincil komutlar

- Giriş toplamak veya seçimler yapmak için kullanılan pencereleri, ikincil komutlar olsalar bile görüntüleme

- Bozucu veya geri alınamaz eylemler

- Sihirbazlar ve sayfa akışları içindeki taahhüt düğmeleri

Araç pencerelerindeki komut düğmelerinden kaçının veya etiket için ikiden fazla sözcükten fazlasına ihtiyacınız varsa. Bağlantılar daha uzun etiketlere sahip olabilir.

 Bağlantıların ne zaman kullanılacağı:

- Başka bir pencere, belge veya Web sayfasına gezinme

- Eylemin amacını açıklamaya yönelik daha uzun bir etiket veya kısa tümce gerektiren durumlar

- Bir düğmenin Kullanıcı arabirimini bir yere yapması durumunda, eylemin bozucu veya geri alınamaz olması şartıyla sıkı boşluklar

- Birçok komutun olduğu durumlarda ikincil komutları serbest bırakma

#### <a name="examples"></a>Örnekler
![Durum iletisini izleyen bilgi çubuğunda kullanılan komut bağlantıları](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Durum iletisini izleyen bilgi çubuğunda kullanılan komut bağlantıları

![CodeLens açılan penceresinde kullanılan bağlantılar](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />CodeLens açılan penceresinde kullanılan bağlantılar

![Düğmelerin çok fazla dikkat çekecek ikincil komutlar için kullanılan bağlantılar](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Düğmelerin çok fazla dikkat çekecek ikincil komutlar için kullanılan bağlantılar

### <a name="common-buttons"></a>Ortak düğmeler

#### <a name="text"></a>Metin
[Kullanıcı arabirimi metin ve terminolojisi](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)yazma yönergelerini izleyin.

#### <a name="visual-style"></a>Görsel stili

##### <a name="standard-unthemed"></a>Standart (temalı)
Visual Studio 'daki birçok düğme yardımcı program iletişim kutularında görünür ve stillendirilecektir. Bunlar, işletim sistemi tarafından dikte edildiği gibi düğmelerin standart görünümünü yansıtmalıdır.

##### <a name="themed"></a>Uygulanmış
Bazı örneklerde düğmeler, stilli Kullanıcı arabirimi içinde kullanılabilir ve bu düğmeler uygun şekilde stillendirilmiş olmalıdır. Temalı denetimler hakkında bilgi için bkz. [Iletişim kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) .

### <a name="special-buttons"></a>Özel düğmeler

#### <a name="browse-buttons"></a>Gözatmaya... düð
**[Gözatmaya...]** düğmeler, kılavuzlar, diyaloglar ve araç pencereleri ve diğer engelleyici Kullanıcı arabirimi öğelerinde kullanılır. Kullanıcılara bir değeri bir denetime doldurmasına yardımcı olan bir seçici görüntüler. Bu düğmenin uzun ve kısa iki çeşidi vardır.

![Long [gözatmaya...] düğmesi](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Long [gözatmaya...] düğmesi

![Yalnızca üç nokta kısa [...] düğmesi](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Yalnızca üç nokta kısa [...] düğmesi

Yalnızca üç nokta olan kısa düğme ne zaman kullanılır:

- Bir iletişim kutusunda birden fazla uzun **[göz at...]** düğmesi varsa, bazı alanlar göz atmaya izin veriyor gibi. Her biri için kısa **[...]** düğmesini kullanarak bu durum tarafından oluşturulan karmaşık erişim tuşlarından kaçının (**&göz atarak** aynı iletişim kutusunda **&rowte** ).

- Sıkı bir iletişim kutusunda veya uzun düğme koymak için makul bir yer yoksa.

- Düğme, kılavuz denetiminde görünür.

Düğme kullanımı için yönergeler:

- Erişim anahtarı kullanmayın. Klavye kullanarak erişmek için, kullanıcının bitişik denetimden Tab olması gerekir. Sekme sırasının, dolduracağı alandan hemen sonra gelen herhangi bir gözatmaya karşılık gelen şekilde olduğundan emin olun. İlk dönemin altında hiçbir zaman alt çizgi kullanmayın.

- Ekran okuyucularının "nokta-nokta-nokta" veya "dönem dönem dönemi" değil "tarama" olarak okuyabilmesi için, Microsoft Etkin Erişilebilirlik (MSAA) **ad** özelliğini (üç nokta dahil) **.** Yönetilen denetimler için, bu, **erişilebilir ad** özelliğinin ayarlanması anlamına gelir.

- Bir tek nokta **[...]** düğmesini, bir gözatma eylemi dışında hiçbir şey kullanmayın. Örneğin, bir **[New...]** düğmesine ihtiyacınız varsa ancak metin için yeterli yeriniz yoksa, iletişim kutusunun yeniden tasarlanması gerekir.

##### <a name="sizing-and-spacing"></a>Boyutlandırma ve Aralık
![Boyutlandırma [göz at...] düğmeleri: Standart sürüm 75x23 piksel, kısa sürüm 26x23 piksel](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Boyutlandırma [gözatmaya...] düğmeleri

![Boşluk [zat...] düğmeler: ilişkili denetim ile standart tarama düğmesi 7 piksel, ilişkili denetim ile kısa tarama düğmesi 5 piksel arasında boşluk](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Boşluk [gözatmaya...] düğmeleri

#### <a name="graphical-buttons"></a>Grafik düğmeleri
Bazı düğmelerin her zaman bir grafik görüntü kullanması ve alanları korumak ve yerelleştirme sorunlarından kaçınmak için hiçbir zaman metin içermemesi gerekir. Bunlar genellikle alan seçiciler ve diğer sıralanabilir listelerde kullanılır.

> [!NOTE]
> Kullanıcıların bu düğmelere Tab 'a (erişim anahtarı yoktur) göre sekme eklemek gerekir, bu nedenle bunları bir veya daha fazla sıraya koyun. `name`Düğmenin özelliğini, ekran okuyucularının düğme eylemini doğru bir şekilde yorumlaması için aldığı eyleme eşleyin.

| İşlev | Düğme |
| --- | --- |
| Ekle | ![Grafik "Ekle" düğmesi](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Kaldır | ![Grafik "Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Tümünü Ekle | ![Grafik "Tümünü Ekle" düğmesi](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Tümünü Kaldır | ![Grafik "Tümünü Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Yukarı Taşı | ![Grafik "yukarı taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Aşağı Taşı | ![Grafik "aşağı taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Sil | ![Grafik "Sil" düğmesi](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Boyutlandırma ve Aralık
Grafik düğmelerinin boyutlandırılması, **[göz at...]** düğmesinin kısa sürümü ile aynıdır (26x23 piksel):

![Şeffaf renkli ve görünmeyen, düğme üzerinde grafik görüntü görünümü](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Şeffaf renkli ve görünmeyen, düğme üzerinde grafik görüntü görünümü

### <a name="hyperlinks"></a>Köprüler
Köprüler, yardım konusu, kalıcı iletişim kutusu veya sihirbaz açma gibi gezinti tabanlı eylemlere uygundur. Bir komut için bir köprü kullanılıyorsa, Kullanıcı arabirimine her zaman görünür ve belirgin bir değişiklik görüntülemesi gerekir. Genel olarak, bir eyleme (Save, Cancel ve DELETE gibi) uygulanan eylemler bir düğme kullanılarak daha iyi iletilir.

#### <a name="writing-style"></a>Yazma stili
[Kullanıcı arabirimi metni Için Windows Masaüstü Kılavuzu](/windows/desktop/uxguide/text-ui)' nu izleyin. "Daha fazla bilgi edinin," "Bu konuda daha fazla bilgi ver" veya "Bu ifade hakkında yardım al" seçeneğini kullanmayın. Bunun yerine, tümcecik, yardım içeriği tarafından yanıtlanan birincil soru açısından metin bağlantısı sağlanmasına yardımcı olur. Örneğin, "**Nasıl yaparım? Sunucu Gezgini bir sunucu eklemek istiyor musunuz?**"

#### <a name="visual-style"></a>Görsel stili

- Köprüler her zaman [Vscrenkli hizmetini](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)kullanmalıdır. Köprü doğru şekilde stilsiz değilse, etkin olduğunda kırmızı yanıp sönmez veya ziyaret edildikten sonra farklı bir renk gösterir.

- Bağlantı, bir filigrandaki bir tam tümce içindeki tümce parçası değilse, denetimin bekletme durumunda alt çizgileri eklemeyin.

- Alt çizgiler, üzerine gelme üzerinde görünmemelidir. Bunun yerine, bağlantının etkin olduğu kullanıcıya geri bildirim, hafif bir renk değişikliği ve uygun bağlantı imlecine sahiptir.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Ağaç görünümleri

Ağaç görünümleri, karmaşık listeleri üst-alt gruplar halinde düzenlemek için bir yol sağlar. Bir Kullanıcı, temel alınan alt öğeleri göstermek veya gizlemek için üst grupları genişletebilir veya daraltabilir. Bir ağaç görünümündeki her öğe, başka bir eylem sağlamak için seçilebilir.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Ağaç görünümü görsel stili

#### <a name="expanders"></a>Genişleticileri
Ağaç görünüm denetimleri Windows ve Visual Studio tarafından kullanılan genişletici tasarımına uymalıdır. Her düğüm, temeldeki öğeleri göstermek veya gizlemek için bir genişletici denetimi kullanır. Genişletici denetimi kullanmak, Windows ve Visual Studio içinde farklı ağaç görünümleriyle karşılaşabilirler kullanıcılar için tutarlılık sağlar.

![Doğru: genişletici denetimi kullanarak ağaç görünümü düğümünün doğru stili](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Doğru: genişletici denetimi kullanarak ağaç görünümü düğümünün doğru stili

![Yanlış: ağaç görünümü düğümünün hatalı stili](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Yanlış: ağaç görünümü düğümünün hatalı stili

#### <a name="selection"></a>Seçim
Ağaç görünümü içinde bir düğüm seçildiğinde, vurgu, ağaç görünümü denetiminin tam genişliğine genişlemelidir. Bu, kullanıcıların hangi öğeyi seçtikleri açıkça belirlemesine yardımcı olur. Seçim renkleri geçerli Visual Studio temasını yansıtmalıdır.

![Doğru: seçili düğümün vurgulaması, ağaç görünümü denetiminin genişliğinin tamamına uyar.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Doğru: seçili düğümün vurgulaması, ağaç görünümü denetiminin genişliğinin tamamına uyar.

![Yanlış: seçili düğümün vurgulaması, ağaç görünümü denetiminin genişliğinin tamamına uymuyor.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Yanlış: seçili düğümün vurgulaması, ağaç görünümü denetiminin genişliğinin tamamına uymuyor.

#### <a name="icons"></a>Simgeler
Simgeler yalnızca öğeler arasındaki farkları görsel olarak tanımlamaya yardımcı olmaları durumunda ağaç görünümü denetimlerinde kullanılmalıdır. Genel olarak, simgeler yalnızca simgelerin öğe türlerini ayırt etmek için bilgi taşıyan heterojen listelerde kullanılmalıdır. Simgeleri kullanarak homojen sıklıkla gürültü olarak görülebileceği ve kaçınılması gereken bir liste. Bu durumda, Grup simgesi (üst) içindeki öğelerin türünü de aktarabilirsiniz. Bu kuralın istisnası, simgenin dinamik olması ve durumu göstermek için kullanılması durumunda olur.

#### <a name="scroll-bars"></a>Kaydırma çubukları
İçerik ağaç görünümü denetimi içine sığıyorsa, kaydırma çubukları her zaman gizli olmalıdır. Kaydırma çubuklarının gizlenmesi veya kaydırılabilir bir pencerede yarı saydam olması ve ağaç görünümünü içeren pencere odağa sahip olduğunda ya da ağaç görünümünün üzerine gelme durumunda gösterilmesi kabul edilebilir.

![İçerik ağaç görünümü denetiminin sınırlarını aştığından hem dikey hem de yatay kaydırma çubukları görüntülenir.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />İçerik ağaç görünümü denetiminin sınırlarını aştığından hem dikey hem de yatay kaydırma çubukları görüntülenir.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Ağaç görünümü etkileşimleri

#### <a name="context-menus"></a>Bağlam menüleri
Ağaç görünümü düğümü, bir bağlam menüsündeki alt menü seçeneklerini açığa çıkarır. Genellikle, bu, bir Kullanıcı bir öğeye sağ tıklandığında veya seçili öğe ile Windows klavyesindeki menü tuşuna basıldığında oluşur. Düğümün odağı kazanması ve seçili olması önemlidir. Bu, kullanıcının alt menünün hangi öğeye ait olduğunu belirlemesine yardımcı olur.

![Bağlam menüsünü oluşturan öğe, kullanıcıya hangi öğenin seçili olduğunu bildirmek için odak kazanır.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />Bağlam menüsünü oluşturan öğe, kullanıcıya hangi öğenin seçili olduğunu bildirmek için odak kazanır.

#### <a name="keyboard"></a>Klavye
Ağaç görünümü, öğeleri seçme ve klavyeyi kullanarak düğümleri genişletme/daraltma yeteneği sağlamalıdır. Bu, gezinmede erişilebilirlik gereksinimlerimizi karşıladığından emin olmanızı sağlar.

##### <a name="tree-view-control"></a>Ağaç görünümü denetimi
Visual Studio ağaç denetimleri ortak klavye gezintisini izlemelidir:

- **Yukarı ok:** Ağacı yukarı taşıyarak öğeleri seçme

- **Aşağı ok:** Ağacı aşağı taşıyarak öğeleri seçin

- **Sağ ok:** Ağaçtaki bir düğümü genişletme

- **Sol ok:** Ağaçtaki bir düğümü daraltma

- **Anahtar girin:** Seçili öğeyi başlatın, yükleyin, yürütün

##### <a name="trid-tree-view-and-grid-view"></a>ID (ağaç görünümü ve kılavuz görünümü)
Bir ID denetimi, Kılavuz içindeki ağaç görünümünü içeren karmaşık bir denetimdir. Ağaç genişletme, daraltma ve gezinme, aşağıdaki eklemelerle aynı klavye komutlarının ağaç görünümüyle aynı olması gerekir:

- **Sağ ok:** Bir düğümü genişletin. Düğüm genişletildikten sonra sağ taraftaki en yakın sütuna gidilmeye devam edilmelidir. Gezinme, satırın sonunda durmalıdır.

- **Sekme:** Sağ taraftaki en yakın hücreye gider.  Satırın sonunda, gezinti sonraki satıra devam eder.

- **SHIFT + TAB:** Soldaki en yakın hücreye gider.  Satırın başlangıcında, gezinti önceki satırda en sağdaki hücreye devam eder.

![Visual Studio 'da bir ID denetimi](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Visual Studio 'da bir ID denetimi
