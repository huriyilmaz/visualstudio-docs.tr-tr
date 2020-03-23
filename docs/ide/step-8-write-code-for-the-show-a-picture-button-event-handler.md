---
title: 'Adım 8: Resim düğmesi olay işleyicisi için kod yazma'
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579812"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Adım 8: Resim düğmesi olay işleyicisi için kod yazma

Bu adımda, **Resim Göster** düğmesini aşağıdaki gibi çalıştırın:

- Bir kullanıcı bu düğmeyi seçtiğinde, <xref:System.Windows.Forms.OpenFileDialog> uygulama bir kutu açar.

- Bir kullanıcı bir resim dosyası açarsa, <xref:System.Windows.Forms.PictureBox>uygulama bu resmi .

IDE kod yazmanıza yardımcı olan IntelliSense adında güçlü bir araca sahiptir. Kod yazarken, IDE girdiğiniz kısmi sözcükler için önerilen tamamlamaları içeren bir kutu açar.

IntelliSense bir sonraki adımda ne yapmak istediğinizi belirlemeye çalışır ve otomatik olarak listeden seçtiğiniz son öğeye atlar. Listede taşımak için yukarı veya aşağı okları kullanabilir veya seçenekleri daraltmak için harfler yazmaya devam edebilirsiniz. İstediğiniz seçimi gördüğünüzde, seçmek için **Sekme** anahtarını seçin. Veya gerekli değilse önerileri yoksayabilirsiniz.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Resim düğmesi olay işleyicisi için kod yazmak için

1. Windows **Forms Designer'a** gidin ve **resim göster** düğmesini çift tıklatın. IDE hemen kod tasarımcısına gider ve imlecinizi daha önce `showButton_Click()` eklediğiniz `ShowButton_Click()`(alternatif olarak) yöntemin içinde olacak şekilde hareket ettirir.

1. İki `i` ayraç arasındaki boş çizgiye `{ }`bir tane yazın. (Visual Basic'te, boşluk arasındaki `Private Sub...` `End Sub`boş satıra yazın.) Aşağıdaki resimde gösterildiği gibi Bir **IntelliSense** penceresi açılır.

    ![Görsel C&#35; kodu ile IntelliSense](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > Kodunuz olay işleyicilerini "camelCase" harflerinde görüntülemeyebilir.

1. **IntelliSense** penceresi sözcüğü `if`vurgulamalıdır. (Değilse, bir küçük `f`harf girin ve o olacaktır.) **IntelliSense** penceresinin yanındaki *araç ipucu* kutusunun açıklamayla nasıl göründüğüne dikkat edin, **if deyimi için Kod parçacığı.** (Visual Basic'te, araç ipucu bunun bir parçacık olduğunu, ancak biraz farklı ifadeler le birlikte olduğunu belirtir.) Bu parçacığı kullanmak istiyorsanız, bu nedenle kodunuza eklemek `if` için **Sekme** anahtarını seçin. Ardından, snippet'i kullanmak için Sekme tuşunu yeniden seçin. **Tab** `if` (Başka bir yeri seçtiyseniz ve **IntelliSense** pencereniz `i` kaybolduysa, arka boşluğu n için ilerler ve yeniden yazarsanız, **IntelliSense** penceresi yeniden açılır.)

    ![Görsel C&#35; kodu](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Daha fazla kod girmek için IntelliSense'i kullanın

Ardından, **Dosya Aç** iletişim kutusunu açmak için daha fazla kod girmek için IntelliSense'i kullanırsınız. Kullanıcı **Tamam** düğmesini seçerse, PictureBox kullanıcının seçtiği dosyayı yükler. Aşağıdaki adımlar kodun nasıl girilen gösteriş ve birçok adım olmasına rağmen, bu sadece birkaç tuş vuruşu' s:

 1. Seçili metin snippet **doğru** ile başlayın. Üzerine `op` yazmak için yazın. (Visual Basic'te, bir başlangıç kapağıyla `Op`başlarsınız, bu nedenle yazın.)

 1. **IntelliSense** penceresi açılır ve **openFileDialog1**görüntüler. Seçmek için **Sekme** tuşunu seçin. (Visual Basic'te, bir başlangıç kapağıyla başlar, böylece **OpenFileDialog1'i**görürsünüz. **OpenFileDialog1'in** seçildiğinden emin olun.)

     Hakkında `OpenFileDialog`daha fazla bilgi edinmek için [OpenFileDialog'a](<xref:System.Windows.Forms.OpenFileDialog>)bakın.

 1. Bir dönem`.`yazın ( ) (Birçok programcı buna nokta der.) **OpenFileDialog1'den**hemen sonra bir nokta yazdığınız için, **OpenFileDialog** bileşeninin tüm özellikleri ve yöntemleriyle doldurulmuş bir **IntelliSense** penceresi açılır. Bunlar, **Windows Forms Designer'da**seçtiğinizde **Özellikler** penceresinde görünen özelliklerle aynıdır. Bileşene bir şeyler yapmasını söyleyen yöntemler de seçebilirsiniz (iletişim kutusunu açmak gibi).

    > [!NOTE]
    > **IntelliSense** penceresi size hem özellikleri hem de yöntemleri gösterebilir. Gösterilenleri belirlemek için, **IntelliSense** penceresindeki her öğenin sol tarafındaki simgeye bakın. Her yöntemin yanında bir blok görüntüsü ve her özelliğin yanında bir anahtar (veya anahtar) görüntüsü görürsünüz. Ayrıca her olayın yanında bir şimşek simgesi vardır. <br><br>Görünen simgeler şunlardır:<br><br>![Yöntem simgesi](../ide/media/express_iconmethod.png)<br>![Özellik simgesi](../ide/media/express_iconproperty.png)<br>![Olay simgesi](../ide/media/express_iconevent.png)

 1. Yazmaya `ShowDialog` başlayın (büyük harf IntelliSense için önemsizdir). Yöntem, `ShowDialog()` **Dosyayı Aç** iletişim kutusunu gösterir. Pencere **ShowDialog'u**vurguladıktan sonra **Sekme** anahtarını seçin. Ayrıca "ShowDialog"u vurgulayabilir ve yardım almak için **F1** tuşunu seçebilirsiniz.

    Yöntem hakkında daha `ShowDialog()` fazla bilgi edinmek için [ShowDialog Yöntemi'ne](<xref:System.Windows.Forms.Form.ShowDialog%2A>)bakın.

 1. Bir denetim veya bileşen üzerinde bir yöntem kullandığınızda *(yöntem çağırma*olarak adlandırılır), parantez eklemeniz gerekir. Yani hemen sonra açılış ve kapanış parantez girin `ShowDialog` `()` "g" içinde: Şimdi "openFileDialog1.ShowDialog()" gibi görünmelidir.

    > [!NOTE]
    > Yöntemler herhangi bir uygulamanın önemli bir parçasıdır ve bu öğretici yöntemleri kullanmak için çeşitli yollar göstermiştir. **OpenFileDialog** bileşeninin `ShowDialog()` yöntemini nasıl adlandırdığınız gibi bir şey yapmasını söylemek için bir bileşenin yöntemini arayabilirsiniz. Uygulamanızın şu anda oluşturduğunuz yöntem gibi, bir iletişim kutusunu ve `showButton_Click()` bir kullanıcı bir düğme yi seçtiğinde bir resim açan yöntem gibi bir şeyler yapmasını sağlamak için kendi yöntemlerinizi oluşturabilirsiniz.

 1. C# için bir boşluk ekleyin ve sonra`==`iki eşit işaret ekleyin ( ). Visual Basic için bir boşluk ekleyin ve ardından`=`tek bir eşit işareti kullanın ( ). (C# ve Visual Basic farklı eşitlik işleçleri kullanır.)

 1. Başka bir alan ekleyin. Bunu yapar yapmaz, başka bir **IntelliSense** penceresi açılır. Yazmaya `DialogResult` başlayın ve eklemek için **Sekme** anahtarını seçin.

    > [!NOTE]
    > Bir yöntemi çağırmak için kod yazdığınızda, bazen bir değer döndürür. Bu durumda, **OpenFileDialog** bileşeninin <xref:System.Windows.Forms.CommonDialog.ShowDialog> yöntemi <xref:System.Windows.Forms.DialogResult> bir değer döndürür. DialogResult, iletişim kutusunda neler olduğunu size belirten özel bir değerdir. **OpenFileDialog** bileşeni, kullanıcının **Ok** veya **İptal'i** `ShowDialog()` seçmesine `DialogResult.OK` neden `DialogResult.Cancel`olabilir, bu nedenle yöntemi ya da .

 1. DialogResult değeri **IntelliSense** penceresini açmak için bir nokta yazın. Harfi `O` girin ve **Tamam**eklemek için **Sekme** tuşunu seçin.

    DialogResult hakkında daha fazla bilgi edinmek için [DialogResult'a](<xref:System.Windows.Forms.DialogResult>)bakın.

    > [!NOTE]
    > İlk kod satırı tamamlanmış olmalıdır. C# için aşağıdakilere benzer olmalıdır.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  Visual Basic için aşağıdaki ler olmalıdır.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Şimdi bir kod satırı daha ekle. Yazabilir (veya kopyalayıp yapıştırabilirsiniz), ancak eklemek için IntelliSense'i kullanmayı düşünün. IntelliSense'e ne kadar aşina ysanız, kendi kodunuzu o kadar hızlı yazabilirsiniz. Son `showButton_Click()` yönteminiz aşağıdaki koda benzer olmalıdır.

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>Sonraki adımlar

* Bir sonraki öğretici adıma gitmek için **[Bkz. Adım 9: Kodunuzu gözden geçirin, yorumyapın ve test edin.](../ide/step-9-review-comment-and-test-your-code.md)**

* Önceki öğretici adıma dönmek için [bkz: Adım 7: Formunuza iletişim bileşenleri ekleyin.](../ide/step-7-add-dialog-components-to-your-form.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlanmış matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [öğretici 3: eşleşen bir oyun oluşturma](tutorial-3-create-a-matching-game.md)
