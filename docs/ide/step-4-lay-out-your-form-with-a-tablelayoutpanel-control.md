---
title: '4\. Adım: TableLayoutPanel denetimi ile formunuzu düzenleme'
ms.date: 08/30/2019
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f4ca58506e99331c48b33717903d1925874912
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590026"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>4\. Adım: TableLayoutPanel denetimi ile formunuzu düzenleme

Bu adımda formunuza bir <xref:System.Windows.Forms.TableLayoutPanel> denetimi eklersiniz. TableLayoutPanel, daha sonra ekleyeceğiniz formdaki denetimleri düzgün şekilde hizalamaya yardımcı olur.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>TableLayoutPanel denetimi ile formunuzu düzenleme

1. Visual Studio IDE 'nin sol tarafında, **araç kutusu** sekmesini seçin. (alternatif olarak, menü çubuğundan > **araç kutusunu** **görüntüle** ' yi seçin veya **CTRL**+**alt**+**X**tuşlarına basın.)

1. Aşağıdaki ekran görüntüsünde gösterildiği gibi, açmak için **kapsayıcılar** grubunun yanındaki küçük üçgen sembolünü seçin.

     ![kapsayıcılar grubu](../ide/media/express_toolbox.png)<br>
***Kapsayıcılar*** *grubu*

1. Formunuza düğmeler, onay kutuları ve Etiketler gibi denetimler ekleyebilirsiniz. **Araç kutusunda**TableLayoutPanel denetimine çift tıklayın. (Veya, denetimi araç kutusu ' ndan form üzerine sürükleyebilirsiniz.) Bunu yaptığınızda, IDE, aşağıdaki ekran görüntüsünde gösterildiği gibi formunuza bir TableLayoutPanel denetimi ekler.

     TableLayoutPanel denetimi](../ide/media/express_formtablelayout.png) ![<br>
***TableLayoutPanel*** *denetimi*

    > [!NOTE]
    > TableLayoutPanel ' i ekledikten sonra, formunuzda **TableLayoutPanel görevleri**başlıklı bir pencere görünürse, kapatmak için formun içinde herhangi bir yeri seçin. Bu pencere hakkında daha sonra öğreticide daha fazla bilgi edineceksiniz.

     **Araç kutusu** , sekmesini seçerken formunuzu nasıl genişlettiğine ve bunun dışında herhangi bir yeri seçtikten sonra kapandığına dikkat edin. Bu, IDE 'deki otomatik gizleme özelliğidir. Pencerenin sağ üst köşesinde yer alan raptiye simgesini seçerek otomatik gizlemeyi açıp bir yere kilitlemek için bu öğeyi etkinleştirebilir veya devre dışı bırakabilirsiniz. Raptiye simgesi aşağıdaki gibi görünür.

     ![raptiye simgesi](../ide/media/express_pushpintoolbox.png)<br>
***Raptiye*** *simgesi*

1. Bu öğeyi seçerek TableLayoutPanel 'in seçili olduğundan emin olun. Aşağıdaki ekran görüntüsünde gösterildiği gibi, **Özellikler** penceresinin en üstündeki açılan listeye bakarak hangi denetimin seçildiğini doğrulayabilirsiniz.

     TableLayoutPanel denetimini gösteren ![Özellikler penceresi](../ide/media/express_controlspropwin.png)<br>
***TableLayoutPanel*** *denetimini* gösteren ***Özellikler*** *penceresi*

1. **Özellikler** penceresinde araç çubuğundan **alfabetik** düğmesini seçin. Bu **, Özellikler penceresindeki özellikler** listesini alfabetik sırada sıralar ve bu öğreticide özellikleri bulmayı kolaylaştırır.

1. Denetim Seçicisi, **Özellikler** penceresinin üst kısmındaki açılan bir listesidir. Bu örnekte, `tableLayoutPanel1` adlı bir denetimin seçili olduğunu gösterir. **Windows Form Tasarımcısı** bir alanı seçerek veya denetim seçicinden seçim yaparak denetimleri seçebilirsiniz.

   TableLayoutPanel seçili olduğuna göre **Dock** özelliğini bulun ve **yok**olarak ayarlanması gereken **Yerleştir**' i seçin. Değerin yanında bir açılan okun göründüğünü unutmayın. Oku seçin ve ardından aşağıdaki ekran görüntüsünde gösterildiği gibi **doldur** düğmesini (ortadaki büyük düğme) seçin.

     ![seçili Özellikler penceresi](../ide/media/express_docktable.png)<br>
***Doldur*** *seçiliyken* ***Özellikler*** *penceresi*

     Visual Studio 'ya *yerleştirme* , BIR pencerenin IDE 'deki başka bir pencere veya alana Eklenme anlamına gelir. Örneğin, **Özellikler** penceresi, Visual Studio&mdash;içinde yerleştirilmemiş ve serbest kayabilecek&mdash;takılabilir veya **Çözüm Gezgini**'e göre yerleştirilmiş olabilir.

1. ' Yi **doldurmak**Için TableLayoutPanel **Dock** özelliğini ayarladıktan sonra, panelin formun tamamını doldurduğuna dikkat edin. Formu yeniden boyutlandırırsanız, TableLayoutPanel sabitlenmiş kalır ve kendisini sığacak şekilde yeniden boyutlandırır.

    > [!NOTE]
    > TableLayoutPanel Microsoft Office Word 'de bir tablo gibi çalışmaktadır: satırlar ve sütunlar bulunur ve tek bir hücre birden çok satıra ve sütuna yayılabilir. Her hücre bir denetim (bir düğme, onay kutusu veya etiket gibi) tutabilir. TableLayoutPanel ' de en üstteki satırın tamamını kapsayan bir <xref:System.Windows.Forms.PictureBox> denetimi, sol alt hücresinde bir <xref:System.Windows.Forms.CheckBox> denetimi ve sağ alt hücresindeki dört <xref:System.Windows.Forms.Button> denetimi olmalıdır.

1. Şu anda TableLayoutPanel 'in iki eşit boyutta satırı ve iki eşit boyutlu sütunu vardır. En üstteki satır ve sağ sütunun her ikisi de daha büyük olacak şekilde bunları yeniden boyutlandıralım. **Windows Form Tasarımcısı**, TableLayoutPanel ' i seçin. Sağ üst köşede, aşağıdaki gibi görünen küçük bir siyah üçgen düğmesi vardır.

     ![üçgen düğme](../ide/media/express_iconblacktriangle.gif)<br>
***Üçgen*** *düğme*

     Bu düğme, denetimin özelliklerini otomatik olarak ayarlamanıza yardımcı olan görevler olduğunu gösterir.

1. Aşağıdaki ekran görüntüsünde gösterildiği gibi, denetimin görev listesini göstermek için üçgeni seçin.

     TableLayoutPanel görevleri ![](../ide/media/express_tablepanel.png)<br>
***TableLayoutPanel*** *görevleri*

1. **Sütun ve satır stilleri** penceresini göstermek için **satırları ve sütunları Düzenle** görevini seçin. **Sütun1**' yi seçin ve yüzde düğmesinin seçili olduğundan emin olun ve **yüzde** kutusuna **15** girerek **boyutunu yüzde 15** olarak ayarlayın. (Bu, sonraki bir öğreticide kullanacağınız bir <xref:System.Windows.Forms.NumericUpDown> denetimidir.) **Sütun2** 'yi seçin ve yüzde 85 olarak ayarlayın. Pencere kapandığı için **Tamam** düğmesini henüz seçmeyin. (Ancak bunu yaparsanız, görev listesini kullanarak yeniden açabilirsiniz.)

     TableLayoutPanel sütun ve satır stilleri ![](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TableLayoutPanel*** *sütunu ve satır stilleri*

1. **Sütun ve satır stilleri** penceresinin en üstündeki **göster** açılan listesinden **Satırlar**' ı seçin. **Row1** değerini yüzde 90 ve **Row2** olarak ayarlayın.

1. Seçin **Tamam** düğmesi. TableLayoutPanel, artık büyük bir üst satıra, küçük bir alt satıra, küçük bir sol sütuna ve büyük bir sağ sütuna sahip olmalıdır. (TableLayoutPanel içindeki satırları ve sütunları formda **tableLayoutPanel1** seçerek ve sonra satır ve sütun kenarlıklarını sürükleyerek yeniden boyutlandırabilirsiniz.)

     yeniden boyutlandırılan TableLayoutPanel ile ![Form1](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1*** *(resim Görüntüleyicisi) yeniden boyutlandırılmış* ***TableLayoutPanel***

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına geçmek için, bkz. **[5. Adım: Formunuza denetim ekleme](../ide/step-5-add-controls-to-your-form.md)** .

* Önceki öğretici adımına dönmek için bkz. 3. [Adım: form özelliklerinizi ayarlama](../ide/step-3-set-your-form-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
