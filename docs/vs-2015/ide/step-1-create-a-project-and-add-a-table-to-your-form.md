---
title: '1\. Adım: proje oluşturma ve formunuza tablo ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1cac4ba4-f3cd-43bd-ad5d-50fc599234e8
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 05a7f9930dc1619d6f35a6024bd0f754f7caeeb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643510"
---
# <a name="step-1-create-a-project-and-add-a-table-to-your-form"></a>1\. Adım: Proje Oluşturma ve Formunuza Tablo Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eşleştirme oyunu hazırlarken ilk adım projeyi oluşturmak ve formunuza bir tablo eklemektir. Tablo, simgeleri 4x4'lük muntazam bir kılavuza hizalamaya yardımcı olur. Ayrıca, oyun tahtasının görünüşünü iyileştirmek için çeşitli özellikleri ayarlarsınız.

### <a name="to-create-a-project-and-add-a-table-to-your-form"></a>Bir proje oluşturmak ve formunuza bir tablo eklemek için

1. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin.

2. Visual Studio Express kullanmıyorsanız, önce bir programlama dili seçmeniz gerekir. **Yüklü şablonlar** listesinden, **görsel C#**  veya **Visual Basic**seçin.

3. Proje şablonları listesinde **Windows Forms uygulama**' yı seçin, proje **MatchingGame**olarak adlandırın ve **Tamam** düğmesini seçin.

4. **Özellikler** penceresinde, aşağıdaki form özelliklerini ayarlayın.

   1. Formun **Text** özelliğini **Form1** iken **eşleşen oyunla**değiştirin. Bu metin oyun penceresinin en üstünde görünür.

   2. Formun boyutunu 550 piksel genişliğe ve 550 piksel uzunluğa ayarlayın. Bunu, **Boyut** özelliğini **550, 550**olarak ayarlayarak veya tümleşik geliştirme ortamının sağ alt köşesinde (IDE) doğru boyutu görene kadar formun köşesini sürükleyerek yapabilirsiniz.

5. IDE 'nin sol tarafındaki **araç kutusu** sekmesini seçerek araç kutusunu görüntüleyin.

6. Araç kutusundaki **kapsayıcılar** kategorisinden bir `TableLayoutPanel` denetimini sürükleyin ve sonra bunun için aşağıdaki özellikleri ayarlayın.

   1. **BackColor** özelliğini **CornflowerBlue**olarak ayarlayın. Bunu yapmak için, **Özellikler** penceresinde **BackColor** özelliğinin yanındaki açılan oku seçerek **BackColor** iletişim kutusunu açın.  Ardından, kullanılabilir renk adlarının listesini görüntülemek için **BackColor** Iletişim kutusundaki **Web** sekmesini seçin.

      > [!NOTE]
      > Renkler alfabetik sırada değildir ve CornflowerBlue listenin sonuna yakın bir yerdedir.

   2. Özelliğin yanındaki açılan düğmeyi seçerek ve büyük orta düğmesini seçerek, **Dock** özelliğini **Fill** olarak ayarlayın. Böylece tablo formun tamamını kaplayacak şekilde yayılır.

   3. **CellBorderStyle** özelliğini **ınmetinolarak**ayarlayın. Böylece, tahta üzerindeki her bir hücre arasında görsel kenarlıklar olur.

   4. TableLayoutPanel denetiminin sağ üst köşesindeki üçgen düğmesini seçerek ilgili görev menüsünü görüntüleyin.

   5. Görev menüsünde, iki satır daha eklemek için **satır ekle** ' yi seçin ve daha sonra iki sütun eklemek için sütun Iki kez **Ekle** ' yi seçin.

   6. Görev menüsünde **satırları ve sütunları Düzenle** ' yi seçerek **sütun ve satır stilleri** penceresini açın. Sütunların her birini seçin, **yüzde** seçenek düğmesini seçin ve sonra her bir sütunun genişliğini toplam genişliğinin yüzde 25 ' i olarak ayarlayın. Ardından pencerenin üst kısmındaki açılan kutudan **Satırlar** ' ı seçin ve her satırın yüksekliğini yüzde 25 olarak ayarlayın. İşiniz bittiğinde **Tamam** düğmesini seçin.

      TableLayoutPanel denetiminiz şu anda, eşit boyutlu on altı kare hücre içeren 4x4'lük bir kılavuz halinde olmalıdır. Bu satırlar ve sütunlar, sonradan simge resimlerinin görüneceği yerlerdir.

7. Form düzenleyicisinde TableLayoutPanel seçildiğinden emin olun. Bunu doğrulamak için, **Özellikler** penceresinin en üstünde **tableLayoutPanel1** görmeniz gerekir. Seçili değilse, formda TableLayoutPanel öğesini seçin veya **Özellikler** penceresinin en üstündeki açılan denetimde seçin.

    TableLayoutPanel seçiliyken, araç kutusunu açın ve TableLayoutPanel 'in sol üst hücresine bir **etiket** denetimi ( **ortak denetimler** kategorisinde bulunur) ekleyin. @No__t_0 denetimi artık IDE 'de seçilmelidir. Bu öğe için aşağıdaki özellikleri ayarlayın.

   1. Etiketin **BackColor** özelliğinin **CornflowerBlue**olarak ayarlandığından emin olun.

   2. **AutoSize** özelliğini **false**olarak ayarlayın.

   3. **Dock** özelliğini **Fill**olarak ayarlayın.

   4. Özelliğin yanındaki açılan düğmeyi seçerek ve ardından ortadaki düğmeyi seçerek **TextAlign** özelliğini **MiddleCenter** olarak ayarlayın. Böylece, simgenin hücrenin ortasında görünmesi sağlanır.

   5. **Yazı tipi** özelliğini seçin. Üç nokta (…) düğmesi görünmelidir.

   6. Üç nokta düğmesini seçin ve **yazı tipi** değerini **Web**'e, **yazı tipi stilini** **kalın**olarak ve **Boyut** olarak **72**olarak ayarlayın.

   7. Etiketin **Text** özelliğini **c**harfine ayarlayın.

        TableLayoutPanel öğesinin sol üst hücresinde şimdi, mavi arka plan üzerinde ortalanmış bir siyah kutu yer alıyor olmalıdır.

       > [!NOTE]
       > Webdings yazı tipi, simgelerden oluşan bir yazı tipi olup Windows işletim sistemiyle birlikte gelir. Eşleştirme oyununuzda oyuncunun simge çiftlerini eşleştirmesi gerektiğinden, eşleştirilecek simgeleri göstermek için bu yazı tipini kullanıyorsunuz. **Metin** özelliğine **c** koymak yerine, hangi simgelerin görüntülendiğini görmek için farklı harfler girmeyi deneyin. Ünlem işareti bir örümcek, büyük N harfi bir göz ve virgül ise kırmızı biberdir.

8. Etiket denetiminizi seçin ve TableLayoutPanel içinde sonraki hücreye kopyalayın. (CTRL + C tuşlarını seçin veya menü çubuğunda **Düzenle**, **Kopyala**' yı seçin.) Ardından yapıştırın. (Ctrl + V tuşlarını seçin veya menü çubuğunda **Düzenle**, **Yapıştır**' ı seçin.) İlk etiketin bir kopyası TableLayoutPanel 'in ikinci hücresinde görüntülenir. Yeniden yapıştırdığınızda, üçüncü hücrede bir başka etiket görünür. Tüm hücreler dolduruluncaya kadar `Label` denetimlerini yapıştırmayı sürdürün.

   > [!NOTE]
   > Çok fazla kez yapıştırırsanız, yeni etiket denetiminizi ekleyecek bir yer olması için IDE TabloLayoutPanel öğesine yeni bir satır yapıştırır. Bunu geri alabilirsiniz. Yeni hücreyi kaldırmak için CTRL + Z tuşlarını seçin veya menü çubuğunda **Düzenle**, **geri al**' ı seçin.

    Artık formunuz düzenlenmiştir. Aşağıdaki resim gibi görünmelidir.

    ![İlk eşleşen oyun formu](../ide/media/express-tut4step1.png "Express_Tut4Step1") İlk eşleşen oyun formu

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. [2. Adım: rastgele bir nesne ve simge listesi ekleme](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

- Genel bakış konusuna dönmek için bkz. [öğretici 3: eşleşen oyun oluşturma](../ide/tutorial-3-create-a-matching-game.md).
