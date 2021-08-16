---
title: '7. Adım: formunuza Iletişim kutusu bileşenleri ekleme'
description: <xref:System.Windows.Forms.OpenFileDialog>Formunuza bir iletişim kutusu bileşeni ve bir <xref:System.Windows.Forms.ColorDialog> iletişim kutusu bileşeni eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8f3282e019c1818c782a578a248a93871ec3926d295f1779f432c6bafecc8545
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121289159"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>7. Adım: Formunuza iletişim kutusu bileşenleri ekleme

Uygulamanızın resim dosyalarını açmasını ve bir arka plan rengi seçmesini etkinleştirmek için, bu adımda <xref:System.Windows.Forms.OpenFileDialog> formunuza bir bileşen ve <xref:System.Windows.Forms.ColorDialog> bileşen eklersiniz.

Bir bileşen, bazı yollarla denetim gibidir. Formunuza bir bileşen eklemek için **araç kutusunu** kullanın ve **Özellikler penceresini kullanarak özelliklerini ayarlarsınız** . Ancak, bir denetimin aksine formunuza bir bileşen eklemek, kullanıcının formda görebileceği görünür bir öğe eklemez. Bunun yerine, kodla tetikleyebileceğiniz belirli davranışları sağlar. Bu, bir **Dosya Aç** iletişim kutusu açan bir bileşendir.

## <a name="to-add-dialog-components-to-your-form"></a>Formunuza iletişim kutusu bileşenleri eklemek için

1. **Windows Form Tasarımcısı** (**Form1. cs [Design]**) öğesini seçin ve ardından **araç kutusundan** **iletişim** kutusu grubunu açın.

    > [!NOTE]
    > **Araç kutusundaki** **iletişim** kutusu grubunda, sizin için birçok yararlı iletişim kutusu açan bileşenler bulunur. Bu, dosyaları açmak ve kaydetmek, klasörlere gözatmak ve yazı tipi ve renkler seçmek için kullanılabilir. Bu projede iki iletişim kutusu bileşeni kullanıyorsunuz: OpenFileDialog ve ColorDialog.

1. Formunuza **OpenFileDialog1** adlı bir bileşen eklemek Için, **OpenFileDialog** öğesine çift tıklayın. Formunuza **colorDialog1** adlı bir bileşen eklemek Için **araç kutusunda** **ColorDialog** ' a çift tıklayın. (Bunu bir sonraki öğretici adımında kullanırsınız.) aşağıdaki görüntüde gösterildiği gibi, eklediğiniz iki iletişim kutusu bileşeninin bir simgesine sahip **Windows Form Tasarımcısı** ( **resim görüntüleyicisi** formunun altında) altında bir alan görmeniz gerekir.

     ![İletişim kutusu bileşenleri](../ide/media/express_dialogsadded.png)<br>***Iletişim kutusu** _ _components *

1. **Windows Form Tasarımcısı** altındaki alanda bulunan **openFileDialog1** simgesini seçin. İki özellik ayarlayın:

    - **Filter** özelliğini aşağıdaki gibi ayarlayın (kopyalayabilir ve yapıştırabilirsiniz):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - **Title** özelliğini şu şekilde ayarlayın: **bir resim dosyası seçin**

         **Filtre** özelliği ayarları, **resim dosyası seç** iletişim kutusunda görünecek dosya türü türlerini belirtir.

    > [!TIP]
    > farklı bir uygulamadaki **dosya aç** iletişim kutusunun bir örneğini görmek için **Not Defteri** veya **Paint** açın ve menü çubuğunda **dosya**  >  **aç**' ı seçin. Dosya adı ' nın yanında dosya türünü seçmenizi sağlayan bir açılan listenin yanında yer alan bir açılır liste olduğunu unutmayın. <br/><br/>Uygulamanızı ayarlamak için **OpenFileDialog** bileşenindeki **Filter** özelliğini kullandınız. Ayrıca, **başlık** ve **filtre** özelliklerinin **Özellikler** penceresinde nasıl kalın olduğuna dikkat edin. IDE, varsayılan değerlerinden değiştirilmiş olan özellikleri göstermek için bunu yapar.

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için bkz. **[8. Adım: resim göster düğmesi olay işleyicisi için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)**.

* Önceki öğretici adımına dönmek için bkz. 6. [Adım: düğme denetimlerinizi adlandırma](../ide/step-6-name-your-button-controls.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
