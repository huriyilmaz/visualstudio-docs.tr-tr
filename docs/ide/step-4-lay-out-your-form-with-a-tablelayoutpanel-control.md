---
title: TableLayoutPanel denetimi ile formunuzu düzenleme
description: Resim görüntüleyici oluşturma öğreticisinde bir TableLayoutPanel denetimiyle formunuzu düzenleyin.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: aa997d001fb2e6400516acea39e299ea39dc19ef
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397804"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>4. Adım: TableLayoutPanel denetimi ile formunuzu düzenleme

Bu adımda <xref:System.Windows.Forms.TableLayoutPanel> formunuza bir denetim eklersiniz. TableLayoutPanel, daha sonra ekleyeceğiniz formdaki denetimleri düzgün şekilde hizalamaya yardımcı olur.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>TableLayoutPanel denetimi ile formunuzu düzenleme

1. Visual Studio ıde 'nin sol tarafında, **araç kutusu** sekmesini seçin. (alternatif olarak, menü çubuğundan **görünüm**  >  **araç kutusunu** seçin veya **Ctrl** + **Alt** + **X** tuşlarına basın.)

1. Aşağıdaki ekran görüntüsünde gösterildiği gibi, açmak için **kapsayıcılar** grubunun yanındaki küçük üçgen sembolünü seçin.

     ![Kapsayıcılar grubu](../ide/media/express_toolbox.png)<br>
***Kapsayıcılar** _ _group *

1. Formunuza düğmeler, onay kutuları ve Etiketler gibi denetimler ekleyebilirsiniz. **Araç kutusunda** TableLayoutPanel denetimine çift tıklayın. (Veya, denetimi araç kutusu ' ndan form üzerine sürükleyebilirsiniz.) Bunu yaptığınızda, IDE, aşağıdaki ekran görüntüsünde gösterildiği gibi formunuza bir TableLayoutPanel denetimi ekler.

     ![TableLayoutPanel denetimi](../ide/media/express_formtablelayout.png)<br>
***TableLayoutPanel** _ _control *

    > [!NOTE]
    > TableLayoutPanel ' i ekledikten sonra, formunuzda **TableLayoutPanel görevleri** başlıklı bir pencere görünürse, kapatmak için formun içinde herhangi bir yeri seçin. Bu pencere hakkında daha sonra öğreticide daha fazla bilgi edineceksiniz.

     **Araç kutusu** , sekmesini seçerken formunuzu nasıl genişlettiğine ve bunun dışında herhangi bir yeri seçtikten sonra kapandığına dikkat edin. Bu, IDE 'deki otomatik gizleme özelliğidir. Pencerenin sağ üst köşesinde yer alan raptiye simgesini seçerek otomatik gizlemeyi açıp bir yere kilitlemek için bu öğeyi etkinleştirebilir veya devre dışı bırakabilirsiniz. Raptiye simgesi aşağıdaki gibi görünür.

     ![Raptiye simgesi](../ide/media/express_pushpintoolbox.png)<br>
***Raptiye** _ _icon *

1. Bu öğeyi seçerek TableLayoutPanel 'in seçili olduğundan emin olun. Aşağıdaki ekran görüntüsünde gösterildiği gibi, **Özellikler** penceresinin en üstündeki açılan listeye bakarak hangi denetimin seçildiğini doğrulayabilirsiniz.

     ![TableLayoutPanel denetimini gösteren Özellikler penceresi](../ide/media/express_controlspropwin.png)<br>
*_* ***TableLayoutPanel**_ _control * gösteren **Özellikler** _ penceresi

1. **Özellikler** penceresinde araç çubuğundan **alfabetik** düğmesini seçin. Bu **, Özellikler penceresindeki özellikler** listesini alfabetik sırada sıralar ve bu öğreticide özellikleri bulmayı kolaylaştırır.

1. Denetim Seçicisi, **Özellikler** penceresinin üst kısmındaki açılan bir listesidir. Bu örnekte, çağrılan bir denetimin seçili olduğunu gösterir `tableLayoutPanel1` . **Windows Form Tasarımcısı** bir alanı seçerek veya denetim seçicinden seçim yaparak denetimleri seçebilirsiniz.

   TableLayoutPanel seçili olduğuna göre **Dock** özelliğini bulun ve **yok** olarak ayarlanması gereken **Yerleştir**' i seçin. Değerin yanında bir açılan okun göründüğünü unutmayın. Oku seçin ve ardından aşağıdaki ekran görüntüsünde gösterildiği gibi **doldur** düğmesini (ortadaki büyük düğme) seçin.

     ![Dolguyla Özellikler penceresi seçili](../ide/media/express_docktable.png)<br>
*_* ***Fill**_ _selected * ile _ pencere **özellikleri**

     Visual Studio *sabitleme* , bir pencere ıde içindeki başka bir pencere veya alana eklendiğinde anlamına gelir. örneğin, **özellikler** penceresi, &mdash; Visual Studio içinde iliştirilmemiş ve serbest kayabilecek &mdash; veya **Çözüm Gezgini** göre sabitlenebilir.

1. ' Yi **doldurmak** Için TableLayoutPanel **Dock** özelliğini ayarladıktan sonra, panelin formun tamamını doldurduğuna dikkat edin. Formu yeniden boyutlandırırsanız, TableLayoutPanel sabitlenmiş kalır ve kendisini sığacak şekilde yeniden boyutlandırır.

    > [!NOTE]
    > TableLayoutPanel Microsoft Office Word 'de bir tablo gibi çalışmaktadır: satırlar ve sütunlar bulunur ve tek bir hücre birden çok satıra ve sütuna yayılabilir. Her hücre bir denetim (bir düğme, onay kutusu veya etiket gibi) tutabilir. TableLayoutPanel <xref:System.Windows.Forms.PictureBox> , en üstteki satırı, <xref:System.Windows.Forms.CheckBox> sol alt hücresinde bir denetimi ve <xref:System.Windows.Forms.Button> sağ alt hücresinde dört denetimi kapsayan bir denetime sahip olmalıdır.

1. Şu anda TableLayoutPanel 'in iki eşit boyutta satırı ve iki eşit boyutlu sütunu vardır. En üstteki satır ve sağ sütunun her ikisi de daha büyük olacak şekilde bunları yeniden boyutlandıralım. **Windows Form Tasarımcısı**, TableLayoutPanel ' i seçin. Sağ üst köşede, aşağıdaki gibi görünen küçük bir siyah üçgen düğmesi vardır.

     ![Üçgen düğme](../ide/media/express_iconblacktriangle.gif)<br>
***Üçgen** _ _button *

     Bu düğme, denetimin özelliklerini otomatik olarak ayarlamanıza yardımcı olan görevler olduğunu gösterir.

1. Aşağıdaki ekran görüntüsünde gösterildiği gibi, denetimin görev listesini göstermek için üçgeni seçin.

     ![TableLayoutPanel görevleri](../ide/media/express_tablepanel.png)<br>
***TableLayoutPanel** _ _tasks *

1. **Sütun ve satır stilleri** penceresini göstermek için **satırları ve sütunları Düzenle** görevini seçin. **Sütun1**' yi seçin ve yüzde düğmesinin seçili olduğundan emin olun ve **yüzde** kutusuna **15** girerek **boyutunu yüzde 15** olarak ayarlayın. (Bu <xref:System.Windows.Forms.NumericUpDown> , sonraki bir öğreticide kullanacağınız bir denetimdir.) **Sütun2** 'yi seçin ve yüzde 85 olarak ayarlayın. Pencere kapandığı için **Tamam** düğmesini henüz seçmeyin. (Ancak bunu yaparsanız, görev listesini kullanarak yeniden açabilirsiniz.)

     ![TableLayoutPanel sütunu ve satır stilleri](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TableLayoutPanel** _ _column ve satır stilleri *

1. **Sütun ve satır stilleri** penceresinin en üstündeki **göster** açılan listesinden **Satırlar**' ı seçin. **Row1** değerini yüzde 90 ve **Row2** olarak ayarlayın.

1. **Tamam** düğmesini seçin. TableLayoutPanel, artık büyük bir üst satıra, küçük bir alt satıra, küçük bir sol sütuna ve büyük bir sağ sütuna sahip olmalıdır. (TableLayoutPanel içindeki satırları ve sütunları formda **tableLayoutPanel1** seçerek ve sonra satır ve sütun kenarlıklarını sürükleyerek yeniden boyutlandırabilirsiniz.)

     ![Yeniden boyutlandırılmış TableLayoutPanel ile Form1](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1** _ _ (resim Görüntüleyicisi) yeniden boyutlandırıldı * ***TableLayoutPanel***

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına geçmek için, bkz. **[5. Adım: Formunuza denetim ekleme](../ide/step-5-add-controls-to-your-form.md)**.

* Önceki öğretici adımına dönmek için bkz. 3. [Adım: form özelliklerinizi ayarlama](../ide/step-3-set-your-form-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
