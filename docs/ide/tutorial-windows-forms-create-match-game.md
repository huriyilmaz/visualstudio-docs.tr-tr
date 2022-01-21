---
title: 'Öğretici: eşleşen oyun oluşturma'
description: Bu öğreticilerde, bir oyuncunun simgelerle eşleştiği bir oyun oluşturacaksınız. başlamak için, C# veya VB Windows Forms kullanarak Visual Studio bir proje oluşturun ve düzen ekleyin.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.topic: tutorial
ms.date: 01/07/2022
ms.custom:
- vs-acquisition
ms.openlocfilehash: b4f4deb5dc01a98d81a518dc3d5aeb36ae780ab8
ms.sourcegitcommit: 7746657b87b22a7684e79e508af598b02dfe24b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "137609501"
---
# <a name="tutorial-create-a-matching-game-winforms-app"></a>Öğretici: eşleşen bir oyun WinForms uygulaması oluşturma

Bu dört öğretici serisinde, Player 'ın gizli simge çiftlerini eşleştiği eşleşen bir oyun oluşturursunuz.

Visual Studio tümleşik tasarım ortamında (ıde) aşağıdaki görevler hakkında bilgi edinmek için bu öğreticileri kullanın.

- Simgeler gibi nesneleri bir <xref:System.Collections.Generic.List%601> nesnede depolayın.
- `foreach` `For Each` bir listedeki öğeler arasında yinelemek için C# veya Visual Basic döngüsünde bir döngü kullanın.
- Başvuru değişkenlerini kullanarak bir formun durumunu takip edin.
- Birden fazla nesneyle kullanabileceğiniz olaylara yanıt vermek için bir olay işleyicisi oluşturun.
- Geriye doğru sayan ve başlatılmasının ardından bir olayı kesin olarak tetikleyen bir zamanlayıcı hazırlayın.

Bitirdiğinizde, tamamen oyun alacaksınız.

![Ekran görüntüsünde, bir kılavuzda görüntülenen birkaç eşleşen simge ile oluşturduğunuz oyun gösterilmektedir.](../ide/media/tutorial-windows-forms-create-match-game/match-game-final.png)

Bu ilk öğreticide şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
> - Windows Forms kullanan bir Visual Studio projesi oluşturun.
> - Düzen öğesi ekleyin ve biçimlendirin.
> - Görüntülenecek etiketleri ekleyin ve biçimlendirin.

## <a name="prerequisites"></a>Önkoşullar

bu öğreticiyi tamamlayabilmeniz için Visual Studio gerekir.
ücretsiz sürüm için [Visual Studio indirmeleri sayfasını](https://visualstudio.microsoft.com/vs/) ziyaret edin.

## <a name="create-your-windows-forms-match-game-project"></a>Windows Forms eşleştir oyun projenizi oluşturun

eşleşen oyununuzu oluşturduğunuzda, ilk adım Windows Forms bir uygulama projesi oluşturmaktır.

::: moniker range="vs-2017"
1. Visual Studio'yu açın.

1. menü çubuğunda **dosya** > **yeni** > **Project**' yi seçin.

   ![Ekran görüntüsü yeni proje iletişim kutusunu gösterir.](../ide/media/newprojectdialogcallouts.png)

1. **yeni Project** iletişim kutusunun sol tarafında, **Visual C#** veya **Visual Basic**' i seçin ve ardından **Windows masaüstü**' nü seçin.

1. proje şablonları listesinde **Windows Forms uygulama (.NET Framework)** öğesini seçin. Yeni form *MatchingGame* olarak adlandırın ve ardından **Tamam**' ı seçin.

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **.net masaüstü geliştirme** iş yükünü yüklemek için Visual Studio Yükleyicisi kullanın.
   >
   > ![ekran görüntüsünde, Visual Studio Yükleyicisi nokta ağı masaüstü geliştirme iş yükü gösterilmektedir.](../ide/media/tutorial-windows-forms-create-match-game/install-dot-net-desktop-env.png)
   >
   > daha fazla bilgi için, [Visual Studio yüklemesi](../install/install-visual-studio.md) sayfasına bakın.
::: moniker-end

::: moniker range=">=vs-2019"
1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![ekran görüntüsü Visual Studio başlangıç penceresinde yeni proje oluştur seçeneğini gösterir.](./media/tutorial-windows-forms-create-match-game/create-new-project-dark-theme.png)

1. **yeni proje oluştur** penceresinde, *Windows Forms* için arama yapın. Ardından **tüm proje türleri** listesinden **Masaüstü** ' nü seçin.

1. C# veya Visual Basic için **Windows Forms App (.NET Framework)** şablonunu seçin ve ardından **ileri**' yi seçin.

   ![ekran görüntüsü, Windows Forms uygulama için Windows Forms girilen ve seçeneklerin bulunduğu yeni proje oluştur iletişim kutusunu gösterir.](./media/tutorial-windows-forms-create-match-game/create-project-windows-forms.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi ' nde **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![Ekran görüntüsü yeni proje oluştur iletişim kutusunda ileti aradığınızı bulma hakkında daha fazla araç ve özellik yüklemesi bağlantısını gösterir.](./media/tutorial-windows-forms-create-match-game/install-more-tools.png)
   >
   > sonra, Visual Studio Yükleyicisi ' de **.net masaüstü geliştirme**' yi seçin.
   >
   > ![ekran görüntüsünde Visual Studio Yükleyicisi .net Core iş yükü gösterilmektedir.](../ide/media/tutorial-windows-forms-create-match-game/install-dot-net-desktop-env.png)
   >
   > Visual Studio Yükleyicisi **değiştir** ' i seçin. İşinizi kaydetmeniz istenebilir. Sonra, iş yükünü yüklemek için **devam** ' ı seçin.

1. **Yeni projeyi yapılandırın** penceresinde, projenizin *MatchingGame*' i adlandırın, sonra **Oluştur**' u seçin.

::: moniker-end

Visual Studio, uygulamanız için bir çözüm oluşturur.
Çözüm, uygulamanız için gereken tüm proje ve dosyalar için bir kapsayıcıdır.

bu noktada, Visual Studio **Windows form tasarımcısında** boş bir form görüntüler.

## <a name="create-a-layout-for-your-game"></a>Oyununuz için bir düzen oluşturun

Bu bölümde, oyunun dört-by-dört kılavuzunu oluşturursunuz.

1. Windows Form Tasarımcısı seçmek için forma tıklayın. Sekme, Visual Basic için C# veya **Form1. vb [Design]** için **Form1. cs [Design]** okur. **Özellikler** penceresinde, aşağıdaki form özelliklerini ayarlayın.

   - **Text** özelliğini **Form1** iken **eşleşen oyunla** değiştirin. Bu metin oyun penceresinin en üstünde görünür.
   - Formun boyutunu ayarlayın. **boyut** özelliğini **550, 550** ya da Visual Studio ıde 'nin altındaki doğru boyutu görene kadar formun köşesini sürükleyerek değiştirebilirsiniz...

1. IDE 'nin sol tarafındaki **araç kutusu** sekmesini seçin.
   Bunu görmüyorsanız,   >  menü çubuğundan veya **CTRL** alt X ' ten Görünüm **araç kutusunu** seçin +  + .

1. <xref:System.Windows.Forms.TableLayoutPanel>Araç kutusundaki **kapsayıcılar** kategorisinden bir denetim sürükleyin veya çift tıklayın.
   **Özellikler** penceresinde panel için aşağıdaki özellikleri ayarlayın.

   - **BackColor** özelliğini **CornflowerBlue** olarak ayarlayın.
     Bu özelliği ayarlamak için **BackColor** özelliğinin yanındaki oku seçin.
     **BackColor** Iletişim kutusunda **Web**' i seçin.
     Kullanılabilir renk adlarında **CornflowerBlue**' yı seçin.

     > [!NOTE]
     > Renkler alfabetik sırada değildir ve **CornflowerBlue** listenin en altına yakındır.

   - **Yerleştir** özelliğini açılan listeden **dolduracak** şekilde ayarlayın, büyük orta düğmesini seçin.
     Bu seçenek, tüm formu kaplamasını sağlamak için tabloyu kullanıma yayar.
   - **CellBorderStyle** özelliğini **ınmetinolarak** ayarlayın.
     Bu değer, panoda bulunan her bir hücre arasında görsel kenarlıklar sağlar.
   - Görev menüsünü göstermek için TableLayoutPanel 'in sağ üst köşesindeki üçgen düğmesini seçin.
     İki satır daha eklemek için görev menüsünde satırı iki kez **Ekle** ' yi seçin.
     Daha sonra iki sütun eklemek için **sütun Ekle** 'yi iki kez seçin.
   - Görev menüsünde **satırları ve sütunları Düzenle** ' yi seçerek **sütun ve satır stilleri** penceresini açın.
     Her sütun için **yüzde** seçeneğini belirleyin ve sonra her bir sütunun genişliğini yüzde *25* olarak ayarlayın.
   - Pencerenin üstündeki listeden **Satırlar** ' ı seçin ve ardından her satırın yüksekliğini yüzde 25 ' e ayarlayın.
   - İşiniz bittiğinde, değişikliklerinizi kaydetmek için **Tamam** ' ı seçin.

TableLayoutPanel 'niz artık, 16 eşit ölçekli kare hücresi olan dört-by dört kılavuza sahiptir.
Bu satırlar ve sütunlar simgelerin daha sonra göründüğü yerdir.

![Ekran görüntüsü, dört ile dört arasında kılavuz içeren formlar sekmesini gösterir.](../ide/media/tutorial-windows-forms-create-match-game/match-game-grid.png)

## <a name="add-and-format-labels-to-display"></a>Görüntülenecek etiketleri Ekle ve Biçimlendir

Bu bölümde, oyun sırasında görüntülenecek etiketleri oluşturur ve biçimlendirir.

1. Form düzenleyicisinde TableLayoutPanel seçildiğinden emin olun.
   **Özellikler** penceresinin üst kısmında **tableLayoutPanel1** görmeniz gerekir.
   Seçili değilse, formda TableLayoutPanel öğesini seçin veya **Özellikler** penceresinin en üstündeki listeden seçin.

1. Daha önce olduğu gibi araç kutusunu açın ve **ortak denetimler** kategorisini açın.
   <xref:System.Windows.Forms.Label>TableLayoutPanel 'in sol üst hücresine bir denetim ekleyin.
   Etiket denetimi artık IDE 'de seçilmiştir.
   Bu öğe için aşağıdaki özellikleri ayarlayın.

   - Etiketin **BackColor** özelliğini **CornflowerBlue** olarak ayarlayın.
   - **AutoSize** özelliğini **false** olarak ayarlayın.
   - **Dock** özelliğini **Fill** olarak ayarlayın.
   - Özelliğin yanındaki açılan düğmeyi seçerek ve ardından ortadaki düğmeyi seçerek **TextAlign** özelliğini **MiddleCenter** olarak ayarlayın.
     Bu değer, simgenin, hücrenin ortasında görünmesini sağlar.
   - **Yazı tipi** özelliğini seçin. Üç nokta (**...**) düğmesi görünür.
     Üç noktayı seçin ve **yazı tipi** değerini **Web** **'e,** **yazı tipi stilini** **kalın** olarak ve **48** olarak ayarlayın.
   - Etiketin **Text** özelliğini **c** harfine ayarlayın.

   TableLayoutPanel 'in sol üst hücresi artık mavi bir arka planda ortalanmış siyah bir kutu içeriyor.

   > [!NOTE]
   > web, Windows işletim sistemiyle birlikte gelen simgelerin yazı tipidir.
   > Eşleşen oyununuzda oyuncu simge çiftleriyle eşleşir.
   > Bu yazı tipi eşleştirilecek simgeleri görüntüler.
   >
   > **C** yerine, **Text** özelliğinde farklı harfler deneyin.
   > Ünlem işareti bir örümcek, büyük N harfi bir göz ve virgül ise kırmızı biberdir.

1. Etiket denetiminizi seçin ve TableLayoutPanel içindeki bir sonraki hücreye kopyalayın.
   **CTRL** + **C** tuşlarını veya menü çubuğunda kopyayı **Düzenle**' yi seçin  >  .
   Sonra **CTRL** + **V** veya yapıştırmayı **Düzenle**' yi kullanarak yapıştırın  >  .

   İlk etiketin bir kopyası TableLayoutPanel 'in ikinci hücresinde görüntülenir.
   Tekrar yapıştırın ve üçüncü hücrede başka bir etiket görüntülenir. Tüm hücreler dolduruluncaya kadar etiket denetimlerini yapıştırmayı sürdürün.

Bu adım formunuzun yerleşimini tamamlar.

![Ekran görüntüsü, eşleşen oyun formunu on altı siyah kare ile gösterir.](../ide/media/tutorial-windows-forms-create-match-game/match-game-grid-fill.png)

## <a name="next-steps"></a>Sonraki adımlar

Her etikete rastgele bir simge atamayı ve etiketlere olay işleyicileri eklemeyi öğrenmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Eşleşen oyununuza simgeler ekleme](tutorial-windows-forms-match-game-icons.md)

