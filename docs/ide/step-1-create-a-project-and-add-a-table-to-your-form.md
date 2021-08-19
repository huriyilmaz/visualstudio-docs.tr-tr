---
title: '1. Adım: Proje oluşturma ve formunuza tablo ekleme'
description: Eşleştirme Oyunu projesini oluşturma ve form sayfanıza tablo ekleme hakkında bilgi.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 68f87a6d9e9b601e0226614eb82b8a689d4a6f47
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122040989"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>1. Adım: Proje oluşturma ve formunuza tablo ekleme

Eşleştirme oyunu hazırlarken ilk adım projeyi oluşturmak ve formunuza bir tablo eklemektir. Tablo, simgeleri 4x4'lük muntazam bir kılavuza hizalamaya yardımcı olur. Ayrıca, oyun tahtasının görünüşünü iyileştirmek için çeşitli özellikleri ayarlarsınız.

## <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Bir proje oluşturmak ve formunuza bir tablo eklemek için

::: moniker range="vs-2017"

1. Menü çubuğunda Dosya Yeni **Dosya'Project.** >  > 

1. Yeni Project iletişim **Visual Basic kutusunun sol** tarafındaki Visual  **C#** veya Project'ı seçin ve ardından Masaüstü'Windows **seçin.**

1. Şablon listesinde Windows **Forms Uygulaması (.NET Framework)** şablonunu seçin, *matchingGame* olarak ad girin ve ardından **Tamam düğmesini** seçin.

    Seçtiğiniz programlama diline bağlı *olarak Form1.cs* veya *Form1.vb* adlı bir form görüntülenir.

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız. **.NET** masaüstü Visual Studio Yükleyicisi iş yükünü yüklemek için Visual Studio Yükleyicisi kullanın.<br/><br/>![.NET masaüstü geliştirme iş yükü Visual Studio Yükleyicisi](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Daha fazla bilgi için Yükleme [Visual Studio](../install/install-visual-studio.md) bakın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresini görüntüleme](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde,** arama kutusuna *Windows Formlar* yazın veya yazın. Ardından, uygulama **türü** listesinden **Project'ı** seçin.

   Uygulama türü **filtresini Project** C# **veya Windows için Windows Forms Uygulaması (.NET Framework)** şablonunu seçin ve Visual Basic'yi **seçin.**

   ![Windows Forms Uygulaması için C# veya Visual Basic şablonunu seçin (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Windows Forms Uygulaması **(.NET Framework)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Yükleyicisi **.NET** masaüstü geliştirme iş yükünü seçin.
   >
   > ![.NET Core iş yükü Visual Studio Yükleyicisi](../ide/media/install-dot-net-desktop-env.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; varsa, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin.

1. Yeni **projenizi yapılandır penceresinde,** Yeni projenizin adı kutusuna *MatchingGame* **Project girin.** Ardından **Oluştur'a seçin.**

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Formun özelliklerini ayarlamak için

1. Özellikler **penceresinde** aşağıdaki form özelliklerini ayarlayın.

   1. Formun **Text** özelliğini **Form1'den Eşleştirme** Oyunu **olarak değiştirme.** Bu metin oyun penceresinin en üstünde görünür.

   2. Formun boyutunu 550 piksel genişliğe ve 550 piksel uzunluğa ayarlayın. Bunu yapmak için **Size** özelliğini **550, 550** olarak veya tümleşik geliştirme ortamının (IDE) sağ alt köşesinde doğru boyutu görene kadar formun köşesini sürükleyerek bunu yapabiliriz.

2. IDE'nin sol **tarafındaki Araç** Kutusu sekmesini seçerek araç kutusunu görüntüleyin.

3. Araç <xref:System.Windows.Forms.TableLayoutPanel> kutusunda **Kapsayıcılar kategorisinden** bir denetimi sürükleyin ve ardından bunun için aşağıdaki özellikleri ayarlayın.

   1. **BackColor özelliğini** **CornflowerBlue olarak ayarlayın.** Bunu yapmak için, **Özellikler penceresinde BackColor** özelliğinin yanındaki açılan oku seçerek **BackColor** iletişim **kutusunu** açın.  Ardından, kullanılabilir renk adlarının listesini görüntülemek için **BackColor** iletişim kutusundaki **Web** sekmesini seçin.

      > [!NOTE]
      > Renkler alfabetik sırada değil ve **CornflowerBlue** listenin alt kısmında yer alıyor.

   2. Özelliğin yanındaki açılan **düğmeyi** ve büyük ortadaki düğmeyi seçerek **Dock** özelliğini Fill olarak ayarlayın. Böylece tablo formun tamamını kaplayacak şekilde yayılır.

   3. **CellBorderStyle özelliğini** **Inset olarak ayarlayın.** Böylece, tahta üzerindeki her bir hücre arasında görsel kenarlıklar olur.

   4. TableLayoutPanel denetiminin sağ üst köşesindeki üçgen düğmesini seçerek ilgili görev menüsünü görüntüleyin.

   5. Görev menüsünde, iki satır daha **eklemek için** Satır Ekle'yi iki kez seçin ve sonra iki sütun daha eklemek için Sütun Ekle'yi iki kez seçin. 

   6. Görev menüsünde Satırları ve Sütunları **Düzenle'yi seçen** Sütun ve **Satır Stilleri penceresini** açın. Sütunların her birini seçin, Yüzde **seçeneği** düğmesini seçin ve her sütunun genişliğini toplam genişliğin yüzde 25'ine ayarlayın. Ardından **pencerenin üst** kısmında yer alan açılan kutudan Satırlar'ı seçin ve her satırın yüksekliğini yüzde 25 olarak ayarlayın. Bitirin ve Tamam **düğmesini** seçin.

      TableLayoutPanel denetiminiz şu anda, eşit boyutlu on altı kare hücre içeren 4x4'lük bir kılavuz halinde olmalıdır. Bu satırlar ve sütunlar, sonradan simge resimlerinin görüneceği yerlerdir.

4. Form düzenleyicisinde TableLayoutPanel seçildiğinden emin olun. Bunu doğrulamak için Özellikler penceresinin **üst kısmında tableLayoutPanel1'i** **görüyor** gerekir. Seçili değilse formda TableLayoutPanel'i seçin veya Özellikler penceresinin üst kısmında açılan liste **denetiminde** seçin.

    TableLayoutPanel seçiliyken araç kutusunu açın ve <xref:System.Windows.Forms.Label> TableLayoutPanel'in sol üst hücresine bir denetim (Ortak Denetimler kategorisinde bulunur)  ekleyin. Etiket denetimi artık IDE'de seçilidir. Bu öğe için aşağıdaki özellikleri ayarlayın.

   1. Etiketin **BackColor** özelliğinin **CornflowerBlue olarak ayarlanmış olduğundan emin olun.**

   2. **AutoSize özelliğini** False olarak **ayarlayın.**

   3. Dock özelliğini **Fill** olarak **ayarlayın.**

   4. Özelliğin yanındaki açılan **düğmeyi ve** ardından ortadaki düğmeyi seçerek **TextAlign** özelliğini MiddleCenter olarak ayarlayın. Böylece, simgenin hücrenin ortasında görünmesi sağlanır.

   5. Font **özelliğini** seçin. Üç nokta (**...**) düğmesi görünmektedir.

   6. Üç nokta düğmesini seçin ve  Yazı tipi değerini **Webdings,** Yazı Tipi Stili'nin **Kalın** ve **Boyut** değerini **48 olarak ayarlayın.** 

   7. Etiketin **Text** özelliğini c harfi olarak **ayarlayın.**

        TableLayoutPanel öğesinin sol üst hücresinde şimdi, mavi arka plan üzerinde ortalanmış bir siyah kutu yer alıyor olmalıdır.

       > [!NOTE]
       > Webdings yazı tipi, simgelerden oluşan bir yazı tipi olup Windows işletim sistemiyle birlikte gelir. Eşleştirme oyununuzda oyuncunun simge çiftlerini eşleştirmesi gerektiğinden, eşleştirilecek simgeleri göstermek için bu yazı tipini kullanıyorsunuz. Görüntülenen simgeleri görmek için **Text** özelliğine **c** harfini koymak yerine farklı harfler girmeyi deneyin. Ünlem işareti bir örümcek, büyük N harfi bir göz ve virgül ise kırmızı biberdir.

5. Etiket denetiminizi seçin ve TableLayoutPanel'de sonraki hücreye kopyalayın. **(Ctrl tuşunu seçin** + **C** tuşları veya menü çubuğunda Kopyalamayı   >  **Düzenle'yi seçin.)** Ardından yapıştırın. **(Ctrl tuşunu seçin** + **V** anahtarları veya menü çubuğunda Yapıştır'ı **Düzenle'yi**  >  seçin.) TableLayoutPanel'in ikinci hücresinde ilk Etiketin bir kopyası görüntülenir. Bunu yeniden yapıştırarak üçüncü hücrede başka bir Etiket görünür. Tüm hücreler doldurulana kadar Etiket denetimlerini yapıştırabilirsiniz.

   > [!NOTE]
   > Çok fazla yapıştırırsanız, IDE TableLayoutPanel'e yeni etiket denetiminizi ekleyen bir yer olacak şekilde yeni bir satır ekler. Bunu geri alabilirsiniz. Yeni hücreyi kaldırmak için **Ctrl** Z tuşlarını seçin veya menü çubuğunda Geri +  Al'ı **Düzenle'yi**  >  **seçin.**

    Şimdi formunuz ortaya konur. Aşağıdaki resme benzer bir görünüme sahip olması gerekir.

    ![İlk eşleştirme oyunu formu](../ide/media/express_tut4step1.png)<br/>*İlk eşleştirme oyunu formu*

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için [bkz. 2. Adım: Rastgele nesne ve simge listesi ekleme.](../ide/step-2-add-a-random-object-and-a-list-of-icons.md)

- Genel bakış konu başlığına dönmek için [bkz. Öğretici 3: Eşleşen bir oyun oluşturma.](../ide/tutorial-3-create-a-matching-game.md)
