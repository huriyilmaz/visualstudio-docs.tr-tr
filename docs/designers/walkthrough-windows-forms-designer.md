---
title: Windows Form Tasarımcısı öğreticisi
description: Windows Forms Designer tarafından sağlanan çeşitli araçları kullanarak Windows öğrenin. Uygulama, birçok kullanılabilir düzen özelliği kullanan özel bir denetimdir.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: tutorial
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.openlocfilehash: 6e43c010e84f31b39167baa60cef6cceb7b21c25
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035416"
---
# <a name="tutorial-get-started-with-windows-forms-designer"></a>Öğretici: Kullanmaya başlayın Forms Windows ile birlikte kullanma

Windows Forms Tasarımcısı, Formlar uygulamaları oluşturmak için Windows araçlar sağlar. Bu makalede, aşağıdaki görevler de dahil olmak üzere tasarımcı tarafından sağlanan çeşitli araçları kullanarak uygulama oluşturma adımları açıklanmıştır:

- Yas çizgileri kullanarak denetimleri düzenleme.
- Akıllı etiketleri kullanarak tasarımcı görevlerini gerçekleştirin.
- Denetimler için kenar boşluklarını ve doldurmayı ayarlayın.
- Denetim kullanarak denetimleri <xref:System.Windows.Forms.TableLayoutPanel> düzenleme.
- Denetim kullanarak denetiminizin düzenini <xref:System.Windows.Forms.SplitContainer> bölümleme.
- Belge Ana Hat penceresiyle düzeninize gidin.
- Denetimleri boyut ve konum bilgileriyle birlikte konumlandırma.
- özelliğini kullanarak özellik değerlerini Özellikler penceresi.

Bitirdikten sonra, Windows Forms Tasarımcısı'nda bulunan düzen özelliklerinin birçoğu kullanılarak birleştirilmiş özel bir denetime sahip oluruz. Bu denetim, basit bir hesaplayıcı için kullanıcı arabirimini (UI) uygulamaya almaktadır. Aşağıdaki görüntüde hesap makinesi denetimi genel düzeni gösterir:

![Kılavuzlu Tur Hesaplayıcısı Kullanıcı Arabirimi](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Özel denetim projesi oluşturma

İlk adım DemoCalculator denetim projesini oluşturmaktır.

1. Form Visual Studio'i açın ve yeni bir **Windows Forms Denetim Kitaplığı projesi** oluşturun. Projeye **DemoCalculatorLib adını girin.**

   ::: moniker range=">=vs-2019"

   ![Windows Visual Studio 2019'da Forms Denetim Kitaplığı şablonu](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Dosyayı yeniden adlandırmak **için Çözüm Gezgini'de** **UserControl1.vb** veya **UserControl1.cs'ye** sağ tıklayın, Yeniden Adlandır'ı seçin ve dosya adını DemoCalculator.vb veya DemoCalculator.cs olarak değiştirebilirsiniz.  "UserControl1" kod öğesine yapılan tüm başvuruları yeniden adlandırmak istediğiniz sorulması için Evet'i seçin. 

Windows Forms Tasarımcısı, DemoCalculator denetimi için tasarımcı yüzeyini gösterir. Bu görünümde, Araç Kutusu'nda denetimleri ve bileşenleri seçerek ve bunları tasarımcı yüzeyine yerleştirerek denetimin görünümünü grafiksel olarak tasarabilirsiniz. Özel denetimler hakkında daha fazla bilgi için [bkz. Özel denetim çeşitliliği.](/dotnet/framework/winforms/controls/varieties-of-custom-controls)

## <a name="design-the-control-layout"></a>Denetim düzenini tasarlama

DemoCalculator denetimi birçok farklı Form Windows içerir. Bu yordamda, Windows Forms Designer'ı kullanarak denetimleri düzenleysiniz.

1. Windows Forms Tasarımcısı'nda, sağ alt köşedeki boyutlandırma tutamacı seçerek ve aşağı ve sağa sürükleyerek DemoCalculator denetiminde daha büyük bir boyuta dokunun. Denetimin sağ alt köşesinde Visual Studio için boyut ve konum bilgilerini bulun. Denetimi yeniden boyutlandırılırken boyut bilgilerini izleyerek denetimin boyutunu 500 ve yükseklik 400 olarak ayarlayın.

2. Araç **Kutusu'da** **Kapsayıcılar düğümünü** seçerek açın. **SplitContainer denetimi** seçin ve tasarımcı yüzeyine sürükleyin.

   `SplitContainer`, DemoCalculator denetimin tasarımcı yüzeyine yerleştirilir.

    > [!TIP]
    > Denetim, `SplitContainer` kendini DemoCalculator denetimi boyutuna göre boyutlar. Denetimin **özellik** ayarlarını görmek için Özellikler penceresine `SplitContainer` bakın. özelliğini <xref:System.Windows.Forms.SplitContainer.Dock%2A> bulun. Değeri [DockStyle.Fill'tir.](xref:System.Windows.Forms.DockStyle.Fill)Bu da denetimin kendisini her zaman `SplitContainer` DemoCalculator denetimi sınırlarına göre boyutlandırması anlamına gelir. Bu davranışı doğrulamak için DemoCalculator denetimi yeniden boyutlandırılır.

3. Özellikler **penceresinde** özelliğinin değerini olarak <xref:System.Windows.Forms.SplitContainer.Dock%2A> `None` değiştirin.

    Denetim `SplitContainer` varsayılan boyutuna küçülür ve artık DemoCalculator denetimi boyutunu takip eder.

4. Denetimin sağ üst köşesinde ![ akıllı etiket glyph ](media/smart-tag-glyph.gif) ( Akıllı Etiket Etiketi ) öğesini `SplitContainer` seçin. Özelliği **olarak ayarlamak için Üst Kapsayıcıda** `Dock` Yerleştir'i `Fill` seçin.

    Denetim, `SplitContainer` DemoCalculator denetimi sınırlarına yerleştirildi.

    > [!NOTE]
    > Tasarımı kolaylaştırmak için çeşitli denetimler akıllı etiketler sunar. Daha fazla bilgi için [bkz. Walkthrough: Windows Forms](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls)denetimlerini akıllı etiketler kullanarak yaygın görevleri gerçekleştirme.

5. Paneller arasındaki dikey kenarlığı seçin ve boşluğun büyük bir çoğunun sol panel tarafından alınması için bunu sağa sürükleyin.

    , `SplitContainer` DemoCalculator denetimine, bunları ayıran taşınabilir kenarlıklı iki panele böler. Sol tarafta yer alan panelde hesap makinesi düğmeleri ve ekranı, sağ tarafta ise kullanıcı tarafından gerçekleştirilen aritmetik işlemlerin kaydı gösterilir.

6. Özellikler **penceresinde** özelliğinin değerini olarak `BorderStyle` `Fixed3D` değiştirin.

7. Araç **Kutusu'da** Ortak **Denetimler düğümünü** seçerek açın. Denetimi `ListView` seçin ve denetimin sağ paneline `SplitContainer` sürükleyin.

8. Denetimin `ListView` akıllı etiket glyph'ini seçin. Akıllı etiket panelinde ayarını olarak `View` `Details` değiştirebilirsiniz.

9. Akıllı etiket panelinde Sütunları **Düzenle'yi seçin.**

   **ColumnHeader Koleksiyon Düzenleyicisi** iletişim kutusu açılır.

10. **ColumnHeader Koleksiyon Düzenleyicisi iletişim** kutusunda Ekle'yi  seçerek denetime bir sütun `ListView` ekleyin. Sütunun özelliğinin değerini `Text` Geçmiş olarak **değiştirme.** Sütunu **oluşturmak** için Tamam'ı seçin.

11. Akıllı etiket panelinde Üst Kapsayıcıya **Yerleştir'i** seçin ve akıllı etiket glyph'i seçerek akıllı etiket panelini kapatın.

12. Kapsayıcılar  düğümü **Araç Kutusundan,** `TableLayoutPanel` denetimin sol paneline bir denetim `SplitContainer` sürükleyin.

    Denetim, `TableLayoutPanel` akıllı etiket paneli açık şekilde tasarımcı yüzeyinde görünür. Denetim, `TableLayoutPanel` alt denetimlerini bir kılavuzda organize eder. Denetim, `TableLayoutPanel` DemoCalculator denetimi ekran ve düğmelerini tutar. Daha fazla bilgi için [bkz. Adım adım: TableLayoutPanel kullanarak denetimleri düzenleme.](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel)

13. Akıllı **etiket panelinde Satırları ve** Sütunları Düzenle'yi seçin.

    Sütun **ve Satır Stilleri** iletişim kutusu açılır.

14. Beş **sütun görüntülenene** kadar Ekle düğmesini seçin. Beş sütunun hepsini ve ardından Boyut **Türü** kutusunda **Yüzde'yi** seçin. Yüzde **değerini** **20 olarak ayarlayın.** Bu, her sütunu aynı genişlikte ayarlar.

15. **Göster'in** altında Satırlar'ı **seçin.**

16. Beş **satır görüntülenene** kadar Ekle'yi seçin. Beş satırın hepsini ve Boyut Türü **kutusunda** **Yüzde'yi** seçin. Yüzde **değerini** **20 olarak ayarlayın.** Bu, her satırı aynı yüksekliğe ayarlar.

17. **Değişikliklerinizi** kabul etmek için Tamam'ı seçin ve akıllı etiket etiketini seçerek akıllı etiket panelini kapatın.

18. Özellikler **penceresinde** özelliğinin değerini olarak `Dock` `Fill` değiştirin.

## <a name="populate-the-control"></a>Denetimi doldurmak

Artık denetimin düzeni ayarlanmış olduğu için DemoCalculator denetimine düğmeler ve bir ekran sızabilirsiniz.

1. Araç **Kutusu'da** denetim `TextBox` simgesini seçin.

   Denetim, `TextBox` denetimin ilk hücresine `TableLayoutPanel` yerleştirilir.

2. Özellikler **penceresinde** denetimin `TextBox` ColumnSpan özelliğinin değerini 5 olarak **değiştirin.**

   Denetim, `TextBox` satırın ortası olan bir konuma taşınır.

3. Denetimin `TextBox` özelliğinin değerini `Anchor` , olarak `Left` `Right` değiştirir.

   Denetim, `TextBox` beş sütuna da yayma için yatay olarak genişler.

4. Denetimin `TextBox` özelliğinin değerini `TextAlign` olarak `Right` değiştirme.

5. Özellikler **penceresinde** özellik `Font` düğümünü genişletin. `Size` **14 olarak ayarlayın** ve denetim `Bold` için **true** olarak `TextBox` ayarlayın.

6. Denetimi `TableLayoutPanel` seçin.

7. Araç **Kutusu'nda** simgesini `Button` seçin.

   Denetim, `Button` denetimin sonraki açık hücresine `TableLayoutPanel` yerleştirilir.

8. Araç **Kutusu'nda,** `Button` denetimin ikinci satırı doldurmak için simgeyi dört kez daha `TableLayoutPanel` seçin.

9. Shift tuşunu `Button` basılı tutarak bu denetimleri seçerek beş denetimi **de** seçin. Denetimleri panoya kopyalamak için **Ctrl** + **C** `Button` tuşlarına basın.

10. Denetimlerin kopyalarını denetimin kalan satırlarına yapıştırmak için **Ctrl** + **V** `Button` tuşlarına üç kez `TableLayoutPanel` basın.

11. Shift tuşunu basılı tutarak `Button` 20 denetimin  hepsini seçin.

12. **Özellikler** penceresinde, `Dock` özelliğinin değerini olarak değiştirin `Fill` .

    Tüm `Button` denetimler, kapsayan hücrelerini dolduracak şekilde yerleştirme.

13. **Özellikler** penceresinde, `Margin` özellik düğümünü genişletin. Değerini `All` **5** olarak ayarlayın.

    Tüm denetimler, aralarında `Button` daha büyük bir kenar boşluğu oluşturmak için daha küçük boyutlardır.

14. **Button10** ve **button20**' i seçin ve sonra düzenden kaldırmak için **Sil** ' e basın.

15. **Button5** ve **button15** öğesini seçin ve ardından `RowSpan` özelliğinin değerini **2** olarak değiştirin. Bu,  **=** demohesaplayıcı denetimi için açık ve düğmeler olacaktır.

## <a name="use-the-document-outline-window"></a>Belge Anahattı penceresini kullanın

Denetiminiz veya formunuz çeşitli denetimlerle doldurulduğu zaman, belge anahattı penceresi ile mizanpajınızı gezinmeyi daha kolay bulabilirsiniz.

1. menü çubuğunda   >  **diğer Windows**  >  **belge anahattını** görüntüle ' yi seçin.

   Belge Anahattı penceresi, Demohesaplayıcı denetiminin ve onun bileşen denetimlerinin ağaç görünümünü gösterir. İçindeki kapsayıcı denetimleri, `SplitContainer` alt denetimlerini ağaçta alt düğümleri olarak göster. Ayrıca Belge Anahattı penceresini kullanarak yerinde denetimleri yeniden adlandırabilirsiniz.

2. **Belge ana hattı** penceresinde **button1**' e sağ tıklayın ve ardından **Yeniden Adlandır**' ı seçin. Adını yeti düğmesi olarak değiştirin.

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

   - MultiplicationButton denetim metni özelliğini **\*** (yıldız işareti) olarak değiştirme

   - OneButton denetim metni özelliğini **1** olarak değiştirin

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

3. Denetimi test etmeyi bitirdiğinizde **Kapat**' ı seçin.

## <a name="use-the-control-on-a-form"></a>Form üzerinde denetimi kullanma

Demohesaplayıcı denetimi, diğer bileşik denetimlerde veya bir formda kullanılabilir. Aşağıdaki yordamda nasıl kullanılacağı açıklanmaktadır.

### <a name="create-the-project"></a>Proje oluşturma

İlk adım uygulama projesini oluşturmaktır. Bu projeyi, özel denetiminizi gösteren uygulamayı oluşturmak için kullanacaksınız.

1. yeni bir **Windows Forms uygulama** projesi oluşturun ve bunu **demohesaplatortest** olarak adlandırın.

2. **Çözüm Gezgini**, **Demohesaplatortest** projesine sağ tıklayın ve **sonra başvuru Ekle Iletişim kutusunu** açmak için **Başvuru Ekle** ' yi seçin.

3. **Projeler** sekmesine gidin ve ardından başvuruyu test projesine eklemek Için Demohesaplatorlib projesini seçin.

4. **Çözüm Gezgini**, **Demohesaplatortest** öğesine sağ tıklayın ve ardından **Başlangıç Project olarak ayarla**' yı seçin.

5. Windows Form Tasarımcısı, formun boyutunu **700 x 500** hakkında artırın.

### <a name="use-the-control-in-the-forms-layout"></a>Formun düzeninde denetimi kullanın

Bir uygulamada Demohesaplayıcı denetimini kullanmak için, onu bir forma yerleştirmeniz gerekir.

1. **Araç kutusu**'Nda **Demohesaplatorlib bileşenleri** düğümünü genişletin.

2. **Araç kutusu** ' ndan **demohesaplayıcı** denetimini formunuza sürükleyin. Denetimi formun sol üst köşesine taşıyın. Denetim formun kenarlıklarına yakınsa, yama *çizgileri* görüntülenir. Anlık görüntü çizgileri, formun `Padding` özelliğinin ve denetimin özelliğinin uzaklığını belirtir `Margin` . Denetimi, snaplines belirtilen konuma konumlandırın.

   Daha fazla bilgi için bkz. [Izlenecek yol: denetimleri, yama çizgileri kullanarak düzenleme](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines).

3. `Button` **Araç kutusu** ' ndan bir denetim sürükleyip form üzerine bırakın.

4. `Button`Denetimi Demohesaplayıcı denetiminin çevresinde taşıyın ve anlık görüntü çizgilerinin nerede göründüğünü gözlemleyin. Bu özelliği kullanarak denetimlerinizi tam ve kolay bir şekilde hizalayabilirsiniz. `Button`İşiniz bittiğinde denetimi silin.

5. Demohesaplayıcı denetimine sağ tıklayıp **Özellikler**' i seçin.

6. `Dock`Özelliğin değerini olarak değiştirin `Fill` .

7. Formu seçin ve ardından `Padding` özellik düğümünü genişletin. All (Hepsi) **değerini** **20 olarak değiştirir.**

   DemoCalculator denetimi, formun yeni değerine uyum sağlayacak `Padding` şekilde azaltıldı.

8. Çeşitli boyutlandırma tutamaçlarını farklı konumlara sürükleyerek formu yeniden boyutlandırabilirsiniz. DemoCalculator denetimine sığacak şekilde nasıl yeniden boyutlandırıldıklarını gözlemlemek.

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, basit bir hesaplayıcı için kullanıcı arabiriminin nasıl inşa edildikleri açıklanmıştır. Devam etmek için hesap makinesi mantığını uygulayarak işlevselliğini genişletebilirsiniz, ardından uygulamayı [ClickOnce.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) Veya, Windows Forms kullanarak resim [görüntüleyici oluşturarak farklı bir öğreticiye devam edin.](../ide/tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms denetimleri](/dotnet/framework/winforms/controls/)
- [Windows Forms denetimleri için erişilebilirlik](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [ClickOnce kullanarak yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
