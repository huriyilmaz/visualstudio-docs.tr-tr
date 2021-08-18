---
title: Resim göster düğmesi olay işleyicisi için kod yazma
description: Resim görüntüleyici oluşturma öğreticisinde resim göster düğmesi olay işleyicisi için kod yazın.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
ms.topic: tutorial
dev_langs:
- CSharp
- VB
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 468ed364b6ee36c4ae4f015ca1db8e471eef4835
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040794"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>8. Adım: Resim göster düğmesi olay işleyicisi için kod yazma

Bu adımda Resim göster düğmesini **aşağıdaki gibi** çalışır hale gelirsiniz:

- Kullanıcı bu düğmeyi seçerken uygulama bir kutu <xref:System.Windows.Forms.OpenFileDialog> açar.

- Kullanıcı resim dosyası açarsa, uygulama bu resmi içinde <xref:System.Windows.Forms.PictureBox> gösterir.

IDE,kod yazmanıza yardımcı olan IntelliSense adlı güçlü bir araca sahip. Siz kod yazarak IDE, girebilirsiniz kısmi sözcükler için önerilen tamamlamaları olan bir kutu açar.

IntelliSense, bundan sonra yapmak istediğiniz şeyi belirlemeye çalışır ve otomatik olarak listeden seçtiğiniz son öğeye atlar. Listede hareket etmek için yukarı veya aşağı okları kullanabilir veya seçenekleri daraltmak için harf yazmaya devam edebilirsiniz. İstediğiniz seçimi gördüğünüzde Sekme **tuşuna** basın. Veya gerekirse önerileri yoksayabilirsiniz.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Resim göster düğmesi olay işleyicisi için kod yazmak için

1. Form **Windows'a** gidin ve Resim göster **düğmesine çift** tıklayın. IDE hemen kod tasarımcısına gider ve imlecinizi daha önce ekley istediğiniz (alternatif olarak `showButton_Click()` `ShowButton_Click()` ) yönteminin içinde olacak şekilde taşır.

1. İki `i` ayraç arasına boş satıra bir `{ }` yazın. (Visual Basic arasındaki boş satıra `Private Sub...` `End Sub` yazın.) Aşağıdaki görüntüde gösterildiği gibi bir **IntelliSense** penceresi açılır.

    ![Visual C ile IntelliSense&#35; kodu](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > Kodunuz olay işleyicilerini "camelCase" harfiyle görüntülemeyebilirsiniz.

1. **IntelliSense penceresinde** sözcüğü `if` vurgulanır. (Yoksa, küçük harfli bir `f` girin ve girer.) **IntelliSense** *penceresinin* yanında if deyimi için kod parçacığı açıklamasıyla birlikte bir araç ipucu kutusunun **göründüğüne dikkat edin.** (Visual Basic ipucu, bunun bir kod parçacığı olduğunu ancak biraz farklı ifadeyle birlikte olduğunu da ifade ediyor.) Bu kod parçacığını kullanmak istediğiniz için **kodunuza eklemek** istediğiniz Sekme `if` tuşuna basın. Ardından, kod **parçacığını** kullanmak için Sekme tuşuna `if` tekrar tıklayın. (Başka bir yerde seçim yaptıysanız **ve IntelliSense** pencereniz kayboldu, üzerine geri al ve yeniden yazarak `i` **IntelliSense** penceresi yeniden açılır.)

    ![Visual C&#35; kodu](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Daha fazla kod girmek için IntelliSense kullanma

Ardından IntelliSense'i kullanarak daha fazla kod girerek Dosya Aç **iletişim kutusunu** açabilirsiniz. Kullanıcı Tamam düğmesini **seçtiyse** PictureBox kullanıcının seçtiği dosyayı yükler. Aşağıdaki adımlarda kodun nasıl gir kurallarına sahip olduğu ve birçok adımın olduğu birkaç tuş vuruşu vardır:

 1. Kod parçacığında seçilen **true metniyle** başlama. Üzerine `op` yazmak için yazın. (Visual Basic baş harfle başlar, bu nedenle `Op` yazın.)

 1. **IntelliSense penceresi** açılır ve **openFileDialog1 görüntülenir.** Seçmek **için Sekme** tuşuna basın. (Visual Basic, başlangıç sınırıyla başlar, bu nedenle **OpenFileDialog1 ifadesinin olduğunu görüyorsunuz.** **OpenFileDialog1'in seçili olduğundan** emin olun.)

     hakkında daha fazla bilgi edinmek `OpenFileDialog` için bkz. [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

 1. Bir nokta ( `.` ) yazın (Çoğu programcı buna nokta adı verdi.) **openFileDialog1'den** hemen sonra bir nokta yazarak, **Tüm OpenFileDialog** bileşeninin özellikleri ve yöntemleriyle doldurulmuş bir **IntelliSense** penceresi açılır. Bunlar, Form Tasarımcısı'nda **seçtiğiniz** Özellikler penceresinde görünen **Windows özelliklerdir.** Ayrıca bileşene bir şeyler yapmalarını (örneğin bir iletişim kutusu açma) söyleme yöntemlerini de seçebilirsiniz.

    > [!NOTE]
    > **IntelliSense penceresi** hem özellikleri hem de yöntemleri gösterebilir. Gösterilenleri belirlemek için **IntelliSense** penceresindeki her bir öğenin sol tarafındaki simgeye bakın. Her yöntemin yanında bir bloğun ve her özelliğin yanında bir İngiliz anahtarı (veya spanner) resmi görüyorsunuz. Ayrıca her olayın yanında bir şimşek simgesi de vardır. <br><br>Görünen simgeler şu şekildedir:<br><br>![Yöntem simgesi](../ide/media/express_iconmethod.png)<br>![Özellik simgesi](../ide/media/express_iconproperty.png)<br>![Olay simgesi](../ide/media/express_iconevent.png)

 1. Türe başlama `ShowDialog` (büyük harfe yazma IntelliSense için önemli değildir). yöntemi, `ShowDialog()` Dosya Aç **iletişim** kutusunu gösterir. Pencere **ShowDialog'u vurguladikten** sonra **Sekme tuşuna** basın. Ayrıca "ShowDialog"u vurgulayın ve yardım almak için **F1** tuşuna basın.

    yöntemi hakkında daha fazla bilgi `ShowDialog()` edinmek için bkz. [ShowDialog Metodu.](<xref:System.Windows.Forms.Form.ShowDialog%2A>)

 1. Bir denetimde veya bileşende bir yöntem (yöntem çağırma olarak adlandırılır) kullanıyorsanız parantez eklemeniz gerekir. Bu nedenle içindeki "g" ifadesinin hemen ardından açma ve kapatma parantezlerini girin: Artık `ShowDialog` `()` "openFileDialog1.ShowDialog()" gibi görünüyor.

    > [!NOTE]
    > Yöntemler herhangi bir uygulamanın önemli bir parçasıdır ve bu öğreticide yöntemleri kullanmanın çeşitli yolları gösterilmiştir. **OpenFileDialog** bileşeninin yöntemini çağırma gibi bir şey yapmalarını söylemek için bir bileşenin yöntemini `ShowDialog()` çağırebilirsiniz. Uygulamanıza şu anda oluşturmakta olduğunuz yöntem gibi bir işlem yapmak için kendi yöntemlerinizi oluşturabilirsiniz. Bu yöntem, kullanıcı bir düğmeyi seçtiklerinden bir iletişim kutusu ve resim `showButton_Click()` açar.

 1. C# için bir boşluk ekleyin ve ardından iki eşittir işareti ( ) `==` ekleyin. Daha Visual Basic bir boşluk ekleyin ve ardından tek bir eşittir işareti () `=` kullanın. (C# ve Visual Basic eşitlik işleçleri kullanır.)

 1. Başka bir alan ekleyin. Bunu yapar yapmaz başka bir **IntelliSense penceresi** açılır. Yazın ve `DialogResult` Eklemek için **Sekme** tuşuna basın.

    > [!NOTE]
    > Bir yöntemi çağıracak kodu yazarak bazen bir değer döndürür. Bu durumda **OpenFileDialog bileşeninin** yöntemi <xref:System.Windows.Forms.CommonDialog.ShowDialog> bir değer <xref:System.Windows.Forms.DialogResult> döndürür. DialogResult, bir iletişim kutusunda neler olduğunu size anlatan özel bir değerdir. **OpenFileDialog** bileşeni kullanıcının Tamam veya  İptal'i seçmesi ile **sonuçlansa da** yöntemi `ShowDialog()` veya `DialogResult.OK` `DialogResult.Cancel` döndürür.

 1. DialogResult değeri **IntelliSense** penceresini açmak için bir nokta yazın. Harfi girin `O` ve **Tamam'ı eklemek için** Sekme tuşuna **basın.**

    DialogResult hakkında daha fazla bilgi edinmek için bkz. [DialogResult](<xref:System.Windows.Forms.DialogResult>).

    > [!NOTE]
    > İlk kod satırı tamamlanır. C# için aşağıdakine benzer olması gerekir.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  Bu Visual Basic için aşağıdaki gibi olması gerekir.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Şimdi bir kod satırı daha ekleyin. Bunu yazarak (veya kopyalayıp yapıştırarak) ancak eklemek için IntelliSense kullanmayı göz önünde bulundurarak. IntelliSense hakkında ne kadar çok bilginiz olursa, kendi kodunuzu o kadar hızlı yazabilirsiniz. Son `showButton_Click()` yönteminiz aşağıdaki koda benzer şekilde çalışmalı.

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step8/cs/form1.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step8/vb/form1.vb" id="Snippet1":::

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için **[bkz. 9. Adım:](../ide/step-9-review-comment-and-test-your-code.md)** Kodunuzu gözden geçirme, açıklama ve test edin.

* Önceki öğretici adımına dönmek için [bkz. 7. Adım: Formnize iletişim kutusu bileşenleri ekleme.](../ide/step-7-add-dialog-components-to-your-form.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlı matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: Eşleştirme oyunu oluşturma](tutorial-3-create-a-matching-game.md)
