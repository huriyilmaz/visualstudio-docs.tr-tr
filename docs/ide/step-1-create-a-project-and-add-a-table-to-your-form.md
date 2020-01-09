---
title: '1\. Adım: proje oluşturma ve formunuza tablo ekleme'
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abaae887e39b85e4f2d363a63ef6cde5845e3fa2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597405"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>1\. Adım: proje oluşturma ve formunuza tablo ekleme

Eşleştirme oyunu hazırlarken ilk adım projeyi oluşturmak ve formunuza bir tablo eklemektir. Tablo, simgeleri 4x4'lük muntazam bir kılavuza hizalamaya yardımcı olur. Ayrıca, oyun tahtasının görünüşünü iyileştirmek için çeşitli özellikleri ayarlarsınız.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Bir proje oluşturmak ve formunuza bir tablo eklemek için

::: moniker range="vs-2017"

1. Menü çubuğunda **dosya** > **Yeni** > **Proje**' yi seçin.

1. **Yeni proje** iletişim kutusunun sol tarafındaki **görsel C#**  veya **Visual Basic** seçin ve ardından **Windows Masaüstü**' nu seçin.

1. Şablon listesinde **Windows Forms App (.NET Framework)** şablonunu seçin, *MatchingGame*olarak adlandırın ve **Tamam** düğmesini seçin.

    Seçtiğiniz programlama diline bağlı olarak, *Form1.cs* veya *Form1. vb* adlı bir form görüntülenir.

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **.net masaüstü geliştirme** iş yükünü yüklemek için Visual Studio yükleyicisi kullanın.<br/><br/>Visual Studio Yükleyicisi](../ide/media/dot-net-desktop-dev-workload.png) .NET masaüstü geliştirme iş yükünü ![<br/><br/> Daha fazla bilgi için bkz. [Visual Studio 'Yu Install](../install/install-visual-studio.md) sayfası.

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **Yeni proje oluştur** penceresinde, arama kutusuna *Windows Forms* girin veya yazın. Ardından, **Proje türü** listesinden **Masaüstü** ' ni seçin.

   **Proje türü** filtresini uyguladıktan sonra, C# veya Visual Basic için **Windows Forms App (.NET Framework)** şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Windows Forms uygulama (.NET Framework C# ) için ya da Visual Basic şablonunu seçin](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **Yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Sonra, Visual Studio Yükleyicisi **.net masaüstü geliştirme** Iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi'nde .NET core iş yükü](../ide/media/install-dot-net-desktop-env.png)
   >
   > Bundan sonra Visual Studio Yükleyicisi **Değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin.

1. **Yeni projeyi yapılandırın** penceresinde, **Proje adı** kutusuna *MatchingGame* yazın veya girin. Ardından **Oluştur**' u seçin.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Form özelliklerini ayarlamak için

1. **Özellikler** penceresinde, aşağıdaki form özelliklerini ayarlayın.

   1. Formun **Text** özelliğini **Form1** iken **eşleşen oyunla**değiştirin. Bu metin oyun penceresinin en üstünde görünür.

   2. Formun boyutunu 550 piksel genişliğe ve 550 piksel uzunluğa ayarlayın. Bunu, **Boyut** özelliğini **550, 550**olarak ayarlayarak veya tümleşik geliştirme ortamının sağ alt köşesinde (IDE) doğru boyutu görene kadar formun köşesini sürükleyerek yapabilirsiniz.

2. IDE 'nin sol tarafındaki **araç kutusu** sekmesini seçerek araç kutusunu görüntüleyin.

3. Araç kutusundaki **kapsayıcılar** kategorisinden bir <xref:System.Windows.Forms.TableLayoutPanel> denetimini sürükleyin ve sonra bunun için aşağıdaki özellikleri ayarlayın.

   1. **BackColor** özelliğini **CornflowerBlue**olarak ayarlayın. Bunu yapmak için, **Özellikler** penceresinde **BackColor** özelliğinin yanındaki açılan oku seçerek **BackColor** iletişim kutusunu açın.  Ardından, kullanılabilir renk adlarının listesini görüntülemek için **BackColor** Iletişim kutusundaki **Web** sekmesini seçin.

      > [!NOTE]
      > Renkler alfabetik sırada değildir ve **CornflowerBlue** listenin en altına yakındır.

   2. Özelliğin yanındaki açılan düğmeyi seçerek ve büyük orta düğmesini seçerek, **Dock** özelliğini **Fill** olarak ayarlayın. Böylece tablo formun tamamını kaplayacak şekilde yayılır.

   3. **CellBorderStyle** özelliğini **ınmetinolarak**ayarlayın. Böylece, tahta üzerindeki her bir hücre arasında görsel kenarlıklar olur.

   4. TableLayoutPanel denetiminin sağ üst köşesindeki üçgen düğmesini seçerek ilgili görev menüsünü görüntüleyin.

   5. Görev menüsünde, iki satır daha eklemek için **satır ekle** ' yi seçin ve daha sonra iki sütun eklemek için sütun Iki kez **Ekle** ' yi seçin.

   6. Görev menüsünde **satırları ve sütunları Düzenle** ' yi seçerek **sütun ve satır stilleri** penceresini açın. Sütunların her birini seçin, **yüzde** seçenek düğmesini seçin ve sonra her bir sütunun genişliğini toplam genişliğinin yüzde 25 ' i olarak ayarlayın. Ardından pencerenin üst kısmındaki açılan kutudan **Satırlar** ' ı seçin ve her satırın yüksekliğini yüzde 25 olarak ayarlayın. İşiniz bittiğinde **Tamam** düğmesini seçin.

      TableLayoutPanel denetiminiz şu anda, eşit boyutlu on altı kare hücre içeren 4x4'lük bir kılavuz halinde olmalıdır. Bu satırlar ve sütunlar, sonradan simge resimlerinin görüneceği yerlerdir.

4. Form düzenleyicisinde TableLayoutPanel seçildiğinden emin olun. Bunu doğrulamak için, **Özellikler** penceresinin en üstünde **tableLayoutPanel1** görmeniz gerekir. Seçili değilse, formda TableLayoutPanel öğesini seçin veya **Özellikler** penceresinin en üstündeki açılan denetimde seçin.

    TableLayoutPanel seçiliyken, araç kutusunu açın ve TableLayoutPanel 'in sol üst hücresine bir <xref:System.Windows.Forms.Label> denetimi ( **ortak denetimler** kategorisinde bulunur) ekleyin. Etiket denetimi artık IDE 'de seçilmelidir. Bu öğe için aşağıdaki özellikleri ayarlayın.

   1. Etiketin **BackColor** özelliğinin **CornflowerBlue**olarak ayarlandığından emin olun.

   2. **AutoSize** özelliğini **false**olarak ayarlayın.

   3. **Dock** özelliğini **Fill**olarak ayarlayın.

   4. Özelliğin yanındaki açılan düğmeyi seçerek ve ardından ortadaki düğmeyi seçerek **TextAlign** özelliğini **MiddleCenter** olarak ayarlayın. Böylece, simgenin hücrenin ortasında görünmesi sağlanır.

   5. **Yazı tipi** özelliğini seçin. Üç nokta ( **...** ) düğmesi görünmelidir.

   6. Üç nokta düğmesini seçin ve **yazı tipi** değerini **Web**'e, **yazı tipi stilini** **kalın**olarak ve **Boyut** olarak **48**olarak ayarlayın.

   7. Etiketin **Text** özelliğini **c**harfine ayarlayın.

        TableLayoutPanel öğesinin sol üst hücresinde şimdi, mavi arka plan üzerinde ortalanmış bir siyah kutu yer alıyor olmalıdır.

       > [!NOTE]
       > Webdings yazı tipi, simgelerden oluşan bir yazı tipi olup Windows işletim sistemiyle birlikte gelir. Eşleştirme oyununuzda oyuncunun simge çiftlerini eşleştirmesi gerektiğinden, eşleştirilecek simgeleri göstermek için bu yazı tipini kullanıyorsunuz. **Metin** özelliğine **c** koymak yerine, hangi simgelerin görüntülendiğini görmek için farklı harfler girmeyi deneyin. Ünlem işareti bir örümcek, büyük N harfi bir göz ve virgül ise kırmızı biberdir.

5. Etiket denetiminizi seçin ve TableLayoutPanel içindeki bir sonraki hücreye kopyalayın. ( **Ctrl**+**C** tuşlarını seçin veya menü çubuğunda **Düzenle** > **Kopyala**' yı seçin.) Ardından yapıştırın. ( **Ctrl**+**V** tuşlarını seçin veya menü çubuğunda **Düzenle** > **Yapıştır**' ı seçin.) İlk etiketin bir kopyası TableLayoutPanel 'in ikinci hücresinde görüntülenir. Tekrar yapıştırın ve üçüncü hücrede başka bir etiket görüntülenir. Tüm hücreler dolduruluncaya kadar etiket denetimlerini yapıştırmayı sürdürün.

   > [!NOTE]
   > Çok sayıda yapıştırırsanız, IDE, yeni etiket denetiminizi eklemek için bir yer olmasını sağlamak üzere TableLayoutPanel 'e yeni bir satır ekler. Bunu geri alabilirsiniz. Yeni hücreyi kaldırmak için **Ctrl**+**Z** tuşlarını seçin veya menü çubuğunda **Düzenle** > **geri al**' ı seçin.

    Artık formunuz düzenlenmiştir. Aşağıdaki resme benzer görünmelidir.

    ![Ilk eşleşen oyun formu](../ide/media/express_tut4step1.png)<br/>*İlk eşleşen oyun formu*

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. [2. Adım: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Genel bakış konusuna dönmek için bkz. [öğretici 3: eşleşen oyun oluşturma](../ide/tutorial-3-create-a-matching-game.md).
