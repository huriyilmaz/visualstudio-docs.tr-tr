---
title: Windows Form Tasarımcısı öğreticisi
description: Windows Form Tasarımcısı tarafından sunulan çeşitli araçları kullanarak uygulama oluşturmayı öğrenin. Uygulama, kullanılabilen birçok düzen özelliğini kullanan özel bir denetimdir.
ms.custom: SEO-VS-2020
ms.date: 01/31/2022
ms.topic: tutorial
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.openlocfilehash: c147a2f20932d8888b25c4b7aaaa0e9a33f7a5c9
ms.sourcegitcommit: 3766c051f9a8b35106b16f751db7fecde0b92254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137951513"
---
# <a name="tutorial-get-started-with-windows-forms-designer"></a>öğretici: Windows Form Tasarımcısı kullanmaya başlayın

Windows Form Tasarımcısı, Windows Forms uygulamalar oluşturmak için birçok araç sağlar. Bu makalede, aşağıdaki görevler de dahil olmak üzere tasarımcı tarafından sunulan çeşitli araçları kullanarak bir uygulamanın nasıl oluşturulacağı gösterilmektedir:

- Denetimleri, yama çizgileri kullanarak düzenleyin.
- Akıllı etiketleri kullanarak tasarımcı görevlerini gerçekleştirin.
- Denetimler için kenar boşluklarını ve doldurmayı ayarlayın.
- Denetimleri bir <xref:System.Windows.Forms.TableLayoutPanel> denetim kullanarak düzenleyin.
- Denetim kullanarak <xref:System.Windows.Forms.SplitContainer> denetiminizin yerleşimini bölümleyin.
- Belge Anahattı penceresi ile mizanpajına gidin.
- Boyut ve konum bilgileri görüntüsüne sahip denetimleri konumlandırın.
- Özellikler penceresi kullanarak özellik değerlerini ayarlayın.

işiniz bittiğinde, Windows Form Tasarımcısı kullanılabilen çeşitli düzen özellikleri kullanılarak birleştirilen özel bir denetiminiz olacaktır. Bu denetim, basit bir Hesaplayıcı için Kullanıcı arabirimini (UI) uygular. Aşağıdaki görüntüde Hesaplayıcı denetiminin genel yerleşimi gösterilmektedir:

![Kılavuzlu Tur Hesaplayıcı Kullanıcı arabirimi](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Özel denetim projesi oluşturma

İlk adım, Demohesaplayıcı denetim projesini oluşturmaktır.

1. Visual Studio açın ve yeni bir **Windows Forms denetim kitaplığı** projesi oluşturun. Projenin **Demohesap Torlib** olarak adlandırın.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 ' de denetim kitaplığı şablonu Windows Forms](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Dosyayı yeniden adlandırmak için, **Çözüm Gezgini**' de, **UserControl1. vb** veya **UserControl1. cs** öğesine sağ tıklayın, **Yeniden Adlandır**' ı seçin ve dosya adını demohesaplayıcı. vb veya demohesaplayıcı. cs olarak değiştirin. "UserControl1" kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** ' i seçin.

Windows Form Tasarımcısı demohesaplayıcı denetimi için tasarımcı yüzeyini gösterir. Bu görünümde, araç kutusu ' ndan denetimler ve bileşenler ' i seçip tasarımcı yüzeyine yerleştirerek denetimin görünümünü grafiksel olarak tasarlayabilirsiniz. Özel denetimler hakkında daha fazla bilgi için bkz. [Özel denetimlerin değişen özellikleri](/dotnet/framework/winforms/controls/varieties-of-custom-controls).

## <a name="design-the-control-layout"></a>Denetim düzeni tasarlama

demohesaplayıcı denetimi çeşitli Windows Forms denetimleri içerir. bu yordamda, Windows Form Tasarımcısı kullanarak denetimleri düzenleyebilirsiniz.

1. Windows Form Tasarımcısı, sağ alt köşedeki boyutlandırma tutamacını seçerek ve sağa sürükleyerek demohesaplayıcı denetimini daha büyük bir boyutla değiştirin. Visual Studio sağ alt köşesinde, denetimler için boyut ve konum bilgilerini bulun. Denetimi yeniden boyutlandırırken boyut bilgilerini izleyerek denetimin boyutunu Width 500 ve Height 400 olarak ayarlayın.

2. **Araç kutusu**'nda, açmak için **kapsayıcılar** düğümünü seçin. **SplitContainer** denetimini seçin ve tasarımcı yüzeyine sürükleyin.

   , `SplitContainer` Demohesaplayıcı denetiminin tasarımcı yüzeyine yerleştirilir.

    > [!TIP]
    > `SplitContainer`Denetim, Demohesaplayıcı denetiminin boyutunu sığacak şekilde boyutlandırır. Denetimin özellik ayarlarını `SplitContainer` görmek Için **Özellikler** penceresine bakın. <xref:System.Windows.Forms.SplitContainer.Dock%2A>Özelliği bulun. Değeri [DockStyle. Fill](xref:System.Windows.Forms.DockStyle.Fill)' dir. Bu, denetimin kendisini her zaman demohesaplayıcı denetiminin sınırlarına göre boyutlandıracağı anlamına gelir `SplitContainer` . Bu davranışı doğrulamak için Demohesaplayıcı denetimini yeniden boyutlandırın.

3. **Özellikler** penceresinde, özelliğinin değerini <xref:System.Windows.Forms.SplitContainer.Dock%2A> olarak `None` değiştirin.

    `SplitContainer`Denetim varsayılan boyutunu küçültür ve artık Demohesaplayıcı denetiminin boyutunu takip eder.

4. Denetimin sağ üst köşesinde `SplitContainer` akıllı etiket karakterini ( ![ akıllı etiket karakteri ](media/smart-tag-glyph.gif) ) seçin. Özelliği olarak `Fill` ayarlamak `Dock` Için **üst kapsayıcıda yerleştir '** i seçin.

    `SplitContainer`Denetim noktaları Demohesaplayıcı denetiminin sınırlarına göre yapılır.

    > [!NOTE]
    > Birçok denetim, tasarımı kolaylaştırmak için akıllı etiketler sunar. daha fazla bilgi için bkz. [izlenecek yol: Windows Forms denetimlerinde akıllı etiketleri kullanarak ortak görevleri gerçekleştirme](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls).

5. Panolar arasındaki dikey kenarlığı seçin ve sağa sürükleyin, böylece alanın çoğu sol panel tarafından alınır.

    `SplitContainer`Demohesaplayıcı denetimini, taşınabilir bir kenarlık ile iki panele böler. Soldaki panel, hesaplayıcı düğmelerini ve görüntülemeyi tutar ve sağdaki panel, Kullanıcı tarafından gerçekleştirilen aritmetik işlemlerin bir kaydını gösterir.

6. **Özellikler** penceresinde, özelliğinin değerini `BorderStyle` olarak `Fixed3D` değiştirin.

7. **Araç kutusu**' nda **ortak denetimler** düğümünü seçerek açın. `ListView`Denetimi seçin ve denetimin sağ paneline `SplitContainer` sürükleyin.

8. `ListView`Denetimin akıllı etiket karakterini seçin. Akıllı etiket panelinde ayarı olarak `Details` değiştirin `View` .

9. Akıllı etiket panelinde **Sütunları Düzenle**' yi seçin.

   **ColumnHeader koleksiyon Düzenleyicisi** iletişim kutusu açılır.

10. **ColumnHeader koleksiyon Düzenleyicisi** iletişim kutusunda, denetime sütun `ListView` eklemek için **Ekle** ' yi seçin. Sütunun `Text` özelliğinin değerini **History** olarak değiştirin. Sütunu oluşturmak için **Tamam ' ı** seçin.

11. Akıllı etiket panelinde, **Ana kapsayıcıda yerleştir**' i seçin ve akıllı etiket panelini kapatmak için akıllı etiket glifi ' nı seçin.

12. **Kapsayıcılar** düğüm **araç kutusundan** denetimin sol paneline `SplitContainer` bir `TableLayoutPanel` Denetim sürükleyin.

    `TableLayoutPanel`Denetim, akıllı etiket paneli açık olan tasarımcı yüzeyinde görünür. Denetim, `TableLayoutPanel` alt denetimlerini bir kılavuzda düzenler. `TableLayoutPanel`Denetim, Demohesaplayıcı denetiminin görüntüleme ve düğmelerini tutacaktır. Daha fazla bilgi için bkz. [Izlenecek yol: TableLayoutPanel kullanarak denetimleri düzenleme](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel).

13. Akıllı etiket panelinde **satırları ve sütunları Düzenle** ' yi seçin.

    **Sütun ve satır stilleri** iletişim kutusu açılır.

14. Beş sütun görüntülenene kadar **Ekle** düğmesini seçin. Beş sütunu da seçin ve ardından **Boyut türü** kutusunda **yüzde** ' yi seçin. **Yüzde** değerini **20** olarak ayarlayın. Bu, her sütunu aynı genişliğe ayarlar.

15. **Göster** altında **Satırlar**' ı seçin.

16. Beş satır görüntülenene kadar **Ekle** ' yi seçin. Beş satırı ve **Boyut türü** kutusunda **yüzde** seçimini seçin. **Yüzde** değerini **20** olarak ayarlayın. Bu, her bir satırı aynı yüksekliğe ayarlar.

17. Değişikliklerinizi kabul etmek için **Tamam** ' ı seçin ve akıllı etiket panelini kapatmak için akıllı etiket glifi ' nı seçin.

18. **Özellikler** penceresinde, özelliğinin değerini `Dock` olarak `Fill` değiştirin.

## <a name="populate-the-control"></a>Denetimi doldur

Artık denetimin düzeni ayarlanmış olduğuna göre, Demohesaplayıcı denetimini düğmeler ve bir ekran ile doldurabilirsiniz.

1. **Araç kutusu**' nda denetim simgesini seçin `TextBox` .

   `TextBox`Denetim, denetimin ilk hücresine `TableLayoutPanel` yerleştirilir.

2. **Özellikler** penceresinde, denetimin ColumnSpan özelliğinin değerini `TextBox` **5** olarak değiştirin.

   `TextBox`Denetim, satırında ortalanmış bir konuma gider.

3. Denetimin `Anchor` özelliğinin `Left` değerini `TextBox` olarak `Right` değiştirin.

   Denetim, `TextBox` beş sütunun tamamını kapsayacak şekilde yatay olarak genişletilir.

4. Denetimin `TextAlign` özelliğinin değerini `TextBox` olarak `Right` değiştirin.

5. **Özellikler** penceresinde, özellik düğümünü genişletin `Font` . **14** olarak ayarlayın `Size` ve denetim için `TextBox` **true** olarak ayarlayın `Bold` .

6. `TableLayoutPanel`Denetimi seçin.

7. **Araç kutusu**'nda simgesini seçin `Button` .

   Denetim, denetimin bir `Button` sonraki açık hücresine `TableLayoutPanel` yerleştirilir.

8. **Araç kutusu**' nda, denetimin ikinci satırını `TableLayoutPanel` doldurmak için simgeyi dört kez daha seçin `Button` .

9. **Shift** tuşunu basılı tutarken beş `Button` denetimin tamamını seçerek seçin. Denetimleri panoya kopyalamak `Button` için **CTRL** + **C** tuşlarına basın.

10. Denetimlerin kopyalarını `Button` denetimin kalan satırlarına `TableLayoutPanel` kopyalamak için **CTRL** + **V** ' ye üç kez basın.

11. **Shift** tuşunu basılı tutarken tüm 20 `Button` denetimleri seçerek seçin.

12. **Özellikler** penceresinde, özelliğinin değerini `Dock` olarak `Fill` değiştirin.

    Tüm denetimler, `Button` kapsayan hücrelerini dolduracak şekilde yerleştirme.

13. **Özellikler** penceresinde, özellik düğümünü genişletin `Margin` . Değerini `All` **5** olarak ayarlayın.

    Tüm denetimler, `Button` aralarında daha büyük bir kenar boşluğu oluşturmak için daha küçük boyutlardır.

14. **Button10** ve **button20**' i seçin ve sonra düzenden kaldırmak için **Sil** ' e basın.

15. **Button5** ve **button15** öğesini seçin ve ardından özelliğinin değerini `RowSpan` **2** olarak değiştirin. Bu, Demohesaplayıcı denetimi için **Açık** ve **=** düğmeler olacaktır.

## <a name="use-the-document-outline-window"></a>Belge Anahattı penceresini kullanın

Denetiminiz veya formunuz çeşitli denetimlerle doldurulduğu zaman, belge anahattı penceresi ile mizanpajınızı gezinmeyi daha kolay bulabilirsiniz.

1. menü çubuğunda **diğer Windows**  >  **belge anahattını** **görüntüle**  >  ' yi seçin.

   Belge Anahattı penceresi, Demohesaplayıcı denetiminin ve onun bileşen denetimlerinin ağaç görünümünü gösterir. İçindeki kapsayıcı denetimleri, `SplitContainer` alt denetimlerini ağaçta alt düğümleri olarak göster. Ayrıca Belge Anahattı penceresini kullanarak yerinde denetimleri yeniden adlandırabilirsiniz.

2. **Belge ana hattı** penceresinde **button1**' e sağ tıklayın ve ardından **Yeniden Adlandır**' ı seçin. Adını yeti düğmesi olarak değiştirin.

3. **Belge Anahattı** penceresini kullanarak, aşağıdaki listeye göre tasarımcı tarafından oluşturulan ad içindeki denetimleri üretim adı olarak yeniden adlandırın `Button` :

   - Button1- **on yedi düğmesi**

   - Button2 to **Sektbutton**

   - Button3 to **nineButton**

   - Button4 to **divisionButton**

   - Button5 to **clearButton**

   - Button6 to **on düğmesi**

   - button7 to **Fıvebutton**

   - button8 to **Altbutton**

   - Button9 to **multiplicationButton**

   - button11 to **oneButton**

   - button12- **Twobtan**

   - button13 to **threeButton**

   - button14 to **subtractionButton**

   - button15 to **equalsButton**

   - button16 to **Zerobtan**

   - button17 to **changeSignButton**

   - button18 to **decimalButton**

   - button19 to **additionButton**

4. **Belge ana hattını** ve **Özellikler** pencerelerini kullanarak her `Button` Denetim adı için özellik değerini aşağıdaki listeye göre değiştirin `Text` :

   - On yedi düğme denetim metni özelliğini **7** olarak değiştirin

   - Sekizinci Tbutton denetim metni özelliğini **8** olarak değiştirme

   - NineButton denetim metni özelliğini **9** olarak değiştirme

   - DivisionButton denetim metni özelliğini (eğik çizgi) olarak **/** değiştirme

   - ClearButton denetim metni özelliğini **Temizle** olarak değiştirme

   - On Button denetim metni özelliğini **4** olarak değiştirin

   - FiveButton denetim metni özelliğini **5** olarak değiştirin

   - Altbutton denetim metni özelliğini **6** olarak değiştirme

   - MultiplicationButton denetim metni özelliğini (yıldız işareti) olarak **\*** değiştirme

   - OneButton denetim metni özelliğini **1** olarak değiştirin

   - Twobtan denetim metni özelliğini **2** olarak değiştirme

   - ThreeButton denetim metni özelliğini **3** olarak değiştirme

   - SubtractionButton denetim metni özelliğini (kısa çizgi) olarak **-** değiştirme

   - EqualsButton denetim metni özelliğini (eşittir işareti) olarak **=** değiştirme

   - Zerobtan Control Text özelliğini **0** olarak değiştirme

   - ChangeSignButton denetim metni özelliğini şu şekilde değiştirin **+/-**

   - DecimalButton denetim metni özelliğini olarak değiştirin **.** (nokta)

   - AdditionButton denetim metni özelliğini (artı işareti) olarak **+** değiştirme

5. Tasarımcı yüzeyinde, **Shift** tuşunu basılı tutarken tüm `Button` denetimleri seçerek seçin.

6. **Özellikler** penceresinde, özellik düğümünü genişletin `Font` . **14** olarak ayarlayın `Size` ve tüm `Button` denetimler için **true** olarak ayarlayın. `Bold`

Bu, Demohesaplayıcı denetiminin tasarımını tamamlar. Kalan şey, hesaplayıcı mantığını sağlamaktır.

## <a name="implement-event-handlers"></a>Olay işleyicilerini Uygula

Demohesaplayıcı denetimindeki düğmelerin, hesaplayıcı mantığının çoğunu uygulamak için kullanılabilecek olay işleyicileri vardır. Windows Form Tasarımcısı, tek bir seçimle tüm düğmelerin tüm olay işleyicilerinin saplamalarını uygulamanıza olanak sağlar.

1. Tasarımcı yüzeyinde, **Shift** tuşunu basılı tutarken tüm `Button` denetimleri seçerek seçin.

2. Denetimlerden birini `Button` seçin.

   Kod Düzenleyicisi, tasarımcı tarafından oluşturulan olay işleyicileri için açılır.

## <a name="test-the-control"></a>Denetimi test etme

Demohesaplayıcı denetimi sınıfından devraldığından <xref:System.Windows.Forms.UserControl> , onun davranışını **UserControl Test kapsayıcısı** ile test edebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol).

1. **UserControl Test kapsayıcısında** demohesaplayıcı denetimini derlemek ve çalıştırmak için **F5** tuşuna basın.

2. Paneller arasındaki `SplitContainer` kenarlığı seçin ve sola ve sağa sürükleyin. Ve tüm alt denetimleri, `TableLayoutPanel` kullanılabilir alana sığacak şekilde kendilerini yeniden boyutlandırır.

3. Denetimi test etmeyi bitirdiğinizde **Kapat**' ı seçin.

## <a name="use-the-control-on-a-form"></a>Form üzerinde denetimi kullanma

Demohesaplayıcı denetimi, diğer bileşik denetimlerde veya bir formda kullanılabilir. Aşağıdaki yordamda nasıl kullanılacağı açıklanmaktadır.

### <a name="create-the-project"></a>Proje oluşturma

İlk adım uygulama projesini oluşturmaktır. Bu projeyi, özel denetiminizi gösteren uygulamayı oluşturmak için kullanacaksınız.

1. yeni bir **Windows Forms uygulama** projesi oluşturun ve bunu **demohesaplatortest** olarak adlandırın.

2. **Çözüm Gezgini**, **demohesaplatortest** projesine sağ tıklayın ve ardından **başvuru yöneticisi** iletişim kutusunu açmak için **Project başvuru** **ekle**  >  ' yi seçin.

    (Visual Studio 2017 kullanıyorsanız başvuru **yöneticisi** iletişim kutusunu açmak için **başvuru** **ekle**  >  ' yi seçin.)

3. **Projeler** sekmesine gidin ve ardından başvuruyu test projesine eklemek Için Demohesaplatorlib projesini seçin.

4. **Çözüm Gezgini**, **Demohesaplatortest** öğesine sağ tıklayın ve ardından **Başlangıç Project olarak ayarla**' yı seçin.

5. Windows Form Tasarımcısı, formun boyutunu **700 x 500** hakkında artırın.

### <a name="use-the-control-in-the-forms-layout"></a>Formun düzeninde denetimi kullanın

Bir uygulamada Demohesaplayıcı denetimini kullanmak için, onu bir forma yerleştirmeniz gerekir.

1. **Araç kutusu**'Nda **Demohesaplatorlib bileşenleri** düğümünü genişletin.

2. **Araç kutusu** ' ndan **demohesaplayıcı** denetimini formunuza sürükleyin. Denetimi formun sol üst köşesine taşıyın. Denetim formun kenarlıklarına yakınsa, yama *çizgileri* görüntülenir. Anlık görüntü çizgileri, formun `Padding` özelliğinin ve denetimin `Margin` özelliğinin uzaklığını belirtir. Denetimi, snaplines belirtilen konuma konumlandırın.

   Daha fazla bilgi için bkz. [Izlenecek yol: denetimleri, yama çizgileri kullanarak düzenleme](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines).

3. **Araç kutusu** ' ndan bir `Button` Denetim sürükleyip form üzerine bırakın.

4. `Button`Denetimi Demohesaplayıcı denetiminin çevresinde taşıyın ve anlık görüntü çizgilerinin nerede göründüğünü gözlemleyin. Bu özelliği kullanarak denetimlerinizi tam ve kolay bir şekilde hizalayabilirsiniz. `Button`İşiniz bittiğinde denetimi silin.

5. Demohesaplayıcı denetimine sağ tıklayıp **Özellikler**' i seçin.

6. Özelliğin değerini `Dock` olarak `Fill` değiştirin.

7. Formu seçin ve ardından özellik düğümünü `Padding` genişletin. All (Hepsi) **değerini** **20 olarak değiştirir**.

   DemoCalculator denetimi, formun yeni değerine uyum sağlayacak `Padding` şekilde azaltıldı.

8. Çeşitli boyutlandırma tutamaçlarını farklı konumlara sürükleyerek formu yeniden boyutlandırabilirsiniz. DemoCalculator denetimine sığacak şekilde nasıl yeniden boyutlandırıldıklarını gözlemlemek.

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, basit bir hesaplayıcı için kullanıcı arabiriminin nasıl inşa edildikleri açıklanmıştır. Devam etmek için hesap makinesi mantığını uygulayarak işlevselliğini genişletebilirsiniz, sonra da hesap makinesi mantığını [kullanarak ClickOnce](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md). Veya Formlar'ı kullanarak resim [görüntüleyiciyi oluşturarak farklı bir Windows devam edin](../ide/tutorial-windows-forms-picture-viewer-layout.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms denetimleri](/dotnet/framework/winforms/controls/)
- [Windows Forms denetimleri için erişilebilirlik](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [ClickOnce kullanarak yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
