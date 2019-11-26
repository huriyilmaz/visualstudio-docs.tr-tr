---
title: '4\. Adım: TableLayoutPanel denetimi ile formunuzu düzenleyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54e4713abef096d5a23cf1ebf74a9d90db0d6409
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295732"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>4\. Adım: TableLayoutPanel Denetimi ile Formunuzu Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu adımda formunuza bir `TableLayoutPanel` denetimi eklersiniz. TableLayoutPanel, daha sonra ekleyeceğiniz formdaki denetimleri düzgün şekilde hizalamaya yardımcı olur.

 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz [. öğretici 1: Visual Basic resim görüntüleyici oluşturma-video 2](https://go.microsoft.com/fwlink/?LinkId=205211) veya [öğretici 1: video 2 ' de C# bir resim görüntüleyici oluşturma](https://go.microsoft.com/fwlink/?LinkId=205200). Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır.

### <a name="to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Bir TableLayoutPanel denetimiyle formunuzu düzenlemek için

1. Visual Studio IDE 'nin sol tarafında, **araç kutusu** sekmesini bulun. **araç** kutusu sekmesini seçin ve araç kutusu görüntülenir. (Veya menü çubuğunda **Görünüm**, **araç kutusu**' nu seçin.)

2. Aşağıdaki resimde gösterildiği gibi, açmak için **kapsayıcılar** grubunun yanındaki küçük üçgen sembolünü seçin.

     ![Kapsayıcılar grubu](../ide/media/express-toolbox.png "Express_Toolbox") Kapsayıcılar grubu

3. Formunuza düğmeler, onay kutuları ve Etiketler gibi denetimler ekleyebilirsiniz. Araç kutusunda `TableLayoutPanel` denetimine çift tıklayın. (Veya, denetimi araç kutusu ' ndan form üzerine sürükleyebilirsiniz.) Bunu yaptığınızda, IDE aşağıdaki resimde gösterildiği gibi formunuza bir `TableLayoutPanel` denetimi ekler.

     ![TableLayoutPanel denetimi](../ide/media/express-formtablelayout.png "Express_FormTableLayout") TableLayoutPanel denetimi

    > [!NOTE]
    > TableLayoutPanel ' i ekledikten sonra, formunuzda **TableLayoutPanel görevleri**başlıklı bir pencere görünürse, kapatmak için formun içinde herhangi bir yeri seçin. Bu pencere hakkında daha sonra öğreticide daha fazla bilgi edineceksiniz.

     Araç kutusu, sekmesini seçerken formunuzu nasıl genişlettiğine ve bunun dışında herhangi bir yeri seçtikten sonra kapandığına dikkat edin. Bu, IDE otomatik gizleme özelliğidir. Pencerenin sağ üst köşesinde bulunan raptiye simgesini seçerek otomatik gizlemeyi açıp bir yere kilitlemek için bu simgeyi etkinleştirebilir veya devre dışı bırakabilirsiniz. Raptiye simgesi aşağıdaki gibi görünür.

     ![Raptiye simgesi](../ide/media/express-pushpintoolbox.png "Express_PushpinToolbox") Raptiye simgesi

4. Bu öğeyi seçerek **TableLayoutPanel** 'in seçili olduğundan emin olun. Aşağıdaki resimde gösterildiği gibi, **Özellikler** penceresinin en üstündeki açılan listeye bakarak hangi denetimin seçildiğini doğrulayabilirsiniz.

     ![TableLayoutPanel denetimini gösteren Özellikler penceresi](../ide/media/express-controlspropwin.png "Express_ControlsPropWin") TableLayoutPanel denetimini gösteren Özellikler penceresi

5. **Özellikler** penceresinde araç çubuğundan **alfabetik** düğmesini seçin. Bu **, Özellikler penceresindeki özelliklerin** listesinin alfabetik sırayla görüntülenmesine neden olur, bu da bu öğreticide özellikleri bulmayı kolaylaştırır.

6. Denetim Seçicisi, **Özellikler** penceresinin üst kısmındaki açılan bir listesidir. Bu örnekte, `tableLayoutPanel1` adlı bir denetimin seçili olduğunu gösterir. Windows Form Tasarımcısı bir alanı seçerek veya denetim seçicinden seçim yaparak denetimleri seçebilirsiniz. Artık `TableLayoutPanel` seçili olduğuna göre **Dock** özelliğini bulun ve **yok**olarak ayarlanması gereken **Yerleştir**' i seçin. Değerin yanında bir açılan okun göründüğünü unutmayın. Oku seçin ve ardından aşağıdaki resimde gösterildiği gibi **doldur** düğmesini (ortadaki büyük düğme) seçin.

     ![Dolguyla Özellikler penceresi seçili](../ide/media/express-docktable.png "Express_DockTable") Dolguyla Özellikler penceresi seçili

     Visual Studio 'ya *yerleştirme* , BIR pencerenin IDE 'deki başka bir pencere veya alana Eklenme anlamına gelir. Örneğin, Özellikler penceresi yerleştirilmemiş olabilir. Bu, Visual Studio içinde iliştirilmemiş ve ücretsiz olarak taşınabilir ya da **Çözüm Gezgini**göre sabitlenebilir.

7. TableLayoutPanel **Dock** özelliğini **Fill**olarak ayarladıktan sonra, panel formun tamamını doldurur. Formu yeniden boyutlandırırsanız, TableLayoutPanel sabitlenmiş kalır ve kendisini sığacak şekilde yeniden boyutlandırır.

    > [!NOTE]
    > TableLayoutPanel Microsoft Office Word 'de bir tablo gibi çalışmaktadır: satırlar ve sütunlar bulunur ve tek bir hücre birden çok satıra ve sütuna yayılabilir. Her hücre bir denetim (bir düğme, onay kutusu veya etiket gibi) tutabilir. TableLayoutPanel 'niz, en üst satırının tamamını kapsayan bir `PictureBox` denetimine, sol alt hücresinde bir `CheckBox` denetimine ve sağ alt hücresindeki dört `Button` denetime sahip olur.

8. Şu anda TableLayoutPanel 'in iki eşit boyutta satırı ve iki eşit boyutlu sütunu vardır. En üstteki satır ve sağ sütunun her ikisi de daha büyük olması için bunları yeniden boyutlandırmanız gerekiyor. Windows Form Tasarımcısı, TableLayoutPanel ' i seçin. Sağ üst köşede, aşağıdaki gibi görünen küçük bir siyah üçgen düğmesi vardır.

     ![Üçgen düğme](../ide/media/express-iconblacktriangle.gif "Express_IconBlackTriangle") Üçgen düğme

     Bu düğme, denetimin özelliklerini otomatik olarak ayarlamanıza yardımcı olan görevler olduğunu gösterir.

9. Aşağıdaki resimde gösterildiği gibi, denetimin görev listesini göstermek için üçgeni seçin.

     ![TableLayoutPanel görevleri](../ide/media/express-tablepanel.png "Express_TablePanel") TableLayoutPanel görevleri

10. **Sütun ve satır stilleri** penceresini göstermek için **satırları ve sütunları Düzenle** görevini seçin. **Sütun1**' yi seçin ve yüzde düğmesinin seçili olduğundan emin olun ve **yüzde** kutusuna `15` girerek **boyutunu yüzde 15** olarak ayarlayın. (Bu, sonraki bir öğreticide kullanacağınız bir `NumericUpDown` denetimidir.) **Sütun2** 'yi seçin ve yüzde 85 olarak ayarlayın. Pencere kapandığı için **Tamam** düğmesini henüz seçmeyin. (Ancak bunu yaparsanız, görev listesini kullanarak yeniden açabilirsiniz.)

     ![TableLayoutPanel sütunu ve satır stilleri](../ide/media/vs-tablelayoutpanel-setup.png "VS_TableLayoutPanel_Setup") TableLayoutPanel sütunu ve satır stilleri

11. Pencerenin üst kısmındaki **göster** açılan listesinden **Satırlar**' ı seçin. **Row1** değerini yüzde 90 ve **Row2** olarak ayarlayın.

12. **Tamam** düğmesini seçin. TableLayoutPanel, artık büyük bir üst satıra, küçük bir alt satıra, küçük bir sol sütuna ve büyük bir sağ sütuna sahip olmalıdır. TableLayoutPanel içindeki satırları ve sütunları formda tableLayoutPanel1 seçerek ve sonra satır ve sütun kenarlıklarını sürükleyerek yeniden boyutlandırabilirsiniz.

     Yeniden ![boyutlandırılmış TableLayoutPanel Ile Form1](../ide/media/vs-formafterlayoutpanel.png "VS_FormAfterLayoutPanel") Yeniden boyutlandırılmış TableLayoutPanel ile Form1

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. [5. Adım: Formunuza denetim ekleme](../ide/step-5-add-controls-to-your-form.md).

- Önceki öğretici adımına dönmek için bkz. 3. [Adım: form özelliklerinizi ayarlama](../ide/step-3-set-your-form-properties.md).
