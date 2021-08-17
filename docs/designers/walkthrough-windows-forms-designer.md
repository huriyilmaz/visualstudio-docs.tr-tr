---
title: Windows Form Tasarımcısı öğreticisi
description: Windows Form Tasarımcısı tarafından sunulan çeşitli araçları kullanarak uygulama oluşturmayı öğrenin. Uygulama, kullanılabilen birçok düzen özelliğini kullanan özel bir denetimdir.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: tutorial
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.openlocfilehash: 95c8d746e39fdf4c5536dd69028c5f246280ba5c76a51f69ee4c92eea21f52c3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121452905"
---
# <a name="tutorial-get-started-with-windows-forms-designer"></a>öğretici: Windows Form Tasarımcısı kullanmaya başlayın

Windows Form Tasarımcısı, Windows Forms uygulamalar oluşturmak için birçok araç sağlar. Bu makalede, aşağıdaki görevler de dahil olmak üzere tasarımcı tarafından sunulan çeşitli araçları kullanarak bir uygulamanın nasıl oluşturulacağı gösterilmektedir:

- Denetimleri, yama çizgileri kullanarak düzenleyin.
- Akıllı etiketleri kullanarak tasarımcı görevlerini gerçekleştirin.
- Denetimler için kenar boşluklarını ve doldurmayı ayarlayın.
- Denetimleri bir denetim kullanarak düzenleyin <xref:System.Windows.Forms.TableLayoutPanel> .
- Denetim kullanarak denetiminizin yerleşimini bölümleyin <xref:System.Windows.Forms.SplitContainer> .
- Belge Anahattı penceresi ile mizanpajına gidin.
- Boyut ve konum bilgileri görüntüsüne sahip denetimleri konumlandırın.
- Özellikler penceresi kullanarak özellik değerlerini ayarlayın.

işiniz bittiğinde, Windows Form Tasarımcısı kullanılabilen çeşitli düzen özellikleri kullanılarak birleştirilen özel bir denetiminiz olacaktır. Bu denetim, basit bir Hesaplayıcı için Kullanıcı arabirimini (UI) uygular. Aşağıdaki görüntüde Hesaplayıcı denetiminin genel yerleşimi gösterilmektedir:

![Kılavuzlu Tur Hesaplayıcı Kullanıcı arabirimi](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Özel denetim projesi oluşturma

İlk adım, Demohesaplayıcı denetim projesini oluşturmaktır.

1. Visual Studio açın ve yeni bir **Windows Forms denetim kitaplığı** projesi oluşturun. Projenin **Demohesap Torlib** olarak adlandırın.

   ::: moniker range=">=vs-2019"

   ![Windows Visual Studio 2019 ' de Forms denetim kitaplığı şablonu](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Dosyayı yeniden adlandırmak için, **Çözüm Gezgini**' de, **UserControl1. vb** veya **UserControl1. cs** öğesine sağ tıklayın, **Yeniden Adlandır**' ı seçin ve dosya adını demohesaplayıcı. vb veya demohesaplayıcı. cs olarak değiştirin. "UserControl1" kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** ' i seçin.

Windows Form Tasarımcısı demohesaplayıcı denetimi için tasarımcı yüzeyini gösterir. Bu görünümde, araç kutusu ' ndan denetimler ve bileşenler ' i seçip tasarımcı yüzeyine yerleştirerek denetimin görünümünü grafiksel olarak tasarlayabilirsiniz. Özel denetimler hakkında daha fazla bilgi için bkz. [Özel denetimlerin değişen özellikleri](/dotnet/framework/winforms/controls/varieties-of-custom-controls).

## <a name="design-the-control-layout"></a>Denetim düzeni tasarlama

demohesaplayıcı denetimi çeşitli Windows Forms denetimleri içerir. bu yordamda, Windows Form Tasarımcısı kullanarak denetimleri düzenleyebilirsiniz.

1. Windows Form Tasarımcısı, sağ alt köşedeki boyutlandırma tutamacını seçerek ve sağa sürükleyerek demohesaplayıcı denetimini daha büyük bir boyutla değiştirin. Visual Studio sağ alt köşesinde, denetimler için boyut ve konum bilgilerini bulun. Denetimi yeniden boyutlandırırken boyut bilgilerini izleyerek denetimin boyutunu Width 500 ve Height 400 olarak ayarlayın.

2. **Araç kutusu**'nda, açmak için **kapsayıcılar** düğümünü seçin. **SplitContainer** denetimini seçin ve tasarımcı yüzeyine sürükleyin.

   , `SplitContainer` Demohesaplayıcı denetiminin tasarımcı yüzeyine yerleştirilir.

    > [!TIP]
    > `SplitContainer`Denetim, Demohesaplayıcı denetiminin boyutunu sığacak şekilde boyutlandırır. Denetimin özellik ayarlarını görmek için **Özellikler** penceresine bakın `SplitContainer` . Özelliği bulun <xref:System.Windows.Forms.SplitContainer.Dock%2A> . Değeri [DockStyle. Fill](xref:System.Windows.Forms.DockStyle.Fill)' dir. Bu, `SplitContainer` denetimin kendisini her zaman demohesaplayıcı denetiminin sınırlarına göre boyutlandıracağı anlamına gelir. Bu davranışı doğrulamak için Demohesaplayıcı denetimini yeniden boyutlandırın.

3. **Özellikler** penceresinde, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğinin değerini olarak değiştirin `None` .

    `SplitContainer`Denetim varsayılan boyutunu küçültür ve artık Demohesaplayıcı denetiminin boyutunu takip eder.

4. Denetimin sağ üst köşesinde akıllı etiket karakterini ( ![ akıllı etiket karakteri ](media/smart-tag-glyph.gif) ) seçin `SplitContainer` . Özelliği olarak ayarlamak için **üst kapsayıcıda yerleştir '** i seçin `Dock` `Fill` .

    `SplitContainer`Denetim noktaları Demohesaplayıcı denetiminin sınırlarına göre yapılır.

    > [!NOTE]
    > Birçok denetim, tasarımı kolaylaştırmak için akıllı etiketler sunar. daha fazla bilgi için bkz. [izlenecek yol: Windows Forms denetimlerinde akıllı etiketleri kullanarak ortak görevleri gerçekleştirme](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls).

5. Panolar arasındaki dikey kenarlığı seçin ve sağa sürükleyin, böylece alanın çoğu sol panel tarafından alınır.

    `SplitContainer`Demohesaplayıcı denetimini, taşınabilir bir kenarlık ile iki panele böler. Soldaki panel, hesaplayıcı düğmelerini ve görüntülemeyi tutar ve sağdaki panel, Kullanıcı tarafından gerçekleştirilen aritmetik işlemlerin bir kaydını gösterir.

6. **Özellikler** penceresinde, `BorderStyle` özelliğinin değerini olarak değiştirin `Fixed3D` .

7. **Araç kutusu**' nda **ortak denetimler** düğümünü seçerek açın. Denetimi seçin `ListView` ve denetimin sağ paneline sürükleyin `SplitContainer` .

8. `ListView`Denetimin akıllı etiket karakterini seçin. Akıllı etiket panelinde `View` ayarı olarak değiştirin `Details` .

9. Akıllı etiket panelinde **Sütunları Düzenle**' yi seçin.

   **ColumnHeader koleksiyon Düzenleyicisi** iletişim kutusu açılır.

10. **ColumnHeader koleksiyon Düzenleyicisi** iletişim kutusunda, denetime sütun eklemek için **Ekle** ' yi seçin `ListView` . Sütunun `Text` özelliğinin değerini **History** olarak değiştirin. Sütunu oluşturmak için **Tamam ' ı** seçin.

11. Akıllı etiket panelinde, **Ana kapsayıcıda yerleştir**' i seçin ve akıllı etiket panelini kapatmak için akıllı etiket glifi ' nı seçin.

12. **Kapsayıcılar** düğüm **araç kutusundan** denetimin `TableLayoutPanel` sol paneline bir denetim sürükleyin `SplitContainer` .

    `TableLayoutPanel`Denetim, akıllı etiket paneli açık olan tasarımcı yüzeyinde görünür. `TableLayoutPanel`Denetim, alt denetimlerini bir kılavuzda düzenler. `TableLayoutPanel`Denetim, Demohesaplayıcı denetiminin görüntüleme ve düğmelerini tutacaktır. Daha fazla bilgi için bkz. [Izlenecek yol: TableLayoutPanel kullanarak denetimleri düzenleme](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel).

13. Akıllı etiket panelinde **satırları ve sütunları Düzenle** ' yi seçin.

    **Sütun ve satır stilleri** iletişim kutusu açılır.

14. Beş sütun görüntülenene kadar **Ekle** düğmesini seçin. Beş sütunu da seçin ve ardından **Boyut türü** kutusunda **yüzde** ' yi seçin. **Yüzde** değerini **20** olarak ayarlayın. Bu, her sütunu aynı genişliğe ayarlar.

15. **Göster** altında **Satırlar**' ı seçin.

16. Beş satır görüntülenene kadar **Ekle** ' yi seçin. Beş satırı ve **Boyut türü** kutusunda **yüzde** seçimini seçin. **Yüzde** değerini **20** olarak ayarlayın. Bu, her bir satırı aynı yüksekliğe ayarlar.

17. Değişikliklerinizi kabul etmek için **Tamam** ' ı seçin ve akıllı etiket panelini kapatmak için akıllı etiket glifi ' nı seçin.

18. **Özellikler** penceresinde, `Dock` özelliğinin değerini olarak değiştirin `Fill` .

## <a name="populate-the-control"></a>Denetimi doldur

Artık denetimin düzeni ayarlanmış olduğuna göre, Demohesaplayıcı denetimini düğmeler ve bir ekran ile doldurabilirsiniz.

1. **Araç kutusu**' nda `TextBox` Denetim simgesini seçin.

   Denetim, `TextBox` denetimin ilk hücresine yerleştirilir `TableLayoutPanel` .

2. **Özellikler** penceresinde, `TextBox` denetimin ColumnSpan özelliğinin değerini **5** olarak değiştirin.

   `TextBox`Denetim, satırında ortalanmış bir konuma gider.

3. `TextBox`Denetimin `Anchor` özelliğinin değerini olarak değiştirin `Left` `Right` .

   `TextBox`Denetim, beş sütunun tamamını kapsayacak şekilde yatay olarak genişletilir.

4. `TextBox`Denetimin `TextAlign` özelliğinin değerini olarak değiştirin `Right` .

5. **Özellikler** penceresinde, `Font` özellik düğümünü genişletin. `Size` **14** olarak ayarlayın ve `Bold` Denetim için **true** olarak ayarlayın `TextBox` .

6. Denetimi seçin `TableLayoutPanel` .

7. **Araç kutusu**'nda simgesini seçin `Button` .

   Denetim, `Button` denetimin bir sonraki açık hücresine yerleştirilir `TableLayoutPanel` .

8. **Araç kutusu**' nda, `Button` denetimin ikinci satırını doldurmak için simgeyi dört kez daha seçin `TableLayoutPanel` .

9. `Button` **Shift** tuşunu basılı tutarken beş denetimin tamamını seçerek seçin.  + Denetimleri panoya kopyalamak için CTRL **C** tuşlarına basın `Button` .

10.  + Denetimlerin kopyalarını denetimin kalan satırlarına kopyalamak için CTRL **V** ' ye üç kez basın `Button` `TableLayoutPanel` .

11. `Button` **Shift** tuşunu basılı tutarken tüm 20 denetimleri seçerek seçin.

12. Özellikler **penceresinde** özelliğinin değerini olarak `Dock` `Fill` değiştirin.

    Tüm `Button` denetimler, içeren hücreleri doldurmak için dock'a sahiptir.

13. Özellikler **penceresinde** özellik `Margin` düğümünü genişletin. değerini `All` **5 olarak ayarlayın.**

    Tüm `Button` denetimler, aralarında daha büyük bir kenar boşluğu oluşturmak için daha küçük boyutlu olur.

14. **düğme10 ve** **düğme20'yi** seçin ve sonra **bunları düzenden** kaldırmak için Sil'e basın.

15. **düğme5'i** **ve düğme15'i** seçin ve ardından özelliğinin `RowSpan` değerini **2 olarak değiştirir.** Bunlar DemoCalculator **denetimi** **=** için Clear ve düğmeleridir.

## <a name="use-the-document-outline-window"></a>Belge Ana Hat penceresini kullanma

Denetiminiz veya formunuz çeşitli denetimlerle doldurulduğunda, Belge Ana Hat penceresiyle düzeninize daha kolay bir şekilde gidebilirsiniz.

1. Menü çubuğunda, Belge Ana **Hatlarını Görüntülemek**  >  **için**  >  **Windows'yi seçin.**

   Belge Ana Hat penceresi DemoCalculator denetimi ve onun bağlı denetimlerinin ağaç görünümünü gösterir. gibi kapsayıcı `SplitContainer` denetimleri, alt denetimlerini ağaçta altnode olarak gösterir. Ayrıca Belge Ana Hat penceresini kullanarak denetimleri yerinde yeniden adlandırabilirsiniz.

2. Belge Ana **Hat penceresinde1** düğmesine sağ tıklayın **ve** yeniden adlandır'ı **seçin.** Adını sevenButton olarak değiştirme.

3. Belge Ana **Hat penceresini** kullanarak, tasarımcı tarafından oluşturulan addan denetimleri aşağıdaki listeye göre üretim adıyla `Button` yeniden adlandırın:

   - button1'den **sevenButton'a**

   - button2'den **eightButton'a**

   - button3'den **nineButton'a**

   - button4'den **divisionButton'a**

   - button5 to **clearButton**

   - button6 'dan **fourButton'a**

   - button7 'den **fiveButton'a**

   - button8 'den **sixButton'a**

   - button9'dan **çarpmadüzmesidüz**

   - button11'den **oneButton'a**

   - button12 'den **twoButton'a**

   - button13 'den **threeButton'a**

   - button14 to **subtractionButton**

   - button15 to **equalsButton**

   - button16'dan **zeroButton'a**

   - **changeSignButton** için button17

   - button18'den **decimalButton'a**

   - button19'dan **additionButton'a**

4. Belge Ana **Hatları ve** **Özellikler** pencerelerini kullanarak her denetim adı için özellik değerini aşağıdaki listeye `Text` göre `Button` değiştirin:

   - sevenButton denetim metni özelliğini **7 olarak değiştirme**

   - eightButton denetim metni özelliğini **8 olarak değiştirme**

   - nineButton denetim metni özelliğini **9 olarak değiştirme**

   - divisionButton denetim metni özelliğini olarak (eğik **/** çizgi) değiştirme

   - clearButton denetim metni özelliğini Clear olarak **değiştirme**

   - fourButton denetim metni özelliğini **4 olarak değiştirme**

   - fiveButton denetim metni özelliğini **5 olarak değiştirme**

   - sixButton denetim metni özelliğini **6 olarak değiştirme**

   - multiplicationButton denetim metni özelliğini **\*** (yıldız işareti) olarak değiştirme

   - oneButton denetim metni özelliğini **1 olarak değiştirme**

   - twoButton denetim metni özelliğini **2 olarak değiştirme**

   - threeButton denetim metni özelliğini **3 olarak değiştirme**

   - subtractionButton denetim metni özelliğini (kısa **-** çizgi) olarak değiştirme

   - equalsButton denetim metni özelliğini **=** (eşittir işareti) olarak değiştirme

   - zeroButton denetim metni özelliğini **0 olarak değiştirme**

   - changeSignButton denetim metni özelliğini olarak değiştirme **+/-**

   - decimalButton denetim metni özelliğini olarak **değiştirme.** (nokta)

   - additionButton denetim metni özelliğini (artı **+** işareti) olarak değiştirme

5. Tasarımcı yüzeyinde, Shift tuşunu basılı `Button` tutarak tüm denetimleri  seçin.

6. Özellikler **penceresinde** özellik `Font` düğümünü genişletin. `Size` **14 olarak ayarlayın** ve tüm `Bold` **denetimler için true** olarak `Button` ayarlayın.

Bu, DemoCalculator denetimi tasarımını tamamlar. Kalan tek şey hesap makinesi mantığı sağlamaktır.

## <a name="implement-event-handlers"></a>Olay işleyicileri uygulama

DemoCalculator denetimi düğmeleri, hesap makinesi mantığının büyük bir sini uygulamak için kullanılan olay işleyicilerine sahip olur. Windows Forms Tasarımcısı, tek bir seçimle tüm düğmeler için tüm olay işleyicilerinin saplamalarını uygulamana olanak sağlar.

1. Tasarımcı yüzeyinde, Shift tuşunu basılı `Button` tutarak tüm denetimleri  seçin.

2. Denetimlerden birini `Button` seçin.

   Kod Düzenleyicisi, tasarımcı tarafından oluşturulan olay işleyicilerini açar.

## <a name="test-the-control"></a>Denetimi test etmek

DemoCalculator denetimi sınıfından devralınmış olduğundan, davranışını <xref:System.Windows.Forms.UserControl> UserControl Test Kapsayıcısı **ile test edin.** Daha fazla bilgi için, [bkz. How to: Test the run-time behavior of a UserControl](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol).

1. UserControl Test Kapsayıcısı içinde DemoCalculator denetimi derlemek ve çalıştırmak için **F5** **tuşuna basın.**

2. Paneller arasındaki `SplitContainer` kenarlığı seçin ve sola ve sağa sürükleyin. ve `TableLayoutPanel` tüm alt denetimleri kullanılabilir alana sığacak şekilde yeniden boyutlandırılır.

3. Denetimi test etme tamamlandığında Kapat'ı **seçin.**

## <a name="use-the-control-on-a-form"></a>Formda denetimi kullanma

DemoCalculator denetimi diğer bileşik denetimlerde veya bir formda kullanılabilir. Aşağıdaki yordamda bu yordamın nasıl kullanımı açık bir şekilde açıkmektedir.

### <a name="create-the-project"></a>Proje oluşturma

İlk adım, uygulama projesini oluşturmaktır. Bu projeyi kullanarak özel denetiminizi gösteren uygulamayı derlemeniz gerekir.

1. Yeni bir form **Windows Forms Uygulaması projesi** oluşturun ve bunu **DemoCalculatorTest olarak ad girin.**

2. Bu **Çözüm Gezgini,** **DemoCalculatorTest** projesine sağ tıklayın ve  başvuru ekle iletişim kutusunu açmak için Başvuru **Ekle'yi** seçin.

3. Projeler **sekmesine** gidin ve ardından DemoCalculatorLib projesini seçerek test projesine başvuru ekleyin.

4. Bu **Çözüm Gezgini** **DemoCalculatorTest'e** sağ tıklayın ve Ardından Başlangıç Olarak **Ayarla'yı** Project.

5. Windows Form Tasarımcısı'nda formun boyutunu yaklaşık **700 x 500 olarak artırabilirsiniz.**

### <a name="use-the-control-in-the-forms-layout"></a>Formun düzeninde denetimi kullanma

Bir uygulamada DemoCalculator denetimi kullanmak için bunu bir forma yer gerekir.

1. Araç **Kutusunda** **DemoCalculatorLib Bileşenleri düğümünü** genişletin.

2. Araç **Kutusundan DemoCalculator** **denetiminizi form** üzerine sürükleyin. Denetimi formun sol üst köşesine taşıma. Denetim formun kenarlıklara yakın olduğunda, *yaslık çizgileri* görüntülenir. Yas çizgileri, formun özelliğinin `Padding` ve denetimin özelliğinin mesafeyi `Margin` gösteriyor. Denetimi, yaslık çizgilerinin işaret olduğu konuma konumlandırma.

   Daha fazla bilgi için [bkz. Adım adım kılavuz: Denetimleri yas çizgileri kullanarak düzenleme.](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines)

3. Araç `Button` Kutusundan **bir denetimi** sürükleyip forma bırakın.

4. Denetimi `Button` DemoCalculator denetimi çevresinde hareket ettirin ve yaslama çizgilerinin nerede görüntülenmiş olduğunu gözlemler. Bu özelliği kullanarak denetimlerinizi tam olarak ve kolayca hizalayabilirsiniz. Bitirdikten `Button` sonra denetimi silin.

5. DemoCalculator denetimine sağ tıklayın ve Özellikler'i **seçin.**

6. özelliğinin değerini `Dock` olarak `Fill` değiştirme.

7. Formu seçin ve ardından özellik `Padding` düğümünü genişletin. All (Hepsi) **değerini** **20 olarak değiştirir.**

   DemoCalculator denetimi, formun yeni değerine uyum sağlayacak `Padding` şekilde azaltıldı.

8. Çeşitli boyutlandırma tutamaçlarını farklı konumlara sürükleyerek formu yeniden boyutlandırabilirsiniz. DemoCalculator denetimine sığacak şekilde nasıl yeniden boyutlandırıldıklarını gözlemlemek.

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, basit bir hesaplayıcı için kullanıcı arabiriminin nasıl inşa edildikleri açıklanmıştır. Devam etmek için hesap makinesi mantığını uygulayarak işlevselliğini genişletebilirsiniz ve ardından uygulamayı [ClickOnce.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) Veya , Formlar'ı kullanarak resim [görüntüleyiciyi oluşturarak farklı bir Windows devam edin.](../ide/tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms denetimleri](/dotnet/framework/winforms/controls/)
- [Windows Forms denetimleri için erişilebilirlik](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [ClickOnce kullanarak yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
