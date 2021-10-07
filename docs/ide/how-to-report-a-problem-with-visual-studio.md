---
title: Visual Studio ile ilgili bir sorun bildirme
description: Sorun bildirme hakkında daha fazla Visual Studio
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 1b65be107c750ca841d018db5b6d62b373f2d77d
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2021
ms.locfileid: "129635431"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Visual Studio veya Visual Studio Yükleyicisi

> [!NOTE]
> Daha Mac için Visual Studio için [bkz. Mac için Visual Studio'de bir sorun bildirme.](/visualstudio/mac/report-a-problem)

Bir sorunu Visual Studio yükleyicisi ile bildirebilirsiniz. Yerleşik Geri Bildirim Aracı, ekiplerin sorunları tanılamasını ve düzeltmelerini Visual Studio tanılama bilgilerini kolayca eklemenize olanak sağlar. Bir sorunu bildirme adımları aşağıdaki gibidir.

1. **Bu Visual Studio** sağ üst köşedeki geri bildirim simgesini ve ardından Sorun Bildir'i seçin. Geri bildirim aracına, Yardım Geri Bildirim Raporu Sorun **Bildir**  >    >  **menüsünden de erişebilirsiniz.**
![Visual Studio penceresinin sağ üst köşesinde seçilen geri bildirim simgesini ve bağlam menüsünden Bir Sorun Bildir seçeneğinin seçili olduğunu gösteren ekran görüntüsü.](media/feedback-button.png)
Alternatif olarak, Visual Studio Yükleyicisi  yükleyemiyorsanız veya Visual Studio içinde geri bildirim aracına erişemiyorsanız sorun Visual Studio.  Yükleyici'de, sağ üst köşedeki geri bildirim simgesini seçin ve Sorun Bildir'i seçin.
![Uygulamanın sağ üst köşesindeki geri bildirim simgesini ve bağlam menüsünden Visual Studio Yükleyicisi Sorun Bildir'i gösteren ekran görüntüsü.](media/installer.png)

1. Sorun **Bildir'e** tıklarsanız varsayılan tarayıcınız açılır ve oturum açmak için aynı hesabı kullanarak oturum Visual Studio

   ![Sorun bildirmeye oturum açma](../ide/media/feedback-browser-top.png)

1. Başlangıç olarak hata rapor unvanını girin. En az 25 karakter uzunluğunda olmalıdır.

    ![Sorun bildirin](../ide/media/feedback-report.png)

1. Yazmaya başladıktan sonra, olası yinelemeler başlık alanı altında gösterilir

    ![Yinelenenleri arama](../ide/media/feedback-search.png)

1. Kendi problemle eşleşen bir hata olup ola bir hata raporu olup ola bir hata raporlarını seçin. Varsa, kendi biletinizi oluşturmak yerine oy kullanın.

    ![Yinelenenleri oyla](../ide/media/feedback-duplicate.png)

2. Yinelenen öğe bulunamasa, sorunun açıklamasını girerek devam eder. Hatayı yeniden oluşturma olasılığımızı artırmak için mümkün olduğunca net olmak önemlidir. Net yeniden üretme adımlarını dahil edin.

3. Hata raporuyla ilgili ise, Ekran görüntüsünü dahil edin onay kutusunu *Visual Studio ekran* görüntüsü alın.

    ![Ekran görüntüsü al ](../ide/media/feedback-screenshot.png) *Yalnızca Microsoft mühendisleri ekran görüntüsünü görebilir*

    Hatta ekran görüntüsünü doğrudan tarayıcıdan kırparak hassas veya ilgisiz bölümleri kaldırabilirsiniz.

4. Visual Studio mühendislik ekibinin sorunu çözmelerine yardımcı olmak için en iyi yöntemlerden biri, izleme ve yığın döküm dosyaları sağlamaktır. Hataya neden olan adımları kaydederek bunu kolayca yapabilirsiniz.

    ![Eylemlerinizi ](../ide/media/feedback-recording.png) *kaydetme Kaydı yalnızca Microsoft mühendisleri görebilir*

5. Ekli dosyaları gözden geçirin ve sorunu tanılamaya yardımcı olacağını inanıyorsanız ek dosyaları karşıya yükleyin.

    ![Eklenen dosyalar ](../ide/media/feedback-attachments.png) *Yalnızca Microsoft mühendisleri ekli dosyaları görebilir*

6. Son adım Gönder düğmesine **basmaktır.** Rapor göndererek, bu raporu doğrudan Visual Studio hata raporlama sistemine gönderir.

## <a name="when-further-information-is-needed"></a>Daha fazla bilgi gerektiğinde

Bir sorunda önemli bilgiler eksik olduğunda, Daha Fazla Bilgi Gerekiyor **durumunu atarız.** Sorun hakkında ihtiyacımız olan belirli bilgilerle ilgili yorumda bulunduk ve bir e-posta bildirimi alırsınız. Yedi gün içinde bilgileri al yer yer almazsa size bir anımsatıcı göndeririz. Bundan sonra, 14 gün boyunca hiç hareketsizlik olduktan sonra bileti kapatırız.

1. Sorun raporunun e-postasında yer alan bağlantıyı izleyin veya giriş sayfasına gidip Daha Fazla Bilgi Gerekiyor durumuna **gelen tüm raporları** görebilirsiniz.

    ![Visual Studio Geri Bildirim penceresinin Giriş sayfasının ekran görüntüsü. Bir geri bildirim öğesi listelenir ve kırmızı renkle "Daha Fazla Bilgi Gerekiyor" etiketiyle işaretlenir.](../ide/media/feedback-my-feedback.png)

1. Sorun raporunda Daha Fazla Bilgi Sağla bağlantısı seçerek yeni bir ekrana gidin. Burada, hangi bilgilerin isten yaptığını görebilir.

   ![Sorunun çözümü Visual Studio Microsoft tarafından istenen bilgileri gösteren Geri Bildirim penceresinin ekran görüntüsü.](../ide/media/feedback-need-more-info.png)

1. Açıklamalar, ekler veya kayıt adımları ekleyerek daha fazla bilgi sebilirsiniz. Bu deneyim, yeni bir sorun bildirmeye veya bir soruna oy verme konusunda ek bilgi sağlamaya benzer.

1. İstekte olan Microsoft mühendisi, sağlanan ek bilgiler hakkında bir bildirim alır. Araştırma için yeterli bilgiye sahipse sorun durumu değişir. Aksi takdirde mühendis daha fazla bilgi sorar.

Bu istekleri Geri Bildirimim ekranında **diğer tüm** Sorunlarınız ve **Önerileriniz ile birlikte** **görebilirsiniz.**

## <a name="search-for-solutions-or-provide-feedback"></a>Çözüm arama veya geri bildirim sağlama

Visual Studio'i kullanarak sorun bildirmeyi istemiyor veya kullana istemiyorsanız, sorunun önceden bildirilmiş ve [Visual Studio Developer Community](https://developercommunity2.visualstudio.com/search?space=8) sayfasında bir çözüm bildirilmiş olma ihtimali vardır.

Raporla ilgili bir sorun yoksa ancak bir özellik önermek istemenizi sağlarsanız bunu da yapmak için bir yer vardır. Daha fazla bilgi için Özellik [önerin sayfasına](https://aka.ms/feedback/suggest?space=8) bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Geliştirici Community Yönergeleri](./developer-community-guidelines.md)
* [Sorun bildirme Mac için Visual Studio](/visualstudio/mac/report-a-problem)
* [C++ ile ilgili bir sorun bildirme](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Geliştirici Community](https://developercommunity.visualstudio.com/home)
* [Geliştirici Topluluğu veri gizliliği](developer-community-privacy.md)
