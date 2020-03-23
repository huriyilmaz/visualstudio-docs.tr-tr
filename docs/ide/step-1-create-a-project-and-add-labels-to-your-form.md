---
title: 'Adım 1: Proje oluşturma ve forma etiket ekleme'
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bf904fca84fba88e81306ff91add6c2156b4544
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579453"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>Adım 1: Proje oluşturma ve forma etiket ekleme

Bu testi geliştirmenin ilk adımları olarak, projeyi oluşturursunuz ve bir forma etiketler, bir düğme ve diğer denetimler eklersiniz. Ayrıca eklediğiniz her denetim için özellikler de ayarlarsınız. Proje, form, denetimler ve (daha sonra öğretici) kodunu içerir. Düğme testi başlatır, etiketler test sorunlarını gösterir ve diğer denetimler sınav yanıtlarını ve testi bitirmek için kalan süreyi gösterir.

> [!NOTE]
> Bu konu temel kodlama kavramları hakkında bir öğretici serisinin bir parçasıdır. [Öğreticiye](../ide/tutorial-2-create-a-timed-math-quiz.md)genel bir bakış için bkz.

## <a name="to-create-a-project-for-a-form"></a>Form için proje oluşturmak için

::: moniker range="vs-2017"

1. Menü çubuğunda **Yeni** > **Proje** **yi seçin.** >

1. **Yeni Proje** iletişim kutusunun sol tarafındaki **Visual C#** veya **Visual Basic'i** seçin ve ardından **Windows Desktop'ı**seçin.

1. Şablonlar **listesinde, Windows Forms App (.NET Framework)** şablonuna girin, *mathquiz*adını girin ve ardından **Tamam** düğmesini seçin.

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

1. Yeni **proje pencerenizi Yapılandır'da** **Proje adı** kutusuna *MathQuiz* yazın veya girin. Ardından **Oluştur'u**seçin.

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Form için özellikleri ayarlamak için

1. Visual Studio'da formu seçin *(programlama* diline bağlı olarak Form1.cs veya *Form1.vb)* ve **metin** özelliğini **Math Quiz**olarak değiştirin.

     **Özellikler** penceresi form için özellikler içerir.

1. Formun boyutunu 400 piksel genişliğinde 500 piksel olarak değiştirin.

     Tümleşik geliştirme ortamının (IDE) sol alt köşesinde doğru boyut görünene kadar kenarlarını sürükleyerek formu yeniden boyutlandırabilirsiniz. Alternatif olarak, **Boyut** özelliğinin değerlerini değiştirebilirsiniz.

1. **FormBorderStyle** özelliğinin değerini **Fixed3D**olarak değiştirin ve **MaximizeBox** özelliğini **False**olarak ayarlayın.

     Bu değerler, sınav girenlerin formu yeniden boyutlandırmasını engeller.

## <a name="to-create-the-time-remaining-box"></a>Kalan süre kutusunu oluşturmak için

1. Araç <xref:System.Windows.Forms.Label> **Kutusundan**bir denetim ekleyin ve sonra **(Ad)** özelliğinin değerini **timeLabel**olarak ayarlayın.

     Bu etiket, testte kalan saniye sayısını gösteren sağ üst köşede bir kutu haline gelecektir.

2. Kutuyu yeniden boyutlandırabilmeniz için **Otomatik Boyutlandırma** özelliğini **False** olarak değiştirin.

3. Kutunun etrafına bir çizgi çizmek için **BorderStyle** özelliğini **FixedSingle** olarak değiştirin.

4. **Boyut** özelliğini **200, 30**olarak ayarlayın.

5. Etiketi, mavi boşluk çizgilerinin görüneceği formun sağ üst köşesine taşıyın.

     Bu satırlar, formdaki denetimleri hizalamanıza yardımcı olur.

6. **Özellikler** penceresinde Metin **özelliğini** seçin ve değerini temizlemek için **Arka Boşluk** anahtarını seçin.

7. Yazı**+** **Tipi** özelliğinin yanındaki artı işaretini ( ) seçin ve ardından **Boyut** özelliğinin değerini **15,75**olarak değiştirin.

     Aşağıdaki ekran görüntüsünün gösterdiği gibi, birkaç yazı tipi özelliğini değiştirebilirsiniz.

     ![Yazı tipi boyutunu gösteren özellikler penceresi](../ide/media/express_setfontsize.png)

8. **Araç Kutusundan**başka bir Etiket denetimi ekleyin ve yazı tipi boyutunu **15,75**olarak ayarlayın.

9. **Metin** özelliğini **Zaman Sol'a**ayarlayın.

10. Etiketi, **timeLabel** etiketinin hemen solunda olacak şekilde taşıyın.

### <a name="to-add-controls-for-the-addition-problems"></a>Ekleme sorunları için denetimeklemek için

1. **Araç Kutusundan**etiket denetimi ekleyin ve **metin** özelliğini şu **şekilde ayarlar?** (soru işareti).

2. Otomatik **Boyutlandırma** özelliğini **False**olarak ayarlayın.

3. **Boyut** özelliğini **60, 50**olarak ayarlayın.

4. Yazı tipi boyutunu **18**olarak ayarlayın.

5. **TextAlign** özelliğini **MiddleCenter**olarak ayarlayın.

6. Formu üzerinde kontrol konumlandırmak için **Konum** **özelliği50, 75** olarak ayarlayın.

7. **(Ad)** özelliğini **plusLeftLabel**olarak ayarlayın.

8. **plusLeftLabel** etiketini seçin ve ardından **Edit** menüsünde **Ctrl**+**C** tuşlarını veya **Kopyala'yı** seçin.

9. **Düzenleme** menüsünde **Ctrl**+**V** tuşlarını veya **Yapıştır'ı** seçerek etiketi üç kez yapıştırın.

10. Üç yeni **etiketi, plusLeftLabel** etiketinin sağında üst üste olacak şekilde düzenleyin.

     Boşluk satırlarını kullanarak onları uzaya çıkarıp hizalayabilirsiniz.

11. İkinci etiketin **Metin** özelliğinin değerini **+** (artı işareti) ayarlayın.

12. Üçüncü etiketin **(Ad)** özelliğinin değerini **plusRightLabel**olarak ayarlayın.

13. Dördüncü etiketin **Metin** özelliğinin değerini **=** (eşit işaret) olarak ayarlayın.

14. <xref:System.Windows.Forms.NumericUpDown> **Toolbox'tan**bir denetim ekleyin, yazı tipi boyutunu **18'e**ayarlayın ve genişliğini **100'e**ayarlayın.

     Bu tür bir kontrol hakkında daha sonra daha fazla bilgi edineceksiniz.

15. Ekleme sorunu için Etiket denetimleriyle SayısalUpDown denetimini hizala.

16. NumericUpDown denetiminin **(Ad)** özelliğinin değerini **toplamı**için değiştirin.

     Aşağıdaki resimde gösterildiği gibi ilk satırı oluşturdunuz.

     ![Matematik testinin ilk sırası](../ide/media/express_firstrow.png)

## <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Çıkarma, çarpma ve bölme sorunları için denetim eklemek için

1. Ekleme sorunu (dört Etiket denetimi ve Sayısal Hedef Denetim) için beş denetimi de kopyalayın ve yapıştırın.

     Form, hala seçili olan beş yeni denetim içerir.

2. Tüm denetimleri, ek denetimlerinin altında hizalayabilmeleri için yerine taşıyın.

     İki satır arasında yeterli mesafe vermek için boşluk satırlarını kullanabilirsiniz.

3. İkinci etiket için **Metin** özelliğinin değerini **-** (eksi işareti) olarak değiştirin.

4. İlk soru işareti **etiketini eksiLeftLabel**olarak adlandırın.

5. İkinci soru işareti **etiketini eksiRightLabel**olarak adlandırın.

6. SayısalUpDown denetim **farkını**adlandırın.

7. Beş denetimi iki kez daha yapıştırın.

8. Üçüncü satır için, ilk etiket **timesLeftLabel**adı, ikinci etiketin **Metin** **özelliğini ×** (çarpma işareti) olarak değiştirin, üçüncü etiket **timesRightLabel**adını ve NumericUpDown kontrol **ürünü**adını .

9. Dördüncü satır için, ilk etiket **bölünmüşLeftLabel**adı, **÷** (bölme işareti) için ikinci **etiketin Metin** özelliğini değiştirmek, üçüncü etiket **bölünmüşRightLabel**adı , ve NumericUpDown kontrol **quotient**adı .

    > [!NOTE]
    > Çarpma işareti × ve bölme işaretini bu öğreticiden kopyalayıp forma yapıştırabilirsiniz.

## <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Başlat düğmesi eklemek ve sekme dizini sırasını ayarlamak için

1. Araç <xref:System.Windows.Forms.Button> **Kutusundan**bir denetim ekleyin ve ardından **(Ad)** özelliğini **startButton'a**ayarlayın.

2. **Metni** **başlatacak metin özelliğini**ayarlayın.

3. Yazı tipi boyutunu **14**olarak ayarlayın.

4. Otomatik **Boyutlandırma** özelliğini **True**olarak ayarlayın , bu da düğmenin metne uyacak şekilde otomatik olarak yeniden boyutlandırılabına neden olur.

5. Düğmeyi formun altına yakın ortalayın.

6. **BaşlatDüğmesi** denetimi için **TabIndex** özelliğinin değerini **1**olarak ayarlayın.

    > [!NOTE]
    > **Sekme Özelliği,** sınav sahibi **Sekme** anahtarını seçtiğinde denetimlerin sırasını ayarlar. Nasıl çalıştığını görmek için, herhangi bir iletişim kutusunu açın (örneğin, menü çubuğunda **Dosya** > **Aç'ı**seçin) ve ardından **Sekme** anahtarını birkaç kez seçin. **Sekme** anahtarını her seçtiğinizde imlecin denetimden denetime nasıl hareket ettiğini izleyin. Bir programcı bu formu oluştururken sipariş karar verdi.

7. NumericUpDown toplamı denetimi için **TabIndex** özelliğinin değerini **2**olarak ayarlayın , fark denetimi için **3**, ürün kontrolü için **4**, ve bölüm kontrolü için **5**.

     Form aşağıdaki ekran görüntüsüne benzer olmalıdır.

     ![İlk matematik sınav formu](../ide/media/express_formlaidout.png)

8. **TabIndex** özelliğinin beklediğiniz gibi çalışıp çalışmadığını doğrulamak için, **F5** anahtarını seçerek veya menü çubuğunda **Hata Ayıklama** > **Hata Ayıklama'yı** seçerek programınızı kaydedin ve çalıştırın ve ardından **sekme** anahtarını birkaç kez seçin.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için **[bkz: Adım 2: Rastgele bir ekleme sorunu oluşturun.](../ide/step-2-create-a-random-addition-problem.md)**

- Genel bakış konusuna dönmek için [bkz.](../ide/tutorial-2-create-a-timed-math-quiz.md)
