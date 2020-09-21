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
ms.openlocfilehash: b2deb3f8ff19c2d7805031c0c3ba02bc82b8a3e7
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810880"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Visual Studio veya Visual Studio Yükleyicisi ilgili bir sorunu bildirme

> [!NOTE]
> Mac için Visual Studio için bkz. [Mac için Visual Studio bir sorunu bildirme](/visualstudio/mac/report-a-problem).

Visual Studio 'dan veya yükleyicisinden bir sorun rapor edebilirsiniz. Yerleşik geri bildirim aracı, Visual Studio ekiplerinin sorunları tanılamanıza ve düzeltmesine yardımcı olan tanılama bilgilerini kolayca eklemenize olanak tanır. Sorun bildirme adımları aşağıda verilmiştir.

1. **Visual Studio 'da**sağ üst köşedeki geri bildirim simgesini seçin ve sorun bildir ' i seçin. Ayrıca, geri bildirim **aracına menü aracılığıyla**da erişebilirsiniz  >  .**geri bildirim gönder**  >  **sorun bildir**.
![Visual Studio Geliştirici topluluğu 'nda sorun raporu oluşturma ](media/feedback-button.png) , Visual Studio 'yu yükleyemezseniz **Visual Studio yükleyicisi** bir sorun bildirin veya Visual Studio içindeki geri bildirim aracına erişemedik.  Yükleyicide, sağ üst köşedeki geri bildirim simgesini seçin ve sorun bildir ' i seçin.
![Visual Studio Geliştirici topluluğu 'nda bir sorun açılır penceresi bildirin](media/installer.png)

1. **Sorun bildir** ' e tıkladığınızda varsayılan tarayıcınız açılır ve Visual Studio 'da oturum açmak için kullandığınız hesabı kullanarak oturumunuzu açacaksınız

   ![Sorun bildirmek için oturum açın](../ide/media/feedback-browser-top.png)

1. Hata raporunuzun açıklayıcı başlığını girerek başlayın. En az 25 karakter uzunluğunda olmalıdır.

    ![Sorun bildirin](../ide/media/feedback-report.png)

1. Yazmaya başladığınızda, olası yinelemeler başlık alanının altında gösterilir

    ![Yinelemeleri ara](../ide/media/feedback-search.png)

1. Kendi sorununuzun eşleşen bir sorun olup olmadığını görmek için olası yinelenen hata raporlarını seçin. Varsa, kendi biletinizi oluşturmak yerine BT için oy verin.

    ![Yinelemeler için oy ver](../ide/media/feedback-duplicate.png)

2. Yinelenen öğe bulunmazsa, sorunun açıklamasını girerek devam edin. Hatayı yeniden oluşturma olasılığınızı artırmak için mümkün olduğunca net olması önemlidir. Açık çoğaltma adımlarını eklediğinizden emin olun.

3. Hata raporuyla ilgiliyse, *Visual Studio ekran görüntüsünü Ekle* onay kutusunu işaretleyerek ekran görüntüsünü alın.

    ![Ekran görüntüsünü Al ](../ide/media/feedback-screenshot.png) *yalnızca Microsoft mühendisleri ekran görüntüsünü görebilir*

    Hassas veya ilişkisiz parçaları kaldırmak için ekran görüntüsünü doğrudan tarayıcıda da kırpabilirsiniz.

4. Visual Studio mühendislik ekibinin sorunu çözmesine yardımcı olmanın en iyi yöntemlerinden biri, bunların görünmesi için bir izleme ve yığın döküm dosyası sağlamaktır. Hataya neden olan adımları kaydederek kolayca bunu yapabilirsiniz. 

    ![](../ide/media/feedback-recording.png) *Yalnızca Microsoft mühendisleri, kayıt işlemlerini görebilir*

5. Ekli dosyaları gözden geçirin ve sorunu tanılamanıza yardımcı olacağını düşünüyorsanız ek dosyaları karşıya yükleyin.   

    ![Ekli dosyalar ](../ide/media/feedback-attachments.png) *yalnızca Microsoft mühendisleri ekli dosyaları görebilir*

6. Son adım **Gönder düğmesine ulaşmaları** . Raporun gönderilmesi, doğrudan önceliklendirme bekleyen dahili Visual Studio hata raporlama sistemine gönderilir.

## <a name="when-further-information-is-needed"></a>Daha fazla bilgi gerektiğinde

Bir sorun için önemli bilgiler eksik olduğunda, **Ihtiyaçları daha fazla bilgi** durumuna atacağız. İhtiyaç duyduğumuz belirli bilgilerle ilgili sorun hakkında yorum yaptık ve bir e-posta bildirimi alacaksınız. Bilgileri yedi gün içinde almadığımızda size bir anımsatıcı göndereceğiz. Bundan sonra, 14 gün etkin olmama sonrasında bilet kapattık.

1. Sorun raporuna e-postadaki bağlantıyı izleyin veya **gereksinimler daha fazla bilgi** durumunda tüm raporları görmek Için geri bildirimime gidin.

    ![Geri bildirimim](../ide/media/feedback-my-feedback.png)

1. Sorun raporundaki daha fazla bilgi sağla bağlantısı seçildiğinde sizi yeni bir ekrana götürür. Burada, hangi bilgileri istendiğini görebilirsiniz.

   ![Geri bildirimim](../ide/media/feedback-need-more-info.png)

1. Açıklamalar, ekler veya kayıt adımları ekleyerek daha fazla bilgi sağlayabilirsiniz. Bu deneyim, yeni bir sorunu raporlamaya veya bir sorun üzerinde oylama yaparken ek bilgi sağlamaya benzer.

1. İstekte bulunan Microsoft mühendis, sunulan ek bilgiler hakkında bir bildirim alır. Araştırmak için yeterli bilgi varsa, sorun durumu değişir. Aksi takdirde mühendis daha da fazla bilgi ister.

Bu istekleri, tüm diğer **sorun** ve **önerilerinizle birlikte geri bildirim** ekranında görebilirsiniz. **Suggestions**

## <a name="search-for-solutions-or-provide-feedback"></a>Çözüm arayın veya geri bildirim sağlayın

Bir sorunu bildirmek için Visual Studio 'Yu kullanmak istemiyorsanız, sorun daha önce bildirilme ve [Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/) sayfasında gönderilen bir çözüm olabilir.

Rapor almak için bir sorun yoksa ancak bir özellik önermek istiyorsanız, bunu yapmanın bir yeri de vardır. Daha fazla bilgi için bkz. [özellik önerme](https://developercommunity.visualstudio.com/content/idea/post.html?space=8) sayfası.

## <a name="see-also"></a>Ayrıca bkz.

* [Geliştirici topluluğu yönergeleri](./developer-community-guidelines.md)
* [Visual Studio geri bildirim seçenekleri](../ide/feedback-options.md)
* [Mac için Visual Studio sorun bildirme](/visualstudio/mac/report-a-problem)
* [C++ ile ilgili sorun bildirme](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/)
* [Geliştirici Topluluğu veri gizliliği](developer-community-privacy.md)