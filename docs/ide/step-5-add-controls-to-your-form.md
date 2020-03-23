---
title: 'Adım 5: Formunuza denetim ekleme'
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631def96fc7e4b5d7858ea3474492b41c526da65
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579356"
---
# <a name="step-5-add-controls-to-your-form"></a>Adım 5: Formunuza denetim ekleme

Bu adımda, formunuza <xref:System.Windows.Forms.PictureBox> denetim ve <xref:System.Windows.Forms.CheckBox> denetim gibi denetimler eklersiniz. Ardından formunuza denetimler eklersiniz. <xref:System.Windows.Forms.Button>

## <a name="how-to-add-controls-to-your-form"></a>Formunuza denetim ekleme

1. Visual Studio IDE'nin sol tarafındaki **Araç Kutusu** sekmesini seçin (veya **Ctrl**+**Alt**+**X**tuşuna basın), ve ardından **Ortak Denetimler** grubunu genişletin. Bu, formlarda gördüğünüz en yaygın denetimleri gösterir.

1. Formunuza PictureBox denetimi eklemek için **PictureBox** öğesini çift tıklatın. TableLayoutPanel formunuzu doldurmak için sabitlenmiş olduğundan, IDE PictureBox denetimini ilk boş hücreye (sol üst köşe) ekler.

1. Seçmek için yeni **PictureBox** denetimini seçin ve ardından aşağıdaki ekran görüntüsünde gösterildiği gibi görev listesini görüntülemek için yeni PictureBox denetimindeki siyah üçgeni seçin.

    ![PictureBox görevleri](../ide/media/express_pictureboxtasks.png)<br/>PictureBox*** *görevleri**

    > [!NOTE]
    > TableLayoutPanel'inize yanlışlıkla yanlış türde bir denetim eklerseniz, silebilirsiniz. Denetimi sağ tıklatın ve ardından bağlam menüsünde **Sil'i** seçin. Menü çubuğunu kullanarak denetimleri formdan da kaldırabilirsiniz. Menü çubuğunda, > **Geri** **Al'ı**veya**Sil'i** **Düzenle'yi** > seçin.

1. **PictureBox** denetimindeki **PictureBox Görevler** **menüsünde, ana kapsayıcı bağlantısındaki Dock** bağlantısını seçin. Bu, PictureBox **Dock** özelliğini otomatik olarak **Dolduracak**şekilde ayarlar. Bunu görmek için **PictureBox** denetimini seçin, **Özellikler** penceresine gidin ve **Dock** özelliğinin **Dolgu**olarak ayarlandıkından emin olun.

1. **ColumnSpan** özelliğini değiştirerek PictureBox'ın her iki sütuna da yayılmasını sağlayabilir. **PictureBox'ta** **PictureBox** denetimini seçin ve **ColumnSpan** özelliğini **2**olarak ayarlayın. Ayrıca, PictureBox boşolduğunda boş bir çerçeve göstermek istersiniz. **BorderStyle** özelliğini **Fixed3D**olarak ayarlayın.

    > [!NOTE]
    > PictureBox'ınız için bir **ColumnSpan** özelliği görmüyorsanız, PictureBox'ın TabloDüzeni Paneli yerine forma eklenmesi olasıdır. Bunu düzeltmek için **PictureBox'ı**seçin, silin, **TableLayoutPanel'i**seçin ve ardından yeni bir PictureBox ekleyin.

1. Formdaki **TableLayoutPanel'i** seçin ve ardından forma bir Onay Kutusu denetimi ekleyin. Tablonuzdaki bir sonraki boş hücreye yeni bir Onay Kutusu denetimi eklemek için **Araç Kutusu'ndaki** **Onay Kutusu** öğesini çift tıklatın. PictureBox TableLayoutPanel'deki ilk iki hücreyi kapladığı için, Onay Kutusu denetimi sol alt hücreye eklenir. **Metin** özelliğini seçin ve aşağıdaki resimde gösterildiği gibi **Stretch**sözcüğüne yazın.

    ![Stretch özelliği ile TextBox denetimi](../ide/media/express_pictureviewercheckbox.png)<br/>***Stretch*** *özelliği* ile ***TextBox*** *denetimi*

1. Formdaki **TableLayoutPanel'i** seçin ve ardından **Araç Kutusu'ndaki** **Kapsayıcılar** grubuna gidin (TableLayoutPanel denetiminizi aldığınız yer) ve son hücreye (sağ altta) yeni bir denetim eklemek için **FlowLayoutPanel** öğesini çift tıklatın. Ardından FlowLayoutPanel'i TableLayoutPanel'e sabitle. Bunu, FlowLayoutPanel'in siyah üçgen görev **listesindeki ana kapsayıcıda Dock'u** seçerek veya FlowLayoutPanel'in **Dock** özelliğini **Dolduracak**şekilde ayarlayarak yapabilirsiniz.

    > [!NOTE]
    > A, <xref:System.Windows.Forms.FlowLayoutPanel> diğer denetimleri birbiri ardına sırayla düzenleyen bir kapsayıcıdır. Bir Akış Düzeni Panelini yeniden boyutlandırdığınızda, bunu yapacak yeri varsa, tüm denetimlerini tek bir satırda düzenler. Aksi takdirde, onları üst üste sıralar halinde düzenler. <br/><br/>Burada, dört düğme tutmak için bir FlowLayoutPanel kullanırsınız. Düğmeleri eklediğinizde üst üste bir tane düzenliyorsa, düğmeleri eklemeden önce Akış Düzeni Panelini seçtiğinizden emin olun. <br/><br/>(Genellikle, her hücre yalnızca bir denetim içerir. Bu örnekte, TableLayoutPanel'in sağ alt hücresi dört düğme denetimi içerir. Neden?  Akış Düzeni Paneli, diğer denetimleri tutan bir hücrede bir denetim olan bir kapsayıcı denetimi olduğundan.)

## <a name="to-add-buttons"></a>Düğme eklemek için

1. Eklediğiniz yeni FlowLayoutPanel'i seçin. **Araç Kutusundaki** **Ortak Denetimler'e** gidin ve FlowLayoutPanel'inize **button1** adlı bir düğme denetimi eklemek için **Düğme** öğesini çift tıklatın. Başka bir düğme eklemek için tekrarlayın. IDE zaten **button1** adlı bir düğme olduğunu belirler ve bir sonraki **düğmeyi çağırır2**.

1. Genellikle, **Araç Kutusu'nu**kullanarak diğer düğmeleri eklersiniz. Bu kez **button2'yi**seçin ve ardından menü çubuğundan**Kopyayı** **Edin'i** > seçin (veya **Ctrl**+**C**tuşuna basın). Ardından, düğmenizin bir kopyasını yapıştırmak için menü çubuğundan**Yapıştır'ı** **(veya** >  **Ctrl**+**V**tuşuna basın) seçin. Şimdi tekrar yapıştır. IDE'nin FlowLayoutPanel'e **button3** ve **button4** eklediğine dikkat edin.

    > [!NOTE]
    > Herhangi bir denetimi kopyalayıp yapıştırabilirsiniz. IDE, yeni denetimleri mantıksal bir şekilde adlandırır ve yerleştirir. Denetimi bir kapsayıcıya yapıştırArsanız, IDE yerleşim için bir sonraki mantıksal alanı seçer.

1. İlk düğmeyi seçin ve **Metin** özelliğini **resim göster'e**ayarlayın. Daha sonra **resmi temizlemek**için sonraki üç düğmenin **Metin** özelliklerini ayarlayın, arka plan **rengini ayarlayın**ve **kapatın.**

1. Düğmeleri boyutlandıralım ve panelin sağ tarafına hizalayacak şekilde düzenleyelim. **FlowLayoutPanel'i** seçin ve **FlowDirection** özelliğine bakın. **RightToLeft**olarak ayarlanan şekilde değiştirin.

   Düğmeler kendilerini hücrenin sağ tarafına hizalamalı ve resim **göster** düğmesinin sağda olması için siparişlerini tersine çevirmelidir.

    > [!NOTE]
    > Düğmeler hala yanlış sıradaysa, akışları herhangi bir sırada yeniden düzenlemek için FlowLayoutPanel'in etrafındaki düğmeleri sürükleyebilirsiniz. Bir düğme yi seçebilir ve sola veya sağa sürükleyebilirsiniz.

1. Seçmek için **Kapat** düğmesini seçin. Ardından, düğmelerin geri kalanını aynı anda seçmek için **Ctrl** tuşuna basın ve basılı tutun ve düğmeleri de seçin.

   Tüm düğmeleri seçtikten sonra **Özellikler** penceresine gidin ve **Otomatik Boyutlandırma** özelliğine gidin. Bu özellik, düğmenin tüm metnine uyacak şekilde kendisini otomatik olarak yeniden boyutlandırmasını söyler. **True**olarak ayarlayın.

   Düğmeleriniz artık düzgün boyutlandırılmalı ve doğru sırada olmalıdır. (Dört düğme de seçildiği sürece, dört Otomatik **Boyutlandırma** özelliğini de aynı anda değiştirebilirsiniz.) Aşağıdaki resimde dört düğme gösterilmektedir.

    ![Dört düğmeli Resim Görüntüleyici](../ide/media/express_autosize.png)<br/>*Dört düğmeli* ***Resim Görüntüleyici***

1. Şimdi değişikliklerinizi görmek için programınızı yeniden çalıştırın.

   Düğmeler ve onay kutusu henüz&mdash;bir şey yapmaz ama yakında, onlar dikkat edin.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

* Bir sonraki öğretici adıma gitmek için **[bkz: Adım 6: Düğme denetimlerinizi adlandırın.](../ide/step-6-name-your-button-controls.md)**

* Önceki öğretici adıma dönmek için [bkz.](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlanmış matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [öğretici 3: eşleşen bir oyun oluşturma](tutorial-3-create-a-matching-game.md)
