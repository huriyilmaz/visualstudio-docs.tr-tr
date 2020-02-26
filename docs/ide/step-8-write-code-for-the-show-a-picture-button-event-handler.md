---
title: '8\. Adım: resim göster düğmesi olay işleyicisi için kod yazma'
ms.date: 08/30/2019
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d74c9ecda0e3ab23c1f2ab1cb2180a60701c069a
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579812"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>8\. Adım: resim göster düğmesi olay işleyicisi için kod yazma

Bu adımda, **bir resim göster** düğmesini aşağıdaki gibi çalışır hale getirebilirsiniz:

- Kullanıcı bu düğmeyi seçtiğinde, uygulama bir <xref:System.Windows.Forms.OpenFileDialog> kutusunu açar.

- Bir Kullanıcı bir resim dosyası açarsa, uygulama bu resmi <xref:System.Windows.Forms.PictureBox>gösterir.

IDE 'de kod yazmanıza yardımcı olan, IntelliSense adlı güçlü bir araç vardır. Kod yazdığınızda, IDE girdiğiniz kısmi sözcüklerin önerilen tamamlarla bir kutu açar.

IntelliSense, daha sonra ne yapmak istediğinizi belirlemeyi dener ve listeden seçtiğiniz son öğeyi otomatik olarak atlar. Listede gezinmek için yukarı veya aşağı okları kullanabilir veya seçimleri daraltmak için harfleri yazmaya devam edebilirsiniz. İstediğiniz seçeneği gördüğünüzde, seçmek için **sekme** tuşunu seçin. Veya gerekmiyorsa, önerileri yoksayabilirsiniz.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Resim göster düğmesi olay işleyicisi için kod yazmak için

1. **Windows Form Tasarımcısı** gidin ve **resim göster** düğmesine çift tıklayın. IDE hemen kod tasarımcısına gider ve imlecinizi, daha önce eklediğiniz `showButton_Click()` (alternatif olarak `ShowButton_Click()`) yönteminin içine taşımaktır.

1. İki küme ayracı `{ }`arasındaki boş satıra bir `i` yazın. (Visual Basic `Private Sub...` ve `End Sub`arasında boş satıra yazın.) Aşağıdaki görüntüde gösterildiği gibi bir **IntelliSense** penceresi açılır.

    ![Visual C&#35; Code ile IntelliSense](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > Kodunuz, "camelCase" harflerine olay işleyicilerini görüntülemeyebilir.

1. **IntelliSense** penceresi `if`sözcük vurgulaması gerekir. (Yoksa, küçük bir `f`girin ve bu işlem olur.) **IntelliSense** penceresinin yanındaki bir *araç ipucu* kutusunun Açıklama, **If ifadesi için kod parçacığı**gibi göründüğünü fark edebilirsiniz. (Visual Basic araç ipucu, bunun bir parçacık olduğunu ancak biraz farklı bir ifade olduğunu da belirtir.) Bu kod parçacığını kullanmak istiyorsanız, kodunuza `if` eklemek için **sekme** tuşunu seçin. Sonra `if` parçacığı kullanmak için **Tab** tuşunu yeniden seçin. (Başka bir yerde tercih ederseniz **IntelliSense** penceresi kaybolduysa, `i` üzerine geri yazıp yeniden yazın ve **IntelliSense** penceresi tekrar açılır.)

    ![Visual C&#35; kodu](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Daha fazla kod girmek için IntelliSense kullanın

Daha sonra, bir **Dosya Aç** iletişim kutusunu açmak için daha fazla kod girmek üzere IntelliSense 'i kullanırsınız. Kullanıcı **Tamam** düğmesini seçerse, PictureBox kullanıcının seçtiği dosyayı yükler. Aşağıdaki adımlarda kodun nasıl girilmesi gösterilmektedir ve birçok adım olsa da yalnızca birkaç tuş vuruşu vardır:

 1. Kod parçacığında **doğru** seçili metinle başlayın. Üzerine yazmak için `op` yazın. (Visual Basic, ilk Cap ile başlayıp `Op`yazın.)

 1. **IntelliSense** penceresi açılır ve **OpenFileDialog1**görüntüler. Seçmek için **sekme** tuşunu seçin. (Visual Basic bir başlangıç üst sınırı ile başlar, bu nedenle **OpenFileDialog1**görürsünüz. **OpenFileDialog1** seçildiğinden emin olun.)

     `OpenFileDialog`hakkında daha fazla bilgi için bkz. [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

 1. Bir nokta (`.`) yazın (birçok programcı bu noktayı çağırır.) **OpenFileDialog1**sonrasında bir nokta yazdığınızdan, bir **IntelliSense** penceresi açılır ve tüm **OpenFileDialog** bileşeni özellikleri ve yöntemleri ile doldurulur. Bunlar, **Windows Form Tasarımcısı**' de seçerken **Özellikler** penceresinde görüntülenen özelliklerden aynıdır. Ayrıca, bileşene bir şeyler (bir iletişim kutusu aç gibi) yapacağını söyleyen yöntemler de seçebilirsiniz.

    > [!NOTE]
    > **IntelliSense** penceresi her iki özelliği ve yöntemi gösterebilir. Neyin gösterilmekte olduğunu belirlemek için, **IntelliSense** penceresindeki her öğenin sol tarafındaki simgeye bakın. Her yöntemin yanında bir bloğun görüntüsünü ve her bir özelliğin yanındaki bir wrana (ya da Spanner) görüntüsünü görürsünüz. Her olayın yanında bir şimşek simgesi de vardır. <br><br>Görüntülenen simgeler aşağıda verilmiştir:<br><br>![yöntemi simgesi](../ide/media/express_iconmethod.png)<br>![Özellik simgesi](../ide/media/express_iconproperty.png)<br>![olay simgesi](../ide/media/express_iconevent.png)

 1. `ShowDialog` yazın (büyük/küçük harfe dönüştürme, IntelliSense için önemli değildir). `ShowDialog()` yöntemi **Dosya Aç** iletişim kutusunu gösterecektir. Pencerede **ShowDialog**vurgulandıktan sonra **sekme** tuşunu seçin. Ayrıca, "ShowDialog" ifadesini vurgulayabilir ve yardım almak için **F1** tuşunu seçebilirsiniz.

    `ShowDialog()` yöntemi hakkında daha fazla bilgi edinmek için bkz. [ShowDialog yöntemi](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

 1. Bir denetim veya bileşen üzerinde bir yöntem kullandığınızda ( *bir yöntemi çağırmak*olarak adlandırılır), parantez eklemeniz gerekir. Bu nedenle, `ShowDialog`içinde "g" den hemen sonra açma ve kapatma parantezleri girin: `()` şimdi "openFileDialog1. ShowDialog ()" şeklinde görünmelidir.

    > [!NOTE]
    > Yöntemler, herhangi bir uygulamanın önemli bir parçasıdır ve bu öğretici, yöntemlerin kullanılması için çeşitli yollar göstermiştir. Bir bileşenin yöntemini çağırmak için, **OpenFileDialog** bileşenin `ShowDialog()` yöntemini nasıl adlandırmış olursunuz. Bir Kullanıcı bir düğme seçtiğinde bir iletişim kutusu ve resim açan `showButton_Click()` yöntemi olarak, uygulamanızın sizin oluşturduğunuz gibi işlemler yapmasını sağlamak için kendi yöntemlerinizi oluşturabilirsiniz.

 1. İçin C#, bir boşluk ekleyin ve ardından iki eşittir işareti (`==`) ekleyin. Visual Basic için bir boşluk ekleyin ve sonra tek bir eşittir işareti (`=`) kullanın. (C# ve Visual Basic farklı eşitlik işleçleri kullanın.)

 1. Başka bir boşluk ekleyin. Bunu yaptığınızda, başka bir **IntelliSense** penceresi açılır. `DialogResult` yazın ve eklemek için **sekme** tuşunu seçin.

    > [!NOTE]
    > Bir yöntemi çağırmak için kod yazdığınızda bazen bir değer döndürür. Bu durumda, **OpenFileDialog** bileşeninin <xref:System.Windows.Forms.CommonDialog.ShowDialog> yöntemi bir <xref:System.Windows.Forms.DialogResult> değeri döndürür. DialogResult, iletişim kutusunda ne olduğunu belirten özel bir değerdir. Bir **OpenFileDialog** bileşeni, kullanıcının **Tamam** veya **iptal**' i seçmelerini sağlayabilir, bu nedenle `ShowDialog()` yöntemi `DialogResult.OK` veya `DialogResult.Cancel`döndürür.

 1. DialogResult değeri **IntelliSense** penceresini açmak için bir nokta yazın. `O` harfini girin ve **Tamam 'ı**eklemek için **sekme** tuşunu seçin.

    DialogResult hakkında daha fazla bilgi edinmek için bkz. [DialogResult](<xref:System.Windows.Forms.DialogResult>).

    > [!NOTE]
    > Kodun ilk satırı tamamlanmalıdır. İçin C#, aşağıdakine benzer olmalıdır.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  Visual Basic için aşağıdaki olmalıdır.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Şimdi bir kod satırı ekleyin. Yazabilir (veya kopyalayabilir ve yapıştırabilirsiniz), ancak eklemek için IntelliSense kullanmayı düşünün. IntelliSense ile ne kadar tanıdık olduğunu öğrenin, kendi kodunuzu daha hızlı yazabilirsiniz. Son `showButton_Click()` yönteminiz aşağıdaki koda benzemelidir.

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için bkz. **[adım 9: İnceleme, yorum ve test kodunuzu test](../ide/step-9-review-comment-and-test-your-code.md)** etme.

* Önceki öğretici adımına dönmek için, bkz. [7. Adım: formunuza iletişim kutusu bileşenleri ekleme](../ide/step-7-add-dialog-components-to-your-form.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
