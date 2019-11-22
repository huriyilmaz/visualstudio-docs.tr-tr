---
title: '7\. Adım: formunuza Iletişim kutusu bileşenleri ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f734c818265d32f6895c09ab01fd2468e0f5a247
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295690"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>7\. Adım: Formunuza İletişim Kutusu Bileşenleri Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programınızın resim dosyalarını açmasını ve bir arka plan rengi seçmesini etkinleştirmek için, bu adımda formunuza bir **OpenFileDialog** bileşeni ve bir **ColorDialog** bileşeni eklersiniz.

 Bir bileşen, bazı yollarla denetim gibidir. Formunuza bir bileşen eklemek için araç kutusunu kullanın ve **Özellikler penceresini kullanarak özelliklerini ayarlarsınız** . Ancak, bir denetimin aksine formunuza bir bileşen eklemek, kullanıcının formda görebileceği görünür bir öğe eklemez. Bunun yerine, kodla tetikleyebileceğiniz belirli davranışları sağlar. Bu, bir **Dosya Aç** iletişim kutusu açan bir bileşendir.

 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz [. öğretici 1: Visual Basic resim görüntüleyici oluşturma-video 3](https://go.microsoft.com/fwlink/?LinkId=205213) veya [öğretici 1: video 3 ' te C# resim görüntüleyici oluşturma](https://go.microsoft.com/fwlink/?LinkId=205202). Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır.

### <a name="to-add-dialog-components-to-your-form"></a>Formunuza iletişim kutusu bileşenleri eklemek için

1. Windows Form Tasarımcısı (Form1.cs [Design] veya Form1. vb [Design]) seçin ve ardından araç kutusunda **Iletişim** kutusu grubunu açın.

    > [!NOTE]
    > Araç kutusundaki **Iletişim** kutusu grubunda, sizin için birçok yararlı iletişim kutusu açan bileşenler bulunur. Bu, dosyaları açmak ve kaydetmek, klasörlere gözatmak ve yazı tipi ve renkler seçmek için kullanılabilir. Bu projede iki iletişim kutusu bileşeni kullanıyorsunuz: **OpenFileDialog** ve **ColorDialog**.

2. Formunuza **OpenFileDialog1** adlı bir bileşen eklemek Için, **OpenFileDialog**öğesine çift tıklayın. Formunuza **colorDialog1** adlı bir bileşen eklemek Için araç kutusunda **ColorDialog** ' a çift tıklayın. (Bunu bir sonraki öğretici adımında kullanırsınız.) Aşağıdaki resimde gösterildiği gibi, eklediğiniz iki iletişim kutusu bileşeninin bir simgesine sahip Windows Form Tasarımcısı (resim Görüntüleyicisi formunun altında) altında bir alanı görmeniz gerekir.

     ![Iletişim kutusu bileşenleri](../ide/media/express-dialogsadded.png "Express_DialogsAdded") İletişim kutusu bileşenleri

3. Windows Form Tasarımcısı altındaki alanda bulunan **OpenFileDialog1** simgesini seçin. İki özellik ayarlayın:

    - **Filter** özelliğini aşağıdaki gibi ayarlayın (kopyalayabilir ve yapıştırabilirsiniz):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - **Title** özelliğini şu şekilde ayarlayın: **bir resim dosyası seçin**

         **Filtre** özelliği ayarları, **resim dosyası seç** iletişim kutusunda görünecek dosya türü türlerini belirtir.

    > [!NOTE]
    > Farklı bir uygulamadaki **Dosya Aç** iletişim kutusunun bir örneğini görmek Için, Not defteri veya Paint ' i açın ve menü çubuğunda **Dosya**, **Aç**' ı seçin. En altta bulunan bir **dosya türü** aşağı açılan listesi hakkında dikkat edin. Bunu ayarlamak için **OpenFileDialog** bileşeninde **Filter** özelliğini kullandınız. Ayrıca, **başlık** ve **filtre** özelliklerinin **Özellikler** penceresinde nasıl kalın olduğuna dikkat edin. IDE, varsayılan değerlerinden değiştirilmiş olan özellikleri göstermek için bunu yapar.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. [8. Adım: resim göster düğmesi olay işleyicisi Için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

- Önceki öğretici adımına dönmek için bkz. 6. [Adım: düğme denetimlerinizi adlandırma](../ide/step-6-name-your-button-controls.md).
