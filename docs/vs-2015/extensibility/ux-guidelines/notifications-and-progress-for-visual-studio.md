---
title: Bildirimler ve İlerleme Durumu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: f0ef65e9-0f1f-45f4-9f25-6e2398691168
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f17b875f0637883222a633cb1082ad24788d4c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825647"
---
# <a name="notifications-and-progress-for-visual-studio"></a>Visual Studio İçin Bildirimler ve İlerleme Durumu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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

 ![Kalıcı hata iletisi](../../extensibility/ux-guidelines/media/0901-01-modalerrormessage.png "0901-01_ModalErrorMessage")

 **Kalıcı bir hata iletisi iletişim kutusu, bir veritabanına geçersiz bir bağlantı dizesi kullanıcısını uyarır**

#### <a name="ide-status-bar"></a><a name="BKMK_IDEStatusBar"></a> IDE durum çubuğu
 Kullanıcıların durum çubuğu metnini nasıl fark ettiğini ve Windows platformuyla ilgili belirli bir deneyimle karşılaşması olasılığını aşın. Visual Studio müşteri tabanı her iki alanda da karşılaşmak üzere eğilimi gösterir, ancak bilgili Windows kullanıcıları durum çubuğundaki değişiklikleri kaçırmayabilir. Bu nedenle, durum çubuğu en iyi bilgi amaçlı olarak veya başka bir yerde sunulan bilgiler için bir gereksiz ipucu olarak kullanılır. Kullanıcının hemen çözümlenmesi gereken her türlü kritik bilgi, bir iletişim kutusunda veya bildirimler araç penceresinde sağlanmalıdır.

 Visual Studio durum çubuğu, çeşitli bilgi türlerinin görüntülenmesine izin vermek için tasarlanmıştır. Geri bildirim, tasarımcı, ilerleme çubuğu, animasyon ve istemci için bölgelere bölünmüştür.

 Geri bildirim bölgesi ve tasarımcı bölgesi her zaman görünür. İlerleme çubuğu ve animasyon bölgeleri her zaman dinamik ve Kullanıcı bağlamına dayalıdır. Tasarımcı bölgesinin, SMS mesajı için eşlik eden bir kaynaktan çekilen dizenin uzunluğuna göre belirlenen statik bir genişliği vardır. Bu, yerelleştirmenin bir kod değişikliğine gerek duymadan genişliği yeniden boyutlandırmasını sağlar. Ingilizce için bu dizenin genişliği kabaca 220 pikseldir. Tasarımcı bölgesi normal şekilde davranır ve geri bildirim bölgesi kalan alanı artışlarını devralarak olacaktır.

 Durum çubuğu ayrıca, IDE 'nin hata ayıklama modunda olduğu gibi çeşitli IDE durum değişikliklerine iletişim kurarak görsel ilgi ve işlevsel değer eklemek için de renklendirilmiştir.

 ![IDE durum çubuğu renk değişiklikleri](../../extensibility/ux-guidelines/media/0901-02-idestatusbar.png "0901-02_IDEStatusBar")

 **IDE durum çubuğu renkleri**

#### <a name="embedded-infobar"></a><a name="BKMK_EmbeddedInfobar"></a> Katıştırılmış bilgi çubuğu
 Bir bilgi çubuğu, bir belge penceresinin veya araç penceresinin en üstünde, bir durum veya koşulun kullanıcıya bilgi vermek için kullanılabilir. Ayrıca, kullanıcının kolayca işlem yapması için bir yol kullanabilmesi için komutlar sunabilir. Bilgi çubuğu standart bir kabuk denetimidir. Kendi verilerinizi oluşturmaktan kaçının. Bu, IDE 'deki diğer kişilerle tutarsız ve görünür olacak şekilde çalışır. Uygulama ayrıntıları ve kullanım [Kılavuzu için bkz](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars) ..

 ![Katıştırılmış bilgi çubuğu](../../extensibility/ux-guidelines/media/0901-03-embeddedinfobar.png "0901-03_EmbeddedInfobar")

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

 ![Visual Studio bildirimleri penceresi](../../extensibility/ux-guidelines/media/0901-06-vsnotificationswindow.png "0901-06_VSNotificationsWindow")

 **Visual Studio bildirimleri araç penceresi**

#### <a name="error-list"></a><a name="BKMK_ErrorList"></a> Hata listesi
 Hata listesi içindeki bir bildirim, derleme ve derleme işlemleri sırasında oluşan hataları ve uyarıları gösterir ve kullanıcının kodda belirli bir kod hatasına gitmesini sağlar.

 ![Hata listesi](../../extensibility/ux-guidelines/media/0901-08-errorlist.png "0901-08_ErrorList")

 **Visual Studio 'da hata listesi**

#### <a name="embedded-status-bars"></a><a name="BKMK_EmbeddedStatusBars"></a> Gömülü durum çubukları
 IDE durum çubuğu dinamik olduğu için, istemci bölgesi bağlamı etkin belge penceresine ayarlanmış ve kullanıcının bağlamında ve/veya sistem yanıtlarında bilgi güncelleştiren bir sürekli bilgi görüntülenmesini veya uzun süreli zaman uyumsuz işlemlere durum vermenizi zorlaştırıyor. Örneğin, IDE durum çubuğu, birden çok çalıştırma ve/veya hemen eyleme dönüştürülebilir öğe seçimi için test çalıştırması sonuçlarının bildirimleri için uygun değildir. Bu tür durum bilgilerinin, kullanıcının seçim yaptığı veya bir işlemi başlattığı belge veya araç penceresi bağlamında tutulması önemlidir.

 ![Gömülü durum çubuğu](../../extensibility/ux-guidelines/media/0901-09-embeddedstatusbar.png "0901-09_EmbeddedStatusBar")

 **Visual Studio 'da katıştırılmış durum çubuğu**

#### <a name="windows-tray-notifications"></a><a name="BKMK_WindowsTray"></a> Windows tepsi bildirimleri
 Windows bildirim alanı, Windows görev çubuğundaki sistem saatinin yanında yer alır. Birçok yardımcı program ve yazılım bileşeni, kullanıcının ekran çözünürlüğünü değiştirme veya yazılım güncelleştirmelerini alma gibi sistem genelinde görevlere yönelik bağlam menüsünü elde edebilmesi için bu alana simgeler sağlar.

 Ortam düzeyinde bildirimler, Windows bildirim alanında değil, Visual Studio Bildirim Hub 'ında kullanıma alınmalıdır.

#### <a name="notification-bubbles"></a><a name="BKMK_NotificationBubbles"></a> Bildirim kabarcıkları
 Bildirim kabarcıkları bir düzenleyici/tasarımcı içinde veya Windows bildirim alanının parçası olarak görünebilir. Kullanıcı bu kabarcıkları daha sonra çözebilecekleri sorunlar olarak beyin, bu da kritik olmayan bildirimlere yönelik bir avantajdır. Kabarcıklar, kullanıcının hemen çözmeleri gereken kritik bilgiler için uygun değildir. Visual Studio 'da bildirim kabarcıkları kullanıyorsanız, [bildirim kabarcıkları Için Windows Masaüstü kılavuzunu](https://msdn.microsoft.com/library/windows/desktop/dn742472\(v=vs.85\).aspx)izleyin.

 ![Bildirim balonu](../../extensibility/ux-guidelines/media/0901-07-notificationbubbles.png "0901-07_NotificationBubbles")

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
 ![Belirsiz ilerleme çubuğu](../../extensibility/ux-guidelines/media/0901-04-indeterminate.png "0901-04_Indeterminate")

 **Belirsiz ilerleme çubuğu**

 "Belirsiz" bir işlemin veya işlemin genel ilerleme durumunun belirlenemediği anlamına gelir. Sınırsız miktarda zaman gerektiren veya bilinmeyen sayıda nesneye erişen işlemler için belirsiz ilerleme çubukları kullanın. Gerçekleşenleri eşlik etmek için bir metinsel açıklama kullanın. Zaman tabanlı işlemlere sınırlara izin vermek için zaman aşımlarını kullanın. Belirsiz ilerleme çubukları, ilerleme durumunu göstermek için animasyonları kullanır, ancak başka bilgi sağlamaz. Yalnızca olası doğruluğun olmamasından bağımsız olarak belirsiz ilerleme çubuğu seçmeyin.

##### <a name="determinate"></a>Kararlı
 ![İlerleme çubuğunu kesin](../../extensibility/ux-guidelines/media/0901-05-determinate.png "0901-05_Determinate")

 **İlerleme çubuğunu kesin**

 "Determinan" bir işlemin veya işlemin sınırlı bir süre gerektirdiği, bu sürenin doğru tahmin edilemez olması anlamına gelir. Tamamlamayı açıkça belirtin. İşlem tamamlanana kadar bir ilerleme çubuğunun yüzde 100 ' a gitmesini sağlayın. İlerleme çubuğu animasyonunu, 0 ' dan %100 ' a kadar sağa doğru kaydırır.

 İşlem sırasında ilerleme göstergesini hiçbir şekilde geriye taşıyın. İşlem başladığında ve sona erdiğinde %100 ' a ulaştığında çubuğun ileri artmasıyla ' i taşıması gerekir. İlerleme çubuğunun noktası, kullanıcıya kaç adımın dahil olduğu fark etmeksizin tüm işlemin ne kadar süreceğine ilişkin bir fikir vermektir.

##### <a name="concurrent-reporting-stacked-progress-bars"></a>Eşzamanlı raporlama (yığılmış ilerleme çubukları)
 Bir işlem uzun zaman alıyorsa, belki birkaç dakika – bir işlemin genel ilerleme durumunu ve geçerli adımın ilerleme durumunu gösteren iki ilerleme çubuğu kullanılabilir. Örneğin, bir kurulum programı birçok dosyayı kopyalayacağından, bir ikinci işlemin tamamının ne kadar sürdüğünü göstermek için tek bir ilerleme çubuğu kullanılabilir; ikincisi geçerli dosyanın veya dizinin ne kadarının kopyalanacağını belirtebilir. Yığılmış ilerleme çubukları kullanarak beşten fazla eşzamanlı işlem veya işlemden daha fazla rapor vermeyin. Raporlanacak en fazla beş eşzamanlı işlem veya işlem varsa, bir Iptal düğmesi ile kalıcı iletişim kutusunu kullanın ve ilerleme ayrıntılarını Çıkış Penceresi bildirin.

##### <a name="textual-descriptions"></a>Metinsel açıklamaları
 Oluşan ve tahmini tamamlanma süresi ile birlikte bir metinsel açıklama kullanın. Bir işlemin ne kadar süreceğine ilişkin saptanıyorsa, geri bildirimde bulunmak için daha iyi bir seçenek, ilerleme çubuğu yerine animasyon eklenmiş bir simge olabilir.

 Visual Studio, Visual Studio ile tümleştirilmiş herhangi bir ürün tarafından kullanılabilen, durum çubuğunda standart bir ilerleme çubuğu sağlar. İlerleme çubuğu hareketlendirilirken neyin gerçekleşdiklerin metinsel açıklamaları için durum çubuğu metni güncelleştirilebilen olabilir.

#### <a name="other-progress-indicators"></a>Diğer ilerleme göstergeleri

##### <a name="ants-animated-horizontal-dots"></a>Anlar (animasyonlu yatay noktalar)
 ![İlerleme durumu](../../extensibility/ux-guidelines/media/0903-01-ants.png "0903-01_Ants")

 "Dönüşümlü," animasyonlu yatay noktalar, belirsiz bir gidiş dönüş sunucusu işlemi için görsel bir başvuru sağlar.

##### <a name="spinner-progress-ring"></a>Değer değiştirici (ilerleme halkası)
 ![İlerleme değiştiricisi](../../extensibility/ux-guidelines/media/0903-02-spinner.png "0903-02_Spinner")

 Değer değiştirici ("ilerleme halkası" olarak da bilinir), öncelikli olarak bağlamsal Kullanıcı arabirimine göre kullanılan belirsiz bir ilerleme göstergesidir. Metinsel kategori üstbilgisi, mesajlaşma veya denetim gibi ilgili içeriğe yakın bir değer değiştirici görüntüleyin.

##### <a name="cursor-feedback"></a>İmleç geri bildirimi
 2-7 saniye arasında geçen işlemler için imleç geri bildirimi sağlayın. Genellikle, bu, işletim sistemi tarafından sunulan Bekleme imlecini kullanma anlamına gelir. Rehberlik için bkz. MSDN makalesi [imleçler. Wait özelliği](https://msdn.microsoft.com/library/system.windows.input.cursors.wait\(v=vs.110\).aspx).

#### <a name="progress-indicator-locations"></a>İlerleme göstergesi konumları

##### <a name="status-bar"></a>Durum çubuğu
 Durum çubuğu, uygulamanıza, kullanıcının işini kesintiye uğramadan iletileri ve yararlı bilgileri göstermek için bir yer sağlar. Genellikle pencerenin en altında görüntülenen ilerleme durumu, ilerleme çubuğu göstergesi ile birlikte ilerleme ölçüsü hakkında bir ileti içeren bir araç ipucu bölmesi olacaktır.

 ![İlerleme çubuğu ile durum çubuğu](../../extensibility/ux-guidelines/media/0903-03-statusbarprogressbar.png "0903-03_StatusBarProgressBar")

 **İlerleme çubuğu ile durum çubuğu**

 ![Mesajlaşma ile durum çubuğu](../../extensibility/ux-guidelines/media/0903-04-statusbarmessage.png "0903-04_StatusBarMessage")

 **Metinsel açıklamasıyla durum çubuğu**

##### <a name="infobar"></a>Üstündeki
 Durum çubuğuna benzer şekilde, bilgi çubuğu, ayrıca ilerleme çubuğu veya değer değiştirici gibi belirsiz ilerleme göstergeleriyle eşleştirilemez bağlamsal bildirim ve mesajlaşma sağlar. Bilgi çubuğu ayrıntılı düzey ilerleme durumu sağlamamalı veya ilerleme durumunu belirleyici bir şekilde sağlamayabilir. Bkz. [Esnek](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md#BKMK_Infobars).

 ![İlerleme çubuğu ve mesajlaşma ile bilgi çubuğu](../../extensibility/ux-guidelines/media/0903-05-infobar.png "0903-05_InfoBar")

 **İlerleme çubuğu ve metin açıklamasıyla bilgi çubuğu**

 ![Pencere içindeki bilgi çubuğu](../../extensibility/ux-guidelines/media/0903-06-infobarinwindow.png "0903-06_InfoBarInWindow")

 **Kod Analizi penceresi içinde bilgi çubuğu**

##### <a name="inline"></a>Satır içi
 Satır içi ilerleme göstergesi, herhangi bir ilerleme yükleyicisi türü tarafından temsil edilebilir. Genellikle ilerleme göstergesi mesajlaşma ile eşleştirilir, ancak bu bir gereklilik değildir.

 ![Satır içi ilerleme değiştiricisi](../../extensibility/ux-guidelines/media/0903-07-inlinespinner.png "0903-07_InlineSpinner")

 **Değer, metinsel açıklamasıyla birlikte**

 ![Satır içi yığılmış ilerleme çubukları](../../extensibility/ux-guidelines/media/0903-08-inlinestackedprogress.png "0903-08_InlineStackedProgress")

 **Yığılmış ilerleme çubuklarını kesin**

 ![Satır içi ilerleme mesajlaşması](../../extensibility/ux-guidelines/media/0903-09-inlinetext.png "0903-09_InlineText")

 **Satır içi metin Sunucu Gezgini: yenileniyor...**

##### <a name="tool-windows"></a>Araç pencereleri
 Genel ilerleme durumu göstergesi, doğrudan araç çubuğunun altında konumlandırılmış bir belirsiz ilerleme çubuğu tarafından temsil edilir.

 ![Genel belirsiz ilerleme çubuğu](../../extensibility/ux-guidelines/media/0903-23-globalindeterminate.png "0903-23_GlobalIndeterminate")

 **Takım Gezgini genel belirsiz ilerleme çubuğu**

##### <a name="dialogs"></a>İletişim Kutuları
 İletişim kutuları, ilerleme yükleyicisi türlerinden herhangi birini içerebilir. İlerleme göstergeleri mesajlaşma ile eşleştirilebilir ve ayrıntılı ve alt süreçler temsil etmek için birden çok ilerleme göstergesi düzeyiyle birleştirilebilir.

 ![Birden çok ilerleme göstergesi türüyle iletişim kutusu](../../extensibility/ux-guidelines/media/0903-11-dialog.png "0903-11_Dialog")

 **Eşzamanlı süreçler ve birden çok ilerleme göstergesi türü içeren Visual Studio iletişim kutusu**

 ![İlerleme yükleyicisi ve mesajlaşma ile iletişim kutusu](../../extensibility/ux-guidelines/media/0903-12-dialog2.png "0903-12_Dialog2")

 **İlerleme yükleyicisi ve mesajlaşma satır içi komutlama içeren Visual Studio iletişim kutusu**

##### <a name="document-well"></a>Belge kutusu
 Belge kutusu, denetimlerle birlikte birden çok ilerleme yükleyici türü görüntüleyebilir.

 ![Belge kutusu 'nda ilerleme mesajlaşması](../../extensibility/ux-guidelines/media/0903-13-documentwell.png "0903-13_DocumentWell")

 **Araç çubuğunun altındaki belirsiz ilerleme çubuğu**

##### <a name="output-window"></a>Çıktı Penceresi
 Çıkış penceresi, işlem ilerlemesini ve sürekli ilerleme durumunu satır içi metinsel mesajlaşma yoluyla işlemeye uygundur. Durum çubuğunu, çıkış penceresi ilerleme durumu raporlamasıyla birlikte kullanmanız gerekir.

 ![Çıkış Penceresi ilerleme durumu iletisi](../../extensibility/ux-guidelines/media/0903-14-outputwindow.png "0903-14_OutputWindow")

 **Devam eden işlem durumu ve ileti bekleme ile Çıkış Penceresi**

## <a name="infobars"></a><a name="BKMK_Infobars"></a> Çocuk

### <a name="overview"></a>Genel Bakış
 Çocuk, kullanıcıya dikkat çekici bir gösterge ve paylaşılan bilgi çubuğu denetiminin kullanılması, görsel görünüm ve etkileşime göre tutarlılık sağlar.

 ![Üstündeki](../../extensibility/ux-guidelines/media/0904-01-infobar.png "0904-01_Infobar")

 **Visual Studio 'da çeşitliler**

#### <a name="appropriate-uses-for-an-infobar"></a>Bilgi çubuğu için uygun kullanımlar

- Kullanıcıya, geçerli bağlamla ilgili olmayan ancak önemli bir ileti vermek için

- Kullanıcı arabiriminin geçmiş hata ayıklama gibi bazı etkileşim etkilerini taşıyan belirli bir durumda veya koşulda olduğunu göstermek için

- Bir uzantının performans sorunlarına neden olduğu gibi, kullanıcıya sistemin sorun algıladığını bildirmek için

- Kullanıcıya, düzenleyicinin bir dosyanın karışık sekmeler ve boşluklar olduğunu algıladığında olduğu gibi kolayca işlem yapması için bir yol sağlamak için

##### <a name="do"></a>Gösterme

- Bilgi çubuğu ileti metnini ve noktasına tutun.

- Kısa bağlantılarında ve düğmelerde metni tutun.

- Kullanıcılara sağladığınız "eylem" seçeneklerinin yalnızca gerekli eylemleri gösteren en düşük düzeyde olduğundan emin olun.

##### <a name="dont"></a>Yapma:

- Bir araç çubuğuna yerleştirilmesi gereken standart komutları sunmak için bir bilgi çubuğu kullanın.

- Kalıcı bir iletişim kutusu yerine bir bilgi çubuğu kullanın.

- Pencerenin dışında bir kayan ileti oluşturun.

- Aynı penceredeki çeşitli konumlarda birden çok çocuk kullanın.

#### <a name="can-multiple-infobars-show-at-the-same-time"></a>Aynı anda birden çok çeşitliler gösterilebilir mi?
 Evet, birden çok çocuk aynı anda gösterilebilir. İlk gelen, ilk kez sunulan ilk bilgi çubuğu ve aşağıda gösterilen ek popüler sırada görüntülenir.

 Kullanıcı aynı anda en fazla üç ve daha fazla, daha fazla çocuk varsa bilgi çubuğu bölgesinin kaydırılabilir hale gelmesini sağlayacak.

### <a name="creating-an-infobar"></a>Bilgi çubuğu oluşturma
 Bilgi çubuğu, soldan sağa dört bölümden oluşur:

- **Simge:** Bu, bir uyarı simgesi gibi bilgi çubuğu için görüntülenmesini istediğiniz herhangi bir simgeyi eklediğiniz yerdir.

- **Metin:** Kullanıcının içinde bulunduğu senaryoyu/durumu, gerekirse metnin içindeki bağlantıları tanımlayacak şekilde metin ekleyebilirsiniz. Kısa metnini tutmayı unutmayın.

- **Eylemler:** Bu bölüm, kullanıcının bilgi çubuğunda gerçekleştirebileceği eylemlere yönelik bağlantılar ve düğmeler içermelidir.

- **Kapat düğmesi:** Sağ taraftaki son bölümde bir kapatma düğmesi olabilir.

#### <a name="creating-a-standard-infobar-in-managed-code"></a>Yönetilen kodda standart bilgi çubuğu oluşturma
 Infobarmodel sınıfı, bilgi çubuğu için bir veri kaynağı oluşturmak üzere kullanılabilir. Şu dört oluşturuculardan birini kullanın:

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

 Burada köprü, eylem düğmesi ve simge içeren bir metin içeren bir InfoBarModel oluşturan örnek verilmiştir.

 ![Köprü ile bilgi çubuğu](../../extensibility/ux-guidelines/media/0904-02-infobarhyperlink.png "0904-02_InfobarHyperlink")

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
 Yerel koddan bir bilgi çubuğu sağlamak için ısınfobar arabirimini uygulayın.

```
public interface IVsInfoBar
{
    IVsInfoBarActionItemCollection ActionItems { get; }
    ImageMoniker Image { get; }
    bool IsCloseButtonVisible { get; }
    IVsInfoBarTextSpanCollection TextSpans { get; }
}

```

#### <a name="getting-an-infobar-uielement-from-an-infobar"></a>Bilgi çubuğu 'ndan bilgi çubuğu UIElement 'i alma
 Infobarmodel veya ısınfobar uygulamasının Kullanıcı arabiriminde gösterilmesi için bir UIElement 'e açılması gereken veri modelleri vardır. Svsınfobaruifactory/ısınfobaruifactory hizmeti ile bir UIElement elde edilebilir.

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
 , Aşağıdaki konumlardan bir veya daha fazlası olabilir:

- Araç pencereleri

- Belge sekmesi içinde

> [!IMPORTANT]
> Genel bağlam hakkında bir ileti vermek için bir bilgi çubuğu yerleştirmek mümkündür. Bu, araç çubukları ve belge kutusu arasında görünür. Bu, IDE 'nin "atılması ve Jerk" ile sorun yaşamadığı ve kesinlikle gerekli ve uygun olmadıkça kaçınılması gerektiğinden önerilmez.

#### <a name="placing-an-infobar-in-a-toolwindowpane"></a>ToolWindowPane 'a bir bilgi çubuğu yerleştirme
 Araç penceresine bir bilgi çubuğu eklemek için ToolWindowPane. Addbilgi çubuğu (IVsInfoBar) yöntemi kullanılabilir. Bu API, bir IComparer (Of ınfobarmodel varsayılan bir uygulama) veya bir IVsUIElement 'ten ekleyebilirsiniz.

#### <a name="placing-an-infobar-in-a-document-or-non-toolwindowpane"></a>Belge veya araç kutusu olmayan pencere bölmesine bilgi çubuğu yerleştirme
 Herhangi bir IVsWindowFrame 'e bir bilgi çubuğu yerleştirmek için VSFPROPID_InfoBarHost özelliğini kullanarak çerçeve için ısınfobarhost 'u alın ve ardından bilgi çubuğu UIElement 'i ekleyin.

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

#### <a name="placing-an-infobar-in-the-main-window"></a>Ana pencereye bir bilgi çubuğu yerleştirme
 Ana pencereye bir bilgi çubuğu yerleştirmek için IVsShell hizmetinin VSSPROPID_MainWindowInfoBarHost kullanarak ana pencerenin ısınfobarkonağını alın ve ardından bilgi çubuğu UIElement 'i ekleyin.

### <a name="will-i-know-when-the-user-takes-action-in-my-infobar"></a>Kullanıcının bilgi çubuğunda ne zaman işlem yapması gerektiğini biliyorum mıyım?
 Evet, her olay eylemini bilgi çubuğu yazarına geri döndüreceğiz. Daha sonra bilgi çubuğu 'ndaki Kullanıcı seçimine bağlı olarak IDE 'de işlem yapmak için bilgi çubuğu yazarına kadar. İzin, kapatma düğmesine tıklandığı konaktan otomatik olarak kaldırılacak, ancak diğer engelleri kapatmadan sonra kaldırılması gerekiyorsa ek çalışma gerekir. Telemetride her bilgi çubuğu tarafından bağımsız olarak günlüğe kaydedilmiş olması gerekir.

#### <a name="receiving-infobar-events-in-a-toolwindowpane"></a>Araç çubuğu olaylarını bir ToolWindowPane içinde alma
 ToolWindowPane, esnek bir şekilde iki olaya sahiptir. InfoBarClosed olayı, ToolWindowPane 'daki bir bilgi çubuğu kapatıldığında tetiklenir. Bilgi çubuğu içindeki bir köprü veya düğme tıklandığında Infobaractionıtemclicked olayı tetiklenir.

#### <a name="receiving-infobar-events-directly-from-the-uielement"></a>Doğrudan UIElement 'ten bilgi çubuğu olaylarını alma
 Isınfobaruıelement. Advise, olaylara doğrudan bir bilgi çubuğu 'nun UIElement 'ten abone olmak için kullanılabilir. Isınfobaruıevents uygulamak, yazarın kapatma ve tıklama olayları almasına izin verir.

```
public interface IVsInfoBarUIEvents
{
    void OnActionItemClicked(IVsInfoBarUIElement infoBarUIElement, IVsInfoBarActionItem actionItem);
    void OnClosed(IVsInfoBarUIElement infoBarUIElement);
}

```

## <a name="error-validation"></a><a name="BKMK_ErrorValidation"></a> Hata doğrulama
 Bir Kullanıcı, gerekli bir alanın atlanması veya hatalı biçimde veri girildiğinde olduğu gibi, kabul edilebilir olmayan bilgiler girdiğinde, engelleme açılan menüsü hata iletişim kutusu kullanmak yerine denetim doğrulama veya denetimin yakınında geri bildirim kullanmak daha iyidir.

### <a name="field-validation"></a>Alan doğrulama
 Form ve alan doğrulaması üç bileşenden oluşur: bir denetim, simge ve araç ipucu. Birçok denetim türü bunu kullanabilir ancak örnek olarak bir metin kutusu kullanılacaktır.

 ![Alan doğrulaması boş &#40;&#41;](../../extensibility/ux-guidelines/media/0905-01-fieldvalidation.png "0905-01_FieldValidation")

 Alan gerekliyse, bir filigran metni **\<Required>** ve alan arka planının açık sarı (Vscgr:) olması gerekir `Environment.ControlEditRequiredBackground` ve ön plan gri (vscgr:) olmalıdır `Environment.ControlEditRequiredHintText` :

 !["Required" etiketiyle alan doğrulama](../../extensibility/ux-guidelines/media/0905-02-fieldvalidationrequired.png "0905-02_FieldValidationRequired")

 Program, odağın başka bir denetime taşındığı veya Kullanıcı belgeyi veya formu kaydettiğinde bir [Tamam] kaydetme düğmesine tıkladığı zaman, denetimin *Geçersiz içerik* durumunda olduğunu belirleyebilir.

 Geçersiz içerik durumu saptandıktan sonra, denetimin içinde ya da hemen yanında bir simge görünür. Hatayı açıklayan bir araç ipucu, simgenin ya da denetimin üzerine gelme durumunda görünmelidir. Ayrıca, geçersiz durumu oluşturan denetimin etrafında 1 piksellik bir kenarlık görünmelidir.

 ![Alan doğrulama düzeni belirtimleri](../../extensibility/ux-guidelines/media/0905-03-layoutspecs.png "0905-03_LayoutSpecs")

 **Alan doğrulama için Düzen belirtimleri**

#### <a name="acceptable-variations-for-icon-location"></a>Simge konumu için kabul edilebilir Çeşitlemeler
 Kullanıcıların doğrulama hataları hakkında bilgilendirilmesi gereken sayaçsuz benzersiz durumlar vardır. Kullanıcı arabiriminin denetim türünü ve yapılandırmasını göz önünde bulundurarak, durumunuza uygun olan simge yerleşimini seçin.

 ![Simge konumu için kabul edilebilir konumlar](../../extensibility/ux-guidelines/media/0905-04-iconlocation.png "0905-04_IconLocation")

 **Alan doğrulama simgesi konumları için kabul edilebilir Çeşitlemeler**

#### <a name="validation-requiring-a-round-trip-to-a-server-or-network-connection"></a>Sunucu veya ağ bağlantısına gidiş dönüş gerektiren doğrulama
 Bazı durumlarda, içeriğin doğrulanması için sunucuya gidiş dönüş gerekir ve Kullanıcı ilerleme durumu, doğrulama ve hata durumlarını göstermek önemlidir. Aşağıdaki şekilde, bu durumun ve önerilen Kullanıcı arabiriminin bir örneği gösterilmektedir.

 ![Sunucuya gidiş dönüş içeren doğrulama](../../extensibility/ux-guidelines/media/0905-05-roundtrip.png "0905-05_RoundTrip")

 **Sunucuya gidiş dönüş içeren doğrulama**

 "Doğrulanıyor..." öğesine uyum sağlamak için, denetimin sağ tarafındaki yeterli kullanılabilir alanın sağlanması gerektiğini unutmayın. ve "yeniden dene" metni.

#### <a name="in-place-warning-text"></a>Yerinde uyarı metni
 Hata iletisinin bir hata durumunda denetime yakın olması için kullanılabilir yer olduğunda, bu araç ipucunun tek başına kullanılması tercih edilir.

 ![&#45;yerleştir uyarısı](../../extensibility/ux-guidelines/media/0905-06-inplacewarning.png "0905-06_InPlaceWarning")

 **Yerinde uyarı metni**

#### <a name="watermarks"></a>Filigranlar
 Bazen tüm denetim veya pencere bir hata durumunda olabilir. Bu durumda, hatayı göstermek için bir filigran kullanın.

 ![Filigr](../../extensibility/ux-guidelines/media/0905-07-watermark.png "0905-07_Watermark")

 **Filigran alanı doğrulaması**
