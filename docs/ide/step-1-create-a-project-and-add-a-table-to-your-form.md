---
title: 'Adım 1: Proje oluşturma ve forma tablo ekleme'
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1134fb5bb02bd8c78f347ef582f12da35074c36
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579925"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>Adım 1: Proje oluşturma ve forma tablo ekleme

Eşleştirme oyunu hazırlarken ilk adım projeyi oluşturmak ve formunuza bir tablo eklemektir. Tablo, simgeleri 4x4'lük muntazam bir kılavuza hizalamaya yardımcı olur. Ayrıca, oyun tahtasının görünüşünü iyileştirmek için çeşitli özellikleri ayarlarsınız.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Bir proje oluşturmak ve formunuza bir tablo eklemek için

::: moniker range="vs-2017"

1. Menü çubuğunda **Yeni** > **Proje** **yi seçin.** >

1. **Yeni Proje** iletişim kutusunun sol tarafındaki **Visual C#** veya **Visual Basic'i** seçin ve ardından **Windows Desktop'ı**seçin.

1. Şablonlar **listesinde, Windows Forms App (.NET Framework)** şablonuna tıklayın, *ona MatchingGame*adını ve ardından **Tamam** düğmesini seçin.

    Seçtiğiniz programlama diline bağlı olarak *Form1.cs* veya *Form1.vb* adlı bir form görüntülenir.

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **.NET masaüstü geliştirme** iş yükünü yüklemek için Visual Studio Yükleyicisini kullanın.<br/><br/>![.NET masaüstü geliştirme iş yükü Visual Studio Installer](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Daha fazla bilgi için [Visual Studio'yu yükle](../install/install-visual-studio.md) sayfasına bakın.

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresinde yeni **bir proje oluştur'u**seçin.

   !['Yeni proje oluşturma' penceresini görüntüleme](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur** penceresinde, arama kutusuna *Windows Formları* girin veya yazın. Ardından, **Proje türü** listesinden **Masaüstü'nü** seçin.

   **Proje türü** filtresini uyguladıktan sonra C# veya Visual Basic için Windows Forms **App (.NET Framework)** şablonunu seçin ve **ardından İleri'yi**seçin.

   ![Windows Forms Uygulaması (.NET Framework) için C# veya Visual Basic şablonundan birini seçin](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Windows Forms App **(.NET Framework)** şablonunu görmüyorsanız, **yeni bir proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisinde, daha **fazla araç ve özellik yükle** bağlantısını seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Aradığınızı bulamıyor' iletisinden 'Daha fazla araç ve özellik yükleyin' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Installer'da **.NET masaüstü geliştirme** iş yükünü seçin'i seçin.
   >
   > ![.NET Core iş yükü Visual Studio Yükleyici](../ide/media/install-dot-net-desktop-env.png)
   >
   > Bundan sonra Visual Studio Installer'daki **Değiştir** düğmesini seçin. Çalışmanızı kaydetmeniz istenebilir; eğer öyleyse, bunu yapın. Ardından, iş yükünü yüklemeye **devam** et'i seçin.

1. Yeni **proje pencerenizi Yapılandır'da,** **Project ad** kutusuna *MatchingGame* yazın veya girin. Ardından **Oluştur'u**seçin.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Form için özellikleri ayarlamak için

1. **Özellikler** penceresinde, aşağıdaki form özelliklerini ayarlayın.

   1. Formun **Metin** özelliğini **Form1'den** **Eşleşen Oyuna**değiştirin. Bu metin oyun penceresinin en üstünde görünür.

   2. Formun boyutunu 550 piksel genişliğe ve 550 piksel uzunluğa ayarlayın. Bunu, **Boyut** özelliğini **550, 550'ye**ayarlayarak veya tümleşik geliştirme ortamının (IDE) sağ alt köşesinde doğru boyutu görene kadar formun köşesini sürükleyerek yapabilirsiniz.

2. IDE'nin sol tarafındaki **Araç Kutusu** sekmesini seçerek araç kutusunu görüntüleyin.

3. Araç <xref:System.Windows.Forms.TableLayoutPanel> kutusundaki **Kapsayıcılar** kategorisinden bir denetim sürükleyin ve ardından bunun için aşağıdaki özellikleri ayarlayın.

   1. **BackColor** özelliğini **CornflowerBlue**olarak ayarlayın. Bunu yapmak için, **Özellikler** penceresindeki **BackColor** özelliğinin yanındaki açılır ok seçerek **BackColor** iletişim kutusunu açın.  Ardından, kullanılabilir renk adlarının listesini görüntülemek için **BackColor** iletişim kutusundaki **Web** sekmesini seçin.

      > [!NOTE]
      > Renkler alfabetik sırada değildir ve **CornflowerBlue** listenin en altında dır.

   2. Tesisin yanındaki açılır düğmeyi seçerek ve büyük orta düğmeyi seçerek **Dock** özelliğini **Doldurma'ya** ayarlayın. Böylece tablo formun tamamını kaplayacak şekilde yayılır.

   3. **CellBorderStyle** özelliğini **Inset**olarak ayarlayın. Böylece, tahta üzerindeki her bir hücre arasında görsel kenarlıklar olur.

   4. TableLayoutPanel denetiminin sağ üst köşesindeki üçgen düğmesini seçerek ilgili görev menüsünü görüntüleyin.

   5. Görev menüsünde, iki satır daha eklemek için Satır **Ekle'yi** iki kez seçin ve sonra iki sütun daha eklemek için **Sütun Ekle'yi** iki kez seçin.

   6. Görev menüsünde, **Sütun ve Satır Stilleri** penceresini açmak için Satır ve **Sütunları Edin'i** seçin. Sütunların her birini seçin, **Yüzde** seçeneği düğmesini seçin ve sonra her sütunun genişliğini toplam genişliğin yüzde 25'ine ayarlayın. Ardından pencerenin üst kısmındaki açılır kutudan **Satırlar'ı** seçin ve her satırın yüksekliğini yüzde 25'e ayarlayın. Bittiğinde Tamam **düğmesini** seçin.

      TableLayoutPanel denetiminiz şu anda, eşit boyutlu on altı kare hücre içeren 4x4'lük bir kılavuz halinde olmalıdır. Bu satırlar ve sütunlar, sonradan simge resimlerinin görüneceği yerlerdir.

4. Form düzenleyicisinde TableLayoutPanel seçildiğinden emin olun. Bunu doğrulamak **için, Özellikler** penceresinin üst kısmında **tabloLayoutPanel1** görmelisiniz. Seçili değilse, formdaki TableLayoutPanel'i seçin veya **Özellikler** penceresinin üst kısmındaki açılır pencerede seçin.

    TableLayoutPanel seçilirken, araç kutusunu açın ve <xref:System.Windows.Forms.Label> TableLayoutPanel'in sol üst hücresine bir denetim **(Ortak Denetimler** kategorisinde yer alır) ekleyin. Etiket denetimi artık IDE'de seçilmelidir. Bu öğe için aşağıdaki özellikleri ayarlayın.

   1. Etiketin **BackColor** özelliğinin **CornflowerBlue**olarak ayarlandıklarından emin olun.

   2. Otomatik **Boyutlandırma** özelliğini **False**olarak ayarlayın.

   3. **Dock** özelliğini **Doldur'a**ayarlayın.

   4. Özelliğin yanındaki açılır düğmeyi seçerek ve ardından orta düğmeyi seçerek **TextAlign** özelliğini **MiddleCenter** olarak ayarlayın. Böylece, simgenin hücrenin ortasında görünmesi sağlanır.

   5. Yazı **Tipi** özelliğini seçin. Bir elips (**...**) düğmesi görünmelidir.

   6. Elips düğmesini seçin ve **Yazı Tipi** değerini **Webdings'e,** **Yazı Tipi Stilini** **Kalın'a**ve **Boyut'u 48'e**ayarlayın. **Size**

   7. Etiketin **Metin** özelliğini **c**harfine ayarlayın.

        TableLayoutPanel öğesinin sol üst hücresinde şimdi, mavi arka plan üzerinde ortalanmış bir siyah kutu yer alıyor olmalıdır.

       > [!NOTE]
       > Webdings yazı tipi, simgelerden oluşan bir yazı tipi olup Windows işletim sistemiyle birlikte gelir. Eşleştirme oyununuzda oyuncunun simge çiftlerini eşleştirmesi gerektiğinden, eşleştirilecek simgeleri göstermek için bu yazı tipini kullanıyorsunuz. **Metin** özelliğine **c** koymak yerine, hangi simgelerin görüntülendiğini görmek için farklı harfler girmeyi deneyin. Ünlem işareti bir örümcek, büyük N harfi bir göz ve virgül ise kırmızı biberdir.

5. Etiket denetiminizi seçin ve TableLayoutPanel'deki bir sonraki hücreye kopyalayın. **(Ctrl**+**C** tuşlarını seçin veya menü çubuğunda **Kopyala'yı Edit'i** > **Copy**seçin.) O zaman yapıştır. **(Ctrl**+**V** tuşlarını seçin veya menü çubuğunda**Yapıştır'ı** **Edit'i** > seçin .) İlk Etiketin bir kopyası TableLayoutPanel'in ikinci hücresinde görünür. Yeniden yapıştırın ve üçüncü hücrede başka bir Etiket görüntülenir. Tüm hücreler dolana kadar Etiket denetimlerini yapıştırma tutun.

   > [!NOTE]
   > Çok fazla yapıştırMa sanız, IDE TableLayoutPanel'e yeni bir satır ekler, böylece yeni Etiket denetiminizi ekleyecek bir yeri olur. Bunu geri alabilirsiniz. Yeni hücreyi kaldırmak için **Ctrl**+**Z** tuşlarını veya menü çubuğunda Geri >  **Al'ı**seçin.**Undo**

    Şimdi formun ortaya kondu. Aşağıdaki resme benzer görünmelidir.

    ![İlk eşleştirme oyunu formu](../ide/media/express_tut4step1.png)<br/>*İlk eşleştirme oyunu formu*

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için [bkz: Adım 2: Rastgele nesne ve simgelerin listesini ekleyin.](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)

- Genel bakış konusuna dönmek için [bkz.](../ide/tutorial-3-create-a-matching-game.md)
