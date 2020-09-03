---
title: '1. Adım: proje oluşturma ve formunuza etiketler ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f44e50be-a5f5-4d77-9cff-dd52374c3f74
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2a13d96d8932a3a9e4628f2d0e67a28869252c95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667357"
---
# <a name="step-1-create-a-project-and-add-labels-to-your-form"></a>1. Adım: Proje Oluşturma ve Formunuza Etiketler Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu testi geliştirmenin ilk adımı olarak, projeyi oluşturur ve bir forma Etiketler, bir düğme ve diğer denetimler eklersiniz. Eklediğiniz her denetim için de Özellikler ayarlarsınız. Proje formu, denetimleri ve (öğreticide daha sonra) kodu içerecektir. Düğme, testi başlatır, Etiketler test sorunlarını gösterir ve diğer denetimler, test yanıtlarını ve testi tamamlaması için kalan süreyi gösterir.

> [!NOTE]
> Bu konu, temel kodlama kavramlarıyla ilgili bir öğretici serisinin bir parçasıdır. Öğreticiye genel bakış için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-create-a-project-and-set-properties-for-a-form"></a>Bir proje oluşturmak ve bir formun özelliklerini ayarlamak için

1. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

2. **Yüklü şablonlar** listesinde, **C#** veya **Visual Basic**seçin.

3. Şablon listesinde **Windows Forms uygulama** şablonunu seçin, **Math test**olarak adlandırın ve ardından **Tamam** düğmesini seçin.

     Seçtiğiniz programlama diline bağlı olarak, **Form1.cs** veya **Form1. vb** adlı bir form görüntülenir.

4. Formu seçin ve sonra **metin** özelliğini **matematik sınavından**değiştirin.

     **Özellikler** penceresi form özelliklerini içerir.

5. Formun boyutunu, 400 piksel yüksekliğinde 500 piksel genişliğinde olarak değiştirin.

     Tümleşik geliştirme ortamının (IDE) sol alt köşesinde doğru boyut görünene kadar, kenarlarını sürükleyerek formu yeniden boyutlandırabilirsiniz. Alternatif olarak, **size** özelliğinin değerlerini değiştirebilirsiniz.

6. **FormBorderStyle** özelliğinin değerini **Fixed3D**olarak değiştirin ve **MaximizeBox** özelliğini **false**olarak ayarlayın.

     Bu değerler, test takipçilerin formu yeniden boyutlandırmasını engeller.

### <a name="to-create-the-time-remaining-box"></a>Kalan süre kutusunu oluşturmak için

1. Araç kutusundan bir **etiket** denetimi ekleyin ve sonra **(Name)** özelliğinin değerini olarak ayarlayın `timeLabel` .

     Bu etiket, sağ üst köşede, test içinde kalan saniye sayısını gösteren bir kutu olur.

2. Kutuyu yeniden boyutlandırabilmeniz için **AutoSize** özelliğini **false** olarak değiştirin.

3. Kutunun çevresinde bir çizgi çizmek için **BorderStyle** özelliğini **FixedSingle** olarak değiştirin.

4. **Boyut** özelliğini **200, 30**olarak ayarlayın.

5. Etiketi formun sağ üst köşesine taşıyın, burada mavi yer çizgisi çizgileri görünür.

     Bu satırlar formdaki denetimleri hizalamaya yardımcı olur.

6. **Özellikler** penceresinde, **metin** özelliğini seçin ve sonra değerini temizlemek için geri al tuşunu seçin.

7. **Yazı tipi** özelliğinin yanındaki artı işaretini (+) seçin ve ardından **Size** özelliğinin değerini **15,75**olarak değiştirin.

     Aşağıdaki resimde gösterildiği gibi çeşitli yazı tipi özelliklerini değiştirebilirsiniz.

     ![Yazı tipi boyutunu gösteren Özellikler penceresi](../ide/media/express-setfontsize.png "Express_setFontSize") Yazı tipi boyutunu gösteren Özellikler penceresi

8. Araç kutusundan başka bir **etiket** denetimi ekleyin ve ardından yazı tipi boyutunu **15,75**olarak ayarlayın.

9. **Text** özelliğini **Left zaman**olarak ayarlayın.

10. Etiketi **timeLabel** etiketinin hemen soluna doğru olacak şekilde taşıyın.

### <a name="to-add-controls-for-the-addition-problems"></a>Ek sorunlara yönelik denetimler eklemek için

1. Araç kutusundan bir **etiket** denetimi ekleyin ve **Text** **özelliğini olarak ayarlayın** . (soru işareti).

2. **AutoSize** özelliğini **false**olarak ayarlayın.

3. **Boyut** özelliğini **60, 50**olarak ayarlayın.

4. Yazı tipi boyutunu **18**olarak ayarlayın.

5. **TextAlign** özelliğini **MiddleCenter**olarak ayarlayın.

6. Denetimi form üzerinde konumlandırmak için **Location** özelliğini **50, 75** olarak ayarlayın.

7. **(Ad)** özelliğini **plusLeftLabel**olarak ayarlayın.

8. **PlusLeftLabel** etiketini seçin ve ardından CTRL + C tuşlarını veya **Düzen** menüsünden **Kopyala** ' yı seçin.

9. CTRL + V tuşlarını seçerek veya **Düzen** menüsüne **yapıştırarak** etiketi üç kez yapıştırın.

10. Üç yeni etiketi, **plusLeftLabel** etiketinin sağındaki bir satırda olacak şekilde düzenleyin.

     Yer çizgilerini, aralarında boşluk bırakmak ve bunları hizalamak için kullanabilirsiniz.

11. İkinci etiketin **metin** özelliğinin değerini **+** (artı işareti) olarak ayarlayın.

12. Üçüncü etiketin **(Name)** özelliğinin değerini **plusRightLabel**olarak ayarlayın.

13. Dördüncü etiketin **Text** özelliğinin değerini **=** (eşittir işareti) olarak ayarlayın.

14. Araç kutusundan bir **NumericUpDown** denetimi ekleyin, yazı tipi boyutunu **18**olarak ayarlayın ve genişliğini **100**olarak ayarlayın.

     Daha sonra bu tür bir denetim hakkında daha fazla bilgi edineceksiniz.

15. Ek sorun için etiket denetimleriyle **NumericUpDown** denetimini hizalamak.

16. **NumericUpDown** denetimi Için **(Name)** özelliğinin değerini **Sum**olarak değiştirin.

     Aşağıdaki resimde gösterildiği gibi ilk satırı oluşturdunuz.

     ![Matematik sınavından ilk satır](../ide/media/express-firstrow.png "Express_firstRow") Matematik sınavından ilk satır

### <a name="to-add-controls-for-the-subtraction-multiplication-and-division-problems"></a>Çıkarma, çarpma ve bölme sorunlarına yönelik denetimler eklemek için

1. Ek sorun için beş denetimi (dört etiket denetimi ve NumericUpDown denetimi) kopyalayın ve ardından yapıştırın.

     Form, hala seçili olan beş yeni denetim içerir.

2. Tüm denetimleri, toplama denetimlerinin altına gelecek şekilde yerleştirmek üzere taşıyın.

     Boşluk çizgilerini, iki satır arasında yeterli mesafe sağlamak için kullanabilirsiniz.

3. İkinci etiket için **metin** özelliğinin değerini **–** (eksi işareti) olarak değiştirin.

4. İlk soru-işaret etiketini **minusLeftLabel**olarak adlandırın.

5. İkinci soru-işaret etiketini **minusRightLabel**olarak adlandırın.

6. **NumericUpDown** denetim **farkını**adlandırın.

7. Beş denetimi iki kez yapıştırın.

8. Üçüncü satır için, ilk etiketi **timesLeftLabel**olarak adlandırın, Ikinci etiketin **Text** özelliğini **×** (çarpma işareti) olarak değiştirin, üçüncü etiketi **timesRightLabel**olarak adlandırın ve NumericUpDown denetim **ürününe**adlandırın.

9. Dördüncü satır için, ilk etiketi **Dividedleftlabel**olarak adlandırın, Ikinci etiketin **Text** özelliğini **÷** (bölme işareti) olarak değiştirin, üçüncü Label **Dividedrigulabel**' ı adlandırın ve NumericUpDown denetim **bölümünü**adlandırın.

    > [!NOTE]
    > Bu öğreticiden çarpma işareti × ve bölüm işareti ÷ kopyalayabilir ve bunları forma yapıştırabilirsiniz.

### <a name="to-add-a-start-button-and-set-the-tab-index-order"></a>Bir başlangıç düğmesi eklemek ve sekme-dizin sırasını ayarlamak için

1. Araç kutusundan bir **düğme** denetimi ekleyin ve sonra **(Name)** özelliğini **startButton**olarak ayarlayın.

2. **Testi başlatmak**için **metin** özelliğini ayarlayın.

3. Yazı tipi boyutunu **14**olarak ayarlayın.

4. **AutoSize** özelliğini **true**olarak ayarlayın. Bu, düğmenin metne sığacak şekilde otomatik olarak yeniden boyutlandırmasına neden olur.

5. Formun alt kısmındaki düğmeyi ortalayın.

6. **StartButton** denetimi için **TabIndex** özelliğinin değerini **1**olarak ayarlayın.

    > [!NOTE]
    > **TabIndex** özelliği, test Taklayıcı sekme tuşunu seçtiğinde denetimlerin sırasını ayarlar. Nasıl çalıştığını görmek için herhangi bir iletişim kutusunu açın (örneğin, menü çubuğunda **Dosya**, **Aç**' ı seçin) ve ardından SEKME tuşuna birkaç kez tıklayın. Her sekme tuşunu seçtiğiniz her seferinde imlecinizin denetim ' e nasıl taşındığını izleyin. Bir programcı bu formu oluştururken bir sıraya karar verdi.

7. Değer denetimi için **TabIndex** özelliğinin değerini **2**, fark denetimi için **3**, ürün denetimi için **4**ve bölüm denetimi için **5**olarak ayarlayın.

     Form aşağıdaki çizimde gösterildiği gibi görünmelidir.

     ![İlk matematik testi formu](../ide/media/express-formlaidout.png "Express_FormLaidOut") İlk matematik testi formu

8. **TabIndex** özelliğinin beklendiği gibi çalışıp çalışmadığını doğrulamak için F5 tuşunu seçerek veya **Hata Ayıkla**, menü çubuğunda **hata ayıklamayı Başlat** ' ı seçerek ve ardından SEKME tuşuna birkaç kez tıklayarak programınızı kaydedin ve çalıştırın.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 2. [Adım: rastgele bir ek sorun oluşturma](../ide/step-2-create-a-random-addition-problem.md).

- Genel bakış konusuna dönmek için bkz. [öğretici 2: zamanlı matematik testi oluşturma](../ide/tutorial-2-create-a-timed-math-quiz.md).
