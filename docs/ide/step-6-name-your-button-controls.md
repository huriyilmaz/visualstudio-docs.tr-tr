---
title: 'Adım 6: Düğme denetimlerinizi adlandırın'
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579800"
---
# <a name="step-6-name-your-button-controls"></a>Adım 6: Düğme denetimlerinizi adlandırın

Formunda sadece <xref:System.Windows.Forms.PictureBox> bir tane var. Eklediğinizde, IDE otomatik olarak **pictureBox1**adını verdi. Yalnızca bir tane <xref:System.Windows.Forms.CheckBox>var, adı **checkBox1.** Yakında, bazı kod yazacaksınız ve bu kod Onay Kutusu ve PictureBox'a başvurulacak. Bu denetimlerin her birinde yalnızca bir tane olduğundan, kodunuzda **pictureBox1** veya **checkBox1'i** gördüğünüzde bunun ne anlama geldiğini anlarsınız.

> [!TIP]
> Visual Basic'te, herhangi bir denetim adının varsayılan ilk harfi ilk harftir, bu nedenle adlar **PictureBox1**, **CheckBox1**, ve benzeridir.

Formunuzda dört düğme vardır ve IDE onlara **button1,** **button2**, **button3**ve **button4**adını verdi. Geçerli adlarına bakarak, hangi düğmenin **Kapat** düğmesi, hangisinin **resim göster** düğmesi olduğunu bilemezsin. Bu nedenle düğme denetimlerinize daha bilgilendirici adlar vermek yararlıdır.

## <a name="to-name-your-button-controls"></a>Düğme denetimlerinizi adlandırmak için

1. Formda **Kapat** düğmesini seçin. (Tüm düğmeler hala seçiliyse, seçimi iptal etmek için **Esc** tuşunu seçin.) **(Ad)** özelliğini görene kadar **Özellikler** penceresinde ilerleyin. **(((Ad)** özelliği, özellikler alfabetik olduğunda en üste yakındır.) Aşağıdaki ekran görüntüsünde gösterildiği gibi, adı **kapatmak Düğmesi**olarak değiştirin.

    ![closeButton adı olan özellikler penceresi](../ide/media/express_setnameproperty.png)<br>***closeButton*** *adı* olan ***özellikler*** *penceresi*

    > [!NOTE]
    > "Kapat" ve "Düğme" sözcükleri arasında bir boşluk olan **Düğme'yi kapatmak**için düğmenizin adını değiştirmeyi deneyin. Bunu yaptığınızda, IDE bir hata iletisi görüntüler: "Özellik değeri geçerli değildir." Denetim adlarında boşluklara (ve birkaç karaktere) izin verilmez.

1. Diğer üç düğmeyi arka plana yeniden **adlandırDüğmesi,** **clearButton**ve **showButton'** a yeniden adlandırın.
**Özellikler** penceresinde denetim seçici açılır listesini seçerek adları doğrulayabilirsiniz. Yeni düğme adları görüntülenir.

1. Formdaki **resim göster** düğmesini çift tıklatın. Alternatif olarak, formdaki **resim göster** düğmesini seçin ve ardından **Enter** tuşuna basın. Bunu yaptığınızda, IDE ana pencerede **Form1.cs**adlı ek bir sekme açar. (Visual Basic kullanıyorsanız, sekme **Form1.vb**olarak adlandırılır).

   Bu sekme, aşağıdaki ekran görüntüsünde gösterildiği gibi formun arkasındaki kod dosyasını görüntüler.

    ![Visual C&#35; koduile Form1.cs sekmesi](../ide/media/express_showbuttoncode.png)<br>
***Form1.cs*** *C# kodu ile* Form1.cs sekmesi

    > [!NOTE]
    > Form1.cs veya Form1.vb sekmeniz **showButton'u** **ShowButton** olarak görüntüleyebilir.

1. Kodun bu kısmına odaklanın.

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

   Kod adlı `showButton_Click()` bakıyoruz (alternatif olarak, `ShowButton_Click()`). **ShowButton** düğmesinin kod dosyasını açtığınızda IDE bunu formun koduna ekledi. Tasarım zamanında, bir formdaki denetim için kod dosyasını açtığınızda, zaten yoksa denetim için kod oluşturulur. *Yöntem*olarak bilinen bu kod, uygulamanızı çalıştırdığınızda ve denetimi seçtiğinizde çalışır - bu durumda resim **göster** düğmesi.

1. Windows **Forms Designer** sekmesini yeniden seçin **(Form1.cs [Tasarım]** sekmesini seçin ve ardından formun kodunda bunun için bir yöntem oluşturmak için **resmi temizle** düğmesinin kod dosyasını açın. Kalan iki düğme için bunu tekrarlayın. Her seferinde, IDE formun kod dosyasına yeni bir yöntem ekler.

1. Bir yöntem daha eklemek için, IDE'nin bir `checkBox1_CheckedChanged()` yöntem eklemesini sağlamak için Windows Forms **Designer'da** **CheckBox** denetimiiçin kod dosyasını açın. Bu yöntem, kullanıcı onay kutusunu seçtiğinde veya temizlediğinde çağrılır.

   > [!TIP]
   > Bir uygulama üzerinde çalışırken, genellikle kod düzenleyicisi ve **Windows Forms Designer**arasında hareket. IDE, projenizde gezinmeyi kolaylaştırır. **Windows Forms Designer'ı** C# veya *Form1.vb'de* Visual Basic'te veya menü çubuğunda *Form1.cs* çift tıklayarak açmak için **Solution Explorer'ı** kullanın, **Tasarımcıyı Görüntüle'yi** > **Designer**seçin.

    Aşağıda kod düzenleyicisinde gördüğünüz yeni kod gösterilmektedir.

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    > [!NOTE]
    > Kodunuz olay işleyicilerini "camelCase" harflerinde görüntülemeyebilir.

    Eklediğiniz beş *yöntemolay işleyicileri*olarak adlandırılır, çünkü uygulamanız bir olay olduğunda (bir kullanıcı bir düğme seçerek veya kutu seçmek gibi) bunları çağırır.

    Tasarım zamanında IDE'de bir denetim kodunu görüntülediğinizde, Visual Studio denetim için bir olay işleyicisi yöntemi ekler. Örneğin, bir düğmeyi çift tıklattığınızda, IDE <xref:System.Windows.Forms.Control.Click> olayı için bir olay işleyicisi ekler (kullanıcı düğmeyi seçtiğinde çağrılır). Bir onay kutusunu çift tıklattığınızda, IDE <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayı için bir olay işleyicisi ekler (kullanıcı kutuyu seçtiğinde veya temizlediğinde çağrılır).

    Denetim için bir olay işleyicisi ekledikten sonra, denetimi çift tıklatarak veya menü çubuğunda **Görünüm** > **Kodu'nu**seçerek istediğiniz zaman **Windows Forms Designer'dan** geri dönebilirsiniz.

    Programlar oluştururken adlar önemlidir ve yöntemler (olay işleyicileri dahil) istediğiniz herhangi bir ada sahip olabilir. IDE ile bir olay işleyicisi eklediğinizde, denetimin adını ve işlenen olayı temel alan bir ad oluşturur.

    Örneğin, **showButton** adlı bir düğme için Click `showButton_Click()` olayı (alternatif olarak) `ShowButton_Click()`olay işleyicisi yöntemi olarak adlandırılır. Ayrıca, açılış ve kapanış `()` parantez genellikle yöntemleri tartışıldı olduğunu belirtmek için yöntem adı sonra eklenir.

    Bir kod değişken adını değiştirmek istediğinize karar verirseniz, koddaki değişkeni sağ tıklatın ve ardından Yeniden > **Düzenleme'yi**seçin. **Refactor** Koddaki bu değişkenin tüm örnekleri yeniden adlandırılır. Daha fazla bilgi için yeniden [adlandırma'ya](../ide/reference/rename.md)bakın.

## <a name="next-steps"></a>Sonraki adımlar

* Bir sonraki öğretici adıma gitmek için **[bkz: Adım 7: Formunuza iletişim bileşenleri ekleyin.](../ide/step-7-add-dialog-components-to-your-form.md)**

* Önceki öğretici adıma dönmek için [bkz: Adım 5: Formunuza denetimler ekleyin.](../ide/step-5-add-controls-to-your-form.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlanmış matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [öğretici 3: eşleşen bir oyun oluşturma](tutorial-3-create-a-matching-game.md)
