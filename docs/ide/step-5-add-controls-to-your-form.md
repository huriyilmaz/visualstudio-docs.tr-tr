---
title: '5. Adım: Formunuza denetimler ekleme'
description: Formnize denetim ve denetim <xref:System.Windows.Forms.PictureBox> gibi denetimleri <xref:System.Windows.Forms.CheckBox> nasıl ekleyebilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 638d7e32a522523cf53213fee1194c7a1a1bbc4e
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123398422"
---
# <a name="step-5-add-controls-to-your-form"></a>5. Adım: Formunuza denetimler ekleme

Bu adımda, formunuza denetim ve <xref:System.Windows.Forms.PictureBox> denetim <xref:System.Windows.Forms.CheckBox> gibi denetimler eklersiniz. Ardından <xref:System.Windows.Forms.Button> formnize denetimler eklersiniz.

## <a name="how-to-add-controls-to-your-form"></a>Formnize denetimler ekleme

1. **IDE'nin** sol tarafındaki Araç Kutusu sekmesini Visual Studio (veya **Ctrl** Alt X tuşlarına basın) ve ardından +  +  **Ortak Denetimler grubunu** genişletin. Bu, formlarda gördüğünüz en yaygın denetimleri gösterir.

1. **Formnize bir PictureBox** denetimi eklemek için PictureBox öğesini çift tıklatın. TableLayoutPanel formlarınızı dolduracak şekilde yerleştirildi. IDE, PictureBox denetimine ilk boş hücreye (sol üst köşede) ekler.

1. Yeni **PictureBox denetimlerini** seçerek seçin ve ardından aşağıdaki ekran görüntüsünde gösterildiği gibi yeni PictureBox denetiminde siyah üçgeni seçerek görev listesini görüntülenin.

    ![PictureBox görevleri](../ide/media/express_pictureboxtasks.png)<br/>PictureBox **_ _tasks**

    > [!NOTE]
    > TableLayoutPanel denetiminize yanlışlıkla yanlış denetim türü eklersiniz, silebilirsiniz. Denetime sağ tıklayın ve bağlam menüsünde **Sil'i** seçin. Menü çubuğunu kullanarak da formda denetimleri kaldırabilirsiniz. Menü çubuğunda, Geri Almayı **Düzenle'yi**  >  **veya** Sil'i **Düzenle'yi**  >  **seçin.**

1. **PictureBox** **denetiminden PictureBox** Görevleri menüsünde Üst kapsayıcıya **yerleştir bağlantısını** seçin. Bu, PictureBox **Dock** özelliğini otomatik olarak Fill olarak **ayarlar.** Bunu görmek için **PictureBox** denetimlerini seçerek Özellikler  penceresine gidin ve **Dock** özelliğinin Fill olarak ayarlanmış olduğundan emin **olun.**

1. PictureBox'ın ColumnSpan özelliğini değiştirerek her iki **sütunu da yayma.** **PictureBox'ta** **PictureBox denetimi seçin** ve **ColumnSpan** özelliğini **2 olarak ayarlayın.** Ayrıca, PictureBox boş olduğunda boş bir çerçeve göstermek de gerekir. **BorderStyle özelliğini** **Fixed3D olarak ayarlayın.**

    > [!NOTE]
    > PictureBox'niz için **ColumnSpan** özelliğini görmüyorsanız büyük olasılıkla PictureBox, TableLayoutPanel yerine forma eklenmiş olabilir. Bunu düzeltmek için **PictureBox'ı** seçin, silin, **TableLayoutPanel'i** seçin ve ardından yeni bir PictureBox ekleyin.

1. Formda **TableLayoutPanel'i** seçin ve forma bir CheckBox denetimi ekleyin. Tablodaki sonraki boş hücreye yeni bir **CheckBox** denetimi eklemek için Araç Kutusunda **CheckBox** öğesini çift tıklatın. Bir PictureBox, TableLayoutPanel'de ilk iki hücreyi üstleniyorsa, CheckBox denetimi sol alt hücreye eklenir. Text **özelliğini** seçin ve aşağıdaki görüntüde gösterildiği gibi **Stretch** sözcüğüne yazın.

    ![Stretch özelliğiyle TextBox denetimi](../ide/media/express_pictureviewercheckbox.png)<br/>*_***Stretch** _property*_ ile **TextBox** _ denetimi

1. Formda **TableLayoutPanel'i** seçin ve ardından  **Araç** Kutusunda Kapsayıcılar grubuna (TableLayoutPanel denetiminizi edinmişsiniz) gidin ve son hücreye (sağ alt) yeni bir denetim eklemek için **FlowLayoutPanel** öğesini çift tıklatın. Ardından FlowLayoutPanel'i TableLayoutPanel'e yerleştirin. Bunu, FlowLayoutPanel'in siyah üçgen görev listesinde üst kapsayıcıda **Dock'ı** seçerek veya FlowLayoutPanel'in **Dock** özelliğini Fill olarak ayarerek **bunu yapabiliriz.**

    > [!NOTE]
    > , <xref:System.Windows.Forms.FlowLayoutPanel> diğer denetimleri bir satırda, arka arkaya yerleştiren bir kapsayıcıdır. FlowLayoutPanel'i yeniden boyutlandırırsanız, tüm denetimlerini tek bir satırda (buna yer varsa) sağlar. Aksi takdirde, bunları bir diğeri üzerinde satırlar olarak düzenlenmiştir. <br/><br/>Burada flowLayoutPanel kullanarak dört düğmeyi tutabilirsiniz. Düğmeleri eklerken düğmelerin üst kısmında düzenlemesi varsa, düğmeleri eklemeden önce FlowLayoutPanel'i seçin. <br/><br/>(Genellikle her hücre yalnızca bir denetim içerir. Bu örnekte TableLayoutPanel'in sağ alt hücresinde dört düğme denetimi vardır. Neden?  FlowLayoutPanel, diğer denetimleri tutan bir hücrede bulunan bir denetim olan kapsayıcı denetimi olduğundan.)

## <a name="to-add-buttons"></a>Düğme eklemek için

1. Eklemiş olduğunu yeni FlowLayoutPanel'i seçin. Araç Kutusunda  Ortak **Denetimler'e gidin** ve FlowLayoutPanel dosyanıza **button1** adlı bir düğme denetimi eklemek için Düğme öğesini çift tıklatın.  Başka bir düğme eklemek için tekrarlayın. IDE, **button1** adlı bir düğme olduğunu belirler ve bir sonraki **düğmeyi2 olarak belirler.**

1. Genellikle, Araç Kutusunu kullanarak diğer düğmeleri **eklersiniz.** Bu kez **düğme2'yi seçin** ve ardından menü çubuğundan Kopyayı Düzenle'yi  >   seçin (veya Ctrl C  + **tuşlarına basın).** Ardından menü **çubuğundan**  >  **Yapıştır'ı** Düzenle'yi seçin **(veya Ctrl** + **V tuşlarına** basarak) düğmenizin bir kopyasını yapıştırın. Şimdi tekrar yapıştırın. IDE'nin FlowLayoutPanel'e **button3** ve **button4** ekli olduğunu fark etmek.

    > [!NOTE]
    > Herhangi bir denetimi kopyalayıp yapıştırarak. IDE, yeni denetimleri mantıksal bir şekilde adlar ve yerler. Bir kapsayıcıya denetim yapıştırırsanız, IDE yerleştirme için bir sonraki mantıksal alanı seçer.

1. İlk düğmeyi seçin ve Text özelliğini **Resim** göster **olarak ayarlayın.** Ardından, sonraki **üç** düğmenin Metin özelliklerini Resmi **temizle,** Arka plan rengini ayarla ve **Kapat** olarak **ayarlayın.**

1. Şimdi düğmelerin boyutunu ve panelin sağ tarafına hizalanması için bunları düzenleyebilirsiniz. **FlowLayoutPanel'i seçin** ve **FlowDirection özelliğine** bakın. RightToLeft olarak ayar **yapmak için bunu değiştirebilirsiniz.**

   Düğmelerin hücrenin sağ tarafına hizalanması ve sıralarını ters çevirarak Resim göster **düğmesinin** sağ tarafta olması gerekir.

    > [!NOTE]
    > Düğmeler hala yanlış sırada ise, herhangi bir sırada yeniden düzenlemek için düğmeleri FlowLayoutPanel'in etrafına sürükleyebilirsiniz. Bir düğmeyi seçebilir ve sola veya sağa sürükleyebilirsiniz.

1. Kapatmak **için** Kapat düğmesini seçin. Ardından, düğmelerin geri kalanını aynı anda seçmek için **Ctrl** tuşuna basın ve basılı tutun ve bunları da seçin.

   Tüm düğmeleri seçtikten sonra Özellikler penceresine **gidin** ve **AutoSize özelliğine kaydırın.** Bu özellik, düğmeye tüm metni sığacak şekilde otomatik olarak yeniden boyutlandırmasını söyler. True olarak **ayarlayın.**

   Düğmeleriniz artık düzgün boyutlandır olmalı ve doğru sırada olmalıdır. (Dört düğmenin de seçili olduğu sürece, dört **AutoSize** özelliğini de aynı anda değiştirebilirsiniz.) Aşağıdaki görüntüde dört düğme bulunur.

    ![Dört düğmeli Resim Görüntüleyici](../ide/media/express_autosize.png)<br/>***Picture Viewer** _ _with dört düğme*

1. Şimdi değişikliklerinizi görmek için programınızı yeniden çalıştırın.

   Düğmelerin ve onay kutusunun henüz bir şey yapmasa da kısa süre &mdash; içinde yapacaklarını fark edin.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

* Sonraki öğretici adımına gitmek için bkz. **[6. Adım: Düğme denetimlerinizi olarak ad girin.](../ide/step-6-name-your-button-controls.md)**

* Önceki öğretici adımına dönmek için [bkz. 4. Adım: Formlarınızı TableLayoutPanel denetimiyle oluşturma.](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlı matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: Eşleştirme oyunu oluşturma](tutorial-3-create-a-matching-game.md)
