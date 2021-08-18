---
title: TableLayoutPanel denetimi ile formunuzu düzenleme
description: Resim görüntüleyici oluşturma öğreticisinde formlarınızı TableLayoutPanel denetimiyle oluşturun.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 22ae56bace1620971563914b2c2c1e7291404242
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056088"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>4. Adım: TableLayoutPanel denetimi ile formunuzu düzenleme

Bu adımda, formnize <xref:System.Windows.Forms.TableLayoutPanel> bir denetim eklersiniz. TableLayoutPanel, denetimleri daha sonra ekleyeceğimiz biçimde düzgün bir şekilde hizalamanıza yardımcı olur.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>TableLayoutPanel denetimiyle formlarınızı oluşturma

1. IDE'nin sol Visual Studio Araç Kutusu sekmesini **seçin.** (Alternatif olarak, menü çubuğundan Araç Kutusunu Görüntüle'yi seçin veya  >   **Ctrl** Alt X tuşlarına +  + basın.)

1. Aşağıdaki ekran görüntüsünde gösterildiği gibi **Kapsayıcılar** grubunun yanındaki küçük üçgen simgesini seçen.

     ![Kapsayıcılar grubu](../ide/media/express_toolbox.png)<br>
***Kapsayıcılar** _ _group*

1. Formuza düğmeler, onay kutuları ve etiketler gibi denetimler ebilirsiniz. Araç Kutusunda TableLayoutPanel denetimine **çift tıklayın.** (Veya denetimi araç kutusundan forma sürükleyebilirsiniz.) Bunu yapmak için aşağıdaki ekran görüntüsünde gösterildiği gibi IDE formnize bir TableLayoutPanel denetimi ekler.

     ![TableLayoutPanel denetimi](../ide/media/express_formtablelayout.png)<br>
***TableLayoutPanel** _ _control*

    > [!NOTE]
    > TableLayoutPanel'inizi ekledikten sonra form içinde **TableLayoutPanel Görevleri** başlığıyla bir pencere görünürse formu kapatmak için herhangi bir yeri seçin. Öğreticinin devamlarında bu pencere hakkında daha fazla bilgi edinebilirsiniz.

     Araç **Kutusunun, sekmesini seçtiğiniz** zaman formlarınızı kapsayacak şekilde genişletildi ve siz dışında bir yer seçtikten sonra kapanıyor. Bu, IDE'nin Otomatik Gizleme özelliğidir. Otomatik Gizle'yi açıp yerinde kilitlemek için pencerenin sağ üst köşesindeki itme simgesini seçerek pencerelerden herhangi biri için bu düğmeyi açıp kapatabilirsiniz. Pushpin simgesi aşağıdaki gibi görünür.

     ![Pushpin simgesi](../ide/media/express_pushpintoolbox.png)<br>
***Pushpin** _ _icon*

1. TableLayoutPanel'in seçerek seçildiğinden emin olun. Aşağıdaki ekran görüntüsünde gösterildiği gibi Özellikler penceresinin üst kısmında yer alan açılan listeye **bakarak** hangi denetimin seçili olduğunu doğruabilirsiniz.

     ![Özellikler penceresi TableLayoutPanel denetimi gösteriliyor](../ide/media/express_controlspropwin.png)<br>
***Özellikler** _ _penceresi* ***TableLayoutPanel _control***_

1. Özellikler **penceresinde araç** çubuğunda alfabetik **düğmesini** seçin. Bu, Özellikler penceresindeki özellik **listesini** alfabetik sırada sıralar ve bu da bu öğreticide özelliklerin daha kolay bulunmasına yardımcı olur.

1. Denetim seçici, Özellikler penceresinin en üstünde yer alan bir açılan **listedir.** Bu örnekte adlı bir denetimin `tableLayoutPanel1` seçilmelidir. Form Tasarımcısı'nda bir alan seçerek **veya Windows** seçiciden seçim kullanarak denetimleri seçin.

   TableLayoutPanel seçili olduğu için Dock özelliğini bulun ve **Dock** 'ı **seçin.** Bu, Hiçbiri olarak **ayarilmelidir.** Değerin yanında bir açılan ok göründüğüne dikkat etmek. Aşağıdaki ekran görüntüsünde gösterildiği gibi oku **ve** ardından Doldur düğmesini (ortadaki büyük düğme) seçin.

     ![Özellikler penceresi dolgu seçiliyken](../ide/media/express_docktable.png)<br>
***Özellikler** _ _penceresi ile* ***Dolgu**_ _selected*

     *Bir Visual Studio,* bir pencerenin IDE'de başka bir pencereye veya alana ne zaman ekli olduğunu ifade eder. Örneğin Özellikler **penceresi,** içinde bağlı olmayan ve serbest kayan Visual Studio çıkarılamaz veya &mdash; &mdash; Çözüm Gezgini. 

1. TableLayoutPanel Dock özelliğini **Fill** olarak ayar **verdikten** sonra panelin formun tamamını dolduran bir not alırsınız. Formu yeniden boyutlandırırsanız TableLayoutPanel yerleştirmede kalır ve sığacak şekilde yeniden boyutlandırılır.

    > [!NOTE]
    > TableLayoutPanel, Word'de Microsoft Office tablo gibi çalışır: Satırlar ve sütunlar içerir ve tek bir hücre birden çok satıra ve sütuna yay olabilir. Her hücre bir denetim (düğme, onay kutusu veya etiket gibi) tutabilir. TableLayoutPanel'inizin tüm üst satırına yayılan bir denetimi, sol alt hücresinde bir denetim ve sağ alt hücresinde dört <xref:System.Windows.Forms.PictureBox> <xref:System.Windows.Forms.CheckBox> denetim olması <xref:System.Windows.Forms.Button> gerekir.

1. TableLayoutPanel şu anda iki eşit boyutlu satıra ve iki eşit boyutlu sütuna sahiptir. Şimdi bunları üst satır ve sağ sütunun çok daha büyük olacak şekilde yeniden boyutlandıracağız. Form **Windows'nda** TableLayoutPanel'i seçin. Sağ üst köşede aşağıdaki gibi görünen küçük bir siyah üçgen düğmesi vardır.

     ![Üçgen düğmesi](../ide/media/express_iconblacktriangle.gif)<br>
***Üçgen** _ _button*

     Bu düğme, denetimin özelliklerini otomatik olarak ayarlamanıza yardımcı olan görevleri olduğunu gösterir.

1. Aşağıdaki ekran görüntüsünde gösterildiği gibi denetimin görev listesini görüntülemek için üçgeni seçin.

     ![TableLayoutPanel görevleri](../ide/media/express_tablepanel.png)<br>
***TableLayoutPanel** _ _tasks*

1. Sütun ve **Satır Stilleri penceresini görüntülemek** için Satırları ve Sütunları Düzenle **görevini** seçin. **Sütun1'i** seçin ve Yüzde düğmesinin seçildiğinden  emin olarak ve Yüzde kutusuna 15 girerek boyutunu **yüzde 15** **olarak** ayarlayın. (Bu, sonraki <xref:System.Windows.Forms.NumericUpDown> bir öğreticide kullanmak üzere bir denetimdir.) **Sütun2'yi** seçin ve yüzde 85 olarak ayarlayın. Pencere kapanacak **olduğundan** henüz Tamam düğmesini seçmeyebilirsiniz. (Ancak bunu yaptıysanız görev listesini kullanarak yeniden açabilirsiniz.)

     ![TableLayoutPanel sütun ve satır stilleri](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TableLayoutPanel** _ _column ve satır stilleri*

1. Sütun **ve** Satır Stilleri penceresinin üst kısmında yer alan Göster açılan **listesinde Satırlar'ı** **seçin.** **Satır1'i** yüzde 90 ve **Satır2'i yüzde** 10 olarak ayarlayın.

1. Tamam **düğmesini** seçin. TableLayoutPanel artık büyük bir üst satıra, küçük bir alt satıra, sol küçük bir sütuna ve büyük bir sağ sütuna sahip olmalı. (Formda **tableLayoutPanel1'i** seçerek ve ardından satır ve sütun kenarlıklarını sürükleyerek TableLayoutPanel'de satırları ve sütunları yeniden boyutlandırabilirsiniz.)

     ![Yeniden boyutlandırıldı TableLayoutPanel ile Form1](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1** _ _(Resim Görüntüleyici) ve yeniden boyutlandırılan* ***TableLayoutPanel***

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için **[bkz. 5. Adım: Formnize denetim ekleme.](../ide/step-5-add-controls-to-your-form.md)**

* Önceki öğretici adımına dönmek için [bkz. 3. Adım: Form özelliklerinizi ayarlama.](../ide/step-3-set-your-form-properties.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlı matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: Eşleştirme oyunu oluşturma](tutorial-3-create-a-matching-game.md)
