---
title: Görsel Stüdyo için UX Essentials | Microsoft Dokümanlar
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6c329eda477d77ab73be2ad913ac18d67ff3c08
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698337"
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio İçin UX Temel Bileşenleri

## <a name="best-practices"></a>En iyi uygulamalar

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Visual Studio ortamında tutarlı olun.

- Kabuk içindeki mevcut [etkileşim modellerini](interaction-patterns-for-visual-studio.md) izleyin.

- Tasarım özellikleri kabuk görsel dil ve [işçilik gereksinimleri](evaluation-tools-for-visual-studio.md)ile tutarlı olması.

- Paylaşılan komutları ve denetimleri var olduklarında kullanın.

- Visual Studio hiyerarşisini ve bağlamı nasıl oluşturduğunu ve UI'yi nasıl yönlendirdiğini anlayın.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. Yazı tipleri ve renkler için ortam hizmetini kullanın.

- Kullanıcı Arabirimi, Seçenekler iletişim kutusundaki Yazı Tipleri ve Renkler sayfasında özelleştirme için açıkta olmadığı sürece geçerli [ortam yazı tipi](fonts-and-formatting-for-visual-studio.md) ayarına saygı göstermelidir.

- Kullanıcı Bira Birimi öğeleri, paylaşılan ortam belirteçlerini veya özel belirteçleri kullanarak [VSColor Hizmetini](colors-and-styling-for-visual-studio.md)kullanmalıdır.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. Tüm görüntüleri yeni VS stiliyle tutarlı hale getirin.

- Simgeler, glifler ve diğer grafikler için Visual Studio tasarım ilkelerini izleyin.

- Metni grafik öğelerine yerleştirmeyin.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Kullanıcı merkezli bir bakış açısıyla tasarım.

- Görev akışını, içindeki tek tek özelliklerden önce oluşturun.

- Kullanıcılarınızı tanımak ve bu bilgileri spec açık olun.

- UI'yi gözden geçirirken, tüm deneyimi ve ayrıntıları değerlendirin.

- UI'nizi, yerel veya dilden bağımsız olarak işlevsel ve çekici kalacak şekilde tasarla.

## <a name="screen-resolution"></a>Ekran çözünürlüğü

### <a name="minimum-resolution"></a>En düşük çözünürlük

- Visual Studio 2015 için minimum çözünürlük **1280x720'dir.** Bu, en iyi kullanıcı deneyimi olmasa da Visual Studio'nun bu çözünürlükte kullanılmasının *mümkün* olduğu anlamına gelir. 1280x720'den daha düşük çözünürlüklerde tüm yönleriyle kullanılabilir olacağının garantisi yoktur.

- Visual Studio için hedef çözünürlük **1366x768.** Bu, *iyi* bir kullanıcı deneyimi vaat ettiğimiz en düşük çözünürlük.

- İlk iletişim yüksekliği **700 pikselden daha küçük**olmalıdır, bu nedenle 96 dpi'deki IDE çerçevesinin minimum çözünürlüğüne sığar.

### <a name="high-density-displays"></a>Yüksek yoğunluklu ekranlar
 Visual Studio'daki UI, Windows'un kutunun dışında desteklediği tüm DPI ölçekleme faktörlerinde iyi çalışmalıdır: %150, %200 ve %250.

## <a name="anti-patterns"></a>Anti-desenler
 Visual Studio, yönergelerimize ve en iyi uygulamaları takip eden birçok ui örneği içerir. Tutarlı olmak amacıyla, geliştiriciler genellikle kendi inşa ettiklerine benzer ürün ui tasarım desenlerinden ödünç alın. Bu, kullanıcı etkileşimi ve görsel tasarımda tutarlılığı teşvik etmemize yardımcı olan iyi bir yaklaşım olsa da, zaman zaman zamanlama kısıtlamaları veya hata önceliklendirmesi nedeniyle yönergelerimize uymayan birkaç ayrıntı içeren gemi özellikleri yaparız. Bu gibi durumlarda, ekiplerin visual studio ortamında kötü veya tutarsız uI'yi çoğalttığı için bu "anti-desenlerden" birini kopyalamalarını istemeyiz.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Varsayılan olarak hata durumunda gösterilen gerekli alanlar/ayarlar

#### <a name="feature-team-goals"></a>Özellik takım hedefleri

- Kullanıcıları, yapılandırılması gereken bir öğe ekledikleri konusunda uyarın.

- Kullanıcının dikkatini giriş gereken alanlara çekin.

#### <a name="anti-pattern-solution"></a>Anti-desen çözeltisi
 Kullanıcı bir eylem başlattıktan sonra ve görevi tamamlamadan önce, yapılandırma gereken alanların yanına hemen kritik durdurma simgeleri yerleştirin.

#### <a name="example-manifest-designer-declarations"></a>Örnek: Manifest Designer bildirimleri
 Listeye bir bildirim eklemek, kullanıcı gerekli özellikleri ayarlayana kadar devam eden bir hata durumuna hemen yerleştirir.

 Bu durumda, uyarı için kullanılan simge " " simgesi&times;içerdiğinden, ortak kaldırma simgesi yanında kullanılamadığından, ek bir sorun vardır. Sonuç olarak, UI, daha aksak bir denetim olan Kaldır düğmesini kullanır.

 ![UI'yi varsayılan olarak bir hata durumuna yerleştirmek Visual Studio anti-desenidir.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-desen")<br />UI'yi varsayılan olarak bir hata durumuna yerleştirmek Visual Studio anti-desenidir.

#### <a name="alternatives"></a>Alternatifler

Bu soruna daha iyi bir çözüm:

- Kullanıcının uyarı yapmadan bir bildirim eklemesine izin verin ve ardından öğedeki özellikleri ayarlamak için hemen hareket edin.

- Odak öğeden hareket ettiğinde (listeye başka bir bildirim eklemek veya tasarımcı içindeki sekmeleri değiştirmeye çalışmak gibi) uyarı simgesini (altın üçgen) ekleyin.

- Kullanıcı herhangi bir bildirimde özellikleri ayarlamadan önce sekmeleri değiştirmeye çalışırsa, uyarılar çözülene kadar uygulamanın oluşturmeyeceğini (veya etkileri ne olursa olsun) açıklayan bir iletişim kutusu oluşturun. Kullanıcı iletişim kutusunu reddederse ve sekmeleri yine de değiştirirse, Bildirimler sekmesine bir simge (uygun olduğu şekilde kritik veya uyarı) eklenir.

### <a name="multiple-clicks-to-dismiss-ui"></a>UI'yi reddetmek için birden çok tıklama

#### <a name="feature-team-goals"></a>Özellik takım hedefleri
 Kullanıcının açıklama metnini görmeden Kullanıcı Arabirimi'ni reddetmesine izin vermeyin.

#### <a name="anti-pattern"></a>Anti-desen
 Video bağlantılarını VS UI içindeki çeşitli yerlere yerleştiren ekip, UX&times;tarafından belirtildiği gibi " yakın düğme ve araç ucu açıklamasının ortak desenine karşı karar verdi ve bunun yerine bir açılır bırakma ve "Tekrar gösterme" bağlantısını uyguladı.

#### <a name="example-video-links-in-team-explorer"></a>Örnek: Team Explorer'daki video bağlantıları
Kullanıcıyı Kullanıcı Arabirimi'ni reddetmeden önce açıklayıcı metni okumaya zorlamak Visual Studio'da bir anti-desendir. Doğru tasarlanmış, video bağlantıları hover ek bilgi ile bir araç ucu&times;görüntülemeli ve " " düğmesini tıklatarak daha fazla etkileşim için gerek kalmadan iletiyi kapatmalıdır.

 ![Açıklayıcı metin anti&#45;desen &#45; yanlış](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Multipleclicks'in yanlış kullanımı")<br />Yanlış video bağlantısı deseni

Basit bir yakın düğme (tek tıklama) yerine, kullanıcı yalnızca video bağlantılarının göründüğü her yerde Kullanıcı Arabirimi'ni kapatmak için iki tıklama kullanmak zorunda kalır.

Bu durum için doğru tasarım Internet Explorer, Office ve Visual Studio ortak desen takip etmektir: hover üzerinde, kullanıcı araç ipucu açıklamasını görebilir ve bir tıklama Kullanıcı Arabirimi gizler.

 ![Açıklayıcı metin anti&#45;desen &#45; doğru](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Açıklayıcı textanti-desen-doğru")<br />Video bağlantısı deseni düzelt

### <a name="using-command-bars-for-settings"></a>Ayarlar için komut çubuklarını kullanma

**Şekil A** bu anti-deseni temsil eder: komut düğmesinin altına yalnızca komuttan daha fazlasına uygulanan bir ayar koymak. Bu çizimde, Hata Ayıklama başlat'ın yanı sıra seçilen ayara saygı gösterebilecek Tarayıcıda Görüntüle, Hata Ayıklama olmadan Başlat ve Adım Adım gibi komutlar vardır.

![Şekil A: Komut çubuğu anti-desen](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-desen-FigureA")<br />Şekil A: Komut çubuğu anti-desen

Biraz daha iyi, ama yine de istenmeyen, **şekil B'de**gösterildiği gibi, araç çubuklarında bu tür ayarları koyarak . Bölünmüş düğmeler daha az yer kaplar ve bu nedenle açılır düşmeler üzerinde bir gelişme olsa da, her iki tasarım da hala gerçekten bir komut olmayan bir şeyi tanıtmak için bir araç çubuğu kullanıyor.

![Şekil B: Daha iyi, ama yine de bir komut çubuğu anti-desen](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-desen-FigureB")<br />Şekil B: Daha iyi, ama yine de bir komut çubuğu anti-desen

**Şekil C'de**gösterilen doğru yaklaşımda ayar bir dizi komuta bağlıdır. Ayarlanmış bir küresel ayar yok ve biz sadece dört komut arasında geçiş yapıyoruz. Araç çubuğundaki komutların kabul edilebilir olduğu tek durum budur.

![Şekil C: Visual Studio komut çubuğu deseninin doğru kullanımı](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-desen-FigureC")<br />Şekil C: Visual Studio komut çubuğu deseninin doğru kullanımı

### <a name="control-anti-patterns"></a>Anti-desenleri kontrol edin
 Bazı anti-desenler sadece yanlış kullanımı veya bir denetim veya denetim grubu sunumu vardır.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Köprü olarak değil, grup etiketi olarak kullanılan alt çizgi
 Altı çizili metin yalnızca köprüler için kullanılmalıdır.

 **Kötü:**\
 ![Köprü olmayan altı çizili metin Visual Studio anti-desenidir.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />Köprü olmayan altı çizili metin Visual Studio anti-desenidir.

 **Iyi:**\
 ![Doğru şekilde stile, köprü olmayan metin ortam yazı tipinde süslenmemiş olarak görünür.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Doğru şekilde stile, köprü olmayan metin ortam yazı tipinde süslenmemiş olarak görünür.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Onay kutusunu tıklatma, açılır iletişim kutusunda sonuçlanır
 "Windows Azure Uygulamasını Yayımla" sihirbazındaki "Tüm roller için Uzak Masaüstü'nü Etkinleştir" onay kutusunu tıklattığınızda hemen bir açılır iletişim kutusu, bir Visual Studio anti-deseni açılır. Buna ek olarak, onay kutusu alanı seçildikten sonra bir onay kutusu ile doldurmaz, başka bir etkileşim anti-desen.

 ![Onay kutusunu tıklattıktan sonra bir iletişim kurma visual studio anti-desen.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />Onay kutusunu tıklattıktan sonra bir iletişim kurma visual studio anti-desen.

### <a name="hyperlink-anti-patterns"></a>Köprü anti-desenleri
 Aşağıdaki örnekte iki anti-desen içerir:

1. Havada kırmızıya dönüşmek, yazı tipi hizmetinden doğru paylaşılan rengin kullanılmadığı anlamına gelir.

2. "Daha fazla bilgi edinin" kavramsal bir konuya bağlantı için uygun metin değildir. Kullanıcının amacı daha fazla bilgi edinmek değil, kendi seçtikleri sonuçları anlamaktır.

   ![Renk hizmetini göz ardı etmek ve köprüler için "Daha fazla bilgi edinin" kullanmak Visual Studio anti-desenleridir.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />Renk hizmetini göz ardı etmek ve köprüler için "Daha fazla bilgi edinin" kullanmak Visual Studio anti-desenleridir.

**Daha iyi çözüm:** Bağlantıyı tıklayarak kullanıcının soracağı soruyu sor. Örnek:

- Windows Azure hizmetleri nasıl çalışır?

- Windows Azure Mobil Hizmetler projesine ne zaman ihtiyacım var?

#### <a name="using-click-here-for-links"></a>Bağlantılar için "Buraya tıklayın" seçeneğini kullanma
 Köprüler kendini açıklayıcı olmalıdır. "Buraya tıklayın" veya benzer bir varyasyon kullanmak için bir anti-desen.

 **Kötü:** "Yeni bir projenin nasıl oluşturulacağına ilişkin talimatlar için burayı tıklatın."

 **İyi:** "Yeni bir projeyi nasıl oluştururum?"
