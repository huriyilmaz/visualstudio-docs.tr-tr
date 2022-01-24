---
title: 'Öğretici: Windows Forms uygulamasına kullanıcı arabirimi denetimleri ekleme'
description: Resim görüntüleyici WinForms uygulamasına kullanıcı arabirimi denetimleri ekleme hakkında bilgi Visual Studio. Denetimler resim kutusu, onay kutusu ve düğmelere göredir.
dev_langs:
- CSharp
- VB
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.topic: tutorial
ms.date: 01/05/2022
ms.custom:
- vs-acquisition
ms.openlocfilehash: 9d93ba0e8a6c77ddc6b90fffadea7e4243490882
ms.sourcegitcommit: 7d319435c35075d4cec021b7b667666a81c02435
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "137650438"
---
# <a name="tutorial-add-code-to-the-picture-viewer-windows-forms-app-in-visual-studio"></a>Öğretici: Visual Studio'de Forms uygulaması Windows resim görüntüleyiciye kod Visual Studio

Bu üç öğretici serisinde, bir resim yük Windows görüntüleyen bir Windows Forms uygulaması oluşturabilirsiniz.
Visual Studio Tümleşik Tasarım Ortamı (IDE), uygulamayı oluşturmak için ihtiyacınız olan araçları sağlar.
Daha fazla bilgi edinmek için [bkz. IDE'Visual Studio hoş geldiniz.](../get-started/visual-studio-ide.md)

Denetimler C# veya Visual Basic ile ilişkili eylemleri yapmak için kod kullanır.

Bu üçüncü öğreticide şunların nasıl olduğunu öğrenirsiniz:

> [!div class="checklist"]
> - Denetimleriniz için olay işleyicileri ekleme
> - İletişim kutusunu açmak için kod yazma
> - Diğer denetimler için kod yazma
> - Uygulamanızı çalıştırma

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici önceki öğreticiler, Resim görüntüleyici uygulaması oluşturma [ve](tutorial-windows-forms-picture-viewer-layout.md) Resim görüntüleyiciye [kullanıcı arabirimi denetimleri ekleme öğreticilerini içerir.](tutorial-windows-forms-picture-viewer-controls.md)
Bu öğreticileri henüz yapmadıysanız önce bunları gözden bulun.

## <a name="add-event-handlers-for-your-controls"></a>Denetimleriniz için olay işleyicileri ekleme

Bu bölümde, ikinci *öğreticide eklenen* denetimler için olay işleyicileri ekleyin: [Resim görüntüleyici uygulamasına denetimler ekleme.](tutorial-windows-forms-picture-viewer-code.md)
Uygulamanız, bir düğme seçme gibi bir eylem ıldığında bir olay işleyicisi çağırıyor. 

1. Visual Studio'yu açın. Resim Görüntüleyicisi projeniz Yakın zamanda aç **altında görünür.**

1. Windows **Forms Tasarımcısı'nda** Resim göster **düğmesine çift** tıklayın.
   Bunun yerine formda **Resim göster düğmesini** seçerek Enter tuşuna **basabilirsiniz.**

   IDE Visual Studio de ana pencerede bir sekme açılır. C# için sekme **Form1.cs olarak adlandırılmıştır.** Bu sekmeyi kullanıyorsanız Visual Basic **Form1.vb olarak adlandırılmıştır.**

   Bu sekme, formun arkasındaki kod dosyasını görüntüler.

   ![Visual C net koduyla Form1.cs sekmesini gösteren ekran görüntüsü.](../ide/media/tutorial-windows-forms-picture-viewer-code/show-picture-button-code.png)

   > [!NOTE]
   > Form1.vb sekmeniz **showButton'i ShowButton** **olarak gösterebilir.**

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

1. Windows **Forms Tasarımcısı** sekmesini yeniden seçin ve ardından Resmi temizle düğmesine **çift tıklayarak** kodunu açın.
   Kalan iki düğme için tekrarlayın.
   Her zaman, Visual Studio IDE formun kod dosyasına yeni bir yöntem ekler.

1. Form Tasarımcısı'nda **CheckBox** denetimine **Windows çift tıklar** ve bir yöntem `checkBox1_CheckedChanged()` ekleyin. 
   Onay kutusunu işaretle veya temizle, bu yöntem çağrılır.

   Aşağıdaki kod parçacığı, kod düzenleyicisinde gördüğünüz yeni kodu gösterir.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs" id="Snippet2":::

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb" id="Snippet2":::

Olay işleyicileri de dahil olmak üzere yöntemlerin istediğiniz adı olabilir.
IDE ile bir olay işleyicisi eklerken, denetimin adına ve iş çıkan olaya göre bir ad oluşturur.

Örneğin **showButton** *adlı* düğmenin Tıklama olayı veya olarak `showButton_Click()` `ShowButton_Click()` adlandırılmıştır. Bir kod değişkeninin adını değiştirmek için kodda değişkenine sağ tıklayın ve Yeniden **Adlandır'ı yeniden düzenleme'yi**  >  **seçin.** Kodda bu değişkenin tüm örnekleri yeniden adlandırılır. Daha fazla bilgi için [bkz. Yeniden düzenlemeyi yeniden adlandırma.](../ide/reference/rename.md)

## <a name="write-code-to-open-a-dialog-box"></a>İletişim kutusunu açmak için kod yazma

Resim **göster düğmesi,** resim dosyasını görüntülemek için OpenFileDialog bileşenini kullanır.
Bu yordam, bu bileşeni çağıran kodu ekler.

IDE Visual Studio *IntelliSense* adlı güçlü bir araç sunar.
Siz yazarak IntelliSense olası kodlar önerir.

1. Form **Windows'da** Resim göster düğmesine **çift** tıklayın. 
   IDE imlecinizi veya yönteminin `showButton_Click()` içine `ShowButton_Click()` taşır.

1. İki *ayraç* arasındaki boş satıra veya ile arasına bir i `{ }` `Private Sub...` `End Sub` yazın.
   Bir **IntelliSense penceresi** açılır.

   ![Visual C net koduyla IntelliSense'i gösteren ekran görüntüsü.](../ide/media/tutorial-windows-forms-picture-viewer-code/intellisense-window.png)

1. **IntelliSense penceresinde** sözcüğü `if` vurgulanır. Eklemek **için Sekme** tuşuna `if` basın.

1. **true'yi** seçin ve `op` C# veya daha sonra yazmak `Op` için Visual Basic.

   ![True değerinin seçili olduğu göster düğmesinin olay işleyicisini gösteren ekran görüntüsü.](../ide/media/tutorial-windows-forms-picture-viewer-code/show-button-handler-true-selected.png)

   IntelliSense **openFileDialog1 dosyasını görüntüler.**

1. OpenFileDialog1 eklemek için Sekme'yi seçin.  

1. `.` **openFileDialog1'den** hemen sonra bir nokta ( ) veya nokta yazın. 
   IntelliSense, **OpenFileDialog bileşeninin** tüm özelliklerini ve yöntemlerini sağlar.
   Yazın ve `ShowDialog` Sekme'yi **seçin.** `ShowDialog()` Yöntem, Dosya **Aç iletişim** kutusunu gösterir.

1. içinde "g" ifadesinin hemen sonrasını parantez `ShowDialog` `()` ekleyin.
   Kodunuz olması `openFileDialog1.ShowDialog()` gerekir.

1. C# için bir boşluk ekleyin ve ardından iki eşittir işareti ( ) `==` ekleyin. Daha Visual Basic için bir boşluk ekleyin ve ardından tek bir eşittir işareti () `=` kullanın.

1. Başka bir alan ekleyin. *DialogResult* girmek için IntelliSense kullanın.

1. **IntelliSense** penceresinde DialogResult değerini açmak için bir nokta yazın. Harfi girin `O` ve **Tamam'ı eklemek için** Sekme tuşuna **basın.**

   > [!NOTE]
   > İlk kod satırı tamamlanır. C# için aşağıdakine benzer olması gerekir.
   >
   >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
   >
   >  Bu Visual Basic için aşağıdaki gibi olması gerekir.
   >
   >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

1. Aşağıdaki kod satırı ekleyin.

   ```csharp
   pictureBox1.Load(openFileDialog1.FileName);  
   ```

   ```vb
   PictureBox1.Load(OpenFileDialog1.FileName)
   ```

   IntelliSense'i kopyalayıp yapıştırarak veya kullanarak ebilirsiniz.
   Son `showButton_Click()` yönteminiz aşağıdaki koda benzer şekilde çalışmalı.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step8/cs/form1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step8/vb/form1.vb" id="Snippet1":::

1. Kodunuz için aşağıdaki açıklamayı ekleyin.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb" id="Snippet1":::

   Kodunuzu her zaman açıklama olarak yapmak en iyi yöntemdir.
   Kod açıklamalarını kullanarak gelecekte kodunuzu daha kolay anabilir ve koruyabilirsiniz.

## <a name="write-code-for-the-other-controls"></a>Diğer denetimler için kod yazma
Şimdi uygulamayı çalıştırdıysanız Resim **göster'i seçin.**
Resim Görüntüleyici, **görüntülemek istediğiniz** resmi seçerek Dosya Aç iletişim kutusunu açar.

Bu bölümde, diğer olay işleyicileri için kodu ekleyin.

1. Form **Windows'nda** Resmi temizle **düğmesine** çift tıklayın.
   Kodu küme ayraçları içinde ekleyin.

   ```csharp
   private void clearButton_Click(object sender, EventArgs e)
   {
       // Clear the picture.
       pictureBox1.Image = null;
   }
   ```

   ```vb
   Private Sub clearButton_Click() Handles clearButton.Click
       ' Clear the picture.
       PictureBox1.Image = Nothing
   End Sub   
   ```

1. Arka plan rengini **ayarla düğmesine çift** tıklayın ve kodu küme ayraçları içinde ekleyin.

   ```csharp
   private void backgroundButton_Click(object sender, EventArgs e)
   {
       // Show the color dialog box. If the user clicks OK, change the
       // PictureBox control's background to the color the user chose.
       if (colorDialog1.ShowDialog() == DialogResult.OK)
           pictureBox1.BackColor = colorDialog1.Color;
   }
   ```

   ```vb
   Private Sub backgroundButton_Click() Handles backgroundButton.Click
       ' Show the color dialog box. If the user clicks OK, change the
       ' PictureBox control's background to the color the user chose.
       If ColorDialog1.ShowDialog() = DialogResult.OK Then
           PictureBox1.BackColor = ColorDialog1.Color
       End If
   End Sub
   ```

1. Kapat düğmesine **çift tıklayın** ve kodu küme ayraçları içinde ekleyin.

   ```csharp
   private void closeButton_Click(object sender, EventArgs e)
   {
       // Close the form.
       this.Close();
   }

   ```

   ```vb
   Private Sub closeButton_Click() Handles closeButton.Click
       ' Close the form.
       Close()
   End Sub  
   ```

1. Esned **onay** kutusuna çift tıklayın ve kodu küme ayraçları içinde ekleyin.

   ```csharp
   private void checkBox1_CheckedChanged(object sender, EventArgs e)
   {
       // If the user selects the Stretch check box, 
       // change the PictureBox's
       // SizeMode property to "Stretch". If the user clears 
       // the check box, change it to "Normal".
       if (checkBox1.Checked)
           pictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;
       else
           pictureBox1.SizeMode = PictureBoxSizeMode.Normal;
   }
   ```

   ```vb
   Private Sub CheckBox1_CheckedChanged() Handles CheckBox1.CheckedChanged
       ' If the user selects the Stretch check box, change 
       ' the PictureBox's SizeMode property to "Stretch". If the user 
       ' clears the check box, change it to "Normal".
       If CheckBox1.Checked Then
           PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage
       Else
           PictureBox1.SizeMode = PictureBoxSizeMode.Normal
       End If
   End Sub   
   ```

## <a name="run-your-application"></a>Uygulamanızı çalıştırma

Uygulamayı yazarken herhangi bir zamanda çalıştırabilirsiniz.
Önceki bölümde kodu ekledikten sonra Resim Görüntüleyicisi tamamlanır.
Önceki öğreticilerde olduğu gibi, uygulamalarınızı çalıştırmak için aşağıdaki yöntemlerden birini kullanın:

- **F5 anahtarını** seçin.
- Menü çubuğunda Hata Ayıklama Hata **Ayıklamayı**  >  **Başlat'ı seçin.**
- Araç çubuğunda Başlat **düğmesini** seçin.

Resim Görüntüleyici başlığına **sahip bir pencere** görüntülenir.
Tüm denetimleri test eder.

1. Arka plan **rengini ayarla düğmesini** seçin. Renk **iletişim** kutusu açılır.

   ![Renk iletişim kutusunu gösteren ekran görüntüsü.](../ide/media/tutorial-windows-forms-picture-viewer-code/color-dialog-box.png)

1. Arka plan rengini ayarlamak için bir renk seçin.

1. Resim **görüntülemek için Resim göster'i** seçin.

   ![Resim Görüntüleyicisi uygulamasını gösteren ve bir resim görüntülenen ekran görüntüsü.](../ide/media/tutorial-windows-forms-picture-viewer-code/run-picture-viewer.png)

1. Esnet'i seçin ve seçimini **kaldırın.**

1. Resmin **temiz olduğundan emin** olmak için Resmi temizle düğmesini seçin.

1. Uygulamadan **çıkmak** için Kapat'ı seçin.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler!
Bu öğretici serisini tamamladık.
Bu programlama ve tasarım görevlerini IDE'de Visual Studio gerçekleştirebilirsiniz:

- Windows Forms kullanan bir Visual Studio projesi oluşturuldu
- Resim görüntüleme uygulaması için bitti düzeni
- Düğmeler ve onay kutusu eklendi
- İletişim kutuları eklendi
- Denetimleriniz için olay işleyicileri eklendi
- Olayları işlemek için Visual Basic C# veya kod yazma

Zamanlı matematik testi oluşturma hakkında başka bir öğretici serisiyle öğrenmeye devam edin.
> [!div class="nextstepaction"]
> [Öğretici 2: Zamanlı matematik testi oluşturma](tutorial-windows-forms-math-quiz-create-project-add-controls.md)
