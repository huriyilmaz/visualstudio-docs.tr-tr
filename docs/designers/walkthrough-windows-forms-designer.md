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
manager: jillfra
ms.openlocfilehash: f3dfdecb28254e5b9683cd1e9640c5a45b728a6c
ms.sourcegitcommit: a731a9454f1fa6bd9a18746d8d62fe2e85e5ddb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93134700"
---
# <a name="tutorial-get-started-with-windows-forms-designer"></a>Öğretici: Windows Form Tasarımcısı kullanmaya başlayın

Windows Form Tasarımcısı, Windows Forms uygulamalar oluşturmak için birçok araç sağlar. Bu makalede, aşağıdaki görevler de dahil olmak üzere tasarımcı tarafından sunulan çeşitli araçları kullanarak bir uygulamanın nasıl oluşturulacağı gösterilmektedir:

- Denetimleri, yama çizgileri kullanarak düzenleyin.
- Akıllı etiketleri kullanarak tasarımcı görevlerini gerçekleştirin.
- Denetimler için kenar boşluklarını ve doldurmayı ayarlayın.
- Denetimleri bir denetim kullanarak düzenleyin <xref:System.Windows.Forms.TableLayoutPanel> .
- Denetim kullanarak denetiminizin yerleşimini bölümleyin <xref:System.Windows.Forms.SplitContainer> .
- Belge Anahattı penceresi ile mizanpajına gidin.
- Boyut ve konum bilgileri görüntüsüne sahip denetimleri konumlandırın.
- Özellikler penceresi kullanarak özellik değerlerini ayarlayın.

İşiniz bittiğinde, Windows Form Tasarımcısı kullanılabilen çeşitli düzen özellikleri kullanılarak birleştirilen özel bir denetiminiz olacaktır. Bu denetim, basit bir Hesaplayıcı için Kullanıcı arabirimini (UI) uygular. Aşağıdaki görüntüde Hesaplayıcı denetiminin genel yerleşimi gösterilmektedir:

![Kılavuzlu Tur Hesaplayıcı Kullanıcı arabirimi](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Özel denetim projesi oluşturma

İlk adım, Demohesaplayıcı denetim projesini oluşturmaktır.

1. Visual Studio 'Yu açın ve yeni bir **Windows Forms denetim kitaplığı** projesi oluşturun. Projenin **Demohesap Torlib** olarak adlandırın.

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019 ' de denetim kitaplığı şablonu Windows Forms](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Dosyayı yeniden adlandırmak için, **Çözüm Gezgini** ' de, **UserControl1. vb** veya **UserControl1.cs** öğesine sağ tıklayın, **Yeniden Adlandır** ' ı seçin ve dosya adını demohesaplayıcı. vb veya DemoCalculator.cs olarak değiştirin. "UserControl1" kod öğesiyle tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet** ' i seçin.

Windows Form Tasarımcısı Demohesaplayıcı denetimi için tasarımcı yüzeyini gösterir. Bu görünümde, araç kutusu ' ndan denetimler ve bileşenler ' i seçip tasarımcı yüzeyine yerleştirerek denetimin görünümünü grafiksel olarak tasarlayabilirsiniz. Özel denetimler hakkında daha fazla bilgi için bkz. [Özel denetimlerin değişen özellikleri](/dotnet/framework/winforms/controls/varieties-of-custom-controls).

## <a name="design-the-control-layout"></a>Denetim düzeni tasarlama

Demohesaplayıcı denetimi çeşitli Windows Forms denetimleri içerir. Bu yordamda, Windows Form Tasarımcısı kullanarak denetimleri düzenleyebilirsiniz.

1. Windows Form Tasarımcısı, sağ alt köşedeki boyutlandırma tutamacını seçerek ve sağa sürükleyerek Demohesaplayıcı denetimini daha büyük bir boyutla değiştirin. Visual Studio 'nun sağ alt köşesinde, denetimler için boyut ve konum bilgilerini bulun. Denetimi yeniden boyutlandırırken boyut bilgilerini izleyerek denetimin boyutunu Width 500 ve Height 400 olarak ayarlayın.

2. **Araç kutusu** 'nda, açmak için **kapsayıcılar** düğümünü seçin. **SplitContainer** denetimini seçin ve tasarımcı yüzeyine sürükleyin.

   , `SplitContainer` Demohesaplayıcı denetiminin tasarımcı yüzeyine yerleştirilir.

    > [!TIP]
    > `SplitContainer`Denetim, Demohesaplayıcı denetiminin boyutunu sığacak şekilde boyutlandırır. Denetimin özellik ayarlarını görmek için **Özellikler** penceresine bakın `SplitContainer` . Özelliği bulun <xref:System.Windows.Forms.SplitContainer.Dock%2A> . Değeri [DockStyle. Fill](xref:System.Windows.Forms.DockStyle.Fill)' dir. Bu, `SplitContainer` denetimin kendisini her zaman demohesaplayıcı denetiminin sınırlarına göre boyutlandıracağı anlamına gelir. Bu davranışı doğrulamak için Demohesaplayıcı denetimini yeniden boyutlandırın.

3. **Özellikler** penceresinde, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğinin değerini olarak değiştirin `None` .

    `SplitContainer`Denetim varsayılan boyutunu küçültür ve artık Demohesaplayıcı denetiminin boyutunu takip eder.

4. Denetimin sağ üst köşesinde akıllı etiket karakterini ( ![ akıllı etiket karakteri ](media/smart-tag-glyph.gif) ) seçin `SplitContainer` . Özelliği olarak ayarlamak için **üst kapsayıcıda yerleştir '** i seçin `Dock` `Fill` .

    `SplitContainer`Denetim noktaları Demohesaplayıcı denetiminin sınırlarına göre yapılır.

    > [!NOTE]
    > Birçok denetim, tasarımı kolaylaştırmak için akıllı etiketler sunar. Daha fazla bilgi için bkz. [Izlenecek yol: Windows Forms Denetimlerinde akıllı etiketleri kullanarak ortak görevleri gerçekleştirme](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls).

5. Panolar arasındaki dikey kenarlığı seçin ve sol panel tarafından alınan alanın çoğu için sağa sürükleyin.

    `SplitContainer`Demohesaplayıcı denetimini, taşınabilir bir kenarlık ile iki panele böler. Soldaki panel, hesaplayıcı düğmelerini ve görüntülemeyi tutar ve sağdaki panel, Kullanıcı tarafından gerçekleştirilen aritmetik işlemlerin bir kaydını gösterir.

6. **Özellikler** penceresinde, `BorderStyle` özelliğinin değerini olarak değiştirin `Fixed3D` .

7. **Araç kutusu** ' nda **ortak denetimler** düğümünü seçerek açın. Denetimi seçin `ListView` ve denetimin sağ paneline sürükleyin `SplitContainer` .

8. `ListView`Denetimin akıllı etiket karakterini seçin. Akıllı etiket panelinde `View` ayarı olarak değiştirin `Details` .

9. Akıllı etiket panelinde **Sütunları Düzenle** ' yi seçin.

   **ColumnHeader koleksiyon Düzenleyicisi** iletişim kutusu açılır.

10. **ColumnHeader koleksiyon Düzenleyicisi** iletişim kutusunda, denetime sütun eklemek için **Ekle** ' yi seçin `ListView` . Sütunun `Text` özelliğinin değerini **History** olarak değiştirin. Sütunu oluşturmak için **Tamam ' ı** seçin.

11. Akıllı etiket panelinde, **Ana kapsayıcıda yerleştir** ' i seçin ve akıllı etiket panelini kapatmak için akıllı etiket glifi ' nı seçin.

12. **Kapsayıcılar** düğüm **araç kutusundan** denetimin `TableLayoutPanel` sol paneline bir denetim sürükleyin `SplitContainer` .

    `TableLayoutPanel`Denetim, akıllı etiket paneli açık olan tasarımcı yüzeyinde görünür. `TableLayoutPanel`Denetim, alt denetimlerini bir kılavuzda düzenler. `TableLayoutPanel`Denetim, Demohesaplayıcı denetiminin görüntüleme ve düğmelerini tutacaktır. Daha fazla bilgi için bkz. [Izlenecek yol: TableLayoutPanel kullanarak denetimleri düzenleme](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel).

13. Akıllı etiket panelinde **satırları ve sütunları Düzenle** ' yi seçin.

    **Sütun ve satır stilleri** iletişim kutusu açılır.

14. Beş sütun görüntülenene kadar **Ekle** düğmesini seçin. Beş sütunu da seçin ve ardından **Boyut türü** kutusunda **yüzde** ' yi seçin. **Yüzde** değerini **20** olarak ayarlayın. Bu, her sütunu aynı genişliğe ayarlar.

15. **Göster** altında **Satırlar** ' ı seçin.

16. Beş satır görüntülenene kadar **Ekle** ' yi seçin. Beş satırı ve **Boyut türü** kutusunda **yüzde** seçimini seçin. **Yüzde** değerini **20** olarak ayarlayın. Bu, her bir satırı aynı yüksekliğe ayarlar.

17. Değişikliklerinizi kabul etmek için **Tamam** ' ı seçin ve akıllı etiket panelini kapatmak için akıllı etiket glifi ' nı seçin.

18. **Özellikler** penceresinde, `Dock` özelliğinin değerini olarak değiştirin `Fill` .

## <a name="populate-the-control"></a>Denetimi doldur

Artık denetimin düzeni ayarlanmış olduğuna göre, Demohesaplayıcı denetimini düğmeler ve bir ekran ile doldurabilirsiniz.

1. **Araç kutusu** ' nda `TextBox` Denetim simgesini seçin.

   Denetim, `TextBox` denetimin ilk hücresine yerleştirilir `TableLayoutPanel` .

2. **Özellikler** penceresinde, `TextBox` denetimin ColumnSpan özelliğinin değerini **5** olarak değiştirin.

   `TextBox`Denetim, satırında ortalanmış bir konuma gider.

3. `TextBox`Denetimin `Anchor` özelliğinin değerini olarak değiştirin `Left` `Right` .

   `TextBox`Denetim, beş sütunun tamamını kapsayacak şekilde yatay olarak genişletilir.

4. `TextBox`Denetimin `TextAlign` özelliğinin değerini olarak değiştirin `Right` .

5. **Özellikler** penceresinde, `Font` özellik düğümünü genişletin. `Size` **14** olarak ayarlayın ve `Bold` Denetim için **true** olarak ayarlayın `TextBox` .

6. Denetimi seçin `TableLayoutPanel` .

7. **Araç kutusu** 'nda simgesini seçin `Button` .

   Denetim, `Button` denetimin bir sonraki açık hücresine yerleştirilir `TableLayoutPanel` .

8. **Araç kutusu** ' nda, `Button` denetimin ikinci satırını doldurmak için simgeyi dört kez daha seçin `TableLayoutPanel` .

9. `Button` **Shift** tuşunu basılı tutarken beş denetimin tamamını seçerek seçin. **Ctrl** + Denetimleri panoya kopyalamak için CTRL **C** tuşlarına basın `Button` .

10. **Ctrl** + Denetimlerin kopyalarını denetimin kalan satırlarına kopyalamak için CTRL **V** ' ye üç kez basın `Button` `TableLayoutPanel` .

11. `Button` **Shift** tuşunu basılı tutarken tüm 20 denetimleri seçerek seçin.

12. **Özellikler** penceresinde, `Dock` özelliğinin değerini olarak değiştirin `Fill` .

    Tüm `Button` denetimler, kapsayan hücrelerini dolduracak şekilde yerleştirme.

13. **Özellikler** penceresinde, `Margin` özellik düğümünü genişletin. Değerini `All` **5** olarak ayarlayın.

    Tüm denetimler, aralarında `Button` daha büyük bir kenar boşluğu oluşturmak için daha küçük boyutlardır.

14. **Button10** ve **button20** ' i seçin ve sonra düzenden kaldırmak için **Sil** ' e basın.

15. **Button5** ve **button15** öğesini seçin ve ardından `RowSpan` özelliğinin değerini **2** olarak değiştirin. Bu, **Clear** **=** demohesaplayıcı denetimi için açık ve düğmeler olacaktır.

## <a name="use-the-document-outline-window"></a>Belge Anahattı penceresini kullanın

Denetiminiz veya formunuz çeşitli denetimlerle doldurulduğu zaman, belge anahattı penceresi ile mizanpajınızı gezinmeyi daha kolay bulabilirsiniz.

1. Menü çubuğunda, **View**  >  **diğer Windows**  >  **belge anahattını** görüntüle ' yi seçin.

   Belge Anahattı penceresi, Demohesaplayıcı denetiminin ve onun bileşen denetimlerinin ağaç görünümünü gösterir. İçindeki kapsayıcı denetimleri, `SplitContainer` alt denetimlerini ağaçta alt düğümleri olarak göster. Ayrıca Belge Anahattı penceresini kullanarak yerinde denetimleri yeniden adlandırabilirsiniz.

2. **Belge ana hattı** penceresinde **button1** ' e sağ tıklayın ve ardından **Yeniden Adlandır** ' ı seçin. Adını yeti düğmesi olarak değiştirin.

3. **Belge Anahattı** penceresini kullanarak, `Button` aşağıdaki listeye göre tasarımcı tarafından oluşturulan ad içindeki denetimleri üretim adı olarak yeniden adlandırın:

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

4. **Belge ana hattını** ve **Özellikler** pencerelerini kullanarak `Text` her denetim adı için özellik değerini `Button` aşağıdaki listeye göre değiştirin:

   - On yedi düğme denetim metni özelliğini **7** olarak değiştirin

   - Sekizinci Tbutton denetim metni özelliğini **8** olarak değiştirme

   - NineButton denetim metni özelliğini **9** olarak değiştirme

   - DivisionButton denetim metni özelliğini **/** (eğik çizgi) olarak değiştirme

   - ClearButton denetim metni özelliğini **Temizle** olarak değiştirme

   - On Button denetim metni özelliğini **4** olarak değiştirin

   - FiveButton denetim metni özelliğini **5** olarak değiştirin

   - Altbutton denetim metni özelliğini **6** olarak değiştirme

   - MultiplicationButton denetim metni özelliğini * *\** _ (yıldız işareti) olarak değiştirin

   - OneButton denetim metni özelliğini _ *1* olarak değiştirin*

   - Twobtan denetim metni özelliğini **2** olarak değiştirme

   - ThreeButton denetim metni özelliğini **3** olarak değiştirme

   - SubtractionButton denetim metni özelliğini **-** (kısa çizgi) olarak değiştirme

   - EqualsButton denetim metni özelliğini **=** (eşittir işareti) olarak değiştirme

   - Zerobtan Control Text özelliğini **0** olarak değiştirme

   - ChangeSignButton denetim metni özelliğini şu şekilde değiştirin **+/-**

   - DecimalButton denetim metni özelliğini olarak değiştirin **.** (nokta)

   - AdditionButton denetim metni özelliğini **+** (artı işareti) olarak değiştirme

5. Tasarımcı yüzeyinde, `Button` **Shift** tuşunu basılı tutarken tüm denetimleri seçerek seçin.

6. **Özellikler** penceresinde, `Font` özellik düğümünü genişletin. `Size` **14** olarak ayarlayın ve `Bold` tüm denetimler için **true** olarak ayarlayın `Button` .

Bu, Demohesaplayıcı denetiminin tasarımını tamamlar. Kalan şey, hesaplayıcı mantığını sağlamaktır.

## <a name="implement-event-handlers"></a>Olay işleyicilerini Uygula

Demohesaplayıcı denetimindeki düğmelerin, hesaplayıcı mantığının çoğunu uygulamak için kullanılabilecek olay işleyicileri vardır. Windows Form Tasarımcısı, tek bir seçimle tüm düğmelerin tüm olay işleyicilerinin saplamalarını uygulamanıza olanak sağlar.

1. Tasarımcı yüzeyinde, `Button` **Shift** tuşunu basılı tutarken tüm denetimleri seçerek seçin.

2. Denetimlerden birini seçin `Button` .

   Kod Düzenleyicisi, tasarımcı tarafından oluşturulan olay işleyicileri için açılır.

## <a name="test-the-control"></a>Denetimi test etme

Demohesaplayıcı denetimi sınıfından devraldığından <xref:System.Windows.Forms.UserControl> , onun davranışını **UserControl Test kapsayıcısı** ile test edebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol).

1. **UserControl Test kapsayıcısında** demohesaplayıcı denetimini derlemek ve çalıştırmak için **F5** tuşuna basın.

2. Paneller arasındaki kenarlığı seçin `SplitContainer` ve sola ve sağa sürükleyin. `TableLayoutPanel`Ve tüm alt denetimleri, kullanılabilir alana sığacak şekilde kendilerini yeniden boyutlandırır.

3. Denetimi test etmeyi bitirdiğinizde **Kapat** ' ı seçin.

## <a name="use-the-control-on-a-form"></a>Form üzerinde denetimi kullanma

Demohesaplayıcı denetimi, diğer bileşik denetimlerde veya bir formda kullanılabilir. Aşağıdaki yordamda nasıl kullanılacağı açıklanmaktadır.

### <a name="create-the-project"></a>Proje oluşturma

İlk adım uygulama projesini oluşturmaktır. Bu projeyi, özel denetiminizi gösteren uygulamayı oluşturmak için kullanacaksınız.

1. Yeni bir **Windows Forms uygulama** projesi oluşturun ve bunu **Demohesaplatortest** olarak adlandırın.

2. **Çözüm Gezgini** , **Demohesaplatortest** projesine sağ tıklayın ve **sonra başvuru Ekle Iletişim kutusunu** açmak için **Başvuru Ekle** ' yi seçin.

3. **Projeler** sekmesine gidin ve ardından başvuruyu test projesine eklemek Için Demohesaplatorlib projesini seçin.

4. **Çözüm Gezgini** , **Demohesaplatortest** öğesine sağ tıklayın ve ardından **Başlangıç projesi olarak ayarla** ' yı seçin.

5. Windows Form Tasarımcısı, formun boyutunu **700 x 500** hakkında artırın.

### <a name="use-the-control-in-the-forms-layout"></a>Formun düzeninde denetimi kullanın

Bir uygulamada Demohesaplayıcı denetimini kullanmak için, onu bir forma yerleştirmeniz gerekir.

1. **Araç kutusu** 'Nda **Demohesaplatorlib bileşenleri** düğümünü genişletin.

2. **Araç kutusu** ' ndan **demohesaplayıcı** denetimini formunuza sürükleyin. Denetimi formun sol üst köşesine taşıyın. Denetim formun kenarlıklarına yakınsa, yama *çizgileri* görüntülenir. Anlık görüntü çizgileri, formun `Padding` özelliğinin ve denetimin özelliğinin uzaklığını belirtir `Margin` . Denetimi, snaplines belirtilen konuma konumlandırın.

   Daha fazla bilgi için bkz. [Izlenecek yol: denetimleri, yama çizgileri kullanarak düzenleme](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines).

3. `Button` **Araç kutusu** ' ndan bir denetim sürükleyip form üzerine bırakın.

4. `Button`Denetimi Demohesaplayıcı denetiminin çevresinde taşıyın ve anlık görüntü çizgilerinin nerede göründüğünü gözlemleyin. Bu özelliği kullanarak denetimlerinizi tam ve kolay bir şekilde hizalayabilirsiniz. `Button`İşiniz bittiğinde denetimi silin.

5. Demohesaplayıcı denetimine sağ tıklayıp **Özellikler** ' i seçin.

6. `Dock`Özelliğin değerini olarak değiştirin `Fill` .

7. Formu seçin ve ardından `Padding` özellik düğümünü genişletin. **All** değerini **20** olarak değiştirin.

   Demohesaplayıcı denetiminin boyutu, formun yeni değerine uyum sağlayacak şekilde azaltılır `Padding` .

8. Çeşitli boyutlandırma tutamaçlarını farklı konumlara sürükleyerek formu yeniden boyutlandırın. Demohesaplayıcı denetiminin sığması için nasıl yeniden boyutlandırıldığını gözlemleyin.

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, basit bir Hesaplayıcı için Kullanıcı arabiriminin nasıl oluşturulacağı gösterilmiştir. Devam etmek için, hesaplayıcı mantığını uygulayarak ve ardından [uygulamayı ClickOnce kullanarak yayımlayarak](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)işlevselliğini genişletebilirsiniz. Ya da [Windows Forms kullanarak bir resim görüntüleyici oluşturduğunuz](../ide/tutorial-1-create-a-picture-viewer.md)farklı bir öğreticiye devam edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms denetimleri](/dotnet/framework/winforms/controls/)
- [Windows Forms denetimleri için erişilebilirlik](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [ClickOnce kullanarak yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
