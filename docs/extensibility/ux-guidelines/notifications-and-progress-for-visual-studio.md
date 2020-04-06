---
title: Görsel Stüdyo için Bildirimler ve İlerleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f6a7ddd5d1a5a7257617b03098722e1341017b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699879"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Visual Studio İçin Bildirimler ve İlerleme Durumu
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a>Bildirim sistemleri

### <a name="overview"></a>Genel Bakış
 Visual Studio'da yazılım geliştirme görevleri yle ilgili olarak kullanıcıyı bilgilendirmenin çeşitli yolları vardır.

 Herhangi bir bildirim uygularken:

- **Bildirim sayısını en az** etkin numaraya kadar tutun. Bildirim iletileri Visual Studio kullanıcılarının çoğunluğu veya belirli bir özellik/özellik alanının kullanıcıları için geçerli olmalıdır. Bildirimlerin aşırı kullanımı kullanıcıyı rahatsız edebilir veya sistemin algılanan kullanım kolaylığını azaltabilir.

- Kullanıcının daha karmaşık seçimler yapmak ve daha fazla eylem yapmak için uygun bağlamı çağırmak için kullanabileceği **açık, işlem yapılabilir iletiler sunduğunuzdan emin olun.**

- **Senkron ve eşzamanlı iletileri uygun şekilde sunun.** Eşzamanlı bildirimler, bir web hizmetinin çökmesi veya bir kod özel durum atılması gibi bir şeyin hemen ilgilenilmesi gerektiğini gösterir. Kullanıcı, modal iletişim kutusu gibi, kendi girdisini gerektiren bir şekilde bu durumlardan hemen haberdar edilmelidir. Eşkron bildirimler, kullanıcının bilmesi gereken ancak bir yapı işlemi tamamlandığında veya bir web sitesi dağıtımı nın tamamlanması gibi hemen harekete geçmeleri gerekmeyen bildirimlerdir. Bu iletiler daha ortamlı olmalı ve kullanıcının görev akışını kesintiye uğratmamalıdır.

- Kullanıcının iletiyi kabul etmeden veya iletişim kutusunda sunulan bir karar vermeden önce **daha fazla eylemde bulunmasını önlemek için yalnızca gerektiğinde modal iletişim bilgilerini kullanın.**

- **Ortam bildirimlerini artık geçerli olmadığında kaldırın.** Kullanıcının, kendisine bildirilen sorunu gidermek için daha önce harekete geçtiyse, bildirimi reddetmesini gerekmez.

- **Bildirimlerin yanlış korelasyonlara yol açabileceğini unutmayın.** Kullanıcılar, aslında nedensel bir ilişki olmadığında, eylemlerinden bir veya daha fazlasının bir bildirimi tetiklediğine inanabilir. Bildirimin içeriği, tetikleyicisi ve kaynağı hakkındaki bildirim iletisinde açık olun.

### <a name="choosing-the-right-method"></a>Doğru yöntemi seçme
 İletinizi kullanıcıya bildirmek için doğru yöntemi seçmenize yardımcı olmak için bu tabloyu kullanın.

|Yöntem|Kullanım|Kullanmayın|
|------------|---------|----------------|
|[Modal hata iletiiletişim idapları](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Devam etmeden önce bir kullanıcı yanıtı gerektiğinde kullanın.|Kullanıcıyı engellemeye ve akışını kesmeye gerek olmadığında kullanmayın. İletiyi başka, daha az müdahaleci bir şekilde göstermek mümkünse modal iletişim leri kullanmaktan kaçının.|
|[IDE durum çubuğu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Bir işlemin durumuyla ilgili ortam metinsel bilgiler olduğunda kullanın.|Tek başına kullanmayın. En iyi başka bir geri bildirim mekanizması ile birlikte kullanılır.|
|[Gömülü bilgi çubuğu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Bir araç penceresinde veya belge penceresinde, ilerlemeyi, hata durumunu, sonuçları ve/veya işlem uygulanabilir bilgileri bildirmek için kullanın.|Bilgiler bilgi çubuğunun yerleştirildiği konumla alakalı değilse kullanmayın.<br /><br /> Belge/araç penceresi dışında kullanmayın.|
|[Fare imleci değişiklikleri](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Bir işlemin devam ettiğini bildirmek için kullanılabilir. Ayrıca, sürükle/bırak devam ederken veya fare imleci çizim modu gibi belirli bir modda olduğu gibi farede bir durum değişikliği olduğunu bildirmek için de kullanılır.|Kısa ilerleme değişiklikleri için veya imlecin çırpınma olasılığı yüksekse (örneğin, tüm işlem yerine daha uzun süren bir işlemin bölümlerine bağlıyken) kullanmayın.|
|[İlerleme göstergeleri](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|İlerlemeyi bildirmeniz gerektiğinde (belirsiz veya belirsiz) kullanın. Her biri için çeşitli ilerleme göstergesi türleri ve belirli kullanım vardır. Bkz. [İlerleme göstergeleri.](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators)||
|[Visual Studio Bildirimler penceresi](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Bildirimler penceresi genel olarak genişletilebilir değildir. Ancak, Visual Studio ile ilgili bir dizi ileti, lisans ve Visual Studio veya paketlere güncellemeleri bilgilendirme bildirimleri ile kritik sorunlar da dahil olmak üzere iletişim için kullanılır.|Diğer bildirim türleri için kullanmayın.|
|[Hata listesi](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Sorun, kullanıcının şu anda açık olan çözümüyle (hata/uyarı/bilgi) doğrudan ilişkili olduğunda, kod üzerinde işlem başlatmaları gerekebilir.<br /><br /> Bu, örneğin içerir:<br /><br /> - Derleyici mesajları (hata/uyarı/bilgi)<br /><br /> - Kod hakkında Kod Çözümleyici/Tanılama iletileri<br /><br /> - İleti oluşturma<br /><br /> Proje veya çözüm dosyalarıyla ilgili sorunlar için uygun olabilir, ancak önce bir Çözüm Gezgini göstergesi düşünün.|Kullanıcının açık çözüm koduyla ilişkisi olmayan öğeler için kullanmayın.|
|Editör bildirimleri: Ampul|Açık dosyada bulunan bir sorunu gidermek için kullanılabilir bir düzeltmeniz olduğunda kullanın.<br /><br /> Ampul de refactorings gibi isteğe bağlı kullanıcı kodu üzerinde alınan Hızlı Eylemler barındırma kıda lanması gerektiğini unutmayın, ancak bu durumda "bildirim stili görünmez."|Açık dosyayla ilişkisi olmayan öğeler için kullanmayın.|
|Editör bildirimleri: Squiggles|Kullanıcıyı açık kodlarının belirli bir açık lığıyla ilgili bir soruna karşı uyarmak için kullanın (örneğin, hatalar için kırmızı bir dalgalı).|Açık kodlarının belirli bir açık lığıyla ilgili olmayan öğeler için kullanmayın.|
|[Katıştılmış durum çubukları](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Belirli bir araç penceresi, belge penceresi veya iletişim penceresi bağlamında içerik veya işlemle ilgili durum sağlamak için kullanın.|Belirli bir penceredeki içerikle ilişkisi olmayan genel ürün bildirimleri, işlemler veya öğeler için kullanmayın.|
|[Windows tepsi bildirimleri](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|Proc dışı işlemler veya eşlik eden uygulamalar için bildirimleri yüzeye çıkarmak için kullanın.|IDE ile ilgili bildirimler için kullanmayın.|
|[Bildirim balonu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Uzak bir işlemi bildirmek veya IDE **dışında** değişiklik yapmak için kullanın.|IDE **içindeki** işlemleri kullanıcıya bildirmek için bir araç olarak kullanmayın.|

### <a name="notification-methods"></a>Bildirim yöntemleri

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a>Modal hata iletiiletişim idapları
 Modal hata iletisi iletişim kutusu, kullanıcının onayını veya eylemini gerektiren bir hata iletisini görüntülemek için kullanılır.

 ![Modal hata iletisi](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Bir veritabanına geçersiz bir bağlantı dizesi kullanıcıyı uyaran bir modal hata iletisi iletişim kutusu**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a>IDE durum çubuğu
 Kullanıcıların durum çubuğu metnini fark etme olasılığı, windows platformuyla ilgili bilgisayar deneyimleri ve belirli deneyimleriyle ilişkilidir. Bilgili Windows kullanıcıları bile durum çubuğundaki değişiklikleri kaçırsa da Visual Studio müşteri tabanı her iki alanda da deneyimli olma eğilimindedir. Bu nedenle, durum çubuğu en iyi bilgilendirme amacıyla veya başka bir yerde sunulan bilgiler için gereksiz bir ipucu olarak kullanılır. Kullanıcının hemen çözmesi gereken her türlü kritik bilgi bir iletişim kutusunda veya Bildirimler aracı penceresinde sağlanmalıdır.

 Visual Studio durum çubuğu, çeşitli türde bilgilerin görüntülenmesine izin verecek şekilde tasarlanmıştır. Geri bildirim, tasarımcı, ilerleme çubuğu, animasyon ve istemci için bölgelere ayrılmıştır.

 Geri bildirim bölgesi ve tasarımcı bölgesi her zaman görünür. İlerleme çubuğu ve animasyon bölgeleri her zaman dinamiktir ve kullanıcı bağlamına bağlıdır. Tasarımcı bölgesi, metin iletisi için eşlik eden bir kaynaktan çekilen dize uzunluğuna göre belirlenen statik bir genişliğe sahiptir. Bu, yerelleştirmenin bir kod değişikliği gerektirmeden genişliği yeniden boyutlandırmasına olanak tanır. İngilizce için bu dize genişliği kabaca 220 pikseldir. Tasarımcı bölgesi normal şekilde çalışacak ve geri bildirim bölgesi kalan alanı emer.

 Durum çubuğu, IDE'nin hata ayıklama modunda olduğu zaman gibi çeşitli IDE durum değişikliklerini ileterek görsel ilgi ve işlevsel değer eklemek için de renklendirilir.

 ![IDE durum çubuğu renk değişiklikleri](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **IDE durum çubuğu renkleri**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a>Gömülü bilgi çubuğu
 Bir bilgi çubuğu, kullanıcıyı bir durum veya durum hakkında bilgilendirmek için belge penceresinin veya araç penceresinin üst kısmında kullanılabilir. Ayrıca, kullanıcının kolayca harekete geçmenin bir yolunu bulabilmeleri için komutlar da sunabilir. Bilgi Çubuğu standart bir kabuk kontrolüdür. Hareket edecek ve IDE'deki diğer leriyle tutarsız görünecek olan kendi oluşturmaktan kaçının. Uygulama ayrıntıları ve kullanım kılavuzu için [Bilgi Çubukları'na](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) bakın.

 ![Gömülü bilgi çubuğu](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Bir belge penceresine katıştırılmış bir bilgi çubuğu, Kullanıcıyı IDE'nin geçmiş hata ayıklama modunda olduğu ve düzenleyicinin standart hata ayıklama modunda olduğu gibi yanıt vermez.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a>Fare imleci değişiklikleri
 Fare imlecini değiştirirken, VSColor hizmetine bağlı ve imleçle zaten ilişkili renkleri kullanın. İmleç değişiklikleri, devam eden bir işlemi belirtmek ve kullanıcının sürüklenebilen, üzerine bırakılabilen veya bir nesneyi seçmek için kullanılabilen bir hedefin üzerinde gezindiği isabet bölgelerini belirtmek için kullanılabilir.

 Meşgul/bekle fareimleci yalnızca kullanılabilir tüm CPU zamanı bir işlem için rezerve edildiğinde kullanın ve kullanıcının daha fazla giriş ifade etmesini engelleyin. Çok iş parçacığı kullanan iyi yazılmış uygulamalarda çoğu durumda, kullanıcıların diğer işlemleri yapmasıengellenen zamanlar nadir olmalıdır.

 İmleç değişikliklerinin başka bir yerde sunulan bilgiler için gereksiz bir ipucu olarak yararlı olduğunu unutmayın. İmleç değişikliğine, özellikle kullanıcının ele alması gereken kritik bir şeyi iletmeye çalışırken kullanıcıyla iletişim kurmanın tek yolu olarak güvenmeyin.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a>İlerleme göstergeleri
 İlerleme göstergeleri, tamamlanması birkaç saniyeden uzun süren işlemler sırasında kullanıcıya geri bildirim vermek için önemlidir. İlerleme göstergeleri yerinde (devam eden eylemin başlatma noktasının yakınında), gömülü bir durum çubuğunda, modal iletişim kutusunda veya Visual Studio durum çubuğunda gösterilebilir. Bunların kullanımı ve uygulanmasıyla ilgili [İlerleme göstergelerindeki](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) kılavuzu izleyin.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Visual Studio Bildirimler penceresi
 Visual Studio Bildirimleri penceresi geliştiricilere lisanslama, ortam (Visual Studio), uzantılar ve güncelleştirmeler hakkında bilgi verir. Kullanıcılar tek tek bildirimleri kapatabilir veya belirli bildirim türlerini yok saymayı seçebilir. Göz ardı edilen bildirimler **listesi, Araçlar > Seçenekleri** sayfasında yönetilir.

 Bildirimler penceresi şu anda genişletilebilir değil.

 ![Visual Studio Bildirimler penceresi](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio Bildirimleraraç penceresi**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a>Hata listesi
 Hata listesindeki bir bildirim, derleme ve oluşturma işlemi sırasında oluşan hataları ve uyarıları gösterir ve kullanıcının kodda bu belirli kod hatasına gitmesini sağlar.

 ![Hata listesi](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Visual Studio'da hata listesi**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a>Katıştılmış durum çubukları
 IDE durum çubuğu dinamik olduğundan, istemci bölge bağlamı etkin belge penceresine ayarlanmış ve kullanıcının bağlamı ve/veya sistem yanıtları hakkında bilgi güncelleştirilmektedir, sürekli bilgi görüntülemek veya uzun vadeli eşzamanlı işlemlerde durum vermek zordur. Örneğin, IDE durum çubuğu, birden çok çalıştırma ve/veya hemen işlenebilir madde seçimleri için test çalıştırma sonuçları bildirimleri için uygun değildir. Bu tür durum bilgilerini, kullanıcının seçim yaptığı veya bir işlem başlattığı belge veya araç penceresi bağlamında saklamak önemlidir.

 ![Gömülü durum çubuğu](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Visual Studio'da gömülü durum çubuğu**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Windows tepsi bildirimleri
 Windows bildirim alanı, Windows görev çubuğundaki sistem saatinin yanındadır. Birçok yardımcı program ve yazılım bileşeni, kullanıcının ekran çözünürlüğünü değiştirme veya yazılım güncelleştirmeleri alma gibi sistem genelindeki görevler için bağlam menüsü elde edebilmesi için bu alanda simgeler sağlar.

 Ortam düzeyinde bildirimler, Windows bildirim alanında değil, Visual Studio Bildirimleri hub'ında su yüzüne çıkarılmalıdır.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a>Bildirim balonu
 Bildirim baloncukları bir düzenleyici/tasarımcı içinde veya Windows Bildirimi alanının bir parçası olarak bilgilendirilebilir. Kullanıcı bu kabarcıkları daha sonra çözebilecekleri sorunlar olarak algılar ve bu da kritik olmayan bildirimler için bir avantajdır. Kabarcıklar, kullanıcının hemen çözmesi gereken kritik bilgiler için uygun değildir. Visual Studio'da bildirim balonu kullanıyorsanız, [bildirim kabarcıkları için Windows Masaüstü kılavuzunu](/windows/desktop/uxguide/mess-notif)izleyin.

 ![Bildirim balonu](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Visual Studio için kullanılan Windows Bildirim alanında bildirim balonu**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a>İlerleme göstergeleri

### <a name="overview"></a>Genel Bakış
 İlerleme göstergeleri, kullanıcıya geri bildirim vermek için bir bildirim sisteminin önemli bir parçasıdır. İşlemlerin ve işlemlerin ne zaman tamamlalacağını kullanıcıya söylerler. Tanıdık gösterge türleri ilerleme çubukları, dönen imleçler ve animasyonlu simgeleri içerir. İlerleme göstergesinin türü ve yerleşimi, nelerin raporlandığı ve işlemin veya işlemin tamamlanmasının ne kadar süreceği de dahil olmak üzere içeriğe bağlıdır.

#### <a name="factors"></a>Faktörler
 Hangi gösterge türünün uygun olduğunu belirlemek için aşağıdaki faktörleri belirlemeniz gerekir.

1. **Zamanlama:** operasyonun alacağı süre

2. **Modalite:** işlemin çevreye uygun olup olmadığı (işlem tamamlanana kadar UI'yi kilitler)

3. **Kalıcı/Geçici:** ilerlemenin nihai sonucunun daha sonra raporlanması ve/veya görüntülenebilir olup olmadığı

4. **Belirli/Belirsiz:** operasyonun bitiş zamanı ve ilerlemesinin hesaplanıp hesaplanamayacağı

5. **Grafik/Metin konumu:** Ilerleme veya işlem satır satırda, iletinin gövdesinde veya Ağaç denetimi gibi belirli bir denetimde yakalanıp yakalanmadığı

6. **Yakınlık:** ilerlemenin ilişkili olduğu UI'ye yakın olması gerekip gerekmediği. (Örneğin, çok uzakta olabilecek durum çubuğunda olabilir veya işlemi başlatan düğmeye yakın olması gerekir mi?)

#### <a name="determinate-progress"></a>Belirsiz ilerleme

|İlerleme türü|Ne zaman ve nasıl kullanılır|Notlar|
|-------------------|-------------------------|-----------|
|İlerleme çubuğu (belirsiz)|beklenen süre >5 saniye.<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.|Metni animasyona **yerleştirmeyin.**|
|Bilgi Çubuğu|Bağlamsal UI ile ilişkili ileti. [Bkz. Bilgi Çubukları](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.|**DON'T** Birden çok işlemi belirtmeniz gerektiğinde birden çok bilgi barı kullanmayın. Bunun yerine yığılmış ilerleme çubuklarını kullanın.|
|Çıktı Penceresi|Geçici bildirim: kullanıcının tamamlandıktan sonra ayrıntılarını **gözden** geçirmek istediği uygulama düzeyindeki işlem.|Kullanıcının verilere daha sonra başvurması gerekiyorsa **KULLANMAYIN.**|
|Günlük dosyası|Tamamlandıktan sonra ayrıntıları **kaydetmek** için önemli olduğu durumlarda geçici bildirim ile eşleştirilmiş.||
|Durum çubuğu|Geçici bildirim: kullanıcının tamamlandıktan sonra **ayrıntılarına ihtiyaç duymayacak** uygulama düzeyindeki işlem.<br /><br /> Katıştılmış bir ilerleme çubuğu içerir.<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.||

#### <a name="indeterminate-progress"></a>Belirsiz ilerleme

|İlerleme türü|Ne zaman ve nasıl kullanılır|Notlar|
|-------------------|-------------------------|-----------|
|İlerleme çubuğu (belirsiz)|beklenen süre >5 saniye.<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.|Metni animasyona **yerleştirmeyin.**|
|Karıncalar (hareketli yatay nokta)|Sunucuya gidiş dönüş.<br /><br /> Üst kapsayıcının üst tarafına bağlam noktasına yakın yerleştirilir.|Tüm kapsayıcı tarafından ebeveynlik değilse **DON'T.**|
|Spinner (ilerleme halkası)|Bağlamsal AraBirimi ile ilişkili işlem veya alanın göz önünde bulundurulduğu yer.<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.||
|Bilgi Çubuğu|Bağlamsal UI ile ilişkili ileti. [Bkz. Bilgi Çubukları](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|**DON'T** Birden çok işlemi belirtmeniz gerektiğinde birden çok bilgi barı kullanmayın. Bunun yerine yığılmış ilerleme çubuklarını kullanın.|
|Çıktı Penceresi|Geçici bildirim: kullanıcının tamamlandıktan sonra ayrıntıları **gözden geçirmek** isteyeceği uygulama düzeyinde ki işlem.|OTURUMLAR ARASıNDA devam etmesi gereken bilgiler için **KULLANMAYIN.**|
|Günlük dosyası|Tamamlandıktan sonra ayrıntıları **kaydetmek** için önemli olduğu durumlarda geçici bildirim ile eşleştirilmiş.||
|Durum çubuğu|Geçici bildirim: kullanıcının tamamlandıktan sonra **ayrıntılarına ihtiyaç duymayacak** uygulama düzeyindeki işlem.<br /><br /> Katıştılmış ilerleme çubuğu içerir.<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.||

### <a name="progress-indicator-types"></a>İlerleme göstergesi türleri

#### <a name="progress-bars"></a>İlerleme çubukları

##### <a name="indeterminate"></a>Belirsiz
 ![Belirsiz ilerleme çubuğu](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Belirsiz ilerleme çubuğu**

 "Belirsiz", bir işlemin veya sürecin genel ilerlemesinin belirlenemeyeceği anlamına gelir. Sınırsız zaman gerektiren veya bilinmeyen sayıda nesneye erişen işlemler için belirsiz ilerleme çubukları kullanın. Olanlara eşlik etmek için metinsel bir açıklama kullanın. Zaman tabanlı işlemlere sınır vermek için zaman zaman zaman larını kullanın. Belirsiz ilerleme çubukları, ilerleme nin yapıldığını göstermek için animasyonlar kullanır, ancak başka bilgi sağlamaz. Yalnızca olası doğruluk eksikliğine bağlı olarak belirsiz bir ilerleme çubuğu seçmeyin.

##### <a name="determinate"></a>Belirli
 ![Belirsiz ilerleme çubuğu](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **Belirsiz ilerleme çubuğu**

 "Belirli" bir işlemin veya işlemin, bu süre doğru tahmin edilemese bile, sınırlı bir süre gerektirdiği anlamına gelir. Açıkça tamamlanmayı gösteriyor. İşlem tamamlanmadıkça ilerleme çubuğunun yüzde 100'e gitmesine izin vermeyin. Belirli ilerleme çubuğu animasyonu soldan sağa 0'dan %100'e taşır.

 İşlem sırasında ilerleme göstergesini asla geriye doğru hareket ettirin. Çubuk, işlem başladığında sürekli olarak ilerlemeli ve sona erdiğinde %100'e ulaşmalıdır. İlerleme çubuğunun amacı, kullanıcıya kaç adım ın söz konusu olduğuna bakılmaksızın tüm işlemin ne kadar süreceği hakkında bir fikir vermektir.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Eşzamanlı raporlama (yığılmış ilerleme çubukları)
 Bir işlem uzun zaman alacaksa - belki birkaç dakika - o zaman iki ilerleme çubukları kullanılabilir, bir işlem için genel ilerleme gösterir ve başka geçerli adımın ilerlemesi için. Örneğin, bir kurulum programı çok sayıda dosyayı kopyalıyorsa, bir saniye geçerli dosya veya dizinin yüzde kaçının kopyalandığını gösterebilirken tüm işlemin ne kadar sürdüğünü belirtmek için bir ilerleme çubuğu kullanılabilir. Yığılmış ilerleme çubuklarını kullanarak beşten fazla eşzamanlı işlem veya işlem bildirmeyin. Rapor edecek beşten fazla eşzamanlı işlem veya işlem varsa, İptal düğmesine sahip bir modal iletişim kutusu kullanın ve ilerleme ayrıntılarını Çıktı Penceresi'ne bildirin.

##### <a name="textual-descriptions"></a>Metin açıklamaları
 Neler olup bittiğine ve tamamlanması için tahmini süreye eşlik etmek için metinsel bir açıklama kullanın. Bir işlemin ne kadar süreceğini belirlemek mümkün değilse, geri bildirim vermek için daha iyi bir seçim ilerleme çubuğu yerine animasyonlu bir simge olabilir.

 Visual Studio, durum çubuğunda Visual Studio'ya entegre edilmiş herhangi bir ürün tarafından kullanılabilecek standart bir ilerleme çubuğu sağlar. İlerleme çubuğu animasyonluyken neler olduğuna ait metinaçıklamaları için durum çubuğu metni güncelleştirilebilir.

#### <a name="other-progress-indicators"></a>Diğer ilerleme göstergeleri

##### <a name="ants-animated-horizontal-dots"></a>Karıncalar (hareketli yatay nokta)
 ![İlerleme karıncalar](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Karıncalar," animasyonlu yatay nokta, belirsiz bir gidiş-dönüş sunucu işlemi için görsel bir referans sağlar.

##### <a name="spinner-progress-ring"></a>Spinner (ilerleme halkası)
 ![İlerleme spinner](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 Spinner ("ilerleme halkası" olarak da bilinir), öncelikle bağlamsal UI ile ilgili olarak kullanılan belirsiz bir ilerleme göstergesidir. Bir spinner'ı metin kategori üstbilgi, ileti veya denetim gibi ilgili içeriğine yakın bir şekilde görüntüleyin.

##### <a name="cursor-feedback"></a>İmleç geri bildirimi
 2-7 saniye arasında süren işlemler için imleç geri bildirimi sağlayın. Genellikle, bu işletim sistemi tarafından sağlanan bekleme imleci kullanarak anlamına gelir. Kılavuz için, MSDN makale [Imleçleri.Wait Özellik](/dotnet/api/system.windows.input.cursors.wait)bakın.

#### <a name="progress-indicator-locations"></a>İlerleme göstergesi konumları

##### <a name="status-bar"></a>Durum çubuğu
 Durum çubuğu, uygulamanız için kullanıcının çalışmasını kesintiye uğratmadan kullanıcıya iletileri ve yararlı bilgileri görüntüleyebilme yeri verir. Genellikle bir pencerenin alt kısmında görüntülenen, ilerleme durumu bir ilerleme çubuğu göstergesi ile birlikte ilerleme ölçüsü hakkında bir ileti içeren bir araç ipucu bölmesi olacaktır.

 ![İlerleme çubuğu olan durum çubuğu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **İlerleme çubuğu olan durum çubuğu**

 ![İleti içeren durum çubuğu](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Metin açıklaması içeren durum çubuğu**

##### <a name="infobar"></a>Bilgi Çubuğu
 Durum çubuğuna benzer şekilde, bilgi çubuğu da ilerleme çubuğu veya spinner gibi belirsiz ilerleme göstergeleri ile eşleştirilmiş olabilir bağlamsal bildirim ve ileti sağlar. Bilgi çubuğu parçalı düzey ilerleme veya belirsiz ilerleme göstergesi sağlamamalıdır. [Bkz. Bilgi Çubukları](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![İlerleme çubuğu ve mesajlaşma ile bilgi çubuğu](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **İlerleme çubuğu ve metin açıklaması ile bilgi çubuğu**

 ![Pencere içindeki bilgi çubuğu](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Satır içi
 Satır satırlı ilerleme göstergesi, ilerleme yükleyici türlerinden herhangi biri tarafından temsil edilebilir. Genellikle ilerleme göstergesi iletiyle eşlenir, ancak bu bir gereklilik değildir.

 ![Satır satırda ilerleme spinner](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Spinner metin açıklaması ile birlikte**

 ![Satır satırlı ilerleme çubukları](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Yığılmış ilerleme çubuklarını belirli**

 ![Satır satırlı ilerleme iletisi](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Sunucu Gezgini satır içinde metin: Yenileniyor...**

##### <a name="tool-windows"></a>Araç pencereleri
 Genel ilerleme göstergesi, araç çubuğunun hemen altında konumlandırılmış belirsiz bir ilerleme çubuğu yla temsil edilir.

 ![Genel belirsiz ilerleme çubuğu](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Takım Gezgini genel belirsiz ilerleme çubuğu**

##### <a name="dialogs"></a>İletişim Kutuları
 İletişim kutuları, ilerleme yükleyici türlerinden herhangi birini içerebilir. İlerleme göstergeleri, ayrıntılı ve alt süreçleri temsil edecek şekilde birden çok ilerleme göstergesi düzeyiyle birleştirilebilir.

 ![Birden çok ilerleme göstergesi türüolan iletişim kutusu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Eşzamanlı süreçler ve birden çok ilerleme gösterge türü içeren Visual Studio iletişim kutusu**

 ![İlerleme yükleyici ve mesajlaşma ile iletişim kutusu](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Progress loader ve ileti satır altı komutu ile Visual Studio iletişim kutusu**

##### <a name="document-well"></a>Belge iyi
 Belge iyi denetimleri ile birlikte birden çok ilerleme yükleyici türleri görüntüleyebilirsiniz.

 ![Belgede ilerleme iletisi iyi](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Araç çubuğunun altında belirsiz ilerleme çubuğu**

##### <a name="output-window"></a>Çıktı Penceresi
 Çıktı penceresi, satır satırlı metin iletisi aracılığıyla işlem ilerlemesi ve devam eden ilerleme durumunu işlemek için uygundur. Herhangi bir Çıktı penceresi ilerleme raporlaması ile birlikte Durum çubuğunu kullanmalısınız.

 ![Çıkış Penceresinde İlerleme iletisi](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Devam eden işlem durumu ve bekleme iletisi ile Çıkış Penceresi**

## <a name="infobars"></a><a name="BKMK_Infobars"></a>Bilgi Çubukları

### <a name="overview"></a>Genel Bakış
 Bilgi çubukları kullanıcıya dikkat noktasına yakın bir gösterge verir ve paylaşılan bilgi çubuğu denetimini kullanmak görsel görünüm ve etkileşimde tutarlılık sağlar.

 ![Bilgi Çubuğu](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Visual Studio'daki Bilgi Çubukları**

#### <a name="appropriate-uses-for-an-infobar"></a>Bilgi çubuğu için uygun kullanımlar

- Kullanıcıya geçerli bağlamla ilgili engelleyici olmayan ancak önemli bir ileti vermek için

- UI'nin, geçmiş hata ayıklama gibi bazı etkileşim etkileri taşıyan belirli bir durumda veya durumda olduğunu belirtmek için

- Kullanıcıya sistemin performans sorunlarına neden olduğu gibi sorunlar algıladığını bildirmek için

- Kullanıcıya, düzenleyicinin bir dosyanın karışık sekmeleri ve boşlukları olduğunu algılaması gibi, kolayca işlem yapmanın bir yolunu sağlamak için

##### <a name="do"></a>Yapın:

- Bilgi çubuğu ileti metnini kısa ve noktaya kadar tutun.

- Bağlantıları ve düğmeleri kısa metin tutun.

- Kullanıcılara sağladığınız "eylem" seçeneklerinin yalnızca gerekli eylemleri gösteren en az düzeyde olduğundan emin olun.

##### <a name="dont"></a>Yapma:

- Araç çubuğuna yerleştirilmesi gereken standart komutlar sunmak için bir bilgi çubuğu kullanın.

- Modal iletişim kutusu yerine bir bilgi çubuğu kullanın.

- Pencerenin dışında kayan bir ileti oluşturun.

- Aynı pencere içinde çeşitli konumlarda birden çok bilgi barı kullanın.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Birden çok bilgi barı aynı anda gösterilebilir mi?
 Evet, birden çok bilgi barı aynı anda gösterilebilir. Bunlar, ilk gelen, ilk hizmet sırasına göre, üstte gösterilen ilk bilgi çubuğu ve aşağıda gösterilen ek bilgi çubukları yla görüntülenir.

 Kullanıcı aynı anda en fazla üç bilgi çubuğu görür, bundan sonra daha fazla bilgi çubuğu varsa, bilgi çubuğu bölgesi kaydırılabilir hale gelir.

### <a name="creating-an-infobar"></a>Bilgi çubuğu oluşturma
 Bilgi çubuğu soldan sağa dört bölümden oluşur:

- **Simge:** Burası, bilgi çubuğu için görüntülemek istediğiniz simgeyi uyarı simgesi gibi eklersiniz.

- **Metin:** Gerekirse, metin içindeki bağlantılarla birlikte, kullanıcının içinde olduğu senaryoyu/durum durumunu açıklamak için metin ekleyebilirsiniz. Metni kısa tutmayı unutmayın.

- **Eylemler:** Bu bölümde, kullanıcının bilgi çubuğunuzda alabilecekleri eylemler için bağlantılar ve düğmeler bulunmalıdır.

- **Kapat düğmesi:** Sağdaki son bölümde bir kapatma düğmesi olabilir.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Yönetilen kodda standart bir bilgi çubuğu oluşturma
 InfoBarModel sınıfı, bir bilgi çubuğu için veri kaynağı oluşturmak için kullanılabilir. Bu dört yapıcıdan birini kullanın:

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(IEnumerable<IVsInfoBarTextSpan> textSpans, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);

```

```
public InfoBarModel(string text, IEnumerable<IVsInfoBarActionItem> actionItems, ImageMoniker image = default(ImageMoniker), bool isCloseButtonVisible = true);
```

 Burada bir köprü, bir eylem düğmesi ve bir simge ile bazı metin ile bir InfoBarModel oluşturur bir örnektir.

 ![Köprülü Bilgi Çubuğu](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

```
var infoBar = new InfoBarModel(
    textSpans: new[]
    {
        new InfoBarTextSpan("This is a "),
        new InfoBarHyperlink("hyperlink"),
        new InfoBarTextSpan(" InfoBar.")
    },
    actionItems: new[]
    {
        new InfoBarButton("Click Me")
    },
    image: KnownMonikers.StatusInformation,
    isCloseButtonVisible: true);

```

#### <a name="creating-a-standard-infobar-in-native-code"></a>Yerel kodda standart bir bilgi çubuğu oluşturma
 Yerel koddan bir bilgi çubuğu sağlamak için IVsInfoBar arabirimini uygulayın.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Bilgi çubuğundan bilgi çubuğu UIElement alma
 InfoBarModel veya IVsInfoBar uygulaması, UI'de gösterilebilmesi için UIElement'e dönüştürülmesi gereken veri modelleridir. Bir Kullanıcı Bir Kullanıcı Yada Kullanıcı Burdası, SVsInfoBarUIFactory/IVsInfoBarUIFactory hizmeti ile alınabilir.

```
private bool TryCreateInfoBarUI(IVsInfoBar infoBar, out IVsInfoBarUIElement uiElement)
{
    IVsInfoBarUIFactory infoBarUIFactory = serviceProvider.GetService(typeof(SVsInfoBarUIFactory)) as IVsInfoBarUIFactory;
    if (infoBarUIFactory == null)
    {
        uiElement = null;
        return false;
    }

    uiElement = infoBarUIFactory.CreateInfoBar(infoBar);
    return uiElement != null;
}
```

### <a name="placement"></a>Yerleştirme
 Bilgi çubukları aşağıdaki konumlardan birinde veya daha fazlasında gösterilebilir:

- Araç pencereleri

- Belge sekmesi içinde

> [!IMPORTANT]
> Küresel bağlam hakkında bir ileti vermek için bir bilgi çubuğu konumlandırmak mümkündür. Bu, araç çubukları ve belge arasında iyi görünür. Bu, IDE'nin atlama ve ile ilgili sorunlara neden olduğu ve kesinlikle gerekli ve uygun olmadıkça kaçınılması gerektiği için önerilmez.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>ToolWindowPane'ye bilgi çubuğu yerleştirme
 ToolWindowPane.AddInfoBar(IVsInfoBar) yöntemi bir araç penceresine bilgi çubuğu eklemek için kullanılabilir. Bu API ya bir IVsInfoBar (infobarmodel varsayılan bir uygulama) veya bir IVsUIElement ekleyebilirsiniz.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Bir belgeye bilgi çubuğu yerleştirme veya ToolWindowPane olmayan
 Herhangi bir IVsWindowFrame içine bir bilgi çubuğu yerleştirmek için, çerçeve için IVsInfoBarHost almak ve sonra infobar UIElement eklemek için VSFPROPID_InfoBarHost özelliğini kullanın.

```
private void AddInfoBar(IVsWindowFrame frame, IVsUIElement uiElement)
{
    IVsInfoBarHost infoBarHost;
    if (TryGetInfoBarHost(frame, out infoBarHost))
    {
        infoBarHost.AddInfoBar(uiElement);
    }
}
private bool TryGetInfoBarHost(IVsWindowFrame frame, out IVsInfoBarHost infoBarHost)
{
    object infoBarHostObj;
    if (ErrorHandler.Failed(frame.GetProperty((int)__VSFPROPID7.VSFPROPID_InfoBarHost, out infoBarHostObj)))
    {
        infoBarHost = null;
        return false;
    }

    infoBarHost = infoBarHostObj as IVsInfoBarHost;
    return infoBarHost != null;
}

```

#### <a name="placing-an-infobar-in-the-main-window"></a>Ana pencereye bilgi çubuğu yerleştirme
 Ana pencereye bir bilgi çubuğu yerleştirmek için, ana pencerenin IVsInfoBarHost almak için IVsShell hizmetinin VSSPROPID_MainWindowInfoBarHost kullanın ve sonra infobar UIElement ekleyin.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Kullanıcının bilgi çubuğumda ne zaman harekete geçeceğini bilecek miyim?
 Evet, her etkinlik eylemini bilgi çubuğu yazarına geri döndüreceğiz. Daha sonra bilgi çubuğundaki kullanıcı seçimine dayalı olarak IDE'de işlem yapmak bilgi çubuğu yazarına bağlıdır. Bilgi çubukları, Kapat düğmesi tıklatılmış olan ana bilgisayardan otomatik olarak kaldırılır, ancak diğer bilgi çubuklarının kapatılmasından sonra kaldırılması gerekiyorsa ek çalışma gerekir. Telemetri de her bilgi çubuğu tarafından bağımsız olarak günlüğe kaydedilmesi gerekir.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>ToolWindowPane'de bilgi çubuğu olayları alma
 ToolWindowPane bilgi çubukları için iki olay vardır. ToolWindowPane'deki bir bilgi çubuğu kapatıldığında InfoBarClosed olayı açılır. InfoBarActionItemClicked olayı, bilgi çubuğunun içindeki bir köprü veya düğme tıklatıldığında yükseltilir.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Bilgi çubuğu olaylarını doğrudan UIElement'ten alma
 IVsInfoBarUIElement.Advise doğrudan bir infobar's UIElement olaylara abone olmak için kullanılabilir. IVsInfoBarUIEvents uygulanması yazarın yakın ve tıklama olayları almak için izin verecektir.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a>Hata doğrulama
 Bir kullanıcı, gerekli bir alanın atlanması veya verilerin yanlış biçimde girilmesi gibi kabul edilemez bilgiler girdiğinde, engelleme açılır hata iletişim kutusunu kullanmak yerine denetimin yanında denetim doğrulamaveya geri bildirim kullanmak daha iyidir.

### <a name="field-validation"></a>Alan doğrulama
 Form ve alan doğrulaması üç bileşenden oluşur: denetim, simge ve araç ucu. Bunu çeşitli denetim türleri kullanabilse de, bir metin kutusu örnek olarak kullanılır.

 ![Alan doğrulama &#40;boş&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Alan gerekiyorsa, ** \<gerekli>** belirten filigran metin olmalı ve alan arka plan `Environment.ControlEditRequiredBackground`açık sarı olmalıdır (VSColor: ) `Environment.ControlEditRequiredHintText`ve ön plan gri olmalıdır (VSColor: ):

 !["Gerekli" etiketiyle alan doğrulaması](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Program, denetimin başka bir denetime taşındığında veya kullanıcı [Tamam] commit düğmesini tıklattığında veya kullanıcı belgeyi veya formu kaydettiğinde *girilen geçersiz içerik* durumunda olduğunu belirleyebilir.

 Geçersiz içerik durumu belirlendiğinde, denetimin içinde veya hemen yanında bir simge görüntülenir. Hatayı açıklayan bir araç ucu simgenin veya denetimin üzerinde görünmelidir. Ayrıca, geçersiz durumu oluşturan denetimin çevresinde 1 piksellik kenarlık görünmelidir.

 ![Alan doğrulama düzeni belirtimleri](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Alan doğrulama için düzen belirtimleri**

#### <a name="acceptable-variations-for-icon-location"></a>Simge konumu için kabul edilebilir varyasyonlar
 Kullanıcıların doğrulama hataları hakkında bilgilendirilmesi gereken sayısız benzersiz durum vardır. UI'nin denetim türünü ve yapılandırmasını göz önünde bulundurarak, durumunuza uygun simge yerleşimini seçin.

 ![Simge konumu için kabul edilebilir konumlar](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Alan doğrulama simgesi konumları için kabul edilebilir varyasyonlar**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Sunucuya veya ağ bağlantısına gidiş-dönüş gerektiren doğrulama
 Bazı durumlarda, içeriği doğrulamak için sunucuya gidiş-dönüş bir yolculuk gerekir ve kullanıcının ilerlemesini, doğrulanmış ve hata durumlarını göstermek önemlidir. Aşağıdaki şekil, bu durumun bir örneğini ve önerilen u-posta adresini gösterir.

 ![Sunucuya gidiş dönüş içeren doğrulama](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Sunucuya gidiş dönüş içeren doğrulama**

 "Doğrulama..." ve "Yeniden Deneyin" metni.

#### <a name="in-place-warning-text"></a>Yerinde uyarı metni
 Hata iletisini denetime yakın bir hata durumunda koymak için kullanılabilir bir alan olduğunda, bu araç ucunu tek başına kullanmak için tercih edilir.

 ![&#45;yerde uyarı](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Yerinde uyarı metni**

#### <a name="watermarks"></a>Filigranlar
 Bazen tüm denetim veya pencere hata durumundadır. Bu durumda, hatayı belirtmek için bir filigran kullanın.

 ![Filigran](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Filigran alan doğrulaması**
