---
title: '7\. Adım: formunuza Iletişim kutusu bileşenleri ekleme'
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 319cfee254aa0b0f1709fa566e4e1bbca208eb9a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589961"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>7\. Adım: formunuza iletişim kutusu bileşenleri ekleme

Uygulamanızın resim dosyalarını açmasını ve bir arka plan rengi seçmesini etkinleştirmek için, bu adımda formunuza bir <xref:System.Windows.Forms.OpenFileDialog> bileşeni ve bir <xref:System.Windows.Forms.ColorDialog> bileşeni eklersiniz.

Bir bileşen, bazı yollarla denetim gibidir. Formunuza bir bileşen eklemek için **araç kutusunu** kullanın ve **Özellikler penceresini kullanarak özelliklerini ayarlarsınız** . Ancak, bir denetimin aksine formunuza bir bileşen eklemek, kullanıcının formda görebileceği görünür bir öğe eklemez. Bunun yerine, kodla tetikleyebileceğiniz belirli davranışları sağlar. Bu, bir **Dosya Aç** iletişim kutusu açan bir bileşendir.

## <a name="to-add-dialog-components-to-your-form"></a>Formunuza iletişim kutusu bileşenleri eklemek için

1. **Windows Form Tasarımcısı** (**Form1.cs [Design]** ) öğesini seçin ve ardından **araç kutusundan** **iletişim** kutusu grubunu açın.

    > [!NOTE]
    > **Araç kutusundaki** **iletişim** kutusu grubunda, sizin için birçok yararlı iletişim kutusu açan bileşenler bulunur. Bu, dosyaları açmak ve kaydetmek, klasörlere gözatmak ve yazı tipi ve renkler seçmek için kullanılabilir. Bu projede iki iletişim kutusu bileşeni kullanıyorsunuz: OpenFileDialog ve ColorDialog.

1. Formunuza **OpenFileDialog1** adlı bir bileşen eklemek Için, **OpenFileDialog**öğesine çift tıklayın. Formunuza **colorDialog1** adlı bir bileşen eklemek Için **araç kutusunda** **ColorDialog** ' a çift tıklayın. (Bunu bir sonraki öğretici adımında kullanırsınız.) Aşağıdaki görüntüde gösterildiği gibi, eklediğiniz iki iletişim kutusu bileşeninin bir simgesine sahip **Windows Form Tasarımcısı** ( **Resim Görüntüleyicisi** formunun altında) altında bir alan görmeniz gerekir.

     ![Iletişim kutusu bileşenleri](../ide/media/express_dialogsadded.png)<br>***Iletişim kutusu*** *bileşenleri*

1. **Windows Form Tasarımcısı**altındaki alanda bulunan **OpenFileDialog1** simgesini seçin. İki özellik ayarlayın:

    - **Filter** özelliğini aşağıdaki gibi ayarlayın (kopyalayabilir ve yapıştırabilirsiniz):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - **Title** özelliğini şu şekilde ayarlayın: **bir resim dosyası seçin**

         **Filtre** özelliği ayarları, **resim dosyası seç** iletişim kutusunda görünecek dosya türü türlerini belirtir.

    > [!TIP]
    > Farklı bir uygulamadaki **Dosya Aç** iletişim kutusunun bir örneğini görmek Için, **Not defteri** veya **Paint**' i açın ve menü çubuğunda **Dosya** > **Aç**' ı seçin. Dosya adı ' nın yanında dosya türünü seçmenizi sağlayan bir açılan listenin yanında yer alan bir açılır liste olduğunu unutmayın. <br/><br/>Uygulamanızı ayarlamak için **OpenFileDialog** bileşenindeki **Filter** özelliğini kullandınız. Ayrıca, **başlık** ve **filtre** özelliklerinin **Özellikler** penceresinde nasıl kalın olduğuna dikkat edin. IDE, varsayılan değerlerinden değiştirilmiş olan özellikleri göstermek için bunu yapar.

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için bkz. **[8. Adım: resim göster düğmesi olay işleyicisi için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)** .

* Önceki öğretici adımına dönmek için bkz. 6. [Adım: düğme denetimlerinizi adlandırma](../ide/step-6-name-your-button-controls.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
