---
title: UX Temel Bileşenleri
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f3ed2d3f8bc52b21f6a87ac7d6da00f665f6b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181459"
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio İçin UX Temel Bileşenleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="best-practices"></a>En iyi uygulamalar

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Visual Studio ortamı dahilinde tutarlı olun.

- Kabuğun içindeki mevcut etkileşim desenlerini izleyin.

- Özellikleri, kabuğun görsel dili ve craftsmansevkiyat gereksinimleriyle tutarlı olacak şekilde tasarlayın.

- Varsa paylaşılan komutları ve denetimleri kullanın.

- Visual Studio hiyerarşisini ve nasıl bağlam sağladığını ve Kullanıcı arabirimini nasıl yönlendiren anlayın.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. yazı tipi ve renkler için ortam hizmetini kullanın.

- Seçenekler iletişim kutusundaki yazı tipleri ve renkler sayfasında, özelleştirme için sunulmadığı müddetçe, Kullanıcı arabirimi geçerli ortam yazı tipi ayarına uymalıdır.

- Kullanıcı arabirimi öğeleri, paylaşılan ortam belirteçlerini veya özelliğe özgü belirteçleri kullanarak Vscbir hizmeti kullanmalıdır.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. tüm Imagery 'leri yeni VS stiliyle tutarlı yapın.

- Simgeler, Glifler ve diğer grafikler için Visual Studio tasarım ilkelerini izleyin.

- Metni grafik öğelerine yerleştirmeyin.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Kullanıcı merkezli bir perspektiften tasarlayın.

- Görev akışını, içindeki özelliklerden önce oluşturun.

- Kullanıcılarınız hakkında bilgi sahibi olun ve bu bilgiyi belirtiminiz içinde açık hale getirin.

- Kullanıcı arabirimini gözden geçirirken, tüm deneyimi ve ayrıntıları değerlendirin.

- Kullanıcı arabiriminizi, yerel ayar veya dilden bağımsız olarak işlevsel ve etkileyici kalacak şekilde tasarlayın.

## <a name="screen-resolution"></a>Ekran çözünürlüğü

### <a name="minimum-resolution"></a>En düşük çözünürlük
 Visual Studio Dev14 için en düşük çözüm 1280x1024 ' dir. Bu, en iyi kullanıcı deneyimi olmasa da Visual Studio 'Nun bu çözünürlükte kullanılması *mümkün* olduğu anlamına gelir. Tüm yönlerinin 1280x1024 ' den daha düşük çözünürlükte kullanılabilir olacağını garanti etmez.

 İlk iletişim kutusu boyutu yükseklik olarak 1000 pikseli aşmamalıdır, bu nedenle IDE 'nin çerçevesini en düşük çözünürlükte, 96 dpi olarak sığdırabilmelidir.

### <a name="high-density-displays"></a>Yüksek yoğunluklu ekranlar
 Visual Studio 'daki Kullanıcı arabirimi, Windows 'un şu kutudan birini desteklediği tüm DPı ölçeklendirme faktörlerinde iyi çalışmalıdır: %150, 200% ve %250.

## <a name="anti-patterns"></a>Desenler
 Visual Studio, kılavuzlarımızı ve en iyi uygulamalarınızı izleyen birçok kullanıcı arabirimine örnek içerir. İş açısından tutarlı olması için geliştiriciler genellikle ürün Kullanıcı arabirimi tasarım desenlerinden, oluşturma biçimlerinize benzer. Bu, Kullanıcı etkileşimi ve görsel tasarımda tutarlılık sağlamamıza yardımcı olan iyi bir yaklaşım olsa da, zamanlama kısıtlamaları veya hata önceliklendirmesi nedeniyle yönergelerimizi karşılamayan bazı ayrıntılarla birlikte bazı özellikler sunarız. Bu durumlarda, Visual Studio ortamında kötü veya tutarsız Kullanıcı arabirimine sahip olmaları nedeniyle ekiplerin bu "koruma" düzenlerini "kopyalamasını istemedik.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Varsayılan olarak hata durumunda gösterilen gerekli alanlar/ayarlar

#### <a name="feature-team-goals"></a>Özellik ekibi hedefleri

- Kullanıcıları, yapılandırılması gereken bir öğe eklediğine uyar.

- Kullanıcının giriş ihtiyacı olan alanlara dikkatini çizin.

#### <a name="anti-pattern-solution"></a>Kenar yumuşatma çözümü
 Kullanıcı bir eylemi başlattıktan hemen sonra görevi tamamladıktan sonra, yapılandırmaya ihtiyacı olan alanların yanına hemen kritik durağı simgeleri yerleştirin.

#### <a name="example-manifest-designer-declarations"></a>Örnek: bildirim Tasarımcısı bildirimleri
 Listeye bir bildirim eklemek, Kullanıcı gerekli özellikleri ayarlana kadar devam eden bir hata durumuna hemen koyar.

 Bu durumda, uyarı için kullanılan simgenin bir "x" içerdiğinden ve bunun yanında ortak kaldırma simgesi kullanılamaz olduğu için ek bir sorun vardır. Sonuç olarak, Kullanıcı arabirimi daha fazla clunky denetimi olan bir Kaldır düğmesini kullanır.

 ![Bildirim Tasarımcısı hata bildirimi&#45;model Anti](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-model")

 **Kullanıcı arabirimini bir hata durumuna yerleştirme, varsayılan olarak bir Visual Studio Anti-model ' dir.**

#### <a name="alternatives"></a>Alternatifler
 Bu soruna yönelik daha iyi bir çözüm şöyle olacaktır:

- Kullanıcının uyarı olmadan bir bildirim eklemesine izin verin ve ardından öğe üzerinde özellikleri ayarlamak için hemen taşıyın.

- Odak öğeden başka bir bildirim eklemek ya da tasarımcı içindeki sekmeleri değiştirmeyi denemek gibi, öğe bir öğeden taşınmışken uyarı simgesini (altın üçgen) ekleyin.

- Kullanıcı herhangi bir bildirime Özellikler ayarlamadan önce sekmeleri değiştirmeye çalışırsa, uyarılar çözümlenene kadar uygulamanın derlenmeyeceğini (veya etkileri olduğunu) açıklayan bir iletişim kutusu açılır. Kullanıcı iletişim kutusu ve değişiklik sekmelerini yine de kapatır, bildirimler sekmesine bir simge (kritik veya uyarı) eklenir.

### <a name="forcing-the-user-to-read-text-before-dismissing-ui"></a>Kullanıcı, eksik Kullanıcı ARABIRIMINDEN önce metin okumayı zorluyor

#### <a name="feature-team-goals"></a>Özellik ekibi hedefleri
 Kullanıcının Kullanıcı ARABIRIMINI, açıklama metnini görmeden kapatması için izin verme.

#### <a name="anti-pattern"></a>Kenar yumuşatma
 Takım, ekran bağlantılarını VS UI içindeki çeşitli konumlara ekleyerek, UX tarafından belirtilen bir X Close düğmesi ve araç ipucu açıklamasına ilişkin ortak düzende karar vermiştir ve bunun yerine bir açılan menü ve "bir daha gösterme" bağlantısı uygulanır.

 ![Açıklayıcı metin anti&#45;deseninin yanlış &#45;](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")

 **Yanlış: Kullanıcı yok etmeden önce açıklayıcı metin okumayı zorluyor, Visual Studio içindeki bir anti-model.**

#### <a name="result"></a>Sonuç
 Basit bir kapatma düğmesi (bir tıklama) yerine, Kullanıcı, video bağlantılarının göründüğü her yerde Kullanıcı ARABIRIMINI kapatmak için iki tıklama kullanmaya zorlanır.

#### <a name="alternatives"></a>Alternatifler
 Bu durumun doğru tasarımı, Internet Explorer, Office ve Visual Studio 'da ortak olan kalıbı izlemek olacaktır: üzerine gelindiğinde, Kullanıcı araç ipucu açıklamasını görebilir ve bir tıklama Kullanıcı ARABIRIMINI gizler.

 ![Açıklayıcı metin anti&#45;deseninin &#45; doğru](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-model-doğru")

 **Doğru: tasarlandığı gibi, video bağlantılarında, üzerine gelme hakkında ek bilgiler içeren bir araç ipucu görüntülenmelidir ve "X" i tıklatmak daha fazla etkileşime gerek olmadan iletiyi yok saymalıdır.**

### <a name="using-command-bars-for-settings"></a>Ayarlar için komut çubuklarını kullanma
 ![Komut çubuğu Anti&#45;deseninin &#45; Şekil A](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-model-FigureA")

 **Şekil A: komut çubuğu Anti-model**

 **Şekil A** , bu kenar yumuşatmayı temsil eder: bir ayarı yalnızca komutu için geçerli olan bir komut düğmesinin altına koymak. Bu taslağa, hata ayıklamayı Başlat (tarayıcıda görüntüle, hata ayıklama olmadan Başlat ve adım adım) gibi komutlar vardır. Bu, seçilen ayara göre değişir.

 ![Komut çubuğu Anti&#45;deseninin &#45; Şekil B](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-model-FigureB")

 **Şekil B: daha Iyi, ancak yine de bir komut çubuğu Anti-model**

 **Şekil B**' de gösterildiği gibi biraz daha iyidir, ancak yine de bu türün ayarlarını araç çubuklarına yerleştirmektedir. Bölünmüş düğmeler daha az alan kaplamakta ve bu nedenle açılan listede geliştirirken, her iki tasarım de gerçekten bir komut olmayan bir şeyi yükseltmek için araç çubuğu kullanmaya devam etmektedir.

 ![Komut çubuğu Anti&#45;deseninin &#45; Şekil C](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-model-FigureC")

 **Şekil C: Visual Studio komut çubuğu deseninin doğru kullanımı**

 **Şekil C**'de, ayar bir dizi komuta bağlıdır. Ayarlanmış genel ayar yoktur ve yalnızca dört komut arasında geçiş yapıyoruz. Bu, araç çubuğundaki komutların kabul edilebilir olduğu tek durumdur.

### <a name="control-anti-patterns"></a>Denetim önleme desenleri
 Bazı koruma desenleri, bir denetimin veya denetim grubunun yalnızca yanlış kullanımı veya sunumudur.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Köprü değil, Grup etiketi olarak kullanılan altı çizili
 Metnin altını çizme yalnızca köprüler için kullanılmalıdır.

 **Hatalı**

 ![Grup etiketlerindeki Anti&#45;deseninin altını çizme](../../extensibility/ux-guidelines/media/0102-g-grouplabelincorrect.png "0102-g_GroupLabelIncorrect")

 **Köprü olmayan altı çizili metin bir Visual Studio Anti-model değildir.**

 **İyi**

 ![Grup etiketlerindeki Anti&#45;deseninin altını çizme &#40;doğru&#41;](../../extensibility/ux-guidelines/media/0102-h-grouplabelcorrect.png "0102-h_GroupLabelCorrect")

 **Doğru stillendirilmiş, köprü dışı metin, ortam yazı tipinde donatılamayan şekilde görünür.**

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Bir onay kutusuna tıkladığınızda açılan iletişim kutusu oluşur
 "Windows Azure uygulaması yayımlama" sihirbazının "tüm roller için uzak masaüstünü etkinleştir" onay kutusunun tıklatılması, hemen bir Visual Studio Anti-of açılır iletişim kutusu görüntüler. Ayrıca, onay kutusu alanı, seçildikten sonra bir onay kutusuyla, başka bir etkileşim Anti-deseninin doldurulmaz.

 ![Onay kutusu pop&#45;yukarı&#45;örüntüsünün](../../extensibility/ux-guidelines/media/0102-i-checkboxpopup.png "0102-i_CheckboxPopup")

 **Onay kutusuna tıklandıktan sonra bir iletişim kutusunun getirilmesi bir Visual Studio Anti-model ' dir.**

### <a name="hyperlink-anti-patterns"></a>Köprü Netleştirme desenleri
 Aşağıdaki örnek iki tane Anti-deseni içerir.

1. Üzerine gelindiğinde kırmızı olan ön plan, yazı tipi hizmetinden doğru paylaşılan rengin kullanılmadığını gösterir.

2. "Daha fazla bilgi", kavramsal konunun bağlantısı için uygun metin değildir. Kullanıcının amacı daha fazla bilgi almak için tercih ettikleri sonuçları anlamaktır.

   ![Köprü Anti&#45;desenleri](../../extensibility/ux-guidelines/media/0102-j-hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")

   **Renk hizmeti yok sayılıyor ve köprüler için "daha fazla bilgi" kullanılarak Visual Studio Anti-desenler bulunur.**

   **Daha iyi çözüm:** Kullanıcının bağlantıya tıklayarak istediği soruyu ortaya çıkaran.

- Windows Azure hizmetleri nasıl çalışır?

- Bir Windows Azure Mobile Services projesi ne zaman gerekir?

#### <a name="using-click-here-for-links"></a>Bağlantılar için "buraya tıklayın" kullanma
 Köprüler kendine açıklayıcı olmalıdır. "Buraya tıklayın" veya benzer çeşitçlikleri kullanmak için bir kenar modelidir.

 **Hatalı:** "Yeni bir proje oluşturma hakkında yönergeler için buraya tıklayın."

 **İyi:** "Yeni proje oluşturmak Nasıl yaparım? mı?"
