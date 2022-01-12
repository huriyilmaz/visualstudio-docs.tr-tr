---
title: 'Öğretici: bir resim görüntüleyici uygulamasına denetimler ekleme.'
description: Bu öğreticide, resim görüntüleyici uygulamanıza bir resim kutusu, onay kutusu ve düğme eklersiniz.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.topic: tutorial
ms.date: 01/05/2022
ms.custom:
- vs-acquisition
ms.openlocfilehash: 5a18b0161439b4f4457c6b5ead3ac6428c1d578d
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135808663"
---
# <a name="tutorial-add-ui-controls-to-the-picture-viewer-windows-forms-app-in-visual-studio"></a>öğretici: Visual Studio içindeki resim görüntüleyicisi Windows Forms uygulama kullanıcı arabirimi denetimleri ekleme

bu üç öğretici serisinde, bir resim yükleyen ve onu görüntüleyen bir Windows Forms uygulaması oluşturacaksınız.
Visual Studio tümleşik tasarım ortamı (ıde), uygulamayı oluşturmak için gereken araçları sağlar.
daha fazla bilgi edinmek için bkz. [Visual Studio ıde 'ye hoş geldiniz](../get-started/visual-studio-ide.md).

Bu program, uygulamayı denetlemek için kullandığınız bir resim kutusu, bir onay kutusu ve birkaç düğme içerir.
Bu öğretici, bu denetimlerin nasıl ekleneceğini gösterir.

Bu ikinci öğreticide şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
> - Uygulamanıza denetim ekleme
> - Düzen paneline düğme ekleme
> - Denetim adlarını ve konumlarını değiştirme
> - İletişim kutusu bileşenleri ekleme

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici, önceki öğreticide oluşturulur, [bir resim görüntüleyici uygulaması oluşturur](tutorial-windows-forms-picture-viewer-layout.md).
Bu öğreticiyi yapmadıysanız, önce bunlardan birine gidin.

## <a name="add-controls-to-your-application"></a>Uygulamanıza denetim ekleme
Resim görüntüleyici uygulaması bir resmi göstermek için PictureBox denetimini kullanır.
Resmi ve arka planı yönetmek ve uygulamayı kapatmak için bir onay kutusu ve birkaç düğme kullanır.
Visual Studio ıde 'deki araç kutusundan PictureBox ve bir onay kutusu ekleyeceksiniz.

1. Visual Studio'yu açın. Resim görüntüleyici projeniz **yakın zamanda aç** altında görüntülenir.

1. **Windows Form Tasarımcısı**, önceki öğreticide eklediğiniz TableLayoutPanel öğesini seçin.
   **Özellikler** penceresinde **tableLayoutPanel1** göründüğünden emin olun.

1. Visual Studio ıde 'nin sol tarafında **araç kutusu** sekmesini seçin. Bunu görmüyorsanız,   >  menü çubuğundan veya **CTRL** alt X ' ten Görünüm **araç kutusunu** seçin +  + .
   Araç kutusunda **ortak denetimler**' i genişletin.

1. Formunuza PictureBox denetimi eklemek için **PictureBox** öğesine çift tıklayın. Visual Studio ıde, PictureBox 'ın ilk boş hücresine PictureBox denetimini ekler.

1. Yeni **PictureBox** denetimini seçerek seçin ve ardından yeni PictureBox denetimindeki siyah üçgeni seçerek görev listesini görüntüleyin.

   ![Ekran görüntüsü, üst kapsayıcıda Dock 'un vurgulandığı PictureBox görevleri iletişim kutusunu gösterir.](../ide/media/tutorial-windows-forms-picture-viewer-controls/picture-box-tasks-dialog.png)

1. **Üst kapsayıcıda yerleştir**' i seçerek PictureBox **Dock** özelliğini **Fill** olarak ayarlar.
   Bu değeri **Özellikler** penceresinde görebilirsiniz.

1. PictureBox 'ın **Özellikler** penceresinde **ColumnSpan** özelliğini **2** olarak ayarlayın.
   PictureBox artık her iki sütunu da doldurur.

1. **BorderStyle** özelliğini **Fixed3D** olarak ayarlayın.

1. **Windows Form Tasarımcısı** **TableLayoutPanel**' i seçin.
   Sonra, **araç kutusunda**, yeni bir CheckBox denetimi eklemek için **onay** kutusu öğesine çift tıklayın.
   PictureBox, TableLayoutPanel içindeki ilk iki hücreyi kaplar, bu nedenle CheckBox denetimi sol alt hücreye eklenir.

1. **Text** özelliğini seçin ve **Esnetme** girin.

    ![Ekran görüntüsü, Esnetme adlı CheckBox denetimini gösterir.](../ide/media/tutorial-windows-forms-picture-viewer-controls/checkbox-named-stretch.png)

## <a name="add-buttons-in-a-layout-panel"></a>Düzen paneline düğme ekleme

Şimdiye kadar olan denetimler TableLayoutPanel 'e eklenmiştir.
Bu adımlarda, TableLayoutPanel 'de yeni bir Düzen paneline dört düğme eklemenin nasıl yapılacağı gösterilmektedir.

1. Formda TableLayoutPanel öğesini seçin.
   **Araç kutusunu** açın, **kapsayıcılar**' ı seçin.
   TableLayoutPanel 'in son hücresine yeni bir denetim eklemek için **FlowLayoutPanel** ' e çift tıklayın.

1. FlowLayoutPanel 'in **Dock** özelliğini **Fill** olarak ayarlayın.
   Bu özelliği, siyah üçgeni seçip **üst kapsayıcıda yerleştir**' i seçerek ayarlayabilirsiniz.

   <xref:System.Windows.Forms.FlowLayoutPanel>, Bir satırdaki diğer denetimleri izleyen bir kapsayıcıdır.

1. Yeni FlowLayoutPanel ' i seçin ve ardından **araç kutusunu** açın ve **ortak denetimler**' i seçin.
   **Button1** adlı bir düğme denetimi eklemek için **düğme** öğesine çift tıklayın.

1. Başka bir düğme eklemek için **düğmeye** çift tıklayın. IDE **, bir sonraki** bir sonrakini çağırır.

1. Bu şekilde iki düğme daha ekleyin.
   Diğer bir seçenek de **button2**' i seçin ve sonra **kopyayı Düzenle**' yi seçin  >   veya **CTRL** + **C** tuşuna basın.
   Sonra, menü çubuğundan yapıştırmayı **Düzenle**' yi seçin  >   veya **CTRL** + **V** tuşuna basın.
   Düğme kopyasını yapıştırmak için. Şimdi yapıştırın. IDE 'nin FlowLayoutPanel 'e **Button3** ve **Button4** eklediğine dikkat edin.

1. İlk düğmeyi seçin ve **Text** özelliğini **bir resim gösterecek** şekilde ayarlayın.

1. **Resmi temizlemek**, **arka plan rengini ayarlamak** ve **kapatmak** için sonraki üç düğmenin **Text** özelliklerini ayarlayın.

1. Düğmeleri boyutlandırma ve düzenleme için FlowLayoutPanel ' i seçin. **FlowDirection** özelliğini **RightToLeft** olarak ayarlayın.

   Düğmeler, hücrenin sağ tarafına hizalanmalıdır ve **bir resim göster** düğmesi sağ tarafta olacak şekilde sıralarını tersine çevirir.
   Bunları herhangi bir sırada düzenlemek için FlowLayoutPanel etrafında düğmeleri sürükleyebilirsiniz.

1. Kapatmak için **Kapat** düğmesini seçin. Daha sonra düğmeleri aynı anda seçmek için **CTRL** tuşuna basın ve basılı tutun ve bunları da seçin.

1. **Özellikler** penceresinde **AutoSize** özelliğini **true** olarak ayarlayın.
   Düğmeler, metin sığacak şekilde yeniden boyutlandırılır.

    ![Ekran görüntüsü, dört düğme içeren resim Görüntüleyicisi formunu gösterir.](../ide/media/tutorial-windows-forms-picture-viewer-controls/buttons-autosize.png)

Denetimlerin nasıl görünmeyeceğini görmek için programınızı çalıştırabilirsiniz. **F5** tuşunu seçin, **hata**  >  **ayıklamayı Başlat**' ı seçin veya **Başlat** düğmesini seçin.
Eklediğiniz düğmeler henüz hiçbir şey yapmaz.

## <a name="change-control-names"></a>Denetim adlarını Değiştir

Formunuzda, C# ' de **button1**, **button2**, **Button3** ve **Button4** adlı dört düğme vardır.
Visual Basic, herhangi bir denetim adının varsayılan ilk harfi büyük harfle yazılır, bu nedenle düğmeler **Button1**, **Button2**, **Button3** ve **Button4** olarak adlandırılır.
Daha bilgilendirici adlar vermek için bu adımları kullanın.

1. Formda, **Kapat** düğmesini seçin.
   Hala tüm düğmeleri seçtiyseniz, seçimi iptal etmek için **ESC** 'yi seçin.

1. **Özellikler** penceresinde, **(ad)** öğesini arayın.
   Adı **CloseButton** olarak değiştirin.

   ![CloseButton adıyla Özellikler penceresi](../ide/media/tutorial-windows-forms-picture-viewer-controls/close-button-name-property.png)

   IDE, boşluk içeren adları kabul etmez.

1. Diğer üç düğmeyi **backgroundButton**, **clearButton** ve **showButton** olarak yeniden adlandırın.
   **Özellikler** penceresinde denetim Seçicisi açılan listesini seçerek adları doğrulayabilirsiniz.
   Yeni düğme adları görüntülenir.

TableLayoutPanel veya onay kutusu gibi herhangi bir denetimin adını değiştirebilirsiniz.

## <a name="add-dialog-components"></a>İletişim kutusu bileşenleri ekleme

Uygulamanız, resim dosyalarını açabilir ve bileşenleri kullanarak bir arka plan rengi seçebilir.
Bir bileşen denetim gibidir.
Formunuza bir bileşen eklemek için **araç kutusunu** kullanın.
**Özellikler penceresini kullanarak** özelliklerini ayarlarsınız.

Bir denetimin aksine, formunuza bir bileşen eklemek görünür bir öğe eklemez.
Bunun yerine, kodla tetikleyebileceğiniz belirli davranışları sağlar.
Örneğin, bu bir **Dosya Aç** iletişim kutusu açan bir bileşendir.

Bu bölümde <xref:System.Windows.Forms.OpenFileDialog> formunuza bir bileşen ve <xref:System.Windows.Forms.ColorDialog> bileşen eklersiniz.

1. **Windows Form Tasarımcısı** (**Form1. cs [Design]**) seçin. Ardından **araç kutusunu** açın ve **iletişim kutuları** grubunu seçin.

1. Formunuza **OpenFileDialog1** adlı bir bileşen eklemek için **OpenFileDialog** öğesine çift tıklayın.

1. **ColorDialog1** adlı bir bileşen eklemek Için **ColorDialog** ' a çift tıklayın.
   bileşenler simge olarak **Windows Form Tasarımcısı** altında görüntülenir.

   ![İletişim kutusu bileşenleri](../ide/media/tutorial-windows-forms-picture-viewer-controls/components-window-forms-designer.png)

1. **OpenFileDialog1** simgesini seçin ve iki özelliği ayarlayın:

   - **Filter** özelliğini şu şekilde ayarlayın:

     ```console
     JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
     ```

   - **Title** özelliğini şu şekilde ayarlayın: **bir resim dosyası seçin**

   **Filtre** özelliği ayarları, **resim Seç** iletişim kutusunun görüntülediği türleri belirler.

## <a name="next-steps"></a>Sonraki adımlar

Uygulamanıza kod ekleme hakkında bilgi edinmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Öğretici Bölüm 3: resim görüntüleyiciye kod ekleme](tutorial-windows-forms-picture-viewer-code.md)
