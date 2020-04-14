---
title: Visual Studio ile ilgili bir sorun nasıl bildirilir?
description: Visual Studio ile ilgili bir sorunu nasıl bildireceklerini öğrenin
ms.date: 03/11/2018
ms.topic: conceptual
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fca63b5e117f77d07c54f7556a603052853c7ef
ms.sourcegitcommit: 22deb247ad951e4971f27fdab413b158415d0584
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81276507"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Visual Studio veya Visual Studio Installer ile ilgili bir sorun nasıl bildirilir?

> [!NOTE]
> Mac için Visual Studio [için, Mac için Visual Studio'da bir sorunu nasıl bildirin.](/visualstudio/mac/report-a-problem)

Visual Studio'dan veya yükleyicisinden gelen bir sorunu, içinde bulunan Geri Bildirim Aracı'nı kullanarak bildirebilirsiniz. Geri Bildirim Aracı, geri bildirimlerinize tanısal bilgileri kolayca eklemenize olanak tanır ve Visual Studio ekiplerinin sorunları çok daha etkili bir şekilde tanılayıp düzeltmelerine yardımcı olur. Bir sorunu bildirme adımları aşağıda verilmiştir.

1. **Visual Studio'da**sağ üst köşedeki geri bildirim simgesini seçin ve Sorun Bildir'i seçin. Geri bildirim aracına da menüden erişebilirsiniz **Geri** > **Bildirim** > Gönder**Bir Sorunu Bildirin.**
![Visual Studio Developer Community](media/vsfeedbackentry.png) Alternatively'de bir sorun açılır penceresini bildirin, Visual Studio'yu yükleyemiyorsanız veya Visual Studio'daki geri bildirim aracına erişemiyorsanız Visual Studio **Installer'da** bir sorun bildirin.  Yükleyici'de sağ üst köşedeki geri bildirim simgesini seçin ve Sorun Bildir'i seçin.
![Visual Studio Developer Community'de bir sorun açılır penceresi bildirme](media/installer.png)

1. Oturum açmıyorsanız, aşağıdaki ekran görüntüsünde gösterildiği gibi **Oturum Aç'ı** seçin. Oturum açmayönergelerini ekranda izleyin.

   ![Bir sorunu bildirmek için oturum açın](../ide/media/sign-in-new-ux.png)

   Oturum açKen bir sorunu bildirmekle kalmamış, aynı zamanda mevcut geri bildirimleri oylayabilir ve yorum yapabilirsiniz.

1. Oturum imzaladıktan **sonra, Sorunlarınızı** ve **Etkinliğinizi** **takip ettiğim Öğeler** ekranında görebileceksiniz

   ![Takip Ettiğim Öğeler](../ide/media/items-i-follow.png)

1. Visual Studio, sorununuzu aramak ve başkalarının bunu rapor edip etmeyişemelerini görmek için bir arayüz sağlar. Birisi bunu bildirdi, "up-vote" bize bildirmek için.
   > [!NOTE]
   > Arama yapmak için lütfen arama kutusuna istediğiniz metni girin ve Enter'u tıklatın veya Arama simgesine basın.

   ![Benzer sorunları arama ve oy kullanma](../ide/media/search-and-vote.png)

1. Karşılaştığınız sorunu bulamazsanız, ekranın alt kısmında **yeni sorunu bildir'i** seçin.

   > [!NOTE]
   > **Yeni sorun bildir** düğmesi yalnızca Geliştirici Topluluğu için Visual Studio arabiriminde görünür. Bir sorunu doğrudan [Geliştirici Topluluğu](https://developercommunity.visualstudio.com/) web sitesinde bildiremezsiniz.

1. Sorun için, sorunu doğru Visual Studio ekibine yönlendirmemize yardımcı olacak açıklayıcı bir başlık oluşturun.

1. Bize ek ayrıntılar verin ve mümkünse sorunu yeniden oluşturma adımlarını sağlayın.

   ![Yeni bir sorun bildirme](../ide/media/report-new-problem.png)

1. **Ekler** sekmesine geçmek için **İleri'yi** seçin. Burada, Microsoft'a göndermek için geçerli ekranınızı yakalayabilirsiniz. Ek ekran görüntüleri veya diğer dosyalar eklemek için **Ek Dosyalar Ekle'yi**seçin.

   ![Visual Studio sorun raporuna ekran görüntüsü ekleme](media/report-a-problem-screenshot.png)

1. Ekran görüntüsü eklemek veya [bir repro kaydetmek](#record-a-repro)istemiyorsanız, **Özet** sekmesine geçmek için **İleri'yi** seçin.

1. Raporunuzu göndermek için gönder'i ve herhangi bir resim ve izleme veya döküm dosyaları yla birlikte **Gönder'i** seçin. (Gönder **Submit** düğmesi gri renkteyse, rapor için bir başlık ve açıklama sağladığından emin olun.)

   Hangi verilerin toplandığı hakkında bilgi için, [topladığımız Verilere](developer-community-privacy.md#data-we-collect)bakın.

## <a name="record-a-repro"></a>Bir repro kaydetme

İzleme ve yığın döküm dosyaları sorunları tanılamamıza yardımcı olur. Repro adımlarınızı kaydetmek ve verileri Microsoft'a göndermek için **Sorun Bildir** aracını kullandığınızda bunu takdir ederiz. Bunu şu şekilde yapabilirsiniz:

1. Sorununuzun başlığını ve açıklamasını girdikten sonra **Ekler** sekmesine geçmek için **İleri'yi** seçin.

1. **Kayıt** sekmesini seçin.

1. **Eylemlerinizi Kaydet**altında, sorunu orada yeniden oluşturabiliyorsanız Visual Studio'nun geçerli örneğini seçin. Eğer yapamıyorsanız, örneğin Visual Studio asıldıysa, eylemleri Visual Studio'nun yeni bir örneğine kaydetmek için ** \<>yeni bir örnek oluştur'u** seçin.

1. **Kayıt Başlat'ı**seçin. Aracı çalıştırmak için izin verin.

   ![Visual Studio sorun raporunda izleme ve yığın döküm dosyası sağlamak için "Kayıt Başlat"ı seçin](../ide/media/record-dialog-box.png)

1. Steps **Kaydedici** aracı göründüğünde, sorunu yeniden oluşturan adımları gerçekleştirin.

1. Bittiğinde, **Kaydı Durdur** düğmesini seçin.

1. Visual Studio'nun kaydettiğiniz bilgileri toplaması ve paketlemesi için birkaç dakika bekleyin.

   Hangi verilerin toplandığı hakkında bilgi için, [topladığımız Verilere](developer-community-privacy.md#data-we-collect)bakın.

## <a name="when-further-information-is-needed-need-more-info"></a>Daha fazla bilgiye ihtiyaç duyulduğunda (Daha Fazla Bilgiye İhtiyaç)

Visual Studio 2017 Sürüm 15.5'ten başlayarak, kullanıcıların sorun raporları hakkında ek bilgi vermelerine yardımcı olacak yeni bir iş akışı vardır.

1. Bir Microsoft mühendisi [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) sorununu **Need More Info** durumuna ayarladığında, sorunu gönderen, oylayan, takip eden veya yorum yapan herhangi bir kullanıcı Visual Studio'daki Bir **Sorun Bildir** aracında bir bildirim alır.

   ![Visual Studio'da Daha Fazla Bilgi Bildirimine İhtiyaç](../ide/media/nmi-notification.png)

1. Dikkat gerektiren sorunları filtrelemek ve görünümü sıralamak için **Sorunları Görüntüle** bağlantısını tıklatın. Bu sorunlar, genel arama da onları ayırt etmek için, yanlarında bir gösterge var.

1. Sorun ayrıntılarını görüntülemek için bir soruna tıklayın.

   ![Daha Fazla Bilgi Bildirimine İhtiyaç](../ide/media/nmi-details-view.png)

1. **Daha Fazla Bilgi İsteği İsteği'ni** görüntülemek için, sorun ayrıntıları görünümünde **isteklerini görüntüle ve yanıtla** bağlantısını tıklatın. Bir iletişim kutusu isteği gösterir.

   ![Daha Fazla Bilgi Bildirimine İhtiyaç](../ide/media/nmi-request.png)

1. Yorum, ek veya kayıt adımları ekleyerek daha fazla bilgi sağlayabilirsiniz. Bu deneyim, yeni bir sorun bildirmeye veya bir soruna oy verirken ek bilgi sağlamaya benzer.

1. İstenen Microsoft mühendisi, sağlanan ek bilgiler hakkında bir bildirim alır. Araştırmak için yeterli bilgiye sahiplerse, sorun durumu değişir. Aksi takdirde, mühendis daha fazla bilgi ister.

   > [!NOTE]
   > * Yanıtladığınızda, bildirim ortadan kalkar. Onun yerine, size teşekkür eden ve daha fazla bilgi sağlamak için bir yol kolaylaştıran bir afiş bakın.
   > * Sorun durumu değiştikten sonra, sorunu izleyen herkes için bildirim ortadan kalkar.
   > * Aynı **Need More Info** isteğini birden fazla kişi yanıtlayabilir.
   > * [Geliştirici Topluluğu'nda](https://developercommunity.visualstudio.com/) doğrudan bir web tarayıcısı üzerinden erişdiğinizde Daha Fazla **Bilgi İhtiyacı** İş Akışı yoktur, ancak burada yorum ve ekleri de sağlayabilirsiniz.

## <a name="search-for-solutions-or-provide-feedback"></a>Çözüm arama veya geri bildirim sağlama

Bir sorunu bildirmek için Visual Studio'yu kullanmak istemiyorsanız veya kullanamıyorsanız, sorunun zaten bildirilmiş olma olasılığı ve [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) sayfasında bir çözüm yayınlanmıştır.

Bildirmek için bir sorun yoksa ancak bir özellik önermek istiyorsanız, bunun için de bir yer vardır. Daha fazla bilgi için [bir özellik öner](https://developercommunity.visualstudio.com/content/idea/post.html?space=8) sayfasına bakın.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio geri bildirim seçenekleri](../ide/feedback-options.md)
* [Mac için Visual Studio ile ilgili bir sorun bildirme](/visualstudio/mac/report-a-problem)
* [C++ ile ilgili bir sorunu bildirme](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Geliştirici Topluluğu](https://developercommunity.visualstudio.com/)
* [Geliştirici Topluluğu veri gizliliği](developer-community-privacy.md)
