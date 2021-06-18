---
title: '1. Adım: Proje oluşturma ve formunuza etiketler ekleme'
description: Projeyi oluşturma, bir forma etiketler, bir düğme ve diğer denetimler ekleme ve eklerken her denetim için özellikleri ayarlama hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 10/15/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0400c29e53c45ad9a98e7edca78fd2cf9741fcf0
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307758"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>1. Adım: Proje oluşturma ve formunuza etiketler ekleme

Bu testi geliştirmenin ilk adımları olarak projeyi oluşturabilir ve forma etiketler, düğme ve diğer denetimler eklersiniz. Ayrıca, ekley istediğiniz her denetimin özelliklerini de ayarlayabilirsiniz. Proje form, denetimler ve (öğreticinin sonraki adımlarında) kodunu içerir. Düğme testi başlatır, etiketler test sorunlarını gösterirken diğer denetimler testin yanıtlarını ve testi tamamlamak için kalan zamanı gösterir.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçası. Öğreticiye genel bakış için [bkz. Öğretici 2: Zamanlı matematik testi oluşturma.](../ide/tutorial-2-create-a-timed-math-quiz.md)

## <a name="to-create-a-project-for-a-form"></a>Form için proje oluşturmak için

::: moniker range="vs-2017"

1. Menü çubuğunda Dosya Yeni **Proje'yi** >  > **seçin.**

1. Yeni Proje iletişim kutusunun **sol tarafındaki Visual C#** veya Visual Basic'yi ve ardından Windows Masaüstü'nü **seçin.**  

1. Şablon listesinde Windows Forms **App (.NET Framework)** şablonunu seçin, *MathQuiz* olarak ve ardından Tamam **düğmesini** seçin.

    Seçtiğiniz programlama diline bağlı *olarak Form1.cs* veya *Form1.vb* adlı bir form görüntülenir.

   > [!NOTE]
   > **Windows Forms App (.NET Framework)** şablonunu görmüyorsanız. **.NET** masaüstü Visual Studio Yükleyicisi iş yükünü yüklemek için Visual Studio Yükleyicisi kullanın.<br/><br/>![.NET masaüstü geliştirme iş yükü Visual Studio Yükleyicisi](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Daha fazla bilgi için Yükleme [Visual Studio](../install/install-visual-studio.md) bakın.

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresini görüntüleme](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Yeni **proje oluştur penceresinde,** arama kutusuna *Windows Forms* yazın veya yazın. Ardından Proje türü **listesinden** **Masaüstü'leri** seçin.

   Proje türü **filtresini uyguladikten** sonra, C# veya Windows Forms için .NET Framework Uygulaması **(.NET Framework)** şablonunu seçin ve Visual Basic'yi **seçin.**

   ![Windows Forms Uygulaması (.NET Framework) için C# veya Visual Basic şablonunu seçin](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > **Windows Forms App (.NET Framework) şablonunu** görmüyorsanız Yeni proje oluştur **penceresinden yükleyebilirsiniz.** Neyi **bulasınız? iletisinde** Daha fazla araç ve **özellik yükle bağlantısını** seçin.
   >
   > !['Yeni proje oluştur' penceresindeki 'Ne arıyorsanız bu değil' iletisinden 'Daha fazla araç ve özellik yükle' bağlantısı](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ardından, Visual Studio Yükleyicisi .NET masaüstü geliştirme **iş yükünü** seçin.
   >
   > ![.NET Core iş yükü Visual Studio Yükleyicisi](../ide/media/install-dot-net-desktop-env.png)
   >
   > Bundan sonra, **dosyanın** üst Visual Studio Yükleyicisi. Çalışmanızı kaydetmeniz isteniyor olabilir; öyleyse, bunu yap. Ardından, iş yükünü **yüklemek için** Devam'ı seçin.

1. Yeni **projenizi yapılandır penceresinde** Proje adı kutusuna *MathQuiz* **yazın veya** girin. Ardından **Oluştur'a seçin.**

::: moniker-end

## <a name="to-set-properties-for-a-form"></a>Formun özelliklerini ayarlamak için

1. Bu Visual Studio, formu (programlama diline bağlı olarak *Form1.cs* veya *Form1.vb)* seçin ve **ardından Text** özelliğini Matematik Testi **olarak değiştirebilirsiniz.**

     Özellikler **penceresi** formun özelliklerini içerir.

1. Formun boyutunu 500 piksel genişliğinde ve 400 piksel uzunluğunda olacak şekilde değiştirebilirsiniz.

     Tümleşik geliştirme ortamının (IDE) sol alt köşesinde doğru boyut görünene kadar kenarlarını sürükleyerek formu yeniden boyutlandırabilirsiniz. Alternatif olarak Size özelliğinin değerlerini **değiştirebilirsiniz.**

1. **FormBorderStyle özelliğinin** değerini **Fixed3D** olarak ve **MaximizeBox özelliğini False** olarak **ayarlayın.**

     Bu değerler, test alan kullanıcıların formu yeniden boyutlandırmasını önler.

## <a name="to-create-the-time-remaining-box"></a>Kalan zamanı oluşturmak için kutusu

1. Araç <xref:System.Windows.Forms.Label> Kutusundan bir **denetim ekleyin** ve ardından **(Name)** özelliğinin değerini **timeLabel olarak ayarlayın.**

     Bu etiket, sağ üst köşede testte kalan saniye sayısını gösteren bir kutu haline gelecektir.

2. Kutuyu **yeniden boyutlandırmak için AutoSize** **özelliğini False** olarak değiştirebilirsiniz.

3. Kutunun etrafında bir çizgi çizmek için **BorderStyle** özelliğini **FixedSingle** olarak değiştirebilirsiniz.

4. Size özelliğini **200, 30 olarak ayarlayın.** 

5. Etiketi formun sağ üst köşesine, burada mavi boşluk çizgileri görünecek şekilde hareket ettirin.

     Bu satırlar, form üzerinde denetimleri hizalamanıza yardımcı olur.

6. Özellikler **penceresinde Text** özelliğini **seçin ve** ardından Geri Al **tuşuna basın.**

7. Font özelliğinin yanındaki artı işaretine ( ) ve ardından Size özelliğinin değerini **+** **15,75 olarak değiştirerek.**  

     Aşağıdaki ekran görüntüsünde olduğu gibi birkaç yazı tipi özelliği değiştirebilirsiniz.

     ![Özellikler penceresi boyutunu gösteren ekran tipi](../ide/media/express_setfontsize.png)

8. Araç Kutusundan başka bir Etiket **denetimi ekleyin** ve ardından yazı tipi boyutunu **15,75 olarak ayarlayın.**

9. Text özelliğini **Time** **Left olarak ayarlayın.**

10. Etiketi **timeLabel** etiketinin hemen sol tarafından yukarı doğru sıra olacak şekilde hareket ettirin.

### <a name="to-add-controls-for-the-addition-problems"></a>Ekleme sorunlarına denetimler eklemek için

1. Araç Kutusundan bir Etiket **denetimi ekleyin ve** text özelliğini **?** olarak **ayarlayın** (soru işareti).

2. **AutoSize özelliğini** False olarak **ayarlayın.**

3. Size özelliğini **60, 50 olarak ayarlayın.** 

4. Yazı tipi boyutunu **18 olarak ayarlayın.**

5. **TextAlign özelliğini** **MiddleCenter olarak ayarlayın.**

6. Formda **denetimi** konumlandırmak için Location özelliğini **50, 75** olarak ayarlayın.

7. **(Name) özelliğini** **plusLeftLabel olarak ayarlayın.**

8. **plusLeftLabel etiketini** seçin ve ardından Düzenle menüsünde **Ctrl** + **C** tuşlarını veya **Kopyala'yı** seçin. 

9. Ctrl V tuşlarını veya Düzenle menüsünde **Yapıştır'ı** +  **seçerek etiketi** üç **kez** yapıştırın.

10. Üç yeni **etiketi, plusLeftLabel** etiketinin sağ tarafından bir satırda olacak şekilde düzenleme.

     Ara çizgilerini kullanarak bunları aralara yer ve sıralaabilirsiniz.

11. İkinci etiketin Text özelliğinin değerini **(artı** **+** işareti) olarak ayarlayın.

12. Üçüncü etiketin **(Name) özelliğinin değerini** **plusRightLabel olarak ayarlayın.**

13. Dördüncü etiketin **Text** özelliğinin değerini (eşittir **=** işareti) olarak ayarlayın.

14. Araç <xref:System.Windows.Forms.NumericUpDown> Kutusundan bir **denetim ekleyin,** yazı tipi boyutunu **18** olarak ayarlayın ve genişliğini **100 olarak ayarlayın.**

     Bu tür denetimler hakkında daha fazla bilgi edinmek için daha sonra bilgi alasiniz.

15. NumericUpDown denetimlerini toplama sorunu için Etiket denetimleriyle sırala.

16. NumericUpDown denetimi **için (Name)** özelliğinin değerini toplam olarak **değiştirir.**

     Aşağıdaki çizimde gösterildiği gibi ilk satırı oluşturduk.

     ![Matematik testinin ilk satırı](../ide/media/express_firstrow.png)

## <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Çıkarma, çarpma ve bölme sorunlarına denetimler eklemek için

1. Toplama sorununa (dört Etiket denetimi ve NumericUpDown denetimi) beş denetimi de kopyalayıp yapıştırın.

     Formda hala seçili olan beş yeni denetim vardır.

2. Tüm denetimleri, toplama denetimlerinin altına doğru sıralayacak şekilde yerinde hareket ettirin.

     İki satır arasında yeterli mesafeyi vermek için boşluk çizgilerini kullanabilirsiniz.

3. İkinci etiketin **Text özelliğinin** değerini (eksi **-** işareti) olarak değiştirebilirsiniz.

4. İlk soru işareti etiketini **minusLeftLabel olarak girin.**

5. İkinci soru işareti etiketini **minusRightLabel olarak anın.**

6. NumericUpDown denetim farkını olarak **ifade eder.**

7. Beş denetimi iki kez daha yapıştırın.

8. Üçüncü satır için ilk **etiketi timesLeftLabel** olarak, ikinci etiketin **Text** özelliğini **×** (çarpma işareti) olarak, üçüncü etiketi **timesRightLabel** olarak ve NumericUpDown denetim ürününü olarak **yazın.**

9. Dördüncü satır için ilk etiketi **dividedLeftLabel** olarak, ikinci etiketin **Text** özelliğini **÷** (bölme işareti) olarak, üçüncü **etiketi dividedRightLabel** olarak ve NumericUpDown denetim bölüme **adını girin.**

    > [!NOTE]
    > Bu öğreticiden çarpma × ve bölme ÷ kopyalayıp forma yapıştırabilirsiniz.

## <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Başlat düğmesi eklemek ve sekme dizini sıralamayı ayarlamak için

1. Araç <xref:System.Windows.Forms.Button> Kutusundan bir **denetim ekleyin ve** ardından **(Name)** özelliğini **startButton olarak ayarlayın.**

2. Text özelliğini **Testi** başlat **olarak ayarlayın.**

3. Yazı tipi boyutunu **14 olarak ayarlayın.**

4. **AutoSize özelliğini** **True** olarak ayarlayın. Bu, düğmenin metne sığacak şekilde otomatik olarak yeniden boyutlandırılmanıza neden olur.

5. Düğmeyi formun alt kısmında ortalar.

6. **startButton** denetimi **için TabIndex** özelliğinin değerini **1 olarak ayarlayın.**

    > [!NOTE]
    > **TabIndex** özelliği, sınava alan kullanıcı Sekme tuşuna basınca denetimlerin **sıralamalarını** ayarlar. Nasıl çalıştığını görmek için herhangi bir iletişim kutusunu açın (örneğin, menü çubuğunda Dosya Aç'ı seçin) ve ardından   >   **Sekme** tuşuna birkaç kez tıklayın. Her **sekme** tuşunu seçtiğiniz her seferinde imlecinizin denetim ' e nasıl taşındığını izleyin. Bir programcı bu formu oluştururken bir sıraya karar verdi.

7. Değer denetimi için **TabIndex** özelliğinin değerini **2**, fark denetimi için **3**, ürün denetimi için **4** ve bölüm denetimi için **5** olarak ayarlayın.

     Form aşağıdaki ekran görüntüsüne benzer şekilde görünmelidir.

     ![İlk matematik testi formu](../ide/media/express_formlaidout.png)

8. **TabIndex** özelliğinin beklendiği gibi çalışıp çalışmadığını doğrulamak için **F5** tuşunu seçerek veya menü çubuğunda Hata **Ayıkla** Başlat ' ı seçerek programınızı kaydedip çalıştırın  >   ve ardından **sekme** tuşuna birkaç kez tıklayın.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 2. **[Adım: rastgele bir ek sorun oluşturma](../ide/step-2-create-a-random-addition-problem.md)**.

- Genel bakış konusuna dönmek için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).
