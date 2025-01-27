---
title: 'Öğretici: Eşleştirme oyunu oluşturma'
description: Bu öğreticilerde bir oyuncunun simgelerle eş olduğu bir oyun oluşturabilirsiniz. Başlamak için C# veya VB Visual Studio Formlar kullanarak Windows proje oluşturun ve düzen ekleyin.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.topic: tutorial
ms.date: 01/07/2022
ms.custom:
- vs-acquisition
ms.openlocfilehash: 0327447fd1eeb64b486c0200d1069b494c2d7c52
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137887500"
---
# <a name="tutorial-create-a-matching-game-winforms-app"></a>Öğretici: Eşleşen bir oyun WinForms uygulaması oluşturma

Bu dört öğretici serisinde, oyuncunun gizli simge çiftlerini eşleştiren bir eşleştirme oyunu derlemek.

Visual Studio Tümleşik Tasarım Ortamı'nın (IDE) Visual Studio hakkında bilgi edinmek için bu öğreticileri kullanın.

- Simgeler gibi nesneleri bir nesnede depolar <xref:System.Collections.Generic.List%601> .
- `foreach` C# içinde bir döngü veya bir `For Each` Visual Basic öğeleri arasında döngü yapmak için bir döngü kullanın.
- Başvuru değişkenlerini kullanarak bir formun durumunu takip edin.
- Birden fazla nesneyle kullanabileceğiniz olaylara yanıt vermek için bir olay işleyicisi oluşturun.
- Geriye doğru sayan ve başlatılmasının ardından bir olayı kesin olarak tetikleyen bir zamanlayıcı hazırlayın.

Tamamlandıktan sonra eksiksiz bir oyunla karşınız olur.

![Bir kılavuzda birkaç eşleşen simgenin görüntülendiğinden, sizin oluşturtuz oyunu gösteren ekran görüntüsü.](../media/tutorial-windows-forms-create-match-game/match-game-final.png)

Bu ilk öğreticide şunların nasıl olduğunu öğrenirsiniz:

> [!div class="checklist"]
> - Windows Forms Visual Studio bir Windows oluşturun.
> - Düzen öğesini ekleyin ve biçimlendirin.
> - Görüntülemek için etiketleri ekleyin ve biçimlendirin.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi Visual Studio için bir adıma ihtiyacınız var.
Ücretsiz sürüm [Visual Studio indirmeler](https://visualstudio.microsoft.com/vs/) sayfasını ziyaret edin.

## <a name="create-your-windows-forms-match-game-project"></a>Windows Forms eşleşme oyunu projenizi oluşturma

Eşleştirme oyunlarınızı  oluşturmanın ilk adımı bir Windows Forms Uygulaması projesi oluşturmaktır.

::: moniker range="vs-2017"
1. Visual Studio'yu açın.

1. Menü çubuğunda Dosya Yeni **Dosya'Project** >  > **.**

   ![Yeni proje iletişim kutusunu gösteren ekran görüntüsü.](../media/new-project-dialog-callouts.png)

1. Yeni Uygulama iletişim kutusunun sol **Project** **Visual C#** veya **Visual Basic'ı seçin** ve Windows **Masaüstü'Windows seçin**.

1. Proje şablonları listesinde form formlarını Windows **(.NET Framework) seçin**. Yeni forma *MatchingGame adını ve* ardından Tamam'ı **seçin**.

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız **. .NET** masaüstü Visual Studio Yükleyicisi iş yükünü yüklemek için Visual Studio Yükleyicisi kullanın.
   >
   > ![Uygulamanın içinde nokta NET masaüstü geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.](../media/tutorial-windows-forms-create-match-game/install-dot-net-desktop-env.png)
   >
   > Daha fazla bilgi için Yükleme [Visual Studio](../../install/install-visual-studio.md) bakın.
::: moniker-end

::: moniker range=">=vs-2019"
1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın**.

   ![Yeni proje oluştur seçeneğini başlangıç penceresinde gösteren Visual Studio görüntüsü.](../media/tutorial-windows-forms-create-match-game/create-new-project-dark-theme.png)

1. Yeni proje **oluştur penceresinde Yeni** Formlar için *Windows arama.* Ardından Tüm **proje türleri** **listesinden Masaüstü'leri** seçin.

1. C# **Windows formlar için .NET Framework Forms Uygulaması (Visual Basic)** şablonunu seçin ve ardından Sonraki'yi **seçin**.

   ![Windows Forms'ların girildi olduğu yeni proje oluştur iletişim kutusunu ve Windows Forms Uygulaması'nın seçeneklerini gösteren ekran görüntüsü.](../media/tutorial-windows-forms-create-match-game/create-project-windows-forms.png)

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz**. Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > ![Yeni proje oluştur iletişim kutusunda, Arayıcınız ne arıyorsanız bu değil iletisiyle Daha fazla araç ve özellik yükle bağlantısını gösteren ekran görüntüsü.](../media/tutorial-windows-forms-create-match-game/install-more-tools.png)
   >
   > Ardından, Visual Studio Yükleyicisi **.NET masaüstü geliştirme'yi seçin**.
   >
   > ![Uygulamanın .NET Core iş yükünü gösteren Visual Studio Yükleyicisi.](../media/tutorial-windows-forms-create-match-game/install-dot-net-desktop-env.png)
   >
   > **Dosyanın içinde** Değiştir'Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz istendiğinde. Ardından, iş yükünü **yüklemek için** Devam'ı seçin.

1. Yeni **projenizi yapılandır penceresinde projenize** *MatchingGame adını ve ardından* Oluştur'a **tıklayın**.

::: moniker-end

Visual Studio için bir çözüm oluşturur.
Çözüm, uygulamanıza gereken tüm projeler ve dosyalar için bir kapsayıcıdır.

Bu noktada, Visual Studio Form Tasarımcısı'nda boş **Windows görüntüler**.

## <a name="create-a-layout-for-your-game"></a>Oyun için düzen oluşturma

Bu bölümde, oyunun dörte dört kılavuzu oluşturacağız.

1. Form Tasarımcısı'nda Windows tıklayın. Sekme C# için **Form1.cs [Tasarım]** veya **form1.vb [Tasarım]** Visual Basic. Özellikler **penceresinde** aşağıdaki form özelliklerini ayarlayın.

   - Text özelliğini  **Form1'den Eşleştirme** **Oyunu olarak değiştirme**. Bu metin oyun penceresinin en üstünde görünür.
   - Formun boyutunu ayarlayın. Boyut özelliğini **550, 550** olarak ayarerek veya formun köşesini sürükleyerek, Visual Studio IDE'nin en altında doğru boyutu görene kadar değiştirebilirsiniz.

1. **IDE'nin** sol tarafındaki Araç Kutusu sekmesini seçin.
   Bunu görmüyorsanız menü çubuğundan Veya  > **CtrlAltX** tuşlarına basarak **GörünümToolbox'ı**++ **seçin**.

1. Araç kutusunda <xref:System.Windows.Forms.TableLayoutPanel> Kapsayıcılar **kategorisinden** bir denetimi sürükleyin veya çift tıklayın.
   Özellikler penceresinde panel için **aşağıdaki özellikleri ayarlayın** .

   - **BackColor özelliğini** **CornflowerBlue olarak ayarlayın**.
     Bu özelliği ayarlamak için **BackColor** özelliğinin yanındaki oku seçin.
     **BackColor iletişim kutusunda** **Web'i seçin**.
     Kullanılabilir renk adlarında **CornflowerBlue'yi seçin**.

     > [!NOTE]
     > Renkler alfabetik sırada değil ve **CornflowerBlue** listenin alt kısmında yer alıyor.

   - Ortadaki büyük **düğmeyi seçerek** açılan listeden **Dock** özelliğini Fill olarak ayarlayın.
     Bu seçenek tabloyu formun tamamını kapsayacak şekilde yalıtır.
   - **CellBorderStyle özelliğini** **Inset olarak ayarlayın**.
     Bu değer, tahtada yer alan her hücre arasında görsel kenarlıklar sağlar.
   - TableLayoutPanel'in sağ üst köşesindeki üçgen düğmesini seçerek görev menüsünü açın.
     Görev menüsünde Satır **Ekle'yi iki kez** seçerek iki satır daha ekleyin.
     Ardından Sütun **Ekle'yi** iki kez seçerek iki sütun daha ekleyin.
   - Görev menüsünde Satırları ve Sütunları **Düzenle'yi seçerek** Sütun ve **Satır Stilleri penceresini** açın.
     Her sütun için Yüzde **seçeneğini belirleyin** ve her sütunun genişliğini yüzde *25 olarak* ayarlayın.
   - Pencerenin **üst** kısmından Satırlar'ı seçin ve ardından her satırın yüksekliğini yüzde 25 olarak ayarlayın.
   - Bitirerek değişikliklerinizi kaydetmek **için Tamam'ı** seçin.

TableLayoutPanel artık 16 eşit boyutlu kare hücreye sahip dörte dört kılavuzdur.
Bu satırlar ve sütunlar simgelerin daha sonra görüntüleniyor olduğu yer.

![Dört tarafından dört kılavuza sahip Formlar sekmesini gösteren ekran görüntüsü.](../media/tutorial-windows-forms-create-match-game/match-game-grid.png)

## <a name="add-and-format-labels-to-display"></a>Görüntülemek için etiket ekleme ve biçimlendirme

Bu bölümde, oyun sırasında görüntülemek için etiketler oluşturabilir ve biçimlendirebilirsiniz.

1. Form düzenleyicisinde TableLayoutPanel seçildiğinden emin olun.
   Özellikler penceresinin **üst kısmında tableLayoutPanel1'i** **görüyor** gerekir.
   Seçili değilse, formda TableLayoutPanel'i seçin veya Özellikler penceresinin en üstünde yer alan **listeden seçin.**

1. Araç kutusunu daha önce olduğu gibi açın ve Ortak **Denetimler kategorisini** açın.
   <xref:System.Windows.Forms.Label> TableLayoutPanel'in sol üst hücresine bir denetim ekleyin.
   Etiket denetimi artık IDE'de seçilidir.
   Bu öğe için aşağıdaki özellikleri ayarlayın.

   - Etiketin **BackColor** özelliğini **CornflowerBlue olarak ayarlayın**.
   - **AutoSize özelliğini** **False olarak ayarlayın**.
   - Dock özelliğini **Fill** olarak **ayarlayın**.
   - Özelliğin yanındaki açılan **düğmeyi ve** ardından ortadaki düğmeyi seçerek **TextAlign** özelliğini MiddleCenter olarak ayarlayın.
     Bu değer, simgenin hücrenin ortasında görünür.
   - **Font özelliğini** seçin. Üç nokta (**...**) düğmesi görüntülenir.
     Üç noktayı seçin ve Yazı tipi değerini **Webdings**, Yazı Tipi Stili'nin  **Kalın** ve **Boyut** değerini **48 olarak ayarlayın**.
   - Etiketin **Text** özelliğini c harfi olarak **ayarlayın**.

   TableLayoutPanel'in sol üst hücresinde artık mavi arka planda ortalı bir siyah kutu var.

   > [!NOTE]
   > Webdings, işletim sistemiyle birlikte Windows yazı tipidir.
   > Eşleştirme oyununda oyuncu simge çiftleri ile eştir.
   > Bu yazı tipi eşleşmek için simgeleri görüntüler.
   >
   > Text **özelliğinde c** yerine **farklı harfleri deneyin** .
   > Ünlem işareti bir örümcek, büyük N harfi bir göz ve virgül ise kırmızı biberdir.

1. Etiket denetiminizi seçin ve TableLayoutPanel'de sonraki hücreye kopyalayın.
   **CtrlC tuşlarını**+ veya menü çubuğunda DüzenleCopy'yi  > **seçin**.
   Ardından **CtrlV**+ veya **EditPaste tuşlarını kullanarak** >  yapıştırın.

   TableLayoutPanel'in ikinci hücresinde ilk Etiketin bir kopyası görüntülenir.
   Bunu yeniden yapıştırarak üçüncü hücrede başka bir Etiket görünür. Tüm hücreler doldurulana kadar Etiket denetimlerini yapıştırabilirsiniz.

Bu adım form düzeninizi tamamlar.

![On altı siyah kare ile eşleşen oyun formunu gösteren ekran görüntüsü.](../media/tutorial-windows-forms-create-match-game/match-game-grid-fill.png)

## <a name="next-steps"></a>Sonraki adımlar

Her etikete rastgele bir simge atamayı ve etiketlere olay işleyicileri eklemeyi öğrenmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Eşleştirme Oyun'nize simgeler ekleme](tutorial-windows-forms-match-game-icons.md)

