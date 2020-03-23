---
title: Windows Forms Designer öğretici
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer, get started
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 07526637f2d8083f37f55aa3da36bb01479db087
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589844"
---
# <a name="walkthrough-get-started-with-windows-forms-designer"></a>Walkthrough: Windows Forms Designer ile başlayın

Windows Forms Designer, Windows Forms uygulamalarını oluşturmak için birçok araç sağlar. Bu makalede, aşağıdaki görevler de dahil olmak üzere tasarımcı tarafından sağlanan çeşitli araçları kullanarak bir uygulama oluşturmak için nasıl gösteriş:

- Snaplines kullanarak denetimleri düzenleyin.
- Akıllı etiketleri kullanarak tasarımcı görevlerini yerine getirin.
- Denetimler için kenar boşluklarını ve dolguları ayarlayın.
- Denetimi <xref:System.Windows.Forms.TableLayoutPanel> kullanarak denetimleri düzenleyin.
- Denetim <xref:System.Windows.Forms.SplitContainer> kullanarak denetiminizin düzenini bölümleme.
- Belge Anahattı penceresiyle düzeninizde gezinin.
- Boyut ve konum bilgileri ekranıyla konum denetimleri.
- Özellikler penceresini kullanarak özellik değerlerini ayarlayın.

Bitirdikten sonra, Windows Forms Designer'da bulunan birçok düzen özelliği kullanılarak bir araya getirilmiş özel bir denetime sahip olacaksınız. Bu denetim, basit bir hesap makinesi için kullanıcı arabirimini (UI) uygular. Aşağıdaki resim hesap makinesi denetiminin genel düzenini gösterir:

![Rehberli Tur Hesap Makinesi UI](media/calculator-ui.gif)

## <a name="create-the-custom-control-project"></a>Özel denetim projesini oluşturma

İlk adım DemoCalculator kontrol projesi oluşturmaktır.

1. Visual Studio'u açın ve yeni bir **Windows Forms Control Library** projesi oluşturun. Proje **DemoCalculatorLib**adı .

   ::: moniker range=">=vs-2019"

   ![Visual Studio 2019'da Windows Forms Control Library şablonu](media/windows-forms-control-library-template.png)

   ::: moniker-end

2. Dosyayı yeniden adlandırmak **için, Solution**Explorer'da, **UserControl1.vb'i** sağ seçin veya **UserControl1.cs,** **Yeniden Adlandır'ı**seçin ve dosya adını DemoCalculator.vb veya DemoCalculator.cs olarak değiştirin. "UserControl1" kod öğesine yapılan tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda **Evet'i** seçin.

Windows Forms Designer, DemoCalculator denetimi için tasarımcı yüzeyini gösterir. Bu görünümde, Toolbox'tan denetimleri ve bileşenleri seçip tasarımcı yüzeyine yerleştirerek denetimin görünümünü grafik olarak tasarlayabilirsiniz. Özel denetimler hakkında daha fazla bilgi için, [özel denetim çeşitleri](/dotnet/framework/winforms/controls/varieties-of-custom-controls)ne bakın.

## <a name="design-the-control-layout"></a>Denetim düzenini tasarla

DemoCalculator denetimi birkaç Windows Forms denetimi içerir. Bu yordamda, Windows Forms Designer kullanarak denetimleri düzenlersiniz.

1. Windows Forms Designer'da, sağ alt köşedeki boyutlandırma tutamacını seçip aşağı ve sağa sürükleyerek DemoCalculator denetimini daha büyük bir boyuta değiştirin. Visual Studio'nun sağ alt köşesinde, denetimler için boyut ve konum bilgilerini bulun. Denetimi yeniden boyutlandırırken boyut bilgilerini izleyerek denetimin boyutunu 500 ve yükseklik 400 genişliğe ayarlayın.

2. **Araç**Kutusu'nda, açmak için **Kapsayıcılar** düğümünü seçin. **SplitContainer** denetimini seçin ve tasarımcı yüzeyine sürükleyin.

   DemoCalculator `SplitContainer` denetiminin tasarımcı yüzeyine yerleştirilir.

    > [!TIP]
    > Denetim, `SplitContainer` democalculator denetiminin boyutuna uyacak şekilde boyutlandır. Denetimin **Properties** özellik ayarlarını görmek için `SplitContainer` Özellikler penceresine bakın. <xref:System.Windows.Forms.SplitContainer.Dock%2A> Mülkü bulun. Değeri [DockStyle.Fill'](xref:System.Windows.Forms.DockStyle.Fill)dir, `SplitContainer` bu da denetimin kendisini her zaman DemoCalculator denetiminin sınırlarına kadar boyutlandıracağı anlamına gelir. Bu davranışı doğrulamak için DemoCalculator denetimini yeniden boyutlandırın.

3. **Özellikler** penceresinde, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğin değerini ' `None`den ' e değiştirin

    Denetim `SplitContainer` varsayılan boyutuna küçülür ve artık DemoCalculator denetiminin boyutunu izler.

4. Denetimin sağ üst köşesindeki akıllı etiket](media/smart-tag-glyph.gif)glyph 'i `SplitContainer` (Smart![Tag Glyph) seçin. `Dock` Özelliği `Fill`' ye ayarlamak için Üst **Kapsayıcı'da Dock'u** seçin

    Denetim, `SplitContainer` DemoCalculator denetiminin sınırlarına yanaşacak.

    > [!NOTE]
    > Çeşitli denetimler tasarımı kolaylaştırmak için akıllı etiketler sunar. Daha fazla bilgi için Bkz. [Walkthrough: Windows Forms denetimlerinde Akıllı Etiketler'i kullanarak ortak görevleri gerçekleştirin.](/dotnet/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls)

5. Paneller arasındaki dikey kenarlığı seçin ve sol panel tarafından alınan alanın çoğunu n için sağa sürükleyin.

    DemoCalculator `SplitContainer` denetimini, onları ayıran hareketli kenarlıklı iki panele böler. Soldaki panel hesap makinesi düğmelerini ve ekranı tutar ve sağdaki panel kullanıcı tarafından gerçekleştirilen aritmetik işlemlerin bir kaydını gösterir.

6. **Özellikler** penceresinde, `BorderStyle` özelliğin değerini ' `Fixed3D`den ' e değiştirin

7. **Araç**Kutusu'nda, açmak için **Ortak Denetimler** düğümünü seçin. `ListView` Denetimi seçin ve denetimin sağ paneline sürükleyin. `SplitContainer`

8. Denetimin `ListView` akıllı etiket glyph'ini seçin. Akıllı etiket panelinde, `View` ayarı `Details`' da ' olarak değiştirin

9. Akıllı etiket panelinde **Sütunları Edit'i**seçin.

   **ColumnHeader Collection Editor** iletişim kutusu açılır.

10. **ColumnHeader Collection Editor** iletişim kutusunda, denetime sütun eklemek `ListView` için **Ekle'yi** seçin. Sütunun `Text` özelliğinin değerini **Geçmiş**olarak değiştirin. Sütunu oluşturmak için **Tamam'ı** seçin.

11. Akıllı etiket **panelinde, Ana Kapsayıcı'da Dock'u**seçin ve ardından akıllı etiket panelini kapatmak için akıllı etiket glyph'sini seçin.

12. **Kapsayıcılar** düğümü **Araç**Kutusu'ndan, denetimi `TableLayoutPanel` denetimin `SplitContainer` sol paneline sürükleyin.

    Denetim, `TableLayoutPanel` akıllı etiket paneli açık olan tasarımcı yüzeyinde görünür. Denetim, `TableLayoutPanel` alt denetimlerini bir ızgarada düzenler. Denetim, `TableLayoutPanel` DemoCalculator denetiminin ekranını ve düğmelerini tutar. Daha fazla bilgi için [Bkz. Walkthrough: TableLayoutPanel kullanarak denetimleri düzenleyin.](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel)

13. Akıllı etiket panelinde **Satırları ve Sütunları Edit'i** seçin.

    **Sütun ve Satır Stilleri** iletişim kutusu açılır.

14. Beş sütun görüntülenene kadar **Ekle** düğmesini seçin. Beş sütunun tümünü seçin ve ardından **Boyut Türü** kutusunda **Yüzde'yi** seçin. **Yüzde** değerini **20**olarak ayarlayın. Bu, her sütunu aynı genişliğe ayarlar.

15. **Göster**altında, **Satırları**seçin.

16. Beş satır görüntülenene kadar **Ekle'yi** seçin. Beş satırın tümünü ve Boyut **Türü** kutusunda **yüzde'yi** seçin. **Yüzde** değerini **20**olarak ayarlayın. Bu, her satırı aynı yüksekliğe ayarlar.

17. Değişikliklerinizi kabul etmek için **Tamam'ı** seçin ve ardından akıllı etiket panelini kapatmak için akıllı etiket gph'sini seçin.

18. **Özellikler** penceresinde, `Dock` özelliğin değerini ' `Fill`den ' e değiştirin

## <a name="populate-the-control"></a>Denetimi doldurma

Denetimin düzeni ayarlıolduğundan, DemoCalculator denetimini düğmeler ve ekranla doldurabilirsiniz.

1. **Araç Kutusu'nda,** denetim `TextBox` simgesini çift tıklatın.

   Denetim, `TextBox` denetimin ilk hücresine `TableLayoutPanel` yerleştirilir.

2. **Özellikler** penceresinde, denetimin ColumnSpan `TextBox` özelliğinin değerini **5**olarak değiştirin.

   Denetim, `TextBox` satırında ortalanan bir konuma taşınır.

3. `TextBox` Denetimin `Anchor` özelliğinin değerini `Left`, . `Right`

   Denetim, `TextBox` beş sütunun tümüne de yayılacak şekilde yatay olarak genişler.

4. `TextBox` Denetimin `TextAlign` özelliğinin değerini ' den' e `Right`değdirin.

5. **Özellikler** penceresinde özellik düğümlerini genişletin. `Font` **14**olarak `Bold` ayarlayın `Size` ve **true** `TextBox` denetim için doğru ayarlayın.

6. `TableLayoutPanel` Denetimi seçin.

7. **Araç Kutusu'nda,** simgeyi `Button` çift tıklatın.

   Denetim, `Button` denetimin bir sonraki açık `TableLayoutPanel` hücresine yerleştirilir.

8. **Araç Kutusu'nda,** `Button` `TableLayoutPanel` denetimin ikinci satırını doldurmak için simgeyi dört kez daha tıklatın.

9. `Button` **Shift** tuşunu basılı tutarken bunları seçerek beş denetimin tümünü seçin. Denetimleri `Button` panoya kopyalamak için **Ctrl**+**C** tuşuna basın.

10. `Button` Denetimlerin kopyalarını `TableLayoutPanel` denetimin kalan satırlarına yapıştırmak için **Ctrl**+**V** tuşuna üç kez basın.

11. **Shift** tuşunu `Button` basılı tutarken bunları seçerek tüm 20 denetimi seçin.

12. **Özellikler** penceresinde, `Dock` özelliğin değerini ' `Fill`den ' e değiştirin

    Tüm `Button` kontroller, içerdiği hücreleri doldurmak için kenetlendi.

13. **Özellikler** penceresinde özellik düğümlerini genişletin. `Margin` Değerini `All` **5**olarak ayarlayın.

    Tüm `Button` denetimler aralarında daha büyük bir kenar boşluğu oluşturmak için daha küçük boyutlandırılır.

14. **button10** ve **button20'yi**seçin ve ardından düzenden kaldırmak için **Sil** tuşuna basın.

15. **button5** ve **button15'i**seçin ve `RowSpan` sonra mülklerinin değerini **2**olarak değiştirin. Bunlar DemoCalculator **Clear** denetimi **=** için Açık ve düğmeler olacaktır.

## <a name="use-the-document-outline-window"></a>Belge Anahat penceresini kullanma

Denetiminiz veya formunuz çeşitli denetimlerle doldurulduğunda, Belge Anahattı penceresinde düzeninizde gezinmek daha kolay olabilir.

1. Menü çubuğunda,**Diğer Windows** > **Belge Anahattını** **Görüntüle'yi** > seçin.

   Belge Anahat penceresi, DemoCalculator denetiminin ve kurucu denetimlerinin bir ağaç görünümünü gösterir. Çocuğunun ağaçta subnode olarak kontrol lerini `SplitContainer` gösterdiği gibi kapsayıcı denetimleri. Belge Anahattı penceresini kullanarak denetimleri yerinde yeniden adlandırabilirsiniz.

2. Belge **Anahat** penceresinde, sağ seç **düğmesi1**ve ardından **Yeniden Adlandır'ı**seçin. Adını sevenButton olarak değiştirin.

3. Belge **Anahat** penceresini kullanarak, `Button` denetimleri tasarımcı tarafından oluşturulan addan üretim adına aşağıdaki listeye göre yeniden adlandırın:

   - button1 **-7Button**

   - button2 **-eightButton**

   - button3 'den **9Button'a**

   - button4 için **divisionButton**

   - **button5 clearButton** için

   - button6 **-fourButton**

   - button7 **-fiveButton**

   - button8 **-sixButton**

   - button9 **çarpmaButton**

   - button11 to **oneButton**

   - button12 için **twoButton**

   - button13 için **üçDüğme**

   - button14 için **çıkarmaDüğmesi**

   - button15 **eşittirDüğme**

   - button16 için **zeroButton**

   - button17 **değiştirmek içinSignButton**

   - button18 **ondalık Düğme**

   - button19 için **additionButton**

4. Belge **Anahattı** ve **Özellikleri** pencerelerini `Text` kullanarak, `Button` aşağıdaki listeye göre her denetim adının özellik değerini değiştirin:

   - yediDüğme denetim metin özelliğini **7** olarak değiştirin

   - sekizDüğme denetim metin özelliğini **8** olarak değiştirme

   - nineButton denetim metin özelliğini **9** olarak değiştirme

   - BölmeDüğme denetimi metin özelliğini **/** değiştirin (ileri eğik çizgi)

   - ClearButton denetim metin özelliğini **Temizle** olarak değiştirme

   - fourButton denetim metin özelliğini **4** olarak değiştirme

   - fiveButton denetim metin özelliğini **5** olarak değiştirme

   - altıDüğme denetim metin özelliğini **6** olarak değiştirin

   - Çarpma düğme denetimi metin özelliğini **\*** değiştirin (yıldız işareti)

   - oneButton denetimi metin özelliğini **1** olarak değiştirme

   - twoButton denetim metin özelliğini **2** olarak değiştirme

   - üçDüğme denetimi metin özelliğini **3** olarak değiştirin

   - Çıkarma Düğme denetimi metin özelliğini (tire) olarak **-** değiştirin

   - Eşitleri değiştirmeDüğme denetimi metin **=** özelliğini (eşittir işareti) olarak değiştirin

   - zeroButton denetim metin özelliğini **0** olarak değiştirme

   - ChangeSignButton denetim metin özelliğini**+/-**

   - Ondalık Düğme denetimi metin özelliğini **''** olarak değiştirin (nokta)

   - EklemeDüğme denetimi metin özelliğini (artı işareti) değiştirin **+**

5. Tasarımcı yüzeyinde, `Button` **Shift** tuşunu basılı tutarken tüm denetimleri seçerek seçin.

6. **Özellikler** penceresinde özellik düğümlerini genişletin. `Font` **14**olarak `Bold` ayarlayın `Size` ve **true** tüm denetimler `Button` için doğru ayarlayın.

Bu, DemoCalculator denetiminin tasarımını tamamlar. Geriye kalan tek şey hesap makinesi mantığını sağlamak.

## <a name="implement-event-handlers"></a>Olay işleyicileri uygulama

DemoCalculator denetimindeki düğmelerde hesap makinesi mantığının çoğunu uygulamak için kullanılabilecek olay işleyicileri vardır. Windows Forms Designer, tüm düğmeler için tüm olay işleyicilerinin saplamalarını tek bir çift tıklatarak uygulamanızı sağlar.

1. Tasarımcı yüzeyinde, `Button` **Shift** tuşunu basılı tutarken tüm denetimleri seçerek seçin.

2. `Button` Denetimlerden birini çift tıklatın.

   Kod Düzenleyicisi, tasarımcı tarafından oluşturulan olay işleyicilerine açılır.

## <a name="test-the-control"></a>Denetimi test edin

DemoCalculator denetimi <xref:System.Windows.Forms.UserControl> sınıftan devraldığı için, kullanıcı denetimi **test kapsayıcısı**ile davranışını sınayabilirsiniz. Daha fazla bilgi için [bkz: UserControl'un çalışma zamanı davranışını test](/dotnet/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol)edin.

1. **UserControl Test Konteynerinde**DemoCalculator denetimini oluşturmak ve çalıştırmak için **F5** tuşuna basın.

2. `SplitContainer` Paneller arasındaki kenarlığı seçin ve sola ve sağa sürükleyin. Ve `TableLayoutPanel` tüm alt kontrolleri kullanılabilir alana sığacak şekilde kendilerini yeniden boyutlandırın.

3. Denetimi test etme yi bitirdiğinizde **Kapat'ı**seçin.

## <a name="use-the-control-on-a-form"></a>Form üzerindeki denetimi kullanma

DemoCalculator denetimi diğer bileşik denetimlerde veya formda kullanılabilir. Aşağıdaki yordam, nasıl kullanılacağını açıklar.

### <a name="create-the-project"></a>Proje oluşturma

İlk adım uygulama projesi oluşturmaktır. Bu projeyi, özel denetiminizi gösteren uygulamayı oluşturmak için kullanırsınız.

1. Yeni bir **Windows Forms Uygulama** projesi oluşturun ve **democalculatortest**adını.

2. **Çözüm Gezgini'nde** **DemoCalculatorTest** projesini sağ tıklatın ve ardından **Başvuru Ekle** iletişim kutusunu açmak için Başvuru **Ekle'yi** seçin.

3. **Projeler** sekmesini seçin ve ardından test projesine başvuru eklemek için DemoCalculatorLib projesini çift tıklatın.

4. **Solution Explorer'da** **DemoCalculatorTest'i**sağ tıklatın ve ardından **StartUp Project olarak ayarla'yı**seçin.

5. Windows Forms Designer'da formun boyutunu yaklaşık **700 x 500'e**yükseltin.

### <a name="use-the-control-in-the-forms-layout"></a>Formun düzeninde denetimi kullanma

Bir uygulamada DemoCalculator denetimini kullanmak için bir forma yerleştirmeniz gerekir.

1. **Araç Kutusunda,** **DemoCalculatorLib Bileşenleri** düğümlerini genişletin.

2. **DemoCalculator** denetimini **Araç Kutusu'ndan** formunuza sürükleyin. Denetimi formun sol üst köşesine taşıyın. Denetim formun kenarlıklarına yakın *olduğunda, snaplines* görüntülenir. Snaplines formun `Padding` özelliğinin ve denetimin `Margin` özelliğinin uzaklığını gösterir. Denetimi snaplines tarafından belirtilen konuma yerleştirin.

   Daha fazla bilgi için [Bkz. Walkthrough: Snaplines kullanarak denetimleri düzenleyin.](/dotnet/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines)

3. `Button` **Toolbox'tan** bir denetim sürükleyin ve forma bırakın.

4. Denetimi `Button` DemoCalculator denetiminin etrafında taşıyın ve snaplines'in nerede göründüğünü gözlemleyin. Bu özelliği kullanarak kontrollerinizi tam ve kolay bir şekilde hizalayabilirsiniz. Bitirdiğinizde `Button` denetimi silin.

5. DemoCalculator denetimini sağ seçin ve ardından **Özellikler'i**seçin.

6. Özelliğin değerini `Dock` ' `Fill`den' e değdirme

7. Formu seçin ve ardından `Padding` özellik düğümünü genişletin. **Tüm** değerini **20'ye**değiştirin.

   DemoCalculator denetiminin boyutu, formun yeni `Padding` değerini karşılayacak şekilde küçültülür.

8. Çeşitli boyutlandırma tutamaçları farklı konumlara sürükleyerek formu yeniden boyutlandırın. DemoCalculator denetiminin uyacak şekilde nasıl yeniden boyutlandırıldığını gözlemleyin.

## <a name="next-steps"></a>Sonraki adımlar

Bu makalede, basit bir hesap makinesi için kullanıcı arabirimi oluşturmak için nasıl gösterilmiştir. Devam etmek için, hesap makinesi mantığını uygulayarak işlevselliğini genişletebilir, ardından [ClickOnce'yi kullanarak uygulamayı yayımlayabilirsiniz.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) Veya, [Windows Formlarını kullanarak bir resim görüntüleyicisi oluşturduğunuz](../ide/tutorial-1-create-a-picture-viewer.md)farklı bir öğreticiye devam edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms denetimleri](/dotnet/framework/winforms/controls/)
- [Windows Forms denetimleri için erişilebilirlik](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)
- [ClickOnce kullanarak yayımla](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
