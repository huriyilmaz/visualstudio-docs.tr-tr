---
title: '6. Adım: Düğme denetimlerinizi adlandırma'
description: Düğme denetimlerinizi nasıl adlaydırabilirsiniz?
ms.custom: SEO-VS-2020
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
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
ms.openlocfilehash: e1214d5e640364e0a5cc256f3f78cbd17cc1acdb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094053"
---
# <a name="step-6-name-your-button-controls"></a>6. Adım: Düğme denetimlerinizi adlandırma

Form üzerinde yalnızca <xref:System.Windows.Forms.PictureBox> bir tane var. Bunu eklediğniz zaman, IDE otomatik olarak **pictureBox1 olarak adlandırılmıştır.** yalnızca bir tane vardır <xref:System.Windows.Forms.CheckBox> ve bu onay **kutusu1 olarak adlandırılmıştır.** Yakında bazı kodlar yazacak ve bu kod CheckBox ve PictureBox'a başvurur. Bu denetimlerden yalnızca biri olduğundan, kodunda **pictureBox1** veya **checkBox1'i** gördüğünüzde bunun ne anlama geldiğini bilirsiniz.

> [!TIP]
> Bu Visual Basic denetim adlarının varsayılan ilk harfi ilk harftir, dolayısıyla adlar **PictureBox1,** **CheckBox1** ve diğer adlardır.

Form üzerinde dört düğme vardır ve IDE bunları **button1**, **button2**, **button3** ve **button4 olarak adlandırılmıştır.** Yalnızca geçerli adlarına bakarak hangi düğmenin Kapat  düğmesinin, hangisinin ise Resim göster **düğmesinin hangisi olduğunu bilmiyor** olursınız. Bu nedenle düğme denetimlerinize daha bilgilendirici adlar vermek yararlı olur.

## <a name="to-name-your-button-controls"></a>Düğme denetimlerinizi ad olarak

1. Formda Kapat **düğmesini** seçin. (Tüm düğmeler seçiliyse, seçimi iptal etmek **için Esc** tuşuna basın.) (Ad) **özelliğini** görene kadar **Özellikler penceresinde kaydırın.** (Özellikler alfabetik olduğunda **(Name)** özelliği üst düzeye yakın.) Aşağıdaki ekran görüntüsünde gösterildiği gibi adı **closeButton** olarak değiştirebilirsiniz.

    ![Özellikler penceresi closeButton adı ile birlikte](../ide/media/express_setnameproperty.png)<br>***Özellikler** _ _penceresi* ***closeButton**_ _name*

    > [!NOTE]
    > Düğmenizin adını düğmeyi kapatacak **şekilde değiştirmeyi deneyin.** Bu, "close" (Kapat) ve "Button" (Düğme) sözcükleri arasında boşluk bırakın. Bunu yapmak için IDE şu hata iletisini görüntüler: "Özellik değeri geçerli değil." Denetim adlarında boşluklara (ve birkaç karaktere) izin verilmez.

1. Diğer üç düğmeyi **backgroundButton**, **clearButton** ve **showButton olarak yeniden adlandırabilirsiniz.**
Özellikler penceresinde denetim seçici açılan listesini seçerek adları **doğruabilirsiniz.** Yeni düğme adları görüntülenir.

1. Formda **Resim göster düğmesine** çift tıklayın. Alternatif olarak formda **Resim göster düğmesini** seçin ve Enter tuşuna basın.  Bunu yapmak için IDE, **form1.cs** adlı ana pencerede ek bir sekme açar. (Bu sekmeyi kullanıyorsanız Visual Basic **Form1.vb olarak adlandırılmıştır.**

   Bu sekme, aşağıdaki ekran görüntüsünde gösterildiği gibi formun arkasındaki kod dosyasını görüntüler.

    ![Visual C kod ile Form1.cs&#35; oluşturma](../ide/media/express_showbuttoncode.png)<br>
***C# koduyla form1.cs** _ _tab_

    > [!NOTE]
    > Form1.cs veya Form1.vb sekmeniz bunun yerine **showButton'i** **ShowButton olarak** gösterebilir.

1. Kodun bu parçasına odaklanın.

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

   Adlı koda `showButton_Click()` (alternatif olarak) `ShowButton_Click()` bakabilirsiniz. ShowButton düğmesinin kod dosyasını açtığınız zaman IDE bunu formun **koduna** ekledi. Tasarım zamanında, bir formda denetim için kod dosyasını açsanız, henüz yoksa denetim için kod oluşturulur. Yöntemi olarak bilinen bu *kod,* uygulama çalıştırıldığında ve denetimi (bu durumda Resim göster **düğmesi) seçtiğiniz zaman** çalışır.

1. Form **Windows** sekmesini yeniden seçin (**Form1.cs [Tasarım]**) ve ardından  Resmi temizle düğmesinin kod dosyasını açın ve formun kodunda bunun için bir yöntem oluşturun. Kalan iki düğme için bunu tekrarlayın. IDE her zaman formun kod dosyasına yeni bir yöntem ekler.

1. Bir yöntem daha eklemek için, IDE'nin yöntem eklemesini Windows **Form** Tasarımcısı'nda **CheckBox** denetimi için kod dosyasını `checkBox1_CheckedChanged()` açın. Bu yöntem, kullanıcı onay kutusunu her seçer veya temizleyene kadar çağrılır.

   > [!TIP]
   > Bir uygulama üzerinde çalışırken genellikle kod düzenleyicisi ile Form Tasarımcısı arasında **Windows olur.** IDE, projeniz içinde gezinmeyi kolaylaştırır. Windows  Çözüm Gezgini C# veya *Form1.vb'de Form1.vb'ye* çift  tıklayarak Visual Basic **Forms** Tasarımcısı'Visual Basic açmak için kullanın veya menü çubuğunda Tasarımcıyı **Görüntüle'yi**  >  **seçin.**

    Aşağıda, kod düzenleyicisinde gördüğünüz yeni kodlar yer almaktadır.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs" id="Snippet2":::

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb" id="Snippet2":::

    > [!NOTE]
    > Kodunuz olay işleyicilerini "camelCase" harfiyle görüntülemeyebilirsiniz.

    Eklenen beş yöntem olay işleyicileri olarak anıldığından, uygulamanız bir olay (bir düğme seçen veya bir kutu seçen kullanıcı gibi) her olduğunda bunları çağırıyor.

    Tasarım zamanında IDE'de bir denetimin kodunu görüntüleyen Visual Studio, orada değilse denetim için bir olay işleyici yöntemi ekler. Örneğin, bir düğmeye çift tıklarken IDE, olayı için bir olay işleyicisi ekler (kullanıcı düğmeyi her seçerse <xref:System.Windows.Forms.Control.Click> bu çağrılır). Bir onay kutusuna çift tıklarsınız, IDE olayı için bir olay işleyicisi ekler (kullanıcı kutuyu her seçer veya <xref:System.Windows.Forms.CheckBox.CheckedChanged> temizleyene zaman çağrılır).

    Bir denetim için olay işleyicisi ekledikten sonra, **denetime** çift tıklayarak veya menü çubuğunda Kodu Görüntüle'yi seçerek Windows Forms Tasarımcısı'nda istediğiniz zaman **bu** denetime  >  **geri dönebilirsiniz.**

    Program derleme sırasında adlar önemlidir ve yöntemlerin (olay işleyicileri dahil) istediğiniz herhangi bir adı olabilir. IDE ile bir olay işleyicisi eklerken, denetimin adına ve iş çıkan olaya göre bir ad oluşturur.

    Örneğin, **showButton** adlı bir düğme için Click olayına `showButton_Click()` (alternatif olarak) olay `ShowButton_Click()` işleyicisi yöntemi denir. Ayrıca, açma ve kapatma parantezleri genellikle yöntemlerin tartışılmaktadır `()` olduğunu belirtmek için yöntem adının ardından eklenir.

    Bir kod değişkeninin adını değiştirmek istediğinize karar veriyorsanız, kodda değişkenine sağ tıklayın ve Yeniden **Adlandır'ı yeniden düzenleme'yi**  >  **seçin.** Kodda bu değişkenin tüm örnekleri yeniden adlandırılır. Daha fazla bilgi için [bkz. Yeniden düzenlemeyi yeniden adlandırma.](../ide/reference/rename.md)

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için **[bkz. 7. Adım: Formnize iletişim kutusu bileşenleri ekleme.](../ide/step-7-add-dialog-components-to-your-form.md)**

* Önceki öğretici adımına dönmek için [bkz. 5. Adım: Formnize denetim ekleme.](../ide/step-5-add-controls-to-your-form.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: Zamanlı matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: Eşleştirme oyunu oluşturma](tutorial-3-create-a-matching-game.md)
