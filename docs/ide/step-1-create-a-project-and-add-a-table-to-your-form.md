---
title: '1. Adım: Proje oluşturma ve formunuza tablo ekleme'
description: Eşleşen oyun projesini oluşturma ve formunuza tablo ekleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: e3a9082f645a30bc47c755b50c332d8e3dc47d1c
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397791"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>1. Adım: Proje oluşturma ve formunuza tablo ekleme

Eşleştirme oyunu hazırlarken ilk adım projeyi oluşturmak ve formunuza bir tablo eklemektir. Tablo, simgeleri 4x4'lük muntazam bir kılavuza hizalamaya yardımcı olur. Ayrıca, oyun tahtasının görünüşünü iyileştirmek için çeşitli özellikleri ayarlarsınız.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Bir proje oluşturmak ve formunuza bir tablo eklemek için

::: moniker range="vs-2017"

1. menü çubuğunda **dosya** > **yeni** > **Project**' yi seçin.

1. **yeni Project** iletişim kutusunun sol tarafındaki **Visual C#** veya **Visual Basic** seçin, sonra da **Windows masaüstü**' ne tıklayın.

1. şablon listesinde **Windows Forms App (.NET Framework)** şablonunu seçin, *matchinggame* olarak adlandırın ve **tamam** düğmesini seçin.

    Seçtiğiniz programlama diline bağlı olarak *Form1. cs* veya *Form1. vb* adlı bir form görüntülenir.

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **.net masaüstü geliştirme** iş yükünü yüklemek için Visual Studio Yükleyicisi kullanın.<br/><br/>![Visual Studio Yükleyicisi .net masaüstü geliştirme iş yükü](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> daha fazla bilgi için, [Visual Studio yüklemesi](../install/install-visual-studio.md) sayfasına bakın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. **yeni proje oluştur** penceresinde, arama kutusuna *Windows Forms* girin veya yazın. sonra, **Project türü** listesinden **masaüstü** ' ne tıklayın.

   **Project tür** filtresini uyguladıktan sonra C# veya Visual Basic için **Windows Forms uygulama (.NET Framework)** şablonunu seçin ve ardından **ileri**' yi seçin.

   ![Windows Forms uygulaması için C# veya Visual Basic şablonunu seçin (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz?** iletisi için **daha fazla araç ve özellik yüklemeyi** seçin bağlantısına tıklayın.
   >
   > ![' Yeni proje oluştur ' penceresindeki ' daha fazla araç ve özellik yüklemesi ' ' ne aradığınızı bulma ' iletisi bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > sonra, Visual Studio Yükleyicisi **.net masaüstü geliştirme** iş yükünü seçin.
   >
   > ![Visual Studio Yükleyicisi .net Core iş yükü](../ide/media/install-dot-net-desktop-env.png)
   >
   > bundan sonra Visual Studio Yükleyicisi **değiştir** düğmesini seçin. İşinizi kaydetmeniz istenebilir; Öyleyse, bunu yapın. Sonra, iş yükünü yüklemek için **devam** ' ı seçin.

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *matchinggame* yazın veya girin. Ardından **Oluştur**' u seçin.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Form özelliklerini ayarlamak için

1. **Özellikler** penceresinde, aşağıdaki form özelliklerini ayarlayın.

   1. Formun **Text** özelliğini **Form1** iken **eşleşen oyunla** değiştirin. Bu metin oyun penceresinin en üstünde görünür.

   2. Formun boyutunu 550 piksel genişliğe ve 550 piksel uzunluğa ayarlayın. Bunu, **Boyut** özelliğini **550, 550** olarak ayarlayarak veya tümleşik geliştirme ortamının sağ alt köşesinde (IDE) doğru boyutu görene kadar formun köşesini sürükleyerek yapabilirsiniz.

2. IDE 'nin sol tarafındaki **araç kutusu** sekmesini seçerek araç kutusunu görüntüleyin.

3. <xref:System.Windows.Forms.TableLayoutPanel>Araç kutusundaki **kapsayıcılar** kategorisinden bir denetim sürükleyin ve sonra bunun için aşağıdaki özellikleri ayarlayın.

   1. **BackColor** özelliğini **CornflowerBlue** olarak ayarlayın. Bunu yapmak için, **Özellikler** penceresinde **BackColor** özelliğinin yanındaki açılan oku seçerek **BackColor** iletişim kutusunu açın.  Ardından, kullanılabilir renk adlarının listesini görüntülemek için **BackColor** Iletişim kutusundaki **Web** sekmesini seçin.

      > [!NOTE]
      > Renkler alfabetik sırada değildir ve **CornflowerBlue** listenin en altına yakındır.

   2. Özelliğin yanındaki açılan düğmeyi seçerek ve büyük orta düğmesini seçerek, **Dock** özelliğini **Fill** olarak ayarlayın. Böylece tablo formun tamamını kaplayacak şekilde yayılır.

   3. **CellBorderStyle** özelliğini **ınmetinolarak** ayarlayın. Böylece, tahta üzerindeki her bir hücre arasında görsel kenarlıklar olur.

   4. TableLayoutPanel denetiminin sağ üst köşesindeki üçgen düğmesini seçerek ilgili görev menüsünü görüntüleyin.

   5. Görev menüsünde, iki satır daha eklemek için **satır ekle** ' yi seçin ve daha sonra iki sütun eklemek için sütun Iki kez **Ekle** ' yi seçin.

   6. Görev menüsünde **satırları ve sütunları Düzenle** ' yi seçerek **sütun ve satır stilleri** penceresini açın. Sütunların her birini seçin, **yüzde** seçenek düğmesini seçin ve sonra her bir sütunun genişliğini toplam genişliğinin yüzde 25 ' i olarak ayarlayın. Ardından pencerenin üst kısmındaki açılan kutudan **Satırlar** ' ı seçin ve her satırın yüksekliğini yüzde 25 olarak ayarlayın. İşiniz bittiğinde **Tamam** düğmesini seçin.

      TableLayoutPanel denetiminiz şu anda, eşit boyutlu on altı kare hücre içeren 4x4'lük bir kılavuz halinde olmalıdır. Bu satırlar ve sütunlar, sonradan simge resimlerinin görüneceği yerlerdir.

4. Form düzenleyicisinde TableLayoutPanel seçildiğinden emin olun. Bunu doğrulamak için, **Özellikler** penceresinin en üstünde **tableLayoutPanel1** görmeniz gerekir. Seçili değilse, formda TableLayoutPanel öğesini seçin veya **Özellikler** penceresinin en üstündeki açılan denetimde seçin.

    TableLayoutPanel seçiliyken, araç kutusunu açın ve <xref:System.Windows.Forms.Label> TableLayoutPanel 'in sol üst hücresine bir denetim ( **ortak denetimler** kategorisinde bulunur) ekleyin. Etiket denetimi artık IDE 'de seçilmelidir. Bu öğe için aşağıdaki özellikleri ayarlayın.

   1. Etiketin **BackColor** özelliğinin **CornflowerBlue** olarak ayarlandığından emin olun.

   2. **AutoSize** özelliğini **false** olarak ayarlayın.

   3. **Dock** özelliğini **Fill** olarak ayarlayın.

   4. Özelliğin yanındaki açılan düğmeyi seçerek ve ardından ortadaki düğmeyi seçerek **TextAlign** özelliğini **MiddleCenter** olarak ayarlayın. Böylece, simgenin hücrenin ortasında görünmesi sağlanır.

   5. **Yazı tipi** özelliğini seçin. Üç nokta (**...**) düğmesi görünmelidir.

   6. Üç nokta düğmesini seçin ve **yazı tipi** değerini **Web**'e, **yazı tipi stilini** **kalın** olarak ve **Boyut** olarak **48** olarak ayarlayın.

   7. Etiketin **Text** özelliğini **c** harfine ayarlayın.

        TableLayoutPanel öğesinin sol üst hücresinde şimdi, mavi arka plan üzerinde ortalanmış bir siyah kutu yer alıyor olmalıdır.

       > [!NOTE]
       > Webdings yazı tipi, simgelerden oluşan bir yazı tipi olup Windows işletim sistemiyle birlikte gelir. Eşleştirme oyununuzda oyuncunun simge çiftlerini eşleştirmesi gerektiğinden, eşleştirilecek simgeleri göstermek için bu yazı tipini kullanıyorsunuz. **Metin** özelliğine **c** koymak yerine, hangi simgelerin görüntülendiğini görmek için farklı harfler girmeyi deneyin. Ünlem işareti bir örümcek, büyük N harfi bir göz ve virgül ise kırmızı biberdir.

5. Etiket denetiminizi seçin ve TableLayoutPanel içindeki bir sonraki hücreye kopyalayın. ( **CTRL** + 'yi seçin **C** tuşları, ya da menü çubuğunda kopyayı **Düzenle**' yi seçin  >  .) Ardından yapıştırın. ( **CTRL** + 'yi seçin **V** tuşları, ya da menü çubuğunda yapıştırmayı **Düzenle**' yi seçin  >  .) İlk etiketin bir kopyası TableLayoutPanel 'in ikinci hücresinde görüntülenir. Tekrar yapıştırın ve üçüncü hücrede başka bir etiket görüntülenir. Tüm hücreler dolduruluncaya kadar etiket denetimlerini yapıştırmayı sürdürün.

   > [!NOTE]
   > Çok sayıda yapıştırırsanız, IDE, yeni etiket denetiminizi eklemek için bir yer olmasını sağlamak üzere TableLayoutPanel 'e yeni bir satır ekler. Bunu geri alabilirsiniz. Yeni hücreyi kaldırmak için **CTRL** + **Z** tuşlarını seçin veya menü çubuğunda   >  **geri al**'ı Düzenle ' yi seçin.

    Artık formunuz düzenlenmiştir. Aşağıdaki resme benzer görünmelidir.

    ![İlk eşleştirme oyunu formu](../ide/media/express_tut4step1.png)<br/>*İlk eşleştirme oyunu formu*

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. [2. Adım: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Genel bakış konusuna dönmek için bkz. [öğretici 3: eşleşen oyun oluşturma](../ide/tutorial-3-create-a-matching-game.md).
