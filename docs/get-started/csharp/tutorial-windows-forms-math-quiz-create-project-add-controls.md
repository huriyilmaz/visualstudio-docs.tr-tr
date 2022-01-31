---
title: "öğretici: ' math test ' Windows Forms uygulaması oluşturma"
description: bir math test uygulaması için C# veya Visual Basic Windows Forms projesi oluşturmayı öğrenin. bir forma uı denetimleri eklemek için Visual Studio ıde 'yi kullanacaksınız.
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
ms.openlocfilehash: ca578f060984521ff945cd060fea4768815a6a18
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137887518"
---
# <a name="tutorial-create-a-math-quiz-winforms-app"></a>Öğretici: matematik testi WinForms uygulaması oluşturma

Bu dört öğreticilerde, bir matematik testi oluşturacaksınız. Test, bir sınavın belirli bir süre içinde yanıt almaya çalışacağı dört rastgele matematik sorunu içerir.

Visual Studio tümleşik geliştirme ortamı (ıde), uygulamayı oluşturmak için ihtiyacınız olan araçları sağlar. bu ıde hakkında daha fazla bilgi edinmek için bkz. [Visual Studio ıde 'ye hoş geldiniz](../visual-studio-ide.md).

Bu ilk öğreticide şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
> - Windows Forms kullanan bir Visual Studio projesi oluşturun.
> - Form için Etiketler, düğme ve diğer denetimler ekleyin.
> - Denetimlerin özelliklerini ayarlayın.
> - Projenizi kaydedin ve çalıştırın.

## <a name="prerequisites"></a>Önkoşullar

bu öğreticiyi tamamlayabilmeniz için Visual Studio gerekir. ücretsiz sürüm için [Visual Studio indirmeleri sayfasını](https://visualstudio.microsoft.com/vs/) ziyaret edin.

## <a name="create-your-windows-forms-project"></a>Windows Forms projenizi oluşturma

bir matematik testi oluşturduğunuzda, ilk adım Windows Forms bir uygulama projesi oluşturmaktır.

::: moniker range="vs-2017"

1. Visual Studio'yu açın.

1. menü çubuğunda **dosya** > **yeni** > **Project**' yi seçin.

1. **yeni Project** iletişim kutusunun sol tarafında, **Visual C#** veya **Visual Basic**' i seçin ve ardından **Windows masaüstü**' nü seçin.

1. proje şablonları listesinde **Windows Forms uygulama (.NET Framework)** öğesini seçin. Yeni formu **MathQuiz** olarak adlandırın ve ardından **Tamam**' ı seçin.

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **.net masaüstü geliştirme** iş yükünü yüklemek için Visual Studio Yükleyicisi kullanın.
   >
   > :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/install-dot-net-desktop-env.png" alt-text="Visual Studio Yükleyicisi 'de nokta ağı masaüstü geliştirme iş yükünü gösteren ekran görüntüsü.":::
   >
   > Daha fazla bilgi için bkz. [ınstall Visual Studio](../../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/create-new-project-dark-theme-2019.png" alt-text="Visual Studio başlangıç penceresinde yeni proje oluştur seçeneğini gösteren ekran görüntüsü.":::

1. **yeni proje oluştur** penceresinde, **Windows Forms** için arama yapın. ardından **Project tür** listesinden **masaüstü** ' nü seçin.

1. C# veya Visual Basic için **Windows Forms App (.NET Framework)** şablonunu seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/create-project-windows-forms.png" alt-text="Yeni proje oluştur iletişim kutusunu gösteren ekran görüntüsü. arama kutusu, Project türü listesi ve iki şablon çağırılır.":::

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz? iletisi için** **daha fazla araç ve özellik yükleyebilirsiniz**' i seçin.
   >
   > :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/install-more-tools.png" alt-text="Yeni proje oluştur iletişim kutusunda ileti aradığınızı bulma hakkında daha fazla araç ve özellik yüklemesi bağlantısını gösteren ekran görüntüsü.":::
   >
   > sonra, Visual Studio Yükleyicisi ' de **.net masaüstü geliştirme**' yi seçin.
   >
   > :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/install-dot-net-desktop-env.png" alt-text="Visual Studio Yükleyicisi 'de nokta ağı masaüstü geliştirme iş yükünü gösteren ekran görüntüsü.":::
   >
   > Visual Studio Yükleyicisi **değiştir** ' i seçin. İşinizi kaydetmeniz istenebilir. Sonra, iş yükünü yüklemek için **devam** ' ı seçin.

1. **Yeni projeyi yapılandırın** penceresinde projenize **MathQuiz** adını yazıp **Oluştur**' u seçin.

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/create-new-project-dark-theme.png" alt-text="Visual Studio başlangıç penceresinde yeni proje oluştur seçeneğini gösteren ekran görüntüsü.":::

1. **yeni proje oluştur** penceresinde, **Windows Forms** için arama yapın. ardından **Project tür** listesinden **masaüstü** ' nü seçin.

1. C# veya Visual Basic için **Windows Forms App (.NET Framework)** şablonunu seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/create-project-windows-forms.png" alt-text="Yeni proje oluştur iletişim kutusunu gösteren ekran görüntüsü. arama kutusu, Project türü listesi ve iki şablon çağırılır.":::

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız, **yeni proje oluştur** penceresinden yükleyebilirsiniz. **Aradığınızı bulamıyor musunuz? iletisi için** **daha fazla araç ve özellik yükleyebilirsiniz**' i seçin.
   >
   > :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/install-more-tools.png" alt-text="Yeni proje oluştur iletişim kutusunda ileti aradığınızı bulma hakkında daha fazla araç ve özellik yüklemesi bağlantısını gösteren ekran görüntüsü.":::
   >
   > sonra, Visual Studio Yükleyicisi ' de **.net masaüstü geliştirme**' yi seçin.
   >
   > :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/install-dot-net-desktop-env.png" alt-text="Visual Studio Yükleyicisi 'de nokta ağı masaüstü geliştirme iş yükünü gösteren ekran görüntüsü.":::
   >
   > Visual Studio Yükleyicisi **değiştir** ' i seçin. İşinizi kaydetmeniz istenebilir. Sonra, iş yükünü yüklemek için **devam** ' ı seçin.

1. **Yeni projeyi yapılandırın** penceresinde projenize **MathQuiz** adını yazıp **Oluştur**' u seçin.

::: moniker-end

Visual Studio, uygulamanız için bir çözüm oluşturur. Çözüm, uygulamanızın ihtiyaç duyacağı tüm proje ve dosyalar için bir kapsayıcıdır.

## <a name="set-form-properties"></a>Form özelliklerini ayarla

şablonunuzu seçtikten ve dosyanızı adınızla, Visual Studio sizin için bir form açar. Bu bölümde, bazı form özelliklerinin nasıl değiştirileceği gösterilmektedir.

1. projenizde **Windows Form Tasarımcısı**' yi seçin. Tasarımcı sekmesi, Visual Basic için C# veya **Form1. vb [Design]** için **Form1. cs [Design]** olarak etiketlenir.

1. , **Form1** formunu seçin.

1. **Özellikler** penceresi artık formun özelliklerini görüntüler. Bu pencere genellikle Visual Studio sağ alt köşesindedir. **Özellikler**' i görmüyorsanız **Özellikler penceresini** **görüntüle**  >  ' yi seçin.

1. **Özellikler** penceresinde **Text** özelliğini bulun. Listenin nasıl sıralandığına bağlı olarak aşağı kaydırmanız gerekebilir. **Metin** değeri Için **matematik testi** değerini girin ve ardından **ENTER**' u seçin.

   Formunuz artık başlık çubuğunda "matematik testi" metnini içeriyor.

   > [!NOTE]
   > Özellikleri kategoriye veya alfabetik olarak gösterebilirsiniz.
   > İleri ve geri dönmek için **Özellikler** penceresindeki düğmeleri kullanın.

1. Formun boyutunu, 400 piksel yüksekliğinde 500 piksel genişliğinde olarak değiştirin.

   **Özellikler** penceresinde **Boyut** değeri olarak doğru boyut görünene kadar, kenarlarını sürükleyerek formu yeniden boyutlandırabilir veya tutamacı sürükleyin. Sürükleme tutamacı, formun sağ alt köşesinde küçük bir beyaz kare olur. Boyut özelliğinin değerlerini değiştirerek de formun **boyutunu** değiştirebilirsiniz.

1. **FormBorderStyle** özelliğinin değerini **Fixed3D** olarak değiştirin ve **MaximizeBox** özelliğini **false** olarak ayarlayın.

     Bu değerler, test takipçilerin formu yeniden boyutlandırmasını engeller.

## <a name="create-the-time-remaining-box"></a>Kalan süre kutusunu oluşturma

Matematik sınavından sağ üst köşedeki bir kutu bulunur. Bu kutu, test içinde kalan saniye sayısını gösterir. Bu bölümde, bu kutu için bir etiketin nasıl kullanılacağı gösterilmektedir. Bu serinin sonraki bir öğreticide geri sayım süreölçeri için kod ekleyeceksiniz.

1. Visual Studio ıde 'nin sol tarafında **araç kutusu** sekmesini seçin. Araç kutusunu görmüyorsanız, menü çubuğundan veya **CTRL** + **alt** + **X**' ten **Görünüm**  >  **araç kutusunu** seçin.

1. <xref:System.Windows.Forms.Label> **Araç kutusunda** denetimi seçin ve ardından form üzerine sürükleyin.

1. **Özellikler** kutusunda etiket için aşağıdaki özellikleri ayarlayın:

   - **(Name)** değerini **timeLabel** olarak ayarlayın.
   - Kutuyu yeniden boyutlandırabilmeniz için **AutoSize** **değerini false** olarak değiştirin.
   - Kutunun etrafına bir çizgi çizmek için **BorderStyle stili** **FixedSingle** olarak değiştirin.
   - **Boyutu** **200, 30** olarak ayarlayın.
   - **Metin** özelliğini seçin ve sonra **metin** değerini temizlemek için **geri al** tuşunu seçin.
   - **Yazı tipi** özelliğinin yanındaki artı işaretini ( **+** ) seçin ve ardından **boyutu** **15,75** olarak ayarlayın.

1. Etiketi formun sağ üst köşesine taşıyın. Mavi yer çizgisi çizgileri görüntülendiğinde, denetimi forma konumlandırmak için bunları kullanın.

1. **Araç kutusundan** başka bir etiket denetimi ekleyin ve ardından yazı tipi boyutunu **15,75** olarak ayarlayın.

1. Bu etiketin **Text** özelliğini **Left zaman** olarak ayarlayın.

1. Etiketi **timeLabel** etiketinin soluna doğru olacak şekilde taşıyın.

   :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/time-remaining-box.png" alt-text="Time Left etiketini ve kalan zaman etiketini gösteren ekran görüntüsü. Denetimler formun sağ üst köşesinde yanlara doğru sıralanır.":::

<!-- Original material -->

## <a name="add-controls-for-the-addition-problem"></a>Ekleme sorunu için denetimler ekleme

Testin ilk bölümü bir ek sorundur. Bu bölümde bu sorunu görüntülemek için etiketleri nasıl kullanabileceğiniz gösterilir.

1. Forma Araç **Kutusundan bir Etiket** denetimi ekleyin.

1. Özellikler **kutusunda** etiket için aşağıdaki özellikleri ayarlayın:

   - Metin olarak **ayarlayın****.** (soru işareti).
   - **AutoSize'i** **False olarak ayarlayın**.
   - Boyut **olarak** **60, 50'ye ayarlayın**.
   - Yazı tipi boyutunu **18 olarak ayarlayın**.
   - **TextAlign'i** **MiddleCenter olarak ayarlayın**.
   - Denetimi **forma** **konumlandırmak için Konum olarak 50, 75'i** ayarlayın.
   - (Ad **) için** **plusLeftLabel olarak ayarlayın**.

1. Formda, oluşturduğunuz **plusLeftLabel** etiketini seçin. **EditCopy veya CtrlC'yi** >  seçerek **etiketi**+ **kopyalayın**.

1. **EditPaste** veya CtrlV tuşlarını **üç kez** >  seçerek etiketi **forma üç**+ **kez** yapıştırın.

1. Üç yeni etiketi **, plusLeftLabel** etiketinin sağ tarafından bir satırda olacak şekilde düzenleme.

1. İkinci etiketin **Text özelliğini (** artı işareti **+** ) olarak ayarlayın.

1. Üçüncü etiketin **(Name) özelliğini** **plusRightLabel olarak ayarlayın**.

1. Dördüncü etiketin **Text özelliğini (** eşittir işareti **=** ) olarak ayarlayın.

1. Forma <xref:System.Windows.Forms.NumericUpDown> Araç **Kutusundan bir** denetim ekleyin. Bu tür denetimler hakkında daha fazla bilgi edinmek için daha sonra bilgi alasiniz.

1. Özellikler **kutusunda** NumericUpDown denetimi için aşağıdaki özellikleri ayarlayın:

   - Yazı tipi boyutunu **18 olarak ayarlayın**.
   - Genişliği **100 olarak ayarlayın**.
   - (Ad **) toplam olarak** **ayarlayın**.

1. NumericUpDown denetimlerini toplama sorunu için Etiket denetimleriyle sırala.

   :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/addition-problem.png" alt-text="Matematik testinin ilk satırı gösteren ekran görüntüsü. Etiketler görünür durumdadır ve ok tuşlarına sahip bir denetim sıfır görüntüler.":::

## <a name="add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Çıkarma, çarpma ve bölme sorunları için denetimler ekleme

Ardından, kalan matematik sorunları için forma etiketler ekleyin.

1. Ekleme sorunu için oluşturduğunuz dört Etiket denetimi ve NumericUpDown denetimi kopyalayın. Bunları forma yapıştırın.

1. Yeni denetimleri toplama denetimlerinin altına doğru yukarı doğru hareket ettirin.

1. Özellikler **kutusunda** , yeni denetimler için aşağıdaki özellikleri ayarlayın:

   - İlk soru **işareti etiketinin (Ad)** adını **minusLeftLabel olarak ayarlayın**.
   - İkinci **etiketin** Metin'ini (eksi **-** işareti) olarak ayarlayın.
   - İkinci soru **işareti etiketinin (Ad)** adını **minusRightLabel olarak ayarlayın**.
   - NumericUpDown denetimi (Name **)** değerini fark olarak **ayarlayın**.

1. Toplama denetimlerini kopyalayın ve forma iki kez daha yapıştırın.

1. Üçüncü satır için:

   - İlk soru **işareti etiketinin (Ad)** adını **timesLeftLabel olarak ayarlayın**.
   - İkinci **etiketin Text** (Metin **) × (** çarpma işareti) olarak ayarlayın. Bu öğreticiden çarpma imzasını kopyalayıp forma yapıştırabilirsiniz.
   - İkinci soru **işareti etiketinin (Ad)** adını **timesRightLabel olarak ayarlayın**.
   - NumericUpDown denetimi (Name **)** değerini product olarak **ayarlayın**.

1. Dördüncü satır için:

   - İlk soru **işareti etiketinin (Ad)** adını **dividedLeftLabel olarak ayarlayın**.
   - İkinci **etiketin Text** (Metin) **÷ (bölme** işareti) olarak ayarlayın. Bu öğreticiden bölme imzasını kopyalayıp forma yapıştırabilirsiniz.
   - İkinci soru **işareti etiketinin (Ad)** adını **dividedRightLabel olarak ayarlayın**.
   - NumericUpDown denetimi (Name **)** değerini **bölüm olarak ayarlayın**.

:::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/all-math-problems.png" alt-text="Dört satır sorun içeren bir matematik testi gösteren ekran görüntüsü. Ok tuşlarına sahip etiketler ve denetimler görünür durumdadır.":::

## <a name="add-a-start-button-and-set-the-tab-index-order"></a>Başlat düğmesi ekleme ve sekme dizini sıralamayı ayarlama

Bu bölümde, başlat düğmesinin nasıl ekli olduğu gösterir. Ayrıca denetimlerin sekme sırası da belirtebilirsiniz. Bu sıralama, Sekme tuşuna basın ve test sonuçlarının bir denetimden bir sonrakine nasıl **ilerler olduğunu** belirler.

1. Forma <xref:System.Windows.Forms.Button> Araç **Kutusundan bir** denetim ekleyin.

1. Özellikler **kutusunda** Düğmenin aşağıdaki özelliklerini ayarlayın:

   - (Ad **) düğmesini** **startButton olarak ayarlayın**.
   - **Metin'i** Testi **başlat olarak ayarlayın**.
   - Yazı tipi boyutunu **14 olarak ayarlayın**.
   - **AutoSize'i** **True olarak** ayarlayın; bu, düğmenin metne sığacak şekilde otomatik olarak yeniden boyutlandırılmanıza neden olur.
   - **TabIndex'i** **0 olarak ayarlayın**. Bu değer start düğmesini odağı alacak ilk denetim yapar.

1. Düğmeyi formun alt kısmında ortalar.

   :::image type="content" source="../media/tutorial-windows-forms-timed-math-quiz/math-problems-start-button.png" alt-text="Dört satır sorun içeren bir matematik testi ve başlat düğmesini gösteren ekran görüntüsü.":::

1. Özellikler **kutusunda** , her NumericUpDown **denetiminde TabIndex** özelliğini ayarlayın:

   - Sum NumericUpDown **denetiminde TabIndex** değerini **1 olarak ayarlayın**.
   - **NumericUpDown** denetimi farkının **TabIndex** değerini **2 olarak ayarlayın**.
   - **NumericUpDown** **ürününün TabIndex** değerini **3 olarak ayarlayın**.
   - NumericUpDown **sekmesinin TabIndex** **değerini** **4 olarak ayarlayın**.

## <a name="run-your-app"></a>Uygulamanızı çalıştırma

Matematik sorunları henüz testte çalışmıyor. Ancak Yine de **TabIndex** değerlerinin beklediğiniz gibi olup olmadığını kontrol etmek için uygulamayı çalıştırabilirsiniz.

1. Aşağıdaki yöntemlerden birini kullanarak uygulamanızı kaydedin:

   - **CtrlShifts'i**++ **seçin**.
   - Menü çubuğunda DosyaSave  > **All seçeneğini belirleyin**.
   - Araç çubuğunda, Tüm Kaydet **düğmesini** seçin.

1. Uygulamalarınızı çalıştırmak için aşağıdaki yöntemlerden birini kullanın:

   - **F5'i seçin**.
   - Menü çubuğunda Hata Ayıkla Hata **Ayıklamayı** **Başlat'ı** >  seçin.
   - Araç çubuğunda Başlat **düğmesini** seçin.

1. Odağın **bir** denetimden sonraki denetime nasıl hareket ettiğinden görmek için Sekme tuşuna birkaç kez tıklayın.

## <a name="next-steps"></a>Sonraki adımlar

Matematik testize rastgele matematik sorunları ve olay işleyicisi eklemek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Öğreticinin 2. bölümü: Matematik testi WinForms uygulamasına matematik sorunları ekleme](tutorial-windows-forms-math-quiz-add-math-problems.md)