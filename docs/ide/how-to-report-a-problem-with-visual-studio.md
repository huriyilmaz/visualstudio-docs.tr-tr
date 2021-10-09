---
title: Visual Studio ile ilgili bir sorun bildirme
description: Sorun bildirme hakkında daha fazla Visual Studio
ms.date: 10/07/2021
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 35bf0e0ab52a1754308fdd36dd409424d062649f
ms.sourcegitcommit: 5f1e0171626e13bb2c5a6825e28dde48061208a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2021
ms.locfileid: "129704668"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Visual Studio veya Visual Studio Yükleyicisi ile ilgili bir sorun bildirme

> [!NOTE]
> Daha Mac için Visual Studio için, [bkz. How to report a problem in Mac için Visual Studio.](/visualstudio/mac/report-a-problem)

Bir sorunu yükleyiciden veya Visual Studio bildirebilirsiniz. Yerleşik Geri Bildirim Aracı, ekiplerin sorunları tanılamasını ve düzeltmelerini Visual Studio tanılama bilgilerini kolayca eklemenize olanak sağlar. 

Sorun bildirme adımları burada veserdedir.

1. **Bu Visual Studio** sağ üst köşedeki geri bildirim simgesini ve ardından Sorun Bildir'i seçin. Geri bildirim aracına, Yardım Geri Bildirim Raporu Sorun **Bildir**  >    >  **menüsünden de erişebilirsiniz.**
![Visual Studio penceresinin sağ üst köşesindeki geri bildirim simgesini ve bağlam menüsünden Bir Sorun Bildir seçeneğinin seçili olduğunu gösteren ekran görüntüsü.](media/feedback-button.png)
Alternatif olarak, **Visual Studio Yükleyicisi'i** yükleyemiyorsanız veya Visual Studio geri bildirim aracına erişemiyorsanız Visual Studio.  Yükleyici'de, sağ üst köşedeki geri bildirim simgesini seçin ve Sorun Bildir'i seçin.
![Uygulamanın sağ üst köşesinde seçilen geri bildirim simgesini ve bağlam menüsünde Visual Studio Yükleyicisi Sorun Bildir'i gösteren ekran görüntüsü.](media/installer.png)

1. Sorun **Bildir'e** tıklarsanız varsayılan tarayıcınız açılır ve oturum açmak için aynı hesabı kullanarak oturum Visual Studio

   ![Sorun bildirmeye oturum açma](../ide/media/feedback-browser-top.png)

1. Hata rapor unvanını girerek başlayabilirsiniz. En az 25 karakter uzunluğunda olmalıdır.

    ![Sorun bildirin](../ide/media/feedback-report.png)

1. Yazmaya başladıktan sonra, olası yinelemeler başlık alanı altında gösterilir

    ![Yinelenenleri arama](../ide/media/feedback-search.png)

1. Kendi problemle eşleşen bir hata olup bula ilgili olası yinelenen hata raporlarını seçin. Varsa, kendi biletinizi oluşturmak yerine oy kullanın.

    ![Yinelenenleri oyla](../ide/media/feedback-duplicate.png)

2. Yinelenen öğe bulunamasa, sorunun açıklamasını girerek devam eder. Hatayı yeniden oluşturma olasılığımızı artırmak için mümkün olduğunca net olmak önemlidir. Net yeniden üretme adımlarını dahil edin.

3. Hata raporuyla ilgili ise, Ekran görüntüsünü dahil edin onay kutusunu *Visual Studio ekran* görüntüsü alın.

    ![Ekran görüntüsü al ](../ide/media/feedback-screenshot.png) *Yalnızca Microsoft mühendisleri ekran görüntüsünü görebilir*

    Hatta ekran görüntüsünü doğrudan tarayıcıdan kırparak hassas veya ilgisiz bölümleri kaldırabilirsiniz.

4. Visual Studio mühendislik ekibinin sorunu çözmelerine yardımcı olmak için en iyi yöntemlerden biri, izleme ve yığın döküm dosyaları sağlamaktır. Hataya neden olan adımları kaydederek bunu kolayca yapabilirsiniz.

    ![Eylemlerinizi ](../ide/media/feedback-recording.png) *kaydetme Kaydı yalnızca Microsoft mühendisleri görebilir*

5. Ekli dosyaları gözden geçirin ve sorunu tanılamaya yardımcı olacağını inanıyorsanız ek dosyaları karşıya yükleyin.

    ![Eklenen dosyalar ](../ide/media/feedback-attachments.png) *Yalnızca Microsoft mühendisleri ekli dosyaları görebilir*

6. Son adım Gönder düğmesine **basmaktır.** Rapor göndererek, bu raporu doğrudan Visual Studio raporlama sistemine gönderir.

Sorun raporlarınızı her biri çekirdek mühendislik sistemimizde iş öğesi haline gelir ve bu da etkili sorunları belirlememize ve çözmemize yardımcı olmak için doğrudan ürün ekiplerimiz ile etkileşim kurmanızı sağlar. Zengin tanılama bilgileriyle gönderilen geri bildiriminiz, ürün ailesini geliştirmek Visual Studio kritik öneme sahip. Zaman alarak sorunları bildirmeniz bizim için çok önemli.

Ayrıca, bir soruna daha fazla dikkat çekmek ve sorunu daha hızlı düzeltmeye yardımcı olmak için diğer topluluk üyelerinin geri bildirimlerini oyabilirsiniz.

## <a name="when-further-information-is-needed"></a>Daha fazla bilgi gerektiğinde

Bir sorunda önemli bilgiler eksik olduğunda, Daha Fazla Bilgi Gerekiyor **durumunu atarız.** Soruna ihtiyacımız olan belirli bilgilerle ilgili yorumda bulunduk ve bir e-posta bildirimi alırsınız. Yedi gün içinde bilgileri al yer yer almazsa size bir anımsatıcı göndeririz. Bundan sonra, 14 gün boyunca hiç hareketsizlik olduktan sonra bileti kapatırız.

1. Sorun raporunun e-postasında yer alan bağlantıyı izleyin veya giriş sayfasına gidip Daha Fazla Bilgi Gerekiyor durumuna **gelen tüm raporları** görebilirsiniz.

    ![Geri Bildirim penceresinin Giriş Visual Studio görüntüsü. Bir geri bildirim öğesi listelenir ve kırmızı renkle "Daha Fazla Bilgi Gerekiyor" etiketiyle işaretlenmiştir.](../ide/media/feedback-my-feedback.png)

1. Sorun raporunda Daha Fazla Bilgi Sağla bağlantısı seçerek yeni bir ekrana gidin. Burada, hangi bilgilerin isten yaptığını görebilir.

   ![Sorunun çözümü Visual Studio Microsoft tarafından istenen bilgileri gösteren Geri Bildirim penceresinin ekran görüntüsü.](../ide/media/feedback-need-more-info.png)

1. Açıklamalar, ekler veya kayıt adımları ekleyerek daha fazla bilgi sebilirsiniz. Bu deneyim, yeni bir sorun bildirmeye veya bir soruna oy verme konusunda ek bilgi sağlamaya benzer.

1. İstekte olan Microsoft mühendisi, sağlanan ek bilgiler hakkında bir bildirim alır. Araştırma için yeterli bilgiye sahipse sorun durumu değişir. Aksi takdirde mühendis daha fazla bilgi sorar.

Bu istekleri Geri Bildirimim ekranında **diğer tüm** Sorunlarınız ve **Önerileriniz ile birlikte** **görebilirsiniz.**

## <a name="problem-status"></a>Sorun Durumu

Bir sorun bildirdikten sonra, eyaletler gönderimlerinizi yaşam döngüsünde nerede olduğunu gösteriyor. Microsoft ekipleri geri bildiriminizi inceleyene kadar uygun bir durumla ayarladı. Aşağıda listelenen durumlara ve bunların anlam ve renk göstergelerine başvurarak sorun raporlarınızı takip edin.

| **Durum** | **Açıklama**                                                                                                         |
|-------------|-------------------------------------------------------------------------------------------------------------------------|
|  ![Geliştirici Raporları'nın sorun raporlaması için yeni Community](../ide/media/ProblemStates/New.jpg)           | **Yeni,** hatanın veya sorunun yeni bildiriliyor olduğunu ve henüz herhangi bir işlem yapılmadı.                    |
| ![Geliştirici Raporları'nın sorun raporlaması için Community](../ide/media/ProblemStates/Triaged.jpg)    | **Triaged** denetimi, çeviri ve ilk yineleme denetimi gibi ön adımların tamam olduğunu gösterir. Biletiniz, dikkate alınması için uygun mühendislik ekibine yönlendirildi.                                     |
| ![Geliştirici Raporları'nın sorun raporlama durumu altında Community](../ide/media/ProblemStates/UnderConsideration.jpg)   | **Önemli altında** Microsoft'un sorunlarınızı topluluk etkisi için gözden geçirerek buna göre öncelikleri belirlemesi gerekir. Topluluk etkisi henüz net değilse veya önemli değilse, sorunu bu durumda izlemeye devam edeceğiz.                                                                                           |
| ![Geliştirici Raporları'nın sorun raporlaması için Araştırma durumu altında Community](../ide/media/ProblemStates/UnderInvestigation.jpg)    |  **Araştırma'nın** altında, mühendislerin çözüm bulmak için sorunlarınızı etkin bir şekilde araştıran bir durum olduğu ifade edildi.                                                                                           |
|   ![Geliştirici Raporları'nın sorun raporlaması için Daha Fazla Bilgi durumu Community](../ide/media/ProblemStates/NeedMoreInfo.jpg) | **Daha Fazla Bilgi** Gerekiyor, araştırmayı devam etmek için daha fazla tanılama bilgisine ihtiyacımız olduğunu gösterir.  [Daha Fazla Bilgi Gerekiyor isteklerini yanıtlamayı öğrenin.](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed)                                                                                        |
| ![Düzeltildi - Geliştirici Raporları'nın sorun raporlaması için Yayın bekleniyor Community](../ide/media/ProblemStates/FixedPendingRelease.jpg)    | **Düzeltildi - Bekleyen Sürüm,** sorun için bir düzeltmemiz olduğunu ve bunun gelecek bir önizleme veya yayında kullanılabilir olacağını gösterir.  Düzeltme bir önizlemede kullanılabilir hale geldiğinde, sorun önizleme sürümünü belirten bir 'içinde düzeltildi' etiketiyle etiketlenir. |
| ![Kapalı - Geliştirici Raporları'nın sorun raporlaması için Community](../ide/media/ProblemStates/ClosedFixed.jpg)    | **Kapalı -** Düzeltildi, sorun için bir düzeltme yayımlamıştık. Sorun artık yayın sürümünü belirten "fixed in:" etiketiyle de etiketlenir. |
| ![Kapalı - Geliştirici Raporları'nın sorun raporlaması için Community](../ide/media/ProblemStates/ClosedDuplicate.jpg)    | **Kapalı - Yinelenen,** soruna başka bir geri bildirim yoluyla daha önce raporlandığına işaret ediyor. Özgün sorun raporunu takip etmek için size bağlantı sağlarız. |
| ![Kapalı - Geliştirici Raporları'nın sorun raporlaması için düşük öncelikli Community](../ide/media/ProblemStates/ClosedLowerPriority.jpg)    | **Kapalı - Düşük Öncelik** Geliştirici topluluğumuza her birlerinizi en iyi değere getirmek için sorunları en yüksek müşteri etkisiyle öncelik sırasına alacağız. Şu anda bu sorunu ele alamasanız da tüm geri bildirimlerinizin değerli olduğunu ve geri bildirimlerinizin iyileştirilmesine yardımcı Visual Studio. |
| ![Kapalı - Geliştirici Raporları üzerinde sorun raporlama için hata durumu Community](../ide/media/ProblemStates/ClosedNotABug.jpg)    | **Kapalı - Hata Değil,**  bildirilen işlevselliğin geçerli tasarıma göre olduğunu belirlediğimize işaret etti. |
| ![Kapalı - Geliştirici Raporları'nın sorun raporlaması için Yeterli Bilgi Community](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)    | **Kapalı - Yeterli Bilgi Yok,** bunu sizin için araştırmak için yeterli bilgiye sahip olmadığını gösterir. Gerekli bilgiler kullanılabilir olduktan sonra geri bildirimi yeniden değerlendirebilirsiniz. |
| ![Kapalı - Geliştirici Raporları'nın sorun raporlaması için diğer ürün Community](../ide/media/ProblemStates/ClosedOtherProduct.jpg)    | **Kapalı - Diğer Ürün,** sorunnizin başka bir ürün için geçerli olduğunu belirlediğimizi gösterir. Hangi dış ürün ve ilgili bağlantılar için Microsoft'tan gelen açıklamaya bakın. |

## <a name="faq"></a>SSS

#### <a name="how-can-i-increase-the-chance-of-my-problem-getting-resolved-quickly"></a>Sorunum hızla çözülme şansını nasıl artırabilirsiniz?
Rapor etmekte olduğunuz sorunun önceden bildirilmez olduğundan emin olmak için aramanın kullanılması önerilir. Problemle eşleşen mevcut bir öğe bulursanız bu sorun biletini izleyin ve oy kullanın.

Ekiplerimizin yaşadığı sorunları yeniden oluşturması için size yardımcı olacak tüm bilgileri sağlama.  Bu bilgiler gerekli yeniden proje adımlarını, kod parçalarını, ekran görüntülerini, yenidenpro kayıtlarını, günlük dosyalarını ve diğer yapıtları içerir.

#### <a name="how-is-my-feedback-prioritized"></a>Geri bildirimimin önceliği nedir?
Müşterilerimizden çok sayıda değerli sorun var. Geliştirici topluluğumuz içinde her bir kullanıcıya en iyi değeri sunduğumuzdan emin olmak için, en yüksek topluluk etkisine sahip olan geri bildirim eylemine öncelik veririz.

Geri bildiriminize kişisel olarak yanıt vere bilmiyorsanız, girdiniz bizim için çok önemli. Tüm geri bildirimlerinizin doğru takıma geldiğinden emin olun.

Daha iyi bir iş yapmak için yatırım Visual Studio değer veririz.

#### <a name="what-actions-can-i-take-if-im-not-satisfied-with-the-resolution"></a>Çözümden memnun değilim, hangi eylemleri gerçekleştir miyim?
Ekiplerimiz, sorun yaşamanız gereken sorunları tanılamak ve düzeltmek için en iyi şekilde çalışmalarına rağmen öneriden tam olarak memnun olmadığınız zamanlar olabilir. Geri bildirime geri yorum gönderin ve tam olarak nelerden memnun olmadığınız hakkında bize bildirin. İhtiyaçlarınızı karşılamamız için elimizden geleni yapacağız.

#### <a name="how-will-i-get-notified-of-progress-on-my-feedback"></a>Geri bildirimimde ilerleme durumu nasıl bildirilecek?
Microsoft mühendislik ekipleri geri bildirim bileti hakkında yorumda bulundurarak ve ilerleme kaydettikçe biletinizin durumunu değiştirerek iletişim kurar. Bilet durumu değişirken veya bir açıklama gönderilirken gönderilen e-posta bildirimlerini izleyin.  Bildirim sıklığını Geliştirici yönetim sitesinde Profil ve Tercihler ayarlarından Community yönetebilirsiniz.

#### <a name="why-cant-i-add-a-problem-for-visual-studio-ide-on-the-developer-community-website"></a>Developer Community web sitesinde IDE'Visual Studio için neden sorun Community ekley bilmiyorum?
Tanılama bilgileri aracılığıyla Visual Studio tanılama bilgileri rapora otomatik olarak dahil edilir. Mühendislerimize sorununuzu tam olarak anlamaları ve çözmek için çalışması gereken bağlamı veren temel bilgilerdir.

Visual Studio aracılığıyla rapor edebilirim; büyük günlük dosyaları, kilitlenme bilgileri, ekran görüntüleri, yeniden üretim kaydı ve daha yüksek kaliteli çözünürlükleri size daha hızlı teslim etmeye yardımcı olan diğer yapıtlar gibi zengin tanılama bilgilerini bizimle kolayca paylaşabilirsiniz.

## <a name="search-for-solutions-or-provide-feedback"></a>Çözüm arama veya geri bildirim sağlama

Visual Studio'i kullanarak sorun bildirmeyi istemiyor veya kullana istemiyorsanız, sorunun önceden bildirilmiş ve [Visual Studio Developer Community](https://developercommunity2.visualstudio.com/search?space=8) sayfasında bir çözüm bildirilmiş olma ihtimali vardır.

Raporla ilgili bir sorun yoksa ancak bir özellik önermek istemenizi sağlarsanız bunu da yapmak için bir yer vardır. Daha fazla bilgi için Özellik [önerin sayfasına](https://aka.ms/feedback/suggest?space=8) bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Geliştirici Community Yönergeleri](./developer-community-guidelines.md)
* [Sorun bildirme Mac için Visual Studio](/visualstudio/mac/report-a-problem)
* [C++ ile ilgili bir sorun bildirme](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Geliştirici Community](https://developercommunity.visualstudio.com/home)
* [Geliştirici Topluluğu veri gizliliği](developer-community-privacy.md)
