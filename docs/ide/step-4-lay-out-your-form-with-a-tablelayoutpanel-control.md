---
title: 'Adım 4: TabloDüzeniPanel denetimi ile formunuzu düzene sürün'
ms.date: 08/30/2019
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d827077266adbe0a1ba8cabd1f19ae6d815df833
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579388"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Adım 4: TabloDüzeniPanel denetimi ile formunuzu düzene sürün

Bu adımda, formunuza bir <xref:System.Windows.Forms.TableLayoutPanel> denetim eklersiniz. TableLayoutPanel, daha sonra ekleyeceğiniz formda denetimleri düzgün bir şekilde hizalamanıza yardımcı olur.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>TabloDüzeniPanel denetimi ile formunuzu nasıl döşeyin?

1. Visual Studio IDE'nin sol **tarafında, Araç Kutusu** sekmesini seçin. (Alternatif olarak, menü çubuğundan**Araç Kutusunu** **Görüntüle'yi** > seçin veya **Ctrl**+**Alt**+**X**tuşuna basın .)

1. Aşağıdaki ekran görüntüsünde gösterildiği gibi, açmak için **Kapsayıcılar** grubunun yanındaki küçük üçgen simgesini seçin.

     ![Konteynerler grubu](../ide/media/express_toolbox.png)<br>
***Konteynerler*** *grubu*

1. Formunuza düğmeler, onay kutuları ve etiketler gibi denetimler ekleyebilirsiniz. **Araç Kutusundaki**TableLayoutPanel denetimini çift tıklatın. (Veya denetimi araç kutusundan forma sürükleyebilirsiniz.) Bunu yaptığınızda, IDE aşağıdaki ekran görüntüsünde gösterildiği gibi formunuza bir TableLayoutPanel denetimi ekler.

     ![TabloDüzeniPanel kontrolü](../ide/media/express_formtablelayout.png)<br>
***TabloDüzeniPanel*** *kontrolü*

    > [!NOTE]
    > TableLayoutPanel'inizi ekledikten sonra, **tabloDüzeniPanel Görevleri**başlığıyla formunuzun içinde bir pencere beliriyorsa, formun içinde herhangi bir yeri seçin ve kapatAbilirsiniz. Bu pencere hakkında daha sonra öğreticide daha fazla bilgi edineceksiniz.

     **Sekmeyi** seçtiğinizde Araç Kutusu'nun formunuzu kapsayacak şekilde nasıl genişlediğini ve bunun dışında herhangi bir yeri seçtikten sonra nasıl kapandığını öğrenin. Bu, IDE'deki Otomatik Gizleme özelliğidir. Otomatik Gizle'yi geçiş yapmak ve yerine kilitlemek için pencerenin sağ üst köşesindeki toka simgesini seçerek pencerelerden herhangi biri için açabilir veya kapatabilirsiniz. Toka simgesi aşağıdaki gibi görünür.

     ![Pushpin simgesi](../ide/media/express_pushpintoolbox.png)<br>
***Pushpin*** *simgesi*

1. TableLayoutPanel'in seçilerek seçildiğinden emin olun. Aşağıdaki ekran görüntüsünde gösterildiği gibi **Özellikler** penceresinin üst kısmındaki açılır listeye bakarak hangi denetimin seçildiğini doğrulayabilirsiniz.

     ![TabloDüzeniPanel denetimini gösteren özellikler penceresi](../ide/media/express_controlspropwin.png)<br>
***TabloDüzeniPanel*** *denetimini gösteren* ***özellikler*** penceresi *control*

1. **Özellikler** penceresindeki araç çubuğundaki **Alfabetik** düğmeyi seçin. Bu, **Özellikler** penceresindeki özelliklerin listesini alfabetik sıraya göre sıralar ve bu da bu öğreticideki özellikleri bulmayı kolaylaştırır.

1. Denetim seçici, **Özellikler** penceresinin üst kısmındaki açılır listedir. Bu örnekte, çağrılan `tableLayoutPanel1` bir denetimin seçildiğini gösterir. **Denetimleri Windows Forms Designer'da** bir alan seçerek veya denetim seçiciden seçerek seçebilirsiniz.

   TableLayoutPanel seçildiğine göre, **Dock** özelliğini bulun ve **Yok**olarak ayarlanmalıdır Dock **seçin**. Değerin yanında açılır ok göründüğüne dikkat edin. Oku seçin ve ardından aşağıdaki ekran görüntüsünde gösterildiği gibi **Dolgu** düğmesini (ortadaki büyük düğme) seçin.

     ![Fill seçili özellikler penceresi](../ide/media/express_docktable.png)<br>
***Properties*** ***Fill*** *seçili* *özellikler penceresi*

     Visual Studio'da *yerleştirme,* Bir pencerenin IDE'deki başka bir pencereye veya alana bağlı olması anlamına gelir. Örneğin, **Özellikler** penceresi, Visual Studio&mdash;&mdash;içinde bekar ve serbest çeşnili olan sabitlenebilir veya **Solution Explorer'a**sabitlenebilir.

1. TableLayoutPanel **Dock** özelliğini **Dolduracak**şekilde ayarladıktan sonra, panelin formun tamamını doldurduğunu fark edin. Formu yeniden boyutlandırsanız, TableLayoutPanel sabitkalır ve kendisini sığacak şekilde yeniden boyutlandırIr.

    > [!NOTE]
    > TabloDüzeni Panel Microsoft Office Word'de bir tablo gibi çalışır: Satırlar ve sütunlar vardır ve tek bir hücre birden çok satır ve sütuna yayılabilir. Her hücre bir denetimi (düğme, onay kutusu veya etiket gibi) tutabilir. TableLayoutPanel'inizin <xref:System.Windows.Forms.PictureBox> tüm üst satırını kapsayan bir <xref:System.Windows.Forms.CheckBox> denetimi, sol alt hücresinde <xref:System.Windows.Forms.Button> bir denetime ve sağ alt hücresinde dört denetime sahip olması gerekir.

1. Şu anda TableLayoutPanel'de iki eşit boyutlu satır ve iki eşit boyutlu sütun bulunmaktadır. Üst satır ve sağ sütun çok daha büyük olacak şekilde onları yeniden boyutlandıralım. **Windows Forms Designer'da**TableLayoutPanel'i seçin. Sağ üst köşede aşağıdaki gibi görünen küçük bir siyah üçgen düğmesi vardır.

     ![Üçgen düğmesi](../ide/media/express_iconblacktriangle.gif)<br>
***Üçgen*** *düğmesi*

     Bu düğme, denetimin özelliklerini otomatik olarak ayarlamanıza yardımcı olan görevleri olduğunu gösterir.

1. Aşağıdaki ekran görüntüsünde gösterildiği gibi denetimin görev listesini görüntülemek için üçgeni seçin.

     ![TabloDüzeniPanel görevleri](../ide/media/express_tablepanel.png)<br>
***TabloDüzeniPanel*** *görevleri*

1. Sütun ve **Satır Stilleri** penceresini görüntülemek için Satırları **ve Sütunları Edin** görevini seçin. **Sütun1'i**seçin ve **Yüzde** düğmesinin seçildiğinden emin olarak boyutunu yüzde **15'e** ayarlayın ve **Yüzde** kutusuna 15 girin. (Bu, daha <xref:System.Windows.Forms.NumericUpDown> sonraki bir öğreticide kullanacağınız bir denetimdir.) **Sütun2'yi** seçin ve yüzde 85 olarak ayarlayın. Pencere kapanacağı için **henüz Tamam** düğmesini seçmeyin. (Ancak bunu yaparsanız, görev listesini kullanarak yeniden açabilirsiniz.)

     ![TabloDüzeniPanel sütun ve satır stilleri](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TabloDüzeniPanel*** *sütun ve satır stilleri*

1. **Sütun ve Satır Stilleri** penceresinin üst kısmındaki açılır listedeki **Göster** listesinden **Satırlar'ı**seçin. **Row1'i** yüzde 90'a, **Satır2'yi** yüzde 10'a ayarlayın.

1. **Tamam** düğmesini seçin. TableLayoutPanel'inizin artık büyük bir üst satır, küçük bir alt satır, küçük bir sol sütun ve büyük bir sağ sütunu olmalıdır. (TabloDüzeniPanel'deki satırları ve sütunları, **tabloDüzeniPanel1'i** formda seçip satır ve sütun kenarlıklarını sürükleyerek yeniden boyutlandırabilirsiniz.)

     ![Yeniden boyutlandırılmış TabloDüzeniPanel ile Form1](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1*** *(Resim Görüntüleyici) yeniden boyutlandırılmış* ***TableLayoutPanel*** ile

## <a name="next-steps"></a>Sonraki adımlar

* Bir sonraki öğretici adıma gitmek için **[bkz: Adım 5: Formunuza denetimler ekleyin.](../ide/step-5-add-controls-to-your-form.md)**

* Önceki öğretici adıma dönmek için [bkz.](../ide/step-3-set-your-form-properties.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlanmış matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [öğretici 3: eşleşen bir oyun oluşturma](tutorial-3-create-a-matching-game.md)
