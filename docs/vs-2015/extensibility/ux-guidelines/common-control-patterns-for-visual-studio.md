---
title: Yaygın Denetim Desenleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd2b2723a5ecfe66e9471cfea1e8eb55ed7ced59
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547452"
---
# <a name="common-control-patterns-for-visual-studio"></a>Visual Studio İçin Yaygın Denetim Desenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Ortak denetimler

### <a name="overview"></a>Genel Bakış
 Ortak denetimler, Visual Studio 'daki Kullanıcı arabiriminin çoğunu yapar. Visual Studio arabiriminde kullanılan çoğu ortak denetim, [Windows Masaüstü etkileşim yönergeleri](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx)' ni izlemelidir. Bu belge, Visual Studio 'ya özeldir ve bu Windows kılavuzlarını geliştiren özel durumları veya ayrıntıları içerir.

#### <a name="common-controls-in-this-topic"></a>Bu konudaki ortak denetimler

- [Çubuklarını](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Giriş alanları](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Birleşik giriş kutuları ve açılan listeler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Onay kutuları](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Radyo düğmeleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Grup çerçeveleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Metin denetimleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Düğmeler ve köprüler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Ağaç görünümleri](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Görsel stil
 Stil oluşturma denetimlerinde göz önünde bulundurmanız gereken ilk şey, denetimlerin temalı Kullanıcı arabiriminde kullanılıp kullanılmayacağını belirtir. Standart Kullanıcı arabirimindeki denetimler, temalı Kullanıcı arabirimi ve [normal Windows Masaüstü stilini](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx)izlemelidir, yani bu değerler yeniden Şablonsuz ve varsayılan denetim görünümünde görünür olmalıdır.

- **Standart (yardımcı program) iletişim kutuları:** temalı değildir. Yeniden şablon kullanmayın. Temel denetim stili varsayılanlarını kullanın.

- **Araç pencereleri, belge düzenleyicileri, tasarım yüzeyleri ve temalı iletişim kutuları:** Renk hizmetini kullanarak özelleştirilmiş temalı görünümü kullanın.

### <a name="scrollbars"></a><a name="BKMK_Scrollbars"></a>Çubuklarını
 Kaydırma çubukları, kod Düzenleyicisi gibi içerik bilgileriyle genişletmedikleri sürece [Windows kaydırma çubukları için ortak etkileşim düzenlerini](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) izlemelidir.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Giriş alanları
 Tipik etkileşim davranışı için, [metin kutuları Için Windows Masaüstü yönergeleri](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx)' ni izleyin.

#### <a name="visual-style"></a>Görsel stil

- Giriş alanları, yardımcı program iletişim kutularında stilleştirmemelidir. Denetimin iç temel stilini kullanın.

- Temalı giriş alanları yalnızca temalı iletişim kutularında ve araç penceresinde kullanılmalıdır.

#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimler

- Salt okuma alanları gri (devre dışı) bir arka plana, ancak varsayılan (etkin) ön plana sahip olacaktır.

- Gerekli alanlar, **\<Required>** içindeki filigranlara sahip olmalıdır. Nadir durumlar haricinde arka planın rengini değiştirmemelisiniz.

- Hata doğrulaması: bkz. [Visual Studio Için bildirimler ve Ilerleme durumu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Giriş alanları, gösterilen pencerenin genişliğine uyacak şekilde değil, içerik sığacak şekilde boyutlandırılmalıdır, ya da bir yol gibi uzun bir alanın uzunluğuna göre daha fazla eşleşir. Uzunluk, alanda kaç karaktere izin verileceğini gösteren sınırlamalar kullanıcısına bir gösterge olabilir.

     ![Hatalı giriş alanı denetim genişliği](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl") **yanlış giriş alanı uzunluğu: ad bu uzun olacaktır.**

     ![Doğru giriş alanı denetim genişliği](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl") **doğru giriş alanı uzunluğu: giriş alanı, beklenen içerik için makul bir genişliktir.**

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Birleşik giriş kutuları ve açılan listeler
 Tipik etkileşim davranışı için, [açılan listeler ve Birleşik giriş kutuları Için Windows Masaüstü yönergeleri](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx)' ni izleyin.

#### <a name="visual-style"></a>Görsel stil

- Yardımcı program iletişim kutularında denetimi yeniden şablon olarak ayarlamayın. Denetimin iç temel stilini kullanın.

- Temalı Kullanıcı arabiriminde, Birleşik giriş kutuları ve açılan kutular, denetimlerin standart temalarını izler.

#### <a name="layout"></a>Layout
 Birleşik giriş kutuları ve açılan listeler, gösterilen pencerenin genişliğine sığması için veya bir yol gibi uzun bir alanın uzunluğuna göre değil, içeriğe uyacak şekilde boyutlandırılmalıdır.

 ![Yanlış bırakma&#45;aşağı düzen](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")

 **Açılan denetim için yanlış alan uzunluğu**

 ![&#45;aşağı doğru bırakma düzeni](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707-04_CorrectDropDownLayout")

 **Açılan denetim için alan uzunluğunu doğru bırak**

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Onay kutuları
 Tipik etkileşim davranışı için, [onay kutuları Için Windows Masaüstü yönergeleri](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx)' ni izleyin.

#### <a name="visual-style"></a>Görsel stil

- Yardımcı program iletişim kutularında denetimi yeniden şablon olarak ayarlamayın. Denetimin iç temel stilini kullanın.

- Temalı Kullanıcı arabiriminde, onay kutuları denetimlerin standart temalarını izler.

#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimler

- Onay kutusuyla etkileşim hiçbir koşulda bir iletişim kutusu içermemelidir veya başka bir alana gitmelidir.

- Metnin ilk satırının taban çizgisiyle birlikte onay kutularını hizalayın.

     ![Yanlış onay kutusu hizalaması](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign") **yanlış onay kutusu hizalaması: onay kutusu metin üzerinde ortalandı.**

     ![Doğru onay kutusu hizalaması](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign") **doğru onay kutusu hizalaması: onay kutusu, metnin ilk satırının taban çizgisiyle hizalanır.**

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Radyo düğmeleri
 Tipik etkileşim davranışı için, [radyo düğmeleri Için Windows Masaüstü yönergeleri](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx)' ni izleyin.

#### <a name="visual-style"></a>Görsel stil
 Yardımcı program iletişim kutularında radyo düğmelerine stil kullanmayın. Denetimin iç temel stilini kullanın.

#### <a name="specialized-interactions"></a>Özelleştirilmiş etkileşimler
 Radyo seçeneklerini kapsamak için bir grup çerçevesinin kullanılması gerekli değildir.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Grup çerçeveleri
 Tipik etkileşim davranışı için, [Grup çerçevelerine yönelik Windows Masaüstü yönergelerini](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx)izleyin.

#### <a name="visual-style"></a>Görsel stil
 Yardımcı program iletişim kutularında, Grup çerçevelerini stillemeyin. Denetimin iç temel stilini kullanın.

#### <a name="layout"></a>Layout

- Daha sıkı bir düzende grup ayrım yapmanız gerekmedikçe radyo seçeneklerini kapsamak için bir grup çerçevesinin kullanılması gerekli değildir.

- Hiç bir grup çerçevesini tek bir denetim için kullanmayın.

- Bazen grup çerçevesi kapsayıcısı yerine yatay bir kural kullanılması kabul edilebilir.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Metin denetimleri

### <a name="labels"></a>Etiketler

#### <a name="active-label-state"></a>Etkin etiket durumu

##### <a name="utility-standard-dialogs"></a>Yardımcı program (Standart) iletişim kutuları)

- Genel olarak, denetim etiketleri için Windows Masaüstü Kılavuzu ' nu izleyin.

- Yardımcı program iletişim kutularında Etiketler, standart ortam yazı tipinde ve metin renginde kalın olmayan görünmelidir. Bkz. [Visual Studio Için yazı tipleri ve biçimlendirme](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

- Üç nokta, her zaman etiketleri izlemelidir.

##### <a name="signature-themed-dialogs"></a>İmza (temalı) iletişim kutuları)
 Etiket denetimleri kalın veya açık gri olabilir.

#### <a name="disabled-label-state"></a>Devre dışı etiket durumu
 Etiketler ilişkili oldukları denetimin görünümünü yansıtmalıdır. Örneğin, ilişkili denetim devre dışıysa, etiket gri ve devre dışı görünmelidir. Bu genellikle işletim sistemi tarafından işlenir ve özel bir işleme gerektirmez.

#### <a name="dynamic-labels"></a>Dinamik Etiketler
 Dinamik Etiketler, geçerli seçime göre değişir. Mümkün olduğunda, kullanıcının görüntülenen bilgilerin genel bilgilerle değil belirli bir seçimle ilgili olduğunu anlamalarına yardımcı olmak için ana/ayrıntı düzenlerindeki dinamik etiketleri kullanın.

 ![Dinamik içerikle kullanılan dinamik etiket](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702-01_DynamicLabel")

 **Dinamik içerik ile kullanılan dinamik etiket örneği**

#### <a name="instructional-text"></a>Yönerge metni
 Bazı arabirim öğeleri, kullanıcının UI amacını anlamasına veya hangi eylemin gerçekleştirilecek olduğunu belirtebilmesi için yol gösterici metinden faydalanır.

- Yol gösterici metin, iletişim kutularının en üstünde ortaktır, ancak karmaşık denetim gruplandırmasına talimat vermek için diğer alanlarda görünebilirler.

- Yönerge metni etkileşimli değildir, ancak yardım konularına yönelik köprüler de içerebilir.

- Eğitici metin ve yalnızca gerektiğinde kullanın.

##### <a name="formatting"></a>Biçimlendirme
 Yönerge metni, ortam yazı tipi, standart (temalı olmayan) denetim metni olmalıdır. Bkz. [Visual Studio Için yazı tipleri ve biçimlendirme](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Eğitici metin yazma hakkında ayrıntılı bilgi için bkz. [UI metni ve terimleri](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Yönerge metni biçimlendirme](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702-02_InstructionalTextFormatting")

 **Visual Studio iletişim kutusunda yönerge metni**

#### <a name="informational-text"></a>Bilgilendirici metin
 Bilgilendirici metin, kullanıcıya ek bilgiler sağlayan metindir. Statik veya dinamik olabilir ya da bildirim olarak kullanılabilir. Her zaman salt okunurdur, ancak kullanıcının bilgileri kopyalayabilme özelliği olması faydalı ise, dinamik metin salt okunurdur metin alanı gibi bir denetim kapsayıcısına yerleştirilmelidir.

##### <a name="dynamic-context-specific-text"></a>Dinamik (içeriğe özgü) metin
 Dinamik bilgi metni, Kullanıcı odağa geçtiğinde olduğu gibi, bağlama göre değişir. Genellikle, her zaman dinamik içerik dinamik bir etiketle eşleştirilmelidir.

 ![Dinamik bilgi metni](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702-03_InformationalDynamicText")

 **Dinamik bilgilendirici metin, bağlama göre değişir.**

##### <a name="formatting"></a>Biçimlendirme
 Salt okuma metin alanlarını görüntülemenin iki yolu vardır: doğrudan kullanıcı arabirimi yüzeyine (yukarıya bakın) veya bir grup çerçevesi ya da metin kutusu gibi başka bir denetimin içinde yer alır. Duruma bağlı olarak doğru olur. Salt okuma bilgilerinin nasıl gösterileceğini öğrenmek için özellik tasarımcısına kadar.

 Metin, salt okunurdur metin kutusu içinde olabilir. Bu genellikle içeriğin seçilebileceğini ve kopyalanamayacağını, ancak düzenlenemeyeceğini gösterir.

 ![Yalnızca okuma&#45;alanları için bilgilendirici metin biçimlendirmesi](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702-04_InformationalFormatting")

 **Salt okuma alanları için bilgilendirici metin biçimlendirmesi**

#### <a name="watermarks"></a>Filigranlar
 Bu ifade aynı olsa da, Filigranlar ve eğitici metin arasındaki fark, Denetim/pencere boş olmadığında filigranların içerikle değiştirilmesinin yanı sıra eğitici metnin her zaman görünür kaldığı bir yerdir.

 Bir pencere veya denetim boş olduğunda filigranlar kullanılmalıdır. Bu, alanı doldurmak için ne yapılması gerektiğini belirtir ve Sürükle kaynağı gibi ilgili pencereleri açmak için eylem bağlantıları içerebilir.

##### <a name="visual-style"></a>Görsel stil

- Filigranlar pencere içinde yatay olarak ortalanmalıdır.

- Filigranlar, sola hizalı değil, ortahizalı olmalıdır.

- Filigranlar dikey olarak ortalanmış veya alanın en üstüne konumlandırılmış olabilir. Alanın en üstüne konumlandırıldığında, filigranın üst tarafına doğru olması için yeterli alan olması gerekir.

- `Environment.GrayText`Renk belirteci ve standart ortam yazı tipini kullanın. Köprüler standart köprü paylaşılan belirteçlerini kullanmalıdır: `Environment.PanelHyperlink` , `Environment.PanelHyperlinkHover` , `Environment.PanelHyperlinkPressed` , ve `Environment.PanelHyperlinkDisabled` .

- Arka planda filigranlar seçilemez

- Mümkünse, kullanıcının kullanmaya başlamanıza yardımcı olmak için filigrandaki bağlantıları ekleyin.

  ![Tasarımcı penceresinde filigran metni](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702-05_Watermark1")

  ![Bir araç penceresinde filigran metni](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702-06_Watermark2")

  **Visual Studio 'da filigran metni örnekleri**

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Düğmeler ve köprüler

### <a name="overview"></a>Genel Bakış
 Düğmeler ve bağlantı denetimleri (köprüler), kullanım, ifade, boyutlandırma ve aralığa yönelik [köprülerde temel Windows Masaüstü kılavuzumuzu](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) izlemelidir.

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
 ![Durum iletisini izleyen bilgi çubuğu komut bağlantıları](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703-01_CommandLinkInfobar")

 **Durum iletisini izleyen bilgi çubuğunda kullanılan komut bağlantıları**

 ![CodeLens açılan penceresinde kullanılan bağlantılar](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703-02_LinksInCodeLens")

 **CodeLens açılan penceresinde kullanılan bağlantılar**

 ![İkincil komutlar olarak kullanılan bağlantılar](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")

 **Düğmelerin çok fazla dikkat çekecek ikincil komutlar için kullanılan bağlantılar**

### <a name="common-buttons"></a>Ortak düğmeler

#### <a name="text"></a>Metin
 [Kullanıcı arabirimi metin ve terminolojisi](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)yazma yönergelerini izleyin.

#### <a name="visual-style"></a>Görsel stil

##### <a name="standard-dialogs"></a>Standart iletişim kutuları
 Visual Studio 'daki birçok düğme standart iletişim kutularında görünür ve stillendirilecektir. Bunlar, işletim sistemi tarafından dikte edildiği gibi düğmelerin standart görünümünü yansıtmalıdır.

##### <a name="themed"></a>Uygulanmış
 Bazı örneklerde düğmeler, stilli Kullanıcı arabirimi içinde kullanılabilir ve bu düğmeler uygun şekilde stillendirilmiş olmalıdır. Temalı denetimler hakkında bilgi için bkz. [Iletişim kutuları](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) .

### <a name="special-buttons"></a>Özel düğmeler

#### <a name="browse-buttons"></a>Gözatmaya... düğmeler
 **[Gözatmaya...]** düğmeler, kılavuzlar, diyaloglar ve araç pencereleri ve diğer engelleyici Kullanıcı arabirimi öğelerinde kullanılır. Kullanıcılara bir değeri bir denetime doldurmasına yardımcı olan bir seçici görüntüler. Bu düğmenin uzun ve kısa iki çeşidi vardır.

 ![Uzun &#91;tarama... &#93; düğmesi](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703-04_BrowseLong")

 **Long [gözatmaya...] düğmesi**

 ![Kısa üç nokta&#45;yalnızca &#91;araştır... &#93; düğmesi](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703-05_BrowseShort")

 **Yalnızca üç nokta kısa [...] düğmesi**

 Yalnızca üç nokta olan kısa düğme ne zaman kullanılır:

- Bir iletişim kutusunda birden fazla uzun **[göz at...]** düğmesi varsa (örneğin, çok sayıda alan göz atmaya izin verir). Her biri için kısa **[...]** düğmesini kullanarak bu durum tarafından oluşturulan karmaşık erişim tuşlarından kaçının (**&göz atarak** aynı iletişim kutusunda **&rowte** ).

- Sıkı bir iletişim kutusunda veya uzun düğme koymak için makul bir yer yoksa.

- Düğme, kılavuz denetiminde görünür.

  Düğme kullanımı için yönergeler:

- Erişim anahtarı kullanmayın. Klavye kullanarak erişmek için, kullanıcının bitişik denetimden Tab olması gerekir. Sekme sırasının, dolduracağı alandan hemen sonra gelen herhangi bir gözatmaya karşılık gelen şekilde olduğundan emin olun. İlk dönemin altında hiçbir zaman alt çizgi kullanmayın.

- Ekran okuyucularının "nokta-nokta-nokta" veya "dönem dönem dönemi" değil "tarama" olarak okuyabilmesi için, Microsoft Etkin Erişilebilirlik (MSAA) **ad** özelliğini (üç nokta dahil) **.** Yönetilen denetimler için, bu, **erişilebilir ad** özelliğinin ayarlanması anlamına gelir.

- Bir tek nokta **[...]** düğmesini, bir gözatma eylemi dışında hiçbir şey kullanmayın. Örneğin, bir **[New...]** düğmesine ihtiyacınız varsa ancak metin için yeterli yeriniz yoksa, iletişim kutusunun yeniden tasarlanması gerekir.

##### <a name="sizing-and-spacing"></a>Boyutlandırma ve Aralık
 ![Boyutlandırma &#91;gözden geçirme... &#93; düğmeleri](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703-06_BrowseSizing")

 **Boyutlandırma [gözatmaya...] düğmeleri**

 ![Aralık &#91;gözatmaya... &#93; düğmeleri](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703-07_BrowseSpacing")

 **Boşluk [gözatmaya...] düğmeleri**

#### <a name="graphical-buttons"></a>Grafik düğmeleri
 Bazı düğmelerin her zaman bir grafik görüntü kullanması ve alanları korumak ve yerelleştirme sorunlarından kaçınmak için hiçbir zaman metin içermemesi gerekir. Bunlar genellikle alan seçiciler ve diğer sıralanabilir listelerde kullanılır.

> [!NOTE]
> Kullanıcıların bu düğmelere Tab 'a (erişim anahtarı yoktur) göre sekme eklemek gerekir, bu nedenle bunları bir veya daha fazla sıraya koyun. Düğmenin Name özelliğini, ekran okuyucularının düğme eylemini doğru bir şekilde yorumlayabilmesi için aldığı eyleme eşleyin.

|Name|Görüntü|
|-|-|
|Ekle|![Grafik "Ekle" düğmesi](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703-08_ButtonAdd")|
|Kaldır|![Grafik "Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703-09_ButtonRemove")|
|Tümünü Ekle|![Grafik "Tümünü Ekle" düğmesi](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703-10_ButtonAddAll")|
|Tümünü Kaldır|![Grafik "Tümünü Kaldır" düğmesi](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703-11_ButtonRemoveAll")|
|Yukarı Taşı|![Grafik "yukarı taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703-12_ButtonMoveUp")|
|Aşağı Taşı|![Grafik "aşağı taşı" düğmesi](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703-13_ButtonMoveDown")|
|Sil|![Grafik "Sil" düğmesi](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703-14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Boyutlandırma ve Aralık
 Grafik düğmelerinin boyutlandırılması, **[göz at...]** düğmesinin kısa sürümü ile aynıdır (26x23 piksel):

 ![Saydam rengi gösteren ve içermeyen düğme](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")

 **Şeffaf renkli ve görünmeyen, düğme üzerinde grafik görüntü görünümü**

### <a name="hyperlinks"></a>Köprüler
 Köprüler, yardım konusu, kalıcı iletişim kutusu veya sihirbaz açma gibi gezinti tabanlı eylemlere uygundur. Bir komut için bir köprü kullanılıyorsa, Kullanıcı arabirimine her zaman görünür ve belirgin bir değişiklik görüntülemesi gerekir. Genel olarak, bir eyleme (Kaydet, Iptal ve silme gibi) yapılan eylemler bir düğme kullanılarak daha iyi iletilir.

#### <a name="writing-style"></a>Yazma stili
 [Kullanıcı arabirimi metni Için Windows Masaüstü Kılavuzu](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx)' nu izleyin. "Daha fazla bilgi edinin," "Bu konuda daha fazla bilgi ver" veya "Bu ifade hakkında yardım al" seçeneğini kullanmayın. Bunun yerine, tümcecik, yardım içeriği tarafından yanıtlanan birincil soru açısından metin bağlantısı sağlanmasına yardımcı olur. Örneğin, "**Nasıl yaparım? Sunucu Gezgini bir sunucu eklemek istiyor musunuz?**"

#### <a name="visual-style"></a>Görsel stil

- Köprüler her zaman [Vscrenkli hizmetini](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService)kullanmalıdır. Köprü doğru şekilde stilsiz değilse, etkin olduğunda kırmızı yanıp sönmez veya ziyaret edildikten sonra farklı bir renk gösterir.

- Bağlantı, bir filigrandaki gibi tam tümce içindeki bir cümle parçası değilse, denetimin bekletme durumunda alt çizgileri eklemeyin.

- Alt çizgiler, üzerine gelme üzerinde görünmemelidir. Bunun yerine, bağlantının etkin olduğu kullanıcıya geri bildirim, hafif bir renk değişikliği ve uygun bağlantı imlecine sahiptir.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Ağaç görünümleri

### <a name="overview"></a>Genel Bakış
 Ağaç görünümleri, karmaşık listeleri üst-alt gruplar halinde düzenlemek için bir yol sağlar. Bir Kullanıcı, temel alınan alt öğeleri göstermek veya gizlemek için üst grupları genişletebilir veya daraltabilir. Bir ağaç görünümündeki her öğe, başka bir eylem sağlamak için seçilebilir.

 Bu konu, ağaç görünümlerinin kabul edilebilir kullanımını, uygun tasarımını ve işlevselliğini kapsar.

#### <a name="in-this-topic"></a>Bu konuda

- [Görsel stil](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [Etkileşimler](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Görsel stil

#### <a name="expanders"></a>Genişleticileri
 Ağaç görünüm denetimleri Windows ve Visual Studio tarafından kullanılan genişletici tasarımına uymalıdır. Her düğüm, temeldeki öğeleri göstermek veya gizlemek için bir genişletici denetimi kullanır. Genişletici denetimi kullanmak, Windows ve Visual Studio içinde farklı ağaç görünümleriyle karşılaşabilirler kullanıcılar için tutarlılık sağlar.

 ![Doğru ağaç görünümü denetimi](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Doğru: genişletici denetimi kullanarak ağaç görünümü düğümünün doğru stili**

 ![Ağaç görünümü düğümleri yanlış](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705-2_TreeViewIncorrect1")

 **Yanlış: ağaç görünümü düğümünün hatalı stili**

#### <a name="selection"></a>Seçim
 Ağaç görünümü içinde bir düğüm seçildiğinde, vurgu, ağaç görünümü denetiminin tam genişliğine genişlemelidir. Bu, kullanıcıların hangi öğeyi seçtikleri açıkça belirlemesine yardımcı olur. Seçim renkleri geçerli Visual Studio temasını yansıtmalıdır.

 ![Doğru ağaç görünümü denetimi](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Doğru: seçili düğümün vurgulaması, ağaç görünümü denetiminin genişliğinin tamamına uyar.**

 ![Ağaç görünümü vurgulaması yanlış](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705-3_TreeViewIncorrect2")

 **Yanlış: seçili düğümün vurgulaması, ağaç görünümü denetiminin genişliğinin tamamına uymuyor.**

#### <a name="icons"></a>Simgeler
 Simgeler yalnızca öğeler arasındaki farkları görsel olarak tanımlamaya yardımcı olmaları durumunda ağaç görünümü denetimlerinde kullanılmalıdır. Genel olarak, simgeler yalnızca simgelerin öğe türlerini ayırt etmek için bilgi taşıyan heterojen listelerde kullanılmalıdır. Simgeleri kullanarak homojen sıklıkla gürültü olarak görülebileceği ve kaçınılması gereken bir liste. Bu durumda, Grup simgesi (üst) içindeki öğelerin türünü de aktarabilirsiniz. Bu kuralın istisnası, simgenin dinamik olması ve durumu göstermek için kullanılması durumunda olur.

#### <a name="scroll-bars"></a>Kaydırma çubukları
 İçerik ağaç görünümü denetimi içine sığıyorsa, kaydırma çubukları her zaman gizli olmalıdır. Kaydırma çubuklarının gizlenmesi veya kaydırılabilir bir pencerede yarı saydam olması ve ağaç görünümünü içeren pencere odağa sahip olduğunda ya da ağaç görünümünün üzerine gelme durumunda gösterilmesi kabul edilebilir.

 ![Kaydırma çubuklarının bulunduğu ağaç görünümü](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705-4_Scrollbars")

 **İçerik ağaç görünümü denetiminin sınırlarını aştığından hem dikey hem de yatay kaydırma çubukları görüntülenir.**

### <a name="interactions"></a><a name="BKMK_TreeViewInteractions"></a>Lerinizin

#### <a name="context-menus"></a>Bağlam menüleri
 Ağaç görünümü düğümü, bir bağlam menüsündeki alt menü seçeneklerini açığa çıkarır. Genellikle, bu, bir Kullanıcı bir öğeye sağ tıklandığında veya seçili öğe ile Windows klavyesindeki menü tuşuna basıldığında oluşur. Düğümün odağı kazanması ve seçili olması önemlidir. Bu, kullanıcının alt menünün hangi öğeye ait olduğunu belirlemesine yardımcı olur.

 ![Seçili ağaç düğümü ve bağlam menüsü](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705-5_ContextMenu")

 **Bağlam menüsünü oluşturan öğe, kullanıcıya hangi öğenin seçili olduğunu bildirmek için odak kazanır.**

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
 Bir ID denetimi, kılavuz içinde ağaç görünümü içeren karmaşık bir denetimdir. Ağaç genişletme, daraltma ve gezinme, aşağıdaki eklemelerle aynı klavye komutlarının ağaç görünümüyle aynı olması gerekir:

- **Sağ ok:** Bir düğümü genişletin. Düğüm genişletildikten sonra sağ taraftaki en yakın sütuna gidilmeye devam edilmelidir. Gezinme, satırın sonunda durmalıdır.

- **Sekme:** Sağ taraftaki en yakın hücreye gider.  Satırın sonunda, gezinti sonraki satıra devam eder.

- **SHIFT + TAB:** Soldaki en yakın hücreye gider.  Satırın başlangıcında, gezinti önceki satırda en sağdaki hücreye devam eder.

  ![Visual Studio 'da ID denetimi](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705-6_Trid")

  **Visual Studio 'da bir ID denetimi**
