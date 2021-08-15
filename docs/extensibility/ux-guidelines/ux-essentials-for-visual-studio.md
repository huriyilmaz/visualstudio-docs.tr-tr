---
title: Visual Studio için UX temelleri | Microsoft Docs
description: ekran çözünürlüğü hakkında bilgi de dahil olmak üzere Visual Studio için geliştirdiğiniz yeni özellikler için bu kullanıcı deneyimi en iyi yöntemlerini gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: a793cf7a-f230-43ce-88d0-fa5d6f1aa9c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 569ab6c839c9944550b351152abe86c0f7a6722dab3bd3b743adbaf87139d695
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121259857"
---
# <a name="ux-essentials-for-visual-studio"></a>Visual Studio İçin UX Temel Bileşenleri

## <a name="best-practices"></a>En iyi uygulamalar

### <a name="1-be-consistent-within-the-visual-studio-environment"></a>1. Visual Studio ortamı dahilinde tutarlı olun.

- Kabuğun içindeki mevcut [etkileşim desenlerini](interaction-patterns-for-visual-studio.md) izleyin.

- Özellikleri, kabuğun görsel dili ve [craftsmansevkiyat gereksinimleriyle](evaluation-tools-for-visual-studio.md)tutarlı olacak şekilde tasarlayın.

- Varsa paylaşılan komutları ve denetimleri kullanın.

- Visual Studio hiyerarşisini anlayın ve kullanıcı arabirimini nasıl bağlam ve sürücü olarak belirler.

### <a name="2-use-the-environment-service-for-fonts-and-colors"></a>2. yazı tipi ve renkler için ortam hizmetini kullanın.

- Seçenekler iletişim kutusundaki yazı tipleri ve renkler sayfasında, özelleştirme için sunulmadığı müddetçe, Kullanıcı arabirimi geçerli [ortam yazı tipi](fonts-and-formatting-for-visual-studio.md) ayarına uymalıdır.

- Kullanıcı arabirimi öğeleri, paylaşılan ortam belirteçlerini veya özelliğe özgü belirteçleri kullanarak [Vscbir hizmeti](colors-and-styling-for-visual-studio.md)kullanmalıdır.

### <a name="3-make-all-imagery-consistent-with-the-new-vs-style"></a>3. tüm Imagery 'leri yeni VS stiliyle tutarlı yapın.

- simgeler, glifler ve diğer grafikler için Visual Studio tasarım ilkelerini izleyin.

- Metni grafik öğelerine yerleştirmeyin.

### <a name="4-design-from-a-user-centric-perspective"></a>4. Kullanıcı merkezli bir perspektiften tasarlayın.

- Görev akışını, içindeki özelliklerden önce oluşturun.

- Kullanıcılarınız hakkında bilgi sahibi olun ve bu bilgiyi belirtiminiz içinde açık hale getirin.

- Kullanıcı arabirimini gözden geçirirken, tüm deneyimi ve ayrıntıları değerlendirin.

- Kullanıcı arabiriminizi, yerel ayar veya dilden bağımsız olarak işlevsel ve etkileyici kalacak şekilde tasarlayın.

## <a name="screen-resolution"></a>Ekran çözünürlüğü

### <a name="minimum-resolution"></a>En düşük çözünürlük

- 2015 Visual Studio için en düşük çözünürlük **1280x720**' dir. bu, en iyi kullanıcı deneyimi olmasa da Visual Studio bu çözünürlükte kullanmak *mümkün* olduğu anlamına gelir. Tüm yönlerinin 1280x720 ' den daha düşük çözünürlükte kullanılabilir olacağını garanti etmez.

- Visual Studio hedef çözünürlüğü **1366x768**' dir. Bu, *iyi* bir kullanıcı deneyimi taahhüdünü taahhüt eden en düşük çözünürlüğünüz.

- İlk iletişim kutusu yüksekliği **700 pikselden daha küçük** olmalıdır, bu nedenle IDE çerçevesinin en düşük çözünürlüğüne 96 DPI ile sığar.

### <a name="high-density-displays"></a>Yüksek yoğunluklu ekranlar
 Visual Studio içindeki kullanıcı arabirimi, Windows şu kutudan birini desteklediği tüm dpı ölçeklendirme faktörlerinde iyi çalışmalıdır: %150, 200% ve %250.

## <a name="anti-patterns"></a>Desenler
 Visual Studio, kılavuzlarımızı ve en iyi uygulamalarınızı izleyen birçok kullanıcı arabirimine örnek içerir. İş açısından tutarlı olması için geliştiriciler genellikle ürün Kullanıcı arabirimi tasarım desenlerinden, oluşturma biçimlerinize benzer. Bu, Kullanıcı etkileşimi ve görsel tasarımda tutarlılık sağlamamıza yardımcı olan iyi bir yaklaşım olsa da, zamanlama kısıtlamaları veya hata önceliklendirmesi nedeniyle yönergelerimizi karşılamayan bazı ayrıntılarla birlikte bazı özellikler sunarız. bu durumlarda, Visual Studio ortamında kötü veya tutarsız kullanıcı arabirimine sahip olmaları nedeniyle ekiplerin bu "koruma" düzenlerini "kopyalamasını istemedik.

### <a name="required-fieldssettings-shown-in-error-state-by-default"></a>Varsayılan olarak hata durumunda gösterilen gerekli alanlar/ayarlar

#### <a name="feature-team-goals"></a>Özellik ekibi hedefleri

- Kullanıcıları, yapılandırılması gereken bir öğe eklediğine uyar.

- Kullanıcının giriş ihtiyacı olan alanlara dikkatini çizin.

#### <a name="anti-pattern-solution"></a>Kenar yumuşatma çözümü
 Kullanıcı bir eylemi başlattıktan hemen sonra görevi tamamladıktan sonra, yapılandırmaya ihtiyacı olan alanların yanına hemen kritik durağı simgeleri yerleştirin.

#### <a name="example-manifest-designer-declarations"></a>Örnek: bildirim Tasarımcısı bildirimleri
 Listeye bir bildirim eklemek, Kullanıcı gerekli özellikleri ayarlana kadar devam eden bir hata durumuna hemen koyar.

 Bu durumda, uyarı için kullanılan simgenin "" simgesi içerdiği için ek bir sorun vardır &times; , bu nedenle ortak kaldırma simgesi bunun yanında kullanılamaz. Sonuç olarak, Kullanıcı arabirimi daha fazla clunky denetimi olan bir Kaldır düğmesini kullanır.

 ![kullanıcı arabirimini bir hata durumuna yerleştirme, varsayılan olarak Visual Studio bir anti-öründir.](../../extensibility/ux-guidelines/media/manifestdesignererrordeclarationsanti-pattern.png "ManifestDesignererrordeclarationsanti-model")<br />kullanıcı arabirimini bir hata durumuna yerleştirme, varsayılan olarak Visual Studio bir anti-öründir.

#### <a name="alternatives"></a>Alternatifler

Bu soruna yönelik daha iyi bir çözüm şunlardır:

- Kullanıcının uyarı olmadan bir bildirim eklemesine izin verin ve ardından öğe üzerinde özellikleri ayarlamak için hemen taşıyın.

- Odak öğeden başka bir bildirim eklemek ya da tasarımcı içindeki sekmeleri değiştirmeyi denemek gibi, öğe bir öğeden taşınmışken uyarı simgesini (altın üçgen) ekleyin.

- Kullanıcı herhangi bir bildirime Özellikler ayarlamadan önce sekmeleri değiştirmeye çalışırsa, uyarılar çözümlenene kadar uygulamanın derlenmeyeceğini (veya etkileri olduğunu) açıklayan bir iletişim kutusu açılır. Kullanıcı iletişim kutusu ve değişiklik sekmelerini yine de kapatır, bildirimler sekmesine bir simge (kritik veya uyarı) eklenir.

### <a name="multiple-clicks-to-dismiss-ui"></a>UI 'yi kapatmak için birden çok tıklama

#### <a name="feature-team-goals"></a>Özellik ekibi hedefleri
 Kullanıcının Kullanıcı ARABIRIMINI, açıklama metnini görmeden kapatması için izin verme.

#### <a name="anti-pattern"></a>Kenar yumuşatma
 Ekip, VS UI içindeki çeşitli konumlara video bağlantıları ekleyerek &times; , UX tarafından belirtilen "" Kapat düğmesinin ve araç ipucu açıklamasına ilişkin ortak düzende karar vermiştir ve bunun yerine bir açılan ve "bir daha gösterme" bağlantısını uyguladık.

#### <a name="example-video-links-in-team-explorer"></a>Örnek: Takım Gezgini video bağlantıları
Eksik Kullanıcı ARABIRIMINDEN önce açıklayıcı metin okumaya zorlamak, Visual Studio içinde bir anti-örünmedir. Doğru tasarlanmış, video bağlantıları, üzerine gelme hakkında ek bilgiler içeren bir araç ipucu görüntülemelidir ve " &times; " iletisinin daha fazla etkileşime gerek duymadan bu iletiyi kapatması gerekir.

 ![Açıklayıcı metin anti&#45;deseninin yanlış &#45;](../../extensibility/ux-guidelines/media/incorrectuseofmultipleclicks.png "Incorrectuseofmultipleclicks")<br />Hatalı video bağlantısı kalıbı

Basit bir kapatma düğmesi (bir tıklama) yerine, Kullanıcı, video bağlantılarının göründüğü her yerde Kullanıcı ARABIRIMINI kapatmak için iki tıklama kullanmaya zorlanır.

bu durumun doğru tasarımı, ınternet Explorer, Office ve Visual Studio yaygın olarak kullanılan kalıbı izleyebildir: üzerine gelindiğinde, kullanıcı araç ipucu açıklamasını görebilir ve bir tıklama kullanıcı arabirimini gizler.

 ![Açıklayıcı metin anti&#45;deseninin &#45; doğru](../../extensibility/ux-guidelines/media/explanatorytextanti-pattern-correct.png "Explanatorytextanti-model-doğru")<br />Doğru video bağlantısı kalıbı

### <a name="using-command-bars-for-settings"></a>Ayarlar için komut çubuklarını kullanma

**Şekil A** , bu kenar yumuşatmayı temsil eder: bir ayarı yalnızca komutu için geçerli olan bir komut düğmesinin altına koymak. Bu taslağa, hata ayıklamayı Başlat (tarayıcıda görüntüle, hata ayıklama olmadan Başlat ve adım adım) gibi komutlar vardır. Bu, seçilen ayara göre değişir.

![Şekil A: komut çubuğu Anti-model](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurea.png "Commandbaranti-model-FigureA")<br />Şekil A: komut çubuğu Anti-model

**Şekil B**' de gösterildiği gibi biraz daha iyidir, ancak yine de bu türün ayarlarını araç çubuklarına yerleştirmektedir. Bölünmüş düğmeler daha az alan kaplamakta ve bu nedenle açılan listede geliştirirken, her iki tasarım de gerçekten bir komut olmayan bir şeyi yükseltmek için araç çubuğu kullanmaya devam etmektedir.

![Şekil B: daha Iyi, ancak yine de bir komut çubuğu Anti-model](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figureb.png "Commandbaranti-model-FigureB")<br />Şekil B: daha Iyi, ancak yine de bir komut çubuğu Anti-model

**Şekil C**' de gösterilen doğru yaklaşımda, ayar bir dizi komuta bağlıdır. Ayarlanmış genel ayar yoktur ve yalnızca dört komut arasında geçiş yapıyoruz. Bu, araç çubuğundaki komutların kabul edilebilir olduğu tek durumdur.

![şekil C: Visual Studio komut çubuğu deseninin doğru kullanımı](../../extensibility/ux-guidelines/media/commandbaranti-pattern-figurec.png "Commandbaranti-model-FigureC")<br />şekil C: Visual Studio komut çubuğu deseninin doğru kullanımı

### <a name="control-anti-patterns"></a>Denetim önleme desenleri
 Bazı koruma desenleri, bir denetimin veya denetim grubunun yalnızca yanlış kullanımı veya sunumudur.

#### <a name="underlining-used-as-a-group-label-not-a-hyperlink"></a>Köprü değil, Grup etiketi olarak kullanılan altı çizili
 Metnin altını çizme yalnızca köprüler için kullanılmalıdır.

 **Hatalı**\
 ![köprü olmayan altı çizili metin, Visual Studio bir anti-model değildir.](../../extensibility/ux-guidelines/media/0102-g_grouplabelincorrect.png "0102-g_GroupLabelIncorrect")<br />köprü olmayan altı çizili metin, Visual Studio bir anti-model değildir.

 **İyi**\
 ![Doğru stillendirilmiş, köprü dışı metin, ortam yazı tipinde donatılamayan şekilde görünür.](../../extensibility/ux-guidelines/media/0102-h_grouplabelcorrect.png "0102-h_GroupLabelCorrect")<br />Doğru stillendirilmiş, köprü dışı metin, ortam yazı tipinde donatılamayan şekilde görünür.

#### <a name="clicking-on-a-check-box-results-in-a-pop-up-dialog"></a>Bir onay kutusuna tıkladığınızda açılan iletişim kutusu oluşur
 "Azure uygulaması Windows yayımlama" sihirbazı 'ndaki "tüm roller için uzak masaüstünü etkinleştir" onay kutusunun tıklanması, hemen bir açılan iletişim kutusu olan Visual Studio bir anti-of-up açılır iletişim kutusu açar. Ayrıca, onay kutusu alanı, seçildikten sonra bir onay kutusuyla, başka bir etkileşim Anti-deseninin doldurulmaz.

 ![onay kutusuna tıklandıktan sonra bir iletişim kutusu getirmek Visual Studio bir anti-örünmedir.](../../extensibility/ux-guidelines/media/0102-i_checkboxpopup.png "0102-i_CheckboxPopup")<br />onay kutusuna tıklandıktan sonra bir iletişim kutusu getirmek Visual Studio bir anti-örünmedir.

### <a name="hyperlink-anti-patterns"></a>Köprü Netleştirme desenleri
 Aşağıdaki örnek iki tane Anti-deseni içerir:

1. Üzerine gelindiğinde kırmızı olan ön plan, yazı tipi hizmetinden doğru paylaşılan rengin kullanılmadığını gösterir.

2. "Daha fazla bilgi", kavramsal konunun bağlantısı için uygun metin değildir. Kullanıcının amacı daha fazla bilgi almak için tercih ettikleri sonuçları anlamaktır.

   ![renk hizmeti yok sayılıyor ve köprüler için "daha fazla bilgi" kullanmak Visual Studio desenler için kullanılır.](../../extensibility/ux-guidelines/media/0102-j_hyperlinkincorrect.png "0102-j_HyperlinkIncorrect")<br />renk hizmeti yok sayılıyor ve köprüler için "daha fazla bilgi" kullanmak Visual Studio desenler için kullanılır.

**Daha iyi çözüm:** Kullanıcının bağlantıya tıklayarak istediği soruyu ortaya çıkaran. Örnek:

- Windows Azure hizmetleri nasıl çalışır?

- Windows Azure Mobile Services projesi ne zaman gerekir?

#### <a name="using-click-here-for-links"></a>Bağlantılar için "buraya tıklayın" kullanma
 Köprüler kendine açıklayıcı olmalıdır. "Buraya tıklayın" veya benzer çeşitçlikleri kullanmak için bir kenar modelidir.

 **Hatalı:** "Yeni bir proje oluşturma hakkında yönergeler için buraya tıklayın."

 **İyi:** "Yeni proje oluşturmak Nasıl yaparım? mı?"
