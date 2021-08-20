---
title: '1. Adım: Proje oluşturma ve formunuza etiketler ekleme'
description: Bir forma proje oluşturmayı, etiket, düğme ve diğer denetimleri eklemeyi ve eklediğiniz her denetim için özellikleri ayarlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
author: j-martens
ms.author: jmartens
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: cb535463f2f7213923e6c7964d5663dcad5dc2a5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150943"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>1. Adım: Proje oluşturma ve formunuza etiketler ekleme

Bu testi geliştirmenin ilk adımı olarak, projeyi oluşturur ve bir forma Etiketler, bir düğme ve diğer denetimler eklersiniz. Eklediğiniz her denetim için de Özellikler ayarlarsınız. Proje formu, denetimleri ve (öğreticide daha sonra) kodu içerecektir. Düğme, testi başlatır, Etiketler test sorunlarını gösterir ve diğer denetimler, test yanıtlarını ve testi tamamlaması için kalan süreyi gösterir.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-project-for-a-form"></a>Form için bir proje oluşturmak için

::: moniker range="vs-2017"

1. menü çubuğunda **dosya** > **yeni** > **Project**' yi seçin.

1. **yeni Project** iletişim kutusunun sol tarafındaki **Visual C#** veya **Visual Basic** seçin, sonra da **Windows masaüstü**' ne tıklayın.

1. şablon listesinde **Windows Forms App (.NET Framework)** şablonunu seçin, *MathQuiz* olarak adlandırın ve **tamam** düğmesini seçin.

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

1. **yeni projeyi yapılandırın** penceresinde, **Project adı** kutusuna *MathQuiz* yazın veya girin. Ardından **Oluştur**' u seçin.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Form özelliklerini ayarlamak için

1. Visual Studio, formu seçin (programlama diline bağlı olarak *form1. cs* veya *form1. vb*) ve ardından **Text** özelliğini **matematik sınavına** değiştirin.

     **Özellikler** penceresi form özelliklerini içerir.

1. Formun boyutunu, 400 piksel yüksekliğinde 500 piksel genişliğinde olarak değiştirin.

     Tümleşik geliştirme ortamının (IDE) sol alt köşesinde doğru boyut görünene kadar, kenarlarını sürükleyerek formu yeniden boyutlandırabilirsiniz. Alternatif olarak, **size** özelliğinin değerlerini değiştirebilirsiniz.

1. **FormBorderStyle** özelliğinin değerini **Fixed3D** olarak değiştirin ve **MaximizeBox** özelliğini **false** olarak ayarlayın.

     Bu değerler, test takipçilerin formu yeniden boyutlandırmasını engeller.

## <a name="to-create-the-time-remaining-box"></a>Kalan süre kutusunu oluşturmak için

1. <xref:System.Windows.Forms.Label> **Araç kutusundan** bir denetim ekleyin ve sonra **(Name)** özelliğinin değerini **timeLabel** olarak ayarlayın.

     Bu etiket, sağ üst köşede, test içinde kalan saniye sayısını gösteren bir kutu olur.

2. Kutuyu yeniden boyutlandırabilmeniz için **AutoSize** özelliğini **false** olarak değiştirin.

3. Kutunun çevresinde bir çizgi çizmek için **BorderStyle** özelliğini **FixedSingle** olarak değiştirin.

4. **Boyut** özelliğini **200, 30** olarak ayarlayın.

5. Etiketi formun sağ üst köşesine taşıyın, burada mavi yer çizgisi çizgileri görünür.

     Bu satırlar formdaki denetimleri hizalamaya yardımcı olur.

6. **Özellikler** penceresinde, **metin** özelliğini seçin ve sonra değerini temizlemek için **geri al** tuşunu seçin.

7. **+** **Yazı tipi** özelliğinin yanındaki artı işaretini () seçin ve ardından **size** özelliğinin değerini **15,75** olarak değiştirin.

     Aşağıdaki ekran görüntüsünde gösterildiği gibi çeşitli yazı tipi özelliklerini değiştirebilirsiniz.

     ![Yazı tipi boyutunu gösteren Özellikler penceresi](../ide/media/express_setfontsize.png)

8. **Araç kutusundan** başka bir etiket denetimi ekleyin ve ardından yazı tipi boyutunu **15,75** olarak ayarlayın.

9. **Text** özelliğini **Left zaman** olarak ayarlayın.

10. Etiketi **timeLabel** etiketinin hemen soluna doğru olacak şekilde taşıyın.

### <a name="to-add-controls-for-the-addition-problems"></a>Ek sorunlara yönelik denetimler eklemek için

1. **Araç kutusundan** bir etiket denetimi ekleyin ve **Text** **özelliğini olarak ayarlayın** . (soru işareti).

2. **AutoSize** özelliğini **false** olarak ayarlayın.

3. **Boyut** özelliğini **60, 50** olarak ayarlayın.

4. Yazı tipi boyutunu **18** olarak ayarlayın.

5. **TextAlign** özelliğini **MiddleCenter** olarak ayarlayın.

6. Denetimi form üzerinde konumlandırmak için **Location** özelliğini **50, 75** olarak ayarlayın.

7. **(Ad)** özelliğini **plusLeftLabel** olarak ayarlayın.

8. **PlusLeftLabel** etiketini seçin ve ardından **CTRL** + **C** tuşlarını veya **Düzen** menüsünden **Kopyala** ' yı seçin.

9. **CTRL** + **V** tuşlarını seçerek veya **Düzen** menüsüne **yapıştırarak** etiketi üç kez yapıştırın.

10. Üç yeni etiketi, **plusLeftLabel** etiketinin sağındaki bir satırda olacak şekilde düzenleyin.

     Yer çizgilerini, aralarında boşluk bırakmak ve bunları hizalamak için kullanabilirsiniz.

11. İkinci etiketin **metin** özelliğinin değerini **+** (artı işareti) olarak ayarlayın.

12. Üçüncü etiketin **(Name)** özelliğinin değerini **plusRightLabel** olarak ayarlayın.

13. Dördüncü etiketin **Text** özelliğinin değerini **=** (eşittir işareti) olarak ayarlayın.

14. <xref:System.Windows.Forms.NumericUpDown> **Araç kutusundan** bir denetim ekleyin, yazı tipi boyutunu **18** olarak ayarlayın ve genişliğini **100** olarak ayarlayın.

     Daha sonra bu tür bir denetim hakkında daha fazla bilgi edineceksiniz.

15. Ek sorun için etiket denetimleriyle NumericUpDown denetimini hizalamak.

16. NumericUpDown denetimi için **(Name)** özelliğinin değerini **Sum** olarak değiştirin.

     İlk satırı aşağıdaki çizimde gösterildiği gibi oluşturdunuz.

     ![Matematik sınavından ilk satır](../ide/media/express_firstrow.png)

## <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Çıkarma, çarpma ve bölme sorunlarına yönelik denetimler eklemek için

1. Ek sorun için beş denetimi (dört etiket denetimi ve NumericUpDown denetimi) kopyalayın ve ardından yapıştırın.

     Form, hala seçili olan beş yeni denetim içerir.

2. Tüm denetimleri, toplama denetimlerinin altına gelecek şekilde yerleştirmek üzere taşıyın.

     Boşluk çizgilerini, iki satır arasında yeterli mesafe sağlamak için kullanabilirsiniz.

3. İkinci etiket için **metin** özelliğinin değerini **-** (eksi işareti) olarak değiştirin.

4. İlk soru-işaret etiketini **minusLeftLabel** olarak adlandırın.

5. İkinci soru-işaret etiketini **minusRightLabel** olarak adlandırın.

6. NumericUpDown denetim **farkını** adlandırın.

7. Beş denetimi iki kez yapıştırın.

8. Üçüncü satır için, ilk etiketi **timesLeftLabel** olarak adlandırın, Ikinci etiketin **Text** özelliğini **×** (çarpma işareti) olarak değiştirin, üçüncü etiketi **timesRightLabel** olarak adlandırın ve NumericUpDown denetim **ürününe** adlandırın.

9. Dördüncü satır için, ilk etiketi **Dividedleftlabel** olarak adlandırın, Ikinci etiketin **Text** özelliğini **÷** (bölme işareti) olarak değiştirin, üçüncü Label **Dividedrigulabel**' ı adlandırın ve NumericUpDown denetim **bölümünü** adlandırın.

    > [!NOTE]
    > Bu öğreticiden çarpma işareti × ve bölüm işareti ÷ kopyalayabilir ve bunları forma yapıştırabilirsiniz.

## <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Bir başlangıç düğmesi eklemek ve sekme-dizin sırasını ayarlamak için

1. <xref:System.Windows.Forms.Button> **Araç kutusundan** bir denetim ekleyin ve sonra **(Name)** özelliğini **startButton** olarak ayarlayın.

2. **Testi başlatmak** için **metin** özelliğini ayarlayın.

3. Yazı tipi boyutunu **14** olarak ayarlayın.

4. **AutoSize** özelliğini **true** olarak ayarlayın. Bu, düğmenin metne sığacak şekilde otomatik olarak yeniden boyutlandırmasına neden olur.

5. Formun alt kısmındaki düğmeyi ortalayın.

6. **StartButton** denetimi için **TabIndex** özelliğinin değerini **1** olarak ayarlayın.

    > [!NOTE]
    > **TabIndex** özelliği, test Taklayıcı **sekme** tuşunu seçtiğinde denetimlerin sırasını ayarlar. Nasıl çalıştığını görmek için herhangi bir iletişim kutusunu açın (örneğin, menü çubuğunda **Dosya**  >  **Aç**' ı seçin) ve ardından **sekme** tuşuna birkaç kez tıklayın. Sekme tuşuna her seçimde imlecinizin denetimden nasıl hareket **ettiğinden emin** olmak. Bu formu oluştururken sırayı programcı verdi.

7. NumericUpDown toplam denetimi **için TabIndex** özelliğinin değerini **2,** fark denetimi **için 3,** ürün denetimi için **4** ve bölüm denetimi için **5** olarak ayarlayın.

     Formun aşağıdaki ekran görüntüsüne benzer olması gerekir.

     ![İlk matematik testi formu](../ide/media/express_formlaidout.png)

8. **TabIndex özelliğinin** beklediğiniz gibi çalıştığını doğrulamak için **F5** anahtarını seçerek veya menü çubuğunda Hata AyıklamaYı Başlat'ı seçerek programınızı kaydedin ve çalıştırın ve ardından Sekme tuşuna birkaç  >   kez basın. 

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için **[bkz. 2. Adım: Rastgele toplama sorunu oluşturma.](../ide/step-2-create-a-random-addition-problem.md)**

- Genel bakış konu başlığına dönmek için [bkz. Öğretici 2: Zamanlı matematik testi oluşturma.](../ide/tutorial-2-create-a-timed-math-quiz.md)
