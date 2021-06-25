---
title: Visual Studio için bildirimler ve Ilerleme durumu | Microsoft Docs
description: Kullanıcıları, yazılım geliştirme görevleriyle ilgili olarak Visual Studio 'da neler olduğunu bilgilendirmek için çeşitli yollar hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 994a315d04b06d1998a8c8e0c4291b6a4c54cb61
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902247"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Visual Studio İçin Bildirimler ve İlerleme Durumu
## <a name="notification-systems"></a><a name="BKMK_NotificationSystems"></a> Bildirim sistemleri

### <a name="overview"></a>Genel Bakış
 Kullanıcıya, yazılım geliştirme görevleriyle ilgili olarak Visual Studio 'da neler olduğunu bildirmek için birkaç yol vardır.

 Herhangi bir tür bildirim uygularken:

- **Bildirimlerin sayısını en düşük etkin sayı olarak tutun** . Bildirim iletileri çoğu Visual Studio kullanıcısı veya belirli bir özellik/özellik alanının kullanıcıları için geçerlidir. Bildirimlerin aşırı kullanımı, kullanıcıyı daha fazla izleyebilir veya sistem tarafından algılanan kullanımı hafifletmek için kullanılabilir.

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
|[Visual Studio bildirimleri penceresi](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_VSNotificationsToolWindow)|Bildirimler penceresi genel olarak genişletilebilir değildir. Ancak, Visual Studio hakkında kritik sorunlar, Visual Studio veya paketlere yönelik güncelleştirmelerin bilgilendirme bildirimleri dahil olmak üzere Visual Studio hakkında bir dizi ileti iletmek için kullanılır.|Diğer bildirim türleri için kullanmayın.|
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
 Kullanıcıların durum çubuğu metnini nasıl fark ettiğini ve Windows platformuyla ilgili belirli bir deneyimle karşılaşması olasılığını aşın. Visual Studio müşteri tabanı her iki alanda da karşılaşmak üzere eğilimi gösterir, ancak bilgili Windows kullanıcıları durum çubuğundaki değişiklikleri kaçırmayabilir. Bu nedenle, durum çubuğu en iyi bilgi amaçlı olarak veya başka bir yerde sunulan bilgiler için bir gereksiz ipucu olarak kullanılır. Kullanıcının hemen çözümlenmesi gereken her türlü kritik bilgi, bir iletişim kutusunda veya bildirimler araç penceresinde sağlanmalıdır.

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
 İlerleme göstergeleri, birkaç saniyeden daha fazla geçen bir işlem sırasında Kullanıcı geri bildirimi vermek için önemlidir. İlerleme göstergeleri, yerinde (sürmekte olan eylemin başlatma noktasının yakınında), katıştırılmış durum çubuğunda, kalıcı bir iletişim kutusunda veya Visual Studio durum çubuğunda gösterilir. Kullanım ve uygulamayla ilgili olarak [devam eden göstergeler](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_ProgressIndicators) kılavuzunu izleyin.

#### <a name="visual-studio-notifications-window"></a><a name="BKMK_VSNotificationsToolWindow"></a> Visual Studio bildirimleri penceresi
 Visual Studio bildirimleri penceresi, geliştiricilere lisanslama, ortam (Visual Studio), Uzantılar ve güncelleştirmeler hakkında bilgilendirir. Kullanıcılar bireysel bildirimleri kapatabilir veya belirli bildirim türlerini yok saymayı seçebilirler. Yoksayılan bildirimlerin listesi bir **araçlar > seçenekleri** sayfasında yönetilir.

 Bildirimler penceresi şu anda genişletilebilir değil.

 ![Visual Studio bildirimleri penceresi](../../extensibility/ux-guidelines/media/0901-06_vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio bildirimleri araç penceresi**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Hata listesi
 Hata listesi içindeki bir bildirim, derleme ve derleme işlemleri sırasında oluşan hataları ve uyarıları gösterir ve kullanıcının kodda belirli bir kod hatasına gitmesini sağlar.

 ![Hata listesi](../../extensibility/ux-guidelines/media/0901-08_errorlist.png "0901-08_ErrorList")

 **Visual Studio 'da hata listesi**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Gömülü durum çubukları
 IDE durum çubuğu dinamik olduğu için, istemci bölgesi bağlamı etkin belge penceresine ayarlanmış ve kullanıcının bağlamında ve/veya sistem yanıtlarında bilgi güncelleştiren bir sürekli bilgi görüntülenmesini veya uzun süreli zaman uyumsuz işlemlere durum vermenizi zorlaştırıyor. Örneğin, IDE durum çubuğu, birden çok çalıştırma ve/veya hemen eyleme dönüştürülebilir öğe seçimi için test çalıştırması sonuçlarının bildirimleri için uygun değildir. Bu tür durum bilgilerinin, kullanıcının seçim yaptığı veya bir işlemi başlattığı belge veya araç penceresi bağlamında tutulması önemlidir.

 ![Gömülü durum çubuğu](../../extensibility/ux-guidelines/media/0901-09_embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Visual Studio 'da katıştırılmış durum çubuğu**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Windows tepsi bildirimleri
 Windows bildirim alanı, Windows görev çubuğundaki sistem saatinin yanında yer alır. Birçok yardımcı program ve yazılım bileşeni, kullanıcının ekran çözünürlüğünü değiştirme veya yazılım güncelleştirmelerini alma gibi sistem genelinde görevlere yönelik bağlam menüsünü elde edebilmesi için bu alana simgeler sağlar.

 Ortam düzeyinde bildirimler, Windows bildirim alanında değil, Visual Studio Bildirim Hub 'ında kullanıma alınmalıdır.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Bildirim kabarcıkları
 Bildirim kabarcıkları bir düzenleyici/tasarımcı içinde veya Windows bildirim alanının parçası olarak görünebilir. Kullanıcı bu kabarcıkları daha sonra çözebilecekleri sorunlar olarak beyin, bu da kritik olmayan bildirimlere yönelik bir avantajdır. Kabarcıklar, kullanıcının hemen çözmeleri gereken kritik bilgiler için uygun değildir. Visual Studio 'da bildirim kabarcıkları kullanıyorsanız, [bildirim kabarcıkları Için Windows Masaüstü kılavuzunu](/windows/desktop/uxguide/mess-notif)izleyin.

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
|Çıktı Penceresi|Geçici bildirim: Kullanıcının tamamlandıktan sonra ayrıntılarını gözden geçirmek **istemesi gereken** uygulama düzeyinde işlem.|**OTURUMLAR ARASıNDA** kalıcı olması gereken bilgiler için KULLANMAYIN.|
|Günlük dosyası|Tamamlandıktan sonra ayrıntıları kaydetmenin önemli olduğu durumlarda, geçişsiz **bildirimle** eşleştirildi.||
|Durum çubuğu|Geçici bildirim: Uygulama düzeyinde işlem tamamlandıktan sonra **kullanıcının ayrıntılarına** ihtiyacı olmaz.<br /><br /> Katıştırılmış ilerleme çubuğu içerir.<br /><br /> İşlem ayrıntılarının metinsel açıklamasını içerebilir.||

### <a name="progress-indicator-types"></a>İlerleme göstergesi türleri

#### <a name="progress-bars"></a>İlerleme çubukları

##### <a name="indeterminate"></a>Belirsiz
 ![Belirsiz ilerleme çubuğu](../../extensibility/ux-guidelines/media/0901-04_indeterminate.png "0901-04_Indeterminate")

 **Belirsiz ilerleme çubuğu**

 "Belirsiz", bir işlem veya sürecin genel ilerleme durumu belirlenemeyen anlamına gelir. Sınırsız süre gerektiren veya bilinmeyen sayıda nesneye erişen işlemler için belirsiz ilerleme çubukları kullanın. Neler olduğunu eşlik etmek için metinsel bir açıklama kullanın. Zaman tabanlı işlemlere sınır vermek için zaman aşımı kullanın. Belirsiz ilerleme çubukları, ilerlemenin devam ediyor olduğunu göstermek için animasyonlar kullanır ancak başka bilgi sağlamaz. Yalnızca olası doğruluk eksikliğine bağlı olarak belirsiz bir ilerleme çubuğu seçmeyin.

##### <a name="determinate"></a>Belirli
 ![İlerleme çubuğunu belirleme](../../extensibility/ux-guidelines/media/0901-05_determinate.png "0901-05_Determinate")

 **İlerleme çubuğunu belirleme**

 "Belirlenebilir", bir işlem veya işlem için sınırlayıcı bir süre (bu süre doğru şekilde tahmin edilese bile) gerektirdiği anlamına gelir. Tamamlanmayı açıkça belirt. İşlem tamamlanmadıkça ilerleme çubuğunun yüzde 100'e ine izin verme. İlerleme çubuğu animasyonu 0'dan %100'e doğru sola taşınır.

 bir işlem sırasında ilerleme göstergesini asla geri taşımayın. Çubuk, işlem başladığında kararlı bir şekilde ilerlemeli ve sona erdiğinde %100'e ulaşmaktadır. İlerleme çubuğunun noktası, kaç adımdan bağımsız olarak kullanıcıya tüm işlemi ne kadar sürece dahil olduğu konusunda fikir vermektir.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Eşzamanlı raporlama (yığılmış ilerleme çubukları)
 Bir işlem uzun sürecekse (belki birkaç dakika) iki ilerleme çubukları kullanılabilir; bunlardan biri bir işlem için genel ilerlemeyi, diğeri ise geçerli adımın ilerleme durumu için. Örneğin, bir kurulum programı çok sayıda dosya kopyalüyorsa, bir ilerleme çubuğu tüm sürecin ne kadar sürece devam ederken bir saniyenin geçerli dosyanın veya dizinin kopyalanan yüzdesini belirterek belirtebilirsiniz. Yığılmış ilerleme çubukları kullanarak beşten fazla eş zamanlı işlem veya işlem bildirmeyin. Rapor edilecek beşten fazla eşzamanlı işleminiz veya işleminiz varsa, İptal düğmesiyle kalıcı bir iletişim kutusu kullanın ve ilerleme ayrıntılarını rapora Çıkış Penceresi.

##### <a name="textual-descriptions"></a>Metinsel açıklamalar
 Neler olduğunu ve tahmini tamamlanma süresine eşlik etmek için metinsel bir açıklama kullanın. Bir işlemi ne kadar süreyle tamamlaymayacaklarını belirlemek mümkün olmayacaksa, geri bildirim vermek için daha iyi bir seçenek ilerleme çubuğu yerine animasyonlu bir simge olabilir.

 Visual Studio, durum çubuğuna standart bir ilerleme çubuğu sağlar ve bu çubuk, uygulamayla tümleştirilmiş tüm ürünler Visual Studio. İlerleme çubuğu animasyonluyken neler olduğuyla ilgili metinsel açıklamalar için durum çubuğu metni güncelleştirilebilir.

#### <a name="other-progress-indicators"></a>Diğer ilerleme göstergeleri

##### <a name="ants-animated-horizontal-dots"></a>Ants (animasyonlu yatay noktalar)
 ![İlerleme durumu olan ants](../../extensibility/ux-guidelines/media/0903-01_ants.png "0903-01_Ants")

 "Ants", animasyonlu yatay noktalar, belirsiz bir gidiş dönüş sunucu işlemi için görsel bir başvuru sağlar.

##### <a name="spinner-progress-ring"></a>Spinner (ilerleme halkası)
 ![İlerleme durumu döndürücü](../../extensibility/ux-guidelines/media/0903-02_spinner.png "0903-02_Spinner")

 Döndürücü ("ilerleme halkası" olarak da bilinir), öncelikli olarak bağlamsal kullanıcı arabirimiyle ilgili olarak kullanılan belirsiz bir ilerleme göstergesidir. Metin kategorisi üst bilgisi, mesajlaşma veya denetim gibi ilgili içeriğine yakın bir şekilde bir döndürücü görüntüler.

##### <a name="cursor-feedback"></a>İmleç geri bildirimi
 2-7 saniye arasındaki işlemler için imleç geri bildirimini paylaşın. Bu genellikle işletim sistemi tarafından sağlanan bekleme imlecini kullanmak anlamına gelir. Rehberlik için, [Cursors.Wait Özelliği MSDN makalesine bakın.](/dotnet/api/system.windows.input.cursors.wait)

#### <a name="progress-indicator-locations"></a>İlerleme göstergesi konumları

##### <a name="status-bar"></a>Durum çubuğu
 Durum çubuğu, uygulamanıza kullanıcının çalışmalarını kesintiye uğratmadan kullanıcıya iletilerin ve yararlı bilgilerin görüntüldüğü bir yer sağlar. Genellikle bir pencerenin en altında görüntülenir; ilerleme durumu, ilerleme durumu çubuğu göstergesiyle birlikte ilerleme ölçüsü hakkında bir ileti içeren bir araç ipucu bölmesi olur.

 ![İlerleme çubuğuyla durum çubuğu](../../extensibility/ux-guidelines/media/0903-03_statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **İlerleme çubuğuyla durum çubuğu**

 ![Mesajlaşma ile durum çubuğu](../../extensibility/ux-guidelines/media/0903-04_statusbarmessage.png "0903-04_StatusBarMessage")

 **Metin açıklaması ile durum çubuğu**

##### <a name="infobar"></a>Bilgi Çubuğu
 Durum çubuğuna benzer şekilde, bilgi çubuğu bağlamsal bildirim ve mesajlaşma sağlar ve bu da ilerleme çubuğu veya döndürücü gibi belirsiz ilerleme göstergeleriyle eşleştirilmiş olabilir. Bilgi çubuğu ayrıntılı düzey ilerleme durumu veya belirleyici ilerleme göstergesi sağlamamalı. Bkz. [Bilgi Çubuğu.](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars)

 ![İlerleme çubuğu ve mesajlaşma ile bilgi çubuğu](../../extensibility/ux-guidelines/media/0903-05_infobar.png "0903-05_InfoBar")

 **İlerleme çubuğu ve metin açıklaması ile bilgi çubuğu**

 ![Bir pencerenin içindeki bilgi çubuğu](../../extensibility/ux-guidelines/media/0903-06_infobarinwindow.png "0903-06_InfoBarInWindow")

##### <a name="inline"></a>Satır içi
 Satır içi ilerleme göstergesi, ilerleme yükleyici türlerinden herhangi biri tarafından temsil olabilir. İlerleme göstergesi genellikle mesajlaşma ile eşleştirilmektedir ancak bu bir gereksinim değildir.

 ![Satır içi ilerleme durumu döndürücü](../../extensibility/ux-guidelines/media/0903-07_inlinespinner.png "0903-07_InlineSpinner")

 **Spinner, metin açıklamasıyla birlikte**

 ![Satır içi yığılmış ilerleme çubukları](../../extensibility/ux-guidelines/media/0903-08_inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Yığılmış ilerleme çubuklarını belirleme**

 ![Satır içi ilerleme durumu mesajlaşması](../../extensibility/ux-guidelines/media/0903-09_inlinetext.png "0903-09_InlineText")

 **Sunucu Gezgini satır içi metin: Yenileniyor...**

##### <a name="tool-windows"></a>Araç pencereleri
 Genel ilerleme göstergesi, doğrudan araç çubuğunun altına konumlanmıştır ve belirsiz bir ilerleme çubuğuyla temsil edilmektedir.

 ![Genel belirsiz ilerleme çubuğu](../../extensibility/ux-guidelines/media/0903-23_globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Takım Gezgini belirsiz ilerleme çubuğu**

##### <a name="dialogs"></a>İletişim Kutuları
 İletişim kutuları, ilerleme durumu yükleyici türlerinden herhangi birini içerebilir. İlerleme göstergeleri mesajlaşma ile eşleştirilmelerinin yanı sıra ayrıntılı ve alt işlemleri temsil eden birden çok ilerleme göstergesi düzeyiyle bir araya da olabilir.

 ![Birden çok ilerleme göstergesi türü içeren iletişim kutusu](../../extensibility/ux-guidelines/media/0903-11_dialog.png "0903-11_Dialog")

 **Visual Studio işlemler ve birden çok ilerleme göstergesi türü içeren iletişim kutusu**

 ![İlerleme durumu yükleyici ve mesajlaşma ile iletişim kutusu](../../extensibility/ux-guidelines/media/0903-12_dialog2.png "0903-12_Dialog2")

 **Visual Studio yükleyici ve mesajlaşma satır içi komutlarını kullanarak iletişim kutusu**

##### <a name="document-well"></a>Belge iyi
 Belge, denetimlerle birlikte birden çok ilerleme durumu yükleyici türü ekleyebilirsiniz.

 ![Belge içinde ilerleme durumu mesajlaşması](../../extensibility/ux-guidelines/media/0903-13_documentwell.png "0903-13_DocumentWell")

 **Araç çubuğunun altındaki belirsiz ilerleme çubuğu**

##### <a name="output-window"></a>Çıktı Penceresi
 Çıkış penceresi, satır içi metin mesajlaşması aracılığıyla sürecin ilerleme durumunu ve devam eden ilerleme durumunu işlemeye uygundur. Herhangi bir Çıkış penceresi ilerleme durumu raporlaması ile birlikte Durum çubuğunu kullanabilirsiniz.

 ![Çıkış Penceresi'de ilerleme Çıkış Penceresi](../../extensibility/ux-guidelines/media/0903-14_outputwindow.png "0903-14_OutputWindow")

 **Çıkış Penceresi işlem durumu ve bekleme mesajlaşması ile ilgili sorun**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Bilgi Çubuğu

### <a name="overview"></a>Genel Bakış
 Bilgi çubuğu, kullanıcıya dikkat noktasına yakın bir gösterge sağlar ve paylaşılan bilgi çubuğu denetiminin kullanılması, görsel görünümde ve etkileşimde tutarlılık sağlar.

 ![Bilgi Çubuğu](../../extensibility/ux-guidelines/media/0904-01_infobar.png "0904-01_Infobar")

 **Visual Studio'de bilgi Visual Studio**

#### <a name="appropriate-uses-for-an-infobar"></a>Bilgi çubuğu için uygun kullanımlar

- Kullanıcıya geçerli bağlamla ilgili engelleyici olmayan ancak önemli bir ileti vermek için

- Kullanıcı arabiriminin belirli bir durumda veya geçmişte hata ayıklama gibi etkileşim etkileri taşıyan bir koşulda olduğunu belirtmek için

- Kullanıcıya, bir uzantının performans sorunlarına neden olduğu zaman gibi sistem sorunları algıladı bildirimi yapmak için

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
 Evet, aynı anda birden çok bilgi çubuğu gösterebilirsiniz. Bunlar, ilk gelen ilk kez sunulan sırada, üstte ilk bilgi çubuğu ve aşağıda gösterilen ek bilgi çubuğu ile birlikte görüntülenir.

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

 Burada köprü, eylem düğmesi ve simge içeren bir infoBarModel örneği ve bir metin oluşturur.

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
 Ana pencereye bir bilgi çubuğu eklemek için, ana pencerenin IVsInfoBarHost VSSPROPID_MainWindowInfoBarHost ı almak için IVsShell hizmetinin VSSPROPID_MainWindowInfoBarHost'sını kullanın ve ardından buna bilgi çubuğu UIElement'i ekleyin.

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
 Bir kullanıcı, gerekli bir alanın atlanması veya verilerin yanlış biçimde girilir olması gibi kabul edilebilir olmayan bilgileri girdiği zaman, bir engelleme açılan hata iletişim kutusu kullanmak yerine denetimin yakınında denetim doğrulamasını veya geri bildirimi kullanmak daha iyi olur.

### <a name="field-validation"></a>Alan doğrulama
 Form ve alan doğrulaması üç bileşenden oluşur: denetim, simge ve araç ipucu. Bunu çeşitli denetim türleri kullanabilir ancak örnek olarak bir metin kutusu kullanılır.

 ![Alan doğrulama &#40;boş&#41;](../../extensibility/ux-guidelines/media/0905-01_fieldvalidation.png "0905-01_FieldValidation")

 Alan gerekli ise, filigran metni belirterek olmalı ve alan arka planı açık sarı (VSColor: ) ve ön plan gri **\<Required>** `Environment.ControlEditRequiredBackground` (VSColor: ) `Environment.ControlEditRequiredHintText` olmalı:

 !["Gerekli" etiketiyle alan doğrulaması](../../extensibility/ux-guidelines/media/0905-02_fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Program, odak başka bir denetime  taşındığında veya kullanıcı bir [Tamam] işleme düğmesine tıkladığında ya da kullanıcı belgeyi veya formu kaydederken denetimin geçersiz içerik durumuna girdiğini belirler.

 Geçersiz içerik durumu belirlenirse denetimin içinde veya hemen yanında bir simge görünür. Simgenin veya denetimin üzerine gelindiğinde hatayı açıklayan bir araç ipucu görüntü gerekir. Buna ek olarak, geçersiz durumu oluşturmakta olan denetimin etrafında 1 piksel kenarlık görünerek.

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

 Denetimin sağ tarafından sağlanan yeterli kullanılabilir alan, "Doğrulanıyor..." ve "Yeniden dene" metni.

#### <a name="in-place-warning-text"></a>Yerinde uyarı metni
 Hata iletisini denetime yakın bir hata durumuna koymak için uygun alan olduğunda, bunun tek başına araç ipucu kullanımına tercih edilir.

 ![Şu&#45;uyarısı](../../extensibility/ux-guidelines/media/0905-06_inplacewarning.png "0905-06_InPlaceWarning")

 **Yerinde uyarı metni**

#### <a name="watermarks"></a>Filigranlar
 Bazen denetimin veya pencerenin tamamı hata durumuna neden olabilir. Bu durumda, hatayı belirtmek için filigran kullanın.

 ![Filigran](../../extensibility/ux-guidelines/media/0905-07_watermark.png "0905-07_Watermark")

 **Filigran alanı doğrulaması**
