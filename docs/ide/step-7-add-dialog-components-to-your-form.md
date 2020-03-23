---
title: 'Adım 7: Formunuza İletişim bileşenleri ekleme'
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9697bf6cf84c2a74daac2017b4f63d52a7019b6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579285"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Adım 7: Formunuza iletişim bileşenleri ekleme

Uygulamanızın resim dosyalarını açıp bir arka plan rengi seçmesini <xref:System.Windows.Forms.OpenFileDialog> sağlamak için, bu adımda forma bir bileşen ve bileşen <xref:System.Windows.Forms.ColorDialog> eklersiniz.

Bileşen bazı yönlerden denetim gibidir. Formunuza bir bileşen eklemek için **Araç Kutusu'nu** kullanırsınız ve **özellikler** penceresini kullanarak özelliklerini ayarlarsınız. Ancak denetimin aksine, formunuza bir bileşen eklemek, kullanıcının formda görebileceği görünür bir öğe eklemez. Bunun yerine, kodla tetikleyebileceğiniz belirli davranışları sağlar. **Dosya aç** iletişim kutusunu açan bir bileşendir.

## <a name="to-add-dialog-components-to-your-form"></a>Formunuza iletişim bileşenleri eklemek için

1. Windows **Forms Designer** **'ı (Form1.cs [Design]**) seçin ve ardından **Araç Kutusu'ndaki** **İletişim Grubu'nu** açın.

    > [!NOTE]
    > **Araç Kutusundaki** **İletişim Grubu,** dosyaları açmak ve kaydetmek, klasörlere göz atmak ve yazı tiplerini ve renkleri seçmek için kullanılabilecek birçok yararlı iletişim kutusu açan bileşenlere sahiptir. Bu projede iki iletişim bileşeni kullanırsınız: OpenFileDialog ve ColorDialog.

1. Formunuza **openFileDialog1** adlı bir bileşen eklemek için **OpenFileDialoglog'u**çift tıklatın. Formunuza **colorDialog1** adlı bir bileşen eklemek **için, Toolbox'ta** **ColorDialog'u** çift tıklatın. (Bir sonraki öğretici adımda bunu kullanın.) Aşağıdaki resimde gösterildiği gibi, eklediğiniz iki iletişim bileşeninin her biri için simgesi olan **Windows Forms Designer'ın** **(Resim Görüntüleyen** formu altında) altında bir alan görmeniz gerekir.

     ![İletişim bileşenleri](../ide/media/express_dialogsadded.png)<br>***İletişim*** *bileşenleri*

1. **Windows Forms Designer'ın**altındaki alandaki **openFileDialog1** simgesini seçin. İki özellik ayarlayın:

    - **Filtre** özelliğini aşağıdaki lere ayarlayın (kopyalayıp yapıştırabilirsiniz):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - **Başlık** özelliğini aşağıdakilere ayarlama: **Resimli dosya seçin**

         **Filtre** özelliği ayarları, **resimli** dosya seç iletişim kutusunda görüntülenecek dosya türlerini belirtir.

    > [!TIP]
    > Farklı bir uygulamada **Dosya Aç** iletişim kutusunun bir örneğini görmek için **Not Defteri** veya **Paint'i**açın ve menü çubuğunda **Dosya** > **Aç'ı**seçin. Dosya adının yanında dosya türünü seçmenize olanak tanıyan bir açılır listenin nasıl olduğuna dikkat edin. <br/><br/>Uygulamanızda bunu ayarlamak için **OpenFileDialog** bileşenindeki **Filtre** özelliğini kullandınız. Ayrıca, **Özellikler** penceresinde **Başlık** ve **Filtre** özelliklerinin nasıl kalın olduğuna dikkat edin. IDE bunu, varsayılan değerlerinden değiştirilen özellikleri göstermek için yapar.

## <a name="next-steps"></a>Sonraki adımlar

* Bir sonraki öğretici adıma gitmek için **[bkz: Adım 8: Resim düğmesi olay işleyicisi için kod yazın.](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)**

* Önceki öğretici adıma dönmek için [bkz.](../ide/step-6-name-your-button-controls.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlanmış matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [öğretici 3: eşleşen bir oyun oluşturma](tutorial-3-create-a-matching-game.md)
