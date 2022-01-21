---
title: "Öğretici: Forms Uygulaması'Windows 'matematik testi' oluşturma"
description: Matematik testi uygulaması için C# veya Visual Basic Windows Forms projesi oluşturma hakkında bilgi. Kullanıcı arabirimi denetimlerini bir Visual Studio eklemek için IDE'nin ilk kullanıcı arabirimini kullanabilirsiniz.
ms.custom:
- vs-acquisition
ms.date: 01/20/2022
ms.topic: tutorial
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d6e4dc6b111c6c72987d5404838695661957be1f
ms.sourcegitcommit: 7746657b87b22a7684e79e508af598b02dfe24b7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/21/2022
ms.locfileid: "137610039"
---
# <a name="tutorial-create-a-math-quiz-winforms-app"></a>Öğretici: Matematik testi WinForms uygulaması oluşturma

Bu dört öğretici serisinde matematik testi oluşturacak. Test, bir sınav sınavını belirli bir süre içinde yanıtlamaya çalışan dört rastgele matematik sorunu içerir.

Tümleşik Visual Studio ortamı (IDE), uygulamayı oluşturmak için ihtiyacınız olan araçları sağlar. Bu IDE hakkında daha fazla bilgi edinmek için [bkz. IDE'Visual Studio hoş geldiniz.](../get-started/visual-studio-ide.md)

Bu ilk öğreticide şunların nasıl olduğunu öğrenirsiniz:

> [!div class="checklist"]
> - Windows Forms Visual Studio bir Windows oluşturun.
> - Bir forma etiket, düğme ve diğer denetimler ekleyin.
> - Denetimlerin özelliklerini ayarlayın.
> - Projenizi kaydedin ve çalıştırın.

## <a name="prerequisites"></a>Önkoşullar

Bu öğreticiyi Visual Studio için bir adıma ihtiyacınız var. Ücretsiz sürüm [Visual Studio indirmeler](https://visualstudio.microsoft.com/vs/) sayfasını ziyaret edin.

## <a name="create-your-windows-forms-project"></a>Windows Forms projenizi oluşturma

Matematik testi oluşturmanın ilk adımı, Windows Forms Uygulaması projesi oluşturmaktır.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. Menü çubuğunda Dosya Yeni'yi **seçin** > **ve** > **Project.**

1. Yeni Uygulama iletişim kutusunun sol **Project** **Visual C#** veya Visual Basic seçin ve ardından Masaüstü'Windows **seçin.**

1. Proje şablonları listesinde, Windows **Forms Uygulaması (.NET Framework) öğesini seçin.** Yeni formu **MathQuiz olarak ve ardından** Tamam'ı **seçin.**

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız.NET masaüstü Visual Studio Yükleyicisi iş yükünü yüklemek **için Visual Studio Yükleyicisi kullanın.**
   >
   > :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/install-dot-net-desktop-env.png" alt-text="Visual Studio Yükleyicisi'daki nokta NET masaüstü geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.":::
   >
   > Daha fazla bilgi için [bkz. Yükleme Visual Studio.](../install/install-visual-studio.md)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/create-new-project-dark-theme-2019.png" alt-text="Yeni proje oluştur seçeneğini başlangıç penceresinde gösteren Visual Studio görüntüsü.":::

1. Yeni proje **oluştur penceresinde formlar** için **Windows.** Ardından, **Project** **türü listesinden Desktop'ı** seçin.

1. C# Windows formlar için .NET Framework Forms Uygulaması **(.NET Framework)** şablonunu seçin ve Visual Basic'yi **seçin.**

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/create-project-windows-forms.png" alt-text="Yeni proje oluştur iletişim kutusunu gösteren ekran görüntüsü. Arama kutusu, Project türü listesi ve iki şablon çağrılır.":::

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde Daha** fazla araç ve **özellik yükle'yi seçin.**
   >
   > :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/install-more-tools.png" alt-text="Yeni proje oluştur iletişim kutusunda Arayıcınız ne arıyorsanız yok iletisinden Daha fazla araç ve özellik yükle bağlantısını gösteren ekran görüntüsü.":::
   >
   > Ardından, Visual Studio Yükleyicisi **.NET masaüstü geliştirme'yi seçin.**
   >
   > :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/install-dot-net-desktop-env.png" alt-text="Visual Studio Yükleyicisi'daki nokta NET masaüstü geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.":::
   >
   > Dosyada **Değiştir'Visual Studio Yükleyicisi.** Çalışmanızı kaydetmeniz istendiğinde. Ardından, iş yükünü **yüklemek için** Devam'ı seçin.

1. Yeni **projenizi yapılandır penceresinde projenize** **MathQuiz** adını ve ardından Oluştur'a **tıklayın.**

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/create-new-project-dark-theme.png" alt-text="Yeni proje oluştur seçeneğini başlangıç penceresinde gösteren Visual Studio görüntüsü.":::

1. Yeni proje **oluştur penceresinde formlar** için **Windows.** Ardından, **Project** **türü listesinden Desktop'ı** seçin.

1. C# Windows formlar için .NET Framework Forms Uygulaması **(.NET Framework)** şablonunu seçin ve Visual Basic'yi **seçin.**

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/create-project-windows-forms.png" alt-text="Yeni proje oluştur iletişim kutusunu gösteren ekran görüntüsü. Arama kutusu, Project türü listesi ve iki şablon çağrılır.":::

   > [!NOTE]
   > **Windows Forms Uygulaması (.NET Framework)** şablonunu görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde Daha** fazla araç ve **özellik yükle'yi seçin.**
   >
   > :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/install-more-tools.png" alt-text="Yeni proje oluştur iletişim kutusunda Arayıcınız ne arıyorsanız yok iletisinden Daha fazla araç ve özellik yükle bağlantısını gösteren ekran görüntüsü.":::
   >
   > Ardından, Visual Studio Yükleyicisi **.NET masaüstü geliştirme'yi seçin.**
   >
   > :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/install-dot-net-desktop-env.png" alt-text="Visual Studio Yükleyicisi'daki nokta NET masaüstü geliştirme iş yükünü gösteren Visual Studio Yükleyicisi.":::
   >
   > Dosyada **Değiştir'Visual Studio Yükleyicisi.** Çalışmanızı kaydetmeniz istendiğinde. Ardından, iş yükünü **yüklemek için** Devam'ı seçin.

1. Yeni **projenizi yapılandır penceresinde projenize** **MathQuiz** adını ve ardından Oluştur'a **tıklayın.**

::: moniker-end

Visual Studio için bir çözüm oluşturur. Çözüm, uygulamanıza gereken tüm projeler ve dosyalar için bir kapsayıcıdır.

## <a name="set-form-properties"></a>Form özelliklerini ayarlama

Şablon seçin ve dosyanıza bir ad verdikten sonra Visual Studio form açılır. Bu bölümde bazı form özelliklerini nasıl değiştiryebilirsiniz?

1. Projenizin Form **Tasarımcısı'Windows seçin.** Tasarımcı sekmesi C# için **Form1.cs [Tasarım]** veya **form1.vb [Tasarım]** Visual Basic.

1. **Form1 formunu seçin.**

1. Özellikler **penceresi** artık formun özelliklerini görüntüler. Bu pencere genellikle pencerenin sağ alt Visual Studio. Özellikler'i görmüyorsanız **Özellikler** Penceresini   >  **Görüntüle'yi seçin.**

1. Özellikler **penceresinde Text** **özelliğini** bulun. Listenin nasıl sıralanmış olduğunu bağlı olarak, aşağı kaydırmak için ihtiyacınız olabilir. Metin değeri için **Matematik Testi** değerini **girin ve** Enter tarak **seçin.**

   Formunuz artık başlık çubuğunda "Matematik Testi" metnine sahip.

   > [!NOTE]
   > Özellikleri kategoriye veya alfabetik olarak görüntüebilirsiniz.
   > Geri ve ileri geçiş **yapmak** için Özellikler penceresindeki düğmeleri kullanın.

1. Formun boyutunu 500 piksel genişliğinde ve 400 piksel uzunluğunda olacak şekilde değiştirebilirsiniz.

   Özellikler penceresinde Boyut değeri olarak doğru boyut görünene kadar kenarlarını sürükleyerek veya tutamacı **sürükleyerek** formu yeniden **boyutlandırabilirsiniz.** Sürükleme tutamacı, formun sağ alt köşesindeki küçük bir beyaz karedir. Size özelliğinin değerlerini değiştirerek de formu yeniden **boyutlandırabilirsiniz.**

1. **FormBorderStyle özelliğinin değerini** **Fixed3D** olarak ve **MaximizeBox özelliğini False** olarak **ayarlayın.**

     Bu değerler, test alan kullanıcıların formu yeniden boyutlandırmasını önler.

## <a name="create-the-time-remaining-box"></a>Kalan zamanı oluşturma kutusu

Matematik testi, sağ üst köşede bir kutu içerir. Bu kutu, testte kalan saniye sayısını gösterir. Bu bölümde, bu kutu için nasıl etiket kullanabileceğiniz gösterir. Bu serinin sonraki bir öğreticisinde geri sayım zamanlayıcısı için kod eksersiniz.

1. IDE'nin sol Visual Studio Araç Kutusu **sekmesini** seçin. Araç kutusunu görmüyorsanız menü çubuğundan Araç Kutusunu **Görüntüle'yi**  >  **veya** **Ctrl** Alt X + **tuşlarını** + **kullanın.**

1. Araç <xref:System.Windows.Forms.Label> Kutusunda denetimi **seçin ve** forma sürükleyin.

1. Özellikler **kutusunda** etiket için aşağıdaki özellikleri ayarlayın:

   - **(Ad) için** **timeLabel olarak ayarlayın.**
   - Kutuyu **yeniden boyutlandırmak için AutoSize'i** **False** olarak değiştirme.
   - Kutunun etrafında bir çizgi çizmek için **BorderStyle'i** **FixedSingle** olarak değiştirebilirsiniz.
   - Boyut **olarak** **200, 30'a ayarlayın.**
   - Text **özelliğini** seçin ve ardından Geri Al **tuşuna basın** ve Text değerinin **temizlerini** seçin.
   - Font özelliğinin yanındaki artı () işaretine ( ) ve ardından Boyut'ı **+** **15,75 olarak ayarlayın.**  

1. Etiketi formun sağ üst köşesine taşıma. Mavi boşluk çizgileri görüntüde, formun üzerinde denetimi konumlandırmak için bunları kullanın.

1. Araç Kutusundan başka bir Etiket **denetimi ekleyin** ve ardından yazı tipi boyutunu **15,75 olarak ayarlayın.**

1. Bu etiketin **Text özelliğini Time** **Left olarak ayarlayın.**

1. Etiketi **timeLabel** etiketinin sol tarafından yukarı doğru sıra olacak şekilde hareket ettirin.

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/time-remaining-box.png" alt-text="Time Left etiketini ve kalan zaman etiketini gösteren ekran görüntüsü. Denetimler formun sağ üst köşesinde yanlara doğru sıralanır.":::

<!-- Original material -->

## <a name="add-controls-for-the-addition-problem"></a>Ekleme sorunu için denetimler ekleme

Testin ilk bölümü bir ek sorundur. Bu bölümde bu sorunu görüntülemek için etiketleri nasıl kullanabileceğiniz gösterilir.

1. Forma Araç **Kutusundan bir Etiket** denetimi ekleyin.

1. Özellikler **kutusunda** etiket için aşağıdaki özellikleri ayarlayın:

   - Metin olarak **ayarlayın.**  (soru işareti).
   - **AutoSize'i** False olarak **ayarlayın.**
   - Boyut **olarak** **60, 50'ye ayarlayın.**
   - Yazı tipi boyutunu **18 olarak ayarlayın.**
   - **TextAlign'i** **MiddleCenter olarak ayarlayın.**
   - Denetimi **forma** **konumlandırmak için Konum olarak 50, 75'i** ayarlayın.
   - **(Ad) için** **plusLeftLabel olarak ayarlayın.**

1. Formda, oluşturduğunuz **plusLeftLabel** etiketini seçin. Kopyala'yi Düzenle veya   >  Ctrl C **tuşlarını** **seçerek etiketi** + **kopyalayın.**

1. Yapıştır'ı Düzenle veya Ctrl V'yi üç **kez**  >   seçerek etiketi  + **forma üç kez** yapıştırın.

1. Üç yeni **etiketi, plusLeftLabel** etiketinin sağ tarafından bir satırda olacak şekilde düzenleme.

1. İkinci etiketin Text özelliğini **(artı** **+** işareti) olarak ayarlayın.

1. Üçüncü etiketin **(Name) özelliğini** **plusRightLabel olarak ayarlayın.**

1. Dördüncü etiketin **Text özelliğini (eşittir** **=** işareti) olarak ayarlayın.

1. Forma <xref:System.Windows.Forms.NumericUpDown> Araç **Kutusundan bir** denetim ekleyin. Bu tür denetimler hakkında daha fazla bilgi edinmek için daha sonra bilgi alasiniz.

1. Özellikler **kutusunda** NumericUpDown denetimi için aşağıdaki özellikleri ayarlayın:

   - Yazı tipi boyutunu **18 olarak ayarlayın.**
   - Genişliği **100 olarak ayarlayın.**
   - **(Ad) toplam olarak** **ayarlayın.**

1. NumericUpDown denetimlerini toplama sorunu için Etiket denetimleriyle sırala.

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/addition-problem.png" alt-text="Matematik testinin ilk satırı gösteren ekran görüntüsü. Etiketler görünür durumdadır ve ok tuşlarına sahip bir denetim sıfır görüntüler.":::

## <a name="add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Çıkarma, çarpma ve bölme sorunları için denetimler ekleme

Ardından, kalan matematik sorunları için forma etiketler ekleyin.

1. Ekleme sorunu için oluşturduğunuz dört Etiket denetimi ve NumericUpDown denetimi kopyalayın. Bunları forma yapıştırın.

1. Yeni denetimleri toplama denetimlerinin altına doğru yukarı doğru hareket ettirin.

1. Özellikler **kutusunda,** yeni denetimler için aşağıdaki özellikleri ayarlayın:

   - İlk soru **işareti etiketinin (Ad)** adını **minusLeftLabel olarak ayarlayın.**
   - İkinci **etiketin** Metin'ini **-** (eksi işareti) olarak ayarlayın.
   - İkinci soru **işareti etiketinin (Ad)** adını **minusRightLabel olarak ayarlayın.**
   - NumericUpDown **denetimi (Name)** değerini fark olarak **ayarlayın.**

1. Toplama denetimlerini kopyalayın ve forma iki kez daha yapıştırın.

1. Üçüncü satır için:

   - İlk soru **işareti etiketinin (Ad)** adını **timesLeftLabel olarak ayarlayın.**
   - İkinci **etiketin Text** (Metin) **×** (çarpma işareti) olarak ayarlayın. Bu öğreticiden çarpma imzasını kopyalayıp forma yapıştırabilirsiniz.
   - İkinci soru **işareti etiketinin (Ad)** adını **timesRightLabel olarak ayarlayın.**
   - NumericUpDown **denetimi (Name)** değerini product olarak **ayarlayın.**

1. Dördüncü satır için:

   - İlk soru **işareti etiketinin (Ad)** adını **dividedLeftLabel olarak ayarlayın.**
   - İkinci **etiketin Text** (Metin) ÷ **(bölme** işareti) olarak ayarlayın. Bu öğreticiden bölme imzasını kopyalayıp forma yapıştırabilirsiniz.
   - İkinci soru **işareti etiketinin (Ad)** adını **dividedRightLabel olarak ayarlayın.**
   - NumericUpDown **denetimi (Name)** değerini **bölüm olarak ayarlayın.**

:::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/all-math-problems.png" alt-text="Dört satır sorun içeren bir matematik testi gösteren ekran görüntüsü. Ok tuşlarına sahip etiketler ve denetimler görünür durumdadır.":::

## <a name="add-a-start-button-and-set-the-tab-index-order"></a>Başlat düğmesi ekleme ve sekme dizini sıralamayı ayarlama

Bu bölümde, başlat düğmesinin nasıl ekli olduğu gösterir. Ayrıca denetimlerin sekme sırası da belirtebilirsiniz. Bu sıralama, Sekme tuşuna basın ve test sonuçlarının bir denetimden bir sonrakine nasıl **ilerler olduğunu** belirler.

1. Forma <xref:System.Windows.Forms.Button> Araç **Kutusundan bir** denetim ekleyin.

1. Özellikler **kutusunda** Düğmenin aşağıdaki özelliklerini ayarlayın:

   - **(Ad) için** **startButton ayarlayın.**
   - **Metin'i Testi** **başlat olarak ayarlayın.**
   - Yazı tipi boyutunu **14 olarak ayarlayın.**
   - **AutoSize'i** **True olarak ayarlayın.** Bu, düğmenin metne sığacak şekilde otomatik olarak yeniden boyutlandırılmalarını sağlar.
   - **TabIndex'i** **0 olarak ayarlayın.** Bu değer start düğmesini odağı alacak ilk denetim yapar.

1. Düğmeyi formun alt kısmında ortalar.

   :::image type="content" source="./media/tutorial-windows-forms-timed-math-quiz/math-problems-start-button.png" alt-text="Dört satır sorun içeren bir matematik testi ve başlat düğmesini gösteren ekran görüntüsü.":::

1. Özellikler **kutusunda,** her NumericUpDown **denetiminde TabIndex** özelliğini ayarlayın:

   - Sum NumericUpDown **denetiminde** **TabIndex** değerini **1 olarak ayarlayın.**
   - **NumericUpDown** denetimi farkının **TabIndex** değerini **2 olarak ayarlayın.**
   - **NumericUpDown** **ürününün TabIndex** değerini **3 olarak ayarlayın.**
   - NumericUpDown **sekmesinin TabIndex** **değerini** **4 olarak ayarlayın.**

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

Matematik sorunları henüz testte çalışmıyor. Ancak Yine de **TabIndex** değerlerinin beklediğiniz gibi olup olmadığını kontrol etmek için uygulamayı çalıştırabilirsiniz.

1. Aşağıdaki yöntemlerden birini kullanarak uygulamanızı kaydedin:

   - **Ctrl Shift** +  + **S'yi seçin.**
   - Menü çubuğunda Dosya Hepsini **Kaydet'i**  >  **seçin.**
   - Araç çubuğunda, Tüm Kaydet **düğmesini** seçin.

1. Uygulamalarınızı çalıştırmak için aşağıdaki yöntemlerden birini kullanın:

   - **F5'i seçin.**
   - Menü çubuğunda Hata Ayıklama Hata **Ayıklamayı**  >  **Başlat'ı seçin.**
   - Araç çubuğunda Başlat **düğmesini** seçin.

1. Odağın **bir** denetimden sonraki denetime nasıl hareket ettiğinden görmek için Sekme tuşuna birkaç kez tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Matematik testize rastgele matematik sorunları ve olay işleyicisi eklemek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Öğreticinin 2. bölümü: Matematik testi WinForms uygulamasına matematik sorunları ekleme](tutorial-windows-forms-math-quiz-add-math-problems.md)