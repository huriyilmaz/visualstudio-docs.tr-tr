---
title: Visual Studio için bildirimler ve Ilerleme durumu | Microsoft Docs
description: kullanıcılara yazılım geliştirme görevleriyle ilgili Visual Studio neler olduğunu bildirmek için çeşitli yollar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e4c42692a4540febbcce4355f0324355a92e362b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144476"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Visual Studio İçin Bildirimler ve İlerleme Durumu
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Bildirim sistemleri

### <a name="overview"></a>Genel Bakış
 kullanıcıya yazılım geliştirme görevleriyle ilgili Visual Studio neler olduğunu bildirmek için birkaç yol vardır.

 Herhangi bir tür bildirim uygularken:

- **Bildirimlerin sayısını en düşük etkin sayı olarak tutun** . bildirim iletileri büyük bir Visual Studio kullanıcı veya belirli bir özellik/özellik alanı kullanıcıları için geçerlidir. Bildirimlerin aşırı kullanımı, kullanıcıyı daha fazla izleyebilir veya sistem tarafından algılanan kullanımı hafifletmek için kullanılabilir.

- Kullanıcının daha karmaşık seçimler yapmak ve daha fazla eylem gerçekleştirmek için uygun bağlamı çağırmak için kullanabileceği **Açık, işlem yapılabilir iletiler Suntığınızdan emin olun** .

- **Zaman uyumlu ve zaman uyumsuz iletileri uygun şekilde sunun.** Zaman uyumlu bildirimler, bir Web hizmeti kilitlenmesinin veya kod özel durumunun oluşturulduğu durumlar gibi bir şeyin anında ilgilenilmesi gerektiğini gösterir. Kullanıcı, kalıcı iletişim kutusunda olduğu gibi giriş gerektiren bir şekilde bu durumlardan haberdar olmalıdır. Zaman uyumsuz bildirimler, kullanıcının hakkında bilgi sahibi olması gerekir, ancak bir derleme işlemi tamamlandığında veya bir Web sitesi dağıtımı tamamlandığında, hemen üzerinde işlem yapması gerekmez. Bu iletiler daha fazla çevresel olmalıdır ve kullanıcının görev akışını kesintiye uğramaz.

- Yalnızca kullanıcının iletiyi bildirmeden veya iletişim kutusunda sunulma kararı vermeden önce **daha fazla işlem yapmasını engellemek için gerekli olduğunda kalıcı iletişim kutularını kullanın** .

- **Ortam bildirimlerini artık geçerli olmadığında kaldırın.** Bildirimde bulunuldukları sorunu gidermek üzere bir işlem gerçekleştirmişse kullanıcının bir bildirimi kapatması gerekmez.

- **Bildirimlerin, yanlış Bağıntılara yol açabileceğini unutmayın.** Kullanıcılar bir veya daha fazla eylemi, aslında bir causal ilişkisi olmadığında bir bildirim tetiklediğini düşünmeyebilir. Bildirim iletisinde bağlam, tetikleyici ve bildirimin kaynağı hakkında net bir onay olun.

### <a name="choosing-the-right-method"></a>Doğru yöntemi seçme
 İletinizin kullanıcısına bildirimde bulunan doğru yöntemi seçerken size yardımcı olması için bu tabloyu kullanın.

|Yöntem|Kullanın|Kullanma|
|------------|---------|----------------|
|[Kalıcı hata iletisi iletişimleri](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ModalErrorMessageDialogs)|Devam etmeden önce bir kullanıcı yanıtı gerektiğinde kullanın.|Kullanıcıyı engellemeye ve akışını kesmeye gerek kalmadığında kullanmayın. İletiyi başka, daha az zorlayıcı bir biçimde göstermek mümkünse, kalıcı iletişim kutuları kullanmaktan kaçının.|
|[IDE durum çubuğu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_IDEStatusBar)|Bir işlemin durumuyla ilgili çevresel metin bilgisi olduğunda kullanın.|Tek başına kullanmayın. Başka bir geri bildirim mekanizmasıyla birlikte en iyi şekilde kullanılır.|
|[Katıştırılmış bilgi çubuğu](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedInfobar)|Bir araç penceresinde veya belge penceresinde, ilerlemeyi, hata durumunu, sonuçları ve/veya eyleme dönüştürülebilir bilgileri bildirmek için öğesini kullanın.|Bilgiler bilgi çubuğu 'nun yerleştirildiği konumla ilgili değilse kullanmayın.<br /><br /> Belge/araç penceresi dışında kullanmayın.|
|[Fare imleci değişiklikleri](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_MouseCursorChanges)|Bir işlemin devam ettiğinin bildirilmesini bildirmek için kullanılabilir. Ayrıca, sürükle/bırak işlemi devam ederken veya fare imlecinin çizim modu gibi belirli bir modda olduğu gibi, fare içinde bir durum değişikliği olduğunu bildirmek için de kullanılır.|Kısa ilerleme değişiklikleri için kullanmayın veya imlecin (örneğin, tüm işlem yerine daha uzun çalışan bir işlemin bölümlerine bağlı olduğunda).|
|[İlerleme göstergeleri](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotSysProgressIndicators)|İlerlemeyi raporlamak için ihtiyacınız olduğunda kullanın (determinya da belirsiz). Her biri için çeşitli ilerleme göstergesi türleri ve belirli kullanımlar vardır. Bkz. [ilerleme göstergeleri](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators).||
|[Visual Studio Bildirimler penceresi](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Bildirimler penceresi genel olarak genişletilebilir değildir. bununla birlikte, Visual Studio hakkındaki bir aralıktaki iletileri iletmek ve Visual Studio veya paketlere yönelik güncelleştirmelerin bilgilendirme bildirimleriyle ilgili önemli sorunlar da dahil olmak üzere kullanılır.|Diğer bildirim türleri için kullanmayın.|
|[Hata listesi](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ErrorList)|Sorun, kullanıcının şu anda açık olan çözümüyle bir sorun (hata/uyarı/bilgi) ile bağlantılı olduğunda, kod üzerinde işlem yapması gerekebilir.<br /><br /> Bu, örneğin:<br /><br /> -Derleyici iletileri (hata/uyarı/bilgi)<br /><br /> -Kod çözümleyici/kodla ilgili tanılama iletileri<br /><br /> -Derleme iletileri<br /><br /> Proje veya çözüm dosyalarıyla ilgili sorunlar için uygun olabilir, ancak önce Çözüm Gezgini bir gösterge düşünün.|Kullanıcının açık çözüm koduyla hiçbir ilişkisi olmayan öğeler için kullanmayın.|
|Düzenleyici bildirimleri: ampul|Açık dosyada bulunan bir sorunu çözmeye yönelik bir düzelme olduğunda kullanın.<br /><br /> Açık ampul 'in, yeniden düzenlemeler gibi isteğe bağlı olarak kullanıcının kodunda gerçekleştirilen hızlı eylemleri barındırmak için de kullanılması gerektiğini unutmayın, ancak bu durumda "bildirim stili" görüntülenmez.|Açık dosyayla ilişkisi olmayan öğeler için kullanmayın.|
|Düzenleyici bildirimleri: dalgalı çizgiler|Kullanıcıyı açık kodların belirli bir yayılımı (örneğin, hatalara yönelik kırmızı bir dalgalı çizgi) ile ilgili bir sorun için uyarmak üzere kullanın.|Açık kodların belirli bir yayılımı ile ilgisi olmayan öğeler için kullanmayın.|
|[Gömülü durum çubukları](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_EmbeddedStatusBars)|Belirli bir araç penceresi, belge penceresi veya iletişim penceresi bağlamı dahilinde içerik veya işlemle ilgili durum sağlamak için kullanın.|Genel ürün bildirimleri, süreçler veya belirli bir pencerede bulunan içerikle ilişkisi olmayan öğeler için kullanmayın.|
|[Windows tepsi bildirimleri](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_WindowsTray)|İşlem dışı süreçler veya yardımcı uygulamalar için yüzey bildirimleri için kullanın.|IDE ile ilgili bildirimler için kullanmayın.|
|[Bildirim kabarcıkları](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_NotificationBubbles)|Uzak bir işlemi bilgilendirmek veya IDE **dışındaki** değişikliği yapmak için kullanın.|IDE **içinde** işlem kullanıcısına bildirimde bulunmak için bir yol olarak kullanmayın.|

### <a name="notification-methods"></a>Bildirim yöntemleri

#### <a name="modal-error-message-dialogs"></a><a name="BKMK_ModalErrorMessageDialogs"></a> Kalıcı hata iletisi iletişimleri
 Kullanıcının onayını veya eylemini gerektiren bir hata iletisini göstermek için kalıcı bir hata mesajı iletişim kutusu kullanılır.

 ![Kalıcı hata iletisi](../../extensibility/ux-guidelines/media/0901-01_modalerrormessage.png "0901-01_ModalErrorMessage")

 **Kalıcı bir hata iletisi iletişim kutusu, bir veritabanına geçersiz bir bağlantı dizesi kullanıcısını uyarır**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> IDE durum çubuğu
 kullanıcıların durum çubuğu metnini nasıl fark ettiğini fark eden, Windows platformuyla ilgili kendi bilgisayar deneyimine ve belirli deneyimlerle nasıl ilişkili olduğuna dair bir olasılık. Visual Studio müşteri tabanı her iki alanda da karşılaşılmalıdır, ancak bilgili Windows kullanıcılar durum çubuğundaki değişiklikleri kaçırırmış olabilir. Bu nedenle, durum çubuğu en iyi bilgi amaçlı olarak veya başka bir yerde sunulan bilgiler için bir gereksiz ipucu olarak kullanılır. Kullanıcının hemen çözümlenmesi gereken her türlü kritik bilgi, bir iletişim kutusunda veya bildirimler araç penceresinde sağlanmalıdır.

 Visual Studio durum çubuğu, çeşitli bilgi türlerinin görüntülenmesine izin vermek için tasarlanmıştır. Geri bildirim, tasarımcı, ilerleme çubuğu, animasyon ve istemci için bölgelere bölünmüştür.

 Geri bildirim bölgesi ve tasarımcı bölgesi her zaman görünür. İlerleme çubuğu ve animasyon bölgeleri her zaman dinamik ve Kullanıcı bağlamına dayalıdır. Tasarımcı bölgesinin, SMS mesajı için eşlik eden bir kaynaktan çekilen dizenin uzunluğuna göre belirlenen statik bir genişliği vardır. Bu, yerelleştirmenin bir kod değişikliğine gerek duymadan genişliği yeniden boyutlandırmasını sağlar. Ingilizce için bu dizenin genişliği kabaca 220 pikseldir. Tasarımcı bölgesi normal şekilde davranır ve geri bildirim bölgesi kalan alanı artışlarını devralarak olacaktır.

 Durum çubuğu ayrıca, IDE 'nin hata ayıklama modunda olduğu gibi çeşitli IDE durum değişikliklerine iletişim kurarak görsel ilgi ve işlevsel değer eklemek için de renklendirilmiştir.

 ![IDE durum çubuğu renk değişiklikleri](../../extensibility/ux-guidelines/media/0901-02_idestatusbar.png "0901-02_IDEStatusBar")

 **IDE durum çubuğu renkleri**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Katıştırılmış bilgi çubuğu
 Bir bilgi çubuğu, bir belge penceresinin veya araç penceresinin en üstünde, bir durum veya koşulun kullanıcıya bilgi vermek için kullanılabilir. Ayrıca, kullanıcının kolayca işlem yapması için bir yol kullanabilmesi için komutlar sunabilir. Bilgi çubuğu standart bir kabuk denetimidir. Kendi verilerinizi oluşturmaktan kaçının. Bu, IDE 'deki diğer kişilerle tutarsız ve görünür olacak şekilde çalışır. Uygulama ayrıntıları ve kullanım [Kılavuzu için bkz](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) ..

 ![Katıştırılmış bilgi çubuğu](../../extensibility/ux-guidelines/media/0901-03_embeddedinfobar.png "0901-03_EmbeddedInfobar")

 **Belge penceresine gömülü bir bilgi çubuğu, kullanıcıya IDE 'nin geçmiş hata ayıklama modunda olduğunu ve düzenleyicinin standart hata ayıklama modunda olduğu gibi yanıt vermemesini uyarır.**

#### <a name="mouse-cursor-changes"></a><a name="BKMK_MouseCursorChanges"></a> Fare imleci değişiklikleri
 Fare imlecini değiştirirken, Vsccolors hizmetine bağlı olan ve imleç ile zaten ilişkili olan renkleri kullanın. İmleç değişiklikleri, devam eden bir işlemin, kullanıcının sürüklenebileceği, üzerinde bırakılan veya bir nesne seçmek için kullanılan bir hedefin üzerinde işaret ettiği bir hedefin üzerine gelmekte olduğu isabet bölgelerinin yanı sıra kullanılabilir.

 Meşgul/bekleme fare imlecini yalnızca, kullanılabilir tüm CPU saatinin bir işlem için ayrılması ve kullanıcının başka bir girişi ifade etmesini engellemek için kullanın. Birçok durumda, iş parçacığı kullanan iyi yazılmış uygulamalar, kullanıcıların başka işlemler yapmaktan engellenmesinin ne zaman nadir olması gerekir.

 İmleç değişikliklerinin başka bir yerde sunulan bilgiler için gereksiz bir ipucu olarak yararlı olduğunu aklınızda bulundurun. Bir imlece güvenmeyin, özellikle kullanıcının ele alması gereken önemli bir şeyi almaya çalışırken kullanıcıyla iletişim kurmanın tek bir yolu olarak değişir.

#### <a name="progress-indicators"></a><a name="BKMK_NotSysProgressIndicators"></a> İlerleme göstergeleri
 İlerleme göstergeleri, birkaç saniyeden daha fazla geçen bir işlem sırasında Kullanıcı geri bildirimi vermek için önemlidir. ilerleme göstergeleri, yerinde (sürmekte olan eylemin başlatma noktasının yakınında), gömülü bir durum çubuğunda, kalıcı bir iletişim kutusunda veya Visual Studio durum çubuğunda gösterilir. Kullanım ve uygulamayla ilgili olarak [devam eden göstergeler](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) kılavuzunu izleyin.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a>Visual Studio Bildirimler penceresi
 Visual Studio bildirimleri penceresi, geliştiricilere lisanslama, ortam (Visual Studio), uzantılar ve güncelleştirmeler hakkında bilgilendirir. Kullanıcılar bireysel bildirimleri kapatabilir veya belirli bildirim türlerini yok saymayı seçebilirler. Yoksayılan bildirimlerin listesi bir **araçlar > seçenekleri** sayfasında yönetilir.

 Bildirimler penceresi şu anda genişletilebilir değil.

 ![Visual Studio Bildirimler penceresi](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio Bildirimler araç penceresi**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Hata listesi
 Hata listesi içindeki bir bildirim, derleme ve derleme işlemleri sırasında oluşan hataları ve uyarıları gösterir ve kullanıcının kodda belirli bir kod hatasına gitmesini sağlar.

 ![Hata listesi](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Visual Studio hata listesi**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Gömülü durum çubukları
 IDE durum çubuğu dinamik olduğu için, istemci bölgesi bağlamı etkin belge penceresine ayarlanmış ve kullanıcının bağlamında ve/veya sistem yanıtlarında bilgi güncelleştiren bir sürekli bilgi görüntülenmesini veya uzun süreli zaman uyumsuz işlemlere durum vermenizi zorlaştırıyor. Örneğin, IDE durum çubuğu, birden çok çalıştırma ve/veya hemen eyleme dönüştürülebilir öğe seçimi için test çalıştırması sonuçlarının bildirimleri için uygun değildir. Bu tür durum bilgilerinin, kullanıcının seçim yaptığı veya bir işlemi başlattığı belge veya araç penceresi bağlamında tutulması önemlidir.

 ![Gömülü durum çubuğu](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Visual Studio katıştırılmış durum çubuğu**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a>Windows tepsi bildirimleri
 Windows bildirim alanı Windows görev çubuğundaki sistem saatinin yanında olur. Birçok yardımcı program ve yazılım bileşeni, kullanıcının ekran çözünürlüğünü değiştirme veya yazılım güncelleştirmelerini alma gibi sistem genelinde görevlere yönelik bağlam menüsünü elde edebilmesi için bu alana simgeler sağlar.

 ortam düzeyinde bildirimler, Windows bildirim alanında değil Visual Studio bildirim hub 'ında kullanıma alınmalıdır.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Bildirim kabarcıkları
 bildirim kabarcıkları bir düzenleyici/tasarımcı içinde veya Windows bildirim alanının parçası olarak görünebilir. Kullanıcı bu kabarcıkları daha sonra çözebilecekleri sorunlar olarak beyin, bu da kritik olmayan bildirimlere yönelik bir avantajdır. Kabarcıklar, kullanıcının hemen çözmeleri gereken kritik bilgiler için uygun değildir. Visual Studio 'de bildirim kabarcıkları kullanıyorsanız, [bildirim kabarcıkları için Windows masaüstü kılavuzunu](/windows/desktop/uxguide/mess-notif)izleyin.

 ![Bildirim balonu](../../extensibility/ux-guidelines/media/0901-07_notificationbubbles.png "0901-07_NotificationBubbles")

 **Visual Studio için kullanılan Windows bildirim alanındaki bildirim balonu**

## <a name="progress-indicators"></a><a name="BKMK_ProgressIndicators"></a> İlerleme göstergeleri

### <a name="overview"></a>Genel Bakış
 İlerleme göstergeleri, Kullanıcı geri bildirimi vermek için bir bildirim sisteminin önemli bir parçasıdır. İşlemler ve işlemler tamamlandığında kullanıcıya bildirir. Tanıdık gösterge türleri arasında ilerleme çubukları, dönen imleçler ve animasyonlu simgeler bulunur. İlerleme göstergesinin türü ve yerleşimi, nelerin bildirilmekte olduğunu ve işlemin veya işlemin tamamlanması için ne kadar sürdüğünü de içerecek şekilde bağlama göre değişir.

#### <a name="factors"></a>Etmen
 Hangi gösterge türünün uygun olduğunu belirleyebilmek için aşağıdaki faktörleri belirlemeniz gerekir.

1. **Zamanlama:** işlemin gerçekleşmesi için gereken süre

2. **Modlık:** işlemin ortama kalıcı olup olmadığı (işlem tamamlanana kadar Kullanıcı arabirimini kilitler)

3. **Kalıcı/geçici:** ilerlemenin nihai sonucunun daha sonra raporlanıp bildirilmeyeceğini ve/veya ne zaman görüntülenemeyeceğini

4. **Kesin/belirsiz:** işlemin bitiş saati ve ilerleme durumunun hesaplanıp hesaplanmayacağını belirtir

5. **Grafik/metinsel konum:** ilerleme veya işlemin satır içinde, bir iletinin gövdesinde mi yoksa ağaç denetimi gibi belirli bir denetimin mi yakalandığından

6. **Yakınlık:** ilerleme durumunun, ilişkili olduğu Kullanıcı arabirimine yakın bir yerde olması gerekip gerekmediğini belirtir. (Örneğin, durum çubuğunda olabilir, bu da çok daha fazla olabilir veya işlemi başlatan düğmeye yaklaşmak zorunda kalabilir mi?)

#### <a name="determinate-progress"></a>İlerlemeyi belirleyici

|İlerleme türü|Ne zaman ve nasıl kullanılır?|Notlar|
|-------------------|-------------------------|-----------|
|İlerleme çubuğu (Determina)|5 saniyelik beklenen süre >.<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.|Animasyonu **metne katıştırma.**|
|Üstündeki|Bağlamsal Kullanıcı arabirimiyle ilişkili mesajlaşma. Bkz. [Esnek](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.|Birden çok işlem belirtmeniz gerektiğinde birden çok **çocuk kullanmayın.** Bunun yerine yığılmış ilerleme çubukları kullanın.|
|Çıktı Penceresi|Geçici bildirim: kullanıcının tamamlandığında ayrıntıları **gözden geçirmek** istediği uygulama düzeyi işleme.|Kullanıcının verilere daha sonra başvurması **gerekiyorsa kullanmayın.**|
|Günlük dosyası|Tamamlanma sonrasında ayrıntıları **kaydetmek** önemli olduğunda, durumlarda geçici bildirimle eşleştirilmiş.||
|Durum çubuğu|Geçici bildirim: uygulama düzeyindeki işlem, kullanıcının tamamlanmasının ardından ayrıntılarına **ihtiyaç duymayacak** .<br /><br /> Gömülü bir ilerleme çubuğu içerir.<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.||

#### <a name="indeterminate-progress"></a>Belirsiz ilerleme

|İlerleme türü|Ne zaman ve nasıl kullanılır?|Notlar|
|-------------------|-------------------------|-----------|
|İlerleme çubuğu (belirsiz)|5 saniyelik beklenen süre >.<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.|Animasyonu **metne katıştırma.**|
|Anlar (animasyonlu yatay noktalar)|Sunucuya gidiş dönüş.<br /><br /> Üst kapsayıcının üst kapsayıcısının üzerinde neredeyse bağlam noktası yerleştirildi.|Tüm kapsayıcının üst öğesi **değilse kullanmayın.**|
|Değer değiştirici (ilerleme halkası)|Bağlamsal Kullanıcı arabirimi ile ilişkili işlem veya boşluk nerede bir noktadır.<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.||
|Üstündeki|Bağlamsal Kullanıcı arabirimiyle ilişkili mesajlaşma. Bkz. [Esnek](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).|Birden çok işlem belirtmeniz gerektiğinde birden çok **çocuk kullanmayın.** Bunun yerine yığılmış ilerleme çubukları kullanın.|
|Çıktı Penceresi|Geçici bildirim: Kullanıcı, tamamlandıktan sonra ayrıntılarını **Gözden** geçirmek istediği uygulama düzeyi işlemidir.|Oturumlar arasında kalıcı olması gereken bilgiler **için kullanmayın.**|
|Günlük dosyası|Tamamlanma sonrasında ayrıntıları **kaydetmek** önemli olduğunda, durumlarda geçici bildirimle eşleştirilmiş.||
|Durum çubuğu|Geçici bildirim: uygulama düzeyindeki işlem, kullanıcının tamamlanmasının ardından ayrıntılarına **ihtiyaç duymayacak** .<br /><br /> Gömülü ilerleme çubuğunu içerir.<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.||

### <a name="progress-indicator-types"></a>İlerleme göstergesi türleri

#### <a name="progress-bars"></a>İlerleme çubukları

##### <a name="indeterminate"></a>'Dır
 ![Belirsiz ilerleme çubuğu](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Belirsiz ilerleme çubuğu**

 "Belirsiz" bir işlemin veya işlemin genel ilerleme durumunun belirlenemediği anlamına gelir. Sınırsız miktarda zaman gerektiren veya bilinmeyen sayıda nesneye erişen işlemler için belirsiz ilerleme çubukları kullanın. Gerçekleşenleri eşlik etmek için bir metinsel açıklama kullanın. Zaman tabanlı işlemlere sınırlara izin vermek için zaman aşımlarını kullanın. Belirsiz ilerleme çubukları, ilerleme durumunu göstermek için animasyonları kullanır, ancak başka bilgi sağlamaz. Yalnızca olası doğruluğun olmamasından bağımsız olarak belirsiz ilerleme çubuğu seçmeyin.

##### <a name="determinate"></a>Kararlı
 ![İlerleme çubuğunu kesin](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **İlerleme çubuğunu kesin**

 "Determinan" bir işlemin veya işlemin sınırlı bir süre gerektirdiği, bu sürenin doğru tahmin edilemez olması anlamına gelir. Tamamlamayı açıkça belirtin. İşlem tamamlanana kadar bir ilerleme çubuğunun yüzde 100 ' a gitmesini sağlayın. İlerleme çubuğu animasyonunu, 0 ' dan %100 ' a kadar sağa doğru kaydırır.

 İşlem sırasında ilerleme göstergesini hiçbir şekilde geriye taşıyın. İşlem başladığında ve sona erdiğinde %100 ' a ulaştığında çubuğun ileri artmasıyla ' i taşıması gerekir. İlerleme çubuğunun noktası, kullanıcıya kaç adımın dahil olduğu fark etmeksizin tüm işlemin ne kadar süreceğine ilişkin bir fikir vermektir.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Eşzamanlı raporlama (yığılmış ilerleme çubukları)
 Bir işlem uzun bir süre zaman alıyorsa, bir işlem için genel ilerlemeyi ve geçerli adımın ilerleme durumunu gösteren iki ilerleme çubuğu kullanılabilir. Örneğin, bir kurulum programı birçok dosyayı kopyalayacağından, bir ikinci işlemin tamamının ne kadar sürdüğünü göstermek için tek bir ilerleme çubuğu kullanılabilir; ikincisi geçerli dosyanın veya dizinin ne kadarının kopyalanacağını belirtebilir. Yığılmış ilerleme çubukları kullanarak beşten fazla eşzamanlı işlem veya işlemden daha fazla rapor vermeyin. Raporlanacak en fazla beş eşzamanlı işlem veya işlem varsa, bir Iptal düğmesi ile kalıcı iletişim kutusunu kullanın ve ilerleme ayrıntılarını Çıkış Penceresi bildirin.

##### <a name="textual-descriptions"></a>Metinsel açıklamaları
 Oluşan ve tahmini tamamlanma süresi ile birlikte bir metinsel açıklama kullanın. Bir işlemin ne kadar süreceğine ilişkin saptanıyorsa, geri bildirimde bulunmak için daha iyi bir seçenek, ilerleme çubuğu yerine animasyon eklenmiş bir simge olabilir.

 Visual Studio, durum çubuğunda Visual Studio tümleştirilmiş herhangi bir ürün tarafından kullanılabilen standart bir ilerleme çubuğu sağlar. İlerleme çubuğu hareketlendirilirken neyin gerçekleşdiklerin metinsel açıklamaları için durum çubuğu metni güncelleştirilebilen olabilir.

#### <a name="other-progress-indicators"></a>Diğer ilerleme göstergeleri

##### <a name="ants-animated-horizontal-dots"></a>Anlar (animasyonlu yatay noktalar)
 ![İlerleme durumu](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Dönüşümlü," animasyonlu yatay noktalar, belirsiz bir gidiş dönüş sunucusu işlemi için görsel bir başvuru sağlar.

##### <a name="spinner-progress-ring"></a>Değer değiştirici (ilerleme halkası)
 ![İlerleme değiştiricisi](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 Değer değiştirici ("ilerleme halkası" olarak da bilinir), öncelikli olarak bağlamsal Kullanıcı arabirimine göre kullanılan belirsiz bir ilerleme göstergesidir. Metinsel kategori üstbilgisi, mesajlaşma veya denetim gibi ilgili içeriğe yakın bir değer değiştirici görüntüleyin.

##### <a name="cursor-feedback"></a>İmleç geri bildirimi
 2-7 saniye arasında geçen işlemler için imleç geri bildirimi sağlayın. Genellikle, bu, işletim sistemi tarafından sunulan Bekleme imlecini kullanma anlamına gelir. Rehberlik için bkz. MSDN makalesi [imleçler. Wait özelliği](/dotnet/api/system.windows.input.cursors.wait).

#### <a name="progress-indicator-locations"></a>İlerleme göstergesi konumları

##### <a name="status-bar"></a>Durum çubuğu
 Durum çubuğu, uygulamanıza, kullanıcının işini kesintiye uğramadan iletileri ve yararlı bilgileri göstermek için bir yer sağlar. Genellikle pencerenin en altında görüntülenen ilerleme durumu, ilerleme çubuğu göstergesi ile birlikte ilerleme ölçüsü hakkında bir ileti içeren bir araç ipucu bölmesi olacaktır.

 ![İlerleme çubuğu ile durum çubuğu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **İlerleme çubuğu ile durum çubuğu**

 ![Mesajlaşma ile durum çubuğu](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Metinsel açıklamasıyla durum çubuğu**

##### <a name="infobar"></a>Üstündeki
 Durum çubuğuna benzer şekilde, bilgi çubuğu, ayrıca ilerleme çubuğu veya değer değiştirici gibi belirsiz ilerleme göstergeleriyle eşleştirilemez bağlamsal bildirim ve mesajlaşma sağlar. Bilgi çubuğu ayrıntılı düzey ilerleme durumu sağlamamalı veya ilerleme durumunu belirleyici bir şekilde sağlamayabilir. Bkz. [Esnek](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![İlerleme çubuğu ve mesajlaşma ile bilgi çubuğu](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **İlerleme çubuğu ve metin açıklamasıyla bilgi çubuğu**

 ![Pencere içindeki bilgi çubuğu](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Satır içi
 Satır içi ilerleme göstergesi, herhangi bir ilerleme yükleyicisi türü tarafından temsil edilebilir. Genellikle ilerleme göstergesi mesajlaşma ile eşleştirilir, ancak bu bir gereklilik değildir.

 ![Satır içi ilerleme değiştiricisi](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Değer, metinsel açıklamasıyla birlikte**

 ![Satır içi yığılmış ilerleme çubukları](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Yığılmış ilerleme çubuklarını kesin**

 ![Satır içi ilerleme mesajlaşması](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Satır içi metin Sunucu Gezgini: yenileniyor...**

##### <a name="tool-windows"></a>Araç pencereleri
 Genel ilerleme durumu göstergesi, doğrudan araç çubuğunun altında konumlandırılmış bir belirsiz ilerleme çubuğu tarafından temsil edilir.

 ![Genel belirsiz ilerleme çubuğu](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Takım Gezgini genel belirsiz ilerleme çubuğu**

##### <a name="dialogs"></a>İletişim Kutuları
 İletişim kutuları, ilerleme yükleyicisi türlerinden herhangi birini içerebilir. İlerleme göstergeleri mesajlaşma ile eşleştirilebilir ve ayrıntılı ve alt süreçler temsil etmek için birden çok ilerleme göstergesi düzeyiyle birleştirilebilir.

 ![Birden çok ilerleme göstergesi türüyle iletişim kutusu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **eşzamanlı süreçler ve birden çok ilerleme göstergesi türü ile Visual Studio iletişim kutusu**

 ![İlerleme yükleyicisi ve mesajlaşma ile iletişim kutusu](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **ilerleme yükleyicisi ve mesajlaşma satır içi komutlama içeren Visual Studio iletişim kutusu**

##### <a name="document-well"></a>Belge kutusu
 Belge kutusu, denetimlerle birlikte birden çok ilerleme yükleyici türü görüntüleyebilir.

 ![Belge kutusu 'nda ilerleme mesajlaşması](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Araç çubuğunun altındaki belirsiz ilerleme çubuğu**

##### <a name="output-window"></a>Çıktı Penceresi
 Çıkış penceresi, işlem ilerlemesini ve sürekli ilerleme durumunu satır içi metinsel mesajlaşma yoluyla işlemeye uygundur. Durum çubuğunu, çıkış penceresi ilerleme durumu raporlamasıyla birlikte kullanmanız gerekir.

 ![Çıkış Penceresi ilerleme durumu iletisi](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Devam eden işlem durumu ve ileti bekleme ile Çıkış Penceresi**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Çocuk

### <a name="overview"></a>Genel Bakış
 Çocuk, kullanıcıya dikkat çekici bir gösterge ve paylaşılan bilgi çubuğu denetiminin kullanılması, görsel görünüm ve etkileşime göre tutarlılık sağlar.

 ![Bilgi Çubuğu](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Visual Studio'de bilgi Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Bilgi çubuğu için uygun kullanımlar

- Kullanıcıya geçerli bağlamla ilgili engelleyici olmayan ama önemli bir ileti vermek için

- Kullanıcı arabiriminin belirli bir durumda veya geçmişte hata ayıklama gibi etkileşim etkileri taşıyan bir koşulda olduğunu belirtmek için

- Kullanıcıya sistemin, örneğin bir uzantının performans sorunlarına neden olduğu sorunlar algıladı bildirimi yapmak için

- Kullanıcıya, örneğin düzenleyici bir dosyanın karışık sekmeler ve boşluklar olduğunu algılayan kolayca eylemde bulunacak bir yol sağlamak için

##### <a name="do"></a>Şunları yap:

- Bilgi çubuğu ileti metnini kısa ve noktasına kadar bırakın.

- Metni bağlantılarda ve düğmelerde kısa ve öz şekilde tutma.

- Kullanıcılara, yalnızca gerekli eylemleri gösteren "eylem" seçeneklerinin minimum düzeyde olduğundan emin olur.

##### <a name="dont"></a>Yapma:

- Bir araç çubuğuna yerleştiril olmalı standart komutlar sunmak için bir bilgi çubuğu kullanın.

- Kalıcı iletişim kutusunun yerine bir bilgi çubuğu kullanın.

- Bir pencerenin dışında kayan ileti oluşturun.

- Aynı pencere içindeki çeşitli konumlarda birden çok bilgi çubuğu kullanın.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Aynı anda birden çok bilgi çubuğu gösterebilir mi?
 Evet, aynı anda birden çok bilgi çubuğu gösterebilirsiniz. Bunlar ilk gelen, ilk kez sunulan sırada, üstte ilk bilgi çubuğu ve aşağıda gösterilen ek bilgi çubuğu ile birlikte görüntülenir.

 Kullanıcı bir kerede en fazla üç bilgi çubuğu görebilir ve daha fazla bilgi çubuğu varsa bilgi çubuğu bölgesi kaydırılabilir hale gelecektir.

### <a name="creating-an-infobar"></a>Bilgi çubuğu oluşturma
 Bilgi çubuğu soldan sağa dört bölüm içerir:

- **Simge:** Burası, bilgi çubuğu için görüntülemek istediğiniz herhangi bir simgeyi (uyarı simgesi gibi) eklemek istediğiniz yerdir.

- **Metin:** Gerekirse, kullanıcının içinde olduğu senaryoyu/durumu açıklamak için metin ve metin içindeki bağlantıları ekebilirsiniz. Metni kısa tutmayı unutmayın.

- **Eylemler:** Bu bölüm, kullanıcının bilgi çubuğuna ek olarak gerçekleştirebilirsiniz eylemleri için bağlantılar ve düğmeler içermesi gerekir.

- **Kapat düğmesi:** Sağ son bölümde bir kapat düğmesi olabilir.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Yönetilen kodda standart bilgi çubuğu oluşturma
 InfoBarModel sınıfı, bir bilgi çubuğu için veri kaynağı oluşturmak için kullanılabilir. Şu dört oluşturucudan birini kullanın:

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

 Burada köprü, eylem düğmesi ve simge içeren bir infoBarModel örneği ve bir metin oluşturabilirsiniz.

 ![Köprü içeren bilgi çubuğu](../../extensibility/ux-guidelines/media/0904-02_infobarhyperlink.png "0904-02_InfobarHyperlink")

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

#### <a name="creating-a-standard-infobar-in-native-code"></a>Yerel kodda standart bilgi çubuğu oluşturma
 Yerel koddan bilgi çubuğu sağlamak için IVsInfoBar arabirimini uygulama.

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
 InfoBarModel veya IVsInfoBar uygulaması, kullanıcı arabiriminde gösterilmek için bir UIElement'e çevrilen veri modelleridir. SVsInfoBarUIFactory/IVsInfoBarUIFactory hizmetiyle bir UIElement alınabilirsiniz.

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
 Bilgi çubuğu aşağıdaki konumlardan bir veya daha fazlasinde gösterebilirsiniz:

- Araç pencereleri

- Belge sekmesinde

> [!IMPORTANT]
> Genel bağlam hakkında ileti vermek için bir bilgi çubuğu konumlandırmak mümkündür. Bu, araç çubukları ve belge iyi durumda görünür. Bu, IDE'nin "atlama ve atlama" sorunlarına neden olduğu ve kesinlikle gerekli ve uygun olmadığı sürece kaçınılması gerektiği için önerilmez.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>ToolWindowPane'a bilgi çubuğu yerleştirme
 ToolWindowPane.AddInfoBar(IVsInfoBar) yöntemi, bir araç penceresine bilgi çubuğu eklemek için kullanılabilir. Bu API bir IVsInfoBar (InfoBarModel varsayılan uygulamadır) veya IVsUIElement ekleyebilir.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Belgeye veya ToolWindowPane olmayan bir bilgi çubuğu yerleştirme
 Herhangi bir IVsWindowFrame'e bilgi çubuğu eklemek için VSFPROPID_InfoBarHost özelliğini kullanarak çerçeve için IVsInfoBarHost'u alın ve ardından bilgi çubuğu UIElement'i ekleyin.

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
 Ana pencereye bir bilgi çubuğu eklemek için IVsShell hizmetinin VSSPROPID_MainWindowInfoBarHost'sını kullanarak ana pencerenin IVsInfoBarHost'ını edinin ve ardından bilgi çubuğu UIElement'i ekleyin.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Kullanıcının bilgi çubuğumda ne zaman eylemde olduğunu biliyor musunuz?
 Evet, her olay eylemlerini bilgi çubuğu yazarına geri döneceğiz. Ardından bilgi çubuğu yazarı, bilgi çubuğuna kullanıcı seçimine göre IDE'de eyleme geçilir. Kapat düğmesine tıkılan konaktan bilgi çubuğu otomatik olarak kaldırılır, ancak kapatma sonrasında diğer bilgi çubuklarını kaldırılması gerekirse ek çalışma gerekir. Telemetri ayrıca her bilgi çubuğu tarafından bağımsız olarak günlüğe kaydedilir.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>ToolWindowPane'da bilgi çubuğu olaylarını alma
 ToolWindowPane'da bilgi çubuğu için iki olay vardır. ToolWindowPane'daki bir bilgi çubuğu kapatılan InfoBarClosed olayı ortaya çıkar. InfoBarActionItemClicked olayı, bilgi çubuğu içindeki bir köprü veya düğmeye tıkıldığında ortaya çıkar.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Bilgi çubuğu olaylarını doğrudan UIElement'den alma
 IVsInfoBarUIElement.Advise, doğrudan bir bilgi çubuğu uiElement öğesinden olaylara abone olmak için kullanılabilir. IVsInfoBarUIEvents'in uygulanması, yazarın yakın ve tıklama olaylarını almalarına olanak sağlar.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> Hata doğrulama
 Kullanıcı, gerekli bir alanın atlanması veya verilerin yanlış biçimde girilir olması gibi kabul edilebilir olmayan bilgileri girdiği zaman, bir engelleme açılır pencere hatası iletişim kutusu kullanmak yerine denetimin yakınında denetim doğrulamasını veya geri bildirimi kullanmak daha iyi olur.

### <a name="field-validation"></a>Alan doğrulama
 Form ve alan doğrulaması üç bileşenden oluşur: denetim, simge ve araç ipucu. Bunu çeşitli denetim türleri kullanabilir ancak örnek olarak bir metin kutusu kullanılır.

 ![Alan doğrulama &#40;boş&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Alan gerekli ise, filigran metni belirterek olmalı ve alan arka planı açık sarı (VSColor: ) ve ön plan gri **\<Required>** `Environment.ControlEditRequiredBackground` (VSColor: ) `Environment.ControlEditRequiredHintText` olmalı:

 !["Gerekli" etiketiyle alan doğrulaması](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Program, odak başka bir denetime  taşındığında veya kullanıcı bir [Tamam] işleme düğmesine tıkladığında veya kullanıcı belgeyi veya formu kaydederken denetimin geçersiz içerik durumuna girdiğini belirler.

 Geçersiz içerik durumu belirlenirse denetimin içinde veya yanında bir simge görünür. Simgenin veya denetimin üzerine gelindiğinde hatayı açıklayan bir araç ipucu görüntü gerekir. Buna ek olarak, geçersiz durumu oluşturmakta olan denetimin etrafında 1 piksel kenarlık görünerek.

 ![Alan doğrulama düzeni belirtimleri](../../extensibility/ux-guidelines/media/0905-03_layoutspecs.png "0905-03_LayoutSpecs")

 **Alan doğrulaması için düzen belirtimleri**

#### <a name="acceptable-variations-for-icon-location"></a>Simge konumu için kabul edilebilir çeşitlemeler
 Kullanıcıların doğrulama hataları hakkında bilgi sahibi olması gereken sayısız benzersiz durum vardır. Kullanıcı arabiriminin denetim türünü ve yapılandırmasını göz önünde bulundurarak, durumunuz için uygun simge yerleşimini seçin.

 ![Simge konumu için kabul edilebilir konumlar](../../extensibility/ux-guidelines/media/0905-04_iconlocation.png "0905-04_IconLocation")

 **Alan doğrulama simgesi konumları için kabul edilebilir çeşitlemeler**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Sunucu veya ağ bağlantısına gidiş dönüş gerektiren doğrulama
 Bazı durumlarda, içeriği doğrulamak için sunucuya gidiş dönüş gereklidir ve kullanıcının ilerleme durumu, doğrulanmış ve hata durumlarını göstermek önemlidir. Aşağıdaki şekilde bu durum ve önerilen kullanıcı arabirimi örneği gösterilmiştir.

 ![Sunucuya gidiş dönüş içeren doğrulama](../../extensibility/ux-guidelines/media/0905-05_roundtrip.png "0905-05_RoundTrip")

 **Sunucuya gidiş dönüş içeren doğrulama**

 Denetimin sağ tarafından "Doğrulanıyor..." ifadesinin uygun olması için yeterli kullanılabilir alan sağlanmalıdır ve "Yeniden dene" metni.

#### <a name="in-place-warning-text"></a>Yerinde uyarı metni
 Hata iletisini denetime yakın bir hata durumuna koymak için uygun alan olduğunda, bunun tek başına araç ipucu kullanımına tercih edilir.

 ![Şu&#45;uyarısı](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Yerinde uyarı metni**

#### <a name="watermarks"></a>Filigranlar
 Bazen denetimin veya pencerenin tamamı hata durumuna neden olabilir. Bu durumda, hatayı belirtmek için filigran kullanın.

 ![Filigran](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Filigran alanı doğrulaması**
