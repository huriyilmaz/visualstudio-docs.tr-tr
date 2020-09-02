---
title: '6. Adım: Düğme denetimlerinizi adlandırma'
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
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
ms.openlocfilehash: a5c23f48e803665e00155d1b546ace4e4ec7bc54
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77579800"
---
# <a name="step-6-name-your-button-controls"></a>6. Adım: Düğme denetimlerinizi adlandırma

Formunuz üzerinde yalnızca bir tane vardır <xref:System.Windows.Forms.PictureBox> . Bunu eklediğinizde, IDE otomatik olarak **PictureBox1**olarak adlandırılır. Yalnızca <xref:System.Windows.Forms.CheckBox> **CheckBox1**adlı bir tane vardır. Yakında bazı kodlar yazacaksınız ve bu kod CheckBox ve PictureBox 'a başvuracaktır. Bu denetimlerden yalnızca biri olduğundan, kodunuzda **PictureBox1** veya **CheckBox1** gördüğünüz zaman ne anlama geldiğini bilirsiniz.

> [!TIP]
> Visual Basic, herhangi bir denetim adının varsayılan ilk harfi ilk tepdir, bu nedenle adlar **PictureBox1**, **CheckBox1**vb. olur.

Formunuzda dört düğme vardır ve bunları **button1**, **button2**, **BUTTON3**ve **Button4**olarak adlandırılan IDE. Yalnızca geçerli adlarına bakarak, hangi düğmenin **kapatma** düğmesi olduğunu ve hangilerinin **resim göster** düğmesi olduğunu bilemezsiniz. Bu nedenle, düğme denetimlerinizi daha bilgilendirici adlar yararlı olur.

## <a name="to-name-your-button-controls"></a>Düğme denetimlerinizi adlandırmak için

1. Formda, **Kapat** düğmesini seçin. (Tüm düğmeler seçiliyse, seçimi iptal etmek için **ESC** tuşunu seçin.) **(Ad)** özelliğini görene kadar **Özellikler** penceresinde kaydırma yapın. ( **(Ad)** özelliği, Özellikler alfabetik olduğunda üst kısımdaki bir yakındır.) Aşağıdaki ekran görüntüsünde gösterildiği gibi, adı **CloseButton**olarak değiştirin.

    ![CloseButton adıyla Özellikler penceresi](../ide/media/express_setnameproperty.png)<br>***CloseButton*** *adıyla* ***Özellikler*** *penceresi*

    > [!NOTE]
    > Düğme adını "Close" ve "Button" kelimeleri arasında bir boşluk olacak şekilde **Kapat düğmesine**değiştirmeyi deneyin. Bunu yaptığınızda, IDE bir hata iletisi görüntüler: "özellik değeri geçerli değil." Denetim adlarında boşluklara (ve diğer birkaç karaktere) izin verilmez.

1. Diğer üç düğmeyi **backgroundButton**, **clearButton**ve **showButton**olarak yeniden adlandırın.
**Özellikler** penceresinde denetim Seçicisi açılan listesini seçerek adları doğrulayabilirsiniz. Yeni düğme adları görüntülenir.

1. Formdaki **resim göster** düğmesine çift tıklayın. Alternatif olarak, formda **bir resim göster** düğmesini seçin ve **ENTER** tuşuna basın. Bunu yaptığınızda IDE, **Form1.cs**adlı ana pencerede ek bir sekme açar. (Visual Basic kullanıyorsanız, sekme **Form1. vb**olarak adlandırılır).

   Bu sekme, aşağıdaki ekran görüntüsünde gösterildiği gibi, formun arkasındaki kod dosyasını görüntüler.

    ![Visual C&#35; Code ile Form1.cs sekmesi](../ide/media/express_showbuttoncode.png)<br>
***Form1.cs*** *C# kodu ile Form1.cs sekmesi*

    > [!NOTE]
    > Form1.cs veya Form1. vb sekmesinizdeki **showButton** **yerine showButton görüntülenebilir** .

1. Kodun bu bölümüne odaklanın.

    ```csharp
        private void ShowButton_Click(object sender, EventArgs e)
    {
    }
    ```

    ```vb
        Private Sub showButton_Click() Handles showButton.Click

    End Sub
    ```

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   Adlandırılan koda bakıyorsunuz `showButton_Click()` (alternatif olarak, `ShowButton_Click()` ). IDE bunu, **showButton** düğmesi için kod dosyasını açtığınızda formun koduna eklemiştir. Tasarım zamanında, bir formdaki denetim için kod dosyasını açtığınızda, zaten mevcut değilse denetim için kod oluşturulur. *Yöntem*olarak bilinen bu kod, uygulamanızı çalıştırdığınızda çalışır ve bu durumda **bir resim göster** düğmesi.

1. **Windows Form Tasarımcısı** sekmesini yeniden seçin (**Form1.cs [Design]**) ve ardından formun kodunda bir yöntem oluşturmak için **Resmi Temizle** düğmesine ait kod dosyasını açın. Bunu kalan iki düğme için tekrarlayın. Her seferinde IDE, formun kod dosyasına yeni bir yöntem ekler.

1. Bir yöntemi daha eklemek için, IDE 'nin bir yöntem eklemesini sağlamak üzere **Windows form tasarımcısı** **onay kutusu** denetimi için kod dosyasını açın `checkBox1_CheckedChanged()` . Bu yöntem, Kullanıcı onay kutusunu seçtiğinde veya temizlediğinde çağrılır.

   > [!TIP]
   > Uygulama üzerinde çalışırken genellikle kod Düzenleyicisi ve **Windows Form Tasarımcısı**arasında geçiş yapabilirsiniz. IDE, projenizde gezinmeyi kolaylaştırır. **Windows Form Tasarımcısı** açmak için **Çözüm Gezgini** kullanın Visual Basic C# veya *Form1. vb* içindeki *Form1.cs* çift tıklayarak ya da menü çubuğunda, **Görünüm**  >  **Tasarımcısı**' nı seçin.

    Aşağıdaki kod düzenleyicisinde gördüğünüz yeni kodu gösterir.

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    > [!NOTE]
    > Kodunuz, "camelCase" harflerine olay işleyicilerini görüntülemeyebilir.

    Eklediğiniz beş yönteme olay *işleyicileri*denir, çünkü uygulamanız her bir olay (bir düğme seçme veya bir kutu seçtiğinizde) olur.

    Tasarım zamanında IDE 'deki bir denetimin kodunu görüntülediğinizde, Visual Studio bir tane değilse denetim için bir olay işleyici yöntemi ekler. Örneğin, bir düğmeye çift tıkladığınızda IDE, olayı için bir olay işleyicisi ekler <xref:System.Windows.Forms.Control.Click> (Kullanıcı düğmeyi seçtiğinde çağrılır). Bir onay kutusunu çift tıklattığınızda, IDE, olayı için bir olay işleyicisi ekler <xref:System.Windows.Forms.CheckBox.CheckedChanged> (Kullanıcı kutuyu seçtiğinde veya temizlediğinde çağrılır).

    Bir denetim için bir olay işleyicisi ekledikten sonra, denetime çift tıklayarak veya menü çubuğunda kodu **görüntüle**' yi seçerek **Windows Form Tasarımcısı** istediğiniz zaman buna dönebilirsiniz  >  **Code**.

    Programlar oluştururken adlar önemlidir ve Yöntemler (olay işleyicileri dahil) istediğiniz herhangi bir ada sahip olabilir. IDE ile bir olay işleyicisi eklediğinizde, denetimin adına ve işlenmekte olan olaya göre bir ad oluşturur.

    Örneğin, **showButton** adlı bir düğmenin Click olayına `showButton_Click()` (alternatif olarak `ShowButton_Click()` ) olay işleyicisi yöntemi denir. Ayrıca, yöntemlerin açıklanmakta olduğunu göstermek için, açma ve kapatma parantezleri `()` genellikle yöntem adından sonra eklenir.

    Kod değişkeni adını değiştirmek istediğinize karar verirseniz, koddaki değişkene sağ tıklayıp yeniden **Düzenle**' yi seçin  >  **Rename**. Koddaki bu değişkenin tüm örnekleri yeniden adlandırılır. Daha fazla bilgi için [yeniden düzenlemeyi yeniden adlandırma](../ide/reference/rename.md)bölümüne bakın.

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına geçmek için, bkz. **[7. Adım: formunuza iletişim kutusu bileşenleri ekleme](../ide/step-7-add-dialog-components-to-your-form.md)**.

* Önceki öğretici adımına dönmek için bkz. 5. [Adım: Formunuza denetim ekleme](../ide/step-5-add-controls-to-your-form.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
