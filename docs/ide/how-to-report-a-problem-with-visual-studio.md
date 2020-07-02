---
title: Visual Studio ile ilgili sorun bildirme
description: Visual Studio ile ilgili sorun bildirme hakkında bilgi edinin
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c985d6699c75a78900366204c8bd5275f4c051d
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769928"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Visual Studio veya Visual Studio Yükleyicisi ilgili bir sorunu bildirme

> [!NOTE]
> Mac için Visual Studio için bkz. [Mac için Visual Studio bir sorunu bildirme](/visualstudio/mac/report-a-problem).

Bir sorunu Visual Studio 'dan veya yükleyicisinden dahil edilen geri bildirim aracını kullanarak rapor edebilirsiniz. Geri bildirim aracı, geri bildirimlerinize kolayca tanılama bilgileri eklemenizi sağlar ve Visual Studio ekiplerinin sorunları daha verimli bir şekilde tanılamasına ve düzeltmesine yardımcı olur. Sorun bildirme adımları aşağıda verilmiştir.

1. **Visual Studio 'da**sağ üst köşedeki geri bildirim simgesini seçin ve sorun bildir ' i seçin. Ayrıca, geri bildirim **aracına menü aracılığıyla**da erişebilirsiniz  >  .**geri bildirim gönder**  >  **sorun bildir**.
![Visual Studio Geliştirici topluluğu 'nda sorun raporu oluşturma ](media/vsfeedbackentry.png) , Visual Studio 'yu yükleyemezseniz **Visual Studio yükleyicisi** bir sorun bildirin veya Visual Studio içindeki geri bildirim aracına erişemedik.  Yükleyicide, sağ üst köşedeki geri bildirim simgesini seçin ve sorun bildir ' i seçin.
![Visual Studio Geliştirici topluluğu 'nda bir sorun açılır penceresi bildirin](media/installer.png)

1. Oturum açmadıysanız, aşağıdaki ekran görüntüsünde gösterildiği gibi **oturum aç** ' ı seçin. Oturum açmak için ekrandaki yönergeleri izleyin.

   ![Sorun bildirmek için oturum açın](../ide/media/sign-in-new-ux.png)

   Oturum açtığınızda bir sorun bildiremeyebilir, ancak mevcut geri bildirimde de oy verebilir ve yorum yapabilirsiniz.

1. Oturum açtıktan sonra, **izlediğim öğelerde** **sorun** ve **etkinliğinizi** görebileceksiniz

   ![İzlediğim öğeler](../ide/media/items-i-follow.png)

1. Visual Studio, sorununuzu aramak ve başkalarının raporlanmasını sağlamak için bir arabirim sağlar. Birisi rapor verdi, bize bildirmek için "yukarı-oy" kullanın.
   > [!NOTE]
   > Arama yapmak için lütfen istenen metni arama kutusuna girin ve ENTER ' a tıklayın ya da arama simgesine basın.

   ![Benzer sorunlar için arama ve oylayın](../ide/media/search-and-vote.png)

1. Karşılaştığınız sorunu bulamazsanız, ekranın alt kısmında **yeni sorun bildir** ' i seçin.

1. Sorun için doğru Visual Studio ekibine yönlendirmemize yardımcı olacak açıklayıcı bir başlık oluşturun.

1. Bize ek ayrıntılar verin ve mümkünse sorunu yeniden oluşturma adımlarını sağlayın.

   ![Yeni bir sorun bildirin](../ide/media/report-new-problem.png)

1. **Ekler** sekmesine geçmek için **İleri ' yi** seçin. Burada, Microsoft 'a göndermek için geçerli ekranınızı yakalayabilirsiniz. Ek ekran görüntüleri veya başka dosyalar eklemek için **ek dosya Ekle**' yi seçin.

   ![Visual Studio sorun raporuna bir ekran görüntüsü iliştirme](media/report-a-problem-screenshot.png)

1. Bir ekran görüntüsü eklemek veya yeniden [üretme kaydetmek](#record-a-repro)istemiyorsanız **Özet** sekmesine gitmek için **İleri** ' yi seçin.

1. Raporunuzu, herhangi bir görüntü ve izleme ya da döküm dosyası ile birlikte göndermek için **Gönder** ' i seçin. ( **Gönder** düğmesi gri ise rapor için bir başlık ve açıklama girdiğinizden emin olun.)

   Toplanan veriler hakkında daha fazla bilgi için bkz. [Topladığımız veriler](developer-community-privacy.md#data-we-collect).

## <a name="record-a-repro"></a>Yeniden üretme Kaydet

İzleme ve yığın dökümü dosyaları, sorunları tanılamamıza yardımcı olmak için yararlıdır. Yeniden oluşturma adımlarınızı kaydetmek ve verileri Microsoft 'a göndermek için **sorun bildir** aracını kullandığınızda teşekkür ederiz. Bunun nasıl yapılacağı aşağıda verilmiştir:

1. Sorununuz için bir başlık ve açıklama girdikten sonra, **İleri** ' yi seçerek **ekler** sekmesine geçin.

1. **Kayıt** sekmesini seçin.

1. **Eylemlerinizi kaydetme**altında, sorunu yeniden oluşturmak Için Visual Studio 'nun geçerli örneğini seçin. Bu durumda, örneğin Visual Studio askıda ise, **\<Create a new instance>** eylemleri Visual Studio 'nun yeni bir örneğine kaydetmek için öğesini seçin.

1. **Kaydı Başlat**' ı seçin. Aracı çalıştırmak için izin verin.

   ![Visual Studio sorun raporuna bir izleme ve yığın döküm dosyası sağlamak için "kaydı Başlat" ı seçin](../ide/media/record-dialog-box.png)

1. **Adım Kaydedicisi** aracı göründüğünde, sorunu yeniden oluşturmak için gereken adımları gerçekleştirin.

1. İşiniz bittiğinde, **Kaydı Durdur** düğmesini seçin.

1. Visual Studio 'nun kaydettiğiniz bilgileri toplaması ve paketlemeleri için birkaç dakika bekleyin.

   Toplanan veriler hakkında daha fazla bilgi için bkz. [Topladığımız veriler](developer-community-privacy.md#data-we-collect).

## <a name="when-further-information-is-needed-need-more-info"></a>Daha fazla bilgi gerektiğinde (daha fazla bilgi gerekiyor)

Visual Studio 2017 sürüm 15,5 ' den başlayarak, kullanıcıların sorun raporları hakkında ek bilgiler sağlamasına yardımcı olmak için yeni bir iş akışı vardır.

1. Bir Microsoft mühendis, [Visual Studio Geliştirici topluluk](https://developercommunity.visualstudio.com/) sorununu **daha fazla bilgi olması gereken** şekilde ayarlarsa, sorun üzerinde gönderilen, izlenen veya açıklamalı tüm kullanıcılar Visual Studio 'daki **sorun bildir** aracında bir bildirim alır.

   ![Visual Studio 'da daha fazla bilgi bildirimi gerekiyor](../ide/media/nmi-notification.png)

1. Filtreleri **görüntüle** bağlantısına tıklayın ve görünüme dikkat edilmesi gereken sorunlar için sıralama yapın. Bu sorunlar, genel aramada ayrım yapmak için bunların yanında bir gösterge de vardır.

1. Sorun ayrıntıları görünümünü görmek için bir soruna tıklayın.

   ![Daha fazla bilgi bildirimi gerekiyor](../ide/media/nmi-details-view.png)

1. **Daha fazla bilgi** iste isteği görüntülemek için sorun ayrıntıları görünümündeki **istek ve yanıt bağlantısını görüntüle** bağlantısına tıklayın. Bir iletişim kutusu isteği gösterir.

   ![Daha fazla bilgi bildirimi gerekiyor](../ide/media/nmi-request.png)

1. Açıklamalar, ekler veya kayıt adımları ekleyerek daha fazla bilgi sağlayabilirsiniz. Bu deneyim, yeni bir sorunu raporlamaya veya bir sorun üzerinde oylama yaparken ek bilgi sağlamaya benzer.

1. İstekte bulunan Microsoft mühendis, sunulan ek bilgiler hakkında bir bildirim alır. Araştırmak için yeterli bilgi varsa, sorun durumu değişir. Aksi takdirde mühendis daha da fazla bilgi ister.

   > [!NOTE]
   > * Yanıt gönderdiğinizde bildirim kaybolur. Bunun yerine, sizi teşekkür eden bir başlık görürsünüz ve daha da fazla bilgi sağlamak için bir yol sağlar.
   > * Sorunun durumu değişirse, bildirim sorunu izleyen herkes için kaybolur.
   > * Aynı **gereksinim daha fazla bilgi** isteği üzerinde birden fazla kişi yanıt verebilir.
   > * Doğrudan bir Web tarayıcısı üzerinden eriştiğinizde [Geliştirici topluluğu](https://developercommunity.visualstudio.com/) üzerinde **daha fazla bilgi** iş akışı gerekmez, ancak burada açıklamalar ve ekler de sağlayabilirsiniz.

## <a name="search-for-solutions-or-provide-feedback"></a>Çözüm arayın veya geri bildirim sağlayın

Bir sorunu bildirmek için Visual Studio 'Yu kullanmak istemiyorsanız, sorun daha önce bildirilme ve [Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/) sayfasında gönderilen bir çözüm olabilir.

Rapor almak için bir sorununuz yoksa ancak bir özellik önermek istiyorsanız, bunun de bir yerinde olabilir. Daha fazla bilgi için bkz. [özellik önerme](https://developercommunity.visualstudio.com/content/idea/post.html?space=8) sayfası.

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio geri bildirim seçenekleri](../ide/feedback-options.md)
* [Mac için Visual Studio sorun bildirme](/visualstudio/mac/report-a-problem)
* [C++ ile ilgili sorun bildirme](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/)
* [Geliştirici Topluluğu veri gizliliği](developer-community-privacy.md)
